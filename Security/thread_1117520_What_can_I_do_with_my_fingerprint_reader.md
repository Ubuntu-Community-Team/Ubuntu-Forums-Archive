---
title: "What can I do with my fingerprint reader?"
date: 2009-04-06
forum: Security
---

### Post by diablo75 on 2009-04-06
I just bought an HP 6715b off of ebay which has a fingerprint scanner built into it.  I was wondering what the latest news is on software for Ubuntu that can make use of this reader and what kind of cool things I can do with it.  The thought of swiping my finger instead of typing my admin password every time I do an update or play with apt-get in the terminal just sounds freaking snazzy and convenient.  But is that still a fantasy?

---

### Post by diablo75 on 2009-04-07
Bump....

---

### Post by ubuntu27 on 2009-04-07
I don't have fingerprint reader but, looking at the new GNOME 2.26 (Which Ubuntu Jaunty uses) Release Notes it says:

"**Fingerprint Reader Integration**

GNOME 2.26 now integrates with the fprintd fingerprint service to allow users to enroll fingerprints for use in authentication.

If a system is configurated for allowing fingerprint authentication, users can enroll their fingerprints via Desktop &#9656; Preferences &#9656; About Me from the panel menu."

Here is the link to GNOME 2.26 Release NOtes:

[http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/)

---

### Post by diablo75 on 2009-04-07
AWESOME!  I love you.

---

### Post by ubuntu27 on 2009-04-07
> **diablo75 said:**
> AWESOME!  I love you.

^^You are welcome.

So, did you try it? Are you using Jaunty Beta?

---

### Post by diablo75 on 2009-04-07
Not yet.  I don't expect the laptop to arrive for about a week but I will give the beta a shot once it gets here and report back to this thread with results.

---

### Post by forevertheuni on 2009-04-11
Didn't work out of the box for me.
the fingerprint device works, only as root for now.

---

### Post by bigbrovar on 2009-04-12
> **ubuntu27 said:**
> I don't have fingerprint reader but, looking at the new GNOME 2.26 (Which Ubuntu Jaunty uses) Release Notes it says:

"**Fingerprint Reader Integration**

GNOME 2.26 now integrates with the fprintd fingerprint service to allow users to enroll fingerprints for use in authentication.

If a system is configurated for allowing fingerprint authentication, users can enroll their fingerprints via Desktop &#9656; Preferences &#9656; About Me from the panel menu."

Here is the link to GNOME 2.26 Release NOtes:

[http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/)

I dont think ubuntu implemented that part of gnome in jaunty. up till now i fingerprint reader is broken in jaunty.same thing that worked out of the box from a livecd in fedora 11 beta.

---

### Post by diablo75 on 2009-04-12
Crap, does that mean I'll have to wait for 9.10 before it'll show up as a built in feature?

---

### Post by bigbrovar on 2009-04-13
> **diablo75 said:**
> Crap, does that mean I'll have to wait for 9.10 before it'll show up as a built in feature?

personally am not sure why the feature was not implemented in jaunty. since its was a part of gnome my guess would be that it was stripped out. however it was implemented and works out of the box on fedora 11 beta

---

### Post by mudguts on 2009-04-13
I have a fingerprint reader in my IBM T60.   I wish that it was just a big bigger so I could use as a tongue reader...

anyway..  build it and they will come.

---

### Post by diablo75 on 2009-04-21
Well I finally got my laptop today and got Jaunty RC installed.  As suspected, the necessary software to use the fingerprint scanner is not installed by default.  I followed [this guide]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#fingerprint") to get it working.  Condensed, here's what I did:

```
sudo apt-get update && sudo apt-get install aes2501-wy fprint-demo libfprint0 libpam-fprint
```

Then:

```
gksudo gedit /etc/pam.d/common-auth
```

I then appended the following text to the very bottom of the common-auth file:

```
auth sufficient pam_fprint.so
```

Finally I ran this in terminal:

```
fprint_demo
```

(That is an underscore, the guide is incorrect in saying the command is fprint-demo).

Once this is loaded, you can enroll your finger prints, and then close.

Bugs I noticed:  Login requires you to type your password and then swipe your finger, but there is no prompt telling you to swipe your finger.  It will sit and wait until you do.  This is common for many different prompts that ask for your password.  Sometimes (not always) you have to swipe while not being prompted to.  I was also under the impression that using the clause "auth sufficient pam_fprint.so" instead of "auth required pam_fprint.so" would allow me to forego typing my password at all points and allow me to just simply swipe my finger....

Anyway, it appears to be working great otherwise.  I was pretty impressed with the fprint_demo program.

---

### Post by Melk79 on 2009-05-12
Yeah, this worked.  Unfortunately, like diablo75 said, the sufficient line doesn't work as intended and you have to swipe your finger and then enter a password.  I'm not concerned about the security risk with biometrics for this computer, I just wanted the convenience.  This worked fine under Hardy and Intrepid; although you still didn't get any prompts to swipe except when using the terminal.

---

