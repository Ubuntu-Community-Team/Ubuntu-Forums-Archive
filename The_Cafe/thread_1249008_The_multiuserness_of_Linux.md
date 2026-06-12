---
title: "The multiuserness of Linux"
date: 2009-08-24
forum: The Cafe
---

### Post by sefs on 2009-08-24
Linux / Ubuntu is a multi-user system.

Does that mean multiple users but one at a time (each users data seamlessly separated from each oter)

OR

multiple users simultaneously.

I am trying to think of a scenario where you would have multiple persons using the computer at the same time (not talking about file sharing etc)

What are the multi user scenarios.

Thanks.

---

### Post by tuxxy on 2009-08-24
Do you mean numerous physically using the computer or remote like shell provider?

---

### Post by Nimless on 2009-08-24
> **sefs said:**
> Linux / Ubuntu is a multi-user system.

Does that mean multiple users but one at a time (each users data seamlessly separated from each oter)

OR

multiple users simultaneously.

I am trying to think of a scenario where you would have multiple persons using the computer at the same time (not talking about file sharing etc)

What are the multi user scenarios.

Thanks.

An example is me and you connected with ssh to the same computer :P

---

### Post by &#32 Greg on 2009-08-24
> **sefs said:**
> Linux / Ubuntu is a multi-user system.

Does that mean multiple users but one at a time (each users data seamlessly separated from each oter)

OR

multiple users simultaneously.

I am trying to think of a scenario where you would have multiple persons using the computer at the same time (not talking about file sharing etc)

What are the multi user scenarios.

Thanks.

Linux is often used for servers, and can be used for distributed computing.

---

### Post by t0p on 2009-08-24
If you had, say, openssh-server installed, multiple users could connect simultaneously.  If you had several terminals connected, you could have multiple users logged on simultaneously.

I have a shell account on a NetBSD machine (not linux, I know, but the principle is the same) run by freeshell.org, and that machine often has 50+ users connected at a time.  If you've got enough lines going in, you can have a lot of users logged in.

---

### Post by sefs on 2009-08-24
> **tuxxy said:**
> Do you mean numerous physically using the computer or remote like shell provider?

I have no idea what i mean exactly it is open for discussion...but the closet thing is what t0p said.  

I asked because when ever I do something on this desktop i always do it in a way that I think would be good for the fictional mass use of my desktop by the multiple family members.  

So I just caught my self and asked myself what are you doing it for. Really you are the only person touching this desktop, and maybe the little nieces that i can sucker into thinking its the best OS since slice bread.   But they outsmart me every time.  They get pissed at noscript because it stops their barbie flash games but have figured out somehow how to get past it.

---

### Post by sefs on 2009-08-24
> **t0p said:**
> If you had, say, openssh-server installed, multiple users could connect simultaneously.  If you had several terminals connected, you could have multiple users logged on simultaneously.

I have a shell account on a NetBSD machine (not linux, I know, but the principle is the same) run by freeshell.org, and that machine often has 50+ users connected at a time.  If you've got enough lines going in, you can have a lot of users logged in.

What do you actually do with a free shell account.  What is it useful for.

---

### Post by tuxxy on 2009-08-24
> **sefs said:**
> What do you actually do with a free shell account.  What is it useful for.

IRC access, eggdrop IRC bots, IRC bouncers, compiling etc

---

### Post by tom66 on 2009-08-24
You can open as many connections as you want to the X server running on Ubuntu. You could remotely run programs, as X transparently supports networked windowing (it's what it's based on.) Multiuserness means that programs like Apache and MySQL can run in their own user, and be able to only modify what they need to, limiting potential damaged caused by a security hole.

---

### Post by t0p on 2009-08-24
> **sefs said:**
> What do you actually do with a free shell account.  What is it useful for.

In general, a shell account is good for the irc stuff tuxxy mentioned.  But freeshell.org in particular is good because of the community on their servers.  It's a real old school internet scene, with bulletin boards and MUDs and stuff.

If you're really interested, you should go get an account.  You can go to [the website]("http://sdf.lonestar.org"), or telnet to sdf.lonestar.org.  You'll find the instructions on how to sign up when you get there.

---

### Post by Firestem4 on 2009-08-24
Linux has been always designed around a Multi-User environment. To give you an idea, windows is NOT a Multi-user Enviroment. (Windows has support for using more than 1 user-account but not at the same time.)

Linux can technically have unlimited users connected/activated concurrently via either shell or X. The only limitation is the hardware.

If you want to try it out yourself, anywhere within Linux you can press the key combination Cntrol+Alt+F1-F6. (By Default) This will bring up a shell prompt. Cntrol+Alt+F-7-F-12 (By Default) bring up another X Window. These are called TTY's by the way.

Using this I can for instance log into my desktop user account and press cntrl+alt+F1, and log in through a traditional shell, do some command line stuff. Oh hell my brothers annoying me, he needs to log in so I press cntrl+alt+f8 and it brings me to the log-in screen and he can log into his user. Both of my shells are still active though. The difference being that in Windows when another user wants to log in it Suspends the primary-user that is already logged in.

Hope this helped explain some of it.

---

### Post by oldos2er on 2009-08-24
> **sefs said:**
> What do you actually do with a free shell account.  What is it useful for.

 Back in the good ol' days we used it for everything. Lynx for the web, nn for Usenet, mutt for mail, ftp for ftp.

---

### Post by Firestem4 on 2009-08-24
> **sefs said:**
> Linux / Ubuntu is a multi-user system.

Does that mean multiple users but one at a time** (each users data seamlessly separated from each oter)**

Thanks.

Data is separated by permissions too. IE: Only user A can access data in his ~/home directory, and User B is restricted likewise. However Administrator can access their data any time whether they're on or not. 

A good example too which happened to me recently I am contracting for one of my Companies contractors (hooray for side work lol). I was VPN'd to his office-network and  was logged in through SSH as Administrator, It turns out he was was also on using his main account which also has sudo-root access. We were both (without knowing it either) modifying the same file in our TFTP root server (/var/lib/tftpdboot/). I was wondering why in the hell the folder *not_used* appeared out of nowhere and where a couple files showed up that I didn't put there.  Well I called him up and found out :lolflag:

---

### Post by Tibuda on 2009-08-25
> **Firestem4 said:**
> Data is separated by permissions too. IE: Only user A can access data in his ~/home directory, and User B is restricted likewise.
By default (in Ubuntu Desktop), user A can read /home/B but not write. If you don't want this behaviour you have to change /home/B permissions:
```
chmod 700 /home/B
```
(or using your GUI file manager)

---

### Post by ssam on 2009-08-25
you can have multiple users logged in on the virtual terminals (CTRL+ALT+F1).

you can have multiple users logged on over a network, eg using ssh for commandline, or VNC for GUI.

you can have multiple graphical sessions running. easy to do with the fast-user-switching applet (the one in the panel with your user name).

you can plug in N monitors, keyboards, and mice into one machine and let N users use the system at once. (tricky to set up currently [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html) but should get easier with time)

---

### Post by Aearenda on 2009-08-25
Here's a prime example of modern multi-user capability in Linux: the Linux Terminal Server Project (LTSP) as used in Edubuntu allows a large number of old computers to act as "thin clients" or terminals, like in the mainframe days, but with a graphical user interface. The terminals send keystrokes and mouse movements to the terminal server, which is a single multi-user powerful machine; it runs the users' programs, and sends screen updates and sound back to the terminals. Thus the old machines live out their days doing an easy job, and the central more powerful machine avoids the need to maintain patches and programs on all the standard PCs that would be otherwise needed, one for each user.

More details [here]("https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/ThinClient").

---

### Post by ReddogOne on 2009-08-25
Maybe pushing the limits of this thread (sorry if I am) but:

Using my laptop. I can log into my desktop use my laptop as a thin client... which is cool. 

Now can I be logged on to ubuntu on my laptop (where I do my emailing and browsing) but then run an application (say something like eclipse) remotely on my desktop but have the application input and output on the laptop?

Not even sure that makes sense...

See I like to use the desktop for work, but like to use the laptop (and the comfort or a big comfy chair) for pondering things but want the same development environment.

---

### Post by koenn on 2009-08-25
or just hook up multiple monitors and keyboards to 1 computer ....

[http://www.multiseatcomputer.be/en/](http://www.multiseatcomputer.be/en/)
[http://www.linuxtoys.org/multiseat/multiseat.html](http://www.linuxtoys.org/multiseat/multiseat.html)
[http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)

---

### Post by ssam on 2009-08-25
> **ReddogOne said:**
> Maybe pushing the limits of this thread (sorry if I am) but:

Using my laptop. I can log into my desktop use my laptop as a thin client... which is cool. 

Now can I be logged on to ubuntu on my laptop (where I do my emailing and browsing) but then run an application (say something like eclipse) remotely on my desktop but have the application input and output on the laptop?

Not even sure that makes sense...

See I like to use the desktop for work, but like to use the laptop (and the comfort or a big comfy chair) for pondering things but want the same development environment.

simplest method.
on the desktop
system->preference->remote desktop
enable sharing and control, set password.

on laptop
applications->internet->remote desktop viewer.
select the desktop. unless you have setup firewalls it should get found over zeroconf.

second easiest (and more secure)
set up ssh so you can log from the laptop into the desktop (i recommend you set up keys, and install denyhost to prevent brute force attacks).
then from the laptop do
ssh -X DESKTOP eclipse
where DESKTOP is the hostname or IP address of the desktop. if you are on a local network and have not disabled zeroconf/avahi then you can use desktopname.local.

---

### Post by Bachstelze on 2009-08-25
> **Firestem4 said:**
> To give you an idea, windows is NOT a Multi-user Enviroment. (Windows has support for using more than 1 user-account but not at the same time.)

Not true.

---

### Post by forrestcupp on 2009-08-25
Here's a far simpler example.

When my boy and I play a 2-player game of Neverputt, we are simultaneous multiple users.  :)

---

### Post by ReddogOne on 2009-08-29
> **ssam said:**
> simplest method.
on the desktop
system->preference->remote desktop
enable sharing and control, set password.

on laptop
applications->internet->remote desktop viewer.
select the desktop. unless you have setup firewalls it should get found over zeroconf.

second easiest (and more secure)
set up ssh so you can log from the laptop into the desktop (i recommend you set up keys, and install denyhost to prevent brute force attacks).
then from the laptop do
ssh -X DESKTOP eclipse
where DESKTOP is the hostname or IP address of the desktop. if you are on a local network and have not disabled zeroconf/avahi then you can use desktopname.local.

Big thanks. Exactly the information I needed. Just need to read up the ssh bit but know google will answer that question ;)

---

