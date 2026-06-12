---
title: "Ubuntu security concern"
date: 2005-09-15
forum: Server Platforms
---

### Post by geocritter on 2005-09-15
Hey guys,

Been looking at both pure Debian and Ubuntu, and am going to do a new install (got a new HD) when I get my DSL working in the next couple of days.  I really like Debian, but Ubuntu is soooo nice...but I'm worried about security.  I'll have a firewall going on the router, so...  But I don't know what all I need to secure.  I know that any machine can be hacked, and I don't want to have to spend forever on getting it hardened, just hardened for normal usage on the net.  Here's 2 questions:

1.  Is the lack of a root acount (with sudo capability) actually safe, or is it just an easy way for someone to get su capabilities into my system?

2.  What would you recommend that a normal user harden?  I don't know much about it (I've always had dialup with firestarter, so it's never been an issue), in terms of how to check, what needs to be checked, etc.  Maybe there's an easy hardening script or something, I don't know.

Any help would be greatly appreciated!
Thanks so much,
Dan

---

### Post by jshein on 2005-09-15
When I setup a Ubuntu / Kubuntu system for someone, I create the first account called "system". Essentially going back to having a seperate root account. Then after booting into Ubuntu for the first time I create the User account for the person. That way, if they have to do any maintenance or potentially harmful changes they will have to log in as a seperate user altogether.

I have found that most users, if they have sudo rights, will just enter their password when prompted withought thought of the possible consequences.

This one user - sudo thing is the only fault I have found with Ubuntu yet. Easy to overcome if someone experienced is installing, a nightmare if they do it on their own.

---

### Post by geocritter on 2005-09-15
Maybe I'm showing my ignorance here, but isn't that the same as jumping out of the frying pan and into the fire?  Unless you disable the sudo permissions for that user, that is.  

Is that doable?  In which case, wouldn't I be just as well off to install like normal, then create the root account (as described in the how-to's), then somehow, disable sudo permissions (HOW?) for the regular user that I created?

I'm not arguing or anything, just trying to think it out...

Thanks,
Dan

---

### Post by jshein on 2005-09-15
My main reason for doing it this way is that if the user wants to modify his/her system in a way that requires root access, they will have to log out of their user account and log back in as the system user.

They still get prompted for the "system" user password, and at that time they know it is asking to change something that can possibly cripple / damage the system, and to be sure of what they are trying to do. ( or else pay for a support call to me )

Pure psychology and nothing else. Sometimes getting though to windows converts is a little difficult at first.

On all my personaly managed systems I just enabled the root account, removed sudo priveleges, and made it function as a normal linux system.

---

### Post by geocritter on 2005-09-15
Thanks for the info...I think that's what I'd much rather do...to make it more like a "pure Debian" system (I know, it's kind of a fork, sort of...but still Debian nonetheless).  But I think that enabling root would give me better security for me (I'm the only one on the system).

Would you mind telling me (steps, please):

1.  How to enable the root account (I can't remember the best way to do it)
2. How to get rid of sudo priviledge to other accounts, everything that's not "root"

Thanks so much for the help,
Dan

---

### Post by jshein on 2005-09-15
To enable the root account

user#sudo su
user#"enter your user pasword here"
root#passwd
root#"enter your root password here"

root#nano /etc/sudoers

comment out the last line

#%admin  ALL=(ALL) ALL

save your changes ctrl+o , ctrl+x


all done

---

### Post by geocritter on 2005-09-15
THANK YOU SO MUCH!

Hey, since I'm getting ready to do a fresh install either tonight or tomorrow, do you think I should go ahead and get the breezy preview and install that, or stick to Hoary?  I wasn't sure how "beta" breezy is right now, or if it's almost pretty completely ready to roll, minus something tiny here or there...

---

### Post by jshein on 2005-09-15
I am currently typing this on an Acer AMD Turion 64 laptop, running todays breezy updates. The only isssue I am having is that there is no battery status.

Stability is not guaranteed. Each user will have different experiences based on hardware. Try a live cd first. If it works, then go for it.

*WARNING*

Things can and probably will break during the preparation process for relase. If you are not confident in your abilities to fix this if it should happen, then stick to hoary.
Every time I go to do updates I backup my /etc directory and if I notice major updates, I will do a complete backup berfore updating.

---

### Post by geocritter on 2005-09-15
Thanks!  I'll stick with Hoary for now...I'm sure I *could* fix it if it broke, but I don't have the time or inclination to fight with it (got too many other things to keep up with, between my wife's system and mine, as it is).

Thanks again for the help,
-d

---

### Post by LordHunter317 on 2005-09-15
[QUOTE=geocritter]1.  Is the lack of a root acount (with sudo capability) actually safe, or is it just an easy way for someone to get su capabilities into my system?[/quote]Yes.  Capability wise, it's no less secure.

> 2.  What would you recommend that a normal user harden?There's nothing significantly major I can think of.

[quote=jshein]I have found that most users, if they have sudo rights, will just enter their password when prompted withought thought of the possible consequences.[/quote]Logically, it's reasonable to assume they will switch users and run stuff without thinking as well.  This adds no security or real saftey.  It's a dubious measure at best.

---

### Post by dannysauer on 2005-09-20
[QUOTE=jshein]My main reason for doing it this way is that if the user wants to modify his/her system in a way that requires root access, they will have to log out of their user account and log back in as the system user.[/QUOTE]

Until they decide "man, this changing users thing is irritating - I'll just start doing everything in this account".  If the user can't grasp that only important things ask for their password after they're already logged in, then they're not going to understand why they shouldn't do the same things in the "other" account.  Then they won't have to worry about remembering two passwords, wasting time logging in again, remembering what user they're logged in as, etc.

[QUOTE=jshein]On all my personaly managed systems I just enabled the root account, removed sudo priveleges, and made it function as a normal linux system.[/QUOTE]

Why would you remove sudo privileges?  Are you just a masochist, preferring to tempt fate by occasionally starting up a full-blown root shell just to run the occasional "make install"?  Were you aware that, by simply running "sudo -s" (or sudo -i) you can get a root shell *without* enabling arbitrary root logins, but that's very nearly never required?  Of course, some people prefer remembering yet another password that can be cracked (and is a specifically targeted account for password cracking, as opposed to a random user account that probably doesn't exist on every system) rather than simply learning to use a tool properly.  If only those uninformed few would refrain from giving bad advise to other impressionable newbies...

Starting a shell up as root increases the likelyhood of accidentally running something damaging, but gains nothing.  The inconvenience of switching users further encourages more things to be done as root that shouldn't be ("maybe I'll just look up this documentation on line - it'd be a pain to switch users, though, so I'll do it here.  What?  My browser was compromised, and the compromise ran as root?  Whoops!"). Enabling root login increases the likleyhood of several more popular attack vectors working, as well.  Would you notice a brute force password attack on your system?  Furthermore, sudo does some path and environment variable sanitising, as another way to clean up possible attacks - "su" does not.  So, at least three losses, and no gain.  Yeah, sounds like a great idea.  ](*,)

---

### Post by jshein on 2005-09-23
Actually my main reason is for security.

I use ssh to manage many systems. I disalow root logins via ssh. I must first login as a user, ( first password ) then su to root ( second password - with a minimum 10 characters, consisting of numbers, symbols, upper and lower case letters ) therefore increasing security to the system being administered.

> Until they decide "man, this changing users thing is irritating - I'll just start doing everything in this account". If the user can't grasp that only important things ask for their password after they're already logged in, then they're not going to understand why they shouldn't do the same things in the "other" account. Then they won't have to worry about remembering two passwords, wasting time logging in again, remembering what user they're logged in as, etc.

People always tend to be lazy. All we can do it take steps to minimize the chances that they will do something damaging to their system. If a client wants to administer some of the aspects of the system themselves, then they take the chance ( and responsibility ) of damaging that system.

They have 2 choices:

1: Pay for a maintenance contract, and my company will administer the system when need be.

2: Administer the basic needs of the system themselves, and when they break it, call for service / recovery. ( It is obvious which of these I reccommend ;)  )

To each their own.

---

### Post by LordHunter317 on 2005-09-23
[QUOTE=jshein]I use ssh to manage many systems. I disalow root logins via ssh. I must first login as a user, ( first password ) then su to root ( second password - with a minimum 10 characters, consisting of numbers, symbols, upper and lower case letters ) therefore increasing security to the system being administered.[/quote]And how is this any different from sudo?  It's not, except you have two passwords.  Two passwords is arguably worse for security, because most people can't remember that many distinct passwords.

---

