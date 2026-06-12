---
title: "Website Sub-Directories Not Viewable"
date: 2008-01-18
forum: Server Platforms
---

### Post by dbqp on 2008-01-18
Hi All,

I have had a web server up and running for some time now and recently added an additional domain/site.

I can access the site through a browser both on the internal network and externally from outside the network.

What I cannot access are the folders listed under top level of the site. It give me a 403 Error - Forbidden message:

You are not permitted to access the requested URL

Please contact the Webmaster with any queries

So I can access [http://www.domain-name.com/](http://www.domain-name.com/)

But NOT [http://www.domain-name.com/Plone/](http://www.domain-name.com/Plone/)

I tried setting my permissions from ISPConfig for a folder listed under the top level, but ISPConfig returns a chmod failed message from within the ISPConfig control panel.

Any guidance or help would be appreciated!

---

### Post by Vinno on 2008-01-18
I havent used ISPConfig but have you checked the directory permissions for the directory that is serving the files you want to get to.

Just make sure the directory has the Read/Execute permissions for Others.

---

### Post by dbqp on 2008-01-18
Thanks Vinno, but it did not solve my problem. I performed the following:

chmod -R 0755 /var/www/web2/web/Plone

it accepted that command and I see the permissions have been given to 'group', but if I go to the folder via the website, I still get that 403 Error.

Would I need to restart the web server or machine to see these changes applied?

Anyone else want to take a stab or have some tips?

---

### Post by dbqp on 2008-01-18
Also, an FYI - I just tried FTP'ing a file to that directory and it too returned a Failed status. So it appears I cannot upload to this sub folder as well...

???

---

### Post by dbqp on 2008-01-18
As rsemilik pointed out in this thread:

[http://ubuntuforums.org/showthread.php?t=404908&highlight=forbidden+directory](http://ubuntuforums.org/showthread.php?t=404908&highlight=forbidden+directory)

and do this:

If you as root do
chown -R www:www /srv
then everything under and including /srv will be owned by user www and group www.


Seems there is a simple solution. Sorry for posting the same question but I could not find threads such as this earlier!

---

### Post by dbqp on 2008-01-19
Well, upon trying this solution, I am back at square one. The command returns an error: 

```
chown: 'www:www' : invalid user
```

I tried switching directories, but still no luck...

Anybody?

---

### Post by Vinno on 2008-01-19
Try, www-data.

---

### Post by dbqp on 2008-01-25
Vino, thanks for the response. I have been away so I have not had a chance to try this until now.

replacing www:www with www-data, did not work as it stated there is no user or group www-data???

I just don't know what else to try!:confused:

---

