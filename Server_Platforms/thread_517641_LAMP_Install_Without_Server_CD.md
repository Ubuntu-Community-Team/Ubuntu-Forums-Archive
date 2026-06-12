---
title: "LAMP Install Without Server CD"
date: 2007-08-04
forum: Server Platforms
---

### Post by Noah0504 on 2007-08-04
I have an older computer that I guess doesn't like the kernel that the Ubuntu server CD tries to install.  After the GRUB menu, it just reboots.  I was wondering how to go about a LAMP install with just installing Ubuntu 6.06 from an alternate install CD.

---

### Post by bodhi.zazen on 2007-08-05
Just install AMP. You can user synaptic or the command line if you prefer ...

---

### Post by koenn on 2007-08-05
> **Noah0504 said:**
>   I was wondering how to go about a LAMP install with just installing Ubuntu 6.06 from an alternate install CD.
If you do this, select "Advanced" (or is it "expert") mode when you install (F6 before you boot the installer). It will allow you to skip the "select and install packages" step. In normal mode, this step is executed without asking for confirmation, and will install a complete ubuntu-desktop (GUI + all standard desktop apps). You may not want that on a LAMP server. 
You may have to manually install metapackages such as ubuntu-minimal afterwards - I'm not sure; I usually add software as I need it in stead of relying on ubuntu meta-packages.

---

### Post by ruibernardo on 2007-08-05
Like koen said, install the ubuntu-minimal package afterwards. It will install a minimal command line linux.

Then, to install Lamp as a metapakage use tasksel (also found in Synaptic, on the Edit menu. I think it works from the console too without Gnome):

```
user@ubuntu-desktop:~$ tasksel --list-tasks
u dns-server    DNS server
u edubuntu-server       Edubuntu server
u lamp-server   LAMP server
u edubuntu-desktop      Edubuntu desktop
u kubuntu-desktop       Kubuntu desktop
i ubuntu-desktop        Ubuntu desktop
u xubuntu-desktop       Xubuntu desktop
u edubuntu-live Edubuntu live CD
u kubuntu-live  Kubuntu live CD
u ubuntu-live   Ubuntu live CD
u xubuntu-live  Xubuntu live CD
```

To install it the Lamp (din't try it and I'm in Feisty, but it should work in Dapper too) execute:

```
sudo tasksel install lamp-server


```

---

### Post by Circus-Killer on 2007-08-05
see the howto in my signiture.

---

### Post by az on 2007-08-05
> **Noah0504 said:**
> I have an older computer that I guess doesn't like the kernel that the Ubuntu server CD tries to install.  After the GRUB menu, it just reboots.  I was wondering how to go about a LAMP install with just installing Ubuntu 6.06 from an alternate install CD.

As mentioned: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The server kernel only works on 686 or better.  The steps to install LAMP from the alternate cd are on that page.

Don't use expert mode and don't use tasksel.  Tasksel only is installed by default on Edgy and Fesity, not Dapper.  And you want a standard base system, not just a minimal install.

---

### Post by koenn on 2007-08-05
> **az said:**
> 
Don't use expert mode  ...  And you want a standard base system, not just a minimal install.
Come again ? 

re. the OP, the guy wanted to use the server CD, but it fails because of the686 optimized kernel. He's resorting to the alternate CD? I assume he want's a server-like install cause he tried the server CD first, and doesn't use the Desktop Live CD as plan B.
Correct me if I'm wrong but iirc, the alternate install installs ubuntu-desktop without user confirmation, unless you increase debconf priority, eg by running in expert mode

And if by "standard base system" you mean ubuntu-standard, OK, although -minimal would imo be sufficent (and anything else would be pulled in as a dependency if it's required).
[http://packages.ubuntu.com/dapper/base/ubuntu-minimal](http://packages.ubuntu.com/dapper/base/ubuntu-minimal)
[http://packages.ubuntu.com/dapper/base/ubuntu-standard](http://packages.ubuntu.com/dapper/base/ubuntu-standard)

Unless he want's to play Gnometris on his server ..

---

### Post by az on 2007-08-05
> **koenn said:**
> Come again ? 

re. the OP, the guy wanted to use the server CD, but it fails because of the686 optimized kernel. He's resorting to the alternate CD? I assume he want's a server-like install cause he tried the server CD first, and doesn't use the Desktop Live CD as plan B.
Correct me if I'm wrong but iirc, the alternate install installs ubuntu-desktop without user confirmation, unless you increase debconf priority, eg by running in expert mode

And if by "standard base system" you mean ubuntu-standard, OK, although -minimal would imo be sufficent (and anything else would be pulled in as a dependency if it's required).
[http://packages.ubuntu.com/dapper/base/ubuntu-minimal](http://packages.ubuntu.com/dapper/base/ubuntu-minimal)
[http://packages.ubuntu.com/dapper/base/ubuntu-standard](http://packages.ubuntu.com/dapper/base/ubuntu-standard)

Unless he want's to play Gnometris on his server ..

A standard base system is the system you end up with when you pick the "install base system" option from the Dapper alternate cd.  That's different from the desktop system.  

Ubuntu-minimal is basically a system that can only run apt and dpkg.  Ubuntu-standard is a system with all the typical console tools you will need.  No, they will not all be pulled-in by the LAMP stack.  You will end up with a frustrating situation when you expect a script to work, but have to search for hours to find out that sed or gawk are not installed...  It's also nice to be able to read manpages...

---

### Post by koenn on 2007-08-05
OK, he wants to install a standard base system - probably something like what ubuntu-minimal and ubuntu-standard would install. That wasn't my point. 
sed, awk and and other interesting stuff s.a. the  ubuntufied sudo are in ubuntu-minimal, btw. 

He should still be able to skip the 'Select and install software" step, which in Ubuntu, contrary to Debian where this installer comes from, does not let you select anything : it just installs - a complete Desktop. 

So, you can do that without going to expert mode ?

---

### Post by az on 2007-08-05
> **koenn said:**
> OK, he wants to install a standard base system - probably something like what ubuntu-minimal and ubuntu-standard would install. That wasn't my point. 
sed, awk and and other interesting stuff s.a. the  ubuntufied sudo are in ubuntu-minimal, btw. 

Yes, but you won't really want to run a system without ubuntu-standard.  

Ubuntu-minimal is not enough to run a proper system - you won't even be able to figure out why your system is not working...


> **koenn said:**
> 
He should still be able to skip the 'Select and install software" step, which in Ubuntu, contrary to Debian where this installer comes from, does not let you select anything : it just installs - a complete Desktop. 

So, you can do that without going to expert mode ?


In Feisty, that option is called "install a command-line system".

In Dapper, when you boot the alternate cd, you get the option to install a desktop or a base system (among other options.)  Of course you don't need to go into expert mode.  Expert mode is debugging mode.  If you think you need to use expert mode to do something, either it's a bug or you are not doing it the easy way.

Expert mode is to be avoided.

---

### Post by koenn on 2007-08-06
Fine with me, and maybe I'm mistaking between the alternate and the mini-cd re the installer options. Anyway, as long as the OP manages to get his server up ...

> **az said:**
> 
Ubuntu-minimal is not enough to run a proper system - you won't even be able to figure out why your system is not working...

Expert mode is debugging mode.  If you think you need to use expert mode to do something, either it's a bug or you are not doing it the easy way.

Expert mode is to be avoided.

Sometimes I prefer to decide myself what the system I set up is going to need in stead of relying on some prefab configs. I thought that was the point of "expert mode", but since you say so, I will shut down all the pc's I've set up this way  -- apparently  they shouldn't be capable of running  anyway --, and not use expert mode again. 
Come to think of it, maybe i ought to just install Windows or buy a Mac.

---

### Post by az on 2007-08-06
> **koenn said:**
> 
Sometimes I prefer to decide myself what the system I set up is going to need in stead of relying on some prefab configs. I thought that was the point of "expert mode", but since you say so, I will shut down all the pc's I've set up this way  -- apparently  they shouldn't be capable of running  anyway --, and not use expert mode again. 
Come to think of it, maybe i ought to just install Windows or buy a Mac.

You can do whatever you want.  And that may be an excellent choice for you.  However, when giving advice to an inexperienced audience, I would always recommend adhering to standards and doing what is simplest and most known.  

A barebones system has it's advantages, but in this context, I doubt that saving a few dozen megs of disk space is worth the potential headaches of having a non-standard environment.

---

### Post by ruibernardo on 2007-08-06
Now i'm confused.

Just to focus on the question of this thread, how would Noah0504 install the lamp server with the Alternate CD of Dapper without installing the ubuntu-desktop and without using the Server CD?

---

### Post by koenn on 2007-08-06
maybe az should answer that one

---

### Post by az on 2007-08-07
> **epimeteo said:**
> Now i'm confused.

Just to focus on the question of this thread, how would Noah0504 install the lamp server with the Alternate CD of Dapper without installing the ubuntu-desktop and without using the Server CD?

Using the Dapper alternate cd, 

Install a base system and then install

apache2 php5-mysql libapache2-mod-php5 mysql-server

That's it.  You end up with exactly the same system as if you installed with the server cd, but with the desktop kernel.  The desktop kernel can boot on the OP's pentium I, while the server kernel cannot.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Dapper does not install tasksel by default.

---

### Post by ruibernardo on 2007-08-07
Ok, just trying to make all this more clear and accurate. I didn't use Dapper installation for almost a year and was a little bit forgotten about its install options.

I've downloaded a 6.06 LTS Dapper Alternate CD (the 6.06.1 one) and was going to try to do what we've been talking about...

Thankfully the Dapper Alternate has an option to "Install a Server", although doesn't install any server (no apache/mysql/etc), but only the "ubuntu-standard", which doesn't include the ubuntu-desktop (Gnome).

Then, after rebooting the system, we can install the packages for the LAMP. 

I said "thankfully" because I've tried to use the "expert" on the boot options (and all the other options like "server", "server-expert") and it didn't work. Always ended with Gnome installed, no questions asked...
:lolflag:

Just for the record, how do you guys enable the "expert" option?

---

### Post by koenn on 2007-08-08
> **epimeteo said:**
> 
Just for the record, how do you guys enable the "expert" option?
hit F6 in the boot menu and select it. 

to avoid having the desktop installed, you should skip the step "Select and install software", reboot, and manually install the packages you want.

---

