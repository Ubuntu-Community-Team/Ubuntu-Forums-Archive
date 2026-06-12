---
title: "Apache and public_html"
date: 2005-02-28
forum: Server Platforms
---

### Post by charlie763 on 2005-02-28
I am running Ubuntu on my 12" Al Powerbook with apache installed and running. When I go to [http://127.0.0.1](http://127.0.0.1) I get shown the directory contents of Apache's root directory. When I go to [http://127.0.0.1/~](http://127.0.0.1/~)[User Name]/ I want Apache to properly handle the contents of /home/[User Name]/public_html/. I have tried to figure the apache2.conf file, but nothing seemes to be working. I also restarted the server each time I saved a change to apache2.conf. Does anyone know how I can go about fixing this. Much thanks...

---

### Post by jdonnell on 2005-02-28
I replied to your post in the other category. It should help you. Let me know if you have any further questions.

---

### Post by charlie763 on 2005-03-01
Quoted:
[INDENT][I]You should see something like this in your apache2.conf
```
# UserDir is now a module
#UserDir public_html
#UserDir disabled root

#<Directory /home/*/public_html>
#       AllowOverride FileInfo AuthConfig Limit
#       Options Indexes SymLinksIfOwnerMatch IncludesNoExec
#</Directory>
```

Change it to this.
```
# UserDir is now a module
UserDir public_html
#UserDir disabled root

<Directory /home/*/public_html>
       AllowOverride FileInfo AuthConfig Limit
       Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>
```

Now restart apache and all should be working. You may need to change the permissions of your home folder.

$ chmod 755 /home/username[/I][/INDENT]

It looks like that should work. I'll try it when I get home tonight. I imagine that "UserDir disabled root" disables the public_html directory for the root user. What I had been doing was removing the comment tag on the "UserDir disabled root" line to make my code look as follows:
```
# UserDir is now a module
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
       AllowOverride FileInfo AuthConfig Limit
       Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>
```

The permissions on /home/charles/public_html was set so owner, group and others could read and execute, but only the owner could write. I don't think changing the permissions on /home/charles should not matter as long as /home/charles/public_html is readable. I changed the permissions of /home/charles/public_html before and it did not work.

I'll modify the apache2.conf file exactly the same way you said and report back tomorrow. Thanks for all you help. I love help forums.

---

### Post by charlie763 on 2005-03-02
I did exactly what you said and it did not work. I even saved the changes to apache2.conf and rebooted to see if that worked and it didn't.

I'm the only one who will be using my computer so using the default apache directory is no big deal. Thanks anyway for the help, but I think I'll just use the default directory until Hoary final comes out and I can do a fresh install.

Cheers!

---

### Post by jdonnell on 2005-03-02
Hm, well if you want to mess with it I'll help. Messing with things like this is how I learned how apache works :)

If you want, do this.
Request a page from your public_html directory.
[http://localhost/~user/something.html](http://localhost/~user/something.html)
What does it say?
Look in the log files and see what they show for this requiest.
tail /var/log/apache2/access.log
tail /var/log/apache2/error.log

---

### Post by hantsy on 2005-03-02
[QUOTE=jdonnell]Hm, well if you want to mess with it I'll help. Messing with things like this is how I learned how apache works :)

If you want, do this.
Request a page from your public_html directory.
[http://localhost/~user/something.html](http://localhost/~user/something.html)
What does it say?
Look in the log files and see what they show for this requiest.
tail /var/log/apache2/access.log
tail /var/log/apache2/error.log[/QUOTE]
 debian apache has its own configuer rule ...
#a2enmod user_dir
#chmod 755 /home/<username>
#mkdir -p /home/<username>/public_html
#chmod 755 /home/<username>/public_html

All is OK

---

### Post by Glarbl_Blarbl on 2006-02-11
Personally, I don't like to have my homedir world-readable...  I'd amend that to:

[FONT="Times New Roman"]#chmod 751 /home/<username>[/FONT]

cheers!

---

### Post by denisesballs on 2006-02-23
Has anyone found the user_dir apache module in dapper anywhere?

---

### Post by tbrownaw on 2006-02-23
[QUOTE=denisesballs]Has anyone found the user_dir apache module in dapper anywhere?[/QUOTE]
I think it's in apache2-common?

---

### Post by LordHunter317 on 2006-02-23
No, it's part of the mpm you have installed.  However, it's part of the standard installation.

---

### Post by hoodwink on 2006-02-23
[QUOTE=charlie763]I am running Ubuntu on my 12" Al Powerbook with apache installed and running. When I go to [http://127.0.0.1](http://127.0.0.1) I get shown the directory contents of Apache's root directory. When I go to [http://127.0.0.1/~](http://127.0.0.1/~)[User Name]/ I want Apache to properly handle the contents of /home/[User Name]/public_html/. I have tried to figure the apache2.conf file, but nothing seemes to be working. I also restarted the server each time I saved a change to apache2.conf. Does anyone know how I can go about fixing this. Much thanks...[/QUOTE]
In comparison to other distros, debian has a rather strange (IMO) setup for aqpache. You need to do the following; then restart apache.

1. in /etc/apache2/apache2.conf

UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

2. in /etc/apache2/mods-enabled, create the following symlinks

ln -s /etc/apache2/mods-available/userdir.conf userdir.conf
ln -s /etc/apache2/mods-available/userdir.load userdir.load

 This will fix your problem.

---

### Post by Kurt` on 2006-02-24
> **charlie763]I also restarted the server each time I saved a change to apache2.conf.[/QUOTE]
No need to do that my friend  said:**
> killall -SIGHUP httpd
or

> killall -SIGUSR1 httpd

The difference? SIGHUP will cause any file transfers in progress to be terminated (it causes all the "child" processes to restart), while SIGUSR1 will cause only *new* child processes to start using the new conf file. So don't use SIGHUP on a production server. ;)

---

### Post by denisesballs on 2006-02-24
[QUOTE=tbrownaw]I think it's in apache2-common?[/QUOTE]

Well I don't see it. Just uncommenting the "UserDir public_html" line gives me this when restarting apache:

```
root@dapper:/home/jesse# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... Syntax error on line 205 of /etc/apache2/apache2.conf:
Invalid command 'UserDir', perhaps mis-spelled or defined by a module not included in the server configuration
                                                                                                                                                            [fail]
```

---

### Post by gfwp on 2006-05-07
I have the same issue, and it looks like a 64 bit problem.

Facts: on a 32 bit ubuntu machine with apache2 everthings works and i can connect to my public_html without any manual configuration (just set up apache2 from synaptic). Same operation on an amd64 architecture fails.

greeetings

gfwp

---

### Post by manager on 2006-05-10
gfwp: i was having the same problem on a 32bit machine. With running "a2enmod userdir" on the CLI, it was fixed.

---

### Post by gfwp on 2006-05-10
well...

I have already tried this (a2en....) with no success! 

I checked everythings, links, userdir.conf, file rights, and all is Ok but it doesn't work on my brand new amd64 box and works perfectly on my old laptop i386....

any other ideas will be fine!

thanks

gfwp

---

### Post by oyvindaa on 2006-05-11
I can't view the letters æ, ø and å in webpages added to the /var/www/ directory. 

Are there any packages available that will let me fix that?

---

### Post by gfwp on 2006-05-12
very funny...

I have changed my userdir directory to /var/www (UserDir /var/www) copied the whole public_html into a new folder with my username,restarted apache2 and suddently everythigs worked fine. The permissions on the new /var/www/newfolder are the same as in /home/username/public_html !!!!

BUT (see my above messages)

/home is on a differen phisical partition as the / partition on my amd64 box

as opposite to my laptop where I have only 1 partition and apache worked greatly already after installing it through synaptic!

My BIG QUESTION: are some stupid access rules to partitions (llike umask in fstab) making such a mess with the userdir module???? Seems to be true!

Other people with same userdir-problems. Check that before complaining.

greetings

gfwp

---

### Post by ulissesroc on 2007-10-04
@hoodwink

Thanks, your solution worked for me. It's ages that I don't log in here, but I wanted to say thanks to you :D

---

