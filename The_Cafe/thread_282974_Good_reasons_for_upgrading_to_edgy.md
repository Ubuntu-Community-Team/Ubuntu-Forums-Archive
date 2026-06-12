---
title: "Good reasons for upgrading to edgy?"
date: 2006-10-23
forum: The Cafe
---

### Post by nickle on 2006-10-23
I checked out the new edgy release yesterday. As a "normal" user, I couldn't see much difference to Dapper. Now I know there is meant to be plenty of new stuff "under the hood", but is it a good reason to update?
This thread is not meant to be provocative and not meant to run down the work put into the release, but the differences to dapper seem minimal. Now that may be a good thing if many bugs have been fixed, but luckily, I have not suffered much from these in my set up. The upgrade to Dapper was certainly worthwhile, does the same apply for edgy?

---

### Post by mostwanted on 2006-10-23
New artwork, better power management (laptop owner pet issue), newer versions of most programs (Banshee and Monodevelop work properly for me now!), supposed to be faster, newer kernel.

---

### Post by insane_alien on 2006-10-23
slightly faster in normal use. if your happy with dapper, stay with it until feisty fawn. but it doesn't really matter too much if you decide to go for edgy since its just as stable(i've not had it crash seriously yet) as dapper for normal use. it would make upgrading to feisty easier in future as well

---

### Post by bruce89 on 2006-10-23
The (fairly up-to-date) list of new things is here - [https://wiki.ubuntu.com/EdgyEft/Beta](https://wiki.ubuntu.com/EdgyEft/Beta) (They have changed the artwork)

---

### Post by .t. on 2006-10-23
It's great! It has AIGLX on by default, which is a plus for eye-candy lovers...

---

### Post by skymt on 2006-10-23
> **.t. said:**
> It's great! It has AIGLX on by default, which is a plus for eye-candy lovers...

I should clarify this, to avoid confusion: AIGLX is on by default, but you still need Beryl or Compiz to enable the eye candy. Many people think XGL and AIGLX are responsible for the shadows and wobbly windows.

Also, AIGLX doesn't work with the current stable nVidia drivers. It works with the beta drivers, but they're obviously less stable.

---

### Post by .t. on 2006-10-23
Since we're into clarifying things, doesn't nVidia provide their own AIGLX infrastructure in the beta drivers? They don't use the X.org system, but having their own still means that Xglx isn't needed any more.

The stable drivers didn't have any AIGLX set-up, so needed to be used with Xglx (what is commonly referred to as XGL).

---

### Post by taurus on 2006-10-23
Because you just want to be cool, using the latest release!!!  :mrgreen:

---

### Post by weasel fierce on 2006-10-23
Is it reasonably safe to dist-upgrade now, or should people hold off ?

---

### Post by maniacmusician on 2006-10-23
lmao, is it ever safe to dist-upgrade?

just kidding, I'm actually pretty interested in seeing how dist-upgrade goes for people. hopefully, they're working on making that better for people. So, anyone care to try and post back?

---

### Post by weasel fierce on 2006-10-23
hehe :)

It went horribly wrong the first time, the next two times went great. 

I need to get things backed up anyways, but Im itchy for something new :)

---

### Post by vayu on 2006-10-23
> **maniacmusician said:**
> lmao, is it ever safe to dist-upgrade?

just kidding, I'm actually pretty interested in seeing how dist-upgrade goes for people. hopefully, they're working on making that better for people. So, anyone care to try and post back?

I'm not in the you must do a fresh install camp.  I have three computers that all started with Hoary then Breezy and are currently running Dapper w Compiz.  They are all rock solid stable, and they have all the goodies and tricks I've added all along still intact.

The caveat: dependency issues, the installation sometimes needs some dpkg tricks, purging and reinstalling and such.

---

### Post by maniacmusician on 2006-10-24
I'm not in any camp at all :) i've just seen lots of people having problems with dist-upgrade. Is there a troubleshooting guide for the process somewhere? 

I'm doing a clean install this time, because I really need to, but I think it would be awesome for everyone to be able to easily dist-upgrade. For those with broadband connections, it's so much more convenient.

---

### Post by Somniis on 2006-10-24
I did a clean install of Dapper and upgraded to Edgy.  I didn't have any problems with it. :)

I would hope it is safe to upgrade, seeing as how it is so close to "official" release.

(Note: I should have mentioned this sooner, but I had to re-install Dapper because of an error with the upgrade to Edgy. :p  Dependency issues plagued it, but it was my own fault.)

---

### Post by mips on 2006-10-24
> **Somniis said:**
> I did a clean install of Dapper and upgraded to Edgy.  I didn't have any problems with it. :)


Why would you want to do that ? Is it not easier to simply download a edgy iso than jumping through 2 hoops to achieve a not so predictable result.

How much bandwidth does a dist upgrade use ? Pretty sure it's more than downloading a iso.

---

### Post by Circus-Killer on 2006-10-24
> **skymt said:**
> I should clarify this, to avoid confusion: AIGLX is on by default, but you still need Beryl or Compiz to enable the eye candy. Many people think XGL and AIGLX are responsible for the shadows and wobbly windows.

Also, AIGLX doesn't work with the current stable nVidia drivers. It works with the beta drivers, but they're obviously less stable.

and also for ATI users, the ati drivers dont work either, and the only solution for that is resort going back to the open-source mesa drivers.

---

### Post by frodon on 2006-10-24
> **maniacmusician said:**
> lmao, is it ever safe to dist-upgrade?

just kidding, I'm actually pretty interested in seeing how dist-upgrade goes for people. hopefully, they're working on making that better for people. So, anyone care to try and post back?I did a dist-upgrades last week, the only conflicts i had to solve were due to the fact i installed compiz at the time and it installed some beta libraries (libcairo, libmesa, ...) so i just needed to downgrades these libraries to dapper and all went fine.

Basically i would say that the dist-upgrade works just fine and is safe.

Here is a sticky i created to list all the know bugs and workaround for edgy : [http://ubuntuforums.org/showthread.php?t=283364](http://ubuntuforums.org/showthread.php?t=283364)

To answer the original question :
It's worth to install edgy to have gnome 2.16 and the latest version of many softwares and it's worth the install especially for xorg 7.1 and the built-in aiglx which allow you to run beryl/compiz without Xgl which means without any bugs even with openGL accelerated apps.

---

### Post by nickle on 2006-10-24
Thanks all for the feedback.

I think I will hold off for the moment with the update, certainly until the final release and await the general feedback on the forum...

I guess part of the problem is that Dapper is so damn good already!!!!!:-D

---

### Post by ixus_123 on 2006-10-24
I'm holding off for the next version.

I'm happy with Dapper & have it set up nicely.  Last time I upgraded a few things broke and some programs wouldn't play nicely when others were on ther system.  Everything works now so I'll keep it like that.

Even when I usd an Apple Mac I'd only ever updrade every other release at most.

---

### Post by m.musashi on 2006-10-24
> **skymt said:**
> I should clarify this, to avoid confusion: AIGLX is on by default, but you still need Beryl or Compiz to enable the eye candy. Many people think XGL and AIGLX are responsible for the shadows and wobbly windows.

Also, AIGLX doesn't work with the current stable nVidia drivers. It works with the beta drivers, but they're obviously less stable.

How is AIGLX different from XGL? I have XGL and beryl. If I dist-upgrade will AIGLX and XGL both be running? Is that OK? Do I want AIGLX instead of XGL? Sorry for the questions but I have yet to figure all this out and you seem "in the know."

Thanks.

---

### Post by .t. on 2006-10-24
Xglx runs an OpenGL server as a client above the main, standard X server. It provides more overhead but the same features as both the X.org and nVidia AIGLX implementations. If you have an Intel or nVidia card - or a few ATIs - you should be using AIGLX. Otherwise, Xglx is the only choice. If you are in fact running on an nVidia, you will need the beta drivers to use their AIGLX system.

---

### Post by m.musashi on 2006-10-24
> **.t. said:**
> Xglx runs an OpenGL server as a client above the main, standard X server. It provides more overhead but the same features as both the X.org and nVidia AIGLX implementations. If you have an Intel or nVidia card - or a few ATIs - you should be using AIGLX. Otherwise, Xglx is the only choice. If you are in fact running on an nVidia, you will need the beta drivers to use their AIGLX system.

Thanks for the info. I have an nvidia card so I suppose that means I should use AIGLX. However, since I have GLX running now, would I uninstall this or just let AIGLX "take over"? I am using dapper but will upgrade to edgy this weekend after the final release. If edgy installs AIGLX will I have problems if I don't uninstall XGL before dist-updgrade?

Thanks.

---

### Post by .t. on 2006-10-24
There won't be problems, but you won't (so long as you are running the beta drivers) need Xglx any more. You can safely remove all that hackish-ness!

---

### Post by m.musashi on 2006-10-24
Sweet. Thanks.

---

### Post by Aberrix on 2006-10-24
Xorg 7.1 + Beryl + Beta Nvidia drivers = :D

I upgraded last Saturday and love it! no problems yet!

---

### Post by Circus-Killer on 2006-10-24
yeah, i must say, beryl has come along way since the first time i tried xgl + compiz. i hope the development keeps going that way, and ati catch up with composite support :P

---

