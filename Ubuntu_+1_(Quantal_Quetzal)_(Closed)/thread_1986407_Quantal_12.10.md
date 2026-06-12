---
title: "Quantal 12.10"
date: 2012-05-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by unibroker on 2012-05-24
I made a live cd of 12.10 today.  When I checked System Settings, Details it still says 12.04 LTS.  I checked my iso and it's named Quantal.  Anyone else notice this?  No biggie but just want to be tracking the new development.

---

### Post by MadmanRB on 2012-05-24
> **unibroker said:**
> I made a live cd of 12.10 today.  When I checked System Settings, Details it still says 12.04 LTS.  I checked my iso and it's named Quantal.  Anyone else notice this?  No biggie but just want to be tracking the new development.

This is normal, as the pre alphas and such are not branded or heavily modified yet.
I have tested a few alphas and most of them didnt have the new name until at least alpha 2

---

### Post by unibroker on 2012-05-24
> **MadmanRB said:**
> This is normal, as the pre alphas and such are not branded or heavily modified yet.
I have tested a few alphas and most of them didnt have the new name until at least alpha 2

Thanks for the quick response Madman.

---

### Post by oldfred on 2012-05-25
Moved thread to Ubuntu +1 Quantal forum.

---

### Post by grahammechanical on 2012-05-25
Open System Monitor. It will show Release 12.10 (quantal). Also run these commands:

```
uname -a
```

will give something like this:

> 3.4.0-1-generic #3-Ubuntu SMP Wed May 2 17:56:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

and

```
lsb_release -a
```

will give something like this:

> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu quantal (development branch)
Release:	12.10
Codename:	quantal

@unibroker

Have you thought of installing 12.10 into its own partition and dual booting? Become one of the development release testers.

If you do install to hard disk do not tick to install proprietary software. That will install proprietary video drivers as well. Which can be a good thing but I have found that it is possible to get Ubuntu 3D using the Nouveau open source driver which is activated when we do not activate a proprietary driver. We can also install Ubuntu Extras after installation.

Regards

---

### Post by unibroker on 2012-05-25
> **grahammechanical said:**
> Open System Monitor. It will show Release 12.10 (quantal). Also run these commands:

```
uname -a
```

will give something like this:



and

```
lsb_release -a
```

will give something like this:



@unibroker

Have you thought of installing 12.10 into its own partition and dual booting? Become one of the development release testers.

If you do install to hard disk do not tick to install proprietary software. That will install proprietary video drivers as well. Which can be a good thing but I have found that it is possible to get Ubuntu 3D using the Nouveau open source driver which is activated when we do not activate a proprietary driver. We can also install Ubuntu Extras after installation.

Regards

Thanks GM for your informative post.  I tried to edit the Title of this post because since it was moved here from Absolute Beginner Talk the original is hardly descriptive.  Any idea how to do that?

I would like to help in whatever way I can to advance the effort.  I have learned a lot in the brief time I have been here. This forum has been exceptional; lots of bright people  Currently I'm dual boot WinXP (have to have access to a proprietary database) and Ubuntu Precise.  Any suggestions?

---

### Post by jbicha on 2012-05-25
Unfortunately, the System Settings>Detail screen uses an image for the Ubuntu version, and not auto-generated text like it should.

---

### Post by cariboo on 2012-05-25
> **unibroker said:**
> Thanks GM for your informative post.  I tried to edit the Title of this post because since it was moved here from Absolute Beginner Talk the original is hardly descriptive.  Any idea how to do that?

I would like to help in whatever way I can to advance the effort.  I have learned a lot in the brief time I have been here. This forum has been exceptional; lots of bright people  Currently I'm dual boot WinXP (have to have access to a proprietary database) and Ubuntu Precise.  Any suggestions?

Click the report button in your first post, with a suggestion of what you would like the title to be, and I or one of the other staff members will edit the title.

---

