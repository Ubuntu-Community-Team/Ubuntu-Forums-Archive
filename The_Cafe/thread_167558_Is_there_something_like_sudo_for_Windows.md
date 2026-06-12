---
title: "Is there something like sudo for Windows?"
date: 2006-04-28
forum: The Cafe
---

### Post by aysiu on 2006-04-28
I have to use Windows XP at work.

Basically, most of the time, the technology department sets people up as regular users. If you beg them to, and they trust you enough, they'll set you up as an administrator for the computer.

I happen to like being administrator, as the technology department is understaffed, and if I had to contact them every time I needed to do a Windows update or do something else that needs administrative privileges, it just wouldn't happen.

However, I don't like running as administrator all the time. It makes me feel really unsafe. Is there an easy way to set up something like *sudo* in Windows XP? I'd like to basically be a user, but when I need to do something administrative be prompted for a password.

---

### Post by mostwanted on 2006-04-28
I think Windows Vista comes with something like that (taken from Mac I guess). Win XP, no don't think so.

---

### Post by helpme on 2006-04-28
[QUOTE=aysiu]I have to use Windows XP at work.

Basically, most of the time, the technology department sets people up as regular users. If you beg them to, and they trust you enough, they'll set you up as an administrator for the computer.

I happen to like being administrator, as the technology department is understaffed, and if I had to contact them every time I needed to do a Windows update or do something else that needs administrative privileges, it just wouldn't happen.

However, I don't like running as administrator all the time. It makes me feel really unsafe. Is there an easy way to set up something like *sudo* in Windows XP? I'd like to basically be a user, but when I need to do something administrative be prompted for a password.[/QUOTE]
There's runas:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/runas.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/runas.mspx?mfr=true)

As for being easy, I'm not a windows expert, but what I heard wasn't to positive, to put it mildly.

---

### Post by Kernel Sanders on 2006-04-28
[QUOTE=aysiu]I have to use Windows XP at work.

Basically, most of the time, the technology department sets people up as regular users. If you beg them to, and they trust you enough, they'll set you up as an administrator for the computer.

I happen to like being administrator, as the technology department is understaffed, and if I had to contact them every time I needed to do a Windows update or do something else that needs administrative privileges, it just wouldn't happen.

However, I don't like running as administrator all the time. It makes me feel really unsafe. Is there an easy way to set up something like *sudo* in Windows XP? I'd like to basically be a user, but when I need to do something administrative be prompted for a password.[/QUOTE]


Quite simply, no.

With Windows XP your either an Adminsitrator all the time, or a restricted user all the time.

You cant have both. [useless information]Windows Vista does what you want though [/useless information]

John :)

---

### Post by NeghVar on 2006-04-28
> You cant have both. [useless information]Windows Vista does what you want though [/useless information]

In a VERY bad way. Every review I've read has said that it presents a user with so many security alerts that it runs the risk of having users just ignoring them and blindly clicking yes to everything. That is no different than what is out there now.

---

### Post by Kernel Sanders on 2006-04-28
[QUOTE=NeghVar]In a VERY bad way. Every review I've read has said that it presents a user with so many security alerts that it runs the risk of having users just ignoring them and blindly clicking yes to everything. That is no different than what is out there now.[/QUOTE]

The latest build is better, so MS are starting to get it right.

John :)

---

### Post by aysiu on 2006-04-28
[QUOTE=helpme]There's runas:[/QUOTE] Yeah, Run-as isn't going to help me, because I'm already administrator.

---

### Post by bionnaki on 2006-04-28
I think there is something called a superuser I believe. I forget how it works or how to set it up. it's been awhile - I think you can only use it with XP Pro.

---

### Post by ice60 on 2006-04-28
i think there's a MS program which lets you run as a limited user while running as an admin, or at least as a more restricted user, there's another program i use which restricts my browser too, it's been awhile since i used windows, i can't remember their names. off hand though i can think of Safexp, hardenit, and secureit which all help harden windows, you run them once and that's it. if you don't like the changes they all have options to return to the settings you used before running them.

infact, i think secureit has something called drop.exe which helps run programs with more restrictions.

[http://www.wilderssecurity.com/showthread.php?t=77607](http://www.wilderssecurity.com/showthread.php?t=77607)

[http://www.sniff-em.com/index.shtml](http://www.sniff-em.com/index.shtml)
[http://www.theorica.net/safexp.htm](http://www.theorica.net/safexp.htm)

---

### Post by ice60 on 2006-04-28
this is the program i thought was by MS, but i think it does exactly the same thing as drop.exe which comes with secureit.
[http://nonadmin.editme.com/DropMyRights](http://nonadmin.editme.com/DropMyRights)

to use drop.exe you have to change the execution path (right-click the .exe and select properties) then include the path for drop.exe as well as leaving the path for the program you want to launch)

---

### Post by blastus on 2006-04-28
> However, I don't like running as administrator all the time. It makes me feel really unsafe. Is there an easy way to set up something like sudo in Windows XP? I'd like to basically be a user, but when I need to do something administrative be prompted for a password

Get your network admin to setup a second login for you with the same privileges on the network as your existing account. Then remove one of the users from the Administrator's group on the local machine. When you login, login with the account that is not a member of the Administrator's group on the local machine. Then, whenever you need to run a program that requires Administrator access, open up the program using the runas command supplying the username@domain and password of your other account. If you need a root shell, you can also open up a "command prompt" using the runas command.

In this way you can login to Windows with an account that doesn't have root access to the local machine, but still be able to run programs that require root access. Some programs can't be run using the runas command. One such application is Windows Explorer. Also, there is no GUI for runas so you'll be stuck with using a batch file if you want to automatically supply your other username@domain to the runas command so that it just prompts you for a password.

As for getting Windows to automatically prompt you for an Administrator password if you try to run a program that requires root privileges on the local machine, it can't be done. Windows is stupid in that regard.

---

### Post by ice60 on 2006-04-28
there's this too, you can either buy it or use the free version which i think only allows three programs to use it at any one time.
[http://www.runsafe.com/](http://www.runsafe.com/)

you can use a sandbox too which are very safe. they run at the kernel level so they can intercept programs before they are loaded into memory, you then make rules for each program saying whether they can run or not. there's afew good free ones.

---

### Post by aysiu on 2006-04-29
It may be a bit more complicated than just setting up another user, as--in order to be productive--I need to be part of the domain, so he would have to set my old user to be not part of the domain and transfer my settings over to the new user (who, incidentally, would have to have the same username as my old user)... it all seems a bit convoluted.

Maybe I'll just wait until Vista, and if I screw up my system, I screw it up. I've been spyware/virus-free for a couple of years now... keeping my fingers crossed.

**Edit**: Oh! Runsafe looks interesting. I'll look into that.

---

### Post by blastus on 2006-04-29
You don't need to transfer any settings to a new account because you can continue using your existing account. The idea is that your network admin would simply create a second account and you would use that account when you need root access to the local machine. The two accounts don't even have to be a part of the same domain. Any network admin should be able to easily create such an account.

For example, if the account you use right now is aysui@orangewhitecat and the second account that your network admin creates is aysui2@orangewhitecat, then you would:

1. Add aysui2@orangewhitecat to the Administrator's group on the local machine if your network admin doesn't do so (obviously to do that you need to be aysui@orangewhitecat)

2. Remove aysui@orangewhitecat from the Administrator's group and just make that user a member of the User's group on the local machine.

From there on you would continue logging in as aysui@orangewhitecat but use the runas command and the aysui2@orangewhitecat account to run programs that require root access. Depending on the programs you need to run, you may have to grant aysui@orangewhitecat access to some directories/files as that user would no longer have root access on the local machine.

---

### Post by aysiu on 2006-04-29
blastus, your solution could work, but our tech department really doesn't like to be bugged with such things--again, mainly because they're understaffed. I think that would be the ideal solution. Runsafe seems to be a good "I don't need to bother them" solution, though.

**Edit**: I'll propose your solution to them, though--see if they go for it.

---

### Post by aysiu on 2006-05-01
I ditched Runsafe... nagware like nobody's business (worse than Windowblinds).

The tech department got back to me, and they're in favor of blastus' suggestion. Let's just see how long it takes to get set up. (The weird thing is--I'm an administrator, theoretically, but I can't set up new accounts...)

---

### Post by aysiu on 2006-05-02
**Final update:** Got a representative from technology to help me out. Even he had trouble adding a new user (same error I encountered). He had to play around and find some sneaky backdoor to adding a user.

So now my regular account on the domain is a "power user," and I have a separate "administrator" for Windows updates and such. I tried using a "restricted user" instead of "power user," but one of my programs wouldn't run without write access to the C:\ directory.

---

### Post by mfarquhar on 2006-05-02
EDIT: added after problem fixed. read if you are bored

if you check with the tech guys they might be able to set you up with restricted admin access. ie. only able to do certain things. i believe you were able to do this with older windows os's it may still be available.

if that works you wont have to worry about killing the computer with one keystroke, although that may be hard to do with windows (i mean it's bound to be dificult to do cause not everybody has killed their install...yet...........)

---

### Post by blastus on 2006-05-02
[QUOTE=aysiu]**Final update:** Got a representative from technology to help me out. Even he had trouble adding a new user (same error I encountered). He had to play around and find some sneaky backdoor to adding a user.

So now my regular account on the domain is a "power user," and I have a separate "administrator" for Windows updates and such. I tried using a "restricted user" instead of "power user," but one of my programs wouldn't run without write access to the C:\ directory.[/QUOTE]

Hey that's great :) If it's just one or two programs that demand write access to a specific directory or file that normal users wouldn't have access to, then you can grant write permissions to that specific directory/file for your restricted user. Or you could just run those programs using runas. That way, your restricted user can truly be a restricted user (i.e. only a member of Users.) 

Also, you can create a shortcut to a batch file that runs the runas command for a given user and program executable and then add it to your Start Menu. That way, if you need to access a program that requires administrative privileges, you can open the shortcut and it will open up a DOS prompt prompting you to enter in the password for your other user. Otherwise you have to manually open a DOS prompt and type in all the arguments to the runas command including the user name and the program executable OR right-click on the program and select runas. The nice thing about creating a shortcut to a batch file as opposed to right-clicking and selecting runas, is that you don't have to select your other user everytime...so it's kind of like sudo, you just get prompted for a password.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=blastus]Hey that's great :) If it's just one or two programs that demand write access to a specific directory or file that normal users wouldn't have access to, then you can grant write permissions to that specific directory/file for your restricted user. Or you could just run those programs using runas. That way, your restricted user can truly be a restricted user (i.e. only a member of Users.) 

Also, you can create a shortcut to a batch file that runs the runas command for a given user and program executable and then add it to your Start Menu. That way, if you need to access a program that requires administrative privileges, you can open the shortcut and it will open up a DOS prompt prompting you to enter in the password for your other user. Otherwise you have to manually open a DOS prompt and type in all the arguments to the runas command including the user name and the program executable OR right-click on the program and select runas. The nice thing about creating a shortcut to a batch file as opposed to right-clicking and selecting runas, is that you don't have to select your other user everytime...so it's kind of like sudo, you just get prompted for a password.[/QUOTE]

Unfortunantly the runas command does not work if the program needs an external library that is admin-only.

Vista will fix this in a nice way, yes you will get warnings when you go out of bounds like installing programs and such without admin access but it's actually possible to install programs in a safe environment (much like a chroot environment on OpenBSD as user install) while it is not possible at all on Ubuntu.

Vista WILL carry a lot of weight when it comes to safety procedures, much more so than any Linux distro i know of except maybe FC5.

It's going to be an interesting OS, don't get me wrong, i'm all for free systems but i'm also for MS improving their OS and i won't lie about the stuff they do right. 

99% of all articles you read about how hard it is to install Linux and how crappy Vista is are filled with FUD and not-knoiwing-better.

---

### Post by blastus on 2006-05-02
> Unfortunantly the runas command does not work if the program needs an external library that is admin-only.

Other than Windows Explorer (which appears to be a special case), can you give an example of a program that requires admin access but cannot be run using the runas command with an account that is a member of Administrators? My understanding is that as long as the current user has read privileges to the executable and the user supplied to the runas command has admin privileges, it doesn't matter what program is being run.

---

### Post by TheCaptain on 2006-05-02
[QUOTE=blastus]Other than Windows Explorer (which appears to be a special case), can you give an example of a program that requires admin access but cannot be run using the runas command with an account that is a member of Administrators? My understanding is that as long as the current user has read privileges to the executable and the user supplied to the runas command has admin privileges, it doesn't matter what program is being run.[/QUOTE]

Any program requiring execute access of any shared library with admin only access, example of today being MFC71.

Try to run Nero without admin access.

Or try to get packet writing to run without admin access.

Or try to get gimp filters to run without admin access.

Or... well, you get the picture, we're in the process of installing SuSE on all our boxes so things will change shortly but for now, i spend more time granting access to users than being productive as a NOC.

---

### Post by blastus on 2006-05-04
[QUOTE=TheCaptain]Any program requiring execute access of any shared library with admin only access, example of today being MFC71.

Try to run Nero without admin access.

Or try to get packet writing to run without admin access.

Or try to get gimp filters to run without admin access.

Or... well, you get the picture, we're in the process of installing SuSE on all our boxes so things will change shortly but for now, i spend more time granting access to users than being productive as a NOC.[/QUOTE]

I'm not sure what you mean. The idea of runas is to run a program as another user. There is no difference between running a program using runas as a specific user, or actually logging into Windows as that user and running the program. The program being run with runas assumes the credentials of the targeted runas user and any applications that the program launches or spawns inherit those credentials. 

It doesn't matter what permissions the program requires or what libraries that program uses. If a program requires admin access to the local machine, you can run that program using the runas command, supplying it the user name and password of an account that has administrator access. As mentioned, this works for *all* applications except Windows Explorer.

Aysiu wants to login to Windows with an account that does not have adminstrator access to his local machine. To run programs that require administrator access, he will use the runas command supplying it with the user name and password of an account that does have administrator access to his local machine.

---

### Post by aysiu on 2006-05-08
Stupid Windows XP.

I hope they fix this for Vista.

I tried doing Windows Update with the "Run as..." command, and I can't do it. It won't let me install the updates. I had to log out of user, log in as administrator, do the updates, reboot, and then log in as user again.

We don't even have a "switch user" option, as that option's disabled if your login belongs to a domain.

Boo XP! Boo!

---

### Post by mostwanted on 2006-05-08
[QUOTE=aysiu]Stupid Windows XP.

I hope they fix this for Vista.

I tried doing Windows Update with the "Run as..." command, and I can't do it. It won't let me install the updates. I had to log out of user, log in as administrator, do the updates, reboot, and then log in as user again.

We don't even have a "switch user" option, as that option's disabled if your login belongs to a domain.

Boo XP! Boo![/QUOTE]

Last time I logged in it installed updates behind my back and suddenly, without warning, popped up a message saying "System will now restart" and it restarted, closing all my open documents (no time to save anything). Didn't even get the "restart later" option.

---

### Post by aysiu on 2006-05-08
[QUOTE=mostwanted]Last time I logged in it installed updates behind my back and suddenly, without warning, popped up a message saying "System will now restart" and it restarted, closing all my open documents (no time to save anything). Didn't even get the "restart later" option.[/QUOTE] I've had something similar happen, when I'm pressing Enter in another application, and the "Restart Now"/"Restart Later" dialogue pops up right before I press Enter. Doh!

---

