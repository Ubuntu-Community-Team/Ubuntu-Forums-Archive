---
title: "VirtualBox 2.1 in Synaptic..."
date: 2008-12-30
forum: Virtualisation
---

### Post by akelsall on 2008-12-30
Anyone know when the newest version of VirutalBox will be availbe via Synaptic? I've tried following the instructions to compile the OSE version on VirtualBox's website, but I'm running into problems. It'd be nice to install this with Synaptic.

Andy

---

### Post by solwic on 2008-12-30
> **akelsall said:**
> Anyone know when the newest version of VirutalBox will be availbe via Synaptic? I've tried following the instructions to compile the OSE version on VirtualBox's website, but I'm running into problems. It'd be nice to install this with Synaptic.

Andy

Virtualbox.org should have a .deb file that you can just double click and choose "Install package"

[http://download.virtualbox.org/virtualbox/2.1.0/virtualbox-2.1_2.1.0-41146_Ubuntu_intrepid_i386.deb](http://download.virtualbox.org/virtualbox/2.1.0/virtualbox-2.1_2.1.0-41146_Ubuntu_intrepid_i386.deb) for the 8.10 version of the non-OSE

I guess you still have to compile OSE from source as yet...but the non-OSE is just as good (I think it adds USB support, doesn't it?)

Good luck.

---

### Post by akelsall on 2008-12-30
I should have mentioned I tried the .deb file initially, but couldn't get Vbox to launch (got a couple of different error messages), so I thought I'd try the other route.

Thanks,

Andy

---

### Post by howefield on 2008-12-30
Post the errors here, chances are high that you can get them sorted easily and quickly.

---

### Post by solwic on 2008-12-30
> **akelsall said:**
> I should have mentioned I tried the .deb file initially, but couldn't get Vbox to launch (got a couple of different error messages), so I thought I'd try the other route.

Thanks,

Andy

Post the error messages here...they'll help diagnose the problem.  

The two key things you must do with Virtualbox is install the Kernal (which the .deb should have done for you) and add yourself to the virtualbox users group.  

I don't know the CLI, but: 

System -> Administration -> Users and Groups

Click the "Unlock" button and type in your password

Click "Manage Groups"

Scroll down until you see "vboxusers" (mine is at the very bottom)

Highlight it, and then click the "Properties" button

In the Group Members box, check the box next to your user name (leave root blank)

Then use Ctrl + Alt + Backspace and log in again.  

That's the most common problem I've seen, anyway.  

Good luck!

---

### Post by akelsall on 2008-12-30
I'll reinstall the .deb package and post the error messages under a different thread (so as not to confuse the topic). Thanks for everyone's feedback.

Andy

---

### Post by akelsall on 2008-12-30
Well, I re-installed the .deb package, rebooted, and now it works! (and I don't have to use sudo anymore. I just go to Applications | System Tools | Sun xVM VirtualBox). 

I'm not sure about this, but I think what "may" have helped is a command I ran when trying to compile the new vbox 2.1 myself (from Virtualbox.org's web site). I have no idea what this command does, but it took forever to complete. Here it is. Could this have done anything to help the .deb package install properly the second time around?


```
apt-get install gcc g++ bcc iasl xsltproc uuid-dev zlib1g-dev libidl-dev \
                libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev \
                libasound2-dev libstdc++5 libhal-dev libpulse-dev libxml2-dev \
                libxslt1-dev python2.5-dev libqt4-dev qt4-dev-tools libcap-dev
```

---

### Post by mikewhatever on 2008-12-30
No. That command installs a bunch of packages needed to compile stuff, completely irrelevant to the regular .deb installation. It is safe to remove them unless you want more things compiled.

---

### Post by akelsall on 2008-12-30
That's good to know. Since I have no clue where these where installed, is there an easy way to remove them, without messing up my vbox install?

Thanks,

Andy

(I know we're getting off topic here. If I need to start a new thread, please advise).

---

### Post by EightBitHustler on 2008-12-30
Slightly off topic, I tried VBox 2.1 on a Macbook Pro and ran 8.10 server on it. I found the whole experience very buggy and crash prone. 

I haven't tried running it on my Ubuntu host machine yet.

---

### Post by solwic on 2008-12-30
> **akelsall said:**
> That's good to know. Since I have no clue where these where installed, is there an easy way to remove them, without messing up my vbox install?

Thanks,

Andy

(I know we're getting off topic here. If I need to start a new thread, please advise).

You should be able to take the list of packages and do a 

```

sudo apt-get remove package1 package2 package3

```

and so on.  

Giving you:

```

sudo apt-get remove gcc g++ bcc iasl xsltproc uuid-dev zlib1g-dev libidl-dev \
                libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev \
                libasound2-dev libstdc++5 libhal-dev libpulse-dev libxml2-dev \
                libxslt1-dev python2.5-dev libqt4-dev qt4-dev-tools libcap-dev

```

based on the list in your post.  

Glad you got it working.  :)

---

### Post by akelsall on 2008-12-31
jrock612, thanks for the info. I'll give that a shot this weekend. I don't know what that command does, but it makes sense "reversing" what I did earlier. 

This won't have any impact on the .deb file I installed for v2.1.0, will it?

Andy

---

### Post by physeetcosmo on 2009-01-09
> **akelsall said:**
> Well, I re-installed the .deb package, rebooted, and now it works! (and I don't have to use sudo anymore. I just go to Applications | System Tools | Sun xVM VirtualBox). 

I'm not sure about this, but I think what "may" have helped is a command I ran when trying to compile the new vbox 2.1 myself (from Virtualbox.org's web site). I have no idea what this command does, but it took forever to complete. Here it is. Could this have done anything to help the .deb package install properly the second time around?


```
apt-get install gcc g++ bcc iasl xsltproc uuid-dev zlib1g-dev libidl-dev \
                libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev \
                libasound2-dev libstdc++5 libhal-dev libpulse-dev libxml2-dev \
                libxslt1-dev python2.5-dev libqt4-dev qt4-dev-tools libcap-dev
```

Thankyou so much! i ran the block of 'dependency packages' that is in the tutorial for compiling my own VirtualBox2.1 package but i never ran across this other command.
What this command does is install dependencies for the application to work properly. Remember, Linux is a huge compilation of tiny packages of C library and header files that do fairly 'simple' tasks. Linux combines all these tiny tasks to perform larger more complex tasks.

Thanks again for the command!

-Dustin:wink:

---

### Post by ngpsaki4 on 2009-01-09
[posted as new thread]

[http://ubuntuforums.org/showthread.php?p=6522191#post6522191](http://ubuntuforums.org/showthread.php?p=6522191#post6522191)

---

