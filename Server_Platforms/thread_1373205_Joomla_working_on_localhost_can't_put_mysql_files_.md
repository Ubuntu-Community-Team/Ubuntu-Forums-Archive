---
title: "Joomla working on localhost: can't put mysql files on a hosting service (godaddy)"
date: 2010-01-05
forum: Server Platforms
---

### Post by BuzzGizard on 2010-01-05
Preamble.. I know there are many threads addressing this issue.. and I think I've tried a significant portion of the advice that's out there with no luck. Here, I'll write how I got here and what I've done so far looking for the solution:

I'm very new to design and this is my first joomla site. I've also been using Linux Ubuntu for a year now. I think my feet are getting wet, but that's the limit of my experience.

So, i think my site turned out surprisingly well and I am excited to get it on the godaddy server. The first of the 2 attached images is a screenshot of the files that I've moved to godaddy so far. This includes the template and most files, but I can't get the MySQL database to import on godaddy. I don't want to lose all of my content! The second image shows the MySQL (i think) databases that need to accompany the joomla files for the site to work, as it does on localhost. 


When I try to import the databases through godaddy's FTP I get the following error message:
[I]Error

SQL query:

--
-- Database: `information_schema`
--
CREATE DATABASE `information_schema` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

MySQL said: Documentation
#1044 - Access denied for user 'bmt'@'%' to database 'information_schema' [/I]

I really would like to get this up and running even if I have to use a different hosting service. It would be nice to get it working with godaddy since I've already paid for it though. Any advice or tips? I probably could be more clear if I knew what I was doing a bit more. I've read 100 threads about similar issues, but the advice was all over the place and some i tried while others just looked way beyond me. I appreciate your help! 

Oh, and here is my configure.php file in case it would be helpful.  
[B]
configure.php file (in case it would be helpful)?:[/B]
**Quote:**
<?php
class JConfig {
    var $offline = '0';
    var $editor = 'tinymce';
    var $list_limit = '20';
    var $helpurl = 'http://help.joomla.org';
    var $debug = '0';
    var $debug_lang = '0';
    var $sef = '1';
    var $sef_rewrite = '0';
    var $sef_suffix = '0';
    var $feed_limit = '10';
    var $secret = 'WuyMxC6R0HzbHl5B';
    var $gzip = '0';
    var $error_reporting = '-1';
    var $xmlrpc_server = '0';
    var $log_path = '/var/www/joomla/logs';
    var $tmp_path = '/var/www/joomla/tmp';
    var $live_site  = 'http://www.mysite.com';
    var $offset = '0';
    var $caching = '1';
    var $cachetime = '15';
    var $cache_handler = 'file';
    var $memcache_settings = array();
    var $ftp_enable = '0';
    var $ftp_host = '127.0.0.1';
    var $ftp_port = '21';
    var $ftp_user = 'ftpusername';
    var $ftp_pass = 'ftppassword';
    var $ftp_root = '';
    var $dbtype = 'mysql';
    var $host = 'localhost';
    var $user = 'godaddydatabaseusername';
    var $db = 'joomla';
    var $dbprefix = 'jos_';
    var $mailer = 'mail';
    var $mailfrom = [EMAIL="%27myaddress@berkeley.edu"]'myaddress@berkeley.edu[/EMAIL]';
    var $fromname = 'stuff';
    var $sendmail = '/usr/sbin/sendmail';
    var $smtpauth = '0';
    var $smtpuser = '';
    var $smtppass = '';
    var $smtphost = 'localhost';
    var $MetaAuthor = '1';
    var $MetaTitle = '1';
    var $lifetime = '15';
    var $session_handler = 'database';
    var $password = 'mygodaddydatabasepassword';
    var $sitename = 'notsurewhatgoeshere-URL or ';
    var $MetaDesc = 'stuff';
    var $MetaKeys ='stuff';
    var $offline_message = 'This site is down for maintenance. Please check back again soon.';
}
?>

---

### Post by BkkBonanza on 2010-01-05
That message indicates that you don't have permission for that user bmt@% where bmt is the mysql username and % is probably localhost. I'm not familiar with the details of what they give you for controlling mysql on GoDaddy but generally a host will provide some way to configure user privileges for mysql. Perhaps through a control panel of some sort. 

You need to find that and add/edit a user for yourself, or if they assign you a user then make note of it. Then you need to make sure that Joomla is going to use the user for accessing the database. Also that user needs to have privileges for that specific database. This is all about getting mysql configured for your use. I'm not a GoDaddy user so I can't give you more exact details - but hopefully someone who uses them can...

To create a database/tables you need to have "create" privilege assigned to the user.

Edit: Ah, I see from your photos that they give you phpMyadmin. That's good. Use the privileges tab to alter them for user "bmt" so it has the rights you need. Probably "ALL" for now though you may tighten it later after it works.

From your php script: var $user = 'godaddydatabaseusername';
Make sure this name matches your user name in mysql, and likewise password.

---

