---
title: "PHP template"
date: 2012-02-25
forum: Server Platforms
---

### Post by gameguy on 2012-02-25
Is there some sort of template thing I can use for php on a LAMP server, where at the start of the file, certain code will be executed on certain files on the website. Specifically:

[LIST]
[*] template header / footer at the top and bottom of the HTML - all pages
[*]Check if you are logged in - all files except login, create account, and forgot password
[*]Log in to the mysql server and select a database - any page inside the login directory
[/LIST]
I have coded up all of these, but I would like to know how to make it happen on every page.

Also, I would like to have all the files on the server hidden unless specified.

---

### Post by SeijiSensei on 2012-02-25
> **gameguy said:**
> [LIST]
[*] template header / footer at the top and bottom of the HTML - all pages
[*]Check if you are logged in - all files except login, create account, and forgot password
[*]Log in to the mysql server and select a database - any page inside the login directory
[/LIST]
I have coded up all of these, but I would like to know how to make it happen on every page.

Create a template index.php file that contains no content of its own but uses include() or require() statements to build the actual HTML page from separate component files.  I usually have separate header and footer files, and a template body.  I'll also typically load some initialization files to connect to the database, load object libraries, and do other housekeeping activities at the start of each page.

So a typical index.php file might look like this:

```

<?php
$scripts="/path/to/scripts/";

# run startup routines; manage session (see below); connect to DB, etc.
require($scripts."startup.php");

include($scripts."header.php");
include($scripts."body.php");
include($scripts."footer.php");

require($scripts."cleanup.php");
?>


```

In this method, where the page is always called "index.php", you control the content to be displayed by the use of URL parameters.  I typically include one or two parameters on most pages.  The first, which I call "go" tells the PHP script which content to display.  Sometimes I add a second "do" parameter which controls which actions are performed on a particular "go" page.  Then I end up using URIs like this:

```
/index.php?go=directory&do=list
```

to display, e.g., a directory listing page.  In some cases I'll add other specific parameters.  For instance, the page for someone to edit a directory entry might be referenced by:

```
/index.php?go=directory&do=edit&user=1234567
```

which would tell the script to retrieve user 1234567's record and display it for editing.  The content displayed by "body.php" above would be determined by the values of these parameters.  

If you expect to be tracking users across multiple pages, e.g., after logging them in, you should make yourself acquainted with [PHP sessions]("http://www.php.net/manual/en/book.session.php").

> Also, I would like to have all the files on the server hidden unless specified.

With apache, the files need to be readable by the user under whose account the server software is running.  On Ubuntu that's the "www-data" user.  I usually put all my websites into separate /home directories with a structure like this:

```

/home/user
/home/user/include
/home/user/public

```

I put the scripts into /home/user/include, and the index.php file and any other publicly visible content like graphics in /home/user/public.  I point the DocumentRoot to /home/user/public.

This enables me to put more restrictive permissions on the /include/ directory where the actual code resides like this:

```

cd /home
sudo chmod 0711 user
cd user
sudo chown -R user.www-data include
sudo chown -R user.user public
sudo chmod 770 include
sudo chmod -R 640 include/*
sudo chmod 755 public
sudo chmod -R 644 public/*

```

This lets Apache's www-data user list and read all the directories under /home/user, but files in include are only readable by the user and www-data.  They are also outside the DocumentRoot /public/ directory so they can't be unearthed by browsing the site.

I add one additional layer of security by naming the included scripts with ".inc" extensions, then using a [FilesMatch]("http://httpd.apache.org/docs/2.2/mod/core.html#filesmatch") directive in Apache that prohibits downloads of files with that extension.

---

### Post by gameguy on 2012-02-25
That sounds like a good method, but I would like to have different pages, and have them not all display as index.html. Also, by securing the pages, this is what I mean. I seem to recall some sort of setting to turn on public directory listing or something like that.

What does sound useful, though, is the require and include methods. How would I use them properly? I gather I would need a checkloggedin file, a header file, a footer file, and a connect_db file, each a php script. Would I just say this on every file?

```

require(checkloggedin)
include(connect_db)
include(header)
include(footer)

```

---

### Post by SeijiSensei on 2012-02-25
Pretty much, though you need complete file paths in the include() and require() statements.

If you have separate pages, you'd need to include a few lines of the code at the top of each page to handle the initialization, etc.  I recommend trying to put as much content into common files, though, because it makes global changes much much easier.  

As for security, it sounds like you're talking about Apache's [Indexes option]("http://httpd.apache.org/docs/2.2/mod/core.html#options") which controls whether a directory may be listed.  The default in Ubuntu is to prohibit the listing of directories other than ones specifically designated in the site's configuration.  You need to allow Indexes in the DocumentRoot so that "index.html" or "index.php" will be displayed in response to a generic request for the root URI ("http://www.example.com/").  

But that's not the only security issue involved if you're trying to protect your code.  The best approach, as I described above, is to keep the code entirely separate from any publicly-visible location in a directory only you and the www-data user can read.  I've seen widely used PHP applications that put all the scripts in subdirectories below the DocumentRoot.  These directories inherit the Indexes setting for the parent and so may be visible unless you're careful about permissions.  To my mind this is just asking for trouble.

---

### Post by gameguy on 2012-02-25
That seems to make sense. Thanks.

Just one last thing. How does the include work. Do I need to use a return value on the include scripts - something like this?

```

<?
if ($_SESSION['user']) {
    return True;
} else {
    return false;
}
?>

```

---

