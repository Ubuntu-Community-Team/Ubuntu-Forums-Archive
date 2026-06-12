---
title: "An Operating System Field Report"
date: 2009-03-03
forum: Testimonials &amp; Experiences
---

### Post by Cruncher on 2009-03-03
Recently, a friend of mine bought three different Laptops that had been scrapped by his company. They had been wiped clean, and so they asked me whether I had a Windoze install. I denied, since I don't keep stuff like that in the house. ...yes, and I want to avoid having to install and maintain it for people I know :D
So what to do? Pay another 300 bucks for three Windoze CDs? Plus Office, plus Virus Scanner, plus any other essential software package, plus...?
Hm. I payed them a visit to look at what we got so far.
Three laptops, and they installed this Use-30-days-for-free-then-pay-up-Windows on two of them. Only problem - those installations didn't know jack about the Laptops - no network, rudimentary graphics, what the heck is WLAN, etc.  
Wait. No network? I checked the device manager. Oh, so many happy yellow questionmarks.
Hm, but how to download network drivers if you don't have any network?
Bummer.  :-k
And the third laptop - well, it didn't even have a physical CD drive. Luckily they bought the docking station to go with it. Except that it didn't have a CD drive, either.... So there was no way we could install *anything* on it - or was there?

So I started writing down obscure hexcodes from the device manager, supposedly identifying ethernet, wlan, and graphics card devices, and started googling for them on another machine, following trails of sparse information, to download possible drivers from insecure websites, to burn them on CDs, to... :roll:
Then it occured to me.
I quickly went to the Xubuntu site, downloaded the disk image, burned it, and booted the first laptop with it.
A full-fledged Desktop with Firefox (yes, unfortunately no Opera here  ) available greeted me. A click on the network manager, entering the WPA2 password, starting Firefox - voila, working WLAN connection.  
Network, graphics, mousepad - all there. It even recognized the fingerprint sensor built into the laptop.
A little icon on the Desktop saying "Install". Clicking on it, you can repartition your disk, keeping the original Windows partition, only reduced in size, just by dragging a marker to determine the relative sizes of the new and old partitions.
And then fire away. While the system was installing, I had full access to the internet and could do other stuff on the machine.

Once finished, I shoved the CD into the next laptop, and continued installing all the essential stuff on the first one: a fully compatible Office suite, Video player with all imaginable codecs, Wine to run Windows programs, Zip, Skype, Java, Brettspielwelt, etc., AIM/ICQ/MSN and whatnot.
And the best part - it's all just a matter of clicking checkmarks in a huge list of available software. No rummaging through the internet, finding the right site, the right version, the right system specifics, downloading, running, rebooting...none of that.
Just click everything together, press Go, and wait for the stuff to be installed.
Any imaginable software package. In one place. For free.

And the third laptop? The one without CD? Well, we [[COLOR="Blue"]copied[/COLOR]](http://unetbootin.sourceforge.net/) the install CD onto an USB stick, jacked it into the machine, turned it on - voila, booting from the stick, installing, ready.

Way to go. 8-)

(wow, reading through this it sounds like a Linux marketing brochure :D But I swear this is exactly what happened.)

Happy computing!
Cruncher

---

### Post by K7522 on 2009-03-03
It's always great to see new life in old hardware, especially when Linux helps to accomplish it. Good read, makes me want to Ubuntufy my grandmother's old slow thing.

---

### Post by mkvnmtr on 2009-03-03
Is not that the way computers are supposed to work?

---

### Post by tgalati4 on 2009-03-03
Excellent story, thanks for sharing.

---

### Post by stchman on 2009-03-03
You do know there is a program called usb-creator to make bootable USB devices from Ubuntu .iso files?  It is installed by default on Intrepid.  You don't need Windows at all.

---

### Post by solwic on 2009-03-03
> **stchman said:**
> You do know there is a program called usb-creator to make bootable USB devices from Ubuntu .iso files?  It is installed by default on Intrepid.  You don't need Windows at all.

And installing via USB rather than CD is about three times faster.  It doesn't just have to be Ubuntu, either.  You can use it to create bootable .iso USB sticks with any .iso file (at least that I've found).  

:)

---

### Post by mdsmedia on 2009-03-03
> **stchman said:**
> You do know there is a program called usb-creator to make bootable USB devices from Ubuntu .iso files?  It is installed by default on Intrepid.  You don't need Windows at all.
 How big a USB drive do I need to install Ubuntu/Xubuntu? I've got a 1GB drive but do I need to get a larger one?

Do I need to set the bios to boot from USB?

---

### Post by solwic on 2009-03-03
> **mdsmedia said:**
> How big a USB drive do I need to install Ubuntu/Xubuntu? I've got a 1GB drive but do I need to get a larger one?

Do I need to set the bios to boot from USB?

I use a Kingston 1GB, and I just press F10 at bootup and it lets me choose the device to boot from.

Your motherboard needs to support the boot-from-USB function, and the key you press could vary, depending on your BIOS.  

Should say when you boot up.

---

### Post by stchman on 2009-03-03
> **mdsmedia said:**
> How big a USB drive do I need to install Ubuntu/Xubuntu? I've got a 1GB drive but do I need to get a larger one?

Do I need to set the bios to boot from USB?

Most Ubuntu .iso files are ~700MB.  I use my Sandisk 1GB for OS install.

---

### Post by stchman on 2009-03-03
> **jrock612 said:**
> And installing via USB rather than CD is about three times faster.  It doesn't just have to be Ubuntu, either.  You can use it to create bootable .iso USB sticks with any .iso file (at least that I've found).  

:)

Agreed on the speed.  

I have found that usb-creator only works with Ubuntu or Linux Mint.  I cannot create a Puppy USB drive.  Puppy is only ~100MB so it loads pretty fast using CD.

---

### Post by mdsmedia on 2009-03-03
> **jrock612 said:**
> I use a Kingston 1GB, and I just press F10 at bootup and it lets me choose the device to boot from.

Your motherboard needs to support the boot-from-USB function, and the key you press could vary, depending on your BIOS.  

Should say when you boot up.
Thanks. That was what I was worried about, whether the machine I want to boot to will support USB boot. I've started to try a few different distros on an older machine. I'm thinking it might be less inclined to accept a boot from USB.

I'll have a look at all my machines and see what's available in BIOS.

jrock, Yep, I know about accessing BIOS. I have been using PCs since PCs were an itch. I guessed that was the case. I just hoped for a different answer. I'm no expert, but I'm not a PC noob either. No disrespect for your response. I appreciate it.

---

### Post by solwic on 2009-03-04
> **mdsmedia said:**
> 
jrock, Yep, I know about accessing BIOS. I have been using PCs since PCs were an itch. I guessed that was the case. I just hoped for a different answer. I'm no expert, but I'm not a PC noob either. No disrespect for your response. I appreciate it.

Well what I was saying is that I don't have to access the BIOS to boot from USB.  When I power up, I can use F2 to enter BIOS, or F10 to enter Boot Menu.  The Boot Menu is just a list of bootable devices attached to the PC, and since my BIOS boots from USB, it lists my external USB HDD and my Kingston flash drive.  Actually entering the BIOS isn't necessary.

And no, I know you're not a PC noob.  :)

Anyway, good luck!

[quote=stchman]I have found that usb-creator only works with Ubuntu or Linux Mint. I cannot create a Puppy USB drive. Puppy is only ~100MB so it loads pretty fast using CD.[/quote]

It works with Kubuntu as well, for me.  I'm going to try to use it to make a Windows boot stick, just for grins.  :)

---

### Post by mdsmedia on 2009-03-07
I'm about to try it with Arch. See how I go. Looks like my desktop might boot from USB. If not, I'll just have to burn a CD.

---

### Post by wolfen69 on 2009-03-07
> **stchman said:**
> I cannot create a Puppy USB drive.

why not? i have 2 pendrives with puppy on them.

---

### Post by mdsmedia on 2009-03-07
> **wolfen69 said:**
> why not? i have 2 pendrives with puppy on them.
Using usb-creator?

---

