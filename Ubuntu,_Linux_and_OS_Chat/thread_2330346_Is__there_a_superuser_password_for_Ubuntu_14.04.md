---
title: "Is  there a superuser password for Ubuntu 14.04"
date: 2016-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by wjbradley on 2016-07-10
I installed Ubuntu 14,04 successfully on an HP Mini tablet that I have. This was accomplished from a thumb drive.
A screen keep coming up that I have a problem and when I click on it to see what it is it asks for my root or superuser password.
I don't remember putting in a root password during the installation. It asked me to name the computer which I did but that is not what I am looking for here.
So I am stuck and any help would be appreciated.
Thank you, William

---

### Post by &amp;KyT$0P# on 2016-07-10
root password is disabled and locked by default in Ubuntu.  But you should be able to become root using the password for the account you set up in the installation.

---

### Post by oldfred on 2016-07-10
[https://3.bp.blogspot.com/-ZA7bWlTQ5Y0/Vjfct9BRGjI/AAAAAAAAKxQ/iEUthjiM0Qw/s640/ubuntuinstall9.png](https://3.bp.blogspot.com/-ZA7bWlTQ5Y0/Vjfct9BRGjI/AAAAAAAAKxQ/iEUthjiM0Qw/s640/ubuntuinstall9.png)

When installing you have to create password in screen similar to above.

---

### Post by wjbradley on 2016-07-10
Over the years I have installed many distros and in the installation have had go through a "user" and "root" setups. I simply do not remember doing it for this distro. So can you point me to where my membership is on Ubuntu. I read an article on how to bring on a new member and give them root privileges. It was all command line stuff and this is a bit more than m I want to deal with at the moment.
Any further suggestions will be appreciated.
William.

---

### Post by lisati on 2016-07-10
As has been noted, the "root" or "superuser" user is disabled/locked by default in Ubuntu. A common way of temporarily granting superuser privileges is by prefixing commands with "sudo" - more information can be found [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by grahammechanical on 2016-07-10
I use the development version of the next release of Ubuntu (16.10) so it is normal to get messages about system problems. I am always able to see details of the problem before I am required to enter my password. I just click a button labeled Details. If I want to send a report about the problem I click Continue and then I am asked to Authenticate sending the report. This is because as part of the reporting process certain log files are copied and they may contain information such as password. The OS needs my authorization to send those log file to the Ubuntu developers.

 I am never asked for a root password. When Ubuntu asks us to Authenticate we enter the password that we created when we first installed Ubuntu. See the installation guide section 7 - Enter your login and password details. That is how it is done in Ubuntu. Unlike some distributions we do not create a root account and a non root account for Ubuntu.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)

Regards.

---

### Post by mastablasta on 2016-07-11
it is your user password. the first created user is also a super user/admin or rather a member of that group.

---

### Post by &amp;KyT$0P# on 2016-07-11
> **grahammechanical said:**
> I use the development version of the next release of Ubuntu (16.10) so it is normal to get messages about system problems. I am always able to see details of the problem before I am required to enter my password. I just click a button labeled Details. If I want to send a report about the problem I click Continue and then I am asked to Authenticate sending the report. 
Not so in 14.04 where if the problem happens when not fully logged in we have to authenticate to even see the report information

---

### Post by pauljw on 2016-07-11
> **wjbradley said:**
> Over the years I have installed many distros and in the installation have had go through a "user" and "root" setups. I simply do not remember doing it for this distro. So can you point me to where my membership is on Ubuntu. I read an article on how to bring on a new member and give them root privileges. It was all command line stuff and this is a bit more than m I want to deal with at the moment.
Any further suggestions will be appreciated.
William.

I came from a distro that had root access, too.  It took a bit to get accustomed to the 'sudo' philosophy, but I'm cool with it now.  I have only one beef with it.  In a system with a root acct/password, two passwords must be breached before allowing unauthorised system access.  In a sudo system, only one needs to be breached.  Other than that, sudo does a fine job of elevating a user to superuser for system changes and package installs.

So you simply use your acct password when prompted in order to make changes that require superuser access.  Other users can be added to the sudo group if you have multiple accounts set up on your computer and you want those users to have system access.

Paul

---

### Post by &amp;KyT$0P# on 2016-07-11
> **pauljw said:**
> In a system with a root acct/password, two passwords must be breached before allowing unauthorised system access.
As a user of both types of distro, I only count one password required for root access either way.  In root-account-enabled distro, obviously one is the root password itself, which can be used, say, to directly log in as root from a console tty (not recommended unless needed in case of emergency! ;) ).. but what's the second password?

---

### Post by pauljw on 2016-07-11
You're right, only the root password would be needed.

---

### Post by T.J. on 2016-07-11
Resolving the root access is easy.  Just use the sudo account to set root password "sudo passwd root".   The root account is there, it is just flagged as locked.  Resetting the password will remove the flag.  If you want to restore the lock in the future, use the *usermod* command with the proper options.

I find sudo to be useful, but an annoyance.  Certain commands, such as long cp commands do not work in sudo unless you spawn a shell. If you are going to do that, why bother using sudo in the first place?  It seems self defeating. Sudo is useful if you are running a server as it records access for audit.  On a desktop, I'd rather disable it and use the root account sparingly. If you want the pros and cons of sudo, I am sure you can find them somewhere.

---

### Post by montag dp on 2016-07-11
Sudo becomes annoying if you want to do more than one or two commands as root.  It won't ask for a password again for a certain length of time, but you still have to enter "sudo" in front of every command.

---

### Post by QIII on 2016-07-11
Disabling a security feature is unwise, but you are free to do whatever you wish on your machine.  Suggesting such a solution in a public forum where new users, without the experience to tell them the dangers, is irresponsible.

Please see [this]("https://help.ubuntu.com/community/RootSudo") for the Forums Staff's policy on root and sudo.  This is what we would prefer to be the stock answer with regard to root and sudo.

Notice that there is a suggestion for how to avoid repetitive use of "sudo" and it does NOT require disabling a security feature.

---

### Post by uNoubu8a on 2016-07-11
> **montag dp said:**
> Sudo becomes annoying if you want to do more than one or two commands as root.  It won't ask for a password again for a certain length of time, but you still have to enter "sudo" in front of every command.

Then again if you are going to be entering multiple commands that need root and don't want to set the root password (which if memory serves was typically thought not to be a good idea) you simply have to use;
```
sudo su -
```

---

### Post by montag dp on 2016-07-11
> **work-work said:**
> Then again if you are going to be entering multiple commands that need root and don't want to set the root password (which if memory serves was typically thought not to be a good idea) you simply have to use;
```
sudo su -
```That's good to know.  I didn't realize sudo would let you get an su shell.

---

### Post by T.J. on 2016-07-11
> **QIII said:**
> Suggesting such a solution in a public forum where new users, without the experience to tell them the dangers, is irresponsible.

Please see [this]("https://help.ubuntu.com/community/RootSudo") for the Forums Staff's policy on root and sudo.  This is what we would prefer to be the stock answer with regard to root and sudo.

Notice that there is a suggestion for how to avoid repetitive use of "sudo" and it does NOT require disabling a security feature.

I'm confused.  Please forgive me if I seem rude, but at no point did anyone suggest actually disabling sudo or even explain how. Speaking only for myself, I expressed an opinion regarding the value of sudo (which I believe is limited, buggy and severely "overhyped" - but that is beside the point). 

The original poster asked about the root account, and advice was offered as to accessing it.  There are legitimate reasons to do so.  Some of which stem from the fact that Ubuntu is based on Debian, but Canonical does not manage the entire codebase - so occasionally a bug is missed. Since Debian, by design, has the root account enabled - it is sometimes beneficial to do so on Ubuntu. I am not criticising you or policy, as I am just a guest here. However, even if there weren't legitimate reasons, I believe it is up to each person to decide what is "responsible" for themselves as it is impossible to fully know or judge their situation by a forum post.

I bid you all a good day.

---

### Post by wildmanne39 on 2016-07-11
> **T.J. said:**
> I'm confused.  Please forgive me if I seem rude, but at no point did anyone suggest actually disabling sudo or even explain how. Speaking only for myself, I expressed an opinion regarding the value of sudo (which I believe is limited, buggy and severely "overhyped" - but that is beside the point). 

The original poster asked about the root account, and advice was offered as to accessing it.  There are legitimate reasons to do so.  Some of which stem from the fact that Ubuntu is based on Debian, but Canonical does not manage the entire codebase - so occasionally a bug is missed. Since Debian, by design, has the root account enabled - it is sometimes beneficial to do so on Ubuntu. I am not criticising you or policy, as I am just a guest here. However, even if there weren't legitimate reasons, I believe it is up to each person to decide what is "responsible" for themselves as it is impossible to fully know or judge their situation by a forum post.

I bid you all a good day.
Hello if the OP reads the whole link it does give the information needed to do what he asks but it gives the preferred methods first that are the safest.

---

### Post by mastablasta on 2016-07-11
> **T.J. said:**
>  It seems self defeating. Sudo is useful if you are running a server as it records access for audit.  On a desktop, I'd rather disable it and use the root account sparingly.

server is a fancy PC running services usually only in CLI. a new user might install a service on a desktop requiring him to open a port. unless you are under some hacker collective eye, the automated scripted attacks all try to brute force into root or lately pi user. they start within 24 hours of opening the port. so first - why give attackers (bots as it seems) the username?

also i use it so rare (mostly just for updates), so i don't see an issue in using this feature.

---

### Post by DuckHook on 2016-07-11
> **wjbradley said:**
> Over the years I have installed many distros and in the installation have had go through a "user" and "root" setups. I simply do not remember doing it for this distro. So can you point me to where my membership is on Ubuntu. I read an article on how to bring on a new member and give them root privileges. It was all command line stuff and this is a bit more than m I want to deal with at the moment.
Any further suggestions will be appreciated.
William.Welcome to Ubuntu and the forums, wjbradley. You seem to have wandered into one of the recurring holy wars of Ubuntu that arouse great passions on both sides. As a non-technical user like yourself, I hope I can give you my own personal view on this matter. I take pains repeating that what follows is purely a personal view, and should not be mistaken for forum policy or anything other than my personal views:

You will know by now from the other reply-posts that Ubuntu defaults to using sudo rather than enabling root. I feel that this is a superior strategy for new users because it generally leads to less trouble. This is not because there is something inherently wrong with enabling the root account, nor due to any inherent superiority of sudo (this is also why the holy war that exists between the two camps is so confusing to me). Rather, it has to do with human nature. To be blunt, humans have a propensity to do dumb things when given too much power. Given a choice between convenient laziness and inconvenient thoughtfulness, most people&#8213;especially new users&#8213;choose convenient laziness. In the case of operating systems, this can lead to major problems. I am not too proud to admit that when I started out with Linux, I once wiped out my entire system precisely because I enabled my root account, forgot I was in it, and invoked the *rm* command from the / directory. This would not have happened had I made a habit of using sudo. That very small step of having to prepend the word *sudo* in front of *rm* would have stopped me from doing a really stupid thing.

So, that's the real reason for *sudo*. It enforces good habits. And after many years of helping out people who get into trouble, what has become clear to me is that most of the battle in avoiding trouble involves cultivating good computing habits. The technical aspects are actually of secondary importance. So, the debate over which method is technically more "efficient", or "less buggy", or "more linux" is really beside the point. It's a human consideration, not a technical one.

---

### Post by T.J. on 2016-07-11
> **mastablasta said:**
> server is a fancy PC running services usually only in CLI. a new user might install a service on a desktop requiring him to open a port. unless you are under some hacker collective eye, the automated scripted attacks all try to brute force into root or lately pi user. they start within 24 hours of opening the port. so first - why give attackers (bots as it seems) the username?

also i use it so rare (mostly just for updates), so i don't see an issue in using this feature.


Honestly that hacking justification for disabling root disappeared years ago.  You can block remote access to root, so that it is console only.

---

### Post by mc4man on 2016-07-12
> **wjbradley said:**
> Over the years I have installed many distros and in the installation have had go through a "user" and "root" setups. I simply do not remember doing it for this distro. So can you point me to where my membership is on Ubuntu. I read an article on how to bring on a new member and give them root privileges. It was all command line stuff and this is a bit more than m I want to deal with at the moment.
Any further suggestions will be appreciated.
William.
Considering  your use of "membership" I'd suggest you go to Systems Settings > User Accounts, should be obvious there.

---

