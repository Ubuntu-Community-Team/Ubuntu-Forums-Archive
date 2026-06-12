---
title: "Network Antivirus"
date: 2009-08-25
forum: Security
---

### Post by NZ-Stevo on 2009-08-25
Hi all. Just new to Ubuntu after migrating from Windows XP

Have a problem i would like to try and resolve. I have a NAS drive, which is a LevelOne unit (run by linux) and i want to have an antivirus application on my ubuntu machine to scan the NAS for viruses as this is accessed from windows machines.

I have trialled all the AV's suggested on the Ubuntu website but nothing does what i am after.

I would also prefer to have a gui based option rather than something run through terminal.

Any suggestions welcomed.

---

### Post by zipperback on 2009-08-25
clamtk is the gui for clamav

Hope this helps you.

- zipperback
:popcorn:

---

### Post by TuckLive on 2009-08-25
Have a look at [OSSEC]("http://www.ossec.net/").  It has a nice web-based gui so you can monitor all computers on your network.

---

### Post by cdenley on 2009-08-25
> **NZ-Stevo said:**
> I have trialled all the AV's suggested on the Ubuntu website but nothing does what i am after.
You couldn't get any AV scanner to scan a locally mounted NAS drive? You should be able to scan any locally-accessible file or directory.

---

### Post by HermanAB on 2009-08-25
Use ClamAV.  It is easy to configure.  The reason why Linux programs frequently don't have a configuration GUI is because it is done once only, so there is no point in making a GUI that will almost never be used.

---

