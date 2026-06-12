---
title: "How do you make your sever beep?"
date: 2006-05-20
forum: Server Platforms
---

### Post by zasf on 2006-05-20
I'm running a ubuntu server, since there is no monitor,keyboard,etc connected I use ssh and some script to automate things. 

I would like the server to beep to signal different states/warning, how do you do that?

Thanks

---

### Post by louis_nichols on 2006-05-21
I have a desklet which tells me of mails received via pop3. And when I get an email, it causes a beep. That's done via a script that's in the package, which contains the following

```
#!/bin/sh
#
# Written by S.Fourmanoit, 2005
#
# Small script, probably not portable across UNIXes,
# That sends a bell character (ascii 0x07) to the first writable terminal
# device (i.e. own by the current user). This has only been tested
# on linux systems, with GNU sed, cut from GNU coretutils, w from
# procps and GNU which. Bourne script by itself should be POSIX
# 1003.2 and 1003.2a compliant.

DEV=`w -hu \`whoami\` | \
      sed -n '1{s/[[:space:]]\+/\t/g;p}' | cut -f2`
: ${DEV:=null}
`which echo` -n -e '\a' > /dev/$DEV

```

It works. All credits go to sylvain for this (lead developer of adesklets)

---

### Post by zasf on 2006-05-21
thanks for your reply, I tried that but no help.

I found a very nice package called 'beep' that works.

---

