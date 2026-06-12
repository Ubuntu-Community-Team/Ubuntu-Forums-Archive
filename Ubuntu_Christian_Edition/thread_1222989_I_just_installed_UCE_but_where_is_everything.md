---
title: "I just installed UCE but where is everything?"
date: 2009-07-25
forum: Ubuntu Christian Edition
---

### Post by Jerriy on 2009-07-25
I just installed ubuntu christian edition. I opened a terminal window and typed the following command and pressed "enter":
```
# wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

The installation went on then it finished. Then, well then what? 

Where is everything?(I don't notice any new thing on my screen, no icons of Xiphos or OpenSong or E-Sword installer, I don't see any change

---

### Post by Jerriy on 2009-07-25
I don't see no new wallpapers

---

### Post by Jerriy on 2009-07-25
Have I missed something? What one earth is going on?

---

### Post by Jerriy on 2009-07-25
Hello?

---

### Post by RevJack on 2009-07-25
Did you try rebooting?

---

### Post by david_kt on 2009-07-25
> **Jerriy said:**
> I just installed ubuntu christian edition. I opened a terminal window and typed the following command and pressed "enter":
```
# wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

The installation went on then it finished. Then, well then what? 

Where is everything?(I don't notice any new thing on my screen, no icons of Xiphos or OpenSong or E-Sword installer, I don't see any change

Make sure the command do not start with #.
For desktop wallpaper, it is not included yet in the repository.
For GDM theme, you must select ubuntu -ce from:

system >> administration >> login windows

but other then that, all should be available.

DK

---

### Post by Jerriy on 2009-07-25
> **david_kt said:**
> Make sure the command do not start with #.Ah that was a typo. Just to be sure I did it again (without #) but nothing happenend (when I file-search the only new file I find is the christian-edition iso file that is downloaded at the very beginning before the installation commences. Other than that I see no other file associated with ubuntu christian edition in my computer

> For desktop wallpaper, it is not included yet in the repository.Okay
> For GDM theme, you must select ubuntu -ce from:

system >> administration >> login windowsI don't see no "ubuntu -ce" anywhere there

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122434&d=1248579114[/IMG]

> but other then that, all should be available.

DKAll should be, but none is :)

---

### Post by Jerriy on 2009-07-25
Maybe the problem is related to what happenes during installation?

---

### Post by david_kt on 2009-07-26
> **Jerriy said:**
> Maybe the problem is related to what happenes during installation?

Could try:
```
sudo apt-get install opensong
```

and post here what is the error.

And then check also:

```
sudo apt-get install usplash-theme-ubuntu-ce
```


and post here what is the error.

DK

---

### Post by david_kt on 2009-07-26
There might be a conflict between 64 and 32 bit packages, as such I have created separate repository.

For 32 bit:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

For 64 bit:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

```

DK

---

### Post by Caraibes on 2009-07-26
I must say the CE login window is not available here neither... I never paid attention to this, as I have my own tweaked login already, but went to look after reading this post... No Ubuntu_CE in the login windows...

---

### Post by david_kt on 2009-07-26
> **Caraibes said:**
> I must say the CE login window is not available here neither... I never paid attention to this, as I have my own tweaked login already, but went to look after reading this post... No Ubuntu_CE in the login windows...

You have to activate from:

System > Administration >Login Windows

And then click "local" tab.

You should see ubuntu ce. I have not found a way to activate it automatically.

DK

---

### Post by trulan on 2009-07-26
Yeah, it's there.  It's called 'human' in bold print, Ubuntu Christian edition is in rather fine print.  Also, no desktop icons are installed (which is fine).  The items are in the start menu.  (Xiphos is under Accessories, Dansguardian GUI is under System - Administration, etc.)

The only 'obvious' changes that were made automatically were the startup and shutdown splash screens.

---

### Post by Jerriy on 2009-07-26
> **david_kt said:**
> There might be a conflict between 64 and 32 bit packages, as such I have created separate repository.

For 32 bit:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
```

For 64 bit:

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

```

DK

Yes that did it! I see stuff now (haven't tested it all but we'll see)

Thank you so much

---

### Post by Jerriy on 2009-07-26
> **Caraibes said:**
> I must say the CE login window is not available here neither... I never paid attention to this, as I have my own tweaked login already, but went to look after reading this post... No Ubuntu_CE in the login windows...It's a copy of the ubuntu-jaunty login-screen/window image 

That's why I have now two identical login windows in my "login window preferences" (i.e. the one that already pre-existed which is titled 'HUMAN ubuntu default welcome theme' and the other new one which is 'HUMAN ubuntu ce welcome theme'.

---

### Post by Caraibes on 2009-07-27
Ok, guys.. I found it... But I won't use it, as I really dislike the Jaunty Human GDM... I am using the "gnome color" (Arc-Brave) GDM, very nice, very smooth... Anyway, good job !

---

