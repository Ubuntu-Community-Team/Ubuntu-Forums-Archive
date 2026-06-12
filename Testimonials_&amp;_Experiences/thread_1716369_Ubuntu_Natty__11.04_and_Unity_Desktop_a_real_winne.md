---
title: "Ubuntu Natty  11.04 and Unity Desktop a real winner!"
date: 2011-03-28
forum: Testimonials &amp; Experiences
---

### Post by tlcstat on 2011-03-28
Greetings,
I finally got my 500gig Hd and have installed the Natty 11.04 and the Unity Desktop. Even though I use all linux software I installed a dual boot so that I can support a previous customer without using the VM. 
I have to say that the Unity Desktop is just great! The more shortcuts I find the more I like it. Also, it gets better with every update which has been running around 100meg a day excluding Sunday. Because of the size of the hd I used a multi partition scheme that looks like this. 

Primary SDA 50Gig NTFS (fully install WindowsXp to boot before preceeding.
Primary SDA2 500Meg ext2 /boot partition for grub files. Grub in SDA mbr.
Primary SDA3 3Gig Linux Swap
Extended SDA4 433Gig
SDA5 EXT4 20Gig /Ubuntu Natty DEV installed.
SDA6 EXT4 20Gig /USR
SDA7 EXT4 20Gig reserved for testing extra operating system.
SDA8 EXT4 265Gig /HOME
SDA9 NTFS 110Gig Window NT partition for shared data.
This scheme allows me to reinstall my Windows or Ubuntu without having to deal with Ubuntu, Windows, or Grub data since they are on their own partitions. 

As much as I have enjoyed Maverick 10.10 and Gnome, I am moving on. This Unity Desktop is a really great system that gets better as I learn to use it. 
The side menu bar has been improved in that it will auto hide if you run an app in full screen or even in a window if you move the window to the left side of the screen, the window will push the bar out of the way. 

There is a control panel (system settings) shortcut under the shutdown link in the upper right corner.

Minimized pages will have a single left side tick mark on menu icon. Hence there are no minimized items on the bottom of the screen.

You can easily add items to the menu bar by dragging them from /USR/SHARE/Applications. 

If you are running a full screen application and need to access your hidden menu bar, you can hover your mouse pointer over the top left corner of the screen and the menu bar will appear in transparent mode. You can scroll straigt down to the item you need to open. 

At this point I haven't been able to add anything to the top panel. 

If you have an app open the "file"menu will be on the top left panel. The menu will switch with the app that you have on top.

Also, I not going to tell you what happens if you "alt" "tab" to switch windows. Install it and find out for yourself!

Compiz is working just fine with my Intel graphics. If you have the Intel chipset and compiz wasn't working then try it again with the updates. I am still getting some "error" popups but they are too few to be a bother. 

I put my old 160Gig HD in a USB controller box so that I can boot my old Maverick installation if needed. So far I haven't had to use it at all.

This is going to be a popular desktop. No question about it! 

Toshiba L305 15" Laptop, 500Gig HD, 4Gig Ram, Intel chipset, Atheros Wifi, GPRS internet. 

tlcstat

---

### Post by ventrical on 2011-03-28
I have natty running from a USB flash. Unity is great - pretty nifty .. but I can't seem to tame compiz settings manager. Perhaps  (natty) is for higher end systems or to just wait it out for daily updates.

I'll wait and see how this improves but i still have to give all the high marks to maveric because of assistive techs.

---

### Post by tlcstat on 2011-03-28
Greetings,
I don't know what your situation is, but I would recommend testing from a USB HD. You can buy a SATA HD and a usb controller from Amazon.com for less than you can buy a USB Drive. With USB2 the speed is just as fast a an internal HD. My experience is that it's hard to get a sense of speed running from a flash drive. 

I installed the Compiz Manager from the Software Center. Everything seems to be improving with the updates so far as functionality. When I first installed one week ago the Intel Video didn't work with Compiz at all on this machine. I have 1200Meg of Video ram with this chip set so that seems to me to be a lot of hardware to work with. I think they put their effort behind the high end gaming chips to start with.

---

### Post by cariboo on 2011-03-28
Depending on what Intel graphics chipset you have, I've been using Unity on my netbook with the 945 chipset since the tool chain upload, and haven't had any problems since the 2.6.38 kernel was released.

There are some Intel graphics chipsets that can still be a problem. specifically the i3//5/7 built ins, seem to be giving people problems.

I have to agree about running a disto on a usb thumb drive,  it can run fairly well, but updating seems to take a very long time.

---

### Post by tlcstat on 2011-03-28
Greetings,
I don't know what your situation is, but I would recommend testing from a USB HD. You can buy a SATA HD and a usb controller from Amazon.com for less than you can buy a USB Drive. With USB2 the speed is just as fast a an internal HD. My experience is that it's hard to get a sense of speed running from a flash drive. 

I installed the Compiz Manager from the Software Center. Everything seems to be improving with the updates so far as functionality. When I first installed one week ago the Intel Video didn't work with Compiz at all on this machine. I have 1200Meg of Video ram with this chip set so that seems to me to be a lot of hardware to work with. I think they put their effort behind the high end gaming chips to start with.

---

### Post by ventrical on 2011-03-28
I do most of my experimenting on an Acer Aspire, 3620 with 1.5 GB ddr and a Dell Inspiron B130.  The graphics work ok  and it appears that the monitors are being detected but I'm doing somthing wrong with compiz settings.

I also have a USB to IDE converter so that speeds it up pretty good - but I just like the USB route. 

Perhaps I will give my Dell OptiGX a try with (natty) using a different surplus drive. Currently I have it dual boot with XP and Ubuntu 10.04.

---

### Post by ventrical on 2011-03-28
I am going to put the (natty) alpha 3 as a dual boot on my Maveric HDD.

I'll get back :)

---

### Post by ventrical on 2011-03-28
Ok... works a lot better now that it is installed on my hdd alongside of Maveric.

Even the wireless is up now!!:)

The Unity Docky thingy is pretty swift - but it takes a little getting used to. it is really stable. I am going to try the compiz manager now.

So far, so good.

---

### Post by LittleCui on 2011-03-31
i don't like unity. In the beginning i choose  gnome because it's simply. But for the unity, i don't like it now. i will just stay in the simply gnome classic.

---

### Post by Tamlynmac on 2011-03-31
> littlecui
but for the unity, i don't like it now. I will just stay in the simply gnome classic.

+1

---

### Post by bowens44 on 2011-04-03
IMO Unity looks and feels like a poorly designed child's toy, not a computer DE for serious users.

---

### Post by XubuRoxMySox on 2011-04-04
A child's toy? Sounds perfect for *this* child, lol. Actually during my flirtation with LXDE (omygosh, more than a year ago now!) I had a big ol' transparent oversized panel that looked more like a dock, and when I first saw screenshots of Unity I was like, "Whoa, that's my old LXDE desktop!"

My family thought it was too "Fisher-Price" for them. Even most of the other kids at the dance studio didn't like it. My brother called it "Win-98ish."

But they *all* like the new Xfce! I can have my "docky-looking" transparent, oversized panel or not, but with all the versatility and power of Xfce! I think it will become a very popular alternative to Gnome 3 and Unity for people who hate the "Fisher-Price" look, but *also* for kids like me who happen to actually *like* the "Fisher-Price" look.

No accounting for taste I guess, lol. But that's the beauty of Linux - and the versatility of the new Xfce desktop - it can be just about whatever you want it to be!

-Robin

---

### Post by frncz on 2011-04-04
I installed 11.04 on 3 machines at work and three machines at home. They all work fine most of the time and my family adapted to the change pretty quickly. changing the UNITY options using ccsm -c UNITY made a big difference, particularly minimizing the icons to their smallest value (32 pixels), never hiding the panel and making the top panel transparent.

Compiz does crash occasionally which is a pain. Matlab does not work smoothly (Compiz issue?) and gimp causes problems as well. I update and upgrade everyday, and problems disappear steadily, as expected.
It is all good fun.

---

