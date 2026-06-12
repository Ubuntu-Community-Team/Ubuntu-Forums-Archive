---
title: "Running out of space in /boot"
date: 2015-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by SeijiSensei on 2015-05-18
Lately we've seen a spate of postings from people running out of space in /boot because they have a large number of stale kernels and associated files.  I reported this as a bug a year or two ago and was told by the developers that they had fixed the management of kernels so that only the current and previous one are retained.  Yet in the past couple of weeks at least half-a-dozen people have posted about having a full /boot partition, and usually they have quite a few stale kernels that were never removed.

Autoremove handles this problem to a degree, but if there are many outdated kernels it usually fails to identify and remove them.

This sudden flurry of reports makes me wonder if something changed in a recent update that has caused Ubuntu to start leaving behind stale kernels that it would have otherwise deleted.  Any ideas?

---

### Post by v3.xx on 2015-05-18
I see the problem with a boot partition.  I know that a bug is long standing for this.

---

### Post by ajgreeny on 2015-05-18
I have also noted a lot more of these thread types recently and believe this must be a result of the option either for encryption or to use LVM, which is much more obvious in the installer now than I ever remember it being in the past.

I think a lot of new users are choosing one or other of those without realising the implications of doing so, thus automatically getting a /boot partition of 250MB (I think), sufficient only for about 4 kernels, which is very quickly exceeded in normal updates these days.

Perhaps there should at least be some sort of warning about this possibility should  users choose encryption or LVM when they install Ubuntu; we might then see a reduction in the number of threads similar to the ones SeijiSensei is talking of here.

---

### Post by coffeecat on 2015-05-18
> **SeijiSensei said:**
> I reported this as a bug a year or two ago and was told by the developers that they had fixed the management of kernels so that only the current and previous one are retained.

I'm fairly sure that every one of my Ubuntu systems over the last few years - a fresh installation usually every 6 months when the new version comes out - has amassed a significant number of kernels by the time 6 months is up. My abandoned Utopic system, which was only a couple of months old, has 5 kernels in situ.

Do you have a link to the bug report you mention? This is a more recent one which unfortunately hasn't attracted enough heat yet:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

---

### Post by SeijiSensei on 2015-05-18
> **coffeecat said:**
> Do you have a link to the bug report you mention? This is a more recent one which unfortunately hasn't attracted enough heat yet:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

Turns out I posted a comment to [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690911](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690911).

Launchpad really has a difficult-to-navigate interface.  I cannot get it to list all my reports or comments.  I just keep getting the "no open bugs" response.  Any hints on how I can see every posting I've made at bugs.launchpad.net regardless of the status of the bugs involved?  I've tried checking all the boxes like "WontFix" on the Advanced Search page, but the search still comes up empty.

> **ajgreeny said:**
> I have also noted a lot more of these thread types recently and believe this must be a result of the option either for encryption or to use LVM, which is much more obvious in the installer now than I ever remember it being in the past.

I think a lot of new users are choosing one or other of those without realising the implications of doing so, thus automatically getting a /boot partition of 250MB (I think), sufficient only for about 4 kernels, which is very quickly exceeded in normal updates these days.
I know LVM is an option on server installs.  Is it also offered for desktop installations?  That makes no sense and is just asking for trouble.  Ordinary users don't need LVM and would be confused about how to manage the volumes.

---

### Post by grahammechanical on 2015-05-18
> Is it also offered for desktop installations?

Yes. And I can see some purpose to offering to encrypt the new installation but not to offer LVM on a machine with one hard disk. It might be useful on a machine with an SSD and a hard disk and only Ubuntu on it. I do not know much about LVM.

I did see one post where the OP accepted encryption and then promptly forgot the password and so could not unlock the file system to use Ubuntu. What is the point of a security system if you can go on a web site and be told how to bypass security?

A practical solution would be for the installer to create a larger /boot partition then it is at presently doing.

Regards.

---

### Post by Erik1984 on 2015-05-18
I have to manually run apt-get autoremove once in a while to prevent /boot from filling up (for no good reason I went with a 500 MB partition for /boot). Have to say that apt-get is nice and tells me when there are obsolete packages to remove. Also that autoremove is doing a good job when removing old kernels. So the mechanism seems to be working but you have to push the button yourself.

---

### Post by coffeecat on 2015-05-18
> **grahammechanical said:**
> 
A practical solution would be for the installer to create a larger /boot partition then it is at presently doing.


Indeed. This is the focus of the bug I linked in post #4. If you could pass the word around on that bug so that more people mark it as affecting them too, it might actually get noticed by those that need to notice it. Thanks.

---

### Post by bapoumba on 2015-05-18
@SeijiSensei : log into LP > go to your user (or anyone else's) > bugs > on the right, commented bugs. The only one I see related to the /boot partition filling up is the one you liked to.

I suppose increasing the default /boot size partition, or setting up an alert when it fills up (not sure this is possible or practical) is material for the devel list if anyone here has the right to post there, or devel-discuss if not.

---

### Post by ian-weisser on 2015-05-18
Looking through /etc/apt.conf.d/,
Looks like autoremove should be run automatically by /etc/apt/apt.conf.d/50unattended-upgrades , provided by the unattended-upgrades package, IF you have changed the switch on line 46.

At some point in the past, I installed that package, and apparently turned unattended-autoremove on (I would do that). And my kernels seem maintained properly.

If you have too many kernels, do you have the unattended-upgrades package installed?
If so, in /etc/apt/apt.conf.d/50unattended-upgrades , is line 46 ('Unattended-Upgrade::Remove-Unused-Dependencies "true";') active or commented out?

---

### Post by Erik1984 on 2015-05-18
Didn't know about that file. Line 46 is indeed commented out. Think I'll keep it that way but it's good to know that cleaning up obsolete kernels can be performed automatically.

---

### Post by monkeybrain20122 on 2015-05-18
Fedora automatically removes the oldest kernel whenever there is a kernel upgrade (default is to keep only the latest two and delete the third, but that can be customized by editing some config file). Ubuntu should implement something like this instead of expecting inexperienced users to run autoremove manually.

---

### Post by ian-weisser on 2015-05-18
> **monkeybrain20122 said:**
> Ubuntu should implement something like this instead of expecting inexperienced users to run autoremove manually.

I think Ubuntu did that. The developer's intent seems to be autoremoval of old kernels without pestering the user, and it does seem to work for most users. I think the lack of autoremove under some conditions (including separate /boot partition) is a bug or bugs.

So far, I don't see that anybody has triaged this bug and successfully identified a culprit...which makes me suspect that the cause might be a subtle or complex bug.

---

### Post by monkeybrain20122 on 2015-05-18
> **ian-weisser said:**
> I think Ubuntu did that. The developer's intent seems to be autoremoval of old kernels without pestering the user, and it does seem to work for most users. I think the lack of autoremove under some conditions (including separate /boot partition) is a bug or bugs.

So far, I don't see that anybody has triaged this bug and successfully identified a culprit...which makes me suspect that the cause might be a subtle or complex bug.

This is new for me. Old kernels do show up in "autoremove" section in synaptic but nothing get actually removed until I run the command. I am using ext4 file system with no encryption. I have separate / and /home but don't have a /boot partition (never know why I would need one) I have the same setup in Fedora, running yum update in either command line or Yumex (kind of like synaptic) would automatically remove the oldest kernel if there is a kernel update.

---

### Post by ian-weisser on 2015-05-20
Bug in unattended-upgrades that is supposed to run autoremove: [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1267059](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1267059)
...aside from it not being turned on at all.

---

