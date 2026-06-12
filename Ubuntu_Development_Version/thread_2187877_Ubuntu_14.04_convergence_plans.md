---
title: "Ubuntu 14.04 convergence plans"
date: 2013-11-14
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2013-11-14
Ubuntu On Air has a Jono Bacon video called Ubuntu 14.04 Convergence Plans. I am watching it now.

[http://ubuntuonair.com/](http://ubuntuonair.com/)

UPDATE:

One thing I picked out was that 14.04 will have a login option to run Mir + Unity 8. Here is a better breakdown on what was said.

[http://www.omgubuntu.co.uk/2013/11/ubuntu-tablet-will-key-focus-ubuntu-14-04-lts-cycle](http://www.omgubuntu.co.uk/2013/11/ubuntu-tablet-will-key-focus-ubuntu-14-04-lts-cycle)

Regards.

---

### Post by ventrical on 2013-11-14
> 
Work on **improving ‘side-stage’,** the Windows 8-like  feature for running two applications on screen side-by-side, will also  get underway. To make use of this, many of Ubuntu’s core apps will be  adapted to become “convergent” – better able to make use of larger  screens and tablet workflows.


Iv'e been testing Win 8 across various form factors , ie; desktops,  and it does not blacklist older legacy graphics cards. The 'side-stage' effect works well  (as I commented somewhere before)  and definitely has faster bootup times so I am just curious as to how Canonical are going to dig themselves out of this hole.

 I'm not advocating Windows 8, I'm just pointing out a factual advantage that currently exists with that OS and brings up a follow up question .. Why now ?

Regards..

---

### Post by grahammechanical on 2013-11-14
As I understand it attention is now switching to optimising Ubuntu on tablets and this feature is better suited to wider screen sizes. So, it is time to make this feature work. It seems to me that Ubuntu will have one significant advantage over Microsoft. That is a converged code base used on all form factors. The advantage being in needing fewer developers to maintain and develop the code. This is very important to a small company like Canonical. I am not saying that Canonical can compete with Microsoft but that Microsoft will not find it easy to give users the same user interface experience across these devices. And that is the challenge that Ubuntu has taken up.

I think that the idea of a mobile device emulator as part of the SDK is most interesting. Another challenge I think. It might make testing on the desktop more interesting?

Regards.

---

### Post by ventrical on 2013-11-14
> **grahammechanical said:**
> As I understand it attention is now switching to optimising Ubuntu on tablets and this feature is better suited to wider screen sizes. So, it is time to make this feature work. It seems to me that Ubuntu will have one significant advantage over Microsoft. That is a converged code base used on all form factors. The advantage being in needing fewer developers to maintain and develop the code. This is very important to a small company like Canonical. I am not saying that Canonical can compete with Microsoft ... 

I am sorry to say but I agree 100%. Not only can Canonical not compete with new Windows 8, it buries them! I just did an install of Win8  on a desktop Tower which has onboard ATi Radeon x400.  Not even  Ubuntu Unity 2D will operate on that video form factor. 



> 
It might make testing on the desktop more interesting?

Regards.

With all due respect, I disagree. When you see what Windows 8 'side stage' can do on legacy graphics adapter cards (that are now all obsoleted by Ubuntu Unity/Mir) you'll see that,  as far as Ubuntu Desktop is concerned, .. it will be a tough job.

Regards

---

### Post by grahammechanical on 2013-11-14
@ventrical

No offence taken. When I made that comment I was actually thinking about having an emulator on the desktop that emulates mobile devices and lets us test the mobile apps as if we were actually running one of those devices. I had moved away from the subject of Windows 8.

I guess I will just have to knuckle down and install that developer preview version of Windows 8 that I picked up. I will have to use the 32 bit version as my machine does not meet the recommended 2 GB RAM for the 64 bit version. I now have a second hard disk so I no longer worry about Windows taking over the whole drive. I could, of course, let Windows 8 install to the whole disk and then test the Ubuntu install alongside option.

Regards.

---

### Post by ventrical on 2013-11-14
> **grahammechanical said:**
> @ventrical

No offence taken. When I made that comment I was actually thinking about having an emulator on the desktop that emulates mobile devices and lets us test the mobile apps as if we were actually running one of those devices. I had moved away from the subject of Windows 8.


  That's exactly what I am talking about and exactly what I have been expecting (since raring) and we had some ?? inklings or reasonable faxsimilies thereof with  Ubuntu Calendar and Calculator etc. 


  I am still hoping that as trusty develops with Mir that we will get exactly what you have mentioned ..a mobile emulator on our desktops. That emulator was once already  part of the Unity Desktop. It was called Unity 2D (currently available in Precise) and somebody(s) decided to brick it. And to this day they still have not been able to get Unity 3D to smooth scroll  the apps like Unity 2D did which was the closest thing to a mobile emulator for Ubuntu that  I have seen.  But guaranteed ubuntu touch smooth scrolls on tablets. 


Regards..

---

### Post by cariboo on 2013-11-14
All this talk of Windows 8 is moving this thread off topic. We are here to discuss the development of Trusty, not compare it to that other operating system.

---

### Post by ventrical on 2013-11-14
> **cariboo907 said:**
> All this talk of Windows 8 is moving this thread off topic. We are here to discuss the development of Trusty, not compare it to that other operating system.



 I took the reference from one of the links graham provided:

```


Work on **improving ‘side-stage’,** the Windows 8-like  feature for  running two applications on screen side-by-side, will also  get  underway. To make use of this, many of Ubuntu’s core apps will be   adapted to become “convergent” – better able to make use of larger   screens and tablet workflows. 			 		


```

which was provided by  Canonical's Jono Bacon and I think the discussion is very topical  as these "Windows 8-like feature"  - "get underway", otherwise we cannot fairly discuss critical comments during the cycle - so- to have a fair understanding of what Jono is refering to when he makes his "Windows 8-like features" I think it important that others  have a general idea of what those features are but, if you would rather  have end_users google these features on thier own then I will be more that happy to accomodate your notion that it is not topical  and cease and desist from discussing  it further. However, if we do not  bring in current and new trends from other OSes that are currently under development then we become insular and stagnant and it robs from the effervescence of the discussion process.

Regards..

---

### Post by cariboo on 2013-11-14
I agree Jono did reference a Windows like feature, but you are getting a little of topic with your discussion of viewing 3D content in Windows, especially when there hasn't been any mention of that type of function from the graphics driver creators.

Jono's comment was about running two applications side by side on the same tablet screen, which isn't possible with either Android or IOS, I personally haven't seen any Windows tablets here (in Williams Lake) that have that function, but with a very little bit of searching, I found a how-to [here]("http://www.techulator.com/resources/5147-how-enable-windows-snap-feature.aspx"). It looks like it isn't a part of the default install, as you have to download an addon, and have to have a high resolution monitor. I'd say more power to the developers, if they can get this feature to work on a default tablet installation.

I have nothing against discussion specific functions, but wide ranging comments that aren't about the thread topic, just don't belong in threads in this sub-forum.

---

### Post by ventrical on 2013-11-14
> **cariboo907 said:**
> I agree Jono did reference a Windows like feature, but you are getting a little of topic with your discussion of viewing 3D content in Windows, especially when there hasn't been any mention of that type of function from the graphics driver creators.
.

My apologies .. I was just having a little fun ;)


Best Regards..

---

### Post by ventrical on 2013-11-21
Mark Shuttleworth explained convergence  thoughtfully with this brief snippet;

"It is a tough job .. you know .. bridging the needs and the passions and enthusiasms of so many different parts of the community is challenging. It requires highly resolved ... or .. Firm Resolve! and great judgment about people and an ability to lead and make decisions."

Regards..

---

### Post by ventrical on 2013-11-22
Just a side note on "side stage".. I had wrongly assumed that Jono was including desktops in the convergence plan also but, after reveiwing Mark's keynote again and also looking at Jono's statement .. I see now that this is for tablets/phones exclusively , although the tools will be in the repos and we can still experiment with mir? unity-system-co .. etc..


Regards..

---

### Post by ventrical on 2013-11-22
> **grahammechanical said:**
> @ventrical

No offence taken. When I made that comment I was actually thinking about having an emulator on the desktop that emulates mobile devices and lets us test the mobile apps as if we were actually running one of those devices. 

Regards.

As so here it is :)

---

### Post by grahammechanical on 2013-11-22
@ventrical

Are you tempting me to go off topic? :) How did you get that?  A couple of hours ago I put in a fresh trusty install and followed the instructions here

[https://wiki.ubuntu.com/Touch/Emulator](https://wiki.ubuntu.com/Touch/Emulator)

And it worked. I got a panel with a key pad and some VCR type controls but I could not work out how to use the thing.

Regards.

---

### Post by ventrical on 2013-11-22
> **grahammechanical said:**
> @ventrical

Are you tempting me to go off topic? :) How did you get that?  A couple of hours ago I put in a fresh trusty install and followed the instructions here

[https://wiki.ubuntu.com/Touch/Emulator](https://wiki.ubuntu.com/Touch/Emulator)

And it worked. I got a panel with a key pad and some VCR type controls but I could not work out how to use the thing.

Regards.

:)

I went to synaptic and typed in unity8 and then installed it and all the other files with it. Then, reboot. Then type in:

```

unity8

```

in terminal. You will see a lot of verbose stuff scroll by .. but the mobile phone will come up and some of the apps work already ! :)

I'll take a look at that link.

 Moi  :) .. off topic? :) lol

---

### Post by ventrical on 2013-11-22
I log in to terminal after the 'phablet' shows up and then it does nothing. Followed directions from link you posted.

---

### Post by neu5eeCh on 2013-11-22
> **ventrical said:**
> I am sorry to say but I agree 100%. Not only can Canonical not compete with new Windows 8, it buries them! I just did an install of Win8  on a desktop Tower which has onboard ATi Radeon x400.  Not even  Ubuntu Unity 2D will operate on that video form factor. 

I'm interested in installing and beta-ing 14.04 when the first ISOs come out (did it for 12.04). Is there a list, in the meantime, of which ATI cards Unity8/Mir has blacklisted?

---

### Post by grahammechanical on 2013-11-23
> [COLOR=#000000]Is there a list, in the meantime, of which ATI cards Unity8/Mir has blacklisted?[/COLOR]

I do not know of such a list but from experiments during the saucy cycle (mainly by Ventrical) Xmir works great on Nouveau but not so great on proprietary video drivers. It usually does not load. In fact in Trusty it is Xmir that is blacklisted not to load by default. Here is the thread where we discuss Xmir on Trusty. Note that we now install the ubuntu-desktop-mir package.

[http://ubuntuforums.org/showthread.php?t=2186679](http://ubuntuforums.org/showthread.php?t=2186679)

There is also a Unity 8 in Trusty thread here.

[http://ubuntuforums.org/showthread.php?t=2189491](http://ubuntuforums.org/showthread.php?t=2189491)

Regards.

---

### Post by ventrical on 2013-11-23
I have an Acer Extensa 4420 with Radeon Express 1250.  I haven't tried trusty on that yet but I have been having problems with older ATi cards.. mostly anything under 1250 and under 256MB of RAM. I do not know of any obsolete list either but for sure there is one as proven out by all the ATi graphic adapter cards that now do not work (starting with saucy) and those nipped at the bud with raring.  But ,if I understood correctly, I think Mark said something about hardware and open stack .. etc... and whether or not older hardware is to be included, we will have to see.

edit:

  A side note here . I tried to load  the trusty iso and on ATi RadeonX1250 and I got the same error as I did with saucy . Verbose scripts with  one line echoing ::radeon registered panic notifier::  . Upon warm boot it will correct itself and load up the live session. It will also work after a hard boot. The thing is I am using read only .iso (discard on shutdown)  So I am not exactly sure how this is being corrected in the .iso  It can be perhaps that the .iso is 'flipping a bit" during load-up in BIOS so that a depend is met and  the panic notifier is no longer called.  What this has to do with convergence? It may be a more efficient method of jockeying in older hardware to meet depends for open-source drivers. I am assuming this atm but haven't documented it as of yet.

 Regards..

---

### Post by ventrical on 2013-11-23
Looks like convergence with hardware and openstack in on the fast-track because I just got an instal that rendered Unity 3D where it would not before on previous versions, after updating the trusty daily.

```

01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)
ventrical@ventrical-P4M266A-8237:~$ 

```

---

