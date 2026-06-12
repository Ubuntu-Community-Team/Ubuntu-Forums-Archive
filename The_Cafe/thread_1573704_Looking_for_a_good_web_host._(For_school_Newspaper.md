---
title: "Looking for a good web host. (For school Newspaper)"
date: 2010-09-13
forum: The Cafe
---

### Post by JamezQ on 2010-09-13
My school has a journalism class, and we all get roles, some people do interviews, some people do sports, I am the person that is doing the website and tech stuff.

Anyway, so far I have used a free web host to host all my content. But now we are looking for a better one. I will be writing a review on all these web hosts for class, so I am looks for suggestions.

At minimum I need a reliable site that can host images, html,css and javascript.

However, what the school would really like is the ability to only let certain people view the site, because we will be having students pictures on it, we don't want anyone to be able to get into it.

The site doesn't have to be totally free, but I would like it, does anyone have any suggestions. I also would like to know how to exactly whitelist people ^ ^

---

### Post by mendhak on 2010-09-13
If you want to restrict who can view it, you'll either have to introduce some configuration options that gives the user username-password prompt or introduce a login mechanism.

To do it in Apache, have a look at [this page](http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/), which involves working with an .htaccess file.  (I assume you're going to use Apache)

The other way is to do it with PHP - do you know PHP/MySql?  If security isn't paramount, you could even have a hardcoded username and password in your PHP.

---

### Post by JamezQ on 2010-09-13
> **mendhak said:**
> If you want to restrict who can view it, you'll either have to introduce some configuration options that gives the user username-password prompt or introduce a login mechanism.

To do it in Apache, have a look at [this page](http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/), which involves working with an .htaccess file.  (I assume you're going to use Apache)

The other way is to do it with PHP - do you know PHP/MySql?  If security isn't paramount, you could even have a hardcoded username and password in your PHP.

Can what you said be done with a free web host??? 

And I don't need super security, nobody is going to try any hack into this, I just need something simple, for privacy reasons.

Any specific hosts you suggest?

---

### Post by mendhak on 2010-09-13
If your free host allows htaccess, then yes, you can do it with the free host.  Does your free host have Apache? If you don't know, mind telling us the name of the host?  I'm sure it's a simple search or a perusal through their FAQ section in order to find out.

If you want a paid host, then there are loads - have a look at 1and1 and bluehost.  I'm sure other members of this forum will also have recommendations. I know that 1and1 and bluehost both run Apache.

---

### Post by JamezQ on 2010-09-13
> **mendhak said:**
> If your free host allows htaccess, then yes, you can do it with the free host.  Does your free host have Apache? If you don't know, mind telling us the name of the host?  I'm sure it's a simple search or a perusal through their FAQ section in order to find out.

If you want a paid host, then there are loads - have a look at 1and1 and bluehost.  I'm sure other members of this forum will also have recommendations. I know that 1and1 and bluehost both run Apache.

Right now it is [http://1free.ws/](http://1free.ws/). But I have found it to be a bit slow, so far, and am still learning server stuff.(Heck, I don't know ANY server stuff)

"which allows you to create sub domains, add-on new ones, manage MySQL databases, upload and edit files right online, or via FTP, use custom .htaccess and .htpaswd... Safe mode is off, so every script will work."

Alright so it does, but, I still think I might find a better free host. And, I don't know how to really work that stuff or have scripts on servers.


*Last Edit:* It seems I cannot use cpanel on this, only vistapanel(I don't know what that means for me though), However I do know that other free hosts do offer cpannel.

---

### Post by mendhak on 2010-09-13
I think you'll find that all free hosts are a bit slow, considering how many people sign up to use the same server as you.  If performance and availability is important, you will eventually need to sign up for a paid hosting service.  If it's not that important then try using 1free.ws' htaccess.  Take a backup copy of the htaccess file (if it already exists) in case you mistype something, you could just restore the original settings. Since you're on 1free.ws already, why not give it a shot?

As for cPanel/vistaPanel, they're just administrative interfaces that let you do basically the same thing.  You'll be perfectly fine with either one.

---

### Post by JamezQ on 2010-09-13
Can you recommended me a good paid host or three?

---

### Post by scottuss on 2010-09-13
5quid host are very good, I've used them and their paid for accounts are really cheap (near free)

They do free accounts too.

[http://www.5quidhost.co.uk/](http://www.5quidhost.co.uk/)

---

### Post by JamezQ on 2010-09-13
A problem has arises! When using 1free.ws and following this:

[http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/](http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/)

any page that is password protected 404's. help?

---

### Post by mendhak on 2010-09-13
Can you post your htaccess, or whatever you've done so far?

---

### Post by JamezQ on 2010-09-13
> **mendhak said:**
> Can you post your htaccess, or whatever you've done so far?

```
AuthUserFile /htdocs/.htpasswd
AuthType Basic
AuthName "College"
Require valid-user
```

That is the file.

---

### Post by whiskeylover on 2010-09-13
[https://sites.google.com](https://sites.google.com)

---

### Post by JamezQ on 2010-09-13
I got it took work ^ ^ A php program I tried showed the full path(even though the program itself did not work)

---

### Post by mendhak on 2010-09-15
> **JamezQ said:**
> ```
AuthUserFile /htdocs/.htpasswd
AuthType Basic
AuthName "College"
Require valid-user
```

That is the file.
Sorry about the delay.  

You've done that, which is good so far, but it's basically looking for a file called .htpasswd in /htdocs/.  Does that file exist?  If not, you can create it.  Also note that the password itself needs to be encrypted.  An easy tool to do this is here:

[http://tools.dynamicdrive.com/password/](http://tools.dynamicdrive.com/password/)

Fill in the details there, and it gives you two textboxes containing the htaccess and htpasswd that you can put on your server.

---

### Post by TTanae on 2010-09-24
Check out [www.ultrawebsitehosting.com]("http://www.ultrawebsitehosting.com") that's who I use they offer a few different options but their prices start at $3 a month so if you're looking for a good webhost at a pretty cheap price they are deffinately worth checking out. Good luck hope it helps

---

### Post by perspectoff on 2010-09-25
You can host your web server on your own computer, if you want. Use

Drupal, Joomla, or WordPress.

Probably WordPress is the easiest, but Drupal the most powerful.

Your server would run a LAMP server.

See:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Web_Publishing](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Web_Publishing)

Detailed instructions for Drupal are given as an example (also WordPress).

Also see the ultimate server instructions at 

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Ultimate_Server_Walkthrough](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Ultimate_Server_Walkthrough)

Adapt them to your own Ubuntu version, but instructions are pretty similar for all.

---

