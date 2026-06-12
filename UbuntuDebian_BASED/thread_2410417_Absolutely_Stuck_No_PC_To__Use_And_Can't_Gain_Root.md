---
title: "Absolutely Stuck No PC To  Use And Can't Gain Root To Live CD"
date: 2019-01-15
forum: Ubuntu/Debian BASED
---

### Post by mod1t on 2019-01-15
Hi new here just signed up, can someone please help me I'm clueless with linux really a total noobie, any way I've been pulling my hair out trying to login to Robolinux, this is say the 6th reboot where it's locked me out, I cannot use my password even if I reset it it's rejected, sick of re-installing everything now, can someone tell me how I can gain superuser priveledges in the live cd to try fsck as I cannot login to that either, if I type su it says password, I tried it empty with passwords of: root/password & Password with robolinux & Robolinux with robo and also with passwd I cannot use my computer right now because it won't boot any windows disc on this fm2 asrock board never buy one.

It's really strange though after rebooting with these Robolinux installs that it keeps on throwing incorrect password every time after a while of successfully logging into the os repeatedly, it only once logged back into a second account which is set with an an openbox window to use only steam as I was having tearing issues in steam and even after that I still am lol every single thing is going wrong for me and I just don't know the password for the Robolinux live cd which some places say leave it blank which is wrong as it doesn't work as a blank password tried it.

I don't know what to do at this point I'm debating pulling the plug and going real deal ubuntu?

Robo won't respond to the tweets I send and there's absolutely next to nobody anywhere commenting o such an issue or even posting anything I am aware of.

---

### Post by TheFu on 2019-01-15
Never heard of robolinux.  Why not just use an Ubuntu variant?  Reading the robolinux main page seems to be a bunch of hype over standard Linux capabilities that any Ubuntu version (or any mainstream Linux distro) can do.

If you were using an Ubuntu Live boot from flash, we could tell you exactly what to do.  The root account isn't enabled on Ubuntu-based distros. On Ubuntu, we use sudo + the command to temporarily elevate permissions for 1 command.

As for password entry issues at login, this can be caused by using different keyboard settings that don't match the selected language.  This is allowed because some experts want complete control, but for someone new, mixing those settings is a huge problem.  If you have a US keyboard, be certain to pick en-US as the language and keyboard.

So ... first try **sudo fsck /dev/sda** and see if that helps.  I doubt it will, but that was the command you asked about.

---

### Post by mod1t on 2019-01-16
Yeah tried it thanks though. It's a ubuntu distro based on the 18.04 release with stealth vm for windows preloaded to use a prefab virtual machine basically. But the beauty is all the included installers making it easy to load the programs rather than spending ages writing apt-get jumbo in.

---

