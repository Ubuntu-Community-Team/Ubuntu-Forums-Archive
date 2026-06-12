---
title: "How do I update Ubuntu packages?"
date: 2012-04-12
forum: Server Platforms
---

### Post by Matsaki on 2012-04-12
Hi,
I just got a Ubuntu 10.04.3 LTS running on my dedicated server. I'm some what new to Ubuntu and not very familiar with Unix language.

I do a cat /etc/issue and I get:

> 39 packages can be updated.
29 updates are security updates.

I know I will run > $ sudo apt-get update and then > $ sudo apt-get upgrade upgrade but I have a vague memory that something else has to be done after that? Do I have to reboot?

How will I run this updates? And is this updates including the essentials of a server such as MySQL, Apache etc.? Is there a list where I can see what applications is updated automatically, so I see what's not?

Thanks!

---

### Post by kc1di on 2012-04-12
can't answer all your question but the normal update method would be in terminal ```
sudo apt-get update
``` then issue this command ```
sudo apt-get upgrade
``` Since your running a server I'm not sure you have access to a GUI but if you do go to synaptic and refresh then click mark all upgrades it will give you a list of files that are going to be updated. 

Cheers

---

### Post by Matsaki on 2012-04-12
Thanks for the reply kc1di.

So I don't have to reboot after the update? Will it tell me if I have to?

I't very important if I could find where to read what this updates includes so I don't miss anything important such as MySQL, Apache etc. :(

---

### Post by kc1di on 2012-04-12
> **Matsaki said:**
> Thanks for the reply kc1di.

So I don't have to reboot after the update? Will it tell me if I have to?

I't very important if I could find where to read what this updates includes so I don't miss anything important such as MySQL, Apache etc. :(

it will tell you if a reboot is needed. It will only update security patches and packages that are needed for dependencies of those packages.
so you should not have to worry about it messing up your MySQL.
if you need newer packages for MySQL you would have to install it separately. unless there is a security patch for it then it will be updated.

good Luck

---

### Post by Matsaki on 2012-04-12
Aha I see. Do I have to manually keep track on MySQL, Apache, PHP and all the essentials for a server. Or is there a easier way?

(I know this newbie questions is a pain in the a**, but one must start somewhere :) )

---

### Post by kc1di on 2012-04-12
> **Matsaki said:**
> Aha I see. Do I have to manually keep track on MySQL, Apache, PHP and all the essentials for a server. Or is there a easier way?

(I know this newbie questions is a pain in the a**, but one must start somewhere :) )

unfortunately 10.04 is due to come to end of life in October after which they will not continue to update it. here is a page with details the different releases. [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")
To answer your question if their are significant updates you will have to find them or upgrade to the next version of ubuntu. However with a server for other than security purposes if it's working and able to do the task you require them to do you don't really have to update them.

---

### Post by snowpine on 2012-04-12
> **kc1di said:**
> unfortunately 10.04 is due to come to end of life in October after which they will not continue to update it. here is a page with details the different releases. [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

No, no, no... Ubuntu Server 10.04 will be supported through April 2015.

To the OP: Your update strategy looks good, unless you want kernel updates. For those you should use:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and you'll need to reboot. 

Updates to 10.04 will never include major version updates to Apache, PHP, MySQL, etc. so they won't break your site. But you will get security patches to fix any vulnerabilities. :)

---

### Post by Matsaki on 2012-04-12
Wow you really scared me there for a while there kc1di :)

So how often should one do the "dist-upgrade"? Or how shall I know when it's time to do that?

My Ubuntu was installed in February so it should be somewhat updated. But I'm more concerned how to keep up with security patches/updates for MySQL, Apache etc. :-?

---

### Post by arrrghhh on 2012-04-12
> **Matsaki said:**
> Wow you really scared me there for a while there kc1di :)

So how often should one do the "dist-upgrade"? Or how shall I know when it's time to do that?

My Ubuntu was installed in February so it should be somewhat updated. But I'm more concerned how to keep up with security patches/updates for MySQL, Apache etc. :-?

Now I'm confused, I thought kernel updates would come thru with apt-get upgrade...

dist-upgrade is to go to a new distribution, no?  A new release?

OP, I think your sudo apt-get update && sudo apt-get upgrade are just fine ;).  You'll get kernel updates if they're available thru the upgrade command.  dist-upgrade and do-release-upgrade are for going to the next release - for example 12.04 :).

I found this post on another forum, it explains the concept well I think:

> Hi,

From the man-page:

"upgrade is used to install the newest versions of all packages currently installed on the system
...
dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages"

Quote:
I only want currently installed packages to be updated and packages improving the reliablilty/stability of the OS to be installed.
Dist-upgrade will not go and install every package under the sun.

Quote:
Which one should I use?
Well, if you want to do a distro-upgrade, use dist-upgrade. For instance, moving from Debian -stable to Debian -testing. Dist-upgrade is a special upgrade that is used if you are fetching packages from a new location, which is specified in /etc/apt/sources.list

If you want to simply upgrade the packages you have installed for your current distro, use 'apt-get upgrade'.

I hope that clears up your confusion.

---

### Post by kc1di on 2012-04-12
> **snowpine said:**
> No, no, no... Ubuntu Server 10.04 will be supported through April 2015.

To the OP: Your update strategy looks good, unless you want kernel updates. For those you should use:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and you'll need to reboot. 

Updates to 10.04 will never include major version updates to Apache, PHP, MySQL, etc. so they won't break your site. But you will get security patches to fix any vulnerabilities. :)
Thanks for the clarification I had forgotten the server was supported longer.

---

### Post by snowpine on 2012-04-12
> **Matsaki said:**
> So how often should one do the "dist-upgrade"? Or how shall I know when it's time to do that?

My Ubuntu was installed in February so it should be somewhat updated. But I'm more concerned how to keep up with security patches/updates for MySQL, Apache etc. :-?

I only ever use "dist-upgrade" personally.
The only situation I can think to use "upgrade" would be if you don't plan to reboot (like a server with 100% uptime).

Either "dist-upgrade" or "upgrade" will work if your primary goal is to keep MySQL, Apache, etc. secure.

Since you are getting conflicting advice :) I recommend to read "man apt-get" and to use the -s flag, which will "simulate" the upgrade so that you can see for yourself exactly what each command does without actually upgrading.

```
sudo apt-get update
sudo apt-get -s upgrade
sudo apt-get -s dist-upgrade
```

---

### Post by arrrghhh on 2012-04-12
> **kc1di said:**
> Thanks for the clarification I had forgotten the server was supported longer.

Even Desktop is supported until April 2013 ;).

> **snowpine said:**
> I only ever use "dist-upgrade" personally.
The only situation I can think to use "upgrade" would be if you don't plan to reboot (like a server with 100% uptime).

Either "dist-upgrade" or "upgrade" will work if your primary goal is to keep MySQL, Apache, etc. secure.

Since you are getting conflicting advice :) I recommend to read "man apt-get" and to use the -s flag, which will "simulate" the upgrade so that you can see for yourself exactly what each command does without actually upgrading.

```
sudo apt-get update
sudo apt-get -s upgrade
sudo apt-get -s dist-upgrade
```

Hrm.  I may be misreading the man page... Now I'm still confused about how dist-upgrade works, but -s is always a good tip ;)

As for the difference, it seems dist-upgrade under Ubuntu isn't necessarily for going to the next distribution :confused:.

> dist-upgrade:
dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. So, dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

I find it interesting that dist-upgrade changes dependencies, while upgrade does not...

> upgrade:
upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be performed first so that apt-get knows that new versions of packages are available.

I think I will stick with upgrade, it seems safer IMHO!

---

### Post by snowpine on 2012-04-12
"apt-get upgrade" is roughly equivalent to "aptitude safe-upgrade"
and "apt-get dist-upgrade" is roughly equivalent to "aptitude full-upgrade"

Confusing, I know. :)

---

### Post by arrrghhh on 2012-04-12
Matsaki - sorry for muddying your thread with this confusing conversation...

Long story short, both methods (upgrade/dist-upgrade) you will get kernel updates, do not fear about that.  I'll let you read more and make your own informed decision about whether to use dist-upgrade or simply upgrade ;).

---

