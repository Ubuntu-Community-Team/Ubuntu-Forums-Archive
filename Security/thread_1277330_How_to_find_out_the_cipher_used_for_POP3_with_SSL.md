---
title: "How to find out the cipher used for POP3 with SSL"
date: 2009-09-28
forum: Security
---

### Post by Ulysses_ on 2009-09-28
How do I find out what cipher (eg RC4 128 bit) is used for POP3 SSL?    I know with HTTPS you can double-click on the padlock icon and the popup tells you, but how do I find out the cipher used for POP3 SSL?

---

### Post by sasho_zl on 2009-09-29
I think this command will give you all the info you need:

[COLOR=Black]**[FONT=monospace][COLOR=blue]openssl s_client -host pop.name.com -port 995[/COLOR][/FONT]**[/COLOR]

---

