---
title: "backport of firefox issue -passwords not saving"
date: 2005-02-18
forum: Ubuntu Backports
---

### Post by gregtrob on 2005-02-18
I recently installed Warty - and then got the latest version of Firefox from the backports project.  For some reason Firefox won't save my user ids/passwords (which is normally in a file named somerandomnumbers.s).  I do have a file in the directory called signons.txt that looks like it might be the file but it still fails to show any of them when going to a page with the user id and password nor does it show them when i go to "remove".

Any thoughts?

Thanks,

Greg

---

### Post by jdong on 2005-02-18
I use that feature regularly and it works fine. 


Are you talking about the built-in Forms Manager that remembers passwords, or an extension?

---

### Post by gregtrob on 2005-02-20
The built in for saving passwords and form history - Form history appears to work however passwords do not appear to save for any site.

---

### Post by Marquis_de_Carabas on 2005-02-20
I've also had this issue since a recent re-install. Firefox simply doesn't offer to save passwords any more. However, I was using the backported Firefox before the reinstall and it worked perfectly, so unless the package has changed recently it wouldn't appear to be an issue with the backport.

I haven't had the time (or inclination) to really look into this yet, but I'm sure a bit of Googling will reveal all. I'll post back when I've figured it out, unless someone else beats me to it...

---

### Post by jdong on 2005-02-20
The firefox backport hasn't been touched in ages!

---

### Post by kassetra on 2005-02-20
I know the answer to this one!  I just dealt with it myself!
 
 You have to remove your signons.txt file from /home/username/.mozilla/firefox/default*
 
 The 0.93 and the 1.x have incompatibilites with the signons.txt file.
 
 Yeah, it sucks when you have a ton of places you don't want / remember the sign-in stuff for... but that's the only way to fix it (so far) because the import feature is uhhh, not working.

---

### Post by jdong on 2005-02-20
[QUOTE=kassetra]The 0.93 and the 1.x have incompatibilites with the signons.txt file.
[/QUOTE]
Yeah, that's one of the reasons Ubuntu doesn't do the Gentoo/Fedora style updates....

---

### Post by kassetra on 2005-02-20
which is a *REALLY* good thing.  :)

---

### Post by Marquis_de_Carabas on 2005-02-21
[QUOTE=kassetra]I know the answer to this one!  I just dealt with it myself!
 
 You have to remove your signons.txt file from /home/username/.mozilla/firefox/default*
 
 The 0.93 and the 1.x have incompatibilites with the signons.txt file.
 
 Yeah, it sucks when you have a ton of places you don't want / remember the sign-in stuff for... but that's the only way to fix it (so far) because the import feature is uhhh, not working.[/QUOTE]
 Thanks kassetra; works like a dream. I *knew* somebody would beat me to it! :)

---

