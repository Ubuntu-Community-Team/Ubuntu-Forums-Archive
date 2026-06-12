---
title: "Can't see the point (a safety issue)"
date: 2012-01-27
forum: The Cafe
---

### Post by Lalaith on 2012-01-27
Hi all from newbieland,  
 

 As it is recommended on some webpages, I created a new user account which has no admin rights, in order to prevent messing up my Oeniric Ubuntu.
 

 Now there are some actions that I'm not allowed to do even if – as far as I know – cannot hurt the system, for example: sudo shutdown now, sudo modprobe psmouse, …  
 I'm sure there is a way to break this not-allowance, but does it have any sense to do it, since I created the account for that? And more, why some sudo actions aren't allowed and some are?


I can't understand the philosophy behind it :confused:

---

### Post by ajgreeny on 2012-01-27
I am not sure I see the point personally of always using a non admin user account, and I have never seen a recommendation to do what you have done.  Perhaps I have never looked in the right (wrong) places.  In view of the difficulties you are experiencing, that view seems to be strengthened.

Even with a user who has admin rights, nothing that needs admin rights can be done without the use of your password, so as long as you do not just give your password for something that you don't understand, you should be just as safe, whichever user you are running as.

---

### Post by Lalaith on 2012-01-27
maybe I misunderstood what "root" means:

here [http://linuxcommand.org/lts0010.php](http://linuxcommand.org/lts0010.php) it says:
 	**[COLOR=Red]You're not logged in as root, 	are you?[/COLOR]**

  	Don't operate the computer as 	the superuser. You should only become the superuser 	when absolutely necessary. Doing otherwise is 	dangerous, stupid, and in poor taste. Create a user 	account for yourself now!

---

### Post by haqking on 2012-01-27
> **Lalaith said:**
> maybe I misunderstood what "root" means:

here [http://linuxcommand.org/lts0010.php](http://linuxcommand.org/lts0010.php) it says:
 	**[COLOR=Red]You're not logged in as root, 	are you?[/COLOR]**

  	[COLOR=Red]Don't operate the computer as 	the superuser. You should only become the superuser 	when absolutely necessary. Doing otherwise is 	dangerous, stupid, and in poor taste. Create a user 	account for yourself now![/COLOR]

Root is the root user, it is an account which owns/admins the system in the context of users (in the context of filesystems it is the top of the filesystem heirarchy, or bottom depending on how you look at it)

Sudo is not root, it allows you as a regular user to perform sudo (super user do) actions if in the sudo group.

Sudo is not root, it just allows you to perform root/admin actions for a given moment or time.

Use your regular account which is probably in the sudo group if you setup the system and only authorise admin actions to take place if you know you want them to.

read [rootsudo]("https://help.ubuntu.com/community/RootSudo")

Cheers

---

### Post by Lalaith on 2012-01-27
When you run Ubuntu for the very first time you've got only one user account, wich has admin privileges. Is that the Root user known as well as SuperUser? 
This is what it confuses me, I think.

Also, I guess that from my standard user account I can't do sudos because I'm not on the sudoers file, and I guess that it's "safe" to add me there?

---

### Post by haqking on 2012-01-27
> **Lalaith said:**
> When you run Ubuntu for the very first time you've got only one user account, wich has admin privileges. Is that the Root user known as well as SuperUser? 
This is what it confuses me, I think.

Also, I guess that from my standard user account I can't do sudos because I'm not on the sudoers file, and I guess that it's "safe" to add me there?

When you run Ubuntu for the first time, there is the root account which has no password set so therefore locked by default in Ubuntu.

And as the user/installer of the system you will be asked to create a user account, this user account will go into the sudo group so to perform admin actions that user can provide there own password which authenticates the action if the user is in the sudo group which they should be.

and as i said in my post above no it is not the root user.

Sudo is not root and root is not sudo.

sudo means superuser do or do as the superuser (root) would/can do.

root is there but locked by default, any sudo action is allowed if the user is a sudo user and in the sudo group but this does not mean it is root.

sudo is not root, but can perform root actions.

if you installed/set up the system then you should be a sudo user or in the sudo group and so when asked for a sudo/admin action then supply your own password to authenticate

If you want to check you are in the sudo group then from terminal

```
groups
```

cheers

---

### Post by grahammechanical on 2012-01-27
I think that the mistake you are making is to look at the way Ubuntu does things from the point of view of other Linux distributions and not see things the way Ubuntu see things.

This link explains why Ubuntu uses sudo and not root.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Remember, Ubuntu is Linux for Humans. It is developed specifically so that ordinary people can just use Ubuntu without needing to know all that Linux technical stuff and still be secure.

If you are the only user with Ubuntu then you only need one user account. You will be listed as Administrator but you will be working as a standard user until you try to do something that requires administrator privileges. Then you will be asked to authenticate the task. And when the task is finished you will revert to being a standard user again. That is how Ubuntu does things.

With other distributions you have to log out of being the standard user into being root user and you remain as root/administrator until you log out again. This means that if you leave your machine someone else could sit down and use it with administrator privileges. What is more, in the unlikely event that some malicious code has infected the machine it will be able to run with root privileges. This is why the users of those distributions recommend the setting up of a standard user account and using that for normal work.

That link explains it all. Note this comment on the page:

> **Special notes on sudo and shells**

None of the methods below are suggested or supported by the designers of Ubuntu.

Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as Root.

You have been warned.

Regards.

---

### Post by forrestcupp on 2012-01-27
If we all were root users all of the time, then it would be very easy for people to make malicious scripts that could do anything they want to trash our systems. It's not only about protecting you from mistakes.

---

### Post by jwbrase on 2012-01-27
> **Lalaith said:**
> When you run Ubuntu for the very first time you've got only one user account, wich has admin privileges. Is that the Root user known as well as SuperUser? 

No, it's not.

There is only one account visible on the login screen, but that's not the only account on your system. There are several other accounts that aren't meant to be directly user accessible (and thus don't have passwords or entries on the login screen), including root (which is directly accessible on some Linux systems, but not on Ubuntu).

Administrator accounts are accounts that are directly user accessible and can use sudo, which allows you to run a command as root without being logged in as root yourself. (This makes it less likely that you'll leave your computer unattended with a terminal running a root login session open).

---

### Post by Lalaith on 2012-01-29
Many thanks to all. 

I was confused because I didn't know that, as jwbrase said, "There is only one account visible on the login screen, but that's not the only account on your system"

Thanks to all to help us learn :D

---

