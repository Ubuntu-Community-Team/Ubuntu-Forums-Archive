---
title: "Copy filesystem from USB on boot - without any prompt"
date: 2015-02-06
forum: Server Platforms
---

### Post by Nikola.srb on 2015-02-06
Hello, I need help packing my Ubuntu 14.04 server on an USB flash drive in such way that, when I insert it into machine and auto boot from USB, filesystem from USB gets copied onto that machine, thus on next reboot (without USB) machine boots newly flashed distro.

Now, in more detail: 
- I have ~3000 machines that need to move from Fedora Core 3 to Ubuntu server (CLI only).
- Those machines need to be re-flashed (reverted to factory defaults, sort of speaking) every now and then, by someone who does not know much about IT (insert USB, reboot, wait, reboot again - that's pretty much it).


Is there any guide on how to do it, or at least any ideas that could help me out?

Cheers,
Nikola

---

### Post by sudodus on 2015-02-06
Are the computers similar enough, so that the same system can be cloned into all of them? Or would you need some kind of installation, that is adjusted individually for each of them (automatically)?

What about hostname, UUIDs? Can a portable network setting be used (for ethernet)?

-o-

Is there a budget for commercial assistance from Canonical (the company behind Ubuntu)?

[http://www.canonical.com/services](http://www.canonical.com/services)

---

### Post by Nikola.srb on 2015-02-06
There are 2 types of machines, but for now we're focusing on one type that holds majority.

Machines have no ethernet, they have only PPP connection over GPRS modem, so no need for uniqueness, as far as I can figure out.

Unfortunately, serious cuts in fundings are the reason we had to halt cooperation with company that was paid for tech support on those machines...  Few of my colegues and myself are now working on a way to continue production and maybe improve it a bit with bit more effort we're putting in.  Good thing is that director of IT department is die-hard supporter of Ubuntu. :)

---

### Post by sudodus on 2015-02-06
In that case you might be able to make a system that works and make a compressed image, and then you can make cloned copies from (copies of) that compressed image.

***Clonezilla*** is one tool to use. I think the easiest way is to have two USB pendrives, one with Clonezilla, and one with the compressed image. It is also possible to merge it to one single USB pendrive, that boots into Clonezilla and expands from an image on the same pendrive. It is possible to create a batch file (basically one command line plus whatever help commands you would like to supply) that can do the job.

Another method could be to make a compressed image with ***dd*** (clone with dd and pipe it via ***gzip*** (faster) or ***xz*** (better compression) to a file. That process might be a little tricky, but I do it manually. If free space is zeroized, the compressed image will be smaller, and the expansion will be faster. The expansion into the target computers can be made using ***mkusb*** or ***mkusb-nox***, which is rather simple and safe. It is also possible to create a custom shell-script, that can do the expansion. This method is very simple and straight-forward, but slower than Clonezilla and the One Button Installer, if the created partitions are big, because free space is also written (zeroes are expanded and written faster but not as fast as when it is skipped).

[http://clonezilla.org/](http://clonezilla.org/)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If you have hard disk drives of different sizes, you might want to use a system, that can take advantage of that automatically (which is not possible with cloning).

The ***One Button Installer*** might be an alternative. You make a compressed tarball of a system that works. Then it is very fast and easy to expand the system into the target computer, but it is limited to a system with one root partition and one swap partition. The tarball can reside in the same pendrive as the One Button Installer, so you need only one pendrive.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by TheFu on 2015-02-08
Take a look at pxe and **cobbler**.  Probably also want to add in **ansible** for ongoing maintenance.
These tools definitely work and once the MAC is in your DB, that will be the last time you probably have to physically touch the machine.

---

