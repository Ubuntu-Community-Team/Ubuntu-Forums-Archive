---
title: "DAV problem. ALMOST there...."
date: 2008-12-05
forum: Server Platforms
---

### Post by jamieh on 2008-12-05
My total geek tutor wants me to make a CalDAV so he can post due dates and stuff and have it sync to my iCal.

I am almost done making WebDAV work. I followed [this]("http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622") guide, and it seemed to work okay. When I connect to the the DAV folder, I am prompted for a username and password. I was never asked to create a user or password in the tutorial. How do I make one, or see what the current one is?

I have used DAV a lot, but I have never had to start one myself, so I am a bit of a n00b at this.

Thanks

---

### Post by volkswagner on 2008-12-05
I think the instructions were not for the newbie.  I had a hard time with the password/user section.

From the how=to:
> 
#  Setup Authentication and Add Users
WebDAV can open your web server up to security risks. You don't want just anyone to wander in and change your files! There are several ways you can do authentication for your WebDAV directory, but htpasswd is the easiest and probably best for most cases. We'll make the passwords using MD5 and store them where we store the apache configurations and add an initial user while we're at it.


htpasswd -m -c /etc/apache2/.htpasswd 

For help use:

```
htpasswd -h
```

This will show you the format and options.  Depending on how you want to setup security/encryption (md5, plain text, SHA, etc.) your commands will vary. 

To use MD5 and allow for prompt on password use the following.

```
sudo htpasswd -m -c /etc/apache2/.htpasswd username
```

Replace "username"  with the actual user you want to create.

Notice the -c creates the file.  Only use it for the first entry.

---

### Post by jamieh on 2008-12-05
> **volkswagner said:**
> I think the instructions were not for the newbie.  I had a hard time with the password/user section.

From the how=to:


For help use:

```
htpasswd -h
```

This will show you the format and options.  Depending on how you want to setup security/encryption (md5, plain text, SHA, etc.) your commands will vary. 

To use MD5 and allow for prompt on password use the following.

```
sudo htpasswd -m -c /etc/apache2/.htpasswd username
```

Replace "username"  with the actual user you want to create.

Notice the -c creates the file.  Only use it for the first entry.

Okay thanks :)

Lets say I want to make another DAV folder. Is it the same user/password for all of them, or can I make different ones?

---

