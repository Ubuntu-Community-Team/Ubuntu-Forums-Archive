---
title: "VirtualBox Installation Problem"
date: 2008-05-01
forum: Virtualisation
---

### Post by dlobo on 2008-05-01
Hi,

I have tried to install VBox from ubuntu repositories on Hardy and I got an error that said "can't open /etc/init.d/functions".
I checked that location and the functions file does not exist.
In the end VBox is installed but it's unusable. I would like to re-install it but when I try to uninstall first I get the following error message:
****
E: virtualbox-ose: subprocess post-installation script returned error exit status 2

Removing virtualbox-ose-modules-2.6.24-16-generic ...
dpkg - warning: while removing virtualbox-ose-modules-2.6.24-16-generic, directory `/lib/modules/2.6.24-16-generic/misc' not empty so not removed.
Setting up virtualbox-ose (1.5.6-dfsg-6ubuntu1) ...
.: 60: Can't open /etc/init.d/functions
invoke-rc.d: initscript virtualbox-ose, action "start" failed.
dpkg: error processing virtualbox-ose (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 virtualbox-ose
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
****

Again the same functions file missing.
Now I am stuck with a half installed virtualbox that I cannot finish to install nor I can remove.
I was thinking that if anyone had that functions file and could paste it here I could go and create it manually on my machine. I know this sounds a little to drastic, so any other ideas are welcome.

Thanks a lot

dmlobo

---

### Post by Sukarn on 2008-05-01
I have virtualbox-ose installed and running fine on my system, and I do not have the file /etc/init.d/functions

Something's weird on your system.

---

### Post by reiki on 2008-05-01
Just FYI...
The OSE version does not have USB support. If you want USB support you need to go to Virtualbox web site and download from there. There is a .deb for Gutsy that works just fine on Hardy (I'm using it).

As to the OP's problems.... I've not encountered that error and it does sound like more of a system problem than a vbox problem, but of course I could be wrong about that.

---

### Post by dlobo on 2008-05-01
I just found out what the problem was. It's in this link:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/224836](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/224836)

I have a file in /etc called redhat-release. So when I was installing VBox it thought it was installing on redhat therefore it needed that functions file.
I created redhat-release file when I installed Oracle 11g a few months back on 7.10.
I renamed the file and re-install VBox and everything is working fine.

Thanks a lot for your responses

---

### Post by unc0nn3ct3d on 2008-06-04
Yup, was having the same problems here, got rid of the redhat file and everything is kosher.. Thanks for posting the solution!

---

### Post by rschauer on 2011-07-12
> **dlobo said:**
> 
I have a file in /etc called redhat-release. So when I was installing VBox it thought it was installing on redhat therefore it needed that functions file.
I created redhat-release file when I installed Oracle 11g a few months back on 7.10.
I renamed the file and re-install VBox and everything is working fine.


I know this is a super-ancient thread; please forgive my necromancy. I just wanted to say thanks for this, and to point out that it's still a relevant issue under 10.04 / VBox 4.0. I had this exact same problem (for the same reason, having installed 11g), and renaming the redhat-release file fixed it.

Amazing that Oracle software relies on such weak methods of determining the OS it runs on; wouldn't a simple `uname` command in the install script be better? Of course, that would be harder to work around for us Ubuntu users. :-P

---

### Post by chncho on 2012-01-10
> **dlobo said:**
> I just found out what the problem was. It's in this link:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/224836](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/224836)

I have a file in /etc called redhat-release. So when I was installing VBox it thought it was installing on redhat therefore it needed that functions file.
I created redhat-release file when I installed Oracle 11g a few months back on 7.10.
I renamed the file and re-install VBox and everything is working fine.

Thanks a lot for your responses
:popcorn::D:D:D,thanks!
My problem is the same to you!!!

---

