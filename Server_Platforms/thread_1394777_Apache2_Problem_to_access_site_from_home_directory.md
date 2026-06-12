---
title: "Apache2: Problem to access site from home directory"
date: 2010-01-31
forum: Server Platforms
---

### Post by Kdar on 2010-01-31
I used this tutorial to:
[http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/](http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/)

I set up directory in my home directory for web development.
I called it webdev and then created another inside of it, "site1", with a index.html

I created new file for this site in "cd /etc/apache2/sites-available" and added name of the site inside "sudo nano /etc/hosts"
and then later I reloaded/restated apache.

But... when I got to "http://sitename/" in my browser. I get 403 Forgiden error
```
Forbidden

You don't have permission to access / on this server.

Apache/2.2.12 (Ubuntu) Server at joomla Port 80
```

What can I do to fix this?

I did the same thing on my laptop and I never had such problems...
However on this computer, I have root and home on separate partitions. I am not sure if this is a problem?

---

### Post by Barriehie on 2010-01-31
Can't help you with the permissions issue but I do somewhat the same thing except I put symlinks in /var/www that point to the actual files in my home/dir.  The less I have to change the better!

HTH,
Barrie

---

### Post by Kdar on 2010-01-31
How did you create that link?

Can you still easily update your site's content without having root privileges?

---

### Post by Barriehie on 2010-01-31
> **Kdar said:**
> How did you create that link?

Can you still easily update your site's content without having root privileges?

To create the link I did this:
```

ln -s /home/barrie/www/**SomeFolderName** /var/www/**SomeFolderName**

```

This creates a soft link in the /var/www directory pointing to the actual folder in my home directory.

Yes, I can change the .html, .php, .css, .whatever files in ~/www/**SomeFolderName** and it doesn't affect the soft link pointing to those files.  This can be done with a 'normal' login because I'm editing files I own! If this isn't clear post back.

HTH,
Barrie

Edit: Links are cool because I've moved my ~/Pictures and ~/Music folders to another drive so I don't have to back them up.  I've got links to them in my root dir so the system *thinks* they're still in the original location.  This way I don't have to --exclude=**path/file** when I backup.

---

### Post by Kdar on 2010-02-02
mm
very strange. I did what you wrote.. but I still getting the permition errors:

> Forbidden

You don't have permission to access /joomla/ on this server.

Apache/2.2.12 (Ubuntu) Server at localhost Port 80

I might try to use link for my music and movies folders too, like you told. It sounds like good idea.

---

### Post by Barriehie on 2010-02-02
> **Kdar said:**
> mm
very strange. I did what you wrote.. but I still getting the permition errors:



I might try to use link for my music and movies folders too, like you told. It sounds like good idea.

What are your permissions for your joomla folder???

Barrie

---

### Post by jbruced on 2010-02-02
[QUOTE=Kdar;8751929]I used this tutorial to:
[http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/](http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/)

But... when I got to "http://sitename/" in my browser. I get 403 Forgiden error


was this a typo?

it should be typed in as "http://localhost/sitename/"


what happens when you go to

"http://localhost/"

?

---

### Post by Kdar on 2010-02-03
> **Barriehie said:**
> What are your permissions for your joomla folder???

Barrie

here: drwxr-xr-x 17 armen armen 4096 2010-02-02 17:26 joomla
(thats the folder inside my home, which is linked.

Permission for the link:
lrwxrwxrwx 1 root root   22 2010-02-02 18:01 joomla -> /home/armen/www/joomla


> **jbruced said:**
> [QUOTE=Kdar;8751929]I used this tutorial to:
[http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/](http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/)

But... when I got to "http://sitename/" in my browser. I get 403 Forgiden error

was this a typo?
it should be typed in as "http://localhost/sitename/"
what happens when you go to "http://localhost/"?[/QUOTE]

No, it wasn't typo. I set it up this way so it can be accessed like this, but just [http://sitename](http://sitename)
I created new site and enabled it. Like in that tutorial.
I had it like this on my laptop and everything works just fine.
But here it doesn't.
When I go to [http://localhost](http://localhost) it works.

---

