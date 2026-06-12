---
title: "woot finally finished setting her up"
date: 2009-01-31
forum: The Cafe
---

### Post by ugkbunb on 2009-01-31
After a few attempts that ended in borked partitions I finally got my 8.10 xubuntu box setup.

Running:
2.6.28-6 kernel + updated grub
180.27 nvidia drivers
1.0.19 alsa driver + pulseaudio
2009.1.1 ntfs-3g driver
svn of gParted w/ ext4 support
converted all my partitions to ext4

Only issue and it was a minor one... the default ubuntu version of firefox kept randomly crashing... tried numerous things to fix it including deleting all traces of nspluginwrapper/flashplugin and reinstalling the x64 alpha Flash using the instructions... the crashes would exit terminal with a mere "Aborted" message and since the crash reporter is disabled in firefox ubuntu version it was diff to diagnosis the problem. Ended up just installing ubuntuzilla and back to rock solid browsing... downside is I am back to 32-bit browser although I cant humanly tell a difference.

I noticed that e4defrag is not in the kernel... is it planned to be merged in before Jaunty release?

[img]http://i27.photobucket.com/albums/c174/grekens/fin.png[/img]

---

### Post by NTolerance on 2009-01-31
Why so much bleeding edge software?

---

### Post by Dr Small on 2009-01-31
> **NTolerance said:**
> Why so much bleeding edge software?
What's wrong with bleeding edge software?

---

### Post by Sand &amp; Mercury on 2009-01-31
> **Dr Small said:**
> What's wrong with bleeding edge software?
It keeps bleeding!

---

### Post by ugkbunb on 2009-01-31
> **NTolerance said:**
> Why so much bleeding edge software?

I enjoy testing out new software... and if it breaks... it nothing a format and untar won't fix.

The alsa driver had numerous fixes to my mobo's soundcard.
The ntfs driver also had numerous fixes relating to files with diff languanges... this was affecting my ability to access my bros anime folder.
The kernel is needed for ext4 and was interested in testing it out : )

---

### Post by NTolerance on 2009-01-31
> **Dr Small said:**
> What's wrong with bleeding edge software?

Nothing wrong with that.  I was just curious.  ;)

I deal with alpha software during the day, so at night the craziest I get is with intrepid-proposed.

---

### Post by Nepherte on 2009-01-31
It looks like you installed the wrong distribution. As you noticed you have to install every new version yourself because ubuntu "freezes" it updates, only when it's a security issue they include it. A rolling release distribution would keep up with newer versions.

---

### Post by ugkbunb on 2009-01-31
> **Nepherte said:**
> It looks like you installed the wrong distribution. As you noticed you have to install every new version yourself because ubuntu "freezes" it updates, only when it's a security issue they include it. A rolling release distribution would keep up with newer versions.

I don't update everythin to alpha software... just a few things that catch my eye or are applicable to my situation. I enjoy the community of these forums + the ease of debian based distro.

---

