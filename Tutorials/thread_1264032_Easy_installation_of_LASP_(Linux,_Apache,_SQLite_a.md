---
title: "Easy installation of LASP (Linux, Apache, SQLite and PHP)"
date: 2009-09-11
forum: Tutorials
---

### Post by bubblehead74 on 2009-09-11
Credits. This tutorial has been originally posted under Creative Commons Attribution-Noncommercial-No Derivative Works 3.0 United States License here:
[http://www.bioinformatics.org/librarian/blog/2009/09/11/easy-installation-of-lasp-linux-apache-sqlite-and-php-on-ubuntu/]("http://www.bioinformatics.org/librarian/blog/2009/09/11/easy-installation-of-lasp-linux-apache-sqlite-and-php-on-ubuntu/")

If you think about learning how to create dynamic database-driven web sites, the simplest way to start is with PHP and SQLite. PHP offers high level programming, but most importantly, unparalleled documentation with clear and easy to understand usage examples. There are many SQL database engines out there, but SQLite is definitely the most simple to set up, because it is completely self-contained, cross-platform, and serverless. SQLite database is actually a single file that is also cross-platform. Conveniently, SQLite comes bundled in PHP5 as PDO extension. This extension provides abstracted access to your database. It means that if you later decide to switch to a different database like MySQL or PostgreSQL, you can use the same functions that you used to access SQLite.

Ubuntu is a wonderful Linux distribution that makes installation of this software extremely easy. Installation process literally takes seconds. All you need to do is open Terminal and type:

```
sudo aptitude install apache2 php5 php5-sqlite
```

Hit enter and type your password when you are prompted. That's really it! Aptitude is an installation program that will take care of everything. It will download, install and configure Apache with PHP and PDO SQLite driver. Your server is now running and you can verify that by opening your web browser and typing [http://localhost](http://localhost). The directory for this website is /var/www. To create a page, press Alt-F2 and type:

```
gksu nautilus
gksu gedit
```

This will open the file browser and the text editor Gedit with root privileges. Now you can navigate to /var/www and create a directory (e.g. /var/www/testsite), where you can create your first file. In Gedit window, write:

[PHP]<?php

echo "I like ".PHP_OS;

?>[/PHP]

Save the file in /var/www/testsite as test.php. Now open your web browser and go to [http://localhost/testsite/test.php](http://localhost/testsite/test.php). You will see white page with "I like Linux".

Creating SQLite database is also very easy. There are a few things, however, that you should know. First, the best practice is to place the database file outside the /var/www directory. For our purpose, create new directory /var/databases/testsite. Second, Apache needs write permissions for both the directory where the database resides and the database file itself. Therefore you must change the owner of the database directory to Apache. Open Terminal and write:

```
sudo chown www-data /var/databases/testsite
```

Now create the database with single table "mybooks". Save the following in /var/www/testsite as createdatabase.php:

[PHP]<?php

$dbHandle = new PDO("sqlite:/var/databases/testsite/database.sqlite");

$dbHandle->exec("CREATE TABLE mybooks (id INTEGER PRIMARY KEY, author NOT NULL, title NOT NULL)");

$mybooks = array
(
     "Mass Effect: Revelation" => "Drew Karpyshyn",
     "Mass Effect: Ascension" => "Drew Karpyshyn",
     "Dragon Age: The Stolen Throne" => "David Gaider"
);

while (list($title,$author) = each($mybooks)) {

     $author = $dbHandle->quote($author);
     $title = $dbHandle->quote($title);
     $result = $dbHandle->exec("INSERT INTO mybooks (author,title) VALUES ($author,$title)");
}

?>[/PHP]

Create the database, go to [http://localhost/testsite/createdatabase.php](http://localhost/testsite/createdatabase.php).

Finally, create a dynamic web page that will randomly display a single book from your library. Save the following as pickbook.php:

[PHP]<?php

$random = rand(1,3);

$dbHandle = new PDO("sqlite:/var/databases/testsite/database.sqlite");

$result = $dbHandle->query("SELECT * FROM mybooks WHERE id=$random");

$book = $result->fetch(PDO::FETCH_ASSOC);

echo "Random peek into my libary:<br><br>$book[title] by $book[author]";

?>[/PHP]

Go to [http://localhost/testsite/pickbook.php](http://localhost/testsite/pickbook.php) and refresh the page several times to see that the book titles are indeed randomly picked from your database.

I hope you see from this brief example the idea behind PDO and how simple SQLite is to setup and use on Ubuntu. There is so much more you can do with the simple but powerful SQLite. Visit these links to learn more:
[http://www.php.net/manual/en/book.pdo.php]("http://www.php.net/manual/en/book.pdo.php")
[http://sqlite.org]("http://sqlite.org")

---

### Post by Newbie89 on 2013-05-23
How to install LASP in chroot?

---

