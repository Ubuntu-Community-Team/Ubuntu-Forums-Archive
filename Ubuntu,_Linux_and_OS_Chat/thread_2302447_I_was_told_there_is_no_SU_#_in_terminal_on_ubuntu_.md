---
title: "I was told there is no SU # in terminal on ubuntu and everything is sudo per event"
date: 2015-11-10
forum: Ubuntu, Linux and OS Chat
---

### Post by gh0zt362 on 2015-11-10
Not true I found . You can run in a SU terminal mode after all . And I found it by accident . 

We all know sudo must be performed to get into a single instance super user permission to do admin tasks like installing software other tasks that require SU . 

But as you will see in the code below and subsequent state . If you sudo SU it requires your password and then leaves you at a super user terminal . 




Just thought I'd share this discovery as I was told it was possible.  For those of you whom already know I'm sure there are plenty like me who didn't. :popcorn: 

```
redacted@Toshi:~$ sudo su
 [sudo] password for redacted: 
root@Toshi:/home/redacted# 
```

---

### Post by QIII on 2015-11-10
Cheers!  Discovery is always fun!

But I don't use it often.  Better to use sudo and have that little reminder than to su and think you are safe and bork something.  sudo also protects you from accidentally changing permissions on files you'd rather not.

---

### Post by gh0zt362 on 2015-11-10
> **QIII said:**
> Cheers!  Discovery is always fun!

But I don't use it often.  Better to use sudo and have that little reminder than to su and think you are safe and bork something.  sudo also protects you from accidentally changing permissions on files you'd rather not.


Agreed , this is not a state a novice user who doesn't know what they are doing would want to operate in .  But I feel I've stretched my legs enough in the linux world that Im ok to do so . I came from Fedora 22 KDE and I switched to Ubuntu studio 15.10  Cause I was having all kinds of issues with multi media codecs on Fedora no matter ffmpeg or other plugins . ( I swear I installed them all ) and hstill had issues playing say burned DVD movies and even some factory DVDs so I wanted a distro that was created for multimedia . Ubuntu studio plays EVERYTHING . out the box.

But I missed the root state in terminal cause I dont like having to password for EVERY thing I do .   

But again you are correct. If anyone reading this is a novice linux user Root terminal can do alot of damage if you arn't sure of what you are telling it to do and you CAN end up borking the system . 


But I havn't done it yet so ...

---

### Post by coffeecat on 2015-11-10
If you really must use a root shell - I very rarely do - then you are better of using "sudo -i" rather than "sudo su" which can cause problems as described here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You are well advised to read that link. 

Now that you have, here's another link for you, our forum policy on root login:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Having now told everyone, newcomers included, how to log into a root shell, will you make yourself available 24/7 to support any user experiencing issues as a result of running a root shell, and as requested in the first link?

---

### Post by gh0zt362 on 2015-11-10
> **coffeecat said:**
> If you really must use a root shell - I very rarely do - then you are better of using "sudo -i" rather than "sudo su" which can cause problems as described here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You are well advised to read that link. 

Now that you have, here's another link for you, our forum policy on root login:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Having now told everyone, newcomers included, how to log into a root shell, will you make yourself available 24/7 to support any user experiencing issues as a result of running a root shell, and as requested in the first link?

Is that really the case though ? As per your link it states anyone that shows how to setup a root password . I didn't do that at all . I merely showed how to login as root for people who already have a root account enabled.  

In any event I'd be happy to assist in anyway I can . If there is any problems. I'm not a super expert but Ive learned a few things over the years . ;)

---

### Post by deadflowr on 2015-11-10
Your title is still right, you know.

sudo su is still an event using sudo.
try it without sudo and see what you get.

---

### Post by gh0zt362 on 2015-11-10
> **deadflowr said:**
> Your title is still right, you know.

sudo su is still an event using sudo.
try it without sudo and see what you get.
Authentication failure :-k   so it is a shell inside of a shell ?

---

### Post by deadflowr on 2015-11-10
> **gh0zt362 said:**
> Authentication failure :-k   so it is a shell inside of a shell ?
it's because su need root's password, which on Ubuntu is locked and disabled.
sudo su bypasses su's need for root password.
is all.

---

### Post by matt_symes on 2015-11-10
Hi

> I was told there is no SU # in terminal on ubuntu and everything is sudo per event 

There is a su binary on Ubuntu.

```
media-server1:/home/matthew:7 % which su
/bin/su
media-server1:/home/matthew:7 %
```

If you know another users password then you can use su to change to that user.
```

media-server1:/home/matthew:7 % su - jerry
Password: 
jerry@media-server1:~$ whoami
jerry
jerry@media-server1:~$ 
```

As has been pointed out though, because the root password is locked you cannot su to root.

```
sudo su
```

will get you to a root shell but it uses sudo to authenticate you. You have to enter your sudoers password.

sudo itself is a setuid binary and is owned by root.
```

matthew-laptop:/home/matthew:0 % ls -l $(which sudo)
-rwsr-xr-x 1 root root 155008 Aug 27 20:26 /usr/bin/sudo*
matthew-laptop:/home/matthew:0 
```

When you run the command sudo <command>, it runs sudo with the effective ID of 0 or root's ID. Root's ID is usually 0 but, as far as i'm aware, it does not have to be and is generally 0 due to convention.

sudo can then decide whether you have permission to run the command that follows sudo by looking at the rules in the file /etc/sudoers.

These rules include looking at the machine name in the case of a network sudoers file, the command itself and under what user you are trying to run the command under.

```
media-server1:/home/matthew:7 % whoami && sudo -u jerry whoami
matthew
jerry
media-server1:/home/matthew:7 % sudo -u jerry cat /etc/shadow
cat: /etc/shadow: Permission denied
media-server1:/home/matthew:7 % 
```

In the case of running sudo without a user specified, it will use the root user.

However, unless you edit the sudoers file, it will ask you for your password because sudo wants to authenticate you are you, then check you are a valid sudo user and then check if you can run the command you want to run.

The above is a bit simplified but you get the idea.

As has also been stated, it's best to keep away from root shells. 

Kind regards

---

### Post by gh0zt362 on 2015-11-10
Very cool . Lots to read .  I wish fedora had ubuntu's functionality . But no matter how many ppa I installed to attain access to different codec packs and plugins it just never worked right with multi media.   I was never even able to solve the realtek rts134 or whatever module problem that prevented my SD card slot from working .  Although I did repair my filesystem from a pre mount state which was pretty cool . 

Thanks for the info ladies and gents. This is precisely why I love linux so much . Theres always a challenge  , always something to learn .  Not like mind numbing windows that just drones on sending your information to NSA data fusion centers in utah . lol

---

### Post by mastablasta on 2015-11-11
> **gh0zt362 said:**
> Very cool . Lots to read .  I wish fedora had ubuntu's functionality . 

what do you mean? you can install sudo on Fedora, no?

---

### Post by buzzingrobot on 2015-11-12
> **gh0zt362 said:**
> I wish fedora had ubuntu's functionality. 

Fedora's implementation of of sudo and the root user is conventional.  I.e., there is a root user.  It's Ubuntu that deviates from the Unix/Linux convention.  I seldom find a reason to run as root anywhere.  When I use Fedora, I configure it to allow use of sudo without a prompt for authentication. 

> But no matter how many ppa I installed to attain access to different codec packs and plugins...

There are no PPA's for Fedora.  By commitment to FOSS ideology and legal constraints on Red Hat, Fedora's sponsor, Fedora does not and will not ship non-free software.  Canonical is not subject to the same legal constraints as Red Hat. The primary source of software that Fedora cannot ship is rpmfusion.org.

> ...mind numbing windows that just drones on sending your information to NSA...

Don't believe everything you read on the net.  People do lie.   Besides, the internet is the internet and it's an open public space. Any government or private institution with the right resources can pretty much read what it wants to read. In all probability, your traffic is just bothersome noise.

---

### Post by gh0zt362 on 2015-12-04
> **mastablasta said:**
> what do you mean? you can install sudo on Fedora, no?

I meant multimedia. As I said I ran every multimedia codec and plugin I could find on F22 KDE and it still cant play some ripped dvds as well as factory OEM DVD movies.

---

### Post by Motuka on 2015-12-06
I use sudo -i when I want to enter root for long and many root operations, but still I do not use it often. As pointed out, you may forget that you are in su privillege and mess up - esp. since I multitask a lot.

---

### Post by Skaperen on 2015-12-06
i use it a lot, too, but, i use it like this:  **ssh admin@someserver -t sudo -i**

---

