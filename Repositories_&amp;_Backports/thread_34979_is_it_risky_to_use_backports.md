---
title: "is it risky to use backports?"
date: 2005-05-17
forum: Repositories &amp; Backports
---

### Post by ruben_b on 2005-05-17
hi

i´m using the universe and multiverse repositories in my source.list as well as the marillat repository. but i have read a few times, that the marillat reps aren´t that good for ubuntu.

but i don´t know anything about backporting ubuntu. 
is it less risky then using marillat? 
who creates this backports? 
are the updated regularly?
can i use the backport repositories even if i allready used some packages from marillat?

thanks in advance

---

### Post by l.tambiah on 2005-05-17
I would say its a matter of choice, but just be aware that the backports are not officially supported by the Ubuntu team. Backports are supported by the community you can add them to your sources.list. 

The backports url can be found at [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org).

 I use the backports on my distro and i havent had any problems as of yet, so this could suggest that the use of the backports is viable. 

Why the need for backports? Well Ubuntu release a distro but do not plan to give you new updates to products. So if you dont use backports in Hoary you will still have a firefox 1.02 version for example, even though 1.04 is out now. Ubuntu will patch the 1.02 in terms of security patches but you will not get any new features if any are added. If you want the bleeding edge and latest release then use the backports, if you do you will have the latest firefox 1.04.

Add the following to your sources.list

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

I do not use universe or multiverse though on the backports, so my list looks like:

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main restricted

Hope this helps....

---

### Post by ruben_b on 2005-05-17
why aren´t you using universe/multiverse?
will all my packages getting updated with the packages from the backport repository if i add it to my list? i´d like to allways have the newest packages of a programm so i think the backports a good for me.

---

### Post by Burgundavia on 2005-05-17
The major issue with backports is that of upgrading to the next version. When you do so, expect so see some issues.

Corey

---

### Post by 23meg on 2005-05-17
[QUOTE=Burgundavia]The major issue with backports is that of upgrading to the next version. When you do so, expect so see some issues.

Corey[/QUOTE]

you should make a list of which applications you upgrade using backports, and before doing a dist-upgrade to breezy when the time comes, downgrade them. theoretically you shouldn't have any issues this way.

---

### Post by jasplund on 2005-05-17
Is it possible to see in synaptic which packages have been upgraded or installed through backports?

---

### Post by harryc on 2005-05-17
Yes, just do a custom search for ubp in the version name.

---

### Post by jasplund on 2005-05-17
[QUOTE=harryc]Yes, just do a custom search for ubp in the version name.[/QUOTE]

Ok that's great. Then there's no reason to keep a list of packages installed from the backports.

---

### Post by harryc on 2005-05-17
[QUOTE=jasplund]Ok that's great. Then there's no reason to keep a list of packages installed from the backports.[/QUOTE]That is true.

---

