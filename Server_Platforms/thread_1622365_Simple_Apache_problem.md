---
title: "Simple Apache problem"
date: 2010-11-15
forum: Server Platforms
---

### Post by gantww on 2010-11-15
Greetings,
I'm trying to get my head around configuring Apache. Towards this end, I've set up an account on Slicehost, using an Ubuntu slice. I can SSH into the box. I eventually plan to use this box for a production webserver, but I'm just learning on it now.

I installed apache and navigated to the webserver in my browser. I got the "It Works" message with no problem.

I went in through SSH and created a directory as follows:
/root/websites/GSS

I stuck an HTML file out there.

Next, I created a virtual host file (/etc/apache2/sites-available/GSS), as follows (except for the IP address - I used the correct IP of the server):

<VirtualHost *:80>

  ServerAdmin [email]will@mydomain.com[/email]
  ServerName 127.0.0.1

  DirectoryIndex default.html
  DocumentRoot /root/websites/GSS
</VirtualHost>

I also did the following to give access to the files in question to the apache process (my current working directory is /root/websites/GSS):
chmod -R a+rX ~/websites

Now, when I try to navigate to the default.html page, I get a 403 error. I tried to get there through the following URL (IP redacted as above):
[http://127.0.0.1/default.html](http://127.0.0.1/default.html)

I'm missing something. Any ideas what it could be?

---

### Post by hobbestec on 2010-11-15
I think it's not working because you put the websites under the root user's directory.  Normally websites are put into either a regular user /home directory or in apache's default DirectoryRoot which is usually set to /var/www

---

### Post by volkswagner on 2010-11-15
Did you enable the site then restart Apache2?```
sudo a2ensite GSS
sudo /etc/init.d/apache2 reload
```

---

### Post by gantww on 2010-11-15
I restarted Apache. I also tried restarting the box.

Do I need to change the owner of the directory or something?

---

### Post by gantww on 2010-11-15
> **gantww said:**
> I restarted Apache. I also tried restarting the box.

Do I need to change the owner of the directory or something?

sudo chmod a+rx ~

Fixed it. Apparently it was the permissions on the root's home directory. So if I have to do that, I definitely should make a different user for the purposes of doing stuff like this.

Am I correct in understanding that restrictions on a parent directory are processed before restrictions on a child?

---

### Post by SeijiSensei on 2010-11-15
/root usually has 0700 permissions so no one other than root can even list the contents of the directory much less read or write files there.

Apache runs as the www-data user; any files owned by that user are readable by the web server.  It can also serve up files that are  readable by the www-data group, or ones that have 0644 permissions so they are world-readable.

Either place the files under the main /var/www directory where the default Apache files are stored, or use an Alias directive in Apache to point the DirectoryRoot to another location in the filesystem.  For instance, I'll sometimes create a "web" user and put the files in something like /home/web/public with ownership web:www-data.  I just need to make sure that the top-level directory, /home/web/, has 0710 permissions, and /home/web/public has 0750 permissions.  I then make the web user's primary group www-data in /etc/passwd and make sure it has umask 007 so any files created by that user are group readable/writable.

---

