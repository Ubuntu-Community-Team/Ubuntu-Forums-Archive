---
title: "What terminal commands do you use most often?"
date: 2008-06-11
forum: The Cafe
---

### Post by diablo75 on 2008-06-11
I'm putting together a blog about the Terminal, and am looking for some commands that are used most often.

The easy beginner commands that I can think of include ls, cd, mv, cp.... there's a lot out there to pick from.  What commands are best for beginners to learn?

Also, features like tab-completion are also well worth mentioning.  Are there any other tricks that I should know about?

---

### Post by robertchahine on 2008-06-11
aptitude
apt-get (remove install purge...)
locate
ln
gedit
nano
du 
df
find
fdiskl, lspci,for sure sudo and gksudo (difference between them)

---

### Post by robertchahine on 2008-06-11
by the way .
nice blog, i really like it.(especially the graphics and pictures)

---

### Post by diablo75 on 2008-06-11
> **robertchahine said:**
> by the way .
nice blog, i really like it.(especially the graphics and pictures)

Hey thanks!  :)

---

### Post by KingTermite on 2008-06-11
It probably was "nedit" until 2 days ago. Nedit was my favorite editor and I used it to edit any config type files. 2 days ago somebody here turned me on to Geany which is an even better editor and has a built in terminal window in a lower window pane to test out changes.

So now it will probably be "geany".

---

### Post by Sealbhach on 2008-06-11
Yeah, nice blog.

Recently I've used:

sudo halt

killall



.

---

### Post by Joeb454 on 2008-06-11
probably ```
(conky &)
cd
sudo shutdown -P now
```

---

### Post by diablo75 on 2008-06-11
I know I've used **init 6** to restart my computer from the command line before.  What are some other commands like this?... Does anyone know the origin of this init command?

---

### Post by aeiah on 2008-06-11
```

eject -t
cd
ls
sudo shutdown -h ti:me
sed
nano
grep
cat
scp -P port user@domain:/path/to/file /destination/file
wget
apt-get

```

the best part about the terminal are the pipes though

---

### Post by elvinatom on 2008-06-11
mkfs

---

### Post by Luke has no name on 2008-06-11
```
sudo rm -rf /
```

Not on my computer, of course.

apt-get and nano, smarttools.

---

### Post by diablo75 on 2008-06-11
> **Luke has no name said:**
> ```
sudo rm -rf /
```



Thanks for the reminder to warn others about risky/dangerous commands.  ;)

---

### Post by cardinals_fan on 2008-06-11
vim
cd
ls
rm
mv
cp

---

### Post by mthei on 2008-06-11
dpkg -i

---

### Post by diablo75 on 2008-06-11
> **robertchahine said:**
> for sure sudo and gksudo (difference between them)

...What is the difference between them?

---

### Post by bufsabre666 on 2008-06-11
> **diablo75 said:**
> ...What is the difference between them?

gksudo opens an application as root from outside the terminal while still allowing you to use the terminal for other things, with sudo it wont let you use the terminal again till the task is closed, or if you close the terminal youll quit the program

---

### Post by SomeGuyDude on 2008-06-11
I use apt-get mainly. Aside from "sudo nautilus" and "sudo update-manager -c -d".

---

### Post by diablo75 on 2008-06-11
> **bufsabre666 said:**
> gksudo opens an application as root from outside the terminal while still allowing you to use the terminal for other things, with sudo it wont let you use the terminal again till the task is closed, or if you close the terminal youll quit the program

There's another way to do this, right?  Like if you append a & after a command?.... I think, is that right?

---

### Post by id1337x on 2008-06-11
Most common terminal commands?

```

sudo 
gksudo
apt-get source
cd
ls
gedit
gcc
perl

./configure
make
make test
make install
make clean
make distclean

```

I prefer to compile things from source.

---

### Post by melrom on 2008-06-11
well, directory stuff is nice too.

```

mkdir
rmdir

```

That said, I like the basics you listed, i.e. cd, mv, ls.

---

### Post by ghindo on 2008-06-11
There's a thread somewhere in the Community Cafe that asked this question and then gave a command which told you the top ten terminal commands you had ever used.  I'll go looking for it after I post this.

---

### Post by bobdob20 on 2008-06-11
> **melrom said:**
> well, directory stuff is nice too.

That said, I like the basics you listed, i.e. cd, mv, ls.

Along with the basics, **exit** is useful if you are using a borderless window manager or just dont feel like clicking on that X button. **clear** is good for when cli programs don't revert the terminal back and just leave the bottom line showing.

---

### Post by ghindo on 2008-06-11
> **ghindo said:**
> There's a thread somewhere in the Community Cafe that asked this question and then gave a command which told you the top ten terminal commands you had ever used.  I'll go looking for it after I post this.Here's the thread I was referring to:

[http://ubuntuforums.org/showthread.php?t=472090](http://ubuntuforums.org/showthread.php?t=472090)

---

### Post by Therion on 2008-06-11
```
**sudo** make me a sandwich rm onion
```

---

### Post by bufsabre666 on 2008-06-11
> **Therion said:**
> ```
**sudo** make me a sandwich rm onion
```

no you need to split that up
```
sudo make me a sandwich
cd sandwich
rm onion
```

---

### Post by RebounD11 on 2008-06-11
> **bufsabre666 said:**
> no you need to split that up
```
sudo make me a sandwich
cd sandwich
rm onion
```

it could be like this:

```
sudo make me a sandwich && cd sandwich && rm onion
```

now on topic:

```
killall npviewer.bin
```

and since I posted this does someone know of a good 64-bit flash player plugin that works with youtube, speedtest.net and livescore.com?

---

### Post by diablo75 on 2008-06-11
> **ghindo said:**
> Here's the thread I was referring to:

[http://ubuntuforums.org/showthread.php?t=472090](http://ubuntuforums.org/showthread.php?t=472090)

Hey that's pretty cool!  I'll have to do some reading to split that code up so I know what each little bit does (just for fun later).  All the top 10's in that thread are good info too.  I like your Aphex Twin avatar by the way.

---

### Post by _DD_ on 2008-06-11
Now that everything is set up how I want it I don't really use the terminal often. If I do its usually to install software or...
```
$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```
...once in a while to make sure some config file hasn't changed by an update and my drive isn't suddenly being eaten again.

---

### Post by zmjjmz on 2008-06-11
```

gedit
espeak
sudo
ls
cd
rm
nano
ping
mplayer
make

```
This was generated from the aforementioned commands in the other thread.

---

### Post by Therion on 2008-06-11
> **bufsabre666 said:**
> no you need to split that up
```
sudo make me a sandwich
cd sandwich
rm onion
```
DAMN... Seems obvious once someone points it out.  

Anyone have the modifier for grey poupon?




And props to the original at [xkcd dot com](http://xkcd.com/149/): 

[img]http://www.trackback.it/img/sandwich.png[/img]

---

### Post by Sealbhach on 2008-06-11
> **Therion said:**
> 

And props to the original at [xkcd dot com](http://xkcd.com/149/): 

[img]http://www.trackback.it/img/sandwich.png[/img]

That made me laugh. I must be getting it.:)


.

---

### Post by NJC on 2008-06-11
gedit
top
free
locate

---

### Post by elashish on 2008-06-11
apt-cache (search, policy, show)

i wish i knew a better way to know if I have a package installed. any help?

---

### Post by grossaffe on 2008-06-11
sudo apt-get install more RAM

---

