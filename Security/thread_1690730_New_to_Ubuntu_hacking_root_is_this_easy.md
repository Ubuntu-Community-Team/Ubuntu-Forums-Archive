---
title: "New to Ubuntu: hacking root is this easy?"
date: 2011-02-18
forum: Security
---

### Post by visual1ce on 2011-02-18
I was just wondering if it is really so easy to hack root: [http://social.microsoft.com/Forums/en/learningresources/thread/3a410e46-fb3e-44c0-92ad-957e6dfc2db5](http://social.microsoft.com/Forums/en/learningresources/thread/3a410e46-fb3e-44c0-92ad-957e6dfc2db5)

Here are the instructions verbatim:

When you want to log on to a linux machine and you dont know any password then here is a way to do it
At the login prompt just reboot the system
When a blue sort of screen comes
in which there is the name of your operating system written
This is called the grub screen
just press e
you will get a new list
go second item of the list and just press e
now some text will be displayed
remove all the rubbish written in front of / and just type single there and then press the escape key
and then press b
then another prompt will apear
type passwd there
it will ask for new password
now just give and after that type exit at the terminal
you are done

I'm migrating to ubuntu and I'm certain there are measures one may take to eliminate this issue although I wonder if ubuntu is vulnerable to this method 'out of the box'.

Also, thanks to the moderators and contributors for this website; it is an excellent resource for newbies like me.

---

### Post by whatthefunk on 2011-02-18
> **visual1ce said:**
> I was just wondering if it is really so easy to hack root: [http://social.microsoft.com/Forums/en/learningresources/thread/3a410e46-fb3e-44c0-92ad-957e6dfc2db5](http://social.microsoft.com/Forums/en/learningresources/thread/3a410e46-fb3e-44c0-92ad-957e6dfc2db5)

Here are the instructions verbatim:

When you want to log on to a linux machine and you dont know any password then here is a way to do it
At the login prompt just reboot the system
When a blue sort of screen comes
in which there is the name of your operating system written
This is called the grub screen
just press e
you will get a new list
go second item of the list and just press e
now some text will be displayed
remove all the rubbish written in front of / and just type single there and then press the escape key
and then press b
then another prompt will apear
[SIZE=4]**type passwd there**[/SIZE]
it will ask for new password
now just give and after that type exit at the terminal
you are done

I'm migrating to ubuntu and I'm certain there are measures one may take to eliminate this issue although I wonder if ubuntu is vulnerable to this method 'out of the box'.

Also, thanks to the moderators and contributors for this website; it is an excellent resource for newbies like me.

Where did this password come from?

---

### Post by Bernie Gallagher on 2011-02-18
I just tried that and it didn't work for me.

Now, that said, the only absolutely 100% safe way to protect your data is to encrypt your hard drive.  Regardless what OS you use, if your HD is unencrypted, all anyone has to do is remove the drive from your computer, put it in an external USB drive enclosure, and plug it into another computer that uses the same OS to access it as an external drive.

---

### Post by mikewhatever on 2011-02-18
Physical access means root access. No need to 'hack' anything, just boot from a live cd.

---

### Post by visual1ce on 2011-02-18
Thanks for your replies.

I do intend to encrypt with dm-crypt and alternate installation CD so I guess this way my data will be safe. But what if someone accesses root via physical access and installs some kind of keylogger or programme that records my encryption passphrase the next time I enter it? If they have root access they also have access to logs so I might not be able to tell if someone has indeed logged on...

I'm probably getting way ahead of myself though. I'm going to install 10.10 alternate and tinker around.

---

### Post by Am Elder on 2011-02-18
I'm far from a computer expert of any kind, but I understand this goes for Windows as much as for Linux.  Unrestricted physical access gives an attacker free reign.  

According to [wikipedia]("http://en.wikipedia.org/wiki/Physical_access"),
And to [Microsoft support]("http://support.microsoft.com/kb/818200"), and [technet]("http://technet.microsoft.com/en-us/library/cc722487.aspx#EIAA").

Maybe encryption is pretty secure, as mentioned above.

---

### Post by cariboo on 2011-02-18
> **visual1ce said:**
> I was just wondering if it is really so easy to hack root: [http://social.microsoft.com/Forums/en/learningresources/thread/3a410e46-fb3e-44c0-92ad-957e6dfc2db5](http://social.microsoft.com/Forums/en/learningresources/thread/3a410e46-fb3e-44c0-92ad-957e6dfc2db5)

Here are the instructions verbatim:

When you want to log on to a linux machine and you dont know any password then here is a way to do it
At the login prompt just reboot the system
When a blue sort of screen comes
in which there is the name of your operating system written
This is called the grub screen
just press e
you will get a new list
go second item of the list and just press e
now some text will be displayed
remove all the rubbish written in front of / and just type single there and then press the escape key
and then press b
then another prompt will apear
type passwd there
it will ask for new password
now just give and after that type exit at the terminal
you are done

I'm migrating to ubuntu and I'm certain there are measures one may take to eliminate this issue although I wonder if ubuntu is vulnerable to this method 'out of the box'.

Also, thanks to the moderators and contributors for this website; it is an excellent resource for newbies like me.

those instruct are a little convoluted, it's much easier than that, just select recovery mode from the grub menu to get a root prompt, what you do from there is up to you.

It's almost as easy to do it in Windows 7 and Vista. Click Start and type cmd in the search box, next press Ctrl-Shift-Enter to open a prompt as an Administrator.

---

### Post by CharlesA on 2011-02-19
> **cariboo907 said:**
> 
It's almost as easy to do it in Windows 7 and Vista. Click Start and type cmd in the search box, next press Ctrl-Shift-Enter to open a prompt as an Administrator.

Didn't know that, might come in handy sometime. :D

In any case, physical access = root access. Even if you can't access the linux partition by dropping to a root shell, you can always just boot off a livecd to get to the file system (unless it's encrypted)

---

### Post by handy on 2011-02-19
You can password protect /boot can't you, which at least locks an unwanted user out of the Grub menu.

Though with the ease of getting there with a LiveCD (or whatever other type of media), it certainly makes is sound like if you truly have information on your machine that you don't want anyone to access you have to use encryption.

I'm glad I don't have to bother with all that mucking about.

---

### Post by jquis8411 on 2011-02-19
I was given a windows 7 machine last week that the previous owner had no need for and had long forgot the passwords to. Fifteen minutes later I had all the passwords and had it up and running with full admin access. If anyone can get their hands on any computer there is a way in.

---

### Post by Dave_L on 2011-02-19
> **visual1ce said:**
> ...hack root...
...eliminate this issue...
...if ubuntu is vulnerable...

That makes it sound like it's a security bug.

It's a supported, documented, feature of GNU/Linux.

---

### Post by SeijiSensei on 2011-02-19
> **handy said:**
> You can password protect /boot can't you, which at least locks an unwanted user out of the Grub menu.

You can also password-protect the BIOS on many machines so they never gets to boot.

---

### Post by arrrghhh on 2011-02-20
> **SeijiSensei said:**
> You can also password-protect the BIOS on many machines so they never gets to boot.

This is probably the "best" way you can truly secure physical access to the box, short of having it in a locked cabient.

If you're worried about people physically accessing and damaging/compromising your machine, perhaps you need to re-evaluate where you're placing this computer :p.

For laptops, if you are concerned about it getting out the BIOS password is a good method.  There's also software like TrueCrypt.

In addition to that, you can password-protect GRUB to prevent the "hack" that was listed in the first post.

---

