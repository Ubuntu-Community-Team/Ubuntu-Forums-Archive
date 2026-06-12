---
title: "Multiple websites on single host machine without virtualisation."
date: 2010-06-01
forum: Server Platforms
---

### Post by John Rivera on 2010-06-01
I have this intra net server project going on and now I moved to 10.04 however there are still some things that I would like to see clarification and instructions on.

I am interested to set up multiple parallel websites for my apache server, however I am not sure how to do this exactly.

Now I have solid address rivera.wippies.net and port 80 redirecting to my server.

What I would like to get done is that I get multiple independent of each other websites for my server

I was thinking of making websites like this
/var/www/site1 (which would be as rivera.wippies.net)
/var/www/site2 (which would be as rivera.wippies.net/othersite)
/var/www/site3 (which would be rivera.wippies.net/secondothersite)

etc, so that I have multiple "individual" websties for my server.
Requirements would be that each of these websites could have SSL encryption as needed available too, since some of the website could have confidential information.

Is what I am trying to do even possible, or just quite hard to archive ?

If you need some details I will provide those as long as I don't consider it to risk my information security.

---

### Post by arrrghhh on 2010-06-01
You're going to want to look into [vhosts](http://httpd.apache.org/docs/2.0/vhosts/) or virtual hosts thru Apache.  I guess I'm assuming you're using Apache as well and not lighthttpd...

---

### Post by dudumomo on 2010-06-01
Indeed, you can easily do it by setting up several virtualhosts.
Example [here]("http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/"), last part: "4) Domain(s) / Subdomain(s)"

Virtualhosts are located into /etc/apache2/sites-available.
Create or modify one.

The link I gave you is my tutorial :) I hope it will help you.

---

### Post by John Rivera on 2010-06-01
I think I need to clarify more since there seems to be some misunderstanding.

I can get a single domain to work on my server without any problems, however I would like to change configuration, adding websites that are not directly subdirectories.

I currently have working apache2 configuration, but I would like to get more functionality to by adding independent websites to my server, websites that are in parallel directories (sub directories in document root directory)

like that main website would be "rivera.wippies.net" but it would be contained in /var/www/online and then I would have other websites like "rivera.wippies.net/projects" which would be hosted in directory /var/www/projects

 and then I would have other websites as directories side by side

So my core problem is that I do not know if I can create such parallel directory based websites for my server directly or do I need to use other means necessary

---

### Post by new_tolinux on 2010-06-01
> **John Rivera said:**
> I can get a single domain to work on my server without any problems, however I would like to change configuration, adding websites that are not directly subdirectories.
There are two ways:
- Virtualhosts (as described above)
Can be told to use any directory as main root.

- Aliases
An example is in your apache config:
```
Alias /error/include/ "/your/include/path/"
```
This way you can set the /var/www/mainsite/projects folder to actually display the /var/www/projects folder.

---

### Post by dudumomo on 2010-06-02
> **John Rivera said:**
> I think I need to clarify more since there seems to be some misunderstanding.


You were quite clear.
And as told before, you can do it with virtual host (Or aliases indeed)

In my case, with severals virtualhosts (Just conf files), I got my website [www.freelydifferent.com](www.freelydifferent.com) linked to the folder /var/www/freelydifferent ; my pictures hosting pix.freelydifferent.com linked to the folder /var/www/pix, my web gallery gallery.freelydifferent.com linked to /var/www/gallery, my testing forum [www.freelydifferent.com/forum](www.freelydifferent.com/forum) linked to /var/www/forum, etc...

---

### Post by penguin_patrick on 2010-06-02
I as well host several websites using name based virtual hosts.

Was a pain to figure out originally, but now I'm using webmin to administer it, and it works a treat.

I set up my different sites under:

/var/www/somesite1
/var/www/another
/var/www/thatone
/var/www/theother

One of them is SSL which I set up manually with help from walkthroughs from the internet.  

I also use webmin to set up samba shares for each directory, so I can attach my windows box to each web directory, for direct editing.  Nice.

Remember to stop and re-start apache after making new virtual hosts (or changing) in webmin.

---

### Post by Bachstelze on 2010-06-02
> **penguin_patrick said:**
> 
Remember to stop and re-start apache after making new virtual hosts (or changing) in webmin.

Only a reload of the config is needed, no need to stop Apache.

---

### Post by penguin_patrick on 2010-06-02
I don't think webmin has that feature, or it's broken.  

I do agree that cli reload is all that's required, but in webmin, there's a button for 'apply changes' but it never seemed to work, so I perform the stop and start.  

Then the changes are working.

Actually, there's a few buttons that don't work right in webmin on ubuntu, but I work around them when needed. I can't remember which ones, atm.

ymmv, etc.

---

### Post by John Rivera on 2010-06-09
Okay this is solved since what I was trying to do is not simply possible.

My idea was to create multiple websites on single host in way that is not just possible.
What it needs is that each virtual host is in own directory, not in sub directory of main directory.

---

### Post by new_tolinux on 2010-06-09
> **John Rivera said:**
> Okay this is solved since what I was trying to do is not simply possible.

My idea was to create multiple websites on single host in way that is not just possible.
What it needs is that each virtual host is in own directory, not in sub directory of main directory.
Since you'll need to specify the directory which is used by the virtual host, it should be possible to have one virtual host pointing at /var/www/ and another virtualhost at /var/www/subfolder/
Although you'll have to keep in mind that [http://firstvirtualhost/subfolder](http://firstvirtualhost/subfolder) displays the same content as [http://secondvirtualhost/](http://secondvirtualhost/) does. In case of different websites that's probably not what you want.

---

### Post by arrrghhh on 2010-06-10
You can make virtual hosts anywhere.  We have directories in /opt that are serving web pages.

---

