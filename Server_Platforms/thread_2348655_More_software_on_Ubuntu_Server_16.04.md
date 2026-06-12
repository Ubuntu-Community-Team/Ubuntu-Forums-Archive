---
title: "More software on Ubuntu Server 16.04"
date: 2017-01-05
forum: Server Platforms
---

### Post by sethanath2 on 2017-01-05
Hi, 

I have just performed a fresh installation of Ubuntu Server 16.04 on my PC. I did the following steps, afterward.

1. sudo apt install ubuntu-drivers-common
2. sudo ubuntu-drivers autoinstall

After, these two steps, I notice my server is running a lot faster.

3. sudo apt install --no-install-recommends ubuntu-desktop
4. sudo apt install firefox
5. sudo apt install vlc
6. sudo apt install gnome-terminal
7. sudo apt install gksu
8. sudo apt install leafpad
9. sudo apt install ubuntu-restricted-extras

10. sudo apt install libdvd-pkg
11. sudo dpkg-reconfigure libdvd-pkg

12. sudo apt install xfburn
13. sudo ufw enable

My questions to you are below.

1. Right now, I only see Firefox from my Unity desktop. Please help me see many of the software above, especially gnome-terminal.
2. Please teach me how to kill Unity Desktop as well as restart it. This should make the server faster correct?

I am the first time using the server. I hope you can suggest many things as well.

Thank you.

---

### Post by ian-weisser on 2017-01-06
Linux servers are designed to run headless. No Unity, no firefox, no leafpad, no ubuntu-restricted-extras, no xfburn. Just a console and a shell prompt.

If you wish to learn how to run a server, one easy way to install a Virtual Machine on your Ubuntu Desktop (because that's what you now have), and install a shell-only Ubuntu Sever onto it. Many first-timers quickly destroy their first server -there is a learning curve- so having a virtual server that you can protect from malicious probes and that you can simply throw away (or revert to the last snapshot) is a great boon.

Advice: Do not use ufw on a server. It will work, but it will be just as complicated as learning iptables anyway. So skip ufw and go directly to iptables.

Advice: In a server, don't start with applications. Start with security. Learn how to lock down the server (accounts, iptables, ssh server) before doing anything else. Learn the habit of checking your logs and ports and htop regularly.

Advice: Plan what you want to serve. Add a new service slowly, carefully, safely. Use the shell to do it. Take notes on how you configured it.

And have fun. Your first server is a good time!

---

### Post by sethanath2 on 2017-01-06
I see. Thank you so much. What you mentioned matchs with what I found below as well.

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI) It suggests the use of [Openbox]("https://help.ubuntu.com/community/Openbox") and [Fluxbox]("https://help.ubuntu.com/community/Fluxbox").

I will remove my Unity real soon.

At this point, I have Openbox running with my Ubuntu Server 16.04.
```
sudo apt install openbox obconf
```

I also installed Microsoft Fonts and Firefox browser.
```
sudo apt install ttf-mscorefonts-installer
sudo apt install Firefox.
```

I removed Unity and unnecessary software with the commands below.
```
sudo apt remove ubuntu-desktop
sudo apt remove gksu
sudo apt remove leafpad
sudo apt remove libdvd-pkg
sudo apt remove vlc
sudo apt remove ubuntu-restricted-extras
sudo apt remove gnome-terminal
sudo apt remove xfburn
```

I found Openbox is super useful. What other software I should use with the server? I hope someone can provide more information.

Thanks.

---

### Post by TheFu on 2017-01-06
My first 5 minutes on a server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
Lots of other folks here have their own methods too.  Being consistent is important.

---

### Post by sethanath2 on 2017-01-07
> **TheFu said:**
> My first 5 minutes on a server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
Lots of other folks here have their own methods too.  Being consistent is important.

Thank you.

---

### Post by mastablasta on 2017-01-09
if you really need a GUI on server install a webgui (Ajenti, OpenMedia Vault...)

---

