---
title: "Ubuntulite 0.8 RC2 is out."
date: 2008-08-29
forum: The Cafe
---

### Post by kagashe on 2008-08-29
[Ubuntulite]("http://ubuntulite.tuxfamily.org/") 0.8 is based on Hardy with LXDE desktop. RC2 is a live CD.
[Download link]("http://download.tuxfamily.org/ubuntulite/ubuntulite_0.8_beta2.iso").

There is a [review on DeviceGuru]("http://www.deviceguru.com/2008/08/26/getting-to-know-ubuntu-lite/").

kagashe

---

### Post by Warpnow on 2008-08-29
That website needs some work.

The drop down menus color scheme make them unreadable.

The screenshots are to dead links.

---

### Post by billgoldberg on 2008-08-29
For being called Ubuntulite, it isn't that lightweight at all.

---

### Post by Johnsie on 2008-08-29
just how lite is it? I'm looking for something for my eeepc that uses minimal disk space. So far puppylinux has been the best for disk space.

---

### Post by shae on 2008-08-29
I must say I am sorry about the state of the menus and screenshots at the moment.  The entire site is being reworked, but I felt that it should remain open while I complete that process.  My hope is that I will have the menu up and running properly by the end of this weekend and hopefully I can find the time to redo the screenshots too after that.

As to how light it is:  After booting up it uses around 60mb of ram 1.2gb of HD space (I currently am getting 57mb used on my testing install).

---

### Post by andrewabc on 2008-08-29
Thread title and website says RC2, but download link provided is
[http://download.tuxfamily.org/ubuntulite/ubuntulite_0.8_beta2.iso](http://download.tuxfamily.org/ubuntulite/ubuntulite_0.8_beta2.iso)
beta 2.
Maybe keep to naming stuff correctly? :P

EDIT:
Hope the live cd works in virtualbox.

---

### Post by barbedsaber on 2008-08-29
In comparison with xubi, how lite is it?

---

### Post by picpak on 2008-08-29
> **barbedsaber said:**
> In comparison with xubi, how lite is it?

Lighter than Xubi. Not as light as Puppy.

---

### Post by andrewabc on 2008-08-30
Successfully got livecd running in virtualbox. Installed it in virtualbox ok.
Thankfully there is the livecd now. I never wanted to deal with running a script. Made it impossible to test without installing.

Upon starting a fresh install "top" says it is using 157mb of ram. I'm not sure how shae is getting 60mb ram.

So far it looks good.

---

### Post by kagashe on 2008-08-30
> **andrewabc said:**
> Successfully got livecd running in virtualbox. Installed it in virtualbox ok.
Thankfully there is the livecd now. I never wanted to deal with running a script. Made it impossible to test without installing.

Upon starting a fresh install "top" says it is using 157mb of ram. I'm not sure how shae is getting 60mb ram.

So far it looks good.shae does not mean that "top" says 60 MB. No ubuntu based distribution could show 60 MB by "top". Please see what free -m says for -/+ buffers/-cache.

If you want to see that kind of memory in "top" allocate only 64 MB in the virtualbox and see whether you can boot. I think it will.

kagashe

---

### Post by boomtisk on 2008-08-30
Hmmm, I downloaded and burned the Live CD but it doesn't boot for me, I get the following error:

[  815.350015] crc error
[  815.353998] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (8,3)


Could it be that my download got corrupted? Is there a torrent of the .iso?
I tried to install Ubuntulite on an old ThinkPad X600, by the way.

Also, I'm 100% sure my hard drive was unmounted cleanly.

---

### Post by andrewabc on 2008-09-01
> **kagashe said:**
> shae does not mean that "top" says 60 MB. No ubuntu based distribution could show 60 MB by "top". Please see what free -m says for -/+ buffers/-cache.

If you want to see that kind of memory in "top" allocate only 64 MB in the virtualbox and see whether you can boot. I think it will.

kagashe

I understand now. I installed conky to show memory and it is now showing 48 mb upon starting. That is good.

---

### Post by cogitordi on 2008-09-07
I tested both Xubuntu and UbuntuLite on a Thinkpad 380z (Pentium II 300 MHz, 162 MB RAM) this weekend. UbuntuLite is notably lighter than Xubuntu, says Conky.

---

### Post by cogitordi on 2008-09-07
Crunchbang is lighter than Ubuntulite on my ancient notebook. I like the look of Crunchbang more, but something that surprised me is how well OPENOFFICE (caps intentional) runs. Crunchbang forces OpenOffice to use GTK.

I am running Crunchbang with three virtual desktops, Conky, a terminal, Firefox, and OpenOffice Writer running. RAM usage is at about 90 MB of my 162 MB RAM. The notebook has a Pentium II 300 MHz CPU running at 38% with all these programmes and five Firefox tabs open.

It's clear to me that Openbox is the way to go. After a weekend of trying difference "light" Linux distributions, I have to recommend Crunchbang.

---

### Post by boomtisk on 2008-09-16
Awesome, I'm gonna give it a try as Ubuntulite still isn't working for me.

---

### Post by Stan_1936 on 2008-09-16
1.  Have you tried burning the CD at the "Slowest Speed"?
2.  Have you tried doing an Ubuntu mini-CD install and adding Openbox as WM yourself?  Whether or not this works might give you some clue as to what is causing UbuntuLite to give you problems.
3.  There is an UbuntuLite Installation Help Forum here:  [http://ubuntulite.tuxfamily.org/?q=forum/4](http://ubuntulite.tuxfamily.org/?q=forum/4)


Also, I think we need some screenshots for UbuntuLite.  The official website doesn't have any that are working.

---

### Post by Stan_1936 on 2008-09-16
> **cogitordi said:**
> Crunchbang is lighter than Ubuntulite on my ancient notebook......

Haev you got any numbers?  Direct comparison of Conky stats for each of the distros?

---

### Post by cogitordi on 2008-09-17
> **Stan_1936 said:**
> Haev you got any numbers?  Direct comparison of Conky stats for each of the distros?

Hello Stan, I don't have a screen shot for you, but OpenBox and the Crunchbang theme were 5-10 MB RAM lighter on this old hardware than any decent looking Metacity+Gnome theme. 

I've created my own "Thinbuntu" installation on a CLI base. I managed to find and mix a pair of lightweight Gnome themes. Firefox and Xorg are pigs at the trough together, but not using Firefox extensions, using a light Gnome theme, and switching off Firefox's phishing verification (which runs fsync) has made a noticeable difference in performance.

---

### Post by cogitordi on 2008-09-18
If you can live with Epiphany instead of Firefox, conky tells me that you can save about 20 MB RAM.

---

### Post by cogitordi on 2008-09-20
It helps the performance of Firefox (speed and RAM usage) if you install the NoScript extension. 

In fact, the NoScript extension is part of secure Internet usage today and should be part of the Firefox distribution.

---

### Post by Stan_1936 on 2008-09-20
you got a link to instructions on installing that extension?

---

### Post by cardinals_fan on 2008-09-20
> **Stan_1936 said:**
> you got a link to instructions on installing that extension?
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by cogitordi on 2008-09-20
Or, in Firefox:
click >Tools >Add-ons
click >Get Add-ons
type "NoScript" in the search field
click Add to Firefox

---

### Post by motang on 2008-09-21
Downloading it now, and will try it out in Virtualbox, not sure if I will install it on one of my machines but I am a bit curious as how LXDE works.  Got Xubuntu working beautifully with compiz and awn on my eee box so I am pretty happy right now. :)

---

### Post by FrankVdb on 2008-09-22
> **Johnsie said:**
> just how lite is it? I'm looking for something for my eeepc that uses minimal disk space. So far puppylinux has been the best for disk space.

There is a dedicated Ubuntu eee distro:
[http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)

---

### Post by FrankVdb on 2008-09-22
> **Johnsie said:**
> just how lite is it? I'm looking for something for my eeepc that uses minimal disk space. So far puppylinux has been the best for disk space.

There is a dedicated Ubuntu eee distro:
[http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)

---

### Post by Stan_1936 on 2008-09-23
The website has been updated.  Still no screenshots though...

---

### Post by cardinals_fan on 2008-09-23
> **Stan_1936 said:**
> The website has been updated.  Still no screenshots though...
[http://www.thecodingstudio.com/opensource/linux/screenshots/?linux_distribution_sm=Ubuntulite%200.8%20RC2](http://www.thecodingstudio.com/opensource/linux/screenshots/?linux_distribution_sm=Ubuntulite%200.8%20RC2)

---

