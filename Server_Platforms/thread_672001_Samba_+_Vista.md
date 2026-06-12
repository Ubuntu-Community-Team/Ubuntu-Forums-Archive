---
title: "Samba + Vista"
date: 2008-01-19
forum: Server Platforms
---

### Post by rogier.de.groot on 2008-01-19
Hi all,
I've been running a samba server (feisty) for a while now. It's on a simple workgroup setup, with security set to 'share' so we can access two read-only shares without having to enter username/password stuff. We have two other shares, pointing to the same directories, which allow read-write access with username/password authentication.
For most windows clients, this works just fine. Except of course Vista. I'd like to get this working without having to adjust registry settings, but I can't seem to figure out how. Can anyone help me?
TIA, Rogier de Groot

---

### Post by smileypaul on 2008-01-21
oh man.. t he joys of vista.. i came across this problem months ago!!

I did end up adjusting registry settings, but it didnt help.. 

I found the only way to do it, was to map the drive .. and then access it.  

By simply typing //192.168.0.1/share in th addres bar, Vista wouldnt trust the share, and deny the password... quite annoying.

Try mapping the drive.. .should be under tools in any "My Computer" window.

---

### Post by rogier.de.groot on 2008-01-23
Mapping the drive is what we always do to access writable shares, since it offers the option of supplying username/password, I think just trying to browse to it (using XP) ends up with "Guest" in the username field, which you can't change. We do the same with Vista, but it complains about the username/password being invalid, I think. Not entirely sure. If anyone would be so kind as to post a smb.conf known to work with Vista without regediting things.

---

### Post by warrior24 on 2008-01-23
didn't Microsoft get sued for this. I believe some company sued them on behalf of samba and won. Now samba pays like 8 grand   to be able to view there code and make it easer to get them network.

---

### Post by sandyeggoboy on 2008-02-15
hi ,

i am curious if this is resolved for someone? i am having the exact same problem.

---

