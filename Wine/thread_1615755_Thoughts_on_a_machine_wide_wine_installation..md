---
title: "Thoughts on a machine wide wine installation."
date: 2010-11-07
forum: Wine
---

### Post by fang64 on 2010-11-07
Hello everyone,

I recently had a problem with wine, that I know that has been plaguing a select set of users. Specifically dealing with multiple users accessing a single wine prefix. Then I remembered fuse unionfs, I want to know what are the potential problems of having a read only wine prefix when using fuse unionfs with the read only wine prefix folder and a read write folder. I do not know of anyone else whom has tried this but I am investigating this option this afternoon as it's an annoyance to install the application per user. I'd like to have it system wide, I would appreciate any direction or advice to the matter.

---

### Post by cwwilson721 on 2010-11-07
Actually, I have no issues with a setup I have:

/wine/<all the other stuff>

Using ```
env WINEPREFIX="/wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
``` to run World of Warcraft for other users on my system.

I had to make sure the entire /wine folder (actually, a separate harddrive mounted to /wine) had all correct permissions.

And to set it up, I just typed in terminal ```
 env WINEPREFIX="/wine" winecfg
```

---

### Post by cogadh on 2010-11-07
What cwwilson721 said. Just make a Wine prefix in a shared location that all users can access, then you only have to install things once. You will probably have to manually create shortcuts to launch the apps on each user's profiles, but that is significantly easier than individually installing applications.

---

### Post by cwwilson721 on 2010-11-07
> **cogadh said:**
> What cwwilson721 said. Just make a Wine prefix in a shared location that all users can access, then you only have to install things once. You will probably have to manually create shortcuts to launch the apps on each user's profiles, but that is significantly easier than individually installing applications.lol..Yeah, I forgot about that.

But it's not only easier than new installs all over the place, but imagine installing WoW in 4 different spots on one Ubuntu install (16+GB per. it starts adding up...lol)

I DO have a separate WoW/wine install on in my user folder. That way, I can do updates, etc, before I try it on my multi-user wine install

---

### Post by fang64 on 2010-11-07
ok here comes the problem I have a user remoted in with a wine program running using the shared prefix then another user logs in and they are both accessing the registry will it become corrupt? Also add the fact that it could be up to 3 users at a time....

Additionally, the software is a database application, that cannot be replaced at the moment with a linux equal, however I'd rather not install a copy per user as noted by cogadh. I however want the users the ability to modify their settings for the application uniquely per user as each user as preferences. I don't guess anyone has used fuse unionfs to do this....

---

### Post by felix667 on 2012-04-13
> **cwwilson721 said:**
> Actually, I have no issues with a setup I have:

/wine/<all the other stuff>

Using ```
env WINEPREFIX="/wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
``` to run World of Warcraft for other users on my system.

I had to make sure the entire /wine folder (actually, a separate harddrive mounted to /wine) had all correct permissions.

And to set it up, I just typed in terminal ```
 env WINEPREFIX="/wine" winecfg
```

Can you, please, elaborate on the entire /wine folder having all correct permissions?

---

