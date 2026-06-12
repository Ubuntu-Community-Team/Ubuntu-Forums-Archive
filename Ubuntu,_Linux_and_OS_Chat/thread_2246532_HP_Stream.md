---
title: "HP Stream"
date: 2014-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Tar_Ni on 2014-10-01
HP has just unveiled it's new line of laptop, the HP Stream with Windows 8.1. it's a low-cost machine for 200$. This is an attempt by Microsoft to compete with Google's chromebooks which are on the rise.

These cuties would make for good Lubuntu machines don't you think?

[http://www.zdnet.com/hp-unveils-budget-windows-stream-notebooks-with-1tb-onedrive-storage-7000034187/](http://www.zdnet.com/hp-unveils-budget-windows-stream-notebooks-with-1tb-onedrive-storage-7000034187/)


Plus that would be easier than with a Chromebook, just boot your USB stick and voilà!

---

### Post by grahammechanical on 2014-10-01
There is one thing that would stop me from buying something like that. Windows 8. Apart from the fact that I would not buy something that I do not want to use, who knows what HP have done to the EFI firmware to keep Microsoft happy. I would not be too quick to say "voila!"

I would also worry about video drivers. It has got an AMD APU. Is there a Linux driver for it?

 Still someone has to be the first. It might as well be you. Let us know how things go.

Regards

---

### Post by Tar_Ni on 2014-10-01
> **grahammechanical said:**
> There is one thing that would stop me from buying something like that. Windows 8. Apart from the fact that I would not buy something that I do not want to use, who knows what HP have done to the EFI firmware to keep Microsoft happy. I would not be too quick to say "voila!"

The HP Stream just look like a new generation of Windows notebooks. Unless the OS is locked in the bios like Chrome OS it should not be much harder to install than your average Windows 8.1 laptop. Ubuntu supports UEFI secureboot. They are low-priced because the specs are low-end (2GB RAM and Intel Celeron which is bare minimum on Windows.. but with Lubuntu or Xubuntu it looks much more promising) and Microsoft has cutted by half the price of Windows 8.1 to manifacturers to compete with low-cost devices like the chromebooks.

> **grahammechanical said:**
> I would also worry about video drivers. It has got an AMD APU. Is there a Linux driver for it?

I was refering to the 2 new models in the Stream's lineup. The HP Stream 11.6'' and 13.3'' inches have Intel Celeron CPU , Intel HD graphic cards and 32G SSDs which is the same hardware than the 2nd generation of HP chromebooks. These will cost 199$ and 229$ respectively. As far as I know, only the 14'' model has an AMD APU.

See: [http://www.cnet.com/products/hp-stream-11-6/](http://www.cnet.com/products/hp-stream-11-6/)

> **grahammechanical said:**
> Still someone has to be the first. It might as well be you. Let us know how things go.

They will be for sale in November in the US first. I am not from the US but still I intend to grab one when they are available worldwide as I am looking for a second machine. 200$ is an amazing price for a new laptop and I really like the slim design of the HP chromebook. If you can wipe out the harddrive and install Linux without too much trouble that would be awesome.

---

### Post by philippe10 on 2014-11-11
I will be trying this tomorrow but I'm not the first, see: [http://www.amazon.com/gp/cdp/member-reviews/A38A7J9YTH3TD4/ref=pdp_new_read_full_review_link?ie=UTF8&page=1&sort_by=MostRecentReview#R28HR668I6LU8Y](http://www.amazon.com/gp/cdp/member-reviews/A38A7J9YTH3TD4/ref=pdp_new_read_full_review_link?ie=UTF8&page=1&sort_by=MostRecentReview#R28HR668I6LU8Y)

Will let you know.

---

### Post by pascalfuerst on 2014-11-13
I bought the HP Stream 14, wiped the harddrive and installed Ubuntu 14.10 on it  

+ Gnome 3 runs well with the fglrx driver installed and Ubuntu doesn't use too much disk space. I'm pretty sure hardware acceleration is important for this laptops performance. Right now only the non-free driver can deliver that. 
+ it is very lightweight for a 14" laptop + the battery lasts for more than, let's say 6 hours. 
+ it looks very nice considering the low price  

- wifi: the built-in Broadcom BCM43142 card forces the owner to use of Broadcom-STA driver which is very bugy. Very unstable connection after like half an hour. Then I would get weird kernel error messages - permanently broken connection - have to reboot. Roaming and environments with multiple APs aren't handled well either. [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1391657](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1391657)
-The wifi driver has to be installed manually, since it's not include in the installation medium.   
- touchpad: The alps clickpad is not recognised as a touchpad but as a ps/2 mouse. So, no touchpad functionalities. single-tap-to-click works, right and left click with clickpad buttons also. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1390915](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1390915)  

The wifi driver has to be installed manually, since it's not include in the installation medium.   

I would buy it again though. I hope the driver problems get solved.

---

### Post by openmn on 2015-01-19
I recently bought an HP Stream 13 from the Microsoft store. It was on sale for $200.

After imaging the eMMC disk in case I needed to put WIn8 back on, I proceeded to install Ubuntu 14.10 64-bit. I install Ubuntu on machines all the time, so I am used to it taking 20 minutes or less. I think this one took about 2 hours. I did a lot of research before the purchase, and most posts led me to believe it has something to do with the Linux Kernel not working well with the eMMC flash storage. The install took forever, but I did not encounter many problems like I read about with other people, like the partitioning. Part of my problem may also involve the full disk encryption that I chose to use, because this is my on-the-road machine.

Note: It was very easy to enable legacy boot in the BIOS, but I did have to check twice to change the boot order to boot to my Ubuntu Live USB.

Once installed, I booted up. It takes 4-5 minutes to boot to the Ubuntu login screen. Again, I think this has to do with the kernel not playing well with the eMMC interface. I have hope that this will get better with newer kernel releases. I did update the latest Ubuntu updates, with no discernable change in boot time.

Once I get logged in, the machine runs pretty much as I would expect a low-end machine like this to. Wifi seems fully functional, apps like LibreOffice load fairly quickly, and software installs don't seem too slow. I run the normal Unity session, as that it the DE I am most used to. I know others have chosen GNOME or LXDE as the DE on low end machines like this, but Unity doesn't seem to run poorly at all on this machine.

$200 is the lowest I've ever paid for a brand new laptop, so much expectations were rather low. I would have just gotten a Chromebook, but I wanted something I could sync Dropbox to and use LibreOffice. I went with the 13 inch screen, and I like the extra real-estate over my 11.6 inch I had before.

This post is about an HP Stream 13 (Blue). Everything I've researched about this machine makes me think only the screen size is different than the HP Stream 11. The guts should be the same.

---

### Post by Clay_Hamilton on 2015-01-23
I ordered one too. Before I did I went to the local office depot and popped in a Ubuntu trial USB. You just hit the ESC key on startup to get the boot menu. It loaded Ubuntu, the keypad worked. I connected to my iPhone hotspot and ran Firefox, Meteor, and WebStorm from it. All worked great. I plan to build a leave-in 32 gb USB 3.0 drive to run Ubuntu and leave the Windows system as is. I'll just change the boot order or maybe the boot loader will let me choose like it does on my laptop.

---

### Post by Clay_Hamilton on 2015-01-26
Well in an odd turn. The office depot store unit booted from my USB in seconds. The one I got from Amazon has been trying to boot for minutes with no luck. Not sure what's going on here. Tested the USB and booted fine on another machine. Will update if/when I figure it out.

---

### Post by openmn on 2015-01-31
The reason the USB stick worked well and the eMMC HD didn't is because there is a tiny partition on the eMMC that Ubuntu is trying to boot to and cannot access. It slows down the boot process immensly (Mine is at about 4 minutes on Ubuntu 14.10). When you boot to the USB, it skips the eMMC entirely. I have also noticed that this problem also slows down when you are upggrading kernels using the Ubuntu Software Update. I've read there is a fix, but I haven't seen it in the kernel yet. I hoping for it to land in 3.19 so my new Stream 13 will run like it's supposed to.

---

### Post by openmn on 2015-01-31
Slow boot explained: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1333140](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1333140)

---

### Post by thatsmyboy on 2015-02-16
Can anyone comment on file transfers with USB 3.0? I'm really interested in compatibility and speed. looking toward getting one of these for myself

---

### Post by martydelaney3 on 2015-02-21
I can say I've had this machine for a few weeks now and I love it. OOB Windows experience is surprisingly smooth for the low specs, but I really bought it for a cheap linux box. Installed Ubuntu and Xubuntu just to see how it would handle them both and it did a great job on both. Only main issues I can report is that the brightness control doesn't work without a quick workaround and the wireless driver definitely has stability issues. I have had issues booting to the installers for any of the other linux distros I wanted to try such as elementary OS and Linux Mint. I've read a few things about utilizing nomodeset because the issue is caused by the intel graphics but I haven't had any success there yet.

---

### Post by dazmcgaz113 on 2015-02-21
In the case of the buggy WiFi connection, couldn't you just plug in an external usb wifi adapter? I have an Edimax Nano USB adapter for my Raspberry Pi which works on Debian so it should work on Ubuntu with the HP?

[http://www.amazon.co.uk/gp/product/B003MTTJOY?psc=1&redirect=true&ref_=oh_aui_search_detailpage](http://www.amazon.co.uk/gp/product/B003MTTJOY?psc=1&redirect=true&ref_=oh_aui_search_detailpage)

---

### Post by micromachine on 2015-02-24
I have installed ubuntu on a stream notebook, I've run all the updates, and the mouse is extremely buggy. I've tried both the touchpad and usb mouse and it seems like sometimes the buttons will work and sometimes they won't and I can't find a consistent pattern. It's pretty much impossible to do anything on the machine without a mouse. I'm not sure what to even try to get it to work. The touchpad settings seem to be no help at all. Any suggestions?

---

### Post by martinez-bernal on 2015-03-02
In my case I tried lubuntu 14.10 and updating kernel to version 3.19 from [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds) seems to fix the problems with the touchpad.

Click & tap works, but I don't know how to set up the right-click to work like in windows (clicking the bottom-right area of the touchpad). Now I can only simulate right click tapping with two fingers. It would be useful to have right click working; then you could disable tapping completely.

---

### Post by fromite on 2015-04-05
Hey all,

    I purchased a Stream 11 around February-ish and have been having issues getting any linux USB drive to work. I currently have legacy supported (have attempted UEFI and gotten nowhere) and have tested the USB drive on multiple machines to no avail. The error I receive when booting from USB is "missing OS". Any ideas where I should start looking? Need more info?

Thanks

---

### Post by michaelmarsh98 on 2015-04-29
just curious have you had any problems with the speakers on Ubuntu 14.04 or 15.04 with it having beats audio?, everything else works for me besides the buggy wi-fi and not all speakers recognised.

---

### Post by michaelmarsh98 on 2015-04-29
you need to go into bios settings and turn off secure boot i think it is or something to do with security, have a look and make sure you get a distro with UEFI support

---

### Post by night_sky2 on 2015-05-02
I would say better to purchase a Chromebook than the HP Stream... Same price, same hardware, but Linux Ubuntu is much easier to install on the former and remain fully compatible..

---

### Post by neu5eeCh on 2015-05-03
> **night_sky2 said:**
> I would say better to purchase a Chromebook than the HP Stream... Same price, same hardware, but Linux Ubuntu is much easier to install on the former and remain fully compatible..

Nah. Just purchased two Streams for my twins going into high school. There is an excellent guide to installing Linux on the Streams in the comment section at Amazon. Running Ubuntu on a Chromebook requires enabling developer mode, which is still IMHO a "sloppy" way to do things. I would say just the opposite -- much better to buy the Stream -- more storage (usually) and you can hand over the laptop to Ubuntu and get all the benefits of ChromeOS simply by installing Chrome -- plus you can print to a so-called air-quotes [clears throat] "***classic***" printer. (As if it were the printer's fault that ChromeOS can't print.)

---

### Post by caffeinatedev on 2015-05-05
> **VTPoet said:**
> Nah. Just purchased two Streams for my twins going into high school. There is an excellent guide to installing Linux on the Streams in the comment section at Amazon. Running Ubuntu on a Chromebook requires enabling developer mode, which is still IMHO a "sloppy" way to do things. I would say just the opposite -- much better to buy the Stream -- more storage (usually) and you can hand over the laptop to Ubuntu and get all the benefits of ChromeOS simply by installing Chrome -- plus you can print to a so-called air-quotes [clears throat] "***classic***" printer. (As if it were the printer's fault that ChromeOS can't print.)

Can you provide a link to said guide? I can't find it.

---

### Post by neu5eeCh on 2015-05-07
> **caffeinatedev said:**
> Can you provide a link to said guide? I can't find it.

Oh, never saw your response. Sorry it took me so long:

[http://www.amazon.com/review/R28HR668I6LU8Y](http://www.amazon.com/review/R28HR668I6LU8Y)

---

### Post by neu5eeCh on 2015-05-08
Okay. I'm typing this on my daughter's HP Stream. Love this little laptop! And I like the screen -- better than any of the comparable chromebooks I've seen. 

So, I chose to install Ubuntu 15.04 in order to benefit from the latest Kernal (3.16). Everything, so far, just works. No wireless problems. Touchpad works well (though I haven't been able to click & drag and that may just be me). 

In terms of install, I asked her to choose between Windows or Ubuntu. She picked Ubuntu since that's what she's familiar with. (Also trying to teach her about the open source ethic.) I didn't so much as bother to back up WIndows. Have no use for it, really. Soon as it booted up (she tried it) it looked like one big advertisement/billboard, and she asked: "Am I supposed to read all these license agreements?" Gave the whole "HD" to Ubuntu. Boots up fairly quickly and is responsive. Way better than a chromebook IMHO. And it prints to "classic printers". Using about 6.5 Gig of 20 + 1.6 Gig Swap assigned automatically.

---

### Post by 00b00nt00 on 2015-07-07
Owner of an HP Stream 11 here.

Versions of Ubuntu up to 15.04 won't install on the eMMC drive. The dailys of 15.10 will install if one ignores the warning messages; the only problem I have found is that Bluetooth doesn't work properly, but I can live with that.

I recommend an Xubuntu install. The Stream is pretty snappy with that!

---

### Post by fabien-services on 2015-09-22
Installed 15.04 on an HP Stream 11, only had to disable the protected boot then it went smoothly.
I replaced the Windows installation so I have the entire disk for Ubuntu, about 30Gb.
Boot in 22seconds from power on to a working terminal (urxvt) in a window manager (ratpoison).
WiFi, video card and sound card all worked without having to configure anything.
Functions key also worked in Gnome without having to configure anything.
Battery indicated by upower starts at 8hrs.
Powering off using the button worked well.
Resuming worked every single time, just closing then opening back the laptop few times.
No right-click by default but [Option "ClickPad" "true"]("https://www.reddit.com/r/linux/comments/3cw3ei/hp_stream_11_no_right_click/") fixed it, note that this allows for bottom right corner of the touchpad to become a right click and to scroll up and down using 2 fingers (one for pivot, one for scrold

Battery : 6hours on normal usage (WiFi, video, full brightness, not using tlp), a bit more than 2 hours to charge.

So far no problem to report.

---

### Post by alan64 on 2015-11-11
Installed 15.10 on an HP Stream laptop (13-c002dx). Had to use an external wifi card at first, but sudo apt-get update got the onboard wifi working. Everything runs perfectly, silent, cool temperature, OS boots from hard drive in only a few seconds, suspend/resume is all good, etc.

Only problem: can no longer boot from USB, regardless of what I do to BIOS settings.

---

### Post by night_sky2 on 2015-11-11
> **alan64 said:**
> Only problem: can no longer boot from USB, regardless of what I do to BIOS settings.
I think that's because the HP Stream use 32-bit UEFI Secureboot, which is not supported by Ubuntu.

[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

But how did you get it to boot in the first place? And did you try another USB drive?

---

### Post by p-p-8 on 2016-01-29
I just got one of these yesterday for my daughter, a purple 13 in UK, there is a lot of variation in network cards offered across the range (the one in store, blue, also a 13 had a braodcom, this has a realtek)....


There are a few things to note about this laptop, the main bug bear with me is the touchpad is a bit clunky, its an all in one jobby and if you rest your finger where the left click is whilst trying to move the mouse, the mouse will not move, if you click and then move it will drag. The main issue here is you will notice you will have to change your mouse habits a little or you can get some strange results on screen. That being said, enabling tap to click sort of reduces this (with the added habit of removing other hand from pad, hard to teach a 12 year old this though).


Main issue here are the following...


1) First power on machine and hit F10, go into bios boot settings and enable legacy mode (disables secure boot when you do this). UEFI boot did not work for me on 15.10 in 32 or 64bit ubuntu so no point even going down that path. Reboot the machine and press F9 to boot form USB (your ubuntu flasdisk).


2) On boot you will either have no wifi (broadcom) or you will have wifi but really bad signal level (realtec), whilst this is apparent on boot up, I would not fix this yet, lets just do...


```
lspci
```


In terminal to find out network card for info....


3) Now you have limited space here so the best option is to install and set your own partitions, to ensure the nasty unknown partition is removed (this can hang boot times badly), I wiped out all partitions by choosing to manually create my partitions on install.... the usual here, 20gig for / on ext4, 4gig for swap (as this laptop has limited ram) and the rest for /home on ext4 (yes i know this is not much, more on this later).... do not try to connect wifi or download updates on install.


4) Once installed, reboot, remove media and stop machine.


5) Now if by any chance you had the realtec 8723be network card, you are gonna have to get out your comfort zone... If you had the braodcom, you will need to only use a USB wifi card (or tether over USB to your phone) to...


```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```


That should sort your wireless on restart if it was not working already....


If you have the 8723be then get your screwdrivers out as the realtec wifi driver that works uses the aux antenna connection on this card and the windows uses main (the card is dual antenna and only one is connected internally). 
You will need to undo all screws on the bottom, including the two under rubber feet at rear, the one under the rubber bung center rear and two under rubber grommets right at the rear.


Gently unclip the top from the base, use something plastic and pull to the side to unclip. The back clips are very strong and you have to be a little rougher than you would like to get them to free (ensure its not the two screws under the two rubber grommets still in)
Once you have the top (with the keyboard attached) off, you will see the card center rear, with a little thin black wire going to it. Gently pry this upward to free, swap it to the other connector next to it (aux), put it all back together and reboot.




5) Boot time should be pretty good (20 sec ish i would say), like i say either wifi will work or not. Now if you did have the realtec card you will now notice you have full wifi signal, but don't jump around just yet, it wont last long before it stops working so you have to be quick..


```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware

```


this will load the good driver into the kernel, main issue here is if you upgrade the kernel at any point and start getting problems with wifi again, you will need to drop back to this driver again with the last command.


Now is a good time to reboot.


6) You should now have a working laptop, with wifi.


7) I would now go into settings > mouse and enable tap to click (trust me, learn to tap), once done, we just need to sort the home space....


8) Buy yourself a 64gig micro SD card (get a half decent one with good speed of say a min 80) and pop it into the slot. Format this to ext4 and name it SDHOME. At this point we could alter fstab to mount on boot but I didn't for one good reason (the same reason i dont symlink the whole home folder)..
I may need to use the micro slot at some point, which is why we have home still on the inbult ssd, so we can still run without the card in.
Remove all folders in your /home/user directory and we will rebuild them on the card, change USER to youruser name


```

sudo rmdir /home/USER/Desktop
sudo rmdir /home/USER/Documents
sudo rmdir /home/USER/Music
sudo rmdir /home/USER/Pictures
sudo rmdir /home/USER/Videos
sudo rmdir /home/USER/Templates
sudo rmdir /home/USER/Public

```


create these on the SD card, change USER to your username


```

mkdir /media/USER/SDHOME/Desktop
mkdir /media/USER/SDHOME/Documents
mkdir /media/USER/SDHOME/Music
mkdir /media/USER/SDHOME/Pictures
mkdir /media/USER/SDHOME/Videos
mkdir /media/USER/SDHOME/Templates
mkdir /media/USER/SDHOME/Public

```


Now we symlink to your home so your system uses the card now instead of the SSD in your laptop.


```

ln -s /media/USER/SDHOME/Desktop /home/USER/Desktop
ln -s /media/USER/SDHOME/Documents /home/USER/Documents
ln -s /media/USER/SDHOME/Music /home/USER/Music
ln -s /media/USER/SDHOME/Pictures /home/USER/Pictures
ln -s /media/USER/SDHOME/Videos /home/USER/Videos
ln -s /media/USER/SDHOME/Templates /home/USER/Templates
ln -s /media/USER/SDHOME/Public /home/USER/Public

```




This will add links in your home, so now say when you doanload or create a document, it will be stored on the SD card


The main reason for only moving these folders are these are the main folders that take up space, this also keeps your configs on the SSD (should the SDCARD not mount or fail), and allows you to run the laptop without the SDCARD in, but giving you the extra space you need (trash also still sits on the SSD)
You have your SSD home at about 7gig so this is more than enought for trash (just make sure to empty it more often) and configs, best of both worlds and more flexible.


Thats it, boots in 20 sec, wifi solid and works all round the house, only issue is the wacky touch pad which just needs a bit of re-teaching of habits to get used to.


For 200 quid, well worth it

---

### Post by De_Moran on 2016-03-06
Minor quibble
ln -s /media/USER/SDHOME /home/USER
will accomplish the above links in one line.

The step by step is much appreciated.
I am lazy :)


DM

---

