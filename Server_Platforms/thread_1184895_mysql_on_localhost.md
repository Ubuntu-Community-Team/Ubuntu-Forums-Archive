---
title: "mysql on localhost"
date: 2009-06-11
forum: Server Platforms
---

### Post by DFHIII on 2009-06-11
I am trying to connect to mysql on localhost and I get an error message saying mysql cannot connect to user ''@localhost.  I looked at the User table and I have an entry with localhost as Host and User as blank.  Is that a valid entry in the User table?  The connection I am trying to make has % as Host and User as LSAuthor.  

The php code where the error occurs is:

 $conn = db_connect($HTTP_SESSION_VARS['con_h'], $HTTP_SESSION_VARS['con_id'], '');

Prior to executing db_connect I echo the both session vars.  They are:

con_h = localhost and con_id = LSAuthor.

Any ideas?

Thanks,

Dan H.

---

### Post by ubila on 2009-06-11
If you cant connect, how are you able to view the user table? Are you trying to connect to localhost from another computer ?

---

### Post by cariboo on 2009-06-11
Is this what you are looking for?

```
grant all privileges on *.* to LSAuthor@'%' identified by '<password>' with grant option;
```

The above user will be able to access mysql remotely with full privileges eg:

```
mysql -h server -u LSAuthor -p
```

---

### Post by DFHIII on 2009-06-11
I appologize for not being more specific about my problem.  

I am developing an application using LAMP on Ubuntu 8.04 LTS desktop edition.  All was going well until my hardware failed, so I had to rebuild my system on other hardware.  That apparently went well.

I can connect to mysql and my database via the command line, but php code that apparently worked on the old system doesn't now.

In the user table I can find LSAuthor as a user on any host.

mysql> select Host, User, Password from user;
+-------------+------------------+-------------------------------------------+
| Host        | User             | Password                                  |
+-------------+------------------+-------------------------------------------+
| localhost   | root             | *945B8F314DB5EC371FFC18535123E8176747C09B | 
| dan-desktop | root             | *945B8F314DB5EC371FFC18535123E8176747C09B | 
| 127.0.0.1   | root             | *945B8F314DB5EC371FFC18535123E8176747C09B | 
| localhost   | debian-sys-maint | *91E76FCF99FA7A61C169413BEB1F5234F94150AC | 
| %           | LSAdmin          | *33E0789D55ECFFBC7BCDAA0A92E00249073717F4 | 
| %           | LSStudent        |                                           | 
| %           | LSAuthor         |                                           | 
+-------------+------------------+-------------------------------------------+
7 rows in set (0.01 sec)

When I execute the following php code segment --

  // Connect to database.
  $conn = db_connect($HTTP_SESSION_VARS['con_h'], $HTTP_SESSION_VARS['con_id'], '');
  if (!$conn)
  {
    echo 'con_h: '.$HTTP_SESSION_VARS['con_h'].'<br />';
    echo 'con_id: '.$HTTP_SESSION_VARS['con_id'];

    do_html_header('Learning System', 'Author Login');
    $err_msg = 'Could not connect to the database.<br />';
    $err_msg .= 'mysql error number: '.mysql_errno().'<br />';
    $err_msg .= 'mysql error: '.mysql_error();
    $continue = 'Author_Login.php';
    display_err_msg($err_msg, $continue);
    do_html_footer();
    exit;
  }

I get the following on my webpage --

con_h: localhost
con_id: LSAuthor

Learning System

Author Login
Could not connect to the database.
mysql error number: 1044
mysql error: Access denied for user ''@'localhost' to database 'LearningSystem'
Click Continue

Why doesn't it find LSAuthor as user on localhost?  I'M STUMPED!!

Thanks,

Dan H.

---

### Post by v3xtra on 2009-06-12
First off, it isn't reading your username in correctly, as if it was, it would be stating:

```
mysql error: Access denied for user 'LSAuthor'@'localhost' to database 'LearningSystem'
```

Secondly, I would try and add a password to the user, because first off it is not wise to leave it unpassworded, and it makes life just a little bit easier for everyone ( I've always had issues trying to figure out how to connect to a database correctly without a password.  Using a password just makes sense and is easier.  :) )

Thirdly, to test whether or not the connection even works, have you tried actually connecting to it through the command line as LSAuthor and with no password?  If that works, then try just using

```
db_connect('localhost', 'LSAuthor', PASSWORD('password'), 'LearningSystem');
```

To make sure that you are not messing up the outputs ( I always have difficulty knowing when to use escape strings and where/how, and usually a lot of the time nothing gets shown because I am not formatting anything right.  I have a feeling you aren't because it is not showing the username ).

I hope that helps a bit, I know that I've had trouble in the past and I just hope that I could help a little bit with that, and I hope that you get it fixed!  :)  Best of luck!

---

### Post by DFHIII on 2009-06-12
It WORKS!!

I am back in operation.  The problems I was having came from not following all of the necessary steps while trying to rebuild my system.  I am learning those steps through trial and error.

I am going to try to list the steps I took from installing from the CD to testing my code.  The final hang-up I had, not being able to connect through the PHP code was fixed be removing the the entries in the mysql User table that had no user name.  When I did that the PHP code I presented earlier worked and I am back in business.

I have in mind to summarize this experience in a document so that when I have to rebuild again I will know what has to be done.

This conversation has been very helpful to me as I have to think through what I have done and am doing and figure out what is happening.  I am new to linux and ubuntu and like to summarize these conversations into a single document, explaining the problems and solutions.  Would this kind of document be of use to the community as a whole, and where would I put it?

Thanks again to all of you for your help.

Dan H.

---

