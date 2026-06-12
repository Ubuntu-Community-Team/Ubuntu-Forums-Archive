---
title: "I'm not sure if LAMP on my Ubuntu 14.04.1 works correctly"
date: 2014-08-29
forum: Server Platforms
---

### Post by stefanmarkic on 2014-08-29
I installed LAMP on Ubuntu 14.04.1 following [this guide]("http://tuxtweaks.com/2012/04/installing-lamp-on-ubuntu-12-04-precise-pangolin/"). However, when I go to [http://localhost/testing.php/](http://localhost/testing.php/) from the browser, all I get is this:

```
[B]Not Found
[/B]
[COLOR=#000000][FONT=Times New Roman]The requested URL /testing.php/ was not found on this server.[/FONT][/COLOR]
[HR][/HR][COLOR=#000000][FONT=Times New Roman]Apache/2.4.7 (Ubuntu) Server at localhost Port 80[/FONT][/COLOR]
```

What to do? :confused:

---

### Post by yancek on 2014-08-29
If you do [http://localhost/index.html](http://localhost/index.html), do you see the apache It Works page?
You do have the testing.php file in the proper directory under /var/www/html?  That is the new default location for the files in 14.04.

---

### Post by stefanmarkic on 2014-08-30
> **yancek said:**
> 
You do have the testing.php file in the proper directory under /var/www/html?  That is the new default location for the files in 14.04.

This solved the problem. Thanks!

---

### Post by stefanmarkic on 2014-09-01
I have another problem now. I want to change default projects directory from /var/www/html to /home/user/Projects/www.

In /home/user/Pojects/www I created new index.html file ('It works!' page template) and new testing.php script as user. After that i restarted Apache server. Now, when I enter 'localhost' or 'localhost/testing.php' in browser, I get this message:


```
[B]Forbidden
[/B]
[COLOR=#000000][FONT=Times New Roman]You don't have permission to access /testing.php on this server.[/FONT][/COLOR]
[HR][/HR][COLOR=#000000][FONT=Times New Roman]Apache/2.4.7 (Ubuntu) Server at localhost Port 80[/FONT][/COLOR]
```

---

### Post by Lars Noodén on 2014-09-01
Did you set the [DocumentRoot](https://httpd.apache.org/docs/2.4/mod/core.html#documentroot)?  Does that directory have a corresponding [Directory](https://httpd.apache.org/docs/2.4/mod/core.html#directory) entry in the configuration file where it says "Allow from all" or something else appropriate?

Do /home/user/Pojects/www, /home/user/Pojects/, /home/user/, and /home/ all have permissions that allow o=rx so that the web server can read their contents?  Do the files in /home/user/Pojects/www/ have o=r permissions?

Is "Pojects" spelled properly in all instances?  If it is "Pojects" some places and "Projects" elsewhere, there will be problems.

---

### Post by slickymaster on 2014-09-01
Moved to the **Server Platforms** sub-forum.

---

### Post by stefanmarkic on 2014-09-01
Ok, first, I went to /etc/apache2/apache2.conf and added this:

```
<Directory  /home/user/Projects/www/>
    Options FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
```

Then I restarted Apache server and typed 'localhost' and 'localhost/testing.php' in browser and everything worked.

Now, if I were to create another folder in /home/user/Projects/www/ and put a PHP script in it, it would work. However, if I typed in browser 'localhost/newfolder/' I would again get a 'Forbidden' message. So, despite every PHP script being read now, I couldn't access any directory tree within the browser.

I fixed this problem by bringing back the default 'DocumentRoot /var/www/html' path in /etc/apache2/sites-available/000-default.conf and by creating a symbolic link from /var/www/html to /home/user/Projects/www/. So now I can access all project directories from the browser and every PHP script can be read. The only question I have for now is how legit my "fix" really is?

---

### Post by SeijiSensei on 2014-09-02
You get a Forbidden because you don't have the [Indexes]("http://httpd.apache.org/docs/current/mod/core.html#options") option enabled.  Change the Options line above to read
```
Options Indexes FollowSymLinks
```
and you won't get that error any more.  

If you are just learning about Apache, I recommend using "Options All" as a start until you get everything running.

---

