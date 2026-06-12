---
title: "no servers work unless logged in"
date: 2011-02-05
forum: Server Platforms
---

### Post by phazei on 2011-02-05
I have the system setup and working, but I want to put it in a corner and forget about it.  Problem is, nothing starts running unless I'm logged in.  And if I log out, everything stops again.

It's running a LAMP server and has VNC and SSH servers as well.  I want all of that to start without having to log in.  That way I can remote reboot without worries and connect and login with either VNC or SSH.
Everything seems to have an entry in /etc/init.d

Is the way it's acting normal behavior?  It's a fresh install, then I installed everything I needed from the repos.

I do not want it to auto login on boot without asking for a password.

How can I set this up?  Thanks.

---

### Post by kevinthecomputerguy on 2011-02-05
Sounds like you setup Ubuntu desktop instead of Ubuntu server. A desktop may behave as your mentioned, a server should not.
 
You mentioned lamp, did you maybe go GUI on your server, instead of leaving it CLI ?

---

### Post by phazei on 2011-02-05
Well, I installed Ubuntu Desktop, though I want to have it run primarily as a server.  It's just a dev machine, so I wanted the GUI.  I may turn it into a media server later.

I posted in this forum because I'm primarily using it for LAMP.

---

### Post by phazei on 2011-02-05
What if I installed ubuntu-server first, then added xfce, would it then boot cli and let me run xfce and VNC when I felt like it?

Could I launch xfce from SSH, then connect once loaded with VNC?

---

### Post by kevinthecomputerguy on 2011-02-05
Just install server, then webmin
 
here is a how to     [http://woodel.com](http://woodel.com)

---

### Post by CharlesA on 2011-02-05
Even on a desktop install it should "just work"

Are you connecting via wireless or something?

---

### Post by phazei on 2011-02-06
Yes, it is wireless. :D  Great catch.

Can I get that to initialize before login?

EDIT:
Now that I know what I needed to google, [I got it]("http://ubuntuforums.org/showthread.php?t=1401075#4").

Now I just need to get the VNC server working before login.

---

### Post by James78 on 2011-02-06
> **phazei said:**
> Yes, it is wireless. :D  Great catch.

Can I get that to initialize before login?

EDIT:
Now that I know what I needed to google, [I got it]("http://ubuntuforums.org/showthread.php?t=1401075#4").

Now I just need to get the VNC server working before login.
[http://ubuntuforums.org/showpost.php?p=10388675&postcount=11](http://ubuntuforums.org/showpost.php?p=10388675&postcount=11) :p
Soo.. After doing that, you would just do something like adding the very last 2 commands to /etc/rc.local, then doing a "sudo chmod +x /etc/rc.local"

---

