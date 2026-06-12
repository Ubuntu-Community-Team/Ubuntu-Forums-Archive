---
title: "Hacking an old computer."
date: 2007-07-30
forum: The Cafe
---

### Post by Turboaaa2001 on 2007-07-30
I'm having a bit of a problem. A client of mine gave me his old Toshiba Satellite Pro 480CDT. I got all his data off and formatted the HD per his request by removing it and using a dock I have.

Heres my problem, I want to mess around with this old laptop but the BIOS has a password on it. What I mean by that is that before it will let me enter the BIOS or boot-up the OS I need the password. The client does not know the password and cannot get it.

The next thing I tried is to take it apart and remove the battery. The battery to my surprise is a huge cordless phone battery with 2 connections, but I removed it and waited several seconds. After putting everything together I booted it up but got the same password screen.

The computer was owned by Planning Technologies Group and was given to my client. He then forgot the password after using it only a few times.


Tried Passwords:

Password  -    password

Admin  -  admin

Administrator -  administrator

00793

*Client's name*

CMOS -  cmos

setup

ALFAROME

BIOSTAR	 -  biostar -  biosstar -  Biostar

LKWPETER -  lkwpeter

SETUP

Syxz

Wodj

Toshiba -  T0ah1ba

iwill

central

xo11nE

SKY_FOX

24Banc81

toshy99

bios

hewittrand

j262

AMI

Award

AMI?SW1

lkwpeter

AMI!SW1

god

---

### Post by jrusso2 on 2007-07-30
If thats the bios battery make sure its disconnected all day then try it.  Leave the laptop battery out also and unplugged.

---

### Post by Turboaaa2001 on 2007-07-30
You think the CMOS will hold a charge that long? If so then I wonder why they no longer implement such longevity? I'll try it non the less.

I also just thought of trying to call the company that use to have it. I found there number and the password I tried (00793) is the number they gave it.

Their IT people will be talking about this one:lolflag:

---

### Post by WIREHEAD on 2007-07-30
Not familiar with the comp you have , but most desktops have a jumper to clear the CMOS .

These are usually very close to the coin sized battery on the motherboard which keeps the time/date and such from resetting .

Usually this jumper will be a 3 pin affair with only 2 pins connected at a time , moving the jumper to the opposite side of the pins and removing the coin battery ( usually about the size of a US nickle ) will reset the CMOS to default status. 

At reboot you will need to get into setup ( F1 , F2 , Delete key Etc. ) and configure whatever else you do not wish to use defaults on .

Edited to congratulate you on finding the password 1 Min. ago. 


Travis

---

### Post by kerry_s on 2007-07-30
is this solved already? if not try turning it over and look for a paper clip size hole, i'm sure you can guess what goes in it. :)
here> [http://www.uktsupport.co.uk/reference/biosp.htm](http://www.uktsupport.co.uk/reference/biosp.htm) it says toshiba's use the shift key.

---

### Post by Jhongy on 2007-07-30
If that doesn't work, do as advised and remove _all_ batteries -- then short the connections on the mobo where the BIOS backup battery was connected (don't short the battery!). 

I'd leave it like that for several hours for good measure...

---

### Post by Turboaaa2001 on 2007-07-30
I'm very familiar with the jumpers with a desktop MOBO, but this is a notebook. Also I have not solved this yet.

*Sigh* Looks like I have to take this thing apart again. I looked for the hole that was mentioned but did not find it (surprise).

Another thing to mention is the sticker on it that states:
"PROPERTY OF THE PLANNING TECHNOLOGIES GROUP 1-800-508-1538" the a number sequence "00793"
The number got me a fax line but I did find a web site for a company that looked to be the same. I e-maild them about it just for fun.

BTW I'm a PC Tech but have not worked a lot with really old notebook computers. I have a love for vintage electronics and have many old Pentium and 486 towers around but notebooks are new.

---

### Post by popch on 2007-07-30
Taken from Toshiba's web site:

> To change or remove the BIOS Password, it's necessary to know the existing password. Otherwise, it can only be removed by a Toshiba Authorized Service Provider. To locate a Toshiba Authorized Service Provider (ASP) anywhere in the world, visit Toshiba's Global ASP Locator at:[http://pcrepair.toshiba.com](http://pcrepair.toshiba.com)

---

### Post by slimdog360 on 2007-07-30
flash the bios?

---

### Post by popch on 2007-07-30
Some sources say that pressing down the left shift key before powering on and holding it until the POST is complete should do the trick.

Another source names 'Toshiba' as password for Toshiba laptops.

---

### Post by metallicamaster3 on 2007-07-30
> flash the bios?

if the battery plan doesnt work, give that a shot.

---

### Post by distroman on 2007-07-30
I would go with clearing cmos by removing the battery as well however you would go about it on a old laptop I do not know.

[http://www.tech-faq.com/reset-bios-password.shtml](http://www.tech-faq.com/reset-bios-password.shtml)
This was just a quick search but there's definitely more ways to bypass a bios password.
Anything you got local access to should be easily removable anything else is too stupid IMO

---

### Post by heimo on 2007-07-30
Yeah, try "Toshiba". Also [CmosPwd]("http://www.cgsecurity.org/wiki/CmosPwd") may help (I haven't used it).

---

### Post by curuxz on 2007-07-30
try looking on ebay, you used to be able to get little dongle things to remove CMOS passwords (that was often what the compaines tech teams did when you send it off to them).

You may have more luck getting one of those :)

---

### Post by smoker on 2007-07-30
is the password required only to enter the bios, or required before the computer will boot?

if you can boot from the cd, try the UBCD, it has some bios password apps included : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

if the computer won't boot, i have heard of a way to 'short' the pins on the eeprom chip if you can access this. i have never tried this though, so can't supply more info, maybe your fav search engine might yield results this way, if possible with this computer!

here is a link with a host of suggestions, including how to make a toshiba key disk:
[http://rahulhackingarticles.wetpaint.com/page/Clear+BIOS+Password,+All+tricks+!?t=anon](http://rahulhackingarticles.wetpaint.com/page/Clear+BIOS+Password,+All+tricks+!?t=anon)

best of luck

---

### Post by Bungo Pony on 2007-07-30
> flash the bios?

That's probably your best bet. EEproms are "Electronically Eraseable Programmable Read Only Memory". Basically means that you can only change the password with software.

If you can get ahold of a chip reader, you could stick the prom into it, read it, and see if you can find anything. That's how I retrieved the configuration passwords for a UPS once.

---

### Post by Warpnow on 2007-07-30
I was under the impression you can't flash the bios without the password.

I've seen a tutorial on "hot flashing" which involves removing the bios chip and putting it back in with pc running, heh, but I wouldn't try it.

---

### Post by mips on 2007-07-30
Looks like you might have to make a paralell port key and do:

> simply remove the main power battery on your laptop, plug this into the parallel port, and turn on the laptop using the plug in power supply. The BIOS password is now instantly and safely removed. Turn off your laptop, remove this key, replace battery, and enjoy

---

### Post by bigken on 2007-07-30
> **mips said:**
> Looks like you might have to make a paralell port key and do:


yep I got one of these keys off ebay quite a few years back it did its job :)

---

### Post by mips on 2007-07-30
> **bigken said:**
> yep I got one of these keys off ebay quite a few years back it did its job :)

They are very easy to make as well if you know how to use a soldering iron a bit. You just have to jumper some pins together.

---

### Post by bigken on 2007-07-30
> **mips said:**
> They are very easy to make as well if you know how to use a soldering iron a bit. You just have to jumper some pins together.

I still have it its my workshop somewhere if I could find it I would upload a picture of the wiring

---

### Post by mips on 2007-07-30
> **bigken said:**
> I still have it its my workshop somewhere if I could find it I would upload a picture of the wiring

It's in one of the links someone posted above but I will attach it here:

[http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)
> To reset the password of a Toshiba, you can use KeyDisk. If this doesn't work, you can try to build the Toshiba Parallel loopback. To make a simple device that you connect to your parallel port, a lot of Toshiba computers remove the password when you boot it up. The device, named "loopback" by some, could be made out of any parallell wire with 25pins connectors (db25). You should connect these pins: 1-5-10, 2-11, 3-17, 4-12, 6-16, 7-13, 8-14, 9-15, 18-25
[IMG]http://www.cgsecurity.org/db25m.gif[/IMG]

---

### Post by bigken on 2007-07-30
He he found it :)

looks like someone has some soldering to do

---

### Post by Bungo Pony on 2007-07-30
That's even simpler to make than the cable to connect a C-64 floppy drive to a PC :)

---

### Post by init1 on 2007-07-30
If you can boot, there are debug routines you can use to clear the CMOS password. 
> The below debug routine will clear CMOS, BIOS, Passwords, Settings, Viruses, and other items residing in the CMOS. During this process you may get returned characters which are an indication that the string has gone in, if you by chance get ERROR ensure that you have typed the line in correctly, if not retype. Ensure that you do not skip any lines, that it is ALL typed in correctly to help prevent problems. Before running this Debug routine also ensure that you have read the above disclaimer.

After typing debug you will get "-" which is were you can begin by typing A and pressing enter.

A <ENTER>
MOV AX,0 <ENTER>
MOV AX,CX <ENTER>
OUT 70,AL <ENTER>
MOV AX,0 <ENTER>
OUT 71,AL <ENTER>
INC CX <ENTER>
CMP CX,100 <ENTER>
JB 103 <ENTER>
INT 20 <ENTER>
<ENTER> Note: Nothing is typed on this line
G <ENTER> By pressing G this will execute the above script, ensure you have read and agree to the above disclaimer.
Q <ENTER>

Then reboot and you will get a Setup Checksum Error. Go into setup, correct all the incorrect values, time, date...


[http://www.computerhope.com/rdebug.htm](http://www.computerhope.com/rdebug.htm)

---

### Post by jgrabham on 2007-07-30
> **Bungo Pony said:**
> That's even simpler to make than the cable to connect a C-64 floppy drive to a PC :)

Can you do that with the tape drive by any chance (I have an old (Broken) C64 under my desk, and want to play on some of the thousands of games I have on Tape:])

---

### Post by Turboaaa2001 on 2007-07-30
I am so printing this thread out.:guitar:

Let me clearify:

I cannot boot unless I enter the password.
I cannot enter the BIOS
I cannot get past the splash screen without the password.

I'm at work right now and the battery is out and the CMOS battery is unplugged from last night. I will boot it up tonight and see what happens.

The next thing I wiull try is a few more generic passwords and then build that key.

This has turned into a fun little project for me. If this was something important I would be pulling my hair out.

---

### Post by Turboaaa2001 on 2007-07-31
> **mips said:**
> It's in one of the links someone posted above but I will attach it here:

[http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)

I work at Radio Shack so I can get a 25pin DB connector. I just need to know how to do the wiring. I'm assuming that I just take a wire and link each set together on. If I'm wrong let me know.

Update:

Removing the battery and the CMOS battery did not work. I am also unable to boot off other media. Also this computer will not be able to run UBCD (I have had this for a while now) because it lacks the power.

I believe I will be trying different passwords and build one of those parallel keys. I like to try different things and I think it would be fun. Plus I could add it to my tool box.

Edit:

I updated the passwords I used and I also tried the left shift key boot-up. It did not work.

---

### Post by heimo on 2007-07-31
> **Turboaaa2001 said:**
> 
I believe I will be trying different passwords and build one of those parallel keys. 

Also try these:
[LIST]
[*]24Banc81
[*]toshy99
[*]bios[/LIST]
> Toshiba notebooks 
Toshiba has a trapdoor password to bypass the bios password.  The company has adopted a truly asinine attitude regarding this password.  It turns out that if the first five bytes of sector 1 (the second sector) of a floppy in drive a are "4B 45 59 00 00" then you can bypass the password (type enter when asked for the password and you will be asked to set the password again).

Source: [http://www.freelabs.com/~whitis/security/backdoor.html](http://www.freelabs.com/~whitis/security/backdoor.html)

---

### Post by Turboaaa2001 on 2007-07-31
I think I'm having more fun trying password suggestions made by all of you. Keep them coming while I build the physical keys mentioned here.

The first one to get the right password before I crack it will become the Password Keeper of this forum :lolflag:

I will be keeping a fresh list of tried passwords on the first post.

---

### Post by erito on 2007-07-31
heres some more generic passwords you can try:
hewittrand
j262
Biostar
AMI
Award
bios
BIOS
AMI?SW1
setup
lkwpeter
cmos 
password (lol! hey its worth a shot)
AMI!SW1
Apparently those are all fairly common.  Albeit you may be better off doing a hardware hack!

---

### Post by Bungo Pony on 2007-07-31
> Can you do that with the tape drive by any chance (I have an old (Broken) C64 under my desk, and want to play on some of the thousands of games I have on Tape:])

I believe all you have to do is copy the cassettes to .wav files to use them in an emulator. I almost never used cassettes with my c-64, so I never had that problem :)

---

### Post by mips on 2007-07-31
> **Bungo Pony said:**
> I believe all you have to do is copy the cassettes to .wav files to use them in an emulator. I almost never used cassettes with my c-64, so I never had that problem :)


I heard a long time ago that it is possible to connect the cassete deck to your sound cards input. Creating a wav file would probable be a better idea though.

---

### Post by Paul820 on 2007-07-31
If it has a disk drive try this:

> Some Toshiba notebooks allow to bypass BIOS by inserting a "key-disk" in the floppy disk drive while booting. To create a Toshiba Keydisk, take a 720Kb or 1.44Mb floppy disk, format it (if it's not formatted yet), then use a hex editor such as Hex Workshop to change the first five bytes of the second sector (the one after the boot sector) and set them to 4B 45 59 00 00 (note that the first three bytes are the ASCII for "KEY" :) followed by two zeroes). Once you have created the key disk put it into the notebook's drive and turn it on, then push the reset button and when asked for password, press Enter. You will be asked to Set Password again. Press Y and Enter. You'll enter the BIOS configuration where you can set a new password.

Taken from here: [http://www.askmehelpdesk.com/advice/t-12222.html]("http://www.askmehelpdesk.com/advice/t-12222.html")

---

### Post by Turboaaa2001 on 2007-07-31
Thats good and I will be keeping this information, but I can't boot off ANY media unless I have the password.

That is why I will be trying a hardware hack. Until then I still want different passwords to try.

Remember, I update the used passwords list on the first post.

---

