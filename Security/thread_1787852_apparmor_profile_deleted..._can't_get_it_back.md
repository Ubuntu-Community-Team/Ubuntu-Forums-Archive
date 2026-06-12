---
title: "apparmor profile deleted... can't get it back"
date: 2011-06-21
forum: Security
---

### Post by judderwocky on 2011-06-21
i was trying to edit my firefox apparmor profile. I used aa-genprof, and accidentally closed the terminal before the program was finished. Firefox wouldn't load properly after that whenever it was enforced. 

I uninstalled and reinstalled the profiles, but it didn't help.

Finally I deleted the files for the profile itself ... now it will not reinstall them...

I marked all the apparmor packages for complete removal and then reinstalled them but it will not put the original firefox profile back in

?>??????

---

### Post by Dave_L on 2011-06-21
You should be able to get the firefox .deb from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), and then extract the apparmor profile from the .deb using File Roller (Archive Manager).

---

### Post by judderwocky on 2011-06-22
thanks for the tip... I downloaded the 5.0 deb by mistake, and ended up installing firefox 5.0 instead... which i'm actually happier with ... it fixed the apparmor profile in the process lol (both deb files have the profile)

---

