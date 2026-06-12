---
title: "Wayland not going to be in 11.10 or 12.04 apparently."
date: 2011-05-16
forum: The Cafe
---

### Post by MasterNetra on 2011-05-16
> The "still very experimental for the foreseeable future but promising" Wayland has been discussed more at UDS Budapest, on the mailing lists, and now this weekend in Berlin at LinuxTag.

Wayland was already discussed earlier in the week during the Ubuntu Developer Summit (UDS) in Budapest, Hungary. While I had left early on Friday to make it back to Deutschland for LinuxTag, Wayland was discussed some more.

Earlier in the week the Wayland conversation was pretty normal and nothing new to anyone who stays up to date about this display server on Phoronix. There's no plans to deploy Wayland at large before Ubuntu 11.10 and also now Ubuntu 12.04 since that is a Long-Term Support release so radical changes are unwelcome. ...

[http://www.phoronix.com/scan.php?page=news_item&px=OTQ0NA](http://www.phoronix.com/scan.php?page=news_item&px=OTQ0NA)

---

### Post by dh04000 on 2011-05-16
As expected. Wayland is a BIG change. Gnome3/Unity was a big enough change for the linux community all ready. We should get our upper level GUI's fixed, then change the lower level Wayland. One thing at a time.

---

### Post by NormanFLinux on 2011-05-16
Wayland needs a lot of work before it can completely replace the X Window Manager.

---

### Post by murderslastcrow on 2011-05-16
I don't know whoever convinced anyone that Wayland was coming any year soon, but apparently a lot of bozos have been spreading that rumor. Although we're fixing a lot of things to work well with Wayland already (GTK, Qt, SDL, Kwin, Compiz, Clutter already works, etc.), we're only doing that in anticipation of Wayland coming so we're ready when it's ready. I think it would be silly to use Wayland first in an LTS, and no one ever said it was going to be in the next LTS officially, although plenty of news outlets such as the Linux Action Show seemed to be convinced of this.

Sometimes I think that all the changes recently have people unnaturally excited/fearful of other new changes. Gnome 3 has been in development FOREVER and it just came out. Expect the same for Wayland.

---

### Post by MasterNetra on 2011-05-16
> **murderslastcrow said:**
> I don't know whoever convinced anyone that Wayland was coming any year soon, but apparently a lot of bozos have been spreading that rumor. Although we're fixing a lot of things to work well with Wayland already (GTK, Qt, SDL, Kwin, Compiz, Clutter already works, etc.), we're only doing that in anticipation of Wayland coming so we're ready when it's ready. I think it would be silly to use Wayland first in an LTS, and no one ever said it was going to be in the next LTS officially, although plenty of news outlets such as the Linux Action Show seemed to be convinced of this.

Sometimes I think that all the changes recently have people unnaturally excited/fearful of other new changes. Gnome 3 has been in development FOREVER and it just came out. Expect the same for Wayland.

I'm for one excited to see where Unity and wayland go and how it turns out.

---

### Post by adrien214 on 2011-12-28
> **murderslastcrow said:**
> I don't know whoever convinced anyone that Wayland was coming any year soon

Mark Shuttleworth himself was saying on his blog that [ubuntu] will embrace Wayland early... and that was in nov 2010...

---

### Post by 3Miro on 2011-12-28
> **adrien214 said:**
> Mark Shuttleworth himself was saying on his blog that [ubuntu] will embrace Wayland early... and that was in nov 2010...

Neither Nvidia nor ATI support Wayland with their proprietary drivers. Even for Xorg, right now, Nvidia drivers are too weak and ATI and Intel are good only for desktop work, no gaming or really heavy graphics (you also don't want to use FOSS ATI on a laptop as they have bad power and heat management). Nobody would take on Wayland until either there is proprietary support or there is good enough support via FOSS drivers. Furthermore, nobody would make such a big change for an LTS release in the last minute.

---

### Post by thatguruguy on 2011-12-28
> **adrien214 said:**
> Mark Shuttleworth himself was saying on his blog that [ubuntu] will embrace Wayland early... and that was in nov 2010...

Yeah, but Shuttleworth specifically stated in the comments to that article that:
> It’s highly unlikely that the default Ubuntu install in a year will be  on Wayland. It’s possible that there will be versions of Ubuntu that use  it, or proof-of-concept images, by then. More importantly, we won’t  make it the default until it really is widely supported and supportable,  by folks using a wide variety of hardware providers.[URL="http://www.markshuttleworth.com/archives/551#comment-339255"]
Source[/URL].

---

### Post by LowSky on 2011-12-29
If I can't use Nvidia or AMD drivers, then there is no point. OS drivers can't compete. I want perfect video playback from my hardware and I wont use Intel, that just a laugh.

Wayland, HURD, and so many other cool ideas never seem to get off the ground. Even working projects have issues. Gnome, Unity [Open/Libre]Office, KDE just off the top of my head all hit development hell at some point where they cause severe backlash from the community.

---

### Post by alphacrucis2 on 2011-12-29
Intel are doing a lot of work on Wayland so at least Intel hardware should be well supported.

---

### Post by 3Miro on 2011-12-29
> **alphacrucis2 said:**
> Intel are doing a lot of work on Wayland so at least Intel hardware should be well supported.

Intel has all FOSS drivers and FOSS drivers can be ported to Wayland. The problem is that ATI FOSS drivers aren't good enough and the Nvidia ones aren't good at all. The good drivers for those are proprietary and can only be changed by AMD/Nviida and they will not support Wayland until it becomes widespread enough ... then of course Wayland will not become wide spread enough until AMD/Nvidia start supporting it ... in short: proprietary drivers should be illegal.

---

### Post by cap10Ibraim on 2011-12-29
> **3Miro said:**
>  ... in short: proprietary drivers should be illegal.
I remember visiting gnu website to find out that there is a small list of GNU/Linux out there
 [http://www.gnu.org/distros/free-distros.html](http://www.gnu.org/distros/free-distros.html)
all the others use some binaries and kernel components that don't follow the GNU philosophy 
i may replace Ubuntu with Trisquel

---

