---
title: "Not the end of Unity"
date: 2017-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2017-04-06
The current 17.04 version of ubuntu-desktop uses unity7 DE on Gnome (Gtk 3.22.11-0ubuntu2). Mark did not say Unity7 was dead so it will still be unity7 for development. Since their seems to be some confusion on this I had sent an e-mail requesting a clarification on this matter as it concerns development. When I hear of news I'll get back.

Regards..

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.10.0-15-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome  (Gtk 3.22.11-0ubuntu2)
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: desktop Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.19.3 drivers: nouveau (unloaded: modesetting,


```

---

### Post by terry_gardener on 2017-04-06
according to this statement it is "Community Manager Michael Hall confirmed to Ars that the Ubuntu phone and tablet project is over.

"Work on the phone and tablet is also ending, the whole convergence story, really," Hall said. "The desktop will continue, but like it was in the pre-Unity days where we took what upstream [developers] designed and developed."

---

### Post by ventrical on 2017-04-06
> **terry_gardener said:**
> according to this statement it is "Community Manager Michael Hall confirmed to Ars that the Ubuntu phone and tablet project is over.

"Work on the phone and tablet is also ending, the whole convergence story, really," Hall said. "The desktop will continue, but like it was in the pre-Unity days where we took what upstream [developers] designed and developed."

Yes . ."the desktop will continue". Unity8 .. kaput but ubuntu-desktop (unity7) will run on gnome.. unless I am missing something here. I hope to hear from other sources soon. Perhaps after the current 16.04 EOL they might phase out unity7 but I highly  think it is unlikely that we will have gnome3 as default for 18.04  but I am not 100% sure because the statements are not 100% clear, ie; (there will be no unity7 DE in 18.04) Until I see that specifically, I cannot believe otherwise.

Regards..

---

### Post by notso23 on 2017-04-06
From what I read is that Gnome will replace Unity on 18.04 version ... yes they said the phones etc are dead.

Is it a good idea or not to jump the gun and install Gnome 3 now ( is it another desktop environment?) 

Being a new user to Ubuntu I just am not sure what to do. I know wait and see but?

If I install Gnome 3 will it work beside Unity at the login?

[https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

---

### Post by Crimple on 2017-04-06
> **notso23 said:**
> Is it a good idea or not to jump the gun and install Gnome 3 now 
And why would you do that :confused:
Ubuntu 16.04 (with Unity 7) will be supported until 2021.

---

### Post by notso23 on 2017-04-06
This is the post that I read. I know that like the press, not all you read is true so I am not getting excited, just asking questions. Yes I like Ubuntu just the way it is.
[https://itsfoss.com/ubuntu-unity-shutdown/](https://itsfoss.com/ubuntu-unity-shutdown/)

This is near the bottom of the post.

> What will happen to Unity users? Will they have to migrate to GNOME starting Ubuntu 17.10 or 18.04?

---

### Post by Crimple on 2017-04-06
Ubuntu 16.04 will be supported until April 2021
[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by ventrical on 2017-04-06
I actually went ahead and updated my 17.04 installs /intel/nvidia/ graphics and unity8 *desktop* is now restored. The phone is gone but the desktop remains. Most of the xapps like firefox, gnome-disks, gnome-system-monitor, disk-usage-analyzer, nautilus are all working again.

---

### Post by mc4man on 2017-04-06
> **ventrical said:**
> I actually went ahead and updated my 17.04 installs /intel/nvidia/ graphics and unity8 *desktop* is now restored. The phone is gone but the desktop remains. Most of the xapps like firefox, gnome-disks, gnome-system-monitor, disk-usage-analyzer, nautilus are all working again.
Yeah, the fix to qtmir happened & was released..

---

### Post by Yellow Pasque on 2017-04-06
> **ventrical said:**
> ubuntu-desktop (unity7) will run on gnome.. unless I am missing something here. I hope to hear from other sources soon. Perhaps after the current 16.04 EOL they might phase out unity7 but I highly  think it is unlikely that we will have gnome3 as default for 18.04  but I am not 100% sure because the statements are not 100% clear, ie; (there will be no unity7 DE in 18.04) Until I see that specifically, I cannot believe otherwise.

I disagree. I expect Ubuntu to move to Gnome/Wayland for 17.10/18.04. Unity would not run unless they ported Compiz to be a Wayland compositor. That is the kind of labor-intensive reinvention of the wheel they're trying to get away from.

> Mark did not say Unity7 was dead so it will still be unity7 for development.
I don't see any commitment from Canonical to develop Unity7 further, other than security updates and possibly some bug fixes until 16.04 is EOL.

---

### Post by ventrical on 2017-04-06
> **Temüjin said:**
> I disagree. I expect Ubuntu to move to Gnome/Wayland for 17.10/18.04. Unity would not run unless they ported Compiz to be a Wayland compositor. That is the kind of labor-intensive reinvention of the wheel they're trying to get away from.


I don't see any commitment from Canonical to develop Unity7 further, other than security updates and possibly some bug fixes until 16.04 is EOL.

I can see it all now... Awesome Aardvark .. on tap :)

Really . thanks for helping me see the light... it will be interesting... its always interesting.

Regards..

---

### Post by ventrical on 2017-04-07
> **ventrical said:**
> Yes . ."the desktop will continue". Unity8 .. kaput but ubuntu-desktop (unity7) will run on gnome.. unless I am missing something here. I hope to hear from other sources soon. Perhaps after the current 16.04 EOL they might phase out unity7 but I highly  think it is unlikely that we will have gnome3 as default for 18.04  but I am not 100% sure because the statements are not 100% clear, ie; (there will be no unity7 DE in 18.04) Until I see that specifically, I cannot believe otherwise.

Regards..

I am assured that unity7 may be available in the universe during 18.04 cycle. If this does turn out to be the case then unity7 support and bug fixes will extend beyond the current LTSes EOL. I think the market and community input will ultimately govern this. As for Gnome becoming default - yes this has been explained to me a little more clearly.

Regards..

---

### Post by ^83%u#@^ on 2017-04-07
> **ventrical said:**
> Mark did not say Unity7 was dead so it will still be unity7 for development. 



Unity 7 is already obsolete DE, it needs major improvements, but how we know unity 8 was officialy dead. It is very hard to continue unity 8 development by community. Another 3-5 years will be wasted

---

### Post by jbicha on 2017-04-07
> **ventrical said:**
> I am assured that unity7 may be available in the universe during 18.04 cycle.

Unless you've been told otherwise, my guess it that it actually will not be available in Ubuntu 18.04 itself. This is pure speculation on my part and I've not looked into it very deeply at all. But unity7 is a large stack to maintain and from my perspective, it seems clear that Canonical does not want to be responsible for it at all in any Ubuntu release after 17.04.

Various patches required for Unity to work may be dropped. Upgrades to other packages may break other parts. Remember, there was good reason why Canonical delayed GNOME updates, but if GNOME is the flagship Ubuntu, it seems to wrong to hold it back for a fledgling community-supported flavor.

The community is welcome to create a PPA if more invasive packaging is necessary. And if it ends up that unity7 is 1) independently maintained and 2) maintained in Ubuntu without causing problems for GNOME, I don't think we're opposed to having a new unity7 flavor of Ubuntu.

---

### Post by ventrical on 2017-04-07
> **jbicha said:**
> Unless you've been told otherwise, my guess it that it actually will not be available in Ubuntu 18.04 itself. This is pure speculation on my part and I've not looked into it very deeply at all.

I have been told otherwise. Mark brought it up, that it (unity7)  *may* be available in the universe during 18.04. It is also hoped that the other shell extensions will adopt some of the ideas that went into creating unity.

Regards..

---

### Post by ventrical on 2017-04-07
> **jbicha said:**
> 
The community is welcome to create a PPA if more invasive packaging is necessary. And if it ends up that unity7 is 1) independently maintained and 2) maintained in Ubuntu without causing problems for GNOME, I don't think we're opposed to having a new unity7 flavor of Ubuntu.

If there are enough volunteers and some innovative brain storming then perhaps it may not be so difficult to prevent any interference to gnome. Well.. even if perhaps gnome adopted some of the keen and basic ideas that went into building unity - ah .. it's concept and user_friendly desktop interface then there may not be a need to maintain unity7 in the universe. It's a bridge we will eventually have to cross.

Regards..

---

### Post by Crimple on 2017-04-07
> **ventrical said:**
>  It is also hoped that the other shell extensions will adopt some of the ideas that went into creating unity.
Already done.
With Dash to Dock you can recreate Unity's launcher easily.
I just hope Canonical teams up with the devs of some of the best extensions instead of replicating them.

---

### Post by ventrical on 2017-04-07
> **Crimple said:**
> Already done.
With Dash to Dock you can recreate Unity's launcher easily.
I just hope Canonical teams up with the devs of some of the best extensions instead of replicating them.

I am not sure this is exactly what I mean.  I don't think recreating the launcher is incorporating the more fundamental ideas behind unity ... uh .. ie; splotching thumbnails and shortcuts to a stationary desktop. I am not trying to be curt or cheeky but gnome3 gives me one E'll of a migraine :)

Regards..

---

### Post by jbicha on 2017-04-07
I've never heard the technical term "splotching thumbnails to a stationary desktop" before. :lol: Could you explain in more detail what that means to you?

---

### Post by ventrical on 2017-04-07
eh . ehehehe :) I really get moving sometimes .. and I know where everything is..

---

### Post by mc4man on 2017-04-07
> **Crimple said:**
> Already done.
With Dash to Dock you can recreate Unity's launcher easily.
I just hope Canonical teams up with the devs of some of the best extensions instead of replicating them.
D2D is ok though it should really support DnD. It's better than the default dock but no where as nice or useful as unity's..

---

### Post by sgage on 2017-04-08
> **notso23 said:**
> From what I read is that Gnome will replace Unity on 18.04 version ... yes they said the phones etc are dead.

Is it a good idea or not to jump the gun and install Gnome 3 now ( is it another desktop environment?) 

Being a new user to Ubuntu I just am not sure what to do. I know wait and see but?

If I install Gnome 3 will it work beside Unity at the login?

[https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

Gnome is a whole software stack and Desktop Environment. Many other DE's/Window Managers run 'on top of Gnome' or use components of its plumbing. The actual Gnome User Interface is called Gnome Shell, but you can install just about any other DE/Window Manage alongside it, and select that environment at login time.

As far as I know, Unity uses a lot of the Gnome Stack.

People often use 'Gnome' and 'Gnome Shell' interchangably, so you have to pick up the intent from the context of the discussion. You may have noticed that there are many 'flavors' of Ubuntu available: Kubuntu (KDE), Xubuntu (XFCE), etc. One of them is Ubuntu Gnome, which uses Gnome Shell. It is very good, IMO, though I'm a MATE guy :-)

I believe if you just type 'sudo apt install gnome-desktop' at a command prompt, you will have the Gnome Shell environment installed. But you will still have Unity - you would select between them at login time.

---

### Post by izznogooood on 2017-04-09
> **sgage said:**
> I believe if you just type 'sudo apt install gnome-desktop' at a command prompt, you will have the Gnome Shell environment installed. But you will still have Unity - you would select between them at login time.

A word of advice, if you choose to run GDM this messes with your theme settings, amongst others.

---

### Post by thehannibal on 2017-11-13
> **Crimple said:**
> And why would you do that :confused:
Ubuntu 16.04 (with Unity 7) will be supported until 2021.

So I'm safe with Ubuntu 16.04 till 2021, I mean Unity7 updates will keep on coming and I don't have to change a thing right ?

---

### Post by cariboo on 2017-11-13
> **thehannibal said:**
> So I'm safe with Ubuntu 16.04 till 2021, I mean Unity7 updates will keep on coming and I don't have to change a thing right ?

You won't get anything new, just security updates.

---

### Post by ventrical on 2017-11-13
> **cariboo said:**
> You won't get anything new, just security updates.

It appears that unity7 will become official flavor but I do not have 100% confirmation atm. Will keep all posted.

Regards..

---

### Post by thehannibal on 2017-11-13
> **cariboo said:**
> You won't get anything new, just security updates.

At-least I can be assured of security, It doesn't matter whether there will other updates or not (for me I mean). I like Unity7 as it is.

---

### Post by thehannibal on 2017-11-13
> **ventrical said:**
> It appears that unity7 will become official flavor but I do not have 100% confirmation atm. Will keep all posted.

Regards..

Do you have a link of Article/Repo that indicates towards this because currently :

1> Artemis (Unity7 fork) : [https://github.com/artemis-project/artemis](https://github.com/artemis-project/artemis) is blank.

2> Yunit (Unity8 fork) : [https://github.com/yunit-io/yunit](https://github.com/yunit-io/yunit) is going strong.

If you have a Official Flavor link do mind sharing.

---

### Post by Chanath on 2017-11-13
> **thehannibal said:**
> Do you have a link of Article/Repo that indicates towards this because currently :

1> Artemis (Unity7 fork) : [https://github.com/artemis-project/artemis](https://github.com/artemis-project/artemis) is blank.

2> Yunit (Unity8 fork) : [https://github.com/yunit-io/yunit](https://github.com/yunit-io/yunit) is going strong.

If you have a Official Flavor link do mind sharing.

You can catch the first try of ubuntu-unity-amd64.iso here, [https://people.ubuntu.com/~twocamels/](https://people.ubuntu.com/~twocamels/)
and, read about it here, [https://community.ubuntu.com](https://community.ubuntu.com)

and, they are all Ubuntu websites.

---

### Post by ventrical on 2017-11-13
> **thehannibal said:**
> Do you have a link of Article/Repo that indicates towards this because currently :

1> Artemis (Unity7 fork) : [https://github.com/artemis-project/artemis](https://github.com/artemis-project/artemis) is blank.

2> Yunit (Unity8 fork) : [https://github.com/yunit-io/yunit](https://github.com/yunit-io/yunit) is going strong.

If you have a Official Flavor link do mind sharing.

I am awaiting the next steps. It will most likely be up on the qa/tracker at some point. I had built a stock remix for 18.04 and have permissions to distribute from CL. Others in the community are working behind the scenes so when I hear anything I'll post it. You can use the link Chanath provided to give it a test spin and just keep updating it throughout the cycye. Keep in mind it is in development and can be prone to breakage just like the other flavors.
[https://wiki.ubuntu.com/U+1/tester-wiki#New_Beta_Testers_Warnings](https://wiki.ubuntu.com/U+1/tester-wiki#New_Beta_Testers_Warnings)

---

### Post by thehannibal on 2017-11-13
> **ventrical said:**
> I am awaiting the next steps. It will most likely be up on the qa/tracker at some point. I had built a stock remix for 18.04 and have permissions to distribute from CL. Others in the community are working behind the scenes so when I hear anything I'll post it. You can use the link Chanath provided to give it a test spin and just keep updating it throughout the cycye. Keep in mind it is in development and can be prone to breakage just like the other flavors.
[https://wiki.ubuntu.com/U+1/tester-wiki#New_Beta_Testers_Warnings](https://wiki.ubuntu.com/U+1/tester-wiki#New_Beta_Testers_Warnings)

Thanks for the Heads Up. I will try [https://community.ubuntu.com/t/test-daily-current-ubuntu-unity-amd64-iso/1685](https://community.ubuntu.com/t/test-daily-current-ubuntu-unity-amd64-iso/1685) in a Live CD if possible at a later time and share my experience. Great Job whoever is trying to keep Unity7 alive for 18.04

---

### Post by slickymaster on 2017-11-14
Taking in consideration that it's not about an official flavor and its start date, I'm moving this thread here from the **Ubuntu Development Version**&#8203;.

---

### Post by belkinsa on 2017-11-16
As a late comer to the thread, I'm pleased that Unity 7 will be an official favor.  Looking into the future, I think it would be fine to use some of the GMONE programs (for example the Software Center (coming from the the daily testing thread)) as there would be more upstream development on them.  As for the Center itself, that would mean that the built in repos would be close to current to the main Ubuntu. Maybe that could be another thread though.

---

### Post by QIII on 2017-11-16
Despite the wishful thinking,  for Ubuntu with Unity to be an official flavor its developers will need to go through the same rigorous process as any other candidate to be approved.

---

### Post by belkinsa on 2017-11-16
Oh, I guess I read something wrong.

---

### Post by ventrical on 2017-11-17
> **belkinsa said:**
> Oh, I guess I read something wrong.

Hi belkinsa,

Good to see you finally make it :)

Regards..

Dale

---

### Post by belkinsa on 2017-11-18
Thanks, I will try to be active.  I have a hard time following sometimes.

---

