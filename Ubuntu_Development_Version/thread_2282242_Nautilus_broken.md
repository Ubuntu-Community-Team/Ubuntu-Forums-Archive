---
title: "Nautilus broken?"
date: 2015-06-12
forum: Ubuntu Development Version
---

### Post by sgage on 2015-06-12
Nautilus is throwing a segfault today. No icons on the desktop, no file manager, no nothing. What's up?

[This is Gnome 3.16 from proposed]

---

### Post by cariboo on 2015-06-12
I just got the gnome 3.16 update this morning from the regular repositories. I've used nautilus, to transfer a 2GiB file form my laptop to file server and didn't run into any problems. As a matter of fact the transfer rates were steady at 3.3Mbps, I've never seen that kind of speed before on this laptop. I know it has nothing to do with nautilus, but it was nice to see. :)

---

### Post by dino99 on 2015-06-13
i'm using 3.16.1 from the staging ppa, and does not get issue on ubu with GS

---

### Post by ventrical on 2015-06-13
not broke here..

---

### Post by monkeybrain20122 on 2015-06-13
Just out of curiosity, is there a delete bypassing trash option in Preferences > Behaviour in Ubuntu's Nautilus 3.16? I ask because of [http://ubuntuforums.org/showthread.php?t=2280959](http://ubuntuforums.org/showthread.php?t=2280959)

---

### Post by dino99 on 2015-06-13
> **monkeybrain20122 said:**
> Just out of curiosity, is there a delete bypassing trash option in Preferences > Behaviour in Ubuntu's Nautilus 3.16? I ask because of [http://ubuntuforums.org/showthread.php?t=2280959](http://ubuntuforums.org/showthread.php?t=2280959)

this has been disabled as some coding tweaks are not yet done

---

### Post by sgage on 2015-06-13
> **dino99 said:**
> i'm using 3.16.1 from the staging ppa, and does not get issue on ubu with GS

I reinstalled, and stock Ubuntu Gnome is now 3.16.2. Nautilus works fine...

---

### Post by sgage on 2015-06-13
> **ventrical said:**
> not broke here..

Not really sure how I broke mine, but no matter - I reinstalled, and now Ubuntu Gnome is sporting 3.16.2 right out of the box :KS

---

### Post by mc4man on 2015-06-13
> **monkeybrain20122 said:**
> Just out of curiosity, is there a delete bypassing trash option in Preferences > Behaviour in Ubuntu's Nautilus 3.16? I ask because of [http://ubuntuforums.org/showthread.php?t=2280959](http://ubuntuforums.org/showthread.php?t=2280959)
The option to include a delete option is gone, apparently the shortcut remains - 
[https://git.gnome.org/browse/nautilus/commit/?id=655e415e3a5ead27d98b03db14155d61943715ef](https://git.gnome.org/browse/nautilus/commit/?id=655e415e3a5ead27d98b03db14155d61943715ef)

---

### Post by ventrical on 2015-06-13
> **sgage said:**
> Not really sure how I broke mine, but no matter - I reinstalled, and now Ubuntu Gnome is sporting 3.16.2 right out of the box :KS

I just checked my repos and the original staging /ppa/ has been ripped out (meaning it is gone). I have been nursing that ppa since inception. Strange. The mkusb /ppa/ is still there so it beats me as to how this happened. Perhaps it was some auto-remove when we rolled into 15.10?

Regards..

---

### Post by rrnbtter on 2015-06-13
Greetings,
Broken, currently using Midnight Commander

---

### Post by monkeybrain20122 on 2015-06-13
> **mc4man said:**
> The option to include a delete option is gone, apparently the shortcut remains - 
[https://git.gnome.org/browse/nautilus/commit/?id=655e415e3a5ead27d98b03db14155d61943715ef](https://git.gnome.org/browse/nautilus/commit/?id=655e415e3a5ead27d98b03db14155d61943715ef)

That is just great, one more regression of usability pretending to be an 'improvement'. with the shortcut you need to choose the file to delete which has no keyboard shortcut and then reach out to the delete key, with the context menu you can just do it with a click. I am wondering, at least for Unity, if there is a plan or a way to restore this perhaps by rebuilding Nautilus? All other file managers have a permanently delete option. I really don't get it why they try to force people to use the trash, which is trash.

---

### Post by dino99 on 2015-06-13
> **monkeybrain20122 said:**
> That is just great, one more regression of usability pretending to be an 'improvement'. with the shortcut you need to choose the file to delete which has no keyboard shortcut and then reach out to the delete key, with the context menu you can just do it with a click. I am wondering, at least for Unity, if there is a plan or a way to restore this perhaps by rebuilding Nautilus? All other file managers have a permanently delete option. I really don't get it why they try to force people to use the trash, which is trash.

As previously said, that feature needs to be rewritten in the 3.16 version; and devs have considered it was a minor feature for the moment. The trash command will be reactivated when the new code will be available. Its not a show stopper by the way (you surely knows the command line if you need to delete some files).

---

### Post by monkeybrain20122 on 2015-06-13
> **dino99 said:**
> As previously said, that feature needs to be rewritten in the 3.16 version; and devs have considered it was a minor feature for the moment. The trash command will be reactivated when the new code will be available. Its not a show stopper by the way (you surely knows the command line if you need to delete some files).

Where did you see that it will be reactivated? It doesn't sound like it from mc4man's link.

---

### Post by mc4man on 2015-06-13
> **monkeybrain20122 said:**
> Where did you see that it will be reactivated? It doesn't sound like it from mc4man's link.
What Ubuntu chooses to patch back to nautilus is basically nonsensical & somewhat arbitrary. So it would be hard to say especially since nautilus is still at **3.14** in Ubuntu wily.
If there is an upstream accepted bug on this then it may end up back in Ubuntu, who knows.

A small example there is I tried for quite some time, ([almost 3 yrs now]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254")) to get Ubuntu to add back 'open with' on folders, they declined with some alice in wonderland reasoning. Eventually gave up & just ppa'd, now I see Gnome has added it back in 3.16+. So I guess they do occasionally relent to prior nonsense..

In this case it may not be that hard to revert though as time goes by some stuff like this becomes not reasonably possible.
Edit: - so for example if nautilus 3.16+ is installed with current wily gedit then gedit won't open due to  - 
(gedit:4106): GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' does not contain a key named 'enable-delete'
In that case it's possible that a gedit that works with nautilus 3.16+ may segfault on a nautilus that does have that key. If that's the case then 2 sources have to be adjusted making the possibility in Ubuntu alone close to nil..

---

### Post by monkeybrain20122 on 2015-06-14
> **mc4man said:**
> 
Edit: - so for example if nautilus 3.16+ is installed with current wily gedit then gedit won't open due to  - 
(gedit:4106): GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' does not contain a key named 'enable-delete'
In that case it's possible that a gedit that works with nautilus 3.16+ may segfault on a nautilus that does have that key. If that's the case then 2 sources have to be adjusted making the possibility in Ubuntu alone close to nil..

This from a user on the Fedora forum (he didn't provide any link)

```
========================================
  nautilus
========================================

Major changes in 3.17.2:
* Fix window focus issues when starting nautilus (Carlos Soriano)
* Fix handling of command line options in diferent cases (Carlos Soriano)
* Decrease the padding on list view (Carlos Soriano)
* Use a dialog for creating folders (Georges Basile Stavracas Neto)
* Use a dialog for renaming files (Carlos Soriano)
* Allow F5 and ctrl+r as shortcuts for refresh the view (Carlos Soriano)
* Make the zoom slider the preference itself (Carlos Soriano)
* Allow opening with a different app than default for multiple files (Carlos Soriano)
* Fix view scrolling when selecting with ctrl + mouse (Georges Basile Stavracas Neto)
* Don't always make the sidebar visible on start (Antonio Fernandes)
* Allow opening folders with another app (Carlos Soriano)
* **Show Delete Permanently on systems that does not support Trash (Carlos Soriano)**
* Add Alt<down> shorcut for opening
* Fix some icons sizes inconsistency (Cosimo Cechi)
* Add public API documentation for Nautilus extensions (Cosimo Cechi)
* Add a gsetting to toggle recursive search (Felipe Borges) 			 		 
```

So am I correct in thinking that the key enabled-delete should not be in conflict with other applications?

---

### Post by mc4man on 2015-06-14
> **monkeybrain20122 said:**
> This from a user on the Fedora forum (he didn't provide any link)



So am I correct in thinking that the key enabled-delete should not be in conflict with other applications?
From the perspective that the key no longer exists there'd be no conflicts.

---

### Post by monkeybrain20122 on 2015-06-14
> **mc4man said:**
> From the perspective that the key no longer exists there'd be no conflicts.

I meant would that be a conflict with say gedit in your example if the key is restored.

---

### Post by dino99 on 2015-06-14
> **monkeybrain20122 said:**
> Where did you see that it will be reactivated? It doesn't sound like it from mc4man's link.

From the gnome3-staging ppa:

nautilus (1:3.16.2-0ubuntu1~vivid1) vivid; urgency=medium

  [ Tim Lunn ]
  * New upstream release
  * debian/patches:
    - Disable traditional menu's this will need to be ported to
      GActions/gtkbuilder

******* So waiting for that portage being done ***********

---

### Post by mc4man on 2015-06-14
> **monkeybrain20122 said:**
> I meant would that be a conflict with say gedit in your example if the key is restored.

Not in any position to tell, would need to have nautilus 3.16.x with a working gedit.
On the question of whether the context delete can be restored it seems possible in nautilus 3.16, at least in the vivid gnome ppa version, screens would show (eg, installed the vivid ppa nautilus source patched packages into wily

---

### Post by monkeybrain20122 on 2015-06-14
> **mc4man said:**
> Not in any position to tell, would need to have nautilus 3.16.x with a working gedit.
On the question of whether the context delete can be restored it seems possible in nautilus 3.16, at least in the vivid gnome ppa version, screens would show (eg, installed the vivid ppa nautilus source patched packages into wily

Thanks.

---

