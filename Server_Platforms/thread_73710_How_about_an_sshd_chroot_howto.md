---
title: "How about an sshd chroot howto?"
date: 2005-10-09
forum: Server Platforms
---

### Post by invalid on 2005-10-09
I searched briefly, and could find no real information to what I would like help with..

I wan't users who I allow ssh (with openssh) access, to be limited to their home directories. I have seen some information on chroot, and jail, but do not know a whole lot about these and they seem quite complicated to say the least.

Surely there has to be a somewhat simple solution, or a step by step howto would be a great addition.

Thanks
Cb

---

### Post by Glut on 2005-10-10
Hi, 
I am personally of the opinion that chrooting an ssh'd environment can be of limited value. I think that you could provide better quality service through assigning permissions more effectively across the operating system.

Having said that, it's your machine and you can deal with the complaints. There is a quick and dirty solution, where you compile your own openssh daemon and it sorts out most of the problems for you:

[http://chrootssh.sourceforge.net](http://chrootssh.sourceforge.net)
Here's a howto for it:
[http://www.brandonhutchinson.com/chroot_ssh.html](http://www.brandonhutchinson.com/chroot_ssh.html)

---

### Post by howser on 2005-12-20
I'm in favor of this too -- perhaps I misread the howto that was posted, can I set this up via SSH?  The server that I need to secure is in a different state....so I need to be careful.  Any help from Ubuntu users that have done this would be great!

---

### Post by Glut on 2005-12-22
To set it up via ssh you would need to have your sshd listening on another port. edit the /etc/ssh/sshd_config file, point it at another port, then setup the new server to listen on port 22. Of course, if you screw it up you will need another form of access other than ssh to fix it...

Alternatively you could use the standard sshd on port 22 and your chrooted version on another port (even a high port if you didn't want to run it as root.) This method is probably safer, and once setup if necessary swap the ports around.

---

