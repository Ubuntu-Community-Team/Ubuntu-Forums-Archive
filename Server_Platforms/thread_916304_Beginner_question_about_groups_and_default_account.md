---
title: "Beginner question about groups and default account"
date: 2008-09-10
forum: Server Platforms
---

### Post by Kabaal on 2008-09-10
Hello. I recently wiped my server clean and installed ubuntu server over my previous gentoox install and I'm liking it so far. Problem is I wanted a new home directory for my account and instead of just changing it I deleted the default account I had and just created a new one under the same name.

And now to my question(s), what groups is the default user in? I've been googling but I havent found anything about all the different groups, cdrom etc are pretty self-explanatory. But other than that I have no clue what groups I should be adding.
And another thing, I cant use arrow-up to scroll previous commands and I cant see the name of the server and location in the terminal I'm guessing this is group related too?

Any help would be greatly appreciated.

---

### Post by bab1 on 2008-09-10
The home directory has all of the setup for the original user.  This includes the terminal command history.  The typical groups are:```
YOUR_LOGIN adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
```

This will be a pain to get correct.  Plus you have probably lost the ability to use:```
sudo 
```

I would re-install unless that is to much of a hardship.

---

### Post by Kabaal on 2008-09-11
How much settings have I lost? I have the ability to sudo since I added another account to the admin group and then added my newly created account.

---

### Post by kamaji792 on 2008-09-11
Try:
```
groups <user_name>
```
to see the groups a user belongs to.

---

### Post by windependence on 2008-09-11
You can better scroll through screen history by accessing the server from another machine using ssh. I hardly ever work directly at the console.

-Tim

---

### Post by Kabaal on 2008-09-11
I havent touched the keyboard, I'm using putty to SSH in from my laptop. I ended up reinstalling ubuntu instead of hassling with everything. It would be nice to know how to fix it if something similar would happen again though.

---

### Post by bab1 on 2008-09-11
> It would be nice to know how to fix it if something similar would happen again though.

I assume this is not a production server.  Learn how to add a user from the lowest level.  Read the man pages on:```
useradd
``` and ```
usermod
```  There is also: ```
groupadd
``` and ```
groupmod
```.

The user also has config files for preferences.  See what is in the home directory of correctly working user.  I used to keep a set of my home directory files offline.  I had all the config files ready to use if I needed to recover from disaster.

---

