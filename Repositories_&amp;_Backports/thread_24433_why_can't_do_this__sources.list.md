---
title: "why can't do this  sources.list"
date: 2005-04-06
forum: Repositories &amp; Backports
---

### Post by amin_od on 2005-04-06
I try to get the backport. So I edit the sources.list as foolow:

deb [http://backports.ubuntuforums.org/backports/warty-backports ](http://backports.ubuntuforums.org/backports/warty-backports ) main universe multiverse restricted

Since I'm using hoary, I did try change warty-backports to hoary-backports as well. The error msg when reload using sypnaptic:


W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_warty-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)

What's going on here ?

 :-|

---

### Post by moopere on 2005-04-07
>deb [http://backports.ubuntuforums.org/backports/warty-backports](http://backports.ubuntuforums.org/backports/warty-backports) main universe multiverse restricted

The format above is incorrect.  It should be as follows:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main restricted universe multiverse

* Note that there is no '/' between backports and warty-backports, this is the key.

Cheers,
Craig

---

### Post by amin_od on 2005-04-07
Thanks, but still doesn't work. This is my /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

## non free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 


## backport 
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

And this is the error msg:

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


If I put a comment on the deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted  then the err.msg disappear.
 
Please noted that I did my upgrade from warty to hoary one application by one applications. Is there something missing that I don't upgrade ?

---

### Post by cdhotfire on 2005-04-07
Um if someone read what i posted earlier, dont shot me.=;

---

