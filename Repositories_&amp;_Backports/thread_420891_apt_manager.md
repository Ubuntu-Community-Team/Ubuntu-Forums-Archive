---
title: "apt manager"
date: 2007-04-24
forum: Repositories &amp; Backports
---

### Post by kelvin spratt on 2007-04-24
I would like to re-enable apt manager in fiesty as since upgadiing it tells me i need root privelages to use it
and to use sudo but i don't know what to write to activate activate it please anwer so i can copy and paste
to the terminal as i'm dyslexic

---

### Post by paparucino on 2007-04-25
> **kelvin spratt said:**
> I would like to re-enable apt manager in fiesty as since upgadiing it tells me i need root privelages to use it
and to use sudo but i don't know what to write to activate activate it please anwer so i can copy and paste
to the terminal as i'm dyslexic

The sequance of commands

The first one is to update your local  list of programs with repos

```

sudo apt-get update

```

Now you have two choices:

Upgrade all the packages

```

sudo apt-get upgrade

```

Upgrade all the packages and all dependencies

```

sudo apt-get dist-upgrade

```

I prefer last choice since it keeps my system always update

Hope it helps

---

### Post by kelvin spratt on 2007-04-25
thanks for trying to help but your solution is not the problem this is the problem adept starts but i get this message
You will not be able to change your system settings in any way (install, remove or upgrade software), because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions 
what do i do now

---

### Post by paparucino on 2007-04-25
> **kelvin spratt said:**
> thanks for trying to help but your solution is not the problem this is the problem adept starts but i get this message

Substitute apt-get with adept and it'll work

---

### Post by kelvin spratt on 2007-04-25
it says command not found please write so i can copy paste thank you

---

### Post by paparucino on 2007-04-25
> **kelvin spratt said:**
> it says command not found please write so i can copy paste thank you
```

sudo apt-get install adept

```

Take care that you need KDE installed to use adept

---

### Post by kelvin spratt on 2007-04-25
it installs and runs but does not allow any changes

---

### Post by paparucino on 2007-04-25
> **kelvin spratt said:**
> it installs and runs but does not allow any changes
Hold on! :-)
It doesn't allow changes or it doesn't perform changes?
In the second case:
- what repos are you using
- did you change "feisty" to "gutsy"
- did you run the update

In the first case: let me knoe the error, if one.
Gutsy repos are open and I've already changed about 20/30 files

---

### Post by kelvin spratt on 2007-04-25
i'm on fiesty  i used edgy before this and apt manager worked as default but not in fiesty as i said it opens up
then i get the error message that i posted saying i can't change anything i press ok it loads all files but thats it all butons are disablled 

                                          READ ONLY MODE: NEED ROOT PRIVILEGES-APT MANAGER


You will not be able to change your system settings in any way (install, remove or upgrade software), because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions

This is what i get and i really appreciate your time and help

---

### Post by bernied on 2007-04-25
May I suggest that the problem is simply that kelvin is trying to run apt manager as himself, not as root? So it needs to be run using kdesu (if using kde) or gksudo (if using gnome).

So, kelvin, some questions for you:
- are you using gnome (standard ubuntu) or kde (kubuntu)?
- when you run apt manager, do you use a menu item? 

If you just click on a menu item, or a desktop item, or a panel icon, can you find out the real name of the application? I think you need to right-click on the item that you normally select, then select edit, then there should be a box for 'application' or 'command', paste the contents of that box here.

You can fix the command yourself. If you use gnome, add the word 
gksudo
 in front of the command.

If you use kde, add the word 
kdesu
instead.

EDIT: You will need to save the item after you make changes - there should be a button for 'save' or a picture of a disk to press.

If you run apt manager from the command line then use one of these words before the command.

Does this help?

---

### Post by paparucino on 2007-04-25
> **kelvin spratt said:**
> i'm on fiesty  i used edgy before this and apt manager ...
This is what i get and i really appreciate your time and help

Wait....I think there is a little confusion. 
Are you using aptitude, apt-get, adept?
Are you using Feisty with Gnome, KDE, XFCE?
Are you running the command vi terminal or via Alt-F2
If you cannot use adept, which is for KDE eviroment, try

```

sudo apt-get update

```

```

sudo apt-get dist-upgrade

```

It MUST WORK!!!

If you are running commands via Alt-F2


Wait....I think there is a little confusion. 
Are you using aptitude, apt-get, adept?
Are you using Feisty with Gnome, KDE, XFCE?
Are you running the command vi terminal or via Alt-F2
If you cannot use adept, which is for KDE eviroment, try

```

gksudo apt-get update

```

```

gksudo apt-get dist-upgrade

```

If this again doesn't work, check the permissions of the files
Goto the folder/directory where aptitude,apt-get,adept are.
Right click on one of these files, then "properties" then "permission" and check if your user is listed

---

### Post by kelvin spratt on 2007-04-25
thanks for your interest i'm using gnome if you read my 1st post i'm word blind
and could do with things put down so i can copy and paste to make things work as they should
most things work ok but codes are very difficult for me its bad enough with spell check

---

### Post by kelvin spratt on 2007-04-25
i've done all that still comes up the same permissions are to root but normally you are asked for your password before the program loads up i get program loading up then the message then the program finishes loading and all the buttons are shaded its the password screen thats not loading anyway thanks people for your time
i hope somebody can figure this out

---

### Post by bernied on 2007-04-25
ok, try this in a terminal
```
gksudo apt_manager
```

If this works, go back to my last post to fix the issue properly - see if you can make some sense of it.

I'm sorry I don't know what it is like to be dyslexic, so don't know how to improve my posts.

---

### Post by paparucino on 2007-04-25
> **bernied said:**
> 
I'm sorry I don't know what it is like to be dyslexic, so don't know how to improve my posts.
He has some problems to coordinate movements with orders received from brain. This is due to some brain damage.

---

### Post by bernied on 2007-04-25
I think you are mistaken.
Read [this](http://en.wikipedia.org/wiki/Dyslexia).

---

### Post by paparucino on 2007-04-25
> **bernied said:**
> I think you are mistaken.
Read [this](http://en.wikipedia.org/wiki/Dyslexia).
I wrote the same concepts using low-low-low meaning :-)

---

### Post by kelvin spratt on 2007-04-25
people thanks for your concern dyslexic means what you see and write are not always what it is in my case i read by word requisition thats why i need to copy and paste as code etc i can't requinise as words that i do not
know but most people that are dyslexic are above ave iq ie over 125  anyway back to the prob idid the last thing
and got the root permisions notice put in the password clicked ok thinking the prog will start but nothing over to you

---

### Post by bernied on 2007-04-25
OK, try this one:
```
gksudo synaptic
```

Does this work?

The name I used for the program was wrong.
We have to find the right name.

Before you had this trouble, how did you start apt manager?

Did you use the menu?
Did you use a button?

---

### Post by bernied on 2007-04-25
I think you need to use [Skype](http://www.skype.com/intl/en-gb/download/skype/linux/), or something like it.

---

### Post by kelvin spratt on 2007-04-25
apt manager has not worked since i upgraded to fiesty before i always used the menu
synaptic always works ok 
its just apt as its easyer to add repros 
but it will not be the end of the world if it does not work
i read that wiki and find it not very accurate and more of an opinion than anything
as it can be a very complex problem such a spacial awareness and coordination between what you see and what you write and then see in my case its what i write at the time can look correct but next time i read it wrong
but because 50years ago we learned by repetition i can recognize most common words when i read them
but code could be anything as with passwords

---

### Post by bernied on 2007-04-25
You must be a very patient person.

Try this:
```
gksudo adept_manager
```

Is that it?

---

### Post by kelvin spratt on 2007-04-25
thank you very much that will do it opens and all the buttons work 
thank you

---

### Post by bernied on 2007-04-25
You are welcome.

Can anyone here tell kelvin how to fix this in the menu?
(I use kde, not gnome)

Otherwise it will always be copy/paste into a terminal.

---

### Post by paparucino on 2007-04-25
> **bernied said:**
> You are welcome.

Can anyone here tell kelvin how to fix this in the menu?
(I use kde, not gnome)

Otherwise it will always be copy/paste into a terminal.
I think he should have to use Synaptic which is the interface for apt-get.
To solve the problem of the passw, if he is not on a net but on a single computer, IMHO, it should be better to login as root.

---

### Post by jmikeh on 2007-04-30
> **bernied said:**
> You are welcome.

Can anyone here tell kelvin how to fix this in the menu?
(I use kde, not gnome)

Otherwise it will always be copy/paste into a terminal.

Right click Applications, then Edit Menus. Click System Tools menu.  Then right click Adept item, paste the command in an voila..

---

