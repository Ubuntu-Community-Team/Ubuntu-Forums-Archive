---
title: "Is it possible to downgrade compiz?"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pqwoerituytrueiwoq on 2012-04-22
I encountered a couple bugs in compiz while testing it
one of which i can not accept
the version that is on natty has a issue i can't stand as well
i did try LMDE  update 4 it has compiz 0.8.4
[IMG]http://i.imgur.com/HMkNX.png[/IMG]
i did not encounter any bugs in it i would like t know if i can downgrade compiz to this version without going though unmet dependency hell
should i just try it and see what happens? :lolflag:

i dont care it is breaks unity which i expect

---

### Post by xyzzyman on 2012-04-22
> **pqwoerituytrueiwoq said:**
> I encountered a couple bugs in compiz while testing it
one of which i can not accept
the version that is on natty has a issue i can't stand as well
i did try LMDE  update 4 it has compiz 0.8.4
[IMG]http://i.imgur.com/HMkNX.png[/IMG]
i did not encounter any bugs in it i would like t know if i can downgrade compiz to this version without going though unmet dependency hell
should i just try it and see what happens? :lolflag:

i dont care it is breaks unity which i expect

Dropping from 0.9.7.6 to 0.8.4... You're going to have to find all the debs manually. Your efforts would best be to file bug reports on what's broken and give as much help as possible. Be nice to the guy who works on it, as seen by this bug report: [https://bugs.launchpad.net/unity/+bug/861710](https://bugs.launchpad.net/unity/+bug/861710)

---

### Post by jbicha on 2012-04-22
No, downgrading Compiz is definitely not supported. How about telling us what your  problem with Compiz is instead?

---

### Post by pqwoerituytrueiwoq on 2012-04-22
already reported bugs i just need working compiz in the mean time till it is fixed
i did manage to get it working and broke several things doing it and fixed them
i purged metacity, all unity stuff, and compiz and installed these:
compizconfig-backend-gconf_0.8.4-1_amd64.deb
compizconfig-settings-manager_0.8.4-2_amd64.deb
compiz-core_0.8.4-5.1_amd64.deb
compiz-fusion-plugins-extra_0.8.4-2_amd64.deb
compiz-fusion-plugins-main_0.8.4-2+b1_amd64.deb
compiz-fusion-plugins-unsupported_0.8.4-3_amd64.deb
compiz-gtk_0.8.4-5.1_amd64.deb
compiz-plugins_0.8.4-5.1_amd64.deb
fusion-icon_0.1.0-2_all.deb
libcompizconfig0_0.8.4-2_amd64.deb
libdecoration0_0.8.4-5.1_amd64.deb
libmetacity-private0a_1%3a2.34.1-2_amd64.deb
python-compizconfig_0.8.4-2+b1_amd64.deb

these are my issues:
[http://youtu.be/etB_9B1EZGg](http://youtu.be/etB_9B1EZGg)
i can live without window previews but not the other
bug reports:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/965577](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/965577)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/986679]("https://bugs.launchpad.net/ubuntu/+source/compiz-extra/+bug/296087")

EDIT:
This breaks litedm you will have to use gdm or you will not be able to login to the gui i was able to fix this via ssh by using gdm yuo loose access to the guest session at login

---

### Post by mc4man on 2012-04-22
As I mentioned - [the cursor disconnect on edge flip]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/965577") will be fixed when the branch concerning 'flashing' in rotate & expo gets merged & released. It's not a targeted bug for that branch but unless it get 're-broken' should be ok.

It won't be before SRU-0 at the earliest, hopefully at some point soon the people involved (3) reach some happy place, merge it & move on. Hoping for something positive next week

---

### Post by pqwoerituytrueiwoq on 2012-04-22
sorry must have missed that
edit 
so that is where the flicker is shows up in cube rotate but not wall so i never saw the flicker

---

