---
title: "how would a beginner come about making a website"
date: 2010-03-09
forum: The Cafe
---

### Post by redfoxkt on 2010-03-09
Ive been thinking about making a server to put in my house and I want to run a website but im a beginner. I've created a website in a class in highschool using dreamweaver but that's about it. No i do not know exactly what kind of site i want, possibly a forum but im not sure yet. so I'm wondering if any of you have any advice, or names of programs that could help me not just for the site building but for the server as well. Like programs that run the site and what not.

---

### Post by deer dance on 2010-03-09
Definitely check out [http://w3schools.com/](http://w3schools.com/)

and install LAMP

---

### Post by kaldor on 2010-03-09
If I were you, I'd avoid using software like Dreamweaver and use something like QuantaPlus or BlueFish, even Gedit or VIM. They will teach you more than graphical editors will, so you'll be better off in the long run if you are new to this.

---

### Post by redfoxkt on 2010-03-09
Thanks deer dancer

---

### Post by sandyd on 2010-03-09
if youve never really had any website design experience, go out and try a cms. youll have to install mysql, php, and apache2. if you have any queations, send me a pm or leave a post here and ill read it tomorow after I finish sleeping....

---

### Post by Anthon on 2010-03-09
It all depends on what you want to do with the site: what information you want to provide and who you intend to look at it, what programming experience you have (and want to forced to acquire through your efforts ;-) ).
If you want to make anything database oriented like a simple functional website showing your book/cd/dvd collection you should have a look at web2py ([www.web2py.com](www.web2py.com)).

---

### Post by Rabindranath on 2010-03-09
Try out joomla. Its a cms and you can create a great looking website in hours... There are a lot of tutorials available in the internet, so you can check them out...

---

### Post by msathis on 2010-03-09
may be wordpress..simple to learn and a lot of free resources.and for server its not better to use your own.You may buy webspace from webhosting firms.

---

### Post by HappinessNow on 2010-03-09
Drupal is very easy to use.

---

### Post by c174 on 2010-03-11
I just installed drupal using Synaptic, but when I go to //localhost/ I'm not getting the Drupal installation page.

I have found "install.php" in "file:///usr/share/drupal6/" on my system, but when I point Firefox to the file it asks if I want to open the file in gedit. It doesn't run the script, as I thought it was supposed to.

What am I doing wrong?

---

### Post by Phrea on 2010-03-11
Are you sure the PHP server is running?

---

### Post by c174 on 2010-03-11
> **Phrea said:**
> Are you sure the PHP server is running?

No, not really. I don't know how to check it...?

---

### Post by sandyd on 2010-03-11
> **c174 said:**
> No, not really. I don't know how to check it...?

install the "php5" package

---

### Post by c174 on 2010-03-11
I have php5 installed (according to Synaptic). So...

---

### Post by era86 on 2010-03-11
Make sure apache2 is running.

---

### Post by c174 on 2010-03-11
I checked using the System Monitor (view All Processes). There are a number of apache2 processes running:

apache2 Sleeping inet_csk_wait_for_connect
apache2 Sleeping inet_csk_wait_for_connect
apache2 Sleeping inet_csk_wait_for_connect
apache2 Sleeping inet_csk_wait_for_connect
apache2 Sleeping inet_csk_wait_for_connect
apache2 Sleeping inet_csk_wait_for_connect
apache2 Sleeping poll_schedule_timeout

(they have different process IDs)

---

### Post by c174 on 2010-03-11
I think I have found the problem: When I put [http://localhost](http://localhost) Firefox is directed to /var/www, but it should point to /usr/share/drupal6/index.php in order to get the drupal Welcome Page, I think. BTW putting some php-code in a file located under /var/www/ works fine, so I think Apache2 and php are working correctly.

So I only have to figure out how to change what localhost is resolved to. Right? Can anyone help me with this?

---

### Post by Riel on 2010-03-11
Well, copy your drupal install to /var/www/drupal

then go to [http://localhost/drupal](http://localhost/drupal) to fire the installer.

You would also need mysql packages though. It's quite a big jump you are taking now. Well, drupal has it's check page, you will come a long way to get all green 'ok' there ;)


And, well, not to point you from left to right, while Drupal installes quite simple, it's is quite a professional CMS and easy .. for people who know cms's.

I would advice CMSMS where the things that are happening are just a bit more obvious.

---

### Post by sandyd on 2010-03-11
> **c174 said:**
> I think I have found the problem: When I put [http://localhost](http://localhost) Firefox is directed to /var/www, but it should point to /usr/share/drupal6/index.php in order to get the drupal Welcome Page, I think. BTW putting some php-code in a file located under /var/www/ works fine, so I think Apache2 and php are working correctly.

So I only have to figure out how to change what localhost is resolved to. Right? Can anyone help me with this?

```

sudo ln -s /usr/share/drupal6/ /var/www/drupal

```
tada!

---

### Post by cariboo on 2010-03-11
If your php pages wants to open with a text editor, you can fix the problem by installing libapache2-mod-php5, it is in the repositories.

---

### Post by samh785 on 2010-03-11
Bluefish is good for html/css editing, but it isn't a WYSIWYG.
> **deer dance said:**
> Definitely check out [http://w3schools.com/](http://w3schools.com/)
+1

---

### Post by spcwingo on 2010-03-11
I can't believe nobody has mentioned Turnkey Linux.  Here's a link to their site:

[http://www.turnkeylinux.org/]("http://www.turnkeylinux.org/")

---

### Post by c174 on 2010-03-12
> **Riel said:**
> Well, copy your drupal install to /var/www/drupal

I think it is not a good idea to make a copy of drupal, since I used Synaptic to install it. Instead I have used this, as suggested by carlee:

```
sudo ln -s /usr/share/drupal6/ /var/www/drupal
```

This works perfectly! :)

I put [http://localhost/drupal/install.php](http://localhost/drupal/install.php) in Firefox, ... the install continued automatically, and I just had to finish by filling in the name of my website, email, and admninistrator username and password.

I looked briefly at Turnkey Linux - it looks easy, but I didn't try since I already had installed drupal using Synaptic and wanted to get that running.

Thanks to everybody for your help :D

---

### Post by isbiyanto on 2010-05-06
> **carlee said:**
> if youve never really had any website design experience, go out and try a cms. youll have to install mysql, php, and apache2. if you have any queations, send me a pm or leave a post here and ill read it tomorow after I finish sleeping....

i use joomla, wordpress, and drupal. thanks for your advice

---

### Post by user1397 on 2010-05-06
For a very basic guide on how to build your own personal web server at home, try the guide in my sig.  Sounds like it is perfect for your needs.

As far as the web design itself, I recommend downloading free templates and messing around with the code in a simple text editor (like Gedit), and by using [www.w3schools.com](www.w3schools.com) as a reference.

---

