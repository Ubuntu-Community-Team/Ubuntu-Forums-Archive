---
title: "Problems with Node Pack Manager"
date: 2017-10-22
forum: Ubuntu Dev Link Forum
---

### Post by dam034 on 2017-10-22
Dear users,

initially I installed npm on my server to install phonegap.

Now phonegap told me it was available an update and to execute a command to update it. I executed that command and this is the result:
```
root@s-lavorativo:/srv/applicazioni/ddns# npm i -g phonegap
npm WARN deprecated connect@2.30.2: connect 2.x series is deprecated
npm WARN deprecated node-uuid@1.4.8: Use uuid module instead
npm WARN deprecated tough-cookie@2.2.2: ReDoS vulnerability parsing Set-Cookie https://nodesecurity.io/advisories/130
- connect node_modules/phonegap/node_modules/connect-phonegap/node_modules/connect
- serve-static node_modules/phonegap/node_modules/connect-phonegap/node_modules/connect/node_modules/serve-static
- send node_modules/phonegap/node_modules/connect-phonegap/node_modules/connect/node_modules/serve-static/node_modules/send
- localtunnel node_modules/phonegap/node_modules/connect-phonegap/node_modules/localtunnel
- request node_modules/phonegap/node_modules/connect-phonegap/node_modules/localtunnel/node_modules/request
- yargs node_modules/phonegap/node_modules/connect-phonegap/node_modules/localtunnel/node_modules/yargs
- http-signature node_modules/phonegap/node_modules/connect-phonegap/node_modules/request/node_modules/http-signature
- cordova-common node_modules/phonegap/node_modules/cordova/node_modules/cordova-common
- cordova-lib node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib
- aliasify node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/aliasify
- browserify-transform-tools node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/aliasify/node_modules/browserify-transform-tools
- falafel node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/aliasify/node_modules/browserify-transform-tools/node_modules/falafel
- cordova-create node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-create
- cordova-common node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-create/node_modules/cordova-common
- cordova-fetch node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-create/node_modules/cordova-fetch
- cordova-fetch node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-fetch
- cordova-common node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-fetch/node_modules/cordova-common
- cordova-js node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js
- browserify node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify
- browser-pack node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/browser-pack
- crypto-browserify node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/crypto-browserify
- create-hash node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/crypto-browserify/node_modules/create-hash
- create-hmac node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/crypto-browserify/node_modules/create-hmac
- diffie-hellman node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/crypto-browserify/node_modules/diffie-hellman
- pbkdf2 node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/crypto-browserify/node_modules/pbkdf2
- insert-module-globals node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/insert-module-globals
- lexical-scope node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/insert-module-globals/node_modules/lexical-scope
- astw node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/insert-module-globals/node_modules/lexical-scope/node_modules/astw
- module-deps node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/module-deps
- detective node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/module-deps/node_modules/detective
- shasum node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/shasum
- syntax-error node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-js/node_modules/browserify/node_modules/syntax-error
- cordova-serve node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-serve
- express node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-serve/node_modules/express
- send node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/cordova-serve/node_modules/express/node_modules/send
- init-package-json node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/init-package-json
- npm-package-arg node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/init-package-json/node_modules/npm-package-arg
- read-package-json node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/init-package-json/node_modules/read-package-json
- normalize-package-data node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/init-package-json/node_modules/read-package-json/node_modules/normalize-package-data
- npm node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm
- fs-vacuum node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/fs-vacuum
- fstream node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/fstream
- fstream-npm node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/fstream-npm
- fstream-ignore node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/fstream-npm/node_modules/fstream-ignore
- fstream node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/fstream-npm/node_modules/fstream-ignore/node_modules/fstream
- init-package-json node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/init-package-json
- node-gyp node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/node-gyp
- request node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/node-gyp/node_modules/request
- http-signature node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/node-gyp/node_modules/request/node_modules/http-signature
- normalize-package-data node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/normalize-package-data
- npm-install-checks node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-install-checks
- npm-package-arg node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-package-arg
- npm-registry-client node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-registry-client
- normalize-package-data node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-registry-client/node_modules/normalize-package-data
- npm-package-arg node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-registry-client/node_modules/npm-package-arg
- request node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-registry-client/node_modules/request
- http-signature node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/npm-registry-client/node_modules/request/node_modules/http-signature
- read-installed node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/read-installed
- read-package-json node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/read-installed/node_modules/read-package-json
- normalize-package-data node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/read-installed/node_modules/read-package-json/node_modules/normalize-package-data
- read-package-json node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/read-package-json
- normalize-package-data node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/read-package-json/node_modules/normalize-package-data
- realize-package-specifier node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/realize-package-specifier
- npm-package-arg node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/realize-package-specifier/node_modules/npm-package-arg
- request node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/request
- http-signature node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/request/node_modules/http-signature
- tar node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/tar
- fstream node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/npm/node_modules/tar/node_modules/fstream
- request node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/request
- tar node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/tar
- fstream node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/tar/node_modules/fstream
- xcode node_modules/phonegap/node_modules/cordova/node_modules/cordova-lib/node_modules/xcode
- insight node_modules/phonegap/node_modules/cordova/node_modules/insight
- configstore node_modules/phonegap/node_modules/cordova/node_modules/insight/node_modules/configstore
- os-name node_modules/phonegap/node_modules/cordova/node_modules/insight/node_modules/os-name
- win-release node_modules/phonegap/node_modules/cordova/node_modules/insight/node_modules/os-name/node_modules/win-release
- request node_modules/phonegap/node_modules/cordova/node_modules/insight/node_modules/request
- http-signature node_modules/phonegap/node_modules/cordova/node_modules/insight/node_modules/request/node_modules/http-signature
- latest-version node_modules/phonegap/node_modules/cordova/node_modules/update-notifier/node_modules/latest-version
- package-json node_modules/phonegap/node_modules/cordova/node_modules/update-notifier/node_modules/latest-version/node_modules/package-json
- registry-url node_modules/phonegap/node_modules/cordova/node_modules/update-notifier/node_modules/latest-version/node_modules/package-json/node_modules/registry-url
- semver-diff node_modules/phonegap/node_modules/cordova/node_modules/update-notifier/node_modules/semver-diff
- configstore node_modules/phonegap/node_modules/insight/node_modules/configstore
- win-release node_modules/phonegap/node_modules/insight/node_modules/os-name/node_modules/win-release
- request node_modules/phonegap/node_modules/insight/node_modules/request
- http-signature node_modules/phonegap/node_modules/insight/node_modules/request/node_modules/http-signature
- prompt node_modules/phonegap/node_modules/phonegap-build/node_modules/prompt
- utile node_modules/phonegap/node_modules/phonegap-build/node_modules/prompt/node_modules/utile
- utile node_modules/phonegap/node_modules/prompt/node_modules/utile
- package-json node_modules/phonegap/node_modules/update-notifier/node_modules/latest-version/node_modules/package-json
- registry-auth-token node_modules/phonegap/node_modules/update-notifier/node_modules/latest-version/node_modules/package-json/node_modules/registry-auth-token
- registry-url node_modules/phonegap/node_modules/update-notifier/node_modules/latest-version/node_modules/package-json/node_modules/registry-url
- semver-diff node_modules/phonegap/node_modules/update-notifier/node_modules/semver-diff
/usr/local/lib
&#9492;&#9472;&#9472; (empty)

npm WARN optional Skipping failed optional dependency /phonegap/chokidar/fsevents:
npm WARN notsup Not compatible with your operating system or architecture: fsevents@1.1.2
npm ERR! Linux 4.4.0-97-generic
npm ERR! argv "/usr/bin/nodejs" "/usr/bin/npm" "i" "-g" "phonegap"
npm ERR! node v4.2.6
npm ERR! npm  v3.5.2
npm ERR! path /usr/local/lib/node_modules/.staging/abbrev-b74e4034
npm ERR! code ENOENT
npm ERR! errno -2
npm ERR! syscall rename

npm ERR! enoent ENOENT: no such file or directory, rename '/usr/local/lib/node_modules/.staging/abbrev-b74e4034' -> '/usr/local/lib/node_modules/phonegap/node_modules/npm/node_modules/abbrev'
npm ERR! enoent ENOENT: no such file or directory, rename '/usr/local/lib/node_modules/.staging/abbrev-b74e4034' -> '/usr/local/lib/node_modules/phonegap/node_modules/npm/node_modules/abbrev'
npm ERR! enoent This is most likely not a problem with npm itself
npm ERR! enoent and is related to npm not being able to find a file.
npm ERR! enoent 

npm ERR! Please include the following file with any support request:
npm ERR!     /srv/applicazioni/ddns/npm-debug.log
npm ERR! code 1
```

Now, when I try to launch phonegap, I get this error:
```
root@s-lavorativo:/srv/applicazioni/ddns# phonegap -d serve
module.js:328
    throw err;
    ^

Error: Cannot find module 'cordova-lib'
    at Function.Module._resolveFilename (module.js:326:15)
    at Function.Module._load (module.js:277:25)
    at Module.require (module.js:354:17)
    at require (internal/module.js:12:17)
    at Object.<anonymous> (/usr/local/lib/node_modules/phonegap/node_modules/cordova/cordova.js:23:19)
    at Module._compile (module.js:410:26)
    at Object.Module._extensions..js (module.js:417:10)
    at Module.load (module.js:344:32)
    at Function.Module._load (module.js:301:12)
    at Module.require (module.js:354:17)
```

This is due to the npm error, how can I fix the npm issue?

Thanks

---

