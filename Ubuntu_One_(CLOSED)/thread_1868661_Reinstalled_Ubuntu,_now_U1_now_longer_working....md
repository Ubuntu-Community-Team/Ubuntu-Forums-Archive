---
title: "Reinstalled Ubuntu, now U1 now longer working..."
date: 2011-10-24
forum: Ubuntu One (CLOSED)
---

### Post by Z80A on 2011-10-24
I have recently totally reinstalled this machine (11.10), but of course reused the name of the machine. Now as I start up UbuntuOne, I click "*already have an account*" button to sign in. And I KNOW that I type the correct username (e-mail address) and password (this is verified on the web UI and other Ubuntu machine), but i get this odd message as I try to login (in the login box):[INDENT][FONT=Arial]**[COLOR=Red]Method "CreateItem" with signature "[/COLOR]**[COLOR=Red]**a{sv}(oayay)b**[/COLOR][/FONT][FONT=Arial]**[COLOR=Red]" on[/COLOR]**[/FONT]
[FONT=Arial]**[COLOR=Red] interface "org.freedesktop.Secret.Collection" doesn't exist[/COLOR]**[/FONT]
[/INDENT]Now in the web UI I have removed every trace of this machine and in my keyring I see nothing related to UbuntuOne and I can not really think of anything else to do. Seems to be a combination of local machine settings and a server side error. Any good ideas or tricks?

---

### Post by Z80A on 2011-10-25
Just a thought; could it be an idea to remove **~/.config/ubuntuone/syncdaemon.conf** and then restart the client? Would this be sufficient to kind of "reset" the UbuntuOne setup or does it take more than that?

Edit: ...and then just realised that the **syncdaemon.conf** has _not_ been created and the **UbuntuOne** folder is also _missing_. Any way to reset and start this UbuntuOne thing from scratch again?

---

### Post by Z80A on 2011-10-28
Doesn't look like many experience this kind of problem... I very much rely on UbuntuOne for "file mobility" and need to get this working again. I am considering removing UbuntuOne (_temporarily_ of course) and then reinstalling it. My fear is that some configuration data will remain and still prevent me from connecting. Anyone with experiences in this?

Ultimately, I would consider a total re-installation of Ubuntu 11.10 (having in mind the smooth and pleasant experience it is... :D). I would still be giving the machine the same name - hope that is not a part of what seems to be causing the conflict - does anyone know how the machine name influences how the client connects to the UbuntuOne server side?

Still hoping for some way of using **u1sync **or **u1sdtool **commands for kind of resetting...

---

### Post by easy_target on 2011-10-30
Any luck with this yet? I have Gnome installed and apparently it has something to do with it.

---

### Post by Z80A on 2011-10-31
Kind of status quo - could do well with some hint from people with  deeper UbuntuOne insight. I am not quite sure, that I on my own will  manage to put my current UbuntuOne installation into a "factory default"  setting. I will likely do total re-installation one of these days (also  having problems with Gwibber/Facebook and colors on HP DeskJet  895Cxi).

"...Gnome installed..."? Gnome Shell? My system is "off the shelf"  Ubuntu 11.10 and I always aim at using "plain vanilla" configurations to  the extend possible in order to only see problems common to what others  experience using mainstream distributions. Not much luck this time  though...  :(

---

### Post by kapetr on 2011-11-02
It is bug - (partially) fixed.

I don't remember the number now, but search it and you will find it.
Ors simply Google the error message.

---

### Post by Z80A on 2011-11-04
[FONT=Verdana]Just as sort of status on this matter, which I am sure I will mark as closed in the near future, here is an update: I mentioned the problem to the Canonical guys at UbuntuOne support, and they (my new friend Joshua at Canonical) have now confirmed that the problem has been identified as an issue with gnome-keyring and a patch is being worked on:[/FONT][INDENT][FONT=Verdana][https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/874501](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/874501)
[/FONT] [/INDENT][FONT=Verdana]I take a rest from this one and await some update being pushed and I hope to mark this as solved.

[/FONT]      [FONT=Verdana]Never had this kind of interaction with the organization behind my Windows systems, for which I have actually paid...[/FONT]

---

### Post by duanedesign on 2011-11-04
Yes this fix is making its way to the repos. If you absolutely can not wait the fix has been uploaded to a PPA.

```
sudo apt-add-repository ppa:rye/ubuntuone-support
sudo apt-get update
sudo apt-get upgrade
```

I would then remove the ppa:

```
sudo ppa-purge ppa:rye/ubuntuone-support
```

---

### Post by Z80A on 2011-12-04
Haven't been giving this much attention lately, but this bu is still annoying and prevents me from using U1 on this specific machine. I am still awaiting the official fix and try to check Launchpad from time to time:
[INDENT][https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/874501](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/874501)
[/INDENT] Not being actively involved with software development, could someone give me a hint of the status? As I see it, the bug and fix has been identified, but has not been officially released and pushed to end-users - is this the correct interpretation?

---

### Post by Z80A on 2011-12-13
Problem resolved through official bug fix today:
[INDENT] [FONT=Courier New]This bug was fixed in the package gnome-keyring - 3.2.2-0ubuntu0.1
 ---------------
gnome-keyring (3.2.2-0ubuntu0.1) oneiric-proposed; urgency=low
   * New upstream release.
    - Use g_random_int_range() for pseudo-random hash iteration
      count. (LP: [#874501]("https://bugs.launchpad.net/bugs/874501"))
    - Fix problem with 'unsafe storage' prompt deadlocking
    - Remove XFCE & LXDE from OnlyShowIn for autostart files
    - Make clear source of warnings from the rpc module
  * debian/patches/05_revert_order_fix.patch
    - revert upstream fix which always returns most recent keyring result,
      it is hard to verify for an SRU and hard to predict the possibility
      for regression
 -- Ken VanDine <email address hidden>   Mon, 28 Nov 2011 14:20:08 -0500
[/FONT][/INDENT]

---

