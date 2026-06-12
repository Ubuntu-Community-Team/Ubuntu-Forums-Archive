---
title: "convention adding /etc/ files under version control"
date: 2009-12-28
forum: Server Platforms
---

### Post by manolo_asdf on 2009-12-28
hi,

a lot of brains is put to /etc configuration files, so i am thinking to add them to version control system (subversion). is this common, is there a common convention of using scm for operating system configuration files?

thanks!

---

### Post by Gourgi on 2009-12-29
take a look also at etckeeper [http://joey.kitenet.net/code/etckeeper/](http://joey.kitenet.net/code/etckeeper/)
i don't use it (i don't use any revision under etc) but i've seen some good blog posts/guides about it.

> etckeeper is a collection of tools to let /etc be stored in a git, mercurial, darcs, or bzr repository. It hooks into apt (and other package managers including yum and pacman-g2) to automatically commit changes made to /etc during package upgrades. It tracks file metadata that revison control systems do not normally support, but that is important for /etc, such as the permissions of /etc/shadow. It's quite modular and configurable, while also being simple to use if you understand the basics of working with revision control.

---

### Post by Lars Noodén on 2009-12-29
It's not uncommon to use version control for configuration files for large sites.  Pick the version control system you want, then make a branch or project or whatever the version control system calls it.  

Once you have committed your changes to the version control system, then you can check out the changes to the other machines.  If you are using the same files for many machines you will have to fiddle with some of them a little to make sure that they are generic enough to work on all the machines.  I often have trouble with host_aliases in /etc/sudoers.

Another option is to use [radmind](http://rsug.itd.umich.edu/software/radmind/), which allows exceptions to configurations.

---

### Post by manolo_asdf on 2009-12-30
thanks for suggestions. etckeeper looks good, i'll see whether it abstracts stuff more away as me using an own svn-repository. what i don't like about etckeeper is that initiates commits during package upgrade, which aren't run so often in my case... maybe i will setup an own repository and do the commits with a cron-job (so i backup forgotten commits to svn).

in my case it would be only for one machine. the main reason i need it is for backup (don't want to lose accidently overridden configs) and tracking.

---

