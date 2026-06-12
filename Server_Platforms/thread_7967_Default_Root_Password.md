---
title: "Default Root Password?"
date: 2004-12-13
forum: Server Platforms
---

### Post by sway on 2004-12-13
Is there are default password for the root account? Because I just can't log in to it. I wanna install some extra packages. I can't remeber during the installation that it ever asked me for a pw for the root account.

---

### Post by p!=f on 2004-12-13
[QUOTE=sway]Is there are default password for the root account? Because I just can't log in to it. I wanna install some extra packages. I can't remeber during the installation that it ever asked me for a pw for the root account.[/QUOTE]

What's the root password after I install? How do I use the root account?
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

Too lazy to look around? :D

---

### Post by sway on 2004-12-13
omw, so sorry =] i was really in a hurry and btw thank you for the quick response.

---

### Post by percy on 2005-02-21
Hi, 

I've found out a better way howto become root, I've used debian before so I rebooted the laptop with a debian installation cd in. 
Then I started a shell and just mounted the root filesystem under /mnt.
Then I run nano-tiny /etc/shadow and erased the root password. 
That givs you the right to create a new password for root after you reboot again however you have to do that in a another tty.

Cheers

---

### Post by Juergen on 2005-02-22
That doesn't sound much easier than just
```
sudo passwd root
``` ;-)

BTW I haven't found any task I couldn't do with sudo (maybe with -s) or gksudo. 
I really don't know what you all need that root passwd for.

---

### Post by p!=f on 2005-02-22
[QUOTE=Juergen]That doesn't sound much easier than just
```
sudo passwd root
``` ;-)

BTW I haven't found any task I couldn't do with sudo (maybe with -s) or gksudo. 
I really don't know what you all need that root passwd for.[/QUOTE]
Try to change your hostname without changes in /etc/hosts. And then try to sudo. ;) Have a Live CD by hand. :)

---

### Post by Juergen on 2005-02-22
> Try to change your hostname without changes in /etc/hosts. And then try to sudo.Proves my point: you can even shoot yourself with sudo ;-)

Hmm. I just found out that I don't have any boot-menu(-delay) on my system here at work (Virtual PC and so no multi-boot). 
Perhaps I should change this before doing more experiments - single-user mode may be necessary :-)

---

### Post by rb1235 on 2005-04-09
I am also not able to su as root nor to unlock the root password. When i typed
sudo passwd root
I got:
unable to look up 'popeye' voa gethostbyname()

what did i do wrong?

---

### Post by p!=f on 2005-04-09
[QUOTE=rb1235]I am also not able to su as root nor to unlock the root password. When i typed
sudo passwd root
I got:
unable to look up 'popeye' voa gethostbyname()

what did i do wrong?[/QUOTE]
That's what I was talking about some posts above. :) Did you try it? ;)
Looks like you changed your hostname without a correct entry in your /etc/hosts. You have to use LiveCD or the single user mode to change hostname to match the real one.

example:
```

[~] > cat /etc/hosts
127.0.0.1 localhost.localdomain localhost
192.168.1.2 popeye.home popeye

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

[~] > cat /etc/hostname
popeye

```
If you change the hostname, sudo is not able to find the entry to match your new hostname. It probably "works" vice versa so changing "popeye.home popeye" to "popeyes.home popeyes" will also lead to the error.

---

### Post by Gyom on 2005-04-09
I am a new Ubuntu user, and just installed the hoary-rc-install (a week ago). At the beginning everything worked perfektly before I made apt-get upgrade on the 7th of April (at night) just before they released the actual hoary stable version (04/08). The system was upgraded with a new kernel which appear to create some failure when my system is loading.

_First question_: Was Hoary-rc-install-x86 a development release? Does release candidate mean final release?

_Second question_: How can I upgrade my system especially kernels without remove older kernel images (I was under Fedora core 3 before, and I could keep all my kernels)??
[U]
I found another strange and relevnat thing:[/U]

It is possible to change root password with the gnome interface _without any password prompting_ before, that's really bad!!! And "su" command doesn't seem to require the same password as "sudo", what the heck is that?

Why are there two different password to become a super user?

Thanks to people who will reply

Gyom

---

### Post by Moss on 2006-08-13
I'm a newbie to ubuntu and linux, so this could be risky!

This process may reset all your user passwords, and invoking a new password may be necessary for any normal users as well as root (administrator) before shutdown.

1. open bash editor

2. logon as sudo (using normal user password)
   # sudo -i

3. delete root password file called shadow in /etc
   # rm /etc/shadow

4. make a new shadow file with the pwconv command in /etc folder
   # pwconv

5. enter new password for root
   # passwd root

6. enter new password for your normal user name(s). (Important in order to log back into your computer system, as a root account may not be accepted at login).
   # passwd user

---

### Post by aysiu on 2006-08-13
Isn't the normal procedure just ```
sudo passwd root
```

---

### Post by aysiu on 2006-08-13
Isn't the normal procedure just ```
sudo passwd root
``` ?

---

### Post by Moss on 2006-08-13
congratulations if 'sudo passwd root' worked for you as a means to changing the root password, however I (a linux novice) just tried it and it didn't work for me.:confused:

While sudo can do the biz, su I reckon is the ultimate access for total file permission control and software installation, and I think only a proper system root (su) can change an su password that is already been set (unless of course you can delete it from the system first).

Being a newbie, I'm open to correction ;) .

---

### Post by aysiu on 2006-08-13
*sudo* and *su* have the same privileges--total.

---

### Post by wizardleaf on 2006-11-21
I think this will help u!

i had installed ubuntu 6.10 ....i was surprised there was already password made for "root" i dont know if it was the default setup of ubuntu because when i'm in the middle of installing ubuntu i did not remember that i was asked to type the 'Root password' i was only ask for the user and the user password....then there was a time i needed to log as root or to do "su" command to have 'root privilege' but i don't know the password made for it....

the first step i did was to restart then in boot loader or Grub i chose 'ubuntu in recovery/safemode'...from there i was logged as 'root' without asking for any root password ...then inside the terminal i did 'passwd' command...ubuntu was ask me to input NEW password....viola! problem solved!

by the way this only works if you did not set any root password and in newly installed ubuntu!

---

### Post by deanlinkous on 2006-11-21
sheesh ;) Climb over the tree instead of just walking around it...
**sudo passwd root**
or if you wish
**sudo su**
**passwd**

I also keep a launcher on my panel with the command
**gksudo nautilus**
as well as another launcher with the command
**gksudo "gnome-open %u"**
so I can drag and drop a file on it and have root privys to edit it.

---

### Post by wizardleaf on 2006-11-21
i'll go for the long run ...

sudo su passwd

or 

sudo su
passwd

..this  is not working if you try to change root password (if you don't know the root password) if you were logged as ordinary user as my experience a while ago...thats why i go for logging in safemode 

by the way im using ubuntu 6.10 x86-64

---

### Post by fabioleitao on 2006-11-21
Using Linux and other BSDs since 1994, I was very pleased when I first tried Ubuntu and was amazed with the easy integrated and well build result some smart coding could bring to end users and system administrator.

But NOT HAVING A ROOT PASSWORD was the fisrt thing I though was a BIG flaw in Ubuntu](*,) ... but later I've learned to LOVE and UNDERSTAND as security aspect;) .

One may not agree with me, but it is better if you do not work as root for long periods of time and the shortest path to gain root privileges and soon be demoted back to regular user is the sudo command. I use both modalities, depending on what I am trying to accomplish... hundreds of sudo commands or scripts may require my password once at the first... or if they take some time... sudo will expire my privileges and the next bunch will ask for my password again (Automatix used to do just that).

But if you are sure you need to use root account (instead of the privileges), or mantain for quite some time the su status, you can follow those tips:

1 - Ubuntu sudo askes for the USER'S PASSWORD (many distros used to ask for the same password the root uses, there fore, the system adminidtrator would need to tell the sudoers the root password). It's better to remember only one password (yours) and safer not to teel the root one.

2 - Only users in the %admin group can sudo (default Ubuntu user account is in admin; check the **/etc/group** and **/etc/sudoers** files and **id [your login]** command in the bash)

3 - Try the **sudo passwd** without any user (the replies above were always sudo passwd root)... even shorter and worked for me on every version since 5.04.

4 - Do not use **sudo su** followed by **passwd**:-k.  You sould be able to run su (ofcorse) and your prompt would indicate the root login, but you would still not be able to run the passwd command because su (alone) would not have given you the full root privileges[-( . The alternative should be **sudo su -**. The - (dash) forces the su to change the fully to the root privileges (check the set command for the environment differences using and not using the -). The same would happen when trying to change to any other user with su (for instance **su yourmomlogin** and try **set > some.txt **, change the su again using **su - yourmomlogin** , then **set > other.txt** and finally a **diff some.txt other.txt**).

5 - Amongst other settings, the su alone keeps you on the user path (usuallu /home/login#) and su - starts at the /root  (it will show as ~#). Different desktop session, different .xauthoroty, different keyring socket, different ssh auth sock (and PID), different session manager, different user name (su alone still shows the original login).

6 - After you carefully worked under root account, and you did your best not to destroy your system, remember to change back to your user account (either **exit**, **Ctrl-D** or even **su - yourlogin**).

I hope this covers your difficulties.

---

### Post by awsomedude2006 on 2007-07-30
I understand that the last post was from a while ago, but I'll say the (somewhat obvious). As long as you have a feisty or gutsy build, you can do the following:
      Click 'System' at the top bar
      Go into 'Administration'
      Click 'Users and Groups'
      Highlight the 'root' account and click 'Properties' 
      Make sure that 'set password by hand' is checked
      Delete whatever the round black bubbles are supposed to say (who knows?)
      Type whatever you want in the password area
      Log out and try to login to the root account!
  Now, I think that most accounts are marked as admins, so it should work. 
When I tried logging in, it told me: "The System Administrator is not allowed to log in  from this screen" but hey, I changed the pass right?

---

### Post by aysiu on 2007-07-30
Well, apart from the fact that it's unnecessary to log in as root graphically (Alt-F2 ```
gksudo nautilus
``` is much faster and, some would argue, more secure), if you want to log in as root graphically, you'd also have to go to System > Administration > Login Window and allow root logins.

---

