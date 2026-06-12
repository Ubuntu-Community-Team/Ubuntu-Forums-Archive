---
title: "Lubuntu &amp; a time machine"
date: 2011-03-11
forum: The Cafe
---

### Post by Blutkoete on 2011-03-11
Hello!

I was wondering: If I'd take e.g. Lubuntu and minimal Ubuntu installation (no GUI), download all the repositories, burn them on CDs and travel back in time, releasing them [insert your favourite time span here, e.g. 5] years earlier, would that make a great impact or would I run into compatibility issues? Would it help Linux taking over the world (I have to ask, powering up that time machine costs lots of money)?

And for law-suits experts: Which license does apply if I travel back in time to a time before the release?

Blutkoete

---

### Post by Ad1217 on 2011-03-11
Does the time machine run linux?

---

### Post by Lucradia on 2011-03-11
> **Blutkoete said:**
> And for law-suits experts: Which license does apply if I travel back in time to a time before the release?

"The Linux kernel is released under the GNU General Public License version 2 (GPLv2)"

From Wikipedia.

---

### Post by Blutkoete on 2011-03-11
I'm sorry. My wrapping-the-question-up-in-a-time-machine-plot ruined what I actually wanted to know.

Today we have e.g. Lubuntu, which is able to perform quite well on old systems. When those "old systems" were state-of-the-art, a long time ago, would today's Lubuntu be considered a great operating system on them or a ressource-eating eye-candy system?

---

### Post by Lucradia on 2011-03-11
> **Blutkoete said:**
> I'm sorry. My wrapping-the-question-up-in-a-time-machine-plot ruined what I actually wanted to know.

Today we have e.g. Lubuntu, which is able to perform quite well on old systems. When those "old systems" were state-of-the-art, a long time ago, would today's Lubuntu be considered a great operating system on them or a ressource-eating eye-candy system?

You'll want a non-DE system for really getting the low-end systems to work. Don't use compositing, and try not to use flash when possible.

Openbox is a good start, with pcmanfm (though you may want to search out the lubuntu ppa, because it has a better, unstable version of pcmanfm.)

conky may be good too, along with stalonetray. Don't minimize your windows, and you'll be set.

Use startx when you get to the terminal when ubuntu first boots after installing xorg, conky, etc. after installing the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You'll need a network connection to do this.

To recap, these are the packages your base should install once CLI is done:
```
xorg conky openbox stalonetray obmenu menu obconf gtk-chtheme
```
stalonetray is really recommended if you plan to use pidgin. Add pcmanfm2 if you add the lubuntu repo. Or just pcmanfm for the normal repo.

---

### Post by earthpigg on 2011-03-11
If you could take a Lubuntu CD back to 1999, it would have a substantial impact on the entire industry.

---

### Post by Lucradia on 2011-03-11
> **earthpigg said:**
> If you could take a Lubuntu CD back to 1999, it would have a substantial impact on the entire industry.

It would mean the end of the world for propietary operating systems.

---

### Post by koenn on 2011-03-11
> **earthpigg said:**
> If you could take a Lubuntu CD back to 1999, it would have a substantial impact on the entire industry.


too late, 
Windows 95, later 98, had already conquered the home desktop, while businesses were on Windows NT Server and Workstation
Lubuntu would at best be a niche thing, like Apple.

---

### Post by abcd_z on 2011-03-16
I run lubuntu myself and I have persistant fantasies involving a time machine.

I am SO glad to hear I'm not the only one who's wondered this. ;)

---

### Post by t0p on 2011-03-16
> **abcd_z said:**
> I run lubuntu myself and I have persistant fantasies involving a time machine.

I am SO glad to hear I'm not the only one who's wondered this. ;)

For the love of Eris, do NOT use a time machine to try and make Linux popular!  Last time some did that, it caused The Great Abandonment Of Computer Technology, with attendant foul effects on society, and it took me *ages* to get the human race back on track.

There will *never* be a "year of Linux on the desktop".  All you'll do is hasten the extinction of the human race.  Again.  Please please *please* don't do it!!

Yours sincerely,

The Doctor.

PS The Tardis runs on Vista.  Not because it's the best tool for the job; simply because one of my assistants thought she'd "surprise" me by installing the POS and I don't have a clue how to switch back (I can't remember the BIOS password).

---

### Post by Lucradia on 2011-03-16
> **koenn said:**
> too late, 
Windows 95, later 98, had already conquered the home desktop, while businesses were on Windows NT Server and Workstation
Lubuntu would at best be a niche thing, like Apple.

1991 is when Linux came to be. Novell was still aiming to incorporate Linux in some way. In the late 90s, you would've seen redhat on best buy shelves even. If you took all the vast knowledge of linux as we have today; it would certainly cause Apple to go down the drain at the very least. Not to mention having those Android phones / tables sooner.

Similarly, Hardware would be boosted by leaps and bounds; because Linux also has a cache of that information on hand. If you would like me to write up a detailed report on what might happen if you did go back in time with the newer linux, I'd be happy to do so. But please note; all of it would shed bad light on MS and Apple. Due to the fact that Linux would be more revered.

---

