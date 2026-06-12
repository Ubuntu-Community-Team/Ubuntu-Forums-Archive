---
title: "Auto login/logout with USB stick (pamusb)"
date: 2009-12-08
forum: Security
---

### Post by Dr Small on 2009-12-08
I've been following [this post](http://joeb454.ubuntuforums.org/showpost.php?p=4284665&postcount=18), I have installed libpam-usb and pamusb-tools, added the following line to the end of my /etc/pam.d/common-auth:
```
auth    sufficient    pam_usb.so
```

Setup the device nickname and username, and even added the following to my /etc/pamusb.conf in the correct place:
```
        <agent event="lock">xscreensaver-command --lock</agent>
        <agent event="unlock">xscreensaver-command --deactivate</agent>

```

Here is what happens:
I unplug my USB stick, and xscreensaver locks the screen. Okay, this is what I wanted it to do. But when I reinsert the stick, nothing happens. If I try logging in from a TTY with the stick inserted, it still requires me to enter a password. (I am trying to set this up as a passwordless setup, and basically use my stick as my password. (Please let me take my own risks... I am just testing the setup)).

So here is what I would like to be preforming, but it is not, and I am stumped on how to fix it....

I want the screensaver to lock when I unplug the drive, and I want the screensaver to unlock when I reinsert the drive. (This is my primary goal). I would also like to be able to use the drive *as my password* for authentication with GDM, sudo, TTY logins, etc.

Is there something I have forgotten to do? The first part works fine (of locking the screen when the drive is removed), but I can't get the authentication process to work without a password, or even automatically log me in.

Best Regards,
Dr Small

---

### Post by Dr Small on 2009-12-08
I finally went back and read that post, and found one spot that I missed.. I was putting the new shared object at the bottom of the file, instead of ABOVE the other one, as was stated.. :S

So, here is my setup.
/etc/pam.d/common-auth has two lines that look like this:
```
auth    sufficient      pam_usb.so
auth    [success=1 default=ignore]      pam_unix.so nullok_secure

```

I created a couple startup items, such as:
```
pamusb-agent
xscreensaver -nosplash
```

Now, when I pull the pendrive, it locks the screen, and when I reinsert it, I unlocks it. Logging out to GDM, and entering my username automatically logs me in, and yet this setup still allows me to use my system in case I lose the key, I can still log in with my password. :)

---

### Post by bodhi.zazen on 2009-12-08
Very nice Doc

Next time, at least give us a chance to answer =)

---

### Post by Dr Small on 2009-12-08
> **bodhi.zazen said:**
> Very nice Doc

Next time, at least give us a chance to answer =)
Haha! Sorry about that bodhi ;) :p

---

