---
title: "howto: Belkin F7D1101 with RTL8192SU from staging"
date: 2010-07-02
forum: Tutorials
---

### Post by fdm on 2010-07-02
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

This method does not work on any recent kernels(11.4+) as RTL8192SU was dropped in favor of r8712u. This new driver is even more stable and works out-of-the-box considering you have the linux-firmware package installed. Debian users have to copy the firmware manually(copy the rtlwifi folder from the ubuntu package to /lib/firmware).

Also, link to firmware has been updated for you <= 10.10 users out there, as posted and tested in this thread.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I recently purchased a Belkin F7D1101 Basic Wireless USB Adapter just to find it preforms poorly with ndiswrapper and Ubuntu does not support it out-of-the-box. Luckily, it is possible to get this chipset running natively.

1.) First I had to add the device to r8192s_usb(both files are likely empty):

Use this command in the terminal to open the first file:
> sudo gedit /etc/udev/rules.d/network_drivers.rules
and add this line:
> ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb"

Save it then run this command to open the second file:
> sudo gedit /etc/modprobe.d/network_drivers.conf
and add this line:
> install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 945a" > /sys/bus/usb/drivers/rtl819xU/new_id


2.) Then I obtained the firmware from here:
> "http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz"
and copied it to /lib/firmware/RTL8192SU/ with these commands:

> wget "http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz"
gunzip rtl8192sfw.bin.gz 
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU

Afterwards, I restarted and all worked well. Perhaps others with this device will be able to get it running well too.

To expand on this process further, r8192s_usb is the kernel module("device driver") for devices with the RTL8192SU chipset. Since the module does not contain the device id for the wireless card, we use the trick demonstrated above to add it to the module without having to recompile it. This works on most distros newer than the stable branch of debian. On some like Suse, you have to install the staging package first(kmod-staging). I also had to add the firmware, dmesg is good for debugging that part. This same process can be used with other devices as long as you can find a module for the chipset and change the info in the lines accordingly.

Alternatives:
compile closed source Realtek 8192SU driver - preforms like windows xp; good signal, not very stable
use ndiswrapper with the windows driver - poor signal, not very stable

---

### Post by buntu504 on 2010-08-01
I just finish following the directions in the howto and everything seems to be working.  The device now connects to my home WPA wireless network and signal strength is good.  

BIG THANK YOU!  

xubuntu 10.04
belkin f7d1101

---

### Post by Linux_Youth******* on 2010-08-06
I have successfully gotten this same adapter to work on Mepis 8.5 with these instructions. Thank you! :)

---

### Post by bch36 on 2010-08-11
THANK YOU!

Got the **Belkin F7D1101** working on **Ubuntu 10.04** by following your steps, after trying a million other things failed, including using ndiswrapper.

Edit: WPA works fine as well.

---

### Post by FlyinRedneck on 2010-08-17
Okay, I followed everything, but I am still unable to connect to my router. I can see the list now, but I cannot connect to my router with a WEP key (shared), nor can I connect to an open network. Any Ideas?

Ubuntu 10.04

---

### Post by ttugeorocker on 2010-08-18
You say to copy to and create directory /lib/firmware/RTL8192SU 

I was able to create the /RTL8192SU directory in my home directory, but I'm not able to move it to /lib/firmware.  I keep getting "Error moving file: Permission denied".  Thanks for any help.  I've done fine, I think, up until this point.  I installed 10.04 LTS last night and it's my first experience with Linux.

---

### Post by ttugeorocker on 2010-08-18
Alright, I figured that one out. now I can't get it to find the wireless. HELP!

---

### Post by Directrix1 on 2010-08-21
Thank you a million times over for this. Totally did the trick. After downloading the crap from the Realtek website it's definitely nice to see something that works besides ndiswrapper with a 32-bit kernel. This works for me on Ubuntu 10.04 Desktop amd64 just for anyone wondering. BTW, how did you happen to know to echo the usb id to that sys location? Where was that even documented?

---

### Post by spyro777 on 2010-08-28
Yet another success. I actually got it to work first under Virtualbox  with Windows XP as guest OS with Ubuntu 10.04 as host. I could see the  device with lsusb, but I had no indication it was working in Ubuntu, but  this cleared everything up. Many thanks indeed!

---

### Post by jeremy1138 on 2010-09-07
Can anyone confirm whether or not this works with 64 bit Ubuntu 10.04 please?  

I used this to get the wireless card working on a 32 bit WUBI installation but I want to remove that and install 64 bit Ubuntu via the regular installation method so I can have more than 30GB of disk space and so I can use all of my RAM.

Thanks!

[edit]

Woops I just saw that someone posted above about getting this working on a 64 bit installation.  Sorry.

[edit edit]

Just want to confirm that I did get this working with the 64 bit version of Ubuntu 10.04 using the directions in the first post.

---

### Post by sablefoxx on 2010-09-08
MAD PROPS, works like a charm! 

Thanks for the help you saved me a ton of time.

---

### Post by Gannonr on 2010-09-22
Hey I am completely new to Ubuntu, and I do not have any idea how to do what you said to do. If you could actually tell me how I could do those things please? I don't know where to type all that stuff basically. I need to get my f7d1101 to work. And also is there a way to bridge conections like on windows. THanks

---

### Post by Gannonr on 2010-09-22
ok i figured out how to use the terminal and did everything, but I can't make a directory called  			 				/lib/firmware/RTL8192SU/,  it says permission denied??? what am i supposed to do

---

### Post by Joselu on 2010-09-25
i have the same problem with the directory /lib, someone can help us?

---

### Post by thrud00 on 2010-09-29
For those having trouble creating the /lib directory and copying files there, you have to do it from the command line and preface the cp command with sudo. So:

```
sudo mkdir /lib/firmware/RTL8192SU
```

and then

```
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```

Hey, just thought you'd like to to know these instructions worked perfectly on Ubuntu 10.10 too. Even though I'd read that the kernels in 10.10 should support this driver out-of-the-box it wasn't happening.

Thanks for taking the time to document. :)

---

### Post by Messier 66 on 2010-10-03
fdm and thrud00, thanks for making the damn green light blink!:)

---

### Post by CorvisRex on 2010-10-12
WOW!  You are a saint amoung men!  

Worked perfectly with a new install of Ubuntu 10.10 AMD64. Nice and simple.

Thanks!

---

### Post by whackem04 on 2010-10-20
i have done everything in the forum and i can't get it to light up at all
im running 10.10
and help or a finger pointed in the right direction please

---

### Post by punkr0csux on 2010-10-27
This worked perfectly for me in 10.10 64 bit. Thanks for the tip!

> **Directrix1 said:**
>  BTW, how did you happen to know to echo the usb id to that sys location? Where was that even documented?

I'm interested as well.

---

### Post by lt1-gt on 2010-11-04
FYI, I am mega-new to Ubuntu (try 3 hours) so please bear with me...

I just followed the instructions and moved the .bin file over to the directory, and restarted my computer but my card did not start. I re-named the .bin file because there was a space between the "2" and sfw, could that be why?

I have the f7d2101 setup.exe file on my desktop, but it will not install the driver, is THAT my problem?

is there anything else besides those commands that I have to do in order to get it to work?

Thanks

---

### Post by lt1-gt on 2010-11-04
Also,
 what does fdm mean when he says..."First I had to add the device to r8192s_usb"?

does that mean there is a step before adding the code? or is that the first line?

---

### Post by joostvanevert on 2010-11-13
this also works for the sitecom 150n or wl-349 usb adapter.

do everything as described by fdm and replace the vendor and product id's:

**network_drivers.conf**
> install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "**0df6 004b**" > /sys/bus/usb/drivers/rtl819xU/new_id 

**network_drivers.rules**
> ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="**0df6**", ATTR{idProduct}=="**004b**", RUN+="/sbin/modprobe -qba r8192s_usb" 

---

### Post by dacman48 on 2010-11-14
dude, i love you so much right now. for weeks id been using a dd-wrt router/iphone pda net to connect, and IT SUCKED. then i found thiis, and it works a treat. tytyty

---

### Post by ppathak on 2010-11-16
+1 for success story ! It just works on 10.4 ! :guitar:


Thanks a Tonnn !

---

### Post by oogy on 2010-11-17
Running arch linux, but this is the only post about this I've seen anywhere


Did all you described above..

after reboot, when i try to sudo ifconfig wlan0 up
it gives me 

SIOCSIFFLAGS: Resource temporarily unavailable

any thoughts? wlan0 only shows up with ifconfig -a, so somethings not configured correctly..

any help wuold be appreciated.

---

### Post by oogy on 2010-11-17
nevermind i put the firmware .bin in the wrong folder i'm an idiot.


thanks a bunch for this!

---

### Post by lamaistres on 2010-11-18
After following the OP directions but using the RTL8192SE firmware found on the arch forum site, the adapter is working perfectly. I had connection and disconnection problems with the firmware file from svn.debian.org. Thanks fdm for posting the procedure. It helped me greatly.
:)

---

### Post by MrDelish on 2010-11-18
Worked perfectly on 10.04 64-bit. Thanks!

---

### Post by Aledine on 2010-12-15
Good job & Many thanks! It works in Ubuntu 10.10. The Belkin USB adapter in my Linux Box is now working with a much stronger signal than when using the windows XP driver & Ndiswrapper. :D

---

### Post by lespeggy on 2010-12-18
I tried to download the firmware via wget as suggested earlier, but nothing downloads. It shows that it is connected to the server but nothing downloads. It just seams to time out. I've tried 10 times (a definition of insanity). ?

---

### Post by g7r3d on 2010-12-24
Thank you, worked perfectly after I changed, all instances of 945 to 845...never was a fan of ndiswrapper because it seems counter intuitive to wrap Windows drivers and run them on a Linux box, just my $.02!\\:D/

---

### Post by RichieB07 on 2010-12-31
I have done this on Ubuntu Studio 10.10 32-bit AMD64 to no avail.  I've also do the work around posted here: [http://ubuntuforums.org/showpost.php?p=10273494&postcount=12](http://ubuntuforums.org/showpost.php?p=10273494&postcount=12)

This is beyond frustrating, just makes me wonder why you don't just install all the Studio software onto a regular Ubuntu install.

That and now the OS isn't even booting.  It gets to GRUB, I select it and the screen just stays blank.  Ugh!

---

### Post by FloobenShnooben on 2011-01-08
Thank you SO much for this. I know Linux pretty well, but I couldn't get this to work, or find anything else that could help me. But this, this was excellent. Thank you very much.:)

---

### Post by arenacon on 2011-01-11
THANK YOU! Im new to Ubuntu and I've spent several hours trying to get this Belkin USB to work.  After following your steps everything worked on the first try.

---

### Post by Bo0ddha on 2011-01-12
Ok I'm really banging my head against a wall here.  So I followed your guide and it will now show that I have a wireless option.  It will not show what networks are in the area.  I try to enter the network name and password manually and it immediately just says not connected.  Also the green light still won't light up.  Please help me.  This is driving me nuts.

---

### Post by RichieB07 on 2011-01-12
> **Bo0ddha said:**
> Ok I'm really banging my head against a wall here.  So I followed your guide and it will now show that I have a wireless option.  It will not show what networks are in the area.  I try to enter the network name and password manually and it immediately just says not connected.  Also the green light still won't light up.  Please help me.  This is driving me nuts.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart) is a long way to do it.

If you want install NDISgtk from Synaptic, go into your folders on the Drive CD til you find the folder and drag and drop the driver into NDISgtk.  It should work instantly.

---

### Post by Bo0ddha on 2011-01-12
Well I was unable to get it working on 10.10.  Reinstalled with 10.04 and worked right away.  Broken on 10.10?

---

### Post by kg4cna on 2011-01-13
Thanks a million! Works great and gets a great signal :)

Thanks again,
A~

---

### Post by godzy on 2011-01-22
I'm having problem here with ubuntu 10.10 AMD64.
Everything works fine for some minutes (5-10)...than the connection falls down.
I remove the usb pen and re-insert it and it works for others 5-10 minutes...than the connection falls down again.

:confused::confused:

---

### Post by Jacob Christ on 2011-01-23
I got this to work beautifully on my Ubuntu 10.04 LTS system but I did have some frustrations and I'm offering these warnings:

I first tried on another system Sony Viao (VGN-FZ283BN) that has build in wifi.  When I rebooted and logged in, I could launch nothing, could not even shutdown.  So I rebooted with wifi shut off (switch on front of laptop) and Belkin removed and I once again had control.  I could see that the Belkin driver was there, but when I turn the Viao wifi card on again, it seemed as if sudo commands would not work on the command line.  I commented out lines that instructions had me add and rebooted and everything seems to be fine again.

The computer that this worked for me on is a desktop that does not have built in wireless.

Next step, I'm going to upgrade the desktop to 10.10 and see how things go...

Also, this Belkin was the cheapest wireless USB device at the BestBuy, seems like this should be built into the distro, its bound to be popular based on price alone.  If I was smart enough I would do what I could to make this the case, but alas, I know little on how to contribute such changes.

UPDATE 1:  I have this working with 10.10 as well.  Though there is one issue.  When I run Virtual Box (V4.???) (Windows XP Guest) using Bridged Networking everything works fine, but when I close the guest session networking dies for the Ubuntu host and the machine needs to be rebooted to recover.  Bridged Networking didn't work in V3.04(?) of Virtual Box with this dongle.

UPDATE 2: I've decided that the issue I had above was not due to VirtualBox, but instead that the card is just flaky and cuts out every once and a while.  I've been able to run VirtualBox and quit and still have networking, and then just listening to Pandora the several times networking goes out.  Rebooting fixes restores networking.
 
Jacob

---

### Post by Afsoon on 2011-01-29
Hi people. I have done this in Ubuntu 10.10 but not wortk. I am doing all but any change. What i can do wrong?

PD:Sorry for my bad english.

---

### Post by JB_1980 on 2011-01-29
Dude, You rock. I just got this working like a charm on Ubuntu 10.10 32 bit. I couldn't connect with an ethernet cable, so I had to copy the firmware file to a usb and copy and paste it into /lib/firmware/RTL8192SU. I just did that part with using "gksudo nautilus". I am more visual I guess. 

But thank you, thank you. I would have fought for days with this on my own.

---

### Post by IlikeCookies on 2011-02-04
I  just did a blank install of ubuntu 10.10 (64) and this didn't work for me.  Can somebody tell me if the below is normal and I did it right?  

1.  When I used gedit to edit network_drivers.rules and network_drivers.conf both files were empty until I pasted the suggested lines into them.  Were they suppose to be new files / blank?

2.  When I got to this step I couldn't move the file because it did not exist.  sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU.  I had to rename "di...rtl8192sfw.bin" to "rtl8192sfw.bin" in my working directory to be able to copy as defined in the instructions.  Did I do something wrong here and this is why it isn't working?  

When I reboot it says that my wireless is disabled just like I hadn't done any work at all.

Thnx for any help.

---

### Post by hu8mypho on 2011-02-20
> **lamaistres said:**
> After following the OP directions but using the RTL8192SE firmware found on the arch forum site, the adapter is working perfectly. I had connection and disconnection problems with the firmware file from svn.debian.org. Thanks fdm for posting the procedure. It helped me greatly.
:)


Hello, just wanted to clarify that you follow all the details and wordings just used a different firmware file?
I ask this because I noticed that there was a RTL8192SE directory available on my system, can I just simply replace the firmware file that I downloaded with the one already available on my system? 

Thanks!:confused:

ubuntu:/lib/firmware/RTL8192SU# ls -alrt
total 92
drwxr-xr-x  2 root root  4096 2011-02-20 12:23 .
-rw-r--r--  1 root root 68368 2011-02-20 12:23 rtl8192sfw.bin
drwxr-xr-x 51 root root 20480 2011-02-20 12:29 

ubuntu:/lib/firmware/RTL8192SU# ls -alrt ../RTL8192SE
total 276
-rw-r--r--  1 root root 88856 2011-01-05 12:31 rtl8192sfw.bin
-rw-r--r--  1 root root 89616 2011-01-05 12:31 rtl8192sfw74.bin
-rw-r--r--  1 root root 75984 2011-01-05 12:31 rtl8192sfw492.bin
drwxr-xr-x  2 root root  4096 2011-02-20 12:29 .
drwxr-xr-x 51 root root 20480 2011-02-20 12:29 ..

---

### Post by mphollo on 2011-02-24
Thank You very Much! This worked perfectly (Ubuntu 10.04 LTS 32bit) the connection speed is actually showing it is connected at 300 Mb/s! I do not have anything to test this speed but my Lynksys G was only showing it was connected at 54 Mb/s.

---

### Post by Dillz on 2011-03-01
Any help on this I'd really appreciate =]

I followed the instructions and the card DOES find my network now, but it will not connect. It stays in the connecting animation for a few minutes then it says disconnected. The connection I am connecting to is unsecured as well. Like I said, any help I'd really appreciate!

---

### Post by Dillz on 2011-03-02
Tried setting my network up as static today hoping that'd fix the problem but sadly, did not. Any ideas here? =/

---

### Post by coldfire6695 on 2011-03-04
I'm running 10.04, and I followed this tutorial verbatim. I got it to recognize this device, even got it to show the wireless networks in range, but it won't connect. 

I'm about to retry the installation, maybe I copied something wrong, or I missed a step. I will post any further updates if their are any.


Somewhat offtopic: Could someone post the Inf and sys Files for this from XP? I have the installer on a Flash drive, and its all compiled into an exe file. I'd get the myself but all my other system's run linux, mac, or windows 7.

---

### Post by Dillz on 2011-03-04
Still trying to figure this out. It does connect for a short period of time I have noticed, and when it does connect though, there are no IP settings. As in it is completely blank. Then it goes and disconnects. Sorry for being an uber noob but i'm still trying to figure all this out. . . I've only had ubuntu for a week now ahha.

---

### Post by kurtisj on 2011-03-08
Oh man, thank you fdm.

This post is written over a session on my belkin f7d1101 on my Ubuntu 64 bit system:
Linux xxx 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

I believe that I am connected over a WPA2 connection as well. Quick and easy.

---

### Post by celticwonderer2005 on 2011-03-09
Thanks!

Killer fix! Followed your steps and worked first time! Hooked right up to my Verizon Router with WEP and great performance.

Thanks again, before I had to open my router up and the only security I could enable was hiding my SSID broadcast...

Thanks Again!

Jeff

---

### Post by hanketsu on 2011-03-16
I just got Ubuntu 10.04 Functioning on an old xw4100 I had laying around to try it out and get my friend a PC to use. He gave me the Belkin F7D1101 USB wireless adapter and asked if I could make it work. 
I'm really glad I found this posting! Worked like a charm, friggin brilliant! Thanks so much for taking the time to write up the steps to get it working. I'm still new to Ubuntu and this helped a ton!

@celticwonderer2005
Dude, for security sake please change your wifi settings from WEP to WPA2 or something else more secure. I learned in my Cisco class how to crack WEP in 30 seconds or less, instructor showed us just how weak it is. Just an FYI. ^_^

---

### Post by gabevillegas on 2011-03-18
I'm running ubuntu 10.10 and in the first step I had to alter /etc/udev/rules.d/70-peristent-net.rules instead.  After I figured that out everything worked great, excellent tutorial.

---

### Post by kleinfelter on 2011-03-22
This works very nicely with a D-link "nano" USB, and Ubuntu 10.10 (Maverick).  Model is DWA-131.  The DWA-131 contains an RTL-8192SU.  Its VID is 07d1 and its PID is 3303.

---

### Post by ayumu on 2011-03-27
> **Dillz said:**
> Still trying to figure this out. It does connect for a short period of time I have noticed, and when it does connect though, there are no IP settings. As in it is completely blank. Then it goes and disconnects. Sorry for being an uber noob but i'm still trying to figure all this out. . . I've only had ubuntu for a week now ahha.
 I solved "connection/disconnection" problem downloading and compiling last version driver from Realtek's website: [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

 Instructions to install are included in tar.gz file. Probably you need "build-essential" to compile drivers (*sudo apt-get install build-essential*).

 Good luck and sorry for my bad english :(

---

### Post by jramshu on 2011-04-24
Just followed your directions for my brothers old Dell Inspirion 5100 and it works great!!!!

Thanks for the guidance!!

I have converted my brother to Ubuntu today. He's a little nervous about the command line but is eager to jump in and learn. Thanks to seeing support on here.

---

### Post by Wolf_22 on 2011-05-01
I tried to follow the instructions, but I'm having some problems getting it to work with Ubuntu Server 11.04 ("Natty Narwhal"). One issue I've experienced is that the first 2 files in this tutorial don't exist.

Has anyone tried to use this on 11.04 with the Belkin F7D1101???

---

### Post by itsmilesdavis on 2011-05-02
I've (slowly) gotten this card to work on three different installations, by mixing and matching guides.

This one worked perfectly.

Thank you!

Ubuntu 11.06 64bit, clean install.

---

### Post by Wolf_22 on 2011-05-02
> I've (slowly) gotten this card to work on three different installations, by mixing and matching guides.

This one worked perfectly.

Thank you!

Ubuntu 11.06 64bit, clean install. 

You're full of crap. Not only did you not provide any details whatsoever to what it was you did during your installation, but you referred to the device as a "card" when in fact, it's a freaking USB adapter.

And anyone worth their two cents of technical expertise would realize immediately that this write-up is far from perfect. It does help--according to everyone else around here--but is not *perfect* by any stretch of the imagination.

---

### Post by Slownis on 2011-05-12
Can someone help me out? I followed all the directions. I'm on a Sony VGN N130G with built in wireless. The built in wireless has allways been flaky, and so the solution in windows xp was to use this Belkin F7D1101, which worked flawlessly. Now I'm trying to run Ubuntu 11.04 and only the built in wireless shows up. I followed the directions and the green light never comes on, and the adapter never shows up in the list of wireless connections.
 
I also tried the ndis wrapper for windows driver thing first, and with that it would show up in the list and the light would come on, but I could never get it to connect.
 
Edit:
Weirdly after rebooting 2 times, it worked perfectly.... for a while.  I closed the lid and when I opened it up again, the Belkin adapter is still in the list, but it no longer works.  I'll mess with it more tonight and see if I can learn anything.

---

### Post by pwnjangles on 2011-06-03
This worked for me before but now it wont because the link for the firmware 404'd so
I copied the rtl8192su.sys from the CD but can't move it to the file system...what do I do?

---

### Post by calande on 2011-06-06
When I start my computer, I have to unplug and plug back in my dongle into a different USB slot until it shows up in the network applet icon. Do you also have the recognition problem? This looks strange to me.
Thanks,

---

### Post by thebigragu on 2011-06-10
Will these instructions work for version 9.10 of Ubuntu? I haven't used this computer for a while and now need the belkin usb adapter to work in order to update. I did manage to copy the file to the right place and when i restarted there was still no signal from the USB. Is there a way to get it to work with the earlier version or should i just give up?

---

### Post by calande on 2011-06-10
@thebigragu: try unplugging the dongle and plugging it back into a different USB socket, and wait for a few seconds...

---

### Post by thebigragu on 2011-06-10
Actually it turns out that I just made the directory, I tried to copy the file on a flashdrive and not quite sure how to get the file to the directory I just made. Is it possible to move the file I just downloaded to put in the directory.

From what I understand wget goes to the website and downloads the file and then the other commands make a directory for it and it copies the file and all is good.

I know that mv would move but I'm really confused if I have to be on the same directory as the file and say the file is on the desktop how to move that file from there to the one just made.

I keep getting no such file exists or directory when I try something like
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU 			 		
So I am probably misunderstanding something. Would I just need to add more specif of the location because I'm on the desktop directory?

---

### Post by calande on 2011-06-11
@thebigragu:

There's a slash missing after the directory. Go to the directory _where your file rtl8192sfw.bin is_. Then run:

sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU**/**

The difference between with a slash or without a slash is that with a slash, *mv* considers RTL8192SU as a directory, and it will try to place the file under this directory. Without a slash, it considers RTL8192SU as a file, and tries to replace it (or to create it).

---

### Post by thebigragu on 2011-06-11
> **calande said:**
> @thebigragu:

There's a slash missing after the directory. Go to the directory _where your file rtl8192sfw.bin is_. Then run:

sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU**/**

The difference between with a slash or without a slash is that with a slash, *mv* considers RTL8192SU as a directory, and it will try to place the file under this directory. Without a slash, it considers RTL8192SU as a file, and tries to replace it (or to create it).

tried it with the slash and still got the same message that file or directory does not exist. So incredibly frustrating when i know it does exist and this method has worked for others. I really appreciate you're taking the time to help seeing how it wouldn't benefit you in the slightest if i got it to work. Is there anything else you can think of why this isn't working besides human error (i've checked a billion times over)? Thanks again.

---

### Post by calande on 2011-06-11
Yes, run this command:

sudo mkdir /lib/firmware/RTL8192SU

It should say the directory already exists. If it returns nothing, then it created the directory and that was the problem. And then run this one:

ls rtl8192sfw.bin

It should return rtl8192sfw.bin, otherwise if it returns nothing, you're not in the right directory where you file rtl8192sfw.bin is.

Other than that, be careful that it's rtl, not rt1 in the file name.

---

### Post by bindaaz on 2011-06-21
I could get my wireless working with the instructions in the first post. But I had the connect / disconnect problem. Usually after around 30 mins the connection was becoming slow and after a certain point of time it was automatically disconnected. I had to restart the machine to get it working again. Researching further, I found a fix for the problem and now it's working fine for me. I did the following steps.

1. Download the newest driver from real tek website - [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

2. Unzip the driver to any directory. I used the current Downloads directory under /home/user. 

3. Browse to the directory "driver" in the unzipped directory. There is another compressed file rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401.tar.gz in this directory. Unzip this file also in the same directory.

4. Now open the terminal and change to the rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401 directory which is currently unzipped.

5. Execute the following commands in the terminal.
   
sudo su make make install
6. Now restart the machine. The connection should be working without any problem. The workaround specified in the beginning of this post is not required anymore.

---

### Post by bindaaz on 2011-06-21
Sorry the point #5 in my above post is not formatted well.
> . sudo su make make install

The commands should be like the following.

```

sudo su
make
make install

```

---

### Post by calande on 2011-06-21
I sold mine. No time to waste. I'm now using a [PLC]("http://en.wikipedia.org/wiki/Power_line_communication") adaptor. My wife was going nuts having to unplug the dongle and plug it back in on every system start.

---

### Post by pwnjangles on 2011-07-04
Ok this works without a problem on 11.04 but...I hate 11.04 and would like to get this working again on 10.04 or 10.10 every link to the firmware 404'd: [http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)
and
[http://www.dixonjp.com/wp-content/uploads/2011/05/rtl8192sfw.bin](http://www.dixonjp.com/wp-content/uploads/2011/05/rtl8192sfw.bin)
Anyone know of any other links? :(

---

### Post by Wolf_22 on 2011-07-04
> **pwnjangles said:**
> Ok this works without a problem on 11.04 but...I hate 11.04 and would like to get this working again on 10.04 or 10.10 every link to the firmware 404'd: [http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)
and
[http://www.dixonjp.com/wp-content/uploads/2011/05/rtl8192sfw.bin](http://www.dixonjp.com/wp-content/uploads/2011/05/rtl8192sfw.bin)
Anyone know of any other links? :(

Use the *.deb links to install ndiswrapper and use it to install the wifi adapter, but don't screw around with the ******** konsole crap--use the gui (ndisgtk).

1.) Download and install the ndiswrapper deb file from here ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)). You need to find your version of Ubuntu, and then go to the "misc" section (i.e. - if you're using Lucid, you would go get the "ndiswrapper-common" package at "[http://packages.ubuntu.com/lucid/misc/](http://packages.ubuntu.com/lucid/misc/)"). Make sure you get all the deb files you need because you'll have dependencies to take care of with this entire fiasco...

2.) Once you install the deb files, you should probably reboot just to ensure everything's been properly installed, after which you should then go into your System Settings and use the "Install Drivers" or whatever it is that the ndisgtk installs. No, I can't remember what the exact wording is to get to the menu in the Ubuntu "Start" equivalent, but if you installed the deb files correctly, you'll see the new menu item. From there, you should be able to install whatever Windows drivers you need.

3.) If none of the above works, install Windows. lol

---

### Post by ss1979 on 2011-07-06
Hi,

Somehow I followed this method recently for the same belkin USB basic adapter and faced issues during driver initialization. The dmesg log is below:

[    7.731315] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    7.736604] ieee80211_crypt: registered algorithm 'NULL'
[    7.736607] ieee80211_crypt: registered algorithm 'TKIP'
[    7.736610] ieee80211_crypt: registered algorithm 'CCMP'
[    7.736612] ieee80211_crypt: registered algorithm 'WEP'
[    7.736614] 
[    7.736615] Linux kernel driver for RTL8192 based WLAN cards
[    7.736616] Copyright (c) 2007-2008, Realsil Wlan
[    7.736732] usbcore: registered new interface driver rtl819xU
[    7.737782] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[    7.737785] ==>RtInPipes:3  
[    7.737788] ==>RtOutPipes:4  6  13  
[    7.737792] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[    7.737794] 1  1  0  0  2  2  2  2  2  
[    7.741910] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    7.742019] generic-usb 0003:413C:3016.0001: input,hidraw0: USB HID v11.10 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:1d.1-1/input0
[    7.742042] usbcore: registered new interface driver usbhid
[    7.742045] usbhid: USB HID core driver
[    7.844560] lp: driver loaded but no devices found
[    7.866007] parport_pc 00:0a: reported by Plug and Play ACPI
[    7.866069] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.898019] Dot11d_Init()
[    7.898336] ppdev: user-space parallel port driver
[    7.900112] Disabling lock debugging due to kernel taint
[    7.907204] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[    7.946806] [drm] Initialized drm 1.1.0 20060810
[    7.960227] lp0: using parport0 (interrupt-driven).
[    7.964013] leds_ss4200: no LED devices found
[    8.054524] usbcore: registered new interface driver ndiswrapper
[    8.141310] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.141317] i915 0000:00:02.0: setting latency timer to 64
[    8.160832]   alloc irq_desc for 43 on node -1
[    8.160836]   alloc kstat_irqs on node -1
[    8.160846] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    8.160858] [drm] set up 31M of stolen space
[    8.161427] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.389354] Console: switching to colour frame buffer device 200x56
[    8.394478] fb0: inteldrmfb frame buffer device
[    8.394480] drm: registered panic notifier
[    8.394488] Slow work thread pool: Starting up
[    8.394538] Slow work thread pool: Ready
[    8.394568] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.394613] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.394653]   alloc irq_desc for 44 on node -1
[    8.394655]   alloc kstat_irqs on node -1
[    8.394667] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    8.394695] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.399379] rtl819xU:FirmwareRequest92S(): signature: a0a, version: a0a, size: 4f44213c, imemsize: 50595443, sram size: 74682045
[    8.399384] rtl819xU:FirmwareRequest92S(): memory for data image is less than IMEM requires
[    8.399715] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[    8.399717] 
[    8.399899] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[    8.399901] 
[    8.406777] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[    8.458120] rtl819xU:FirmwareEnableCPU(): failed to enable CPU
[    8.458123] rtl819xU:FirmwareCheckReady(): failed to enable CPU
[    8.458126] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), failed
[    8.458270] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: f
[    8.458271] 
[    8.458274] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[    8.458275] 
[    8.465148] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[    8.516119] rtl819xU:FirmwareEnableCPU(): failed to enable CPU
[    8.516122] rtl819xU:FirmwareCheckReady(): failed to enable CPU
[    8.516124] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), failed
[    8.516270] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: f
[    8.516272] 
[    8.523272] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[    8.575871] rtl819xU:FirmwareEnableCPU(): failed to enable CPU
[    8.575876] rtl819xU:FirmwareCheckReady(): failed to enable CPU
[    8.575879] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), failed
[    8.576021] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: f
[    8.576022] 
[    8.576025] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!


Any help in this regard will be of great help. BTW, i am using Linux version 2.6.35-23-generic and Ubuntu 10.10 32bit.

---

### Post by Wolf_22 on 2011-07-06
If I were you, I'd save myself time and hassle and just go get the deb files for ndiswrapper (especially the one for the gui). Saved me LOADS of time and headaches...

---

### Post by walt.smith1960 on 2011-07-06
Take a look at this bug report & fix.  If your error messages in dmesg match those in this bug report, the fix is easy and you should have no issues with speed as have been reported by some when using NDISwrapper. Mine runs at the 150 Mbit/sec. as advertised.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html).  Here's the gist of it:

wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz) 
gunzip rtl8192sfw.bin.gz 
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/ 

the problem is that there's a firmware file missing.  I don't have the Belkin 
but do have 2 RealTek TEW-649UBs using the rtl8192SU chip set.  I did this using Nautilus started with "gksu nautilus"
I'm a woose.:lolflag:

---

### Post by ss1979 on 2011-07-07
Hi Wait.smith

Thanks for the tip. This helped further. Now I am able to see the below log
[  936.983685] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[  936.986806] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[  936.986933] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[  936.988556] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[  936.989683] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[  936.989804] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[  936.989808] rtl819xU:FirmwareDownload92S(): Firmware Download Success
[  939.644627] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Now can anyone please tell me how to configure to make it work?

I tried using Network Manager after this with DHCP and No security key for testing. But it failed to receive the IP and in the UI it is showing device not managed

Here are the other logs from the commands I tried.
**cat /etc/network/interfaces ->**
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

**iwconfig ->**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  Mode:Managed  Frequency=2.417 GHz  
          Access Point: Not-Associated   Bit Rate:130 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ss1979 on 2011-07-07
Hi All,

At last I am able to make this Belkin USB adapter with the above procedure. The problem I faced today was with respect to network configuration as per the settings in the Router. I used WPA Pre-Shared Key method and given a Static IP using Wicd network manager tool in ubuntu. Everything worked fine after that and it is giving a good Signal strength.

Thanks a lot for all your support. BTW, i am posting this using my WIFI connection

---

### Post by walt.smith1960 on 2011-07-07
Don't ya love it when a plan comes together? :KS.  Glad you were successful.

---

### Post by DontWorry on 2011-08-09
After days of searching on how to get the Belkin Basic Wireless USB F7D1101 working with Ubuntu 10.10 I finally got it (With the help of this thread mainly).

I did the first 2 steps, but also edited /etc/udev/rules.d/70-persistent-net.rules and added this:
> ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb" 			 		

I would recommend to not install that firmware he tells you to. At least for me, that was the problem. 

walt.smith1960 posted a bug report and the proper firmware you need to download.
>  wget [http://launchpadlibrarian.net/373876...8192sfw.bin.gz]("http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz") 
gunzip rtl8192sfw.bin.gz 
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

Then I restarted my computer, and it worked perfectly. I can connect to networks and see all of them around me.

---

### Post by ss1979 on 2011-08-20
Hi All,

This method works perfectly on Ubuntu 10.10. Till now I have not seen any issues.

---

### Post by jordanalrifai on 2011-09-11
> **fdm said:**
> I recently purchased a Belkin F7D1101 Basic Wireless USB Adapter just to find it preforms poorly with ndiswrapper and Ubuntu does not support it out-of-the-box. Luckily, it is possible to get this chipset running natively.

1.) First I had to add the device to r8192s_usb(both files are likely empty):

Use this command in the terminal to open the first file:

and add this line:


Save it then run this command to open the second file:

and add this line:



2.) Then I obtained the firmware from here:

and copied it to /lib/firmware/RTL8192SU/ with these commands:



Afterwards, I restarted and all worked well. Perhaps others with this device will be able to get it running well too.

To expand on this process further, r8192s_usb is the kernel module("device driver") for devices with the RTL8192SU chipset. Since the module does not contain the device id for the wireless card, we use the trick demonstrated above to add it to the module without having to recompile it. This works on most distros newer than the stable branch of debian. On some like Suse, you have to install the staging package first(kmod-staging). I also had to add the firmware, dmesg is good for debugging that part. This same process can be used with other devices as long as you can find a module for the chipset and change the info in the lines accordingly.

Alternatives:
compile closed source Realtek 8192SU driver - preforms like windows xp; good signal, not very stable
use ndiswrapper with the windows driver - poor signal, not very stable

Hi friend .. i had the same issue exactly and i spend like 7houres to find out how i do the steps you did .. i didn't .. so may pleas let me know how i can do it.. i don't have know nothing about .. so i hope you can teach me step buy step .. to resolve this issue .. thank you dear

---

### Post by fmiceli24 on 2011-09-12
Thanks!!!!

wget [http://launchpadlibrarian.net/373876...8192sfw.bin.gz](http://launchpadlibrarian.net/373876...8192sfw.bin.gz) 
gunzip rtl8192sfw.bin.gz 
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

This also works on Debian 6!!

Now testing...

---

### Post by infinite143rd on 2011-09-21
ant@ubuntu:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
[sudo] password for ant: 
ant@ubuntu:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
mv: cannot stat `rtl8192sfw.bin': No such file or directory
ant@ubuntu:~$ sudo mkdir /lib/firmware/RTL8192SU
mkdir: cannot create directory `/lib/firmware/RTL8192SU': File exists
ant@ubuntu:~$ ls rtl8192sfw.bin
ls: cannot access rtl8192sfw.bin: No such file or directory


what im i doing wrong? im going nuts ive been at it 6 hours.... when i plug the adapter, under "wireless network" it says device not ready. when i unplug it it no longer recognizes the adapter.. please help someone

---

### Post by infinite143rd on 2011-09-22
fellas please help i really needs web access on ubuntu im really sick of windows

---

### Post by CTenorman on 2011-09-24
I can't seem to get this working under Oneiric beta 2 either. Tried the most recent suggestions as well as the older ones. AH well, time for a new usb wifi adapter!

---

### Post by CTenorman on 2011-09-24
Looks as though this bug may be getting fixed, woo hoo!

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/804671]("https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/804671")

Reformatting and running a quick test on Oneiric. I'd be interested if anyone can turn on the backports and proposed repositories and see if this is working for them as well.

---

### Post by CTenorman on 2011-09-24
It appears not to be working on Oneiric with all repos turned on. At least it's getting looked at!

---

### Post by infinite143rd on 2011-09-25
ok i give up which wireless adapter will work with 10.4.3 out the box......?

---

### Post by fdm on 2011-09-30
Sorry, I should have updated sooner. RTL8192SU was dropped from the kernel some time ago and is now replaced by r8712u. This is included by default and supports F7D1101 out of the box. All you need is the linux-firmware package to supply the necessary firmware. Also, this new driver works better than the old one.

---

### Post by sshoaib on 2012-02-19
It worked very well on ubuntu 10.10/x86_64, thanks mate.

---

### Post by fliphkd23 on 2012-05-10
I followed this guide and it worked very well to get the wireless adapter to work, thanks! 

I am having one problem though. The wireless adapter stops working after the computer comes out of suspend mode. Running lsusb will list the device as being connected, but it doesn't seem to be responding or be able to find/connect to any networks. Rebooting the computer returns the device to working, but is a nuisance! 

If someone could help that would be amazing, this is really irritating me! Oh and if it helps I am running Ubuntu 11.04, 64 bit version.

Thanks

---

### Post by iaponas on 2012-05-14
just completed step by step and its working 100% ... it took me like 3 minutes , while i was trying to make this belkin work for 3 months ... THANK YOU  very much...

---

### Post by VideoRustler on 2012-08-06
Thank You sooo much, worked like a charm with Ubuntu 12.04 LTS.

---

### Post by gbdavidx on 2013-01-14
i am getting cp: cannot stat 'rtl8192sfw.bin': no such file or directory, i have created the lib/firmware/rtl8192su folder too

Any help?

i am on 12.10, latest release

---

