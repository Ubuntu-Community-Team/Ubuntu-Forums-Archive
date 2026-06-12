---
title: "Web Design with Drupal as a back end."
date: 2007-10-03
forum: The Cafe
---

### Post by Omnios on 2007-10-03
Drupal web development pertaining to Linux

Did not see a web development section so posting in Community. The story so far I waited for about three weeks where I managed to get three free webhosts but could not install dropal on them as they restricted certain files such as .htaccess and a hole bunch of other files that returned a this type is not allowed error. FreeWeb7 is working hard to make drupal run on there server and I think older versions of Drupal might work there as there are apparently sites with drupal but have found no solutions as of yet.

 Anyways I snagged a free  c-panel account with a free .info host name from the admin of FreeWen7 and managed to get drupa installed. I started looking into modules for Drupal including a integration modual for SMF forums there are a few other forum that will integrate with Drupal but have not tryed them yet.

 My current site is a rest rig which I will rebuild from scratch once I figure out what modules etc I need for my website. Also made the mistake of trying to install 4.??? stuff and found out later that this was not a module version but reference to what Drupal version you have installed. I will have to seed it out as my /drupal/module file is about 100 megs so far lol.

 K there is different stuff available such and am currently trying to figure out how to make custom pages within drupal for different nodes not show up.

 My main thing right now is trying to figure out how to make a SMF drupal page with different menus etc. But more so a way to show the smf extras such as newest posts etc to show on the forum page and not ont the others. I am trying to get things mixed so all the forum stuff shwos on the forum page and only a few forum parts on the other page possibly such as new  posts etc.

---

### Post by Mr. Picklesworth on 2007-10-04
I've recently come to the realization that the reason there are so many CMSs to choose from is because a CMS that 'just works' is simply impossible. Every web site is slightly different, and the specialized ways that these CMSs tend to operate just doesn't fit with that. In other words, I can smell a Drupal site from a mile off.

They do work great for some people, but if you find trouble with it and want to keep exploring, I suggest you check out web frameworks like Django. They are designed to simplify the process of creating what ammounts to your own CMS (or whatever you want to call it). May seem more complicated, but working with a CMS generally means reversing a pile of what exists as a default; if you *build* the CMS, it's actually easier in the long run. (Django is *very* cool).

Particularly fun is that Django lets you escape the satanic ritual that is PHP, saving at least half of the development time and *a lot* of hair. Instead, you get to work with Python, which is a well designed language whose core capabilities do not fluctuate with every release. Easier than building from scratch, since, as a web framework, it has four very advanced and completely decoupled systems that automatically manage your database and administration systems (while keeping them both easy to tweak), do theming and handle URLs, making everything else dead easy.

---

### Post by az on 2007-10-04
Use Drupal 5.2.  Drupal 6 will be out soon and the 4.7 release will not be supported once that happens.

> **Omnios said:**
> 
Did not see a web development section so posting in Community. The story so far I waited for about three weeks where I managed to get three free webhosts but could not install dropal on them as they restricted certain files such as .htaccess and a hole bunch of other files that returned a this type is not allowed error. FreeWeb7 is working hard to make drupal run on there server and I think older versions of Drupal might work there as there are apparently sites with drupal but have found no solutions as of yet.

Drupal does not have that much of a different requirement than any other CMS out there.  It is database-intensive, so if your database server is on a different machine, or if your shared hosting provider overloads the server, you will experience very poor performance.

In general that's the case for free hosting.

> **Omnios said:**
> 
 My main thing right now is trying to figure out how to make a SMF drupal page with different menus etc. But more so a way to show the smf extras such as newest posts etc to show on the forum page and not ont the others. I am trying to get things mixed so all the forum stuff shwos on the forum page and only a few forum parts on the other page possibly such as new  posts etc.

There are many menu-related modules available.  You should be able to customize your menus without having to hack any code.

The smf integration module does all that you mention and more:
[http://drupal.org/project/smfforum](http://drupal.org/project/smfforum)
Quote:
"1) SMFforum: User login
Allow forum users to login to your Drupal site with their drupal or forum
username and passwords and provides synchronization with the forum.
When a user changes his/her Drupal accounts and profile settings,
the changes will be synced back to the forum database.
Likewise, if the user changes his/her forum profile, it will be synced back
to the Drupal site.

2) SMFforum: Hidden User login
Allow forum users to login to your Drupal from SMF if you are not using
SMFforum: User login block.

3) SMFforum: New forum topics
Display a list of the latest forum topics.

4) SMFforum: New forum posts
Display a list of the latest forum messages.

5) SMFforum: Online forum users
Display a list of all on-line forum users.

6) SMFforum: Forum statistics
Display forum statistics including: number of users, threads, messages,
newest member, etc.

7) SMFforum: Personal messages
Display your forum personal messages if you are logged in.

8) SMFforum: Top posters
Display a list of the top posters."

[http://drupal.org/project/Modules/name](http://drupal.org/project/Modules/name)

---

### Post by curuxz on 2007-10-04
IMHO if your talking Web design with a CMS backend then drupal is not the way to go, its pretty widly agreed that joomla leads when it comes to web design with its theme systems. No matter what the arguments about tables are (Which are being solved in 1.5) you have to admit that there are far and away more themes and normally nicer themes from joomla, droopal is just not as easy to design for.

my 2cents :)

---

### Post by 50words on 2007-10-04
Just installed Joomla and it looks much more like what I am looking for in a CMS. I have been playing with Drupal, as well, trying to convert my website and two blogs to a CMS system ([http://sjglover.com](http://sjglover.com)).

---

