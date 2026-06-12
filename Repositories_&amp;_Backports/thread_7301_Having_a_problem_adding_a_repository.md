---
title: "Having a problem adding a repository"
date: 2004-12-05
forum: Repositories &amp; Backports
---

### Post by Darrena on 2004-12-05
I am certain that I am doing something wrong but I can't figure out what!   :confused: 

I am trying to add this repository so I can get Firefox 1.0x

[http://www.ubuntulinux.org/wiki/MarkusHubig](http://www.ubuntulinux.org/wiki/MarkusHubig)
Here is what I added to my sources.list:
## some updated warty packages from Markus Hubig
deb [http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu](http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu) warty-updates main universe
deb-src [http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu](http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu) warty-updates main universe 

When I start up synaptic I get the following error:
Couldn't stat source package list [http://www.stud.uni-karlsruhe.de](http://www.stud.uni-karlsruhe.de) warty-updates/main Packages (/var/lib/apt/lists/www.stud.uni-karlsruhe.de_%7eut8g_ubuntu_dist_dists_warty-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

I get similar errors for both the source and binary.  

I can reach the repository manually fine, but I can't reach it with apt-get or synaptic.  


What did I do wrong?  

Thank you!   :smile:

---

### Post by Darrena on 2004-12-05
Mmmm  Well I added a trailing / to each line and then reloaded my package list and that did it!

Sorry about that!

---

### Post by stoneguy on 2004-12-05
I had that problem too awhile ago. Eventually I went to Markus' website, d/l'd his packages, and dpkg'd them into place locally.

However, today I went to get the current security updates in Synaptic. It failed because of a broken package. Eventually (I couldn't figure out how to make the filters work) I saw that it was bitching about the (newer) firefox-dev. Since I was stuck, I figured I'd opt for the reinstall and see what happened. Turns out that some kind soul relented about not upgrading to Firefox 1.0 (or maybe a security bug popped up and 0.93 was decomissioned) and put it in the base warty repostitory. So should be able to get Firefox 1.0 next time you upgrade.

BTW, adding the trailing / was something I tried that didn't work. Another mystery.

---

