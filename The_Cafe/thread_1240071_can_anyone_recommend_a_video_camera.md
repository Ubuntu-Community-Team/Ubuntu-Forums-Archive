---
title: "can anyone recommend a video camera?"
date: 2009-08-14
forum: The Cafe
---

### Post by decoherence on 2009-08-14
Warning: this is a cross-post from another forum (where I haven't had a response.) That makes me evil. :D

Can anyone suggest a model of NTSC video camera for the school I work for? There are three criteria... one, it must not require drivers be installed (we have hundreds of computers and these cameras might be hooked up to any of them or loaned and hooked up to home computers, etc) two, it must work on Macs and PCs (a given, if it doesn't require device specific drivers? linux would be good too, but mostly for me) and three, please under $400. 

Panasonic or Canon are preferred because we have batts and chargers for them, but that's not essential. 

In the past we've gone for MiniDV cameras with firewire. These worked fine (as long as the computer had firewire and the firewire port on the camera didn't get smashed by a student or teacher) but it seems like these cameras are falling out of favour in this price range. So before I recommend buying another four of the suckers, I want to check: 

USB-only video cameras still all require drivers? 
Are there non Mini-DV cameras that use firewire? 
Aside from DV streams, what codec is easiest to work with in an editor and also doesn't require a camera-specific codec to be installed first? (and preferably not require us to buy an MPEG-2 license for each computer.) 
Any other considerations for a camera that will be used on arbitrary computers? 

Editing will be done in Final Cut, iMovie and.... oh yeah MovieMaker... It might sound like I'm asking a lot, but I just want to know if any of these modern HDD/SD/DVD/whatever cameras can compare to DV/firewire in terms of being plug and play? 

Finally, we're probably going to look for an HD camera which would have to fill similar criteria. Any suggestions? Thank you for any insight!

---

### Post by The Toxic Mite on 2009-08-14
I recommend the [Panasonic SDR-S7](http://www2.panasonic.com/consumer-electronics/shop/Cameras-Camcorders/Camcorders/SD-Camcorders/model.SDR-S7K_11002_7000000000000005702) - it's a really good camera.

it's compact, and it records to an SDHC memory card.

---

### Post by decoherence on 2009-08-14
> **The Toxic Mite said:**
> I recommend the [Panasonic SDR-S7](http://www2.panasonic.com/consumer-electronics/shop/Cameras-Camcorders/Camcorders/SD-Camcorders/model.SDR-S7K_11002_7000000000000005702) - it's a really good camera.

it's compact, and it records to an SDHC memory card.

Thanks. I see it records in MPEG2 and attaches via USB. Does it require a driver be installed?

---

### Post by The Toxic Mite on 2009-08-14
> **decoherence said:**
> Thanks. I see it records in MPEG2 and attaches via USB. Does it require a driver be installed?

No, although you may need to have an extra set of codecs for it to view though.

GStreamer works fine (if you are to use it on a Linux box) :)

---

### Post by Keith Hedger on 2009-08-14
Sony DCR-SR35 30g hdd with still shot,40Xzoom,simple video editing and infra red mounts the hard drive via USB and records in MPEG format, just plug and play.

---

### Post by decoherence on 2009-08-14
Is it common for these to appear as mass storage devices? That would certainly solve the driver concerns...

With that particular model my concern is the spinning platter. Because it's going to be used by many people, ruggedness is a big concern. In that respect the SD card ones are interesting. Do they also show up as mass storage?

I'm so used to going through a capture process that I didn't even think of that! Thank you for your gentle application of the Clue Stick ;)

---

### Post by The Toxic Mite on 2009-08-14
> **decoherence said:**
> Is it common for these to appear as mass storage devices? That would certainly solve the driver concerns...

With that particular model my concern is the spinning platter. Because it's going to be used by many people, ruggedness is a big concern. In that respect the SD card ones are interesting. Do they also show up as mass storage?

I'm so used to going through a capture process that I didn't even think of that! Thank you for your gentle application of the Clue Stick ;)

The SD card ones will come up as a mass storage device, yes :)

---

### Post by decoherence on 2009-08-14
That sounds ideal except we (the school) have a problem that would need to get fixed before this could work. I'll describe it here, just in case...

Our Windows computers, which automount a bunch of Novell shares during login, often try to assign drive letters that are already used by the shares when you plug in USB storage. The result is that absolutely nothing happens. I have to log in as an admin and manually set the drive letter.

Our main goal is for this to be 'seamless' for the users. Unless we can figure this out (and i'm neither the Novell tech nor the Windows tech) this perfectly ideal solution will fail the seamless test.

Anyway, thanks for the advice! I think we'll act on it provided we get Windows sorted out (it can't tell what letters are already assigned and just assign a different one? or would that open up some kind of massive security hole in the house of cards known as windows):lolflag:

---

### Post by The Toxic Mite on 2009-08-14
> **decoherence said:**
> That sounds ideal except we (the school) have a problem that would need to get fixed before this could work. I'll describe it here, just in case...

Our Windows computers, which automount a bunch of Novell shares during login, often try to assign drive letters that are already used by the shares when you plug in USB storage. The result is that absolutely nothing happens. I have to log in as an admin and manually set the drive letter.

Our main goal is for this to be 'seamless' for the users. Unless we can figure this out (and i'm neither the Novell tech nor the Windows tech) this perfectly ideal solution will fail the seamless test.

Anyway, thanks for the advice! I think we'll act on it provided we get Windows sorted out (it can't tell what letters are already assigned and just assign a different one? or would that open up some kind of massive security hole in the house of cards known as windows):lolflag:

How many Novell shares are mounted on login?

On my school computers, when I plug my USB stick into it, it automatigically mounts, and a drive letter is automagically assigned. We only have about five or six shares mounted upon login (the techies may have more though :P)

---

### Post by decoherence on 2009-08-14
> **The Toxic Mite said:**
> How many Novell shares are mounted on login?

On my school computers, when I plug my USB stick into it, it automatigically mounts, and a drive letter is automagically assigned. We only have about five or six shares mounted upon login (the techies may have more though :P)

For students, just two, H: and G:.

So you'd think it'd come up as E: like mass storage does on every other Windows system I've used. But it only sometimes does this. The other times I check the Disk Management tool and see that it has been assigned to F:. I think it must be some bad interaction between Novell and Windows... I can't image that shares mounted via ActiveDirectory would break devices like this... then again, you never know. Probably a configuration thing that MS handles automagically in an AD setup that didn't get done in our setup.

Our computers are messed up. Sometimes I'm glad it's not my problem and other times I'm ticked that I'm not in a position to do anything.

I've let my boss know that this bug is holding us up. Hopefully he'll do some prodding...

---

