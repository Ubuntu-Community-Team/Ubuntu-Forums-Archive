---
title: "troubleshooting custom 404 error message"
date: 2015-09-24
forum: Server Platforms
---

### Post by Drone4four on 2015-09-24
I'm  trying to customize my 404 error message.  I'm working with a straight forward guide from the DigitalOcean collection of docs called, &#8220;[How To Create a Custom 404 Page in Apache]("https://www.digitalocean.com/community/tutorials/how-to-create-a-custom-404-page-in-apache")&#8221;. And I'm also using an unnecessarily complex but still very helpful guide on the thesitewizard called, &#8220;[How to Set Up A Custom 404 File Not Found Page]("http://www.thesitewizard.com/archive/custom404.shtml")&#8221;.

The contents of my .htaccess file read as follows:
```
Options -Indexes
ErrorDocument 404 /notfound.html 
```

My notfound.html file reads:
```
The address of the content you've requested has been changed or moved.  If you want an updated link, send the webmaster an email at name@DN.com.  He'll give you a fresh link.  All you have to do is ask.
```

The user and group permissions for that file are as follows:
```
user@remotehost :/var/www/html/DN.com/public_html$ ls -l notfound.html 
-rw-r--r-- 1 user group 208 Sep 24 21:23 notfound.html
user@remotehost :/var/www/html/DN.com/public_html$
```

Same permissions for .htaccess

My 404 error message is still the default one that comes with Apache. 

I feel like the solution I need is trivial and that I am overlooking something really simple.  I await a cluebat.

---

### Post by SeijiSensei on 2015-09-25
.htaccess is disabled by default.  Put the directives in the file that defines the virtual host in /etc/apache2/sites-available/.  .htaccess is a kludge to let people have some control over websites on hosting servers.  If you have full control over the machine's configuration, you should place all the Apache directives in their corresponding virtual host definitions.

If you must use .htaccess, add the directive "AllowOverride On" to the <Directory> stanza that points to where .htaccess resides.

---

### Post by Drone4four on 2015-10-13
If there is it is better way to do what I have set out to achieve (404 error message) without an .htaccess, then let's try that first. 

I put directives inside my website's virtual host definition.  Here are the contents of my 
/etc/apache2/sites-available/DN.conf :

```

<VirtualHost *:80>

        ServerAdmin webmaster@DN.coffee
        ServerName  www.DN.coffee
        ServerAlias DN.coffee
        DocumentRoot /var/www/html/DN.coffee/public_html/
        ErrorLog /var/www/html/DN.coffee/logs/error.log
        CustomLog /var/www/html/DN.coffee/logs/access.log combined

     <Directory /var/www/html/DN.coffee/public_html/>
        Order allow,deny
        Allow from all
        Options -Indexes
        ErrorDocument 404 /notfound.html
     </Directory>

</VirtualHost>

```

Notice the third and fourth line within the Directory two tags.  Those lines were previously inside  .htaccess.  Is this what you were suggesting, **SeikiSensei**?  You suggested that I put the information within the Directory tags outside from the VirtualHost tag, but that was only if I were to continue to have a .htaccess file inside my html public folder.  

How do I test whether or not this is working?  I Googled .htaccess test and I encountered [a page at madewithlove.be]("http://htaccess.madewithlove.be/") for doing exactly that.  I entered the request url (a link to my website's homepage) and clicked, 'Check now'.  Nothing happened.  I tried again this time with the contents of my old .htaccess file.  Still no dice.

I apologized for the delay in my reply.  Its been a few weeks since my last post.  I'll try to be more punctual going forward.

---

### Post by SeijiSensei on 2015-10-14
First, make sure you restart Apache with "sudo service apache2 restart".  Now simply request a non-existent page from the site like [http://www.dn.coffee/nosuchpage.html](http://www.dn.coffee/nosuchpage.html). Do you get the custom 404 page?

---

### Post by Drone4four on 2015-10-15
Thanks for your attention, **SeijiSensei**.

I requested a non existent page which gave me this: ```
Not Found
The requested URL /etxss was not found on this server.
``` But when I issued an apache service restart as per your suggestion, I got the same message but with this too: ```
Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.
```So I googled that line and encountered some loosely related problems with configuring htaccess.

---

### Post by Drone4four on 2015-11-12
I just checked my public_html directory and to my surprise there was no trace of notfound.html .  So I created that html file and inserted some placeholder text and now when I navigate to a nonexistent address, it gives me the custom 404 error message as intended.  I am really sorry to have overlooked this.  I evidently wasn't paying close enough attention to what I was doing or to what **SeijiSensei** was suggesting.  I will double up my efforts to pay closer attention to detail with my tinkering.  And I would also like to apologize for my delayed reply.

---

