---
title: "testing unity-session in 18.04/nautilus ppa"
date: 2017-10-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-10-25
We are currently testing nautilus which had the header bar patch removed in 17.10. We want it to use the traditional title bar. Anyone wanting to test it can: 


How to test.
```


[LIST=1]
[*] Add my ppa and update nautilus.
 sudo add-apt-repository ppa:khurshid-alam/unity7-testing
sudo apt-get update
sudo apt-get install nautilus

[*] Reboot and login to unity-session.

[*] Check if it is using traditional titlebar and working well.

[*] Log out and log in to ubuntu (both xorg and wayland) and check if it is using headerbar.

[*] Report back here if you have any issue.
[/LIST]
 If everything goes well, I will make a merge request. Thanks.
 Note: If you have nvidia and if the desktop crashes on wayland, then it’s not a nautilus issue. Just skip testing on wayland.

```

Here is related tracking bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1727168](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1727168)

regards..

---

### Post by Chanath on 2017-10-25
Can you post a screenshot of this Nautilus with the traditional header bar?
EDIT: No need. I just checked Ubuntu 17.04, so I understand, what you are talking about.

---

### Post by Chanath on 2017-10-26
Yes, now Nautilus looks more like Ubuntu...

---

### Post by mc4man on 2017-10-29
At least here looks don't matter as much as function. The path I've decided to explore for 18.04 would be,
unity7, xorg, lightdm & nemo as the file manager. I've reached the point where nautilus greater than 3.14 is no longer something I'd use.

Have got it going reasonably well, there were a few issues to overcome (most notable was cursor run on when using nemo quicklists, that required patching compiz to disable busy cursor altogther..

If any interest would start a thread elsewhere (not this sub forum) as to method & what could be improved. Nemo is everything nautilus used to be..

---

### Post by Chanath on 2017-10-30
> **mc4man said:**
> At least here looks don't matter as much as function. The path I've decided to explore for 18.04 would be,
unity7, xorg, lightdm & nemo as the file manager. I've reached the point where nautilus greater than 3.14 is no longer something I'd use.

How did you make Nemo take over the desktop?

---

### Post by mc4man on 2017-10-30
> **Chanath said:**
> How did you make Nemo take over the desktop?

Discussion of that is for somewhere else so **final** comment here -

There are 2 things, being default file manager & handling the desktop.
As far as nemo both are easy to do but there are issues with nemo handling the desktop in gnome 3.26+
So currently best solution is to allow nautilus to handle the desktop & have nemo as default manager which includes opening any folders on the desktop & any volumes in the unity launcher.

There is no real resource hit with nautilus just doing that & no apparent conflicts. The only other thing nautilus does is control the context menu on the Desktop & files on the Desktop which again is ok & currently better than what nemo could do. (small exception is context menu compressing on Desktop items, you'd get the limited nautilus compressor options, again no big deal.

Whether nemo's handling of the Desktop in gnome 3.26+ can be improved is not yet clear..

---

### Post by Chanath on 2017-10-30
@mc4man

When you start a topic on this matter, let us know where it would be. I'd be happy to use Nemo, instead of Nautilus, together with taking over the desktop. :)

---

### Post by mc4man on 2017-10-30
> **Chanath said:**
> @mc4man

When you start a topic on this matter, let us know where it would be. I'd be happy to use Nemo, instead of Nautilus, together with taking over the desktop. :)
That won't be for some time, am hoping this ppa moves forward as it has numerous unity patchs that could resolve some issues

[https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3)

Over & out..

---

### Post by ventrical on 2017-10-30
> **mc4man said:**
> At least here looks don't matter as much as function. The path I've decided to explore for 18.04 would be,
unity7, xorg, lightdm & nemo as the file manager. I've reached the point where nautilus greater than 3.14 is no longer something I'd use.

Have got it going reasonably well, there were a few issues to overcome (most notable was cursor run on when using nemo quicklists, that required patching compiz to disable busy cursor altogther..

If any interest would start a thread elsewhere (not this sub forum) as to method & what could be improved. Nemo is everything nautilus used to be..

I suggested another file manager but Khurshid puts is like this:

> 
PCMFM doesn’t use gtk-headerbar. It uses toolbar+titlebar (like gimp,  synaptic). Technically we can use any file-manager. But it’s the  integration which is important.

 Nautilus draws the desktop, icons on desktop and tied up with  wallpaper which is related to gnome-settings-daemon. This, in turn,  related to Unity control center (Settings-> Appearance ->  Wallpaper)…Everything is tied up with one another. So if we choose to  use different file manager we have to change code for each of these  components. And this is not an easy task.
 Atm, I am concentrating on fixing which are broken.
 Nautilus will work even without my patch. But people who uses LIM in  Unity (& I think it’s very popular feature) won’t be too happy  because LIM simply can’t work without no-csd patch.
 But there is a discussion going in Canonical desktop team…they want  to remove all the headerbar patches from every gnome apps which is a bad  news for us.  That’s why I am starting a new thread in desktop category  how we can have best of the both world.


so it' still up in the air so I will suggest nemo too.

Regards..

---

### Post by DogMatix on 2017-11-01
I have added the Unity7 testing ppa and installled Nautilus. This is on top of one of Ventrical's Unity7 artful ISO installs that I have updated to bionic. The traditional header bar has returned and everything seems OK in a X11 session. (so far!)

[ATTACH=CONFIG]277373[/ATTACH]

---

### Post by ventrical on 2017-11-01
@dogmatix,

Thanks for that update info! :)

Regards..

---

### Post by #&amp;thj^% on 2017-11-04
> **mc4man said:**
> No longer posting in this sub-form

Same with myself >> No longer posting in this sub-form.

---

### Post by ventrical on 2017-12-11
> **mc4man said:**
> That won't be for some time, am hoping this ppa moves forward as it has numerous unity patchs that could resolve some issues

[https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo3)

Over & out..

Hi mac4man,

 I can't find the nemo ppa for bionic/18.04. Should I use  the one for artful?

---

