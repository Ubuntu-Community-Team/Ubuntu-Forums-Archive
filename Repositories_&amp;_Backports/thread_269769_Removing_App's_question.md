---
title: "Removing App's question"
date: 2006-10-02
forum: Repositories &amp; Backports
---

### Post by englishmen on 2006-10-02
I have just installed ubuntu on my PC(dual boot with XpPro)and before i look for new software to install i was going to go through the apps that come with ubuntu and remove ones i don't want. The problem im having is that when i attempt to un-tick a app. In this case evolution, i get a message saying

> 
Cannot remove "evolution"

One or more application depend on "evolution". To remove "evolution" and the dependant application, please switch to the advanced software manager.

I then started up the Synaptic Package Manager and searched for evolution right clicked and clicked "mark for removal"(can someone tell me whats the difference between mark for removal and mark for complete removal?). It then listed 3 thing that will be removed "evolution-package", "evolution-plugins" and "ubuntu-desktop". Why is it saying that ubuntu -desktop will also be removed, it sound like something i don't want to remove?

Thanks and go easy on me its my the first linux distro i have installed.

---

### Post by pay on 2006-10-02
You want ubuntu-desktop!!!! Without it you will only have the terminal! It looks like you can't remove evolution since it's built into Gnome. I think the difference between mark for removal and mark for complete removal is the latter removes the orphaned dependencies aswell (I'm not 100% on this since I've never used synaptic. It's too slow.)

---

### Post by englishmen on 2006-10-02
Thanks for the quick response pay, so there is no way to remove evolution?

I thought it was only Microsoft to make it so users cant remove apps they don't want?

---

### Post by az on 2006-10-02
Ubuntu-desktop is just an empty package.  It is a meta-package.  It exists to depend on other packages.

The package manager needs to use these sort of packages to be able to install groups of packages.

You can remove the ubuntu-desktop package and everything will work just fine.  However, when you will upgrade to a new release, you may be missing some feature (or you may find some features broken because the particular package has been replaced by another package which provides the same functionality - the only way the package manager would know to install the new package is if something depended on it.  Hence a meta-package)

Mark for removal means remove the files that the installation of the package creates.  Mark for complete removal also wipes the configuration information from the package manager's database.  Not to be confused with the configuration files for that application - just the package manager ones (debconf)

---

### Post by pay on 2006-10-02
I removed ubuntu-desktop and it removed gnome. Maybe something else happened aswell. Anyway if Azz says it's alright then maybe it is.

---

### Post by pay on 2006-10-02
yup azz proved me wrong, it's only a meta package. I don't know what happened when I removed it.:confused: 

ubuntu@ubuntu:~$ sudo apt-get remove ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 41.0kB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by englishmen on 2006-10-10
Thanks for the info azz, you said when i upgrade to a new release are you referring to a new release of ubuntu or the app i remove?

Thanks.

---

### Post by fdoving on 2006-10-15
> **azz said:**
> 
Mark for removal means remove the files that the installation of the package creates.  Mark for complete removal also wipes the configuration information from the package manager's database.  Not to be confused with the configuration files for that application - just the package manager ones (debconf)

That's not entirely true, if synaptic behaves as the other frontends to dpkg/apt.
Atleast dpkg -P <package> removes the configfiles for the application.


- Frode

---

### Post by marcelm on 2006-10-19
I'm confused about this. I want to remove Evolution, is it, or is it not safe to remove it without losing features, and if so -like it's been said- it's like Microsoft IE it must be resident on my HD?


ANd why does it say 'to be installed bltty-X11' when I Remove something ?

---

### Post by savohead on 2006-10-20
i always see the ubuntu-desktop package being packed or unpacked while i instal or remove appz, so i think Azz is right, but i've some other questions.
I tried to uninstall my amarok 'cause i just messed up with its plugins and i couldn't stop one of them. I completely removed it in Synaptic but when i re-installed it i just got my same old amarok.
I had to remove the folder in my home/user to get back to a fresh amarok.
So, i'm doing almost the same thing englishman does, install and see if it's useful for me and then remove, but how could i be sure that when i remove something, EVERYTHING that belongs to it is removed?!
Sorry for my long question, but i'm not so good in english (as in ubuntu!! eheh)
thanks

---

