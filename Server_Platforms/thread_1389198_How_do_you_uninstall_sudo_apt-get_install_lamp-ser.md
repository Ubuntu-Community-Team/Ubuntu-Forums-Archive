---
title: "How do you uninstall sudo apt-get install lamp-server^"
date: 2010-01-24
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-01-24
Hi, I've been searching around the net how to do this but I can't find any clues. I did this:

```
sudo apt-get install lamp-server^
```

But now I want to remove it. I've read this: [http://ubuntuforums.org/showthread.php?t=510403]("http://ubuntuforums.org/showthread.php?t=510403")

It seems it's **dangerous** to do this: ```
sudo tasksel remove lamp-server
```

---

### Post by Barriehie on 2010-01-24
I've installed like that and then removed via:
```

sudo tasksel

```
and selected it to remove.  I couldn't get any of it to work via the install.  I had better luck installing the individual packages and configuring as I went.

---

### Post by AlexanderDGreat on 2010-01-24
> I couldn't get any of it to work via the install. What do you mean you couldn't get any of it to work via the install?

> I had better luck installing the individual packages and configuring as I went. So sudo apt-get install lamp-server^ is a bad command? I just want a simple LAMP server, but after doing lamp-server^ I thought how do you uninstall this thing? Is it possible? Is the tasksel safe? So do I really have to install them one by one? In Linux, Apache2, MySQL, PHP? Thanks for replying.

---

### Post by Cheesemill on 2010-01-24
To uninstall you can do:
```
sudo tasksel remove lamp-server
```

Also I use 'sudo apt-get install lamp-server^' all the time and have never had any problems with it.

---

### Post by AlexanderDGreat on 2010-01-24
Hi Cheesemill, yea, I also heard that sudo tasksel remove lamp-server will do its job, however upon reading this: [http://ubuntuforums.org/showthread.php?t=510403]("http://ubuntuforums.org/showthread.php?t=510403") go to Post#5 and others confirming it as well, that this command will remove other stuff from your Ubuntu as well. Can you clear up the confusion?

---

### Post by Barriehie on 2010-01-24
> **AlexanderDGreat said:**
> What do you mean you couldn't get any of it to work via the install?

I mean apache2 wasn't serving up pages!

> **AlexanderDGreat said:**
>  So sudo apt-get install lamp-server^ is a bad command? Not necessarily, it just didn't work for me.

> **AlexanderDGreat said:**
>  I just want a simple LAMP server, but after doing lamp-server^ I thought how do you uninstall this thing? Is it possible? Is the tasksel safe? So do I really have to install them one by one? In Linux, Apache2, MySQL, PHP? Thanks for replying.

Use tasksel, if I recall correctly on the help page it has instructions for uninstalling if you change your mind about the install and if you run into problems I'm sure we can fix them!

Barrie

---

### Post by AlexanderDGreat on 2010-01-25
@Barriehie - thanks for the info, I guess I'm gonna read this to be sure: ApacheMySQLPHP Community Documentation: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Barriehie on 2010-01-25
> **AlexanderDGreat said:**
> @Barriehie - thanks for the info, I guess I'm gonna read this to be sure: ApacheMySQLPHP Community Documentation: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

That's the page I used.  I've developed the habit after installing anything to open the file /root/.synaptic/log and copy out the list of installed files for a particular app. and save that in ~/installs/PackageName.  Worst case scenario with this file I can then turn into a shell script to remove exactly what was installed.  I had an issue with removing a package once and that file allowed me to proceed.

Piece of cake making the LAMP package work.  After you get the packages installed you'll have to edit, from the top of my head, **/etc/hosts**, **/etc/hosts.allow**, **/etc/hostname**, **/etc/apache2/ports.conf**, **/etc/apache2/apache2.conf**, and the files in **/etc/apache2/sites-available** and **/etc/apache2/sites-enabled**.
If you've done this before then disregard; I see no point in playing richochet rabbit trying to figure out why [http://localhost/](http://localhost/) or [http://mydomain.name.???:SomePort#/](http://mydomain.name.???:SomePort#/) doesn't work. :)

I'm currently using no-ip.com for DNS forwarding.  I've used dyndns in the past but got bamboozled trying to find where on their web page to set my port# for forwarding.

Also, if you're going to add 'dummy' sites to localhost you'll have to add
**search localhost.localdomain** to **/etc/resolv.conf** i.e. if you want 127.0.0.2 = somesitename.whatever

HTH,
Barrie

---

