---
title: "Ubuntu isn't Linux?"
date: 2007-02-03
forum: The Cafe
---

### Post by Roasted on 2007-02-03
I haven't heard this much, but there's been 1 or 2 people who have said that to me.

I use SUSE at school, and when I switched SUSE over to Gnome and worked around with it a bit, it didn't seem all that different from Ubuntu besides a few minor differences.

So I'm left wondering, what is it about folks that sometimes believe that Ubuntu doesn't follow the true path of Linux? Or am I perhaps hearing this from people who simply don't know what they're talking about?

---

### Post by koenn on 2007-02-03
There's a lot more to operating systems than what you see on your screen. Your desktop is just another application; its purpose is to put some panels/taskbars, menus, backgrounds, buttons, etc on your screen. You could say that, with some effort, an Ubuntu system could be made to 'look and feel' like a Mac. That doesn't mean the Operating systems are identical. 

Those people you mention are probably talink about comparing operating systems or linux distributions, not desktop environments.

---

### Post by 23meg on 2007-02-03
> what is it about folks that sometimes believe that Ubuntu doesn't follow the true path of Linux? Or am I perhaps hearing this from people who simply don't know what they're talking about? Most likely, and they're right as well. The problem probably is that they think the "true path of Linux" is obscurity. Ubuntu certainly isn't following that path.

---

### Post by RAV TUX on 2007-02-03
I think what they mean is that you can use Ubuntu for years and never learn how to compile or build your own OS,....traditionally Linux taught you how to take control and tear down and build things on your own...

I guess you could compare this to an auto mechanic that can completely build his own engine from scratch....and one that can drive his car all over the place and can occasionally change a tire, change the oil and paint his car a new cool color...

When are you a true Linux user?....when you can code and build your own kernel.

The rest of here are along for the ride. We are simply users of a different OS based on GNU/Linux.

---

### Post by koenn on 2007-02-03
I've read similar comments on Ubuntu. The way Ubuntu deals with the root account and sudo is not usual in most distro's. If they'd done it badly (like that distro that lets users run as root by default), I'd also say it's not 'the linux way'. Now,I'd say it's innovative, although the usual way (su + root password in stead of sudo + user password) is, more secure (the "bad buys" would need to know 1 additional password to get root) - the ubuntu way makes it easier on the users but (slightly ?) less secure. 

I've also read once (on a mailing list - don't remember where) a remark that Ubuntu would allow users to write outside their home directories, and a reply that "if this is true, Ubuntu is breaking standard Linux/Unix security".

---

### Post by IYY on 2007-02-03
Every operating system that uses the Linux kernel can be informally called "Linux". If you want to be technical, Linux is not an operating system at all, but a kernel. An operating system that uses this kernel as well as the GNU coreutils (as Ubuntu does) can be called a GNU/Linux distribution.

---

### Post by Tomosaur on 2007-02-03
> **koenn said:**
> I've read similar comments on Ubuntu. The way Ubuntu deals with the root account and sudo is not usual in most distro's. If they'd done it badly (like that distro that lets users run as root by default), I'd also say it's not 'the linux way'. Now,I'd say it's innovative, although the usual way (su + root password in stead of sudo + user password) is, more secure (the "bad buys" would need to know 1 additional password to get root) - the ubuntu way makes it easier on the users but (slightly ?) less secure. 

I don't understand your line of thinking here:
'Traditional Linux': Attacker needs to only know the root password, since 'root' is a standard account on all linux platforms.

Ubuntu: Attacker needs to know the account name of someone who has admin access, and then also needs to know their password. Since root is, by default, unavailable on Ubuntu, this means an attacker can't log into the root account which they **already know** is there. In Ubuntu, they need to know the user name of someone who is allowed to use sudo, **and** their password. This is more secure, right? Or am I missing something here?

> 
I've also read once (on a mailing list - don't remember where) a remark that Ubuntu would allow users to write outside their home directories, and a reply that "if this is true, Ubuntu is breaking standard Linux/Unix security".
I think this statement meant that Ubuntu would allow users to modify their root account without any password checks or whatever - similar to how Windows (up to, but not including, Vista) works - something which we all know to be false.

---

### Post by koenn on 2007-02-03
> **RAV TUX said:**
> 
When are you a true Linux user?....when you can code and build your own kernel.

I'd say that makes you a Linux kernel developer.

It is true however, that using Linux is a good way of learning to understand networking and how computers work because the configuration files are human readable and the commands   often reflect 'how stuff works", as opposed to other OS's (or more recent Linux distro's) that hide all this behind glossy GUI's and obscure registry settings.

When / if Ubuntu reaches the point that it sacrifices essentials (security, configurability, ...) to "user-friendlyness' I might start to agree that Ubuntu is not really Linux. 

A similar point: to make things "just work", Ubuntu might go towards running al sorts of deamons and services by default, just in case someone might need them but doesn't want to be bothered with having to configure them. That would kinda gop against (my understanding of) Linux/Unix philosophy as well

---

### Post by koenn on 2007-02-03
> **Tomosaur said:**
> I don't understand your line of thinking here:
'Traditional Linux': Attacker needs to only know the root password, since 'root' is a standard account on all linux platforms.

Ubuntu: Attacker needs to know the account name of someone who has admin access, and then also needs to know their password. Since root is, by default, unavailable on Ubuntu, this means an attacker can't log into the root account which they **already know** is there. In Ubuntu, they need to know the user name of someone who is allowed to use sudo, **and** their password. This is more secure, right? Or am I missing something here?


It's slightly different : You would NOT allow root to login. Anyoneone and everyone would login as a regular, unpriviligues user. So you still need to know a regular account name + password to login. As with sudo, you can limit the use of su to certain users. Then, to get root, you need to know root's password as well (in stead of the password that you already know, since you logged in with it.
Here's something worth looking at if you're interested in the subject:
[http://www.adminschoice.com/docs/P_securing_solaris.htm](http://www.adminschoice.com/docs/P_securing_solaris.htm)

---

### Post by BuffaloX on 2007-02-03
Forget it,
this was not the thread i responded to??????????????????????????????????

This was a totally "(fogged)" up thread merge.
Seems this really was the right thread, but merged with an old thread, that's been inactive for a week!!!!!!!!!!!

And also had a totally different theme IMO.

---

### Post by Tomosaur on 2007-02-03
> **koenn said:**
> It's slightly different : You would NOT allow root to login. Anyoneone and everyone would login as a regular, unpriviligues user. So you still need to know a regular account name + password to login. As with sudo, you can limit the use of su to certain users. Then, to get root, you need to know root's password as well (in stead of the password that you already know, since you logged in with it.
Here's something worth looking at if you're interested in the subject:
[http://www.adminschoice.com/docs/P_securing_solaris.htm](http://www.adminschoice.com/docs/P_securing_solaris.htm)

Yes, but it doesn't make sense to prohibit **yourself** from using root - since it's generally assumed you aren't going to attack your own machine. With Ubuntu, an attacker needs to know:
a) The account name of a user who is able to 'sudo up'.
2) Their password

This is already more difficult then the general Linux method, where you:
a) Need to know the root password

I really don't see how the Ubuntu method is 'less secure' than the broadly accepted 'Linux method'. Su enables you to login as root, for as long as you like (or anyone else for that matter, provided you have their password). Sudo grants you only temporary root priveleges. An 'ordinary user' is not able to modify root until they use su or sudo, and then they must already have the necessary permissions to even use su or sudo in the first place. The general linux method only requires you to know the root password. Maybe I'm misunderstanding what you're trying to say - but if you are seriously arguing that the 'sudo' method is less secure than just logging in as root, then I think you may need to have another think. It is **obviously** a greater level of abstraction than *just one password*.

---

### Post by melancholeric on 2007-02-03
> **Tomosaur said:**
> Yes, but it doesn't make sense to prohibit **yourself** from using root - since it's generally assumed you aren't going to attack your own machine. With Ubuntu, an attacker needs to know:
a) The account name of a user who is able to 'sudo up'.
2) Their password

This is already more difficult then the general Linux method, where you:
a) Need to know the root password

I really don't see how the Ubuntu method is 'less secure' than the broadly accepted 'Linux method'. Su enables you to login as root, for as long as you like (or anyone else for that matter, provided you have their password). Sudo grants you only temporary root priveleges. An 'ordinary user' is not able to modify root until they use su or sudo, and then they must already have the necessary permissions to even use su or sudo in the first place. The general linux method only requires you to know the root password. Maybe I'm misunderstanding what you're trying to say - but if you are seriously arguing that the 'sudo' method is less secure than just logging in as root, then I think you may need to have another think. It is **obviously** a greater level of abstraction than *just one password*.

depends on the scenario. If we're talking about f.ex. remote logins, I believe the SSH daemon can be configured to not allow root login -- so you'll have to first login as a user and then su to root, in which case you'll have to know 1. a username 2. it's password and 3. the root password.

If we're talking about local login the whole point is moot since physical access to the machine > root access. You could boot to single-user mode ... or just steal the hard drive.

---

### Post by koenn on 2007-02-03
> depends on the scenario. If we're talking about f.ex. remote logins, I believe the SSH daemon can be configured to not allow root login -- so you'll have to first login as a user and then su to root, in which case you'll have to know 1. a username 2. it's password and 3. the root password.

If we're talking about local login the whole point is moot since physical access to the machine > root access. You could boot to single-user mode ... or just steal the hard drive.
Correct. But as Unix was traditionally a multi user system for professional use, the computer itself would be unaccessible for anyone but the sysadmin/sysops/ ...

Note, however, how on PC's, you typicvally boot into a desktop environment that does not allow root logins. So here the runlevels and the desktop manager (eg gdm) forces you to log in with a normal account. 
So, the ubuntu way, you need
1) an account name
2) the right to sudo
3) the account's password

the traditional way, you need
1) an account name
2; the password for that account
3) the right to su
4) the root password


Of course, it's good practise to password-protect maintenance mode as well - you don't want just anyone to get into 'maintenance mode'.

> Yes, but it doesn't make sense to prohibit yourself from using root - since it's generally assumed you aren't going to attack your own machine
Even of you are the sysadmin, and even if you could, you shouldn't login as root. You only use the root account for tasks that require root privilegues - to keep you from "shooting yourself in the foot" as it is commenly called. 

One additional advantage of 'su' is that it lets you run an entire session without having to type 'sudo' in front of every command, which is far easier when dealing with complexer commands (especially redirection and pipes) : the shell then gets confused because it sees 2 commands (sudo + the actual command) and doesn't know what to pipe or redirect)

see also [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-02-03
I've never built my own kernel... or needed to.

---

### Post by az on 2007-02-03
> **Roasted said:**
> 
So I'm left wondering, what is it about folks that sometimes believe that Ubuntu doesn't follow the true path of Linux? Or am I perhaps hearing this from people who simply don't know what they're talking about?

I think you are talking about GNU.

The point of GNU is to produce a complete OS that is free-libre.  The only way that Ubuntu doesn't accomplish this if by shipping proprietary drivers.  They are all easily removed by running

sudo apt-get remove linux-restricted-modules*

Ubuntu has gotten alot of press recently because of the intention to not only ship those drivers, but to enable them by default - currently, if you own the that hardware, you use the free-libre open source drivers in the kernel by default.  I think the press is a good thing, since it draws attention to the topic and increases awareness about software freedom.

Those drivers are closed-source and proprietary.  Although they are written for linux by the companies, it slows development because you cannot work with the drivers, nor debug your kernel when they are loaded.  

On a scale of software freedom, Ubuntu is way more free than other distros.  I happen to think that the issue of enabling those drivers by default will have the desired effect of spreading awareness and eventually getting vendors to provide free-libre and open source drivers for linux.  So, IMHO, it's all good.

---

### Post by az on 2007-02-03
> **aysiu said:**
> I've never built my own kernel... or needed to.

I haven't needed to compile (or recompile, actually) a kernel since Debian Woody's 2.4.18bf kernel.

---

### Post by RAV TUX on 2007-02-03
> **Brainfart said:**
> There's a difference between a user and a developer.  Users should not have to know anything about writing a Software, only how to use it.  Even developers for a project of substantial size shouldn't have to know how to code the entire system but only their particular subsystems (knowing the big picture never hurts though).  Are you a Gnome/KDE/WM-of-choice user?  Are you an apt user?   Could you write it yourself?  If you're not a user, then what do you use for those functionalities?

As to your analogy with the mechanic, that brings in a third role - one of a maintainer.  This would be akin to a sysop, who could take a broken system and make it work again.  They don't need to know how it's designed either.  Somehow I doubt the average mechanic would have any idea where to start in designing and manufacturing a vehicle.  Hell, some of them don't know where to start fixing one.

You just contradicted yourself here, saying you're a user.  What is your OS then?  Did you code and build it yourself?

no contradiction,...I am just here for the ride for now...

but I do feel that we should all seek to acquire skills to code...

simple concept really...we are what we are because of what we all are...

I do not feel that embracing lack of knowledge is anything to be proud of...but we should strive to learn to code and to contribute....

for now I am like most people here along for the ride...but I do intend to contribute to code one day....I think this is a worthy goal that we can all strive to acquire...

the acquisition of unknown knowledge isn't that hard...it mostly takes time of which "we" have little of

for now I contribute in other ways...I give of my time freely to help as a staff member here on Ubuntuforums.org, and sabayonlinux.org....

I am active in much more ways to

but I honestly feel guilty that I can not code or contribute to the kernel that we all have come to know and love

My apologies if what I wrote was mis-understood...thats my fault but I hope I have clarified my thoughts just a bit here

---

### Post by Brainfart on 2007-02-03
> **RAV TUX said:**
> but I do feel that we should all seek to acquire skills to code...

simple concept really...we are what we are because of what we all are...

I do not feel that embracing lack of knowledge is anything to be proud of...but we should strive to learn to code and to contribute....
I have to disagree.  Computers have become an integral part of society, and (at least in first-world countries) everyone's using them.  However, we don't need everyone working to improve them, there's already people doing that - the developers.

> for now I am like most people here along for the ride...but I do intend to contribute one day....I think this is a worthy goal that we can all acquire...

the acquisition of unknown knowledge isn't that hard...it mostly takes time of which "we" have little ofIt's great that you want to contribute.  I do too; once I get out of school and get a little experience in development, I'll probably hook onto some free software group or another.  However, not everyone can just jump onto the bandwagon.  As much as some people may claim so, and as much as some people may want to, there is a degree of knowledge and training that is required to make good software.  Not to mention the time requirement (some people put a lot of time into their projects).  

> 
for now I contribute in other ways...I give of my time freely to help as a staff member here on Ubuntuforums.org, and sabayonlinux.org....

I am active in much more ways to

but I honestly feel guilty that I can not code or contribute to the kernel that we all have come to know and love
Just using the software, reporting bugs, spreading the word is plenty of help from the average people.  Contributing to the kernel is a great thing to strive for, but the kernel is only one part of the free software community.  (Furthermore, it's also very complicated without some schooling.) 
> 
My apologies if what I wrote was mis-understood...thats my fault but I hope I have clarified my thoughts just a bit hereNot at all.  I probably phrased things a little rougher than I should have.  I didn't mean to be insulting, I just wanted to point out that your definitions were flawed.  Maybe it's just a difference in perspective though.

---

### Post by igknighted on 2007-02-03
> **Tomosaur said:**
> Yes, but it doesn't make sense to prohibit **yourself** from using root - since it's generally assumed you aren't going to attack your own machine. With Ubuntu, an attacker needs to know:
a) The account name of a user who is able to 'sudo up'.
2) Their password

This is already more difficult then the general Linux method, where you:
a) Need to know the root password

I really don't see how the Ubuntu method is 'less secure' than the broadly accepted 'Linux method'. Su enables you to login as root, for as long as you like (or anyone else for that matter, provided you have their password). Sudo grants you only temporary root priveleges. An 'ordinary user' is not able to modify root until they use su or sudo, and then they must already have the necessary permissions to even use su or sudo in the first place. The general linux method only requires you to know the root password. Maybe I'm misunderstanding what you're trying to say - but if you are seriously arguing that the 'sudo' method is less secure than just logging in as root, then I think you may need to have another think. It is **obviously** a greater level of abstraction than *just one password*.

You could argue it is less secure because most users will pick dictionary words (or combinations of them) for their personal login.  A true root password would be random.

---

### Post by az on 2007-02-03
> **Brainfart said:**
> I have to disagree.  Computers have become an integral part of society, and (at least in first-world countries) everyone's using them.  However, we don't need everyone working to improve them, there's already people doing that - the developers.

It's great that you want to contribute.  I do too; once I get out of school and get a little experience in development, I'll probably hook onto some free software group or another.  However, not everyone can just jump onto the bandwagon.  


It is interesting that in some developing countries (Think OLPC countries) new advances in technology is bringing education to places where it was not before.  In building these curriculums, it is being considered to replace much of some math education  with programming.

For example, it is a much more relevant way to learn some abstract concepts and problem-solving.  

> **igknighted said:**
> A true root password would be random.

Wha?  A strong password is a strong password.  There is no higher standard just because it is a root password.  A root password does not have to be random.

---

### Post by aysiu on 2007-02-04
> **igknighted said:**
> You could argue it is less secure because most users will pick dictionary words (or combinations of them) for their personal login.  A true root password would be random.
But wouldn't, by your assumption, most users pick dictionary words for the root password as well? Why would someone concerned with security pick a weak password for the user password and a strong one for the root password?

Anyone concerned about security will pick strong passwords for root and user. Otherwise, she will pick weak passwords for all accounts.

---

### Post by EdThaSlayer on 2007-02-04
As long as the Linux kernel is used, it's linux.
Those people that don't like Ubuntu don't like the fact that "Linux should be easy to use" and probably like to learn time-consuming things which a dumb-not-technical Windows user can set-up faster using a GUI.

---

### Post by Sunnz on 2007-02-04
Please remember that GNU/Linux is suppose to be a free(dom) OS, you can use to for whatever purpose you want (as long as it is legal in your country), including running your server, learning about inner workings of an OS, **AND** putting it on a desktop for the **average user**.

Learning Linux is another thing. Just because Ubuntu users doesn't learn about Linux as quickily as others, it doesn't mean Ubuntu isn't Linux. What I mean by learning Linux is that you can take your knowledge across many Linux distributions.

BTW, did anyone know that you can just do "sudo su", which is effectively doing su with a sudoer's password?

---

### Post by fuscia on 2007-02-04
real linux is planting an acorn, nurturing it into a large tree and using the leaves instead of toilet paper. this could get as silly as the 'there's no such thing as a real novel, or a real links course' nonsense.

---

### Post by JAPrufrock on 2007-02-04
"What's in a name? that which we call a rose
   By any other name would smell as sweet;"

---

### Post by prizrak on 2007-02-04
Ubuntu is not Linux, it is a Linux based OS. Linux is a kernel, when people talk about not following Linux way they tend to mean the FSF way. That is true, Ubuntu does not follow the FSF way it is alot closer to the ACTUAL Linux way of being pragmatic.

---

### Post by ahaslam on 2007-02-04
> **koenn said:**
> as opposed to other OS's (or more recent Linux distro's) that hide all this behind glossy GUI's and obscure registry settings.

Don't stone me here, but I think that's the way Ubuntu is headed and is almost at. While testing Feisty Herd 2 I almost expected to see the SLAB from openSUSE ;)

Tony.

---

