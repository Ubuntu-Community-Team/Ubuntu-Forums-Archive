---
title: "Is This Even Possible?"
date: 2008-07-05
forum: The Cafe
---

### Post by knudsenjoe on 2008-07-05
Not sure if this is the correct place, but I didn't want to muck up the help sections.

I am a big fan of random logins, and I was wondering if it was possible to have a login manager that looks through say the 'Pictures' folder and even better subfolders as well, and uses that as the background for a login screen? My idea is instead of having to create a new GdmGreeterTheme file for my logins, I could make a 'generic' type of user/password entry, and have a random screen displayed behind it.

Is this even possible?

---

### Post by billgoldberg on 2008-07-05
Well if you select multiple GDM themes, they will rotate.

If that is what you meant.

---

### Post by knudsenjoe on 2008-07-05
Naw, what I'm getting at is like this...

1- Create an otherwise generic user/password entry item
2- When a user logs in, the manager would 'get' a random picture, and place the generic login on top

So instead of having to create/download individual login themes, I could create the sign in part, and have the login manager place a picture with it.

---

### Post by klange on 2008-07-05
If you want a single GDM theme file you can use a script that replaces the image it uses for the background on start up with a random one, easiest way being an ln -sf with a set of random pictures and a bash script. Then you can create a single generic login that, preferably one that would look good with any background, and make it use that symlink as the background. Every time you boot, the script runs, selects a random image, links the file to it, GDM starts and uses your randomly selected background but always uses the same theme file.

---

