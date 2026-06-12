---
title: "VNC and all users desktop??"
date: 2010-08-19
forum: Server Platforms
---

### Post by xendistar on 2010-08-19
A couple of questions if I may, my server is going to run headless and I would like vncserver to start upon reboot, is this possible and where do I put the command? (will it run before I login into XFCE??)

Secondly, I want to place a folder on the desktop of all the users (same as the windows all users desktop), is there an equivilent in ubuntu??

I am running 10.04LTS with the xubuntu desktop

Tim

---

### Post by arrrghhh on 2010-08-19
Not sure if the server section of the forum is right for this post considering...

But if you have a startup script and put it in init.d with update-rc.d, then yes vnc will start before you login.

As far as placing a folder on the desktop for all users... not really.  You can use symlinks or a bind mount to simulate it tho.

---

### Post by Lars Noodén on 2010-08-23
Look at the manuals for system v init scripts, as @arrrghhh suggested.  You'll need a script to start the vnc server to use with update-rc.d
Same if you use upstart.  

Don't leave VNC open to the outside of the machine, it is not so secure.  Use an SSH tunnel to get to it.

---

