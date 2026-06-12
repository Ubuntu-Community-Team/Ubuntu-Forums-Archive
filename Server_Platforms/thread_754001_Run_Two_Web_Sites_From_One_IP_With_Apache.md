---
title: "Run Two Web Sites From One IP With Apache?"
date: 2008-04-13
forum: Server Platforms
---

### Post by jjacquay712@gmail.com on 2008-04-13
Can you run two websites from one ip address with apache? and if you can how would i go about doing this? the config file? im new to apache and was wanting to host two web site with one server

---

### Post by faulkes on 2008-04-13
> **jjacquay712@gmail.com said:**
> Can you run two websites from one ip address with apache?

Yes, this is called name-based virtual hosting.

> and if you can how would i go about doing this? the config file? im new to apache and was wanting to host two web site with one server

This is covered in both the official and community documentation
and fairly well layed out.

You will find links to both sets of resources in my signature.

Once you have tried those, should you have additional questions or
encounter problems, feel free to come back and ask more specific
questions.

Thanks,

Faulkes

---

### Post by shane2peru on 2008-04-13
Perhaps I'm blind but I didn't see anything in those links to the documentation.  I too had been looking for this and needed something to read.  Here is something that I used to get mine working,  [http://wowtutorial.org/en/node/24](http://wowtutorial.org/en/node/24)   however if Ubuntu has documentation, you would be best off following the Ubuntu documenation.  Perhaps faulkes would be so kind as to post the page that it is located at.  I too would like to read it.

Shane

**EDIT:**  Ok, I take that back, I found some info about virtual hosting on those sites:  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)    is one and    [https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html)  is the other.  The are informative sites, but don't really seem like a howto for me.  Good info for the reading though.  That combined with the link above I gave should give you a good idea on how to setup what you want.

---

### Post by teaker1s on 2008-04-13
make life simple for yourself by installing webmin if you use a gui.
you will also need a ddclient or similar to keep your sites dns valid as routers only normally allow 1 dyndns site

---

### Post by shane2peru on 2008-04-13
> **teaker1s said:**
> make life simple for yourself by installing webmin if you use a gui.
you will also need a ddclient or similar to keep your sites dns valid as routers only normally allow 1 dyndns site

I tried the webmin method too, very confusing for me. lol.  If you have a nice little howto with webmin, that would be great to post!  Yes, ddclient is a necesity for dyndns  not too hard to setup either.

Shane

---

### Post by teaker1s on 2008-04-15
okay login to webmin and select servers, apatche webserver

If you want to run multiple websites from your VPS, then you can use Apache's support for Virtual Hosts.
Then, to create a virtual host using Webmin:save your files to example:-/var/www/www.mysite.org



  *** robbed  and edited from previous version guide****

    * Go to servers.
    * Go to Apache WebServer.
    * In the 'Create a New Virtual Server' section select "Any Address" (so you do not end up with a hard coded IP addresses in your conf file)
    * Enter 80 for Port (and select the last radio button).  This way the VirtualHost will co-exist with any SSL-enabled virtual hosts you add later on.  SSL-enabled VirtualHosts need to listen on port 443.
    * In the "Document Root" field enter where the virtual host HTML files will be.  For example, /home/vhostdomain.com/htdocs.
    * For "Server Name" enter the domain name for which you want to serve pages.  e.g. "vhostdomain.com"

After you have created the Virtual Host, there are a few other things you may wish to edit.

For example, click on the Virtual Host, and go to Networking and Addresses.  Enter an "Alternate virtual server names" of *.YourOtherDomain.com.  With this setting, your virtual host will serve pages for [http://yourotherdomain.com/](http://yourotherdomain.com/) as well as [http://www.yourotherdomain.com/](http://www.yourotherdomain.com/).

At this point you may also wish to set other options like "Log Files", so the log files for the Virtual Host end up in separate log file from the main server's log files.

To activate your changes, click "Apply Changes" on the main Apache Webmin page.

Of course, be sure to configure your DNS server so the virtual host domain name points to your server's IP address.

Webmin creates a VirtualHost directive 

regards
Dan

---

