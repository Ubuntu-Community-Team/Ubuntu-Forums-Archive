---
title: "if i can do only one thing to make my computer secure, what would it be?"
date: 2009-11-29
forum: Security
---

### Post by expxe on 2009-11-29
on my windows computer i have kaspersky internet security, that ONE program takes care of all my security needs

on ubuntu, im pretty much on a default install. if i were to just choose one program that would protect my computer, what should it be?

please include detailed step by step instructions for install as well, thanks

---

### Post by insane_alien on 2009-11-29
probably configure the firewall if you are running any services. its already installed and is called iptables. i'm pretty sure the current frontend ubuntu uses is ufw

here's the instructions:

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

i'd type them out but why bother when that one does it so well.

but as it stands, a default ubuntu install is far more secure than windows + kaspersky

---

### Post by User0123 on 2009-11-29
Programs don't make your computer secure. In linux, you do.

---

### Post by admelfo on 2009-11-29
Don't let anyone else use it.

---

### Post by whoop on 2009-11-29
Installing programs to improve security is like fighting the symptoms of a disease, instead of fighting it's cause (lame and probably not even true, I know, but I'm trying to make a point)

It is more logical (in linux) to ask: which rules should I follow to be more secure?

The default ubuntu install is very secure (it didn't even get hacked in the last CanSecWest security conference). So you could state: keep your ubuntu as default and updated as possible <-- every program/service you install makes it potentially less secure (especially if installed from outside of the repos)

An operating system is only as secure as the least secure program installed on it (also quite lame ;) )

---

### Post by BkkBonanza on 2009-11-29
Turn it off.
Just kidding. But really your security is much more related to what you do than any program you install. The default install is secure so don't install any programs from unknown/unsigned sources.

---

### Post by lovinglinux on 2009-11-29
[Ubuntu Security Sticky](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by Agent ME on 2009-11-29
> **admelfo said:**
> Don't let anyone else use it.
This is just silly. Linux is a multiuser system built so several users can use it without being able to step on each other's toes.
If you have other users of your computer, give them each their own account. As long as you don't make them part of the admin group, there is nothing they can do bad on the system beside spawn a bunch of cpu-eating processes or putting large files on the hard drive (which are obvious and very easy to clean up; at worst, you can just remove the user's home folder and start them new, or just not even give them a new account).

> **User0123 said:**
> Programs don't make your computer secure. In linux, you do.
This is great advice. Learn about your system, and don't download things randomly and run (most windows malware comes from this mindset). Everything in the ubuntu software repository is safe and reviewed; let that be the first place to look for software.
If you're searching on google for a certain linux program to do something, and find one, instead of downloading it from the website, check to see if it's in the repository. If it is, install it from there. If it isn't, maybe look for an alternative that is in the repository, or read more about the program and other people's reviews of it to make sure it isn't shady.

---

### Post by SuperSonic4 on 2009-11-29
> **Agent ME said:**
> This is just silly. Linux is a multiuser system built so several users can use it without being able to step on each other's toes.
If you have other users of your computer, give them each their own account. As long as you don't make them part of the admin group, there is nothing they can do bad on the system beside spawn a bunch of cpu-eating processes or putting large files on the hard drive (which are obvious and very easy to clean up; at worst, you can just remove the user's home folder and start them new, or just not even give them a new account).

I would say that locking your PC whenever you leave it is the most practical step you can take- even if you go the toilet or the kitchen

From a software point of view you're right but they can easily pop in a live CD and away they go.

Controlling physical access to your PC is best - keep sensitive data off the local machine and on your person or in a very safe place far from any machine.

---

### Post by Slowspeed on 2009-11-29
Use a password phrase that is at least 15 characters long.

Regards.

---

### Post by koenn on 2009-11-29
> **expxe said:**
> if i can do only one thing to make my computer secure, what would it be?
Think.


As others pointed out, security is not about installing programs. All in all, a default Ubuntu is pretty secure. The problems start when you start to modify it - and you will.
[I]
Every time[/I] you modify the system, ask yourself these couple of questions in light of the changes your about to make:
1- how do I keep the bad guys out ?
2- how do I let the good guys in ?
3- how do I tell the good guys from the bad guys ?
4- how do I keep the good guys from doing bad things

You'll find that all of them apply to simple modifications such as creating a user account to more tricky ones such as setting up file sharing and remote desktops. There well often be more that one solution to each question. You can choose between them, or combine them, 
It's at this point, and no sooner, that you start looking at programs, i.e. the tools that will let you implement your solution. 


And it'll even work on Windows.

---

### Post by wilee-nilee on 2009-11-29
Kaspersky alone hardly makes your MS OS secure, kaspersky is a well known AV program and the people trying to get in will write code to disable it long before kaspersky even realizes it and downloads a new protection. You might at the least try a couple of other free AV programs like.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
[http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)
These along with ccleaner are very good tools especially if you load them to a open cd or thumb in case a redirect trojan locks up you computer or use.
[http://www.ccleaner.com/](http://www.ccleaner.com/)

---

### Post by rookcifer on 2009-11-29
> **expxe said:**
> on my windows computer i have kaspersky internet security, that ONE program takes care of all my security needs

on ubuntu, im pretty much on a default install. if i were to just choose one program that would protect my computer, what should it be?

please include detailed step by step instructions for install as well, thanks

LOL at your signature.

As for security, you don't need anything when using Ubuntu.  Just remember to always install all your software from the Ubuntu repos.  That's all you need if you are only running a desktop box.

---

### Post by expxe on 2009-11-29
where is this "ubuntu repos" that you speak of? surely not every piece of software for linux is available there (what about obscure wireless card drivers)?

---

### Post by Agent ME on 2009-11-29
Check the Ubuntu Software Center (it's under Applications) for a list of the desktop programs in the Ubuntu repository. Some good programs include Inkscape, which is good for drawing graphics, and Cheese, which is a simple program for using a webcam to take pictures and video.

A full list of packages in the Ubuntu repository can be found at System -> Administration -> Synaptic Package Manager. This list includes everything in Ubuntu Software Center, and also many command-line programs and system packages that other programs depend on. Almost all commonly used utilities exist here; the only times I have to install things from outside of the repository is when I'm setting up a system that needs an obscure driver or I'm installing a game.

When using Synaptic, make sure to check what a package is exactly before you install it. Some, like openssh-server, allow your computer's users to log in remotely, and if your users don't have good passwords set up, you've opened yourself up to possible attacks.

---

### Post by powerpleb on 2009-11-29
> **expxe said:**
>  if i can do only one thing to make my computer secure, what would it be?

please include detailed step by step instructions for install as well, thanks
1. Turn it off.
2. Don't turn it back on.

---

### Post by steveneddy on 2009-11-29
> **BkkBonaza said:**
> Turn it off.

Unplug it from the internet.

/jk

I don't think that a regular Ubuntu desktop install really needs any virus detection or removal software.

If you are running a server you would want to consider it.

---

### Post by Marvin666 on 2009-11-29
Make it so only tech-savy people can boot it...
```
To log on solve the following problem:
10110110111+101001
```
If they answer 10111100000, then they can log on.
If they answer 10110211112, then shut down.

---

### Post by ve4cib on 2009-11-29
> **Agent ME said:**
> When using Synaptic, make sure to check what a package is exactly before you install it. Some, like openssh-server, allow your computer's users to log in remotely, and if your users don't have good passwords set up, you've opened yourself up to possible attacks.

You can mitigate those kinds of problems by setting up iptables to allow SSH connections from specific IP addresses only.  For example, if you're on a home LAN with three machines set up with static IP addresses it's pretty trivial to allow only those machines to connect over SSH.

You can also configure the SSH server to only allow specific users to log in remotely.  If you set it up so that only non-sudoers can SSH in then the security risk from weak passwords is relatively low, since the only users who can SSH in have low privileges.  Using chmod to prevent remote users (aka users who can SSH into the machine) from reading sensitive files is the next logical step.

But really, as others have said, there is no single program that you install and it will magically make your computer secure.  There is no such program for Windows, and there is no such program for Linux either.  It all comes down to knowing your system and being a good administrator.

---

### Post by crimesaucer on 2009-11-29
I use iptables with a "stateful firewall script" that drops the packets of common attacks and incoming requests (so as to hide my computer).

---

### Post by MaxIBoy on 2009-11-30
Find any non-root file which is executable, and "chmod -r" it to make it read-only. (This probably includes your .bashrc and .bash_profile.) If you need to edit it, then 
```
chmod -x file #make it no longer executable
chmod +r file #make it editable
<edit your file>
chmod -r file
chmod +x file
```You can find all executable files not owned by root using this method:
```
ls -la | grep "^-" | grep -v root | sed "s/ \+/ /g" | grep  "^[^ ]*x[^ ]* " | cut -d' ' -f9
```How does this help? Well, as an example, the .bash_profile is run every time a shell is opened. Since it is modifiable by default, you can alias "sudo" as a few lines of shell script which will steal your password and hide it somewhere for future use. This way, you need to run something as root or else it can't modify your .bash_profile in this way.

---

### Post by EJeanmaire on 2009-11-30
> **Slowspeed said:**
> Use a password phrase that is at least 15 characters long.

Regards.

This.  Maybe not 15, but complex and lengthy is a plus.

Or you could buy this amazing computer speed booster I saw advertised on late night TV, which will free your computer from the from malware's evil grasp!  On second thought... Stick to the first suggestion.

---

