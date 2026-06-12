---
title: "Root Password for the server edition"
date: 2006-09-27
forum: Server Platforms
---

### Post by mattsites on 2006-09-27
I am trying out the Ubuntu server edition. I come from openSuSE were if you want to run a command under root you would su into root, having already set the root password in the installation. What is the password for the root account? ](*,) 

Thanks!

---

### Post by mitch.c on 2006-09-27
> **mattsites said:**
> I am trying out the Ubuntu server edition. I come from openSuSE were if you want to run a command under root you would su into root, having already set the root password in the installation. What is the password for the root account? ](*,) 

Thanks!

Ubuntu comes with root account disabled be default. During installation you create a user account that is automatically added to the admin group. Then use sudo to run commands that require root access using your password. If you want to temporarily access a shell as root try:
```
sudo -i
```

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info.

---

### Post by IanR on 2007-03-01
Found this old thread in Google, and at least it answered why I had to use brute-force methods to shutdown my ubuntu server instead of the standard unix commands.  

IMHO this is not a good situation as it will prevent servers being shutdown properly. Engineers doing maintenance cannot be expected to know that this distro requires a special  procedure, or to figure-out WHY the root logon doesn't work, perhaps when only limited time is available before a poweroff.. They will assume a fault and yank the plug.

In general, first impressions are that this is a  nice server distro, but I do think you need to properly consider the  effects of a change like this. If the inability to run the shutdown command results in disk-corruption,  that ain't security!

---

### Post by MJN on 2007-03-01
If an engineer didn't have the authority, knowledge and experience to know how to shut a Ubuntu machine down then I wouldn't let them in the same room as one of my servers.

Mathew

---

### Post by imagine on 2007-03-01
Each time an user of the admin group logs in, the following text appears as long as this user hasn't run sudo successfully as least once:
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
And it's not like "sudo" would be new or invented by Ubuntu, in fact it's older than Linux itself.

---

### Post by hortimech on 2007-03-04
I tend to agree that on a server you need to logon as root, so when I load the server edition, I press F6 and change to expert installation, yes, you have to answer a lot more questions but you do get asked if you want to allow root logins.

This should be a user decision, not something forced onto the user, I actually think for Ubuntu, Kubuntu desktop users it is a good thing, IF IT WAS EXPLAINED WHY correctly, just not for servers, but that is my decision and before you try and change my mind, I WILL NOT! so do not waste your time trying :)

---

### Post by jtc on 2007-03-04
It is also possible to enable your root account if you feel you need it.

```
sudo passwd root
```

---

### Post by Highway on 2007-05-30
You don't need to switch to expert mode and answer a lot more questions during installation, if all you want to do is have a working root account.
Install as normal, and when installed, log in as the user you setup and type:
sudo passwd root
<enter the user password>
<enter new password for root>
<reenter new password for root>

Now, login as root and newpassword, and vi the /etc/group file, and remove your original user account from the admin group.  

You now have a working root account like other distros.  Note, it's recommended you secure it from ssh logins, etc, and just su to root when needed.

I agree with you that i am not convinced about the way ubuntu handles the root account.  
A user is typically not very protective of their own logins, and if someone got the users password, then they end up with full root access.  How can this be considered secure.  
They could just set a root password themselves, and then make the machine useless.  I've not seen any convincing argument for doing it the way ubuntu does by default.  

Highway.

---

### Post by dfreer on 2007-05-30
> **hortimech said:**
> I tend to agree that on a server you need to logon as root, so when I load the server edition, I press F6 and change to expert installation, yes, you have to answer a lot more questions but you do get asked if you want to allow root logins.

This should be a user decision, not something forced onto the user, I actually think for Ubuntu, Kubuntu desktop users it is a good thing, IF IT WAS EXPLAINED WHY correctly, just not for servers, but that is my decision and before you try and change my mind, I WILL NOT! so do not waste your time trying :)

Really though, if you don't like this behaviour go to debian. a debian server is pretty much exactly the same as an ubuntu server only sudo isn't setup by default. And I'm pretty sure the ubuntu website and any other ubuntu help site, including this forum, has covered the fact that ubuntu uses sudo by default, why it uses it by default, and the easy way to turn it off. It doesn't need to reinstate the obvious during install time, especially when it will just confuse the new windows users.

> **IanR said:**
> Found this old thread in Google, and at least it answered why I had to use brute-force methods to shutdown my ubuntu server instead of the standard unix commands.  

IMHO this is not a good situation as it will prevent servers being shutdown properly. Engineers doing maintenance cannot be expected to know that this distro requires a special  procedure, or to figure-out WHY the root logon doesn't work, perhaps when only limited time is available before a poweroff.. They will assume a fault and yank the plug.

In general, first impressions are that this is a  nice server distro, but I do think you need to properly consider the  effects of a change like this. If the inability to run the shutdown command results in disk-corruption,  that ain't security!

sudo shutdown -r now

Engineers doing maintenance SHOULD be expected to know their job or they SHOULDN'T be allowed to touch anything. This isn't something completely out of the ordinary, like imagine stated. This is why there are different distros, because each one does things differently. If you don't like the behaviour of one, simply change to one you do like. Not that hard.

---

### Post by blainemiller on 2008-01-19
Hi!

Just loaded 7.10 server edition for 1st time. Trying to set root via sudo as per normal Ubuntu/Debian.

I keep getting reported as _UID_ is not in the sudoers file. You will be reported...

This is getting pretty tedious. I have tried sudo'ing till I'm blue-ing in the face.

Just a finicky install? Scrub and load again? I've not run into this before. I've loaded and run W/S since 5.x and not had a problem with sudo and the macharena dance that Ubuntu/Debian makes one go thru for _real_ root.

It's a catch-22 of biblical proportions! Calling all non-judgmental Ubuntu experts! Which way do I hold my head or what language do I do the voodoo dance in?

Thanks!

Blaine

---

### Post by MJN on 2008-01-19
> **blainemiller said:**
> Calling all non-judgmental Ubuntu experts!

Damn... and I know the answer too!

Mathew

---

### Post by fcigoi on 2008-01-19
Good for you....spit it out then, as I'm having the exact same issue

---

### Post by blainemiller on 2008-01-19
> **MJN said:**
> Damn... and I know the answer too!

Mathew

_Information is not power... access to information is power._ Please elucidate, oh Enlightened One!

Thanks!

---

### Post by blainemiller on 2008-01-19
> **MJN said:**
> Damn... and I know the answer too!

Mathew

Oh, and BTW, if your response contains _ sudo passwd root _, guess again!

I think I'm gonna blow this install off and use OpenSolaris X, a _real_ *nix! (smile)

bm, Mark of Excellence

---

### Post by khansen46 on 2008-01-23
Unfortunately, this type of attitude is exactly why Linux has not caught on as quickly as it could. MS is losing customers left and right because of their **use what we give you the way WE want you to use it** attitude. This is especially evident in the Vista release. Our company will never move to Vista because of some of the feature changes, and the typical MS unwillingness to admit they did something the market doesn't like or want.

This attitude is becoming more and more common in Linux circles. Every time someone wants to find out why they can't log in as root, they are immediately told "**You're not supposed to log in as root. Do it this way...**". Don't expect the whole world to change their business model or practices for the privilege of using your distro. Linux should be easily adaptable to the needs and desires of both businesses and individuals. *I* will decide how to run my business, and *I* will not tell *you* how to run yours. 

I'm on this thread because I had the same problem. I'm not new to the field, but am still a bit green in Linux. I've been using Xandros Server, but am not willing to pay the price ($$) in order to keep up with current versions. I've heard a lot about Ubuntu, and decided to give it a try. After not finding a way to log in as root, and the system not letting me su, su root, or sudo, I wiped it and installed Debian.

Too bad. I really wanted to try out Ubuntu server...

> **dfreer said:**
> Really though, if you don't like this behaviour go to debian. a debian server is pretty much exactly the same as an ubuntu server only sudo isn't setup by default. And I'm pretty sure the ubuntu website and any other ubuntu help site, including this forum, has covered the fact that ubuntu uses sudo by default, why it uses it by default, and the easy way to turn it off. It doesn't need to reinstate the obvious during install time, especially when it will just confuse the new windows users.



sudo shutdown -r now

Engineers doing maintenance SHOULD be expected to know their job or they SHOULDN'T be allowed to touch anything. This isn't something completely out of the ordinary, like imagine stated. This is why there are different distros, because each one does things differently. If you don't like the behaviour of one, simply change to one you do like. Not that hard.

---

### Post by MJN on 2008-01-23
> **khansen46 said:**
> After not finding a way to log in as root, and the system not letting me su, su root, or sudo, I wiped it and installed Debian.

Did you post on the forum requesting help? I'm sure someone could have solved your issue for you.

Shame to see you 'go', but if you're happy now that's all that matters.

Mathew

---

### Post by khansen46 on 2008-01-25
I haven't given up on Ubuntu completely. I plan to install the desktop on a 64-bit laptop I have and play around with it. And yes, I will make sure root is accessible and can log in.

As for the last issue, I had a web site I needed to get up. I didn't have time to deal with more of the "you shouldn't do it that way" attitude that seems to run through the Linux forums - all of them, not just this one.

My point in posting is simply this: People don't want to be told HOW to do something. I've been in the industry for quite a while, and am currently in security. I understand the risk of logging in as root, but I am also pretty well versed in proper procedures and controls. I think it should by MY choice whether or not I can use this account. I don't need someone else trying to protect me from myself. 
This was further compounded by the fact that the server did not install KDE or GNOME, and wouldn't allow me to do it afterward. I'm not a Linux engineer, and am not yet able to totally administer a Linux machine via command line - besides the fact that I wouldn't be able to administer it without access to root privileges anyway.

For what it's worth, here are my 2 suggestions that I think would make the vast majority happy:
1) ASK if the root user should be active and able to log in
2) ASK if the GUI should be installed

I'll play around with it a little more later and figure out how to unlock root.

---

### Post by MJN on 2008-01-25
That's good. If you need any specific help just shout.

Mathew

---

### Post by liverpoolatnight on 2008-05-06
> **jtc said:**
> It is also possible to enable your root account if you feel you need it.

```
sudo passwd root
```

would that work on 8.04 ?

---

### Post by Joeb454 on 2008-05-06
Why would you need to enable the root account? I prefer just typing ```
sudo -i
``` If I want to have a root terminal for a while

---

### Post by dfreer on 2008-05-07
```
sudo passwd root
```
Enter your current user password to get past sudo, then enter the new password you want for root twice.

ZOMG! Ubuntu now has a root account! 

> **khansen46 said:**
> Unfortunately, this type of attitude is exactly why Linux has not caught on as quickly as it could. MS is losing customers left and right because of their **use what we give you the way WE want you to use it** attitude. This is especially evident in the Vista release. Our company will never move to Vista because of some of the feature changes, and the typical MS unwillingness to admit they did something the market doesn't like or want.

Wow, yet another "I can't get this to work OMG this is why linux isn't ready for the desktop post". I can't even read that without gagging a little.

> **khansen46 said:**
> This attitude is becoming more and more common in Linux circles. Every time someone wants to find out why they can't log in as root, they are immediately told "**You're not supposed to log in as root. Do it this way...**".

It's true that response is common here in ubuntu, that's because there is a much of people parroting things without actually knowing what they are talking about. The whole point of disabling the root account is:
(1) Ubuntu is geared to the desktop, and there's absolutely no reason that firefox needs to be run with root privileges on a day-to-day basis. It's a security risk. It doesn't PREVENT you from running as root if you so desire, it just makes it not-default. Same as having no ports open by default.
(2) If a novice (hint: novice) user accidently types a command wrong as root he could totally fsk up the system. The experienced user can use root all year long if they so choose simply by typing one command. How hard is that?

It's not **permanently disabled**, nor are you inviting satan lord of lies to reside in your PC simply by turning on the root account. It's just a default behavior for linus's sake!

> **khansen46 said:**
> Don't expect the whole world to change their business model or practices for the privilege of using your distro.

Don't expect us to change ubuntu simply because your company grew up using Red Hat/whatever and can't figure out how to type sudo or google "enable the root account ubuntu". Seriously, you are not the whole world no matter what you think.

> **khansen46 said:**
> Linux should be easily adaptable to the needs and desires of both businesses and individuals. ***I* will decide how to run my business, and *I* will not tell *you* how to run yours.**
> **khansen46 said:**
> For what it's worth, here are my 2 suggestions that I think would make the vast majority happy:
1) ASK if the root user should be active and able to log in
2) ASK if the GUI should be installed

Hypocritical much? IT is easily adaptable, just type that command in and poof! magical root access. How hard is it really?

> **khansen46 said:**
> This was further compounded by the fact that the server did not install KDE or GNOME, and wouldn't allow me to do it afterward. I'm not a Linux engineer, and am not yet able to totally administer a Linux machine via command line - besides the fact that I wouldn't be able to administer it without access to root privileges anyway.

If you wanted KDE or GNOME Desktops installed beforehand, you should install the "Desktop" version of ubuntu, and install your apache/DNS/whatever stuff after.
If you wanted KDE or GNOME Desktops installed afterwards, all you had to do was install it:
```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
```
Yet another answer solved by 2 seconds of googling. BTW, here's a hint: most admins like having headless servers, gnome and X11 simply tie down resources. 

> **khansen46 said:**
> People don't want to be told HOW to do something. I've been in the industry for quite a while, and am currently in security. I understand the risk of logging in as root, but I am also pretty well versed in proper procedures and controls. I think it should by MY choice whether or not I can use this account. I don't need someone else trying to protect me from myself.

People don't want to be told how to do something, yet you want us to tell you how to enable the root account?

IT. IS. YOUR. CHOICE. WHETHER. YOU. WANT. TO. HAVE. ROOT. ACCESS. OR. NOT. *banging head against the wall* Even though you don't want the OS to provide proper safeguards as defaults, you would surely raise holy crusade against Ubuntu if we installed telnet/ssh by default with no security, or remote desktop enabled with the password "password" wouldn't you? Yes, you would.


> **blainemiller said:**
> Oh, and BTW, if your response contains _ sudo passwd root _, guess again!

I think I'm gonna blow this install off and use OpenSolaris X, a _real_ *nix! (smile)

bm, Mark of Excellence
That IS my response, and thanks for trolling!

---

