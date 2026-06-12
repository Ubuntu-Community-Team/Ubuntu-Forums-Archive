---
title: "Enable the Root Account This Should Be in the FAQ"
date: 2007-08-07
forum: The Cafe
---

### Post by BillB0B on 2007-08-07
I’m probably going to get yelled at by the Ubuntu faithful because the use of sudo to perform root activities is so integral to the operating system, but I’m a traditionalist — I like not having to preface with sudo before every administrative command. I find it to be a hindrance. So, before proceeding further, pull up a terminal prompt (located in the Applications& gt; Accessories menu, if you’re using the default GNOME version of Ubuntu) and enter the following command:
# sudo passwd root

At the prompt, provide the password for your main user account, and then provide a new password for the root account, twice. You should now be able to launch a terminal and type su and the root password to remain as root for the for the remainder of the session. No more annoying timeouts.
Still can't figure out why there isn't a option in the setup to let you set up a root password. I've read the wiki on the reason why no root password you might screw up your install crash your system. That how you learn thru your mistakes.

---

### Post by ThrobbingBrain66 on 2007-08-07
Not everyone wants to learn through mistakes.  Ubuntu's goal is to be as user-friendly as possible, not necessarily to teach.  If you are really that hard up to learn things, maybe Slackware or Gentoo is the right distro for you.

---

### Post by Hospadar on 2007-08-07
I would however agree that the first time you boot up ubuntu something pop up and explain to you why and how you should change your root password.

---

### Post by asmoore82 on 2007-08-07
> **BillB0B said:**
> I’m probably going to get yelled at by the Ubuntu faithful because the use of sudo to perform root activities is so integral to the operating system, but I’m a traditionalist — ***I like not having to preface with sudo before every administrative command. I find it to be a hindrance***. So, before proceeding further, pull up a terminal prompt (located in the Applications& gt; Accessories menu, if you’re using the default GNOME version of Ubuntu) and enter the following command:
# sudo passwd root

At the prompt, provide the password for your main user account, and then provide a new password for the root account, twice. You should now be able to launch a terminal and type su and the root password to remain as root for the for the remainder of the session. No more annoying timeouts.
Still can't figure out why there isn't a option in the setup to let you set up a root password. I've read the wiki on the reason why no root password you might screw up your install crash your system. That how you learn thru your mistakes.

```
asmoore@asmoore-laptop:~$ sudo -i
Password:
root@asmoore-laptop:~#
```

:KS

---

### Post by por100pre1 on 2007-08-07
I think the answer its obvious. There are many new users installing Ubuntu and the developers decided that it wouldn't be a good idea to make new users think about root so they use sudo instead.

---

### Post by ThrobbingBrain66 on 2007-08-07
> **Hospadar said:**
> I would however agree that the first time you boot up ubuntu something pop up and explain to you why and how you should change your root password.

The kind of new user that Ubuntu is targeting doesn't care about root, and being root for extended periods of time.  Once Ubuntu gets closer to its goal, in theory, root privileges shouldn't be needed so often that this is even a concern.

Not to mention, being root for as little amount of time as necessary protects the user from themselves (so they DON'T accidentally delete system files, etc) and from other threats.

---

### Post by vexorian on 2007-08-07
I really don't see much problem with it, prefixing sudo to commands is not so problematic, you only need to input password once in a while, then if you want to run a bunch of things with sudo then just make it an script and call the script with sudo.

Of course, it would not harm to add it to the FAQ to the "previously Unix/other linux user" section

---

### Post by viking777 on 2007-08-07
Billbob is absolutely right but he doesn't go far enough, Ubuntu should have a root account by default. Are there any other distros out there that don't have one? There might be but I have never met with one, and so why is it that Ubuntu is the only one that doesn't? Do you really think that all the other distros out there are more dangerous because they do have one? This is complete nonsense and it is unprecedented arrogance on the part of the Ubuntu developers to fly in the face of accepted practice and place such a millstone around the neck of an otherwise brilliant distro. Now I know enough to circumvent their madness and install a proper root account and login, but most newcomers will not and will move elsewhere when confronted with this nonsense.:mad:

---

### Post by Gmbrdilos on 2007-08-07
sudo does it all so I don't see a need to use the root account. Especially when I like to experiment a lot, a root account would kill my system completely.

---

### Post by vexorian on 2007-08-07
> Billbob is absolutely right but he doesn't go far enough, Ubuntu should have a root account by default.Why?

> There might be but I have never met with one, and so why is it that Ubuntu is the only one that doesn't?because that's what canonical decided?

> Do you really think that all the other distros out there are more dangerous because they do have one?

No, but I think they are silly-er. Let's setup an account you don't need ! yay!


> This is complete nonsense and it is unprecedented arrogance on the part of the Ubuntu developers to fly in the face of accepted practice and place such a millstone around the neck of an otherwise brilliant distro
Boy that's an overreaction, it is just the root account...


> Now I know enough to circumvent their madness and install a proper root account and login, but most newcomers will not and will move elsewhere when confronted with this nonsenseI guess that's the reason most Linux users are not running Ubuntu but other distros according to distrowatch, yeah this explains it all , newcomer comes to ubuntu and asks to himself "Wtf? no root account? wtf?" then he leaves and tries another distro...

---
Freedom of choice my friend, if you like the root account add it, if you think it is better to have it by default use a distro that does.

You can also just make an ubuntu remix that adds a root account.

--
So , I agree it should go to the fact, or perhaps even allow it as an option in the installer under an advanced tab. But I don't think it would be a good idea to switch it, there are a handful of users that learned ubuntu with sudo and I can not help but hear complaints when they upgraded and that was changed...

---

### Post by aysiu on 2007-08-07
For 99% of the desktop users out there, there's no need to enable a root account.

If you're tired of typing *sudo* repeatedly, just do *sudo -i*, and this will change you to a root terminal.

If you want to make drag and drop changes, make a launcher for the command *gksudo nautilus* or *kdesu konqueror*.

I don't see a compelling case for making Ubuntu like every other distro in this respect. The pros and cons of both models are laid out quite well in this document:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by raijinsetsu on 2007-08-07
> **viking777 said:**
> Billbob is absolutely right but he doesn't go far enough, Ubuntu should have a root account by default. Are there any other distros out there that don't have one? There might be but I have never met with one, and so why is it that Ubuntu is the only one that doesn't? Do you really think that all the other distros out there are more dangerous because they do have one? This is complete nonsense and it is unprecedented arrogance on the part of the Ubuntu developers to fly in the face of accepted practice and place such a millstone around the neck of an otherwise brilliant distro. Now I know enough to circumvent their madness and install a proper root account and login, but most newcomers will not and will move elsewhere when confronted with this nonsense.:mad:

This isn't arrogance. It's common sense. Ubuntu is trying to target a larger populace, not a *nix admin. If you were a *nix admin, you'd know about "sudo passwd"...
As for why the root account is created with a (random?) unknown password, it's to prevent a user from running the system as root (which could be very bad); esp. running KDE or GNOME as root. Ubuntu is assuming that most users of it's system won't understand what a root account is.
The purpose of a root account is to do system administration or as a fail-safe. I run several servers, and I almost never need the root account.
Just an FYI - Windows also tries to hide the administrator account from casual users.

If you have need to do many administrative tasks, and hate typing sudo before each command, use "sudo -s". Leave the root password obfusticated. If you lose your password, there's always single-user mode.

Personally, I think it's a great move.

---

### Post by p_quarles on 2007-08-07
Personally, I'm of the mind that any *nix user who doesn't know that you can invoke a root terminal using "sudo" (in addition to the methods listed above, you can type "sudo bash," "sudo gnome-terminal," "sudo xterm," etc., etc.) isn't really experienced enough to express an opinion on whether Ubuntu should ship with a root account.

---

### Post by stmiller on 2007-08-07
> **BillB0B said:**
> 
Still can't figure out why there isn't a option in the setup to let you set up a root password. I've read the wiki on the reason why no root password you might screw up your install crash your system. That how you learn thru your mistakes.

The whole reason of having sudo is for security. There is no root account, so the entire computer is safer than one with a root account enabled. This is the same in Debian, and OS X. I suggest reading up on sudo and why/how it works.

As others have informed you, just do

sudo -i

or 

sudo -s

to get a root prompt if you need one.

---

### Post by overdrank on 2007-08-07
Well my 2 cents, I think it is fine the way it is. You can change into root like mention before and I like it that it gives the operator the choice to do what they choose to do. :guitar:

---

### Post by starcraft.man on 2007-08-07
> **viking777 said:**
> Billbob is absolutely right but he doesn't go far enough, Ubuntu should have a root account by default. Are there any other distros out there that don't have one? There might be but I have never met with one, and so why is it that Ubuntu is the only one that doesn't? Do you really think that all the other distros out there are more dangerous because they do have one? This is complete nonsense and it is unprecedented arrogance on the part of the Ubuntu developers to fly in the face of accepted practice and place such a millstone around the neck of an otherwise brilliant distro. Now I know enough to circumvent their madness and install a proper root account and login, but most newcomers will not and will move elsewhere when confronted with this nonsense.:mad:

You must have been joking when you wrote this, it's not that funny though... why don't we just implement XPs ability to get viruses/spyware too while we are at it? You do know that Vista now defaults to a non-administrator account right?

> **aysiu said:**
> For 99% of the desktop users out there, there's no need to enable a root account.

If you're tired of typing *sudo* repeatedly, just do *sudo -i*, and this will change you to a root terminal.

If you want to make drag and drop changes, make a launcher for the command *gksudo nautilus* or *kdesu konqueror*.

I don't see a compelling case for making Ubuntu like every other distro in this respect. The pros and cons of both models are laid out quite well in this document:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

+1 I use sudo all the time and am perfectly happy with it. When I do lots of changes with the command line I use i or bash.

> **p_quarles said:**
> Personally, I'm of the mind that any *nix user who doesn't know that you can invoke a root terminal using "sudo" (in addition to the methods listed above, you can type "sudo bash," "sudo gnome-terminal," "sudo xterm," etc., etc.) isn't really experienced enough to express an opinion on whether Ubuntu should ship with a root account.

LOL! Well put. :)

---

### Post by vexorian on 2007-08-07
> sudo gnome-terminal
*saves it in his bag of tricks*

How about ctrl+alt+f1, sudo startx ?

---

### Post by aysiu on 2007-08-07
Gah! ```
gksudo gnome-terminal
``` Actually, the proper way to do it is to just launch a regular terminal and then ```
sudo -i
```

---

### Post by @trophy on 2007-08-07
> **vexorian said:**
> *saves it in his bag of tricks*

How about ctrl+alt+f1, sudo startx ?

God Almighty... please don't do that.  Stuff like that is the reason why Canonical decided to hide the root account by default.

LOL it reminds me of [this article](http://blog.lobby4linux.com/index.php?/archives/70-86-Year-Old-Great-Grandmother-Hoists-The-Jolly-Roger.html) about a guy telling his grandmother to rip a CD to MP3 so she could play it under Linux, and he started laughing cause he realized the irony that the solution he was about to tell her to use to get around the DRM was the very thing the DRM was designed to prevent... they disabled the root account precisely because they feared you might do something like "sudo startx" and you end up doing it precisely because they disabled the root account... 

There's a lesson to be learned there, Canonical.

EDIT: On re-reading that, the last sentence looks sort of antagonistic.  That wasn't my intent... I am a faithful poster here, I  use Ubuntu on all of my computers at home and I love it.  I just wanted to point out that changing something that's *related* to a problem won't necessarily fix that problem, and even if it does, there will probably be side effects.  It's usually better to address the problem directly, such as the first time someone does anything with the root account on their system, a popup tells them what the root account is, what you have to be careful of when using it, and some examples of when to use / when not to use it.  That way those of us who already knew could just ignore the popup, and the new users could ignore it and then be sorry when they end up typing "rm -rf /".  And I guess therein lies the rub: if I were a new user, I'd be at just as much risk of typing "sudo rm -rf /" and screwing everything up... so the inconvenient truth here is that we have no choice but to educate users about what kinds of things they need to be careful of.

---

### Post by p_quarles on 2007-08-07
@aysiu: Re: "gksudo"  D'oh. My bad. ](*,)

And, of course, I agree -- the most direct way is the best.

---

### Post by cobrn1 on 2007-08-07
99% of people don't need a root acount - you can do almost everything with sudo. I can't think of an example where you can't...

Root is locked it a way that makes it unhackable (as in, there's no way to brute-force the password as it'll never equate to the password that's in the password file - this is because it's an invalid character - clever, no?) This means that you actually are a lot more secure without it enabled...

You can enable it easily if you want...

you can make it so that you don't have to type in sudo all the time: sudo -i or something like that...

p_quarles, you are both wise and funny, and I very much agree with your sentiments :D

---

### Post by bchaffin72 on 2007-08-07
Ubuntu does what it does for reasons of safety and security. Having come to Ubuntu from a Red Hat/Mandrake background,  I initially did find lack of a root account strange and did reconfigure my box to run a standard root account. However, once I got used to Ubuntu, I found myself restoring the default behavior.
Being that Ubuntu has an emphasis on ease of use and the desktop environment, I do find it is the best way for Ubuntu to be, once you get used to it.

---

### Post by Calash on 2007-08-07
I do not see it as the "Need" for a root account so much as trying to make the OS general user friendly.

Coming from a Windows world your account is Admin by default.  If you want to install something you do not need to log out, then log back in.  Sudo allows this same convenience while maintaining the security of a user level account.  Is your average user really going to want to log out and in as root to install a new app?


If you know enough that it is inconvenient, then it is easy to shut off...though I really do not see the problem with typing 4 characters before the command...but that is just me.

---

### Post by BillB0B on 2007-08-07
> **ThrobbingBrain66 said:**
> Not everyone wants to learn through mistakes.  Ubuntu's goal is to be as user-friendly as possible, not necessarily to teach.  If you are really that hard up to learn things, maybe Slackware or Gentoo is the right distro for you.

Well to tell you the truth over the years I ran many different Linux OS plus a few BSD OS. Do you remember installing from floppy? Sound like you think the people that use this OS are brain dead or complete morons. If that the case they need to check out PCLinuxOS which is  closer to being a drop in replacement for Windows plus let's you set a root password plus is much more user-friendly.
FYI : I was running Linux before there was a KDE or Gnome .

---

### Post by Nekiruhs on 2007-08-07
> **BillB0B said:**
> Well to tell you the truth over the years I ran many different Linux OS plus a few BSD OS. Do you remember installing from floppy? Sound like you think the people that use this OS are brain dead or complete morons. If that the case they need to check out PCLinuxOS which is  closer to being a drop in replacement for Windows plus let's you set a root password plus is much more user-friendly.
FYI : I was running Linux before there was a KDE or Gnome .
Think of it this way. If a hacker wants to gain access to your system, its much easier if root is enabled. He knows the account name is "root" and he knows the permissions it has. All he needs to do now is brute-force your password. Not having a root account is much more secure.

---

### Post by lisati on 2007-08-07
> **Nekiruhs said:**
> Think of it this way. If a hacker wants to gain access to your system, its much easier if root is enabled. He knows the account name is "root" and he knows the permissions it has. All he needs to do now is brute-force your password. Not having a root account is much more secure.

I like the safety in this.... even if we didn't need to worry about hackers, I, for one, sometimes need protection from myself. The "sudo" approach adds a level of protection here a little bit like an "are you sure?" prompt.

---

### Post by K.Mandla on 2007-08-07
Ubuntu should really just ask "Confirm or deny?" after every click.

---

### Post by macogw on 2007-08-07
> **stmiller said:**
> The whole reason of having sudo is for security. There is no root account, so the entire computer is safer than one with a root account enabled. This is the same in Debian, and OS X. I suggest reading up on sudo and why/how it works.

As others have informed you, just do

sudo -i

or 

sudo -s

to get a root prompt if you need one.

Debian has a root account and root password, you just can't use it to log in to X.  On the command line, though, it exists, which is good because the first user does *not* automatically have sudo rights like with Ubuntu.

By the way, there's also "sudo su" or "sudo su -"

---

### Post by LaRoza on 2007-08-07
> **K.Mandla said:**
> Ubuntu should really just ask "Confirm or deny?" after every click.

I hope you are joking...otherwise you in danger of loving Vista.

---

### Post by g2g591 on 2007-08-07
root is not enabled for a reason. This is to keep newcomers from breaking their system. Within the first 3 days of having root enabled/logging in as root i broke my system and had to reinstall, and I am not unexperienced.

---

### Post by @trophy on 2007-08-07
> **g2g591 said:**
> root is not enabled for a reason. This is to keep newcomers from breaking their system. Within the first 3 days of having root enabled/logging in as root i broke my system and had to reinstall, and I am not unexperienced.

Do you mean logging in to X as root?  If so, then that's why you broke your system.  root = CLI ONLY!

---

### Post by vexorian on 2007-08-07
> **BillB0B said:**
> Well to tell you the truth over the years I ran many different Linux OS plus a few BSD OS. Do you remember installing from floppy? Sound like you think the people that use this OS are brain dead or complete morons. If that the case they need to check out PCLinuxOS which is  closer to being a drop in replacement for Windows plus let's you set a root password plus is much more user-friendly.
FYI : I was running Linux before there was a KDE or Gnome .

Not expecting the users to care about gibberish doesn't really mean we think they are brain dead, fact is most people that is not brain dead won't care about gibberish and this whole root account Jazz is simply gibberish.

Then you say some madness about how PCLinuxOS is closer to windows and is more friendly, totally off-topic stuff then you try to brag about how you were using Linux before there was a KDE or Gnome, nobody really finds that impressive, sorry.

---

### Post by cobrn1 on 2007-08-07
Having a root password is _NOT_ more user friendly. If you forget it you're fecked...

In ubuntu if you forget your login password you're a moron, but it's easily fixable anyway. There is no need for the root account, but it's there, ready and waiting if you feel compelled to use it...

Also, sudo is much more versatile, and if you look into the power of sudo then I think you'd appreciate it more (ie, you could set up a guest account with very limited priveleges, etc).

Lastly, the root account in ubuntu is basically unhackable, therefore, with no root acount your pc bacomes much more difficult to break into.

---

### Post by BlueStreak on 2007-08-07
K, so how does one disable the root account if they have it enabled?  Not that I do of course...

---

### Post by aysiu on 2007-08-07
> **BlueStreak said:**
> K, so how does one disable the root account if they have it enabled?  Not that I do of course...
```
sudo passwd -l root
```

---

### Post by BlueStreak on 2007-08-07
Thanks.  I'm realizing a simple 'man passwd' and I could have answered that myself.

---

### Post by saulgoode on 2007-08-07
> **Nekiruhs said:**
> Think of it this way. If a hacker wants to gain access to your system, its much easier if root is enabled. He knows the account name is "root" and he knows the permissions it has. All he needs to do now is brute-force your password. Not having a root account is much more secure.

That same hacker would just as easily (which is to say, not very easily) be able to brute force the password for the 'nekiruhs' account on your machine. I am willing to bet that 'nekiruhs' on your machine has SUDO privileges. Even if he does not, how much better off is he if it is just his personal account that is compromised?

For the vast majority of home desktop users, protecting your personal data is just as critical as protecting your system installation. We're talking Linux here, if you lose system critical files then you just pop in a CD and re-install. Myself, I don't even bother to backup my system setup because, were I ever to lose my system, all the software is already archived in the most secure place possible, the Internet (I basically do a clean install every 12 months or so anyway). However, I **do** backup my personal files -- this is MOST important and not recoverable except through my own devices.

Granted, if someone *were* to acquire root privileges on my system, it would also mean my personal data would be jeopardized as well -- but that is hardly any more of a catastrophe (for me) than if they merely obtained privileges to my non-root, personal account. Neither is acceptable, but at least with a separate root account, it is quite rare that I am actually ever entering its password (except on my development machine).

From all the advice and how-tos I see for Ubuntu, it would seem to be a prevalent practice for the account which its users predominantly use to have SUDO privileges -- prevalent to the point of being assumed, I have never seen instructions state something like "log into your privileged account and perform a 'sudo ...'". This means that the user is in danger of having his privileged password snooped whenever he enters it, *even if he is only intending to access his account in an unprivileged manner*. How often this risk occurs (do you log out when you leave your workstation? does your screensaver or keyboard lock require the same password to restore access?) and how significant the risk is (are there people in the vicinity who might glance at your activities?) certainly is dependent upon the nature of your work/home environment but unless you are working from an unprivileged account for the bulk of the time on your computer (which is the case for those who have root accounts), you *are* increasing the risk.

---

### Post by aysiu on 2007-08-08
Even though I do believe *sudo* to be a better setup than a regular root account, I think people often exaggerate the benefits of *sudo* over root. The benefits do, however, exist.  While it's true that the vast majority of home users of Ubuntu are *sudoers*, it's also true that 100% of the time, the username *root* always has unrestricted privilege over the entire system.

And, as mentioned before, everyone knows the username *root*--both the actual name and what privilege it has. Not everyone knows the username *nekiruhs* or what privilege it has.

*sudo* has benefits beyond security. It has a log of which commands were run with administrative privileges. It allows you to easily add or remove root privilege from particular users. It allows users to memorize only one password instead of two.

It's a good balance between convenience and security.

---

### Post by Spr0k3t on 2007-08-08
I completely agree that it should be included in the FAQ.  However, the information already included in the FAQ should be it.  Directions on how to enable it or make it the default account should be left out or linked to an "unsupported configuration" page.

---

### Post by vexorian on 2007-08-08
> That same hacker would just as easily (which is to say, not very easily) be able to brute force the password for the 'nekiruhs' account on your machine

only that he needs more work to actually know there is a "nekiruhs" account and that it happens to be the one with sudo rights...

> For the vast majority of home desktop users, protecting your personal data is just as critical as protecting your system installation
Neither of those is blocked by the decision to use sudo instead of a root account.


> 
From all the advice and how-tos I see for Ubuntu, it would seem to be a prevalent practice for the account which its users predominantly use to have SUDO privileges -- prevalent to the point of being assumed, I have never seen instructions state something like "log into your privileged account and perform a 'sudo ...'". This means that the user is in danger of having his privileged password snooped whenever he enters it, even if he is only intending to access his account in an unprivileged manner. How often this risk occurs (do you log out when you leave your workstation? does your screensaver or keyboard lock require the same password to restore access?) and how significant the risk is (are there people in the vicinity who might glance at your activities?) certainly is dependent upon the nature of your work/home environment but unless you are working from an unprivileged account for the bulk of the time on your computer (which is the case for those who have root accounts), you are increasing the risk.

Like how is it really increasing the risk?

Only the first account, the one used by the guy that sets the whole system up got sudo rights by default, the rest of the family use non-sudo accounts..

---

### Post by superstylin on 2007-08-08
As a new Linux user, the sudo route was fantastic compared to a root-account similar to Windows or such... If I need extended root access I just do sudo nautilus!

I dont understand why you would want an entire account as root?

:confused::confused:

---

### Post by userundefine on 2007-08-08
alias su='sudo -i'

/thread

---

### Post by aysiu on 2007-08-08
> **superstylin said:**
> If I need extended root access I just do sudo nautilus! Or, better yet, *gksudo nautilus*.

---

### Post by eentonig on 2007-08-08
> **saulgoode said:**
> That same hacker would just as easily (which is to say, not very easily) be able to brute force the password for the 'nekiruhs' account on your machine. I am willing to bet that 'nekiruhs' on your machine has SUDO privileges. ....

Funny logic.

I have an ssh server running at my home, which I left open to everybody for a few weeks. I had daily brute force attacks. You know which accounts they tried?

**root, www, mysql, smb, ftp ..**. With **root** and **www** being the two most used usernames they tried to hack.

But I have never seen any attempt to break **rfonteyn** (yes, I do have another login then my nick. And yes, I don't care that you know it.) or **eentonig** (my public nick, used in several fora).

---

### Post by paulok64 on 2007-08-08
This thread is what i needed i was about to jump ship. I don't know if my installation was bugged or its my flaky Presario Laptop and its  Broadcom card but bcw43xx-fwcutter spams my f1 - f6 terminals with the annoying can't find bla bla bla. I was going to try and fix it by blackboxing bcw43... everything I tried would lock up terminal and not allow me to enter password after i sudoed it. I know I could have downloaded the dang thing and configured the firmware but i didn't want to as im gonna do as this thread [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) suggest as i think ndiswrapper a better solution. I had known this trick at one time but had grown accustomed to just using sudo now i can knock the tar outta that stuppid bcw43xx-fwcitter

---

### Post by ThrobbingBrain66 on 2007-08-08
> **BillB0B said:**
> Well to tell you the truth over the years I ran many different Linux OS plus a few BSD OS. Do you remember installing from floppy? Sound like you think the people that use this OS are brain dead or complete morons. If that the case they need to check out PCLinuxOS which is  closer to being a drop in replacement for Windows plus let's you set a root password plus is much more user-friendly.
FYI : I was running Linux before there was a KDE or Gnome .

I don't know how you gathered that simply from my reply to your first post.  I said nothing of the sort and don't feel that way at all.  

I've only been a part of the Linux community for a little over a year, but there's been one thing that's really bothered me about it.  There seems to be a prevailing opinion (not so much on these forums) that user-friendliness is bad.  That has never, and will never, make sense to me.  If you don't like user-friendliness and are all about compiling code for EVERY app you need and editing config files then Ubuntu may not be for you.

The vast majority of users want a computer to surf the Internet, write papers, listen to music, watch movies....the list could go on.  They DON'T want to have to figure out which section in xorg.conf they have to edit to enable their graphic drivers.

To sum things up, not everyone uses Linux to be leet.

---

### Post by Nekiruhs on 2007-08-08
> **saulgoode said:**
> That same hacker would just as easily (which is to say, not very easily) be able to brute force the password for the 'nekiruhs' account on your machine. I am willing to bet that 'nekiruhs' on your machine has SUDO privileges. Even if he does not, how much better off is he if it is just his personal account that is compromised?

For the vast majority of home desktop users, protecting your personal data is just as critical as protecting your system installation. We're talking Linux here, if you lose system critical files then you just pop in a CD and re-install. Myself, I don't even bother to backup my system setup because, were I ever to lose my system, all the software is already archived in the most secure place possible, the Internet (I basically do a clean install every 12 months or so anyway). However, I **do** backup my personal files -- this is MOST important and not recoverable except through my own devices.

Granted, if someone *were* to acquire root privileges on my system, it would also mean my personal data would be jeopardized as well -- but that is hardly any more of a catastrophe (for me) than if they merely obtained privileges to my non-root, personal account. Neither is acceptable, but at least with a separate root account, it is quite rare that I am actually ever entering its password (except on my development machine).

From all the advice and how-tos I see for Ubuntu, it would seem to be a prevalent practice for the account which its users predominantly use to have SUDO privileges -- prevalent to the point of being assumed, I have never seen instructions state something like "log into your privileged account and perform a 'sudo ...'". This means that the user is in danger of having his privileged password snooped whenever he enters it, *even if he is only intending to access his account in an unprivileged manner*. How often this risk occurs (do you log out when you leave your workstation? does your screensaver or keyboard lock require the same password to restore access?) and how significant the risk is (are there people in the vicinity who might glance at your activities?) certainly is dependent upon the nature of your work/home environment but unless you are working from an unprivileged account for the bulk of the time on your computer (which is the case for those who have root accounts), you *are* increasing the risk.
But the thing is, they don't know my username either. They'd have to brute-force both. With the root account. They know your username. They've already won half the battle.

---

### Post by saulgoode on 2007-08-08
> **Nekiruhs said:**
> But the thing is, they don't know my username either. They'd have to brute-force both. With the root account. They know your username. They've already won half the battle.

It is dependent upon who the "they" are against whom you are protecting your system. If "they" are Internet hackers who are randomly surfing IPs in search of 'root' accounts then yes, they would not be likely even to attempt anything outside the standard accounts (root, ftp, guest, smb, etc). But if "they" have specifically targetted your machine then they would likely have no more trouble than I did in discovering your account name.

Is knowing the name of the privileged account really "half the battle"? You would also have to have:

1) Installed 'ssh-server' on your system.
2) Started the SSH daemon.
3) Opened a port for the daemon to monitor (and leave that port at "22" to simplify the hacker's chance of finding it).
4) Specified no rule limiting the range of external IPs permitted to access your system.
5) Configured your server to permit root logins ("PermitRootLogin yes" in 'sshd_config').

The last point is where having a 'root' account actually proves preferable in this situation. How do you prevent your non-root, privileged user from logging in from outside? I imagine it is possible  to have a rule somewhere specify that user 'nekiruhs' is not permitted to do a SSH login -- I haven't deeply investigated how that would be done because the standard *nix security model handles this quite effectively (the same security that is deployed on about two-thirds of the servers on the Internet).

All of that is premised on preventing attacks from "random strangers" in a scenario that the 'typical' home desktop user would likely never encounter. For cases where the "attack vector" is someone who has access to your machine, perhaps even possessing an unprivileged account, the idea that they would not be able to determine the privileged user's account name would require some stretch of the imagination (I am thinking along the lines of the "attack vector" being a younger brother or a mischievous coworker). Once your privileged user's account name is known, the Ubuntu security model loses its only real advantage (any other benefits that might be suggested could equally be implemented while retaining a 'root' account).

In closing, I would not propose that Ubuntu change its security model; its users have already been well-indoctrinated in its methodology, it is sufficiently robust for Ubuntu's target audience, and there are some benefits with regard to convenience. Nor would I agree with this topic's title in that root accounts should be covered in the FAQ (I prefer FAQs to address truly "frequent" questions). Nonetheless, information on creating root accounts should be available (in the WIKI) and it should be recognized that root accounts are justifiably preferable for some Ubuntu deployments (I don't  know the current state of the WIKI's commentary on this, it has in the past waivered back and forth on the issue).

I would disagree with the Ubuntu model being "much more secure" than those with root accounts; in fact I would go so far as to say that, in being non-standard, Ubuntu has made the task of educating its users about security more difficult. Regardless, the tools are available for both camps to implement the method of their choosing based on their own needs -- what I like to call "The Linux Way".

Regards.

---

### Post by aysiu on 2007-08-08
> **paulok64 said:**
> everything I tried would lock up terminal and not allow me to enter password after i sudoed it. Are you sure the terminal locked up? Maybe it just wasn't giving you any visual feedback:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by @trophy on 2007-08-08
> **saulgoode said:**
> It is dependent upon who the "they" are against whom you are protecting your system. If "they" are Internet hackers who are randomly surfing IPs in search of 'root' accounts then yes, they would not be likely even to attempt anything outside the standard accounts (root, ftp, guest, smb, etc). But if "they" have specifically targetted your machine then they would likely have no more trouble than I did in discovering your account name.

Is knowing the name of the privileged account really "half the battle"? You would also have to have:

1) Installed 'ssh-server' on your system.
2) Started the SSH daemon.
3) Opened a port for the daemon to monitor (and leave that port at "22" to simplify the hacker's chance of finding it).
4) Specified no rule limiting the range of external IPs permitted to access your system.
5) Configured your server to permit root logins ("PermitRootLogin yes" in 'sshd_config').

The last point is where having a 'root' account actually proves preferable in this situation. How do you prevent your non-root, privileged user from logging in from outside? I imagine it is possible  to have a rule somewhere specify that user 'nekiruhs' is not permitted to do a SSH login -- I haven't deeply investigated how that would be done because the standard *nix security model handles this quite effectively (the same security that is deployed on about two-thirds of the servers on the Internet).

All of that is premised on preventing attacks from "random strangers" in a scenario that the 'typical' home desktop user would likely never encounter. For cases where the "attack vector" is someone who has access to your machine, perhaps even possessing an unprivileged account, the idea that they would not be able to determine the privileged user's account name would require some stretch of the imagination (I am thinking along the lines of the "attack vector" being a younger brother or a mischievous coworker). Once your privileged user's account name is known, the Ubuntu security model loses its only real advantage (any other benefits that might be suggested could equally be implemented while retaining a 'root' account).

In closing, I would not propose that Ubuntu change its security model; its users have already been well-indoctrinated in its methodology, it is sufficiently robust for Ubuntu's target audience, and there are some benefits with regard to convenience. Nor would I agree with this topic's title in that root accounts should be covered in the FAQ (I prefer FAQs to address truly "frequent" questions). Nonetheless, information on creating root accounts should be available (in the WIKI) and it should be recognized that root accounts are justifiably preferable for some Ubuntu deployments (I don't  know the current state of the WIKI's commentary on this, it has in the past waivered back and forth on the issue).

I would disagree with the Ubuntu model being "much more secure" than those with root accounts; in fact I would go so far as to say that, in being non-standard, Ubuntu has made the task of educating its users about security more difficult. Regardless, the tools are available for both camps to implement the method of their choosing based on their own needs -- what I like to call "The Linux Way".

Regards.

=D>

That.  Was.  Awesome.  Couldn't have said it better myself.  And I can say that with authority, as I have tried many times, and failed miserably.

---

### Post by cobrn1 on 2007-08-08
You know, I believe that if you use the alternate install CD and choose expert install mode, you can set a root password, so by defaulting to sudo, with the option to set root password if you really want (and have a good reason too) ubuntu is really being one of the more flexible distros...

---

### Post by golding on 2007-08-16
> **ThrobbingBrain66 said:**
> //big-cut//

To sum things up, not everyone uses Linux to be leet.

**Why not!, I do ... :-)**

---

### Post by Dipper on 2007-08-16
Ubuntu's unique system of defaulting to a restricted account and only allowing incidental access to the root account makes sense for most users because the majority of them use terminal commands to do all of their installations and functions.  Typing "sudo" before each command is not a problem because it's just four extra letters and a password.

However, if you prefer to operate your system graphically, it can be an inconvenience.  Certain functions cannot be accessed by anyone but the root and can only be completed in the terminal using sudo commands.  Logging in graphically under the root account solves this problem.

The main reason why RootSudo doesn't sit well with me is because the underlying message is that the user is incompetent and needs to be saved from himself.  I would hope the information provided here becomes a sticky.

---

### Post by smoore on 2007-08-23
Huh, weird.  I remember back in the wild, wild west of 1998 Linux guys were wondering why us BSD guys would DEactivate the root account (as well as toor) and rely completely on sudo.

Why?  It works.  Simply, it's yet another layer of security in a well structured system.  Just use sudo -i to stay root.  Easy.

---

### Post by K.Mandla on 2007-08-23
> **Dipper said:**
> The main reason why RootSudo doesn't sit well with me is because the underlying message is that the user is incompetent and needs to be saved from himself.
I know some Windows users who might fit that definition ... and therefore prove the need for RootSudo.

---

### Post by aysiu on 2007-08-23
How is that the underlying message?

---

### Post by starcraft.man on 2007-08-23
> **Dipper said:**
> 
However, if you prefer to operate your system graphically, it can be an inconvenience.  Certain functions cannot be accessed by anyone but the root and can only be completed in the terminal using sudo commands.  Logging in graphically under the root account solves this problem.


Why can't one just use gksudo and launch the graphical applications as needed?

> The main reason why RootSudo doesn't sit well with me is because the underlying message is that the user is incompetent and needs to be saved from himself.  I would hope the information provided here becomes a sticky.

Like Aysiu, I am equally perplexed by this. I been using computers for ages and I don't feel incompetent or any lesser for using sudo almost exclusively. I don't see where this message is coming from...

---

### Post by southernman on 2007-08-23
I may well get flamed for doing so but...

Ever come into a conversation that you just know without a doubt is as uselss as the day is long? *cough*

You could talk till your blue in the face. It isn't going to change the way Ubuntu deals with root. It's one of the stronger selling points of Ubuntu. One I see on so many sites and 99.9999% of the talk about it is positive.

sudo or cedoyoulater <--- I know... it's lame!

---

### Post by hans12345 on 2007-08-25
Hey, I can see this is a hot topic.

Thanks BillBob.

Let's have more information about root clearly available, with all the needed health warnings. Or, if the Ubuntu approach is different,  more information why root is not available, and why, and how to do things without root.

It is information that is missing.

I have just installed Ubuntu (my first time near Unix for 20 years) and it looks real good, but I need new Nvidia drivers. Out there in the Web everyone gives instructions on installing stuff and they say things like log on as root.

I wasted 2 days trying to find out about root on Ubuntu. Until I found this thread.

So, thanks BillBob

---

### Post by blithen on 2007-08-25
That's kinda sad...complaining about FOUR letters...come on...I don't mean to be harsh, but suck it up.
If you have to do something that uses root graphically then
gksudo <command>

---

### Post by aysiu on 2007-08-25
> **hans12345 said:**
> 
Let's have more information about root clearly available, with all the needed health warnings. Or, if the Ubuntu approach is different,  more information why root is not available, and why, and how to do things without root.

It is information that is missing. No, it isn't:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by maybeway36 on 2007-08-25
when I want to log in as root, I've always logged in as myself and then issued the command:
```
exec sudo su -
```

---

### Post by aysiu on 2007-08-25
> **maybeway36 said:**
> when I want to log in as root, I've always logged in as myself and then issued the command:
```
exec sudo su -
```
What about this? ```
sudo -i
```

---

### Post by K.Mandla on 2007-08-25
This is all kind of funny to me, since I regularly use Arch Linux, which gives you a root account at installation.

And then I immediately install sudo, because I'd rather have it.

---

