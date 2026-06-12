---
title: "Ultra 5 and Ubuntu Install nightmare"
date: 2006-07-20
forum: Sun Sparc Users
---

### Post by zc923 on 2006-07-20
My father got the ultra 5 when he was doing consulting from home. He since then switched carrers and the ultra 5 just sat there collecting dust.

This past week, I decided, hey, why not use it has a file and web server? So the journey began.

When I first booted the system, the mac address of the ethernet adapter came back f'ed out, Quite litteraly (ff:ff:ff:ff:ff:ff...). I thought nothing of it, and put in the install disk. Nothing big in the install.

Once installed, I tried to to update the system. It was then I realised that the system would not connect to the internet. I started researching this as an Ubuntu Problem. I tried everything from defining the device with the correct driver, to disabling ipv6. Nothing worked. Then I thought, this could be a sun problem.

My second guess was correct. Apperantly, while the system was lying dormant, the settings stored in the NVRAM were corrupted or just plain missing. This corruption also led to the IDPROM invaild error message.
(more info here: [http://www.squirrel.com/sun-nvram-hostid.faq.html](http://www.squirrel.com/sun-nvram-hostid.faq.html))

I was lucky enough that I did not need to repace the chip. Following this: [http://www.squirrel.com/squirrel/sun-nvram-hostid.faq.html#QUICK](http://www.squirrel.com/squirrel/sun-nvram-hostid.faq.html#QUICK) did the trick for me.

However, try as I might, ubuntu refused to connect to the internet. At one point, it disabled the network card. I reinstalled, this time with the working ethernet connection.

Again, the installation was uneventfull. Afterwards, when I tried aptitude or apt-get, the connection would time out. I looked this up here, on the ubuntu forums, and was not able to get a clear answer. I knew the ethernet card was working; when I pinged google.com, it worked.

I got around this problem by putting the server in the DMZ. The updates ran. Afterwards, I removed it from the DMZ, and everything still worked. Apache2, php5, mysql, and samba are all working now. Just to make things eaiser, I also isntalled ubuntu-desktop.

Hope my troubled times help out others.

---

### Post by CobyR on 2006-08-07
Question for you?  I have an Ultra 5, that I have been running Debian Linux with a 2.4.xx Kernel.  I decided to upgrade to ubuntu 6.06.

Install goes great, no problems with networking.  I then do the sudo apt-get install ubuntu-desktop, that goes well.

For configurations I specify the ati driver, that is what I have used with Debian in the passed, and after reboot, I get the graphic Ubuntu start up screen, then nothing, screen goes blank.

I can't CTRL-ALT-F1 to a console, I can't CTRL-ALT-F11 or Backspace (I forget which) to kill the x-windows server.

What video driver should I be using for a desktop setup?

Thanks,

---

### Post by allnameswereout on 2006-08-08
Remember that you could always stick in a different PCI NIC instead of using the onboard one. I've been using 3Com 905b/c and Intel eepro100 with success.

As for the video card issue please use the search it has been discussed in other threads on this board.

---

### Post by zc923 on 2006-08-10
I'd be carefull swapping in other hardware in the Sun. Even though the Ultra 5 has PCI Slots, the device has to be SUN compatible.

As for the video driver issue, My ultra 5 has a ATI "3D Rage II + DVD" installed on the mobo.

I had a similar problem when I installed debian on the ultra 5 earlier. As soon as the graphics stage would come, the system was completly unresponsive.

When I installed Ubuntu onto the system for the 2nd time, selecting the proper ati driver worked, and I haven't had any trouble since.

As for an update on the server, its been hosting my websites like a champ.

---

### Post by allnameswereout on 2006-08-14
If the driver is listed at /lib/modules/`uname -r`/kernel/drivers it should work. Which is the case with the 2 PCI NICs I mentioned.

---

