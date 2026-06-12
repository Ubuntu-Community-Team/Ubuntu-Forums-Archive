---
title: "How do I enter Commands in the Terminal Please HELP"
date: 2009-12-15
forum: The Cafe
---

### Post by alexfish on 2009-12-15
Can any One Show Me How To Enter Commands in the Ubuntu Terminal 

I am Total Novice at This

The first line is very confusing ?

it Shows  alexfish-ubuntu@not-win7-or-bing-desktop:~$

Screen shot attached



[SIZE=3]Hi all[/SIZE]

    [SIZE=3][COLOR=Navy][ SOLVED] [/COLOR]Can any One Show Me How To Enter Commands in the Ubuntu Terminal [/SIZE][SIZE=3][COLOR=Navy] [-o< 

Thanks for All the input ,Interesting Reading / and fun to

[/COLOR][/SIZE]Just in TIME FOR CHRISTMAS:lolflag:

---

### Post by pwnst*r on 2009-12-15
rofl.

---

### Post by ubername on 2009-12-15
alexfish-ubuntu@not-win7-or-bing-desktop:~$

is called the 'prompt'. It can be changed but basically it shows your username and the machine you are on (and the ~ means you are in your home folder). The $  is the end of the prompt. You type (or paste) commands there. Note - in gnome-terminal you can use ctl-shift-v to paste things

---

### Post by wojox on 2009-12-15
WTF?   [Terminal HowTo]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by ~sHyLoCk~ on 2009-12-15
```
yes "windows " | tr -d "\n"
```

---

### Post by alexfish on 2009-12-15
> **wojox said:**
> WTF?   [Terminal HowTo]("https://help.ubuntu.com/community/UsingTheTerminal")




To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

alexfish-ubuntu@not-win7-or-bing-desktop:~$ sudo gobbledegook blah_blah -w -t -f aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots
[sudo] password for alexfish-ubuntu: 
sudo: gobbledegook: command not found
alexfish-ubuntu@not-win7-or-bing-desktop:~$ 

EH

---

### Post by Psumi on 2009-12-15
> **alexfish said:**
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

alexfish-ubuntu@not-win7-or-bing-desktop:~$ sudo gobbledegook blah_blah -w -t -f aWkward/ComBinationOf/mixedCase/underscores_strokes/and.dots
[sudo] password for alexfish-ubuntu: 
sudo: gobbledegook: command not found
alexfish-ubuntu@not-win7-or-bing-desktop:~$ 

EH

*facepalm* That was an obvious "example" and not a real command.

---

### Post by pwnst*r on 2009-12-15
[img]http://www.fishingfall.com/fishingfallimages/fishing.jpg[/img]

---

### Post by soni1770 on 2009-12-15
sudo ice-cream  is my fav

---

### Post by Bölvaður on 2009-12-15
this is utterly useless, but I guess you are just trying to feel comfortable with entering commands.. so try these.

this is pretty much just: learn by example.
```

whoami
sudo su [COLOR="Silver"]<and enter your password blindly>[/COLOR]
whoami
exit
whoami

ps -e
ps -e | more
ps -e | less
ps -e | grep gnome
ps -e | grep gnome | head -3

ls
ls -a
ls -a | grep gnome
ls -a | grep g..me
ls -a | grep g.me
ls -a | grep ^[A-Z]
ls -a | grep ^[0-9]
ls -a | grep [0-9]$
ls -R | grep png$

man ls
man ps
man grep

```

like I said, there is no real life gain from this... well perhaps sometimes... specially if you are automating somethings by scripts.

commands are nothing more than


name_of_a_program   -flag   name/of/a/file/or-other-imput

ohh ok I'll show you some useful things.

```

firefox www.ubuntuforums.org
firefox www.ubuntuforums.org &

wget http://imgs.xkcd.com/comics/sandwich.png
eog sandwich.png 
rm sandwich.png
eog sandwich.png 

```
well... the other stuff will change some things.

---

### Post by soni1770 on 2009-12-15
sudo chuck norris

 only! use this if you really need to, it's the most powerfull command out:popcorn:

---

### Post by audiomick on 2009-12-15
sudo apt-get install brain

is one I like.

---

### Post by RiceMonster on 2009-12-15
> **soni1770 said:**
> sudo chuck norris

 only! use this if you really need to, it's the most powerfull command out:popcorn:

You need to add some flags for that command to work, ie:

```
sudo chuck-norris --roundhouse
```

---

### Post by fromthehill on 2009-12-15
> **RiceMonster said:**
> You need to add some flags for that command to work, ie:

```
sudo chuck-norris --roundhouse
```
chuck norris doesn't need anyones permission to kick ***

---

### Post by Tristam Green on 2009-12-15
how i mine 4 fish

---

### Post by soni1770 on 2009-12-15
chuck norris doesn't sleep...  he waits

---

### Post by RiceMonster on 2009-12-15
> **soni1770 said:**
> chuck norris doesn't sleep...  he waits

He uses a nightlight. Not because he's afraid of the dark, but because the dark is afraid of him.

---

### Post by ctrlmd on 2009-12-15
should i laugh or should i worry :-\"

---

### Post by alexfish on 2009-12-15
> **soni1770 said:**
> sudo ice-cream  is my fav

Sounds nice It may cool down Frustrated Win 7 Users Trying use Bing Crosby:guitar:

---

### Post by alexfish on 2009-12-15
> **Bölvaður said:**
> this is utterly useless, but I guess you are just trying to feel comfortable with entering commands.. so try these.

this is pretty much just: learn by example.
```

whoami
sudo su [COLOR=Silver]<and enter your password blindly>[/COLOR]
whoami
exit
whoami

ps -e
ps -e | more
ps -e | less
ps -e | grep gnome
ps -e | grep gnome | head -3

ls
ls -a
ls -a | grep gnome
ls -a | grep g..me
ls -a | grep g.me
ls -a | grep ^[A-Z]
ls -a | grep ^[0-9]
ls -a | grep [0-9]$
ls -R | grep png$

man ls
man ps
man grep

```like I said, there is no real life gain from this... well perhaps sometimes... specially if you are automating somethings by scripts.

commands are nothing more than


name_of_a_program   -flag   name/of/a/file/or-other-imput

ohh ok I'll show you some useful things.

```

firefox www.ubuntuforums.org
firefox www.ubuntuforums.org &

wget http://imgs.xkcd.com/comics/sandwich.png
eog sandwich.png 
rm sandwich.png
eog sandwich.png 

```well... the other stuff will change some things.

Who are you  // man who

---

### Post by alexfish on 2009-12-15
> **audiomick said:**
> sudo apt-get install brain

is one i like.

?

---

### Post by audiomick on 2009-12-16
Didn't know that was there. It opens a terminal and does
```
gksu
```
in one go.

Be careful with that. I gives you root privileges, which means you can break your system with the wrong command.

You need root privileges for some stuff, but should be really sure about the commands you put in.

---

### Post by alexfish on 2009-12-16
> **audiomick said:**
> Didn't know that was there. It opens a terminal and does
```
gksu
```in one go.

Be careful with that. I gives you root privileges, which means you can break your system with the wrong command.

You need root privileges for some stuff, but should be really sure about the commands you put in.

Totally Agree /  Ubuntu     	version suppressed

---

### Post by MaxIBoy on 2009-12-16
Visit this website:
[http://linuxcommand.org/](http://linuxcommand.org/)
It's a little bit out of date (in that some things have been made easier since then,) but still a very good read.

---

### Post by alexfish on 2009-12-16
Here is a good one How Do You Get A Cup Of tea Out Of Ubuntu

Instead of a Cup Of coffee : Cos Tell You What I've Never Had Full Cup Of Ubuntu Yet

But This One Works#-o

---

### Post by alexfish on 2009-12-16
Forgot about this one 

Want To Do A Lot READING

 Clue 

 Do It Over tin of coffee //with the Terminal 

Amazing That One  Need Not Worry About The News Any More

easy Way

[http://www.tin.org/](http://www.tin.org/)

---

### Post by Gizenshya on 2009-12-16
> **RiceMonster said:**
> You need to add some flags for that command to work, ie:

```
sudo chuck-norris --roundhouse
```

careful, I heard that command is strikingly similar to...

```
sudo rm-rf /self
```

---

### Post by handy on 2009-12-16
Here is a course for using the Terminal, when you get through with part 1, you will see at the bottom of the page that there are links to 5 more parts is most likely that you will find all & more that you need in this easy going tutorial:

[http://ubuntuforums.org/showpost.php?p=398953&postcount=1](http://ubuntuforums.org/showpost.php?p=398953&postcount=1)

If you do become obsessed with the Terminal & need scripting knowledge then this is a good place to start:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

---

### Post by yester64 on 2009-12-16
> **alexfish said:**
> Can any One Show Me How To Enter Commands in the Ubuntu Terminal 

I am Total Novice at This

The first line is very confusing ?

it Shows  alexfish-ubuntu@not-win7-or-bing-desktop:~$

Screen shot attached

PLEASE HELP! [-o<

Thanks Advance 

alexfish

Yea, thats your prompt. Looks different from Windows, but its the same.
You would just enter commands like DF or CD.

Since you novice, i would recommend you a book i bought myself too. It explains the basic very well.
Beginning Ubuntu Linux.
I like to use it also as a paperweight. :)

Here is a good guide from the forum.
[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

Take care

---

### Post by alexfish on 2009-12-19
> **pwnst*r said:**
> [IMG]http://www.fishingfall.com/fishingfallimages/fishing.jpg[/IMG]

Looks Terminal This One Cos We ain't See A post Of the fish

  PS got The Chips ready

---

### Post by glnerd on 2009-12-19
Lolololololol

---

### Post by steveneddy on 2009-12-20
```
sudo apt-get install cowsay
```

after that installs, in terminal type

```
cowsay This is cool
```

---

### Post by alexfish on 2009-12-21
> **steveneddy said:**
> ```
sudo apt-get install cowsay
```after that installs, in terminal type

```
cowsay This is cool
```

[SIZE=2]Hi All[/SIZE]   

 [SIZE=4][COLOR=Navy]Look Above For All The Answers[/COLOR][/SIZE]

Thank you ,Thank You , I Could Kiss You  All ...............:guitar::popcorn::lolflag:
Have a merry Xmas

alexfish...............................:P

[SIZE=3][COLOR=Blue]
This One Is For Me

[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")[COLOR=Black]........... :[/COLOR]Karmic    [SIZE=1][COLOR=Black]Saved a copy In " Open Office "  Where it Won't  get Lost[/COLOR][/SIZE]
[/COLOR][/SIZE]

---

