---
title: "[SOLVED] Can No Longer Launch Specific Profiles"
date: 2008-12-16
forum: Ubuntuzilla
---

### Post by PierreDeKat on 2008-12-16
I just upgraded my Seamonkey from 1.1.12, installed via Intrepid's repositories, to 1.1.14, installed via Ubuntuzilla.

I had been dealing with a rather [annoying and possibly dangerous bug]("https://bugs.launchpad.net/ubuntu/+source/seamonkey/+bug/290857"), and I finally decided to take the plunge into Ubuntuzilla.

The upgrade seems to have gone well, though it's still too early for me to tell if it's going to fix my bug or not.

But I have hit one tiny snag.

I have two profiles set up, and I used to be able to launch the particular profiles with:

```
seamonkey -p username1
```
and
```
seamonkey -p username2
```

But this is no longer working for me. My desktop launchers do nothing, and in terminal, I get the message:

```
run-mozilla.sh: Cannot execute /opt/seamonkey/seamonkey-bin.pure.
```

Anybody got any ideas? I'd sure like to be able to launch my profiles without having to go through profilemanager every time.

TIA

---

### Post by PierreDeKat on 2008-12-17
Okay, never mind.

I did "seamonkey --help" and found out that it's supposed to be "seamonkey -P username" -- note the capital "P". Weird. A small "p" worked just fine before, but now it wants a capital "P".

No biggie. Now I've got my launchers back. \\:D/

---

