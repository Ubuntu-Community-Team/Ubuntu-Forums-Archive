---
title: "Not Booting Properly..."
date: 2011-04-17
forum: Server Platforms
---

### Post by haydenh on 2011-04-17
I have Ubuntu 10.04 LTS installed on an old box. I want to reinstall completely using the CD. I tried restarting the machine and waiting for the CD to autorun but it continues to go back to the old install login. I have changed the boot priority and tried using f8 to boot straight to the DVD drive. I also have tried multiple bootable disk which I know work cause I used them to install on this machine previously. Can anyone please guide me in the right direction?

Is there anyway I can load the setup file via the terminal? Thanks!

---

### Post by Sirkyuubi on 2011-04-17
I don't know how to run an install via terminal, but I do know that cd/dvd drives on old box's go bad quite often. You could try a usb install. Thats what I had to use for my box cause the dvd drive went bad. It requires you to reformat your usb drive though. I would back everything up and then do it if you have a usb drive.

---

### Post by haydenh on 2011-04-17
> **Sirkyuubi said:**
> I don't know how to run an install via terminal, but I do know that cd/dvd drives on old box's go bad quite often. You could try a usb install. Thats what I had to use for my box cause the dvd drive went bad. It requires you to reformat your usb drive though. I would back everything up and then do it if you have a usb drive.

Thanks, I don't think it's the CD drive because I've changed it out to a known working one.

I could always try a USB install but I don't really want to do that.

---

### Post by haydenh on 2011-04-18
This is really pissing me off...

---

### Post by Sirkyuubi on 2011-04-18
Sorry dude. I don't know how to do what you are asking.

I can only offer you my USB solution which is really easy to do, and it installs faster than the cd/dvd solution.

---

### Post by GangusKhan on 2011-04-18
You could just get the newest version and tery that or use the usb way

---

### Post by haydenh on 2011-04-18
> **GangusKhan said:**
> You could just get the newest version and tery that or use the usb way

Already tried this. Will probably try via USB in a few.

---

### Post by haydenh on 2011-04-18
> **Sirkyuubi said:**
> Sorry dude. I don't know how to do what you are asking.

I can only offer you my USB solution which is really easy to do, and it installs faster than the cd/dvd solution.

Where are the directions to install via USB. I got it on my thumb drive but do I just boot to the USB drive?

---

### Post by Sirkyuubi on 2011-04-18
boot it through bios. Make it number one on boot priority.

---

### Post by haydenh on 2011-04-18
> **Sirkyuubi said:**
> boot it through bios. Make it number one on boot priority.

Done, exact same thing, boots straight to old install...

---

### Post by Sirkyuubi on 2011-04-18
if you followed the installation instructions on ubuntu's main site then I don't know what to tell you. It seems like you might have a bios issue. Try to clear the cmos and set it up again.

---

### Post by Sirkyuubi on 2011-04-18
after you clear the cmos remove the power from all devices in the computer except for the HDD and the one you want to run the install from. Then make sure the cd or usb is number one on boot priority. ohyeah. Turn off plug and play too, and make sure lagacy usb is enabled

---

### Post by haydenh on 2011-04-18
> **Sirkyuubi said:**
> after you clear the cmos remove the power from all devices in the computer except for the HDD and the one you want to run the install from. Then make sure the cd or usb is number one on boot priority. ohyeah. Turn off plug and play too, and make sure lagacy usb is enabled

Already have done all that. Still a no go. Boots fine to hard drive, but will not boot to CD or USB drive. I've installed Ubuntu Server like 50 times and never had this issue. I agree that it is a hardware issue though. Not really sure what the heck is going on though.

---

### Post by Sirkyuubi on 2011-04-18
try removing the HDD from boot sequence. Only use either USB or CD/DVD in the boot.

---

### Post by haydenh on 2011-04-18
> **Sirkyuubi said:**
> try removing the HDD from boot sequence. Only use either USB or CD/DVD in the boot.

Already tried that, still nothing.

---

### Post by Sirkyuubi on 2011-04-18
well the only thing I can think of is take the HDD out and install ubuntu on it from anther computer and switch it back (dunno how well that will work.) or you can try a net install(which I have no idea how to do).

---

### Post by usatonycuba on 2011-04-19
-Try to set your Bios to default values ?

-Turn off your Computer, unplug power, take off  battery (from your Motherboard), set 5 to 10 minutes, plug battery back.. restart... ?

- This would be your last recourse (I Do not take any responsibility for any damage).   ... Download [Hiren’s BootCD 13.2 ]("http://www.hirensbootcd.org/") from that link. .... Make a Boot CD. ...put the CD in your dvd-rom, restart.. find DOS options, (if i recall well) will be HardDrive tools, and find one that will be Wipe-Out your HardDrive (that will be erase averything one it) so you are aware of it!! (it will take longtime).. after that, make a fresh install From Ubuntu CD.. (try to take option "try Ubuntu before install".. then, make intall with download updates....)

Gl

---

