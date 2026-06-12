---
title: "Mail server only authenticates while signed into SSH"
date: 2015-03-03
forum: Server Platforms
---

### Post by daniel253 on 2015-03-03
Hello, I recently set up a Mail server using Dovecot and Postfix on my Ubuntu 14.04.1 server. It works great, but has one major flaw and I'm wondering if anybody knows what could be the cause.
It will only allow me to sign in from external applications (Thunderbird / Android Mail) while I have an SSH session open, otherwise it keeps failing to authenticate the username/password, but as soon as I connect an SSH session to my server (even before logging in) suddenly everything is allowed to connect properly. Then when I disconnect the session everything fails once again when I try to refresh.
I don't use forums very often so I'm sorry if I've left out important details, if there's anything you need (output from diagnostic commands, etc.) let me know.

---

