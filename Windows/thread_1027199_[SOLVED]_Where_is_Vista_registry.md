---
title: "[SOLVED] Where is Vista registry?"
date: 2009-01-01
forum: Windows
---

### Post by buccaneere on 2009-01-01
My machine HP dv9428nr is triple boot Vista/XPPro/Ubuntu.

I booted Vista for some reason, can't even remember now, and got hassled by Norton AV. I deleted all Symantec keys from the registry that I could find. Some Symantec keys would not delete.

Then the connection went to 'connected(wireless)/local only'. Apparently Vista has a connectivity problem with Norton uninstalls. Norton removal tool needs to know which NAV you have. I cannot tell now, since I've butchered the NAV install.

I found a bunch of Symantec folders (from Ubuntu boot) in the Vista partition, and deleted some more, but not enough.

If I can find the registry, I might be able to delete the rest of the registry entries.

Anybody?

---

### Post by jrusso2 on 2009-01-01
HK local machine and HK current user is where the hives are.

---

### Post by chamber on 2009-01-01
Usually, if you just pick one of the more recent versions of Norton when downloading the removal tool it will do the job.

[http://service1.symantec.com/SUPPORT/norton2008.nsf/docid/2007082908475279?Open&docid=2005033108162039&nsf=tsgeninfo.nsf&view=docid](http://service1.symantec.com/SUPPORT/norton2008.nsf/docid/2007082908475279?Open&docid=2005033108162039&nsf=tsgeninfo.nsf&view=docid)

---

### Post by Kernel Sanders on 2009-01-01
Start---->Run----->regedit

---

### Post by gjoellee on 2009-01-02
> **kernel sanders said:**
> start---->run----->regedit

+1


or you can go 

Windows Button+R---->regedit

---

### Post by buccaneere on 2009-01-05
> **jrusso2 said:**
> HK local machine and HK current user is where the hives are.

> **Kernel Sanders said:**
> Start---->Run----->regedit

> **gjoellee said:**
> 
[QUOTE=Kernel Sanders;6473132]Start---->Run----->regedit+1


or you can go 

Windows Button+R---->regedit[/QUOTE]

Sorry guys; I'm a bad communicator... I thought I made it clear that when I had Vista booted, I know where the registry is, and that I had deleted all the pertinent keys I could find.

> **buccaneere said:**
> My machine HP dv9428nr is triple boot Vista/XPPro/Ubuntu.

I booted Vista for some reason, can't even remember now, and got hassled by Norton AV. **[COLOR="Red"]I deleted all Symantec keys from the registry that I could find.[/COLOR]** Some Symantec keys would not delete.

Then the connection went to 'connected(wireless)/local only'. Apparently Vista has a connectivity problem with Norton uninstalls. Norton removal tool needs to know which NAV you have. I cannot tell now, since I've butchered the NAV install.

I found a bunch of Symantec folders **[COLOR="Red"](from Ubuntu boot) in the Vista partition,[/COLOR]** and deleted some more, but not enough.

If I can find the registry, I might be able to delete the rest of the registry entries.

Anybody?

I'm guilty too; I read the title and don't read the details.

Anybody know where the Vista registry is (from Ubuntu boot)???

Thanks

---

### Post by carml on 2009-01-05
I don't know where is located the registry on Vista,but i suggest you to use a software like CCleaner when you are under Windows.This software like others give you the option to scan for registry problems and try to automatically solve them.
I hope this suggestion can help you. :P

---

### Post by Battie on 2009-01-05
User registry hives are in c:\Users\<username>\ntuser.dat.
The other hives are in c:\Windows\System32\config\.

Unfortunately, you can't just open and edit these.  I've seen a few programs that will mount them and let you view the file structure.  There might be a tool written for Ubuntu to do this, but I don't know about it...

Before we go into that, have you looked at the properties for your network adapter?  I've seen Symantec products put some weird stuff into the stack that will significantly affect the adapter's operation.  Right-click on the adapter that won't work, go to Properties, and show us what's checked there.

---

### Post by bapoumba on 2009-01-05
Moved to Windows Discussions.

---

### Post by cabbiinc on 2009-01-05
You might try a system restore if you have a restore point that's before when the problem started. If the system restore won't work from the hard drive, you could try doing it from the Vista install disk, but you'd still need the restore point saved on your hard drive.

---

### Post by Skripka on 2009-01-05
> **cabbiinc said:**
> You might try a system restore if you have a restore point that's before when the problem started. If the system restore won't work from the hard drive, you could try doing it from the Vista install disk, but you'd still need the restore point saved on your hard drive.

+1

Removing Norton has always been a nightmare-and I've seldom succeeded in removing all trace of it-without repartitioning the HDD.  Fortunately the last time I had to deal with that crap was 6 years ago.

---

### Post by ciscosurfer on 2009-01-05
@OP,

My recommendation would be to boot into Vista and take care of the removal process there.  You are causing yourself more of a headache by wanting/trying to manipulate your Vista registry from within Ubuntu.  Symantec/Norton has good tutorials on their site for manual removal of all of their programs if their automated tools don't do the job they're supposed to.

---

### Post by buccaneere on 2009-01-09
I found a **generic** NAV remover, and all is well with Vista (for when I boot it again in a few months:lol:).

[ftp://ftp.symantec.com/public/english_us_canada/removal_tools/Norton_Removal_Tool.exe](ftp://ftp.symantec.com/public/english_us_canada/removal_tools/Norton_Removal_Tool.exe)

I booted Ubuntu, saved it to the Vista partition (desktop), re-booted Vista, and executed.

All suggestions were good. And you have to read critically, and make some  inferences too.

Such as getting NAV removed at the Norton site. You have to know which version of NAV you have. I had already removed MANY Symantec registry keys while booted into Vista, and removed some 'Symantec' folders while booted in Ubuntu. There THEN was no way to tell what version of NAV I had.

AND, whatever solution was found, it had to be downloaded from within Ubuntu.

---

