---
title: "Serving files online"
date: 2013-05-25
forum: Server Platforms
---

### Post by bubylou on 2013-05-25
I looking for a good way to serve up files over the internet. I want some of my family members to have access to some of my files on my server. Unfortunately all of the people who would like access are not very technically inclined. So the usual SFTP i think is out unless there is a very easy to use client available. Another program I have tried is Owncloud but it worked rather clunky. I was also looking at Ajaxplorer but im unsure as to how usable it will be for others. I guess im looking for something that appears almost cloud storage like but is being hosted in house by me. Let me know what you may use for such a service or can recommend for me to try.

---

### Post by SeijiSensei on 2013-05-28
Why not install Apache and let them use a web browser?

---

### Post by DJ_Max on 2013-05-28
If you don't mind leaving your computer on, and have a dedicated IP or use a dynamic dns service you can install a HTTP server like Nginx.

Or use something like dropbox

---

### Post by bubylou on 2013-05-28
Apache is not exactly what I had in mind but i will mess with it a little bit in the mean time though.
Also this is a dedicated server by the way. Also don't want to use an outside cloud service.

---

### Post by Habitual on 2013-05-29
```
python -c "import SimpleHTTPServer;SimpleHTTPServer.test()
``` in any directory you wish to share.
Navigate them to http://$HOSTNAME:8000/ 
or [http://IP.AD..DR.ESS:8000/](http://IP.AD..DR.ESS:8000/)


**[COLOR=#ff0000]This method IS NOT SECURE[/COLOR]**

---

### Post by markbl on 2013-05-29
> **Habitual said:**
> ```
python -c "import SimpleHTTPServer;SimpleHTTPServer.test()
``` in any directory you wish to share.
Navigate them to http://$HOSTNAME:8000/ 
or [http://IP.AD..DR.ESS:8000/](http://IP.AD..DR.ESS:8000/)
That's not going to work for 99.9% of people without forwarding a port from their home router. Dropbox, or box.net, or google drive is the best way for the OP to share files.

And, btw Habitual, you just need to type "python -m SimpleHTTPServer" rather than all that anyhow, In fact, "python3 -m http.server" is better again because it is easier to remember.

---

### Post by newbie-user on 2013-05-30
I believe you had two key points: 1) do everything in-house, and 2) keep it simple for friends/family

Apache is probably going to be the easiest solution for you.

```
apt-get install apache2
```

Then put all your files in /var/www and either remove the default index.html (apache will show the directory contents) or add hyperlinks to index.html that point to your files. That's pretty much it. Send out your IP address or domain to your family/friends and it's a done deal. It's literally like a two-step process.

---

### Post by SlugSlug on 2013-05-30
I quite liked owncloud, what did you find clunky? You can have it secure with HTTPS and family could map it as a network drive

---

### Post by bubylou on 2013-06-05
If someone could point me in the right direction for getting started with serving files over apache. Most of the stuff i have found isn't working to well for me.

The problem i had with owncloud was how slowly it would process anything i did in the web interface. I believe it was a fairly common database issue. Ill have to see if it was fixed but i also had a few nit picks with owncloud.

---

### Post by SeijiSensei on 2013-06-06
Well, to begin with, if you have installed Apache and navigate to the URL [http://localhost/](http://localhost/) on the server itself, what do you see?  By default the server should display the "It Works!" page.  If that works, then you should be able to get the same result by navigating to [http://ip.of.the.server/](http://ip.of.the.server/) from another machine on the network.  If those both work as expected, we can talk about how to serve the files.

If the server doesn't have a GUI environment, install the text-based elinks browser ("sudo apt-get install elinks") and use that for testing.

The simplest solution would be to put all the files below /var/www, but a better solution would be to create a "virtual host" that serves up the directory tree where your files are stored now.  So lets start with that, where are the files you want to distribute stored now?

---

### Post by bubylou on 2013-06-09
The files that i wish to access are in /srv/samba/share directory.

---

### Post by SeijiSensei on 2013-06-09
Follow /etc/apache2/sites-available/default as a guide and create another virtual host with /srv/samba/share as the DocumentRoot.  Make sure that the user called "www-data" can read that directory and any files and directories it contains.  Then use "a2ensite" to activate the site you created.

Another option is to put a symbolic link to /srv/samba/share in /var/www, the default DocumentRoot.  You may need to alter the "default" file I referenced above by adding "FollowSymLinks" to the [Options](http://httpd.apache.org/docs/current/mod/core.html#options) directive in the <Directory> stanza for /var/www.  

I recommend reading the Ubuntu Server Guide as a starting point:  [https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)

---

