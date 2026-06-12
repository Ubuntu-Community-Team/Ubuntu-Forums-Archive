---
title: "A few various problems"
date: 2009-05-26
forum: System76 Support
---

### Post by melonbug on 2009-05-26
Hi. I have a few various problems that I've been putting off coming here to ask, hoping I'd be able to figure them out or they'd magically fix themselves, and I figure it's time I look for some support.

I have a Pangolin[p4], running Ubuntu 9.04. Issues are as follows:

a) Since upgrading to 8.10 (which I did unwillingly, back in late January, which completely messed up my laptop, gave it kernel panics within 2 hrs of booting up, never got any solution at all to it aside of Live CDs and then 9.04 beta in April), Cheese has not worked. I think I saw somewhere that it was busted for 8.10, but I thought it should be working now? Why is mine still non-working?

b) I have never been able to get a mic to work on this. Neither the built in nor USB. Nothing has made me able to transmit any sound. Can we possibly figure this out? Transmitting sound would be nice, seeing as I am supposed to have it.

c) Since the upgrade to 9.04, Skype has also not *played back* any sound. Like Cheese, this really isn't a *big* deal, but it would be nice if it worked.

d) I have my panel displaying temps, and the last couple weeks it has been running much hotter (frequently in the 60s) than it was previously, though nothing has changed. Any possible deductions for this?

e) I was also wondering if there is now support for the fingerprint reader?

Thanks for any & all help.

---

### Post by thomasaaron on 2009-05-26
> a) Since upgrading to 8.10 (which I did unwillingly, back in late January, which completely messed up my laptop, gave it kernel panics within 2 hrs of booting up, never got any solution at all to it aside of Live CDs and then 9.04 beta in April), Cheese has not worked. I think I saw somewhere that it was busted for 8.10, but I thought it should be working now? Why is mine still non-working?

Cheese works, and the kernel panics are gone, in 9.04. However, you should download and install a fresh image. There were some problems early on with the beta.

> b) I have never been able to get a mic to work on this. Neither the built in nor USB. Nothing has made me able to transmit any sound. Can we possibly figure this out? Transmitting sound would be nice, seeing as I am supposed to have it.

Unless you have a hardware problem, sound works fine on the PanP4, both in 8.10 and 9.04. I've attached screenshots.
> 
c) Since the upgrade to 9.04, Skype has also not played back any sound. Like Cheese, this really isn't a big deal, but it would be nice if it worked.

In Skype's options, you want to set the mic device to 'hda intel' and audio out to 'pulse.' However, if there is a bunch of other stuff hosed, that may not work.

d) I have my panel displaying temps, and the last couple weeks it has been running much hotter (frequently in the 60s) than it was previously, though nothing has changed. Any possible deductions for this?

TA: That's a pretty normal temp.

e) I was also wondering if there is now support for the fingerprint reader?

TA: Yes it is supported.

Here's what I'd suggest: I'd do a fresh install of 9.04 (64-bit) so that you have a fresh slate to work from. Use a with a freshly downloaded image and then let me help you work through these things one at a time. Everything you mentioned does work fine on the PanP4. But you are probably working from a basically flawed upgrade to begin with. That's why we don't really recommend people using the beta releases.

---

### Post by miniyak on 2009-05-26
the mic on my panp5 has yet to record something also. ive mess with the alsa sound controls and it seems to be working. just not actually recording something in the preinstaled sound recorder or audacity.

is there a way i should set my preferences to get it to work? im going to mess around with it some more

---

### Post by thomasaaron on 2009-05-26
Did you set it up according to the Screenshots I just posted?

---

### Post by miniyak on 2009-05-26
the screen shots failed to download properly (something to do with compression)... must be missing something else. sorry i should have mentioned that before

---

### Post by thomasaaron on 2009-05-27
OK, let's try it this way...

---

### Post by miniyak on 2009-05-27
Solved! i figured it out while messing with those setting sometime yesterday. That helps verify that your solution was the same as mine though and it should help anyone whom stumbles across this post. Thanks for the help Tom.

This seems like an issue that would affect anyone getting a s76 laptop with an integrated mic. (gui confusion that is) Has s76 considered recoding things so everything was labeled properly? ex. Integrated Mic, Speakers, Headphone, Mic jack, digital out .ext, vs. hda 0.0, hda 0.1, hidden capture mute... and whatnot

---

### Post by thomasaaron on 2009-05-27
> Has s76 considered recoding things so everything was labeled properly?

No, we wouldn't get into re-coding software. It might make a good bug report against ALSA though.

---

### Post by melonbug on 2009-05-27
> **thomasaaron said:**
> 
Everything you mentioned does work fine on the PanP4. But you are probably working from a basically flawed upgrade to begin with. That's why we don't really recommend people using the beta releases.

I HAD to get it in beta to be able to actually use my laptop, after letting it sit for over 2 mos essentially unused!! We tried multiple things, looking at Ubuntu help threads and various places, NOTHING resolved the kernel panics. It was ridiculous that I couldn't use the laptop so long. I got beta in early April, it's not like it was some alpha version the final was out like 2-3 weeks later!

But ok, say I do a fresh install. How do I do that while retaining all my docs/settings?

---

### Post by thomasaaron on 2009-05-28
Here are instructions for restoring...

> You can download a CD image for Ubuntu here...
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
...I recommend using a FRESH 9.04 64-bit.

Once you've downloaded the CD image, you will need to burn it to a CD. However, it must be burned as an *image* and not as a *data * CD. Otherwise, it will not be bootable. Instructions for this vary based on which operating system you are using to burn the CD. Instructions for various operating systems are here.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Here are instructions for re-imaging your machine...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)
...including instructions for downloading, installing and running your System76 driver.

As for documents and settings, if you have a separate home partition, you can just partition your system manually and leave the home partition in place.

The root partition (/) should be 15GB, and the swap partition should be equal to your installed RAM.

If you don't have a separate home partition, I'd just back up your documents and important settings to an external hard drive.

That said, I'd be leery of keeping anything besides .mozilla (for Firefox) and .purple (for pidgin). At any rate I would not keep .gnome or .gnome2. I'd want the install to be as fresh as possible to avoid running into incompatibilities (and there definitely were some in Jaunty).

---

### Post by Jozza The Wick on 2009-07-10
Thomas -thanks for those 'settings' images. They helped me out, too.

One thing that you might want to check is the 'Allow Skype to automatically adjust my mixer levels' option. I happened to have my volume settings open as I was making a test call and saw the levels move around - usually back down to the minimums, essentially muting my mic. So you might want to uncheck this option and see if it makes a difference, particularly if it seems like none of the changes you make to your audio settings are having any effect, or don't seem to persist when you return to the audio options windows.

---

