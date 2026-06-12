---
title: "Server-side Scripting"
date: 2013-03-17
forum: Server Platforms
---

### Post by furiousanger on 2013-03-17
Afternoon all, 

I have been banging my head against this for a few days now, and need some help ! I have an Ubuntu 12.04 server with media directories containing films and music etc. I have another server which is effectively a mirror of the other for all intents and purposes. What I am trying to do is: 


[LIST]
[*]Use Unison to copy between the servers, and keep the directories in sync using shell scripts
[*]Create a webpage with links/buttons to the relevant scripts to execute them
[/LIST]

So far I have managed to get the shell scripts up and running, which work fine. I have managed to test both that PHP is working on my primary server, and that CGI scripts are able to run. What I cannot figure out is how to create the webpage with the links/buttons. I am getting lost between using PHP / CGi / HTML and getting the output right. 

Any help would be appreciated ! 

Thanks

---

### Post by kuifje09 on 2013-03-17
Well , its not easy to build a secure working html server with cgi-scripts.
It is also not very difficult to start with it.
But it is not very easy to explain it in short.

Best to just read some docs and try one yourself, then ask for specific problems you encounter.

And I am thinking now you want to create a apache server ? right.
Maybe lighthttpd is an option, I never used it.
You may also install additional plugins for appache to handle the php code.

There is a lot of docs around.  just google for   html and cgi  and  apache.
Apache has very good documentation.

I just copy the first I found.
[URL="http://http://www.jmarshall.com/easy/cgi/"]
http://www.jmarshall.com/easy/cgi/[/URL]

[http://snowwhite.it.brighton.ac.uk/~mas/mas/courses/html/html.html](http://snowwhite.it.brighton.ac.uk/~mas/mas/courses/html/html.html)


But a quick hind.

You have a running apache server,   then the page you create is html, with some javascript maby.  and direct links or via the javascript to your  phpscripts on  the apache server.

Edit, to get the output from a script back in your page, you might need ajax. ( sensitive to browsertype )
with ajax you can update a part of your page using "name=" and name is then filled with the returned code.
Have a look here : [http://www.w3schools.com/ajax/default.asp](http://www.w3schools.com/ajax/default.asp)

---

### Post by kuifje09 on 2013-03-17
If it is just about a local page and script then this might help , just made a very little example and a bit incomplete :

create in "your homedir" as example 2 files    aap.html and  noot.php

aap.html:
```

<!DOCTYPE html>

<script>

function Justjava()
{
      alert("Hello World!");
      return true;
}

function Justphp()
{
        window.open ("file://home/"SOME-USER"/noot.php");
        return true;
}

</script>

<body>
<button onclick="Justjava()" type="button">Click Me! java</button>
</br></br>
<button onclick="Justphp()" type="button">Click Me! php</button>

</body>
</html>

```

and noot.php :
```

<?php

// Show all information, defaults to INFO_ALL
phpinfo();

?>


```

Load aap.html and see if you get the picture.

---

### Post by furiousanger on 2013-03-17
Thanks for that, its a start. 

The JAVA button works fine, but the PHP button doesnt do anything.

---

### Post by thnewguy on 2013-03-17
Assuming PHP is enabled on your server you could using something like

```

<form action="myscript.php">
<input type=submit value="Run Script">
</form>

```

Then put your actions into the myscript.php file. As someone else pointed out this isn't really secure as anyone with access to your web server will be able to run the script (or perhaps other scripts) on your server. A more secure and reliable method would be to run your backup/sync script using cron. This would allow you to perform backups at regular intervals without need for user intervention and it would remove a good deal of the security risk.

---

### Post by kuifje09 on 2013-03-17
Shure you installed php ?   phpinfo can be used as testpage.
Tells a lot and creat a nice page for testing

If you want to use ajax also,  this is a nice tutorial : [http://www.tizag.com/ajaxTutorial/index.php](http://www.tizag.com/ajaxTutorial/index.php)

---

### Post by kuifje09 on 2013-03-17
Just in case of.. I can be you configured your browser to deny new paes or popups.
The php button creates a new window for the result of the command.

---

### Post by tgalati4 on 2013-03-17
Is there a reason that you are not using a content management system (CMS) like drupal?  [http://drupal.org](http://drupal.org)  The heavy lifting has already been done.  There is a learning curve, but once it is installed and running, it's works pretty well to serve up media.

---

### Post by furiousanger on 2013-03-18
Re. Drupal, lack of experience and not actually realising what it does.


Have installed it now though, just trying to get a scripts module loaded onto it.

---

### Post by tgalati4 on 2013-03-18
Don't forget to load the *views* module.  Very important for creating templates.  Watch some videos, listen to some Drupal podcasts, read some Drupal forums, read some blogs on how people use Drupal.  It may have a learning curve, but it beats programming a CMS from scratch.  Unless it is a class assignment.

[http://twit.tv](http://twit.tv) is a media-heavy website that uses drupal.

---

### Post by furiousanger on 2013-03-23
Okay, I have managed to get some way further with this. I am now stuck with this code that is supposed to move files from one directory to another: 

[php]<?php
$output = shell_exec("sudo find /media/storage/documents -name '*.doc' -type f -exec mv '{}' /media/storage/backup/ \; 2>&1");
echo "<pre>$output</pre>";
?>[/php]

I am calling this from a button on another page, but I am now getting the following message: 


find: missing argument to `-exec'I am so close to what I am trying to achieve, I can taste it ! 

Help greatly appreciated

---

### Post by SeijiSensei on 2013-03-23
Unless you have added the "www-data" to the sudoers list, or you are running Apache as root, which is strongly discouraged, you cannot run a shell command with sudo from a PHP script.  The easiest solution is to make sure that the www-data user has appropriate permissions on the directories and files and any destinations.

---

### Post by furiousanger on 2013-03-23
I already have the permissions set correctly from the sudoers file. 


I would point out aswell that this is an internal websrver, with no access to/from the outside world.

---

