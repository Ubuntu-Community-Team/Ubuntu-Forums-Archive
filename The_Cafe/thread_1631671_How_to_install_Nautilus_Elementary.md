---
title: "How to install Nautilus Elementary?"
date: 2010-11-26
forum: The Cafe
---

### Post by Cam! on 2010-11-26
Every time I've previously installed it, something screwed up (For instance, the breadcrumbs came up all distorted).

What's the process? What's the PPA? Someone fill me in!:p

---

### Post by deanjm1963 on 2010-11-26
Here you go!

```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
```

Also, I don't know if it's just me, I used to have problems opening nautilus via "gksudo nautilus" unless I created a folder called " nautilus " in /root/.config/ before installing it.

Hope this helps.

---

### Post by Old Marcus on 2010-11-26
For the breadcrumbs issue, after installing, open nautilus and go to Edit>Preferences>Tweaks and check 'Show like breadcrumbs'. that sorts it.

---

### Post by Cam! on 2010-11-27
I checked the Breadcrumbs option, but I'm getting the same old pathbar.

---

### Post by Old Marcus on 2010-11-27
Open gconf-editor, go to Apps>nautilus>preferences, and uncheck 'always_use_location_entry'. That will re-enable the breadcrumbs.

---

### Post by Cam! on 2010-11-27
I did that, but now I just have a big text entry box with the path/folders in it.

---

### Post by koleoptero on 2010-11-27
Also install a theme that has breadcrumbs and use that.

---

### Post by Cam! on 2010-11-27
Alright. What's the PPA for the Elementary theme?

---

### Post by koleoptero on 2010-11-27
I'm terribly sorry for being impolite but... have you heard of google?

---

### Post by Cam! on 2010-11-27
Yeah, but I figured since I always messed up installations before, I could get the proper PPA + instructions from here.

---

### Post by koleoptero on 2010-11-27
Fair enough. First google result for search "elementary ppa"

sudo add-apt-repository ppa:elementaryart/ppa

then 

sudo apt-get update
sudo apt-get install elementary-theme elementary-icon-theme

---

### Post by Cam! on 2010-11-27
I installed Elementary, yet the themed Breadcrumbs don't show up on Nautilus. :/

---

### Post by Oxwivi on 2010-11-27
I've been stalking this thread for while, just dropping by to say that I had absolutely no problems by doing these after adding the PPA:```
**sudo apt-get update && sudo apt-get dist-upgrade**
```

---

### Post by Perfect Storm on 2010-11-27
Remember to 
```
nautilus -q
```
afterwards.

---

### Post by Old Marcus on 2010-11-27
Edit: Late to the party.

---

### Post by Paradigm_Shift on 2010-12-14
> **Old Marcus said:**
> Open gconf-editor, go to Apps>nautilus>preferences, and uncheck 'always_use_location_entry'. That will re-enable the breadcrumbs.
This solved the problem I was having. Thank you very much!

---

