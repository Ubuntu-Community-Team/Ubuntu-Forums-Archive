---
title: "TWiki on Ubuntu 9.04 Server (Universe repo)"
date: 2009-08-19
forum: Server Platforms
---

### Post by ugm6hr on 2009-08-19
Has anyone got experience of installing TWiki from the Universe repo using apt?

I am currently experimenting with it for storing private data on a LAN.

Unfortunately, it appears Ubuntu uses a non-standard install, so files and permissions recommendations given in the twiki wiki do not work properly.

Specifically, I want to install additional plugins, but following the advice re: chown for www-data (apache user) at /var/lib/twiki doesn't appear to allow it to install.  My problem is similar to here: [http://twiki.org/cgi-bin/view/Support/SID-00005](http://twiki.org/cgi-bin/view/Support/SID-00005)

I have some other questions, but can use google to work out how TWiki works with regard to forms, templates etc, but there doen't appear to be much oout there that explains this.

---

### Post by ugm6hr on 2009-08-20
Anyone here have experience with this?

I'm also looking for help with:

1. Recreating a similar page to the registration page, which automatically creates a new page using data entered in a form.

2. Changing the way that form-filled data is displayed (i.e modifying templates).

3.  Editing the copyright notice in the footer and adding a header to print-view.

---

### Post by ugm6hr on 2009-08-22
Looks like I am just bumping my own thread...  Never mind.

In any case, another thread pointed me to foswiki, which is a recent fork of TWiki, but community lead, and has identical features.

It has a Debian / Ubuntu repository which contains the latest version and appears to work as expected.  The only difference between a manual and repository installation is that plugins must be added using apt rather than the config page, but that is no problem at all.  They are then simply enabled from the config page.

I have also found the Foswiki community as helpful as here, so will be supporting it.

As for my other problems:

1. Did this using the FormPlugin following a very quick and thorough answer from the Support page.

2. Haven't worked this out yet...  Modifying the appearance of the wiki appears to be more complex than I had hoped.

3. The System.WebBottomBar page can be copied from WebBottomBarExample and edited as necessary.  Same goes for the WebLeftBar, if you want to include your own default shortcuts for all users.

Will likely give a complete How-to for my new creation on Foswiki in due course, if they are interested.

---

