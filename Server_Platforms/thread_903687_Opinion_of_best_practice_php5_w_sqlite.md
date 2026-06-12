---
title: "Opinion of best practice: php5 w/ sqlite"
date: 2008-08-28
forum: Server Platforms
---

### Post by kdnewton on 2008-08-28
My question: At the bottom of this post.

The scenario:

I have LAMP installed and also apt-get installed php5-sqlite and sqlite (though I'm not sure if installing sqlite was necessary if I only intend to use it with php5).

I created a symlink
`sudo ln -s /home/myusername/path/to/testdir /var/www/testdir`
and pasted in the example code from [http://www.devshed.com/c/a/PHP/Introduction-to-Using-SQLite-with-PHP-5/2/](http://www.devshed.com/c/a/PHP/Introduction-to-Using-SQLite-with-PHP-5/2/) into testdir/index.php (and also removed the "unsigned" part of the "unsigned primary key" as it appears sqlite2 doesn't support unsigned ints).

at which time, of course, I was presented with an error. php5-sqlite requires write access to the directory.

What I've done is added myself to the www-data group
`sudo usermod -a -G www-data myusername`
and then changed the group ownership to www-data
`chgrp www-data /home/myusername/path/to/testdir`
(although looking back now I see I probably didn't have to add myself to the www-data group). And then changed the dir properties to allow rwx for my user and the www-data group
`chmod 0775 /home/myusername/path/to/testdir`

I apologize for the long-winded explanation of what I've done so far. It's my belief that anyone else interested in the topic can find the similarities between what they might have done and then what the proper solution might be.

So if anyone can tell me please, what is the best way of going about allowing sqlite to have read/write access to the directory?

---

