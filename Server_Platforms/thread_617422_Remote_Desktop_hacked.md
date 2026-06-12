---
title: "Remote Desktop hacked"
date: 2007-11-19
forum: Server Platforms
---

### Post by brown_ghost on 2007-11-19
I have a Dell Optiplex270 with Feisty installed at work, I use this computer to get on the internet and sometimes I check my bank account, I also have the remote desktop to log into from other computers. Well on friday I turned on the computer and saw the new updates window pop up like it always does and I clicked on it to do updates, well after about a min into the downloads I saw the remote desktop pop up and it said that it was connected I when I clicked on it I was able to see a partial IP it disconnected, at that time I did not have the Firestarter running and have never really paid attention because I have a netgear FVX538 router. My question is does the remote desktop have a log that I can check to get the IP of the person who logged in? Since then I have disable remote desktop and double checked my settings on my router.

---

### Post by ukripper on 2007-11-19
Should have been using SSH at first place. [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by steveneddy on 2007-11-19
Remote desktop should only be used when you are at the machine showing somebody something that you couldn't any other way.

Otherwise, use SSH to log in securely to your machine remotely.

---

### Post by netlogic on 2007-11-19
Like others have said, VNC is very insecure. Never use it without tunneling through SSH. Here is  a link how to do it easily from a Windows box. VNC is more
insecure than RDP. However, it can be very useful with SSH.

[http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/](http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/)

---

### Post by brown_ghost on 2007-11-19
Thanks a lot fellas, I'm pretty new and have not really gotten into the security of ubuntu, I really love the fact that I think it's faster to download/upload files than my xp, as a matter a fact I have both XPpro and Gusty @ my home computer and I must say I hardly use XP since I now use the wine to use this password application that it only works under windows. I currently have three offices connected via VPN and would like to  eventually start to install/replace my xp pcs with ubunty for the sales reps since they just log on to view emails and surf web. Any ways to get back to my original problem I will install SSH and read more on security. THNX

---

### Post by btdown on 2007-11-19
I recommend NX ([http://nomachine.org](http://nomachine.org)) for remote login. I use it every day and its fast as hell. I keep the client on a thumb drive and can access it from everywhere securely. There are instructions on these boards for installing it if you're interested.

BT

---

