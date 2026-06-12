---
title: "Is this informatio true?"
date: 2011-01-22
forum: Security
---

### Post by nictu on 2011-01-22
Hi,

I;m trying to get my computers, ubuntu and windows as secure as possible.
I came across the following link and wondered if the information contained on that website is true?
Here is the link;

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

I would really appreciate any help in securing my ubuntu machine. 
Many Thanks,
nictu.

---

### Post by rookcifer on 2011-01-22
> Reconfiguring shared memory
Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:
tmpfs /dev/shm tmpfs defaults,ro 0 0

This one's debatable.  If you feel you must do it, then that's fine.  I can't see where it helps a desktop machine, though.

> Disabling SSH root login
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:
PermitRootLogin yes

to

PermitRootLogin no

Not necessary because there is no SSH server running by default, and even if there were, Ubuntu does not have a root account enabled in the first place.

> Limiting access to the "su" program
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su

Not necessary since the root account is locked by default.

The rest of that site is pretty much misguided or out of date (i.e., they don't know what they're talking about).  For instance they say this:

> To keep your computer secure, install the following software:

grsecurity - A complete security suite for protecting Linux's kernel.
PaX - The most critical piece of grsecurity, prevents memory exploits. (Comes standard with grsecurity, you only need to install this if you have no intention of installing grsecurity.)
Pro Police - IBM's solution for protecting against stack smash attacks.
DigSig - Verifies the integrity of executables via user defined digital signatures before running it. If a program is modified without your consent the digital signature changes and DigSig denies the program the ability to run.


LOL.  Who are they kidding?  Running PaX and Grsecurity is not as simple as "installing them."  You have to recompile the kernel and then configure them to get them to work.  It is a major PITA.  These security mechanisms (known as MAC's and RBAC's) are complete overkill for a desktop machine.  If you're running a server farm for a Fortune 500 company, then sure, it might be OK to run PaX/Grsec.  Otherwise don't bother.  Besides, Ubuntu already has its own MAC -- AppArmor.  And Pro Police already comes with the kernel (or at least a technology very much like it).

The only thing you need to do to stay safe is install all updates when prompted and only install software from the official repositories (that is do not install .debs from anywhere outside of the Ubuntu software center).

---

### Post by bodhi.zazen on 2011-01-22
> **rookcifer said:**
> <clip> ... that site is pretty much misguided or out of date (i.e., they don't know what they're talking about).</clip>

I think that site is nothing short of FUD.

That information is written by someone who is unfamiliar with Ubuntu and I would direct you to more credible sources of information such as the security sticky at the top of this page or the official Ubuntu documentation.

I would not take security advice from anyone who makes such obvious mistakes and who is obviously unfamiliar with Ubuntu.

---

### Post by HermanAB on 2011-01-23
Howdy,

With a default Ubuntu install, there are only two things that you should look out for:
1. Always use passwords >8 characters with complexity or >12 characters without complexity for all accounts.
2. Do not play with VNC.  It is a sure way to get your machine compromized.

---

### Post by nictu on 2011-01-24
Many thanks people,

I had a feeling that site wasn't quite right, but I am no expert

Thanks again,
nictu

---

