---
title: "Nautilus 3.6.1"
date: 2012-10-29
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-10-29
Well, so now we have the new Nautilus 3.6.1 in repos of RR.

> **[SIZE=3]Changelog[/SIZE]**

          nautilus (1:3.6.1-0ubuntu1) raring; urgency=low   [ Jeremy Bicha ]
* New upstream release (LP: [#1057780]("https://launchpad.net/bugs/1057780")).
* Dropped git patches
* debian/control.in:
 - Bump minimum GTK & GLib
* debian/nautilus.install, nautilus-data.install:
 - Install GNOME Shell search provider
 - Drop obsolete hicolor icons
* debian/patches/05_desktop_menu_export.patch:
 - commented, it needs to be mostly rewriten for the new design
  or implemented in a different place or way
* Refreshed patches:
 - 03_translations_list_update.patch
 - 12_unity_launcher_support.patch
 - 14_bring_del_instead_ctrl_del.patch
 - 15_use-ubuntu-help.patch[ Dmitry Shachnev ]
* Drop 21_correct_timestamp_use_fix_focus_issue.patch, it's not needed
  with the new version and is causing segmentation faults:
  -- Jeremy Bicha <email address hidden>   Sun, 28 Oct 2012 20:07:08 -0400 

---

### Post by thotz on 2012-10-29
Thank for the news, I like the new design.

---

### Post by dino99 on 2012-10-30
I'm already getting issue for mounting the other distro partitions:

Unable to access &#8220;LTS32&#8221;
Adding read ACL for uid 1000 to `/media/oem' failed: Operation not supported

that was working before upgrading nautilus.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1073084](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1073084)

---

### Post by Yahoé on 2012-10-30
Indeed files 3.6.1 is in Raring now, and with it, again after it's brief life in  Quantal, we lost some important functions, like my favourite, the split panes F3.

---

### Post by mcellius on 2012-10-30
> **Yahoé said:**
> Indeed files 3.6.1 is in Raring now, and with it, again after it's brief life in  Quantal, we lost some important functions, like my favourite, the split panes F3.

Same here.  I like the new look of Nautilus 3.6.1, but the removed functionality makes it less useful for me.  It's disappointing.

---

### Post by jbicha on 2012-10-30
> **dino99 said:**
> I'm already getting issue for mounting the other distro partitions:

Unable to access “LTS32”
Adding read ACL for uid 1000 to `/media/oem' failed: Operation not supported

that was working before upgrading nautilus.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1073084](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1073084)

Silly question, but have you tried rebooting? (I'm still on quantal for a few more days.)

---

### Post by dino99 on 2012-10-30
> **jbicha said:**
> Silly question, but have you tried rebooting? (I'm still on quantal for a few more days.)

yes indeed, the upgrade was done yesterday, since i've rebooted several times.

---

### Post by mc4man on 2012-10-30
I guess they'll be deciding whether to stick with 3.6.1 or move to 3.7/8 
(though maybe some would like to go elsewhere.
If sticking with 3.6.1 hopefully the recursive search commits will be applied, it works quite well *came in right after 3.6.1

(sample patch for self builders line adjusted for 3.6.1 attached
vcs imports 16732 thru 16734

---

### Post by philinux on 2012-10-30
> **mc4man said:**
> I guess they'll be deciding whether to stick with 3.6.1 or move to 3.7/8 
(though maybe some would like to go elsewhere.
If sticking with 3.6.1 hopefully the recursive search commits will be applied, it works quite well *came in right after 3.6.1

(sample patch for self builders line adjusted for 3.6.1 attached
vcs imports 16732 thru 16734
I think 3.8 maybe on the cards.

[http://summit.ubuntu.com/uds-r/meeting/21371/desktop-r-default-file-manager/](http://summit.ubuntu.com/uds-r/meeting/21371/desktop-r-default-file-manager/)

---

### Post by dino99 on 2012-10-30
> **philinux said:**
> I think 3.8 maybe on the cards.

[http://summit.ubuntu.com/uds-r/meeting/21371/desktop-r-default-file-manager/](http://summit.ubuntu.com/uds-r/meeting/21371/desktop-r-default-file-manager/)

as the choice is about using gnome stable for 13.04, 3.8 will not be ready i suppose, but only available via a gnome3 ppa.

---

### Post by philinux on 2012-10-30
Summary of UDS session.

[http://www.omgubuntu.co.uk/2012/10/ubuntus-default-file-manager-debated-at-uds?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/10/ubuntus-default-file-manager-debated-at-uds?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by mc4man on 2012-10-30
> **philinux said:**
> Summary of UDS session.

Sounds fairly positive - personally don't think a "traditional" app menu is that necessary. (menu bar??
At least here have no issue with nautilus menus being broken up - 
app
cog
view
context
(having the cog & view in nautilus window is actually more to my liking

---

### Post by ventrical on 2012-10-30
Looks like the 'permissions' (me) is back.

---

### Post by mc4man on 2012-10-30
> **ventrical said:**
> Looks like the 'permissions' (me) is back.
I don't see Ubuntu or Redhat(Gnome) changing the "Me" deal though I guess if inclined the gnome 3 ppa or any ppa could revert it easily.
(or one can do for themselves, nautilus is any easy build, takes just a few minutes.

no_me patch attached for those inclined, written for current 3.6.1 deb

(for 3.6.1 here I've made a few changes - 
got rid of Me
rearranged toolbar, added up (parent) button
re-enabled 'open with' on folders
restored list tree view
combined toolbar & sidebar colorwise
added recursive search

---

### Post by dino99 on 2012-10-31
> **mc4man said:**
> I don't see Ubuntu or Redhat(Gnome) changing the "Me" deal though I guess if inclined the gnome 3 ppa or any ppa could revert it easily.
(or one can do for themselves, nautilus is any easy build, takes just a few minutes.

no_me patch attached for those inclined, written for current 3.6.1 deb

(for 3.6.1 here I've made a few changes - 
got rid of Me
rearranged toolbar, added up (parent) button
re-enabled 'open with' on folders
restored list tree view
combined toolbar & sidebar colorwise
added recursive search

it only miss the tree view into the left pane (its easier than navigating into the main pane)

---

### Post by philinux on 2012-11-02
Couple of typos in this article,

[http://www.iloveubuntu.net/jason-warner-ubuntu-desktop-manger-uds-r-were-going-stick-nautilus](http://www.iloveubuntu.net/jason-warner-ubuntu-desktop-manger-uds-r-were-going-stick-nautilus)

---

### Post by mc4man on 2012-11-03
> **dino99 said:**
> it only miss the tree view into the left pane (its easier than navigating into the main pane)

I did take a look at that in early sept. - was too much code removed (for me) to put back & maintain.
As it was the list tree turned into quite alot, after the initial removal they kept going back back & removing supporting/now unused code.
I had to build naut every other day for 5 weeks to keep track, ect.
(though maybe someone who knows naut well would have an easier time.

For 3.8 probably won't bother much with the list tree unless my current patch slots in with minimal work.
(the rest of what I personally want modded should be good for some time as they are minor code changes or reordering

---

