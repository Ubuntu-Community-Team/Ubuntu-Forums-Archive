---
title: "Which laptop is more compatible with Ubuntu, HP or Toshiba?"
date: 2008-05-18
forum: The Cafe
---

### Post by egor08 on 2008-05-18
Hi,

My laptop has died this morning :(, and I urgently need a
replacement. Local store carries two computers that look 
decent and within my budget. They are Toshiba Satellite 
(model: A305-S6825) and HP Pavilion (model: dv2740se).

I have found some of their specs:

(for Toshiba)
[http://www.bestbuy.com/site/olspage.jsp?skuId=8770555&productCategoryId=abcat0502003&type=product&tab=2&id=1203815723003#productdetail](http://www.bestbuy.com/site/olspage.jsp?skuId=8770555&productCategoryId=abcat0502003&type=product&tab=2&id=1203815723003#productdetail)

(for HP)
[http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=KC448UA%23ABA&tab=accessories&aoid=5504&lang=en&cc=us](http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=KC448UA%23ABA&tab=accessories&aoid=5504&lang=en&cc=us)

However, these specs seem to be too vague to determine whether
I will be able to run Ubuntu and use wireless.

I was wandering if someone has experience with either
one of these laptops. Also, which laptop would you choose?

Any help or suggestion will be much appreciated!:)

---

### Post by jpeddicord on 2008-05-18
I haven't had good experiences with either, but if I had to choose, it would be the HP. Some Toshiba's are known to have weird BIOS problems that prevent Linux from booting. Not to say Ubuntu won't work on a Toshiba, but they have their quirks. HPs have some problems as well, but I haven't had much trouble with Ubuntu on them. Not to mention HP supports Linux quite a bit more than Toshiba (re: HPLIP).

---

### Post by fmartinez on 2008-05-18
i have a toshiba satellite a215 4747
with Atheros wireless chip
ATI Graphics
2GB 
Vista Prem./Ubuntu Hardy (Dual Boot)
Athlon 64 dual core
Everything worked out of the box after i upgraded to hardy. The only was i needed to install ndiswrapper for the wireless chip, but other than that everything was good to go. 
I have an HP Pavillion desktop Elite Quadcore, and the everything from the wireless to the nvidia card worked out of the box, with the exception of the gigabit network card. Everytime my pc would go to sleep it would disable the card and i wouldnt have network access. I just installed another card and off we go. 

So i've actually had pretty good experiences with brand!

---

### Post by cardinals_fan on 2008-05-18
I prefer Toshibas, but not because of compatibility.  They just seem better made.

HP keyboards are trash.

---

### Post by HalPomeranz on 2008-05-18
I find the write-ups at [**Tuxmobil.org**]("http://tuxmobil.org/mylaptops.html") (or use these specific links for the [**HP**]("http://tuxmobil.org/hp.html") and/or [**Toshiba**]("http://tuxmobil.org/toshiba.html") write-ups) to be useful when I'm trying to choose a new laptop.  I read the experiences of other people to get a sense of how difficult it's going to be to install Linux on a particular vendor's laptop.

---

### Post by Matthew Wiebelhaus on 2008-05-18
Hate Toshiba. PERIOD.

Had a nice HP laptop and I mean nice once and it was cheap. Though the wireless card was bad so I returned it and bought a Dell turned out it was a bad router and I was stuck with a dell and It didnt have a good video card. My neighbors had a Toshiba and it was worthless pile of, well you get it. Go with HP.

---

### Post by FuturePilot on 2008-05-18
I have an HP dv6500t. I got it when Feisty was out and it had a lot of problems as would be expected with cutting edge hardware and any OS. However, a good majority of those were fixed with Gutsy, and even more were fixed with Hardy. Right now I have almost no problems with it aside from some flaky wireless, but that's not specific to any brand of laptop, rather to the Intel wireless cards since they switched to the iwl driver. It's caused some problems for Intel wireless users. Overall though I've had a great experience with this laptop.

Some specs
Intel Centrino Duo
Nvidia 8400M GS
2GB RAM
Intel Pro 3945ABG wireless

---

### Post by SunnyRabbiera on 2008-05-18
Well HP is probably going to be the more compatible, but the toshiba is probably going to be more reliable.
If you are worried about compatibility, you can try to get a dell.

---

### Post by roderick on 2008-05-18
I don't think anyone actually looked at the system specs.. closely. 

After reading, I think the toshiba would be better. It's intel chipset with intel graphcs. Both are very well supported.

The earlier comment about HP supporting Linux better is really only true for their Printers (the HPLIP is the printer driver system). As far as laptops go, I wouldn't say they are any more or less supported. THe HP is an AMD 64 - and 64 bit is a little more of a headache to get running 100%. 

Go with the Toshiba.

---

### Post by jpeddicord on 2008-05-18
> **roderick said:**
> The earlier comment about HP supporting Linux better is really only true for their Printers (the HPLIP is the printer driver system). As far as laptops go, I wouldn't say they are any more or less supported. THe HP is an AMD 64 - and 64 bit is a little more of a headache to get running 100%.

My point was HP realizes Linux *exists*. ;)

Also, the fact that the HP is an AMD 64 is irrelevant - all 64-bit processors can run in a 32-bit mode if the OS is 32-bit. I have a Core 2 Duo - a 64-bit processor - and I'm using the 32-bit version of Ubuntu. (*ducks to avoid bullets - I'll be back on x86_64 soon)

---

### Post by FuturePilot on 2008-05-18
> **roderick said:**
> I don't think anyone actually looked at the system specs.. closely. 

After reading, I think the toshiba would be better. It's intel chipset with intel graphcs. Both are very well supported.

The earlier comment about HP supporting Linux better is really only true for their Printers (the HPLIP is the printer driver system). As far as laptops go, I wouldn't say they are any more or less supported. THe HP is an AMD 64 - and 64 bit is a little more of a headache to get running 100%. 

Go with the Toshiba.

You can install a 32bit OS on a 64bit arch. 
I wouldn't say that compatibility is only true with their printers. I also have an HP PC and Ubuntu runs like a charm on it.

---

### Post by AndrewTheArt on 2008-05-18
I have a Toshiba A215-4767, works fine (had to set up wireless manually though)

The Toshiba laptop you posted a link to actually has wireless drivers built FOR Linux!!!! That's just rare.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng)

Even if those don't work, then using ndiswrapper you can use the windows drivers on the website.

Toshiba will work wonderfully - as noted earlier, the graphics are natively/well supported and the wireless is natively supported. Better than most people can say.

---

### Post by FuturePilot on 2008-05-18
> **AndrewTheArt said:**
> I have a Toshiba A215-4767, works fine (had to set up wireless manually though)

The Toshiba laptop you posted a link to actually has wireless drivers built FOR Linux!!!! That's just rare.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng)

Even if those don't work, then using ndiswrapper you can use the windows drivers on the website.

Toshiba will work wonderfully - as noted earlier, the graphics are natively/well supported and the wireless is natively supported. Better than most people can say.

Those Intel drivers used to be included in the linux-restricted-modules in Ubuntu. However ipw is no longer developed. The development has moved to iwl which is now included in the kernel.

---

### Post by egor08 on 2008-05-18
> **roderick said:**
> I don't think anyone actually looked at the system specs.. closely. 

After reading, I think the toshiba would be better. It's intel chipset with intel graphcs. Both are very well supported.

The earlier comment about HP supporting Linux better is really only true for their Printers (the HPLIP is the printer driver system). As far as laptops go, I wouldn't say they are any more or less supported. THe HP is an AMD 64 - and 64 bit is a little more of a headache to get running 100%. 

Go with the Toshiba.
Glad to hear that. If I will
not see any other arguments,
I will buy the Toshiba first 
thing in the morning.

Thank you!

---

### Post by egor08 on 2008-05-18
> **AndrewTheArt said:**
> I have a Toshiba A215-4767, works fine (had to set up wireless manually though)

The Toshiba laptop you posted a link to actually has wireless drivers built FOR Linux!!!! That's just rare.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng)

Even if those don't work, then using ndiswrapper you can use the windows drivers on the website.

Toshiba will work wonderfully - as noted earlier, the graphics are natively/well supported and the wireless is natively supported. Better than most people can say.
Cool! I really hope to avoid ndiswrapper!

---

### Post by egor08 on 2008-05-18
> **FuturePilot said:**
> Those Intel drivers used to be included in the linux-restricted-modules in Ubuntu. However ipw is no longer developed. The development has moved to iwl which is now included in the kernel.
But I will still be able to use that driver, right?

---

### Post by SomeGuyDude on 2008-05-18
My HP dv6000 worked seamlessly with Gutsy out of the box. I needed, no joke, zero fixes to get anything working. The only thing was the webcam with Youtube, but that's all. Hardy, same deal except there's some issues with my quickplay buttons and the wireless LED. everything else is flawless.

---

### Post by andlinux21 on 2008-05-18
I am on a Toshiba Satellite 1410-S173 and I have a DLink AirPlus DWL-G650 card.  Everything worked out of the box I didnt have to do anything extra with Hardy.  I have never had a HP Laptop but the desktops I used I would touch again. :lolflag:

---

### Post by FuturePilot on 2008-05-18
> **egor08 said:**
> But I will still be able to use that driver, right?

If you really wanted to I'm sure you could. But if it works out of the box I don't see any advantage to going through the trouble to install them since you would probably have to blacklist the iwl driver and probably do a number of other things as well.

> **SomeGuyDude said:**
>  Hardy, same deal except there's some issues with my quickplay buttons and the wireless LED. everything else is flawless.

Wireless LED look here
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

---

### Post by roderick on 2008-05-19
> **jacobmp92 said:**
> My point was HP realizes Linux *exists*. ;)

Also, the fact that the HP is an AMD 64 is irrelevant - all 64-bit processors can run in a 32-bit mode if the OS is 32-bit. I have a Core 2 Duo - a 64-bit processor - and I'm using the 32-bit version of Ubuntu. (*ducks to avoid bullets - I'll be back on x86_64 soon)

HP Printer division is different than HP Laptop division - I'm sure one doesn't deal direct with the other. In fact, I have heard grumblings about HP's desktop/laptops having issues and people complaining about their lack of support for Linux. THe printer division, on the other hand is quite aware and supports Linux openly. If the Desktop/Laptop guys took their direction from the Printer team, it would be great.

The 64 bit is relevant is the user decided to use the 64 bit CD and not the 32 bit, which I could assume would be a likly possibility.

I still stand by the Intel architecture. If the HP system had the intel architecture, I'd probably have a tougher time deciding though.

---

### Post by roderick on 2008-05-19
Oh, the wireless drivers in the Toshiba are 100% supported natively - in kernel.

Yay.

---

### Post by jsilve1 on 2008-05-20
WARNING WARNING! I tried to install Ubuntu Hardy on that very same laptop and IT DIDN'T EVEN BOOT let alone install!!!

I'm talking, exactly the same laptop, purchased from Best Buy. (It is a pretty nice laptop in a lot of ways)

HOWEVER, Ubuntu 7.10 WORKED FINE!

This is your warning! I don't know if I'm too late or not.

Okay so, what I did was

1) Install Ubuntu 7.10
2) Upgrade to 8.04 using Update Manager
BAM! Killed the laptop. The thing hangs at boot and drops out to "initramfs" prompt (this is the same thing that happens when I tried to load the Live CD)
3) Instead of choosing the Hardy kernel at boot, I scrolled down to the Gutsy kernel. Works great!

So the workaround for me was to make the Gutsy kernel the default in Grub.

The alternative workaround is to not use Hardy (8.04) but stick with Gutsy (7.10) until this is fixed in the kernel. And I think kernel 2.6.25 will fix the problem.

Later...

---

### Post by jsilve1 on 2008-05-20
Oh! One more thing on the Toshiba A305: the MODEM WILL NOT WORK WITH LINUX. If you need a modem, you need some sort of external or PCMCIA solution.

Oh, and also, the PCMCIA slot on that laptop is, in fact, an "ExpressCard" slot. There aren't any Expresscard modems that I could find. So, to get a modem working with that laptop, the only solution I had in mind was:

1) get an externmal serial modem
2) get an expresscard Serial port card

We're talking, like, another hundred bucks. Sheesh. For my money, I'd go with a Dell that has Ubuntu Hardy preinstalled at that point. Or

[http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php)
[http://system76.com/](http://system76.com/)

Alrighty. Later...

---

### Post by jsilve1 on 2008-05-20
Oh, and finally, do this: Bring an Ubuntu CD (or CDs) to the store with you and see if the laptop will boot with the Live CD.

And if those mutha-effers at Best Buy don't let you try out the Live CD then, IMO, that is reason enough not to shop at Best Buy. (I personally would never buy a laptop at BB -- and mostly just because they also sell washing machines, if you get my point -- but that's just me).

Later...

---

### Post by bigbrovar on 2008-05-20
Has a member of an Ubuntu loco in my country i get to install Ubuntu a lot for new users .. and from experience HP is by far more linux friendly compared to a Toshiba .. am yet to get a "100% everything just works " experience with Toshiba .. the closest i got was when a roommates Toshiba.. but then the multimedia  keys didn't work .. i installed hardy on an a new hp dv6000 and i was surprised and even envious when everything justed worked .. without an extra tweak ... i was blown away .. web cam, the touch sensitive multimedia control keys, volume control, brightness, compiz .. everything .. i almost traded my sony vaio with Money for the system but he wouldnt have any of it :(

---

### Post by madjr on 2008-05-20
**toshiba** = **miscrosoft**

they're allies to the death

not that you can't get linux to work on it, but toshiba is the biggest manufacturer that simply doesn't care about linux.

they might even be anti-linux

go with hp (not all models are compatible) or get a Dell

---

### Post by sowelie on 2008-05-20
I didn't read the whole post. But my HP DV6355 is a piece of junk.  It runs vista poorly (which is what it came with), not that anything runs vista well.  Ubuntu runs much better on it, but even still it has a lot of issues.  I would recommend Toshiba for purely for the reason that my HP laptop sucks.

---

### Post by Fedz on 2008-05-20
I have a HP lappy with wireless ...etc - it came with XP on it but, formatted installed Ubuntu/8.04.

Works like a dream straight out of the box, not one problem :)

I understand HP pro-actively recognise Linux/Ubuntu ;)

Good luck and keep us informed of which you choose and how it goes :D

---

### Post by egor08 on 2008-05-21
Thank you very much for all your help! I have decided to go with Toshiba
(perhaps if I would see the later posts in time, I would buy HP). 

At first, I was really disappointed, since the Live CD would not boot :shock:.
Thankfully, I was not the only Ubuntu user to purchase Toshiba. I found a
solution to my problem in
[http://ubuntuforums.org/showthread.php?t=793195&highlight=A305&page=2](http://ubuntuforums.org/showthread.php?t=793195&highlight=A305&page=2).
It turns out that there is a problem with the LAN drivers. Everything
worked (except build in web camera and, of course, LAN) after I have
disabled it in BIOS. Since I am using wireless to connect to the internet, 
I doubt that I will ever need the LAN card. So, I think that I will probably
keep this laptop.

Again, thank you for all your help guys! This is my first thread, and I have
to admit that I did not suspect that I will get so much useful information
:guitar:

---

### Post by meborc on 2008-05-21
(edit: this is what i get for typing too slow :) i guess you have already made up your mind)

the toshiba you linked has intel video and intel wireless... so there should be no problems

the hp has nvidia video but no wireless card specified... so if you get broadcom or smth like that you should be aware it might not work out of the box

i have broadcom card and i have to use ndiswrapper + a special script to get it running

my guess is to go to the store and ask for the list of components for both these computers and then search the forums to see if anyone have had any problems with them which were not resolved

---

### Post by billgoldberg on 2008-05-21
> **egor08 said:**
> Hi,

My laptop has died this morning :(, and I urgently need a
replacement. Local store carries two computers that look 
decent and within my budget. They are Toshiba Satellite 
(model: A305-S6825) and HP Pavilion (model: dv2740se).

I have found some of their specs:

(for Toshiba)
[http://www.bestbuy.com/site/olspage.jsp?skuId=8770555&productCategoryId=abcat0502003&type=product&tab=2&id=1203815723003#productdetail](http://www.bestbuy.com/site/olspage.jsp?skuId=8770555&productCategoryId=abcat0502003&type=product&tab=2&id=1203815723003#productdetail)

(for HP)
[http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=KC448UA%23ABA&tab=accessories&aoid=5504&lang=en&cc=us](http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=KC448UA%23ABA&tab=accessories&aoid=5504&lang=en&cc=us)

However, these specs seem to be too vague to determine whether
I will be able to run Ubuntu and use wireless.

I was wandering if someone has experience with either
one of these laptops. Also, which laptop would you choose?

Any help or suggestion will be much appreciated!:)

Just mentioning my hp pavilion dv4000 worked out of the box, including wireless.

---

### Post by Seti on 2008-05-21
Try them both out. 
I've personally had very good experiences with linux on Toshiba laptops. The one and only time I tried to run it on an HP Pavillion however...things didn't work so well, ie, X failed to start, etc.

---

### Post by eentonig on 2008-05-21
Haven't read through the entire thread. But I recently bought an HP Pavillion DV9xxxEB (sorry, the correct number escapes me). Everything was recognized at install.

- Built in camera
- GPU (allthough it asked me to install the restricted drivers)
- WLAN, LAN
- etc, etc.

Suspend works out of the box (haven't tried hibernation yet)

---

### Post by toupeiro on 2008-05-21
> **eentonig said:**
> Haven't read through the entire thread. But I recently bought an HP Pavillion DV9xxxEB (sorry, the correct number escapes me). Everything was recognized at install.

- Built in camera
- GPU (allthough it asked me to install the restricted drivers)
- WLAN, LAN
- etc, etc.

Suspend works out of the box (haven't tried hibernation yet)


I use an HP 8710w and everything works flawlessly, it even detected and configured the built-in bluetooth and LCARS style volume controls.

I have not owned a Toshiba for a few years, but the last modern one I owned was a Tecra A4 from about 2005, but I was not overly impressed with it.  It may have run linux OK, but I did not feel like it was very structurally sound.  It felt very flimsy compared to an HP or IBM.

I do have Xubuntu running on my [Toshiba Libretto]("http://content.answers.com/main/content/wp/en/thumb/e/e0/180px-ToshibaLibretto70ct.jpg") :)

---

### Post by james.faction on 2008-05-22
HP USES LINUX as boot CD that comes with most of their servers now to set up raid and other hardware configuration. You can then insert your OS CD with this running and install whatever - Windows, Linux etc. So it stands to reason their Linux support is very good.

Toshiba... well yeah my 3-year-old Toshiba Satellite M70 is what I'm running Hardy on now, everything works fine except the sound. :( the sound just skips/loops and tends to crash whatever is playing the sound. I've spent a couple nights now trying to get it to fricken work!

---

### Post by zolo on 2008-07-26
I installed Ubuntu 8.04 on a Toshiba A305-6837. So far it is the only distro that will install. Dream Linux runs but hangs, and locks up trying to upgrade. Mepis loaded the live CD, but I did not try to install it.

---

### Post by LookTJ on 2008-07-26
take a look at [www.pricegrabber.com](www.pricegrabber.com) and set filters and price range before buying either.

---

