---
title: "access virtual host through ip and directory"
date: 2012-09-06
forum: Server Platforms
---

### Post by Ortix on 2012-09-06
I'm trying to set up a testing environment on my home server and i want a certain directory in /var/www/ to be linked to my /home/ folder. So basically when I type in

192.168.1.125/directory

it goes to /var/www/directory

but instead i want it to go to /home/directory

how would i go about doing that?

Thanks!

---

### Post by Sergius14 on 2012-09-06
Inside /etc/apache2/sites-enabled you should have a file for running site .

Edit that file (with vi or nano) and in there you shoud find ServerAlias and DocumentRoot.

I guess that ServerAlias is already configured and should only change DocumentRoot.


That is an aproach.

---

### Post by Wim Sturkenboom on 2012-09-07
I don't think that that's really a virtual host ;)

Create a symlink in /var/www that points to your home directory

```

cd /var/www
sudo ln -s /home/yourusername/remainder_of_directorypath somesite

```

But it's not a virtual host, just a subdirectory in your normal host.

---

### Post by SeijiSensei on 2012-09-07
Two caveats.

First, make sure that FollowSymLinks is enabled in the [Options]("https://httpd.apache.org/docs/2.2/mod/core.html#options") directive in the <Directory> stanza that applies to /var/www in the virtual host definition (e.g., /etc/apache2/sites-available/default).  Another alternative is to use the [Alias directive]("https://httpd.apache.org/docs/2.2/urlmapping.html") in the <VirtualHost> container:

```
Alias /bill /home/bill
```

Second, the web server runs as user "www-data" and typically will not have permission to read files in /home/username.  You can fix this as follows:

```

cd /home
sudo chmod 711 username

```

You should check and make sure that the linked directory has world-readable privileges, e.g, 755.

---

### Post by Wim Sturkenboom on 2012-09-07
There is another caveat to websites in a user's home directory; apache can't write there.

Not always an issue, but for e.g. websites that generate reports for download, it's an issue. Permissions can be set on e.g. a *_specific_* directory so apache can write there.

---

### Post by HugoSerrano on 2012-09-07
It's just for test? Only one user?
You can change apache user in /etc/apache2/envvars 

export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

Change www-data to the user.

And then change the apache root to user home instead /var/www

restart apache and your done.

Best Regards!

---

### Post by Ortix on 2012-09-07
I created a symlink and i got it to work (kinda, i still need to click on public_html but that's fine, if anyone knows a quick fix it would be appreciated but it's not a big deal)

However i'm running a joomla site and none of the directories are writable. Like Wim said, apache can't write there because the user is www-data. I can't do what Hugo said because the server will be used for testing environments. Would suPHP be an option?

EDIT
I'm not sure if this is appropriate but I went ahead and installed suPHP but now I have one problem. My site is located at /home/exo/sites/www.exo-l.com/public_html. Obviously that's outside of the standard docroot configured by suPHP. But if I want to change that, how do I point it to the [www.exo-l.com](www.exo-l.com) part without making it website specific. for "exo" i can just use ${HOME}... 

I hate configuring webservers. 

BTW I'm running openpanel. If i could I'd just move everything over to /var/www/ but I don't know how to change the vhost template of openpanel.. I'll research that

---

### Post by Wim Sturkenboom on 2012-09-07
Change the group ownership of public_html to www-data and next change the permissions to 770.

```

chgrp www-data /home/exo/sites/www.exo-l.com/public_html
chmod 770 /home/exo/sites/www.exo-l.com/public_html

```

Not tested, but it will probably do the trick.

Note:
suPHP sounds dangerous

---

### Post by Ortix on 2012-09-07
Wim, i tried what you suggested but with no avail. I disabled suPHP as well btw. I am curious, how do other web servers solve this problem? When the ftp uploads with user rights and apache runs as www-data?

---

### Post by Wim Sturkenboom on 2012-09-07
My intranet websites work like that. (real) Virtual hosts with the 'documentroot' located in the user's home directory.

Not running Ubuntu servers, though.

---

### Post by SeijiSensei on 2012-09-07
> **Ortix said:**
> Wim, i tried what you suggested but with no avail. I disabled suPHP as well btw. I am curious, how do other web servers solve this problem? When the ftp uploads with user rights and apache runs as www-data?

The only permissions the web server needs to have is the ability to read the files in the DocumentRoot.  To enable that you must, as I said before, change the permissions on /home/username to at least 711 and set the permissions on the directory where the website files are located to at least 755.

Suppose you set the DocumentRoot for a site to /home/harriet/mysite.  Then you need to do the following:

```

cd /home
sudo chmod 711 harriet

```

Then as user harriet create /home/harriet/mysite and put the files in there.  Usually the default will set permissions for that directory to 755, which is read/write for harriet, and readable and listable for everyone else.

If you upload files with FTP, those files need to be world-readable.  That's set with the "umask" command in /home/username/.profile.  Sometimes the FTP server is configured to have more limited permissions like only read/write for the user and nothing for anyone else.  The FTP server software often has its own umask setting which overrides the default.  At a minimum the umask should be 022 which translates into read/write for the user, and read for everyone else.

---

### Post by Wim Sturkenboom on 2012-09-08
> 
The only permissions the web server needs to have is the ability to read the files in the DocumentRoot

With the risk of going off-topic.

Where will a file, uploaded vi http, be stored? Or where will a php script store reports?

---

### Post by SeijiSensei on 2012-09-08
I'm not sure I know what you mean by "reports," but if a PHP script writes files, where they are stored depends on how you write the script.  For instance:

```

<?php
$myreport='some bunch of text to write out';
$fp=fopen('/path/to/some/folder/myreport.txt','w+');
fwrite($fp,$myreport);
fclose($fp);
?>

```

/path/to/some/folder/ must be a directory writable by the www-data user.  That means www-data must have at least execute permissions on every parent, grandparent, etc., directory above the final one, and write and execute permissions on the directory where the file is stored.  It doesn't have to have read permissions, though, which can be useful to create files that cannot later be read by the web server, but only by a user with valid rights.

If you use HTTP uploads via PHP, again the location is arbitrary, but it must be writable by www-data.  Look at the documentation for [PHP file uploads]("http://php.net/manual/en/features.file-upload.php") and the [move_uploaded_file()]("http://www.php.net/manual/en/function.move-uploaded-file.php") function for details.

For security purposes, you should be writing files to directories outside the web tree.  Don't write files into the DocumentRoot unless they are intended to be displayed over the web once written.  Even in cases like that, I'll put the content somewhere outside the DocumentRoot and manage access via a script that requires a login or into a directory under the DocumentRoot that uses HTTP Basic Authentication to restrict access.

---

### Post by Wim Sturkenboom on 2012-09-08
Sorry, should have been more clear. I have a site that logs incidents (in a database). Users of the site can pull information from the database in the form of a report (e.g. csv file); a hyperlink is provided that the user can click. That report / file needs to be accessible via the document root else the user can't view / download it.

So where would you store that file? Or how would you approach it?

---

### Post by SeijiSensei on 2012-09-08
> **Wim Sturkenboom said:**
> So where would you store that file? Or how would you approach it?

I'd write a PHP script that queries the database and generates the file on-the-fly.  If you don't care who can see the file, then putting it in the DocumentRoot is fine.  If it contains information that might be considered sensitive, I'd at least create a separate directory off the root, put the file there, and manage access with [HTTP Basic Authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html").

---

### Post by Wim Sturkenboom on 2012-09-09
Thanks, that's what I indeed do. And it implies that apache needs write access under certain circumstances.

Sorry for going a bit off-topic.

---

### Post by SeijiSensei on 2012-09-09
Technically you wouldn't need to write the file anywhere if you generate it on-the-fly.  You could store the report CSV data as a string in PHP, then send it directly to the browser.  You can use the header() function to wrap the report in the Content-Type and Content-Disposition headers, open a separate browser window, and stream the data directly to the browser.  The user would see the file download dialog box pop up.  Here's [a similar example]("http://www.daniweb.com/web-development/php/threads/72631/create-and-send-text-file").

---

### Post by Wim Sturkenboom on 2012-09-10
Thanks, learned something again.

---

