---
title: "Sudo package updated? Or some kind of hack?"
date: 2008-09-12
forum: Security
---

### Post by Hendrik van den Boogaard on 2008-09-12
Today I found two of my servers having an update for the 'sudo' package. My own machine however does not propose this update (but has a AMD64 kernel opposed to the i386 kernels of the other machines). Because I was very curious about this particular update (and because my server hardly runs any packages so does not have updated security packages very often) I checked if there is any security issue on the security notices list ([http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)). Sudo is not listed.

Does anyone have a clue about this package? Is this a real update or is someone somehow trying to trick me into giving anyone root access (strange because you'd have to be root already to change /etc/apt/sources.list I assume).

[FONT="System"]root@asterisk:/tmp# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  sudo
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 176kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main sudo 1.6.9p10-1ubuntu3.3 [176kB][/FONT]

(I canceled the download above ;))

---

### Post by kostkon on 2008-09-12
> **Hendrik van den Boogaard said:**
> Today I found two of my servers having an update for the 'sudo' package. My own machine however does not propose this update (but has a AMD64 kernel opposed to the i386 kernels of the other machines). Because I was very curious about this particular update (and because my server hardly runs any packages so does not have updated security packages very often) I checked if there is any security issue on the security notices list ([http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)). Sudo is not listed.

Does anyone have a clue about this package? Is this a real update or is someone somehow trying to trick me into giving anyone root access (strange because you'd have to be root already to change /etc/apt/sources.list I assume).

[FONT="System"]root@asterisk:/tmp# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  sudo
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 176kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main sudo 1.6.9p10-1ubuntu3.3 [176kB][/FONT]

(I canceled the download above ;))
Do a
```
apt-cache policy sudo
```
to see if really there is a update and from where.

It may be offered by the *Proposed* repository. So, check in your *sources.list* file if you have this repo enabled on these two machines. If it is, better disable it.

---

### Post by unutbu on 2008-09-12
Run 
```

gksu update-manager
```
Select the sudo package.
In the bottom window under the 'Changes' tab you will see a short description of the reason for the update. There should also be a link. Click on the link and your web browser will take you to a page with more information.

Also, you can run 
```

apt-cache policy sudo
```

This will tell you what version you have installed, what version is being proposed (the candidate), and what is the repository that contains the upgrade.

---

### Post by Hendrik van den Boogaard on 2008-09-12
Ah, I didn't know that command. Nice. It's actually in the 'updates' repository. So probably not a security issue, but what can you update on sudo?

[FONT="Fixedsys"]sudo:
Installed: 1.6.9p10-1ubuntu3.2
Candidate: 1.6.9p10-1ubuntu3.3
Version table:
1.6.9p10-1ubuntu3.3 0
500 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy-updates/main Packages
*** 1.6.9p10-1ubuntu3.2 0
100 /var/lib/dpkg/status
1.6.9p10-1ubuntu3 0
500 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) hardy/main Packages[/FONT]

Not too many hits on that version on Google either. The 'changes' is also a bit vague:
[FONT="Fixedsys"]
* Enabled the lecture message, defaults to a message inform users that password will not echoed[/FONT]

---

### Post by unutbu on 2008-09-12
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Search for 'sudo' with the Distribution set to 'hardy-updates'.

You will find this page: [http://packages.ubuntu.com/hardy-updates/sudo](http://packages.ubuntu.com/hardy-updates/sudo)
On the right-side panel click on Changelog.

You will thus reach this page
[http://changelogs.ubuntu.com/changelogs/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3/changelog)
and
[http://www.gratisoft.us/bugzilla/show_bug.cgi?id=296](http://www.gratisoft.us/bugzilla/show_bug.cgi?id=296)
which explains the change.

---

