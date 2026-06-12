---
title: "Samsung PC Studio: maximised"
date: 2009-11-05
forum: Wine
---

### Post by Ampi on 2009-11-05
I have a netbook with UNR 9.10 which works perfectly well. 

Because I have a samsung phone I would like to install the PC Samsung Studio. The installing went just fine through wine, but the interface maximises automatically and entirely. 
So it looks like the fullscreen (F11) but without the possibility of getting rid of it. 

When I press ALT+F2 I get the window with "run command" and I finally get to see my start-menu-button, time, date etc, but still no possibility to close the PC studio. This makes using it very very annoying.
Does somebody have any idea how to solve this?

I'm guessing this has to do with the maximising software of UNR. I'll try it later on my Desktop Ubuntu in the hope it'll work there. So maybe it's a bug and I'll report it. But I've never done that before so I want to be sure. 

Any help/ideas would be greatly appreciated...

---

### Post by mor.nitesh on 2009-11-06
Samsung PC studio isn't very good with wine. (Rated Garbage)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5233](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5233)

---

### Post by Ampi on 2009-11-07
ah, too bad, I'll have to wait for a better version... :(
thanks anyway, better then keep trying with no result :)

---

### Post by mor.nitesh on 2009-11-07
Though the PC studio doesn't work, yet simple file transfer is possible using bluetooth. (The USB cable is as bad as PC studio.)

Just add the phone to the bluetooth devices, and run 'bluetooth-browse'.

---

### Post by Ampi on 2009-11-07
I don't have any bluetooth on my computer. But the problem is going to be solved anyway. I decided to usu my very old laptop instead of having it collecting dust by putting XP on it. 
This way the few programs I would like to use that don't go well with Wine I can still use until they work with Linux.
But thanks anyway!

---

### Post by iris-n on 2009-11-18
Ampi, I think I have solved the problem with the samsung usb file transfer. Would you bear with me to troubleshoot a little?

I need to know if it works with somebody else's device before filing a bug report. ;)

---

### Post by Ampi on 2009-11-19
Sure, more than glad to help. Do I do hope I can help, because I think the file transfer ain't a problem. My problems is moving the rest (not the files) like texts and phone numbers, for that you need PC Studio for now.

Anyway, post away, apart from me more people might be willing. I definitely am!

---

### Post by iris-n on 2009-11-19
Indeed. It breaks my heart that I have little experience with wine and UNR. Well, at least you shall have one thing working ;)

First of all, is file transfer working?
Does it automount?
Does your phone appear when you type lsusb?
What is the model of your phone?
Which type of storage does it have?

---

### Post by Ampi on 2009-11-23
I'm in bit of a delay, that's because I lost my cable... so as soon a I have it.. :)

---

### Post by Ampi on 2009-11-23
I am not sure if I understand this correctly:
You want also other brands to be tested besides Samsung?

The reason we test only Samsung is because the software we're testing is from Samsung. I don't believe phones of other brands are even recognized by the software.

What is possible, is to open another thread we're software for phones from other brands including Samsung is compared to each other in use within Ubuntu/Linux. 

Or have I completely not understood what you mean? :)

---

### Post by Ampi on 2009-12-04
Okay, I found my cable. I just connected my samsung phone through the USB cable on my netbook with UNR 9.10.

My phone is a Samsung Ultra Touch S8300. It has its own phone and sim storage and a small 1GB card. 
The phone does not automount and it does not appear when I type lsusb. 
The phone is somehow recognized. It asks me if I want to connect through PC Studio or Mass Storage. 

Then somehow I also get a different wireless connection. My netbook disconnects from my home wireless connection and chooses to connect throug my cellphone network. 
A question about this: that is the 'same' internet I would have when I would try to connect with my phone to the internet, right? Because I don't have an internet contract on my phone, so that costs me a lot of money, right?

---

### Post by iris-n on 2009-12-06
*EDIT: please do not reboot with that line commented out. It won't be pleasant*

Cool. It is similar enough to my model, so it might work.

You're probably correct about the internet. It is so with my carrier, after all.

Well, let's get to work. First, comment out the line ```
KERNEL!="sr*", IMPORT{program}="/sbin/blkid -o udev -p $tempnode"
``` from the file /lib/udev/rules.d/60-persistent-storage.rules

Type ```
ls /dev/sd*
``` to see which devices you have. Plug in your phone, chose mass storage, and type that again to see if it is recognized. It should appear on this command, but not automount.

If so, the bug is confirmed. If you're interested in making automount works, please be so kind as to give me the output of ```
ls /dev/disk/by-id/
``` after and before plugging in the phone, and I shall graft you an udev rule.

---

### Post by Ampi on 2009-12-07
Hi, 

So I uncommented the line you told me about and then I checked my devices before and after plugging the phone in. 
```
$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sda7  /dev/sda8
```
```
$ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda6  /dev/sda8  /dev/sdb1
/dev/sda1  /dev/sda5  /dev/sda7  /dev/sdb
```
I'm guessing my phone is /dev/sdb1. 

And the output of 
```
$ ls /dev/disk/by-id/
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A-part1
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A-part2
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A-part5
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A-part6
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A-part7
ata-Hitachi_HDP725050GLA360_GEA534RJ130R8A-part8
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A-part1
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A-part2
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A-part5
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A-part6
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A-part7
scsi-SATA_Hitachi_HDP7250_GEA534RJ130R8A-part8
usb-SAMSUNG_S8300_1234-0:0
usb-SAMSUNG_S8300_1234-0:0-part1
```
As you can see the last ones belong to the phone. 
I would like to try the mass storage automount.

For being able of copy messages and phone contacts I'll probably  have to wait longer, that will only be available through PC Studio, right? I mean the small card storage is the only thing connected through this option, right?

---

### Post by iris-n on 2009-12-07
Cool. So this is it.

If I recall correctly, there's a setting in the phone that lets you change between the internal memory or the SD card to store the messages and contacts. So, in theory, you should be able to access them manually through the filesystem. Although I gather that should be rather unpleasant.

Anyway, let's confirm it once and for all: try ```
sudo blkid -o udev -p /dev/sdb
``` That should hang. I think they fixed this bug with util-linux-ng-2.16.3, so this workaround will probably not be need in Lucid.

Now, replace the line you commented out with ```
KERNEL!="sr*", ENV{ID_SERIAL}!="SAMSUNG_S8300_1234",
IMPORT{program}="/sbin/blkid -o udev -p $tempnode"
``` and paste after that ```
KERNEL!="sr*", ENV{ID_SERIAL}=="SAMSUNG_S8300_1234",
ENV{ID_FS_USAGE}="filesystem", ENV{ID_FS_LABEL_ENC}="Ampi_Phone",
ENV{ID_FS_UUID_ENC}="acabacafe"
```

Where, obviously, Ampi_Phone can be anything you want.

That should be it, mylady. Thanks for playing ;)

---

### Post by Ampi on 2009-12-08
Yesterday after reboot I had a crash. My \data partition was lost and when I recovered it I got a boot failure. 

 I was now about to post in this thread explaining it would take some more time. And before when opening the thread I saw your edit about rebooting. So in a shell I commented again the line you told me about and the boot worked.

You saved me from a HUGE heart attack.

Does this mean that now I have to uncomment the line again, finish what you told me, comment it and then the changes we make will still be working?

---

### Post by sisyphus1978 on 2009-12-08
Hey. I thought I'd give this a go too. I have a Samsung X820 but unfortunately the bluetooth is broken, so it would be nice to get it working over USB. Anyway not wanting to hijack this thread, I seem to have stumbled at ```
ls /dev/sd* 
```because I'm not getting anything different before and after plugging the phone in.

---

### Post by Ampi on 2009-12-08
Does your phone get a popout where it asks you how you want to connect your phone? There are three choices: Mass Storage, Samsung PC Studio and Media Player. 
If you don't have a popout you might have the default choice, don't know which one it is. Unplug your phone and go to (at least in my phone S8300): Menu - Settings - Phone Settings - PC connections. Change to: Ask on connection and Save.
Now check the ls /dev/sd* again, should be the same as before.
Now plug in your phone via usb and choose Mass Storage. Check the ls /dev/sd* again.
Any change?

---

### Post by iris-n on 2009-12-08
Sorry! I had completely forgotten it, though that the edit was quick enough to save you from some trouble.

Actually I am a little confused with what you call commenting and uncommenting. To comment a line is to put a ```
#
``` in its beginning. To uncomment is to remove it.

But no, no more comments. You should replace the whole line with the one in my previous post, without any comments. I doesn't matter how it was before. After you do it, the changes will be effective, with no problem to reboot.

**sisyphus1978**, have you commented out the relevant line? Is your phone set as Mass Storage?

---

### Post by Ampi on 2009-12-08
@all: I think it's okay the hijack this thread, now I will check with the S8300 and you will check with the X820. We only need to be carefull who is talking to who ;).

@iris-n: Maybe this afternoon I have time to carry out the next step, where I replace the entire line :)

---

### Post by sisyphus1978 on 2009-12-08
Okay.

Yes I commented the line out.  The X820 doesn't have a mount mode. When I tried it in the past (windows) you have to use the Samsung software to download and upload files (mp3, 3gp). I plugged it into two of my karmic machines and no response from either.

I tried it on my girlfriend's win7 netbook and the phone is recognised. It installed the Samsung Mobile USB driver. But I still think the Samsung software is needed on top of that.

Last. I just checked the manual and nothing specifically on USB. Is this going to be more trouble than it's worth? :)

---

### Post by Ampi on 2009-12-08
I replaced the line```
KERNEL!="sr*", IMPORT{program}="/sbin/blkid -o udev -p $tempnode"
```
by```
KERNEL!="sr*", ENV{ID_SERIAL}!="SAMSUNG_S8300_1234",
IMPORT{program}="/sbin/blkid -o udev -p $tempnode"
KERNEL!="sr*", ENV{ID_SERIAL}=="SAMSUNG_S8300_1234",
ENV{ID_FS_USAGE}="filesystem", ENV{ID_FS_LABEL_ENC}="Ampi_Phone",
ENV{ID_FS_UUID_ENC}="acabacafe"
```
But I got again the boot crash saying: mount of root filesystem failed, etc etc..

So I changed it back again. What did I do wrong?

Do I need to change also filesystem abd acabacafe? What into, like ext3 and some 30-digit name?

---

### Post by Ampi on 2009-12-08
Hmm,this is funny.
So, like I said in my previous post, I changed the line in /lib/udev/rules.d/60-persistent-storage.rules to the original state. 
I was just cruising the ubuntu forums to see if I could help, when I plugged in my phone for more battery (didn't feel like looking for the other cable), I chose Mass Storage, and suddenly a browser opens?!?!
So effectively I didn't change anything and now my phone is recognized, how??
Of course I can only see my SD-card, I would still like to be able to access my phone contacts and text messages, so I will still check the storage possibilities.. Thanks!

---

### Post by sisyphus1978 on 2009-12-08
Do you think I'm better off installing the Samsung software in wine? I've not found anything useful in regards to accessing it directly.

Glad it's working for Ampi.

:)

---

### Post by iris-n on 2009-12-08
**Sisyphus**, if you had to install specific software even on windows, certainly my solution does not apply. And, to be frank, it is improbable that it can be made to work at all. But yeah, do try installing the software via wine. It can't hurt.

But please be more specific about win7. Have you or have you not tried to do file transfer without the u/d software?

**Ampi**, I'm astonished. If it worked in the original state, it should have been working before any intervention. And it couldn't crash. At all. Even if my rules were wrong. Could you try with just the first one replaced?

And to answer your (now irrelevant) questions, it has indeed to be "filesystem", it just tells udev that it is something that should be mounted. And acabacafe can be any hex string. I chose acabacafe because it's funny and has a low chance of collision.

---

### Post by Ampi on 2009-12-08
**sisyphus1987** Give it a try, but like posted in the second post:

> Samsung PC studio isn't very good with wine. (Rated Garbage)
[http://appdb.winehq.org/objectManage...ation&iId=5233](http://appdb.winehq.org/objectManage...ation&iId=5233)

**iris-n** I'll give it a shot tomorrow and I'll check the lines to make sure I do have still the same... It's too late here now :)

---

