---
title: "Thunderbird 3 won't launch"
date: 2010-02-28
forum: Ubuntuzilla
---

### Post by Aeroclub on 2010-02-28
After unsuccessfully trying to import mail from TB2 to TB3 for quite a while, I decided to try a new installation and used ubuntuzilla...
But now it won't launch, and even terminal doesn't give me any output!
Which is weird because my previous version (extracted archive from official site) launched fine...

---

### Post by chris.olive on 2010-02-28
I have the same problem worked fine this morning now nothing, have tried reinstalling with no joy if I use the lancher on the panel I get this "Failed to execute child process "/usr/share/thunderbird/defaults/pref/thunderbird-branding.js" (Permission denied)"
any ideas.

---

### Post by nanotube on 2010-02-28
> **Aeroclub said:**
> After unsuccessfully trying to import mail from TB2 to TB3 for quite a while, I decided to try a new installation and used ubuntuzilla...
But now it won't launch, and even terminal doesn't give me any output!
Which is weird because my previous version (extracted archive from official site) launched fine...

does it work with a fresh profile?

---

### Post by nanotube on 2010-02-28
> **chris.olive said:**
> I have the same problem worked fine this morning now nothing, have tried reinstalling with no joy if I use the lancher on the panel I get this "Failed to execute child process "/usr/share/thunderbird/defaults/pref/thunderbird-branding.js" (Permission denied)"
any ideas.

ubuntuzilla version doesn't store anything in /usr/share/thunderbird - so you must be running some other version of thunderbird... so i suggest you ask your question in the general support forum, not here in the ubuntuzilla section.

---

### Post by Aeroclub on 2010-03-01
> **nanotube said:**
> does it work with a fresh profile?

It doesn't launch at all, I can't even get to the profile selection...Btw, I'm running LinuxMint 7 Gloria

---

### Post by nanotube on 2010-03-01
> **Aeroclub said:**
> It doesn't launch at all, I can't even get to the profile selection...Btw, I'm running LinuxMint 7 Gloria

well, in that case i have no clue... all i can suggest is to try purging and reinstalling...

---

### Post by Aeroclub on 2010-03-01
> **nanotube said:**
> well, in that case i have no clue... all i can suggest is to try purging and reinstalling...

Already tried.
Again, extracted archive from official website did work, so the program* can* work on my system...

---

### Post by nanotube on 2010-03-01
> **Aeroclub said:**
> Already tried.
Again, extracted archive from official website did work, so the program* can* work on my system...

well, all the ubuntuzilla package 'thunderbird-mozilla-build' is, is the official archive extracted into /opt, plus a symlink to /usr/bin, a menu shortcut, and an icon. so i'm entirely at a loss as to why a manually-extracted tar.gz works for you but ubuntuzilla's install does not.

---

