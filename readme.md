## Vite + Wasm

I'm trying to the zbar.wasm package to import with vite.

It's shipped as commonJS, but uses a `.bin` file to get around some webpack issues:

https://github.com/samsam2310/zbar.wasm/issues/21

Now I can't figure out how to import the thing into a vite project. I've tried:

1. `import { instantiate } from './node_modules/zbar.wasm/dist/zbar.js'`
2. `import { loadWasmInstance } from './node_modules/zbar.wasm/dist/load'`
2. `import { loadWasmInstance } from './node_modules/zbar.wasm/dist/load-browser'`

I think the issue is around vite not knowing how to handle the .bin file. For this, I tried modifying the shipped code with `?url` on the end, no dice.

## Reproduction

1. npm install
2. npm start
3. Visit the server in your browser.

See this:

```bash
✘ [ERROR] No loader is configured for ".bin" files: node_modules/zbar.wasm/dist/zbar.wasm.bin

    node_modules/zbar.wasm/dist/load-browser.js:15:48:
      15 │ const zbar_wasm_bin_1 = __importDefault(require("./zbar.wasm.bin"));
         ╵                                                 ~~~~~~~~~~~~~~~~~
```



