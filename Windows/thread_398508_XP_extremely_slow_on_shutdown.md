---
title: "XP extremely slow on shutdown"
date: 2007-04-01
forum: Windows
---

### Post by insane_alien on 2007-04-01
I have XP installed on a little 5GB partition on my HDD and its been getting extremely slow on shutdown. we're no t talking 5 minutes here, last one took 35 minutes exactly to shut down. normally i would put it down to feisties superb shutdown times but this is excessive even for XP. 

anyone got any ideas?

---

### Post by 1/0 on 2007-04-01
How full is the partition. Windows, as I remember, gets really slow when the partitions gets full (~80%).

---

### Post by insane_alien on 2007-04-01
only about 50% theres not much on it. just office and a silly little game i'm addicted to but can't get working on wine.

its been exactly the same for a week now. there have been no changes.

---

### Post by jariku on 2007-04-01
Try running scandisk and defrag.

---

### Post by 1/0 on 2007-04-01
One of the worst things in Windows is the lack of log files. Its really difficult to track down problems. I used to be tech support for Windows 7 years ago and my recommendation was usually: reinstall. 

Its possible to find the cause but usually it takes more effort than reinstalling. I don't know what you've done so far but some things to do is:

[LIST]
[*]Check for viruses with a good AV (Norton really lowers performance and finds few viruses compared to NOD32, Kaspersky and F-Secure).
[*]Check for spyware (ad-aware, AVG antispyware, spybot)
[*]Disc cleanup
[*]Scan for errors
[*]Update
[*]Defragment
[*]You could run services.msc (or even msconfig if you know what you're doing) and try stopping services and reboot to eliminate the causes. Don't stop important functions though.
[*]Disable "restart on system failure" in properties, My Computer. That way you might get error messages.
[/LIST]

I also found [this guide]("http://aumha.org/win5/a/shtdwnxp.php") that goes through a few things that could cause problems.

---

### Post by insane_alien on 2007-04-01
[LIST]
[*]Check for viruses with a good AV (Norton really lowers performance and finds few viruses compared to NOD32, Kaspersky and F-Secure).  <Not on the internet. Although, i will run it through with the AV the uni provided me with when i got it.
[*]Check for spyware (ad-aware, AVG antispyware, spybot) <-again, not on the internet but i'll run it anyway.
[*]Disc cleanup <- this is setup to get run once a month
[*]Scan for errors <-also runs once a month
[*]Update <-not on the internet but i'll give it a shot
[*]Defragment <- runs once a month
[*]You could run services.msc (or even msconfig if you know what you're doing) and try stopping services and reboot to eliminate the causes. Don't stop important functions though. <- really can't be bothered with that but i'll maybe give it a go if i'm bored.
[*]Disable "restart on system failure" in properties, My Computer. That way you might get error messages. <- it IS disabled, had to check it though.
[/LIST]

i'll have a peek at th guide you linked to.

<EDIT> okay, so i tried the guide and went through it. the suggestions that haven't already been implemented at some point in the installations past have been applied and its still slow. timed at 37minutes last shutdown.

---

