---
title: "Is there new hope for syncing a Zune on Ubuntu 9.04?"
date: 2009-05-04
forum: The Cafe
---

### Post by gymophett on 2009-05-04
I have an 8GB flash Zune, and I have Ubuntu 9.04.
I plugged in my Zune, and it actually 'tried' to mount it!
I got this message.

"Unable to mount Microsoft Corp. Zune"

"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

Is there finally a way we can work around it?

---

### Post by gymophett on 2009-05-04
Here is a screenshot of it actually being noticed.

---

### Post by Brainy142 on 2009-05-04
I read that libmtp + amerok might work... I have mixed reports...

Seems that it is "read only"???

This is due to microsoft and there "bumholioness"

---

### Post by gymophett on 2009-05-04
Is there a way to force mount it?

---

### Post by LightB on 2009-05-04
You can mount it on a bottle rocket. That's what I'd do!

---

### Post by gymophett on 2009-05-04
> **LightB said:**
> You can mount it on a bottle rocket. That's what I'd do!

Even though it was made by Microsoft, it is my far my favorite music player. I love it and it was a gift. I don't have time for silly answers. I mean seriously, I'm sure you can force mount it. How though?

---

### Post by Muffinabus on 2009-05-04
Ooo, muy interesante.  It would be nice if I could sync my 30 GB Zune, as it's one of the few things I absolutely NEED Windows for.  I'm going to see if it recognizes it as it does yours.

EDIT:  Hmph, *nothing* ):

---

### Post by gymophett on 2009-05-04
> **Muffinabus said:**
> Ooo, muy interesante.  It would be nice if I could sync my 30 GB Zune, as it's one of the few things I absolutely NEED Windows for.  I'm going to see if it recognizes it as it does yours.

EDIT:  Hmph, *nothing* ):

Okay. I have an 8GB flash which may be a reason. But go download all the libmtp files for Synaptic. :)

Then try again.

---

### Post by dragos240 on 2009-05-04
try this:
```

if root = apt-get install qlix
if non-root = sudo apt-get install qlix

```

Try putting the zune in MTP mode and disconnecting and reconnecting it. Open qlix from your sound & video section and try accessing it from there.

---

### Post by Vostrocity on 2009-05-04
Well the Zune doesn't support MSC (not even MTP). Just like iPods, Zunes are 100% proprietary, which is why even on Windows you could only sync it with the Zune Media Player software. The only reason why iPods sync so easily with Linux media players is that people have looked at iTunes's code and recoded it into Songbird, Rhythmbox, etc. So far, I don't think Zunes on Linux have been popular enough for someone to write something to make it work. And the Zune software is rated "Garbage" for WINE. Shame because Zunes are pretty nice. Microsoft was even nice enough to make an ugly brown Zune to match Ubuntu. :cool:

---

### Post by dragos240 on 2009-05-04
Well just try it, it is indeed worth a try.

---

### Post by Vostrocity on 2009-05-04
> **dragos240 said:**
> try this:
```

if root = apt-get install qlix
if non-root = sudo apt-get install qlix

```

Try putting the zune in MTP mode and disconnecting and reconnecting it. Open qlix from your sound & video section and try accessing it from there.

I hope you remember that Zunes are not simply "PlaysForSure" MTP like the average DAP. It uses MTPZ which is I think makes it incompatible with MTP media players (like WMP or WinAmp).

---

### Post by Muffinabus on 2009-05-04
Tried what was suggested, still nothing.  Doesn't even recognize that I've plugged something in, heh.

---

### Post by gymophett on 2009-05-04
> **dragos240 said:**
> try this:
```

if root = apt-get install qlix
if non-root = sudo apt-get install qlix

```

Try putting the zune in MTP mode and disconnecting and reconnecting it. Open qlix from your sound & video section and try accessing it from there.

Am trying now.
okay. 
It says detecting devices, my Zune lights up, then Qlix shuts off. :(

---

### Post by LightB on 2009-05-04
Shills must be paid "pretty nice":lolflag:

---

### Post by Muffinabus on 2009-05-04
> **gymophett said:**
> Am trying now.
okay. 
It says detecting devices, my Zune lights up, then Qlix shuts off. :(

Yeah, your flash Zune is behaving differently than mine.  Qlix and my Zune showed no signs of interaction whatsoever.

---

### Post by Vostrocity on 2009-05-04
..nvm

---

### Post by dragos240 on 2009-05-04
> **gymophett said:**
> Am trying now.
okay. 
It says detecting devices, my Zune lights up, then Qlix shuts off. :(

try this:
Open up a terminal,
type in "qlix"
when it crashes, post the result.

---

### Post by LightB on 2009-05-04
[img]http://roughlydrafted.com/RD/Home/37A4A383-9B55-4692-8A96-B1A44DAC0941_files/zuned.png[/img]

[ZUUUNE!!!!](http://www.engadget.com/2008/10/31/al-qaeda-endorses-the-zune-on-conan-obrien/)

---

### Post by gymophett on 2009-05-04
> **dragos240 said:**
> try this:
Open up a terminal,
type in "qlix"
when it crashes, post the result.

usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Is dbus working:  true

---

### Post by dragos240 on 2009-05-04
No.

---

### Post by gymophett on 2009-05-04
I can now browse my songs and Zune shows up on my desktop! :D
But I can't listen to them or write to the folder. :(

---

### Post by Muffinabus on 2009-05-04
> **gymophett said:**
> I can now browse my songs and Zune shows up on my desktop! :D
But I can't listen to them or write to the folder. :(

GASP!  Progress!  I can't get mine to do that );

Terminal output when pluggin in my Zune:

```

usb_claim_interface(): Operation not permitted
LIBMTP PANIC: Unable to initialize device
Is dbus working:  true 
connected:  "/org/freedesktop/Hal/devices/usb_device_45e_710_dddbb23d_928d_4e20_80bd_1ff88ee00652" 
QThread(ptr=0x8d03078) RemoveTimeout: killing timer 2 
QThread(ptr=0x8d03078) RemoveTimeout: killing timer 2 
QThread(ptr=0x8d03078) RemoveTimeout: killing timer 2 
QThread(ptr=0x8d03078) RemoveTimeout: killing timer 2 
PTP: Opening session
Qlix MTP ERROR: PTP Layer error 02ff: get_all_metadata_fast(): could not get proplist of all objects.
Qlix MTP ERROR: (Look this up in ptp.h for an explanation.)
Qlix MTP ERROR: PTP Layer error 02ff: get_handles_recursively(): could not get object handles.
Qlix MTP ERROR: (Look this up in ptp.h for an explanation.)
connected:  "/org/freedesktop/Hal/devices/usb_device_45e_710_dddbb23d_928d_4e20_80bd_1ff88ee00652_if0" 
QThread(ptr=0x8d03078) RemoveTimeout: killing timer 2 
Vendor:  "45e" 
Product:  "710" 
Protocol:  ("mtp") 
Protocol udi:  "/org/freedesktop/Hal/devices/usb_device_45e_710_dddbb23d_928d_4e20_80bd_1ff88ee00652_if0" 
QThread(ptr=0x8d03078) RemoveTimeout: killing timer 2 

```

And the program stops responding around when it says "Opening session".

---

### Post by gymophett on 2009-05-04
> **dragos240 said:**
> No.

No what?

---

### Post by gymophett on 2009-05-04
When trying to read or write to folder I get:

"Could not open location; you might not have permission to open the file."

Is there a way to write to this un-authorized location? Then, I will almost completely free from Windows! :D

---

### Post by gymophett on 2009-05-04
[FONT="Trebuchet MS"]Well, is there a way to get permissions to write or read it? I thought you shouldve been able to hear the songs..
[/FONT]

---

### Post by Aiello on 2009-05-04
Well, I doubt it will work, but if you are able browse your Zune with Nautilus, try using Nautilus with root permissions.

Alt + F2
```
gksu nautilus
```

---

### Post by gymophett on 2009-05-04
> **Aiello said:**
> Well, I doubt it will work, but if you are able browse your Zune with Nautilus, try using Nautilus with root permissions.

Alt + F2
```
gksu nautilus
```

It doesn't show up. Do I need to like dev/usb/etc.. or something to get the files?

---

### Post by sgosnell on 2009-05-04
Remember, this device was built by Microsoft as one more attempt to force people to use Windows.  It's a proprietary device, and the source code is not available.  In the short term, I don't think there is much hope of getting it to work on anything other than Windows.  That's why I will never own one, nor will I own an iAnything.  There are lots of generic devices available that work on any OS, and work as well as, or better than, a Zune or iPod.

---

### Post by Muffinabus on 2009-05-04
> **sgosnell said:**
> Remember, this device was built by Microsoft as one more attempt to force people to use Windows.  It's a proprietary device, and the source code is not available.  In the short term, I don't think there is much hope of getting it to work on anything other than Windows.  That's why I will never own one, nor will I own an iAnything.  There are lots of generic devices available that work on any OS, and work as well as, or better than, a Zune or iPod.

I did buy the thing before I was interested in Linux.  It is a very good player though, I love it, just wish it... wasn't made by Microsoft?  Ha.

---

### Post by gymophett on 2009-05-04
> **Muffinabus said:**
> I did buy the thing before I was interested in Linux.  It is a very good player though, I love it, just wish it... wasn't made by Microsoft?  Ha.

I guess I'll just share my music files to my families XP computer through SAMBA and sync the Zune wirelessly. :)

---

### Post by Muffinabus on 2009-05-04
> **gymophett said:**
> I guess I'll just share my music files to my families XP computer through SAMBA and sync the Zune wirelessly. :)

Hmm, that's actually a nifty idea (:

It's not a huge problem for me right now though, as I don't sync too often anyways, and do find myself on my Windows install every so often for gaming.

---

### Post by Warpnow on 2009-05-04
The Zune is not MTP, as has been said, its MTPZ, which is a forked version of MTP for Zune. MTP can read song lists, but not much else, til some coder actually figures out how to port the MTPZ differences to us.

---

### Post by Dragonbite on 2009-05-05
> **gymophett said:**
> I guess I'll just share my music files to my families XP computer through SAMBA and sync the Zune wirelessly. :)

Or run Windows in a virtual machine.

---

### Post by Vostrocity on 2009-05-05
> **gymophett said:**
> I guess I'll just share my music files to my families XP computer through SAMBA and sync the Zune wirelessly. :)

Ooh that's actually a good idea. You could do a remote connection to your a Windows computer in another room and have your Zune sync to that while you're editing your library over the remote connection. :)

---

