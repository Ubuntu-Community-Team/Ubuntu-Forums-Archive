---
title: "windows XP licensing"
date: 2008-06-12
forum: Virtualisation
---

### Post by gatorbrit on 2008-06-12
Hi - I would like to get XP running in virtual box.  I don't have a licensed copy but i am willing to buy one - if I can find one that is!  But I can't remember how windows controls the licensing of XP.  Can i buy  a copy, then just install it in virtualbox and type in the software key or do I have to connect to Microsoft to get them to unlock my version.

Thanks

---

### Post by wootah on 2008-06-12
> **gatorbrit said:**
> Hi - I would like to get XP running in virtual box.  I don't have a licensed copy but i am willing to buy one - if I can find one that is!  But I can't remember how windows controls the licensing of XP.  Can i buy  a copy, then just install it in virtualbox and type in the software key or do I have to connect to Microsoft to get them to unlock my version.

Thanks
Hmmm... I've been curious about this too.

---

### Post by gatorbrit on 2008-06-12
A little googling came up with this....

[http://www.annoyances.org/exec/show/article03-200](http://www.annoyances.org/exec/show/article03-200)


So when you install windows XP in virtual box - do you have to then register with Microsoft to get the product activation code?

What if you reinstall virtualbox again - do you have to do it again?? 

THanks

---

### Post by LeoSolaris on 2008-06-12
Alright, there is an easy way around this one.  Install it.

Once it is installed, call the number the activation software will give you. (select activate by phone)

Tell the person you finally manage to get a hold of that you would like to activate this copy of windows. Hint: telling them it is a virtual install through VMware for "software testing" confuses them enough,  so I wouldn't bother saying that it is on a Linux system. The Rep will ask you for the product key, and you will have to tell her that you need to purchase a license key. You may be able to haggle it down, but expect it to cost at least an arm, if not a leg, too.

Once you buy the license through the Rep, the Rep will give you the code, and you can type it in. Voila! you now have an active legit copy of Windows. If you need to reinstall, and the code the Rep gave does not work, then call back and have them re-activate the code. (Do MAKE SURE that you write the code down, with spaces between the group of (I think) 5 letters/numbers, otherwise you will have to buy another code!)

Leo

P.S. At least the first couple of times you install with the code it should work just fine, after about three, you will have to call again. I have not tried a fourth time yet to see if I have to call again. Fortunately the call backs for re-installs do not cost anything but a little bit of time.

---

### Post by srodden on 2008-06-13
I suggest you pick up an OEM pack of XP as they're a lot cheaper than a full retail version. Technically you can only get an OEM copy when you buy new hardware so visit your local computer shop and get them to bundle a new USB card or mouse or something :) Whether it's an entirely legal situation to run XP is arguable but you will have a legitimate version of XP that will install just fine and dandy. If you have internetworking on your VM then you can Activate normally or you can use the Activate by Phone method as LeoSolaris mentioned. I would not *buy* it over the phone from those guys though as they won't be able to sell you the cheaper OEM version.

---

### Post by Barriehie on 2008-06-13
I got mine [here](http://www.newegg.com/) and it was about $126.00

Barrie

---

### Post by mehtdosa11 on 2008-06-13
if you have a machine that used to run windows xp there should be an OEM sticker on it somewhere, normally on the base or back. you can use that to register. i have loaded xp on 3 different computers using one rescue disk from a medion laptop. i resuscitated a 9 yr old toshiba laptop for the wife, loaded windows with the medion disc and used the OEM number from my dell inspiron, [which now runs ubuntu]. seems to work.

---

### Post by niteshifter on 2008-06-14
Hi,

As far as using an Win OEM disk - one that ships with a computer - the EULA says no. So does this forum, for that matter. Practically speaking, it's between you and your conscience.

For the heck of it, while waiting for my retail copy of XP SP2 to arrive from Amazon, a few weeks ago I tried a Dell OEM CD (XP SP1) - no go over the phone. I didn't mention Linux or virtual-anything, just it's a re-install after a system crash, and read off the digits from the XP screen - they paused then said not possible and would I like to buy ... They may be on to VBox or they may not. I imagine luck of the draw plays heavily in this.

The retail version installed in VBox A-OK. Key is set network to NAT. It did it's WPA over the net A-OK. The only problem was with SP3 - get IE7 first if that important to you. Mine refused to install until I removed SP3, then install IE7, then re-install SP3. If you can live with SP2, do so.

As to re-activating: If you backup the .VirtualBox folder (specifically VirtualBox.xml, Machines and VDI folder) no. There would no change to VM. Activation can be requested again if you make changes in RAM size, Video RAM size, HD type, etc. So figure out sizes and such ahead of time. In this respect it acts like a real machine, that is, M$ thinks it's theirs, not yours.

---

