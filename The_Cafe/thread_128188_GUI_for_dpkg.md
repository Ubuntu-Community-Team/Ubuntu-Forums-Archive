---
title: "GUI for dpkg"
date: 2006-02-10
forum: The Cafe
---

### Post by detyabozhye on 2006-02-10
To begin, I don't mind using the Terminal at all, I use it almost every day. But when I first started using Ubuntu, I was searching all over for a GUI way to install those .deb files. So now, I'm writing a GUI front-end for dpkg using Mono. It works like this: person downloads deb file because there are absolutely no repositories that have that package, person right-clicks deb package and clicks "Open with Gpkg", person sees a dialog with general info about the package and an install button, person clicks "Install", Gpkg reports if package is installed successfully or not.

Now, I have a few questions:
Do you think this is a good idea?
Has it been done before? (I haven't found anything similar, but I don't really want to reinvent the wheel)
Am I taking the right aproach?
Any suggestions?
Wanna help?

---

### Post by Perfect Storm on 2006-02-10
I think there's an application which make the .deb installable if you double click them. Though I can't remember where I saw that.

---

### Post by Mustard on 2006-02-10
You may be reinventing the wheel.  I believe there is a third party project going on somewhere in the ubuntu community that is considering just such an issue.

---

### Post by engla on 2006-02-10
There should be plenty of applications that do this.

In another thread where this was discussed I posted a python app that basically did just what you described there, and simultaneously another guy posted his take at it..

So don't reinvent the wheel (like we did ;-)

---

### Post by detyabozhye on 2006-02-10
Anybody got a link to that/those thread(s)?

---

### Post by engla on 2006-02-10
Found one:
[http://ubuntuforums.org/showthread.php?t=114215](http://ubuntuforums.org/showthread.php?t=114215)

---

### Post by Virogenesis on 2006-02-10
I believe dapper will have something like this and will also sort out dependecies aswell. 
Maybe I'm wrong can't remember

---

### Post by detyabozhye on 2006-02-10
Thankies, found quite a lot of stuff now. I guess I was reinventing the wheel, at least it helped me learn how to make GUI wrappers in C#. :mrgreen:

---

### Post by detyabozhye on 2006-02-10
Here's what I had so far, btw

---

### Post by detyabozhye on 2006-02-10
I installed gdebi, so I'm fine for now, thanks ppl.

---

### Post by Arktis on 2006-02-11
What's wrong with what you had so far?  It looks nice.  You should keep working on it anyways.

---

### Post by ardchoille on 2006-02-11
Yes, I agree, keep working on it. Variety is one of the things that makes Linux so great in my opinion.

---

### Post by prizrak on 2006-02-11
Actually in this case it's kinda pointless. This is rumors of course, but Dapper is supposed to have a fairly advanced GUI front end that would basically work with apt-get to sort out all the dependancies and stuff. The reason none of the GUI ones that were available when Breezy came out was cuz none of them handled dependencies. At the very leas I'd say wait to see what Dapper offers and then maybe code something. Another thing you might wanna consider is apply them programming skills somewhere else ;)

---

### Post by imagine on 2006-02-11
Rather help testing gdebi from Michael Vogt : )

> Dear Friends,

the current development version of ubuntu ("dapper") contains the new packages "gdebi" and "unattended-upgrades". I would like to ask for testing of those two packages. Please note that they are development software and may have bugs that can do bad things to your system. So don't run it on your production server and keep backups (I think they are pretty ok and shouldn't have major problems, but you have been warned). 

unattended-upgrades is a python-apt based script that will download and install security upgrades automatically and unattended. It does all sorts of checks to ensure that the upgrade can be performed unattended and that only security upgrades are fetched (for details see [https://wiki.ubuntu.com/AutomaticUpdates](https://wiki.ubuntu.com/AutomaticUpdates)). I would like to ask interessted people to test it on their breezy system. To do that, please install the package "unattended-upgrades" from the repository below. This particular package dosn't do the upgrade automatically but needs to be run by hand with "sudo unattended-upgrade". It will log what it does in /var/log/unattended-upgrades/unattended-upgrades.log (and shouldn't have any output on the terminal). Please run it and look into the logfile if it is doing sensible things. I would be interessted in failure/success stories.

gdebi is a application that can install deb packages. It will do dependency resolution and some basic checks to make sure that the system dosn't contain broken packages afterwards. To test it just install the "gdebi" and "libvte4" packages. Then you can right-click on deb packages and select "Deb Package Installer". Please let me know if it makes sensible descisions about the dependency resolution and if it installs the debs correctly. If you experiences problems (crashes) please run it from a termianl with "gdebi-gtk foo.deb" and send me the output. 

The packages are available from:
deb [http://people.ubuntu.com/~mvo/backports/breezy](http://people.ubuntu.com/~mvo/backports/breezy) /

The archive is signed with my gpg-key (0x5662C734). 

If you want your old packages back, please run:
```
$ sudo apt-get install libvte4=1:0.11.15-0ubuntu2 libvte-common=1:0.11.15-0ubuntu2 python2.4-apt=0.6.13.1ubuntu1 python-apt=0.6.13.1ubuntu1 gdebi- unattended-upgrades- python-vte=1:0.11.15-0ubuntu2

```

thanks,
 Michael

The version in the Dapper repositories is a little bit newer than the backports though.
[http://packages.ubuntu.com/dapper/admin/gdebi](http://packages.ubuntu.com/dapper/admin/gdebi)



And since everybody loves screenshots:
[http://people.ubuntu.com/~mvo/gdebi/gdebi-1.png](http://people.ubuntu.com/~mvo/gdebi/gdebi-1.png)
[http://people.ubuntu.com/~mvo/gdebi/gdebi-2.png](http://people.ubuntu.com/~mvo/gdebi/gdebi-2.png)
[http://people.ubuntu.com/~mvo/gdebi/gdebi-3.png](http://people.ubuntu.com/~mvo/gdebi/gdebi-3.png)

---

### Post by detyabozhye on 2006-02-11
I installed gdebi, and it handles dependencies, checks first to see if a packeage is already installed, etc. It's quite a bit more mature than mine.

---

### Post by xequence on 2006-02-11
[QUOTE=detyabozhye]I installed gdebi, and it handles dependencies, checks first to see if a packeage is already installed, etc. It's quite a bit more mature than mine.[/QUOTE]

Put it this way: Choice never hurt anyone. Maybe yours can have a feature that the other guy's program doesent. Maybe it can be easier to use... I dont know =P

---

### Post by detyabozhye on 2006-02-11
I'd definately need some help with doing the dependencies cuz I have no clue on how to implememnt that part at the moment.

---

### Post by detyabozhye on 2006-02-11
If you guys want me to continue, tell me what features you would like in it, and which shouldn't be there.

---

### Post by dolson on 2006-02-12
[QUOTE=detyabozhye]If you guys want me to continue, tell me what features you would like in it, and which shouldn't be there.[/QUOTE]

Well, I like gdebi, although I use it only on my Dapper machine. Competition is good, sure, but I think gdebi has a good chance to one day be in main... I don't know what features could possibly be added to it. It seems to have everything I would ever need, plus more.

---

