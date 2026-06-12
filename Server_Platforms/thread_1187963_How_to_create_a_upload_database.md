---
title: "How to create a upload database"
date: 2009-06-15
forum: Server Platforms
---

### Post by Grey08 on 2009-06-15
Hi

I have Ubuntu 8.10 server installed (using ubuntu desktop GUI), as well as LAMP,phpmyadmin enabled. So i m thinking to create a upload database for my own convenient with MySQL, in the situation such as allowing my friends upload some files to my server and i can download at other places.

What do i do for doing this, and how to start with MySQL?
(MySQL has been correctly setup, with root privileges. Besides that, Apache,PHP5 have already installed and it is working now.) 

Best regards
Grey08

---

### Post by smeerbartje on 2009-06-15
> **Grey08 said:**
> Hi

I have Ubuntu 8.10 server installed (using ubuntu desktop GUI), as well as LAMP,phpmyadmin enabled. So i m thinking to create a upload database for my own convenient, in the situation such as allowing my friends upload some files to my server and i can download at other places.

What do i do for doing this?

Best regards
Grey08
This has nothing to do with Ubuntu. You need to make a choice what software you want to use. Since you are not very familiar with this stuff I would suggest you set up a FTP server. Just Google.

---

### Post by Grey08 on 2009-06-15
Oh yea, i didn't clearly mention about the question. By the way, i have installed ProFTP, and most of my friends they don't know how to upload/download without GUI. That's why i m thinking to create a web based upload database so that they can easily do the uploading. 

Ok, i have editted the topic.

---

### Post by Cheesemill on 2009-06-15
What your talking about is not a database.

One way for you to achieve this would be to set up openssh-server on your machine and forward the required ports through your router. You could then use scp on linux machines or WinSCP on windows machines to transfer files.

You could also look into AjaXplorer as you already have your LAMP server setup.
[http://www.ajaxplorer.info/](http://www.ajaxplorer.info/)


Edit - Just read that you have ProFTP installed. You do know that Windows Explorer is an FTP client don't you? You just have to type [ftp://yourip/](ftp://yourip/) into the address bar.

---

### Post by cdenley on 2009-06-15
If you insist on using a web interface for uploading, I would suggest [uber-uploader]("http://uber-uploader.sourceforge.net/"). I would not suggest using proftpd without SSL encryption, and I don't think windows explorer supports FTP with SSL. FileZilla works on windows or linux with FTP, FTP with SSL, or SSH.

---

### Post by Grey08 on 2009-06-15
> **Cheesemill said:**
> What your talking about is not a database.

One way for you to achieve this would be to set up openssh-server on your machine and forward the required ports through your router. You could then use scp on linux machines or WinSCP on windows machines to transfer files.

You could also look into AjaXplorer as you already have your LAMP server setup.
[http://www.ajaxplorer.info/](http://www.ajaxplorer.info/)


Edit - Just read that you have ProFTP installed. You do know that Windows Explorer is an FTP client don't you? You just have to type [ftp://yourip/](ftp://yourip/) into the address bar.

Yes, but Windows explorer only allows users to View/Download, and i m planning to let my friends to View/Download/Upload (and of course before uploading requires a login/ verification).

Layman don't know how to upload with these, all in their mind are, ms windows is Computer, terminal (black screen) is something unknown. upload files with terminal is already beyond their knowledge.

Wow, AjaXplorer is COOL. But it was built in windows application only, ain't it? cuz it is *.zip.


> **cdenley said:**
> If you insist on using a web interface for uploading, I would suggest uber-uploader. I would not suggest using proftpd without SSL encryption, and I don't think windows explorer supports FTP with SSL. FileZilla works on windows or linux with FTP, FTP with SSL, or SSH. 

You got me, yes, that's what i want!! Thanks! But is there any other better options? I prefer something like PHP code can paste to my homepage, so that whenever my friends want to give me something, they can go to my homepage and upload, as well as showing the files after uploaded.


Best regards
Grey08

---

### Post by v3xtra on 2009-06-15
If you just set up accounts for your friends on your computer for the FTP server, then they can do exactly what you want, view, save, and upload like normal through the FTP.  You can EVEN use SFTP, which goes through port 22, which is SSH and more secure than just FTP.  Any FTP client works too, I had an SFTP server running very simply, and was able to use Filezilla on both Windows and Ubuntu to connect to it, and was able to save, view, and upload files to the server.

PHP options in your browser are more pain than they are worth, because you will have to update the page everytime, you will most likely need a MySQL database to keep track of everything, and unless you know how to get MySQL and PHP to work hand in hand very well, you're probably shooting for something out of your league.  It can be done if you do a bit of research and look online for topics on this, but until you do, I wouldn't suggest it.

Searching on google I found literally TONS of topics about upload scripts in PHP which are ready for the most part to copy paste.

[http://www.google.com/#hl=en&q=php+upload+script+&aq=f&oq=&aqi=g10&fp=DLh7wmTRH1c](http://www.google.com/#hl=en&q=php+upload+script+&aq=f&oq=&aqi=g10&fp=DLh7wmTRH1c)

What you will want to have after that is some kind of index of files, which is not a difficult thing to do.  Just add a field in the form for a FileName, and then input that filename and the actual filename where it is stored to a database ( a simple INSERT command ).  A simple SELECT statement will select all of the filenames, which you can easily output to the webpage to show what files are available for download.  Then, using the filename that it was saved under on the computer, you can easily create a link that allows you to download that file to your computer.

As I said though, if you are looking for an easier solution to this, SFTP is your best bet, it is easy to install and get working, you can give users access to different things ( so that they cannot go into your root directory and screw things up ), and it will give them a GUI ( with FileZilla or any program supporting SFTP ) to manipulate their files.  I would definitely suggest TRYING SFTP and if it isn't for you moving on to some sort of PHP script.  :)

Hope that helps, if you would like help with a PHP script after trying SFTP, I would be happy to try and help.

---

### Post by Cheesemill on 2009-06-15
> **Grey08 said:**
> Wow, AjaXplorer is COOL. But it was built in windows application only, ain't it? cuz it is *.zip.

Nope. AjaXplorer is a web app, you can install it on any machine that has a LAMP stack.

I have it running on my headless Ubuntu 8.04 web server.

---

### Post by Grey08 on 2009-06-15
> **v3xtra said:**
> If you just set up accounts for your friends on your computer for the FTP server, then they can do exactly what you want, view, save, and upload like normal through the FTP.  You can EVEN use SFTP, which goes through port 22, which is SSH and more secure than just FTP.  Any FTP client works too, I had an SFTP server running very simply, and was able to use Filezilla on both Windows and Ubuntu to connect to it, and was able to save, view, and upload files to the server.

PHP options in your browser are more pain than they are worth, because you will have to update the page everytime, you will most likely need a MySQL database to keep track of everything, and unless you know how to get MySQL and PHP to work hand in hand very well, you're probably shooting for something out of your league.  It can be done if you do a bit of research and look online for topics on this, but until you do, I wouldn't suggest it.

Searching on google I found literally TONS of topics about upload scripts in PHP which are ready for the most part to copy paste.

[http://www.google.com/#hl=en&q=php+upload+script+&aq=f&oq=&aqi=g10&fp=DLh7wmTRH1c](http://www.google.com/#hl=en&q=php+upload+script+&aq=f&oq=&aqi=g10&fp=DLh7wmTRH1c)

What you will want to have after that is some kind of index of files, which is not a difficult thing to do.  Just add a field in the form for a FileName, and then input that filename and the actual filename where it is stored to a database ( a simple INSERT command ).  A simple SELECT statement will select all of the filenames, which you can easily output to the webpage to show what files are available for download.  Then, using the filename that it was saved under on the computer, you can easily create a link that allows you to download that file to your computer.

As I said though, if you are looking for an easier solution to this, SFTP is your best bet, it is easy to install and get working, you can give users access to different things ( so that they cannot go into your root directory and screw things up ), and it will give them a GUI ( with FileZilla or any program supporting SFTP ) to manipulate their files.  I would definitely suggest TRYING SFTP and if it isn't for you moving on to some sort of PHP script.  :)

Hope that helps, if you would like help with a PHP script after trying SFTP, I would be happy to try and help.

Thanks for your suggestions, i found that very useful. The problem is, some of the user without better computer knowledge, they don't know what is filezilla, how to get it, and how to connect to my server and things. Imagine my 40 years old aunt with less knowledge of computer, her daily life with computer is only switch on computer, click on web browser and check the email or surf for some News, any other than that she wouldn't know. So i guess the best solution for these kind of users, is to set the web page with upload option for them (since email provides this kind of feature), so that i can easily guide them through telephone.  

Isn't this solution is easier for them?? Correct me if i m wrong.
By the way, i have tried the link about the PHP script. It can upload files, but the file seems like missing after uploaded and couldn't be found in my MySQL database. There are several warnings too telling me error occurred.

---

### Post by cariboo on 2009-06-16
The first thing to think of, is your aunt really going to upload files, be realistic. My dad is in his late 70's and every time he wants to sent pictures to family in europe I have to show him how to attach files to an email. This is my own fault, because I do it for him, the best thing to do is to educate them on how to upload files.

Any cms (content management sytem) will allow you to set up and upload/download system. I haven't played with any of them for a couple of years, but the last one I tried was [xoops]("http:///www.xoops.org/"), it is pretty easy to setup.

---

### Post by Grey08 on 2009-06-16
This is not only for my aunt :) Every user has different level of knowledge, thus we can't just expect they know everything (even these FTP upload/download technics are easier for us). When these happen to have GUI, things are easier for us to guide them through the phone, correct?

By the way, i have tried this PHP script and it works. 

[PHP]<form enctype="multipart/form-data" action="upload.php" method="POST">
Please choose a file: <input name="uploaded" type="file" /><br />
<input type="submit" value="Upload" />
</form> [/PHP]


[PHP]<?php
$target = "upload/";
$target = $target . basename( $_FILES['uploaded']['name']) ;
$ok=1;
if(move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
{
echo "The file ". basename( $_FILES['uploadedfile']['name']). " has been uploaded";
}
else {
echo "Sorry, there was a problem uploading your file.";
}
?> [/PHP]



It upload files to another folder, which is convenient for me. Another question, how should i start with MySQL then? I feel like want to make use of MySQL, what i do now?


Best regards
Grey08

---

### Post by Cheesemill on 2009-06-16
> **Grey08 said:**
> Another question, what do MySQL do then? I feel like want to make use of MySQL, can i do something with it?

Read these for background info on databases / MySQL.
[http://simple.wikipedia.org/wiki/Database](http://simple.wikipedia.org/wiki/Database)
[http://en.wikipedia.org/wiki/MySQL](http://en.wikipedia.org/wiki/MySQL)

---

### Post by Grey08 on 2009-06-16
sorry for my english, i have editted #11.

I meant to say, i want to make use MySQL, but how do i start?

I have tried this PHP script, but it doesn't work:

[http://php.about.com/od/phpbasics/ss/mysql_files_2.htm](http://php.about.com/od/phpbasics/ss/mysql_files_2.htm)

[PHP]<?
$name=$_POST['name'];
$email=$_POST['email'];
$location=$_POST['location'];
mysql_connect("192.168.1.8", "username", "password") or die(mysql_error());
mysql_select_db("Database_Name") or die(mysql_error());
mysql_query("INSERT INTO `data` VALUES ('$name', '$email', '$location')");
Print "Your information has been successfully added to the database.";
?> [/PHP]

it shows the error:
```
Warning: mysql_connect() [function.mysql-connect]: Host 'Edward.local' is not allowed to connect to this MySQL server in /var/www/process.php on line 5
Host 'Edward.local' is not allowed to connect to this MySQL server
```

---

### Post by guilly on 2009-06-16
> **Grey08 said:**
> sorry for my english, i have editted #11.

I meant to say, i want to make use MySQL, but how do i start?

I have tried this PHP script, but it doesn't work:

[http://php.about.com/od/phpbasics/ss/mysql_files_2.htm](http://php.about.com/od/phpbasics/ss/mysql_files_2.htm)

[PHP]<?
$name=$_POST['name'];
$email=$_POST['email'];
$location=$_POST['location'];
mysql_connect("192.168.1.8", "username", "password") or die(mysql_error());
mysql_select_db("Database_Name") or die(mysql_error());
mysql_query("INSERT INTO `data` VALUES ('$name', '$email', '$location')");
Print "Your information has been successfully added to the database.";
?> [/PHP]

it shows the error:
```
Warning: mysql_connect() [function.mysql-connect]: Host 'Edward.local' is not allowed to connect to this MySQL server in /var/www/process.php on line 5
Host 'Edward.local' is not allowed to connect to this MySQL server
```

I'm pretty sure the user Edward does not have permissions to connect the database. You must enter the correct credentials into "username" and "password". How are these two variables getting filled? I suggest for testing purposes to simply hard code values into your mysql_connect method. Once you get the proper connection then bring it to the next level and ask the user to enter in it's credentials.

---

### Post by Grey08 on 2009-06-17
Which username and password should i enter? MySQL's or Ubuntu's password itself?

---

### Post by Grey08 on 2009-06-17
I have editted the $dbhost to 127.0.0.1

[PHP]
<?
$name=$_POST['name'];
$email=$_POST['email'];
$location=$_POST['location'];
mysql_connect("127.0.0.1", "root", "xxxxxxxx" or die

(mysql_error()));
mysql_select_db("upload") or die(mysql_error());
mysql_query("INSERT INTO `data` VALUES ('$name', 

'$email', '$location')");
Print "Your information has been successfully added to 

the database.";
?> [/PHP]

And the information can send to database now, but it appears
'reading initial communication packet', system error: 111 in /var/www/11/process.php on line 5

```
Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server at 'reading initial communication packet', system error: 111 in /var/www/11/process.php on line 5
Your information has been successfully added to the database. 
```

What happened to the process.php??

---

### Post by guilly on 2009-06-17
try removing your loopback address, and adding your local ip for the server.

It's probably having a hard time binding to the 127... address.

---

### Post by Grey08 on 2009-06-17
> **guilly said:**
> try removing your loopback address, and adding your local ip for the server.

It's probably having a hard time binding to the 127... address.

loopback address means 127.0.0.1, isnt it? Local IP address refers to server's IP(192.168.1.8) or my another pc(192.168.1.10) in the LAN?

Best regards
Grey08

---

### Post by Grey08 on 2009-06-18
Alright, i have settled the mysql_connect problem as below:

[PHP]@ $db = mysqli_connect('localhost', 'username', 'xxxx');[/PHP]

and the warning is not appear again.

The question now, how to retrieve the data and show at web with PHP? Can anyone shares their script?

Thanks.

Best regards
Grey08

---

### Post by v3xtra on 2009-06-18
What is location?  Is that the filename that they are uploading to the server?

Then if that is the case, all you will really need to do is just a normal SELECT * FROM data and output it.  There are many ways to do this, one of them is mysql_fetch_array, mysql_fetch_result, or mysql_fetch_assoc all work.  For instance, this may work for your purpose:

```
$sql = "SELECT * 
        FROM   data;

$result = mysql_query($sql);

if (!$result) {
    echo "Could not successfully run query ($sql) from DB: " . mysql_error();
    exit;
}

if (mysql_num_rows($result) == 0) {
    echo "No rows found, nothing to print so am exiting";
    exit;
}

// While a row of data exists, put that row in $row as an associative array
// Note: If you're expecting just one row, no need to use a loop
// Note: If you put extract($row); inside the following loop, you'll
//       then create $userid, $fullname, and $userstatus
while ($row = mysql_fetch_assoc($result)) {
    echo $row["name"];
    echo $row["email"];
    echo $row["location"];
}

```

That should be the general format, what you will most likely need to do is to add a hyperlink in the echo that will put the first part of your address, i.e [http://192.168.1.1/uploads/](http://192.168.1.1/uploads/), and then echo the location part ( or the filename ) after that, and then exit the echo.  What this will do is allow you to upload a file, and unless that filename changes, you should be able to download that file with no problems.  You can set it up in a table format too to make it look more appealing and easier to understand, but it is not necessary.

Hope that helps, the php manual is a huge help for things like this, as most of the comments are snippets of code that could help you!  :)

---

### Post by Grey08 on 2009-06-21
> **v3xtra said:**
> 
```
$sql = "SELECT * 
        FROM   data;

$result = mysql_query($sql);

if (!$result) {
    echo "Could not successfully run query ($sql) from DB: " . mysql_error();
    exit;
}

if (mysql_num_rows($result) == 0) {
    echo "No rows found, nothing to print so am exiting";
    exit;
}

// While a row of data exists, put that row in $row as an associative array
// Note: If you're expecting just one row, no need to use a loop
// Note: If you put extract($row); inside the following loop, you'll
//       then create $userid, $fullname, and $userstatus
while ($row = mysql_fetch_assoc($result)) {
    echo $row["name"];
    echo $row["email"];
    echo $row["location"];
}

```



Thanks for your reply, but the code seems like somewhere missing semicolon? Because the output shown error with [unexpected T_STRING on line 2].

And, what did u mean "where is the location"??

---

### Post by v3xtra on 2009-06-21
Sorry, the SQL statement should be:

```
$sql = "SELECT * FROM data";
```

I missed the last ".  :)

---

### Post by guilly on 2009-06-21
I don't want to be the bad guy here and discourage you with this project, but if you can't trouble shoot simple SQL statements like the one above. There's no way you will be able to accomplish this task without some major help, what will most likely happen is that people will end up coding this project for you which will not help you in the long run.

I suggest you start learning some SQL and PHP and then in a few months come back to this project you have...

---

### Post by Grey08 on 2009-06-23
Saw another statement as follow:

[PHP]$data = mysql_query("SELECT * FROM data")
or die(mysql_error());[/PHP]

and it solved the T_String problem.

Is that possible we do this:

```
[form]
Particular: 
option A: Cash
option B: Purchase
option C: Sale

Amount: [text]

submit
[/form]

```

Once it submits, the data will upload to different table according to the option selected? For instance, when the particular is selected Cash, amount will submit to table 'cash'?


Best regards
Grey08

---

### Post by meditatingfrog on 2009-06-23
Dear Grey08:

I think you and I are in the same boat.  I have installed MySQL on my laptop so that I can practice my SQL coding skills.  I do have experience writing queries for retrieving data, but I have worked, as time allows, on my database creation skills in mysql (such as create table, create database, and insert into commands)  I found getting the syntax right to be rather challenging.  

What I wanted to do, was to create a database of my random thoughts, so that I can query against them.  I thought this would be a good thing to do to understand my own consciousness.  Unfortunately, my coding skills aren't efficient enough to make it possible for me to complete the project within a decent amount of time.  Needless to say, I will continue to practice my mysql coding skills, to hopefully get to a point where I complete at least a considerable portion of the database I've mentioned.

Your project of wanting to be able to use a webserver to handle file copying (also backup and restore of files) is a good idea.  I think it would be cool to set up the server I have here for the same purposes.  People are mentioning sftp as the solution.  This is interesting, because you point out that sftp isn't a solution for your end users because they need a GUI.  This being the case, perhaps there is a way to develop a GUI for sftp?  Or perhaps there is a way to utilize a web interface as the gui, that will interact with sftp?  Just some ideas, tell me what you think.  I'm going to turn on my server now, and play with it a bit.  My initial aversion to starting up the server is the cost of electricity, but I suppose electricity isn't that expensive, and using the server as my preferred method of backup (as opposed to the usb thumb drive I'm using) might help me justify the cost of electricity.  I'm not sure.  Money is pretty tight right now that I don't have a job.  :(

---

