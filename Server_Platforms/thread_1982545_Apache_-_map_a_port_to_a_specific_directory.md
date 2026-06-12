---
title: "Apache - map a port to a specific directory"
date: 2012-05-18
forum: Server Platforms
---

### Post by trundlenut on 2012-05-18
I have a server set up (running 12.04 server) which runs SugarCRM CE, essentially for internal use at work.  However I want to enable data from an external website (outside the lan) to be added to the SugarCRM database.

What I was thinking of doing is opening a port on our internet router to allow access from the external webserver to the internal server.  But I obviously don't particularly want the server visible to all and sundry, consequently I want to know if it possible to redirect traffic on the open port to one specific folder within the SugarCRM installation.

i.e. [www.example.com:100](www.example.com:100) goes to /var/www/sugar/folderX

Opening the port is easy enough but despite a good search on the internet I haven't managed to find a clear method to implement this in apache.  What information I have found is contradictory with suggestions involving virtual hosts and reverse proxys and both stating the other option won't work.

Can anyone help to point me in the right direction please.

---

### Post by CharlesA on 2012-05-18
My first thought was using virtual hosts, but I don't know if that will accomplish what you want.

How is the data you want added from an external source going to get imported into SugarCRM?

---

### Post by trundlenut on 2012-05-18
Virtual hosts is one option I came across, but then another site said this wouldn't work.

I believe data is added to Sugar via php/soap (need to read up on this), I'm waiting to find out from the software supplier exactly how it works and I need to root around in the sugar installation to find out what is in certain folders.

---

### Post by SeijiSensei on 2012-05-19
Virtual hosts would definitely work.  You'll need to have Apache listen on another port beside 80, then bind a virtual host to the address and port like this:

```

Listen 8080
<VirtualHost *:8080>
     ServerName backdoor.example.com
     DocumentRoot /var/www/sugar/folderX

     <Directory /var/www/sugar/folderX>
          Options Indexes FollowSymLinks MultiViews
          AllowOverride None
          Order allow,deny
          allow from all
     </Directory>
</VirtualHost>

```

You'll probably want some other controls over the vhost like [password protection]("http://httpd.apache.org/docs/2.2/howto/auth.html").  Put these directives in a file in /etc/apache2/sites-available and create a symlink to the file in /etc/apache2/sites-enabled (or use a2ensite).  Then restart apache with "sudo service apache2 restart".

Have your router forward an external port (choose one over 1023) back to the server's port 8080 or whatever port you choose for the virtual host.

---

### Post by hawkmage on 2012-05-19
If the files you are trying to share in that directory are already created and the external client is just retrieving them via HTTP(S) then a virtual host could work.

If the files that the client will be accessing require active content like PHP to retrieve them then the setup may be a bit more complicated and my not work within the application you are using.

---

### Post by Lars Noodén on 2012-05-19
SeijiSensei's example should do it for you.  If you're looking for other examples, the term to look for is "port-based virtual host"

---

### Post by trundlenut on 2012-05-19
Thanks everybody, I'll have a go and see what happens.

---

