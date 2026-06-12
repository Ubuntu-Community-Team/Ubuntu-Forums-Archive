---
title: "Rubyripper depends on Mousepad"
date: 2014-05-27
forum: Ubuntu Studio
---

### Post by Charlotte18 on 2014-05-27
Does anyone know why Rubbyripper 0.6.2 has to have Mousepad, Gedit, or Kwrite installed?

---

### Post by bapoumba on 2014-05-28
Where are you getting it from ?
Looks like the project wont be maintained anymore and latest release was Dec 2011 : [https://code.google.com/p/rubyripper/](https://code.google.com/p/rubyripper/)
As to "why" it needs a text editor as a dependency, I have not real idea. May be as a dep from a language pack or another desktop package ?
[http://wiki.hydrogenaud.io/index.php?title=Rubyripper](http://wiki.hydrogenaud.io/index.php?title=Rubyripper)

---

### Post by vasa1 on 2014-05-28
And there's an old thread here: [http://ubuntuforums.org/showthread.php?t=799621](http://ubuntuforums.org/showthread.php?t=799621)

From the second link bapoumba provided, it appears to work with CLI or GTK**2**! [s]As of now, gedit is gtk2[/s] and kate is kde; I think mousepad is still gtk2 (apt-cache show mousepad).

Edit: that should be *As of now, gedit is gtk3*.

---

### Post by bapoumba on 2014-05-28
Thanks vasa, I hesitated to link to this thread because I was not sure the info was still relevant :)

---

### Post by mc4man on 2014-06-01
It's not a required dep & RR will run, work just fine in the absence of any text editor it 'supports'
The use of an editor comes at the conclusion of a rip, there are 2 **options** presented - Open log file & Open directory

For Open log file it needs a text editor it can discover, otherwise you need to set one in Preferences > Other > obvious *if you wanted to use that post rip option*

---

### Post by Charlotte18 on 2014-06-03
I'm not sure how to remove Mousepad since both apt-get and aptitude want to remove Rubyripper (or to install Gedit or Kwrite) whenever I try to remove Mousepad.

---

### Post by mc4man on 2014-06-04
> **Charlotte18 said:**
> I'm not sure how to remove Mousepad since both apt-get and aptitude want to remove Rubyripper (or to install Gedit or Kwrite) whenever I try to remove Mousepad.
Where did you get a RR package that depends on a text editor?
(- At best it should of only been a recommend or suggest

---

### Post by Charlotte18 on 2014-06-04
> **mc4man said:**
> Where did you get a RR package that depends on a text editor?
(- At best it should of only been a recommend or suggest

[http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/rubyripper](http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/rubyripper)

But isn't there a way to tell aptitude or apt-get to ignore dependencies?

---

### Post by bapoumba on 2014-06-04
> **Charlotte18 said:**
> [http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/rubyripper](http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/rubyripper)

But isn't there a way to tell aptitude or apt-get to ignore dependencies?

This package in this ppa does depend on gedit/kwrite/mousepad. It is the package manager job to ensure all dependencies are satisfied. Is thee another repository you can get Rubyipper from that would not have these deps ?

---

### Post by Charlotte18 on 2014-06-04
The only other one I could find is here and stops at saucy:

[https://launchpad.net/~brandonsnider/+archive/ruby-ripper](https://launchpad.net/~brandonsnider/+archive/ruby-ripper)

Actually, I was able to install and use this version in 14.04, and it appears to be the same version number. So maybe I should go back to that one.

---

### Post by mc4man on 2014-06-05
I keep a build here for 14.04 noting that there are quite a number of media packages. Everything in there has been tested by me to some extent, you are not obliged to upgrade all or anything other than something of interest.

[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

---

### Post by bapoumba on 2014-06-05
Thanks mc4man :)

---

