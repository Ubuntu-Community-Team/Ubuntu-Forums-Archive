---
title: "Getting Drupal 6 going"
date: 2011-04-02
forum: Server Platforms
---

### Post by kamaji792 on 2011-04-02
I am trying to get Drupal 6 going on a box on my local network.  I want to use it as a test bed to learn about Drupal.

I have been using this [https://help.ubuntu.com/community/Drupal]("https://help.ubuntu.com/community/Drupal") howto.

It has all gone reasonably smoothly apart from the point where I run the **install.php** script.  I opt to install in English and I get a page telling me that the 'Choose language', 'Verify requirements' and 'Set up database' have run fine.  It stops on 'Install site' where I get the following errors:

[LIST]
[*]user warning: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ') ORDER BY fit DESC LIMIT 0, 1' at line 1 query: SELECT * FROM menu_router WHERE path IN () ORDER BY fit DESC LIMIT 0, 1 in /usr/share/drupal6/includes/menu.inc on line 315.
[*]    user warning: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ') ORDER BY fit DESC LIMIT 0, 1' at line 1 query: SELECT * FROM menu_router WHERE path IN () ORDER BY fit DESC LIMIT 0, 1 in /usr/share/drupal6/includes/menu.inc on line 315.
[/LIST]

To start with when I run the install.php script I don't get the same page as in the howto.  I wonder if this is because I am connecting remotely (from another PC on the network) or because the script failed.

I have looked at the error and am suspicious of the **...WHERE path IN() ORDER BY...'**.  I am sure the **IN()** should have something in the brackets.

In setting up my test box I did set the domain name to 'localhost' as I am never sure what to set it to and am wondering if that might be the problem.

Anybody who can make any sense of the above and offer help or support would be greatfully receaved.

---

### Post by sanderd17 on 2011-04-02
I would start over, my guess is that drupal gets some info from the database and that that info has to be between the brackets. But if the database isn't configured right, the brackets could be empty. Just be sure you have the right mysql database and use the right username and password when you try it again.

---

### Post by leg on 2011-04-02
also remember that you have stated that you are installing on a seprerate machine on your network. When you run it in the browser it wont be localhost it will be the server name.

---

### Post by kamaji792 on 2011-04-09
Thanks for the replies.

I gave up on the apt-get Drupal install and plodded though the manual install.  When you take it in small steps it was not so hard and I now have a far better understanding of how Drupal works.

The first time I got exactly the same error in the manual install.  Eventually I ended up changing the Drupal MySQL user password to something less complicated and that got it going.

For those thinking of having a play with Drupal, if you understand how to create a user in MySQL, you should have no problem doing the manual install.

I still do not have clean urls running but I am sure I will get there eventually.

Found it a bit hard to find a nice introduction tutorial but this one seems pretty good (though I have not completed it yet):

[http://sixrevisions.com/web-development/getting-started-with-drupal-a-comprehensive-hands-on-guide/](http://sixrevisions.com/web-development/getting-started-with-drupal-a-comprehensive-hands-on-guide/)

All the best

---

