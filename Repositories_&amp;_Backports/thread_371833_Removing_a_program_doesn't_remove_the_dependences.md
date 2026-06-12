---
title: "Removing a program doesn't remove the dependences?"
date: 2007-02-27
forum: Repositories &amp; Backports
---

### Post by sleepyenglish on 2007-02-27
When i install a program via synaptic package manager and it requires other packages to be installed. How come is it when i remove the program it doesn't also remove and other packages that was required for the installation?

Thanks

---

### Post by 23meg on 2007-02-27
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by DarkN00b on 2007-02-27
Because other programs may have some of the same dependencies and if they were removed, the other program(s) would stop working.

---

### Post by sleepyenglish on 2007-02-27
Thanks for the replies

DarkN00b i understand what your saying but the program in question was installed including dependences, i used it didn't like it then removed it. Nothing was installed in between there for the dependences it installed are there for no longer needed, yet they were not removed along with the actual app of which i installed.

I use windows xp on my desktop and its annoying having to hunt down registry entries, files and folders left over by  a program i have uninstalled. I was hoping it would be different on ubuntu, how come its not?

---

### Post by christhemonkey on 2007-02-27
To remove folders and config files left behind, make sure you check 'mark for complete removal'
(or sudo apt-get remove --purge foo)

Also there are a couple of ways to remove extra dependencies:
```
sudo apt-get autoremove
```
or install deborphan:
```
sudo apt-get install deborphan 
```
This checks for and presents a list of libs/programs that are redundant dependencies.
I have found that it doesnt always work for me (suggesting removing daft things and not noticing others, but YMMV)
(also gtkorphan is a nice graphical frontend to deborphan so try that as well)

---

### Post by 23meg on 2007-02-27
From the page I linked to:

> Update: Apparently the new version of apt-get in Edgy Eft (Ubuntu 6.10) has a function that allows you to remove unused dependencies when removing an application:
```
sudo apt-get autoremove applicationname
```

> Both aptitude and apt-get will install kword and its dependencies (kspread, kword-data, and libwv2-1c2), but only aptitude will actually remove the dependencies when kword is removed (and only if no other packages depend on those dependencies). 

---

### Post by sleepyenglish on 2007-02-27
Thanks for the suggestions both im going to give them go in a minute.

I found

[System Clean Up Tool]("https://blueprints.launchpad.net/ubuntu/+spec/make-free-space-wizard")

on the launchpad site which sounds like something that when hopefully implemented would hopefully also remove redundant dependencies.

---

### Post by sleepyenglish on 2007-02-27
I just tried the below and the dependences for the program last.fm were listed as no longed being needed as i have already removed last.fm. They amazingly take up 18mb which is amazing as its the only app ive installed so far on my new installation of ubuntu 6.10. Just imagine the space all the unnecessary dependences will take up in a couple of months, the ubuntu dev team should really do something about this.

> 
sudo apt-get autoremove

---

