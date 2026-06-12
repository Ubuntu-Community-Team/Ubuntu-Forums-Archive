---
title: "Going to make a webpage. How can I make &quot;this&quot; feature"
date: 2006-06-12
forum: The Cafe
---

### Post by Jucato on 2006-06-12
Here's what I was planning to do basically: 

I want to make a webpage that has a blog in one of it's pages. Sort of like a blog integrated into the webpage. The main page (index.htm) would have a navigation bar at the side (or top), some links at the bottom, etc, and a blog in the main part.

The reasons I want something like this are:
1. I don't want to be limited, in terms of what I can do/add, by regular blogging services (blogger, for example). Most blogs are really just blog entries, with an additional page for a profile. The only way to add other content would be to link to an outside webpage. 
2. But I want the ease of adding entries that blogs offer. You know, where you just type in an entry and it will be added automatically. And that you could edit each entry individually. Also, the feature that lets other people comment on my entries is a nice feature.
3. I want an integrated website. I could probably have a webpage and a blog, then put the blog in a frame so that it could be seen inside the website, but that wouldn't be integrate. Also, last time I checked, frames in HTML wasn't that recommended. 

I'm very good (I think) with HTML and have had past experience with it, never used WYSIWYG editors, though. Just plain notepad. :D I also have very minimal knowledge with Javascript and CSS, but I could take the time and effort to learn. However, I can't make studying them a full-time activity, as I have other things to do. That's why I'm looking for something that would make my website easy to maintain, like how blogs are easy to maintain. And I don't want to use Flash, to make everyone's lives easier.

So what should I do, where should I start? What do I need to learn, and what software do I need? I've heard some things like CMS, but I don't know exactly what that could do, and I have no plans of running a forum anyway. :D

IMPORTANT EDIT: I won't be running/hosting the webpage on my own PC due to limits on my ISP and on the electricity bill. :D I'll be using a free web hosting service. I'm not sure if there are free services that allow PHP and MySQL, but I'm still looking.

EDIT: Oh, of course I will be working on Linux, so no Windows-only service please? (but that's already presumed, right?)

Anyone has any ideas how to make this dream of mine into a reality? I'd really appreciate any input/pointers. 

Thanks in advance!

---

### Post by basketcase on 2006-06-12
Wordpress?  

You could then just strip the CSS for your index.htm page and use wordpress for your blog.

---

### Post by Jucato on 2006-06-12
Gee that was fast! Thanks I'll check it out. :D

---

### Post by futz on 2006-06-12
> I also have very minimal knowledge with Javascript and CSS, but I could take the time and effort to learn.
Don't bother with javascript, but definitely DO learn CSS. It's totally awesome for building sites (I do the odd site for pay as well as build my own). 

CSS makes the html code tiny (separating content from presentation) and therefore fast loading. With one little CSS file you can control the look of the entire site with ease. None of the old editing every single page on a site to make a change in design.

CSS is the best thing I've learned in years! It just makes everything so much easier without the crappy old "locked tables" methods I (and everybody else) used to use.

Highly recommended are Eric Meyer's books, "Eric Meyer on CSS" and "More Eric Meyer on CSS". He also has a web-site [http://www.ericmeyeroncss.com/](http://www.ericmeyeroncss.com/)

Some other good sites to start from are:
[http://www.cameronolthuis.com/2006/04/top-10-css-tutorials/](http://www.cameronolthuis.com/2006/04/top-10-css-tutorials/)
[http://www.csszengarden.com/](http://www.csszengarden.com/)

WROX has a couple good books too. "Beginning CSS: Cascading Style Sheets for Web Design" and "Professional CSS: Cascading Style Sheets for Web Design". Both are very good as well.

Just google for "css tutorial" and "css design". There's tons of good stuff out there. The books are good, but expensive and probably not necessary. I learned from the web, but for some people books are easier.

EDIT: Learning Perl or other similar language would be wise if you want to automate your blog. Perl is funky, but wonderful for web work. But I suspect you'll find that there are tons of free blog services out there that you could work into your own page with not too much trouble.

---

### Post by basketcase on 2006-06-12
I also agree with what was said.  I love CSS, and has been the best thing I have learned.  To take a site that is a little bloated and make it VERY light weight only switching over to CSS, and only having to edit one page and it affecting all your pages vs. editing all pages.  Makes life easy.

---

### Post by Jucato on 2006-06-12
I was having some reservations about Javascript, as some people nowadays tend to block/disable javascript. But there might be some functions/features that can only be implemented using javascript, so I'm not totally closing my doors on it.

Yes, I think CSS will be worth learning. And for a big site, it will definitely be a necessity.

---

### Post by futz on 2006-06-12
[QUOTE=Fenyx]I was having some reservations about Javascript, as some people nowadays tend to block/disable javascript. But there might be some functions/features that can only be implemented using javascript, so I'm not totally closing my doors on it.[/quote]
Probably true, but fewer and fewer. You'll be shocked how much you can do with simple CSS and no javascript, and how easy and flexible it is.

> And for a big site, it will definitely be a necessity.
A big **DEFINITELY!**

---

### Post by ericesque on 2006-06-13
It'll be even better once MS updates their crusty old browser to current standards... or when the masses finally catch on to firefox.  no more css hacks would be nice.

---

### Post by futz on 2006-06-13
[QUOTE=ericesque]It'll be even better once MS updates their crusty old browser to current standards... or when the masses finally catch on to firefox.  no more css hacks would be nice.[/QUOTE]
That's for sure. IE is a mess. The new one might be better (let's hope)...

---

### Post by Jucato on 2006-06-13
@futz: thanks for the CSS links. I prefer to get my knowledge from the net, as they are usually more up-to-date or more regularly updated than books. That, and computer books here, at least the more recent ones, are quite expensive. That and most tutorials on the web I could download/save and put into my phone for viewing anywhere.

@basketcase: I've been reading around in WordPress, and it seems it might be exactly what I'm looking for. But I have to try it to really know for sure right? I installed wordpress from the repositories. I might sign up for an account in wordpress.com. Right now, I'm stumped on what to do. Anyway, I'll be reading up on it. Guess it will take up most of my time. :D

---

### Post by WildTangent on 2006-06-13
[QUOTE=futz]CSS makes the html code tiny (separating content from presentation) and therefore fast loading. With one little CSS file you can control the look of the entire site with ease. None of the old editing every single page on a site to make a change in design.

CSS is the best thing I've learned in years! It just makes everything so much easier without the crappy old "locked tables" methods I (and everybody else) used to use.[/QUOTE]
Simple use of PHP is great too. I use PHP for its include function. I've got a seperate folder in my web root with .inc files that have the HTML markup for such things as my top banner, sidebar, footer, etc. Then it's as simple as using this code to include it where you want it:
```

<?php include("path/to/your/include/directory/your_inc_file_here.inc"); ?>

```

You put those in wherever you want your include to be, and that's the only PHP code you need, for the rest you can just use plain HTML or XHTML markup. All you do differently is save the file as a .php file. You also need to have it hosted on a server that support PHP.

Here's a sampling of code from my homepage:
```

<?php 

$page = 'Index';

include("include/head.inc"); 

?>

<body>

```
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<!-- This code copyright 2006 Justin Hayes, AKA WildTangent. If you'd like to use it, please ask: wildtangent@w1ldt4ng3nt.net -->

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

  <title>WildTangent's Homepage<?php if( $page != 'Index' ){ echo ' - '; echo $page;} ?></title>

  <link rel="stylesheet" href="css/style.css" type="text/css" />

  <meta name="author" content="Justin Hayes"/>

  <meta name="description" content="Personal homepage of Justin Hayes" />
  
  <meta name="generator" content="Bluefish 1.0.4"/>

</head>

```
This code is what inserts all the page information for my code, it appears at the very top of my code. Those code snippets also show how I manage to make sure each page has its proper title.

-Wild

---

### Post by az on 2006-06-13
[QUOTE=Fenyx]So what should I do, where should I start? What do I need to learn, and what software do I need? I've heard some things like CMS, but I don't know exactly what that could do, and I have no plans of running a forum anyway. :D
[/QUOTE]
Well, wordpress does blogs very well, but you may want (or not) other features.  Drupal is another jack-of-all-trades CMS (drupal.org)  Take a look at the features.  

Now, the big picture:

You want to run this on your box, right?  You want to install this software on your computer and people will visit your site via the internet.

If you have broadband internet, check your ISP's tems and conditions.  Some prohibit you from running HTTP services.  Some don't.  Some even block port 80.  Whatever.

So, if you can do this, another obstacle is that home broadbad providers do not give you a static ip address unless you pay for it.  That's a bundle.  But don't worry.  There are tons of free dynamic dns services available.  See dyndns.org.  You sigh up and you can get a free dynamic dns. 

That means that people will find your box on the internet by visiting your dyndns url
Example:
whosyourdaddy.dyndns.org

or
andy.dyndns.org

You need to install the dynamicdns client on your box to tell the dyndns provider what your current ip address is whenever it changes.


sudo apt-get intstall ddclient

or if you are using a router, config your router to do it - most of them have dyndns clients built-in.


Then install apache mysql php and drupal or wordpress (or any other cms (see cmsmatrix.org))

You will need to create a mysql database and then confgure your cms to use that database.  Your done.



Someone should write a basement-webserver-specific guide.  Currently, the serverguideon the wiki is a little unfriendly, but useful:
[https://wiki.ubuntu.com/Servers](https://wiki.ubuntu.com/Servers)

---

### Post by Jucato on 2006-06-13
Yeah I'm looking at wordpress right now. But I'm quite confused with everything.

I won't be running it on my box. My ISP doesn't allow it, AFAIK. (Sorry about that, I'll edit my first post to make it clear).

I was under the (mis)impression that I would be able to create the webpages, layout, etc. offline, then upload them to a (free) web host server. Then content would either be created online or offline (then sent to the web page through e-mail or some 3rd party apps) like what some blogs do.

Maybe I'm just dreaming if this was possible at all. I presumed that was how Wordpress.org and Wordpress.com worked. I thought that the wordpress software allowed you to create the layout and contents on my PC (offline), then upload/sync them with the web host of my choice, in this case, WordPress.com, since it's the only free web hosting service that has PHP and MySQL.

I'm beginning to wonder if what I was thinking is even possible... :(

Thanks for the suggestions azz.

---

### Post by futz on 2006-06-13
Oh ya! Forgot this link: [http://cssvault.com](http://cssvault.com)

Go there and dig thru the Resources section. There's some *amazing* tutorials out there.

---

### Post by Johnsie on 2006-06-14
If you have php you should use the include feature. If not then you might wanna search the web for information about IFRAMES. However I'm not sure that all browsers suppor IFRAMES.

Javascript is a big no-no unless you have to. It would just complicate things.

---

### Post by Jucato on 2006-06-14
is javascript really that bad? I learned HTML during a time when frames were depracated, Javascript was the "in" thing, and templates meant tables. I guess I have a long way to go in learning new stuff.

Is it possible create a "frames"  effect using CSS. I mean the effect where you click on links, but the changes only happen in a specific portion of the web page. For example, I would have a menu sidebar and a header/footer, and if I click on a menu entry, only the main part of the page changes/loads while the header/footer, and menu remains unchanged. I'm not sure if I can afford to learn PHP and Perl for the mean time.

@azz (I hope you're going to be able to read this): I suddenly realized that my ISP doesn't specifically state that I can't host my own web page. I'll have to check with them. But I also have absolutely 0 idea on how to do that, whether in Linux or in Windows. Would you be kind enough to give some links to web hosting for absolute newbies? I'm willing to take the risk and make the jump, as hosting my own web page  would mean I could make use of PHP and MySQL stuff, right? Only downside is that my web page can't be up 24/7. :D

---

### Post by az on 2006-06-15
[QUOTE=Fenyx]
But I also have absolutely 0 idea on how to do that, whether in Linux or in Windows. Would you be kind enough to give some links to web hosting for absolute newbies? I'm willing to take the risk and make the jump, as hosting my own web page  would mean I could make use of PHP and MySQL stuff, right? Only downside is that my web page can't be up 24/7. :D[/QUOTE]
[https://wiki.ubuntu.com/Servers](https://wiki.ubuntu.com/Servers)

As for the 24/7, you can always buy a used pII (or even a Pentium one) and install LAMP on that.  Leave it turned on, like your refrigerator.  You don't even need a monitor.   You don't need a powerful box to do what you want, unless you want hundred of people to visit your site at the same time.

---

### Post by WildTangent on 2006-06-15
LAMP servers are easy, but I don't like the option the Server image disk provides. It doesn't configure it completely, I'd much rather install it myself and know exactly how its been configured. A manual install is really easy:
```

sudo apt-get install apache2 php5 php5-mysql mysql-server-5.0 libapache2-mod-auth-mysql

```

Then you need to configure PHP to "talk" to MySQL:
```

sudo nano /etc/php5/apache2/php.ini

```
Find (ctrl+w in Nano) the line ";extension=mysql.so" and remove the ";" to uncomment it. Save the file.

Then, set up MySQL:
```

cd /usr
sudo ./bin/mysql_install_db --user=mysql
sudo mysql -u root
```
You are now in the MySQL console. Notice you didn't need a password? We must fix that. ;)
```

SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');

```

Finally, we must make a change to the Apache configuration:
```

sudo gedit /etc/apache2/apache2.conf

```
Find these lines:
```

User www-data
Group www-data

```
Change both instances of "www-data" to the username you created during setup of Ubuntu.

That all covers basic installation of a LAMP server. I know it sounds complicated, but it really isn't.

-Wild

---

### Post by Jucato on 2006-06-15
thanks for your inputs. I've decided against hosting my site for some reasons:

1. I don't have much time to study webhosting/servers, etc. I'm still in the middle of trying to finish some (personal) projects so I can't afford to focus on that.
2. I don't have another box to use as a server. If I were to host my own site, it would be probably using the same box I use as a desktop, which isn't really recommended, right?
3. I don't know my ISP's policy for doing this. And because of the reasons above, I wouldn't bother asking them. Besides, my I only have a bandwidth of 300+ kbps, so it's not really ideal for hosting.

So thanks for all your answers. I will probably be using either WordPress (because it has a separate "Pages" function) or Blogger (because it's more customizable) until I get to the point that I can do what I want using CSS alone. I guess PHP will be a no-no since no free web hosting service offers that.

Last two questions, though:
1. Are blogs using PHP to insert what they would call "templates" or "tags"? For example, in my previous experience with BlogDrive.com, I could modify the layout of the page, and just put tags like [blog] or [date] to display the proper content.

2. In CSS, can I emulate the effect of <frames> where I click on a menu entry at the left side, and only the main window at the right changes while the rest of the page remains static? I don't want to use frames anymore, as they have been considered non-standard. iFrames, too, I think (though I'm not totally sure).

---

### Post by futz on 2006-06-15
[QUOTE=Fenyx]2. In CSS, can I emulate the effect of <frames> where I click on a menu entry at the left side, and only the main window at the right changes while the rest of the page remains static? I don't want to use frames anymore, as they have been considered non-standard. iFrames, too, I think (though I'm not totally sure).[/QUOTE]
Yes you can. I've never done it, but just googled for it and here's the links:
[http://www.cssplay.co.uk/layouts/frame.html](http://www.cssplay.co.uk/layouts/frame.html)
[http://www.thescripts.com/forum/thread100026.html](http://www.thescripts.com/forum/thread100026.html)
[http://www.456bereastreet.com/lab/cssframes/](http://www.456bereastreet.com/lab/cssframes/)
[http://www.fu2k.org/alex/css/frames/](http://www.fu2k.org/alex/css/frames/)
[http://underscorebleach.net/jotsheet/2004/12/frames-with-css-layout](http://underscorebleach.net/jotsheet/2004/12/frames-with-css-layout)
[http://rudhar.com/sfreview/html_en/frames.htm](http://rudhar.com/sfreview/html_en/frames.htm)

Hahahahaha! There's LOTS more. Bet you feel like a doof for asking the question before googling for it, right? ;)

---

### Post by Jucato on 2006-06-15
I did google for it, and my head ached with so many hits that I didn't know where to start. I also couldn't find one that matched what I was looking for. Or maybe I just didn't use the right search keywords.

Thanks for the links. I'll browse through them all. :D

---

### Post by futz on 2006-06-15
[QUOTE=Fenyx]I did google for it, and my head ached with so many hits that I didn't know where to start. I also couldn't find one that matched what I was looking for. Or maybe I just didn't use the right search keywords.[/QUOTE]
Just to give ya a hint of how to use google more effectively, here's what I searched for:

First search: css frame emulation

Second search: css frames

Both gave good results, but the second search was a bit better focused.

---

### Post by Jucato on 2006-06-15
oh I see. I used "css frames target", so I guess I'm quite off the mark.

Thanks again, specially for your patience. :D

---

