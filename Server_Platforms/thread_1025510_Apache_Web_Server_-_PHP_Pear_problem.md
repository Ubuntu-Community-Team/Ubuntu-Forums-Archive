---
title: "Apache Web Server - PHP Pear problem"
date: 2008-12-30
forum: Server Platforms
---

### Post by jeffcham on 2008-12-30
I have installed Apache, PHP and PHP Pear. Apache works and PHP appears to work from the CLI, I can't get it to work from a web browser.

When I enter the web address ie [http://localhost/index.php](http://localhost/index.php) I get the following message.

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

What have I missed?

---

### Post by Adrien Lamothe on 2009-05-29
You have to uncomment and add to the "include_path=.:/usr/share/php" line in /etc/php5/apache2/php.ini configuration file.

The original line will look something like:

;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"
;include_path = ".:/usr/share/php"
;


You need to uncomment the "include_path" line and then add the path for the directory where your pear packages reside, like this:

;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"
include_path = ".:/usr/share/php:/usr/share/pear/PEAR"
;


In this case, pear is installed in /usr/share/pear and the directory where the pear packages live is PEAR (some pear installations use a lower-case directory name of "pear", so check your installation to see which it is.) Of course, you can install pear anywhere, so use the path appropriate to your installation. /usr/share/pear is a good place to install pear.

After modifying /etc/php5/apache2/php.ini like this, you then need to restart Apache2 for the change to take effect, like so:

$sudo /etc/init.d/apache2 restart

That should take care of the problem. You've doubtless figured it out by now, but I'm adding this response for the benefit of anyone else who may experience this problem.

;)  Adrien

---

### Post by drubdrub on 2009-08-12
Having the same problem.  I'm attempting to configure prestashop, which depends on php5.

I noticed that PEAR is not installed on the system, so installed the package.  PEAR stuff is installed in /usr/share/php/PEAR, not /usr/share /pear.  Made the changes to the /etc/php5/apache2/php.ini file, as noted in this thread, supplying /usr/share/php/PEAR.  The file now looks like

> ;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"
include_path = ".:/usr/share/php:/usr/share/php/PEAR"


Restart apache with each php.ini change.  Did not solve the problem.  Only the error changed, reflecting the changes made to php.ini

> Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/www/pfp/install/index.php' (include_path='.:/usr/share/php:/usr/share/php/PEAR') in Unknown on line 0
Please note the difference ... this error shows "/usr/share/php/PEAR", not "/usr/share/pear".

Hey Adrien, your coaching shows > include_path = ".:/usr/share/php:/usr/share/pear/PEAR"  Is that a typo?  There is no /usr/share/pear on my system.  

System:  9.04

---

### Post by drubdrub on 2009-08-12
Tried watching /varl/log/apache2/error.log for hints.  No help there.

It is now functioning.  But, I don't like it *at all*.

The solution?  "chmod -R 777" to the directory contents.  Way ugly!  Fortunately, this is not a public server.  Who knows what security exposure results from this horrible action.

Thanks

---

### Post by am7555 on 2009-08-13
Hi, 
I am new to Ubuntu but I have installed Apache, php and Mysql on Windows before and never had this kind of problems. I have machine that is my sandbox where I'm running dual boot Ubuntu/Windows. I insatlled Apache and PHp and MYSQl recently and managed to setup /var/www as my root Directory.  To access the newly installed server I am using Dreamweaver from another machine on the same network.  

My rpoblems started initially trying to uplaod files to a directory and there weher permisiion problems. Once that was solved I was able to see the files from my development machine.
However, once I created a small database, and created a connection using Dreamweaver, worked nicely until I uploaded the file to the server and tried browsing and got the following error:

Warning: require_once(/nspdev/Connections/connNSP.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/nspdev/test.php on line 1

Fatal error: require_once() [function.require]: Failed opening required '/nspdev/Connections/connNSP.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/nspdev/test.php on line 1

drubdrub, How did you solve your problem?  I tried the suggestions and even installed Pear but no luck at all. 

Any help is appreciated.

Javier

---

### Post by drubdrub on 2009-08-13
Howdy

Javier, I got by the errors by opening permissions to 777, recursively, on the entire directory contents.  That is a [COLOR="DarkOrange"]***way ugly***[/COLOR] solution.  I fear there could be [COLOR="DarkOrange"]severe security implications[/COLOR].  I do **[COLOR="DarkOrange"]*NOT*[/COLOR]** recommend that technique on a public server!!!

I kept bumping into other problems, even after the ugly solution.  This all occurred while attempting a Prestashop install, so I simply re-copied the Prestashop files into the relevant directory.  All went well the second time.

So, I was not able to (or willing?) to ID root cause of the errors discussed in this thread.  Sorry.  Wish I could be better help.

The one coaching point I can offer is ... look closely at the PEAR related paths in the php.ini file.  See my prior post for the details.  Easy to make mistakes there.  Location on my system did not match the doc, or locations earlier in this thread.  Your mileage may vary!  

Best of luck!


> **am7555 said:**
> 

... stuff removed

drubdrub, How did you solve your problem?  I tried the suggestions and even installed Pear but no luck at all. 

Any help is appreciated.

Javier

---

### Post by am7555 on 2009-08-13
Drubdrub,
Security issues are not a corcern for this project. It is only a server for developing and not a public server. 

I am inclined towards unistalling apache, php, mysql and re-starting from scratch.  I am not keen at using the prepackaged LAMP but I may go that route if nothing else works.

Thanks for the reply.

Javier

---

