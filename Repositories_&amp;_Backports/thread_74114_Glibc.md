---
title: "Glibc?"
date: 2005-10-10
forum: Repositories &amp; Backports
---

### Post by Metal Militia on 2005-10-10
setup.gtk failed to start?
DISPLAY: :0.0
Do you need to issue an xhost + command to let root access X11?
The setup program seems to have failed on x86/glibc-2.1


That was the error message I got when trying to install a program (GTKRadiant - Map Editor)
Someone help please?

*Sorry if this is in the wrong section :/*

---

### Post by mlomker on 2005-10-10
I add this command to my ~/.bashrc file:

```

xhost local: > /dev/null 2>&1

```

That'll allow any local user to use the X session.

---

### Post by Metal Militia on 2005-10-10
Lol sorry forgot to mention im a total noob :P

i typed ~/.bashrc while rooted and got this:

bash: /root/.bashrc: Permission denied

---

### Post by mlomker on 2005-10-10
You can edit the file from a command-line using nano:

```

nano ~/.bashrc

```

Change what you want to and then Ctrl-W, Y, and Enter to save the file.  The changes won't take effect at your terminal prompt until you close and re-open a new one.

Here's a nice [shell introduction]("http://linuxcommand.org") for when you have some time.

---

### Post by Metal Militia on 2005-10-10
xhost local: > /dev/null 2>&1
is already in ~/.bashrc at the bottom, twice..

according to a couple other people, my problem is that my version of glibc is too old..  could that be the problem maybe?

Thanks for the help btw..

---

### Post by mlomker on 2005-10-11
> according to a couple other people, my problem is that my version of glibc is too old..  could that be the problem maybe?


I don't know--that must be a problem with the program that you are installing and not xhost.  If it is something that you are compiling then the author usually provides a README file with a list of dependencies for the program.

You cannot update glibc--it'll fry your system.  If you are running Hoary then you could upgrade to Breezy and give it another try--Breezy's version is newer.

---

### Post by Metal Militia on 2005-10-11
Im already on breezy, but thanks for the help anyways, i guess ill have to live without the program :P.

---

