---
title: "Request: mail-notification 1.1"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-06-15
This is in breezy.  I'm currently using 1.0 in hoary but it has crashed on me a couple of times and I've read 1.1 solves some of these issues.

---

### Post by ow50 on 2005-06-15
If this is about the crashing with Gmail, I tried the breezy version, and it crashed just the same as the hoary version.

---

### Post by Technoviking on 2005-06-15
I will look at this.

Mike

---

### Post by Mez on 2005-06-15
[QUOTE=McQuaid]This is in breezy.  I'm currently using 1.0 in hoary but it has crashed on me a couple of times and I've read 1.1 solves some of these issues.[/QUOTE]
 uplaoded to staging

---

### Post by McQuaid on 2005-06-15
thanks i'll grab it now.

---

### Post by fishfork on 2005-06-20
Is SSL support enabled in this version?

---

### Post by shanghaipi on 2005-06-22
I think that it has to do with Gmail changing its server name or something.  This is happening to every Gmail checker out there.  The firefox plugin is the only one that has fixed this problem that I know of.  Though, could be wrong.

---

### Post by christooss on 2005-06-22
[QUOTE=shanghaipi]I think that it has to do with Gmail changing its server name or something.  This is happening to every Gmail checker out there.  The firefox plugin is the only one that has fixed this problem that I know of.  Though, could be wrong.[/QUOTE]
 Does someone has a soluiton for this. Now my Firefox doesnt ork either.

---

### Post by shanghaipi on 2005-06-22
Did you go and try to update it at Mozilla.org?  They came out with a new version just yesterday I believe.

---

### Post by christooss on 2005-06-22
[QUOTE=shanghaipi]Did you go and try to update it at Mozilla.org?  They came out with a new version just yesterday I believe.[/QUOTE]
 Wierd I had version 4.3.x installed on mozilla.org 3.3.0 is avalible and its not workin either. Which version do you have. Can you post a link to it.

What about mail-notification.

---

### Post by christooss on 2005-06-22
[QUOTE=christooss]Wierd I had version 4.3.x installed on mozilla.org 3.3.0 is avalible and its not workin either. Which version do you have. Can you post a link to it.

What about mail-notification.[/QUOTE]
 Ok I found new gmail notifier

[http://www.extensionsmirror.nl/index.php?showtopic=394](http://www.extensionsmirror.nl/index.php?showtopic=394)

---

### Post by shanghaipi on 2005-06-22
That's weird, I just looked at the Firefox extension database and found 0.4.3 as well.  I do hope mail-notification gets fixed though.  As much as I like firefox, I agree with another person who said this ealier in the thread, I don't have firefox open all the time.  Plus I have 2 gmail accounts and would like to be able to check them simultaneously.  But patience is a virtue.

---

### Post by pangloss on 2005-06-24
SSL doesn't appear to be enabled.

The description of this package (as you see in Synaptic, for instance) needs to be changed to reflect this. The current description suggests that there is SSL support, when in fact it has been disabled. 

Frankly I wish we'd just work with the [other request](http://ubuntuforums.org/showthread.php?t=24768)  and provide an SSL enabled package, because otherwise, I find this package useless.


[QUOTE=fishfork]Is SSL support enabled in this version?[/QUOTE]

---

### Post by ntd on 2005-06-24
[QUOTE=pangloss]SSL doesn't appear to be enabled.

The description of this package (as you see in Synaptic, for instance) needs to be changed to reflect this. The current description suggests that there is SSL support, when in fact it has been disabled. 

Frankly I wish we'd just work with the [other request](http://ubuntuforums.org/showthread.php?t=24768)  and provide an SSL enabled package, because otherwise, I find this package useless.[/QUOTE]
 I know its not perfect; but, you can compile it and get SSL support if it is important to you, all it takes is you having the openssl-dev packages installed, the configure script will autodetect it...I have mine up with SSL support (as well as the newly changed gmail address :)), and although it  isn't as smooth as using DEBs, it works :)

---

### Post by christooss on 2005-06-24
Can you write how to do that. Both SSl support and new gmail address

---

### Post by pangloss on 2005-06-24
I just made a new deb package with SSL support, but I didn't fix the gmail server address. Can you detail where/how to fix the gmail bit? I was just about to post my .deb but I'll wait on this since gmail support is basically broken without.

[QUOTE=ntd]I know its not perfect; but, you can compile it and get SSL support if it is important to you, all it takes is you having the openssl-dev packages installed, the configure script will autodetect it...I have mine up with SSL support (as well as the newly changed gmail address :)), and although it  isn't as smooth as using DEBs, it works :)[/QUOTE]

---

### Post by fishfork on 2005-06-25
I also ended up compiling it myself to get SSL working. I understand there are legal reasons why it's not enabled in the Debian version, but this shouldn't really affect the Ubuntu version, should it?

The right place to get this fixed would be the universe - is it worth asking the MOTU? In the meantime, a backports package would be great of course.

---

