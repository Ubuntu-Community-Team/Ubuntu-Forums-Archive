---
title: "nodejs: node-sqlite3 Error: Module version mismatch. Expected 11, got 1."
date: 2013-12-22
forum: Ubuntu Application Development
---

### Post by Yuzem on 2013-12-22
I'm developing an application using node and node-sqlite3, everything was find with Ubuntu 13.04, now I upgraded to 13.10 and it is not working anymore.

To replicate the error, install the packages:
```
sudo apt-get install nodejs node-sqlite3
```

Run this commnad:
```
nodejs -e "require('sqlite3')"
```

Get the error:
```
module.js:356
  Module._extensions[extension](this, filename);
                               ^
Error: Module version mismatch. Expected 11, got 1.
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Module.require (module.js:364:17)
    at require (module.js:380:17)
    at Object.<anonymous> (/usr/lib/nodejs/sqlite3/sqlite3.js:1:104)
    at Module._compile (module.js:456:26)
    at Object.Module._extensions..js (module.js:474:10)
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Module.require (module.js:364:17)
```

Thanks in advance!

---

### Post by Yuzem on 2013-12-22
Ok, this can be solved by installing nodejs-legacy and then installing sqlite3 using npm:
```
sudo apt-get install nodejs-legacy
npm install sqlite3
```
If nodejs-legacy is not installed, installing sqlite3 using npm will fail.

---

