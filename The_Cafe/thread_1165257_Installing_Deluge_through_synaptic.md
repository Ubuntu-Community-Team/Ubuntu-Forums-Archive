---
title: "Installing Deluge through synaptic?"
date: 2009-05-20
forum: The Cafe
---

### Post by fleaaccela on 2009-05-20
[http://packages.ubuntu.com/jaunty/all/deluge/download](http://packages.ubuntu.com/jaunty/all/deluge/download)

This page says this:
> If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/jaunty/aptitude") or [synaptic]("http://packages.ubuntu.com/jaunty/synaptic") to download and install packages, instead of doing so manually via this website.I tried looking for it in synaptic through a search, but could not find anything. I tried installing this through the Package Installer:

[http://mirrors.kernel.org/ubuntu/pool/universe/d/deluge/deluge_1.1.6+dfsg-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/d/deluge/deluge_1.1.6+dfsg-2ubuntu1_all.deb)

But it comes up with an error message inside of the installer that says:

> Error: Dependency is not satisfiable: deluge-common (= 1.1.6+dfsg-2ubuntu1)I'm using Gnome 2.X. Not sure what I'm doing wrong here. Usually installing progs through synaptic is a breeze, but it's nowhere to be seen - even though the site states that it is available for download through it.

Help? (ps - been using Ubuntu for about 5 days, pretty much straight "out of the box". This is my first problem.)

---

### Post by oldos2er on 2009-05-20
Make sure you have the universe repository enabled.

---

### Post by Kimm on 2009-05-20
> **fleaaccela said:**
> [http://packages.ubuntu.com/jaunty/all/deluge/download](http://packages.ubuntu.com/jaunty/all/deluge/download)

This page says this:
I tried looking for it in synaptic through a search, but could not find anything. I tried installing this through the Package Installer:

[http://mirrors.kernel.org/ubuntu/pool/universe/d/deluge/deluge_1.1.6+dfsg-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/d/deluge/deluge_1.1.6+dfsg-2ubuntu1_all.deb)

But it comes up with an error message inside of the installer that says:

I'm using Gnome 2.X. Not sure what I'm doing wrong here. Usually installing progs through synaptic is a breeze, but it's nowhere to be seen - even though the site states that it is available for download through it.

Help? (ps - been using Ubuntu for about 5 days, pretty much straight "out of the box". This is my first problem.)

Deluge should be in the repos. Open a terminal and type:

```
sudo apt-get install deluge
```

It will ask you for your password (so it can install :) ). That is pretty much a text based Synaptic alternative and lots of tutorials will require you to use it, but do not fret, its not difficult and when you get the hang of it you'll probably even prefer it :)

PS.
If you need to search for a package, do:

```
sudo apt-cache search packagename
```

---

### Post by darthmob on 2009-05-20
to enable the other repositories have a look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

personally, I always look at [getdeb]("http://www.getdeb.net/") for software if it's not existing or too old in synaptic. they have the most recent versions most of the time and provide them in easy to install packages. there seems to be no deluge package for jaunty though and I'm not sure if the intrepid one will install.

---

### Post by kaivalagi on 2009-05-20
Install the latest deluge packages through synaptic by adding this repo to your /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
```

Full instructions on adding the repo (and it's auth key) can be found here: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

The PPA is mentioned on the deluge site: [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)

---

### Post by fleaaccela on 2009-05-20
Fantastic! That was what I needed!

Here's how to do it (since I couldn't find any info on the forum on how to do it):

System > Administration > Software Sources

Check the box that says "Community-maintained Open Source software (universe)"

Go to the Third-Party Software Tab

Click +Add

Enter this line in the ATP box:

deb [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/) jaunty main universe

Click +Add Source

Click Revert

Close the software sources box

System > Administration > Synaptic Package Manager

Search for Deluge

Install! The program should be under the Internet tab in your menu.


Absolutely fantastic! Thanks to everyone for helping!

---

### Post by drawkcab on 2009-05-20
Heck, you can go up to 

applications--> add/remove applications--> internet --> deluge

just make sure you have "all available applications" selected at the top

it doesn't take but a couple clicks

---

### Post by kaivalagi on 2009-05-20
> **fleaaccela said:**
> Fantastic! That was what I needed!

Here's how to do it (since I couldn't find any info on the forum on how to do it):

System > Administration > Software Sources

Check the box that says "Community-maintained Open Source software (universe)"

Go to the Third-Party Software Tab

Click +Add

Enter this line in the ATP box:

deb [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/) jaunty main universe

Click +Add Source

Click Revert

Close the software sources box

System > Administration > Synaptic Package Manager

Search for Deluge

Install! The program should be under the Internet tab in your menu.


Absolutely fantastic! Thanks to everyone for helping!

What version of Deluge does this method install, the latest version is 1.1.7 and is installed via the PPA I posted details on.

You can find out the version of Deluge running "deluge --version" in a terminal

---

### Post by fleaaccela on 2009-05-20
It installed version 1.1.6

I suppose knowing how to upgrade it would also be key! ):P

---

### Post by kaivalagi on 2009-05-20
> **fleaaccela said:**
> It installed version 1.1.6

I suppose knowing how to upgrade it would also be key! ):P

As it is apt based (synaptic) any updates should come through just like anything else you install via synaptic.

If I were you though I would not use the repo you are using, instead use the one I posted. It is maintained by the Deluge team and contains the same packages that are available for download from the deluge site (currently v. 1.1.7).

It looks like the "mirror" you are using is not up-to-date

---

### Post by fleaaccela on 2009-05-20
sounds great. will do!

---

