---
title: "Bonobo Extreme, wifi problems and keyboard backlight problems"
date: 2013-09-09
forum: System76 Support
---

### Post by Zukaro on 2013-09-09
I have two issues with my Bonobo Extreme currently.
First of all (and most important), I recently updated the BIOS (I received an email from System76 with a download link telling me that I should update the BIOS for improved performance, so I went ahead and did it) and now WiFi takes an unusually long amount of time to connect (it does appear to connect however).  This is while plugged into AC power, I've not tested it on battery power.  Before updating the BIOS the WiFi worked fine (when connected to AC power; again, I've yet to test anything on battery power).

Secondly, the keyboard backlight doesn't save the colour I change it to.  I'm not sure if it's supposed to retain those settings, but it'd be nice if I could get it to stay on the colour I put it at.  It only loses the colour settings when I shut the computer off completely and then turn it on again.  The colour it always resets to is dark blue (which I'm assuming is the default).  I looked in the BIOS (after updating) to see if there were any settings related to this as I've heard the ability to change the colour is a BIOS feature.

Another thing I've noticed is that when the system isn't connected to AC power it seems to run a lot slower (it's more choppy when opening and closing windows).  That was before I updated the BIOS, I've yet to see how it preforms with the new update on battery power.


Other than that it's great.

---

### Post by isantop on 2013-09-09
The keyboard, unfortunately, can't remember your settings after it's been powered off. That value is stored in volatile RAM, which is cleared when the power is cycled. Similarly, the BIOS will scale back the CPU and GPU when on battery to save power. We've noticed particularly agressive scaling with Haswell laptops like your Bonobo, and we're considering disabling or turning this down.

About the wireless issues, do you notice that they happen mostly on a single network, or does it happen on any network? There are a lot of things that can affect that connection time.

---

### Post by Zukaro on 2013-09-09
The wifi issue seems to have corrected itself.  I think it may have just been an issue with the access point.

Is there a BIOS update or something I can download which will allow me to mess around with the power settings?  So that I can disable that power scaling feature or at least limit it?  I think the reason for the lag was due to not having the proprietary nVidia drivers (I reinstalled 13.04 as I wanted full disk encryption and that's the only way I knew how to set that up easily).  I have since reinstalled the nVidia drivers as my games weren't running at all with the generic driver and that fixed the issue.  I've yet to test it on battery power however, but it'd make sense (I was assuming that while on battery power some power saving settings would take place, I was just hoping they could be disabled or at least limited).  However, if I still get that lag while on battery power then that's an issue (lag in games I can at least tolerate at that, as I'm likely to only be playing games with AC power connected, but the entire UI lagging is a major issue).  Although I'm assuming it'll be fine when it comes to the UI now that I've fixed the driver issue.

Other than that the only other issue is just the keyboard; it's really just an annoyance however as I'd rather it keep the colour I put it too but it's not a big deal as blue is fine.  I'd just rather have it stay on green.  Is there no way to store the colour settings with the BIOS settings?  I know there isn't currently, but what I mean is, will there be a BIOS update which will allow this feature?  As well, will there be a BIOS update which addresses the power scaling issue?



EDIT: Nevermind.  There IS a problem with the WiFi.  It's extremely slow to connect while other devices connect to the same access point very quickly, or just wont connect at all.

---

### Post by Zukaro on 2013-09-10
Audio also doesn't work.  Audio is choppy and sped up and doesn't automatically switch to headphones when I connect headphones.

EDIT: And now it's working (it fixed itself).

Everything on this computer is so finicky; stuff doesn't work and then starts working and I have no clue if it'll be an issue again in the future.

---

### Post by isantop on 2013-09-10
Do you remember what applications you were using when you first started seeing choppiness? I'm thinking that an app may have caused the problem. If you have the updated BIOS, then everything should be working.

---

### Post by Zukaro on 2013-09-10
The way the UI was acting choppy is no longer an issue since I updated the nVidia driver (I can even play games on battery power with no issue).  Now the only remaining issues are the wifi and sound.  Sound seems to work fine and I've only had one incident with it so far, which was fixed after rebooting the machine (not sure if it'll become an issue again in the future).

Currently wifi is slow to connect and sometimes wont connect at all (other devices connect just fine and quickly too; devices which are 5+ years old too).  As well, sometimes after connecting to wifi pages will take forever to load (and using other devices at the same time, loading the same pages on the same wifi network will go at a normal speed).  So I don't think it's an issue with my wireless access point.  I have updated the BIOS for this machine; I never really tested it before updating the BIOS, so all I know is that with the new update these issues exist (I don't know if they were present before the update).

I don't know if this is relivant, but the wireless card in my Bonobo is the "Killer Wireless-N 802.11 A/B/G/N Wireless LAN + Bluetooth 4.0 Combo Module"; I'm guessing the BIOS update could have only applied to the default wireless card although I'm not sure (I don't remember the email specifying however).

---

### Post by isantop on 2013-09-10
The BIOS actually doeen't have anything to do with the wireless card anymore. It's handled entirely by the OS. 

Can you try unplugging the router for a few minutes, then plugging it back in?

---

### Post by Zukaro on 2013-09-10
I've tried that and there was no improvement.  As well, it now refuses to connect to ANY other wireless access points.  And I've checked, the password is correct (I also copied and pasted it from another computer which is able to connect using the same password).  The SSID is correct as well.  It just refuses to connect.

---

### Post by Zukaro on 2013-09-11
And now it wont even connect to the one and only access point it was able to connect to...  It'll connect, I'll have no connection, then it'll disconnect and try again over and over again and continuing to fail.  Sometimes it'll ask me to put the access point password in again but it has the correct password.

I have no clue what the hell is wrong with this thing.  Is there a driver or something I have to install?  I've tried installing the System76 drivers (those are whats currently on there; I installed them as soon as I got the machine).  Is it possible the wireless card is defective or something?  And if so, is it possible to get a replacement for free?  I know 100% that it's not the access point as not only have I tested it with multiple other computers I've also tried turning it off for a few minutes then turning it on again.  Although just the fact the thing can't connect to any other access points at all tells me there must be something wrong with the computer and not the access point.

If wifi doesn't work on this machine it's essentially useless for me.

---

### Post by isantop on 2013-09-11
Try running this command in a terminal:
```
echo "options ath9k nohwcrypt=1 blink=1 btcoex_enable=1 enable_diversity=1 " | sudo tee /etc/modprobe.d/ath9k.conf
```

Then reboot and see if that improves it.

---

### Post by Zukaro on 2013-09-11
It's still not working.  :v
Same issue as before; although now I can connect to other wireless access points so there's at least been improvement (as far as I can tell anyways).


EDIT:  It appears to be working.  However, I'm not sure if the same problems are going to arise again considering the way they had in the past, so I'm going to try it out for awhile and see if the problem happens again.  If it doesn't happen again then everything is working.

Thanks for the help.

---

