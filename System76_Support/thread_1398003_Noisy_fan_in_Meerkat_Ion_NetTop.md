---
title: "Noisy fan in Meerkat Ion NetTop"
date: 2010-02-03
forum: System76 Support
---

### Post by pureblood on 2010-02-03
I just got today my Meerkat Ion NetTop. This little machine is great, I am impressed how easy was to setup Ubuntu on it. Everything works flawlessly. The only nuance I have found was that the machine is incapable of booting from a USB stick, which could be extremely annoying if you got the version without the CD, given that the hard drive is a real pain to take out. Hopefully I will not have to reinstall the system that often, if ever.

That aside, I find the fan noise really annoying, especially because it is always on, not just when the computer is doing something. I have seen before Ion NetTops with no moving parts. Why is there a fan in this one? I don't believe there is much difference between Ion NetTops with the Atom 330 processor. So, what I am wondering here is, would it be unsafe to remove the fan? Has anybody tried this and had any problems?

---

### Post by thomasaaron on 2010-02-04
> The only nuance I have found was that the machine is incapable of booting from a USB stick, 

It will boot from a USB stick. Are you sure your USB stick is actually bootable? Have you tried it on another machine? Try pressing F10, F11, or F12 (don't remember which one off the top of my head) when you're booting. That *should* give you list of available bootable devices, including your USB stick.

> Why is there a fan in this one? 

It is necessary to keep the nVidia ION gpu cool.

> would it be unsafe to remove the fan?
Yes.

---

### Post by pureblood on 2010-02-04
I actually ended up installing the system booting the usb stick from another computer, so definitely the usb stick is bootable. Maybe it matters which usb port the usb stick is plugged to? I will give it another try tomorrow and let you know.

Concerning the fan, I find it absurd and obnoxious that it has to be on so noisy all the time. This is a deal breaker. Both gpu and cpu seem to run at 42 celsius, so the fan is being abused. Is the motherboard potentially capable of shutting it down when not necessary? My 6 years old laptop with a 25W amd64 is more silent.

---

### Post by thomasaaron on 2010-02-04
> Is the motherboard potentially capable of shutting it down when not necessary?

I think so. However, for whatever reason, the motherboard manufacturer has set the trigger temperature pretty low for the the hardware.

The fan on our shop ION runs a lot too.

Honestly, we've never had anyone else complain about it.

---

### Post by pureblood on 2010-02-04
By the way, I installed Ubuntu Karmic on the Meerkat Ion. I had my own hard drive, so I did not used the shop installation of Ubuntu. Then I also patched and installed the coretemp module, since the one shipped with kernel 2.6.31 is incapable of reading the CPU temperature sensors. Now I get that the temperature of the CPU and GPU are always around 42 degree Celsius, which is the same as me with a high fever (95 seems to be the threshold for the product).

I really hope there is a solution for this. In the directories /proc/acpi/thermal_zone/ and /proc/acpi/fan there is nothing, which means that with the current drivers there is no space for control of the fan. Although that does not mean that the motherboard is not capable. Is the situation with Windows any different?

But I am still a bit confused here. When I saw this review:
[http://baablogic.net/drupal/node/2](http://baablogic.net/drupal/node/2)
I could not see any fan inside the product and, if I am correct assuming that the board is a Zotac Ion D series (I don't have the product in front of me now), then as it says on this webpage:
[http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=175&category_id=15&option=com_virtuemart&Itemid=1](http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=175&category_id=15&option=com_virtuemart&Itemid=1)
then the cooling is passive with a "Optional Low-Noise Fan".

What you have put in the board is far from low-noise. I feel betrayed. If there is no solution to this, what you are offering is at best misleading.

---

### Post by thomasaaron on 2010-02-04
> Then I also patched and installed the coretemp module, since the one shipped with kernel 2.6.31 is incapable of reading the CPU temperature sensors.

Did the fan run all the time before you did this?

> Is the situation with Windows any different?

We don't test with Windows, so I'm not sure.

> I am correct assuming that the board is a Zotac Ion D series

No. It has since changed to a G-series.

> What you have put in the board is far from low-noise. I feel betrayed.

Betrayal? We offer a 30 day satisfaction guarantee if the machine doesn't meet your needs or expectations. Of course, I'd like to avoid that if there is a technical fix for your complaint, but nobody had done you wrong or betrayed you.

> If there is no solution to this, what you are offering is at best misleading.

There is a difference between low noise and no noise. Honestly, it's difficult for me to gage the noise level you are hearing. I've found that there is a very wide range in people's opinions about what is considered too noisy. Unless you have a defect with your fan that makes it noisier than usual (which of course is possible), we've not received other complaints about this, so I'm wondering if we're entering that subjective territory or dealing with a hardware defect.

---

### Post by pureblood on 2010-02-04
> Did the fan run all the time before you did this?

The fan ran either case all the time. The coretemp module is just to check the temperature sensors.

> There is a difference between low noise and no noise. Honestly, it's difficult for me to gage the noise level you are hearing. I've found that there is a very wide range in people's opinions about what is considered too noisy. Unless you have a defect with your fan that makes it noisier than usual (which of course is possible), we've not received other complaints about this, so I'm wondering if we're entering that subjective territory or dealing with a hardware defect.

Well, of course the noise problem might be subjective. But it is objective that the fan is noisier than the hard drive and way noisier than my 6 year old laptop which had a CPU way more power hungry than what the Ion. However, when did you start selling the G model instead of the D model? What is the difference in between the two?

> We offer a 30 day satisfaction guarantee if the machine doesn't meet your needs or expectations. Of course, I'd like to avoid that if there is a technical fix for your complaint, but nobody had done you wrong or betrayed you.

Well, I might want to take advantage of that. Although I also wish there is a technical fix. After all, it is better to have a fan that you can control than no fan at all. I will check what the motherboard manual says about the fan when I get back home.

---

### Post by thomasaaron on 2010-02-04
I've got a Meerkat ION on my desk now. The fan constantly runs, but... seriously... I can *barely* hear it. And I probably *wouldn't* notice it at all were I not listening for it.

So, unless you are SUPER sensitive to sound, I'd call it a defective fan.

---

### Post by pureblood on 2010-02-04
Well, when I was at work with the Meerkat I could not hear it either. My desktop at work compared is a turbo jet, but it probably consumes constantly more than 150W. In the privacy of my room at home the fan becomes bothering. I mean, the hard drive at least is well hidden, so the noise is attenuated. But the fan is right close to the outside. There is no way I can sleep with that thing on.

I read other threads of people complaining about the fact that there is not a fan speed controller to turn down the rpms, so I don't think this is a defective fan.

---

### Post by thomasaaron on 2010-02-04
OK, then. If it is too noisy for you, please contact me at [email]support@system76.com[/email].

---

### Post by pureblood on 2010-02-04
Actually, now that I am back home, I can see that the motherboard is a Zotac IONITX-F and not G. From the manual, I can see that there are some fan controls that you can access from the BIOS, although I have not tried it yet. Also, I can see from the Zotac website:
[http://www.zotac.com/index.php?option=com_docman&task=doc_details&gid=309&Itemid=100032&lang=nd](http://www.zotac.com/index.php?option=com_docman&task=doc_details&gid=309&Itemid=100032&lang=nd)
that there has been a recent BIOS update, on December, which says:
.Added CMOS CPU Temperature Reading, Smart Fan Control
Did you apply it, or is the shipped BIOS version older than that? I should check myself, but I cannot reboot the machine right now.

So I am not sure, but it seems that there is the possibility to control the fan speed and fix this issue. Right now I am running both processors at 100% power, compressing a movie, and the temperature is still 44 Celsius. I can touch the heat sink and I barely feel anything. So keeping the fan on all the time when idling is indeed a huge bug. I will check the BIOS tomorrow when I am done and investigate some more. The only thing I am worried about is how to update the BIOS, since the update supports only Windows and DOS.

Also, in the manual of the motherboard, it says: "If your system working at a torrid room, you can append a FAN to the heatsink." Well, awesome translation aside, definitely I would not describe my room as torrid.

Although I am a bit disappointed. I have bought this system from System76 thinking that I pay someone else to make sure what I buy is fully compatible with linux to save the time, and then I discover that Ubuntu Karmic does not support the CPU temperature sensors (although it seems that kernel 2.6.32 will by default).

Maybe I want to try to get a quiet fan too, I read in some posts that it helps a lot and it is a really cheap upgrade. If I have any luck I will report back.

Edit: Now that I know that I have a Zotac IONITX-F, I can see from the specifications:
[http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=185&category_id=15&option=com_virtuemart&Itemid=1](http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=185&category_id=15&option=com_virtuemart&Itemid=1)
that actually the fan is indeed optional. The IONITX-G has active cooling because, as you can see from the picture:
[http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=192&category_id=15&option=com_virtuemart&Itemid=1](http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=192&category_id=15&option=com_virtuemart&Itemid=1)
it does not come with a heatsink. So running the IONITX-F without the fan should be as safe as running the IONITX-D which was shipped without the fan.

---

### Post by mr23 on 2010-02-06
Thomas: Are the meerkats shipping with the updated BIOS?

Thomas: Do you have any in stock with the -D or -F ?  I'd also prefer no noise or at least a mb throttled unit.

pureblood: did you get your bios updated, and were you able to control your fan to your satisfaction?

Thanks.

---

### Post by pureblood on 2010-02-07
I actually did a lot of search in the fan issue. I am mainly bothered by the fact that the fan is not like a laptop fan which will turn off while the computer is idling. Although, I have to say that I cannot blame the people at System76 for this, and I will explain why.

The IONITX-F motherboard that I received had the original BIOS. This BIOS is capable of controlling the speed of the fan by choosing among five different speeds. The updated BIOS allows you to choose speed dynamically according to the core temperature. I explained in a different post how to perform the BIOS update. It is actually very easy, I suggest you to use unetbootin to install FreeDOS on a USB stick and then copy the new ROM in the stick. You don't even need to waste a CD that way.

The problem is that the CPU FAN connector has 4 pins, one of which is to control the fan, but the fan has only 3 pins, leaving the control pin out. This might seems like a mistake, but I looked online and I honestly could not find a 60mm x 60mm x 10mm fan with the 4 pin connection. The speed control technology is called Pulse Width Modulated (PWM). Some larger fans might support it, but I am not even sure that a 15mm wide would fit in the case since the heat sink is already pretty tall, so you are pretty much limited on what you can choose. That said, I believe you can still use the computer without the fan. After all, the IONITX-D was shipped without one and it has the exact same heatsink. Although I read that when you use CPU and GPU intensively you do get close to the critical temperatures, so it is possible that Zotac realized later that putting a fan there might actually be a better idea, just to make sure.

I wish that someone will come out with a 60mm x 60mm x 10mm fan that supports PWM. I would buy it immediately. If someone finds where to buy it, please let me know. In the meanwhile I bought a Cooljag Everflow Fan (126010DL) which runs at 3000rpm like the one shipped with the Meerkat Ion but which claims to have a 22.9 dBA sound level. I am not even sure it would make a difference, but I wanted to give it a try. When I get it I will let you know. Something else you can try is to plug the fan to the CHIP FAN connector which runs at 5V instead of 12V to slow down the fan, but you will need an adapter, so I am not sure how to do that. If you have any ideas let me know.

---

### Post by pureblood on 2010-02-08
Actually, [www.frozencup.com](www.frozencup.com) sells some 60mm PWM fans:
[http://www.frozencpu.com/cat/l3/g36/c365/s947/list/p1/Fans-12_Volt_Fans_-_PWM-60mm_x_15mm_PWM_Fans-Page1.html](http://www.frozencpu.com/cat/l3/g36/c365/s947/list/p1/Fans-12_Volt_Fans_-_PWM-60mm_x_15mm_PWM_Fans-Page1.html)
These fans would be indeed controlled dynamically by the BIOS according to the CPU temperature. I am a bit scared though that the 15mm width is too much for the case sold with the Meerkat. Thomas, do you think the 15mm fan would actually fit in the case? The shipped fan is at best 2mm away from the grid and my guess is that it is a 10mm fan.

---

### Post by thomasaaron on 2010-02-09
Yeah, that's going to be about 4mm too thick. The fan that's in there is either a 9.5mm or 10mm fan, and it's practically right against the cover. You definitely couldn't add half-again the width.

---

### Post by thomasaaron on 2010-02-09
OK, here is R&D's response.

They've tested without the fan, and had no overheating issues. However, the GPU will work better when cooler.

So, you're clear to remove the fan. But if you experience shutdowns, you should put it back on.

---

### Post by clem11388 on 2011-01-16
> **pureblood said:**
> I actually ended up installing the system booting the usb stick from another computer, so definitely the usb stick is bootable. Maybe it matters which usb port the usb stick is plugged to? I will give it another try tomorrow and let you know.

Concerning the fan, I find it absurd and obnoxious that it has to be on so noisy all the time. This is a deal breaker. Both gpu and cpu seem to run at 42 celsius, so the fan is being abused. Is the motherboard potentially capable of shutting it down when not necessary? My 6 years old laptop with a 25W amd64 is more silent.

It may be possible to find a new fan for about 10 dollars or less on [www.newegg.com]("http://www.newegg.com") that is specifically made to be quiet. Just need to know what size. Generally any new fan of average quality would be at least as fast as any stock one so shouldn't have any worries there. Just make sure you won't be voiding System76's warranty by switching to another fan, I'd say call them to find out, and while your at is tell them about your fan issue and suggest a certain fan you end up going with and are happy with. Then they would likely make the improvements in future versions. Customer feed back is key in development. :-) Let us know how that turns out for ya.

Also, Does that seems to play 1080p videos well? both streaming from the net and on the Hard drive if by chance you have tried. 

Good luck and way to go in supporting Linux in a more direct hardware way. :-D

---

