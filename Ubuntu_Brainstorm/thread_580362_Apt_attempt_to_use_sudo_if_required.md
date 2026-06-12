---
title: "Apt attempt to use sudo if required"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by nesl247 on 2007-10-18
apt-get and aptitude should attempt to use sudo if required when called from the command line.

A lot of times I forget to append sudo to the beginning of the command. I know I could make an alias, but that means EVERY bit of those commands are run under sudo. A simple search or show doesn't really require root permissions.

---

### Post by Megatog615 on 2007-10-19
I'm quite the opposite. I tend to accidentally use sudo with apt-cache on accident. If I could just type apt-get or apt-cache and be prompted only when I need to be, that would be great.

---

### Post by Zdravko on 2007-10-19
Hmm, I rather don't have to type that "sudo". Like the idea.

---

### Post by AusIV4 on 2007-10-19
I think it's a good idea because I've known several beginning users who found that adding sudo to commands made them work more often, so they just started prepending sudo to every command without really understanding the consequences. I think the less often users have to type sudo, the better.

---

### Post by Twintop on 2007-10-19
Is it just me, or does this scream, "Giant Security Hole" to anyone else? Honestly, sudo is there for a reason: do as the super user. You don't want to open the possibility of giving any application access to root that shouldn't need it. Example: simple bash script that tells apt-get to remove ubuntu-desktop. User runs it, and there is no sanity check at all. Suddenly, a convenience for new users becomes a nightmare for a new user -- and this is just a very, very simple example. The benefits vs. the risks just are not justifiable in my opinion.

---

### Post by Zdravko on 2007-10-19
[Twintop]("http://ubuntuforums.org/member.php?u=275596"), nice arguments.

---

### Post by bethaviv on 2007-10-19
> **Twintop said:**
> Is it just me, or does this scream, "Giant Security Hole" to anyone else? Honestly, sudo is there for a reason: do as the super user. You don't want to open the possibility of giving any application access to root that shouldn't need it. Example: simple bash script that tells apt-get to remove ubuntu-desktop. User runs it, and there is no sanity check at all. Suddenly, a convenience for new users becomes a nightmare for a new user -- and this is just a very, very simple example. The benefits vs. the risks just are not justifiable in my opinion.

You have to sacrifice convenience for security, something Microsoft hasn't learned yet, I think. I don't mind typing sudo... when I do, I know my OS is doing it's job =)

---

### Post by Zdravko on 2007-10-19
I hate writing "sudo".

---

### Post by shad0w_walker on 2007-10-19
I doubt that the requirement for sudo will disappear any time soon. As far as I am aware the point of Ubuntu is to make the OS as friendly as possible and for most people that means using the GUI for everything. 

With the GUI is automatically does the whole gksu bit so it doesn't come up to be an issue when you look at the end goal of Ubuntu.

---

### Post by Zdravko on 2007-10-19
What is gksu?

---

### Post by shad0w_walker on 2007-10-19
It does the same job as sudo but geared more towards to GUI based apps. It's that popup window you get when you run synaptic or other admin programs.

---

### Post by m0eman on 2007-10-19
> **Twintop said:**
> Is it just me, or does this scream, "Giant Security Hole" to anyone else? Honestly, sudo is there for a reason: do as the super user. You don't want to open the possibility of giving any application access to root that shouldn't need it. Example: simple bash script that tells apt-get to remove ubuntu-desktop. User runs it, and there is no sanity check at all. Suddenly, a convenience for new users becomes a nightmare for a new user -- and this is just a very, very simple example. The benefits vs. the risks just are not justifiable in my opinion.

Agreed.

---

### Post by nesl247 on 2007-10-19
I don't see how it's a security hole. All this would be is a command line version of the installation instances which call gksu. If it was implemented, something could be done to tie into sudo to reset the cache of the password so that the password is always asked.

---

### Post by Twintop on 2007-10-19
> **nesl247 said:**
> I don't see how it's a security hole. All this would be is a command line version of the installation instances which call gksu.

gksu is a GTK+ frontend to su and sudo, so you still are going to be calling sudo no matter what.

> **nesl247 said:**
> If it was implemented, something could be done to tie into sudo to reset the cache of the password so that the password is always asked.

This is already in place. I believe it is somewhere in the range of 10 minutes after you last called sudo or gksu that you don't have to enter your password again. This is probably configurable if you're willing to hunt for it.

---

### Post by Zdravko on 2007-10-20
I wish the time interval was more than 10 minutes.

---

### Post by dfreer on 2007-10-20
This isn't windows, guys, where you can only do things one way. If you don't having to type sudo, why not just disable it completely? It's your linux, customize things the way you want it. And you can change the time interval as well, so that if you type sudo once in a session it remains open until you log out.

More than that, the "new" user shouldn't have to use apt-get in terminal anyways, they would be using synaptic/add-remove programs/etc which asks for the sudo password when run.

---

### Post by Zdravko on 2007-10-20
Hmm. How do I do that exactly?

---

### Post by dfreer on 2007-10-20
What exactly did you want to do? I mentioned several things... 

You can give yourself root powers by changing your UID/GID to 0, or you could simply enable the root account by giving it a password and login with it (You'll need to edit gdm to allow root logins when using ubuntu, exactly how I can't remember off the top of my head, but you should find it relatively quickly on the forums). I don't recommend any of this, but I really don't care if you bork your own machine :p

---

### Post by FrankQuist on 2007-10-20
I wouldn't exactly suggest apt-get to override the sudo prompt. But if it  prompted for the password (just like the GUI Add/Remove manager) if there wasn't the sudo cache thing going on, that would be nice.

---

### Post by Awalton on 2007-10-20
Simple solution for CLI updaters:
in your .bashrc:
alias apt-install='sudo apt-get install'
alias apt-update='sudo apt-get update'
alias apt-upgrade='sudo apt-get upgrade'

Any time you need install something, you just type "apt-install packagename", and you're prompted for your password. Same goes for update and upgrade (and can be rolled into one command if you so wish). There's really no reason to include this by default as most users won't want this kind of behavior.

---

### Post by Zdravko on 2007-10-21
I want to increase the time onterval between "sudo"-s.

---

### Post by Frak on 2007-10-21
I like the idea as long as when it prompts the user for his/her/its password it explains why.

---

### Post by Zdravko on 2007-10-21
Yes, an explanation would be nice.

---

