---
title: "who organises the backports?"
date: 2007-10-20
forum: The Cafe
---

### Post by LanDan on 2007-10-20
hi all,

just a quick question here with hopefully long answers ;)

who is organising the backports and how is it organised?

i have been using debian and freebsd the last couple of years for some servers and desktops semi-professional and have been keeping an eye on ubuntu since dapper just trying out some releases and mainly using some friends as testing audience just to see how they get along with it..
i must say huge improvements have been made and i'm impressed in general.

so impressed that i'm planning to use hardy for some serious LTSP deployment in a production environment, but the only thing is....in a production environment you don't want to make big changes if you need a newer package now and then.
FreeBSD has the best solution possible and Debian backports saved my life several times........but the dapper backports repo seemed rather empty to me and lacking of needed packages (offcourse kuddo's to the ones that did work on it)

so....how do i find more info on the backports to find out what the plans are and maybe try to lend a hand here and there

---

### Post by bruce89 on 2007-10-20
Backports in Ubuntu are only done for 6 months, then they stop. This is because they have to be from the next stable release. Dapper's backports all have to come from Edgy, which is a year old now.

In other words, I'd stick with Debian.

---

### Post by John.Michael.Kane on 2007-10-20
[UbuntuBackports Wiki]("https://help.ubuntu.com/community/UbuntuBackports")

[The Ubuntu Backporters Team]("https://launchpad.net/~ubuntu-backporters")

[Ubuntu Backports]("http://ubuntuforums.org/forumdisplay.php?f=47")

---

### Post by LanDan on 2007-10-20
> **bruce89 said:**
> Backports in Ubuntu are only done for 6 months, then they stop. This is because they have to be from the next stable release. Dapper's backports all have to come from Edgy, which is a year old now.

In other words, I'd stick with Debian.

thanks for the replies,

but six months sounds strange to me cause in my experience i only start needing them after a year or so because features usually do not change that dramatically in a short period...it would leave the LTS with a gap of 2.5 years and we all know what can happen in such a period.
that forces everybody to roll their own packages :confused:

---

### Post by John.Michael.Kane on 2007-10-20
> **LanDan said:**
> thanks for the replies,

but six months sounds strange to me cause in my experience i only start needing them after a year or so because features usually do not change that dramatically in a short period...it would leave the LTS with a gap of 2.5 years and we all know what can happen in such a period.
that forces everybody to roll their own packages :confused:

LTS does not mean new packages. LTS means the user is guaranteed security updates, and technical support for that period of time in this case 2009 on the desktop 2011 on the server. As stated before any packages backported is usually backported down from one release above in the case of dapper your backports would have come from edgy.

Most users wanting the latest, and greatest packages/programs on Ubuntu usually run the 6month release upgrading their version when the next one is released. Users wanting stable packages, and security updates, and who are willing to compile/backport their own updated packages run the LTS.

---

### Post by plb on 2007-10-20
Stick with Debian.

---

### Post by LanDan on 2007-10-20
i know the "fix only" policy and that backports are a security risk that need a conservative approach, but this would make ubuntu a non-option for any production environment

and i don't see any practical problem between porting a edgy or gutsy app for dapper

---

### Post by John.Michael.Kane on 2007-10-20
> **LanDan said:**
> i know the "fix only" policy and that backports are a security risk that need a conservative approach, but this would make ubuntu a non-option for any production environment

and i don't see any practical problem between porting a edgy or gutsy app for dapper

Dependencies change,As well as libraries. which you would have to make sure are compatible with rest of the OS you are seeking to backport to.

---

### Post by LanDan on 2007-10-20
> **SD-Plissken said:**
> Dependencies change,As well as libraries. which you would have to make sure are compatible with rest of the OS you are seeking to backport to.

that would be my point exactley why you need well tested backports available

---

### Post by LanDan on 2007-10-20
> **plb said:**
> Stick with Debian.

lol :) i can't do Debian for this, i need the languagepacks!

guess thats how vendor-lockin starts :)

---

