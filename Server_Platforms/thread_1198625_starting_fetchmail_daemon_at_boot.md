---
title: "starting fetchmail daemon at boot ?"
date: 2009-06-27
forum: Server Platforms
---

### Post by pdc124 on 2009-06-27
so i can retrieve my POP mail with fetchmail and a ~/.fetchmailrc file  with a --set daemon 180

how do I ensure the daemin is started on a reboot ?

---

### Post by HermanAB on 2009-06-27
The lazy way is to add your start-up commands to the bottom of rc.local

---

### Post by AlexBooton on 2011-11-01
> **HermanAB said:**
> The lazy way is to add your start-up commands to the bottom of rc.local

I'm still having a problem.  Fetchmail is not starting at boot.

Here the line in my /etc/rc.local

[INDENT]fetchmail -d 60 -f /etc/fetchmailrc[/INDENT]

When I run this from the terminal I get:

[INDENT]File /etc/fetchmailrc must be owned by you.[/INDENT]

Here's ls -l /etc/fetchmailrc:

[INDENT]-rw------- 1 fetchmail root 3416 2011-10-17 22:36 /etc/fetchmailrc [/INDENT]

So I have an identical copy in /root.  Here's what ls -l /root/fetchmailrc looks like:
 [INDENT]
-rw------- 1 root root 3416 2011-10-17 22:36 /root/fetchmailrc [/INDENT]

But I don't want to run this from a terminal anyway.  I want it to start at boot.

What am I doing wrong?

Thanks

---

