---
title: "Stop users saving network passwords"
date: 2009-08-01
forum: Security
---

### Post by petermck on 2009-08-01
Hi,
I'm helping a friend set up a couple of machines for work with Ubuntu 8.04 LTS. 
They already have a debian file server with SMB shares.
He wants to have a couple of SMB network shares that are visable to everyone but can only be accessed with the correct username & password.
Normally gnome panel offers a choice:-[LIST=1]
[*]Forget Password Immediately
[*]Remember password until you logout
[*]Remember forever
[/LIST]
I want there to be no save password options so when they have finished using that share and close it anyone without the password cannot open it. It's OK if this is system wide. We're not planning on using home folders in Samba. There will be a couple of webDAV folders and I would like to deny the ability to save passwords for these to.
Does anyone know a way to do this?

---

### Post by Agent ME on 2009-08-01
Are users sharing an account? Because otherwise I can't see how this would be an issue; if user A sets it to remember his password, user B won't be able to retrieve that remembered password.

---

### Post by petermck on 2009-08-02
All staff have access to 3 PC's in the office, it's not a 1 PC per person kind of an organization and people are usually not at their desks. Most information is not sensitive, but there are a couple of staff who need access to information that is sensitive. Everything is stored on a network server. Ideally what I want is a network folder of some kind that you need a password to open and when you close it you need a password to open it again. If the password cannot be saved that's good enough. There is no desire to go to having users with their own computer and login or screensavers, in fact that would disrupt the way they run the business.

---

### Post by Kurgan_it on 2010-05-18
I need exactly the same thing: a way to remove the "remember forever" option. No solutions yet?

Thanks.

---

### Post by HermanAB on 2010-05-18
Linux is a multi-user system.  In order to function securely, it needs to operate with one account per user and people have to log out and log in.  If you don't do that, then there is no real security, so there would not be much point in doing what you propose, since it will not really improve the security.

---

### Post by lavinog on 2010-05-18
I think the issue is that the system is being used as a public or guest system, where setting up a separate user account for every possible user would be impossible to manage.

I am not exactly sure how to go about this yet, but I would suspect that there is a way to purge remembered passwords with a routine script.
You could also look in gconf-editor

---

### Post by teh_drizzle on 2010-05-18
Is it "remembered" by gnome-keyring?

Maybe you could disable the keyring and see if it still prompts for a "remember password"?

[http://ubuntuforums.org/showthread.php?t=796410](http://ubuntuforums.org/showthread.php?t=796410)

---

### Post by Kurgan_it on 2010-05-18
My workstations are "guest-only" systems at a school where I have only one user per workstation that does also auto-login. Then I have about 50 users on a file server that have "personal" data on it. When these users need their data, they can access them from the public workstations by entering their username and password, then they logout from the workstations to "forget" the password.

This is a setup that allows me to have the workstations easily available for 1000 students that store their data on personal USB keys, and for 50 teachers that have an account on a Samba server, that they also access from Windows and MAC computers (some of these are their own notebooks, not property of the school).

This setup is the simplest to manage, and allows for enough security (given that we do not have anything that is really secret), but I'd like to avoid someone setting "remember forever" by mistake.


I have looked at gconf-editor, but I was not able to find some key that sounds like it does such a thing.

I think the passwords are stored in gnome-keyring, I could disable it, but it should be better to leave it alone and just remove the choice from the menu... if it's possible.

---

