---
title: "Installing flash (Firefox) &amp; Radeon driver"
date: 2008-10-20
forum: United Kingdom Team
---

### Post by Mark224 on 2008-10-20
Hi,

I have just downloaded and installed Ubuntu 8.04 LTS (Desktop) and it was an amazingly quick and easy process :-).

However I did have a couple of minor issues and I would be grateful if anyone could help.

1.  I installed Flash player for Firefox using the instructions on this site: [http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash").  Everything appeared to proceed fine.  I got the dialog saying "Sucessfully applied all changes".  However when I look at the installed plugins flash player is not listed.  When I visited a site that needs flash then it still shows the message saying flash is not installed.  I have restarted Firefox and even rebooted but still it does not work.  I tried to install flash again but, of course, it says it is already installed.

2.  I had problems installing the recommended ATI driver.  I tried installing it by enabling it in the restricted drivers GUI and I tried using the command line.  In both cases it proceeds as far as to try to download the actual driver file from the repository but I always get "404 file not found" error.  I haven't had any troubles downloading anything else.  This is not a show stopper for me since I successfully downloaded and installed the ATI binary driver, but I would rather have the open source version.

Thanks, Mark.

---

### Post by itix on 2008-10-21
The official means of installing Flash has gone trough a series of improvements lately. If you go to the adobe site and choose to download flashplayer for linux, yyou get the choice of dowloading a .deb for debian/ubuntu. Use that and you'll have flashplayer 10 which is fresh out of the oven and a bit more stable than 9 that is shipped through the repositories (in other words, firefox won't crash every 3 seconds =p).

---

### Post by Mark224 on 2008-10-25
I tried what you suggested but I still have exactly the same issue.
Synaptic says that "adobe-flashplugin" is installed (version 10) but I still get the same error messages on iplayer & youtube.

---

### Post by Mark224 on 2008-10-25
I finally got the "flashplugin-nonfree" one to work.  I had no success with the one from Adobe.

---

### Post by itix on 2008-10-28
That's wierd. At least it is woking correctly.

---

### Post by Mark224 on 2008-10-29
Thanks for the replies.  Now I can move on to kernel and DST problems ;-)

---

