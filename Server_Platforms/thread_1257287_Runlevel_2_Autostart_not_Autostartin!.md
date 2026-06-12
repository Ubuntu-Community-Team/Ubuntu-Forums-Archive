---
title: "Runlevel 2 Autostart not Autostartin!"
date: 2009-09-03
forum: Server Platforms
---

### Post by snowman4839 on 2009-09-03
I set up a virtual machine of ubuntu x64 server in virtualbox with 256mB of RAM and I've just been messing around in it among other things... The first thing I did was set up an HTTP server (Apache) and after awhile of messing around with the config files, I got that up and running and it works fine and auto-starts with the computer because it is in /etc/init.d and it is in the /etc/rc2.d file with all of the symbolic links. Now I tried setting up solid-pop3d POP3 server which didn't go as well... I don't want the exim4 SMTP server to autostart or be running which is part of solid-pop3d's dependencies so I renamed it K20exim4 instead of S20exim and now that doesn't autostart which is what I want. BUT!! for the life of me I cannot get solid-pop3d to start with the boot process. It didn't autostart when I first installed it, it didn't when I disabled exim4 autostart, and it didn't work when I tried renaming it from S20solid-pop3d to S91solid-pop3d (I just tried everything I could think of). It will start just fine after I boot and login and go to /etc/init.d and "sudo solid-pop3d start" (it doesn't work with "solid-pop3d start" because it needs root) but why doesn't it autostart?!?!? I checked the symbolic link and its pointing to /etc/init.d/S20solid-pop3d so that is fine. This is really bugging me and I've tried everything a moderately knowledgeable Linux user can think of! Please help :-)

---

### Post by snowman4839 on 2009-09-04
nobody has any ideas?!?!?!

---

### Post by snowman4839 on 2009-09-05
SOLVED!!! HURRAY!!!

I got it guys. The /etc/init.d/solid-pop3d file that came with the package was not written correctly so init would not start the solid-pop3d daemon correctly. I just copied /etc/init.d/skeleton (the barebones init file which you can edit a few things to make it work for any file that needs to be init'd (started) at boot) as the new /etc/init.d/solid-pop3d file and edited it so that the DESC="description of solid-pop3d" and NAME="solid-pop3d" and it just used the NAME variable in the rest of the program so that was all I really needed to do. I then set the permissions of the new solid-pop3d file to 755 so that it could be executed by using "sudo chmod solid-pop3d 755" I'm still having a little trouble with getting it to start, stop, restart, etc. but I'll work on that tomorrow. I hope this will help someone along the way. Stay Frosty...

---

