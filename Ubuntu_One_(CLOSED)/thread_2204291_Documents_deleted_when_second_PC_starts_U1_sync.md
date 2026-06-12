---
title: "Documents deleted when second PC starts U1 sync"
date: 2014-02-07
forum: Ubuntu One (CLOSED)
---

### Post by Vladlenin5000 on 2014-02-07
Preamble: The problem reported below didn't happen to me but to a friend. My 50GB U1 is working as designed in several Ubuntu (and flavors) desktops/notebooks, an Android phone and in an Android miniPC (HDMI "dongle"). In all of them (except mobile apps, of course) the sync occurs smoothly as it should and I never had any issue in retrieving my cloud contents even after the several fresh installations of the OS on the machines.
The problem my friend is having is weird and probably eligible for a case study :p (and maybe I shouldn't be using this smiley because it wasn't funny at all for him). I had to see it to believe. Here's the sequence of events just in case it's relevant:



1. Ubuntu One (U1) was firstly installed in a **Lubuntu** (12.04 or 12.10, can't remember) notebook and the initial account setup was done a few years ago. He was still using Windows in the desktop at the time and didn't bothered to install the Windows client in the machine where is personal files were so, for quite some time he didn't actually "used" the U1. This notebook, however, is rarely used.

2. Last year he decided to have Ubuntu only and asked me to backup everything from the Windows machine, install **Ubuntu 12.04** instead and recover the backup into it. Having done that he then proceeded to setup his U1 account. We gave it time to upload everything (less than 1GB), confirmed it was there in web page so at this point everything was fine. He has been using Ubuntu (and U1) daily since then without any issue (i suppose, otherwise he'd tell me).

3. The original notebook, meanwhile, died. Just in case, and as I recommended, he removed that machine from the list in his U1 account.

4. December last year I installed him **Ubuntu 13.10** in his new 'old' Lenovo R60. Later he configured the U1 account as usual (I suppose, but I really don't know what happened after, I wasn't there). The fact is he seldom uses the notebook.

[B]*At this point supposedly the cloud contents should have been synchronized to the new machine*
[/B]However, he noticed that **each and every time he used the notebook** (sometimes just for we browsing) **almost files from his Documents folder would disappear**. The files could be found later in the desktop's Trash folder just like it happens when the files are deleted in a synced folder on the other computer. They weren't. Honestly, I had to see it with my own eyes and meanwhile I repeatedly told him he must have been deleting them, even inadvertently. The files have been recover from Trash meanwhile and are again in the cloud as well. Here's the troubleshooting I could do so far:

1. Removed the notebook from U1 and after assuring nothing was missing again then;
2. Configured U1 account again. No error messages and everything appeared to be fine, ie, nothing different from mine or any other for that matter.

However, **the symptom persisted**. Not only **U1 in the notebook said the sync was complete - it wasn't and nothing in its Trash folder -**, we noticed **the files were again in the desktop's Trash folder**. Again ***important***, **nobody deleted files from the other machine** (notebook). I was there this time and saw it happen without any user intervention.

Any ideas?

---

### Post by Vladlenin5000 on 2014-02-10
Long story short:

Computer 1 (desktop with 12.04) - Upload all the data to the cloud just fine.
Computer 2 (notebook with 13.10) - recently installed, U1 configured for the same user without errors but **as soon as it goes online it deletes all files in Documents folder**.


Any ideas?

---

### Post by thnewguy on 2014-02-11
My idea is to report this as a bug on Launchpad. This issue sounds pretty serious.

Update: This may seem silly, but are the clocks on the two computers set to the same time? I wonder if the clock on the second PC might be ahead of the other, indicating its copy of the Ubuntu One (or Documents) folder is newer than the version on the other PC. It may be that Ubuntu One thinks the laptop is holdest the newest version of files and is removing any "old" files not existing on the laptop.

---

### Post by Vladlenin5000 on 2014-02-12
That quite a weird albeit interesting hypotheses. I'll ba able to check it tomorrow but having different clocks is highly unlikely.
Meanwhile I will report as suggested.

---

