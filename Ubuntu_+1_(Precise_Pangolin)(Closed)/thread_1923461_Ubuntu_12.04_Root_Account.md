---
title: "Ubuntu 12.04 Root Account?"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Cookieh on 2012-02-10
Recently, I have upgraded my Ubuntu 11.10 to Ubuntu 12.04 Precise Pangolin and I can not find a way on how to login as root. I have tried:

```
sudo passwd root
enter new UNIX pass
```
and so on, but I still don't get the other login at the login screen...

Any suggestions?

---

### Post by CharlesA on 2012-02-10
You can't login as root into the GUI. It would be a bad idea to do so in any case.

Ubuntu uses sudo to run commands with root privileges :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Why do you need to login as root?

---

### Post by collisionystm on 2012-02-10
As Charles stated, do not login as root. There is no need.
Having root disabled is the best and safest way to run your system.

BUT if you really want to

edit /etc/lightdm/users.conf

Change minimum-uid=500 to

minimum-uid=0

---

### Post by dcstar on 2012-02-10
> **Cookieh said:**
> Recently, I have upgraded my Ubuntu 11.10 to Ubuntu 12.04 Precise Pangolin
.........
Any suggestions?

[LIST=1]
[*]12.04 is still Alpha development software and should not be used for anything but bug finding and reporting until it is officially released.
[*]All 12.04 issues must be reported using the specific procedure outlined in the development web page: [https://wiki.ubuntu.com/Testing/](https://wiki.ubuntu.com/Testing/) Discussions are here: [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)
[*]You cannot use these forums for any pre-release issues.
[/LIST]

---

### Post by Vishnu V on 2012-02-11
> **collisionystm said:**
> As Charles stated, do not login as root. There is no need.
Having root disabled is the best and safest way to run your system.

BUT if you really want to

edit /etc/lightdm/users.conf

Change minimum-uid=500 to

minimum-uid=0
Hi i dont want root to login into GUI, but i have a hidden user account (uid 503) want to login into gui, but on ubuntu 12.04 there is no option to login (Ubuntu 11.10 there is an "Other" option) to do this
Please help

Thanks 
Vishnu

---

### Post by Cookieh on 2012-02-11
Thats the problem, I know how to use sudo commands and Nautilus, but with Precise, theres a chance of about 40% of Nautilus crashing in Alpha 2, but I know the safety precautions of using root account as GUI as I have used it in 11.10, but the account would be for debugging features as I am trying to collect details of bugs and ways to fix them.

Oh well, Thanks Forum people!

---

### Post by collisionystm on 2012-02-11
> **Vishnu V said:**
> Hi i dont want root to login into GUI, but i have a hidden user account (uid 503) want to login into gui, but on ubuntu 12.04 there is no option to login (Ubuntu 11.10 there is an "Other" option) to do this
Please help

Thanks 
Vishnu

How did you add the user? Anything above 500 should automatically appear on the screen.

---

### Post by Vishnu V on 2012-02-11
> **collisionystm said:**
> How did you add the user? Anything above 500 should automatically appear on the screen.
Only accounts having uid >= 1000 will appear on login screen (Source [http://ubuntuforums.org/showthread.php?t=1344414]("http://ubuntuforums.org/showthread.php?t=1344414"))

i created account using the command
```

sudo useradd -u 505 username

```

---

### Post by oldos2er on 2012-02-11
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by ronacc on 2012-02-11
> **CharlesA said:**
> You can't login as root into the GUI. It would be a bad idea to do so in any case.

Ubuntu uses sudo to run commands with root privileges :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Why do you need to login as root?

You may not "need" to log in as root but sometimes it is a lot more convenient and efficient to do so  .

---

### Post by CharlesA on 2012-02-11
> **ronacc said:**
> You may not "need" to log in as root but sometimes it is a lot more convenient and efficient to do so  .
Logging into a GUI as root is a bad idea.

If you want a root prompt just use sudo -i from a terminal.

There is no need to activate the root account when you can use sudo.

Please read the link in the post you quoted.

---

### Post by Ibidem on 2012-02-11
"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things."

Try to get your head around the notion that maybe, once in a while, there just might be a valid reason for not using your computer exactly the way Canonical says to.

Have you ever run into situations where sudo broke?  Until you can guarantee that nothing will ever screw up sudo, anywhere, flat out insistence that sudo is the ONLY way ANYONE should EVER get root on Ubuntu is premature.

Not that running as root is usually a good idea, just that you are extrapolating that far more than is justifiable.  Plenty of people have used Puppy installs without killing their systems.

---

### Post by cariboo on 2012-02-11
Not enabling the root account, is only a suggestion, nobody ever said that your system would blow up if you enabled the account :). The [RootSudo]("https://help.ubuntu.com/community/RootSudo") howto, even tells you how to enable the root account, with the appropriate warnings. After all it is your computer, and you can do what you want with it, just don't expect to much support if you hose the system, by running as root all the time.

---

### Post by savanna on 2012-02-11
Logging in as root from the GUI is a bad idea - why do you want to do it?

---

### Post by CharlesA on 2012-02-12
> **Ibidem said:**
> 
Have you ever run into situations where sudo broke?  Until you can guarantee that nothing will ever screw up sudo, anywhere, flat out insistence that sudo is the ONLY way ANYONE should EVER get root on Ubuntu is premature.

Broken sudo means a trip to recovery mode and dropping to a root prompt to fix it. That happens even if the root account isn't activated.

> **cariboo907 said:**
> Not enabling the root account, is only a suggestion, nobody ever said that your system would blow up if you enabled the account :). The [RootSudo]("https://help.ubuntu.com/community/RootSudo") howto, even tells you how to enable the root account, with the appropriate warnings. After all it is your computer, and you can do what you want with it, just don't expect to much support if you hose the system, by running as root all the time.

What Cariboo said. If you do enable root, be very careful. ;)

---

### Post by Gregory Lee on 2012-02-12
I do dislike using "sudo" as a prefix to many things that I need to use a terminal shell for, and I was disappointed to find that "su" no longer worked.  However, once I figured out that "sudo -i" could be used to the same purpose, I was happy again.  I don't know why "su" couldn't have been used, but I guess I could make an alias for it, if I really cared.

I never logged in as root in my previous systems, at least not for a decade or so, so I don't miss this at all.

---

### Post by ronacc on 2012-02-12
> **savanna said:**
> Logging in as root from the GUI is a bad idea - why do you want to do it?

here is one of the places I use a root session . If I want to search for and open a file as root I can use nautilus to search for the file as and then use "open with" to open it , if nautilus is invoked with gksudo any child process are not opened as root requiring you to open a second terminal and open the child process (eg gedit) as root whereas if you are root you are root .

---

### Post by Gregory Lee on 2012-02-12
> **cariboo907 said:**
> The [RootSudo]("https://help.ubuntu.com/community/RootSudo") howto, even tells you how to enable the root account ... 
That's a helpful reference, though I didn't want to enable the root account.  I have a related question.  What is the easiest way to use vi instead of nano for system tasks where some editor is automatically invoked?  (I'm not familiar with nano, and I don't think I care for it.)

Reading the man page for visudo gave me the idea that adding "/usr/bin/vi" to the environment variable VISUAL might work, but it doesn't seem to.

---

### Post by ranch hand on 2012-02-12
You can also easily get in as root when booting to recovery.

If you do not need to get in as root often this is easier than setting up the root account.

If you are going in as root more than twice a month the root account is the way to go.

Besides, it gives you the chance to set up a completely different desktop for that root user.  Had one cycle that was funky and spent a lot of time as root (9.10-testing).  Ended up with a nicer root user desktop than on the regular user desktop on that install.

That particular install was strictly for working with grub2.  Every thing was done as root anyway.  Why log in as anything else?  Didn't seem to hurt to play music as root.

I am still using the same box so I guess it survived the ordeal.

That was also one of the few 9.10 testing installs that lasted the entire cycle without reinstallation.  Had a total of 11 installs that round if I recall right.

---

### Post by Ibidem on 2012-02-12
Gregory Lee:
export EDITOR=vi
(Or configure sensible-editor to point there)
VISUAL ought to be checked when X is up and the root shell is properly configured to use it (DISPLAY set & xhost allowing it).

Charles:
If no root password was set, anyone who has physical access can get a root shell by pressing an arrow key, enter, and enter a second time.
That's a little too easy for my own liking, though you can get a shell other ways (unless you use grub1 or lilo with passwords and have USB/CD/... boot turned off in the BIOS--grub2 passwords are done completely wrong)

---

### Post by Gregory Lee on 2012-02-12
> **Ibidem said:**
> 
export EDITOR=vi

Works.  Neat.  Thanks.

---

### Post by VMC on 2012-02-12
> **Gregory Lee said:**
> I do dislike using "sudo" as a prefix to many things that I need to use a terminal shell for, and I was disappointed to find that "su" no longer worked.  However, once I figured out that "sudo -i" could be used to the same purpose, I was happy again.  I don't know why "su" couldn't have been used, but I guess I could make an alias for it, if I really cared.

I never logged in as root in my previous systems, at least not for a decade or so, so I don't miss this at all.

This topic has many branches. I was confused until I tried to su from the terminal and realized I couldn't from Ubuntu install. I didn't know when this ability was stopped. 

This is different than logging in as root from gui.

But as you stated the SUDO docs show using 'sudo -i' works just as well as the su from a terminal.

---

### Post by CharlesA on 2012-02-12
> **VMC said:**
> This topic has many branches. I was confused until I tried to su from the terminal and realized I couldn't from Ubuntu install. I didn't know when this ability was stopped. 

This is different than logging in as root from gui.

But as you stated the SUDO docs show using 'sudo -i' works just as well as the su from a terminal.
Just running su alone doesn't work in Ubuntu because the root account is disabled by default. This is by design - using sudo instead of logging in as root to run admin tasks.

---

### Post by cariboo on 2012-02-13
Su originally (and still does) stood for switch user, which it still does, it gives you the ability to switch to a different user. I haven't tried it lately, but if you have the root account enabled, you should still be able to:

```
su root
```

---

### Post by dcstar on 2012-02-13
Since the (very handy) **nautilus-gksu** extension has been removed in 12.04, anyone wanting a Nautilus session with root privileges can make a Launcher with the following:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```
The **nautilus-open-terminal** plugin is still available, so this functionality is still there in Ubuntu.

---

### Post by VMC on 2012-02-13
> **cariboo907 said:**
> Su originally (and still does) stood for switch user, which it still does, it gives you the ability to switch to a different user. I haven't tried it lately, but if you have the root account enabled, you should still be able to:

```
su root
```

Without a user name it should default to superuser(root).

From man page:
> ...Invoked without a username, su defaults to becoming the superuser..

It doesn't work that way in Precise anymore. I will have to check previous Ubuntu releases to find when it stopped. It works on Mint12.

---

### Post by cariboo on 2012-02-13
> **Vishnu V said:**
> Hi i dont want root to login into GUI, but i have a hidden user account (uid 503) want to login into gui, but on ubuntu 12.04 there is no option to login (Ubuntu 11.10 there is an "Other" option) to do this
Please help

Thanks 
Vishnu

What's the purpose of this account, you want to log into?

---

### Post by cariboo on 2012-02-13
> **VMC said:**
> Without a user name it should default to superuser(root).

From man page:


It doesn't work that way in Precise anymore. I will have to check previous Ubuntu releases to find when it stopped. It works on Mint12.

It hasn't worked that way for the last several releases.

---

### Post by collisionystm on 2012-02-13
if i never need to work as root in terminal I just

sudo bash

---

### Post by Ibidem on 2012-02-13
> **VMC said:**
> Without a user name it should default to superuser(root).

From man page:


It doesn't work that way in Precise anymore. I will have to check previous Ubuntu releases to find when it stopped. It works on Mint12.

Odd. su gets me a root shell (system upgraded from Maverick; root account enabled before upgrade)

---

### Post by Gregory Lee on 2012-02-13
> **Ibidem said:**
> ... root account enabled before upgrade)
Well, I guess that's why.  Not so odd that "su" works.

---

### Post by Bill Gates Foundation on 2012-03-07
the directions in this thread dont work........its just a bunch of people talking about terminal commands and "why do want to have root power?"


ok


your directions are incomplete.......you can change 500 to 0.....you can set the password......



but there is no root at the log in screen.......
:popcorn:

---

### Post by ckasux on 2012-03-12
> **Cookieh said:**
> Recently, I have upgraded my Ubuntu 11.10 to Ubuntu 12.04 Precise Pangolin and I can not find a way on how to login as root. I have tried:

```
sudo passwd root
enter new UNIX pass
```and so on, but I still don't get the other login at the login screen...

Any suggestions?


gksudo

---

### Post by cariboo on 2012-03-12
The op wants to log in to his desktop as root, which you can't do with most distributions these days. Even if it was possible, it is against forum policy to instruct someone on how to do it.

---

### Post by lucazade on 2012-03-12
> **cariboo907 said:**
> The op wants to log in to his desktop as root, which you can't do with most distributions these days. Even if it was possible, it is against forum policy to instruct someone on how to do it.

against forum policy?!? really?
is forbidden like fork bomb commands :D

---

### Post by CharlesA on 2012-03-12
> **lucazade said:**
> against forum policy?!? really?
is forbidden like fork bomb commands :D
You mean like this?

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by lucazade on 2012-03-12
oh.. thanks for pointing this out!

"The goal is to educate new users."
this seems a good motto.. i'll continue to read the rest :)

---

### Post by dcstar on 2012-03-14
> **ronacc said:**
> here is one of the places I use a root session . If I want to search for and open a file as root I can use nautilus to search for the file as and then use "open with" to open it , **if nautilus is invoked with gksudo any child process are not opened as root** requiring you to open a second terminal and open the child process (eg gedit) as root whereas if you are root you are root .

**Wrong**. This will start a root Nautilus session and do things like open a root terminal directly:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

Sudo basically does have the power to do almost anything, and in a much safer way.

---

### Post by giogziro95 on 2012-03-16
> **Cookieh said:**
> Recently, I have upgraded my Ubuntu 11.10 to Ubuntu 12.04 Precise Pangolin and I can not find a way on how to login as root. I have tried:

```
sudo passwd root
enter new UNIX pass
```
and so on, but I still don't get the other login at the login screen...

Any suggestions?

I have no idea why you need to do this. You can use
"sudo <command>" in terminal
or
press Alt+F2 > type "gksudo <program>" & hit enter
or
Alt+f2 > type "gksudo" & hit enter > appears "Run program" dialog and you can run program as any user.

But if you need exactly root session you can do following:
Log out and log in to recovery console (select "recovery console" as session, type password and hit enter :p)
Then run commands:
```

$ sudo su
# gnome-session

```
Wait for a minute and you are done!

Or you can get almost same result by logging in to your user account and running following commands:
```

$ sudo su
# killall nautilus
# unity --replace

```
Good luck! :)

---

### Post by jadonohu on 2012-03-18
> **Cookieh said:**
> Recently, I have upgraded my Ubuntu 11.10 to Ubuntu 12.04 Precise Pangolin and I can not find a way on how to login as root. I have tried:

```
sudo passwd root
enter new UNIX pass
```
and so on, but I still don't get the other login at the login screen...

Any suggestions?
I see this problem as well: there is no "Other" option in the login screen to login as hidden users, not just root.

In my case, I set

> greeter-hide-users=true

in lightdm.conf so no usernames show up in the greeter at all. The user has to choose "Other" and enter their username to login. But the "Other" option is gone.

(Please don't reply, as several have already done on this thread, with "Why do you want to do that?". If you don't know the answer to the question, just say so. The OP's original question was quite clear, and the functionality obviously changed from 11.10.)

---

### Post by cariboo on 2012-03-18
The op of this thread hasn't been back in over a month, so he either found a solution to his problem, or has given up. I think we can safely close this thread now.

---

