---
title: "Is Edgy Safe Yet?"
date: 2007-01-08
forum: The Cafe
---

### Post by Luggy on 2007-01-08
I remember back when Edgy was first released all the people who updated were complaining about things being broken and they had to either do a fresh install or went back to Dapper.

Have these issues been fixed yet?

I run Edgy on my home computer and things are going good now and I want to update my work computer from Dapper to Edgy but I don't want to fight with getting it installed correctly and I can't afford the down time of doing a fresh install.

So, is Edgy safe yet?

---

### Post by Mateo on 2007-01-08
works fine for me.

---

### Post by Cariboo1938 on 2007-01-08
No problems occurred yet! I run Edgy-amd64!;)

---

### Post by frodon on 2007-01-08
> **Luggy said:**
> I remember back when Edgy was first released all the people who updated were complaining about things being broken and they had to either do a fresh install or went back to Dapper.

Have these issues been fixed yet?This is not really true, when each release comes many threads are opened about problems with the upgrade because it's not always easy for some users to perform an upgrade but most of us didn't get any problems with edgy.

Keep in mind that only persons with issues post support requests.

> **Luggy said:**
>  run Edgy on my home computer and things are going good now and I want to update my work computer from Dapper to Edgy but I don't want to fight with getting it installed correctly and I can't afford the down time of doing a fresh install.

So, is Edgy safe yet?I suggest you to just make a ghost of your partition thus you can run the update eyes closed and restore your partition with your ghost image if you're not happy with edgy.

You can use partimage for example :
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Medieval_Creations on 2007-01-08
I haven't had any problems with the upgrade.  I upgraded my Desktop & 2 of my laptops from Dapper to Edgy with no problems.  I lost my RAID when I upgraded the desktop but that was most likely a goof on my part.  I got it back up in a day or so and life is good.

---

### Post by BarfBag on 2007-01-08
Works flawless for me.  The AMD 64 one was just plain awful, though.  I downgraded to the normal version.

---

### Post by ssam on 2007-01-08
if you have installed things from custom repos, used automatix/easyubuntu, installed software not from repos (eg installing newer versions of firefox) then you may get problems during the upgrade.

also make sure you have the ubuntu-desktop package installed.

it is recommended that you use
```
gksu "update-manager -c"
```
this does some extra check to try to help things go smoothly.

make sure you read [https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes)

i think some people still suffer problems with swap partitions not being recognised, have a look in launchpad for solutions.

and finally make sure you have a back up.

---

### Post by macogw on 2007-01-08
I had issues because A) I used command line update B) I did an offline update.  If you're doing it online using the GUI, you'll be fine.  I think at the time there was a little bit of "Gnome's not quite right yet.." but that was fixed within 2 days or so.

---

### Post by Klaidas on 2007-01-08
Fresh install FTW ;)

---

