---
title: "Cannot install wine please help soon!"
date: 2010-01-12
forum: Wine
---

### Post by bubbles99 on 2010-01-12
Hi.
I had wine installed originally. then, i removed it. After that, i did:

apt-get autoremove
apt-get autoclean
apt-get clean

After all three (i think it was in autoremove), it said a number of files had been deleted. The included the word "wine" in their titles, but i dont know the exact files.

I now need to reinstall wine, to play Spore, but when i try to it tells me some additional files are needed but not installed and also that it may conflict with other software. it doesn't tell me what the files/programs are.

Please help me!

---

### Post by sxmaxchine on 2010-01-12
try sudo apt-get install wine
also you may need to add it to your software sources list to do this:
go system> admin > software sources and then choose 3rd party tab
2.also i need to no wat version of ubuntu u have if you have jaunty add this
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
if u have karmic add this
ppa:ubuntu-wine/ppa
then download this save to desktop
[http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg]("http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg")
then in the software sources form go to the authentication tab and then click import and open the file u just downloaded.
now click close and make sure u click reload.
now u can instal it either by finding it in the add/remove programs or by using this code in terminal
sudo apt-get install wine

hopes this helps

---

### Post by bubbles99 on 2010-01-12
i tried what you told me. after entering the command at the terminal, i get this:

aaron@ubuntu:~$ sudo apt-get install wine
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages



(by the way that was supposed to be a "screenshot" of the terminal)

I have Ubuntu Karmic and all the latest updates.

---

### Post by bubbles99 on 2010-01-12
lol! fixed it!
you have to type this:

sudo apt-get install wine**1.2**


you need the 1.2 on the end!


I found this out from another thread. if anyone else is having problems, check this out:
[http://ubuntuforums.org/showthread.php?t=1343312&highlight=install+wine+soon!]("http://ubuntuforums.org/showthread.php?t=1343312&highlight=install+wine+soon%21")

---

