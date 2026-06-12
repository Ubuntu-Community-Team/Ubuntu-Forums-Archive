---
title: "K3b wants - &quot;cdrdao package&quot; ????"
date: 2005-11-05
forum: Repositories &amp; Backports
---

### Post by EvilBill on 2005-11-05
When I start K3b, it tells me I need "cdrdao package" I cannot find this. I installed every single thing even remotely connected with cd burning, of course that did nothing.

How can I get my K3b to actually work, so I can burn an iso image & upgrade to 5.10


:???: :confused:

---

### Post by Xian on 2005-11-05
Here it is: [cdrdao_1.1.9-3](http://archive.ubuntu.com/ubuntu/pool/universe/c/cdrdao/cdrdao_1.1.9-3ubuntu3_i386.deb)

Place in your /home/username/ path.
Install with the terminal command:

```
$ sudo dpkg -i *deb
```

---

### Post by manicka on 2005-11-05
cdrdao is in the repositories

```
sudo apt-get update
sudo apt-get install cdrdao
```

or install it with synaptic

---

### Post by manicka on 2005-11-05
oops, just noticed you'll need to add the universe rep as well

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by EvilBill on 2005-11-05
[QUOTE=manicka]oops, just noticed you'll need to add the universe rep as well

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)[/QUOTE]


That didn't work.

> sudo apt-get update
sudo apt-get install cdrdao
those commands actually worked. They didn't help me, but at least they did something, what I don't know?

> Xian
Here it is: cdrdao_1.1.9-3

Place in your /home/username/ path.
Install with the terminal command:

Code:

$ sudo dpkg -i *deb


My username is "william" I made a folder in "home" called "cdr"

If I d/l the above mentioned file to this folder,...

What command line would I type. I tried to run this command that Xian made for me, it says no such file [something like that]

---

### Post by manicka on 2005-11-05
okay, try this in a terminal

```
cd ~/cdr

sudo dpkg -i *.deb
```

---

### Post by manicka on 2005-11-05
[QUOTE=EvilBill]
those commands actually worked. They didn't help me, but at least they did something, what I don't know?
[/QUOTE]

If they did something with no error messages then it is likely that you succeeded in enabling universe with the instructions on the wiki and installing cdrdao.

Read the wiki again to add the universe and multiverse repos. You will need them for other software in the future.

---

### Post by Xian on 2005-11-06
Just read the wiki entry [Synaptic How-To](https://wiki.ubuntu.com//SynapticHowto).
It describes how to install software and add repositories.

All in one shopping. :)

---

### Post by EvilBill on 2005-11-06
In 5.10 it does not ask for cdrdao, ............good! :p

---

### Post by victorche on 2005-11-07
[QUOTE=EvilBill]In 5.10 it does not ask for cdrdao, ............good! :p[/QUOTE]
As far as I remember, it asks also for cdrdao in Kubuntu 5.10 ;)
It didn't ask you, just because you already have it installed :)
Correct me if I am wrong, but after a clean 5.10 install and starting of K3b, it asks for it.

---

### Post by EvilBill on 2005-11-08
[QUOTE=victorche]As far as I remember, it asks also for cdrdao in Kubuntu 5.10 ;)
It didn't ask you, just because you already have it installed :)
Correct me if I am wrong, but after a clean 5.10 install and starting of K3b, it asks for it.[/QUOTE]

In 5.10 it does not ask for it. I got K3b from the S P Mgr. It included a whole bunch of things when I clicked on it. Everything worked fine, I made a copy of 5.10 x86 install for my dad. :smile:

---

