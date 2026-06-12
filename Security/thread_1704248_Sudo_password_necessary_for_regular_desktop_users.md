---
title: "Sudo password necessary for regular desktop users?"
date: 2011-03-10
forum: Security
---

### Post by Rebelli0us on 2011-03-10
I've set up a user account for friends & colleagues that does NOT require a login password.

Unfortunately, in this OS some things don't work unless you login -- sudo ______

Must regular users have AND use Root's password?

---

### Post by nickleboyblue on 2011-03-10
The sudo command is one of the most important features of Ubuntu.  Without it, code would be able to execute without your permission, thus making it easy for a malicious programmer, of which there are many, to hijack your computer.

As for whether or not your users need the root password, not exactly.  With sudo, you can set them all up with their own account's password.  That password would be treated, in essence, like a root password if their account is an administrative one.  You can still set it up so that they don't have to enter a password to sign in, and still get the benefits of preventing dangerous system changes with sudo.

---

### Post by Rebelli0us on 2011-03-10
Thank you. This is what my users are getting:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=185655&stc=1&d=1299775397[/IMG]

or

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=185656&stc=1&d=1299775397[/IMG]

and since the device in question is THE MOUSE, all this "access denied" nonsense makes this machine useless. What's the solution?

---

### Post by aysiu on 2011-03-10
That's not normal. Something isn't configured right, either at a kernel level or in the Xorg config.

Is that the Wii remote?

Until you figure that out, a temporary workaround would be to just have that particular command not require a password.

**Edit the /etc/sudoers file**
Paste the command ```
sudo visudo
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal)

**Add in the nopasswd parameter**
Paste in the line ```
*username* ALL=(ALL)NOPASSWD:/usr/bin/wminput
``` where *username* is the username of the guest account. To double-check that the location of wminput is actually /usr/bin and not /bin or /sbin, you can run the command ```
locate wminput
``` or ```
which wminput
```

---

### Post by mimor on 2011-03-10
Your question resembles this already existing one:
[http://ubuntuforums.org/showthread.php?t=1624606](http://ubuntuforums.org/showthread.php?t=1624606)

Might be handy to check it out ;)

---

### Post by Rebelli0us on 2011-03-10
> **aysiu said:**
> That's not normal. Something isn't configured right, either at a kernel level or in the Xorg config.

Is that the Wii remote?

Thank you, I don't know Xorg from a hole in the ground. There is nothing of value in this machine so I don't want or need security of any kind. Of paramount importance is that the thing works, otherwise my friends press the Reset button and boot Windows.

Yes... it's the Wii remote.

---

### Post by aysiu on 2011-03-10
> **mimor said:**
> Your question resembles this already existing one:
[http://ubuntuforums.org/showthread.php?t=1624606](http://ubuntuforums.org/showthread.php?t=1624606)

Might be handy to check it out ;)
With all due respect, that has **nothing** to do with the problem in this thread.

---

### Post by Rebelli0us on 2011-03-10
> **aysiu said:**
> With all due respect, that has **nothing** to do with the problem in this thread.

Well... I might be a six-year old, you never know, lol

---

### Post by Rebelli0us on 2011-03-10
ok, using the command from above:

```

**locate wminput**
/etc/cwiid/wminput
/etc/cwiid/wminput/acc_led
/etc/cwiid/wminput/acc_ptr
/etc/cwiid/wminput/buttons
/etc/cwiid/wminput/default
/etc/cwiid/wminput/fps_config
/etc/cwiid/wminput/gamepad
/etc/cwiid/wminput/ir_ptr
/etc/cwiid/wminput/neverball
/etc/cwiid/wminput/nunchuk_acc_ptr
/etc/cwiid/wminput/nunchuk_stick2btn
/usr/bin/wminput
/usr/share/wminput
/usr/share/doc/wminput
/usr/share/doc/wminput/AUTHORS
/usr/share/doc/wminput/NEWS.gz
/usr/share/doc/wminput/README.gz
/usr/share/doc/wminput/Xmodmap
/usr/share/doc/wminput/changelog.Debian.gz
/usr/share/doc/wminput/changelog.gz
/usr/share/doc/wminput/copyright
/usr/share/doc/wminput/wminput.list
/usr/share/man/man1/wminput.1.gz
/usr/share/wminput/plugins
/var/cache/apt/archives/wminput_0.6.00+svn201-2_amd64.deb
/var/lib/dpkg/info/wminput.conffiles
/var/lib/dpkg/info/wminput.list
/var/lib/dpkg/info/wminput.md5sums

```

confusing....

This visudo seems to be a config file. Where do I add the "username ALL=(ALL)NOPASSWD:/usr/bin/wminput"?

---

### Post by aysiu on 2011-03-10
> **Rebelli0us said:**
> ok, using the command from above:

```

**locate wminput**
/etc/cwiid/wminput
/etc/cwiid/wminput/acc_led
/etc/cwiid/wminput/acc_ptr
/etc/cwiid/wminput/buttons
/etc/cwiid/wminput/default
/etc/cwiid/wminput/fps_config
/etc/cwiid/wminput/gamepad
/etc/cwiid/wminput/ir_ptr
/etc/cwiid/wminput/neverball
/etc/cwiid/wminput/nunchuk_acc_ptr
/etc/cwiid/wminput/nunchuk_stick2btn
/usr/bin/wminput
/usr/share/wminput
/usr/share/doc/wminput
/usr/share/doc/wminput/AUTHORS
/usr/share/doc/wminput/NEWS.gz
/usr/share/doc/wminput/README.gz
/usr/share/doc/wminput/Xmodmap
/usr/share/doc/wminput/changelog.Debian.gz
/usr/share/doc/wminput/changelog.gz
/usr/share/doc/wminput/copyright
/usr/share/doc/wminput/wminput.list
/usr/share/man/man1/wminput.1.gz
/usr/share/wminput/plugins
/var/cache/apt/archives/wminput_0.6.00+svn201-2_amd64.deb
/var/lib/dpkg/info/wminput.conffiles
/var/lib/dpkg/info/wminput.list
/var/lib/dpkg/info/wminput.md5sums

```

confusing....

This visudo seems to be a config file. Where do I add the "username ALL=(ALL)NOPASSWD:/usr/bin/wminput"?
```
sudo visudo
``` is the command you paste in in order to edit the /etc/sudoers file

In that file, just add in a new line anywhere with ```
*username ALL=(ALL)NOPASSWD:/usr/bin/wminput*
``` Based on the output you posted, it definitely seems it's in /usr/bin/wminput

---

### Post by Rebelli0us on 2011-03-10
> **aysiu said:**
> ```
sudo visudo
``` is the command you paste in in order to edit the /etc/sudoers file

In that file, just add in a new line anywhere with ```
*username ALL=(ALL)NOPASSWD:/usr/bin/wminput*
``` Based on the output you posted, it definitely seems it's in /usr/bin/wminput

Thank you, this worked. I still have to run:

```
gksudo "wminput -d -c ir_ptr D8:6B:F7:60:94:1B"
```

.. but there is no prompt for password. So I put it in the "Startup Applications". Success! 

I hope this post helps many others too. The Wii is very popular with gamers (which I'm not!) and that means less market share for Windowz.

---

### Post by Rebelli0us on 2011-03-12
I also found what seems to be an alternate way of using the Wii remote without constantly logging in. I haven't tried it, posting here for anyone searching, or anyone that can explain: 

```
sudo sh -c "echo KERNEL==\"uinput\", MODE:=\"0666\" > /etc/udev/rules.d/wiiemote.rules" 
```

This creates some kind of "rule" that allows any user to access the Wiimote without having to constantly login as Root. I wish Linux wasn't so arcane, but it's still fun.

---

