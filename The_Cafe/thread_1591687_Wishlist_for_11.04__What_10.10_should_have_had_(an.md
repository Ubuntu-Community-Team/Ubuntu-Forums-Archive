---
title: "Wishlist for 11.04 / What 10.10 should have had (and doesn't)"
date: 2010-10-09
forum: The Cafe
---

### Post by Speed_arg on 2010-10-09
USC should not freeze, be fast, have a lot more features, better looking, be customizable.

Overall system should be fast, gtk theme needs to be optimized for being baster.

Lots of bugs have to be fixed

Better hardware detection

Delta updates

Make update manager not so big and more simple, make it work in the background (go to the tray bar), maybe automatic updates

---

### Post by Lucradia on 2010-10-09
> **Speed_arg said:**
> USC should not freeze, be fast, have a lot more features, better looking, be customizable.
[COLOR="Red"]Doesn't freeze for me.[/COLOR]

Overall system should be fast, gtk theme needs to be optimized for being baster.
[COLOR="Red"]Works fast for me.[/COLOR]

Lots of bugs have to be fixed
[COLOR="Red"]Like, what bugs? Links please.[/COLOR]

Better hardware detection
[COLOR="Red"]What hardware doesn't detect on your system?[/COLOR]

Delta updates
[COLOR="Red"]Come again? Link to such a term.[/COLOR]

Make update manager not so big and more simple, make it work in the background (go to the tray bar), maybe automatic updates
[COLOR="Red"]As an ***_option_***, sure.[/COLOR]

Replied in red, expect answers from you soon, hopefully. by the way, my system has a GTX 470, HP Printer/Scanner/Fax/Copier, 8 GB of RAM, 1 TB Regular SATA, etc. and works blazing fast, even boots a second faster than windows (which only boots in around 5 seconds.)

---

### Post by stmiller on 2010-10-09
You can already do automatic updates. This has been there for years.


```

sudo apt-get install unattended-upgrades

```

You can have it just do security updates automatically, or all updates. :)


Delta updates has been in discussion in many outlets. Currently Fedora and such have this. That would be nice.

---

### Post by Speed_arg on 2010-10-09
> **Lucradia said:**
> Replied in red, expect answers from you soon, hopefully. by the way, my system has a GTX 470, HP Printer/Scanner/Fax/Copier, 8 GB of RAM, 1 TB Regular SATA, etc. and works blazing fast, even boots a second faster than windows (which only boots in around 5 seconds.)

You shouldn't need a i7+gtx470+8gb for running OK an OS :lolflag:
With the same hardware, windows is much faster than ubuntu. Yes, boot time might be a bit faster in ubuntu, but who cares about boot time, I rather have a 10 mins boot time and a lighting fast OS than a 5 secs boot and a unresponsive OS.

I have a regular netbook, as most people do. With a netbook hardware, USC is impossible to use because when you hit install it freezes like 5 secs. Also installing a .deb now is terrible. Its a great idea to integrate everything, debs and else into USC, but it should work fine for doing so.

Bugs? Take a look at the 10.10 dev forum, and at launchpad bug list. 10.10 doesn't even install for my other netbook.

About the hardware, I have issues with my resolution.

Delta updates means this:
Say a program updates a few lines of their code, say they change a text. Now, you have to download the entire package (maybe 20mb), with delta updates (what windows has been doing since almost 10 years, and fedora and a few more distros already do) you just download the delta (the different bytes), so instead of downloading a 20mb update for a text changed, you download a few kb.

---

### Post by Lucradia on 2010-10-09
> **Speed_arg said:**
> You shouldn't need a **_[COLOR="Red"]AMD Phenom II X6 @ 2.6 GHz[/COLOR]_**+gtx470+8gb for running OK an OS :lolflag:

I have a regular netbook, as most people do. With a netbook hardware, USC is impossible to use because when you hit install it freezes like 5 secs. Also installing a .deb now is terrible. Its a great idea to integrate everything, debs and else into USC, but it should work fine for doing so.
[COLOR="Red"]No. Most people who use Ubuntu, use a desktop or older laptop.[/COLOR]

About the hardware, I have issues with my resolution.
[COLOR="Red"]And that resolution problem is?[/COLOR]

Delta updates means this:
Say a program updates a few lines of their code, say they change a text. Now, you have to download the entire package (maybe 20mb), with delta updates (what windows has been doing since almost 10 years, and fedora and a few more distros already do) you just download the delta (the different bytes), so instead of downloading a 20mb update for a text changed, you download a few kb.
[COLOR="Red"]Some packages do diff updates, we have had this since the start of Linux.[/COLOR]

Fixed and replied again. :)

---

### Post by Speed_arg on 2010-10-09
> **Lucradia said:**
> Fixed and replied again. :)

Lol, it makes no sense what you are saying. Then they have to drop UNE, change min requirements to phenom II x6/i7, 8gb ram, say it doesn't support netbooks nor slow screens, change the slogan about FAST to UBER SLOW AND BLOATED.

It doesn't recognize my resolution

I don't think so, then why has delta debs been proposed (and not done) so many times, and why sometimes I get 400mb of updates.

---

### Post by Lucradia on 2010-10-09
> **Speed_arg said:**
> Lol, it makes no sense what you are saying. Then they have to drop UNE, change min requirements to phenom II x6/i7, 8gb ram, say it doesn't support netbooks nor slow screens, change the slogan about FAST to UBER SLOW AND BLOATED.

It doesn't recognize my resolution

I don't think so, then why has delta debs been proposed (and not done) so many times, and why sometimes I get 400mb of updates.

I had a Toshiba Netbook once (Intel Atom, one core, two threads) and it worked medium-fast, everything was pretty much detected.

---

### Post by dinamic1 on 2010-10-09
> **Speed_arg said:**
> USC should not freeze, be fast, have a lot more features, better looking, be customizable.
**USC is boring slooooow, unresponsive, freezes a lot  ... even scrolling is sluggish** 

**AMD athlon 2500+**


:(

---

### Post by bash on 2010-10-09
[quote=Lucradia]Delta updates
[COLOR="Red"]Come again? Link to such a term.[/COLOR][/quote]

[http://lmgtfy.com/?q=ubuntu+delta+updates](http://lmgtfy.com/?q=ubuntu+delta+updates)

---

### Post by Dustin2128 on 2010-10-09
> **Lucradia said:**
> my system has a GTX 470, HP Printer/Scanner/Fax/Copier, 8 GB of RAM, 1 TB Regular SATA, etc.
thanks a lot, you fried my keyboard.

---

### Post by Lucradia on 2010-10-09
> **bash said:**
> [http://lmgtfy.com/?q=ubuntu+delta+updates](http://lmgtfy.com/?q=ubuntu+delta+updates)

[http://brainstorm.ubuntu.com/idea/13/](http://brainstorm.ubuntu.com/idea/13/)

wow, no developer reply? :shock:

---

### Post by asdacap on 2010-10-23
DELTA UPDATE!!!
I NEED YOU!!
PLEASE...
hello?

Anyway, according to what I've read before, Ubuntu does not (yet) have delta update because ubuntu repos refresh 25 times a day, which means, the server would need to generate delta of the 300GB++ repos every hour if it use the same technique as Debian which already has delta update and Debian repo refresh daily. It was said that they would do the zsync (bla..bla..bla..) technique, but that is years ago and still, no delta update.

Back to the screaming...

GIMME THE DELTA UPDATE!!!!!
I WON'T SWITCH FROM FEDORA UNTIL YOU GIVE ME DELTA UPDATE!!!
WAAAAAAARRRGHHHH!!!!!!

---

### Post by utilitytrack on 2010-10-23
Stability.

---

### Post by 98cwitr on 2010-10-23
I still have nvidia issues with what seems like interlace lag at high frame rates when watching movies. Lines get drawn on the screen, splitting the frame transition. I'd really this to finally be fixed.

Ditch Brasero and go with K3B

Build in actual Java and not OpenJDK

Build a GUI based boot time process and service config (like msconfig in windows)

---

### Post by Cam! on 2010-10-23
[LIST]
[*]Have the bottom panel's window list automatically group windows by default.
[*]Remove the username from the top panel, and replace it with an icon.
[*]The ability to select from Chrome, Firefox, or Opera during installation
[*]Make Ambiance a lighter shade of grey/black, and Radiance white.
[*]Redesign the Human icon theme.
[*]Login Screen customization.
[*]New sound scheme.
[*]New cursor. It looks too similar to Windows 7's.
[*]New Screensavers.
[*]Better 64-bit Flash support.
[*]GNOME + GTK 3 support.
[/LIST]

---

### Post by NightwishFan on 2010-10-23
> **Cam! said:**
> [LIST]
[*]Have the bottom panel's window list automatically group windows by default.
[*]Remove the username from the top panel, and replace it with an icon.
[*]The ability to select from Chrome, Firefox, or Opera during installation
[*]Make Ambiance a lighter shade of grey/black, and Radiance white.
[*]Redesign the Human icon theme.
[*]Login Screen customization.
[*]New sound scheme.
[*]New cursor. It looks too similar to Windows 7's.
[*]New Screensavers.
[*]Better 64-bit Flash support.
[*]GNOME + GTK 3 support.
[/LIST]

[LIST=1]
[*]I agree and have suggested this.
[*]Perhaps, has merit.
[*]Hmm.. Yeah actually that would be nice to, but an extra option to click. Have to find a way to make cool easy configuration like that elegant.
[*]I am all for theme evolution.
[*]Same as above.
[*]Yes, I agree. GDM2 could has a config very easily. In fact you can configure it with gnome-appearance-properties (run it as user gdm).
[*]Could do with one by now, yes.
[*]Win7 looks like ours. :) 
[*]I am indifferent.
[*]This probably will not happen until the adobe plugin goes stable.
[*]Will naturally evolve.
[/LIST]

---

### Post by utilitytrack on 2010-10-23
> **Cam! said:**
> [LIST]
[*]Have the bottom panel's window list automatically group windows by default.
[*]Remove the username from the top panel, and replace it with an icon.
[*]Make Ambiance a lighter shade of grey/black, and Radiance white.
[*]Redesign the Human icon theme.
[*]Login Screen customization.
[*]New sound scheme.
[*]New cursor. It looks too similar to Windows 7's.
[*]New Screensavers.
[*]GNOME + GTK 3 support.
[/LIST]

WTF? For wich purpose this? Did you looked at this page at least once?
[https://bugs.launchpad.net/ubuntu/+bugs]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

Pay attention on the real problems. Especially note #47768, #645818, #657788, #21175, #26058, #27969, #32123, #46520, #68252. Some bugs that related to GRUB are terrible. And do you agree, that next Ubuntu will be released with all it's unresolved bugs? Yes, you agree, because you suggest to have new cursor and screensaver instead of stability.

---

