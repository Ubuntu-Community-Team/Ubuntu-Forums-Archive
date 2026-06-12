---
title: "Remove Gnome Shell: Restore Unity"
date: 2013-02-09
forum: Ubuntu Development Version
---

### Post by mooreted on 2013-02-09
I have Ubuntu 13.04 and was trying out Gnome Shell. I have decided to go back to Unity. The problem is; the Appearance setting is gone, all the dialogs are Gnome3 dialogs, Nautilus is the Gnome version.

How can I remove Gnome Shell and get back to pure Unity?

---

### Post by elliotn on 2013-02-10
```
#sudo apt-get install unity
```
that will install unity

---

### Post by mooreted on 2013-02-10
Thank you for the reply:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity is already the newest version."

Unity runs, but all the settings and themes are Gnome3 settings and themes. And there is no Appearance setting in System Settings so I can't change background, icons, themes, etc.

---

### Post by mooreted on 2013-02-10
Maybe a screen shot would help:

[https://docs.google.com/file/d/0B7OBAVz87uTLb1lhSWtDTXpGU1k/edit?usp=sharing](https://docs.google.com/file/d/0B7OBAVz87uTLb1lhSWtDTXpGU1k/edit?usp=sharing)

---

### Post by kurt18947 on 2013-02-10
> **mooreted said:**
> Maybe a screen shot would help:

[https://docs.google.com/file/d/0B7OBAVz87uTLb1lhSWtDTXpGU1k/edit?usp=sharing](https://docs.google.com/file/d/0B7OBAVz87uTLb1lhSWtDTXpGU1k/edit?usp=sharing)

It appears that link only works for those with google accounts.  Do you know about the 'gear' icon to the right of your log-in name that selects different desktops?  i'd go to the software center or Synaptic and uninstall gnome-shell.  Look at what is being uninstalled before clicking 'go'.

---

### Post by mooreted on 2013-02-10
Sorry, forgot to make the link public. Should work now.

I removed Gnome Shell but no change.

Something kind of strange: When I look at Settings/Details it says I'm running 13.04 but when I boot it says I'm running 12.10.

---

### Post by Bufeu on 2013-02-10
*unity --replace* should replace your current DE with Unity.

EDIT:
What does lsb_release -a and cat /etc/*-release says?

---

### Post by mooreted on 2013-02-10
The realase commands show as Ubuntu 12.10.

unity --replace throws about a hundred errors at me.

Might have to re-install one of these days.

---

### Post by dino99 on 2013-02-10
have just checked my System Settings here , and the Appearance icon is gone too; very bad, need to report that bug.

---

### Post by mooreted on 2013-02-10
Oh, so, it's not just me. I thought I broke something.

---

### Post by howefield on 2013-02-10
Thread moved to the "*Ubuntu +1 (Raring Ringtail)*" forum.

---

### Post by mc4man on 2013-02-10
Do you have installed - 
gnome-control-center-unity, ubuntu-settings, ubuntu-desktop

---

### Post by kansasnoob on 2013-02-10
> **mc4man said:**
> Do you have installed - 
gnome-control-center-unity, ubuntu-settings, ubuntu-desktop

I was thinking we needed to know exactly how gnome-shell was installed :confused:

A lot of people just install the packages 'gnome' or 'gnome-shell' which I think should be deprecated in favor of 'ubuntu-gnome-desktop'.

It's hard to parse things w/o the appropriate 'apt' logs, but sometimes they can be so old that you'd have to pour over several compressed logs :(

---

### Post by mc4man on 2013-02-10
> **kansasnoob said:**
> 

It's hard to parse things w/o the appropriate 'apt' logs, but sometimes they can be so old that you'd have to pour over several compressed logs :(

One of the good reasons to use synaptic for all  is it gives one a very accessible & readable history 
(synaptic has a few gtk3 issues but none are more than a slight annoyance, opening history is one..

---

### Post by mooreted on 2013-02-10
> **kansasnoob said:**
> I was thinking we needed to know exactly how gnome-shell was installed :confused:

A lot of people just install the packages 'gnome' or 'gnome-shell' which I think should be deprecated in favor of 'ubuntu-gnome-desktop'.

It's hard to parse things w/o the appropriate 'apt' logs, but sometimes they can be so old that you'd have to pour over several compressed logs :(

Yeah, I just did "sudo apt-get install gnome-shell"

---

### Post by mooreted on 2013-02-10
> **mc4man said:**
> Do you have installed - 
gnome-control-center-unity, ubuntu-settings, ubuntu-desktop

Ah ha! That was it. I didn't have "gnome-control-center-unity" installed.

Thank you.

---

### Post by mc4man on 2013-02-10
> **mooreted said:**
> The realase commands show as Ubuntu 12.10.

unity --replace throws about a hundred errors at me.

Might have to re-install one of these days.

Side note - starting in 12.10 unity --reset no longer is used, for current way see here
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)

---

### Post by mooreted on 2013-02-10
> **mc4man said:**
> Side note - starting in 12.10 unity --replace no longer is used, for current way see here
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)

Great, thanks. I'll check that out.

---

### Post by kansasnoob on 2013-02-10
> **mc4man said:**
> Side note - starting in 12.10 unity --replace no longer is used, for current way see here
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)

That's super awesome ........... something I'd missed :D

---

### Post by dino99 on 2013-02-11
"dconf reset" is too cool to me (dont want to redo the custom settings) ;)

but still miss that Appearance icon here with gnome-classic

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122190](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122190)

---

### Post by zika on 2013-02-11
> **mc4man said:**
> Side note - starting in 12.10 unity --replace no longer is used, for current way see here
[http://ubuntuforums.org/showpost.php?p=12222839&postcount=9](http://ubuntuforums.org/showpost.php?p=12222839&postcount=9)
Are You takling about```
unity --replace
```or```
unity --reset
```?

---

### Post by mc4man on 2013-02-11
> **zika said:**
> Are You takling about```
unity --replace
```or```
unity--reset
```?
The later, thanks, will fix post

---

### Post by jerrylamos on 2013-02-12
In development testing I re-install.  Often.  Either something breaks or looks like endless updates have made raring bigger and bigger in spite of removes and purges.

So best way in my experience to get rid of a ppa is re-install.  I usually have a couple raring partitions and a precise partition on each test pc's.  Install is good for causing bugs....

---

