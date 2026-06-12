---
title: "Unable to upgrade 9.04 to .910 (server 32-bit)"
date: 2009-11-17
forum: Server Platforms
---

### Post by hankinator on 2009-11-17
I am currently trying to upgrade to my current 9.04 (32-bit) 
Here's a list of the commands to what I did so far.
(I'm logged in as root)
```
apt-get update
```

```
apt-get upgrade
```
(no upgrades)

```
apt-get install update-manager update-manager-core
```

```
apt-get update
```

```
apt-get upgrade
```

```
do-release-upgrade
```

and I get this as an output


```
root@server:/# do-release-upgrade
-bash: do-release-upgrade: command not found

```

I don't know what to do here. Also fyi. The /etc/update-manager/release-upgrades is set to normal so it should at least know there's an update there. 

I searched on google and I wasn't able to find anything, help anyone. :(

---

### Post by hellmet on 2009-11-18
Weird. Have you tried 
"apt-get dist-upgrade" ?

---

### Post by hankinator on 2009-11-24
I have

```
apt-get dist-upgrade
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Still nothing. :(

and /bump

---

### Post by memilanuk on 2009-11-24
Hmmm... just looking at the bits here:

[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

on upgrading the server edition... noticed that everything is done via sudo, vs. being logged in as root (IIRC, the Ubuntu folks frown on that for whatever reason).

I wonder... if perhaps there is a difference in the $PATH between root and the sudo user that is causing 'do-release-upgrade' to not be found?

---

### Post by hankinator on 2009-11-25
I tried all those options, I created a new user and gave him sudo abilities, and still nothing. :( 

I don't understand why it isn't working, that's the problem. Is there anyway I can download and ISO onto the server and install it from there? would that work?

---

### Post by memilanuk on 2009-11-26
Wow.  Thats an odd one, to say the least.

Just to make sure we're not missing anything obvious here, lets try this again from the top:

1)  What do you get for an output of 'lsb_release -a'?

2)  What do you get for an output from 'locate do-release-upgrade'?  (If this is a new system (<24hrs old) you may need to run 'sudo updatedb' to generate the database file that 'locate' uses.)

3)  Are you logged in as the user created during initial install?  Not 'root', not some other user created later?

4)  What do you get when, as that user, you run 'sudo do-release-upgrade'?  Again, make *sure* you are logged in as that user created during initial installation, that is granted sudoer access.  Similarly, what do you get for 'sudo apt-get update && apt-get upgrade && apt-get dist-upgrade'?  If it takes off upgrading on you, and you are *not* ready, either a quick Control-C or wait until it asks for confirmation and answer 'N'o (should be the default anyway).

I don't know for sure, but I have a feeling that you being logged in as 'root' may be part of the problem.  Whether you just have a different $PATH as 'root' than as your regular user (which shouldn't matter, as do-release-upgrade should be under /usr/bin) or if something in the script doesn't like being run by root...

There is a way to upgrade using the Alternate install CD... but I'd be interested in seeing if we can figure out why this isn't working for you in the first place.

Monte

---

### Post by memilanuk on 2009-11-26
> **hankinator said:**
> 
```
apt-get install **[COLOR="Red"]update-manager[/COLOR]** update-manager-core
```


This is just bugging me a bit... did you really do that?  Didn't the question asking you if you wanted to install close to 200MB of stuff tip you off that 'update-manager' is a GUI/desktop program?  I mean, everything *should* work and all, but on a server that part was pretty much un-necessary.

---

### Post by hankinator on 2009-12-02
Okay, well I found out the problem. The company that sold me the server started with 8.10 and upgraded to 9.04 without a restart and handed it over. I went and installed a bunch of packages without a restart and that was bad. Everything was messed up. I thought they did a clean installed of 9.04 rather than upgrading from 8.10. I installed ubuntu 9.04 on virtual-box and I copied over the configs from apt, and it was missing a few repos. When it installed to 9.04 it removed the do-release-upgrade and everything like that. It was weird, I have never seen a upgrade be that buggy and somewhat unsuccessful.

---

### Post by memilanuk on 2009-12-02
I'm not sure how they could have b0rked it like that... I've done a couple 8.04.3 -> 8.10 -> 9.04 -> 9.10 upgrade cycles in Virtualbox without any problems... but lacking any better explanation for how 'do-release-upgrade' went missing... ;)

Thanks for the follow-up report!  You'll probably want to change the topic to [SOLVED]!

Monte

---

### Post by hankinator on 2009-12-02
Yeah, I'm not exactly sure either, every server that I run like that don't have those problems. Honestly, who knows, it could of been a scratched disk to a disk that was burned at a very high speed. Sorry about the delay, I spend the past few week trying to fix it. Thanks for your help.

---

