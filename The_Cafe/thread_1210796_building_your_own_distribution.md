---
title: "building your own distribution"
date: 2009-07-11
forum: The Cafe
---

### Post by PatrickMoore on 2009-07-11
i was curious about how hard it would be to build my own custom distribution based off ubuntu. there is alot of programs preloaded with ubuntu that i dont use and alot that i need to manually install that i use so im compelled to make my own perfect install cd

---

### Post by Gizenshya on 2009-07-11
I've wondered about this myself.

For the time-being I decided to just backup the drive after installing and updating everything I wanted.

Unfortunately, I don't know how to do that either :o

---

### Post by Sublime Porte on 2009-07-11
[Remastersys](http://en.wikipedia.org/wiki/Remastersys)

It has both a backup option (so you can just make a LiveCD of your own personal setup/data) or a distro option, to create your own distro-remix LiveCD.

---

### Post by PatrickMoore on 2009-07-11
> **Sublime Porte said:**
> [Remastersys](http://en.wikipedia.org/wiki/Remastersys)

It has both a backup option (so you can just make a LiveCD of your own personal setup/data) or a distro option, to create your own distro-remix LiveCD.

beautiful. i think im going to have a go. can i change the splash screen to one of my own design

---

### Post by Sealbhach on 2009-07-12
More info here on various ways to roll your own distro:

[http://www.tuxradar.com/content/how-build-your-own-linux-distro](http://www.tuxradar.com/content/how-build-your-own-linux-distro)

.

---

### Post by Sublime Porte on 2009-07-12
> can i change the splash screen to one of my own design

Yes.

---

### Post by P Minix on 2009-07-12
I would rather have a way of generating an APT-GET report that I could use to setup new machines from a CD.  Any ideas.

---

### Post by PatrickMoore on 2009-07-12
> **Sublime Porte said:**
> Yes.

what would i do to change that?

---

### Post by PatrickMoore on 2009-07-12
should i start with a minimal cd? or a plain live cd i want to make it ubuntu based i think?

---

### Post by earthpigg on 2009-07-12
> **P Minix said:**
> I would rather have a way of generating an APT-GET report that I could use to setup new machines from a CD.  Any ideas.

```
dpkg-query -l > packinfo
```

will make a text file, called packinfo, containing every package installed on your system.

in alphabetical order.

now, we need someone smarter than me to figure this out:

```
dpkg-query -l | grep (something to remove the first four characters of every line) | grep (something to remove everything in a line starting with the first space) > packinfo
```


if someone can replace my (parenthesis) with an actual command or option of some type, the result would be a text file containing the package names and *_nothing else_*.

using that file as the pattern, we could then install the exact same packages on multiple machines with exactly _one command per machine._

---

### Post by earthpigg on 2009-07-12
grrrr

there is a command that _**omits**_ things that follow a specific pattern.

what is it?!

---

### Post by earthpigg on 2009-07-12
so i was sitting here thinking 'man, this would be SO much easier to do in arch than ubuntu, usin pacman....'

'...hey! maybe i can just install pacman! its free software, it should be in the repos! im sure those smart folks at debian have long ago figured out how to make another distros package manager work with debian packages'

```
sudo apt-get install pacman
```

[SIZE="5"]'SWEET! its working! this will be easier than i thought!'[/SIZE]

```
man pacman
```

```
NAME
       pacman - the game of pacman

SYNOPSIS
       pacman [grey]

DESCRIPTION
       Pacman is an old action game.

       You  are  Pacman, and you are supposed to eat all the small dots to get
       to the next level. You are also supposed to keep away from the  ghosts,
       if they take you, you lose one life, unless you have eaten a large dot,
       then you can, for a limited amount of time, chase and eat  the  ghosts.
       There is also bonus available, for a limited amount of time. An X gives
       just points, but a little pacman gives an extra life.

       bla bla bla
```


*facepalm*

---

### Post by earthpigg on 2009-07-12
i am reinventing the wheel.

google had *_half_* the answer.

[http://forums.debian.net/viewtopic.php?f=6&t=37979](http://forums.debian.net/viewtopic.php?f=6&t=37979)

to get the list, from the machine-to-be-cloned:

> aptitude search -F '%100p' '~i!~M' > package_list

to use the list, on the target machine:

> sudo apt-get install $(cat package_list)


edit: wtf, the install command 'ate' the package names out of package_list as it installed them.... now that file is empty??!

---

### Post by aysiu on 2009-07-12
If you don't really want to build a distribution but just want to change the default packages and artwork in Ubuntu, then Remastersys is definitely your best bet. Here's a tutorial on how to use it:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by anupam on 2009-07-12
> **earthpigg said:**
> 
```
dpkg-query -l | grep (something to remove the first four characters of every line) | grep (something to remove everything in a line starting with the first space) > packinfo
```


if someone can replace my (parenthesis) with an actual command or option of some type, the result would be a text file containing the package names and *_nothing else_*.

using that file as the pattern, we could then install the exact same packages on multiple machines with exactly _one command per machine._

dpkg-query -l | cut -d" " -f 3 > packinfo

---

### Post by Gizenshya on 2009-07-12
it filled up the ubuntu partition and got stuck.  I had to quit it, and force remove all the files.

how do I make it use another directory?

---

### Post by earthpigg on 2009-07-12
> **Gizenshya said:**
> it filled up the ubuntu partition and got stuck.  I had to quit it, and force remove all the files.

how do I make it use another directory?

downloading all the packages is what filled up the ubuntu partition?

one option is to download them on another machine and copy all the debs from /var/cache/apt/archives on a machine that does not have storage space issues to a thumb drive or external hard drive, and then run them from that external hard drive.

---

### Post by Gizenshya on 2009-07-12
no, sorry lol

I meant I got everything installed but when I tried to make the backup, it filled up the free space on the ubuntu partition (only aobut 2.5 gigs was initially free).

how do I make that program put the files in another drive?

---

### Post by aysiu on 2009-07-12
> **Gizenshya said:**
> it filled up the ubuntu partition and got stuck.  I had to quit it, and force remove all the files.

how do I make it use another directory?
Are you talking about Remastersys?

---

### Post by Gizenshya on 2009-07-12
yeah, I want it to go to host or somewhere, not to /home/remastersys/blah

---

### Post by aysiu on 2009-07-12
> **Gizenshya said:**
> yeah, I want it to go to host or somewhere, not to /home/remastersys/blah
Click on *Modify the remastersys config file to customize options*

Then double-click *Working Directory* and select the place you want it to build your customized Ubuntu.

But also be sure to double-click *Files to Exclude* and exclude that place as well.

---

### Post by Gizenshya on 2009-07-12
ok, but now it says in the terminal where it runs, that /host/remix/remastersys/blah blah blah is not a directory (the folders that I originally deleted in the remastersys /home/ folder).  I thought it would create more there.. but apparently not.  so do I need to reinstall?  and then just copy those folders to the new directory manually?

---

### Post by Gizenshya on 2009-07-12
removed...

I went to the site and added their repository and all is well with the install now...

but I still need to see if I can get it to use the host working directory...

---

### Post by CJ Master on 2009-07-12
There's a simpler way: Simply create a bash script with an apt-get of everything you want.

Then make a minimal Ubuntu install and run it. It'll grab everything you want and no more.

---

