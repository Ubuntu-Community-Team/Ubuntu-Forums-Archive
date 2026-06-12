---
title: "Auto Start XAMPP On Ubuntu Server"
date: 2007-06-17
forum: Server Platforms
---

### Post by UbuNewbie123 on 2007-06-17
I read the tutorial at XAMPP:

[http://www.apachefriends.org/en/faq-xampp-linux.html#fsl](http://www.apachefriends.org/en/faq-xampp-linux.html#fsl)

> There is no real standard way to configure the boot process of a Linux system, but most of them should allow you to start XAMPP at boot time using the following steps.

   1. First, find out your default runlevel.
      Simply type egrep :initdefault: /etc/inittab.
      You should no see a line containing a number between two colons.
      In most cases 3 or 5 (2 if you're using Debian).

   2. Go into the directory which configures this runlevel. If for example your runlevel is 3, then you have to change into the /etc/rc.d/rc3.d directory.

      If your system didn't provide /etc/rc.d/rc3.d please try also /etc/init.d/rc3.d and /etc/rc3.d.
   3. Now carry out the actual configuration by typing:

      ln -s /opt/lampp/lampp S99lampp
      ln -s /opt/lampp/lampp K01lampp

Now XAMPP should start and stop automatically if you boot or shutdown your machine.

I can find the "/etc/init.d/" folder but not the runlevel thing above. Any ideas on how to get this to work? The is rc.local file I think but not sure what to do with it.

---

### Post by UbuNewbie123 on 2007-06-17
Finally figured this out...

sudo ln -s /opt/lampp/lampp /etc/init.d/lampp
sudo update-rc.d -f lampp defaults

---

### Post by ImpelGD on 2007-06-25
Excellent! Thanks for posting the solution UbuNewbie123. :)

---

### Post by MattyGabe on 2008-04-10
I'm running Xubuntu (256MB RAM) and I need XAMPP to autostart.  I found this thread, and also the page off of ApacheFriends that is quoted above, yet the EGREP command doesn't work.  It's because UBUNTU doesn't have an rc.d directory, it's replaced by event.d/rc-default

So, can anyone verify the above information, provide more background?  What about UbuNewbie's solution?  I tried it and it did not work for my installation.  Here's what I propose to do (my Xubuntu installation is not with me at the moment so I can't attempt it):

1. egrep :initdefault: /etc/event.d/rc-default
2. cd /etc/rc_.d (where _ is replaced by the number in between colons in #1)
3. sudo ln -s /opt/lampp/lampp S99lampp
4. sudo ln -s /opt/lampp/lampp K01lampp
5. sudo update-rc.d -f lampp defaults

Yes? No?  I really don't understand what ln does or what S99lampp is supposed to do in conjunction with it, or what egrep's function really is either.

Any help is greatly appreciated.  Thanks!

---

### Post by MattyGabe on 2008-04-17
> **MattyGabe said:**
> I'm running Xubuntu (256MB RAM) and I need XAMPP to autostart.  I found this thread, and also the page off of ApacheFriends that is quoted above, yet the EGREP command doesn't work.  It's because UBUNTU doesn't have an rc.d directory, it's replaced by event.d/rc-default

So, can anyone verify the above information, provide more background?  What about UbuNewbie's solution?  I tried it and it did not work for my installation.  Here's what I propose to do (my Xubuntu installation is not with me at the moment so I can't attempt it):

1. egrep :initdefault: /etc/event.d/rc-default
2. cd /etc/rc_.d (where _ is replaced by the number in between colons in #1)
3. sudo ln -s /opt/lampp/lampp S99lampp
4. sudo ln -s /opt/lampp/lampp K01lampp
5. sudo update-rc.d -f lampp defaults

Yes? No?  I really don't understand what ln does or what S99lampp is supposed to do in conjunction with it, or what egrep's function really is either.

Any help is greatly appreciated.  Thanks!

I actually figured it out and UbuNewbie's solution actually did the trick.  I am not quite sure why it didn't work before, but it finally did this time around.

Thanks again!

Edit: I actually remember why - I have a multi-user installation in Xubuntu (it's in an office environment), so I had to select "multiuser" rather than "default" in the update-rc.d command.  So, it was essentially doing what I needed it to, but only for one user?  I believe that was the problem. 

sudo update-rc.d -f lampp multiuser

is what I believe I typed in.  It was a week ago, however, so I can't be 100% sure.

---

