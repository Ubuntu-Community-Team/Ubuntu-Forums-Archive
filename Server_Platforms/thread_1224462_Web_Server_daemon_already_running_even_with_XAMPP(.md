---
title: "Web Server daemon already running even with XAMPP(lampp) stopped"
date: 2009-07-27
forum: Server Platforms
---

### Post by absk on 2009-07-27
I recently installed xampp and it was all fine when suddenly it started acting strangely. When I try to start it, it says

```
myname-desktop:/opt/lampp/phpmyadmin$ sudo /opt/lampp/lampp startStarting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.

```

I checked the Synaptic package manager and none of Apache, PHP or MySQL was installed. Also, when I go to [http://localhost](http://localhost) it shows me the xampp screen. the phpinfo there shows that it is running from the xampp I just installed. So I stop XAMPP,

```
myname-desktop:/opt/lampp/phpmyadmin$ sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.7.1...
XAMPP: XAMPP-Apache is not running.
XAMPP: XAMPP-MySQL is not running.
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.

```

Even then, [http://localhost](http://localhost) continues to show the xampp screen.

I tried uninstalling it, it is then that localhost says 'not found'.

What is going on?

---

### Post by cdenley on 2009-07-27
It sounds like your servers are running, but the script can't access the PID's for some reason. Either kill the processes manually, or reboot your server. Even better yet, stick with supported ubuntu packages, and avoid third party software/packaging whenever possible.

---

### Post by absk on 2009-07-28
I had earlier installed php, mysql etc using the package manager, but removed them. Restarting worked! don't know how. But now there is a new problem. When I try to access phpmyadmin, instead of giving the phpmyadmin page, it give a dialog box for Opening / Saving the file. Otherwise, php files are being interpreted fine. Whats the problem? I switched to ubuntu just 3 days back, and can't get xampp running till now.

---

### Post by cdenley on 2009-07-28
> **absk said:**
> I had earlier installed php, mysql etc using the package manager, but removed them. Restarting worked! don't know how. But now there is a new problem. When I try to access phpmyadmin, instead of giving the phpmyadmin page, it give a dialog box for Opening / Saving the file. Otherwise, php files are being interpreted fine. Whats the problem? I switched to ubuntu just 3 days back, and can't get xampp running till now.

It sounds like apache doesn't have the php module enabled. If you're not running ubuntu's apache configuration, then I don't know the correct way for you to do it. That along with the conflict you previously encountered are two reasons to stick with the ubuntu repos.

---

### Post by YourSurrogateGod on 2011-10-24
When I go to localhost, this is what I see.
> Index of /
Name	Last Modified	Size	Type
Parent Directory/	 	-  	Directory
index.lighttpd.html	2011-Oct-21 23:45:05	3.4K	text/html
lighttpd/1.4.28

This is where I'm confused.  It should give me the XAMPP welcome page.

---

