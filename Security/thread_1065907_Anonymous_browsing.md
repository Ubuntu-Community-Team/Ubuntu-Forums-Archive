---
title: "Anonymous browsing?"
date: 2009-02-10
forum: Security
---

### Post by duds2008 on 2009-02-10
Hello helpful people!! I`ve been using Linux (various distros) for about a year now. I consider myself to be fairly competent and have usually overcome most of the problems I have encountered along the way. I am however baffled by the anon-proxy program? The man pages are a little unhelpful. Could anybody tell me what I am doing wrong here?

duds@saintsandsoldiers:~$ sudo anon-proxy -jad
[sudo] password for duds: 
[2009/02/10-16:48:38, debug   ] starting as daemon
[2009/02/10-16:48:38, debug   ] daemon - before fork()
[2009/02/10-16:48:38, debug   ] child after fork...
[2009/02/10-16:48:38, debug   ] Exiting parent!
duds@saintsandsoldiers:~$ 

The last time I did this the Ubuntu repo`s refused to acknowledge my connection to them?
Any help or suggestions regarding this is sincerely appreciated.
Thank you. Duds.:)

---

### Post by cdenley on 2009-02-10
Are you sure it's not running, it looks like it forked a daemon process into the background.
```

sudo netstat -tlnp

```
It looks like the same concept as tor. Are you sure you understand what it doesn't accomplish? There will be no extra encryption between the last node and the destination server. You cannot trust any node, so you should assume the last node is a malicious user running a JAP server to intercept sensitive data from users who think they are protecting themselves. That malicious user will be able to read any data that isn't encrypted (https), including any data which may identify you. Of course, they wouldn't be able to trace it back to your IP, unless they also happen to control the initial node you are routing your traffic through.

Also, I'm not sure if it filters stuff that can be used to help identify you such as user agent strings, cookies, or java applets and flash animations which may not use the proxy.

---

### Post by duds2008 on 2009-02-12
Thanks for this useful command. It seems to be running, which is brilliant. I never had to restart the daemon after reboot! Am not an expert on a lot of the things you spoke of in your reply but am steadily learning. Thank you!

---

