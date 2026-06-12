---
title: "Can't get flash to work"
date: 2010-10-29
forum: Wine
---

### Post by benlyboy on 2010-10-29
hi all 

I'm setting up a new system, to replace my older ubuntu 8.4 system that has served me well.

The new system has ubuntu 10.10. and as I use it a lot on my old system, I wanted  wine with firefox on the new system. So I installed wine then downloaded firefox 3.6.12 and all seemed great until I went to youtube.com. This is where I ran into problems. The browser told me I needed a plugin, so I push the button and it seemed to install flash ok.

But if I try to go to a page with flash content the page hangs for a few seconds, then it loses focus and the whole browser grays out.

I have tried uninstalling and reinstalling both fire fox and the plug in but nothing works. flash works just fine on my old system, so not really sure what is going on.

any ideas....please:confused:

---

### Post by lovinglinux on 2010-10-29
Why are you using Firefox for Windows, when you can use the native Firefox with flash support?

---

### Post by benlyboy on 2010-10-29
I play with web page design and the editor I like to use is a windows editor and needs a browser

---

### Post by lovinglinux on 2010-10-29
> **benlyboy said:**
> I play with web page design and the editor I like to use is a windows editor and needs a browser

Well, you could use the Windows version for developing and the native version for testing.

I will try to find a solution anyway. give me a couple of minutes to test on a VM.

---

### Post by benlyboy on 2010-10-29
thanks any help would be great

---

### Post by lovinglinux on 2010-10-29
It doesn't work. I get the same results as you. Browser simply freezes.

Please post a link to the application you want that requires Firefox for Windows. I will try to work on that or find a better native option.

---

### Post by benlyboy on 2010-10-29
mmm seems funny that it works ok on my 8,04....

---

### Post by lovinglinux on 2010-10-29
> **benlyboy said:**
> mmm seems funny that it works ok on my 8,04....

Because Ubuntu 8.04 uses flash 9.

---

### Post by benlyboy on 2010-11-08
> Because Ubuntu 8.04 uses flash 9. 

No it doesn't, well at least on my system it has 10.1

---

### Post by lovinglinux on 2010-11-08
> **benlyboy said:**
> No it doesn't, well at least on my system it has 10.1

This is what it says:

> 10.0.1.218+**really9.0.289**.0ubuntu1

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=flashplugin-nonfree](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=flashplugin-nonfree)

---

### Post by _outlawed_ on 2010-11-08
> **lovinglinux said:**
> This is what it says:



[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=flashplugin-nonfree](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=flashplugin-nonfree)

10.0.1.218 is the version of flash player (beta version).

---

### Post by lovinglinux on 2010-11-08
> **_outlawed_ said:**
> 10.0.1.218 is the version of flash player (beta version).

It is marked as 10.0.1.218 in the package manager, but it includes "really9.0.289" in the package name:

> 10.0.1.218+**really9.0.289**.0ubuntu1

That means the flash version is in fact 9.0.289.

If you type about[noparse]:[/noparse]plugins in the browser address bar you will see that it is identified by the browser and by web sites as:

```
Shockwave Flash 9.0 r289
```

So, is flash 9.

---

### Post by thatguruguy on 2010-11-08
Why not set up a windows installation in Virtual Box or VMWare?

---

