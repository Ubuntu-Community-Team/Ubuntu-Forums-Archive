---
title: "Nautilus missing Delete"
date: 2015-12-09
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-12-09
Running Gnome 16.04 and there is no option to directly delete a file in nautilus only send it to trash.  Appears that the "enable-delete" schema is missing.  Can I add that schema and how do I do so?

---

### Post by QDR06VV9 on 2015-12-09
> [COLOR=#000000]The problem seems to be related to GSettings simply not recognising[/COLOR]that key at all:

    $ gsettings get "org.gnome.nautilus.preferences" "default-sort-order"
    'name'
    $ gsettings get "org.gnome.nautilus.preferences" "enable-delete"
    No such key 'enable-delete'

So the solution will entail restoring that ability in Nautilus, by
reading the existing configuration setting at that key to honour [COLOR=#000000]user's expressed preference.[/COLOR]

Bug [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=802899](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=802899)

---

### Post by crcarson on 2015-12-09
> **runrickus said:**
> Bug [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=802899](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=802899)

Think we are saying the same things that there is no schema for "enable-delete" in nautilus but not clear on what to do.  You said...

"So the solution will entail restoring that ability in Nautilus, by
reading the existing configuration setting at that key to honour [COLOR=#000000]user's expressed preference."

Is this something I can add or do I wait for Nautilus to fix this?
[/COLOR]

---

### Post by QDR06VV9 on 2015-12-09
> [COLOR=#000000]Is this something I can add or do I wait for Nautilus to fix this?[/COLOR]
I Tried a couple of times last nite but no success yet.
So it should get fixed before to long.
And if I find a work around I will post it here in this thread..But I will bet the farm that mc4man will have something here shortly.
On my current setup the keyboard combo's still work..'CTRL+Shift+Delete' && 'Delete'
Kind Regards

---

### Post by mc4man on 2015-12-09
The context menu item was removed, it has been put back as a dconf option but not in 3.18 (in 3.20 I guess
Similar to the ill-advised switch directory on DnD hover in canvas view, finally reverted but again not in 3.18 (patch available

So file a bug requesting it be backported to 3.18 (myself likely will not use 3.18 as I've no use for a window that can't easily be themed & the gtkheaderbar is crap to me.

Or patch &  build nautilus-3.18 yourself, to that end wrote a patch, attached. Screens show implemented in 3.18

---

### Post by QDR06VV9 on 2015-12-09
> **mc4man said:**
> <Snip>
** (myself likely will not use 3.18 as I've no use for a window that can't easily be themed & the gtkheaderbar is crap to me.**

Or patch &  build nautilus-3.18 yourself, to that end wrote a patch, attached. Screens show implemented in 3.18

+1 Thanks mc4man
I can see myself not using gnome3 any more, I still like the old gnome2 but pointless to discuss that any further, But Mate(And Caja) keeps me Happy.;)
Tonite or tomorrow I will try to build nautilus with your patch.
Kind Regards

---

### Post by ronacc on 2015-12-09
delete in nautilus isn't the only thing missing . Gedit is missing a print command , I had to install leafpad yesterday to print a text file .

---

### Post by sammiev on 2015-12-09
@mc4man, Thanks

I came across that tonight and was going to post it but you beat me to the punch. :)

---

### Post by launchpad-washuu on 2015-12-10
Nautilus also seems to be missing "Show copy dialogue".

---

### Post by cariboo on 2015-12-10
> **launchpad-washuu said:**
> Nautilus also seems to be missing "Show copy dialogue".

It's still there, it just doesn't look as expected, see attachment.

---

### Post by launchpad-washuu on 2015-12-10
Oh? Never thought to look there! *facepalm*

---

### Post by monkeybrain20122 on 2015-12-28
Just saw this thread. I have gnome 3.18 on Fedora 23 and it is driving me crazy. I have enough with this gnome upstream madness and installed nemo, sanity restored and I am a happy camper. Is nautilus 3.18 or 3.16 going to be in Xenial (unity)? If it is 3.18 may have to do the same.

---

### Post by fthx on 2015-12-28
[QUOTE=ronacc]delete in nautilus isn't the only thing missing . Gedit is missing a  print command , I had to install leafpad yesterday to print a text file .[/QUOTE]

Gedit does still have a print command.

---

### Post by grahammechanical on 2015-12-28
Is nautilus 3.18 or 3.16 going to be in Xenial (unity)?

Xenial (Unity) already has nautilus 3.18.3.

---

### Post by ventrical on 2015-12-29
> **grahammechanical said:**
> Is nautilus 3.18 or 3.16 going to be in Xenial (unity)?

Xenial (Unity) already has nautilus 3.18.3.

now 3.18.4.

---

### Post by fjgaude on 2015-12-29
Still, 3.18.4 is not fully functional on Unity, more patches needed, I think! The same goes for gedit and likely other apps that use GTK+.

---

### Post by ventrical on 2015-12-29
> **fjgaude said:**
> Still, 3.18.4 is not fully functional on Unity, more patches needed, I think! The same goes for gedit and likely other apps that use GTK+.

I am assuming they will come with development time line.

Regards..

---

### Post by QDR06VV9 on 2015-12-29
> **ventrical said:**
> I am assuming they will come with development time line.

Regards..
Hi and Welcome to Ubuntu Development Version...):P

---

### Post by mc4man on 2015-12-29
If 'they' are going to kowtow to ubuntu dev's & friends using gnome-shell by moving to the out of place nautilus > 3.14 in 16.04/unity/7/compiz/unity window deco then 'they' might as well go all in to 3.20 which at least fixes some poor previous gnome dev decisions.

---

### Post by QDR06VV9 on 2015-12-29
I thought I read some where that Gnome 3.20 will ship with 16.04
> [COLOR=#000000][FONT=museo_sans]It was to be expected for Ubuntu GNOME 16.04 LTS to ship with GNOME 3.20, so it&#8217;s not really a surprise that the devs are starting to upload the GNOME 3.19 packages for the daily builds.
[/FONT][/COLOR][COLOR=#000000][FONT=museo_sans]&#8220;GNOME 3.19 will be on its way to xenial/gnome3-staging PPA shortly, bear in mind that packages from this repository are considered unstable and only for experienced users. gdm packaging and binaries have been migrated to gdm3, all to match Debian, which is a change unnoticeable for casual users, but advanced users may like this change (packages, binaries, services and configurations all now use gdm3 instead of gdm,&#8221; [/FONT][/COLOR][developers wrote on Google+.]("https://plus.google.com/u/0/+UbuntuGNOMEorg/posts/Am1aL2CA3R7")
From Here [http://news.softpedia.com/news/ubuntu-gnome-16-04-lts-gets-first-gnome-3-19-packages-for-daily-build-496640.shtml](http://news.softpedia.com/news/ubuntu-gnome-16-04-lts-gets-first-gnome-3-19-packages-for-daily-build-496640.shtml)
But?!? 
> GNOME 3.20 to Have Separate X11 and Wayland Sessions in Display Manager.

To our surprise, we've discovered that the GNOME devs managed to introduce quite a few things in GDM 3.19.2, such as the implementation of separate X11 and Wayland sessions, support for hiding the Wayland session if the login screen is powered by X11, as well as the removal of the "custom" session.
From Here [http://linux.softpedia.com/blog/gnome-3-20-to-have-separate-x11-and-wayland-sessions-in-display-manager-497737.shtml](http://linux.softpedia.com/blog/gnome-3-20-to-have-separate-x11-and-wayland-sessions-in-display-manager-497737.shtml)
So nothing set in stone yet...

---

### Post by ventrical on 2015-12-30
> **runrickus said:**
> Hi and Welcome to Ubuntu Development Version...):P

Yeeess .... this is the place. ! :)  Have a great and safe New Years everybody. May the new year's testing bring you breakage and joy. ;)

Regards..

---

### Post by QDR06VV9 on 2015-12-30
> **ventrical said:**
> Yeeess .... this is the place. ! :)  Have a great and safe New Years everybody. May the new year's testing bring you breakage and joy. ;)  Regards.. It was good to see your post's again. Kind of different here in the development forum with out seeing multiple post's by The V-man :)

---

### Post by ventrical on 2015-12-31
> **runrickus said:**
> It was good to see your post's again. Kind of different here in the development forum with out seeing multiple post's by The V-man :)

I'm here everyday :) Update everyday or every other day of  Mate, Unity, Gnome and Xubuntu - all with proposed repos enabled.  There have not been many bugs to report, at least of any great magnitude or which fixes have not already been issued. Up to now this cycle has been a virtual rolling release realized!!! but I do not think it will remain so as the days progress onwards. Also with no snappy personal image to experiment with it's kind of difficult to get too excited about any one new development caveat taking place. :) Maybe I'll come up with some more experiments in the new year ! :) hehaheha

Regards..

---

