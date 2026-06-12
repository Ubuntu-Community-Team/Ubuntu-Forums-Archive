---
title: "XP+No Dx10"
date: 2007-07-06
forum: Windows
---

### Post by gwoodard on 2007-07-06
Can anyone tell me (or explain) why microsoft is to lazy or stubborn to make a version of DX 10 for XP?  (Main Reason:  Vista is needed for Halo 2 or other new games)

---

### Post by jinx099 on 2007-07-06
because MS wants you to buy Vista

---

### Post by smoker on 2007-07-07
> **jinx099 said:**
> because MS wants you to buy Vista

true, and unfortunately that is why sp3 for xp seems to be put on the backburner also:(

---

### Post by insane_alien on 2007-07-07
because then gamers would have no reason to upgrade.

---

### Post by Epilonsama on 2007-07-07
Isnt it obvious, Micro$oft wats you to buy Vi$ta

---

### Post by justin1278 on 2007-07-08
If MS doesn't release DX10 for Vista then all gamers must upgrade to Vista to play the latest games. Which means more money for MS if gamers must upgrade..

---

### Post by Depressed Man on 2007-07-08
Yep, pretty much the main reason (money). Though there probably is some physical reason why it can't be done in XP too. Though there is a group that was making progress in emulating DX10 on XP that I read about on the Aero experience forums I think. Though even if they got it completly working it would still be slow.

---

### Post by FoolsGold_MKII on 2007-07-08
> **Depressed Man said:**
> Yep, pretty much the main reason (money). Though there probably is some physical reason why it can't be done in XP too. Though there is a group that was making progress in emulating DX10 on XP that I read about on the Aero experience forums I think. Though even if they got it completly working it would still be slow.
I think you mean "technical reason", not "physical". :)

Which in any case is BS. Microsoft could backport DX10 to Windows XP if they wanted to, heck it's their damn OS! But no, that would limit a lot of justification for moving to Vista in the first place.

---

### Post by gwoodard on 2007-07-15
> **FoolsGold_MKII said:**
> I think you mean "technical reason", not "physical". :)

Which in any case is BS. Microsoft could backport DX10 to Windows XP if they wanted to, heck it's their damn OS! But no, that would limit a lot of justification for moving to Vista in the first place.

good point about that... but what if, oh I don't know someone sued or "forcibly" bought Microsoft out (due to the fact that microsoft are thieves and don't care what people's opinions) that they would have to make a DX 10 for XP (This is a BIG if and only an opinion)

---

### Post by cmat on 2007-07-16
Ever read about DirectX 9L? It gives XP users the features of DirectX 10. Why they don't call it DirectX 10 is beyond me. But I think it's not fully featured like DirectX 10

---

### Post by Depressed Man on 2007-07-16
Oh and DX10 (somewhat) on XP.

[http://www.fallingleafsystems.com/](http://www.fallingleafsystems.com/)

---

### Post by digital_exhaust on 2007-07-16
> **cmat said:**
> Ever read about DirectX 9L? It gives XP users the features of DirectX 10. Why they don't call it DirectX 10 is beyond me. But I think it's not fully featured like DirectX 10

That's not exactly accurate. DX9L is a compatibility layer for XP that will allow DX10 games to run in XP...in DX9 mode. It is not, in any way DX10 for XP.

---

### Post by hobieone on 2007-07-18
yes halo2 requires dx 10 only other thdoes or will require it is all ms game.  looking at what at e3  very few new games comming out  requires it most dev are making themprimarirly dx 9 for compatibilty reasons  and some  are even thnk ing of open gl over dx  due to the screenies  of the new unreal tournament  that based on open gl   which blows the dorrs off halo 2 as far as looks and details go  plus it 'll be  for multiple platforms. way i see it direct x time is starting to run out as it is comming more evident  that a proper standard is waht is needed when it comes to game  such as  new vew opengl proticols can accomplish the same features as direct x  the new unreal proves this. plus open thing up for easly dev games for mutiple platforms verus just one. ther by increasing the cutomer base  for these companies  and other gammining companies are starting to see this  and that is why your not going to see  very many dx 10 only game and why there are not that many in development  if look closley most that do say for dx 10  in fine print  it actually is dx 10 compatible and will use it if you have the equipment.  they just display it for dx 10  just to satisfy ms  to win approvaql that they can say their product is for ms  os

---

### Post by gwoodard on 2007-07-24
> **cmat said:**
> Ever read about DirectX 9L? It gives XP users the features of DirectX 10. Why they don't call it DirectX 10 is beyond me. But I think it's not fully featured like DirectX 10

Sorry dude, Microsoft has put that on the backburner as well (grumble...) and are not going to listen to other people than Bill Kills (I mean Gates lol)

---

### Post by izanbardprince on 2007-07-25
> **digital_exhaust said:**
> That's not exactly accurate. DX9L is a compatibility layer for XP that will allow DX10 games to run in XP...in DX9 mode. It is not, in any way DX10 for XP.

Actually DirectX 9L (L stands for LONGHORN) is a version of DirectX 9 that has been modified to use Vista's new driver model, hence giving existing games a way to run on Windows Vista, Aero Glass also uses DirectX 9L to allow the new interface to work on cards that are not DirectX 10 compliant.

As much as I hate to say it, Microsoft does have a very valid reason to not backport DirectX 10 to XP, as they'd need to rewrite something that probably borders on half the DirectX 10 API so it would work with XP's driver model.

The changes made to Vista's driver framework were not trivial, they're running in User Space instead of Kernel Space, that means that if something crashes a driver, it's like there's a "blast door" separating the kernel from the driver, meaning that Vista can just restart the affected subsystem and carry on, it also lets Vista intentionally initiate a crash of say, the video subsystem, if it thinks you're trying to make a copy of "protected content", AKA an HD-DVD or a Blu Ray Disc.

Besides all the work that would be involved in backporting DirectX 10, it's just not worth paying for man hours for a project to improve an operating system that they're not ever going to make another dime on (XP), and without DirectX 10, Vista essentially amounts to a new skin for XP and a "Protected Mode" for Internet Explorer, which has already been compromised.

---

### Post by darksong on 2007-07-25
Wiith a few tweaks you can get halo 2 and other Vista games to work on XP.

---

### Post by izanbardprince on 2007-07-25
> **darksong said:**
> Wiith a few tweaks you can get halo 2 and other Vista games to work on XP.

Considering that Halo 2 depends on DirectX 10, which is exclusive to Vista, thats not going to happen.

And there won't be some stupid hack to "trick" DirectX 10 to install on XP, it just wouldn't work.

---

### Post by Depressed Man on 2007-07-25
err.. it's already possible to do that. Granted the method is pretty sloppy. But hey, Halo 2 is playable in DX9 (no multiplayer though since I think that requires authentication by Microsoft). 

I think what people are trying to do is not trick DX10 to install on XP. But rather reverse engineer it so it works (which is likely illegal anyway).

---

### Post by izanbardprince on 2007-07-25
> **Depressed Man said:**
> err.. it's already possible to do that. Granted the method is pretty sloppy. But hey, Halo 2 is playable in DX9 (no multiplayer though since I think that requires authentication by Microsoft). 

I think what people are trying to do is not trick DX10 to install on XP. But rather reverse engineer it so it works (which is likely illegal anyway).

Depends on how they go about doing it.

Clean room reverse engineering is legal, that is how WINE has been developed, they take the API's, look at how to interact with the Windows kernel, and come up with a work-alike, thats what Linux itself is, a UNIX workalike.

It should be ok, as long as they don't actually use any of Microsoft's source code.

---

### Post by gwoodard on 2007-07-25
> **izanbardprince said:**
> Depends on how they go about doing it.

Clean room reverse engineering is legal, that is how WINE has been developed, they take the API's, look at how to interact with the Windows kernel, and come up with a work-alike, thats what Linux itself is, a UNIX workalike.

It should be ok, as long as they don't actually use any of Microsoft's source code.

Good Point...

---

