---
title: "Atten: Starling owners | karmic koala (9.10)"
date: 2009-10-28
forum: System76 Support
---

### Post by thomasaaron on 2009-10-28
Starling Owners,

We are not going to have Karmic testing finished on the Starling Netbook on October 29th, 2009.

We will get bug-fixes for the Starling implemented in the System76 Driver as soon as possible, and you should monitor this thread for status updates.

The biggest drawback to upgrading your Starling to Karmic before we are finished testing is that your wireless will not work correctly.

We estimate the having bug-fixes for the Starling finished within a week of Karmic's release.

---

### Post by thomasaaron on 2009-10-28
Bumping this in hopes that Starling owners will see it. ;)

---

### Post by kingnerd on 2009-10-29
> **thomasaaron said:**
> Bumping this in hopes that Starling owners will see it. ;)

Haha.  I was reading the forums to check the Lemur updates as I was updating to Karmic on my Starling... glad I saw this when I did.  Will keep checking for a safe upgrade time.

---

### Post by rubbsdecvik on 2009-10-29
Thanks for the head's up. I specifically checked the forums to see if this was a good idea or not.

---

### Post by Maczimus on 2009-10-29
Ugh... I wish I would have seen this before installing the driver....wireless was working to a point before but now it's not at all and i don't know how to go back...Yes I am disappointed in the wireless performance of my new netbook...

Thomas would there be a way to get it back before the driver install? it worked although the speed jumped around a lot almost like it was a transmit power problem or something. It is wierd as i have a netgear dongle that worked flawlessly in 8.10 on any system but has the same problems in 9.04 or 9.10 i wonder if there was a regression.

---

### Post by Aggzza on 2009-10-30
im planning to purchase a starling netbook in mid november-december.

will it have ubuntu 9.10 by then?

---

### Post by Tart on 2009-10-30
I'm pretty sure, that even if you order it now, you will receive system with 9.10 on it. You can also ask them to put 9.10 in order message, just in case.

---

### Post by thomasaaron on 2009-10-30
Maczimus,

> Ugh... I wish I would have seen this before installing the driver....wireless was working to a point before but now it's not at all and i don't know how to go back...Yes I am disappointed in the wireless performance of my new netbook...

We put out a fix for the Starling's wireless. It was in the 2.3.7 System76 Driver. However, that will not run on Karmic. About the only way you can get it to work is to reinstall 9.04 and the 2.3.7 driver and run it. Then you should get much improved range. You *could* shrink your home partition and install 9.04 on it as a dual-boot so that you don't have to wipe 9.10. Then when the driver that will support 9.10 is ready, you could just delete 9.04 and re-expand your home partition. Of course, all of that assumes you created a separate home partition.

```
It is wierd as i have a netgear dongle that worked flawlessly in 8.10 on any system but has the same problems in 9.04 or 9.10 i wonder if there was a regression.
```

One would think that it *shouldn't* be a regression... but it probably is. Have you googled the model number of the dongle plus "Ubuntu" or "Jaunty" to see if anyone else has found a workaround.

---

### Post by Maczimus on 2009-10-30
Yes Thomas...sorry but the dongle uses the same chipset as the internal one for the Starling. Other than the wireless being flaky I am loving it as I just got it last week. I like living on the bleeding edge and like to use the newest version when it comes out as a RC but don't think i will be doing that anytime soon. yes you made me a seperate home partition per my request i guess and i appreciate it. just puzzling as to why wireless for that chipset wa better in 8.10 but not in 9.04 and 9.10. anyway thanks for the reply.

hmm maybe ndiswrapper would work?

---

### Post by thomasaaron on 2009-10-30
I've seen very little success with nswrapper with that chipset. We never had that chipset during 8.10, so I'm not really sure what it was like. But from what I've read, it's never been *good* until people discovered they needed to compile the latest driver from realtek.

---

### Post by Maczimus on 2009-10-30
OK now i know what the driver does!

---

### Post by Carl Hamlin on 2009-10-30
D'OH!

Should have come to the forums before upgrading, apparently. I was just stepping in here to see if anyone else was having trouble getting wireless under Karmic.

Fortunately, I don't have any meetings planned next week that necessarily involve having to be web-enabled at the conference, so I should be able to wait it out on cable-connection until then.

Is there a firm ETA on the driver update?

---

### Post by thomasaaron on 2009-10-30
Probably mid-next week.

---

### Post by Aggzza on 2009-10-30
> **Tart said:**
> I'm pretty sure, that even if you order it now, you will receive system with 9.10 on it. You can also ask them to put 9.10 in order message, just in case.

thank you

---

### Post by Eldera on 2009-10-31
Bump. I thought this needed to be at the top of the line during the weekend.

[quote=thomasaaron]Starling Owners,

We are not going to have Karmic testing finished on the Starling Netbook on October 29th, 2009.

We will get bug-fixes for the Starling implemented in the System76 Driver as soon as possible, and you should monitor this thread for status updates.

The biggest drawback to upgrading your Starling to Karmic before we are finished testing is that your wireless will not work correctly.

We estimate the having bug-fixes for the Starling finished within a week of Karmic's release.
[/quote]

[quote=thomasaaron]Probably mid-next week.[/quote]

---

### Post by iamadog on 2009-10-31
my netbook is even in a worse condition now. both wired and wireless arent working. I cant do anything now.

---

### Post by CrimsonS on 2009-10-31
Thanks for the feedback. I also hurried to intall karmic not realizing the drivers were not ready for it.

On the bright side, karmic is a lot more functional then when I tried the beta a month ago. It was really slow and some keys (including the letter 'F' if I remember well) didn't work.

---

### Post by rluethy on 2009-10-31
I also was upgrading too fast and ran into this issue. There seems to be a workaround, see [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1247040](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1247040), which works for me: 

edit /etc/modprobe.d/rtl8187.conf and comment out "blacklist rtl8187"

In the thread mentioned above this is discouraged, because the rtl8187 driver apparently  has range issues, but I figure it is better than no wifi and I can switch back to the System76 driver, when it gets updated.

Roland

---

### Post by gamerchick02 on 2009-10-31
Well.  Now I know why wireless doesn't work.

Heh.

I have no problem with a wired connection.  Other than the wireless, karmic is awesome on the Starling.

Thanks for the info.

Amy

---

### Post by mwiktowy on 2009-11-01
> **thomasaaron said:**
> Starling Owners,

We are not going to have Karmic testing finished on the Starling Netbook on October 29th, 2009.

We will get bug-fixes for the Starling implemented in the System76 Driver as soon as possible, and you should monitor this thread for status updates.

The biggest drawback to upgrading your Starling to Karmic before we are finished testing is that your wireless will not work correctly.

We estimate the having bug-fixes for the Starling finished within a week of Karmic's release.

Are you planning to feed these driver improvements back upstream so that the next Ubuntu (and maybe other distros) will work out-of-the-box? It seems that the default Ubuntu (and the one included in Fedora 12 Beta) wireless driver is *so* close to working properly. Transmission power seems wonky since signal of APs are strong but the signal strength as registered on the AP (using DD-WRT) is *very* low even when the netbook is right beside the AP.

---

### Post by thomasaaron on 2009-11-02
> Are you planning to feed these driver improvements back upstream so that the next Ubuntu (and maybe other distros) will work out-of-the-box?

Indeed. That is part of what we do.

---

### Post by htismaqe on 2009-11-02
> **thomasaaron said:**
> Indeed. That is part of what we do.

This is good news.  I would very much like to use the driver, but don't want to have to go back to Jaunty to do so.  Do you think it would solve my problem?

[http://ubuntuforums.org/showthread.php?p=8225097](http://ubuntuforums.org/showthread.php?p=8225097)

---

### Post by Vrekk on 2009-11-02
Ya I upgraded before I saw this message, but I have a spare USB adapter that runs great for now.

For some reason i cant get my sd card reader to run after the update.  Any advice (ran the driver, rebooted, no luck)

---

### Post by ctsdownloads on 2009-11-02
> **Vrekk said:**
> Ya I upgraded before I saw this message, but I have a spare USB adapter that runs great for now.

For some reason i cant get my sd card reader to run after the update.  Any advice (ran the driver, rebooted, no luck)

Smart. Always have a stash of USB wifi dongles on hand.

I own a draw full myself, you never know! :)

---

### Post by Vrekk on 2009-11-03
> **ctsdownloads said:**
> Smart. Always have a stash of USB wifi dongles on hand.

I own a draw full myself, you never know! :)

It comes in handy when I install ubuntu and wireless dose not work out of box :p

And about my SD card reader, its turns out the card i was trying was shot, unless the sd card reader broke on 10 different computers at the same time ;)

Still havn't found any other cards to test it with though :|

---

### Post by Maczimus on 2009-11-04
Havn't completely confirmed it yet but my drops in network functionality in 9.10 with the built in driver for now seem to be caused by a low power level on the wireless adapter. both my internal and external dongle use the same chipset on connection info and they both have the stalling issue so i have narrowed it down to the driver...also i may have found a temp fix. i have a WRT54GL with tomato firmware and i have boosted the power from the router and didnt have any drops walkling around my house unline when i connect directly to the 2wire uverse gave me...

---

### Post by rectagonal on 2009-11-05
> **thomasaaron said:**
> Probably mid-next week.

Any word on how close it is to release ? Really jonesing for Karmic...

---

### Post by thomasaaron on 2009-11-05
A few more days (business days). After this week, I need to spend some time with my Labrador. She has become quite jealous of the Karmic Koala.

---

### Post by jdb on 2009-11-05
> **thomasaaron said:**
> A few more days (business days). After this week, I need to spend some time with my Labrador. She has become quite jealous of the Karmic Koala.

She's a real cutie :)

jdb

---

### Post by gamerchick02 on 2009-11-05
> **rectagonal said:**
> Any word on how close it is to release ? Really jonesing for Karmic...

I am too.  I'd love to be able to surf on the couch with my netbook.

Amy

---

### Post by registering on 2009-11-05
> **thomasaaron said:**
> A few more days (business days). After this week, I need to spend some time with my Labrador. She has become quite jealous of the Karmic Koala.

Adorable dog. If you paint her black she'd look like mine. :)

---

### Post by htismaqe on 2009-11-05
> **gamerchick02 said:**
> I am too.  I'd love to be able to surf on the couch with my netbook.

Amy

Does your wireless work at all, or is it just flaky?

Mine is just flaky and I've found it works alot better if I hard set the bit rate to 11M or lower.

---

### Post by thomasaaron on 2009-11-06
I think it will work fairly well at close range in Karmic. Same problem as in Jaunty before we fixed it.

---

### Post by gamerchick02 on 2009-11-06
It's not working right now in Karmic.  I run an update a couple times a day.  I'm being patient.  :-D

Amy

---

### Post by mwiktowy on 2009-11-06
> **gamerchick02 said:**
> It's not working right now in Karmic.  I run an update a couple times a day.  I'm being patient.  :-D

With my Starling, you pretty much have to be *right* beside the access point for it to connect and work at a reduced speed.

> **thomasaaron said:**
> I think it will work fairly well at close range in Karmic. Same problem as in Jaunty before we fixed it.

So ... not meaning to beat a dead horse or be rude here ... but if S76 are pushing patches upstream, why when you fixed it for Jaunty, did the fixes not make it into Karmic *6 months ago* when development started for it?

I understand the need for a "Special Sauce" driver package to speed up fixes for your customers. However, feeding patches upstream does not mean throwing the source into a personal repository and hope that the driver maintainer will seek it out and pull it into the kernel. Not knowing what efforts you made last time, I am not going to make assumptions.

I just joined the System76/Netbook party so perhaps this Jaunty fix only happened recently too. I am just curious about why your globally useful fixes are not sticking upstream. It must make things a maintenance nightmare for you to essentially maintain a separate distro.

PS ... that is the cutest dog *ever*

---

### Post by thomasaaron on 2009-11-06
> So ... not meaning to beat a dead horse or be rude here ... but if S76 are pushing patches upstream, why when you fixed it for Jaunty, did the fixes not make it into Karmic *6 months ago* when development started for it?

Actually, we tried, but the fix was not completed in time for the developers to work with it and move it into Karmic. It should make it into the next version though.

```
I understand the need for a "Special Sauce" driver package to speed up fixes for your customers. However, feeding patches upstream does not mean throwing the source into a personal repository and hope that the driver maintainer will seek it out and pull it into the kernel. Not knowing what efforts you made last time, I am not going to make assumptions.
```

Right. That's not what we do. We are actually partners with Canonical and work with their devs fairly frequently.

---

### Post by jbraswell on 2009-11-06
Dang, before I never would have done something so crazy as upgrade this quickly when wireless was an issue.  However, since my Starling was literally the first and only Linux machine to ever work with wireless without hours of headaches, I got too optimistic.  

Oh well, hopefully the fix is forthcoming.

---

### Post by bboston7 on 2009-11-08
Is this fixed yet?  I just saw an update to 2.3.9

---

### Post by htismaqe on 2009-11-08
> **thomasaaron said:**
> I think it will work fairly well at close range in Karmic. Same problem as in Jaunty before we fixed it.

Signal strength and attenuation with 802.11b/g have a fairly inverse relationship.  Fixing the bit rate at a lower speed will allow you get farther away, or at least it should in theory.

I've been testing it for the past couple of days. If I put my wireless PC next to my router, it will run at 54M.  At 15 feet, it runs at 18M reliably.  At 30 feet, anything above 11M is flaky and 5.5M is ideal.  At 40 feet or more, I HAVE had success getting a stable connection, but no higher than 1M.

---

### Post by Maczimus on 2009-11-09
> **htismaqe said:**
> Does your wireless work at all, or is it just flaky?

Mine is just flaky and I've found it works alot better if I hard set the bit rate to 11M or lower.

Could you explain how you force the speed? did'nt see it in the connection manager so must be a cli thing.

---

### Post by htismaqe on 2009-11-09
> **Maczimus said:**
> Could you explain how you force the speed? did'nt see it in the connection manager so must be a cli thing.

Yeah, you set it with the **iwconfig** command.

**iwconfig** is transitive, meaning it's not saved when you reboot, so you have to enter it every time you restart.

In my case, I use WICD for my network manager and WICD supports scripting, so I wrote a shell script to set it when it connects.

The full command I use is:

**iwconfig wlan0 rate 11M**

---

### Post by Maczimus on 2009-11-09
> **htismaqe said:**
> Yeah, you set it with the **iwconfig** command.

**iwconfig** is transitive, meaning it's not saved when you reboot, so you have to enter it every time you restart.

In my case, I use WICD for my network manager and WICD supports scripting, so I wrote a shell script to set it when it connects.

The full command I use is:

**iwconfig wlan0 rate 11M**

Thanks a lot...been thinking about WICD as well... used it in 6.06 but not since.

---

### Post by Maczimus on 2009-11-09
Limiting the speed tonight when I got home from work using above command in the terminal....I have to say I have NOT had ANY hiccups or drops on my network all night and it has been SUPER FAST! I am impressed. thanks a lot for that suggestion. Anyone else having this problem should probably try that at least until System76 comes out with the new driver.

---

### Post by jbraswell on 2009-11-10
> **Maczimus said:**
> Limiting the speed tonight when I got home from work using above command in the terminal....I have to say I have NOT had ANY hiccups or drops on my network all night and it has been SUPER FAST! I am impressed. thanks a lot for that suggestion. Anyone else having this problem should probably try that at least until System76 comes out with the new driver.

Er, I don't even see wireless connections right now.  Is that not the same thing that happened when you upgraded?

---

### Post by thomasaaron on 2009-11-10
jbraswell,

If you are on 9.04...
> Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.


If you are on 9.10...
> Please see the first post of this thread...
[http://ubuntuforums.org/showthread.php?t=1304532&highlight=karmic+upgrade+instructions](http://ubuntuforums.org/showthread.php?t=1304532&highlight=karmic+upgrade+instructions)

We are about to release a new System76 driver that will provide short-range wireless capabilities for the Starling until we are finished working on the full-scale fix. Please subscribe to the above post to be notified when the driver is released, along with instructions for installing it.

---

### Post by jbraswell on 2009-11-10
Ah, I'm sorry, I thought they were talking about 9.10.  I performed the above fix on 9.04, but I just got too eager on 9.10.  

Thanks

---

### Post by htismaqe on 2009-11-12
> **jbraswell said:**
> Ah, I'm sorry, I thought they were talking about 9.10.  I performed the above fix on 9.04, but I just got too eager on 9.10.  

Thanks

The workaround I mentioned above works on 9.04 as well, but you have to be able to configure a wireless connection - aka "see a network" - to do it.

If you can't see any connections at all, I would use the fix Thomas suggested for 9.04.

---

### Post by rectagonal on 2009-11-12
> **thomasaaron said:**
> A few more days (business days). 

Not to be too impatient. But do we have any ETA yet ? My Starling is actually my primary machine believe it or not. I was really hoping to show off Karmic to all the Windows 7 users nearby, by now.

---

### Post by xtopher85 on 2009-11-12
Glad i dual boot...

---

### Post by thomasaaron on 2009-11-12
> Not to be too impatient. But do we have any ETA yet ?

Certainly nobody can blame you for being impatient! :D

I'll check on it tomorrow when the R&D guy gets here.

---

### Post by Vrekk on 2009-11-13
Yes! there was an update for the driver got updated,  I ran it and my wireless is running!  :D

EDIT: Never mind i was just close to my router, :|

---

### Post by thomasaaron on 2009-11-16
Yes. It is an interim solution until we can finish with the real fix.

---

### Post by thomasaaron on 2009-11-18
For further information, please subscribe to...
[http://ubuntuforums.org/showthread.php?t=1330531](http://ubuntuforums.org/showthread.php?t=1330531)

---

