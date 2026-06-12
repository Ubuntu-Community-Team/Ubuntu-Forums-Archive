---
title: "Ubuntu Server 10.04 Serious issues"
date: 2010-10-25
forum: Server Platforms
---

### Post by hantechbl on 2010-10-25
I'm not sure if I have a hardware failure, but when I try to install ubuntu server 32-bit 10.04 cd image it says: 
```
Error: Termainal not found
Error: Something Else but I can't remember

```
Sometimes it will come up with a third error too, but it still boots, the boot takes forever and when It does load up the login screen it will automatically time-out because it takes so long, the "server" it is on is a 170mb 1ghz 2gb hdd HP pavilion Xt953.  I can't access recovery mode because grub displays errors and doesn't give me a menu.
It only works the 1st bootup after the install and that's it. I've already tried reinstalling and still, exact same problem, btw I run Minecraft, Apache, Postgre SQL, php, Tomcat.

---

### Post by arrrghhh on 2010-10-25
Hrm... that seems pretty paltry specs, but no reason Ubuntu Server shouldn't be able to run on it.

Can we get exact errors?  You seem unsure of what the problem actually is.  Do you have anything else installed on this machine?  Have you run a memtest?  Have you checked the integrity of the disc?

---

### Post by SlackwareRobert on 2010-10-29
I would suspect the disk drive first.  That it 'install' from the cd, but dies when you boot
the installation gives it the edge over ram which should fail on cd image as often.
Just had a drive go out. it is the retrying till it reads the block that makes it so slow.
I'm running on an old xenon 1ghz board without a problem once I replaced the drive.
I would say get a sata drive with a controller if it doesn't have one.  For a server box the 
multiple commands sata accepts over ide's 1.5 is more efficient. Plus way bigger drive cache never hurts anything.
Now if they would only have a 32bit server kernel so the correct logon help page is shown, so I don't have to lie to the script so it shows correctly. :)
Must be getting old when I am to lazy to just build my own kernel.

---

### Post by E-call on 2010-10-29
depending on what you are doing I would suspect that you dont have enough horsepower under the hood. 170 mb of ram is less than the base recommended amount of 256 and 2gigs of hard drive space wont give you any extra room for things such as you swap drive.
 
based on your specs alone I'd think you would have some issues running the system.
 
have you tried disabling your cd-rom drive after install?
 
I would recomend trying to get a little bit more in the way of ram and hd space if you can afford that option.
 
 
 
also when you did your install did you manually set your partitions or did you let the installer do it for you automatically?

---

### Post by hantechbl on 2010-10-29
Partitions were automatically set, I seem to be running fine.... for now I just haven't restarted i would try a memtest but I doubt theres a way to actually run it in the os. and i think it has plenty of power because when it comes up in webmin it is only using about 90mb ram and 20mb swap with apache, minecraft (4 lvls) and mysql, php.  I'm having problems with php also now, html shows up but with php I got the error 500 but now that I installed php5 I just get blank pages.
Edit: I think it could be that the HDD was from 1997.......
Edit2: I looked at the code in the client browser and it's empty but when viewed directly on the server it shows any ideas?

---

