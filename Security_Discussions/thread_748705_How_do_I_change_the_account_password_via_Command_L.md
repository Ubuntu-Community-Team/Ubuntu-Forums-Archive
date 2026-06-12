---
title: "How do I change the account password via Command Line?"
date: 2008-04-07
forum: Security Discussions
---

### Post by cleverest on 2008-04-07
How do I change the account 'ROOT' login password via the command line?  I haven't been able to figure this out and I need to know for both Kubuntu and Backtrack....everytime I try to use the GUI method it locks up on me...

Any help would be appreciated as I'm a complete and utter Linux Newbie and I'm trying to at least have that much security implemented while I learn things...

Thanks!

- Brett

---

### Post by aysiu on 2008-04-07
Apart from the fact that you shouldn't really give root a login password, my guess is that you're talking about the admin account that can temporarily assume root privileges, in which case this may help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by cleverest on 2008-04-07
> **aysiu said:**
> Apart from the fact that you shouldn't really give root a login password, my guess is that you're talking about the admin account that can temporarily assume root privileges, in which case this may help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The reason I'm trying to change the login name 'root' password is because I'm booting from a USB version of the software which is using a generic password and this just seems like a huge security hole....so I'd like to at least change that generic password to something else.

Thanks for the response!

---

### Post by aysiu on 2008-04-07
I'm still not getting how root plays a part in this. You can change the user password with the instructions I linked to earlier.

---

### Post by cleverest on 2008-04-07
> **aysiu said:**
> I'm still not getting how root plays a part in this. You can change the user password with the instructions I linked to earlier.

Well the OS is having me login AS ROOT and with a generic password...

Doesn't that mean I need to change that generic password since everyone else is logged in like that when they start using it as well?

Don't be surprised if I continue to sound like an idiot, because with Linux, I more or less am.  (I know how to do some data rescue as per my job though with the command line in Ubuntu if that makes me a wee bit smarter, lol)

instructions seem easy..I didn't know about the passwd command it all, lol...thanks!

---

### Post by aysiu on 2008-04-07
When you say you are booting from a USB version of the software, do you mean some kind of "live" version that is on a USB key instead of a CD?

Or do you mean it's an actual installation of Ubuntu? How do you know it's logging you in as root?

---

### Post by cleverest on 2008-04-07
> **aysiu said:**
> When you say you are booting from a USB version of the software, do you mean some kind of "live" version that is on a USB key instead of a CD?

Or do you mean it's an actual installation of Ubuntu? How do you know it's logging you in as root?

Well it's actually Backtrack 3  (USB "live" version, not an installation).

I do plan on doing the same thing with a portable "live" USB version of Kubuntu as well though, so I'm likely going to have the same problem there hence my posting here at this wonderfully helpful forum.

Am I completely out of my mind about this?  Sorry for all the confusion...still learning the terms and stuff...Please educate me, haha

---

### Post by aysiu on 2008-04-07
I don't really know much about Backtrack, but if it's anything like the live CD, it isn't the root account; it's a user called *ubuntu* that has *sudo* privileges (*sudo* allows the user to temporarily assume root-like privileges for certain tasks--you can read more about that [here](https://help.ubuntu.com/community/RootSudo)). The problem, from a security standpoint, is that this is effectively root (even though it technically isn't), since the live CD is set up not to require a password for *sudo* commands.

So, on an ordinary installation, you would use *sudo* to say, "Hey, for this command, can I be root for just a while?" and the computer will say, "Sure. What's your password?"

On a live CD, if you use *sudo*, the computer will just say, "Sure. Go for it" without prompting for a password.

I don't know how to change that behavior, apart from doing an actual installation.

---

### Post by sbenson on 2008-04-07
Just a pointer.

In Terminal:

You could do "sudo passwd" and enter a passwd.

This enables the root account for login in ubuntu.
I would say this is not always the best method.

"sudo -s" and then entering your user password will give you the root shell but still retain the no login status for root.

I would say this is preferable.

They went to a lot of trouble protecting people from themselves with the ` User only sudos vice root login` model. It is a great design. 

I wouldn't break it.

---

