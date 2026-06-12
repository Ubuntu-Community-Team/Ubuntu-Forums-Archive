---
title: "permissions on /var/www"
date: 2008-08-17
forum: Server Platforms
---

### Post by Jean__ on 2008-08-17
I recently moved my file/webserver from xp to hardy.

What do I need to set to have /var/www writeable by me (jean) and by apache.
I'm getting permission denied errors on things like php fopen().

I tried in /var/www:
```

sudo chown -R jean:jean ./
sudo chmod -R 755 ./

```

But I'm still getting the errors.
Thanks.

---

### Post by pytheas22 on 2008-08-17
I think that this would solve the problem:
```

sudo chmod -R 777 /var/www
```

But there may be a better, more secure solution.  Minimally, you may want to give 777 permissions to only the files on your server that need to be writeable--it's probably a bad idea to make the entire web server writeable by anyone.

I think that the reason that changing jean to own /var/www doesn't work is that when you try to run a PHP script through your web browser, the server doesn't know that jean is accessing it; it just treats the person in front of the browser as it would any anonymous person on the Internet who's connecting to your site.  So for PHP scripts that need to open and write to files to work, the files in question must be readable and writeable by the anyone, not just jean.

But I don't have too much experience with Apache, so hopefully someone who does will point out a better solution if there is one.

---

### Post by fahadsadah on 2008-08-17
Setting permissions/ownership on . or .. has no effect.
```
sudo chown -R jean:jean /var/www
sudo chmod -R 755 /var/www
```

---

### Post by Jean__ on 2008-08-17
Thanks pytheas.

Doing chmod 777 could be an option.
But I'm afraid this will result in a situation that I have to chmod everytime I make some small change to a file or create a new one.

What I have in mind, I'm relative new to linux, is some group to wich apache, jean, and for instance a friend of mine who has ftp access on the server and hosts some sites himself there, all have rw access to /var/www

I will wait till hopefully some other person knows more about this. Meanwhile I'm searching the web (and doing a lot of work in porting things over to linux here).

---

### Post by Jean__ on 2008-08-17
@fahadsadah
I knew that already, your 'answer' does not contribute much.

---

### Post by mbeach on 2008-08-17
when apache runs a php script, it is typically run as www-data, not as an anonymous internet user.

I think one solution for you is to include yourself (jean) and friend in the www-data group.  Then make sure the files you want editable are owned by www-data and group www-data (using chown) then make them writable by the group (chmod g+w).  Making changes to existing files will not change the ownership or permissions - they will be retained.  New files will have to have their ownership and permissions set accordingly.

you might want to start with something like

```
sudo chown -R www-data:www-data /var/www/*
```

which should solve your original dilemma of the permission denied on the fopen error depending on which file its trying to open.  If you are attempting to open a file outside of /var/www, you'll probably want to change permission or ownership on the file accordingly.

an alternative solution is to place your website in a folder in your home folder, then alter /etc/apache2/sites-available/default to point to the newly created folder /home/jean/mywww.  This is not ideal if 'friend' is to be editing it.  It's good for you, but not friend.  If friend is to have their own site on your machine, then create another apache conf file (virtual hosting now) pointing to a www folder in their home folder.  It really depends on the future use of this setup.  

another solution I've seen folks do which can work nicely is to use samba to share the /var/www folder forcing the user to be www-data when shared.  Something like the following in your smb conf file:

```
[www]
path = /var/www
available = yes
browseable = yes
public = yes
writable = yes
valid users = jean
create mask = 0755
directory mask = 0755
force user = www-data
force group = www-data

```

---

### Post by cariboo on 2008-08-17
Another way to do this is to create a symbolic link to a directory in your home directory that you have read and write permission to for example:

```
ln -s /home/user/html html
```

Then set ownership of html to www-data with permission of 755. You will have to change the document root in /etc/apache2/apache2.conf to reflect the new directory.

Jim

---

### Post by Jean__ on 2008-08-18
cariboo907 and mbeach, thank you for your answers.
I already am halfway, no more errors from fopen(), have to test some with my friend still.
I consider it solved. :)

---

