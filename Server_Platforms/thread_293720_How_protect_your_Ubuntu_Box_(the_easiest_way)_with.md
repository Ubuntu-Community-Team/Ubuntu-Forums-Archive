---
title: "How protect your Ubuntu Box (the easiest way) with Clam Antivirus"
date: 2006-11-05
forum: Server Platforms
---

### Post by andoty_jazz on 2006-11-05
**Installing Clam Antivirus :: the easiest way**
[SIZE="1"](Ubuntu Dapper 6.06 - 2.6.15-27-386) [/SIZE]


**(1)** :-D  Open Synaptics ===> Go to :::: System -> Administration -> Synaptic Package Manager
[B]
(2)[/B] :-k  Open a Browser and Go To [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories), 
Read the instruction then apply it.

**(3)** :confused: 
3.1. Search for **clam**
3.2. Mark the check boxes namely from: **clamassasin** to **clamsmtp**
3.3. Press Apply.

**(4)** :p Now to make your life easier, install GUI.
4.1. AVSCAN - GTK frontend for the Clam AntiVirus scanner (ClamAV).
            - command --> **avscan**
4.2. KLAMAV - a frontend to the popular Clamav antivirus application.
            - command --> **klamav**
4.3. CLAMTK - graphical front-end for ClamAV
            - command --> **clamtk**

:: To install the above GUIs, just search for them in the Synaptic Package Manager.

**(5.)** :)  Add an icon on the panel to run the GUI for Clam
5.1. Right click on the Panel and Press **Add to Panel** --> **Custom Application**.
5.2. Fill up the necessary forms and put a **command** (refer the commands on number **(4.)**)
5.3. Repeat steps **5.1.** and **5.2** for every GUI you use.

**(6)** :rolleyes: Ooopsss... We must install the necessary dependencies to the run GUI's for Clam Antivirus:
Using Synaptic Package Manager, install "**gcc**", "**zlib**" and "**zlib-devel**"

**(7)** :twisted:  Happy virus killing.

---

### Post by platinumpresto on 2006-11-15
Thank You!!!!

---

### Post by Phidaux on 2006-11-16
Cheers, thanks alot.

---

### Post by andoty_jazz on 2006-11-16
Ur all welcome men... 

1.) Spirit of Linux - "Learning while doing"
2.) Spirit of FOSS - "Always ready to share"

Keep on using Ubuntu, after you migrated completely from any "Virus-Infected" OS, you wont be needing this guide anymore. LOL

---

### Post by WNDS1701 on 2007-05-09
There's just one problem with me ... Freshclam is not working with me.

Any hints?

THANKS IN ADVANCE!

---

### Post by Barfleur on 2007-05-11
Thank you very much. that was awesome!!!!

[COLOR="Red"]Benjamin Barfleur[/COLOR]

[COLOR="Blue"]Registered Linux User: #443487[/COLOR]
[COLOR="DarkOrchid"]Linux Counter: [http://counter.li.org](http://counter.li.org)[/COLOR]

---

### Post by imon9 on 2007-05-11
hope i am not offending anyone here..but i am seriously curious:

(1) why do we need antivirus program in linux (for now) it seems pretty unaffected by any windows virus....

(but i would understand if u want to scan the files that you are sending to your windows frens)

(2) question about Clam antivirus: does it detect virus that affects windows only, or it also aware of linux virus? (is there any btw..hahaha)

---

### Post by peterbrewer on 2007-05-11
> **imon9 said:**
> hope i am not offending anyone here..but i am seriously curious:

(1) why do we need antivirus program in linux (for now) it seems pretty unaffected by any windows virus....

(but i would understand if u want to scan the files that you are sending to your windows frens)

(2) question about Clam antivirus: does it detect virus that affects windows only, or it also aware of linux virus? (is there any btw..hahaha)

My understanding is currently there are no wild viruses for linux.  The software exists for people who share files with windows users and for protecting windows.  You don't need it for Linux.

---

### Post by andoty_jazz on 2007-05-12
> **Barfleur said:**
> Thank you very much. that was awesome!!!!

[COLOR="Red"]Benjamin Barfleur[/COLOR]

[COLOR="Blue"]Registered Linux User: #443487[/COLOR]
[COLOR="DarkOrchid"]Linux Counter: [http://counter.li.org](http://counter.li.org)[/COLOR]

Your very welcome Benjamin. 
Absolutely to make life easier.
To everyone, we should try the bleeding edge Ubuntu 7.04 (Feisty Fawn) it will surely make our computing experience a lot easier. 

"Good that you're using the Latest Flavor"

---

### Post by andoty_jazz on 2007-05-12
> **peterbrewer said:**
> My understanding is currently there are no wild viruses for linux.  The software exists for people who share files with windows users and for protecting windows.  You don't need it for Linux.

I agree. 

You're exactly right peterbrewer. 

Sad to say that there are networks that inter-operate and inter-communicate with each other. For such, Linux and Windows. Anti-Virus is for Windows not for Linux. 

My purpose for this was  just to share and invite Windows users to migrate themselves to Linux not to force them. 

Free Anti-Virus (Clam) and Free Operating System (Ubuntu Linux) that gives you the Freedom. Isn't it a whole new viable solution without even spending a penny? 

Sooner or later, Windows users will feel that the Linux is **"REALLY SOMETHING"**.

---

