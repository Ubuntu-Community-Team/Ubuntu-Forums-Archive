---
title: "additional drivers no longer installed by default ?"
date: 2012-11-20
forum: Ubuntu Development Version
---

### Post by ronacc on 2012-11-20
I went to install nvidia-current , additional-drivers was not installed by default , tried to install it via USC and that installed jockey-kde not jockey-gtk ??? installed jockey gtk via synaptic , no menu entry and wont run from term . gave up and installed the driver by hand . are we back again to trying to keep people from using the proprietary driver ?

---

### Post by deadflowr on 2012-11-20
Look in software sources.
It was moved there, I think during quantal.

---

### Post by ronacc on 2012-11-20
yes its in there but when you install it it installs jockey-KDE not jockey-GTK , also while installing the driver by hand I found out that tab to complete is not working anymore .

---

### Post by mc4man on 2012-11-20
> Look in software sources.

> **ronacc said:**
> yes its in there but when you install it it installs jockey-KDE not jockey-GTK 

Don't think anything has to be installed, isn't the 'Additional Drivers tab' shown in software sources? (built-in

---

### Post by ronacc on 2012-11-20
if you mean "community maintained non free drivers restricted software " I had that already enabled . Why does USC install jockey-KDE instead of jockey-GTK ? from synaptic you can install either . atleast on my sys no menu Item was created anywhere I could find and when run from term it says searching for drivers and then goes away even though drivers are available .


Edit: my bad I see the tab "additional drivers" now . however it says I am using the nvidia-current-updates driver which I did install via synaptic but it didn't trigger dkms and the module never built . I did not get the driver until I hand installed it from the .run file direct from Nvidia .

---

### Post by deadflowr on 2012-11-20
[https://launchpad.net/ubuntu/raring/amd64/jockey-gtk/0.9.7-0ubuntu11]("https://launchpad.net/ubuntu/raring/amd64/jockey-gtk/0.9.7-0ubuntu11")

---

### Post by mc4man on 2012-11-20
> **ronacc said:**
> if you mean "community maintained non free drivers restricted software " I had that already enabled . Why does USC install jockey-KDE instead of jockey-GTK ? from synaptic you can install either . atleast on my sys no menu Item was created anywhere I could find and when run from term it says searching for drivers and then goes away even though drivers are available .

Was referring to what's in screen (system settings > software sources), - the tab is now part of 'software  sources' by default, nothing to install

---

### Post by ronacc on 2012-11-20
> **deadflowr said:**
> [https://launchpad.net/ubuntu/raring/amd64/jockey-gtk/0.9.7-0ubuntu11]("https://launchpad.net/ubuntu/raring/amd64/jockey-gtk/0.9.7-0ubuntu11")

Yes both jockey-GTK  AND jockey-KDE show in synaptic but if you install additional-drivers from Ubuntu-software-center it installs the kde version even though I am using Ubuntu not Kubuntu .

---

### Post by mc4man on 2012-11-22
There has been some discussion of making the built-in "Additional Drivers" easier to find via a .desktop. Probably should be done

(the Exec= would be this which will open the tab
```
software-properties-gtk --open-tab=4
```

---

### Post by ronacc on 2012-11-22
I had been using nouveau for the last couple of cycles since it is (finally) working well for me so I hadn't paid any attention to additional drivers for awhile .

---

### Post by mc4man on 2012-11-22
> **ronacc said:**
> I had been using nouveau for the last couple of cycles since it is (finally) working well for me so I hadn't paid any attention to additional drivers for awhile .

Same here on this getting 'old' laptop, (8400m), starting in 12.10 nouveau worked better than the nvidia drivers in many respects.
(to some extent because nouveau doesn't support powermizer so gpu runs at full speed

---

### Post by Kirk M on 2012-11-23
Guys and gals - Jockey was removed by the Ubuntu devs for the 12.10 release and was replaced by a new "Additional drivers" tab in the "Software Sources" app. It's powered by the the new &#8220;ubuntu-drivers-common&#8221; package.

That being said and after reading the release notes for 12.10, it seems Ubuntu didn't bother to officially announce this change to anyone via it's "What's new/Release notes" leaving the user in limbo as far as AMD/ATI and Nvidia drivers were concerned. Even the users over at Linux Mint are floundering around with this. The only reason I knew about this change ahead of time was by reading about it on a third party Linux site.

No wonder folks are still confused.

By the way, when you first bring up "Software Sources" you will have to wait several seconds before the app will appear. This is due to the app scanning your hardware first just like jockey did except the "Scanning hardware" box does not appear with this new change leaving the user to wonder what's going on.

---

### Post by cariboo on 2012-11-23
> **Kirk M said:**
> Guys and gals - Jockey was removed by the Ubuntu devs for this release and was replaced by a new "Additional drivers" tab in the "Software Sources" app. It's powered by the the new “ubuntu-drivers-common” package.

That being said and after reading the release notes for 12.10, it seems Ubuntu didn't bother to officially announce this change to anyone via it's "What's new/Release notes" leaving the user in limbo as far as AMD/ATI and Nvidia drivers were concerned. Even the users over at Linux Mint are floundering around with this. The only reason I knew about this change ahead of time was by reading about it on a third party Linux site.

Bad form all around.

By the way, when you first bring up "Software Sources" you will have to wait several seconds before the app will appear. This is due to the app scanning your hardware first just like jockey did except the "Scanning hardware" box does not appear with this new change leaving the user to wonder what's going on.

More bad form.

What does this have to do with Raring Ringtail?

---

### Post by Kirk M on 2012-11-23
> **cariboo907 said:**
> What does this have to do with Raring Ringtail?

The original question was "additional drivers no longer installed by default ?". That's the question I answered. I probably should have said it was removed *for the 12.10 release *instead of the way I worded it originally. To be honest, I didn't realize I was posting to the "Ubuntu +1 Raring Ringtail" thread since I found it via search. Sorry about that. :oops: I have edited my first post accordingly. The point being, Ubuntu made the change apparently without officially announcing it to it's users both current and potential. Now the confusion is apparently overflowing into Raring.

---

### Post by ronacc on 2012-11-23
ubuntu software center still installs jockey when you install "additional drivers" it just installs the wrong one . As I stated above it installs the KDE version instead of the GTK one see SS . I am running gnome-shell .

---

### Post by cariboo on 2012-11-23
@ronacc, if you check in synaptic, you'll see that jockey-gtk is just a transitional package, and isin't used any more, that's why you are getting jockey-kde when trying to install it.

> Jockey GTK has been superseded by software-properties, which now handles
third-party driver configuration.

You can safely remove this transitional package after upgrading.

---

### Post by ronacc on 2012-11-23
> **cariboo907 said:**
> @ronacc, if you check in synaptic, you'll see that jockey-gtk is just a transitional package, and isin't used any more, that's why you are getting jockey-kde when trying to install it.

I installed jockey-GTK with synaptic , I just didn't pay any attention to the description , I just saw the name clicked it and hit apply .

---

### Post by mc4man on 2012-11-23
I think they'll make it easier to find, one way would be thru the Dash with common search terms like
add..
dri...
har...
Maybe more depending on Name= & or Comment=
An Ex. one can see would be 
 gedit ~/.local/share/applications/additional-drivers.desktop

using something like - 
```
[Desktop Entry]
Name=Additional Drivers
Comment=Open Additional tab for hardware drivers available for the system
Icon=jockey
Exec=software-properties-gtk --open-tab=4
Terminal=false
Type=Application
Categories=System;Settings;GTK;HardwareSettings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=jockey
NoDisplay=false
```

---

