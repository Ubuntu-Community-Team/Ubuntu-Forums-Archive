---
title: "Firefox keeps opening PHP files with Screem"
date: 2008-06-06
forum: Server Platforms
---

### Post by Browser_ice on 2008-06-06
I have just isntalled PHP5 and Screem. Everytimes when I try to open a PHP file with Firefix, it asks me if I want to open it with Screem or something else.

How can I tell Firefox to always open PHP files itself ?

I have looked at Screem's preferences and do not see a file association to remove PHP.

---

### Post by NilsE on 2008-06-06
Two ways

When you get the prompt to open it with screem or something else select what you want to open it with and below select the option to do that every time. If what you want is not on the list go to /usr/bin and find the executable for the program you want.

OR

Go into edit > preferences > applications (inFF3) or contents (in FF2) and set php files to open with whatever you want.

---

### Post by Browser_ice on 2008-06-06
> **NilsE said:**
> Two ways

When you get the prompt to open it with screem or something else select what you want to open it with and below select the option to do that every time. If what you want is not on the list go to /usr/bin and find the executable for the program you want.

OR

Go into edit > preferences > applications (inFF3) or contents (in FF2) and set php files to open with whatever you want.

When the popup "open a file" showed up for a PHP file, I clicked Firefox as the default application to choose and told it to do it automaticly. But now, when I open a PHP file, Firefox goes into an endless loop of creating a new tab and trying to open the file again.

In my Edit/Preference I do not have an "applications" tab. I do have a "contents" tab but in the "File List" section, there is nothing about PHP.

Before installing PHP and Screem, I had never opened a PHP file with Firefox (recent Ubuntu install).

---

### Post by quelx on 2008-06-06
You probably have not installed **libapache2-mod-php5** or it is not enabled on your server.```
a2enmod php5
```

The server doesn't know how to process the file so it's just sending the source to the client rather than actually parsing it into something the browser understands.

---

### Post by Browser_ice on 2008-06-06
The libapache2-mod-php5 is installed and so is Apache2 but I haven't configured nor enabled (I think) Apache2.

Do I type the a2enmod php5 into my terminal console or in Apache2 ?

I have never used Apache2. I was told I needed it to run PHP5 with mysql.

---

### Post by quelx on 2008-06-06
in the terminal, ```
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

---

### Post by Browser_ice on 2008-06-06
root@browserice-desktop:~# sudo a2enmod php5
This module is already enabled!
root@browserice-desktop:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                      [ OK ]
root@browserice-desktop:~#

---

### Post by quelx on 2008-06-06
So that didn't work?

check your */etc/apache2/mods-avaliable/php.conf* for
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

If it's there then try pasting that code into */etc/apache2/apache2.conf* and restart **apache2**

---

### Post by ubunewbee on 2008-06-07
Hi,

I am actually having exactly the same issue; I opened apache2.conf in a text editor window, pasted the code:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

after:

ServerRoot "/etc/apache2"

Could not save the file /etc/apache2/apache2.conf.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I am trying to setup:

Apache2, MySQL and PHP in order to run a web server.  Any help would be appreciated.

Thanks,

Bill

---

### Post by quelx on 2008-06-07
You must edit system wide configuration files with elevated permissions, eg **sudo**

```
sudo nano -w /etc/apache2/apache2.conf
```

**Only if** you've tried the suggestions in the previous posts in this thread, add those two lines at the **bottom** of the file and ```
sudo /etc/init.d/apache2 restart
``` this is not a real fix but a hack, **a2enmod** is *supposed* to make **php5** work

---

### Post by L a r r y on 2008-06-07
> **Browser_ice said:**
> I have just isntalled PHP5 and Screem. Everytimes when I try to open a PHP file with Firefix, it asks me if I want to open it with Screem or something else.

How can I tell Firefox to always open PHP files itself ?

I have looked at Screem's preferences and do not see a file association to remove PHP.
--
You are evidently trying to directly load a php script file into Firefox.  FF is going to want to open this in a PHP editor.

You need to configure a Web server to parse PHP, and serve it as a rendered HTML page, with your browser pointing to an IP address, localhost or other domain name belonging to the server.

Screem looks like a good editor, which performs nicely on my Ubuntu 6.06 install on an Intel computer, but here under Ubuntu 8.04 on this AMD system, it exhibits a number of bugs as have been reported by others in the Screem bug-tracking system.

Larry
[Edit]*I should have read further into the thread before posting.  it seems a number of people already had answered the question!*[/edit]

---

