---
title: "Apache 2 Errors"
date: 2007-09-13
forum: Server Platforms
---

### Post by tytanic11@gmail.com on 2007-09-13
When trying to restart Apache, I get : 

 * Stopping apache 2.0 web server...                                                                                                                         : No such file or directorybled/*.load
: No such file or directorybled/*.conf
: No such file or directorynf
: No such file or directorynf
: No such file or directory^.#]*
: No such file or directoryabled/[^.#]*


Does anyone know why it does this? It says [Fail] and Apache won't restart.

---

### Post by a9k on 2007-09-14
This can happen when you change the configuration, don't check it, and then restart the server.
Try 
apache2ctl -t
Hopefully it will spit out some error that will help you pin down the problem.

---

