---
title: "Virualizing Ubuntu on Ubuntu?"
date: 2010-01-21
forum: Virtualisation
---

### Post by Nightstrike2009 on 2010-01-21
Hiya everybody,

I was wondering if this is possible I am using Ubuntu 9.04 and have a virtual windows Xp too.

The reason I am asking the question is when I upgraded to Ubuntu 9.10  I found that my 3g modem didn't work anymore (a common fault in 9.10) and had to clean install 9.04 all over again to get on the net.

Is it possible to virtualize ubuntu 9.10 (or more relevant 10.4) within Ubuntu 9.04 Virtual Box so if this problem reoccurs I can just delete the virtual ubuntu (9.10 or 10.4) with no damage to my 9.04 installation?

---

### Post by snowpine on 2010-01-21
Yes, of course, you can run Ubuntu in virtualbox!

Keep in mind that the virtual OS does not "see" your physical hardware (the 3g modem). So if networking is working OK in the "host" OS, it should also work fine in the guest. Good luck!

---

### Post by Nightstrike2009 on 2010-01-21
Thanks Snowpine;

> **By Snowpine**:Keep in mind that the virtual OS does not "see" your physical hardware (the 3g modem). So if networking is working OK in the "host" OS, it should also work fine in the guest. Good luck!

So its possible but as the modem works in Ubuntu 9.04 this would not prove it worked in 10.04 outside of clean installing 10.04? (Which would negate the point in doing it really)

PS: Gotta admit was or is sound in theory though. :-)

---

### Post by snowpine on 2010-01-21
> **Nightstrike2009 said:**
> So its possible but as the modem works in Ubuntu 9.04 this would not prove it worked in 10.04 outside of clean installing 10.04? (Which would negate the point in doing it really)

PS: Gotta admit was or is sound in theory though. :-)

I would recommend testing your modem with an Ubuntu Live CD.

Also keep in mind 10.04 won't be released until April. Just because it's broken now doesn't mean it won't be fixed by release date (or vice versa).

---

### Post by Nightstrike2009 on 2010-01-21
Thank Snowpine,

> **By Snowpine**:I would recommend testing your modem with an Ubuntu Live CD.

I have tried this but sometimes the Live CD works with modem but the hard drive installed ubuntu doesn't, so it seems the only way to test it is clean install. Oh well.:-(

PS: I hope to god this bug is fixed in Ubuntu 10.4LTS has it's annoyed a lot of Vodafone 3g Modem users and even caused newbies to leave linux for good these huawei 3g modems are widely used in Western europe and this bug with ubuntu 9.10 is very serious because its your only connection to the net in some cases leaving Ubuntu 9.10 a broken distro for ever has it cannot be updated because of this major bug, I'd hate to see an Ubuntu LTS affected by this. :-(

PPS: The Modem bug was reported to developers before 9.10's final release but as it was in a frozen state they were unable to rectify this leaving these users the option of giving up or using 9.04 again, lets hope its fixed in 10.4LTS (though it still isn't in 10.4 Alpha 1):-)

---

### Post by arubislander on 2010-01-21
I have a spare partition just for testing versions before I commit my main partition to an upgrade...

---

### Post by Nightstrike2009 on 2010-01-21
Good idea arubislander

I already dual boot Windows XP and Ubuntu 9.04, and virtualize windows Xp on ubuntu (With a view to becoming a ubuntu boot only system once i track down ubuntu alternatives to all my  essential windows programs, I am very close on this too).

I think another partition would make me a Triple Booter (Argh) and cause boot menu problems, has I don't think its that simple to Triple boot as it is dual boot is it?

PS: I have little to no knowledge of Terminal commands or grub setup, I use downloaded .deb files and pull dependencies off the internet by activating my net connection and clicking debs install button to pull them in.:-(

---

### Post by fjgaude on 2010-01-21
Under Linux grub I boot up to five partitions... no issues.

---

### Post by arubislander on 2010-01-22
> **fjgaude said:**
> under linux grub i boot up to five partitions... No issues.

[size="4"]+1[/size]

---

### Post by tipiglen on 2010-01-23
I currently run karmic 9.10 UNR as host on a 2GB RAM Asus netbook.  I have two guests, a Karmic UNR and an XP pro, both 512k and with guest additons.  I can copy and paste between all three machines, and access my usb hard drive from the xp guest via network/samba, but can't (yet) access it from the karmic guest.

All runs pretty smoothly, if a bit slow when playing videos or musicbox...

Using VirtualBox OSE and latest guest additions.  Congratulations to Sun!

---

### Post by Ginsu543 on 2010-01-24
> **Nightstrike2009 said:**
> I already dual boot Windows XP and Ubuntu 9.04, and virtualize windows Xp on ubuntu (With a view to becoming a ubuntu boot only system once i track down ubuntu alternatives to all my  essential windows programs, I am very close on this too).
Yeah, I made this switch when I installed 9.10. The occasional times I need to run Windows software (Microsoft Office because for whatever reason OpenOffice doesn't handle a Greek font I need, and BibleWorks), I just run it through VirtualBox. In any case, I haven't booted into Windows in a long time.

> **Nightstrike2009 said:**
> I think another partition would make me a Triple Booter (Argh) and cause boot menu problems, has I don't think its that simple to Triple boot as it is dual boot is it?
I triple-boot with Ubuntu 9.10, Ubuntu 9.04 (as a backup), and Windows XP, and it's not really that much more difficult than to dual-boot. However, if you're really leery of possibly borking your grub, you can always add a cheap secondary hard drive and install your test OS on that, rather than making another partition on your main hard drive. Then you can boot the test OS by changing the boot order in your BIOS. This will leave everything untouched and intact on your main setup.

---

### Post by tipiglen on 2010-02-05
As a helpful hint:

I run a virtual ubuntu guest in a ubuntu host (both 9.10)
No problems caused by updates to host, but when guest gets a kernel update, the guest additions stop working properly.  Trying to (re)install them from the GUI is ineffective, as is via synaptic - I've tried both.

Solution:
In the guest, open a terminal, and make sure the cdrom is mounted, and then  
```
cd /media/cdrom0
sudo ./VBoxLinuxAdditions-x86.run

OR

sudo ./VBoxLinuxAdditions-amd64.run


```
That should do it - works for me
[http://home2.btconnect.com/tipiglen/loveandpeace3.gif](http://home2.btconnect.com/tipiglen/loveandpeace3.gif)
Salaam/Shalom/Shanthi/Peace
   Namaste -ed

---

