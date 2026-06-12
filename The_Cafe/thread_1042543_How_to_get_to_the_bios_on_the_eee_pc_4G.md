---
title: "How to get to the bios on the eee pc 4G ?"
date: 2009-01-17
forum: The Cafe
---

### Post by I-75 on 2009-01-17
How to get to the bios on the eee pc 4G ? 

 Please tell me what am I missing here. I press escape ESC and hold it down while the PC is powering up and it is supposed to get me to the bios. Except that method does not work...it just goes to the desktop. Any ideas?

(I am trying to install Ubuntu EEE PC, and in every forum I checked, to reach the bios so one can select to install it from the USB , all they have to do is to press ESC while powering up the unit to reach the bios ...except I can't)

I checked the search feature here on the forums and didn't see anything posted on problems trying to reach the bios.


Thanks

---

### Post by utnubuuser on 2009-01-17
Guess you tried some of  the F? keys?

or combination alt or ctrl + esc, etc, etc.

All I know about eeePC is that the FSF's free BIOS can be used on it.

---

### Post by I-75 on 2009-01-17
> **utnubuuser said:**
> Guess you tried some of  the F? keys?

or combination alt or ctrl + esc, etc, etc.

All I know about eeePC is that the FSF's free BIOS can be used on it.

I am looking at the other forums, they keep saying use escape. That must be for a different model. Trying F Keys is my next step.


The problem is with the Xandros, it doesn't display how to enter bios as it is booting. I'm going going to try to install via USB "Easy Peasy for Netbooks" (Ubuntu 8.10 for the EEE PC), its a new distro..about a week or two old. Kinda of surprised that I see no mention of it here on the Ubuntu Forums.

---

### Post by blackened on 2009-01-17
> **I-75 said:**
> I am looking at the other forums, they keep saying use escape. That must be for a different model. Trying F Keys is my next step.


The problem is with the Xandros, it doesn't display how to enter bios as it is booting. I'm going going to try to install via USB "Easy Peasy for Netbooks" (Ubuntu 8.10 for the EEE PC), its a new distro..about a week or two old. Kinda of surprised that I see no mention of it here on the Ubuntu Forums.

Don't hold Esc. Press it rapidly from the time you press the power button and it should get you there.

Having tried both, I prefer [eeebuntu]("http://eeebuntu.org") over Ubuntu EEE. Just make sure you install maximus, as I don't think eeebuntu comes with it installed by default, which is a pain.

---

### Post by I-75 on 2009-01-17
> **blackened said:**
> Don't hold Esc. Press it rapidly from the time you press the power button and it should get you there.

Having tried both, I prefer [eeebuntu]("http://eeebuntu.org") over Ubuntu EEE. Just make sure you install maximus, as I don't think eeebuntu comes with it installed by default, which is a pain.

 What is the difference between eeebuntu and easy peasy for netbooks? The GUI almost looks the same. One of my reasons for switching from Xandros was the problems it would have trying to connect to the internet. It would connect then disconnect then connect..finally. The Xandros GUI has some issues with it, I prefer Ubuntu anyway over it.

I found the F2 key was the way to the bios, normally that is the case with most PC's ...but the ESC recommendation on nearly every forum and site threw me for a loop.

---

### Post by myusername on 2009-01-17
eeebuntu comes in three different types. full - which is pretty much a normal ubuntu install with a different theme. netbook - which is the same as full but with the net book launcher (same as easy peasy (aka ubuntu-eee) but with a different theme) and minimum - which is just a normal install but without the extra crap  apps (games etc.)
hit escape repeatedly to get into the boot menu. hit F2 repeatedly to get into the actual bios

edit: go with eeebuntu. its pretty much the same but it already has the array kernel source (optimized kernel for eeepc) already in it. which will save time updating your kernel

---

### Post by I-75 on 2009-01-18
Its a done deal, I installed "Easy Peasy for Netbooks". If anyone is interested, this works "out of the box". "Easy Peasy for netbooks"  is Ubuntu 8.10 rebranded.

Compared to Xandros , this is better as the wireless doesn't hiccup. The wireless works great as well as it does on my other full fledged laptopn with Ubuntu. This means that the wireless is instantly picked up and stays on.

 Also I noticed that I have more hard drive space. Th EEE PC 4 G with Xandros only had about 400 MB left for space. With this it is like a bit over a Gig left. 

I used Unetbootin for this. For those that haven't done this. You download Unetbootin to your Ubuntu computer. Then either you download the OS to the computer...or...have the ISO (that you want to install on the flash drive) on the computer ready . If you have the ISO already the only thing you do is to download Unetbootin. 

 Format your flash drive to FAT 32 (you can use a Windows machine for that part), then plug the flash drive it into your Ubuntu computer, open up Unetbootin then select the OS you want to install. Look down further and then you see where you can select the ISO...click that and look for the ISO that you want to install on your EEE PC.

 Once you do that, further on the bottom you can select HARD DRIVE or USB. You want to select USB. Then hit start and Unetbootin will copy the entire OS to your flash drive.


Now to the EEE PC

After that is done, now time for the "fun". This is where I had problems. Pressing ESC did not work for me to get to the boot screen or to the bios. I needed to get there in order to be able to boot from the USB flash drive instead of the internal 4GB SSD.

F2 will get you to the BIOS, and you want to make sure the bios sees your Flash drive and activates it (be able to boot from) and you have to change the boot order to the USB first and then the 4 GB SSD. 

From there, just follow the steps that it would take to to install Ubuntu normally. It is straight forward from there.

Some additions...

Activate the wireless as soon as the OS loads (you can run it live off the flash if you wanted to). If you don't want to do this then at least hook it up to a ethernet LAN while installing the OS. 

You want to do this in  case there are some updates needed while installing. You basically want to make sure everything works and installs without a hitch. (So if you have a password for your wireless type it in and activate it before installing...I am sure it isn't that critical...but for me I always made sure the computer was connected to the net when installing any OS).

Final

 The install will take about 20 to 25 minutes. After the install is done it will ask you to (remove the "disc") and restart. (Remember that the OS thinks you installed it by a disc and not but a flash drive...no big deal).

Glitches

So once you restart without the flash drive and everything goes well, if you have encrypted wireless..you have to enter it again. (The reason is because when you entered it earlier...you were running LIVE...and it didn't save the settings..no big deal...re-enter it and it should be there anytime when you start it up again since it is now being written to the SSD.)

As with other Ubuntu installs, there is a password required to log in and another to access the wireless. On my other two laptops with Ubuntu, I was able to pair this down to require only a log in for the wireless only. I have not found how to do this yet on the "EPFN (Easy Peasy For Netbooks").

Even though this is "rebranded". Once you install it and get it running..you will see the familiar Ubuntu "splash" screen...so is isn't completely rebranded. I guess a good example of a rebrand is Linux Mint.

More on this later...

---

### Post by myusername on 2009-01-18
the reason you have more space is because you deleted the hidden drive. its there so your computer bios will already be loaded and it can boot up quicker. you can remake it if you want (it will only take up 16mb but for some reason asus made it bigger). i made a how to but for some reason they wouldn't post it into the tutorial section. i posted it on another forum though so i can post a link if you want.

---

### Post by I-75 on 2009-01-18
> **myusername said:**
> the reason you have more space is because you deleted the hidden drive. its there so your computer bios will already be loaded and it can boot up quicker. you can remake it if you want (it will only take up 16mb but for some reason asus made it bigger). i made a how to but for some reason they wouldn't post it into the tutorial section. i posted it on another forum though so i can post a link if you want.


 Just a update, Office Depot has on sale this week a 8 GB SDHC Card for $19. It installed flawlessly on the EEE PC SD slot and now I have another 8 GB space.

---

### Post by blackened on 2009-01-19
> **I-75 said:**
> Just a update, Office Depot has on sale this week a 8 GB SDHC Card for $19. It installed flawlessly on the EEE PC SD slot and now I have another 8 GB space.

Yeah I saw that in the paper today. I'm gonna splurge and get a 32 or 64Gb Runcore drive instead though.

---

### Post by I-75 on 2009-01-19
> **blackened said:**
> Yeah I saw that in the paper today. I'm gonna splurge and get a 32 or 64Gb Runcore drive instead though.

 A quick Google inquiry says 32 GB SSD's are selling from $97 at B & H Photo to as much as $318 at EWorld Sale. 

 EBay has a 32GB Runcore selling around $119 including shipping. Yet a 16 GB is selling for $148. Hmm.

---

### Post by blackened on 2009-01-19
$119 is the going rate for the 32Gb right now from almost anywhere you check. If you look at some of the benchmarks for them you'll see why.

---

### Post by I-75 on 2009-01-19
> **blackened said:**
> $119 is the going rate for the 32Gb right now from almost anywhere you check. If you look at some of the benchmarks for them you'll see why.

Thanks for the info, I haven't had much interest in SSD drives until now.

---

