---
title: "Ubuntu server 7.10 no GUI"
date: 2008-04-03
forum: Server Platforms
---

### Post by LT72884 on 2008-04-03
So i needed to install ubuntu server on two machines for my schools lab tonight. Well i finish one but whn it boots up, there is no GUI. Just a TTY. So i try a sudo reboot and it gives me a sendmail:fatal error.
I try startx but says it cant find a directory and that xinit is not installed. 

I try sudo apt-get install xinit

says it cant find that file or directory. 

Did i have a bad install?


Thanx in advance

---

### Post by justin whitaker on 2008-04-03
> **LT72884 said:**
> So i needed to install ubuntu server on two machines for my schools lab tonight. Well i finish one but whn it boots up, there is no GUI. Just a TTY. So i try a sudo reboot and it gives me a sendmail:fatal error.
I try startx but says it cant find a directory and that xinit is not installed. 

I try sudo apt-get install xinit

says it cant find that file or directory. 

Did i have a bad install?


Thanx in advance

There is no GUI on a server install. You want to apt-get (or aptitude) ubuntu-desktop if you really want a GUI.

---

### Post by LT72884 on 2008-04-03
Here is some more info. 

when i boot it starts the services but when it gets to running local boot scripts, it shows a flashing cursor under it and stays like that till i hit enter. once i hit enter, it asks me to og in.

---

### Post by LT72884 on 2008-04-03
> **justin whitaker said:**
> There is no GUI on a server install. You want to apt-get (or aptitude) ubuntu-desktop if you really want a GUI.


You dont know how moronic i feel right now. Well i shouldnt feel to bad. never used a server before.

thanx for the info though.

---

### Post by LT72884 on 2008-04-03
ARG. i cant sudo. for soem reason after i enter the password, it says that sendmail: fatal error user not in suders file. 

I know i have to be in that file because it asked me for my username during install for admin purpuses

---

### Post by schneider707 on 2008-04-03
so ur saying when you do something like ```
sudo apt-get update
``` it reports that message? Does it do it to any sudo lines?

If not, you can do ```
sudo passwd root
``` then type ur acct password in, then type a new root password. Once thats all done, just type su, then the new root password and you will have root powers.

Hope you can sudo into something, cause that is bad if you can't.

---

### Post by mopp4 on 2008-04-04
If you absolutely need a GUI here is the command for installing GNOME:

```
sudo apt-get install xserver-xorg xfonts* gnome
```

Honestly, even if you need the GUI, you'll soon realize that your using the command line to get pretty much anything done. I hope this helps.

---

### Post by hyper_ch on 2008-04-04
what do you need a gui for on a server?

---

### Post by jonabyte on 2008-04-04
Is it me, or should they put some sort of note on the Ubuntu page that the server does not come with a gui, or even somewhere when installing.

When I first installed the server version I was pleasantly surprised that it did not have a gui, since I was actually looking for something like that.

:)

---

### Post by rickyjones on 2008-04-04
> **hyper_ch said:**
> what do you need a gui for on a server?

Some people, like myself, find that they can be more productive with a GUI on the server. If I need to test Apache I can do it right from the server to make sure that it is working on localhost. I can have multiple terminals open across multiple desktops. I can quickly send an email while working in the data center.

Not everyone likes working with the single terminal :P

Sincerely,
Richard

---

### Post by roaldz on 2008-04-04
> **rickyjones said:**
> Some people, like myself, find that they can be more productive with a GUI on the server. If I need to test Apache I can do it right from the server to make sure that it is working on localhost. I can have multiple terminals open across multiple desktops. I can quickly send an email while working in the data center.

Not everyone likes working with the single terminal :P

Sincerely,
Richard

You can test apache on localhost with netstat, nc, links, telnet.
You can use all TTY´s you like for your multiple terminals, and with screen you can use more at a time.
Emailing can also be done with the commandline.

There is no need for a GUI on a server - it sucks up memory, processor resources and can cause hangs.  I´d go with a pure commandline install. Remember, the commandline itself is a GUI too! (only then its called a CLI)

Roald

---

### Post by banewman on 2008-04-04
There are six tty's and with screen the number is endless.
:)

---

### Post by hyper_ch on 2008-04-04
there are even cli-based email programs... with screen or six ttys you get teh same confort....

---

### Post by jonray74 on 2008-04-04
Hello,

I hope i'm not too late in this. If you want to have GUI for your Ubuntu Server, you can do the following:

once you login in ubuntu using your account, do the ff:

1.) ***sudo passwd root***
 - this will ask you to change the root password. Make sure you enter a password you can remember for root accounts. Once that's done...next step

2.) ***su***
 - this command is the S-uper U-ser mode, or ROOT account. You need this to install apps, or install the GNOME desktop. Once you login as ROOT, do next step..

3.) ***sudo apt-get update***
 - this will retreive any updates for your Ubuntu server. Make sure you have your Ubuntu CD is in your Drive. Finally, once that's done, it is now time to install your GUI desktop

4.) ***sudo apt-get install ubuntu-desktop***
 - this will start your ubuntu installation. Please be patient as this will retrieve from the internet all the apps, and drivers it needs to install the desktop for your Ubuntu Server. Once that's done, you're good to go. 

welcome to Ubuntu, have fun fiddling with your Server.

---

### Post by hyper_ch on 2008-04-04
why do you enable root first place and then still use sudo?

---

### Post by andguent on 2008-04-04
Others mention 6 different TTY's, but I don't see a mention of how to get there:
While on any Ubuntu box (and nearly any other distro) try:
Ctrl-Alt-F1 through Ctrl-Alt-F6

That should get you 6 different command line sessions to work from. At my old job we actually had an old IBM keyboard that had special keys to do a "left TTY jump" and a "right TTY jump" function to switch between them via one press.

Also note that if you are running the GUI on say, Ubuntu Desktop, you may want to experiement with the above combo and other Function keys. Ctrl-Alt-F7 brings you back to the first user logged into GUI (for gnome at least).

My wife and I log into the same Ubuntu workstation at home. Once she is logged in, I use the switch user option, log in as myself, and then we each have our own settings, windows, and arn't stepping on each other.

To get to her session (since it was the first GUI session):
Ctrl-Alt-F7
To get to my session (since it was the second GUI session):
Ctrl-Alt-F9

F8 is reserved for system output, and I believe more users could be logged on and switched to, but I havin't tested this.

As for configuring apache, I hope you are aware of SSH. I personally would have never walked into the server room at all to configure it, just sit at my workstation and shell into it (ssh on linux command line, putty from windows). Then you have access to your apache configs, and your web browser, without getting up.

/me is lazy

---

### Post by dendrobates on 2008-04-04
There is a bug in 7.10 that can cause your user not to end up in the correct group.  When you install if you select postfix but select the option not to configure it it triggers the bug in the installer.

You need to boot in to single user mode and add your user to the admin group.


Rick

Manager, Ubuntu server team.

---

