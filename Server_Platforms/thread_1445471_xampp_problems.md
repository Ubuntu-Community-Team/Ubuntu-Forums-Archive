---
title: "xampp problems"
date: 2010-04-02
forum: Server Platforms
---

### Post by tamobe on 2010-04-02
I'm trying to run Xampp so that I can test Drupal out. I'm running Lucid Lynx Beta. I'm having a lot of trouble getting Xampp to run. I downloaded Xampp version 1.7.3a and installed it but when I type [http://localhost](http://localhost) in Firefox to see if Xampp is working it just says:

> It Works!
This is the default web page for this server.
 The web server software is running but no content has been added,  yet.
Anyone have any suggestions help?

---

### Post by cdenley on 2010-04-02
> **tamobe said:**
> 
Anyone have any suggestions help?

Yes. Stick with the repos!
```

sudo apt-get install drupal6

```
You will have to undo all the non-ubuntu stuff you did first, though.

---

### Post by tamobe on 2010-04-02
Thanks for the tip.  But now when I try to finish the installation of Drupal in Firefox by typing in: [http://localhost/drupal/install.php](http://localhost/drupal/install.php) it just gives me:

> **[SIZE=1]Not Found[/SIZE]**

 [SIZE=1]The requested URL /drupal/install.php was not found on this server.[/SIZE]
  [SIZE=1]Apache/2.2.14 (Ubuntu) Server at localhost Port 80[/SIZE]

I tried to use these instructions: [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by cdenley on 2010-04-03
[http://localhost/drupal6/install.php](http://localhost/drupal6/install.php)

---

### Post by tamobe on 2010-04-03
ah yes - that makes sense. And it worked - thank you so much for your help.

I have another quick question - it has asked me to update from drupal 6.15 to 6.16. I downloaded the file but now I'm not sure where to put it/how to actually update it.

---

### Post by cdenley on 2010-04-03
> **tamobe said:**
> I have another quick question - it has asked me to update from drupal 6.15 to 6.16. I downloaded the file but now I'm not sure where to put it/how to actually update it.

I would just wait for it to be updated in the repos, although it does have some critical security fixes.
[https://bugs.launchpad.net/ubuntu/+source/drupal6/+bug/539747](https://bugs.launchpad.net/ubuntu/+source/drupal6/+bug/539747)

---

