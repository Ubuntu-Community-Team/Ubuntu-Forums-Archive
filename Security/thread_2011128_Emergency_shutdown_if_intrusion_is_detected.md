---
title: "Emergency shutdown if intrusion is detected"
date: 2012-06-26
forum: Security
---

### Post by Stonecold1995 on 2012-06-26
I'm looking for a way to have my computer power down as quickly as possible if it detects any attempts at intrusion (rapid password guessing, a program trying to use sudo and failing to often, a FireWire cable being plugged into its port, etc).  And by shut down quickly, I mean I want it to cut the power in less than a second after the emergency shutdown script is started.  I was thinking of it doing something like what you can do with SysRq (REISUB) but through a script.  I'd like to do this because I use full disk encryption, and if my computer's off there's no way to access any of the data (well, I suppose cold boot attack, but I'd probably be able to insert a command to wipe the RAM at shutdown, sort of what Tails OS does).

So is there any script that can do this?  Specifically, I want it to detect incorrect password tries and shutdown if there are three (or five) failed password attempts in a row, detect the chassis being opened up (if possible...  It's a laptop though), and especially detect FireWire.  I know FireWire can be used to directly access contents of RAM, and I don't like that.  I don't want to fill the FireWire port with epoxy glue (which is what I've heard is a good idea to prevent DMA attacks) because I might need it, but I want it to trigger shutdown unless I manually inactivate the script.

Does anyone know of a configurable script, application, etc that can do this, or at least a place I can look for one?

---

### Post by lisati on 2012-06-26
Although it doesn't use "power off", [fail2ban]("https://help.ubuntu.com/community/Fail2ban") might be of some help in detecting intruders and slowing them down sufficiently for you to be able to do something about them.

---

### Post by Stonecold1995 on 2012-06-26
> **lisati said:**
> Although it doesn't use "power off", [fail2ban]("https://help.ubuntu.com/community/Fail2ban") might be of some help in detecting intruders and slowing them down sufficiently for you to be able to do something about them.

I'm not really worried about attacks through the network, but attacks from people who have physical access to my computer (and who can do things like cold-boot attack, using FireWire to dump the RAM, etc).  Fail2ban only works by blocking IP addresses and sending e-mail notifications, if I'm right.

---

### Post by zombifier25 on 2012-06-27
If someone has physical access to your computer and they're really determined to hack into it, then all hope is lost. No amount of security can save you.

---

### Post by Stonecold1995 on 2012-06-27
> **zombifier25 said:**
> If someone has physical access to your computer and they're really determined to hack into it, then all hope is lost. No amount of security can save you.

I know that, but if it shuts down and catches them off guard there really isn't much they can do with a fully encrypted disk.  And that's what I'm getting at.  If they first try a DMA attack with FireWire and the computer shuts down the second it plugs in, then they can't access any data.  And to perform a cold-boot attack at that point would require access to the BIOS (to boot into a flash drive with a bootable image that will dump the RAM), and the BIOS password I set would slow them down at least long enough that the volatile RAM will clear (plus it's a laptop, so yanking out the RAM cards and putting them in liquid nitrogen really isn't an option, nor is physically accessing the CMOS to reset the BIOS password).

All it takes is for the attacker to make one mistake and trigger the emergency shutdown, and they're pretty much locked out for good (or at least until they can get their hands on a computer that can crack a 64 character password for 256-bit AES encryption, which I don't think will be available for quite a few decades).

I'm just trying to secure my computer as much as I can.  I'm already looking for things like dead-man's switch software, but that wouldn't be very effective against an expert.

---

### Post by QIII on 2012-06-27
Physical access is the Mother of All Security Risks.

Trip wires, Claymores and steel doors.

Are you leaving a laptop on a park bench while you play frisbee?

---

### Post by Stonecold1995 on 2012-06-27
> **QIII said:**
> Physical access is the Mother of All Security Risks.

Which is why I'm trying to defend myself as much as possible with a script like this.  As far as I can tell, my data's pretty safe if my computer's off (and the RAM's had time for the data to fade) and the disk is fully encrypted.

---

### Post by spynappels on 2012-06-27
I don't know a huge amount about Firewire, but if it is anything like USB, you might just be able to write a script which watches the dmesg log and triggers on a firewire related activity. You could then daemonise it and set it so you manually disable it before inserting a Firewire device.

In the spirit of Linux, it is probably easier to write many small scripts to accomplish individual tasks, than one which does everything. Also adds some redundancy, i.e. if one fails, it does not disable all your measures.

Although this really only matters if you are such an important person with such sensitive data that people would carry out a sustained attack on your data. Are you?

---

### Post by Stonecold1995 on 2012-06-27
> **spynappels said:**
> I don't know a huge amount about Firewire, but if it is anything like USB, you might just be able to write a script which watches the dmesg log and triggers on a firewire related activity. You could then daemonise it and set it so you manually disable it before inserting a Firewire device.

In the spirit of Linux, it is probably easier to write many small scripts to accomplish individual tasks, than one which does everything. Also adds some redundancy, i.e. if one fails, it does not disable all your measures.
I'm not very good at scripting, although I know the basics.  So how would I make a script that can do that and will activate immediately, yet not take up too many CPU cycles by repeatedly monitoring FireWire (I'd assume a simple loop would be too CPU-intensive, and even putting "sleep 0.1" in there might cause unnecessary CPU usage)?  And for redundancy, should I have several scripts to do these things (monitor FireWire, failed password attempts, etc), and then one script which monitors them all and if one of the terminates unexpectedly (or sends a "distress" signal) it should kill the power?

> **spynappels said:**
> Although this really only matters if you are such an important person with such sensitive data that people would carry out a sustained attack on your data. Are you?
Not important, no.  But I do have sensitive data that I need to be absolutely certain is safe from prying eyes.  Plus, I run Folding@home on my computer so it's often on even when I'm asleep (although it's in the same room as me, but still).

I got this idea from DECAF (Detect and Eliminate Computer Assisted Forensics), a program that runs on Windows to detect if COFEE (Computer Online Forensic Evidence Extractor, a program sometimes used by computer-illiterate LE to extract data from a computer) is attacking the computer.  DECAF can be configured to do things such as directly attack COFEE, erase its logs, or immediately power down the computer.  Obviously I don't need to worry about COFEE specifically (it's Windows-only), but I'd still like to equip my computer with as many anti-forensic features as possible.  I've already got the basics, like encrypted LVM, long passwords, TrueCrypt, secure-deletion tools like shred, wipe, and srm/sfill, HIDS, VPN, Tor/I2P, etc.

I guess I'm just kind of paranoid, but you can never be too safe.

---

### Post by sudodus on 2012-06-27
> **Stonecold1995 said:**
> ...
I do have sensitive data that I need to be absolutely certain is safe from prying eyes.  Plus, I run Folding@home on my computer so it's often on even when I'm asleep (although it's in the same room as me, but still).
...
I would recommend that you have your sensitive data in a computer that you always poweroff, when you are not using it, and that you run Folding@home in another computer.

---

### Post by Stonecold1995 on 2012-06-27
> **sudodus said:**
> I would recommend that you have your sensitive data in a computer that you always poweroff, when you are not using it, and that you run Folding@home in another computer.
I understand that, and I keep my most sensitive data on an external drive safely locked away, but I still have information that cannot leave my laptop.  I do power it off if I'm not near it, and I dismount any encrypted TrueCrypt volumes, etc as soon as I am done, but I still want as many layers of protection as I can get.  That's all I'm asking.

---

### Post by Cheesemill on 2012-06-27
One thing to remember:
[http://xkcd.com/538/](http://xkcd.com/538/)

---

### Post by Stonecold1995 on 2012-06-27
> **Cheesemill said:**
> One thing to remember:
[http://xkcd.com/538/](http://xkcd.com/538/)
Which is why I have hidden TrueCrypt volumes for plausible deniability (and DBAN at the ready).

That's one of my favorite computer comics btw.

---

### Post by Cheesemill on 2012-06-27
For Firewire the simplest method would be to just disable it in the BIOS if you have the option.

---

### Post by Stonecold1995 on 2012-06-27
> **Cheesemill said:**
> For Firewire the simplest method would be to just disable it in the BIOS if you have the option.
Unfortunately my BIOS is very limited and doesn't have that option.

---

### Post by Ms. Daisy on 2012-06-27
Low tech is key here. 
 
Keep people physically away from the computer if it really matters to you.  
 
I'm sure someone somewhere will sell you some fancy software claiming to physically protect the computer.  But the truth in that XKCD comic is that a wrench is all it takes regardless of clever scripts. 
 
Lock the computer room. Put a security alarm on the door. Get a big angry dog. Handcuff the computer case to your arm.  You get the idea.

---

### Post by CharlesA on 2012-06-28
> **Ms. Daisy said:**
> Low tech is key here. 
 
Keep people physically away from the computer if it really matters to you.  
 
I'm sure someone somewhere will sell you some fancy software claiming to physically protect the computer.  But the truth in that XKCD comic is that a wrench is all it takes regardless of clever scripts. 
 
Lock the computer room. Put a security alarm on the door. Get a big angry dog. Handcuff the computer case to your arm.  You get the idea.
This x 9000.

Physical access = root access.

---

### Post by Grenage on 2012-06-28
Anyone remotely savvy isn't going to try and break into your laptop, they're just going remove the hard disc and walk away.  One step further, they could swipe the RAM at the same time.

Best thing to do is to keep those soviet secrets in an armoured bunker.

---

### Post by tubbygweilo on 2012-06-28
Are your backups safe, secure and tested?

---

