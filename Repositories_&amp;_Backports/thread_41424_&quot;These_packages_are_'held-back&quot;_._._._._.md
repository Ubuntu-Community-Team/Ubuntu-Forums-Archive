---
title: "&quot;These packages are 'held-back&quot; . . . . ."
date: 2005-06-13
forum: Repositories &amp; Backports
---

### Post by jahLux on 2005-06-13
The following packages - [ acroread, acroread-plugins, libxvidcore4, mplayer-386 ]continue to be reported as 'kept-back' and therefore cannot be upgraded - anyone out there have a workaround ?
Thanks.

---

### Post by Leif on 2005-06-13
Yes, take out the marillat repos from your sources.list. Things are getting moved to the backports (see [http://backports.ubuntuforums.org/)](http://backports.ubuntuforums.org/)), so it's best if you try to get packages from there instead.

---

### Post by Gtaylor on 2005-06-13
[QUOTE=Leif]Yes, take out the marillat repos from your sources.list. Things are getting moved to the backports (see [http://backports.ubuntuforums.org/)](http://backports.ubuntuforums.org/)), so it's best if you try to get packages from there instead.[/QUOTE]
I don't know if I'd do that if you want access to some of the things that Ubuntu can't distribute due to licensing issues. I get my codecs and some other applications from there.

I thought "held back" packages needed to be handled by a dist-upgrade?

Try opening a console and typing:
> 
sudo apt-get update
sudo apt-get dist-upgrade


---

### Post by Leif on 2005-06-13
You're right about the codecs but it looks like he already has them installed. And no, these are held back because they depend on packages newer than those in hoary, and not because of a lack of dist-upgrade.

---

### Post by jahLux on 2005-06-14
[QUOTE=Gtaylor]I don't know if I'd do that if you want access to some of the things that Ubuntu can't distribute due to licensing issues. I get my codecs and some other applications from there.

I thought "held back" packages needed to be handled by a dist-upgrade?

Try opening a console and typing:[/QUOTE]

Thanks Gtaylor, but I'd alreday done that as well as Synaptic and Ubuntu Package Updater before posting - I'm still hoping for a working suggestion!

---

### Post by Xian on 2005-06-14
[QUOTE=Leif]Yes, take out the marillat repos from your sources.list. [/QUOTE]
Agreed, it's a marillat issue. There's really nothing to be done save to work around those repos. There are several packages in that repo that will cause Synaptic to go a little flaky, and I'd say if the only problem you've encountered is some held back applications then you're doing pretty good.

---

