---
title: "John the Ripper Installed Without My Knowledege"
date: 2010-11-02
forum: Security
---

### Post by gdegabriel on 2010-11-02
Hello all,
I am relatively new to Ubuntu and may have a security breech. I was recently looking over synaptics installed packages on my PC and noticed JOHN installed on my system. This was never installed by me nor do I think this entire APP is a dependency of something that may have been installed.

My questions are... 

Has my system been compromised? I use an elaborate password as well as UFW.

Can I determine who installed this package (i.e. local user account or remote user)?

Can I determine when? The system was installed only 3 days ago.

Can I determine if there have been any instances of a successful or failed remote connection to my PC?

Are there specific ports to block in regards to remote access.

I have read the security post for Ubuntu and am not running any server apps that I am aware of. Neither VNC nor SSH are currently installed.

Thanks for your help.

---

### Post by SlugSlug on 2010-11-02
does 
```
sudo grep -C10 *john* /var/log/apt/history.log
```show anything?

---

### Post by gdegabriel on 2010-11-02
unfortunately that command in terminal did not display anything however, I opened up the  /var/log/apt/history.log and a cntrl F reveled the following information...

```
Start-Date: 2010-11-01  11:16:41
Install: sendmail-bin (8.14.3-9.1ubuntu1), sendmail (8.14.3-9.1ubuntu1), sendmail-base (8.14.3-9.1ubuntu1), m4 (1.4.13-3), tiger (3.2.2-11ubuntu1), john-data (1.7.3.1-1), procmail (3.22-18ubuntu1), sensible-mda (8.14.3-9.1ubuntu1), diff (2.8.1-18), sendmail-cf (8.14.3-9.1ubuntu1), chkrootkit (0.49-3), john (1.7.3.1-1)
End-Date: 2010-11-01  11:17:12

After reading some of the descriptions to the packages installed I am even more disturbed. 

It seems that this was the only series of packages installed at this time which is not like me at all. In fact I don't remember being at my computer at that hour.

Wish I could determine which user installed this. I assume the system will only display SUDO. Perhaps there is a way of telling if it was installed via a remote command unless someone gained physical access to my PC I don't see how this is possible.

I currently have a 3 day old installation with only one user account. Frustrating indeed.

Played with the terminal command and it does display the results if typed without the * before and after john. Scratchin my head anyway...

cheeseartist@Pandora:~$ sudo grep -C10 *john* /var/log/apt/history.log
[sudo] password for cheeseartist: 
cheeseartist@Pandora:~$ sudo grep *john* /var/log/apt/history.log
cheeseartist@Pandora:~$ sudo grep john /var/log/apt/history.log
Install: sendmail-bin (8.14.3-9.1ubuntu1), sendmail (8.14.3-9.1ubuntu1), sendmail-base (8.14.3-9.1ubuntu1), m4 (1.4.13-3), tiger (3.2.2-11ubuntu1), john-data (1.7.3.1-1), procmail (3.22-18ubuntu1), sensible-mda (8.14.3-9.1ubuntu1), diff (2.8.1-18), sendmail-cf (8.14.3-9.1ubuntu1), chkrootkit (0.49-3), john (1.7.3.1-1)
cheeseartist@Pandora:~$ sudo grep -C10 john /var/log/apt/history.log
Start-Date: 2010-11-01  08:27:50
Install: privoxy (3.0.15-3)
End-Date: 2010-11-01  08:27:59

Start-Date: 2010-11-01  08:34:53
Install: adobe-flashplugin (10.1.85.3-1lucid1)
Remove: flashplugin-installer (10.1.85.3ubuntu0.10.04.1)
End-Date: 2010-11-01  08:34:59

Start-Date: 2010-11-01  11:16:41
Install: sendmail-bin (8.14.3-9.1ubuntu1), sendmail (8.14.3-9.1ubuntu1), sendmail-base (8.14.3-9.1ubuntu1), m4 (1.4.13-3), tiger (3.2.2-11ubuntu1), john-data (1.7.3.1-1), procmail (3.22-18ubuntu1), sensible-mda (8.14.3-9.1ubuntu1), diff (2.8.1-18), sendmail-cf (8.14.3-9.1ubuntu1), chkrootkit (0.49-3), john (1.7.3.1-1)
End-Date: 2010-11-01  11:17:12

Start-Date: 2010-11-02  04:03:47
Remove: gnome-bluetooth (2.30.0-0ubuntu3), gnome-user-share (2.30.0-0ubuntu2)
End-Date: 2010-11-02  04:04:05

Start-Date: 2010-11-02  04:16:38
Remove: firestarter (1.0.3-7ubuntu5)
End-Date: 2010-11-02  04:16:48

cheeseartist@Pandora:~$ sudo grep -C10 john /var/log/apt/history.log
Start-Date: 2010-11-01  08:27:50
Install: privoxy (3.0.15-3)
End-Date: 2010-11-01  08:27:59

Start-Date: 2010-11-01  08:34:53
Install: adobe-flashplugin (10.1.85.3-1lucid1)
Remove: flashplugin-installer (10.1.85.3ubuntu0.10.04.1)
End-Date: 2010-11-01  08:34:59

Start-Date: 2010-11-01  11:16:41
Install: sendmail-bin (8.14.3-9.1ubuntu1), sendmail (8.14.3-9.1ubuntu1), sendmail-base (8.14.3-9.1ubuntu1), m4 (1.4.13-3), tiger (3.2.2-11ubuntu1), john-data (1.7.3.1-1), procmail (3.22-18ubuntu1), sensible-mda (8.14.3-9.1ubuntu1), diff (2.8.1-18), sendmail-cf (8.14.3-9.1ubuntu1), chkrootkit (0.49-3), john (1.7.3.1-1)
End-Date: 2010-11-01  11:17:12

Start-Date: 2010-11-02  04:03:47
Remove: gnome-bluetooth (2.30.0-0ubuntu3), gnome-user-share (2.30.0-0ubuntu2)
End-Date: 2010-11-02  04:04:05

Start-Date: 2010-11-02  04:16:38
Remove: firestarter (1.0.3-7ubuntu5)
End-Date: 2010-11-02  04:16:48

cheeseartist@Pandora:~$ clear

cheeseartist@Pandora:~$ sudo grep -C10 john /var/log/apt/history.log
Start-Date: 2010-11-01  08:27:50
Install: privoxy (3.0.15-3)
End-Date: 2010-11-01  08:27:59

Start-Date: 2010-11-01  08:34:53
Install: adobe-flashplugin (10.1.85.3-1lucid1)
Remove: flashplugin-installer (10.1.85.3ubuntu0.10.04.1)
End-Date: 2010-11-01  08:34:59

Start-Date: 2010-11-01  11:16:41
Install: sendmail-bin (8.14.3-9.1ubuntu1), sendmail (8.14.3-9.1ubuntu1), sendmail-base (8.14.3-9.1ubuntu1), m4 (1.4.13-3), tiger (3.2.2-11ubuntu1), john-data (1.7.3.1-1), procmail (3.22-18ubuntu1), sensible-mda (8.14.3-9.1ubuntu1), diff (2.8.1-18), sendmail-cf (8.14.3-9.1ubuntu1), chkrootkit (0.49-3), john (1.7.3.1-1)
End-Date: 2010-11-01  11:17:12

Start-Date: 2010-11-02  04:03:47
Remove: gnome-bluetooth (2.30.0-0ubuntu3), gnome-user-share (2.30.0-0ubuntu2)
End-Date: 2010-11-02  04:04:05

Start-Date: 2010-11-02  04:16:38
Remove: firestarter (1.0.3-7ubuntu5)
End-Date: 2010-11-02  04:16:48

removing the c10 displays....
cheeseartist@Pandora:~$ sudo grep john /var/log/apt/history.log
Install: sendmail-bin (8.14.3-9.1ubuntu1), sendmail (8.14.3-9.1ubuntu1), sendmail-base (8.14.3-9.1ubuntu1), m4 (1.4.13-3), tiger (3.2.2-11ubuntu1), john-data (1.7.3.1-1), procmail (3.22-18ubuntu1), sensible-mda (8.14.3-9.1ubuntu1), diff (2.8.1-18), sendmail-cf (8.14.3-9.1ubuntu1), chkrootkit (0.49-3), john (1.7.3.1-1)
cheeseartist@Pandora:~$
```

---

### Post by SlugSlug on 2010-11-02
so it seems what ever was installed at 11:16:41 brought John with it..

you could try 
sudo grep 11:16:41 /var/log/auth.log

---

### Post by SlugSlug on 2010-11-02
are you sure you never installed any security auditing programs?

Tiger & m4 are mentioned there

---

### Post by CharlesA on 2010-11-02
chkrootkit too.

---

### Post by artie_effim on 2010-11-02
According to `apt-rdepends -r john` no other package depends on john.  I strongly suggest disconnecting from the network, booting from a LiveCD with chrootkit, running chrootkit from the LiveCD, doing a full disk wipe with dd and then re-installing -- ALL OFF NETWORK.

Also, are there other computers connected to that network?  If so, I would suggest that they are compromised as well.

---

### Post by cariboo on 2010-11-02
> **artie_effim said:**
> According to `apt-rdepends -r john` no other package depends on john.  I strongly suggest disconnecting from the network, booting from a LiveCD with chrootkit, running chrootkit from the LiveCD, doing a full disk wipe with dd and then re-installing -- ALL OFF NETWORK.

Also, are there other computers connected to that network?  If so, I would suggest that they are compromised as well.

Why should the op do a re-install, john was obviously installed as a dependency of one of the packages he installed. This is more a matter of someone not paying attention when installing packages than anything else.

john is a recommend for tiger.

---

### Post by Rubi1200 on 2010-11-02
From bodhi.zazen's link about installing tiger:

> _**Note**_: This will install [COLOR=Red]john[/COLOR] and [COLOR=Red]ckrootkit[/COLOR] as well.

[http://ubuntuforums.org/showpost.php?p=9265631&postcount=6](http://ubuntuforums.org/showpost.php?p=9265631&postcount=6)

---

### Post by artie_effim on 2010-11-02
> **cariboo907 said:**
> Why should the op do a re-install, john was obviously installed as a dependency of one of the packages he installed. This is more a matter of someone not paying attention when installing packages than anything else.

john is a recommend for tiger.

AH - I only did a search for depends not recommends.  Now I see it.  Then I stand corrected, if OP installed tiger, then by all means there is nothing wrong.  But, OP stated that "It seems that this was the only series of packages installed at this time which is not like me at all. In fact I don't remember being at my computer at that hour."  --- with that I still feel that the box was compromised.  Better safe than sorry.

Or, better yet - would you do your on-line banking on that box??

---

### Post by gdegabriel on 2010-11-02
Ok I feel like an idiot...

I did install said packages via terminal following the guidelines in this post on Ubuntu security [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

My question is this though why oh why would a program like tiger need john? I can kinda see why... let tiger run john to see if can compromise your password yet on the other hand it's like really your going to install an app for hacking passwords and leave it there on my PC?!

Anyway, I tried running tiger as a means of identifying any security holes and it never completed. Will try running again. Sorry folks it was a late night burning the midnight oil into the next morning.

I would like to thank everyone for taking the time to help me with this issue. Much appreciated.

---

