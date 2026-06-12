---
title: "Is it true all Linux ,Unix and Mac computers default root account is locked"
date: 2011-03-14
forum: Security
---

### Post by nec207 on 2011-03-14
People say and some web sites I gone to say by default root account is locked in Linux ,Unix and Mac computers not like windows.
 
And need a root password to do stuff. ( not saying what stuff you need a root password ) But what is strange is in windows we just log out the user profile into the admin profile to do stuff.
 
So it is hard for windows users like my self to understand this .
 
 
> The root user (also known as superuser), full administrative privileges (full access). So using root account for daily work can be very dangerous and you may damage your working system.
 
Most people I know that use windows and know what they are doing uses 2 account one admin for windows use and other for internet use that is not a admin account .
 
But 90% of windows user just run has admin for every thing.
  
> By default root account is locked under Linux ,Unix and Mac computers Therefore, you cannot login as root or use 'su -' command to become a superuser.
 
 
Explain better .Why do they do this by default ?Why not give the people the option to choose ?
 
Can you change this later.
 
> To run all administrative command use sudo command. sudo allows a permitted user to execute a command as the superuser or another user
 
 
I thought default root account is locked ?Can you set it up so you can login has a root user. Or by default that is blocked.
 
_Note I got the QUOTEs_ doing a internet using google to try to explain this better but I got more confused reading the web sites on this.
 
It is so hard for windows user do to by default the account we are admim.And we do not have this stuff like Linux ,Unix and Mac computers hat need a password for stuff or have to run sudo command to do stuff.

---

### Post by doas777 on 2011-03-14
yes in ubuntu root is a locked account and you cannot use it without enabling it, but 99% of users do not need root, because we have sudo

this is the place to start:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

think of sudo/gksu as teh same as right clicking somthing in windows and then saying "run as admin". same concept, but better implementation.

---

### Post by cchhrriiss121212 on 2011-03-14
You do have the option to choose to run as root, but showing how to do it is not allowed on this forum (google will show you the way).
> Why do they [disable root account] by default?
Running as root is dangerous, that's why it is not there by default.

There is nothing hard about using sudo, it just takes a few keystrokes to put your password in every now and then. You will get used to it after a few days.

---

### Post by nec207 on 2011-03-14
> **doas777 said:**
> yes in ubuntu root is a locked account and you cannot use it without enabling it, but 99% of users do not need root, because we have sudo
 
this is the place to start:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
think of sudo/gksu as teh same as right clicking somthing in windows and then saying "run as admin". same concept, but better implementation.
 
 
I thought sudo is command line with command admin.
 
 
Why do people not need root?

---

### Post by bodhi.zazen on 2011-03-14
This is a recurring discussion and has been discussed with several variations several times.

Ubuntu chooses to lock the root account as a part of how security is handled, but this is certainly NOT true of all Linux distros.

Fedora uses su and one sets a root password when installing.

Debian gives you the option of su or sudo when you install (or at least it did last time I installed it).

Slax, a live CD, and others, the system runs as root.

The point is, as you say, you should understand the security implications of all the various options and configure the system the way you like.

---

### Post by doas777 on 2011-03-14
> **nec207 said:**
> I thought sudo is command line with command admin.
 
 
Why do people not need root?
sudo is used to run command line apps as root, whereas gksu runs graphical programs as root.

this might help demonstrate:
```

user@Lucid:~$ whoami
user
user@Lucid:~$ sudo -i 
[sudo] password for user: 
root@Lucid:~# whoami
root
root@Lucid:~# 


```

---

### Post by wojox on 2011-03-14
> **nec207 said:**
> I thought sudo is command line with command admin.
 
 
Why do people not need root?

No if you open a GUI application that needs root / admin privileges you will be asked for a password. Linux is a true multi-user environment. You don't want everyone running around all willee nillee under root.

Root is used for system maintenance and such.

No not all distro's come with default root account locked.

---

### Post by nec207 on 2011-03-14
> **wojox said:**
> No if you open a GUI application that needs root / admin privileges you will be asked for a password. Linux is a true multi-user environment. You don't want everyone running around all willee nillee under root.
 
Root is used for system maintenance and such.
 
No not all distro's come with default root account locked.
 
 
So if I understand there is 2 ways to get root privileges 
 
1. using the GUI you put in password or 2 use sudo is a command line with command admin.Think if sudo like DOS or command promt but sudo is a command line with root privileges .
 
Do you need root privileges every time you install, remove or modify some thing on the computer.

---

### Post by rookcifer on 2011-03-14
> **nec207 said:**
> So if I understand there is 2 ways to get root privileges 
 
1. using the GUI you put in password or 2 use sudo is a command line with command admin.Think if sudo like DOS or command promt but sudo is a command line with root privileges .

No, not really.  Think of it like this:  Root is a user on the system.  Root is all powerful and can do anything.  Every Unix system, by default, has a root user.  Some distros decide to lock the root account so that people will not log-in to the root account for day to day activity.  Ubuntu is one of these distros.

Back in the day, it became apparent to Unix admins that various users on their systems might need to do root stuff, but they didn't want all of their users to have the root password (think about it, if everyone on the system had root access, it makes root pointless).  So, someone invented "sudo" which gives individual users the right to do select root stuff without having to have the root password.  In other words, sudo is fine-grained and the administrator can allow only certain commands to be run with it if he so chooses.  Or, he can allow sudo to be all powerful just like root.  The latter is the default on Ubuntu.

Root and sudo has nothing to do with the GUI or command line.  Root is a user on the system.  Sudo allows non-root users to do root stuff.  Ubuntu makes it so that the root account is locked, but users can still do root stuff by using the sudo command.  The difference is that on Ubuntu one cannot *log-in* to the root account.  That is, one cannot log-in and begin using the browser or desktop as root on Ubuntu.  If you need root privs for a specific task, you use sudo.  This makes it so that the root privs are only used when they are needed and are not unnecessarily abused.
 
> Do you need root privileges every time you install, remove or modify some thing on the computer.

Most of the time, you will.  You just enter your sudo password and the operation will be completed.  Then the root privs are dropped automatically.

---

### Post by nec207 on 2011-03-14
Okay that do this as that may explain it better by looking at it like windows.In windows by default one account is alway full admin.The IT administrator will make accounts for users with little to no privileges .So the IT administrator may make a account so the user cannot install, remove or modify even see other people accounts .
 
Even the users their own files ,desktop wallpaper,screansaver ,pictures ,music so on is for that account and that account only .The IT administrator will log onto his or her account and can make new accounts for users or delete user accounts .
 
The problem with PC in the home is by default one account is alway full admin and that is what most people use for every think , Where has in the IT world the IT administrator will make accounts for users with little to no privileges.If the IT guy wanted he could say yap that guy we do not want him to install, remove or modify any thing or even have read and write privileges out side is account.
 
Well Linux ,Unix and Mac by default the user is just a user that can run admin privileges but need authentication to do admin stuff that is where the password or sudo comes in that is the authentication .Think of windows vista the UAC that comes up for admin stuff the cancel or allow but Linux ,Unix and Mac use password or sudo .
 
- sudo is a command line than GUI?

---

### Post by BkkBonanza on 2011-03-14
**sudo** for command line.
**gksu** for gui apps that don't normally run as root.
eg. you can have a menu item or shortcut that calls **gksu nautilus** to run the file manager with root rights and it will prompt for your password before starting.

Most gui apps that regularly do root stuff have either gksu built in or handle the password request internally. (Similar to windows asking for admin rights).

eg. when you use **gparted** to alter the partitions on your drive it will check if you have sudo rights and prompt for your password. or when you use **synaptics** to add new software it does this internally and prompts for your password.

The **sudoers** file controls who has rights to do what on a very fine grain level.

Since there is typically a time limit on sudo rights you find that on Ubuntu you have to re-authenticate regularly. This tries to help against you mistakenly leaving your system wide open with root privileges as you walk away for a while.

---

### Post by jerome1232 on 2011-03-15
You can think of any user that is granted sudo rights as an administrator. They just don't run tasks as an admin all the time, only when they need to.


On desktop computer this makes a lot more sense to me than having to logout of your regular account, then log into your admin account just to install updates, or install a system program.

---

### Post by rookcifer on 2011-03-15
> **jerome1232 said:**
> On desktop computer this makes a lot more sense to me than having to logout of your regular account, then log into your admin account just to install updates, or install a system program.

You don't have to log-out of your user account to install updates or programs on any Linux or Unix system I am aware of.

---

### Post by jerome1232 on 2011-03-15
> **rookcifer said:**
> You don't have to log-out of your user account to install updates or programs on any Linux or Unix system I am aware of.

If it doesn't have sudo installed you would, though everyone I have tried does have it installed regardless of whether the root account was locked or not.

edit: Maybe I should rephrase that to switching users.

---

### Post by nec207 on 2011-03-15
> **rookcifer said:**
> You don't have to log-out of your user account to install updates or programs on any Linux or Unix system I am aware of.
 
 
 
I think he was talking about windows and saying that is one thing he like about Linux or Unix .
 
 
 
 
> sudo for command line.
gksu for gui apps that don't normally run as root.
 
 
Okay this may explain it better for a windows user to understand you saying sudo or gksu you can think sort of like the UAC that comes up for admin stuff the cancel or allow in windows vista and windows 7.
 
But sudo or gksu is just asking for authentication for admin stuff .
 
The sudo command line for people that like to use the command line and gksu is GUI base for people that like to use the GUI than command line.

---

### Post by Timmer1240 on 2011-03-15
I like it the way it is with root account hidden sudo is fine for doing tasks that require administrative privileges and just run in a normal account all the time.It seems to be a much more safe and secure way to have it setup.One thing I do know Linux is way more secure than Windows if run in this way.

---

### Post by nec207 on 2011-03-16
> **Timmer1240 said:**
> I like it the way it is with root account hidden sudo is fine for doing tasks that require administrative privileges and just run in a normal account all the time.It seems to be a much more safe and secure way to have it setup.One thing I do know Linux is way more secure than Windows if run in this way.
 
Windows do not hide the admin account you have log out of your account  into the admin account .
 
Windows do not use things like sudo or gksu .What windows use is  account with privileges of alot to little to no privileges.

---

### Post by doas777 on 2011-03-16
> **nec207 said:**
> Windows do not hide the admin account you have log out of your account  into the admin account .
 
Windows do not use things like sudo or gksu .What windows use is  account with privileges of alot to little to no privileges.
thats not true. the account "Administrator" is disabled by default in vista and later, and there is very little conceptual differance between gksu and Rightclick -> run as Admin.

btw, sudo/gksu/uac are not authentication (or at least not primarilly). they are not a "runas" solution so much as an authorization mechanism. 

tell me, is most of your windows experience with XP?

---

### Post by nec207 on 2011-03-16
>  
thats not true. the account "Administrator" is disabled by default in vista and later, and there is very little conceptual differance between gksu and Rightclick -> run as Admin.
 

 
All windows computers for public run as admin that means you can install,remove ,modify or delete or do just abount any thing .
 
I have windows 7 and vista computer and if I wanted I can acess windows folder or my programs folder under C:\ or even mess with the registry and do alot of damage if I wanted .
 
But why would I want to do that? If I could do that so could malware !! 
 
> btw, sudo/gksu/uac are not authentication (or at least not primarilly). they are not a "runas" solution so much as an authorization mechanism. 
 
tell me, is most of your windows experience with XP? 
 
The UAC is a security feature and has nothing to do with root acess it just security feature for critical stuff to say do you want to do this or if some malware or program tried to do it well it will pop up.
 
And all sudo and gksu do is say yap you are a user confirm you authorization .But some one can still slip some malware in that will elevate with your privileges of runing sudo and gksu .And if you only have one account and it gets malware you are out of luck.
 
Never have one account on your computer and absolutely never go on the internet with your primary account.Alaway have one account with very little privileges when surfing the internet that way if it does get malware you can delete the account if it is too bad to remove with a anti-virus program.
 
 
If you are using computer for school,office or library most likely the IT guy will set up account with very little to no privileges .

---

### Post by rookcifer on 2011-03-17
> **nec207 said:**
>  
And all sudo and gksu do is say yap you are a user confirm you authorization .But some one can still slip some malware in that will elevate with your privileges of runing sudo and gksu .And if you only have one account and it gets malware you are out of luck.

We've had lots of threads about the feasibility of user account malware elevating to root.  The bottom line is it is highly unlikely to occur without you intentionally downloading malware, making it executable, and running it yourself.  Moreover, if you want to fortify Ubuntu against this attack, you can set the sudo timeout to 0.  That will stop any such malware from appending itself to .bashrc and doing nasty things.
 
> Never have one account on your computer and absolutely never go on the internet with your primary account.Alaway have one account with very little privileges when surfing the internet that way if it does get malware you can delete the account if it is too bad to remove with a anti-virus program.

That's too paranoid.  A standard user account is perfectly safe assuming one doesn't run unknown scripts.

---

### Post by bodhi.zazen on 2011-03-17
> **nec207 said:**
> Never have one account on your computer and absolutely never go on the internet with your primary account.Alaway have one account with very little privileges when surfing the internet that way if it does get malware you can delete the account if it is too bad to remove with a anti-virus program.

Welcome to Linux / Ubuntu. Your "windows mentalilty" may have served you will on Windows, but it will not help you here.

Your suggestions of "Zonealarm", a windows only application, and antivirus will do nothing on Linux / Ubuntu to increase security.

Zonealarm will not run and there are no known active viruses for Linux (your system was patched to the know viruses long ago).

For what you are wanting I highly suggest you learn Apparmor.

If you do not want to put the time and effort into apparmor, switch to Fedora 14, selinux is enabled out of the box. Selinux has a number of graphical tools (lacking in apparmor) to assist you in managing any problems you might have, but honestly selinux is quite mature and works well.

In addition, if you are so inclined, you can lock down user accounts with selinux and you might also want to simply use xguest, an account confined by selinux.

This is a very old guide (fedora 10)

[http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

But you get the idea, it is simple to enforce and, unlike zonealarm or antivirus, actually offers some semblance of security.

---

### Post by doas777 on 2011-03-17
> **nec207 said:**
> All windows computers for public run as admin that means you can install,remove ,modify or delete or do just abount any thing .
 
 <snip/>
 
The UAC is a security feature and has nothing to do with root acess it just security feature for critical stuff to say do you want to do this or if some malware or program tried to do it well it will pop up.
 
And all sudo and gksu do is say yap you are a user confirm you authorization .But some one can still slip some malware in that will elevate with your privileges of runing sudo and gksu .And if you only have one account and it gets malware you are out of luck.
 

thats not what I said. the USER named 'Administrator' is locked by default, just like the USER named 'root' is locked. that is not to say that another user cannot have admin powers in windows or the ability to run commands as root in linux.

also "it just security feature for critical stuff to say do you want to do  this or if some malware or program tried to do it well it will pop up" 
and
"And all sudo and gksu do is say yap you are a user confirm you authorization"
are saying the same thing, albeit not very well expressed. its all just authorization.

yes, there are exploits to get root on linux just as there are in windows UAC/Process isolation model. what is your point?

---

### Post by nec207 on 2011-03-17
> thats not what I said. the USER named 'Administrator' is locked by default, just like the USER named 'root' is locked. that is not to say that another user cannot have admin powers in windows or the ability to run commands as root in linux.
 
We need to clarify the word admin and root user? because the user that can install ,remove or modify any program ,file or software is admin a guest account or limited account cannot do this.
 
A guest account or limited account cannot download things of the internet or install programs like offic or MS works /word so on.
 
If you mean acess to system kernel that is other thing.A user that can use registry is admin a guest account or limited account cannot or make system changes in control panel.
 
I'm just saying I have lots power to mess this computer so could malware.
 
I know Linux has more control how to make the OS work or look has windows is like the _saying leave it or like it mentality_ may be this what you mean by admn.
 
Windows allow some changes but you still stuck with how Microsoft thinks it should look and feel and work.I know Linux allows much more control to change way OS works or looks.
 
 
 
> Welcome to Linux / Ubuntu. Your "windows mentalilty" may have served you will on Windows, but it will not help you here.

 
Well if 95% people use Linux there will be more malware and if you using the account that has control to install ,remove or modify any program ,file or software or even download things of the internet you will get malware.
 
 
> Your suggestions of "Zonealarm", a windows only application, and antivirus will do nothing on Linux / Ubuntu to increase security.
 
> That's too paranoid. A standard user account is perfectly safe assuming one doesn't run unknown scripts 
 
 
May be so do to most of the malware is for windows.But if 95% of people use Linux there will be more malware and if you are not using a guest account or limited account the malware will get on you computer and even if you are using guest account that cannot _install ,remove or modify any program ,file or software or even download things_ if there is a exploit in OS the malware will get on your computer and you can say goodbye to your account .
 
 
I had old windows XP where user account got malware but the other account did not.Give it time there will be more malware for Linux .

---

### Post by cariboo on 2011-03-17
Most of us here are well aware of how windows works, there is no need to explain it to us. This is wandering way off topic.

---

### Post by nec207 on 2011-03-17
Okay thats clarify to get this thread back on topic and no misunderstanding.I don't have Linux and I will like to learn about Linux but the concept of "root" "admin" and "users" with different levels of system access seem to be different in Linux than say windows and this why I think this thread is going the way it is.
 
I'm comparing windows to Linux concept of "root" "admin" and "users" with different levels of system access and that is why I think this thread is going the way it is.I'm saying this is why it done in windows and why it works this way in windows when I don't know why it is done that way in Linux or why it works that way in Linux .
 
The concept of sudo and gksu is hard for me to understand.

---

### Post by cchhrriiss121212 on 2011-03-17
Linux is not about to gain a 95% share of the desktop market, currently it only has ~1%. If you really want to understand Linux security, just stop comparing it to Windows, Linux is not Windows, and trying to align them together is only confusing you.
> The concept of sudo and gksu is hard for me to understand.
Try out a Live CD of Ubuntu or any other distro and you will see how sudo works, as mentioned earlier, it is really not that complex to understand.

If you want you can set up a Linux system with a decreased permission user account, or run everything as root, it is your choice.

---

### Post by cariboo on 2011-03-17
+1 to cchhrriiss121212, If you'd like to learn about Linux, you can use one of the many Live CD's, or install [virtualbox ]("http://www.virtualbox.org/wiki/Downloads")on your windows system, and install and play with the many different Linux distributions, without doing any harm to your running system.

it's a lot easier to learn a concept when you have the operating system sitting in front of you.

---

### Post by FlameReaper on 2011-04-19
In Windows, the actual "Administrator" account is *not* visible by default (thus by logic you *can't* log in into one), and it doesn't work on the same principle as how your user account settings in Windows stated as "Administrator." It's just that you as the user are given enough privileges to do things that normally require Administrator's level of access such as removing and installing software. This is why we have the "Run as administrator" option when we right-click on applications we have to run, so that we won't be bothered by such petty things as requiring permissions to do anything, and have the program exit when they can't have the permissions.

Same thing as Linux users. When you give a user "administration rights" that doesn't mean they become the "root" user. It's just that you grant them the ability to "run as root" - as in performing a command with "sudo" or "gksu" (whichever suits your level of knowledge, it's the same anyway; with the difference that one is for the command line while the other is just a GUI front-end) - and that means thing such as installing and removing software as well.

What I know of is that trying to enable the "Administrator" account in Windows is a lot harder than in a Linux distribution. Been there done that, and I'd say I'm rather... annoyed by my experience that I've gone through.

---

### Post by rookcifer on 2011-04-19
> **nec207 said:**
> People say and some web sites I gone to say by default root account is locked in Linux ,Unix and Mac computers not like windows.

They're wrong.  Most Linux distros do not lock the root account.  Ubuntu is the only major distro that does this.  None of the BSD's do it, nor does Solaris or most other Unices.  Not sure about OSX.
 
> And need a root password to do stuff. ( not saying what stuff you need a root password ) But what is strange is in windows we just log out the user profile into the admin profile to do stuff.

You don't need to log out of Windows to do admin stuff (at least not with Vista/7).  You can right click and click "run as administrator."  On XP, you had to log-out, but there are ways around it with third-party software.  I think logging out is highly inconvenient so I am not sure why anyone would prefer it.

 
> Explain better .Why do they do this by default ?Why not give the people the option to choose ?

It's a debate that has raged ever since Ubuntu decided to do it.  But it's a rather irrelevant debate, imo.  For one, Ubuntu comes with sudo which allows the user to do anything root can do already.  And if you want to go back to the standard root/user way of doing things you can merely unlock the root account.
 
> 
I thought default root account is locked ?Can you set it up so you can login has a root user. Or by default that is blocked.
 
Yes, you can unlock the root account if you so desire.  Google "root sudo Ubuntu" and you'll find the Wiki page.

> It is so hard for windows user do to by default the account we are admim.And we do not have this stuff like Linux ,Unix and Mac computers hat need a password for stuff or have to run sudo command to do stuff.

You need a password because there has to be some way of verifying that the user really is the root user.  Otherwise, you may as well not even have privilege separation.  I realize it might be difficult for Windows converts to understand privilege separation since Microsoft ignored such practices for so long.  But, it is necessary in order to achieve a modicum of security.

EDIT: Forgot I had already responded to this thread.  lolz

Anyway, the OP has never even used Linux so that explains his confusion.  OP, on Ubuntu, when you run sudo you do NOT magically become root.  Only the *command* you are running has root privileges.  The user account is still "confined."  For instance on my Ubuntu box I am running right now as a "limited user" which is the default behavior.  However, if I want to do something that requires admin privileges, then I merely type "sudo <command>".  If something within the GUI requires root, it will prompt you with a password box.  It works the same way, however.  The difference in Ubuntu and most other Linux distros is there is no "root" **user.**  But this does not mean you cannot acquire root level privileges!  You will have to read up on sudo to understand.

---

### Post by mynameisnotbob on 2011-04-19
sudo allows commands to be run in the terminal or graphically, depending on the command. Besides, the root account may be locked but you can still access it using either the 'sudo -i' command or the Root Terminal in system tools, at which point you essentially are 'root@yourcomputername'. You have to enter passwords to use both of those, by the way.

What I'm saying is, root being locked really just means you can't login to root using GDM (the graphical desktop). After all, the 'sudo -i' works just like 'su root' except you're entering your password not the root account's

But really, I'm just saying things that are already said. In this thread, and in the [URL="https://help.ubuntu.com/community/RootSudo"]RootSudo documentation.
[/URL]

---

