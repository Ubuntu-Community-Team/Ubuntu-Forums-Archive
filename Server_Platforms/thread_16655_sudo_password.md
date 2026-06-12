---
title: "sudo password"
date: 2005-02-23
forum: Server Platforms
---

### Post by dstrebel on 2005-02-23
I set my root password and when I try to sudo my password wont work but if I try to su  root it works. Any help would be greatly appreciated.

---

### Post by wulf on 2005-02-23
Which password are you trying when you "sudo"? Yours or root's? If you're trying to use the root password, use yours instead - that confused me when I first started using Ubuntu until I re-read the dialog box that said "You must enter **your** password to continue"! :D

Wulf

---

### Post by dataw0lf on 2005-02-24
sudo is the password of said user with sudoer privileges.  And su is actually 'switching user' to root.
dataw0lf

---

### Post by bored2k on 2005-02-24
anyways, if ur like me when 1st installed ubuntu warty back in beta phase and R annoying with sudo

$sudo su; passwd su 

might do the job  :wink: 

again, after i went back to ubuntu [shame on me for leaving] i havnt got the need to chang su passwd

---

### Post by sundarece on 2005-02-28
> **bored2k]anyways, if ur like me when 1st installed ubuntu warty back in beta phase and R annoying with sudo

$sudo su said:**
>  i havnt got the need to chang su passwd
 So, why is ubuntu allowing a normal user to use the commands that are restricted to the root??  
2. How can I log in as the root?

---

### Post by LongTooth on 2005-03-01
I think I'll jump into this. I too had a problem with 'sudo' at first. But since using Ubuntu from the first release I just don't see a problem. I can do everything and I mean everything using the 'sudo' command. I just don't see a problem. Is using 'sudo' such a big hassle one just can't stand it? I don't understand. What is the problem? I rather like it; not having to remember a root password. I've installed all kinds of packages from the repositories. I've upgraded to Hoary. I've installed debian packages (Opera and others). I can do what ever I need to do. So just what the HELL is the problem. (Sorry, I got carried away). But can someone tell me what they can't do using 'sudo' and why it's so important that they use root? If one absolutely needs to do things as root, just activate it. Thats all one has to. Lets not forget that only the first user has 'sudo' privileges. Not the other users. But if your like me, I'm the only user on my PC.

---

### Post by wulf on 2005-03-01
I was also sceptical about what I'd read about Ubuntu's approach to root access but found I got used to it very quickly. On my previous distro, Mandrake, I'd actually set up sudo permission for commands that I commonly needed in order that I didn't get lazy and end up with a root level terminal open all the time. Therefore, I find Ubuntu's model actually fits me much better than I'd expected!

Wulf

---

### Post by can8dnSix on 2005-03-01
[QUOTE=LongTooth]I think I'll jump into this. I too had a problem with 'sudo' at first. But since using Ubuntu from the first release I just don't see a problem. I can do everything and I mean everything using the 'sudo' command. I just don't see a problem. Is using 'sudo' such a big hassle one just can't stand it? I don't understand. What is the problem? I rather like it; not having to remember a root password. I've installed all kinds of packages from the repositories. I've upgraded to Hoary. I've installed debian packages (Opera and others). I can do what ever I need to do. So just what the HELL is the problem. (Sorry, I got carried away). But can someone tell me what they can't do using 'sudo' and why it's so important that they use root? If one absolutely needs to do things as root, just activate it. Thats all one has to. Lets not forget that only the first user has 'sudo' privileges. Not the other users. But if your like me, I'm the only user on my PC.[/QUOTE]

Isn't sudo also a "security" feature that helps eliminate the user from having run in root mode? I love having to use sudo and in essence always keeping my machine out of root mode. 

can8dnSix

---

### Post by msgyrd on 2005-03-06
[QUOTE=LongTooth]I think I'll jump into this. I too had a problem with 'sudo' at first. But since using Ubuntu from the first release I just don't see a problem. I can do everything and I mean everything using the 'sudo' command. I just don't see a problem. Is using 'sudo' such a big hassle one just can't stand it? I don't understand. What is the problem? I rather like it; not having to remember a root password. I've installed all kinds of packages from the repositories. I've upgraded to Hoary. I've installed debian packages (Opera and others). I can do what ever I need to do. So just what the HELL is the problem. (Sorry, I got carried away). But can someone tell me what they can't do using 'sudo' and why it's so important that they use root? If one absolutely needs to do things as root, just activate it. Thats all one has to. Lets not forget that only the first user has 'sudo' privileges. Not the other users. But if your like me, I'm the only user on my PC.[/QUOTE]
 
To answer your question of what sudo can't do that root (su) can:
Tab completion of root level commands.

I'm new to Ubuntu (but a long time gentoo user), and I know that sudo wouldn't tab complete commands, just directories.  Maybe I'm wrong.

---

### Post by giumo on 2005-03-14
Hi, I want to change the SUDO ubuntu settings, can you Help me?
I want to set my system in this way:
I log in as user "pippo" in the Gnome Desktop.
If I try to make some operation like, for example open Synaptic, the system ask me the ROOT password.
Is it possible?
Thanks and sorry about my english.
Marco

---

### Post by ssam on 2005-03-14
you can get tab completion with sudo.

put this at the end of your ~/.bashrc

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

---

### Post by stefansava on 2005-03-23
Hi,

I tried to mount my fat32 partitions and I went to 

/etc/fstab

and I tried to edit the text , but I cant do it because I think I need root access.

I cant edit anything from 

" / " 

Please, any help!

---

### Post by gmike on 2005-03-24
the same story here, maybe i am a fool but this is not getting any easier.
i cannot edit /etc/apt or /etc/fstab because i do not have proper permission. i understood that sudo -L gives one access to everything as far as command goes, how do you gain root access if you are not in command line?

---

### Post by wulf on 2005-03-24
Run the program with *gksudo*. Personally, I normally work from the command line so, to edit /etc/fstab, I'd type *sudo gvim /etc/fstab* but you could also set up an icon to run your chosen editor in "superuser" mode, pointing to *gksudo /usr/bin/gvim* (or whatever editor you wanted to use).

Of course, if you leave a superpowered text editor sitting on your desktop, it's going to start leaping tall buildings, tossing cars around and causing untold damage to your installation unless you're very careful. Why not just keep a simple terminal up so you have to invoke the superpowers on purpose?

Wulf

---

### Post by TjaBBe on 2005-03-24
I too was at first a bit sceptical about the sudo'ing in Ubuntu. But I too like it for reasons said above. And for the reason that no other user can become root, and noone can login as root directly.

---

### Post by oracledarren on 2005-03-24
If you are ademant that you want to use root to do you set up activity and this is NOT recommended at all you can enable the root login if you want.

First off root must have a password so you will have to go into a terminal and set one up

i.e. sudo password root

first it will ask for you password and then one for root which it will then ask you to confirm.

With that done goto SYSTEM->ADMIN->LOGIN SCREEN SETUP

it will ask you for roots password at this point so enter it

then click on the security tab and check the box which says allow root logins

Once all that is done you can log out and log back in as root.

Please remember though that the whole reason for sudo is security and anyone could potentially cause damage to your system whilst you are logged in as root.

Do what you must and then log out pronto  ;)

---

### Post by 23meg on 2005-03-30
[QUOTE=wulf]Run the program with *gksudo*. Personally, I normally work from the command line so, to edit /etc/fstab, I'd type *sudo gvim /etc/fstab* but you could also set up an icon to run your chosen editor in "superuser" mode, pointing to *gksudo /usr/bin/gvim* (or whatever editor you wanted to use).
[/QUOTE]

i was looking for this kind of a solution too; and this works fine. but how can i set things up so that i have a gksudo icon on my desktop and whatever app i drag and drop on it runs in superuser mode? when i create a gksudo launcher and drag and drop an app on it i get a "changing user" dialog that requests my password but it will accept neither my user password nor the root one!

m.

---

### Post by 23meg on 2005-04-01
got it! (at the gnomesupport forum :) ) 

create a launcher with the command

```
gksudo "gnome-open %u"
```

and whatever you drag and drop on the launcher will be opened as root with its associated application. i find this so handy that i think it deserves a how-to. if anyone else finds it worthy please put one up or give me a sign.

---

### Post by Xgates on 2005-04-11
[QUOTE=oracledarren]If you are ademant that you want to use root to do you set up activity and this is NOT recommended at all you can enable the root login if you want.

First off root must have a password so you will have to go into a terminal and set one up

i.e. sudo password root

first it will ask for you password and then one for root which it will then ask you to confirm.

With that done goto SYSTEM->ADMIN->LOGIN SCREEN SETUP

it will ask you for roots password at this point so enter it

then click on the security tab and check the box which says allow root logins

Once all that is done you can log out and log back in as root.

Please remember though that the whole reason for sudo is security and anyone could potentially cause damage to your system whilst you are logged in as root.

Do what you must and then log out pronto  ;)[/QUOTE]


oracledarren what are you talking about:
Please remember though that the whole reason for sudo is security

Sudo is not as secure as having a root password account, with sudo all someone needs is the user account. With a root account, then someone has to get past the user account then they need to take root, it's an extra step they need to take, with ONE more password in place in order to gain root on the box over just sudo.

Damage the box logged in as root, LOL please --> RULE #1 in Linux NEVER login as root, and people are taught this, so to say that is not the way in which Linux is taught.

Log in is always user then --> 'su' for root the same as sudo. sudo is not more secure, it's ONE less password a cracker needs to get to gain root access, plain and simple.

And if the Ubuntu thinking is we did this so people wouldn't log in by mistake as root, then this is just plain bad thinking on part of Ubuntu. This is not a Windows OS, we are running a Unix based OS that takes more to do and learn, so PLEASE lets stick to good soild REAL facts of how things are done the Unix way, not some wannabe Linux users thinking here!

The problem with Linux now is all the Windows users trying to run it, and use it like Windows creating this type of thought here.

THANK YOU

---

