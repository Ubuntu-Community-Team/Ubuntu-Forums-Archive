---
title: "Seeking advise for new computer"
date: 2020-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by coley9225 on 2020-07-11
Hello all. I am currently using a Lenovo ideapad 320-15 IAP laptop. It is a bit under powered for my tastes. I would like to find a laptop that is linux friendly and won't bust my budget. I went through hell to  get a linux disttro installed, and still have a hassle to install other linux OSs. For some reason, my computer refuses to let the installer install the grub2 package. I have to install the os without the boot loader, then install boot repair and update grub, all in the live usb, before my first reboot. Doable( obviously ), but a hassle I'd prefer to avoid with a new machine. I've many people on the forums, including some the more experienced folks who have helped me numerous time, speaking of the Lenovo thinkpads.. I looked, and can get one with nice specs for around $700.00 or so, doable even on my budget. If that box is a good choice, I'll stay with Lenovo, but I am open to suggestions. Preferred minimum specs would be (aprox) 2.0 ghz, and 8gb ram, PCIe m.2 ssd would be a nice touch. Any suggestions would be appreciated. Thanks

---

### Post by kc1di on 2020-07-11
I have had good success with refurbished Lenovo laptops from newegg.  Found[ here.]("https://www.newegg.com/p/pl?d=lenovo+refurbished")  
Good luck in your search

---

### Post by crip720 on 2020-07-11
Would check with refurbish also, can get more power for less and seeing they are a couple years old Ubuntu/Linux should have all the drivers for them.  Mine is a Dell precision with I7 with Nivida GPU, 16GBs ram SSD and a 1TB HD about $500.  Works good, only problem was finding right settings in bios to boot install USB.

---

### Post by Tadaen_Sylvermane on 2020-07-11
Dell hasn't let me down for ease of use with Linux. At one point they used to sell some machines with Ubuntu. Don't know if they still do.

---

### Post by crip720 on 2020-07-12
Would check with refurbish also, can get more power for less and seeing they are a couple years old Ubuntu/Linux should have all the drivers for them.  Mine is a Dell precision with I7 with Nivida GPU, 16GBs ram SSD and a 1TB HD about $500.  Works good, only problem was finding right settings in bios to boot install USB.

---

### Post by kc1di on 2020-07-12
> **Tadaen_Sylvermane said:**
> Dell hasn't let me down for ease of use with Linux. At one point they used to sell some machines with Ubuntu. Don't know if they still do.

Yep they still do.  Lenovo just announced a line of their machines that will come with Fedora preinstalled also.  but I've used both Lenovo and Dells with no real problems with Ubuntu and other Distros as well.

---

### Post by maglin2 on 2020-07-12
You could consider something from these folks if you want new and linux pre-installed.
[https://starlabs.systems/pages/laptops?currency=GBP](https://starlabs.systems/pages/laptops?currency=GBP)
I got the MkII version of the 11" machine for my wife to replace her chromebook (which is AUE).
Runs Ubuntu nicely enough - the MkIII should be faster.
Had a battery problem after a couple of months - support was excellent.

---

### Post by mastablasta on 2020-07-12
i just recently went through a laptop hunt. but first thing i noticed is that refurbished ones were not much cheaper than new ones. neither were the 2 year old "outlet" models. we are a strange country.
the following models were interesting to me:

[LIST]
[*]Thinkpad E15 - i5–10210U, 16 GB ram 2666Mhz and 512 GB SSD; no OS installed - 850 EUR. if i read correctly you can add 2 more disk drives - unfortunatelly this was over my budget.
[*]Dell Inspiron 3593 - i5–1035G1, 8GB ram 2666 Mhz (can go up to 16 GB), 512 GB SSD disk and dedicted Nvidia MX230 (2GB); Ubuntu 18.04 preinstalled - 687 EUR - this was a serious contender. particularly as it has ubuntu on it and it was promoted as more durable along with durable hinges. it is also easy to repair or upgrade by user.
[*]HP 255 G7 - Ryzen 5 3500U, 8GB 2400Mhz ram (not user upgradeable, but should be able to go up to 16 GB); 256 GB nvme; FreeDOS installed - 410 EUR - i went with this one (since it was within the budget and after checking out service manual i saw i could add another drive. anyway it has full legacy boot support. by default uefi boot and secure boot were off. the only issue is that it looks like it will benefit a lot from getting 5.6 kernel as i had to use a kernel boot option to boot from battery. later on i saw a version with 512 GB nvme disk and DVD drive that was little over 550 EUR.
[/LIST]

other options i investigated:

[LIST]
[*]i also saw one of the HP pavilions 15 with Ryzen 7 3700U, 512 GB disk and 16 GB ram at 570 EUR. this would also be a good option, had i seen it earlier.
[*]i am unsure if HP pavilion 15 gaming have good support, but here they sell them with no os for about 800 EUR. they come with Ryzen 5 the H series and nvidia GTX1650, lit up keyboard etc.
[*]Phoronix tested Ryzen 5 4000 series on new Lenovos. Cheapest one is less than 600 USD (they don't have them here and new Ryzens have high price 800, 900+ EUR laptops). anyway from tests they leave Intel in the dust - better CPU, better GPU.
[/LIST]
 
note cheaper lenovos (often no OS here) & asus often have soldered RAM, though they might work well with linux (some Asus come with their linux version preloaded). while Acer's are usually not build too well and some also have issue loading Linux on them.

in past we used to have HPs with SUSE linux where everything worked out of the box on most linux distros, but i couldn't find them in my country now.



finally i don't add multiple linux on any of the PC. i use virtualbox for that.

---

### Post by zebra2 on 2020-07-12
I'm writing this post from a 320 15iap. Upgraded to 8gig. It only has one ram slot with nothing soldered onboard. So maxed out on ram. I'm running the Ubuntu 20.10 Dev version with Gnome 3.36 and Wayland.  It is a great machine.  I don't game, but give it a pretty good run otherwise. 

I also have two 110 15isk's. One is upgraded to 12Gig Ram and dual boots Win10 and Ubuntu 20.10 Gnome Wayland. Ubuntu and Win10 both boot in Legacy mode, with fast boot disabled.  It is a very good machine in Ubuntu and Windows both. I installed the Ram to get the best Windows 10 performance, it was already ok with Ubuntu.  I don't like Win10 in a VM. My wife uses the other 110 isk and I keep her on LTS systems, currently Ubuntu 20.04 with gnome Wayland.  She is happy with her computer. If I was going to buy another computer right now I would get another Lenovo. But I would definitely check out the memory map before I made my choice. If I needed more performance I would get it from running SATA Chips and Ram upgrades. Incidentally, my 110 15isk runs on 6 watts with power plug and 4 watts on battery. It is always running and is stone cold to the touch. Typical core temp is 35C.   FYI

---

