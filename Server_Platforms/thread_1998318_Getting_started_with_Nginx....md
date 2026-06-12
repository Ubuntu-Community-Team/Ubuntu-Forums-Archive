---
title: "Getting started with Nginx..."
date: 2012-06-06
forum: Server Platforms
---

### Post by Roasted on 2012-06-06
So I'm trying to get Nginx running to see if it's a suitable replacement for Apache on my home server. I'm not running into any sort of issue at all with Apache, just more curious than anything else.

I understand there are a lot of similarities between Apache and Nginx. In particular I'm after a few rather basic items. I simply want to host a series of files that require user authentication. I run video surveillance software (motion) so I'm saving the motion feeds to the hosted directory in Apache. That way I can access them externally when I'm away from my house.

Secondly I want that list to be in a specific order... newest first, oldest last (bottom). 

Besides that, that's really it. I've read through some quick-start guides but I'm still left with some rather extremely basic questions. In Apache, if I put a folder in /var/www named HELLO, then I go to localip/HELLO, suddenly everything just works. Where is that in Nginx? Where does Nginx host directories like that? I know it's a super basic question, but I'm coming up short with a direct answer for it.

---

### Post by rubylaser on 2012-06-06
Nginx supports the concept of vhosts just like Apache.  You'd just need to create a vhost entry in your nginx.conf for your server_name and setup the document root for that URL.  To display a folder's contents and password protect it, you'll want to use Nginx's autoindex module.  Here's a post that discusses [autoindex + password protection]("http://stackoverflow.com/questions/9454150/nginx-password-protected-dir-with-autoindex-feature").

---

### Post by sandyd on 2012-06-06
> **Roasted said:**
> So I'm trying to get Nginx running to see if it's a suitable replacement for Apache on my home server. I'm not running into any sort of issue at all with Apache, just more curious than anything else.

I understand there are a lot of similarities between Apache and Nginx. In particular I'm after a few rather basic items. I simply want to host a series of files that require user authentication. I run video surveillance software (motion) so I'm saving the motion feeds to the hosted directory in Apache. That way I can access them externally when I'm away from my house.

Secondly I want that list to be in a specific order... newest first, oldest last (bottom). 

Besides that, that's really it. I've read through some quick-start guides but I'm still left with some rather extremely basic questions. In Apache, if I put a folder in /var/www named HELLO, then I go to localip/HELLO, suddenly everything just works. Where is that in Nginx? Where does Nginx host directories like that? I know it's a super basic question, but I'm coming up short with a direct answer for it.

--Serving Directory--
Nginx uses virtualhosts, like apache

The default virtual host's root directory is /var/www.

It is changable via /etc/nginx/sites-enabled/default

Change the 'root' (Under location / {) to your desired directory.

Nginx, like apache uses the www-data user/group, so make sure the desired directory is chowned as such.

Oh, and make sure the semicolon at the end of the line stays - otherwise you will get errors.

--Password--
Nginx uses htpasswd, just like apache. Take a look here -> [http://wiki.nginx.org/HttpAuthBasicModule](http://wiki.nginx.org/HttpAuthBasicModule)

---

### Post by Roasted on 2012-06-06
So if I'm understanding this right, Nginx is set up the same way Apache is out of the box... meaning /var/www/folder = 127.0.0.1/folder and that item is hosted.

The curve ball is, I'm not seeing that with Nginx here. I just get a "Welcome to nginx!" banner... no listing like I expected...

---

### Post by sandyd on 2012-06-06
> **Roasted said:**
> So if I'm understanding this right, Nginx is set up the same way Apache is out of the box... meaning /var/www/folder = 127.0.0.1/folder and that item is hosted.

The curve ball is, I'm not seeing that with Nginx here. I just get a "Welcome to nginx!" banner... no listing like I expected...

Delete the index.html, and enable indexes
Indexes can be enabled by adding
```

        autoindex on;
        autoindex_exact_size off;
        autoindex_localtime on;

```
under ```
location / {
```

---

### Post by Roasted on 2012-06-06
There is no index.html. I installed nginx on a freshly installed VM through the repos. dpkg -L nginx reveals only /usr/share/whatever files existing... There's nothing in /var/www. In fact, there's not even /var/www... only var...

I tried to install the PPA, but it errors out:


Cannot access PPA ([https://launchpad.net/api/1.0/~nginx/+archive/ppa](https://launchpad.net/api/1.0/~nginx/+archive/ppa)) to get PPA information, please check your internet connection.

---

### Post by sandyd on 2012-06-06
> **Roasted said:**
> There is no index.html. I installed nginx on a freshly installed VM through the repos. dpkg -L nginx reveals only /usr/share/whatever files existing... There's nothing in /var/www. In fact, there's not even /var/www... only var...

I tried to install the PPA, but it errors out:


Cannot access PPA ([https://launchpad.net/api/1.0/~nginx/+archive/ppa](https://launchpad.net/api/1.0/~nginx/+archive/ppa)) to get PPA information, please check your internet connection.

my bad.
I was looking through debian, not ubuntu.
The correct folder is /usr/share/nginx/www

---

### Post by Roasted on 2012-06-09
Okay, well we're getting somewhere. I created a folder in /usr/share/nginx and was getting 403'd. I found a blog on Google that said you probably need to enable autoindex, so I added that entry in the one config file. Just then my listing came up. Now I'm getting a little more excited.

There's two things I need to accomplish yet. I need to set up user authentication, which I'm sure is easy to do. (does nginx use htpasswd like apache does?)

Secondly I **need** the ability to sort by date modified. Is there a way to do that in nginx? Not having this feature would almost definitely be a deal breaker since the files I'm hosting are video surveillance files, so I want everything to get sorted by date modified when the clip happened. Is that possible?

---

