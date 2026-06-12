---
title: "Help a novice secure his VNC connection ?"
date: 2006-09-12
forum: Server Platforms
---

### Post by Copps on 2006-09-12
Hi all,

I need to be able to access my Ubuntu desktop from a remote Windows machine. 

I have added vnc4server and xinetd via aptitude, set config, and can start an ubuntu session locally via vncviewer:localhost:1

I can also start a session using tightvnc.exe on a Windows machine on my local network. What I've read about accessing sessions through VNC remotely doesn't fill me with much confidence! From what I understand of SSH tunnelling, I could connect remotely to my Ubuntu machine via SSH and begin the desktop session by running the same command as above, "vncviewer:localhost:1"

This is where my understanding may be drifting off. Is this SSH tunnelling? When I try to do this, I get "Error! Cannot open display!"

Here are the things I can't figure.

Do I understand what SSH tunnelling really is?

How can I access an Ubuntu desktop session remotely AND securely using SSH tunnelling?

Do I need to port forward SSH traffic to my Ubuntu machine, which is sat behind a router?

How can I change the SSH connection port to something else to help prevent unauthorised access?

Thanks for any help anyone can offer!

---

### Post by Copps on 2006-09-13
Hm, OK I've made *some* progress here.

I have switched the access port for SSH in sshd_config, and set up port forwarding on my router to the new SSH port.

I've set up a SSH tunnel using the notes at http:[www.brainonfire.net/2006/08/21/vnc-over-ssh/](www.brainonfire.net/2006/08/21/vnc-over-ssh/).

Now here's the thing. I can connect to SSH on my Ubuntu machine via Windows Putty if I use the 192.168.* IP address, and the port number I specified. If I try to connect using the external fixed IP that my ISP has given me, from the same Windows machine, I get "Connection refused" - [http://www.tartarus.org/~simon/puttydoc/Chapter10.html#errors-connrefused](http://www.tartarus.org/~simon/puttydoc/Chapter10.html#errors-connrefused)

I'm far from being an expert as you can probably tell, but this suggests that the port forwarding I have set up on my router is OK, and Ubuntu itself is refusing the SSH connection! Yet it permits the SSH connection when I connect using Ubuntu's internal IP address.

Further, I've double-checked the port is open using [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and everything checks out, and confirmed my external IP address at [http://www.whatismyip.com](http://www.whatismyip.com)

Anyone got an idea why the SSH connection fails to work only when I try to connect on my external IP?

---

### Post by Copps on 2006-09-13
I've fixed this, please disregard/close etc.

---

### Post by DarkKoopa on 2006-09-24
I found your post as was scratching my head with getting VNC to work over SSH

Until I found this post that is

[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)

Works a treat, can access it from anywhere now and I know it's secure.  Yippee!

Took all of 48.98 seconds to get it working too.  =D>

---

