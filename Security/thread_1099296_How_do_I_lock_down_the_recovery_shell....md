---
title: "How do I lock down the recovery shell..."
date: 2009-03-18
forum: Security
---

### Post by deepspring on 2009-03-18
Hi Guys,

I just had to go into recovery mode after making a mistake in the fstab file that prevented me from booting in normal mode. I was shocked to learn that I was able to get root access without even providing a username or password (so much for Ubuntu being "SECURE").

How do I lock down the recovery console so that it is more secure?

Edit: I'm using Ubuntu 8.10 (Intrepid).

Thanks
Deepspring.


[SIZE=4]**LAST EDIT 19/03/09:**[/size]
Thank you everyone for helping me. This problem has now been fixed. Click [[here](http://ubuntuforums.org/showpost.php?p=6918594&postcount=14)] to find out how I did it.

---

### Post by nelskurian on 2009-03-18
To prevent this unauthorized boot-modifications gaining root-access,
grub contains a password command line in menu.lst including a --md5
option. If we set this password and don't change anything different in
menu.lst, the only thing that changes is: grub options can not be
modified and Grub's command line can not be opened to do different
things.
The Grub password can be be user defined during installation or be a
random generated password, choosing a empty password deactivates Grub's
password option.

First, run grub in a terminal. Then use grub's md5crypt command and type in your password - we do this because you don't want your password to be in plaintext in the configuration file. Take the output of the command and edit /boot/grub/menu.lst accordingly.

Code:

```
$ grub
grub> md5crypt
Password: 12345
Encrypted: $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
grub> quit
```

Here's the relevant part in menu.lst:
Code:

```
password --md5 $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
```

---

### Post by dusan.saiko on 2009-03-18
I think this was a behaviour of releases prior to Intrepid, there were some discussions on this issue and nowadays the recovery shell is password protected (at least in Jaunty and I am quite sure in Intrepid too).

What you can do is:
- set grub password
- delete the recovery option from /boot/grub/menu.lst and have some recovery cd ready

The principal problem is that protecting your computer when somebody can physically access it is quite difficult. You would have to at least disable booting from external media (USB/CD/Network), encrypt the harddisk and not to leave the computer running when unattended. Most computers allow booting from CD, in that case no root password is necessary for intruder if your disk is not encrypted anyway; in case you would only disable the booting, your disk can be always dismounted from PC/laptop.

---

### Post by deepspring on 2009-03-18
[deleted]

---

### Post by deepspring on 2009-03-18
> **dusan.saiko said:**
> I think this was a behaviour of releases prior to Intrepid, there were some discussions on this issue and nowadays the recovery shell is password protected (at least in Jaunty and I am quite sure in Intrepid too).

I'm using Intrepid. No username or password required for ROOT access.

> What you can do is:
- set grub password
- delete the recovery option from /boot/grub/menu.lst and have some recovery cd ready

I'll set a grub password (despite the annoyance factor).

I believe the recovery option is useful, but it needs to be secured. full stop.

---

### Post by deepspring on 2009-03-18
> **nelskurian said:**
> To prevent this unauthorized boot-modifications gaining root-access,
grub contains a password command line in menu.lst including a --md5
option. If we set this password and don't change anything different in
menu.lst, the only thing that changes is: grub options can not be
modified and Grub's command line can not be opened to do different
things.
The Grub password can be be user defined during installation or be a
random generated password, choosing a empty password deactivates Grub's
password option.

First, run grub in a terminal. Then use grub's md5crypt command and type in your password - we do this because you don't want your password to be in plaintext in the configuration file. Take the output of the command and edit /boot/grub/menu.lst accordingly.

Code:

```
$ grub
grub> md5crypt
Password: 12345
Encrypted: $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
grub> quit
```

Here's the relevant part in menu.lst:
Code:

```
password --md5 $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
```


Please put it in stupid english for a new Ubuntu user.

---

### Post by deepspring on 2009-03-18
I don't understand why it is so hard to add user authentication to the recovery console. It's not like I'm forcing this on everyone.

---

### Post by nelskurian on 2009-03-18
> Please put it in stupid english for a new Ubuntu user.
Sorry dude..I know its someway heavy...Their is no nedd to tell the whle story.Now their is simple graphical tool called startup manager.

```
sudo aptitude install startupmanager
```

Then, you can access it via System, Administration, Startup-Manager.

From here, it is easy to set options such as how long to wait before booting (timeout), as well as many display options. The other tabs allow you to customize the GRUB menu colors and theme, password protection, and specifying which entries will be visible. It is even possible to change the Ubuntu image that is displayed while things are loading. A nice little tool to completely theme your desktop.Also we can remove the recovery mode from the grub menu.


just igrnore my previous short story,since ubuntu always make matters simple..

---

### Post by deepspring on 2009-03-18
For the record, locking down grub requires a little more than just adding the password field. I discovered this after half an hour of wasting time googling grub password.

You need to need change the following in "/boot/menu.lst" as well...
```
# lockalternative=false
```
to...
```
# lockalternative=true
```
and it helps to change...
```
# lockold=false
```
to..
```
# lockold=true
```
The you need to run "sudo update-grub".

---

### Post by ushills on 2009-03-18
Changing those comment lines won't do anything.

Perhaps you meant to uncomment by removing the #.

Startupmanager does make things easy.

---

### Post by deepspring on 2009-03-18
> **ushills said:**
> Changing those comment lines won't do anything.

Perhaps you meant to uncomment by removing the #.

Startupmanager does make things easy.

Changing those lines does two 2 things...
1. It locks alternative boot options (recovery mode).
2. It locks booting into old (kernel) menu options.

Without those two options set, you can still boot password less into recovery modes, and old kernel recovery modes (I have tested without these options with the password field set, and I can still boot into recovery mode without seeing a single password prompt).

They are meant to remain commented out. This is from the menu.lst file:
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

```

The options are automatically included when you run "update-grub".

Google explained this to me.

---

### Post by deepspring on 2009-03-18
> **nelskurian said:**
> Sorry dude..I know its someway heavy...Their is no nedd to tell the whle story.Now their is simple graphical tool called startup manager.

```
sudo aptitude install startupmanager
```

Then, you can access it via System, Administration, Startup-Manager.

From here, it is easy to set options such as how long to wait before booting (timeout), as well as many display options. The other tabs allow you to customize the GRUB menu colors and theme, password protection, and specifying which entries will be visible. It is even possible to change the Ubuntu image that is displayed while things are loading. A nice little tool to completely theme your desktop.Also we can remove the recovery mode from the grub menu.


just igrnore my previous short story,since ubuntu always make matters simple..

Thanks, will use that in future.

---

### Post by bodhi.zazen on 2009-03-18
FYI: You can lock down grub, set a BIOS or GRUB password, etc and I would not discourage you from doing so if it makes you happy.

I would, however, like to point out that this offers very little protection and these things are easily defeated.

Far better, IMO, to encrypt your installation and personal data.

---

### Post by deepspring on 2009-03-18
**100% FIXED!**

I was talking to some friends on IRC, and they suggested that I crack open a terminal window on do the following:
```
sudo passwd root
```
After a restart, the recovery shell now asks me to enter roots password before allowing shell access.

Consider the case closed. :D

---

### Post by bodhi.zazen on 2009-03-18
I hope your friends on IRC also explained the fact that you have now opened a potentially larger security hole.

Setting a root password as you have is also easily defeated and, IMO, you have actualy reduced your security.

You are losing the forest for the trees, not seeing the bigger picture. Physical access is just bad news and, IMO, you have made the situation worse.

IMO you should use the alternate CD and install an encrypted system. This not only accomplishes your goal, but does so in a way that actually increases security.

---

### Post by deepspring on 2009-03-18
> **bodhi.zazen said:**
> Far better, IMO, to encrypt your installation and personal data.
I use truecrypt. It can be installed in seconds, the container files are portable, and its simple to use.

It's a pitty that there is no easy way to create encrypt partitions during the installation of Ubuntu. Instead you have to have follow this overly complex and convoluted [[guide](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)] (assuming your you can actually access the internet to read it while running the Server Install Disc :rolleyes: ).

---

### Post by bodhi.zazen on 2009-03-18
> **deepspring said:**
> It's a pitty that there is no easy way to create encrypt partitions during the installation of Ubuntu. Instead you have to have follow this overly complex and convoluted [[guide]("https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid")] (assuming your you can actually access the internet to read it while running the Server Install Disc :rolleyes: ).

That is not true. An encrypted installation is a piece of cake, you use the alternate CD.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

---

### Post by deepspring on 2009-03-18
> **bodhi.zazen said:**
> I hope your friends on IRC also explained the fact that you have now opened a potentially larger security hole.

Setting a root password as you have is also easily defeated and, IMO, you have actualy reduced your security.

You are losing the forest for the trees, not seeing the bigger picture. Physical access is just bad news and, IMO, you have made the situation worse.

Gee I'm sorry!

I am looking at the bigger picture, but I fail to see how setting a very strong root password (something like "es!4(arLz13.GH") for a currently passwordless recovery console lowers security more than having no password at all. It seems the opposite to me.

> **bodhi.zazen said:**
> IMO you should use the alternate CD and install an encrypted system. This not only accomplishes your goal, but does so in a way that actually increases security.

Well sadly for me, I didn't know that you could even create encrypted file systems in Ubuntu via the Alternate CD. And after reading up on it (wiki), I don't think I'll even bother attempting it after seeing how difficult it actually is to get setup.

Hopefully ability to create encrypted partitions quickly and easily will be a feature included in one of the next versions of Ubuntu Live/Install CD.

At the moment, I'll stick to using portable Truecrypt containers for sensitive data.

---

### Post by deepspring on 2009-03-18
> **bodhi.zazen said:**
> That is not true. An encrypted installation is a piece of cake, you use the alternate CD.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

Why the frell isn't this on the Wiki?!?

---

### Post by bodhi.zazen on 2009-03-18
> **deepspring said:**
> I am looking at the bigger picture, but I fail to see how setting a very strong root password (something like "es!4(arLz13.GH") for a currently passwordless recovery console lowers security more than having no password at all. It seems the opposite to me.

The big picture is that no matter what password you set on your BIOS / grub / or root, if I have physical access I can have full access to your system quite fast and I would not want you to fool yourself into feeling that somehow you have fixed the complications that physical access imply.

Most exploits target the root account, and so keeping it locked makes a lot of sense.

IMO you should look at things like encryption.

---

### Post by deepspring on 2009-03-18
> **bodhi.zazen said:**
> The big picture is that no matter what password you set on your BIOS / grub / or root, if I have physical access I can have full access to your system quite fast and I would not want you to fool yourself into feeling that somehow you have fixed the complications that physical access imply.

Not everyone in this world knows how to use a live disc to access a linux install and by pass authentication procedures. In fact there are very very few people who do. My setting a root password is my attempt at stopping the average joe/jill (the kind that doesn't carry a BackTrack CD) with only very basic knowledge from accessing a gaping security hole.

> **bodhi.zazen said:**
> Most exploits target the root account, and so keeping it locked makes a lot of sense.

Locking the root account is what I've done, and its all I wanted to do.

> **bodhi.zazen said:**
> IMO you should look at things like encryption.

When the next version of Ubuntu is officially released next month, I will look at using the Alternate CD method to install partition encryption. I prefer to fresh installs rather than upgrades (things break less).

I prefer to use truecrypt for the moment, as I can easily backup the encrypted volumes to an external disk or dvd drive in their encrypted form and open them later.

---

### Post by bodhi.zazen on 2009-03-18
he he he, just wondering (I am playing devils advocate, not really giving you a hard time, just trying to teach you a few "simple" tricks that IMO can really pay off for you.)

so you think the average joe/jill knows how to boot to recovery mode and enter Linux commands at the command prompt but not boot a live cd ?

The average jill/joe will be clueless at the command prompt.

IMHO, I think it is safe to assume anyone who can crack your system by booting to the recovery mode probably knows how to boot a linux live cd.

If you do not like the recovery mode, just remove the stanzas from /boot/grub/menu.lst

As you do so, note the syntax of the stanzas and you can manually boot to recovery mode if you wish (or use a live CD).

Truecrypt is a great tool.

---

### Post by deepspring on 2009-03-18
> **bodhi.zazen said:**
> If you do not like the recovery mode, just remove the stanzas from /boot/grub/menu.lst

As you do so, note the syntax of the stanzas and you can manually boot to recovery mode if you wish (or use a live CD).

LOL!

Then I'd be stuck.

---

### Post by bodhi.zazen on 2009-03-18
Naw, we can show you how

look at the kernel line

boot normally, hit esc to get teh grub screen, hit e to edit the kernel line, add in a few things at the end of the line (look at /boot/grub/menu.lst I will spoon feed you only so much :lolflag: )

then boot.

---

### Post by hyper_ch on 2009-03-19
Installing a fully encrypted system is not difficult. Have a look at my little guide:  [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

Beginning from 9.04 you can even encrypt swap with a random key (which is still bugged in 8.04 and 8.10).

---

