---
title: "Installation and configuration of Lyricue"
date: 2007-09-17
forum: Ubuntu Christian Edition
---

### Post by xilix on 2007-09-17
I installed the lyricue-package in Ubuntu Feisty Fawn. My first problem was, that no entry was created in the menu. 

When I type lyricue in the terminal a dialog opens, asking for the MySQL Administration user and password. I tried several inputs but all I get is this

```
DBI connect('mysql:localhost','lyric',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/bin/lyricue line 8244
DBI connect('mysql:localhost','root',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/bin/lyricue line 7901
Can't call method "prepare" on an undefined value at /usr/bin/lyricue line 7932.

```

Can anyone help me?

---

### Post by silvagroup on 2008-01-17
Same here.
Did Google and not much there either.
I tried installing mysql-client5.0 and it won't install something about breaking some dependencies.
JUsy wondering if this is a better suited for another OS maybe Debian.

---

### Post by silvagroup on 2008-01-19
I just gave up on lyricue for now. I am going to try OpenSong.
It looks like it's pretty much the same thing as lyricue.
Did an install in a vmware windows version and it installed and worked.
Now to see how it does in Linux.

---

### Post by debenham on 2008-02-13
That error indicates that mysql-server is not installed.
To do so run 'apt-get install mysql-server'
Then re-run 'lyricue' and enter 'root' for the root mysql user and generally just leave the password part blank

---

### Post by efrenjiji on 2008-03-13
Uh! well I find it so difficult to deal with this ubuntu and lyricue, after few months is searching on "How to" it wasted my time and it landed me again in MS Window XP and Vista for Easislides which is also free, and not much of a hassle in installing and operating the software for church services,Thanks anyway

---

### Post by silvagroup on 2008-03-13
Unfortunately Lyrciue is a real pain for the technically challenged. like myself. I gave up on it months ago.
OpenSong is also a potential thorn in the side with *buntu's. Woks great in Windows however, so I am not using it either.
I finally settled for something that just works, with Linux and in Windows with no haggling with getting it to work, that was Impress. The only issue is that for some reason on Windows I have a problem getting anything but wav files to play as other sound in slide transitions, not that big an issue since I can use wav files. That problem is not there in the Linux side.
And with Impress I can do many things I can't with OpenSong. You may to try it.:popcorn:

---

### Post by lieryan on 2008-06-13
Anyway, just to add, I recently tried installing lyricue on Hardy and it worked out of the box, apt-get resolves the mysql dependencies correctly.

(although I might have to add: I have noticed that my local Ubuntu's apt-get mirror often doesn't have all the files needed, I set up apt-get to look for programs in the local mirror then looks in the Main Server if it can't find it in the local server, mysql is one that have to be downloaded from the Main server, I have to use the two server configuration since my international Internet speed is extremely slow compared to local internet speed[1])

[1] Problem is, the files that the local server missed is often huge files.

---

### Post by raid996 on 2009-01-31
I have Lyricue up and running with 8.10
Install mysql-serve with synpatic, it will ask for a password to access mysql DB.
Install the Lyricue package from Synaptic, then while installing it will ask for a username, give it the one you will be planning to use.

Then when started it will ask for user and password of the mysql database, just give "root" and whatever password you chose for mysql DB, it should start.
It didnt work for me right away, so i executed in a terminal:
```
sudo dpkg-reconfigure lyricue
```
Gave again the username (i have only mine), i launched lyricue again and it just works.
Hope it helps

---

### Post by wineman on 2009-02-23
> **raid996 said:**
> 
Then when started it will ask for user and password of the mysql database, just give "root" and whatever password you chose for mysql DB, it should start.
It didnt work for me right away, so i executed in a terminal:
```
sudo dpkg-reconfigure lyricue
```
Gave again the username (i have only mine), i launched lyricue again and it just works.
Hope it helps

also to fix the password issue you should try these:
```
sudo dkpg-reconfigure mysql
```

---

### Post by ricgal on 2010-03-07
What is neat about lyricue now is the help pages at lyricue.org

---

### Post by ricgal on 2011-03-18
We used Lyricue with a two-computer setup, because the ATI graphics gave problems setting up video.  We should have gone with an Nvidia card; they are apparently more friendly to Linux.

We blew one computer and decided to load windows 7 on a new box. This lead us to the discovery of screen monkey, which does worship and more very well.:D

In fact, I would like to see screen monkey on Linux.  However, to play powerpoints through SM you need Microsoft office; API for OpenOffice does not give the program developer what he wants.:(

---

