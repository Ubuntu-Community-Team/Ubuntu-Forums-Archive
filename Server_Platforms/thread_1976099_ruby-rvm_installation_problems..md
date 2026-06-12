---
title: "ruby-rvm installation problems."
date: 2012-05-08
forum: Server Platforms
---

### Post by Cheesemill on 2012-05-08
I'm trying to set up a Ruby on Rails development server, the first step of which is to install Ruby Version Manager. I know that this can be done using the instructions on their site [here]("https://rvm.io/rvm/install/") but I'm trying to stick with packages from the repositories.

I get the following error when trying to install ruby-rvm:
```
The following partially installed packages will be configured:
  ruby-rvm 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up ruby-rvm (1.6.9-0ubuntu2) ...
dpkg-statoverride: error: syntax error: unknown group 'admin' in statoverride file
dpkg: error processing ruby-rvm (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ruby-rvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ruby-rvm (1.6.9-0ubuntu2) ...
dpkg-statoverride: error: syntax error: unknown group 'admin' in statoverride file
dpkg: error processing ruby-rvm (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ruby-rvm
```

Any ideas would be welcome please. System is a fresh 12.04 64-bit server install running as a VMware Workstation virtual machine.

---

### Post by rubylaser on 2012-05-08
I'd really suggest you use the directions from the site.  This will automatically checkout the latest stable version from GIT and can be easily maintained by the developer of RVM.  I've never even bothered using the repos for RVM.

---

### Post by Cheesemill on 2012-05-08
Thanks for the info, that was going to be my next step.

---

### Post by Hrosicrucian on 2012-07-09
The fix at the bottom of this thread solved my problem.

[https://bugs.launchpad.net/ubuntu/+source/ruby-rvm/+bug/963662](https://bugs.launchpad.net/ubuntu/+source/ruby-rvm/+bug/963662)

good luck!

-Chris

---

### Post by rubylaser on 2012-07-09
> **Hrosicrucian said:**
> The fix at the bottom of this thread solved my problem.

[https://bugs.launchpad.net/ubuntu/+source/ruby-rvm/+bug/963662](https://bugs.launchpad.net/ubuntu/+source/ruby-rvm/+bug/963662)

good luck!

-Chris

Thanks for the post:)  It's good to know this can be made to work properly.  I just find installing RVM via the developer's  site work really well and are so simple to follow, I've never seen the point to deviate from that path.

---

