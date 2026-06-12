---
title: "Skype MID Ubuntu Moblin Remix"
date: 2009-10-01
forum: Ubuntu Moblin Remix
---

### Post by BanjoPants on 2009-10-01
Hi all,

Can anyone help me install Skype MID on the Dell Ubuntu Moblin Remix?  I am trying to follow the instructions provided here:

[https://developer.skype.com/MidSkype](https://developer.skype.com/MidSkype)

Ideally, and I know I'm asking a lot here, I want skype to start on bootup and be under the status tab on the top.  

As always, any help would be greatly appreciated.

---

### Post by om26er on 2009-10-05
why dont you install this 
[http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
and browse through terminal to its directory and type
sudo dpkg -i package name

---

### Post by matthewbpt on 2009-10-07
Or even better, try 'sudo apt-get install skype-mid' ,  you have to add the medibuntu repository first if you haven't already.

---

### Post by michael37 on 2009-12-21
> **BanjoPants said:**
> Hi all,

Can anyone help me install Skype MID on the Dell Ubuntu Moblin Remix?  I am trying to follow the instructions provided here:

[https://developer.skype.com/MidSkype](https://developer.skype.com/MidSkype)

Ideally, and I know I'm asking a lot here, I want skype to start on bootup and be under the status tab on the top.  

As always, any help would be greatly appreciated.

Sorry, just noticed your post.  Ubuntu binaries were built by Canonical and posted in their "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner" repository.  Yes, Jaunty, even if you are running Karmic. Google how to add this particular repo.

If else fails, download .deb directly from [http://archive.canonical.com/ubuntu/pool/partner/s/skype-mid/](http://archive.canonical.com/ubuntu/pool/partner/s/skype-mid/)

Btw, I prefer to use MidSkype over Skype 2.1 on any one of my computers...

---

