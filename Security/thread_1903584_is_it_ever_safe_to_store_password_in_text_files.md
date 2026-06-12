---
title: "is it ever safe to store password in text files?"
date: 2012-01-02
forum: Security
---

### Post by anon0 on 2012-01-02
I've run into programs that store passwords in plain text files, which seem risky to me. 

One advice I read was: "If you wish to store passwords in text files, you can set the permissions on these files to have no access for "group" and "other", and set the owner uid to the same uid that runs the application that needs to read the file. Then set that uid so that it cannot log in."

I'm new to the concept of UIDs so I'm not really sure what this accomplishes -- would it make it difficult for others to see the file without my user password, even if they have access to my hard drive? If so, instruction on how to do this would be welcome. Thanks.

---

### Post by Dangertux on 2012-01-02
> **anon0 said:**
> I've run into programs that store passwords in plain text files, which seem risky to me. 

One advice I read was: "If you wish to store passwords in text files, you can set the permissions on these files to have no access for "group" and "other", and set the owner uid to the same uid that runs the application that needs to read the file. Then set that uid so that it cannot log in."

I'm new to the concept of UIDs so I'm not really sure what this accomplishes -- would it make it difficult for others to see the file without my user password, even if they have access to my hard drive? If so, instruction on how to do this would be welcome. Thanks.

The answer to the original question is quite simply: no. 

That being said what the other example is saying is that if you absolutely HAVE to do it for some reason, you're basically limiting access to the file to the user, and anyone with root access, you could further this by using chattr to make the permissions immutable. 

That being said if you're having difficulty remembering passwords a much better alternative would be something like keepass or lastpass. 

For the final question, if the person has access to your hard drive, meaning physical access to the machine, none of these methods will really stop them from obtaining the passwords with the exception of something that encrypts them (like lastpass).

Hope this helps.

---

### Post by fdrake on 2012-01-02
> **anon0 said:**
> "If you wish to store passwords in text files, you can set the permissions on these files to have no access for "group" and "other", and set the owner uid to the same uid that runs the application that needs to read the file. Then set that uid so that it cannot log in."
It's as safe as keeping a piece of paper with your passwords written on it next to the monitor. :)

---

### Post by sisco311 on 2012-01-02
Thread moved to **Security Discussions**.

---

### Post by syerges on 2012-01-02
I think I need a new piece of paper with passwords on it taped to my screen! :D It really depends on who is in your house and what the passwords are for. I'm constantly asking my wife what my password is for this and that so she wrote them down for me. People who are in my office can log in to most of my stuff. I just keep the passwords for the important stuff locked away in my mind.

---

### Post by Grenage on 2012-01-03
> **anon0 said:**
> I've run into programs that store passwords in plain text files, which seem risky to me.

As other's have stated - no, it's not very secure.  Yes, you can set permissions that limit access to a file, but the client will generally have read access.

It's also worth mentioning that permissions are generally only respected by the OS which applied them. ;)

---

### Post by mattxhand on 2012-01-03
As with everyone elses' response, NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO NO AND NO.

Never ever store them in plain text. You can encrypt them like what Keypass does, but other than that, you are looking for trouble.

---

### Post by OpSecShellshock on 2012-01-03
> **fdrake said:**
> It's as safe as keeping a piece of paper with your passwords written on it next to the monitor. :)

Ha! actually, as long as you completely control access to the location of the piece of paper, it's safer.

---

### Post by tubbygweilo on 2012-01-04
IIRC some Black Hats may well be working on the remains of the old CIA funded Remote Viewing project....;)

---

### Post by Dangertux on 2012-01-06
> **tubbygweilo said:**
> IIRC some Black Hats may well be working on the remains of the old CIA funded Remote Viewing project....;)

They don't need to, you guys love VNC.

---

### Post by Soul-Sing on 2012-01-07
use a password manager as KeepassX or revelation.
make a truecrypt container, and put the databases into this container. three different passes are needed to access the stored passwords. 
1 truecrypt pass
2 admin/root pass
3 passmanager pass
you can even replace one pass with a static yubikey pass.

---

### Post by bluexrider on 2012-01-07
> **fdrake said:**
> It's as safe as keeping a piece of paper with your passwords written on it next to the monitor. :)
Set up a thumb drive with truecrypt so you can take it with you. Better than folding a piece of paper and stuffing it in your pocket. IMHO

---

