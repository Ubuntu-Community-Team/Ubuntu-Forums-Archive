---
title: "Change username ?"
date: 2015-11-22
forum: Server Platforms
---

### Post by soamz on 2015-11-22
Is there a way I can change the username of the system ?
I mistakenly juggled the usernames. 

Also, another big problem I find. 
While installing it asks for root password .
After installation, if I enter the same, it says wrong. 

Why ?

---

### Post by darkod on 2015-11-23
Ubuntu by default has the root user disabled. The installer is not asking for a root password, it is asking for the "first user" password. That first user has the right to run system commands by putting 'sudo' in front of the command. Upon trying to execute it, it as asking you again to confirm that user password (enter it again).

So if you are trying to login as 'root' with the password you entered during installation, it will give you an error. By default, you can't login as 'root'.

As for changing the username, try this:
```
sudo usermod --login <newuser> <olduser>
```

That should change the olduser username to newuser. Note that the home folder will probably stay the same, so if you want it to match you might need to do manual modifications.

Another option is to add a new user called newuser, give him sudo rights, move any files from one home folder to the other if you wish to do that, and then delete the old user.

---

### Post by soamz on 2015-11-23
So how do I login as root, if I want to ?

---

### Post by darkod on 2015-11-23
You can not, not by default. The root is disabled for security and for protection from hacking into with the root user.

Any command you need to run as root, you can run with your user and sudo in front. For example, to create a new user instead of 'adduser <newuser>' you will do 'sudo adduser <newuser>'. Then it asks you again for your own password, as a protection from running a dangerous command by mistake. After you confirm your password, it will execute the command.

If you need to run root commands for a longer period, you can temporarily "act as root" by executing:
```
sudo -i
```

That will make you root. But try not to use it all the time, only when you really need to work long time as root, to avoid typing sudo in front of each command. Otherwise use sudo, that's the best way.

---

### Post by soamz on 2015-11-23
So basically I will never need root logins ?

---

### Post by darkod on 2015-11-23
Correct. You don't need root basically, almost never. In the situation when you do, log in by ssh with your user and do the 'sudo -i'. But you never need to login as root by ssh.

---

### Post by soamz on 2015-11-23
> **darkod said:**
> Correct. You don't need root basically, almost never. In the situation when you do, log in by ssh with your user and do the 'sudo -i'. But you never need to login as root by ssh.


Awesome!
And whats the command to change the password for the username ? 

After changing the username, I need to reset the password to something better.

---

### Post by darkod on 2015-11-23
If you are logged in as that user, only:
```
passwd
```

To change it for another user:
```
sudo passwd <user>
```

---

### Post by soamz on 2015-11-23
Awesome, thanks!
I will try now.

On issue. 
While installing Debian yesterday, it asked me for username and password.
I had entered and noted it down. 

Now after everything is done, when Im trying to login to it from my Mac terminal ssh agatha@145.45.11.111 , it asks for password, but when I enter the exact same password it says wrong. 
Whats wrong ?

Is there a way to reset that password ?
Or I have to again install everything again ???

---

### Post by darkod on 2015-11-23
Hold on, Debian or Ubuntu? Debian is not disabling the root user, so the installer probably asked you for the root password. In that case you need to try 'root' and the password you selected.

Ubuntu is debian based but is not identical. The ubuntu team disables the root user. What I discussed earlier applies to ubuntu, not debian (although the commands to change a username or a password are the same).

Yes, there should be a way to reset the user from a rescue mode but I haven't done that so far. You need to search on the internet for the procedure. And make sure to search for debian or ubuntu, depending what you installed.

The last option is a reinstall, but it shouldn't come to that unless you prefer it.

---

### Post by soamz on 2015-11-23
Okay I have 3 new servers, I installed Ubuntu server to 1, debian to 1, FreeBSD to 1. 

Debian and Ubuntu server working fine for user login.
FreeBSD, is not letting me in.

---

### Post by TheFu on 2015-11-25
Seems that a basic, cross-platform, Unix admin, book is what you need.  O'Reily's *System Administration* 3rd Ed. is probably what is needed. BSD is very similar, but not identical.

---

### Post by soamz on 2015-11-29
jetplex@jetplex:~$ sudo usermod --login jetspeed jetplex
[sudo] password for jetplex:
usermod: user jetplex is currently used by process 1301


I guess it did not work.

---

### Post by furtom on 2015-11-29
Just to add to the very good answers here: When I first came to Ubuntu from Debian, I too felt unease about not having a root account. You can, and I did, enable the root account in Ubuntu. It's very easy to do.

However, the inertia of the Ubuntu way of doing things has caught up to me. I do use **sudo -i** or **sudo su** when I have to, but I have allowed the root account to remain disabled. 

There can sometimes be [problems with using sudo to run graphical programs]("http://www.psychocats.net/ubuntu/graphicalsudo"), but less so than in the past. Nevertheless, if you are going to run a GUI program with elevated [COLOR=#222222][FONT=Verdana]privileges [/FONT][/COLOR]from the command line, it's best to use [gksudo]("http://linux.die.net/man/1/gksudo") (or [pkexec]("http://manpages.ubuntu.com/manpages/lucid/man1/pkexec.1.html")). 

I still think good security practices with a root account is better than using sudo all the time, but I've given up the fight...

Disabling root strikes me as an u[COLOR=#222222][FONT=Verdana]necessary p[/FONT][/COLOR]recaution in the design strategy of Ubuntu. Unfortunately, nobody asked me... :p

If you did install Debian and not Ubuntu, however, none of the above applies. But then you'd be in the wrong forum, or at least wrong area of it. You wouldn't do that, would you? :)

---

### Post by soamz on 2015-11-29
You can do sudo -i in terminal or SSH, but how will you change the user to root while using SFTP ?

---

