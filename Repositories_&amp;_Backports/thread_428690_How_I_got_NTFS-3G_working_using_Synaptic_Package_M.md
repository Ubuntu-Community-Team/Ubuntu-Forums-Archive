---
title: "How I got NTFS-3G working using Synaptic Package Manager?"
date: 2007-04-30
forum: Repositories &amp; Backports
---

### Post by PradeepSridharan on 2007-04-30
This post is for people who like working on GUI based tools to install packages in UBUNTU. I am not too comfortable with opening terminal and installing stuff. This step by step installation described below is to enable the access of NTFS based file systems in read/write mode. I have had personal experience doing this because I work on a dual boot Windows XP & UBUNTU.

**Installation**

Open Synaptic Package Manager and do the following.
1) Goto **Settings** --> **Repositories**

2) In the window that opens & says "Software Sources", choose the tab "**Third Party Software**".

3) Click on "**Add**" button, provide the following string
**deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all**

4) Click "**Add Source**".

5) Repeat Steps 3) & 4) for the following strings.
[B]deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all[/B]

6) Click on "**Close**" button.

7) Click on "**Reload**" button.

8) Click on "**Search**" icon, provide the search string as **NTFS**.

9) Choose "ntfs-3g" in the search results and "**Mark for Installation**". Approve the installation of dependent libraries as well.

10) Click on "Apply" to download and install the package.

Once installed, it can be accessed to enable NTFS filesystems in read/write mode from the **"System" --> "NTFS Configuration tool"**. This menu structure would be available in KDE environment.

If someone is using this, All the best and good luck.
Pradeep.

---

### Post by agurk on 2007-05-01
Just a word of caution. I know you mean well Pradeep and I'm glad you got things working, but adding random repositories is bad security practise unless you know exactly what you're doing. My advise would instead be to install Feisty, for which ntfs-3g is available in the Universe repository, in a fairly recent version (1.328).

---

### Post by PradeepSridharan on 2007-05-03
Point well taken sir.
Pradeep.

---

