---
title: "Samba install failing on 12.04 server"
date: 2013-01-25
forum: Server Platforms
---

### Post by mcreef on 2013-01-25
Hey folks,

I am attempting to install Samba on a freshly built 12.04 server, but am having some trouble that I can't seem to work out, perhaps you can help me?

I have installed Ubuntu 12.04 with the 3.2.0-29-generic kernel on a system made up of a Supermicro X9SCM-IIF-O motherboard with an Intel Xeon 1230V2 processor and 16GB of RAM.

I am by no means an expert, and had some trouble getting the install to take, but was able to work that out eventually with a little bit of persistence and a lot of google searching. The final install went fairly smoothly in the end, but now I can not seem to figure out where I am going wrong.

I have run sudo apt-get update, and sudo apt-get dist-upgrade, and all seems to go smoothly with no errors.

I have tried installing with -f and using aptitude, and no luck.

It seems my problem is an issue of dependencies, but I am not sure how to rectify the problem. Here are the last few lines that list the errors I get...

The following packages have unmet dependencies:
  samba : Depends: libcap2 (>= 2.10) but it is not installable
                Depends; libcups2 (>= 1.4.0) but it is not going to be installed
                Depends: libtalloc2 (>= 2.0.4~git20101213) but it is not installable
                Depends: libtdb1 (>= 1.2.7+git2010214) but is not installable
                Depends: update-inetd but it is not installable
                Depends: samba-common-bin
                Recommends: tdb-tools but it is not installable
E: Unable to correct problems, you have held broken packages.

Any ideas?

---

### Post by tgalati4 on 2013-01-25
You mean you should have run:

```
sudo apt-get update
sudo apt-get upgrade
```

By running dist-upgrade you upgraded to 12.10.  So you have a system of 12.04 and 12.10 parts.

Post the output of:

```
cat /etc/issue
uname -a
lsb_release -a
```

If this is the case, then I suggest you start again and don't use dist-upgrade.

Now, do you really have a SAMBA problem?

---

### Post by mcreef on 2013-01-28
> **tgalati4 said:**
> You mean you should have run:

```
sudo apt-get update
sudo apt-get upgrade
```

By running dist-upgrade you upgraded to 12.10.  So you have a system of 12.04 and 12.10 parts.

I tried this first, but also tried dist-upgrade afterwards in my attempts to figure out how to fix the issue. The Samba install was failing prior to me running dist-upgrade.

I guess I screwed up there, I was wary of using that command, as I have no desire to move away from the LTS version. After some reading and searching around, I had developed the impression that dist-upgrade would not move me away from precise, but rather just install the updates, and that do-release-upgrade was the command I wanted to stay away from.

> **tgalati4 said:**
> Post the output of:

```
cat /etc/issue
uname -a
lsb_release -a
```If this is the case, then I suggest you start again and don't use dist-upgrade.

Here you go...

Ubuntu 12.04.1 LTS \n \1

Linux <My Machine Name> 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 17:03:23 UTC 2012 x86 64 x86_64 x86_64 GNU/Linux

No LSB Modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04.1 LTS
Release: 12.04
Codename: precise

> **tgalati4 said:**
> Now, do you really have a SAMBA problem?

I was working under the assumption that it was not a problem with Samba, but rather I had made an error in my install. Specifically, I was thinking perhaps I had either chosen the wrong kernel, or perhaps I should not have selected to install the "targeted" driver package option.

I am learning as I go here...

Thanks for the help, I appreciate it.

---

### Post by mcreef on 2013-01-28
So I reinstalled, and Samba now installs without issue.

My thinking is that my root issue was that I made some mistakes during the first install of Ubuntu, and this led to my trouble getting Samba loaded on the machine.

I don't really know what specifically I messed up, but it is working now, so I'll mark this as solved I guess.

---

