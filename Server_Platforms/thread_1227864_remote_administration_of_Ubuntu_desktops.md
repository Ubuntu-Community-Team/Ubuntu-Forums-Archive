---
title: "remote administration of Ubuntu desktops"
date: 2009-07-31
forum: Server Platforms
---

### Post by ulrith on 2009-07-31
Hi all! :)

I would like to install updates on my Ubuntu desktops remotely logged into console connected by ssh. I can switch on (wake up by lan) desktops distantly, but I can't connect to them by ssh and even ping them. (After starting up they open gdm login window, not loggin in any user.)

Could anybody please explain this and may be you can advice some solution?...

---

### Post by wojox on 2009-07-31
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by randyklein99 on 2009-07-31
Have you installed ssh on both machines? I think there is a server and client version you need to install on them.

---

### Post by ulrith on 2009-07-31
Yes I've installed all necessary software on all machines. But it probably is not loaded when not logged in?... And how about pings?...

---

### Post by Macchi on 2009-07-31
The ssh packages are openssh-client and openssh-server. They work marvellously in Ubuntu.

You may also login remotely on your desktops through XDMCP with existing software on a standard Ubuntu installatin. Just allow remote login on System->Administration->Login Window->Remote(tab). From another machine on the same network choose the remote XDMCP login from the login screen.

---

### Post by ulrith on 2009-07-31
**wojox** & **Macchi**, what're you talking about? I can connect to my Ubuntu desktops by ssh when some users logged in them, but I can't even ping them if not. Are you understand what I mean?

---

### Post by Macchi on 2009-08-10
> **ulrith said:**
> I can connect to my Ubuntu desktops by ssh when some users logged in them, but I can't even ping them if not.
Ulrith, I believe that you should control if your network interfaces are configured correctly. Check the boxes for connecting automatically and make the specific network interfaces available for all users. With the network manager it is possible to set up a system that has the behaviour that you described on your last post. The network interfaces will only be active if someone with permission to use the network has logged in. 
Thanks for providing more information.
 


> **ulrith said:**
> **wojox** & **Macchi**, what're you talking about? ... Are you understand what I mean?
I simply hope that your words are not meant to be unfriendly.

---

### Post by cariboo on 2009-08-10
Depending on what version you are running the network interface on desktop editions does not start up until after login. I'm not at my desktop right now, but on my server networking is in /etc/rc0.d. the command looks like this:

```
@S35networking
```

Which starts networking before most other processes.

---

### Post by ulrith on 2009-08-14
> **Macchi said:**
> Check the boxes for connecting automatically and make the specific network interfaces available for all users.

Thank you very much, **Macchi** - it was exactly that: I have to make connection available for all users! Now I can remotely wake up the computer and log in to it for maintenance. Thank you again!

> **Macchi said:**
> I simply hope that your words are not meant to be unfriendly.

Truly you're right - I was disappointed by **wojox** a lot, who post useless link without even understanding my question. I think he just try to post as much "advices" as he can to obtain high rating. May be I'm wrong.

---

