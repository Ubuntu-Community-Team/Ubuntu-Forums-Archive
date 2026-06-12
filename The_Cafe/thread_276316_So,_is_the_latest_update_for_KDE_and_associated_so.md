---
title: "So, is the latest update for KDE and associated software working fine?"
date: 2006-10-12
forum: The Cafe
---

### Post by NickPresta on 2006-10-12
3.5.4 -> 3.5.5

I can't afford to spend any time trying to fix even the smallest thing tonight.

Any feedback is appreciated.

---

### Post by jkugler on 2006-10-13
OK, let's try this again...Konqueror crashed when I was closing the Manage Attachments window.

With my work computer, everything went fine.  With my home computer, I'm getting something I can only describe as image corruption. JPGs and SVGs are all wonky.  Haven't tested with PNGs.  It started after the upgrade to 3.5.5, but the odd thing is it is affecting Gimp too.  I'd blame my video card (or the driver), but all other colors (apps, etc) are displaying fine, and the driver didn't get touched.

The attachment shows the Aurora background, and Gwenview displaying a photo.  If the screen shot looks fine on your end, then I really have display issues...maybe I'll have to post a photo of my screen. :)

Going to try to attach a photo again. :)

j

---

### Post by jkugler on 2006-10-13
OK....WEEEEIRD!  I just restarted X, and logged back in.  All the images look fine, and even my screen shot that I posted is fine.  So, apparently X was rendering correctly, but not displaying correctly.  The odd thing is, I had X shut down during the KDE upgrade, then started it after the upgrade was done, so a restart of X shouldn't have been needed.

So, no, no issues in the upgrade. :)

One thing I noticed: my Google search box seemed to vanish in Konqueror.  To get it back, do Settings -> Configure Extensions -> Extensions Tab -> Google Search (check it).

Have fun!

j

---

### Post by Feanor on 2006-10-13
I can't access the module Display on systemsettings or kcontrol after upgrading...

---

### Post by chaosgeisterchen on 2006-10-13
> **Feanor said:**
> I can't access the module Display on systemsettings or kcontrol after upgrading...

ow.. that's too common.. 

It already occured when installing KDE 3.5.2 on Breezy. So it does on Dapper when upgrading to 3.5.5..

---

### Post by pelle.k on 2006-10-13
I just did a fresh install of kubuntu 6.06.1 and upgraded to kde 3.5.5. Thanks for that tip on google search bar :)
The only hiccup was that font antialiasing didn't work at all. I changed all fonts to another font, disabled antialiasing, rebooted and then changed it all back again. After that all was fine.
Other than that all is working perfectly thankyou very much...

---

### Post by GarethMB on 2006-10-13
My kdesu themes were all reverted to default. It's a two minute fix though if you  save your set up with theme manager and then apply it in kcontrol as root.

---

### Post by asimon on 2006-10-13
I updated and everything is fine. I neither have the mentionend problems with the display settings module nor with fonts antialiasing.

BTW: The google search bar is not really needed at all, you can just use the url bar and enter something like 'gg:foobar' to google for foobar. Have a look at Konqueror->Settings->Configure Konqueror...->Web Shortcuts to enable your favourite web shortcuts. There are even some ubuntu shortcuts enabled by default, for things like searching Ubuntu's bug tracker, etc. They are very handy.

---

### Post by Feanor on 2006-10-13
> **chaosgeisterchen said:**
> ow.. that's too common.. 

It already occured when installing KDE 3.5.2 on Breezy. So it does on Dapper when upgrading to 3.5.5..

So how can I fix this? ç_ç

---

### Post by NickPresta on 2006-10-14
Well, after upgrading, my keyboard stopped working (mouse was fine) and I couldn't open up Konqueror (segfault'd).

I restarted my computer and everything was fine with the exception of my splash screen and screen saver being reverted to the original. That was a quick fix though so I didn't mind.

---

### Post by hvbakel on 2006-10-14
Anyone here tried to mount a USB stick after upgrading to 3.5.5? The kde-hal connection seems messed up ([https://launchpad.net/bugs/65662)](https://launchpad.net/bugs/65662)).

---

### Post by yaa13 on 2006-10-15
> **hvbakel said:**
> Anyone here tried to mount a USB stick after upgrading to 3.5.5? The kde-hal connection seems messed up ([https://launchpad.net/bugs/65662)](https://launchpad.net/bugs/65662)).

At me the same problem.

---

