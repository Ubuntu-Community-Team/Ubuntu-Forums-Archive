---
title: "howto for installing software without an internet connection"
date: 2005-05-13
forum: Repositories &amp; Backports
---

### Post by UbuWu on 2005-05-13
A few months ago, when I didn't have an internet connection yet on my computer, I had a lot of trouble trying to install software on ubuntu. Now I am trying to make a little howto on doing this. The following is what I thought of so far, please give your comments on how it could be done better:

First of all, you need the correct package index files (the files that are updated when you type apt-get update). If you have a dial-up internet connection this should be easy, just use apt-get update. If you don't have an internetconnection at all, you will probably have to find someone who has the same ubuntu version installed as you. The files are stored in /var/lib/apt/lists. You need all the files starting with archive.ubuntu.com_ubuntu_dists_hoary (assuming you are running hoary/5.04). Put them in your own /var/lib/apt/lists directory.

Then the typing the following line in a terminal window will give you the files you need to download:
```
apt-get -qq --print-uris install ***packagename*** | cut -d\' -f2
```
Replace ***packagename*** with the name of the package you want to install.
You can add >filelist to the end of the line to make a file containing all the urls, which you can easily download on any pc with linux using wget -i filelist.

Download all the files and put them in one directory. Then go to the directory and type: 'dpkg-scanpackages . /dev/null | gzip > Packages.gz'
Burn all the files in the directory on a cd.
On your own pc type 'apt-cdrom add'.
Then you are all set and can use apt-get install ***packagename*** to install the package.

Alternatively you can install all the individual package files with dpkg -i filename.deb

---

### Post by andlinux21 on 2005-05-21
[QUOTE=UbuWu]A few months ago, when I didn't have an internet connection yet on my computer, I had a lot of trouble trying to install software on ubuntu. Now I am trying to make a little howto on doing this. The following is what I thought of so far, please give your comments on how it could be done better:

First of all, you need the correct package index files (the files that are updated when you type apt-get update). If you have a dial-up internet connection this should be easy, just use apt-get update. If you don't have an internetconnection at all, you will probably have to find someone who has the same ubuntu version installed as you. The files are stored in /var/lib/apt/lists. You need all the files starting with archive.ubuntu.com_ubuntu_dists_hoary (assuming you are running hoary/5.04). Put them in your own /var/lib/apt/lists directory.

Then the typing the following line in a terminal window will give you the files you need to download:
```
apt-get -qq --print-uris install ***packagename***|tr -d "'"|sed s/' '/'\n'/g|grep http://
```
Replace ***packagename*** with the name of the package you want to install.
You can add >filelist to the end of the line to make a file containing all the urls, which you can easily download on any pc with linux using wget -i filelist.

Download all the files and put them in one directory. Then go to the directory and type: 'dpkg-scanpackages . /dev/null | gzip > Packages.gz'
Burn all the files in the directory on a cd.
On your own pc type 'apt-cdrom add'.
Then you are all set and can use apt-get install ***packagename*** to install the package.

Alternatively you can install all the individual package files with dpkg -i filename.deb[/QUOTE]
 Wouldnt a dialup update take a long time and if you get disconnected can you pick up where you left off?

---

### Post by Elendur on 2005-05-21
[QUOTE=andlinux21]Wouldnt a dialup update take a long time and if you get disconnected can you pick up where you left off?[/QUOTE]

Some MB to download so yes it would take some time, but it's a problem mainly if you're not using the stable (hoary) distribution. And yes "apt-get update" can be interrupted and resumed.

As for the shell command, wouldn't this be enough:

apt-get -qq --print-uris install ***packagename*** | cut -d\' -f2

---

### Post by UbuWu on 2005-05-21
[QUOTE=Elendur]
As for the shell command, wouldn't this be enough:

apt-get -qq --print-uris install ***packagename*** | cut -d\' -f2[/QUOTE]

True, edited my post :-)

---

### Post by ice_florian on 2006-11-13
Hi!

There is one problem: If the package you want to install on the non-network-computer is already installed on the computer where you download the packages then the list of the uris is empty. (sorry for my bad english-skills :???:  ) 

I found a solution for this: add --reinstall

```
apt-get -qq --print-uris install --reinstall ***packagename*** | cut -d\' -f2
```

EDIT: There is another problem: If a dependency of a package has its own dependencys, those de-dependencys won't be downloaded :-( I don't have a solution for this found yet. Can anybody help me please? I want to install xubuntu-desktop, because gnome is too slow on this celeron 466 with 128MB RAM with no NIC :-/

---

### Post by rpradeep on 2006-11-30
I have an internet connection at home but using that is very expensive for me. Therefore i had to find another solution. As i have internet connection at my office i try to do this.

First i downloded the Packages.gz from sites found in sources list.
usually in dist.../i386 something..

Then i copied these Packages.gz to from different directories (say multiverse..universe..main) to home directory with subdirectories of multiverse..universe..etc.
Then i edited the sources list to show only these locations and updated.

You will get all the available softwares in the synaptic.

Then you can get the list of files needed for a particular software using the command mentioned in previous listings..apt-get install...print...something.

Then you take this list and download the required files in the list and install as necessary.

---

### Post by biffta on 2006-12-04
Hey guys, I read the various ways you can bypass the network connection to install software. But here is my situation.

PC1: Ubuntu (dapper) installed with packages X
PC2: Ubuntu (dapper) installed default packages, no network access

Think you can guess what I am going to ask! How do I get all of packages X onto PC2. I thought to copy whole of
/etc/apt/ /var/lib/apt/ /var/cache/apt/
onto a memory stick and transfer to PC2. Will this work? i.e. will all the packages be usable and the apt-get databases be generated?

---

### Post by bryo21 on 2006-12-17
> **rpradeep said:**
> I have an internet connection at home but using that is very expensive for me. Therefore i had to find another solution. As i have internet connection at my office i try to do this.

First i downloded the Packages.gz from sites found in sources list.
usually in dist.../i386 something..

Then i copied these Packages.gz to from different directories (say multiverse..universe..main) to home directory with subdirectories of multiverse..universe..etc.
Then i edited the sources list to show only these locations and updated.

You will get all the available softwares in the synaptic.

Then you can get the list of files needed for a particular software using the command mentioned in previous listings..apt-get install...print...something.

Then you take this list and download the required files in the list and install as necessary.

Hello friend, I'm new to linux system and I don't have an internet connection. So, I downloaded the packages and saved it on my home directory. My problem now is what should I put on the sources.list? I tried:

deb /home/bry/ dapper main restricted
deb-src /home/bry/ dapper main restricted

but I recieved the error:

E: Malformed line 37 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Please help me with this one.. Thank you! :):-D

---

### Post by bryo21 on 2006-12-21
> **bryo21 said:**
> Hello friend, I'm new to linux system and I don't have an internet connection. So, I downloaded the packages and saved it on my home directory. My problem now is what should I put on the sources.list? I tried:

deb /home/bry/ dapper main restricted
deb-src /home/bry/ dapper main restricted

but I recieved the error:

E: Malformed line 37 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Please help me with this one.. Thank you! :):-D


hi, fyi.. i edited my sources.list as: 

deb file:///home/bry dapper main restricted
deb-src file:///home/bry dapper main restricted

and it worked properly.. :)

---

### Post by apparle on 2007-08-30
I have installed Ubuntu feisty fawn 7.04 64bit (amd64)a week ago.
If I exract any .tar.gz package I get an error though the archive is not damaged
I want to install an antivirus.
Important : I donot have an internet connection.:confused::confused::confused:

---

### Post by Euan17 on 2007-08-30
i need to install the files required to setup NFS server, i found this [tutorial]("http://ubuntuforums.org/showthread.php?t=249889"), but i have no internet connection on my linux machine, where can i get these files on the web? sorry im very new to linux

---

