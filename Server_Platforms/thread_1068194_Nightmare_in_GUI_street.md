---
title: "Nightmare in GUI street"
date: 2009-02-12
forum: Server Platforms
---

### Post by mistypotato on 2009-02-12
Hello,

Minutes ago I installed 8.10 server and was pleasantly surprised when I typed my URL into another computer (different network) and it proudly said :It Works!


But now all I have is a command line and I may as well be blind deaf and dumb in a unknown city.

Unless I get a GUI, I won't be able to do anything.

Can you please tell me how to install whatever GUI might be available?

BTW...

sudo apt-get install gdm   -----      returns "couldn't find package"
startx    -----    returns "The Program is not installed"
sudo apt-get install xinit   - ---   returns "package not available, but x11-common is"
sudo apt-get install x11-common    ---    returns "missing destination file"

thx

---

### Post by Iowan on 2009-02-12
I *should* let you discover the raw beauty of the CLI... but [here]("http://ubuntuforums.org/showthread.php?t=1060966") is a thread with some GUI advice.

---

### Post by mistypotato on 2009-02-12
> **Iowan said:**
> I *should* let you discover the raw beauty of the CLI... but [here]("http://ubuntuforums.org/showthread.php?t=1060966") is a thread with some GUI advice.


:lolflag:

Glad to see there ARE some here with a sense of humor.

---

### Post by Go_Big_Blue on 2009-02-12
> **mistypotato said:**
> Hello,

Minutes ago I installed 8.10 server and was pleasantly surprised when I typed my URL into another computer (different network) and it proudly said :It Works!


But now all I have is a command line and I may as well be blind deaf and dumb in a unknown city.

Unless I get a GUI, I won't be able to do anything.

Can you please tell me how to install whatever GUI might be available?

BTW...

sudo apt-get install gdm   -----      returns "couldn't find package"
startx    -----    returns "The Program is not installed"
sudo apt-get install xinit   - ---   returns "package not available, but x11-common is"
sudo apt-get install x11-common    ---    returns "missing destination file"

thx

Here - try reading through this thread.  It might help you out.

[http://ubuntuforums.org/showthread.php?t=1062105](http://ubuntuforums.org/showthread.php?t=1062105)

---

### Post by yknivag on 2009-02-12
Personally I wouldn't install a GUI - I'd use [webmin](http://www.webmin.com/deb.html) (see half way down the page for how to add the repository) and manage your server remotely.  However if you really want a GUI then:
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```
should do what you want.

---

### Post by mistypotato on 2009-02-12
Thanks Go but as I explained in my initial post, I tried those and none worked.

---

### Post by kerry_s on 2009-02-12
> **mistypotato said:**
> Thanks Go but as I explained in my initial post, I tried those and none worked.

look in your /etc/apt/sources.list, see that all your repo's a uncommented, than run> sudo apt-get update

---

### Post by mistypotato on 2009-02-12
I can see the file...but how am I supposed to see if somethings uncommented :confused:

Noobs really need "every" step explained  ;-)

I think as we get familiar with this stuff, we take a lot for granted.

When I type sudo gedit sources.list (I'm IN the apt directory and can see the file in the DIR list,
it just says "COMMAND NOT FOUND"

And someone had the nerve to ask why anyone needed a server GUI  LOL


thx

---

### Post by mistypotato on 2009-02-12
The server works...I can get to the "IT WORKS" page...but nothing else seems to .


Maybe I need to just trash it, start all over and re-install ???


This is definitely NOT a noobie friendly process  :-(

---

### Post by mistypotato on 2009-02-12
> **kerry_s said:**
> look in your /etc/apt/sources.list, see that all your repo's a uncommented, than run> sudo apt-get update

this give me a screen full of lines saying "FAILED TO FETCH blah blah blah......


Could not resolve 'security.ubuntu.com'

(abount 12 times)

---

### Post by unixeducation on 2009-02-12
Try:

```
sudo nano /etc/apt/sources.list
```

to use the nano editor. You don't have any GUI programs installed yet, so gedit isn't available.

---

### Post by boof1988 on 2009-02-12
> **mistypotato said:**
> When I type sudo gedit sources.list (I'm IN the apt directory and can see the file in the DIR list,
it just says "COMMAND NOT FOUND"

*For informational purposes*

gedit is a GUI based test editor (IIRC) and so it wont be installed (by default) with the server edition.

I use...

```

sudo nano <path to file>
``` for files requiring root privileges, or just

```
nano <path to file>
```

for cases which don't require root privileges.

I use nano even when I have a GUI (it's just my preference).  I believe ***nano*** is included with the server installation.  So you should be able to use it in the server edition if you chose to stay with the server edition.

---

### Post by mistypotato on 2009-02-12
> **unixeducation said:**
> Try:

```
sudo nano /etc/apt/sources.list
```

to use the nano editor. You don't have any GUI programs installed yet, so gedit isn't available.


SOMETHING THAT FINALLY WORKED!!   yaAAAAAy!!    

THX  :-)

---

### Post by mistypotato on 2009-02-12
tHE BAD NEWS is they were already uncommented.

---

### Post by mistypotato on 2009-02-12
It's still reporting that it could not resolve SECURITY.ubuntu.com'

Is there a way to check Internet Connectivity at the command line ?

Can I ping Google or something?

---

### Post by mistypotato on 2009-02-12
.............FLUSH.............


I was able to connect to my new server earlier but now I cant.

Something's gone wrong with my new server.



Time to start over

---

### Post by mistypotato on 2009-02-12
Darn!

Now when I'm trying to reinstall it gets to the point where it's mounting the CD and it fails saying the CD-ROM couldnt be mounted.

It wont go past that point now :confused:

I installed it 3 hours ago with no problem :confused:

---

### Post by mistypotato on 2009-02-13
Thanks for your help everyone :)

Got it all sorted out about 2:00am

---

### Post by hyper_ch on 2009-02-13
I just wonder why do you want to setup a server?

---

### Post by mistypotato on 2009-02-13
The company I work for needs it and I volunteered to try since I knew servers fairly well (WinXP) anyway.


btw...if that's your picture in your avatar...you look a lot like that actor...I can't think of his name or roles at the moment....

---

### Post by hyper_ch on 2009-02-13
if it's for a company on a business server (probably also hooked up to the net) thena  GUI is a big "no no". Although it takes longer learn the CLI. You'll benefit a lot more from it. Furthermore, if there's only a cli setup then none of your coworkes will try stupid things - because they will be in the situation where you are now - they don't know their way around.

The cli is not difficult. All you need to now is:

(1) moving along the filesystem hierarchy
(2) manipulate files/folders
(3) install/remove programs/services
(4) manage services
(5) get a grip of the logs

for each service you want to run there's tons and tons of help out there.

---

