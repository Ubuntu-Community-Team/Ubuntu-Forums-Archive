---
title: "Problem installing syslog-ng on Gusty 7.10"
date: 2007-11-26
forum: Server Platforms
---

### Post by martoq on 2007-11-26
I am an old Mandrake/Mandriva user and this is one of my first endevours into Ubuntu so if this is a basic question I do apologize.

I am attempting to install syslog-ng to satisfy a dependency.  Unfortunately I am having very little success in the matter.  

From everything I have read, I am confused.  From what I have seen I should be able to install this no problems, but then I have also read that this is a bug with the packaging and what it depends on.  

Any help would be GREATLY appreciated.

#################

wan@testsrv:~$ sudo apt-get -f install syslog-ng
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  syslog-ng: Conflicts: system-log-daemon
             Conflicts: linux-kernel-log-daemon
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by gg234 on 2007-11-29
try to remove sysklogd first and then install syslog-ng

sudo apt-get remove sysklogd

Now install syslog-ng using the following command

sudo apt-get install syslog-ng

Let me know if this works or not

---

