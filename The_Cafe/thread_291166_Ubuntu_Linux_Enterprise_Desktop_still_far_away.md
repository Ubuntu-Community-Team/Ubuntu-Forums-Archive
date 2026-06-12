---
title: "Ubuntu Linux Enterprise Desktop still far away?"
date: 2006-11-02
forum: The Cafe
---

### Post by rverrips on 2006-11-02
Man, I love Ubuntu!  It's neat, clean and snappy - It has everything I would like on my home-use laptop and with XGL it really makes my neighbours say "Wow, that's nice" ... However I still don't run it on an enterprise level at work?  Why am I still running SUSE on my PC at work? 

Yes, I use SUSE at work (not something from Redmond) and my upline roll their eye-balls when I start talking about Ubuntu ... 

So, no, this is not a debat between Gnome, KDE or their various themes and colour schemes ... 
No, I don't want to compare YAsT and Ubuntu Control panel ...
And no, the OpenSUSE and Ubuntu communities have nothing to do with it ... 

It's simply 'cause all the Enterprise app's we use are only available as rpms, and although with some time and effort they can be tweaked to run on Dapper, or even Edgy, it's still not a justifiable case for migrating and the vendors won't support an installation on Ubuntu.

So my question is this:

Which is more likely to occur first?  Ubuntu to have native support (I'm not simply talking "alien" here, but simply being able to type rpm -ivh at an Ubuntu console) for rpms from Oracle, IBM, Lotus, Novell, Checkpoint ... or are we waiting for those Enterprise vendors to start releasing and supporting their apps as deb's?  

I can't see either happening very soon to be honest, (aside from Oracle releasing 10g XE as deb, but nor for desktop use, more as server solution) so for the time being I guess I'll still be sitting in my SUSE / RedHat tower from 9 to 5 while I hack around in brown at home ...

---

### Post by hey_ian on 2006-11-02
> **rverrips said:**
> Man, I love Ubuntu!  It's neat, clean and snappy - It has everything I would like on my home-use laptop and with XGL it really makes my neighbours say "Wow, that's nice" ... However I still don't run it on an enterprise level at work?  Why am I still running SUSE on my PC at work? 

Yes, I use SUSE at work (not something from Redmond) and my upline roll their eye-balls when I start talking about Ubuntu ... 

So, no, this is not a debat between Gnome, KDE or their various themes and colour schemes ... 
No, I don't want to compare YAsT and Ubuntu Control panel ...
And no, the OpenSUSE and Ubuntu communities have nothing to do with it ... 

It's simply 'cause all the Enterprise app's we use are only available as rpms, and although with some time and effort they can be tweaked to run on Dapper, or even Edgy, it's still not a justifiable case for migrating and the vendors won't support an installation on Ubuntu.

So my question is this:

Which is more likely to occur first?  Ubuntu to have native support (I'm not simply talking "alien" here, but simply being able to type rpm -ivh at an Ubuntu console) for rpms from Oracle, IBM, Lotus, Novell, Checkpoint ... or are we waiting for those Enterprise vendors to start releasing and supporting their apps as deb's?  

I can't see either happening very soon to be honest, (aside from Oracle releasing 10g XE as deb, but nor for desktop use, more as server solution) so for the time being I guess I'll still be sitting in my SUSE / RedHat tower from 9 to 5 while I hack around in brown at home ...

It is indeed possible to install rpm and even yum on Debian. And that packages should be already installed as dependencies of alien. But RPM is a low-quality package format, which cannot be compared to the Debian packager. Anyway Debian is so powerful, that it even supports RPM. I do not recommend to install anything on a Debian system, where the powerful APT and dpkg are available, with rpm -ivh. It will bypass dpkg and the other thing is that there may be dependency problems as the RPM packager does not see all other libs installed with dpkg on your system.

Some of the firms you mentioned at the top of this post may release Debs in future. Novell will not do it since it is promoting RPM.

---

### Post by 3rdalbum on 2006-11-03
An Enterprise desktop is judged not on what packaging format it uses, but by the quality of its software, the available features for things that businesses need, the stability and the support options. Those are the things that make SLED so good.

---

### Post by rverrips on 2006-11-03
> **hey_ian said:**
> It is indeed possible to install rpm and even yum on Debian ....  there may be dependency problems as the RPM packager does not see all other libs installed with dpkg on your system.


Don't get me wrong, I agree that debs leave rpms for dust, but you've just confirmed my point - I've personally had success with all of those app's on Ubuntu (except the Checkpoint VPN) but it took some tweaking and googling and foruming, etc, i.e. not an enterprise solution, and as mentioned, the vendors state they only support Suse/Red Hat.

---

### Post by rverrips on 2006-11-03
> **3rdalbum said:**
> An Enterprise desktop is judged not on what packaging format it uses, but by the quality of its software, the available features for things that businesses need, the stability and the support options. Those are the things that make SLED so good.

Thanks for the reply 3rd-Al' - But it's exactly my point - I'm saying that my experience is that the software most enterprises need are only "officially" supported on rpms based distro's.  Perhaps we have to change the mindset of the Enterprises, as businesses that use MySQL for DB's and Dovecot/Evolution for Mail are all fine with Ubuntu as Desktop, but if you're looking to use Oracle, Lotus Notes, Groupwise, etc. you sorta either need to stick with Windows or goto SUSE/RedHat?

---

