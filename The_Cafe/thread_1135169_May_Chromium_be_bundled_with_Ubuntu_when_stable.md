---
title: "May Chromium be bundled with Ubuntu when stable?"
date: 2009-04-24
forum: The Cafe
---

### Post by cl333r on 2009-04-24
Hi folks,
I'm wondering if the bunch of licenses that Chromium uses are compatible enough with Ubuntu for it to be bundled into the official .iso images of the Ubuntu releases after Chromium gets stable.

Its licenses:
[http://code.google.com/chromium/terms.html](http://code.google.com/chromium/terms.html)

Background info: Chromium is shaping up fast, the difference in JavaScript speed compared to its windows port is only about 5% which makes me think Google cares more about Linux than Mozilla since Firefox on Linux is about 40% slower than its windows port.
Chromium is also from 40% to 4000% faster than Firefox depending on what you're benchmarking, it passes (almost) 100% the acid 3 test + other features, and (unlike Firefox) it has a fast cold startup. These and other features imo make Chromium a strong browser candidate to be included into the default Ubuntu build after Chromium gets stable.

---

### Post by t0p on 2009-04-24
Is Chromium actually Free/open?  I haven't checked it out myself, as I don't run Windows, but the stuff I've read on the internet about the agreement users must sign has led me to believe that it is free as in beer but not Free as in speech.

---

### Post by cb951303 on 2009-04-24
> **t0p said:**
> Is Chromium actually Free/open?  I haven't checked it out myself, as I don't run Windows, but the stuff I've read on the internet about the agreement users must sign has led me to believe that it is free as in beer but not Free as in speech.

if you download the google exe you have to agree to some license but the code is licensed under BSD so there are no problems to bundle it with any distro but I highly doubt any distro will choose it over firefox. firefox's addon capability is unbeatable and people care about it. Also, chrome's look doesn't suit to gnome.

---

### Post by .Maleficus. on 2009-04-24
I'd say that Epiphany would probably be bundled first, since it is a Gnome project and with the Epiphany Addons package retains Firefox's addon compatibility (or so I read).  I have yet to try it myself since it would require me to install Gnome, but it seems like a pretty nice piece of software (if unstable currently).

---

### Post by Tristam Green on 2009-04-24
> **cb951303 said:**
> if you download the google exe you have to agree to some license but the code is licensed under BSD so there are no problems to bundle it with any distro but I highly doubt any distro will choose it over firefox. firefox's addon capability is unbeatable and people care about it. Also, chrome's look doesn't suit to gnome.

The google executable is for Chrome;  Chromium is a different 100% open-source entity.

---

### Post by Mehall on 2009-04-24
> **cb951303 said:**
> if you download the google exe you have to agree to some license but the code is licensed under BSD so there are no problems to bundle it with any distro but I highly doubt any distro will choose it over firefox. firefox's addon capability is unbeatable and people care about it. Also, chrome's look doesn't suit to gnome.

Actually, iirc I read somewhere it was made with gtk and qt operability if needed. It would take some coding, but it could be made to fit in Gnome/KDE about as well as it does in Windows.

---

### Post by Sand &amp; Mercury on 2009-04-24
> **Mehall said:**
> Actually, iirc I read somewhere it was made with gtk and qt operability if needed. It would take some coding, but it could be made to fit in Gnome/KDE about as well as it does in Windows.
It will be done with GTK+, so it'll integrate fine in GNOME. Better than Firefox, even.

---

### Post by Giant Speck on 2009-04-24
> **Sand & Mercury said:**
> It will be done with GTK+, so it'll integrate fine in GNOME. Better than Firefox, even.

I really can't wait for that.

---

### Post by cl333r on 2009-04-24
I'm asking cause I'm using Chromium 2.0.175 from PPA, it's real, no wine stuff and it runs natively using Gtk (it's in pre alpha though):
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

details here:
[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/)

But I really don't know what the Ubuntu devs think about its licenses, as you can see from the link from the/my 1st post, it uses quite a lot of licenses.

---

### Post by zekopeko on 2009-04-24
> **cl333r said:**
> 

But I really don't know what the Ubuntu devs think about its licenses, as you can see from the link from the/my 1st post, it uses quite a lot of licenses.

so does firefox and a lot of software that's in ubuntu. it's very hard to find a large project that's only under a single license.

---

### Post by Hells_Dark on 2009-04-24
> **cl333r said:**
> I'm asking cause I'm using Chromium 2.0.175 from PPA, it's real, no wine stuff and it runs natively using Gtk (it's in pre alpha though):
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

details here:
[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/)

But I really don't know what the Ubuntu devs think about its licenses, as you can see from the link from the/my 1st post, it uses quite a lot of licenses.

It's absolutely not integrated.

(but works well)

---

### Post by cb951303 on 2009-04-24
> **Sand & Mercury said:**
> It will be done with GTK+, so it'll integrate fine in GNOME. Better than Firefox, even.

see the development shell, even though it's mde with GTK, it's actual skin and custom widgets definitely doesn't integrate well. Worst than firefox I'd say.

---

### Post by billgoldberg on 2009-04-24
> **cl333r said:**
> Hi folks,
I'm wondering if the bunch of licenses that Chromium uses are compatible enough with Ubuntu for it to be bundled into the official .iso images of the Ubuntu releases after Chromium gets stable.

Its licenses:
[http://code.google.com/chromium/terms.html](http://code.google.com/chromium/terms.html)

Background info: Chromium is shaping up fast, the difference in JavaScript speed compared to its windows port is only about 5% which makes me think Google cares more about Linux than Mozilla since Firefox on Linux is about 40% slower than its windows port.
Chromium is also from 40% to 4000% faster than Firefox depending on what you're benchmarking, it passes (almost) 100% the acid 3 test + other features, and (unlike Firefox) it has a fast cold startup. These and other features imo make Chromium a strong browser candidate to be included into the default Ubuntu build after Chromium gets stable.

It doesn't matter as it will never happen.

At least not as long as firefox is around.

---

### Post by Giant Speck on 2009-04-24
> **cb951303 said:**
> see the development shell, even though it's mde with GTK, it's actual skin and custom widgets definitely doesn't integrate well. Worst than firefox I'd say.

That's why the post you quoted was written in the future tense.

---

### Post by cb951303 on 2009-04-24
> **Giant Speck said:**
> That's why the post you quoted was written in the future tense.

no, the current linux client is made with GTK (see the PPA) and it doesn't integrate at all.

---

### Post by racoq on 2009-04-24
> **cb951303 said:**
> no, the current linux client is made with GTK (see the PPA) and it doesn't integrate at all.

No one in the Ubuntu dev team, in its perfect sanity would replace Firefox (a full feature browser), with Chrome (a Crippled  browser, wich is just catching up in terms of features)

Also, as it was said here, the look and feel of google chrome totally sucks.

---

### Post by Polygon on 2009-04-24
even if chrome uses gtk, its still a very new browser without a lot of features. I think its better to stay with firefox, and then if people want to use chrome, they can always install it.

firefox better appeals to the majority of linux users.

---

### Post by artir on 2009-04-24
In the long run, i think we'll have epiphany as a default.

---

### Post by Orlsend on 2009-04-24
They would have beat Friefox first, It looks like something really hard. (Since most of the Major distros Use firefox.

---

