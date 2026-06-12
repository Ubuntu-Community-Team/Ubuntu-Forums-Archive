---
title: "Package installation problem"
date: 2014-09-10
forum: Server Platforms
---

### Post by chriso0258 on 2014-09-10
Hello,

I just installed Ubuntu 12.04.5 LTS. When I run apt-get update I get a few messages saying failed to get bzip2 due to hash sum mismatch. Ok, no big deal. However, I'm trying to install a couple of packages such as phpmyadmin and webmin. When I type apt-get install apt-show-versions libapt-pkg-perl libauthen-pam-perl libio-pty-perl libnet-ssleay-perl I get 5 messages each saying that the package "has no installation candidate". Same with phpmyadmin.

When I installed these on a Ubuntu 12.04.3 server, I had no problems. What changed? Do I need to edit/add to the sources.list file? I have uncommented the last four items in the list. 

Thanks for your assistance.

As an update, I have tried installing webmin and then when it says it has errors I tried apt-get -f install as suggested on another site. This however only uninstalled webmin.

---

### Post by ian-weisser on 2014-09-10
I would revert to a working system - no PPAs, no non-Ubuntu software, package manager working without errors.

Then I would add each non-Ubuntu element, one by one, until you get the breakage.
Then you will know what the problem is.

To provide any more specific guidance, we would need to see the complete output of a terminal session showing the errors.

---

### Post by chriso0258 on 2014-09-11
Thank you for your reply. Here are the outputs from my two commands. 

Command: apt-get update (I won't list all the valid hits due to space, only the errors)

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe i386 Packages  404  Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en
Fetched 80 B in 8s (9 B/s)

W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages Hash Sum mismatch
W Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages Hash Sum mismatch

W Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/source/Sources) 404 Not Found [IP 91.189.91.15 80]
W Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/binary-i386/Packages) 404 Not Found [IP 91.189.91.15 80]
E Some index files failed to download. They have been ignored, or old ones used instead.

--------------------------------------------------------------------------
These are the dependencies for installing phpmyadmin.

Command: apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python
Reading package lists...
Building dependency tree...
Reading state information...
Package libio-pty-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libnet-ssleay-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package apt-show-versions is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libauthen-pam-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libnet-ssleay-perl' has no installation candidate
E: Package 'libauthen-pam-perl' has no installation candidate
E: Package 'libio-pty-perl' has no installation candidate
E: Package 'apt-show-versions' has no installation candidate

Any help would be greatly appreciated.

---

### Post by ian-weisser on 2014-09-11
> **chriso0258 said:**
> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe i386 Packages  404  Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en

[...]

W Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/source/Sources) 404 Not Found [IP 91.189.91.15 80]
W Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/univers/binary-i386/Packages) 404 Not Found [IP 91.189.91.15 80]


Edgy is not 12.04. Those entries have been obsolete for years. Delete those entries from your /etc/sources.list.

Open Software Center. Select the menu entry 'Software Sources'. Look for the sources tab. Delete or uncheck everything marked 'edgy'


> **chriso0258 said:**
> Command: apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python

Don't specify dependencies without a good reason.
Let the system figure out the dependencies. That's why you use package management.

I don't know where you got that instruction line from, but you are explicitly telling the system to install four packages that simply do not exist in the repositories, plus two packages it *already* has installed (python, perl).
I wouldn't trust those instructions.


Try:
```
sudo apt-get install phpmyadmin
```

---

