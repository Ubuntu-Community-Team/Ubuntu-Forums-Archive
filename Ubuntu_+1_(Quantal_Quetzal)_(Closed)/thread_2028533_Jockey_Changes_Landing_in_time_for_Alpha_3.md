---
title: "Jockey Changes Landing in time for Alpha 3"
date: 2012-07-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-07-18
Just a heads up, the work going on to change the way drivers are handled in ubuntu is landing very soon! It should land in time for alpha 3. I know this work is of interest to many of you.

[https://wiki.ubuntu.com/SoftwareAndUpdatesSettings#drivers](https://wiki.ubuntu.com/SoftwareAndUpdatesSettings#drivers)

---

### Post by dino99 on 2012-07-18
> **guitara said:**
> Just a heads up, the work going on to change the way drivers are handled in ubuntu is landing very soon! It should land in time for alpha 3. I know this work is of interest to many of you.

[https://wiki.ubuntu.com/SoftwareAndUpdatesSettings#drivers](https://wiki.ubuntu.com/SoftwareAndUpdatesSettings#drivers)

cant open that url (security: not verified)

---

### Post by balloons on 2012-07-18
> **dino99 said:**
> cant open that url (security: not verified)

Really? It's just the ubuntu wiki :-) I can see it even not logged in.

[https://wiki.ubuntu.com/SoftwareAndUpdatesSettings](https://wiki.ubuntu.com/SoftwareAndUpdatesSettings)

Sorry dino99!

---

### Post by philinux on 2012-07-18
Opens here just fine.

---

### Post by dino99 on 2012-07-18
no way here with midori on i386

[https://wiki.ubuntu.com/SoftwareAndUpdatesSettings](https://wiki.ubuntu.com/SoftwareAndUpdatesSettings)

Security unknown

The certificate is invalid or unknown

note: FF opens it smootly  :)

---

### Post by philinux on 2012-07-18
> **dino99 said:**
> no way here with midori on i386

[https://wiki.ubuntu.com/SoftwareAndUpdatesSettings](https://wiki.ubuntu.com/SoftwareAndUpdatesSettings)

Security unknown

The certificate is invalid or unknown

Better change browser then. It only a wiki page.

---

### Post by balloons on 2012-07-18
Here's a bit more info from the ubuntu-devel list:

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html)

It would be helpful for all of you to test out this new code and put it to the test for finding your new drivers :-)

---

### Post by fluteflute on 2012-07-18
It's looking very nice!

---

### Post by mc4man on 2012-07-18
> **guitara said:**
> Here's a bit more info from the ubuntu-devel list:

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-July/035553.html)

It would be helpful for all of you to test out this new code and put it to the test for finding your new drivers :-)

That links to the .89 packages, currently 12.10 has gone to .90 & a bit hard to ck. software-properties as it's a crasher
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1026066](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1026066)

---

### Post by xebian on 2012-07-18
> **fluteflute said:**
> It's looking very nice!

Yeah looks more of a facelift and hopes it makes it 'work' correctly.  Don't see much of 'substance' change.

---

### Post by EgoGratis on 2012-07-18
One question:

Command jockey-text is lost?

---

### Post by mc4man on 2012-07-18
> **EgoGratis said:**
> One question:

Command jockey-text is lost?
It's still in jockey-common

---

### Post by mc4man on 2012-07-19
Applying a yet unreleased proposed fix to aptdaemon & software-properties-gtk now opens. The drivers section seems fine here, better than what jockey was previously doing.
Though a bit slow to open, 4-5 sec.'s

---

### Post by lucazade on 2012-07-19
what about qt4 and kubuntu? any news?

---

### Post by FishboyFive on 2012-07-19
this looks Great im so glad graphics drivers are not forgot about 

I just hope there is a driver for my AMD HD7770 at launch of 12.10 

i play alot of world of warcraft lol

---

### Post by ELD on 2012-07-20
I just hope they are doing something other than just moving where the options are.

---

### Post by as2000 on 2012-07-22
Looking good!

---

### Post by kyleabaker on 2012-07-22
> **ELD said:**
> I just hope they are doing something other than just moving where the options are.

I agree. I've still not seen anything really impressive work its way into 12.10 so far. Its great that they're polishing the user experience, but if thats all that comes out of 12.10 then I'll be greatly disappointed. That said, Jockey has been a mess for a while, so I'm kind of glad to see its being fixed.

---

### Post by Kelvari on 2012-07-23
Will this also have a 'recommended' driver for your hardware? In the case of the nVidia drivers, with there being so many options, it seems somewhat confusing as to which is actually the 'best' option to go with.

---

### Post by dino99 on 2012-07-23
Jockey GTK has been superseded by software-properties, which now handles third-party driver configuration.
You can safely remove this transitional package after upgrading.

---

### Post by Elfy on 2012-07-23
Just an observation and a thought with this.

So - jockey always takes an age for any of the machines I have to start - but that's ok - only ever use it once per install if I even do that, depends if nouveau is sufficient.

But now - software-sources takes an age to start, might look good and remove an icon from menus that unity doesn't use anymore - but the consequence is a perfectly good system tool now takes longer to start.

40s to start :|

---

### Post by mc4man on 2012-07-23
> **Elfy said:**
> 


But now - software-sources takes an age to start, might look good and remove an icon from menus that unity doesn't use anymore - but the consequence is a perfectly good system tool now takes longer to start.

40s to start :|

It's a bit better here than that, 6-10 sec. The add. issue would be that depending how SS is started there may be no indication that anything is happening. From the Dash or directly & S-C nothing is apparent, from Software Updater there is a slight change is the Updater window, from synaptic you get the spinning cursor

I guess a bug could be filed on now though the current package doesn't doesn't work without self patching aptdaemon.

---

### Post by Elfy on 2012-07-23
> **mc4man said:**
> It's a bit better here than that, 6-10 sec. The add. issue would be that depending how SS is started there may be no indication that anything is happening. From the Dash or directly & S-C nothing is apparent, from Software Updater there is a slight change is the Updater window, from synaptic you get the spinning cursor

I guess a bug could be filed on now though the current package doesn't doesn't work without self patching aptdaemon.

Yea - kind of waiting for that all to get fixed and then I'll see.

---

### Post by balloons on 2012-07-24
> **Elfy said:**
> Yea - kind of waiting for that all to get fixed and then I'll see.

Yea -- 40 seconds is WAY too long. I too am trying to keep tabs, but landing the app has been quite a mess. Still doesn't work on my box at all.

---

### Post by Elfy on 2012-07-25
I did the fiddle fix - I've undid those changes now and waited for the fix to land properly which apparently it did.

Still takes about the same time to run software properties - what should I report this as/against?

---

### Post by mc4man on 2012-07-25
> **Elfy said:**
> I did the fiddle fix - I've undid those changes now and waited for the fix to land properly which apparently it did.

Still takes about the same time to run software properties - what should I report this as/against?
probably software-properties-gtk
(run it as software-properties-gtk --debug & see where the delay occurs, here it's after the db & sources, maybe while it's determining what drivers to display?

---

### Post by philinux on 2012-07-25
15 seconds to open settings here from Software Updater

Same opening software-properties-gtk from terminal.

---

### Post by Elfy on 2012-07-25
Seems to be a bit faster now - ~25-30 secs

the trustdb appears at about 8secs - so the remainder ... 

I still think the majority of the time is dealing with the 'jockey' bit of software sources - but that's just hearsay ;)

---

### Post by balloons on 2012-07-25
YAY! I finally was able to launch this without crashing. A bit weird being under 'software sources' imho, but I know they are doing work on it overall. At least it appears in system settings now (if it did before, I don't remember it). On my box it's about 5-8 seconds I suppose before it pops up. Almost long enough that you would feel like something isn't working.

---

### Post by Elfy on 2012-07-26
> **guitara said:**
> On my box it's about 5-8 seconds I suppose before it pops up. Almost long enough that you would feel like something isn't working.

So at 30s - should we think that there isn't something working? 

If it is a bug then the sooner it's reported the more chance there is of something getting done I suppose.

Report against software-properties-gtk ?

---

### Post by mc4man on 2012-07-26
> **Elfy said:**
> So at 30s - should we think that there isn't something working? 

If it is a bug then the sooner it's reported the more chance there is of something getting done I suppose.

Report against software-properties-gtk ?

Maybe the extra time you see is either xubuntu related or your hardware - 
here the sources go quick, less than 2 sec's, the rest is likely 'ubuntu drivers'

Can be seen here from this command which takes about 8 secs, (here) & I think is about what software-props is doing after the sources, so 2+8=the 10 I see

```
ubuntu-drivers devices
```
or 
```
ubuntu-drivers list
```
(both take about the same here,

---

### Post by Elfy on 2012-07-26
> **mc4man said:**
> Maybe the extra time you see is either xubuntu related or your hardware - 
here the sources go quick, less than 2 sec's, the rest is likely 'ubuntu drivers'

Can be seen here from this command which takes about 8 secs, (here) & I think is about what software-props is doing after the sources, so 2+8=the 10 I see

```
ubuntu-drivers devices
```
or 
```
ubuntu-drivers list
```
(both take about the same here,
Possibly hardware - I broke the good one - running a old mobo/cpu with 2Gb RAM

That said jockey always took a long time to decide regardless of the hardware. 

ubuntu-drivers devices - 17s

---

### Post by mc4man on 2012-07-26
That seems to 'add' up for you also,  8+17=25

I do find interesting that here it takes ubuntu-drivers a bit longer to run then sudo lshw does for all the hardware.

I guess the biggest possible 'issue' is depending on how software-props is started there may be no indication that anything is going on though I'm sure people will get the idea pretty quickly to just wait.. rather than keep trying to start it

---

### Post by Elfy on 2012-07-26
> **mc4man said:**
> That seems to 'add' up for you also,  8+17=25

I do find interesting that here it takes ubuntu-drivers a bit longer to run then sudo lshw does for all the hardware.

I guess the biggest possible 'issue' is depending on how software-props is started there may be no indication that anything is going on though I'm sure people will get the idea pretty quickly to just wait.. rather than keep trying to start it

I certainly quickly learnt that is was quicker to use synaptic than jockey :p

I just can't get over feeling that this is yet another backward step - but that's just subjective :D

---

### Post by philinux on 2012-07-26
I see software sources is available from Dash. This now takes 10 seconds to appear.

---

### Post by mc4man on 2012-07-26
At least here where 'drivers' is just limited to nvidia, the new ubuntu-drivers actually works better, especially if deciding to switch from nvidia-current to nouveau.
The previous jockey would never do that correctly & I'd always reboot into no 3d support.

Maybe when this is finished, if not already, it will 'feel' better, open quicker, ect.
though, particularly  as of late,  I never get the feeling that Ubuntu ever releases or SRU's into any sort of 'finished' state. (subjective or otherwise..

---

