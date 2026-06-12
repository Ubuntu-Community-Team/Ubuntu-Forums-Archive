---
title: "perl cgi configuration setting in my homw PC"
date: 2010-09-13
forum: Server Platforms
---

### Post by Lesliesathish on 2010-09-13
Dear friends,

   I planned to lear perl CGI, But I unable to configure it in my home PC.
   I am using ubuntu 10.4 and apache2 web server.
   When I was searching about it , I go this URL [http://ubuntuforums.org/archive/index.php/t-422412.html](http://ubuntuforums.org/archive/index.php/t-422412.html).
   I simply followed that points , which is there in that site.
   But its not worked for me.

I have done this below things,

   =>  Installed  libapache2-mod-perl2
   => Created the directory called cgi-bin under /var/www directory
   => Created the symbolic link like this,
        ln -s  /usr/lib/cgi-bin /var/ww/cgi-bin
  => modified the file called /etc/apache2/site-available/default and added this below lines,
             
      <Directory "/var/www/cgi-bin">
                AllowOverride None
                Options ExecCGI
                AddHandler cgi-script cgi pl
        </Directory>

 => Restarted the server
 => created the testing script under /var/ww/cgi-bin/
      tried to open the page using firefox. Whe i was given this   [http://localhost/cgi-bin/](http://localhost/cgi-bin/) address, its simply says,
[B]
Forbidden[/B]

You don't have permission to access /cgi-bin/ on this server.
 
=> Then I have given the 777 permission for  /var/ww/cgi-bin/ and /usr/lib/cgi/ ( Recursive permission)
CGi is not working.

Can you plzz help me to make it work..

Thanks frds..

---

### Post by spjackson on 2010-09-13
Do you really want [http://localhost/cgi-bin/](http://localhost/cgi-bin/) to be browseable? That's unusual.

Don't you simply want to run scripts e.g. [http://localhost/cgi-bin/myscript.pl]("http://localhost/cgi-bin/") ? Is this working?

Also, there seems to be some confusion between /var/ww/ and /var/www/ in what you have posted. Are these just typos in your posting or did you make these mistakes when setting it up?

---

### Post by Lesliesathish on 2010-09-14
Hi friend,
 
 => [http://localhost/cgi-bin/myscript.pl]("http://localhost/cgi-bin/")  Its not working.
 => Its /var/www/. That is just typos in my post.
 => I want to run the script as a normal user. I don't want run the script as a root user.
      I already configure the PHP. For that I have created the public_html in my home directory and  just made a softlink from /var/www/. Now I can write the PHP script from my home itself.
     Likewise I want to do frd. Can U plzzz help me.

Thank U.

---

### Post by spjackson on 2010-09-14
> **Lesliesathish said:**
> 
 => [http://localhost/cgi-bin/myscript.pl]("http://localhost/cgi-bin/")  Its not working.

So what error do you get in your browser and in the Apache error log?

---

### Post by Lesliesathish on 2010-09-15
Hi frd.. I have configure it successfully... Thanks for ur rply..
Thanks a lot ..

---

