---
title: "Logging in Without Username and Password"
date: 2008-05-06
forum: Server Platforms
---

### Post by azurepancake on 2008-05-06
We use a simple file server for our four computer, home office network. The file server is running Ubuntu Hardy and does its duties very well.

There is just one thing I am curious about. We don't have a monitor for this server and I normally just SSH or VNC into it when configuration needs to be done. There is a monitor used for another computer right next to it that I can use if I have to, but the thing is though, that if we need to restart it, I need to plug in the monitor to log in every time.

So my question is, is there a way to set it up that when I turn on the server, it logs in by its self and I don't have to manually type in the user name and password?

Any advice would be greatly appreciated!

Thanks

---

### Post by hodenkat on 2008-05-06
I'm pretty sure you can go to System/Administration/Login Window
and change it to allow for autologin.

---

### Post by OffAxis on 2008-05-06
do you really need to login at the terminal..?
It shouldn't keep you from logging in via ssh or vnc even if it's at the login screen...

---

### Post by azurepancake on 2008-05-06
Doh, your absolutely right hodenkat. Thanks a lot.

The reason why I want it to be automatic is because I might not always be around to login on the server via SSH. This is my mothers small business and I want it to be as easy as possible for her. 

Your advice is very useful though OffAxis. For some reason I had the idea that networking services only started when logged in. 

I'm learning as I go I suppose! 

Thanks again!

---

