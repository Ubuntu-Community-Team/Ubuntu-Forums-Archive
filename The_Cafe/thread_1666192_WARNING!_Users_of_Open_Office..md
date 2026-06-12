---
title: "WARNING! Users of Open Office."
date: 2011-01-13
forum: The Cafe
---

### Post by neu5eeCh on 2011-01-13
[LEFT]My last Ubuntu update shoved Libre Office down my throat.

It *appears* that Canonical will replace your OO install with LibreOffice. At least, that's what happened on my system.

Setting aside the virtue or value of Libre Office, this isn't the way to do it. I can no longer access my WordPerfect documents using LibreOffice. I **didn't** and **don't** **want** Libre Office. _Yet_.

If you are using OO and want to **keep** using it, do **not** install any further OO or Libre updates.

At present, I have been unable to install OO from OpenOffice.Org because of missing depencies. And trying to install OO from the repositories appears to redirect to Libre but Libre won't install (even if I wanted it) because of missing dependencies.
[/LEFT]

---

### Post by Spice Weasel on 2011-01-13
WordPerfect still exists?

---

### Post by samalex on 2011-01-13
> **VTPoet said:**
> [LEFT]My last Ubuntu update shoved Libre Office down my throat.

What version of Ubuntu are you running?  I'm still on 10.04 so just curious.

---

### Post by undecim on 2011-01-13
Isn't LibreOffice just a rebranded OpenOffice?

What's wrong with switching to it? It should still work just the same.

Also, I'm on 10.10 and still have OOo. Are you running the development version?

---

### Post by NightwishFan on 2011-01-13
I think you are mixing things up a bit due to a common misconception. As far as I know Ubuntu has never shipped OpenOffice.org. It has actually shipped a program known as: Go-oo [http://en.wikipedia.org/wiki/Go-oo](http://en.wikipedia.org/wiki/Go-oo)

Libre Office I believe is based on Go-oo already so the user experience should not be much different.
[QUOTE="Wikipedia"]by late December of 2010 the Go-oo patches were incorporated into release candidate 1 of the LibreOffice fork of OpenOffice.[/QUOTE]

If you want standard OpenOffice.org, that is of course, your decision, and not a bad one or anything. It should certainly be possible to install it, and I am sure someone can help you with that.

---

### Post by neu5eeCh on 2011-01-13
> **Spice Weasel said:**
> WordPerfect still exists?

I know... I know... But I still need to access all those #$%& files.

---

### Post by neu5eeCh on 2011-01-13
> **undecim said:**
> Isn't LibreOffice just a rebranded OpenOffice?

Yes, at least that's what I **thought**. However, in order to run Libre Office, one has to uninstall OpenOffice. The additional extension which allowed me to open WP documents with OO were, at the time, unavailable in Libre.


> **undecim said:**
> What's wrong with switching to it? It should still work just the same.

Also, I'm on 10.10 and still have OOo. Are you running the development version?

As I say, I can't open WP documents with Libre. And no, I wasn't running a development version.

---

### Post by Evil-Ernie on 2011-01-13
> **Spice Weasel said:**
> WordPerfect still exists?
 
Yep! Owned by Corel I know its still used by some academics here at the NHS.

---

### Post by undecim on 2011-01-13
> **VTPoet said:**
> And no, I wasn't running a development version.

Then what version of Ubuntu are you running?

I'm trying to figure out how you got upgraded to Libre when I didn't.

---

### Post by NCLI on 2011-01-13
> **VTPoet said:**
> Yes, at least that's what I **thought**. However, in order to run Libre Office, one has to uninstall OpenOffice. The additional extension which allowed me to open WP documents with OO were, at the time, unavailable in Libre.




As I say, I can't open WP documents with Libre. And no, I wasn't running a development version.

Did you add the LibreOffice PPA? I'm using Natty, and OpenOffice is still installed.

---

### Post by ki4jgt on 2011-01-13
> **undecim said:**
> Then what version of Ubuntu are you running?

I'm trying to figure out how you got upgraded to Libre when I didn't.

I'm running 10.10 and I got LO placed on my system and OO was removed. Of course, I had to uninstall, then sudo aptitude install libreoffice and then install gtk and gnome. b/c the buttons wouldn't work.

---

### Post by forrestcupp on 2011-01-13
It's not their fault.  Ubuntu always shipped with Go-oo, which is Novell's fork of OpenOffice.org.  Go-oo merged with Libre Office.  So how it that Ubuntu's fault?

---

### Post by ki4jgt on 2011-01-13
> **forrestcupp said:**
> It's not their fault.  Ubuntu always shipped with Go-oo, which is Novell's fork of OpenOffice.org.  Go-oo merged with Libre Office.  So how it that Ubuntu's fault?

I'm blaming no one, but this sort of does throw a fork into the whole staying on the same program version until the next release thing.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

> For example, if Ubuntu ships with OpenOffice.org 2.0.x, it will remain at OpenOffice.org 2.0.x for the entire 6-month release cycle, even if a later version gets released during this time.

---

### Post by neu5eeCh on 2011-01-13
> **forrestcupp said:**
> It's not their fault.  Ubuntu always shipped with Go-OO, which is Novell's fork of OpenOffice.org.  Go-OO merged with Libre Office.  So how it that Ubuntu's fault?

I pegged Canonical because it was their last update that wrecked my install of OO (or Go-OO).

As it turns out, I had tried Libre RC1, then uninstalled it because, at the time, I wasn't able to open my old WP docs. I didn't remove the PPA's because I thought I'd try it again at some later date. This **may** have caused some of the problem, but I don't know.

---

### Post by uRock on 2011-01-13
> **VTPoet said:**
> I pegged Canonical because it was their last update that wrecked my install of OO (or Go-OO).

As it turns out, I had tried Libre RC1, then uninstalled it because, at the time, I wasn't able to open my old WP docs. I didn't remove the PPA's because I thought I'd try it again at some later date. This **may** have caused some of the problem, but I don't know.
That has to be the cause. I have two 10.10 machines that are always kept up to date and neither has had any issues with Ubuntu's version of OpenOffice.

---

### Post by NightwishFan on 2011-01-13
Yeah it would only switch on a development version. Ubuntu would not suddenly switch from openoffice to libreoffice, especially in the main repository, which has Canonical support.

---

### Post by cariboo on 2011-01-13
Having the ppa enabled is why LibreOffice overwrote OOo. LibreOffice is supposed to be in the Natty repositories during alpha 2.

Anytime you have ppas enabled the version in the ppa will overwrite the current version you have. The easiest way to remove a program installed from a ppa is to use ppa-purge, the command would look like this for LibreOffice:

```
sudo ppa-purge ppa:libreoffice/ppa
```

the above command will also remove the ppa from your sources list.

---

### Post by ki4jgt on 2011-01-13
> **NightwishFan said:**
> Yeah it would only switch on a development version. Ubuntu would not suddenly switch from openoffice to libreoffice, especially in the main repository, which has Canonical support.

I didn't install the LO PPA :confused:

---

### Post by NightwishFan on 2011-01-13
[LIST]
[*]Maverick OO.org: [http://packages.ubuntu.com/maverick/openoffice.org-writer](http://packages.ubuntu.com/maverick/openoffice.org-writer)
[*]Natty OO.org: [http://packages.ubuntu.com/natty/openoffice.org-writer](http://packages.ubuntu.com/natty/openoffice.org-writer)
[*]Libreoffice (all releases - no results): [http://packages.ubuntu.com/search?keywords=libreoffice-writer&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libreoffice-writer&searchon=names&suite=all&section=all)
[/LIST]

You had to have added a 3rd party source, as no libreoffice packages show up at all.

---

### Post by ki4jgt on 2011-01-13
The source "PPA" has showed up in my sources, but I didn't add it. (Unless I was sleep walking)

---

### Post by NightwishFan on 2011-01-13
> **ki4jgt said:**
> The source "PPA" has showed up in my sources, but I didn't add it. (Unless I was sleep walking)

Nope, you have to add it manually with a copy paste and add the keyring or a "sudo apt-add-repository nameofppa" command. Otherwise the only app I know of that adds ppa is Ubuntu Tweak.

---

### Post by Chronon on 2011-01-13
Well, they don't add themselves.  ;)

---

### Post by ki4jgt on 2011-01-13
The only ppas I remember adding are FBreader, Mozilla, kdenlive, GetDeb, (Google was added with their browser app), Medibuntu, and Opera. Unless I accidently copied it in some commands I picked up from the web, I can't think of any reason I'd have it.

---

### Post by Tibuda on 2011-01-13
> **NightwishFan said:**
> Nope, you have to add it manually with a copy paste and add the keyring or a "sudo apt-add-repository nameofppa" command. Otherwise the only app I know of that adds ppa is Ubuntu Tweak.

Google Chrome and Opera also adds their apt repositories when you install the downloaded .deb file.

---

