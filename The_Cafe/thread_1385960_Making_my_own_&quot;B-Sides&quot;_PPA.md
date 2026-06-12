---
title: "Making my own &quot;B-Sides&quot; PPA"
date: 2010-01-20
forum: The Cafe
---

### Post by humphreybc on 2010-01-20
You all know of the B-Sides project, right?

How can I make my own one, with my own applications?

Currently I use a script to install everything and configure a new system. See attached.

It's certainly not complete or perfect, I'm always improving it. What do you guys think?

---

### Post by Tibuda on 2010-01-20
> **humphreybc said:**
> You all know of the B-Sides project, right?
no

> How can I make my own one, with my own applications?
I'm not sure, but do you mean how to create your own custom Live CD? Remastersys!
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
[http://sites.google.com/site/masonux/home/notes-to-myself](http://sites.google.com/site/masonux/home/notes-to-myself)

> Currently I use a script to install everything and configure a new system. See attached.

It's certainly not complete or perfect, I'm always improving it. What do you guys think?

Nice script. I would replace some apps, but that's personal choice.

---

### Post by humphreybc on 2010-01-20
[http://www.ubuntugeek.com/b-sides-get-applications-that-didn&#8217;t-make-the-ubuntu-cd.html](http://www.ubuntugeek.com/b-sides-get-applications-that-didn&#8217;t-make-the-ubuntu-cd.html)

[http://www.linux-magazine.com/Online/News/Ubuntu-s-B-Sides-Alternative-Apps](http://www.linux-magazine.com/Online/News/Ubuntu-s-B-Sides-Alternative-Apps)

[https://edge.launchpad.net/b-sides](https://edge.launchpad.net/b-sides)

---

### Post by 23meg on 2010-01-20
AFAIK all you have to do is branch the b-sides project on Launchpad, make your changes to the "minimal-all" file and push it to a PPA.

---

### Post by humphreybc on 2010-01-23
Okay... I've tried to do that... but it's wtf hard.

So I've branched the B-sides bzr branch into a folder called "PPA" in my home directory. I went into ~/PPA/b-sides and changed the list of applications to install.

Because I want my PPA to contain another thing, my install script (see first post) I modified the directory structure like this:

~/PPA/benjaminppa/b-sides
~/PPA/benjaminppa/install-script

.. Inside the b-sides one is just everything from the B-Sides project, except that I've changed the list of applications to my own one. Inside "install-script" is just my install script.

I set up a [PPA on launchpad]("https://edge.launchpad.net/~humphreybc/+archive/humphreybc") and then tried to figure out how to upload to it using the [mess]("https://help.launchpad.net/Packaging/PPA/Uploading") [that is]("https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage") the [documentation.]("https://wiki.ubuntu.com/PackagingGuide/Basic")

First it tells me:

> 
You can upload packages to this PPA using:


```

dput ppa:humphreybc/humphreybc <source.changes>

```

... So I try that and put "Initial upload" as my "source changes" - little did I know that this is meant to be a *file* - not a change, like the bzr commit as I'm used to. So I clicked to read some more and was greeted with this complicated way of trying to build something from source.

Ugh! Help!

---

### Post by altonbr on 2010-02-26
> **humphreybc said:**
> You all know of the B-Sides project, right?

How can I make my own one, with my own applications?

Currently I use a script to install everything and configure a new system. See attached.

It's certainly not complete or perfect, I'm always improving it. What do you guys think?

I thought you'd be interested in my 'Ubuntu Assistant' script.. it does pretty much exactly what your's does!

"Project"
------------
[http://brettalton.com/?page=computer_services&subpage=ubuntu_assistant](http://brettalton.com/?page=computer_services&subpage=ubuntu_assistant)
[http://ubuntuforums.org/showthread.php?t=972037](http://ubuntuforums.org/showthread.php?t=972037)

Karmic Shell Scripts
------------------------
[http://brettalton.com/docs/ubuntu_assistant/karmic.sh](http://brettalton.com/docs/ubuntu_assistant/karmic.sh)
[http://brettalton.com/docs/ubuntu_assistant/karmic-brett.sh](http://brettalton.com/docs/ubuntu_assistant/karmic-brett.sh)

It seems like there is a need for a post-installation program in Ubuntu eh? I really think this stuff should get taken care of _during_ the installation however...

Maybe a project to tackle after Ubuntu Manual gets released?

---

### Post by nilarimogard on 2010-02-26
To build and upload bsides, all you have to do (after modifying it) is to add your last changes in the "changelog" file (which is found in the debian folder) and your name and email must be identical to the ones provided when creating your GPG key (see [HERE]("http://www.webupd8.org/2010/01/how-to-create-your-own-gpg-key.html") how to create one)

 "cd" to its folder and then run:
```
debuild -S -sa
```Then create a file in your home folder called ".dput.cf" and paste this in it:
```
[your_ppa_name]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~your_launchpad_id/your_ppa_name/ubuntu/
login = anonymous
allow_unsigned_uploads = 0
```Only change "your_ppa_name", and "your_launchpad_id/your_ppa_name" and save it.

Then run: 

dput your_ppa_name bsides.changes


That's it :)

P.s.: to work without a password you have to set up a SSH key with Launchpad too.

---

### Post by FuturePilot on 2010-02-26
> **nilarimogard said:**
> To build and upload bsides, all you have to do (after modifying it) is to add your last changes in the "changelog" file (which is found in the debian folder) and your name and email must be identical to the ones provided when creating your GPG key (see [HERE]("http://www.webupd8.org/2010/01/how-to-create-your-own-gpg-key.html") how to create one)

 "cd" to its folder and then run:
```
debuild -S -sa
```Then create a file in your home folder called ".dput.cf" and paste this in it:
```
[your_ppa_name]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~your_launchpad_id/your_ppa_name/ubuntu/
login = anonymous
allow_unsigned_uploads = 0
```Only change "your_ppa_name", and "your_launchpad_id/your_ppa_name" and save it.

Then run: 

dput your_ppa_name bsides.changes


That's it :)

P.s.: to work without a password you have to set up a SSH key with Launchpad too.

You don't need an SSH key to upload to a PPA. It authenticates by verifying the signature on the upload with your gpg key.

---

### Post by humphreybc on 2010-02-26
> **altonbr said:**
> I thought you'd be interested in my 'Ubuntu Assistant' script.. it does pretty much exactly what your's does!

"Project"
------------
[http://brettalton.com/?page=computer_services&subpage=ubuntu_assistant](http://brettalton.com/?page=computer_services&subpage=ubuntu_assistant)
[http://ubuntuforums.org/showthread.php?t=972037](http://ubuntuforums.org/showthread.php?t=972037)

Karmic Shell Scripts
------------------------
[http://brettalton.com/docs/ubuntu_assistant/karmic.sh](http://brettalton.com/docs/ubuntu_assistant/karmic.sh)
[http://brettalton.com/docs/ubuntu_assistant/karmic-brett.sh](http://brettalton.com/docs/ubuntu_assistant/karmic-brett.sh)

It seems like there is a need for a post-installation program in Ubuntu eh? I really think this stuff should get taken care of _during_ the installation however...

Maybe a project to tackle after Ubuntu Manual gets released?

Hey thanks, I'll take a look. Haha, perhaps - although we have big things planned for UMP after Lucid ;)

---

### Post by nilarimogard on 2010-02-27
> **FuturePilot said:**
> You don't need an SSH key to upload to a PPA. It authenticates by verifying the signature on the upload with your gpg key.

You are most probably right, I didn't remember exactly why I set up the ssh key :D

---

