---
title: "suggestion"
date: 2005-08-29
forum: Ubuntu Backports
---

### Post by duffman25 on 2005-08-29
Hi

My only problem with ubuntu is the fact that apps don't get upgraded in the 6-month support cycly of the stable release. There are only security fixes, this is fine with some apps, but other apps (such as desktop related) could be updated without compromising the system stability. 

That is why the backports came out. Backports are great, but slow. In fact, there hasn't been many backports updates in a while (or at least I haven't notice them). So I've thought of something... I was thinking that the backports team could have a small list of packages that are prone to be backported in this safe manner. For example, firefox, gaim, etc. Then, since the backports are now an official part of ubuntu, a small script could be created to regulary create a backport of that package once it has entered the development version of ubuntu, this way the backports would be more automated, & many people would be satisfied.

My main concern here is that I would like to have the backports efforts more integrated with ubuntu. This way, people would only have to ask once for a backport, and if it's beleived to be safe to backport it, then automate it so that everytime the current development relase of ubuntu updates that package, there's a backport for it, and users don't have to ask again to backport the new version of that package.

Just my 2 cents. If anyone has an alternative idea please say it. :)

---

### Post by earobinson on 2005-08-29
I think that that is a great idea as long as it is true that the backports are an offical part of ubuntu i did not know this.

---

### Post by duffman25 on 2005-08-29
[QUOTE=earobinson]I think that that is a great idea as long as it is true that the backports are an offical part of ubuntu i did not know this.[/QUOTE]

> Is this project endorsed by the Ubuntu Team?
As of June 2005, we are an official Ubuntu project, so we are acknowledged by the developers. Therefore, the developers won't have issues with Backports users

quoted from [here](http://ubuntuforums.org/showthread.php?t=40291)

---

### Post by dcraven on 2005-08-29
[QUOTE=duffman25]Then, since the backports are now an official part of ubuntu, a small script could be created to regulary create a backport of that package once it has entered the development version of ubuntu, this way the backports would be more automated, & many people would be satisfied.[/QUOTE]

You should attach your small script to a new bugzilla report. That way it could be tested and reviewed. If it works, then this may have a better chance of happening.

~djc

---

### Post by duffman25 on 2005-08-29
[QUOTE=dcraven]You should attach your small script to a new bugzilla report. That way it could be tested and reviewed. If it works, then this may have a better chance of happening.

~djc[/QUOTE]

I'm afraid I don't have such script. It was just an idea

---

### Post by SymGeosis on 2005-08-30
And he wouldn't really be the right person to create such a script. If there ever was a script like this for backports it would be up to the awesome people at Ubuntu/Backports to decide exactly how this script should operate and which packages it should apply to (the latter being the main part of the script I'd imagine).

However, I don't see this as very likely but it can never hurt to hope.

---

### Post by duffman25 on 2005-08-30
[QUOTE=SymGeosis]And he wouldn't really be the right person to create such a script. If there ever was a script like this for backports it would be up to the awesome people at Ubuntu/Backports to decide exactly how this script should operate and which packages it should apply to (the latter being the main part of the script I'd imagine).

However, I don't see this as very likely but it can never hurt to hope.[/QUOTE]


If many os us think is a good idea, maybe the backports team will take it under consideration. I think that the hole backporting thing should be as much automated as possible.

---

### Post by dcraven on 2005-08-30
[QUOTE=SymGeosis]And he wouldn't really be the right person to create such a script. If there ever was a script like this for backports it would be up to the awesome people at Ubuntu/Backports to decide exactly how this script should operate and which packages it should apply to (the latter being the main part of the script I'd imagine).[/QUOTE]

Isn't the Ubuntu/Backports project open to all? I think the possibility for duffman25 or anyone else for that matter to get involved does exist. The more willing and capable people the better. Also, the more you get involved, the louder your voice. I'm sure they would appreciate the help.

Cheers,
~djc

---

### Post by duffman25 on 2005-08-31
[QUOTE=dcraven]Isn't the Ubuntu/Backports project open to all? I think the possibility for duffman25 or anyone else for that matter to get involved does exist. The more willing and capable people the better. Also, the more you get involved, the louder your voice. I'm sure they would appreciate the help.

Cheers,
~djc[/QUOTE]

I think that the backports proyect started as a community driven effort, so everyone wanting to offer a hand should be welcomed. If I had good scripting abilities to help here I would post a scritp, but I don't. I don't know how, althought I think it shouldn't be difficult to do. A cron job, which reads the packages names from a list, checks for newer version in the development tree, grabs the source, builds it and puts it on the staging tree so backports people can test it.

The only thing I see that can't be automated, is the testing of the backport package, since AFAIK all backports are first in staging (as just backported, but not tested) and there the team test it's stability (a human effort).

Maybe people that do backports on their own (like tamir with amd64) could help.

---

