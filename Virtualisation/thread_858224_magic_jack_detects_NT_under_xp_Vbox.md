---
title: "magic jack detects NT under xp Vbox"
date: 2008-07-13
forum: Virtualisation
---

### Post by dpit on 2008-07-13
i have been into computers since basic programming, but am fairly new to Linux. i have never posted a question before because reading answers everything, however i have run into something that i cannot find the answer to.
    I have virtualbox installed with xp. i got all usb working with all permissions,(i think). i plug my magic jack into the usb, xp sees  it, but the magic jack cannot install.
    ERROR message:
your current version of windows is not supported. version detected:NT 5.1 build.
     my guess is vbox uses nt drivers for usb support. HAS ANYONE GOT MAGIC JACK TO WORK ON VIRTUAL BOX? IF SO, PLEASE SHARE. thank you.

---

### Post by spandanj on 2008-09-19
I have it working on winxp on virtual box 1.6.


However, I have a major problem. It works all fine upto the point I can hear the dialtone. But, once i dial a number I dont hear anything, no ring, no answer, nothing. just quiet. I know that ppl are receiving  my calls cuz they tell me. however, they can't hear me, nor can i hear them...


so i dont know what the problem is.. I tried transfering to headset/mic/speaker. nothing works.

---

### Post by lyndaj70 on 2008-12-07
I have Magic Jack working in virtualbox under WinXP, but the sound is choppy.  I visited the MJ forums, installed the upgrade, gave the background processes priority, and the sound is still choppy, but it does work..

I would just like to get it to work better :)

Any ideas?

---

### Post by danielhaynes1979 on 2009-01-02
Hey guys and gals,

I have a working Virtualbox XP system. My 3 Mobile Skypephone started working after much travail (the darned thing would not work in linux; it would not recognize the modem and assign it a location). Also, I got itunes up and running with the ipod syncing just fine. I was successful in getting Magicjack installed and running. I am having the same problem as above about no dial tone; just a long beeping sound. I suppose the USB is working correctly. I tried to plug in a headset and mic just to see if anything would go through, but no luck. I can make calls because the dialer seems to go through and time the call, but only the long beep comes through on the phone. Can someone please help? This is the last thing I need to ditch the whole dual booting in XP thing.

Peace,

Daniel

---

### Post by HotShotDJ on 2009-01-02
> **dpit said:**
> ERROR message:
your current version of windows is not supported. version detected:NT 5.1 build.
     my guess is vbox uses nt drivers for usb support. HAS ANYONE GOT MAGIC JACK TO WORK ON VIRTUAL BOX? IF SO, PLEASE SHARE. thank you.I don't know what the problem with MagicJack is, but it is detecting the proper version of Windows.  WindowsXP = NT 5.1 (Windows2000 = NT 5.0).

---

### Post by coskierken on 2009-04-30
Ok, here is what I got.  I have VMware Workstation 6.5(64-bit) on Jaunty 9.04 (64-bit), running 32-bit xp inside and was able to get MJ to work fine.  Read about this in another post. One error message which pops up is that workstation can't use the device until it is released from the host.  I unmounted the MJ device and then still got the error.  I just hit OK on the error window a few times and boom.  I called my buddy's cell in Orlando (fm CA) and he said the voice was clear.  He was trying it in Virtualbox and told him to release the device.  He did and it worked, also, but his voice was choppy.  My systems spec are below and his is an AMD64x2 6000.  Next is loading 64-bit Vista in via Workstation and confirm it will work there.  I see no reason why not. :lolflag:

.....
MSI G45M MB/ Q9550 OC to 3.GHZ for now :)/8G DDR2-1066 / ATI 4650 512MB / 500G WD boot/1 TB Hitachi / AeroCool M40 case(great case!) 550W Tuniq PSU

---

### Post by coskierken on 2009-05-01
I installed Vista 64 via VMware Workstation 6.5 (64bit) on Jaunty 9.04 (64).  Magicjack does not seem to be as good as with the XP 32bit install. Voice sometimes seems choppy.  I will use it over the next day and see how it does.  Vista was a little harder to get the adapter to be recognized, but it was able to see it after a couple of restarts.

It works until MJ gets off their @$$ and writes some Linux drivers.  At least I can have the phone work while I work in Ubuntu.

---

