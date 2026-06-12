---
title: "Off-line custom repository"
date: 2004-12-07
forum: Repositories &amp; Backports
---

### Post by orestis82 on 2004-12-07
Hello there.

I have installed Ubuntu on my home machine, which only has dial-up access.

I would like to update my installation, however using the dial-up takes forever.

I have broadband access at work, and I can burn cds or bring my external HD and get files to it.

Is it possible to download packages to my hd and use it as a repository for home ?

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=orestis82]Hello there.

I have installed Ubuntu on my home machine, which only has dial-up access.

I would like to update my installation, however using the dial-up takes forever.

I have broadband access at work, and I can burn cds or bring my external HD and get files to it.

Is it possible to download packages to my hd and use it as a repository for home ?[/QUOTE]

hmmm. Its certainly possible that you could make a cd source, but it sounds difficult.

---

### Post by Marauder1 on 2004-12-07
I think it could be done.
Im not sure but if you grab the files and then copy them to the synaptic
cache directory on your system it could be done . ( with root access).
The cache directory is : /var/cache/apt/archives/

Try it and tell me if it works !!!

---

### Post by orestis82 on 2004-12-08
So, where do I grab the packages ? Is there any way I could automatically get them (I don't want to get them one by one...)

PS. I'm using windows at work...

---

### Post by az on 2004-12-08
man apt-get

apt-get upgrade --print-uris > file

copy the file to a floppy and use a windows downloading tool (Download accelerator plus? -  I dunno) to download all of the files to the harddrive.

copy all the files to cd or usb key and bring them home.

Copy them to your /var/cache/apt/archives
or
dpkg-scanpackages . /dev/null >Packages
and your directory is a reposiroty you may add to your sources.list

---

### Post by Marauder1 on 2004-12-08
You have to do an update and an upgrade with Synaptic.
then press the green check to see which packages need an upgrade.
but dont go futher. (you will know what to upgrade whitout actually doing it)
Grab the names of all the packages you need to download.
Then exit Synaptic.
Go to your Windows machine and go to this address:

[http://archive.ubuntulinux.org/ubuntu/pool/](http://archive.ubuntulinux.org/ubuntu/pool/)

All the packages should be there to download by categories.

Hope i'm clear enough  O:)

---

### Post by Marauder1 on 2004-12-08
[QUOTE=azz]man apt-get

apt-get upgrade --print-uris > file

copy the file to a floppy and use a windows downloading tool (Download accelerator plus? -  I dunno) to download all of the files to the harddrive.

copy all the files to cd or usb key and bring them home.

Copy them to your /var/cache/apt/archives
or
dpkg-scanpackages . /dev/null >Packages
and your directory is a reposiroty you may add to your sources.list[/QUOTE]

Thats a good one azz i was a bit confused how to do it.
I knew there was a faster way but my knowlege of apt-get is more GUI !!!

Thanks i'll keep that one  =D>

---

### Post by orestis82 on 2004-12-08
thank you, I'll try that tommorrow.

---

### Post by orestis82 on 2004-12-09
Hurray, it worked.
I created a directory ubuntu-repo in my home directory.

cd ubuntu-repo
create this path: (with mkdir)
/dists/warty/main/binary-i386

Copy all downloaded packages there:
then, from the ubuntu-repo folder:
 dpkg-scanpackages dists/warty/main/binary-i386 /dev/null >Packages
then:
 cp Packages dists/warty/main/binary-i386/
Load Synaptic, add:

create repository:
file:///home/orestis/ubuntu-repo/   (orestis is my user)
distribution: warty
section: main

press New! not ok.

disable all other repositories.
Reload, mark all upgrades, apply. Done!

---

### Post by orestis82 on 2004-12-13
To all mods: Can we please move this to the HOW-TO ? Many people are asking questions like this. If necessary I can post a more contained solution in the HOW-To.

---

### Post by paradox on 2004-12-19
For me this work:

1) Create a dir in your home (ex. /home/pinco/Ubuntu-repository)

2) Generate Package file: dpkg-scanpackages . /dev/null > Packages

3) Insert in sources.list the correctly path like this: 

deb file:/home/pinco/Ubuntu-repository ./

4) sudo apt-get update

:D

---

### Post by jdong on 2004-12-21
It's best practice to put such a repository in a system-wide place, like /var/apt/ubuntu, and own it as root. Otherwise, the user pinco and any app run as pinco can inject apps onto your Ubuntu system.

---

### Post by paradox on 2004-12-22
[QUOTE=jdong]It's best practice to put such a repository in a system-wide place, like /var/apt/ubuntu, and own it as root. Otherwise, the user pinco and any app run as pinco can inject apps onto your Ubuntu system.[/QUOTE]

yes, my practice is only one user oriented :D Anyway this work properly still as  another situation :D. Yes /var/apt/ubuntu with own root is best solution :D

Bye!

---

### Post by paul cooke on 2005-02-02
[QUOTE=jdong]It's best practice to put such a repository in a system-wide place, like /var/apt/ubuntu, and own it as root. Otherwise, the user pinco and any app run as pinco can inject apps onto your Ubuntu system.[/QUOTE]

and if you have several machines on your local network to update, then you should be able to share that directory using NFS or Samba (or whatever) and your other machines should then be able to see it so that you can then set them to use that exported/shared directory as a source (you will have to edit their sources list appropriately)

:)

---

### Post by RomanoGiannetti on 2005-06-17
I know it's a very old thread this one, but I add this to say that I made a page to explain how to do a very similar thing with cross-arch capabilities... 

[http://www.dea.icai.upco.es/romano/linux/ubuntu_and_i.php](http://www.dea.icai.upco.es/romano/linux/ubuntu_and_i.php)

 O:) have a nice day! And thanks for the suggestions of this forum!

---

### Post by gpwil1 on 2008-11-25
I found this thread useful for helping me automate this process for other people who wish to do the same.

See the following for instructions:

#first update the source list
sudo apt-get update
sudo apt-get -f install

#next print selected packages to file 
sudo apt-get install firefox gsynaptics gparted wine unrar-free vlc nmap openssh-server openssh-client gimp samba traceroute mdf2iso --print-uris > file

#strip out html links for packages
egrep -o -e "(ht|f)tp://[^\']+" file > file2

#download packages either in windows or use the following:
rm file
mv file2 /var/cache/apt/archives/
cd /var/cache/apt/archives/
wget `cat file2`

sudo dpkg -i -R /var/cache/apt/archives/

---

### Post by kameleontti on 2010-07-22
No wonder that linux / ubuntu isn't more popular :)

Why can't community make a graphical utility, included in ubuntu management tools, to make all this? 
So utility showing official or mirrored repositories of all ubuntu versions, packages and updates there and tool-buttons to copy them locally according to user selections, which ones? 
Sure would be much much easier to everyone, than scripts and terminal commands and discussions about it.
Nerds like remembering commands and entering them in terminal, but majority of ubuntu users would sure like graphical straighforward utility like update manager now in ubuntu tools. 

Sometimes it is almost impossible to install ubuntu in a machine that needs for example some extra restricted driver for wireless or network to establish internet connection and needs that driver package from web repository - or by some strange reason can't install it from install cd source. And if that is too difficult, one can't install ubuntu nor can get it easily working... and forgets it and continues to use Windows, that more often just works with basic essential things like establishing internet connection. 

Sometimes feels like ubuntu is more like alienware than for humans - unfortunately.

---

