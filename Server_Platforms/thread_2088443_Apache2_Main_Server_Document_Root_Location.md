---
title: "Apache2 Main Server Document Root Location"
date: 2012-11-26
forum: Server Platforms
---

### Post by BAWBCEN1TY on 2012-11-26
I am new to Linux/Ubuntu and was messing around with setting up Apache2 on Ubuntu 12.10. I had made a mistake writing down my IP address, and therefore, entered this incorrect address into the config files.

**#/etc/apache2/ports.conf**

[INDENT]NameVirtualHost 192.168.1.22:80

Listen 80
.
.
.[/INDENT]

**#/etc/apache2/sites-available/default**

<VirtualHost 192.168.1.22:80>

[INDENT]ServerAdmin webmaster@localhost

DocumentRoot /var/www/mysite (this exists)
.
.
.[/INDENT]
</VirtualHost>

**#/etc/apache2/sites-available/www.mysite.com**

<VirtualHost 192.168.1.22.:80>

[INDENT]ServerAdmin webmaster@localhost

ServerName [www.mysite.com](www.mysite.com)

DocumentRoot /var/www/mysite
.
.
.[/INDENT]
</VirtualHost>


Due to this IP being wrong, neither of the Virtual Hosts is triggered, but from what I understand, in a case like this Apache uses the settings of the Main Server (it loaded **/var/www/index.html**). 

I do have this working now. And I also understand that a **_default_** can be used to catch any unresolved requests. I am really just wondering how Apache deals with requests when no Virtual Host is triggered, and no **_default_** is set.

So my question is, where is the Main Server Document Root set? I thought it was set in **/etc/apache2/sites-available/default** but since **/var/www** is used instead of **/var/www/mysite** it doesn't appear that way.

---

### Post by SeijiSensei on 2012-11-26
The sites-available directory contains the virtual host configurations that are "available".  The parallel "sites-enabled" directory includes symbolic links to the files that are active.  Only configurations that are linked in sites-enabled are actively supported by the server.

By the way, do you have control over the IP addressing scheme?  Why not just change the server's IP to match the entries in the VHost configurations?

Also the default typically is to use 

```
NameVirtualHost *:80
```

which makes Apache apply the virtual hosting definitions to all interfaces.  Then it doesn't matter what the machine's actual IP address is.

You need to make sure to use 

```
<VirtualHost *:80>
```

in the host definitions.  If the entry reads "192.168.1.1:80" instead of "*:80", it won't be matched when Apache searches, and you'll end up with the default.

---

### Post by BAWBCEN1TY on 2012-11-26
Yes, I do have control over the IP addressing schemes, and I did end up just using the wild card '*' asterisk. When I was entering the specific IPs I was just messing around to see how everything works. 

What I was wondering was since the IP addresses that I put in the ```
<VirtualHost x.x.x.x:80>
``` in both the **default** and **[www.mysite.com](www.mysite.com)** files are not correct and will never be triggered, how does Apache decide to use the **index.html** file in **/var/www**? 

I realize that ```
<VirtualHost _default_:80>[INDENT]DocumentRoot *desiredPath*[/INDENT]
</VirtualHost>

``` can be used to catch these unresolved requests, but how does Apache deal with it if this isn't specified? Is there a global Document Root setting somewhere that is a fallback if a request is unresolved?

---

### Post by volkswagner on 2012-11-26
> **BAWBCEN1TY said:**
> 

So my question is, where is the Main Server Document Root set? I thought it was set in **/etc/apache2/sites-available/default** but since **/var/www** is used instead of **/var/www/mysite** it doesn't appear that way.

If apache has a request that has no match in any of your virtual host files (sites-enabled), apache will server the first file in alfaNumeric order from ../sites-enabled.

One thing to notice... sites-availabe usually contains a file called 'default' but the symlink in sites-enabled is '000-default' this name will force it to the top of the list (of most any other human named file).

Hope this makes sense.

---

### Post by BAWBCEN1TY on 2012-11-26
Makes perfect sense. I had actually seen the naming difference and hadn't really given much thought to it. It was really bugging me that I could't find an answer to this anywhere I looked, so thank you.

---

### Post by BAWBCEN1TY on 2012-11-26
So I went back to test out what you had said, and it still seems to be loading from **/var/www** instead of **/var/www/mysite**.

My files look as follows:

**#/etc/apache2/ports.conf**

[INDENT]NameVirtualHost 192.168.1.22:80

Listen 80
.
.
.[/INDENT]

**#/etc/apache2/sites-enabled/000-default**

<VirtualHost 192.168.1.22:80>

[INDENT]ServerAdmin webmaster@localhost

DocumentRoot /var/www/mysite
.
.
.[/INDENT]
</VirtualHost>

**#/etc/apache2/sites-enabled/www.mysite.com**

<VirtualHost 192.168.1.22:80>

[INDENT]ServerAdmin webmaster@localhost

ServerName [www.mysite.com](www.mysite.com)

DocumentRoot /var/www/mysite
.
.
.[/INDENT]
</VirtualHost>


Now I do want to make sure that it is understood that the IP address in the **<VirtualHost>** tags is not the actual IP of the server. Any request to port 80 is just forwarded through my router to the server. 

The request comes through on the real IP **192.168.1.21:80** and obviously doesn't trigger either of the Virtual Hosts. So how does Apache decide to serve from **/var/www**?

P.S. - I know it may seem silly to be so concerned with such a bizarre scenario, but I thought it was going to be simple to find an answer to this, and since it has proven quite a challenge, it has turned into a minor obsession. So thank you for indulging me in my odd request.

---

### Post by volkswagner on 2012-11-27
A few things come to mind.

Have you cleared your browser cache?

Have you restarted apache after making changes?

Are there any entries in other config files which may be pointing to /var/www?

What other files may be in hosts-enabled?

```
ls -alt /etc/apache2/sites-enabled
```

What about the logs, is there any info in /var/log/apache/ log files?

What happens if you rename the /var/www/index.html to something else?

```
sudo cp /var/www/index.html /var/www/index.html.bak
sudo mv /var/www/index.html /var/www/test
```

---

### Post by BAWBCEN1TY on 2012-11-28
OK, yes I have cleared my browser cache. Yes, I have restarted Apache. I don't see any other config files that have a reference to **/var/www**. 

I did ```
grep -ir '/var/www' /etc/apache2
``` and didn't get anything that I hadn't already looked at. 

```
ls -alt /etc/apache2/sites-enabled
``` returned the following things:
[INDENT][B] .
..
[www.mysite.com](www.mysite.com)
000-default
[/B][/INDENT]


And I renamed **/var/www/index.html** to **/var/www/test**, and when navigating to my site I got a page that said **Index of /**.

If I put **/mysite** at the end of my URL though, it serves the **index.html** file from **/var/www/mysite**. So Apache definitely seems to use **/var/www** as a default when **../sites-enabled/000-default** can't be, I just don't know how or why it decides to use it.

---

### Post by volkswagner on 2012-11-29
Strange indeed.

I do not have any servers running Ubuntu Server greater than version 10.04 so it is hard to comment.

What you are experiencing is not supposed to happen.  I do recall seeing something similar which resulted in the user uninstalling/reinstalling Apache2.

Grasping at straws here, but have you issued a reboot?


Did you install apache using apt-get?  Wondering if perhaps you have config files in /usr/local or something????

---

### Post by BAWBCEN1TY on 2012-11-29
The server isn't actually serving any real purpose at the moment, so I really only turn it on when I am looking to fool around with it, so it has had many "reboots". 

I tried uninstalling using ```
sudo apt-get --purge remove apache2
```
but that seems to have still left the **/var/www** directory and the **/etc/apache2** directory. Do you know of a way to completely uninstall anything that is associated with the program?

I did install using **apt-get**. And the **/usr/local** directory is empty (I checked this before the uninstall in the previous paragraph).

---

### Post by Mopar1973Man on 2012-11-29
Since your new to the Ubuntu relm I got a program that will make Administration easy for you then. I would go out to...

 [http://webmin.com/](http://webmin.com/)

And download and install Webmin 1.610.  To run webmin just type for a URL...

[https://localhost:10000](https://localhost:10000)

Then you can administer your server with a really easy user interface.  Then you can adjust everything about your server setup as well. Security, IPtables, Networking, Hostname, etc. All in a friendly browser screen.

---

### Post by BAWBCEN1TY on 2012-11-30
Alright, I think that we can put this to rest. I had an extra hard drive laying around, so I decided to do a clean install of Ubuntu to make sure that I didn't have any old config files for Apache2 present anywhere on the drive. I set it up just like I had it on the other drive (same filenames, wrong IPs, etc.), and was able to completely recreate every previous result. 

I did find some documentation that mentioned, "Any request that doesn't match an existing <VirtualHost> is handled by the global server configuration, regardless of the hostname or ServerName" ([http://httpd.apache.org/docs/current/vhosts/name-based.html](http://httpd.apache.org/docs/current/vhosts/name-based.html)). So I decided to do a search on "global server configuration", and it seems that in previous versions of Apache for Ubuntu (and still in other distros), the main configuration file is **/etc/apache2/httpd.conf** instead of **/etc/apache2/apache2.conf**.

And there is a **Document Root** section in that **../httpd.conf** file. So, I did some experimenting, and it seems that you can still set this through adding ```
DocumentRoot */your/preferred/directory*
``` to either **/etc/apache2/apache2.conf** or **/etc/apache2/ports.conf**.

So, thank you for your assistance in helping me figure out the answer to this problem. Your questions and suggestions were a great guide in the right direction. I'm sure I will be back on here before too long, so maybe we can do this again. Take it easy, and Happy Holidays.

---

