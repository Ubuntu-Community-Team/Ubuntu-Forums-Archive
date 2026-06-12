---
title: "How to change the sudo password to be different from login password"
date: 2008-01-30
forum: The Cafe
---

### Post by Lostincyberspace on 2008-01-30
I was going through [this paper]("http://www.utexas.edu/cc/unix/software/npasswd/doc/PasswordSecurity.ps") I found and I thought It would be much easier for someone to get a non root password and then use a sudo command with the password since by default it is the same as the login password. I have seen other posts along this topic but they don't offer how to change the sudo password and I want to be able to login with one password and then use sudo with a different more secure password. 

Can anyone help point me in the right direction?

---

### Post by igknighted on 2008-01-30
> **Lostincyberspace said:**
> I was going through [this paper]("http://www.utexas.edu/cc/unix/software/npasswd/doc/PasswordSecurity.ps") I found and I thought It would be much easier for someone to get a non root password and then use a sudo command with the password since by default it is the same as the login password. I have seen other posts along this topic but they don't offer how to change the sudo password and I want to be able to login with one password and then use sudo with a different more secure password. 

Can anyone help point me in the right direction?

You cannot change the sudo password from your login password.  You could create a root password and use 'su -' or 'su -c' to run commands as root, but sudo merely gives your user admin powers, and hence has to use your user's password

---

### Post by Lostincyberspace on 2008-01-30
So it is not possible to have a separate sudo password form login password I guess that will be one thing to suggest to be made available for future releases. 

Uhh were should I suggest it I have no idea of where that would be developed?

---

### Post by Lostincyberspace on 2008-01-30
> **igknighted said:**
> You could create a root password and use 'su -' or 'su -c' to run commands as root,
I know I could do that but I was thinking about making a how to for new users to make there computer more secure. And since most guides are written to use sudo I was going to make it compliant that way so they can still follow them easily.

---

### Post by az on 2008-01-30
> **Lostincyberspace said:**
> I want to be able to login with one password and then use sudo with a different more secure password. 


I think it just makes more sense to have a secure password to begin with.

Authentication (you are indeed you) is a part of security, but security is implemented by using permissions (you can do this, but you cannot do that).  

Sudo is simply a finer-grained way of determining what tasks a user can perform and when.  It's not sudo's job to be a more involved method of authentication.  And that's because when password authentication is properly used, it just works.

If a lot of users are logging on to your machine with the same account, but you want some of them to have elevated privileges but others not, then the solution is to create different accounts, and not to complicate the method of authentication in place.

---

### Post by Lostincyberspace on 2008-01-30
I want it to be an anti crack measurebecuase if you can crck the password and the person has a sudo enabled account then they can easily change the root password and then screw the whole computer.

Because if you can run
```
sudo su
```
You only need to know the regular user password and not the root password which is generally more secure. So by having a separate password for sudo then the chances of them being able to mess up the system are a lot less likely.

---

### Post by aysiu on 2008-01-30
If she can crack the normal sudo user's password, what would stop this cracker from discovering the non-sudo sudo password?

I don't buy this anti-sudo FUD at all. *sudo* is just as secure as, if not more secure than a separate root login. The strength of your security greatly depends on the strength of the passwords you employ, not how many passwords you have.

---

### Post by Andrewie on 2008-01-30
if you truely want a better password, then the only way I can think of it is to re-enable the root login, and change the sudoer file to ask for the user password

I wouldn't call it fud aysiu, but I agree with you it's not going to do a world have help to make them different. One case where it may work is a person who is watching you type in your password would not be able to gain root access if they see your user password. If someone gains access to your system through a user, it isn't going to take long to gain root. All it will do is slow the hacker down.

---

### Post by aysiu on 2008-01-30
> **Andrewie said:**
> 
One case where it may work is a person who is watching you type in your password would not be able to gain root access if they see your user password. If someone gains access to your system through a user, it isn't going to take long to gain root. All it will do is slow the hacker down. By that same token, couldn't they watch you type in your second password, too, to gain administrative privileges?

**Default Ubuntu behavior**
User logs in as user A and uses user A's password to start Synaptic Package Manager.
Watcher watches user type in password and now knows the sudo password for A and can change the root password.

**This newly proposed behavior**
User logs in as user A and uses user B's password to start Synaptic Package Manager.
Watcher watches user type in password and now knows the password for B and can change the root password.

I don't see the difference, frankly. If you're letting people see your password as you type it in, *that's* the real security risk.

---

### Post by bodhi.zazen on 2008-01-30
You can easily (well maybe not easily) by configuring sudo, see man sudo.

[color=red]WARNING: KEEP A ROOT TERMINAL OPEN UNTIL YOU ARE DONE WITH CONFIGURATION AND YOU KNOW YOUR CHANGES ARE WORKING[/color] or you may lose root access.

NOTE: I have tested this, and it works.

DO NOT CLOSE YOUR ROOT TERMINAL until the new command :

sudo sh "/bin/bash" is working (with a root password)

> rootpw

    If set, sudo will prompt for the root password instead of the password of the invoking user. This flag is off by default.

[http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options](http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options)

use visudo and add rootpw to the end of the defaults line.

The problem, of course you need to then set a root password.

Once you do that , root can log in, not good.

To fix this, change root's default shell to /bin/false -> problem fixed, well almost, ...

Now root has no shell. While you may be perfectly happy with sudo this and sudo that, I like to sudo -i ...

So, rather then sudo -i :

```
sudo sh "/bin/bash"
```

Then, in the root shell, 

```
source /root/.bashrc
```


=====

[size=4][color=navy]Another way of doing this is to create a new user, one not in the admin group. Then, in a shell, su to the admin user and then use sudo  from there.[/color][/size]

---

### Post by Lostincyberspace on 2008-01-31
Thanks bodhi for the info I will have to get back to you on whether it works out fine over here, It is getting late. I would also like to thank aysiu for keeping it up for bodhi to see, but aysiu I would be a little more on the side of saying that it is not possible and not it shouldn't be done. That is what came across to me and new users might be deterred from using the forums if they are answered as if not important.

---

### Post by Erik Trybom on 2008-01-31
I actually think this is a good idea.

If you ask for the password too often, chances are the user will become tired and set a weak password. I know I do. Hell, I don't want to type "7bWr5iI2r" every time I unlock the screen saver. Additionally, the more often you use a password the sloppier you'll get with keeping it safe. So from a psychological perspective, I think it makes perfect sense to require different passwords for root access and for ordinary login.

I agree, of course, that the *real* solution is to educate the users, but that doesn't mean we should dismiss the idea out of hand.

---

### Post by az on 2008-01-31
> **Erik Trybom said:**
>  So from a psychological perspective, I think it makes perfect sense to require different passwords for root access and for ordinary login.


So don't use the first account which has sudo privs.  Create another account and switch into the first one when you need.

The point is that you don't need to make sudo require this.  There are two completely different things.  The problem is not with sudo.

---

### Post by forrestcupp on 2008-01-31
There are good reasons for having separate passwords for sudo and login.

What if I have a kid that I want to be able to log in to my computer, but I don't want him messing with any system stuff?  I don't want to just make an automatic log in because I don't just want anyone to be able to get on my computer and go to my bank's web site that Firefox was nice enough to remember my password for.

So I might want my child to be able to log on, but not be able to do anything that requires sudo privileges.

---

### Post by aysiu on 2008-01-31
> **forrestcupp said:**
> There are good reasons for having separate passwords for sudo and login.

What if I have a kid that I want to be able to log in to my computer, but I don't want him messing with any system stuff?  I don't want to just make an automatic log in because I don't just want anyone to be able to get on my computer and go to my bank's web site that Firefox was nice enough to remember my password for.

So I might want my child to be able to log on, but not be able to do anything that requires sudo privileges.
That's when you create a separate limited user *account* for your child. Then she can have her own settings and bookmarks *and* not be able to modify systemwide settings or mess with your Firefox settings.

Even if you had a separate *sudo* password for the same account, if you let your child log in to your account, she'd still be able to go to your bank's website in Firefox.

---

### Post by forrestcupp on 2008-01-31
I've never messed with separate accounts.  Is it possible to set up an account that can't do anything that requires a sudo password, not even installing files with Synaptic?

I know they could mess with Firefox.

One thing about separate passwords, though, is it would save me from having to log out and back into another account if I want to do something real quick.

Anyway, my point is that there could be viable reasons for wanting something like that.  Just because you don't see a need, doesn't mean nobody will.

---

### Post by bufsabre666 on 2008-01-31
> **forrestcupp said:**
> I've never messed with separate accounts.  Is it possible to set up an account that can't do anything that requires a sudo password, not even installing files with Synaptic?

on limited accounts, the menus lack add/remove synaptic and terminal, i dont know if alt-f2 works i didnt test that

---

### Post by oomingmak on 2008-01-31
I have been meaning to find out if separate sudo and login passwords could be set, as it's something that I'd really like to do (although my reasons for doing it are the exact opposite of the OP's).

I don't mind having long complex login passwords, but if I then have to keep entering that password over and over again every time I so much as want to look in synaptic (even if I am not installing anything) or doing  other regularly used functions (such as changing icons in shared theme folders etc), then it's just not practical to have such a long and complex password. In fact, it's downright irritating. I know I could change the length of time that the sudo session remains valid, but that seems to defeat the purpose (as you have elevated privileges for long periods of time when you don't even need them).

I'd therefore like a *shorter *password for sudo so that I could continue to use a much stronger password for login (which only need be entered once per session), but having read this thread I'm still not clear how much of a security risk that might be. 

I would have thought that if you already have access to the login account then you could get admin / root rights straight away because the sudo password will be the same, so even having a fairly weak (but different) sudo password will be more secure the the exact same one that has already been used to gain access to the account (that is, unless the sudo password can somehow be attacked directly without having to first get past the account login).

I'm not familiar with Linux, so I'd appreciate any comments explaining how feasible the above proposal would be.

Thanks.

---

### Post by aysiu on 2008-01-31
> **forrestcupp said:**
> I've never messed with separate accounts.  Is it possible to set up an account that can't do anything that requires a sudo password, not even installing files with Synaptic? Yes. That's what a non-admin account is. It cannot use Synaptic or other programs that allow system-wide changes to be made.

> One thing about separate passwords, though, is it would save me from having to log out and back into another account if I want to do something real quick. I don't really see how that's relevant. You don't have to log out and log back in to use Synaptic if you have the same password. You just launch Synaptic. And if you were logged into your child's non-admin account, you'd still have to log into your own account to use Synaptic or use some form of *su* (switch user).

> Anyway, my point is that there could be viable reasons for wanting something like that.  Just because you don't see a need, doesn't mean nobody will. And I never said there couldn't be a possible scenario where it might make sense. I just haven't seen any yet in this thread, and my main beef was with the original post, which seemed to indicate that having the same password for *sudo* was a security concern: > **Lostincyberspace said:**
> I was going through [this paper]("http://www.utexas.edu/cc/unix/software/npasswd/doc/PasswordSecurity.ps") I found and I thought It would be much easier for someone to get a non root password and then use a sudo command with the password since by default it is the same as the login password.

---

### Post by aysiu on 2008-01-31
> **oomingmak said:**
> 
I'd therefore like a *shorter *password for sudo so that I could continue to use a much stronger password for login (which only need be entered once per session), but having read this thread I'm still not clear how much of a security risk that might be. From a security standpoint, it'd be better to have it the other way around--a stronger password for system-wide changes and a weaker password for user login. Of course, if you're really that concerned about security, you should have strong passwords for everything. You know that saying about chains and the weakest link...

---

### Post by forrestcupp on 2008-01-31
> **aysiu said:**
> 
 I don't really see how that's relevant. You don't have to log out and log back in to use Synaptic if you have the same password. You just launch Synaptic. And if you were logged into your child's non-admin account, you'd still have to log into your own account to use Synaptic or use some form of *su* (switch user).


It's relevant because if my child was on his non-admin account, I would have to log out and back on to mine if I wanted to install a game for him in Synaptic.  Then I'd have to log out of my admin account and back into his non-admin for him to play the game.  If I had separate passwords, I wouldn't have to do that.  I could just get into Synaptic using the sudo password that he doesn't know.

---

### Post by oomingmak on 2008-01-31
> **aysiu said:**
> From a security standpoint, it'd be better to have it the other way around--a stronger password for system-wide changes and a weaker password for user login. Of course, if you're really that concerned about security, you should have strong passwords for everything. You know that saying about chains and the weakest link...
I was afraid that would be the answer. 

So it's a case of either being relentlessly annoyed to death prompts for long passwords, or weaken your security. Not a good range of options really.

Maybe I should look into biometrics. I'd be fine sticking my finger on a pad every time sudo nagged me. (That'd be quick and easy).

---

### Post by bodhi.zazen on 2008-01-31
> **forrestcupp said:**
> It's relevant because if my child was on his non-admin account, I would have to log out and back on to mine if I wanted to install a game for him in Synaptic.  Then I'd have to log out of my admin account and back into his non-admin for him to play the game.  If I had separate passwords, I wouldn't have to do that.  I could just get into Synaptic using the sudo password that he doesn't know.

Actually, that is not true.

Your first option is to open a terminal and use su

When you are logged in as your child, open a terminal,

```
su your_account
```

You will put in your password. You can use sudo, or in the case of synaptic, gksu from there.

You can also start a new X session if you prefer :

Switch to a console (Ctrl-Alt-F1), log in as your admin user, then :

```
/usr/bin/startx /usr/bin/gnome-panel -- :1
```

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

---

### Post by aysiu on 2008-01-31
You can keep one password for your *sudo* account and not have to log out of your child's non-admin account to use Synaptic. What you would do is make sure the *sux* package is installed.

Then, instead of using *su*, you'd use *sux* to switch users: ```
sux parentadmin
``` at which point you'd use the parent *sudo* password to switch users. Then ```
gksudo synaptic
``` to launch Synaptic.

I'm sure with Zenity, you could probably even make a little interactive-terminal launcher icon.

---

### Post by Lostincyberspace on 2008-01-31
I personally think I would never use it I just want it available for others to use If the need arise where they need a simple password to just be able to use the computer but not have administration options. Of course having a strong to begin with is a great idea I never said it wasn't but having a good password for sudo and an average password for the login.

---

### Post by bodhi.zazen on 2008-01-31
> **aysiu said:**
> You can keep one password for your *sudo* account and not have to log out of your child's non-admin account to use Synaptic. What you would do is make sure the *sux* package is installed.

Then, instead of using *su*, you'd use *sux* to switch users

aysiu, I had never heard of sux before, thanks for that tip.

---

### Post by aysiu on 2008-01-31
> **bodhi.zazen said:**
> aysiu, I had never heard of sux before, thanks for that tip.
You're welcome.

Do you have any idea how that would work in a launchable shell script?

As far as I can tell, the shell script will use all commands for the user who launched it.

Do you know how to have the script execute the second command as the switched-to user?

---

### Post by bodhi.zazen on 2008-01-31
> **aysiu said:**
> You're welcome.

Do you have any idea how that would work in a launchable shell script?

As far as I can tell, the shell script will use all commands for the user who launched it.

Do you know how to have the script execute the second command as the switched-to user?

I think this can be done with expect, but I have not tried.

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

Otherwise, you would need to write a script and launch the script as the new user 

```
sudo <new_user> "sh /path_to/script"
```

---

### Post by aysiu on 2008-01-31
> **bodhi.zazen said:**
> I think this can be done with expect, but I have not tried.

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

Otherwise, you would need to write a script and launch the script as the new user 

```
sudo <new_user> "sh /path_to/script"
```
*expect* looks a little over my head, but the problem with *sudo*ing another script is that the *sudo* would be run as the first (non-admin) user, not the second (admin) one.

---

### Post by Xbehave on 2008-01-31
arg this thread is what annoys me about using these forums, somebody asked a valid question, instead of giving a valid answere there are 3 pages of "security" "experts" talking about the risks.
at the end of the day there are 3 reasons for his setup:
1) it gives 2 passwords to access admin
2) it means he can be sloppy with his user passwords (rember security =~ usability ^ -1)
3) ITS WHAT HE WANTS TO DO

thx go to bodhi.zazen's

---

### Post by aysiu on 2008-01-31
> **Xbehave said:**
> arg this thread is what annoys me about using these forums, somebody asked a valid question, instead of giving a valid answere there are 3 pages of "security" "experts" talking about the risks.
at the end of the day there are 3 reasons for his setup:
1) it gives 2 passwords to access admin
2) it means he can be sloppy with his user passwords (rember security =~ usability ^ -1)
3) ITS WHAT HE WANTS TO DO

thx go to bodhi.zazen's
Well clearly we have differing opinions on what's annoying.

What annoys me about the thread is people spreading FUD about *sudo* being less secure than a direct root login. You don't have to be a security expert to know that you won't gain security by adding a second password. And since the whole point of the OP asking for two separate passwords is based on a lousy premise, it makes sense to confront the premise instead of "helping" the user do something complicated and not necessarily more secure.

---

### Post by bodhi.zazen on 2008-01-31
> **Xbehave said:**
> arg this thread is what annoys me about using these forums, somebody asked a valid question, instead of giving a valid answere there are 3 pages of "security" "experts" talking about the risks.
at the end of the day there are 3 reasons for his setup:
1) it gives 2 passwords to access admin
2) it means he can be sloppy with his user passwords (rember security =~ usability ^ -1)
3) ITS WHAT HE WANTS TO DO

thx go to bodhi.zazen's

LOL Xbehave, the benefit is users understand what they are doing !

> **aysiu said:**
> *expect* looks a little over my head, but the problem with *sudo*ing another script is that the *sudo* would be run as the first (non-admin) user, not the second (admin) one.

OK, just for you aysiu, I am indebted to you ;)

1. First I made a test user named "test",  not in the admin group :

> test@VirtualUbuntu:~$ groups
test
test@VirtualUbuntu:~$


2. Second, We need to configure sudo :twisted:
```
sudo visudo
```To edit your sudoers, add this line.

> # Added for test
test   ALL= **(bodhi)** /home/bodhi/bin/sudo_script
[indent]Put your admin user in parenthesis in place of "bodhi"[/indent]


3. Now lets write a script /home/bodhi/bin/sudo_script:

> # These first two echo the current user
echo "who am i"
echo `whoami`
echo

# Run fdisk -l as bodhi
echo "fdisk -l"
fdisk -l
echo

#run sudo fisk -l as bodhi
echo "sudo fdisk -l"
sudo fdisk -l

Permissions of script :

> -rwxr-----  1 bodhi bodhi  112 2008-01-31 16:17 sudo_script


4. Outupt :

[list=number][*]run fdisk as bodhi> bodhi@VirtualUbuntu:~$ fdisk -l

zsh: command not found: fdisk

[color=blue]fdisk -l does not run without sudo[/color]


[*] su to test and take it for a spin
> bodhi@VirtualUbuntu:~$ [color=blue]su test[/color]
Password: #[color=blue]Enter test Password[/color]

# Test can not run the script without sudo :
test@VirtualUbuntu:~$ [color=green]/home/bodhi/bin/sudo_script[/color]
bash: /home/bodhi/bin/sudo_script: [color=red]Permission denied[/color]
test@VirtualUbuntu:~$ [color=green]sh /home/bodhi/bin/sudo_script[/color]
[color=red]sh: Can't open /home/bodhi/bin/sudo_script[/color]
test@VirtualUbuntu:~$ [color=green]sudo /home/bodhi/bin/sudo_script[/color]
[sudo] password for test:[color=blue]Enter test Password[/color]
[color=red]Sorry, user test is not allowed to execute '/home/bodhi/bin/sudo_script' as **root** on VirtualUbuntu.[/color]

# Note the command is **sudo -u bodhi /home/bodhi/bin/sudo_script**
test@VirtualUbuntu:~$ [color=red]sudo -u bodhi /home/bodhi/bin/sudo_script[/color]
[color=green]who am i[/color]  <--- From the "echo" command
[color=blue]bodhi[/color]

[color=green]fdisk -l[/color]  <--- From the "echo" command

[color=green]sudo fdisk -l[/color]  <--- From the "echo" command

[color=red][sudo] password for bodhi:  **<--- ENTER BODHI's PASSWORD**[/color]

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000842a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1180     9478318+  83  Linux
/dev/sda2            1181        1305     1004062+  82  Linux swap / Solaris
test@VirtualUbuntu:~$[/list]

See how as my user, bodhi, I can not list the partitions without root ?

See how configuring sudo allows me to script sudo ?

[color=red]Note: During the execution of "sudo -u bodhi /home/bodhi/bin/sudo_script" we were not asked for test's password ?[/color]

[indent]This is because we entered it just previously and are within the 15 minute grace period for sudo with the user test.[/indent]

This brings up a good point though, [color=red]you should probably change the grace period for you admin users's sudo[/color]

Add an option to reduce this with visudo :

> timestamp_timeout
    Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively. 


passwd_timeout
    Number of minutes before the sudo password prompt times out. The default is 5, set this to 0 for no password timeout.

[color=red]AS ALWAYS, read and understand what you are doing. USE VISUDO to make changes to sudo functioning.[/color]

:lolflag:

I am sorry my previous commands were off, which is why I wrote a little demo ;)

[font=times][size=4][i]Peace be with you,[/size][/font]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]bodhi.[/color][color=darkgray]zazen[/font][/size][/color][/i]

---

### Post by az on 2008-02-01
> **forrestcupp said:**
> It's relevant because if my child was on his non-admin account, I would have to log out and back on to mine if I wanted to install a game for him in Synaptic.  Then I'd have to log out of my admin account and back into his non-admin for him to play the game.  If I had separate passwords, I wouldn't have to do that.  I could just get into Synaptic using the sudo password that he doesn't know.

Just click on the switch user applet on the default install.

> **oomingmak said:**
> I was afraid that would be the answer. 

So it's a case of either being relentlessly annoyed to death prompts for long passwords, or weaken your security. Not a good range of options really.


That's not an Ubuntu issue.  But with the current user/group permission system, you get to determine how simple or complex you want it to be.

> **Xbehave said:**
> arg this thread is what annoys me about using these forums, somebody asked a valid question, instead of giving a valid answer

An answer that's not what you hear may nonetheless be valid.

> **Xbehave said:**
> 
 there are 3 pages of "security" "experts" talking about the risks.
at the end of the day there are 3 reasons for his setup:
1) it gives 2 passwords to access admin
2) it means he can be sloppy with his user passwords (rember security =~ usability ^ -1)
3) ITS WHAT HE WANTS TO DO


You can already do that without anyone having to add features to sudo.  That's the point.  Just create another account.

---

### Post by oomingmak on 2008-02-01
> **az said:**
> That's not an Ubuntu issue. 
I never said it was. 

> **az said:**
> But with the current user/group permission system, you get to determine how simple or complex you want **it** to be.
How simple I want what to be?

---

### Post by Bob Morane on 2008-02-05
> **az said:**
> Just click on the switch user applet on the default install.

That would be a good point if the applet wasn't bugged.

I don't really understand why there is such a discussion here. I think having a separated sudo password might be usefull for some people, and completely useless to others. Linux is all about allowing every user to adapt their OS to their needs.
> 
you get to determine how simple or complex you want it to be
Mhh, actually, you get to determine how easy OR secure you want it to be, and i can understand SOME people would be happy with an intermediate measure.

---

### Post by bodhi.zazen on 2008-02-06
Just a heads up, for anyone interested, there is also the option of "targetpw".

> **targetpw**

    If set, sudo will prompt for the password of the user specified by the -u flag (defaults to root) instead of the password of the invoking user. Note that this precludes the use of a uid not listed in the passwd database as an argument to the -u flag. This flag is off by default.

I would assume this would involve setting a root password, as in my previous posts, so you may want to disable a root shell (see previous).

This may also help with scripts where you sudo -u <admin_user> and then use the admin user password (this way you would not need to know the password of the restricted user).

See also this post : [http://ubuntuforums.org/showpost.php?p=4280733&postcount=7](http://ubuntuforums.org/showpost.php?p=4280733&postcount=7)

[color=navy]~ Thanks abcuser[/color]

---

### Post by phrostbyte on 2008-02-06
> **bufsabre666 said:**
> on limited accounts, the menus lack add/remove synaptic and terminal, i dont know if alt-f2 works i didnt test that

You have pretty fine grained control over what a user can do with POSIX ACLs and also the built in Gnome stuff. And yes you can block alt-f2 as well.

---

### Post by Andrewie on 2008-02-07
> **aysiu said:**
> By that same token, couldn't they watch you type in your second password, too, to gain administrative privileges?

**Default Ubuntu behavior**
User logs in as user A and uses user A's password to start Synaptic Package Manager.
Watcher watches user type in password and now knows the sudo password for A and can change the root password.

**This newly proposed behavior**
User logs in as user A and uses user B's password to start Synaptic Package Manager.
Watcher watches user type in password and now knows the password for B and can change the root password.

I don't see the difference, frankly. If you're letting people see your password as you type it in, *that's* the real security risk.

very fair point, but I don't see sudo as any less secure then su

---

