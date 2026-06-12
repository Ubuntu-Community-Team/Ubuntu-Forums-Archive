---
title: "A non-restrictive linux distro"
date: 2010-06-01
forum: The Cafe
---

### Post by clgy15 on 2010-06-01
Hey everybody,
I like ubuntu, but some of the restrictions it puts on mounted partitions, the fact that I cant remove the dependency libraries of the programs that I installed. (For instance, I install codeblocks which has some random library, when I uninstall codeblocks it dosent uninstall those very small libraries.) So im looking for a distro, that dosent restrict any partiton or really any device from normal users because I cant develop on restricted mounting. A straight forward Distro with GNOME. Im in the neighborhood of doing LFS so if that puts into perspective on what I do with linux then yeah.
Thanks guys

---

### Post by earthpigg on 2010-06-01
hi,

i think puppy has all users run as root by default.

---

### Post by clgy15 on 2010-06-01
Well I use puppy as a mobile OS. But im kinda looking for a full powered OS like Ubuntu just alittle more kernel development friendly.

---

### Post by BoneKracker on 2010-06-01
> **clgy15 said:**
> ... im looking for a distro, that dosent restrict any partiton or really any device from normal users because I cant develop on restricted mounting.
Here you go.

---

### Post by sisco311 on 2010-06-01
> **clgy15 said:**
> Hey everybody,
I like ubuntu, but some of the restrictions it puts on mounted partitions, the fact that I cant remove the dependency libraries of the programs that I installed. (For instance, I install codeblocks which has some random library, when I uninstall codeblocks it dosent uninstall those very small libraries.)

You have to run:
```
sudo apt-get autoremove
```

it removes packages that were automatically installed to satisfy dependencies for some package and that are no more needed.

---

### Post by BoneKracker on 2010-06-01
Sorry about that. :p

---

### Post by BslBryan on 2010-06-01
> **BoneKracker said:**
> Here you go.

<snip>

Whoo!  Then you could play this:

[Bang! Bang!]("http://members.chello.at/theodor.lauppert/games/bangbang.htm")

---

### Post by nothingspecial on 2010-06-01
> **clgy15 said:**
>  I install codeblocks which has some random library, when I uninstall codeblocks it dosent uninstall those very small libraries.) 

Don`t see the problem here

 
```
rob@rob-desktop:/tmp$ [COLOR="Magenta"]sudo apt-get install codeblocks[/COLOR]
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
 [COLOR="Red"] libcodeblocks0[/COLOR]
Suggested packages:
  wx-common codeblocks-contrib
The following NEW packages will be installed
  codeblocks libcodeblocks0
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 5,739kB of archives.
After this operation, 15.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe [COLOR="Red"]libcodeblocks0 8.02-0ubuntu4[/COLOR] [1,542kB]
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe codeblocks 8.02-0ubuntu4 [4,197kB]                                                 
Fetched 5,739kB in 42s (134kB/s)                                                                                                              
Selecting previously deselected package [COLOR="Red"]libcodeblocks0.[/COLOR]
(Reading database ... 173612 files and directories currently installed.)
Unpacking libcodeblocks0 (from ...[COLOR="Red"]/libcodeblocks0_8.02-0ubuntu4_amd64.deb)[/COLOR] ...
Selecting previously deselected package codeblocks.
Unpacking codeblocks (from .../codeblocks_8.02-0ubuntu4_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for gnome-icon-theme ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for python-support ...
Setting up libcodeblocks0 (8.02-0ubuntu4) ...

Setting up codeblocks (8.02-0ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rob@rob-desktop:/tmp$ [COLOR="Magenta"]sudo apt-get remove codeblocks[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Blue"]The following packages were automatically installed and are no longer required:
  libcodeblocks0[/COLOR]
[COLOR="Lime"]Use 'apt-get autoremove' to remove them.[/COLOR]
The following packages will be REMOVED
  codeblocks
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174215 files and directories currently installed.)
Removing codeblocks ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
rob@rob-desktop:/tmp$ [COLOR="Lime"]sudo apt-get autoremove[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
 [COLOR="Red"] libcodeblocks0[/COLOR]
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 4,399kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173625 files and directories currently installed.)
[COLOR="Red"]Removing libcodeblocks0 ...[/COLOR]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rob@rob-desktop:/tmp$ 
```

Job done :P

---

### Post by nothingspecial on 2010-06-01
Ignore that silly windows stuff, as  sisco311 said, and I tried to illustrate,

```
sudo apt-get autoremove
```

will remove unneeded dependencies.

---

### Post by clgy15 on 2010-06-01
Ha Ha guys, Iv seen Iv struck a nerve. Im not saying no password protection or any of the other security features. I just want to be able to do LFS for start. And I cant do that with the mounting restrictions that ubuntu uses. How do distro developers do this?????

---

### Post by BoneKracker on 2010-06-01
> **clgy15 said:**
> Ha Ha guys, Iv seen Iv struck a nerve. Im not saying no password protection or any of the other security features. I just want to be able to do LFS for start. And I cant do that with the mounting restrictions that ubuntu uses. How do distro developers do this?????
I think you're going to have to be more specific about what exactly you are having trouble doing.  If you can't do what you need to using 'sudo', of you find using sudo too inconvenient for this work, one thing you could do is enable root and then either login as root from the terminal or use the 'su' command.  Then you are operating as root.  Another thing you could do is create a 'dev' group and give the needed privileges (but certain things, such as mounting system partitions and writing to certain devices, _should_ be restricted to root).  It's not rocket science, especially compared to LFS.

In fact, I encourage you come back and look at this thread again after you've done LFS.  Really.  Make a note to yourself to do it. :)

---

### Post by nothingspecial on 2010-06-01
> **clgy15 said:**
> Ha Ha guys, Iv seen Iv struck a nerve. Im not saying no password protection or any of the other security features. I just want to be able to do LFS for start. And I cant do that with the mounting restrictions that ubuntu uses. How do distro developers do this?????

You need to explain further. You gave an example that can easily be sorted.

Ubuntu seems restrictive, and I suppose, and in it`s raw (just installed) state it is. But that is the idea. It is designed to be a linux distro that anyone can use without having to get under the hood (so to speak), although I suppose these forums are a testament to the fact that it hasn`t quite made it yet.

You can (LET IT ALWAYS BE SO), tinker with Ubuntu to tour heart`s content. You can make it as unrestrictive as slackware should you desire (although there`s not much point).

So now you know how to remove unneeded dependencies, what is your problem? :)

---

### Post by clgy15 on 2010-06-01
See now I dont even know.... So let me list what I want to do. 
 In the end I would like to not have to continually enter my password so many times. i know its for the protection of the computer but its just one of those things where I know what im installing so I dont want to be bothered by so many prompts. i know its a bad thing.
Also I want no restrictions to write to hardisks, flash drives etc. I do so much development on these things I want to be able to use my main user instead of logging out and logging back into root. 
Something completly unrelated but the boot screen is impossible to work with and some standard software sources that ubuntu updates fail to update.

---

### Post by oldos2er on 2010-06-01
> **clgy15 said:**
> Also I want no restrictions to write to hardisks, flash drives etc. 

If you're talking about Linux-native file systems, look into **chown**. If not, you'll need to make changes to /etc/fstab (see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)).

If "the boot screen is impossible to work with" is referring to grub2, see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by LowSky on 2010-06-01
You can change the permissions on mounted drives, so long as the file system supports permissions. File formats like FAT and NTFS do not have file permissions and should require you to be a certain user to write to them. You can also give permissions to your user account if it makes things easier.

Please remember that Ubuntu is an OS built for everyday home use. If you need support for business purposes you should really purchase support from Canonical. They can help with your business needs to make Ubuntu work in the enviroment that you require. I know I'm sounding like a sales person saying that but I think it really needs to be said.

---

### Post by koenn on 2010-06-01
> **clgy15 said:**
> Ha Ha guys, Iv seen Iv struck a nerve. Im not saying no password protection or any of the other security features. I just want to be able to do LFS for start. And I cant do that with the mounting restrictions that ubuntu uses. How do distro developers do this?????

it's pretty simple, really. You log in as root, or run a shell with elevated privileges, and bingo, you have unlimited access to any file, any directory and any command, anywhere on the system. 
There's howtos for this all over the net. I'm surprised you're contemplating doing Linux From Scratch while you apparently were not able to find out this rather basic piece of info on linux system administration.

---

### Post by nothingspecial on 2010-06-01
> **clgy15 said:**
> See now I dont even know.... So let me list what I want to do. 
 In the end I would like to not have to continually enter my password so many times. i know its for the protection of the computer but its just one of those things where I know what im installing so I dont want to be bothered by so many prompts. i know its a bad thing.

That`s the Ubuntu security model, there are loads of distros that enable root (mass breakage) By default.

> **clgy15 said:**
> Also I want no restrictions to write to hardisks, flash drives etc. I do so much development on these things I want to be able to use my main user instead of logging out and logging back into root. 

I am no coder, but I am related to one, and he has his (Debian, I think) system locked down far more than default ubuntu ----- maybe your code is not important. As far as I know, when coding (especially for a living), security is paramount.


I would learn about sudo, chown and chmod if I were you.

However, this is linux....... do what you will. :)

As for the boot screen, I don`t use it so can`t help.

Good luck and have fun.

---

### Post by NightwishFan on 2010-06-01
Ubuntu and Debian have done all that I could do on other distros. You can even compile packages with apt somehow. (I forget how :D )

---

### Post by szymon_g on 2010-06-01
just use aptitude for package managment... and about restrictions- windows95 has none of them ;)
but seriously- instead of avoiding it, try to learn and use it properly.

---

### Post by Ebere on 2010-06-01
> **sisco311 said:**
> You have to run:
```
sudo apt-get autoremove
```

As a newby, I had no idea what that code would do, when I read it.

I have, of course, figured it out, just by reading further.

But...

The frustration with having to input the password constantly, is a very common frustration.

Especially among newbys. Who have no more clue about that command than I did.

Since it is possible that someone could come along who doesn't know what the comman does... Who is trusting of such things, simply because it is posted here, and not at some anonymous website... And who is just frustrated enough to give it a try, right away...

Do you really think it wise to post that ?

Ok, forget wise. Do you think it is in keeping with the base intent of this forum ?

If you really -must- post commands which can do major damage like that, whether in jest or not... shouldn't you at least post a disclaimer along with it to warn innocent newbs ?

---

### Post by tjwoosta on 2010-06-01
> **clgy15 said:**
> 
 In the end I would like to not have to continually enter my password so many times. i know its for the protection of the computer but its just one of those things where I know what im installing so I dont want to be bothered by so many prompts. i know its a bad thing.
Also I want no restrictions to write to hardisks, flash drives etc. I do so much development on these things I want to be able to use my main user instead of logging out and logging back into root. 
Something completly unrelated but the boot screen is impossible to work with and some standard software sources that ubuntu updates fail to update.


sounds to me like you just want to su to root user. Ubuntu by default locks out the root account, so you can't just su -, but you should still be able to use sudo to access su.

try this

```
sudo su -
```

it should log you in as root for only the terminal you are working from, and it wont ask you for a password for everything.

---

### Post by NightwishFan on 2010-06-01
To remove unneeded packages, this is what I do:

[LIST=1]
[*]Go to **Synaptic** under System -> Administration.
[*]Under Settings -> Filters, create a new filter, call it "Orphaned".
[*]Hit "Deselect All" and only check "Orphaned" on the right side, then hit ok.
[*]On the bottom left of synaptic there is a button called "Custom Filters". Go to it. Look under the one you made called "Orphaned". This should list the uneeded packages.
[*]Feel free to review and remove them at your leisure.
[/LIST]

---

### Post by Ebere on 2010-06-01
> **sisco311 said:**
> You have to run:
```
sudo apt-get autoremove
```

As a newby, I had no idea what that code would do, when I read it.

I have, of course, figured it out, just by reading further.

But...

The frustration with having to input the password constantly, is a very common frustration.

Especially among newbys. Who have no more clue about that command than I did.

Since it is possible that someone could come along who doesn't know what the comman does... Who is trusting of such things, simply because it is posted here, and not at some anonymous website... And who is just frustrated enough to give it a try, right away...

Do you really think it wise to post that ?

Ok, forget wise. Do you think it is in keeping with the base intent of this forum ?

If you really -must- post commands which can do major damage like that, whether in jest or not... shouldn't you at least post a disclaimer along with it to warn innocent newbs ?

---

### Post by nothingspecial on 2010-06-01
> **Ebere said:**
> 

If you really -must- post commands which can do major damage like that, whether in jest or not... shouldn't you at least post a disclaimer along with it to warn innocent newbs ?

That command does not do major damage.

There, have been, in the past, trolls who have posted malicious code on these forums. At that time I was a "newb,newbie,whatever" and luckily didn`t come across it.

You have to, as in real life, make decisions on advice you are given.

Check out the member`s profile, have a look at other help (s)he has given.

More importantly, try to understand the "code" you are copying and pasting.

---

### Post by sisco311 on 2010-06-01
> **Ebere said:**
> As a newby, I had no idea what that code would do, when I read it.

I have, of course, figured it out, just by reading further.

But...

The frustration with having to input the password constantly, is a very common frustration.

Especially among newbys. Who have no more clue about that command than I did.

Since it is possible that someone could come along who doesn't know what the comman does... Who is trusting of such things, simply because it is posted here, and not at some anonymous website... And who is just frustrated enough to give it a try, right away...

Do you really think it wise to post that ?

Ok, forget wise. Do you think it is in keeping with the base intent of this forum ?

If you really -must- post commands which can do major damage like that, whether in jest or not... shouldn't you at least post a disclaimer along with it to warn innocent newbs ?

Point taken. I updated my OP.

---

### Post by yamfox on 2010-06-01
Sudo has a purpose. That is for good, and good shall always prevail!! :guitar:

---

### Post by doas777 on 2010-06-01
> **yamfox said:**
> Sudo has a purpose. That is for good, and good shall always prevail!! :guitar:

and sudo/gksu are soooo much more elegant than UAC, so I wonder why it is such a big shift for new users. perhaps its because it isn't so easily disabled.

---

### Post by Ebere on 2010-06-01
> **sisco311 said:**
> Point taken. I updated my OP.

Thank you.

:)

---

### Post by cariboo on 2010-06-01
> **Ebere said:**
> As a newby, I had no idea what that code would do, when I read it.

I have, of course, figured it out, just by reading further.

But...

The frustration with having to input the password constantly, is a very common frustration.

Especially among newbys. Who have no more clue about that command than I did.

Since it is possible that someone could come along who doesn't know what the comman does... Who is trusting of such things, simply because it is posted here, and not at some anonymous website... And who is just frustrated enough to give it a try, right away...

Do you really think it wise to post that ?

Ok, forget wise. Do you think it is in keeping with the base intent of this forum ?

If you really -must- post commands which can do major damage like that, whether in jest or not... shouldn't you at least post a disclaimer along with it to warn innocent newbs ?

How about this:

> autoremove
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.

from man apt-get. The man pages, once you learn howto read them, are an invaluable resource that come installed by default.

---

