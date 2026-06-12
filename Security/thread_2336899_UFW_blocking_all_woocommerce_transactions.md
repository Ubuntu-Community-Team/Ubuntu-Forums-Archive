---
title: "UFW blocking all woocommerce transactions"
date: 2016-09-12
forum: Security
---

### Post by clintonlee83 on 2016-09-12
[COLOR=#111111][FONT=Ubuntu]I'm using UFW with Ubuntu, a lamp stack and woocommerce on wordpress. Everything works great except UFW blocks anyone trying to use a credit cart while checking out on woocommerce.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the error messages from the logs:
```
[/FONT][/COLOR]
Sep 12 08:43:52 signa-01 kernel: [425905.328802] [UFW BLOCK] IN=eth0 OUT= MAC=04:01:18:6b:a8:01:30:7c:5e:91:94:30:08:00 SRC=99.225.231.201 DST=159.203.63.97 LEN=52 TOS=0x00 PREC=0x00 TTL=121 ID=29171 DF PROTO=TCP SPT=50130 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0

```[COLOR=#111111][FONT=Ubuntu]

How can I solve this?[/FONT][/COLOR]

---

### Post by Habitual on 2016-09-12
> **clintonlee83 said:**
> ```

...**[COLOR=#ff0000]DPT=443[/COLOR]** ...

```[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
Open port 443

---

### Post by clintonlee83 on 2016-09-13
Habitual, thank you. So simple, best answer ever.

---

### Post by Habitual on 2016-09-13
Glad it worked out!

Please make certain your osCommerce** is up to date.** :)

---

