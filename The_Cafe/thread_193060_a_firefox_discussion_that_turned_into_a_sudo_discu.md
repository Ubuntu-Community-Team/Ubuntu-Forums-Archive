---
title: "a firefox discussion that turned into a sudo discussion"
date: 2006-06-08
forum: The Cafe
---

### Post by jgcamp99 on 2006-06-08
aysiu, if that makes you happy, then by all means do it that way. Let me ask you how you would copy a file that the root or administrator is the only one that has the rights to copy and paste a file to in a specific directory ? There's a method to my madness for re-enabling root for logins. It's easier to install Citrix for one, it's also easier to do a manual install of Macromedia's Flashplayer 7 for Firefox after it fails to do it under sudo, like one fellow has found out the hard way.

[http://www.ubuntuforums.org/showthread.php?t=192592](http://www.ubuntuforums.org/showthread.php?t=192592)

In my world, I am root, an administrator. Not a sudo root/administrator ! ;)

---

### Post by aysiu on 2006-06-09
I followed that link, and it has nothing to do with *sudo* not letting one install Flash manually. Please re-read the post.

There's not a single thing that logging as root lets you modify that using *sudo* or *gksudo* doesn't.

> Mine, you learn a little more about Linux, even understand the OS better as root/administrator. I don't see how logging in as root makes you understand Ubuntu or Linux better. You clearly don't understand the difference between root and *sudo* yourself.

---

### Post by jgcamp99 on 2006-06-09
"You clearly don't understand the difference between root and sudo yourself."

Yeah I do, or enough about it to know I'd rather be root any day of the week for exactly the reason Rondonjin indicated. Prior to Ubuntu, I had always been root and learned Linux, more command line stuff that way. I tried sudo, got denied, I was frustrated that I couldn't copy two lousy plugin files to /usr/lib/firefox/plugins in the file browser when the sudo attempt to run the installer to install flashplayer 7 failed. So I allowed myself to be root and log into gnome and I am able to copy a file and put it anywhere my heart desires without having to preface everything I do with a terminal command telling Ubuntu I want to have root/administrator privileges. I tell the computer what I want to do, not ask it everytime I want to install something. I'm the master and it does what I tell it to do, not vice versa.

Rondonjin, go back to the old ways and things will start to work. I haven't had a single failure/issue doing it the tried and true ways. Sudo is designed to limit what can be installed, root does that same function, only under another user & password. If you understand how to make it work, use that method. Trust me, Sudo ways will still work for Ubuntu sudo user. I re-enabled root, and then made sure my sudo user was a member of the root's administrator group. I, like you want things to work immediately, I have no time for failed attempts. Sudo works for some people, I do it the other way. I bear no ill will towards others for sudo, but if you know how to do it as root, why fight sudo because like you say, it's not working for you !

---

### Post by aysiu on 2006-06-09
You don't really understand sudo if you think it can't install things to /usr/lib/firefox/plugins.

> I tried sudo, got denied, I was frustrated that I couldn't copy two lousy plugin files to /usr/lib/firefox/plugins in the file browser when the sudo attempt to run the installer to install flashplayer 7 failed. Did you ever consider that maybe you weren't using *sudo* correctly? ```
username@ubuntu:~$ **cd Desktop**
username@ubuntu:~/Desktop$ **ls**
install_flash_player_7_linux.tar.gz
username@ubuntu:~/Desktop$ **tar -zxvf install_flash_player_7_linux.tar.gz**
install_flash_player_7_linux/
install_flash_player_7_linux/flashplayer.xpt
install_flash_player_7_linux/flashplayer-installer
install_flash_player_7_linux/libflashplayer.so
install_flash_player_7_linux/Readme.htm
install_flash_player_7_linux/Readme.txt
username@ubuntu:~/Desktop$ cd install_flash_player_7_linux
username@ubuntu:~/Desktop/install_flash_player_7_linux$ **ls**
flashplayer-installer  libflashplayer.so  Readme.txt
flashplayer.xpt        Readme.htm
username@ubuntu:~/Desktop/install_flash_player_7_linux$ **sudo ./flashplayer-installer**

Copyright(C) 2002-2003 Macromedia, Inc.  All rights reserved.

Macromedia Flash Player 7 for Linux

Macromedia Flash Player 7 will be installed on this machine.

You are running the Macromedia Flash Player installer as the "root" user.
Macromedia Flash Player 7 will be installed system-wide.

Support is available at http://www.macromedia.com/support/flashplayer/

To install Macromedia Flash Player 7 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Macromedia Flash Player requires two font packages
      to be installed, gsfonts and gsfonts-x11.

Press ENTER to continue...



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): **/usr/lib/firefox**


----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): **y**


Installation complete.


Perform another installation? (y/n): **n**


Please log out of this session and log in for the changes to take effect.


The Macromedia Flash Player installation is complete.

username@ubuntu:~/Desktop/install_flash_player_7_linux$ **cd /usr/lib/firefox/plugins** 
username@ubuntu:/usr/lib/firefox/plugins$ **ls**
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.so
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libunixprintplugin.so   mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in.so
username@ubuntu:/usr/lib/firefox/plugins$
``` I just ran that on my test machine using only *one* sudo command, and I didn't get any errors or denial of permissions.

If you want to use root because you're **more comfortable** with it, that's fine, but don't claim *sudo* is incapable of things it is capable of.

> I tell the computer what I want to do, not ask it everytime I want to install something. I'm the master and it does what I tell it to do, not vice versa. I don't see how using *sudo* makes the computer "the master" of you.

Do you have a special ATM card that doesn't require a password because you want to be the master of your bank account and not have the bank account be the master of you? Maybe you don't have a lock on your apartment or house door, either.

---

### Post by jgcamp99 on 2006-06-09
"Did you ever consider that maybe you weren't using sudo correctly?"

I said that already, I didn't have the time to teach an old dog new tricks (myself that is). I did the sudo thing a few times and got the same wonderful confirmation of an installation. Even went so far as to reboot the system. Everytime I went to that same web page that required the plugin, it told me to download it and install it. I did it my way, it worked the first time/only time and since it worked for me, I have no use to piddle around with sudo, when I found re-enabling root to work easy enough and I know what I'm doing somewhat with that methodology. Again, I don't need to tell the computer to sudo anything, under root, I just do it, no sudo terminal command, I enter the password once and I'm the root administrator. Free to be the master of all things root ! I don't like typing my password in a bazillion times when test driving an OS or setting it up. Maybe I set root up and then disable it again.

---

### Post by aysiu on 2006-06-09
Okay. We're agreed then.

You didn't have time to learn *sudo*, and you prefer to log in as root.

I guess all that stuff about *sudo* being the master of you basically just means, "I don't understand *sudo*, and I don't have time to learn it, either."

---

### Post by jgcamp99 on 2006-06-09
"I guess all that stuff about sudo being the master of you basically just means, "I don't understand sudo, and I don't have time to learn it, either.""

Again, the purpose of sudo is to keep you or another from having total control without having to sudo something, with the level of control that root has ! I understand sudo, I want more power. I go to be the source user root when I want that power, I don't "sudo this and sudo that" to be able to do what I want to any Linux system. 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ubuntu sells the idea of sudo and even forces your hand on it by setting it up that way.

See what that sudo method does, it leaves you a 15 minute window of opportunity to get the job done. I don't know of anyone that has installed all the applications and set up Ubuntu in 15 minutes with the single live cdrom. Downloading the applications takes that long in and of itself and then learning how to get all these applications that aren't listed by Ubuntu takes time to master an install. How many times do you want to run something only to find out sudo has closed the door on getting it done. I did that once or twice and then found that Ubuntu Wiki and now I have no problems with Sudo. This forum is littered with sudo related problems and half these people don't even know that they sudo'ed something, went beyond 15 minutes to install it and they are screwed because they didn't reissue the sudo terminal commands, the "can't install this or can't install that", leads to threads that bash Ubuntu and it's really a slick and remarkable OS. I have yet to post a single "I can't install this program" thread yet. I was about to when I wasted several hours trying to get Citrix to install using sudo methodology. It took me a few minutes as root. This wiki is invaluable. And like I said, when I get Ubuntu the way I like it, big deal, so I go back and disable root and put Ubuntu back into it's original state with a click of a box in gnome.

So yes, sudo is my master, it's your's too. you are limited by sudo.

"Downsides of using sudo
Although for desktops the benefits of using sudo are great, there are possible issues which need to be noted: 

Redirecting the output of commands run with sudo can catch new users out. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents. 

In a lot of office environments the ONLY local user on a system is root. All other users are imported using NSS techniques such as nss-ldap. To setup a workstation, or fix it, in the case of a network failure where nss-ldap is broken, root is required. This tends to leave the system unusable unless cracked. An extra local user, or an enabled root password is needed here."

Most of us are the only users of our computer, so root is a nice feature to have enabled. With that wiki, do what you need as root and then go back to Ubuntu sudo default. But why would you want to put yourself on the clock when you are learning Linux. That's gotta be the dumbest thought process, to say to a newbie, "you have 15 minutes to master this with no manual" ? A lot can go wrong on an application installation, there can be corrupt file downloads and so on. Sudo's 15 minute window is counter to allowing anyone the time to do/learn what they want at their own pace.

---

### Post by jgcamp99 on 2006-06-09
Stereotypical Rage, I don't have to worry any more whether sudo works or not. Whether I type in the right command or syntax. I log in as root and use the password, done and complete. My argument against sudo includes how has Ubuntu configured it ? What do I need to type in to be able to use it properly, because there is that one case and you know it always happens the 1/2 % that the exception applies and you wind up wasting days and that's if you ever get it to work.

"Enabling the root account
To enable the root account (i.e. set a password) use: 

sudo passwd root
Enter your existing password
Enter password for root
Confirm password for root"

"In Gnome
Open System --> Administration --> Login Screen Setup 

Click on the security tab 

Check Allow root login"

as far as I can tell, enabling the root password allows me to set the password to something I know for myself as the password, not what Ubuntu set it at. After that root still is not allowed to log in graphically, that is not until you perform the second aspect of the re-enabling of root. So how much more difficult is it to do it this way as opposed to sudo this and sudo that everytime system maintenance needs to be performed ?

All these arguments for security for sudo, what if a hacker gets your sudo account, they can do all this with sudo and reenable root just the same. Brute force to hack is brute force, it's time consuming, root and it's password enabled or disabled exists in Ubuntu regardless of whether root is re-enabled or not. Don't believe me, install Ubuntu and go thru the user accounts. even look at it in gnome, it's simply greyed out/disabled, but it is there.

---

### Post by aysiu on 2006-06-09
[QUOTE=jgcamp99]How many times do you want to run something only to find out sudo has closed the door on getting it done.[/QUOTE] Never. Once again, instead of just saying, "I don't understand sudo, and I prefer to use root because I don't have time to understand sudo," you decide to spread mistruths about sudo.

If you don't understand it, don't talk about it.

sudo doesn't close the door on anything getting done. I've issues commands that take well over an hour to accomplish (say--dist-upgrading from Breezy to Dapper), and I've not been prompted again to type *sudo* or enter my password again.

If you're in the middle of a command executed with sudo, you will be able to finish that task regardless of how long it takes.

And you will always have to enter sudo for every separate command, regardless of whether it's been one minute or fifteen minutes. The fifteen minute time limit is for when you need to re-enter your *password.*

Stop digging yourself into a hole and just admit you use root because you're comfortable with it. sudo is perfectly fine to use if you take the time to get to know it.

[quote=mannheim]Yes, 1.5.0.4 has closed a few security weaknesses; but how many ubuntu users have had their machines compromised by those weaknesses in the past week on account of staying with 1.5.0.3? I would guess zero. In my own case, I would reckon I am much more likely to compromise my machine by running firefox as root.[/quote] But if you run Firefox as root only to get the security updates from Mozilla, what risk is there, unless the security hole being patched is some remote code execution that happens when you try to update...

I like to take the approach of being on the safe side. Probably if you're using 1.0.3 on Ubuntu you won't be compromised in all likelihood. In fact, even on Windows, I haven't seen anyone's computer get compromised using Firefox, but do you really want to wait until your computer gets compromised to say, "Geez, I should have upgraded my Firefox"?

---

### Post by matthew on 2006-06-09
I pulled these posts out of the original thread as it began to get off topic. Please feel free to continue your discussion of the merits of sudo vs enabling root here if you want to do so.

Original thread link: [http://ubuntuforums.org/showthread.php?p=1115157](http://ubuntuforums.org/showthread.php?p=1115157)

---

### Post by jgcamp99 on 2006-06-09
"Never. Once again, instead of just saying, "I don't understand sudo, and I prefer to use root because I don't have time to understand sudo," you decide to spread mistruths about sudo.

If you don't understand it, don't talk about it.

sudo doesn't close the door on anything getting done. I've issues commands that take well over an hour to accomplish (say--dist-upgrading from Breezy to Dapper), and I've not been prompted again to type sudo or enter my password again.

If you're in the middle of a command executed with sudo, you will be able to finish that task regardless of how long it takes.

And you will always have to enter sudo for every separate command, regardless of whether it's been one minute or fifteen minutes. The fifteen minute time limit is for when you need to re-enter your password."

That's one of my points, why should I re-enter my password every fifteen minutes during maintenance or upgrades ? Even when setting Ubuntu up for the first time. So you say I'm spreading mistruths, yet you validate that every fifteen minutes the password has to be re-entered. Furthermore, you tell me that for every separate command you tell me I have to issue a sudo terminal command. So where are my mistruths ? I told you on several occasions this was what I was trying to avoid. You told me I didn't understand sudo, I told you clearly I did and what the reasons for me going in as root was in circumventing, security and limitations of sudo. You continue to post to the effect proving exactly what I said to be true. A sudo for this and that, who has time to redundantly type in sudo terminal commands ? Sudo commands are the equivalent of telling a child over and over again that you want to install or upgrade something new/else. Why not re-enable root, setup the computer the way you want and then disable root using the wiki. You'll save yourself a lot of sudo retypes.

---

