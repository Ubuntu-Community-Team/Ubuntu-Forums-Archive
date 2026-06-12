---
title: "I don't know any terminal commands or code"
date: 2010-06-03
forum: The Cafe
---

### Post by isee on 2010-06-03
I really appreciate everything every developer has ever contributed to everything I run on my computer.  I really, really, really wish I knew code.  But I don't.  And terminal commands are to me to request a second opinion, because I can only cut and paste.

Ubuntu has been very good to me!

---

### Post by ssj6akshat on 2010-06-03
dude just chill.You will learn gradually.

---

### Post by Legendary_Bibo on 2010-06-03
> **isee said:**
> I really appreciate everything every developer has ever contributed to everything I run on my computer.  I really, really, really wish I knew code.  But I don't.  And terminal commands are to me to request a second opinion, because I can only cut and paste.

Ubuntu has been very good to me!

You'll learn :D
I was clueless about them, but now I'm starting to understand how they work and remember key functions. The ubuntu website even has a guide for understanding common commands.

---

### Post by kaldor on 2010-06-03
The problem is that people usually compare MS DOS commands to Linux, which is a bad way to go about it.

The command prompt on Windows is usually accociated with geeks and such, but on UNIX systems it's more common and, in my opinion, easier to learn.

Here are some examples... 

"pwd" (Print Working Directory) will show you what directory you are in. So, for example, when you load up the terminal and type "pwd" it should say /home/username :)

cd (change directory) is how you navigate the folders. In your home folder, you want to access your pictures folder and list what is inside. You will type..

```

cd Pictures
ls

```

cd Pictures will bring you to your pictures folder and ls (L, not i) will list the files. You can narrow it down to only one file type, too. 

```

ls *png
ls *jpg
ls *whateverformatyouwant

```

Seems hard at first, but it isn't at all. Just takes practice :)

I will advise you to do your updating etc by the command line so that you can feel more comfortable.

Here's a quick overview...

"sudo" allows a normal user to use root (superuser/administrator) priveleges. apt-get is the package management tool. So, some examples...

Refresh:
```
sudo apt-get update
```

Upgrade:
```
sudo apt-get upgrade
```

Install something:
```
sudo apt-get install firefox
```

Uninstall:
```
sudo apt-get remove firefox
```

etc, etc. 

Sorry for the longish post, but maybe it helped a bit :)

Oh, and you don't need to know any code at all. I don't!

---

### Post by RiceMonster on 2010-06-03
Cool story bro.

---

### Post by wojox on 2010-06-03
> **isee said:**
> I can only cut and paste.

Type them in. It will help you learn and remember them better. :)

---

### Post by DrMelon on 2010-06-03
I knew nothing of terminal commands when I first grabbed linux, but the best way to learn is to just keep using Linux - you pick up most of the stuff within 3 months.

---

### Post by juancarlospaco on 2010-06-03
But a lot of people *works on/do wonderfulll things* on Ubuntu and dont code,
*i.e. Designers*

---

### Post by 98cwitr on 2010-06-03
make this your new wallpaper

[http://www.mattiasgeniar.be/wp-content/uploads/2008/10/linux-wallpaper-for-beginners.jpg](http://www.mattiasgeniar.be/wp-content/uploads/2008/10/linux-wallpaper-for-beginners.jpg)

---

### Post by 2cute4u on 2010-06-03
Just for fun, I uninstalled  the terminal when I installed lucid, just to see how well I could get along without it.  So far it hasn't been a problem. Ubuntu has finally reached the point, where the GUI is good enough to make the terminal optional.

---

### Post by chris200x9 on 2010-06-03
> **98cwitr said:**
> make this your new wallpaper

[http://www.mattiasgeniar.be/wp-content/uploads/2008/10/linux-wallpaper-for-beginners.jpg](http://www.mattiasgeniar.be/wp-content/uploads/2008/10/linux-wallpaper-for-beginners.jpg)

lol, that was my wallpaper for a while :)

---

### Post by TheNessus on 2010-06-03
> **2cute4u said:**
> Just for fun, I uninstalled  the terminal when I installed lucid, just to see how well I could get along without it.  So far it hasn't been a problem. Ubuntu has finally reached the point, where the GUI is good enough to make the terminal optional.

 Well, sometimes I use the terminal so I can have more power in GUI. For example, I can't copy things to my external hard drive with my own user when using GUI. So I open a terminal and simply use "sudo nautilus" (or "sudo dolphin", then I got GUI with root power.

---

### Post by isee on 2010-06-05
Really cool all! :guitar:


I'm without any Windows at all now.  Just let 10.04 clean install the whole HDD.  I wasn't about to do the Windows/Application Recovery thing b/c I didn't want all the crap that installs, and the only other option is Windows SP1 and me install only the drivers and then update for hours.

I'm a little too lazy for that.  I have to get it done by tax time next year though.  Oh well! :)

By that time I hope to be able to make a partition for Windows and install it there and still be able to boot Linux, which didn't work so well the first time, thus my Ubuntu-only box.

Cheers!

Oh by the way I just figured it was time to erase my old windows install.  I was hesitant, because it did work, but I want a clean new one with just drivers.

---

### Post by dragos240 on 2010-06-05
If you want to learn. Just use the following:

sudo (allows the user to access a program using administrator privileges)
sudo apt-get install [package] (install a package)
ls (**L**i**s**t, lists files and folders)
pwd (tells you the directory you're in, however I think that's unnecessary in ubuntu as it says it on the laft hand side anyway.)
cat [file] (Lets you take a peak of what's inside a file)
echo [message] (echos a message, you type it, it repeats it.)

I could list commands all night, but I have to get to bed. OH! And one more.

man [command] (use this often, don't know how to use a package do man [command name]

---

### Post by isee on 2010-06-05
> make this your new wallpaper

[http://www.mattiasgeniar.be/wp-conte...-beginners.jpg]("http://www.mattiasgeniar.be/wp-content/uploads/2008/10/linux-wallpaper-for-beginners.jpg")Awesome!  I have, and it is exactly what one needs to practice and familiarize with Terminal.

>  Just for fun, I uninstalled  the terminal when I installed lucid, just  to see how well I could get along without it.  So far it hasn't been a  problem. Ubuntu has finally reached the point, where the GUI is good  enough to make the terminal optional.     You're right!  If I did not want to learn more I could stop here.  I've been running Ubuntu for over a year and I do not need the Terminal for my computing needs.

However, what I did just over a year ago was launch on an exploration, and in the words of Major Tom, I think my spaceship knows which way to go...

---

### Post by Shining Arcanine on 2010-06-05
> **isee said:**
> I really appreciate everything every developer has ever contributed to everything I run on my computer.  I really, really, really wish I knew code.  But I don't.  And terminal commands are to me to request a second opinion, because I can only cut and paste.

Ubuntu has been very good to me!

[http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628](http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628)
[http://www.amazon.com/Unix-Programming-Environment-Prentice-Hall-Software/dp/013937681X/ref=pd_sim_b_9](http://www.amazon.com/Unix-Programming-Environment-Prentice-Hall-Software/dp/013937681X/ref=pd_sim_b_9)

Those two should be a good start. For further reading, read the following books:

[http://www.amazon.com/C-Programming-Language-Special/dp/0201700735/ref=sr_1_1](http://www.amazon.com/C-Programming-Language-Special/dp/0201700735/ref=sr_1_1)
[http://www.amazon.com/Compilers-Principles-Techniques-Tools-2nd/dp/0321486811/ref=sr_1_1](http://www.amazon.com/Compilers-Principles-Techniques-Tools-2nd/dp/0321486811/ref=sr_1_1)
[http://www.amazon.com/Art-Computer-Programming-Volumes-Boxed/dp/0201485419/ref=sr_1_1](http://www.amazon.com/Art-Computer-Programming-Volumes-Boxed/dp/0201485419/ref=sr_1_1)
[http://www.amazon.com/Art-Computer-Programming-Vol-Fascicles/dp/0321637135/ref=sr_1_2](http://www.amazon.com/Art-Computer-Programming-Vol-Fascicles/dp/0321637135/ref=sr_1_2)
[http://www.amazon.com/Computer-Organization-Design-Fourth-Architecture/dp/0123744938/ref=sr_1_1](http://www.amazon.com/Computer-Organization-Design-Fourth-Architecture/dp/0123744938/ref=sr_1_1)

After reading all of those, you should know just about everything you will ever need to know to program computers. No advanced degree is required.

---

### Post by Austin25 on 2010-06-05
Get a virtual computer running than try anything you can think of. Try to crash it if you can. anything to get practice.

---

### Post by MedianMajik on 2010-06-05
If you feel like learning more about the commandline and just getting under the hood you should try out a live CD of [#! Crunchbang]("http://crunchbanglinux.org/"), which is based off Ubuntu/Debian.

---

### Post by 2cute4u on 2010-06-06
> **TheNessus said:**
> Well, sometimes I use the terminal so I can have more power in GUI. For example, I can't copy things to my external hard drive with my own user when using GUI. So I open a terminal and simply use "sudo nautilus" (or "sudo dolphin", then I got GUI with root power.

You don't need the terminal for that, if you need to have **nautilus-gksu** installed. In Nautilus just right click on  a folder and select "Open as administrator".

---

