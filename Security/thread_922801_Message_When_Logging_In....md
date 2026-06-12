---
title: "Message When Logging In..."
date: 2008-09-17
forum: Security
---

### Post by YetiMachete on 2008-09-17
Whenever I try to login on Ubuntu 8.04, I just started receiving this message before it loads the desktop."User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

What does this mean, and what do I have to change to fix this? It just started popping up, I have no clue how it started appearing. Any input about this would be greatly appreciated

Kyle

---

### Post by Bakon Jarser on 2008-09-17
Open terminal.

```
sudo chmod 644 .dmrc
```

Also open nautilus and go to filesystem > home.  right click on the folder that matches your username and click properties.  go to the permisssions tab and under 'other' make sure it says 'access files'.

---

### Post by YetiMachete on 2008-09-17
Thanks Bakon Jarser, your information solved my problem! Kudos to you sir!

---

### Post by YetiMachete on 2008-09-17
I take it back, it didn't work. I did all the steps you included but to no avail.

---

### Post by Bakon Jarser on 2008-09-18
I used to have this problem and this is exactly what I did.

```
sudo chmod 644 .dmrc
```

Open nautilus and go to filesystem > home.  right click on the folder that matches your username and click properties.  go to the permisssions tab and under 'other' make sure it says 'access files'.  Also, do this for groups.  Hit the apply to all files button towards the bottom.  for some reason this changes the group and other settings back to read/write.  change them back to access only, close everything, and reboot.  if this doesn't fix the problem then I'm stumped.

---

### Post by YetiMachete on 2008-09-18
It worked, I missed setting one of the permissions and the message no longer pops up. So thanks again for your help, and sorry Im such a noob lol

---

