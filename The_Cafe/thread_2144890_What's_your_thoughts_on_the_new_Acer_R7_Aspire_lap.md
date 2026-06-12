---
title: "What's your thoughts on the new Acer R7 Aspire laptop?"
date: 2013-05-13
forum: The Cafe
---

### Post by irv on 2013-05-13
My old Dell Laptop died so I started looking for a new one. This one jumped out at me but it won't be out until the 17th of this month. [Acer Aspire R7 Video]("http://www.acer.com/aspirer7/en_US/"). I am not sure how well the touch screen will work with Ubuntu. I have a SSD in the old Dell I was thinking about popping into it and trying to run Ubuntu on it. I didn't want to change the drives there are in it with Win8 on them.
A friend gave me a Asus netbook to use until this one comes out.
[ATTACH=CONFIG]242554[/ATTACH]

---

### Post by AllRadioisDead on 2013-05-13
There are videos on Youtube of people trying to use Ubuntu with a touchscreen and they all look really clumsy and frustrated. I would stick with a traditional laptop/ultrabook.

---

### Post by irv on 2013-05-14
I was also looking at the [Dell XPS 13 Ubuntu Laptop]("http://www.dell.com/us/business/p/xps-13-linux/pd?refid=xps-13-linux&baynote_bnrank=0&baynote_irrank=0&~ck=baynoteSearch&isredir=true") but the price is to high. $1549. I know it has the i7 processor, but I think it is priced way to high. I am using a Asus eee right now and I could buy it for $150 from a friend of mine. By the way, thanks for  the input.

---

### Post by AllRadioisDead on 2013-05-14
Check out a Lenovo Thinkpad. They're great laptops and typically play well with Linux.

---

### Post by irv on 2013-05-17
Well, I went and picked up my new Acer R7 today. Best buy got 3 in today, and I got the first one. I made them take it out of the box because I wanted to look at the hing on the monitor. I must say it is well build. I will write more one I have it awhile and check it all out. So far I like it. Not so sure about Windows 8? First time I ever use it.

---

### Post by irv on 2013-05-20
OK, I have been using the R7 for three days now and here is what I found.
First, a little about windows 8. I find it works well with the touch screen but windows is windows. First  it didn't have a driver for my older printer (HP 4050). I had to download the driver and manually install it. They moved things around in windows and I had to look for a lot of stuff, but did find them.
Now lets talk about the hardware and Ubuntu.

First I had to go into the BIOS and change a few things to get it to boot from the USB and to turn off some security settings. I booted into the live OS off the USB, and Ubuntu ran OK except for the wifi network. Ubuntu did not see the wifi card. It is a Broadcom card. I had the same problem with the Broadcom card in my Dell, and I needed to load the drivers to get it to work, but the problem I have with the Acer R7 is it does not have an Ethernet port so I have no way of loading any drivers.

So now I have a question. Is there some hardware that I can get to plug into the USB to get wireless without using the internal Broadcom card?

If I can get the wifi to work, I will install Ubuntu. The live OS running off the USB worked great with the touch screen. As far as I can tell the wifi is the only problem hardware so far.

---

### Post by Inodoro Pereyra on 2013-05-20
> **irv said:**
>  Is there some hardware that I can get to plug into the USB to get wireless without using the internal Broadcom card?.

Yep. A thumb drive.
Use another computer to get the driver, put it in a thumb drive, and...

Or, if you don't want to use your internal wi-fi at all, you can get a USB wi-fi card.

---

### Post by irv on 2013-05-20
I was out checking on USB wireless that would work with Ubuntu. Also there are USB to RJ45 connectors that I could get on the internet to get the drivers I need. I guess I do have some options. I also plan on pulling the bottom of the laptop off to get to the hardware. I have a new SSD I would like to install and I may get more memory.

---

### Post by Inodoro Pereyra on 2013-05-20
I would just get a thumb drive or an external hard drive, (or even an SD card, if you have a reader), and use another computer to download the driver into it. I have done it several times, and don't remember ever having a problem, especiaally with the Broadcom drivers. No sense in buying stuff to use it only once, IMO.

---

### Post by irv on 2013-05-21
This morning I tried something. In the laptop that died I had a new Solid State Drive (SSD) which had Ubuntu 12.10 installed on. What I did was go into the BIOS and set it so I could boot off the USB ports and plugged in the drive. It booted into Ubutnu but I did get some errors because it was set to boot into different hardware (my old Dell). I see where I can boot off a USB with the install of 13.04 and then plug in the SSD from the Dell and install a fresh install of 13..04 on it. I need to wait until I get a USB to RJ45 so I can get on the Internet, then I can install on to the SSD and work on getting the wireless card to work. I also found out that I need to set my BIOS back to get back into Windows 8. 
I was really surprised to see how fast it booted into the external SSD with Ubuntu. less that 45 seconds. It must be because of USB3 and the SSD. It boots faster that Windows 8, and Windows 8 is running off a SSD also.. This is the way I am going to run Ubuntu This way I will not void my warranty. After my warranty runs out I can install it on my system HD.

---

### Post by mips on 2013-05-22
> **irv said:**
> I need to wait until I get a USB to RJ45 so I can get on the Internet, then I can install on to the SSD and work on getting the wireless card to work. I also found out that I need to set my BIOS back to get back into Windows 8. 

Install keryx on windows or linux, point it to the repos and it will download whatever packages + dependencies you need...

[http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx](http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx)

As for your SSDs I would just swap the two and keep the original in a safe place should you ever need it again.

---

### Post by irv on 2013-05-24
Thanks for the link, but I am having some other issues with the R7. Been online with tech support a lot this past week so I am returning the laptop and am going to go with a different one.
The big issue is my wifi card (Broadcom), I don't know the model and the tech wouldn't tell me. If I am within 10' of my router it works but only at about 1/2 speed. If I move 30 to 35' it drops off to just about nothing. The tech had me do many things until late into the night, and nothing worked. He was going to send me a different wifi card, but I will have to take the laptop all apart. (a bunch of screws and take the bottom off). I am not going to mess with it, I am just going to get a different kind. Here is what my wifi reading looked like.
[ATTACH=CONFIG]242978[/ATTACH][ATTACH=CONFIG]242979[/ATTACH][ATTACH=CONFIG]242980[/ATTACH][ATTACH=CONFIG]242981[/ATTACH]
The slow speed is when I move away from the router.
I forgot to say my Internet service is 40 mbps and my wifi on most of my devices run at 20 mbps, so you can see I am about half right next to the router.

---

### Post by irv on 2013-05-26
Okay, I took the R7 back to Best Buy and got a ASUS Q500A Touchscreen Laptop

I just got a brand new ASUS Q500A-BHI7T05 I bought a few hours ago at Best Buy.
This laptop was born in January, 2013 with the following specs:
Intel® 3rd Generation Core™ i7 @ 2.2Ghz with 3.2 Ghz Turbo Boost
6 Mb Level 3 cache on die
8 Gb DDR3 ram
750 Gb HD, 5400 RPM
15.6&#8243; 1920×1080 Multi-touch LED-backlit TFT display
6-cell Li Battery
DVD RW drive
Typical assortment of USB 3.0, Wifi-N, G-bit Ethernet, VGA, HDMI
Windows 8

The reason I got this one was because of this webpage. [http://www.writecircuit.com/2013/04/asus-q500a-touchscreen-laptop-gets-ubuntu-12-10/]("http://www.writecircuit.com/2013/04/asus-q500a-touchscreen-laptop-gets-ubuntu-12-10/")

I am on the road right now so I won't be doing any installs until I got home next week. I will try to keep all posted on this. I will have to start a new thread because this is no longer a Acer R7.  If a mod reads this I would think this thread could be closed.

---

### Post by theprateik on 2013-05-28
I bought acer aspire r7 few days ago..... and I think I like it. I wanted it to have dual booting with ubuntu. And yes, ubuntu gave me a headache with wifi.... I was installing ubuntu 12.10.... with 12.10, I could not even open a folder with touch. That was pain. Then I tried ubuntu 13.04. Surprisingly, the wifi was working well out of the box. The wifi is still a bit slower than what it had to be but it works lot better with 13.04. 
Also with 13.04, I can open folders by double tapping and it seems better than 12.10. Still it is not fully optimized for touch. Now and then the touch gets unstable. 
About the wifi, it runs well in windows. I have 50mbps internet and it runs at same speed like my other computers....
I think I will be happy with r7.

---

### Post by theprateik on 2013-05-28
O yeah.... forgot to say that I love the display of this laptop.... Ubuntu looks great with this display....

---

### Post by irv on 2013-05-28
I am glad you have the R7 working, but with the one I bought I really think the wifi card was bad. It wouldn't even work right with Windows 8. I played around with the Asus Q500A today and got it to run the live OS of Ubuntu 13.04 and it found the wifi and the touch screen worked with it. I am still on the road, so I plan to play around with it when I get home. By the way, the Asus has the same touch screen as the R7, same 1920 X 1080. The Asus has the i7 CPU where the R7 has the i5. It also had 2 gig more RAM and a 750 gig HD, where the R7 had a 500 gig HD. Both had a combo drive (a bootable SSD). I do have to say I did like the new hing design on the R7. It has about the same battery life even though the R7 had a 4 cell and the Asus has a 6 cell. The R7 has the newer style battery, but the Asus is much easier to change. I want to see if I can get a 9 cell for it. I don't know if they make one or not.

---

### Post by irv on 2013-06-06
I thought I would update this thread. I ran into a problem with the wifi card and after spending time with Acer's tech support and getting nowhere I took the laptop back and exchanged it for a Asus Q500A which I like much better. Faster processor speed (i7 not the i5), more memory (8 gig not 6), more storage, (750 gig not 500) and $105 cheaper.
 I have another thread started on the Q500A so here is the link. [Q500A link.]("http://ubuntuforums.org/showthread.php?t=2149658")

---

