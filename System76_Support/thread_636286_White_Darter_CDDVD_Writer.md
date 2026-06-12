---
title: "White Darter CD/DVD Writer"
date: 2007-12-09
forum: System76 Support
---

### Post by riseringseeker on 2007-12-09
I was having trouble making an ISO and/or a copy of a data CD.  I tried K3b, cdrecord, as well as the nautilus writer, all gave me multiple input/output errors.  I installed X-CD-Roast, and Gnome CD Master to see if they would do any better - odd thing was neither recognized the CD Writer.  I would add it in manually, but really don't know what parameters the programs call for.

Carl, Tom, anyone?  Can you tell me how to add the CD/RW to either/both of the above programs?

---

### Post by thomasaaron on 2007-12-10
I'm not familiar with either of those programs, but it kind of sounds like a hardware problem to me. The Darter writes CDs (data and iso) well with nautilus.

You might try re-flashing the firmware in the drive, though. I've actully fixed a couple of burn problems recently by re-flashing. Perhaps something got corrupted when you originally flashed it to fix the freezing bug.

You might also just try re-seating the drive. Also, are you using a CD-R? I've never tried a CD-RW, but that might cause a problem too.

---

### Post by riseringseeker on 2007-12-10
> **thomasaaron said:**
> I'm not familiar with either of those programs, but it kind of sounds like a hardware problem to me. The Darter writes CDs (data and iso) well with nautilus.

I have done so with nautilus, but was/am having trouble making a particular copy, so I decided to try a different burner program or two.

Either of these programs are easily available thru synaptic, add/remove, or apt-get, your choice.  xcdroast,  gcdmaster.

K3b seems to work just fine, though it had multiple errors in trying to copy the CD I was trying to do, other than that, works fine.

> You might try re-flashing the firmware in the drive, though. I've actully fixed a couple of burn problems recently by re-flashing. Perhaps something got corrupted when you originally flashed it to fix the freezing bug.

I've used it as a burner several times since the last flash, but i suppose I could try it again.

> You might also just try re-seating the drive. Also, are you using a CD-R? I've never tried a CD-RW, but that might cause a problem too.

"Re-seating"?  Want to give me a better clue here, not sure what you mean.

I've tried both CD-R and CD-RW, both seem to work, except for on the one recalcitrant disk.

---

### Post by thomasaaron on 2007-12-11
OK. I guess I misunderstood you (and maybe I still am). So, you're saying it burns fine with nautilus (right now) except for one particular iso/data cd you're trying to burn. Is that correct?

If so, don't worry about flashing or re-seating the drive.

What exactly are you trying to burn? Is it possible that it is DRM protected?

---

### Post by riseringseeker on 2007-12-12
> **thomasaaron said:**
> OK. I guess I misunderstood you (and maybe I still am). So, you're saying it burns fine with nautilus (right now) except for one particular iso/data cd you're trying to burn. Is that correct?

If so, don't worry about flashing or re-seating the drive.

What exactly are you trying to burn? Is it possible that it is DRM protected?

Yes, it's possible.  It's a Rosetta Stone language CD.  Reading many posts though, if it is copy protected, this is a new thing for RS.  Lots of posts describe how to run it off an ISO image for example, not needing the disk in the drive.  Other posts talk about the need to change case when trying to run it under Wine, but no where was I able to see that anyone had run into a copy protection scheme.

The question still stands though, why does Gnome CD Master, and X-CD-Roast not see the CD drive for the Darter?

---

### Post by thomasaaron on 2007-12-12
Well, I think I figured it out.

If you open Gnome CD Master from a terminal (gcdmaster) WITH a disk in the drive, you get a "resource busy" error. If you run it WITHOUT a disk in the drive, you get a "Permission Denied" error.

I finally got it to recognize my drive by taking the cd out of the drive and running it as root:

```
sudo gcdmaster
```

---

### Post by riseringseeker on 2007-12-12
> **thomasaaron said:**
> Well, I think I figured it out.

If you open Gnome CD Master from a terminal (gcdmaster) WITH a disk in the drive, you get a "resource busy" error. If you run it WITHOUT a disk in the drive, you get a "Permission Denied" error.

I finally got it to recognize my drive by taking the cd out of the drive and running it as root:

```
sudo gcdmaster
```

That works, at least for gdcmaster.

 OK, as I am "on the road" again, and left the language disk at home for the wife to use it, will try again when I get back in a few days. 

 I am also going to call Rosetta Stone and just ask about copies and whether I can get another one.  I am not trying to cheat RS, it's just I am gone ~17 days a month, and I would like both wife and I be able to go through the lessons.

---

### Post by thomasaaron on 2007-12-12
Curious: What language are you trying to learn?

---

### Post by riseringseeker on 2007-12-13
> **thomasaaron said:**
> Curious: What language are you trying to learn?

Danish, for me it's relearning it, but new for spouse.  We have an invitation to visit cousins of mine in Denmark, and would rather be able to speak either language.

I tried to use the instructions [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2497&iTestingId=12450"), the "remarks" by Kerick, which led me to beleive I should be able to copy the disk, or for that matter, just run it using an ISO image.

---

