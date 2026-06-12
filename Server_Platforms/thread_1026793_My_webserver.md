---
title: "My webserver"
date: 2008-12-31
forum: Server Platforms
---

### Post by LOG123 on 2008-12-31
Whenever i try to connect to my website from Firefox it gives me this error :
```
Connection Interrupted

      

      
      
      

      
        
        

          

The connection to the server was reset while the page was loading.

        


        
        

The network link was interrupted while negotiating a connection. Please try again.
```
any help??:confused:

---

### Post by Skyride on 2008-12-31
You are using apache correct? Are you trying to access this over the internet or LAN?

---

### Post by LOG123 on 2008-12-31
um... well, in webmin it shows
```
The Apache webserver does not appear to be installed on your system, or has not yet been set up properly in Webmin's Apache Webserver module. If your system does not use Apache, it should be disabled in Virtualmin's module configuration page.
``` 
but i was using my website just two days ago and this is local and web i need help :confused:

---

### Post by LOG123 on 2008-12-31
<bump> i know its just a few hours after my first post but i'm selling products and can't afford downtime!:(

---

### Post by TestDummy! on 2008-12-31
What changed?

I mean, what was it that you were doing before it stopped working?

---

### Post by Skyride on 2008-12-31
Webmin sometimes won't see Apache unless its installed USING webmin. Try restarting a couple of times and if that dosen't work uninstall apache and install it again using webmin.

---

### Post by LOG123 on 2009-01-01
Will removing apache remove my website data?

---

### Post by LOG123 on 2009-01-01
> **TestDummy! said:**
> What changed?

I mean, what was it that you were doing before it stopped working?
sleeping. :D

---

### Post by volkswagner on 2009-01-01
what do you get when you restart apache2?  

```
sudo /etc/init.d/apache2 force-reload
```

Any errors?

Check apache logs. Location=   /var/log/apache2/

---

### Post by LOG123 on 2009-01-01
> **volkswagner said:**
> what do you get when you restart apache2?  

```
sudo /etc/init.d/apache2 force-reload
```

Any errors?

Check apache logs. Location=   /var/log/apache2/

when i reload it i get this error just from the command line:
```
 * Reloading web server config apache2
[Thu Jan 01 13:04:31 2009] [error] VirtualHost 192.168.2.4:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Jan 01 13:04:31 2009] [error] VirtualHost 192.168.2.4:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
   ...done.

```
will check the apache logs in a min

---

### Post by LOG123 on 2009-01-01
this is a LOG

---

### Post by volkswagner on 2009-01-01
I believe apache will still run with the * ports and * non ports error.  It may give undesired results like wrong page loaded.

It should be easy enough to eliminate the issue though.

If you have individual virtual host's they should all use the same syntax.  Possible the default site got enabled.

List your sites enabled directory and check the config. to verify the naming convention is the same for each.

```
ls -alt /etc/apache2/sites-enabled
```

You could also use process of elimination.  Disable each site and then enable one at a time.  Restart apache with the fist enabled and continue testing your sites till you find the culprit.

You will want to research "[notice] caught SIGWINCH, shutting down gracefully" to see the  cause of that error.

---

### Post by volkswagner on 2009-01-01
Just re-read this whole thread.

We all may have skipped the obvious.  It appears apache is running.

Explain your setup.  Is this a local server?  Can you access the site by entering the LAN ip in FF if it is on you LAN?  Is it behind a router?  It it on a dynamic ISP?

Good chance your isp changed the ip address, that would give the error in FF.

---

### Post by LOG123 on 2009-01-01
> **volkswagner said:**
> Just re-read this whole thread.

We all may have skipped the obvious.  It appears apache is running.

Explain your setup.  Is this a local server?  Can you access the site by entering the LAN ip in FF if it is on you LAN?  Is it behind a router?  It it on a dynamic ISP?

Good chance your isp changed the ip address, that would give the error in FF.
i have a fixed IP (its business class), its behind a router it i enter the ip it brings the page so  i'm clueless :confused:

---

### Post by volkswagner on 2009-01-01
> **LOG123 said:**
> i have a fixed IP (its business class), its behind a router it i enter the ip it brings the page so  i'm clueless :confused:

Can you explain?  What ip and what page?

If you enter the servers internal ip on a LAN connected pc do your webpages display?

EDIT:Check your log again, if apache is still restarting itself you will get the connection errors in firefox.

---

