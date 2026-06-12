---
title: "Gnome keyring - Arbitrary aplication can see unlocked keyring items"
date: 2012-04-25
forum: Security
---

### Post by ivan15 on 2012-04-25
Hello,

I was going to write some python script, which would work with gnome keyring, according to this article:
[http://www.mindbending.org/bending-gnome-keyring-with-python-part-2/](http://www.mindbending.org/bending-gnome-keyring-with-python-part-2/)

But when I tried that example, I was able to get stored secrets from any unlocked keyring using python console without user confirmation. I tried this on ubuntu 11.10 and 10.04 - same behavior.

I have some passwords stored in keyrings, that are not automatically locked. Please, is there any way to make this at least as secure, as it is in thath article - so when application tries to access items in keyring it has not created a confirmation windows is displayed.

Thanks,
Ivan

---

### Post by OpSecShellshock on 2012-04-25
I think the only way to do that would be to set a different password for unlocking the keyring than the one for authenticating the user at the beginning of a session. This comes with other costs, as everything that invokes the keyring (like access to a wireless AP or using a desktop email client) will prompt for the keyring password.

---

### Post by zombifier25 on 2012-04-25
> **ivan15 said:**
> Hello,

I was going to write some python script, which would work with gnome keyring, according to this article:
[http://www.mindbending.org/bending-gnome-keyring-with-python-part-2/](http://www.mindbending.org/bending-gnome-keyring-with-python-part-2/)

But when I tried that example, I was able to get stored secrets from any unlocked keyring using python console without user confirmation. I tried this on ubuntu 11.10 and 10.04 - same behavior.

I have some passwords stored in keyrings, that are not automatically locked. Please, is there any way to make this at least as secure, as it is in thath article - so when application tries to access items in keyring it has not created a confirmation windows is displayed.

Thanks,
Ivan
If you run the script inside a user's account then the keyring for that user is already unlocked. If you want to read other user's keyring, you must give a password.

---

### Post by OpSecShellshock on 2012-04-25
> **zombifier25 said:**
> If you run the script inside a user's account then the keyring for that user is already unlocked. If you want to read other user's keyring, you must give a password.

Actually yes, I forgot about that. Even if it is different than the user's password for the system itself, it is still the case that if one application authenticates against the keyring, it might remain unlocked for all applications that use it from that point on. To be honest I haven't really messed around with that because if there's an active session going on at my computer, that means I'm sitting here anyway.

---

### Post by ivan15 on 2012-04-26
> **OpSecShellshock said:**
> Actually yes, I forgot about that. Even if it is different than the user's password for the system itself, it is still the case that if one application authenticates against the keyring, it might remain unlocked for all applications that use it from that point on.

Yes, it is the same for me as you said. But on that link, I have posted before, if an application tries to access an item created by another aplication, a confirmation prompt is displayed to user. It means, that application can normally access only items created by that application. But the screenshots are from Ubuntu 9.X I think. I would like to have behavior like that in my Ubuntu 11.10 (and 12.04).

> **OpSecShellshock said:**
> To be honest I haven't really messed around with that because if there's an active session going on at my computer, that means I'm sitting here anyway.

Yes, but if an inexperienced user runs a malicious program, it could obtain his stored secret stuff without any problems. If it was like on that link, user confirmation would be required for the malicious program to access keyring.

---

### Post by CivilizationII on 2012-04-26
> **ivan15 said:**
> Hello,

I was going to write some python script, which would work with gnome keyring, according to this article:
[http://www.mindbending.org/bending-gnome-keyring-with-python-part-2/](http://www.mindbending.org/bending-gnome-keyring-with-python-part-2/)

But when I tried that example, I was able to get stored secrets from any unlocked keyring using python console without user confirmation. I tried this on ubuntu 11.10 and 10.04 - same behavior.

I have some passwords stored in keyrings, that are not automatically locked. Please, is there any way to make this at least as secure, as it is in thath article - so when application tries to access items in keyring it has not created a confirmation windows is displayed.

Thanks,
Ivan


This is _exactly_ the way keyring is supposed to work... and not surprisingly works ;-)

Keyring is a mechanism provided to avoid writing password in script or program. To do that, the "extra" passwords are stored in hashed form, and are "released" (*) by keyring once you have provided your login password. 

In fact, this is the same way an encrypted home partition is working, once you're logged on, all your files doesn't look anymore encrypted (*) for any of your program, and obviously you don't need to provide a password each times you want to access one of your files (this would be very painful anyway ;-)). So you even don't need a "malicious program" (**), if you are fool enough to borrow an open session, using either keyring or encrypted home, to a "friend" (or simply forgetting to lock your session when searching for a coffee), then _all_ of your security is instantly vanished ;-)

(*) Please note a subtle difference between encrypted home and keyring: you _must_ explicitly call gnome keyring to read the value of a password. In particular, this mean that you can protect the access to keyring itself via pam (a little bit painful, but very effective).

(**) That said, you're right, a malicious program also can do the job.

Another drawback is while keyring is releasing the value of your password for you only, you must take extra care when using it either in script or program, for not displaying the value of the passwords in the system log, and obviously clearing the memory used to temporarily accept this value in script or program. 

To sum up you're right, this can be a very dangerous feature if used by not very healthy environment _and_ very healthy user. In fact this is one of the worst danger: a false sense of security. That said, if you understand the full mechanism and all of its constraints, it is a wonderful tool, i'm using it heavily.

---

