---
title: "Install a WINE Application System Wide"
date: 2010-11-23
forum: Wine
---

### Post by weatherkid on 2010-11-23
Hello! I am trying to get my school district to switch to Ubuntu, and a question they have is, can you install a program (ex. Office '07) on all accounts at once. Any ideas?

---

### Post by TSJason on 2010-11-23
There are probably a few ways to accomplish this. Some ideas might be:

[LIST]
[*]Create a sym-link in the /etc/skel folder such that the install is automatically made available upon a user's first login.
[*]Create a script or /etc/fstab entry that automatically mounts a shared network resource with the install (read-only)
[*]Install it to a location on each machine and export the $WINEPREFIX  variable to that location in the public profile or bash_profile file.
[/LIST]

I believe all solutions will require a little fiddling with symlinks to someplace in /tmp of the local box because Office likes to store temporary files in places that won't be writable by students. 

Ultimately it's probably going to come down to how your environment is setup and what works best for you.

Ideally it would be nice if they could get away from leaning on Microsoft for software solutions and embrace FOSS.

---

### Post by cwwilson721 on 2010-11-23
I have World of Warcraft installed system-wide.

I created a /WoW folder, changed permissions on it so ALL users have read/write access, and use the 'env WINEPREFIX' variable to access it.

Example:
```
env WINEPREFIX="/WoW" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```

Also, use then same env WINEPREFIX for wineconfig:
```
env WINEPREFIX="/WoW" winecfg
```
The above allows for the 'bottle' to be setup correctly, and setup sound, drives, and whatever else.

Just remember to create a Launcher with the appropriate command for each user (Or have it setup in the 'skel' file )

---

### Post by dankegel on 2010-11-23
Yes, you can totally do it... see how Picasa from Google
did it.  Codeweavers does it with some packages, too.
In fact, you should go look at the rpm/deb creation utility
built into Codeweavers Crossover Professional; that
does exactly what you want, I bet.
See [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

Now, to use the Codeweavers version, you'll need to get
a volume license for the school, but it might be a good deal,
you'd be supporting the Wine project, and you would have
someone to call if Wine broke.

Or you can roll your own by copying how Picasa worked.

Either way, good luck!

---

### Post by dankegel on 2010-11-23
> **cwwilson721 said:**
> I have World of Warcraft installed system-wide.

I created a /WoW folder, changed permissions on it so ALL users have read/write access

Shared system-wide bottles don't work ... the moment two
users try to use it at the same time, it will explode,
and send shards all over the room.

---

### Post by cwwilson721 on 2010-11-25
OP never said "Multiple Simultaneous Users", just "System-wide"

My version works for System-wide.

---

### Post by tjwilli on 2010-11-25
If you can get them to switch to Ubuntu, why not also sell them on OpenOffice?

---

