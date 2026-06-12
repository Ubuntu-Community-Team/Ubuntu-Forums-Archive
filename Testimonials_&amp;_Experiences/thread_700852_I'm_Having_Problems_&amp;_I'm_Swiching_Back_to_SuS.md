---
title: "I'm Having Problems &amp; I'm Swiching Back to SuSE"
date: 2008-02-18
forum: Testimonials &amp; Experiences
---

### Post by money2themax on 2008-02-18
I've been using Ubuntu for about 2 1/2 months now and I have had few to almost no problems but recently I updated KDE and i lost the ability to shut down i go press the shut down button on the task bar and it gives me these options:

```

Log Out
Lock Screen
Switch User
Suspend
Hibernate

```

^ that rather bugs me
so after several other problems i've decided to switch back to SuSE...my only problem is Getting my firefox bookmarks & all my pidgin contacts

everything else i can deal with my self

---

### Post by p_quarles on 2008-02-18
Moved to Testimonials & Experiences.

Copy the ~/.pidgin and ~/.mozilla directories to a storage device. That will keep all the data for those two applications.

---

### Post by jrusso2 on 2008-02-18
> **money2themax said:**
> I've been using Ubuntu for about 2 1/2 months now and I have had few to almost no problems but recently I updated KDE and i lost the ability to shut down i go press the shut down button on the task bar and it gives me these options:

```

Log Out
Lock Screen
Switch User
Suspend
Hibernate

```

^ that rather bugs me
so after several other problems i've decided to switch back to SuSE...my only problem is Getting my firefox bookmarks & all my pidgin contacts

everything else i can deal with my self

I suspect your using GDM with KDE instead of KDM.  This appears to happen when you use this combination

---

### Post by money2themax on 2008-02-18
> **p_quarles said:**
> Moved to Testimonials & Experiences.

Copy the ~/.pidgin and ~/.mozilla directories to a storage device. That will keep all the data for those two applications.

i'm guessing you mean:

/Home/[USER NAME]/.Pidgin
/Home/[USER NAME]/.Firefox

Right?

EDIT: Those Folders Don't Exist

> **jrusso2 said:**
> I suspect your using GDM with KDE instead of KDM. This appears to happen when you use this combination
GDM?
KDM?
What are those?

---

### Post by niethslim on 2008-02-18
Gnome Display Manager and K Display Manager.
```
sudo dpkg-reconfigure gdm
```
And then choose GDM or KDM, depending on if you use Gnome or KDE more.

---

### Post by ryanhaigh on 2008-02-18
thats correct, in a terminal ~/ is associated with your home directory

---

### Post by money2themax on 2008-02-18
i'd rather switch to SuSE and use all my stuff on that OS because i'm used to it 

so if you could tell me how to get all my info for those 2 programs so that i can switch that would be helpful

---

### Post by Shadowmeph on 2008-02-18
Use Foxmarks for your firefox plugins

---

### Post by money2themax on 2008-02-18
pidgin files are in 
```

~/.purple

```

---

### Post by ryanhaigh on 2008-02-18
there are hidden folders in your home directory associated with those two programs i believe for firefox it will be either .firefox, .mozilla-firefox or .mozilla/firefox. for pidgin i believe your settings etc are stored in .purple

---

### Post by money2themax on 2008-02-18
Thank you all for your help i do hope my school switches to Ubuntu Or SuSE

also i will continue to come here to help and try to receive help thanks again wish me luck on switching to SuSE [which one should i switch to 10.1 commercal  or 10.3 OpenSuSE]

---

### Post by money2themax on 2008-02-18
> **niethslim said:**
> Gnome Display Manager and K Display Manager.
```
sudo dpkg-reconfigure gdm
```And then choose GDM or KDM, depending on if you use Gnome or KDE more.
this happened
```
money2themax@MX-Ubuntu-000:~$ sudo dpkg-reconfigure gdm
[sudo] password for money2themax:
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

```

---

### Post by niethslim on 2008-02-18
Is there any change after you reboot?

---

