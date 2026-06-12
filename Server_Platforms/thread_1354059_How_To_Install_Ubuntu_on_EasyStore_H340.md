---
title: "How To Install Ubuntu on EasyStore H340"
date: 2009-12-13
forum: Server Platforms
---

### Post by hammhamm on 2009-12-13
Hi,

i bought the Acer EasyStore H340 but i don't like Windows Home Server... 
Now i've searched a lot and found the thread:
[http://www.backports.ubuntuforums.org/showthread.php?t=1193348](http://www.backports.ubuntuforums.org/showthread.php?t=1193348)

Most people say Ubuntu works GREAT and is COOL and Best EVER ;).

But i don't know how to install Ubuntu on H340. I don't want do buy a cable or PCI Graphic card... 

So please, can somebody help me to ionstall Ubuntu? I've removed the OS HDD from H340 to install Ubuntu Server 9.10 but when i insert the HDD i can't connect anyhow to H340...

I need a step by step install guide please.. :(.

Thank You!!!

---

### Post by noelvh on 2009-12-13
Now I am not sure about Ubuntu as a server, but an easer way I would use is freenas. Freenas has a web interface, and can run from the hard drive, or a cd rom with a config file stored some ware. 

Now when I looked at the specs for this it states it has a video out, so all you would need is a cd rom drive.

Have a look at [free nas]("http://www.freenas.org/")
and this is a [good site]("http://dailycupoftech.com/howto-install-freenas/"). 

I hope this helps..

Noel

---

### Post by hammhamm on 2009-12-13
First at all thanks for the replie. The fact is that H340 has a onbord graphic but i need a graphic card or adapter whit port to use it, and i don't wnat to buy anything.

So how can i install Ubuntu or FreeNas without any graphic,keaboard, mouse? :(

I hoped i can pre install it on HDD with my personal computer, put HDD into H340 and make more install over SSH or something, but i donÄt know how... It sounds like its easy in the thread i posted up...

---

### Post by hammhamm on 2009-12-14
No more ideas, how to install Ubuntu on H340? :(

---

### Post by BkkBonanza on 2009-12-14
I've never used or seen an H340 so I can only give you some generic info.
You can install Ubuntu server onto the hard drive in another system.
You want a fairly generic i386 install, no 64 bit or AMD stuff.
Boot first on your other system and check conectivity on your LAN.
You should be able to connect to SSH on port 22 on whatever IP address it has.
Once that is good move it to the H340 and boot again.
You should be able to connect to port 22 and use the command line to finish any things you want after that without needing a monitor or cd-rom.
If you haven't used linux much then you have a fairly steep learning curve ahead but once you're there you'll enjoy it.

---

### Post by druhboruch on 2009-12-14
[http://www.backports.ubuntuforums.org/showpost.php?p=7599333&postcount=8](http://www.backports.ubuntuforums.org/showpost.php?p=7599333&postcount=8)

Works great with 9.10

---

### Post by Botsvein on 2009-12-26
Confirm, that method by **druhboruch** works fine.

There're several things, I should add:
1. Enable debug modeby setting jumper according to service manual.
2. If server doesn't boot from flash, try taking out all HD's and then boot server - insert HDs after first successful boot from flash drive.
3. You'll need to power up h340 under Windows at least once to "enable" network card - I've lost several hours finding this out. If you try boot linux strait out of the box, NIC will be detected by kernel, but will never send or receive any packages (no lights blinking on the back of the box). Booting windows solves the problem.
4. Clean /etc/udev/rules.d/70-persistent-net.rules should be done just before inserting flash to the cube - it's automatically recreated during each boot.

That's all. Now I've set up ssh and will continue to add services to the box...

And thanks **druhboruch** once again - everything works mainly according to his advice :)

---

