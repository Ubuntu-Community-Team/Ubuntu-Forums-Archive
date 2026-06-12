---
title: "Sound Shuts-Off After I Plug in my Headphones"
date: 2013-10-31
forum: Ubuntu Development Version
---

### Post by OGpmpdog on 2013-10-31
Hi all,

After last night's updates, I plugged my headphones into my T-61 laptop.

I saw a new headphone indicator on the UI :P but heard no sound :P

Sound is restored after unplugging headphones but who the heyo listens to stock laptop speakers??!!:guitar:

I plugged in my headphones 1/2 way, and sound was audible.  Sound is disabled after headphones are fully plugged-in.

I'm wondering what is triggering the sound shut-off??

---

### Post by zika on 2013-10-31
> **OGpmpdog said:**
> Hi all,

After last night's updates, I plugged my headphones into my T-61 laptop.

I saw a new headphone indicator on the UI :P but heard no sound :P

Sound is restored after unplugging headphones but who the heyo listens to stock laptop speakers??!!:guitar:

I plugged in my headphones 1/2 way, and sound was audible.  Sound is disabled after headphones are fully plugged-in.

I'm wondering what is triggering the sound shut-off??
In most (if not all) those HeadPhone jacks there is a contact that is opened with that broader tip of jack... HW solution that works for ages...
[img]http://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Phone_jack_symbols.png/220px-Phone_jack_symbols.png[/img]

---

### Post by QDR06VV9 on 2013-10-31
One more sugestion would be to pull up your mixer weather it be pulseaudio or even alsamixer to be sure volume has not been muted or even turned up!

---

### Post by ventrical on 2013-11-01
> **runrickus said:**
> One more sugestion would be to pull up your mixer weather it be pulseaudio or even alsamixer to be sure volume has not been muted or even turned up!


That happened to me quite often.

---

### Post by Yellow Pasque on 2013-11-01
If Trusty has a 3.12.x kernel now, then you may have hit this issue: [https://github.com/torvalds/linux/commit/1ac3293095deb01ccc491f3c171e12722ebd0bc9](https://github.com/torvalds/linux/commit/1ac3293095deb01ccc491f3c171e12722ebd0bc9)

---

