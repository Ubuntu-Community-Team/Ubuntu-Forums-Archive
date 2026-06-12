---
title: "[SOLVED] Thunderbird 2.x anyone?"
date: 2007-08-14
forum: Repositories &amp; Backports
---

### Post by galvao on 2007-08-14
Ok, this most probably was already discussed here, but it's hard to search for it, since "2", "2." and "2.x" are too-vague terms to run.

I'd like to know when you guys plan to finally release a official, supported Thunderbird 2.x package. I mean it's been out there for quite a while... (please do notice that this is *NOT* criticism, just plain interest and curiosity...)

Thanks,

---

### Post by Seisen on 2007-08-14
Its in the Gutsy Repositories

---

### Post by galvao on 2007-08-14
Sorry for my ignorance, but could you please tell me how do I add this repository to the sources list?

Thanks (a lot) in advance,

---

### Post by walkerk on 2007-08-14
> **galvao said:**
> Sorry for my ignorance, but could you please tell me how do I add this repository to the sources list?

Thanks (a lot) in advance,

It's not a good practice to add a different version of Ubuntu's repositories. These programs have been compiled w/ a newer version of gcc amongst other things. 

A better practice would be to download the tarball from Mozilla and compile it yourself. If I remember correctly you don't have to compile Thunderbird, just extract it to where ever and run it:
```
/path/to/thunderbird
```

thunderbird is a shell script file.

---

### Post by Murrquan on 2007-08-14
I just had to deal with this today! I downloaded Thunderbird 1.x from the repositories, then found out it didn't have Gmail support. So I went and got 2.x from Mozilla.

> A better practice would be to download the tarball from Mozilla and compile it yourself.

Here are some [step-by-step instructions]("http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/") for how to do just that! I followed them, and they worked for me. Two modifications, though.

[LIST]
[*]In step two, where it says **# sudo tar -C /opt -zxvf ~/Desktop/thunderbird-***, replace ~/Desktop/thunderbird with ~/(the directory you downloaded the tarball to).
[*]For the script in step four, replace **Icon=/opt/thunderbird/icons/mozicon16.xpm** with **Icon=/opt/thunderbird/icons/mozicon50.xpm**. Otherwise it uses a smaller icon, which looks all blurry on the desktop.
[/LIST]

These are probably commonsense things for people used to the command line, and you probably didn't need the explanation, but I'm new at this and the above is what I figured out an hour or two ago. ^.^;

> Its in the Gutsy Repositories

Woot! Looking forward to the next release!

---

### Post by Seisen on 2007-08-14
> **galvao said:**
> Sorry for my ignorance, but could you please tell me how do I add this repository to the sources list?

Thanks (a lot) in advance,

Gutsy is the next release coming out in October so you follow Murrquan's directions on how to install the thunderbird tarball, do a dist-upgrade to Gutsy now or wait till October.

---

### Post by vendejp on 2007-08-18
Murrquan's instructions work, but how do i get my mail and addressbook from 1.x to 2.0?  Figuring out where my data and prefs are stored isnt intuitive.

Thanks

---

### Post by doncristobal on 2007-08-19
vendejp: [http://kb.mozillazine.org/Profile_backup](http://kb.mozillazine.org/Profile_backup) or [http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager) should help.

---

### Post by vendejp on 2007-08-19
Thanks doncristobal, that did it.

---

### Post by jrusso2 on 2007-08-19
An advantage to using the regular mozilla version of firefox and thunderbird is you can use the autoupdate and get updates much faster then waiting for the repository to get around to it.

---

### Post by nanotube on 2007-08-22
also see the ubuntuzilla project ([http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)) which automatically installs the mozilla builds of firefox, thunderbird, or seamonkey, and automatically notifies you of any future new releases.

---

### Post by z0mbie on 2007-08-23
**Get the repository key:**
```
wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
```

**Add these to your repositories: **[COLOR="YellowGreen"]**/etc/apt/sources.list**[/COLOR]
```
deb http://ubuntu.iuculano.it feisty thunderbird
deb-src http://ubuntu.iuculano.it feisty thunderbird
```

**Install thunderbird 2.0.0.5 :**
```
sudo aptitude update && sudo aptitude install mozilla-thunderbird
```

---

### Post by bluefightingcat on 2007-08-23
Hey,

Just use Ubuntuzilla. It's great. It will install the latest version of thunderbird (as well as Firefox etc.) automatically. It will also let you know when there are updates. 

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)


BFC

---

### Post by JustinForce on 2007-08-27
> **bluefightingcat said:**
> Hey,

Just use Ubuntuzilla. It's great. It will install the latest version of thunderbird (as well as Firefox etc.) automatically. It will also let you know when there are updates. 

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)


BFC

Exactly what I needed!

---

### Post by mlind on 2007-08-28
Here's yet another repo that contains newer thunderbird for Feisty
[http://ubuntuforums.org/showpost.php?p=2684517&postcount=5](http://ubuntuforums.org/showpost.php?p=2684517&postcount=5)

---

### Post by Cuppa-Chino on 2007-09-05
anyone got the enigmail working from [http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

I just does not work for me...

---

### Post by BoogieKnight on 2007-09-06
I downloaded the plugin directly off the developers website and it works fine for me
[http://enigmail.mozdev.org/download.html](http://enigmail.mozdev.org/download.html)



> **Cuppa-Chino said:**
> anyone got the enigmail working from [http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

I just does not work for me...

---

### Post by nikef on 2007-09-06
how can i just update thunderbird please 
using the terminal
i only need thunderbird updated not firefox
thank you :)

---

### Post by nanotube on 2007-09-06
> **nikef said:**
> how can i just update thunderbird please 
using the terminal
i only need thunderbird updated not firefox
thank you :)

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by nikef on 2007-09-06
> **nanotube said:**
> [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)


thank you :)

---

### Post by panayk on 2007-09-09
Hi, this is particularly towards the people who maintain personal repositories with Thunderbird...

What is the easiest/standard way to make a .deb out of the Mozilla tarball?
I have tried compiling from sources and when I finally succeed I discovered I had made a .deb with the installer... :)

So how can I safely make a .deb out of sources or the installer?

---

### Post by nikef on 2007-09-10
ok i have managed to install tb2  :)

but i still have tb1.5 on   :(

how do i import all my mail ,tried import but it gives another email account  :(

i do not need to import settings,as i have done this  :)

how do i get rid of tb1.5  :confused:

this is the link i used to download 

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by nanotube on 2007-09-10
> **nikef said:**
> ok i have managed to install tb2  :)

but i still have tb1.5 on   :(

how do i import all my mail ,tried import but it gives another email account  :(

i do not need to import settings,as i have done this  :)

how do i get rid of tb1.5  :confused:

this is the link i used to download 

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

you could try using ubuntuzilla to automate the install for you.

but maybe linking your ~/.mozilla-thunderbird dir to ~/.thunderbird will do the trick for getting your mail into tb2. the repositories version uses ~/.mozilla-thunderbird as the profile dir, while the mozilla version uses ~/.thunderbird.

---

### Post by nikef on 2007-09-10
> **nanotube said:**
> you could try using ubuntuzilla to automate the install for you.

but maybe linking your ~/.mozilla-thunderbird dir to ~/.thunderbird will do the trick for getting your mail into tb2. the repositories version uses ~/.mozilla-thunderbird as the profile dir, while the mozilla version uses ~/.thunderbird.

hi and thank you for replying

i do not understand,i am very new to ubuntu
could you explain in step by step please

---

### Post by nanotube on 2007-09-10
> **nikef said:**
> hi and thank you for replying

i do not understand,i am very new to ubuntu
could you explain in step by step please

hi,
the commands to link the profile would be:
```
mv ~/.thunderbird ~/.thunderbird.bak
ln -s ~/.mozilla-thunderbird ~/.thunderbird
```

---

### Post by nikef on 2007-09-11
> **nanotube said:**
> hi,
the commands to link the profile would be:
```
mv ~/.thunderbird ~/.thunderbird.bak
ln -s ~/.mozilla-thunderbird ~/.thunderbird
```


thanks for the commands

i have tried these in the terminal,but nothing happens

---

### Post by nikef on 2007-09-11
ok,thunderbird 1.5 will not open any way,so i will remove it in add and remove
hopefully  this wont cause any problems 

thanks

---

### Post by nanotube on 2007-09-11
> **nikef said:**
> ok,thunderbird 1.5 will not open any way,so i will remove it in add and remove
hopefully  this wont cause any problems 

thanks

if you remove it, you still have to link to your old profile for the new thunderbird to see it. did you try the commands i posted, did they work?

---

### Post by nikef on 2007-09-11
yes i tried commands in terminal.but nothing showed up

i have 2 entry's for thunderbird

1,this does not open
2 this opens up thunderbird 2

not sue what to do now
i have ubuntu installed,but use kubuntu
if this makes any different 

thanks for helping

---

### Post by nanotube on 2007-09-11
> **nikef said:**
> yes i tried commands in terminal.but nothing showed up

i have 2 entry's for thunderbird

1,this does not open
2 this opens up thunderbird 2

not sue what to do now
i have ubuntu installed,but use kubuntu
if this makes any different 

thanks for helping

what happens if you run thunderbird profile manager?
```
thunderbird -P
```
it should let you select a profile...

---

### Post by nikef on 2007-09-12
It opens up thunderbird 2

thanks

---

