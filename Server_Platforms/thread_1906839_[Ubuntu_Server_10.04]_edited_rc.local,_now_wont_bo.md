---
title: "[Ubuntu Server 10.04] edited rc.local, now wont boot"
date: 2012-01-10
forum: Server Platforms
---

### Post by jubei-za on 2012-01-10
Hi

This is my first post in a forum, also I am very new to linux/ubuntu and servers in general - so please go easy on me!

Firstly I'm using Ubuntu Server 10.04 LTS. So I used [this guide]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") to mount my windows shares permanently. I could access everything just fine after running 'sudo mount -a'. Whenever I reboot the windows share mounts are lost, even though I specified them correctly in /etc/fstab. So every time I reboot I had to run 'sudo mount -a' to get the shares to mount. So after some googling I found out about /etc/rc.local and I put in there the command 'sudo mount -a' -- I think this is what runs at boot anyway but thought I could "kludge" it into working without me manually typing it in.

Now boot hangs. It gets up to '* Starting web server apache2' and the the next line is 'Password:' and it wont go any further, and does not respond to keyboard (except ctrl+alt+del). I think its gotten to rc.local and wants the password to complete the 'sudo mount -a' command, but I cant type it in or get passed it. How can I fix this? -- If totally messed up I can reinstall because it is just a box I'm learning on and nothing important that I cant reinstall. I've searched a lot and not found anything...help? 

Personally I think only way to fix would be to boot into another operating system and fix rc.local somehow -- any other ideas?

Its been like this for a few days while I tried to fix it, but if I cant find a way will just format/reinstall Ubuntu 10.04 from CD.

Thanks in Advance.

---

### Post by HugoSerrano on 2012-01-10
Hello!
That "password:" it's because of the "sudo" that you put in rc.local.

Try to write your root password and press enter.

If not, you can boot with a ubuntu live cd and edit the > /etc/rc.local file, removing the "sudo". That should fix it.

Anyway, it should mount things on you fstab without that>  mount -a in rc.local.

---

### Post by SeijiSensei on 2012-01-10
All the startup scripts including rc.local run with root privileges.  You don't need "sudo" in front of the commands in that file.

---

### Post by jubei-za on 2012-01-12
Hi

Thank you for the suggestions for LiveCD. I tried a few LiveCD's 10.04 and 10.10 but the screen kept switching off after it had done some loading. Its an old machine and I still have no clue why the LiveCD did not boot into ubuntu. 

I decided to just format as I didn't want to spend another week trying to figure out another problem.

I should leave this marked as unsolved until someone reports success with the liveCD method?

Any way - thanks for the ideas - will get some nice practice reinstalling apache/et al again :)

Jubei

---

