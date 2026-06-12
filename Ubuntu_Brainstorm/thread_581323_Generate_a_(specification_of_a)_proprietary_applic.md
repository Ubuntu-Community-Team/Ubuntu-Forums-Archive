---
title: "Generate a (specification of a) proprietary application manager"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by FSHero on 2007-10-19
I have a rather bold move: I think it would be a good idea to create a manager for installing/uninstalling proprietary applications. Allow me to elaborate...

I admit that I have no experience of installing proprietary applications on my Kubuntu box except through Adept package manager. However, I have looked at two applications: Skype and Adobe Flash player. (Note: the latter can be installed through the Ubuntu repositories.)

The former comes as a Debian package, but the latter does not (it comes as a .tar.gz, which some people may find difficult to install). Both would require installation as a root user

I believe that some sort of specification should be released by the GNU/Linux community, which proprietary application writers could follow. In my opinion, there should be a package manager, so that programs can be installed and uninstalled cleanly. (No remaining program files, any kernel modules removed, etc.) Then, it would make installation and uninstallation of such programs consistent and easy for the end-user.

There are further benefits to this method, if implemented as a package manager. If an installer is run with root user privileges, then it can do anything it wants: including delete system files, modify system files and scripts, and add background processes that could affect the security and stability of the system.

Such a proprietary application manager could do a 'test run' to ascertain the effects of an installation. Then, the user could install the program proper. By default the proprietary application manager would prevent the modification of essential files such as /etc/apt/sources.list and /etc/X11/xorg.conf, prevent the running of binaries on starting the computer, and so on.

'Good' proprietary applications could conform to a "safe-install specification", which would show no dangers during a test run of the installation (verified by the computing community), as well as guaranteeing a clean removal if uninstalled by the proprietary application manager.

The proprietary application manager could be used to install proprietary drivers that are not in the Ubuntu repositories. It could be used to prevent installers  doing more than they are supposed to. (See: [http://it.slashdot.org/it/07/07/18/0319203.shtml](http://it.slashdot.org/it/07/07/18/0319203.shtml) for a description of how a Samsung printer driver installer allowed Openoffice.org binaries to run as root (I think).)

I think the FOSS community needs to have some way of keeping proprietary drivers and programs in check, so that GNU/Linux doesn't become like Windows with tons of security flaws which may not be intrinsic to the operating system itself, but due to bad drivers and programs being run.

Disclaimer: I am not educated in computer science or programming in any way; I am a home user who happens to be interested and knows a bit about GNU/Linux. Hence, what I might have said above could be total rubbish, or be redundant!

---

### Post by Zdravko on 2007-10-20
Hmm. This is a complicated case. Can you explain what you want in a few words?

---

### Post by smartboyathome on 2007-10-20
I think that, since AT LEAST 50% of the Linux community, if not more, uses Ubuntu, the vendors should compile a debian binary package, and then have a repo with the package in it and the only way to get the repo is by paying for a key to that repo. Then, they could do "upgrades" to a package containing the new key for that repo, so it would be harder for people to get in.

---

### Post by Zdravko on 2007-10-21
[smartboyathome]("http://ubuntuforums.org/member.php?u=264712"), nice idea.

---

### Post by FSHero on 2007-10-22
> **Zdravko said:**
> Hmm. This is a complicated case. Can you explain what you want in a few words?

I can only give you a few words, as I am short of time! ;)

Basically, to ensure that Ubuntu (as well as all GNU/Linux distros) maintain their reputation for stability and security, I think there should be some way of "locking down" proprietary applications.

Perhaps some sort of 'sandbox', or a strictly-regulated install process, would do the trick.

---

### Post by Choad on 2007-10-22
i still vote universal package manager. had this discussion ages ago, and it got nowhere. people just kept repeating the same thing even tho it made no sense.

there are MAJOR disadvantages to the idea of "universal linux", but there are ZERO disadvantages to having a universal package manager; that is to say, one single specification to which all linux distributions (that wish to) would adhere to, that could encorportate all/any of the features supported by current package managers. so long as it handles binary compatability, everything would be sweet. then third parties can just release 1 version, like they do for windows and mac.

---

### Post by Xbehave on 2007-10-22
most proprietary software simply needs you to read the readme, as it launches a file called install
also i think rpms are a good standard, perhaps a tool similar to alien is all thats needed
alternatively all useful programs could be added to the multiverse like flash is



* side note 
as for software that needs compiling perhaps a tool like kompile (for kde) would be usefull with a premade profile and a checkmake all installed via a meta-package like ubuntu-kompile

---

