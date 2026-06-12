---
title: "cannot report bugs / problem logging to flashback ubuntu 21.10"
date: 2021-09-26
forum: Ubuntu Development Version
---

### Post by Claus7 on 2021-09-26
Hello,

having updated to ubuntu 21.10 development version (beta) I face two problems: 

1) the first one is reporting bugs. Every time system crushes for some reason the error I'm getting is the following:
Cannot connect to crush database, please check your internet connection.
HTTP Error 502: Bad Gateway 

Is it me or the website faces some issues? The Uploading problem information process takes a lot of time for the filling bar to complete and at the end it reports this issue. During the very first reports after the upgrade apport had crushed. Any ideas? The connection is via wifi.

2) the second one is that the system refused to loggin to ubuntu flashback compiz or metacity at once by entering a loop. If I change the loggin option things are fine. For this second issue 21.10 is still under development. I just mention it in case someone else has noticed the same behavior as me.

Regards!

---

### Post by Claus7 on 2021-10-11
Hello,

after ~2 weeks for the aforementioned problems:

1) in between this period of time apport made an update. I haven't noticed any problem to report in between though, so I do not know if the internet connection error still remains. One thing that I noticed is that if I try from Software to install an application, internet complains and if I click on the error it opens a new window showing that wired network is not enabled (which is correct since I'm connected via wifi). 

2) the problem remains even if updates of xorg have taken place. I noticed though, as here:
[https://ubuntuforums.org/showthread.php?t=2467453](https://ubuntuforums.org/showthread.php?t=2467453)

that by clicking the session flashback, just before login, the loop is gone and the login proceeds normally. 

Regards!

---

### Post by osse7 on 2021-10-11
Latest change:

apport (2.20.11-0ubuntu70) impish; urgency=medium

  * etc/apport/crashdb.conf: Disable Launchpad crash reports for 21.10
    release.

so your issue is expected ):P

---

### Post by Claus7 on 2021-10-11
Hello,

thank you *osse7* for the input. Good to know. [I would like to mention that with the latest updates Software is working as it should.]
EDIT: Nope, it does not. I can see the applications but I cannot install them. Spoke too soon.
EDIT2: With the latest updates Software is working as it should and flashback login was successful.

Regards!

---

### Post by ariftajru on 2021-10-13
hi! 
Thanks for your Updates - I hope solve your problem And you must work easily -

---

### Post by Claus7 on 2021-10-13
Hello and welcome to the forums,

indeed, so far login logout has no problem.

Regards!

---

### Post by Claus7 on 2022-08-12
Hello,

having installed 22.10 using virtualbox, I face exactly the same problem. A crush occurred and the normal procedure of collecting crush information was followed. Just before the uploading bar was full in order to upload the crush report, the following message appeared (as reported before):
> Cannot connect to crush database, please check your internet connection.

HTTP Error 502: Bad Gateway

The error happened when using flashback while trying to add an item to the panel.

Regards!

---

