---
title: "PHP Problems"
date: 2006-11-26
forum: Server Platforms
---

### Post by offramp13 on 2006-11-26
I have apache2 installed and it works properly, but when i installed php5 it only worked for a day or two, then it stopped working. I get this error message when i try to open php files, but apache can still open html files just fine.
[CENTER][IMG]http://i13.photobucket.com/albums/a274/offramp13/Screenshot.png[/IMG][/CENTER]
I assume that the problem is in php5 not apache, because apache does everything else just fine.

---

### Post by tturrisi on 2006-11-26
The php files have to be in an apache dir like /var/www/ or /home/user/public_html/ else Firefox will not open them.  And the files must be executable, check the file permissions.

---

### Post by offramp13 on 2006-11-26
the files are saved in /var/www/ and you will notice that in the picture i am opening localhost and the default directory is set to /var/www/ so i assume thta is all god. What confuses me the most is that it says it cannot open a ".phtml" file and not a single one of those exist in that folder. I have checked the file permissions, they are set to 755, i believe that is correct

---

### Post by gnaunited on 2006-11-26
> **tturrisi said:**
> The php files have to be in an apache dir like /var/www/ or /home/user/public_html/ else Firefox will not open them.  And the files must be executable, check the file permissions.

Umm, no, this is not CGI.

When you installed PHP5 did you install the libraries for apache?

Do an "apt-cache search apache2 php5"

Look for something like libapache2-php5 and install it

---

### Post by stickboy2642 on 2006-11-26
This actually looks like an apache problem to me.  For some reason, apache doesn't know it has to send .php files on to the php engine, and tells that browser to just download the code.  Check your error logs and see if there is anything out of the ordinary.  It could be that something happened with your apache process.  Check in /etc/apache/modules-enabled to make sure that the files php5.conf and php5.load are there.  They should be symlinks to /etc/apache2/mods-available/php5.conf and /etc/apache2/mods-available/php5.load.  These files are responsible for telling apache how to handle php files.

```

root@laptop:/etc/apache2/mods-enabled# ls -l ls -l /etc/apache2/mods-enabled/php5*
lrwxrwxrwx 1 root root 37 2006-11-26 16:48 php5.conf -> /etc/apache2/mods-available/php5.conf
lrwxrwxrwx 1 root root 37 2006-11-26 16:48 php5.load -> /etc/apache2/mods-available/php5.load
```

If the files do not appear in that directory, type the following commands to make sure that they link to the proper files.

```

ln -sf /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load
ln -sf /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf
```

Then restart apache2

```

/etc/init.d/apache2 restart

```

Hope this helps!  :)

---

### Post by gnaunited on 2006-11-26
I like my idea better, mainly cause this happens to me all of the time. Try mine cause it is simpler, then try his.

---

### Post by gnaunited on 2006-11-26
Under Ubuntu Dapper:

```
sudo apt-get install libapache2-mod-php5
```

That is assuming you are using apache2 and php5

---

### Post by offramp13 on 2006-11-26
I have done that, and now when i open [http://localhost](http://localhost) i get the same message from my screenshot earlier. But when i go to [http://localhost/index.php](http://localhost/index.php) then it works perfectly fine. This is not major problem but i know that something isnt working correctly.

---

### Post by stickboy2642 on 2006-11-27
Check /etc/apache2/apache2.conf and look for the DirectoryIndex directive.  Make sure that index.php is added to that line.  This will tell apache to search for an index.php file if you don't give it a specific filename (like [http://localhost)](http://localhost)).  I am not sure this will help, but it is worth checking out.

```

DirectoryIndex **index.php** index.htm index.html

```

---

### Post by offramp13 on 2006-11-28
it works now! thanks, all of you

---

