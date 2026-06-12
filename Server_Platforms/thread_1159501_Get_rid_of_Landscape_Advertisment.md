---
title: "Get rid of Landscape Advertisment"
date: 2009-05-14
forum: Server Platforms
---

### Post by Ttech on 2009-05-14
Hi,
  I recently upgraded the system to 9.04 and I started getting advertisements for Landscape when I login, I find the information on login a tad useful but I find the fact that my computer is adverting extremely annoying to anyone who logs in. How do I make this go away (but if possible keep the info) and will this be the common thing for future versions.

    Thanks

---

### Post by mbeach on 2009-05-14
I suspect if you edit 
/usr/share/landscape/landscape-sysinfo.wrapper
you could adjust it slightly.

To stop it running completely I suspect you need to dig around  /etc/update-motd.d/

you might find yourself digging down to:
/usr/share/pyshared/landscape/sysinfo/landscapelink.py
if you just want to amend the static text output.

Might be better to wait for someone with a little more info.

---

### Post by Xaroth on 2009-05-15
Might be a quick and dirty hack, but I fixed it as follows:

open up /usr/share/pyshared/landscape/sysinfo/landscapelink.py and comment the following 3 lines:

#        self._sysinfo.add_footnote(
#            "Graph this data and manage this system at "
#            "https://landscape.canonical.com/")


then check if it works properly by running landscape-sysinfo

or you can always just change the footnote to what you like ;)

---

### Post by sartic on 2009-10-04
didn't get this, so adware is what can we expect from canonical?

---

### Post by cariboo on 2009-10-04
It only comes up in the mtod when you first login using ssh.

---

### Post by t3r0 on 2009-10-04
> **cariboo907 said:**
> It only comes up in the mtod when you first login using ssh.

First time? I see it every time when I login.

---

### Post by cariboo on 2009-10-04
I don't log into the server that often, so I may not be paying to much attention. :)

---

### Post by negativ on 2009-10-28
> **t3r0 said:**
> First time? I see it every time when I login.

Also via local logins.  Quite distasteful, I agree.

---

