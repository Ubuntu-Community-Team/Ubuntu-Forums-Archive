---
title: "Sudo or root?"
date: 2005-02-24
forum: The Cafe
---

### Post by Buffalo Soldier on 2005-02-24
Just wanted to know how many of us maintains using **sudo** or have enabled the root user account?

---

### Post by Buffalo Soldier on 2005-02-24
I guess I should start first. Been using sudo ever since I installed Ubuntu.

---

### Post by p!=f on 2005-02-24
Who is root? ;)

---

### Post by ember on 2005-02-24
O.k. I damit, I like sudo ... but only as long as it does not come to terminals. I guess one of the applications I use most often is the root terminal, tweaking a config file here, copying some server stuff there and so on.
But in general I like that sudo-thing because in Ubuntu it actually works quite smooth.

---

### Post by blfamily on 2005-02-24
[QUOTE=ember]O.k. I damit, I like sudo ... but only as long as it does not come to terminals. I guess one of the applications I use most often is the root terminal, tweaking a config file here, copying some server stuff there and so on.
But in general I like that sudo-thing because in Ubuntu it actually works quite smooth.[/QUOTE]
 Sudo was a bit of a shock immediately after the install...but once I realized how useful it was I really like it...gonna stick with it.

Brian

---

### Post by Juergen on 2005-02-24
I discovered and have used sudo loong before Ubuntu was born.

---

### Post by adbak on 2005-02-24
Back when I was with Fedora, I used su, but grew tired of that.  And when I came to Ubuntu, I started using the Root terminal.  About a month ago I decided to give sudo a try and haven't gone back.  IMO sudo is the best implementation of the super user account.

---

### Post by allans on 2005-02-24
sudo. its certainly much more newbie friendly as they only have one password to set up and they can't forget to turn it off.

---

### Post by bored2k on 2005-02-24
[QUOTE=allans]sudo. its certainly much more newbie friendly as they only have one password to set up and they can't forget to turn it off.[/QUOTE]


mixed bag :P
first thing i do is sudo su and dazzit


...sudo i guess

---

### Post by allans on 2005-02-24
[QUOTE=bored2k]mixed bag :P
first thing i do is sudo su and dazzit


...sudo i guess[/QUOTE]

mmm possibly because I was fairly new to linux in general, I hadn't really gotten into the su root habit so it wasn't hard to break.  Either way, it's good to see root is there if you want it.

---

### Post by towner on 2005-02-24
:-k 

Had Fedora on my system until quite recently and was always tempted to just log into root account.

I was a little dubious about the lack of root at first but after a little time invested getting used to sudo, I've decided to stick with sudo.

---

### Post by blfamily on 2005-02-24
It took me less than two days to decide to use only sudo...but one question, Is there anything you can with su that you can't do with sudo or are they EXACTLY the same?
Brian

---

### Post by Buffalo Soldier on 2005-02-24
I guess it's supposed to be the same. So far haven't found anything that needed root that sudo can't handle.

---

### Post by adbak on 2005-02-24
As far as I know they're the same thing, it's just that with 'su' you can set it and forget it but with 'sudo' you have to type it each time.  That's the only discernable difference I can see.

---

### Post by Lovechild on 2005-02-24
I use sudo only because that is the default, it's absolutely my least favorite thing about Ubuntu, I hate it and want it to go away...

---

### Post by Potemkin on 2005-02-25
[QUOTE=Lovechild]I use sudo only because that is the default, it's absolutely my least favorite thing about Ubuntu, I hate it and want it to go away...[/QUOTE]
Easily done. Just type 'sudo passwd root' into a terminal, type in the new root password when prompted (twice), and from then on you can become root just by typing 'su' and giving the password, just like in every other distro of Linux.  :D 

But I agree with Ubuntu's decision to disable 'su' and use only 'sudo' - Ubuntu was tailored for newbies to Linux, *who are always tempted to do **everything** as root*! Having only sudo stops them from getting into this terrible habit.

---

### Post by Potemkin on 2005-02-25
[QUOTE=Buffalo Soldier]I guess it's supposed to be the same. So far haven't found anything that needed root that sudo can't handle.[/QUOTE]
I've enabled the 'su' command in my Ubuntu because I want to be able to click on a .deb package in nautilus and have 'kpackage' install it automatically. Having 'su' disabled means that it stalls when it prompts you to become root. However, it would still be possible to manually install them from the command line using 'dpkg', so it's really just a matter of convenience. But I'm reasonably experienced as a Linux user, so I trust myself not to overuse the root account. Newbies have to be stopped from being able to run *everything* as root all the time, so allowing only 'sudo' was the right decision.

---

### Post by Leif on 2005-02-25
While I have su enabled just in case, haven't touched it once. I think sudo is a good way of doing things, as I'm prone to messing around where I shouldn't be. As a relative newb, I'm all for it.

---

### Post by Buffalo Soldier on 2005-02-25
I guess most agree that using sudo at first was a bit uncomfortable. But after getting used to it that most prefer using sudo.

---

### Post by Mike Douglas on 2005-02-25
[QUOTE=blfamily]It took me less than two days to decide to use only sudo...but one question, Is there anything you can with su that you can't do with sudo or are they EXACTLY the same?
Brian[/QUOTE]
 Actually there are some major differences, sudo allows you to limit the power of a sudo'ed account to, say, running a few commands or only on one PC. Everything is sudo is logged at /var/log/auth.log. su impersonates the user while sudo temporarily gives to super user powers.

---

### Post by CowPie on 2005-02-26
[QUOTE=Mike Douglas]Actually there are some major differences, sudo allows you to limit the power of a sudo'ed account to, say, running a few commands or only on one PC. Everything is sudo is logged at /var/log/auth.log. su impersonates the user while sudo temporarily gives to super user powers.[/QUOTE]
 Sudo is my absolute favourite thing about Linux.  There should be a graphical hook for it however.

---

### Post by Buffalo Soldier on 2005-02-26
Hope I'm not making a fool out of myself here. But is **gksudo** something we call a graphical hook?

---

### Post by jdong on 2005-02-26
sudo all the way. On my desktop, it allows me the luxury of remembering just one password.

On big servers, it really shines through. When you have 5 or so admins all trying to make little changes to the server, it's important to know who's doing what. Root doesn't cut it -- even with good logging.

There's been at least 2 incidents on a school server, where an important config file was butchered or deleted. Of course, disciplinary action must take place for such blunders. However, looking at shell logs & system logs, we were told that user 'root' did it. NO CRAP.

Sudo can be used to create multiple root accounts, and maintains decent logs, too. It should become standard in the Linux community.

---

### Post by CowPie on 2005-02-26
[QUOTE=Buffalo Soldier]Hope I'm not making a fool out of myself here. But is **gksudo** something we call a graphical hook?[/QUOTE]


Oh you're right!  I was just thinking of something a bit more integrated, like in the context menu of Windows XP:  Run as.

---

### Post by neighborlee on 2005-02-26
[QUOTE=CowPie]Oh you're right!  I was just thinking of something a bit more integrated, like in the context menu of Windows XP:  Run as.[/QUOTE]
--------
its in hoary with gnome 2.9.1..which is VERY kewl...not running hoary atm as its a bit buggy for a main partition but its kewl.

I do however think a 'root' account should be optional .  My friend uttterly hates using su all the time and would rather just get on with 'using' linux and go root,  which is exactly what she does ( to her its no different than the convenience she has in windows XP for which she has  no intention of giving up and I dont blame her ).

cheers
nl

---

### Post by Buffalo Soldier on 2005-02-26
[QUOTE=CowPie]Oh you're right!  I was just thinking of something a bit more integrated, like in the context menu of Windows XP:  Run as.[/QUOTE]

What I usually do for that is to create some Nautilus Scripts. It's not as integrated as Windows XP but it works for me. I found the scripts at [http://www.ubuntulinux.org/wiki/NautilusScriptsHowto](http://www.ubuntulinux.org/wiki/NautilusScriptsHowto) and the scripts that I used are:
[list]
[*] Edit file with gedit with root-privileges
[*] Open Nautilus with root-privileges here
[*] Run file with root privileges
[*] Open terminal here
[/list]

---

### Post by earobinson on 2005-12-02
[QUOTE=etc]note that it's insecure and you really should use sudo[/QUOTE]

using the root account is not insecure at all, you just have to make sure to log out.

IMO sudo is more insecure since with the standard install sudo after a password is typed into sudo you dont need a password untill it times out (or the sudo log out command is used) with su you can tell your in root so you remember to log out.

Hey I dident post this lol

---

### Post by aysiu on 2005-12-02
[QUOTE=earobinson]using the root account is not insecure at all, you just have to make sure to log out.[/quote] Which doesn't always happen. In fact, a lot of people like the "convenience" of logging in as root so much, they just stay there. Actually, it's far more convenient to just create a launcher with the command ```
gksudo nautilus
```

> 
IMO sudo is more insecure since with the standard install sudo after a password is typed into sudo you dont need a password untill it times out (or the sudo log out command is used) with su you can tell your in root so you remember to log out. On the contrary, you can stay logged in as root as long as you want. When you type your password in for *sudo*, you have sudo privileges only until it times out (15 minutes, I think), and then you have to retype your password with the next sudo command.

---

### Post by earobinson on 2005-12-02
[QUOTE=aysiu]Which doesn't always happen. In fact, a lot of people like the "convenience" of logging in as root so much, they just stay there. [/QUOTE]
That is a stupid user, and no matter how good the SW is a stupid user with a root account is a bad thing.

[QUOTE=aysiu]On the contrary, you can stay logged in as root as long as you want. When you type your password in for *sudo*, you have sudo privileges only until it times out (15 minutes, I think), and then you have to retype your password with the next sudo command.[/QUOTE]
Thats the problem I have with sudo, on a shared computer another user can jump on after as long as the 15 mins have not passed and do a 
```
sudo su
```
and then they can do whatever they like with the root account.

I guess "more insecure" was the wrong words they are both secure as far as I can tell, I like the nice little root words in the terminal to remind me im logged into the root account. Some may not If I was to use sudo more often the time out would be set to 1 second or something. This is always one of the first things I change when I install ubuntu.

I can just see the case of an admin for a school or something (dont have a really good IT guy) so he just uses sudo then savy student hops on

---

### Post by aysiu on 2005-12-02
[QUOTE=earobinson]
Thats the problem I have with sudo, on a shaird computer another user can jump on after as long as the 15 mins have not passed and do a 
```
sudo su
```
and then they can do whatever they like with the root account.[/QUOTE] Sudo doesn't work that way. In order to have sudo privileges, you have to be specified as having them in the /etc/sudoers file. Not just any old user can jump on and use sudo.

---

### Post by earobinson on 2005-12-02
Im saying same account, the account has sudo privileges but the students just dont know the password so the "admin" jumps on and dose a sudo

(Did not wantto start a war over this, both are great tools if used well) I just like that su gives a viusal que while you are logged in is all :)

---

### Post by aysiu on 2005-12-02
[QUOTE=earobinson]Im saying same account, the account has sudo privileges but the students just dont know the password so the "admin" jumps on and dose a sudo[/quote] So in a scenario in which you have a multi-user computer and someone with sudo privileges logs in, does something with sudo, walks away from the computer and someone else walks up to the unattended computer and wreaks havoc?

Sounds as if that would be a bad situation no matter what security model you use.

> 
(Did not wantto start a war over this, both are great tools if used well) I just like that su gives a viusal que while you are logged in is all :) I like that [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) explains well why Ubuntu uses sudo, but it recognizes the strengths and weaknesses of both models.

---

### Post by aysiu on 2005-12-02
This may very well turn into a flame war (in which case, I'll move it to the Backyard), but I'm curious, seeing as how Ubuntu is one of the few Linux distros that doesn't enable root by default (causing confusion to a lot of Linux veterans who are new Ubuntu users).

---

### Post by xequence on 2005-12-02
When I used ubuntu, sudo was better.

Seriously, there is almost no reason to be running as root all the time that I can think of.

---

### Post by linbetwin on 2005-12-02
I'm new to Linux altogether and I've gotten used to sudo. After all, you can set it to expire in one minute if you want to.

BTW, I like you're website, Mr. Siu! I've been reading on it all yesterday night.

---

### Post by aysiu on 2005-12-02
[QUOTE=xequence]When I used ubuntu, sudo was better.[/quote] You're no longer user Ubuntu?

---

### Post by linbetwin on 2005-12-02
[quote=xequence]When I used ubuntu, sudo was better.[/quote]
You're not using Ubuntu anymore?

---

### Post by earobinson on 2005-12-02
Hey I dident start this thread lol. I doubt that there will be more su users, but that dont make it bad or wrong. Look at linux there are more windows users, that dont make linux bad or wrong. Its a good debate all the same :) I had fun

---

### Post by SweetDreams on 2005-12-02
I like sudo because I don't have to login into the root account to change settings and such.

---

### Post by earobinson on 2005-12-02
its the same thing really

```
sudo <command1>
<type password>
sudo <command2>
sudo <command3>
```
15 mins later you are logged out

```
su
<type password>
<command1>
<command2>
<command3>
exit
```

---

### Post by Jonne on 2005-12-02
Well, I came from Windows, so I'm used to doing everything as admin (I tried running it as a limited user, but that's just not workable).

I think Sudo is wonderful, as it allows you to be pretty safe under a limited account, while the 'dangerous' stuff can be done without logging out or using a complicated command ('runas' in windows just doesn't cut it, and it's a bitch to type from command line).

As for a root account being better or not: I'm not sure if my opinion matters as I'm a Linux n00b, but I haven't needed one while running Ubuntu.

---

### Post by xequence on 2005-12-02
> You're not using Ubuntu anymore?

> You're no longer user Ubuntu?

Nope. I have a relitivally old computer with limited hard drive space. I thought, why do I accually have two OSes when I only need one to do stuff. Also my music collection was growing, so I deleted ubuntu and gave the space to my music.

Its only temporary anyway. I am planning to buy a new computer (maybe around christmas, though not for sure at all) with two hard drives (one 80 GB, half windows, half linux. Another 160 GB one for music, movies, all that stuff) and ill have windows and linux (or I might try freebsd) dual booted.

Its nothing against linux or anything - Linux is a great OS. Its just that having windows is essential for me, so that only left one thing to do, which was delete my ubuntu partition.

---

### Post by Kvark on 2005-12-02
In terms of security it doesn't matter, you need a password in both cases.

If you mean in terms of usability... In the command line it's a bit shorter with "sudo command" then "su; command; exit". In the GUI I would hate to have to close all programs, log out from my account and log into another account just to open synaptic and install something.

BTW. If the user is stupid enough to turn their back at the computer for a moment without locking it or logging out where there are other people nearby then maybe it's a good thing the user learns a lesson.

---

### Post by earobinson on 2005-12-02
There is a big diference between the su command and a log in as the root user.

loging in as the root user everything you do is done as root, using su from the terminal only things you do from that terminal are done as root. I understand why they made the change from a novices point of view it really makes the dangrous programs and commands (yes commands are programs) stand out.

Its just the time out that bugs me and Im a huge fan of the tab key, eg I will type the appr<tab> for appropo, and with sudo you cant do this. Also the visual que telling me im logged in as root is nice.

---

### Post by Lovechild on 2005-12-02
I absolutely hate sudo, of all the bugs the Ubuntu developers introduced, this is by far the worst. Now my user password is the same as root - wonderful idea.. really from a security standpoint, this makes me sick, if I wanted a singleuser root system I'd run Linspire. 

The default was good, why did they absolutely have to mess with it, it brings nothing really useful to the scene, I still have to type in a password for system changes as well as for getting a root terminal (sudo -s has become a daily routine.. so much so that it's aliased to rootme).

---

### Post by 23meg on 2005-12-02
[QUOTE=Lovechild]Now my user password is the same as root - wonderful idea.. [/QUOTE]Not really. What happens is that you use your user password to prove to the system that you are *you* at the moment of entering the command, that you are a user registered as a sudoer, that it's really you sitting in front of the computer trying to perform a system-wide operation. If you weren't a sudoer you wouldn't be able to do anything with that password. The first user created during installation is a sudoer; any users you create later on are not by default. They can only sudo if you become root and allow them to.

You shouldn't see root as an absolute authority, someone else that sits on top of everything. It's just a privileged level you can, and other users can, sometimes elevate to, do what they need to do, and then descend from again.

---

### Post by earobinson on 2005-12-02
Im pretty sure your root password is actualy a bunch or random charters, unless you have changed it.

---

### Post by Kvark on 2005-12-02
[QUOTE=Lovechild]sudo -s has become a daily routine.. so much so that it's aliased to rootme[/QUOTE]
Wow, down from 7 to 6 keystrokes, you saved a whole keystroke with that alias! Amazing compression rate and efficiency increase!

---

### Post by earobinson on 2005-12-02
why not just enable su instead of sudo -s?

---

### Post by Lovechild on 2005-12-02
[QUOTE=Kvark]Wow, down from 7 to 6 keystrokes, you saved a whole keystroke with that alias! Amazing compression rate and efficiency increase![/QUOTE]

tab completion my friend.. I could have called it x but this is more fun

---

### Post by arctic on 2005-12-02
I definitely prefer a root account for security reasons. Imagine this scenario: I set up machines for many users. I have several users working on the same pc. The first user will get su-powers whithout maybe even knowing this. But maybe he knows and messes up the system. With a full root account I can minimize the risk of users wreaking the system because only me and myself will know the root password. Yes, I could create a sudo user and add other users later, but that will only take some extra time, time that some are unwilling to spend on ubuntu. It is that simple.

The best solution would be to have the installer ask the user if he wants a "full root account" (not a borked one like in ubuntu) or the sudo approach. This way, it would be easier to have configure ubuntu to your (companies/schools/institutes) needs imho.

---

### Post by MetalMusicAddict on 2005-12-02
I love sudo now. It was weird at first being used to root with other distros I used. I still do set up the root account and xnest for some things. I think sudo is convenient. I kinda hated to log out and then as root to work on things.

Isnt this the way Apple does it? With a sudo? And now Vista?

---

### Post by poofyhairguy on 2005-12-02
gksudo rules all.

I wish I could do it in Windows. 1,000,000 times better than "run as."

---

### Post by earobinson on 2005-12-02
[QUOTE=arctic]The best solution would be to have the installer ask the user if he wants a "full root account" (not a borked one like in ubuntu) or the sudo approach. This way, it would be easier to have configure ubuntu to your (companies/schools/institutes) needs imho.[/QUOTE]

This would make the installer more complacated something the ubuntu team dont want to do.

The best solution would to have an advanced install that would ask you this, and many other advanced install options

---

### Post by arctic on 2005-12-02
> The best solution would to have an advanced install that would ask you this, and many other advanced install optionsThat was already there in 4.10. But that approach is way too complicated for many users as it is the "default" debian way of setting up a system.

---

### Post by earobinson on 2005-12-02
[QUOTE=arctic]That was already there in 4.10. But that approach is way too complicated for many users as it is the "default" debian way of setting up a system.[/QUOTE]
looks like the dev team has thought of everything then :)

---

### Post by arctic on 2005-12-02
No, not really, as there are users that are keen on a root account but who will get lost using the advanced seupt options. A sensible middle way is still missing in this very crucial question imho.

---

### Post by Wide on 2005-12-02
On the Desktops no sudo.

No one else has root on any of the boxes except me.

When it's time for maintence I just shell in & su -

Why not take full advantage of what *nix has to offer


:cool:

---

### Post by bored2k on 2005-12-02
answer: whatever works.

---

### Post by aysiu on 2005-12-02
[QUOTE=MetalMusicAddict]
Isnt this the way Apple does it? With a sudo?[/QUOTE] Yes.

---

### Post by etc on 2005-12-02
The reason I posted that (I'm being quoted in the OP) was because the person asked how to use the root account and they wanted to log in as root. It sounded like they just wanted to because it was easier.  It seemed as if the person had never used sudo, so I pointed out that logging into the root account is insecure compared to running something with sudo.

---

### Post by aysiu on 2005-12-02
I think a lot of new users are under the illusion that using root is somehow easier than sudo. Even if you fear the command-line and need to make configuration changes all point-and-click, a simple launcher with the command ```
gksudo nautilus
``` solves everything.

---

### Post by amohanty on 2005-12-03
I use the root account for doing most of my admin stuff. I am a bit wary of sudo having been bitten on another distro. However I use both depending on what I am doing. I think if you set it up so that:

1. No XDM login for root
2. Only 1 tty allowed for root
3. TIghten sudoers so that only limited facilities available for only one user (my wife and I both use the same box), might mean getting into the guts of it, but its not so hard.

Its worked nicely for me so far.

AM

---

### Post by kasl33 on 2005-12-03
[QUOTE=earobinson]using the root account is not insecure at all, you just have to make sure to log out.

IMO sudo is more insecure since with the standard install sudo after a password is typed into sudo you dont need a password untill it times out (or the sudo log out command is used) with su you can tell your in root so you remember to log out.

Hey I dident post this lol[/QUOTE]

I am sorry to go dumpster diving here (figure of speech) but, in fact, you can modify sudo to ask for a password every time, part of the time, etc.  It is fully customizable.  See [http://www.linuxhelp.net/guides/sudo/](http://www.linuxhelp.net/guides/sudo/) for more - it is a great reference.

---

### Post by Stormy Eyes on 2005-12-03
[QUOTE=earobinson]using the root account is not insecure at all, you just have to make sure to log out.[/quote]

Given that I sometimes forget to logout, I prefer to use sudo.

[QUOTE=earobinson]IMO sudo is more insecure since with the standard install sudo after a password is typed into sudo you dont need a password untill it times out (or the sudo log out command is used) with su you can tell your in root so you remember to log out.[/QUOTE]

Oh jeez, not this again. Can't you adjust the amount of time sudo retains the password and set sudo to demand a password with every invocation?

---

### Post by vampire_janus on 2005-12-03
the sudo model is better... :D

---

### Post by GreyFox503 on 2005-12-03
I think that sudo is a worthwhile feature, but it has its ups and downs.

Advantages:
  -quickly perform small tasks as root
  -encourage users not to run as root too often

Disadvantages:
  -disables root account by default, something I would change
  -this is not the fault of sudo itself, but spending time on these forums might lead a new user to have a deathly, irrational fear of the root account.  Statements like "you should never log in as root" and "the root is dangerous! avoid it" are not only vague, but just misleading and untrue.  They are generalizations.  Logging in as root is not inherently wrong.


That said, for me personally, I use sudo when I have one and only one command I'm going to need the privileges for.  If it's more than a couple commands, or I'm doing general work which constantly require the privileges, then I switch to root.

And by switch I mean use 'su', not actually log in with a new session.

I think that newcomers to linux should be presented with a more traditional root model, but sudo certainly has its place.

---

### Post by Sanne on 2005-12-03
I like sudo better now because, even if I let the terminal window open in which I sudo'ed before, I'm required to type sudo before every administrative command, so I **know** I'm doing something potentially dangerous.

Typing thoughtlessly something in a root terminal where I did su once with the root password is much more likely, at least for me. Although I made it a habit of always exiting after su to root, I **may** happen to forget that.

So, for me, as a singe Desktop user, sudo has proved to be preferable.

---

### Post by githeko on 2005-12-03
[QUOTE=xequence]When I used ubuntu, sudo was better.

Seriously, there is almost no reason to be running as root all the time that I can think of.[/QUOTE]

The more I read about sudo, the more confused I get.  The site:  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)  seems to talk about Ubuntu since the "Aplication" menu it refers to does not exist in Kubuntu.

I would still like to get an answer from a Kubuntu user who knows what they are talking about:

How to I acaquire root permissions ?????????????

Typing sudo definitely does not give me the permissions even after I type my  (admin?) password.  

I just switched from mepis to kubuntu and it looks like it may have been a mistake...

---

### Post by githeko on 2005-12-03
[QUOTE=githeko]The more I read about sudo, the more confused I get.  The site:  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)  seems to talk about Ubuntu since the "Aplication" menu it refers to does not exist in Kubuntu.

I would still like to get an answer from a Kubuntu user who knows what they are talking about:

How to I acaquire root permissions ?????????????

Typing sudo definitely does not give me the permissions even after I type my  (admin?) password.  

I just switched from mepis to kubuntu and it looks like it may have been a mistake...[/QUOTE]




================

After searching google furiously a several minutes, I came across an answer to my problem (that is how to acquire root permissions while editing a config file).

The answer is at [http://www.kubuntu.org/faq.php#root](http://www.kubuntu.org/faq.php#root) 

I also found that a number of KDE terminals including:

1.  Linux Console ( KDE Menu -> Terminal Sessions)
2. Screen Sessions (ditto)
3.  Console Program [Konsole] (( KDE Menu -> System )

wil accept me to log in  with "sudo" comand.

Screen Sessions and Konsole do not request a password.  Linux Console requests a password (admin user)

The format of the sudo command is:

sudo -s -H

not plan  sudo

Hope this helps anyone in the same pit I was stuck in....

J

---

### Post by earobinson on 2005-12-03
[QUOTE=kasl33]I am sorry to go dumpster diving here (figure of speech) but, in fact, you can modify sudo to ask for a password every time, part of the time, etc.  It is fully customizable.  See [http://www.linuxhelp.net/guides/sudo/](http://www.linuxhelp.net/guides/sudo/) for more - it is a great reference.[/QUOTE]

Then It is a pain In the ass to type the password every time (all my important passwords are 10+ chars) 

But I think they are both fine, from a more hard core admin setup I think that su is better.

Both have flaws if the user is stupid. I like su, and ill use sudo sometimes

---

### Post by egon spengler on 2005-12-03
[QUOTE=arctic]I definitely prefer a root account for security reasons. Imagine this scenario: I set up machines for many users. I have several users working on the same pc. The first user will get su-powers whithout maybe even knowing this. But maybe he knows and messes up the system. With a full root account I can minimize the risk of users wreaking the system because only me and myself will know the root password. Yes, I could create a sudo user and add other users later, but that will only take some extra time, time that some are unwilling to spend on ubuntu. It is that simple.[/QUOTE]

You make it sound as if ```
sudo passwd root
``` is immensely quicker than ```
adduser bob
```

It isn't though.

In fact that penultimate sentence is patently absurd. People (and you are refering to sysadmins here) are unwilling to take the time to create extra users? Do these people intend to just buy a computer for every user or what?

---

### Post by Ruskie on 2005-12-07
[QUOTE=githeko]================


Screen Sessions and Konsole do not request a password.  Linux Console requests a password (admin user)

The format of the sudo command is:

sudo -s -H

not plan  sudo

Hope this helps anyone in the same pit I was stuck in....

J[/QUOTE]

I'm not sure of what your problem was, however, the command you just listed serves you a root shell, practically. It's not that different than having root account enabled and using root login and/or su root when you need.
I.e. it presents the same advantages and disadvantages.
Which leads me to my second consideration. As somebody said earlier in this thread, logging to root is not *inherently* bad. It's something that should be avoided while unnecessary, but not bad in itself. While it is wiser for us newbies to be told not to use it, risks don't change.
And the only risk on having the root account enabled but not using it is that a cracker might find its password, if I'm not wrong.
Personally, I do most of single command that needs privileges via sudo (i.e. "sudo apt-get abcdergs", "sudo vi /etc/network/interfaces", etc.), but if I need to type a bunch of root commands I use "sudo -i -H".

---

### Post by Buffalo Soldier on 2005-12-07
[QUOTE=MetalMusicAddict]I love sudo now. It was weird at first being used to root with other distros I used. I still do set up the root account and xnest for some things. I think sudo is convenient. I kinda hated to log out and then as root to work on things.

Isnt this the way Apple does it? With a sudo? And now Vista?[/QUOTE]

Same story here. Used to use root with other distros. But after using Ubuntu, I'm sticking with using sudo :) I guess sudo is one the thing that's making me stay with Ubuntu.

---

### Post by blueturtl on 2005-12-07
> Im saying same account, the account has sudo privileges but the students just dont know the password so the "admin" jumps on and dose a sudo

This should be thought over. Why do the students have the same user as the admin? You should have a student account without the sudo priveledges for students to use, and a separate teacher/admin account. This way no breach can be made unless the students overpower the teacher while he/she is at his/her desk and force the password out of him/her ;) 

> I absolutely hate sudo, of all the bugs the Ubuntu developers introduced, this is by far the worst. Now my user password is the same as root - wonderful idea.. really from a security standpoint, this makes me sick, if I wanted a singleuser root system I'd run Linspire.

I think the Ubuntu devs are going for a friendlier model than that old-style root. Most likely you create a user account for all users on a single computer. One of these users is likely to be the admin, the boss, the one in charge of maintenance. Why would I as the admin want to keep logging in and out with a different user instead of just using sudo to accomplish the same task at hand? And if I leave my keyboard for a while and someone comes along and taps in they won't be able to do anything hazardous to the system since they'd still need to know my password.

sudo is a good idea, it just takes some getting used to. Remember, different is not automatically inferior.

---

### Post by TeeAhr1 on 2005-12-07
I really like the sudo model.  My computer is the 'public' computer amongst my roommates, and sudo works very well in this regard.  No one ever has to log in/out, I don't have to set up users, I just stay logged in under my user account all the time.  And my roommates know the rule: "If it asks you for a password, you should not be doing it to my machine."

---

### Post by angkor on 2005-12-07
Love sudo, used it already on Debian, so no getting used to for me on Ubuntu. I've enabled the root account anyway though, yet use it rarely.

---

### Post by aysiu on 2005-12-07
[QUOTE=angkor]Love sudo, used it already on Debian, so no getting used to for me on Ubuntu. I've enabled the root account anyway though, yet use it rarely.[/QUOTE] I, too, have enabled a root account just for emergencies. I remember one time I accidentally filled up my /home partition and couldn't log back in--having only one user, I couldn't even sudo. I just plain could not log in. I had to use a live CD to delete the extra files from my /home partition in order to be able to log in again.

Having a separate root account to use occasionally for emergency situations is a good thing.

---

### Post by Wolki on 2005-12-07
sudo for me. sudo <command> is shorter than su -c"<command>", and it means I have one less password to remember.

---

### Post by earobinson on 2005-12-07
[QUOTE=Wolki]sudo for me. sudo <command> is shorter than su -c"<command>", and it means I have one less password to remember.[/QUOTE]
you could use the same password.

---

### Post by prizrak on 2005-12-07
sudo is great in terms of useability sometimes. 
Root is better for security, you will need a separate password. 
It is easy enough to have a GUI driven app to su itself and ask for the password, it's been done in Red Hat back in 7.3 (which was my first Linux distro). 
So overall I think that root is a better model, sudo is more convenient in alot of cases.

---

### Post by Wolki on 2005-12-07
[QUOTE=earobinson]you could use the same password.[/QUOTE]

Yeah, but what would it change? If someone found out my password, he would have root access on my machine in both cases. In addition, if I chose to change my password, I'd have to change it twice.

Add to that that sudo is easier to type than su -c"...", and that sudo is set up by default... one thing I've contemplated doing is alias su="sudo -s", but I'm so used to it now I'd type sudo -s anyway.

I'd consider having a root password in massive multiuser/multiadmin scenarios, though.

---

### Post by robotgeek on 2005-12-08
[QUOTE=earobinson]Im saying same account, the account has sudo privileges but the students just dont know the password so the "admin" jumps on and dose a sudo

(Did not wantto start a war over this, both are great tools if used well) I just like that su gives a viusal que while you are logged in is all :)[/QUOTE]

You can kill your sudo mode by doing a 'sudo -k' . SO, the next time you use sudo, you will have to enter the password.

---

### Post by earobinson on 2005-12-08
[QUOTE=robotgeek]You can kill your sudo mode by doing a 'sudo -k' . SO, the next time you use sudo, you will have to enter the password.[/QUOTE]
I was waiting for some one to point that out, but then why not just use su and exit

---

### Post by atoponce on 2005-12-08
[quote=Lovechild]I absolutely hate sudo, of all the bugs the Ubuntu developers introduced, this is by far the worst. Now my user password is the same as root - wonderful idea.. really from a security standpoint, this makes me sick, if I wanted a singleuser root system I'd run Linspire. 

The default was good, why did they absolutely have to mess with it, it brings nothing really useful to the scene, I still have to type in a password for system changes as well as for getting a root terminal (sudo -s has become a daily routine.. so much so that it's aliased to rootme).[/quote] You have no idea how sudo works, do you?  Sudo has been around long before Ubuntu Linux my friend, and it is definitely not a bug.  Sudo enables system administrators to setup groups of users, and assign those users specific permissions based on the group permissions.  Thus, rather than bug the system admin all day long for root access, they can have limited access to what they need to get the job done.  Sudo is very different from root, and the password you type in for sudo is not root's password, it's yours.  I would suggest studying up on sudo and the /etc/sudoers file to get a better grasp on how it works.

---

### Post by 23meg on 2005-12-08
I use [this trick]("http://www.ubuntuforums.org/showthread.php?t=24008") to sudo via drag and drop.

---

### Post by GreyFox503 on 2005-12-08
If you really don't like sudo for some reason, could you just remove yourself from the sudoers file?  Then no one could sudo, and the only one who could change the sudoers file would be root.  Better enable the root account before trying this one, though. :)

---

### Post by robotgeek on 2005-12-08
[QUOTE=GreyFox503]If you really don't like sudo for some reason, could you just remove yourself from the sudoers file?  Then no one could sudo, and the only one who could change the sudoers file would be root.  Better enable the root account before trying this one, though. :)[/QUOTE]

No, you can always boot into rescue mode, and edit the sudoers file. No need to be root.

Edit: typo

---

### Post by GreyFox503 on 2005-12-08
If you boot into rescue mode and the root password is set, you will have to enter it to continue.  That's all rescue mode is.  It's just that on most setups w/o the root pword ever set, if you go into rescue mode, it will just automatically plop you down at a root terminal.  Try it.

---

### Post by benplaut on 2005-12-08
i use sudo, and when i need to do lots of commands, sudo -s

---

### Post by gruepig on 2005-12-08
I use sudo almost all of the time.  If I'm doing a lot of things as root, I'll su, because I'm lazy enough to get tired of typing 'sudo'.

Sudo pros (imho): actual logging (not .bash_history files which don't appropriately deal with multiple logins), ability to set up accounts with restricted root access (if you're really careful), less likely to run commands as root unnecessarily.

Sudo cons: no tab completion (at least in bash; I end up typing the command and then prepending 'sudo' far too often), default of password caching; if your user password gets compromised, effectively so has your root.

---

### Post by roachk71 on 2005-12-08
[LEFT]Hmm...

It depends on the package. I use Webmin on this computer, and found a root password is pretty much required, since its dpkg-configure script copies that one during configuration.

Some other packages also require you to not simply use sudo or su, but obstinately refuse to work without being logged in as superuser...

This is a good question to ask, and an important note to new users as well.

Very interesting... :cool:
[/LEFT]

---

### Post by curuxz on 2005-12-08
For speed reasons when doing big things like massive package updates or running scripts I enable the Root account (infact im on one now) but only to save me having to enter the password 80 times a second, rest of the time i manage with my account and sudo commands when needed. Its just a case of what your doing, big overhalls on sudo can just get a pain in the ass unless you dont su into root.

---

### Post by aysiu on 2005-12-08
[QUOTE=curuxz]For speed reasons when doing big things like massive package updates or running scripts I enable the Root account (infact im on one now) but only to save me having to enter the password 80 times a second[/QUOTE] You mean once every fifteen minutes, right?

---

### Post by earobinson on 2005-12-08
lol, dose it reset the timer each time u use sudo?

---

### Post by aysiu on 2005-12-08
[QUOTE=earobinson]lol, dose it reset the timer each time u use sudo?[/QUOTE] I don't know. That'd be an interesting thing to test.

---

### Post by Jonne on 2005-12-08
[QUOTE=aysiu]You mean once every fifteen minutes, right?[/QUOTE]
maybe he closes his terminal after each command...

---

### Post by AudioBookDiety on 2006-01-14
When I first installed ubuntu and found no root account I was very displeased. Later I tried Kubuntu, and as I am more familiar with KDE I soon realized that sudo was no problem at all as I could use kdesu to run anything I wished as root. I have moved back to ubuntu now, as Kubuntu just gave me to much trouble, and now have learned gksu.

 so you want to run a terminal as root instead of having to add sudo in front of everything just hit Alt-F2 and type 'gksu gnome-terminal --working-directory=%f'

  password prompt comes up, then your terminal with root privelages runs.

 this can be used with anything such as..  gksu gedit or gksu gedit /etc/X11/xorg.conf


 ofcourse you can also use Gnomes run as a different user thingy as well...but i think my way is faster..

 So now I am a full convert. I think the way (K)(ED)Ubuntu has things set up is the better way. And a much more familiar way to ExMicro$oft users.

---

### Post by Norwal on 2006-01-14
I'm learning towards Root.

See my post here:

[http://www.ubuntuforums.org/showthread.php?t=117344](http://www.ubuntuforums.org/showthread.php?t=117344)

I think with a root login I'd be fixed by now. Maybe/Maybe Not.

---

### Post by BSDFreak on 2006-01-14
su -

---

### Post by imagine on 2006-01-14
sudo
and I love it.

---

### Post by SilentCacophony on 2006-01-14
I like sudo just fine for occasional usage.

If I find myself having to issue strings of commands needing root access, then I'll do a 'sudo su' and finish with an 'exit' to get right back.

Overall, I like the sudo implementation and prefer it over su.

---

### Post by Mr_Grieves on 2006-01-14
But.. with "sudo su" .. you don't get roots all enviorment variable I think.
You need to do "sudo su - root" :)

Root is mostly a security risk. I never use it.

---

### Post by aysiu on 2006-01-14
People who dig this poll may also want to check out [this poll](http://www.ubuntuforums.org/showthread.php?t=98176), too.

**Edit**: It appears the two polls have been merged. Go, moderators!

---

### Post by bored2k on 2006-01-14
[QUOTE=Mr_Grieves]Root is mostly a security risk. I never use it.[/QUOTE] That's fairly subjective. In the wrong hands, sudo can do more or same damage as a root account can.

---

### Post by curtis on 2006-01-14
I tend to use sudo -s here.
I prefer sudo over su for some reason :)

---

### Post by BSDFreak on 2006-01-14
[quote=Mr_Grieves]But.. with "sudo su" .. you don't get roots all enviorment variable I think.
You need to do "sudo su - root" :)

Root is mostly a security risk. I never use it.[/quote] 
su - is enough, you don't need to type root and you don't have to sudo either. 

Edit: you don't have to type exit either, just hit ctrl-d to get out of the root login and then ctrl-d again to log yourself out or if you're in a terminal, close the window.

---

### Post by Mr_Grieves on 2006-01-15
[QUOTE=bored2k]That's fairly subjective. In the wrong hands, sudo can do more or same damage as a root account can.[/QUOTE]
Ah.. but can't you restrict a user accounts sudo capabilities?

---

### Post by Curlydave on 2006-01-15
Neither. I use a root browser.

---

### Post by angkor on 2006-01-15
Always use sudo, yet I do have a root account enabled, just like back in my Debian days.

---

### Post by Stormy Eyes on 2006-01-15
[QUOTE=Buffalo Soldier]Just wanted to know how many of us maintains using **sudo** or have enabled the root user account?[/QUOTE]

Sudo uber alles. I had a bad habit of leaving root logged in, which might be OK at home, but would be unforgivably stupid at work.

---

### Post by eriqk on 2006-01-15
[QUOTE=Mr_Grieves]Ah.. but can't you restrict a user accounts sudo capabilities?[/QUOTE]

Yes, in the Sudoers file. Very powerful (which is why I've never really touched it).
I've been using Sudo since I discovered Terminal.app on OS X. First thing I did when my Gentoo server was up and running was to emerge Sudo.
I do have my Root account enabled, but since then I discovered the sudo -s trick, and I think I will disable it again.

Groet, Erik

---

### Post by ubuntu_demon on 2006-01-15
sudo obviously

It's more safe because :
-I don't want to forget root terminals.
-it prevents mistakes

---

### Post by Bandit on 2006-01-15
sudo, its more secure.

---

