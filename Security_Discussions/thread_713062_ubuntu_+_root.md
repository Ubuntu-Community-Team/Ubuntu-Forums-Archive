---
title: "ubuntu + root"
date: 2008-03-02
forum: Security Discussions
---

### Post by steeler on 2008-03-02
Hi I'm new to ubuntu and i find it very attracting and easy..
I've used debian and suse and i can say i like it more..

Except..
The root concept..
I don't like ubuntu's administration approach. And I've tried switching back to traditional root account.
I've given it a password and I've changed my sudoers by commenting out the last line.

Now i can login as root.
But what i want is to be able to do is to use sudo and gksu providing the ROOT password and not MINE.
Now as far as i have understood it asks for the root password but when i give it it simply crashes..Nothing happens. Neither does it say it's wrong nor it works..

---

### Post by pdub on 2008-03-02
If you are logging in a root, why would you need sudo or gksu?

---

### Post by tubezninja on 2008-03-02
> **steeler said:**
> 
But what i want is to be able to do is to use sudo and gksu providing the ROOT password and not MINE.

That's not how sudo is supposed to work.  On any distribtuion, actually.

The whole intent of sudo ([as per the dev website]("http://www.gratisoft.us/sudo/intro.html")) is not just to permit "sudoers" to perform adminsitrative tasks without invoking the root user, but also to provide an audit trail to clearly mark who did what and when.  You can't do that if the sudoer is always "root."  This isn't just an ubuntu thing, it's (supposed to be) the case on any *nix box that has sudo.

As an alternative, you could try su -c   or su -c -p instead, though obviously that would be a bit annoying to type all the time.

---

### Post by Oldsoldier2003 on 2008-03-02
> **steeler said:**
> Hi I'm new to ubuntu and i find it very attracting and easy..
I've used debian and suse and i can say i like it more..

Except..
The root concept..
I don't like ubuntu's administration approach. And I've tried switching back to traditional root account.
I've given it a password and I've changed my sudoers by commenting out the last line.

Now i can login as root.
But what i want is to be able to do is to use sudo and gksu providing the ROOT password and not MINE.
Now as far as i have understood it asks for the root password but when i give it it simply crashes..Nothing happens. Neither does it say it's wrong nor it works..
```
su root
``` gives you the functionality you are seeking. rather than debate the pros and cons I'll just say that sudo wont ask you for roots password it was designed to allow superuser privs without actually having the root password.

---

### Post by steeler on 2008-03-02
what i mean is for example when i run adept or synaptic i want it to ask for the ROOT password and not mine.

Like in EVERY other distribution i know. For example when u run yast in SuSE or synaptic in debian as a regular user it always asks for the root password.

and as far as i remember when i did sudo in debian or suse it asked for the root password.

ps: i understand the concept but anyway..i'd like to switch to the traditional way..

---

### Post by Oldsoldier2003 on 2008-03-02
> **steeler said:**
> what i mean is for example when i run adept or synaptic i want it to ask for the ROOT password and not mine.

Like in EVERY other distribution i know. For example when u run yast in SuSE or synaptic in debian as a regular user it always asks for the root password.

and as far as i remember when i did sudo in debian or suse it asked for the root password.

ps: i understand the concept but anyway..i'd like to switch to the traditional way..
sudo doesn't ask for the root password. sudo doesn't ask for the root password. sudo doesn't ask for the root password.

If you run synaptic as a user in the admin group it asks you for your admin password, because its actually being run by sudo.

If you insist on using the root password to run things you can either run them as root, or change your password to match the "root" password.

---

### Post by cdenley on 2008-03-03
You can add this to your default line in your sudoers file: "targetpw". I wouldn't recommend it, though. I believe what you call the "traditional" way is actually the unconfigured way. If you look at the sudoers file on your other distribution, it probably has a comment that tells you to remove "targetpw".

from suse:
```

# In the default (unconfigured) configuration, sudo asks for the root password.
# This allows use of an ordinary user account for administration of a freshly
# installed system. When configuring sudo, delete the two
# following lines:
Defaults targetpw    # ask for the password of the target user i.e. root
ALL ALL=(ALL) ALL # WARNING! Only use this together with 'Defaults targetpw'!

```
[http://www.suseforums.net/index.php?showtopic=37668](http://www.suseforums.net/index.php?showtopic=37668)

---

### Post by steeler on 2008-03-03
> **cdenley said:**
> You can add this to your default line in your sudoers file: "targetpw". I wouldn't recommend it, though. I believe what you call the "traditional" way is actually the unconfigured way. If you look at the sudoers file on your other distribution, it probably has a comment that tells you to remove "targetpw".

from suse:
```

# In the default (unconfigured) configuration, sudo asks for the root password.
# This allows use of an ordinary user account for administration of a freshly
# installed system. When configuring sudo, delete the two
# following lines:
Defaults targetpw    # ask for the password of the target user i.e. root
ALL ALL=(ALL) ALL # WARNING! Only use this together with 'Defaults targetpw'!

```
[http://www.suseforums.net/index.php?showtopic=37668](http://www.suseforums.net/index.php?showtopic=37668)

yep...guess u're right about  the unconfigured way.anyway thanks that's what i've been looking for :)
maybe i though it's the traditional because that's what i've encountered till now
i expected from debian to be a lot "unconfigured" but i didn't imagine that about suse
thanks again

---

### Post by bodhi.zazen on 2008-03-03
Personally I have toyed with targetpw as well, and IMO it is no better then setting a root password and disabling sudo ;)

To improve on it a little I disable root logins (changing root's shell to /bin/false).

Then you need to :

sudo /bin/bash

to get a root shell.

---

### Post by p_quarles on 2008-03-03
If you're just wanting to run the graphical programs with your root password using gksu, you'll need to change the configuration file in your user's home directory. Personally, I use kdesu, and the configuration file is here:
```
~/.kde/share/config/kdesurc
```
This file allows me to set the command (su or sudo) that the application uses to acquire root privileges.

---

### Post by aysiu on 2008-03-03
I don't know how to switch it over, but I know if you install Linux Mint, it asks if you want a traditional root/user model instead of the Ubuntu sudo model.

---

### Post by jrusso2 on 2008-03-03
As a long time Linux user I was really put off by the lack of root account in Ubuntu and the sudo alternative.

However I have gotten used to working that way and it does not bother me anymore.

I do continue to enable the root account however, even though I rarely use it just in case I need it.

---

