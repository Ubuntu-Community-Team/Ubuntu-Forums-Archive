---
title: "Apache2, A failure to map URL to the directory outside of /var/www"
date: 2005-05-12
forum: Server Platforms
---

### Post by wntsea on 2005-05-12
I followed <Unofficial UBUNTU 5.04 starter guide: Q: How to map URLs to folders outside /var/www>, but failed.
There is no error message, but the directory I tried to map was not appear in the web.
Do I have to chage some configuration file such as /etc/apache2/apache2.conf?

Thanks

---

### Post by defkewl on 2005-05-12
add a configuration in /etc/apache2/sites-available

You can copy the default

---

### Post by LordHunter317 on 2005-05-12
I don't know what teh guide told you to do, but to map a directory outside the webroot into the virtual web tree, you have to do two things:
[list=1]
[*]Specify an Alias directory giving the name of the directory and where you want it mapped   
[*]Provide a <Directory> directive with access information for the directory. 
[/list] Like so:```
Alias /mystuff /home/mystuff
<Directory "/home/mystuff">
	AllowOverride None
	Limit allow,deny
	Allow from all
</Directory>
```You should put this in the virtual host of whatever site you want this to show up in.  Under the standard configuration, this would be the site in /etc/apache2/sites-enabled/000-default.

---

### Post by wntsea on 2005-05-13
Thanks for your reply.
I tried to do in three different ways you suggested.
1. To follow the <Unofficial guide: How to map URLs to folders outside /var/www/?>
    - sudo gedit /etc/apache2/conf.d/alias
    - Insert the following lines into the new file
          Alias /memories /home/pub/Memories/
          <Directory /home/pub/Memories/>  # here, I used quatation mark for the directory also.
          Order allow,deny
          Allow from all
         </Directory>
    - sudo /etc/init.d/apache2 restart
    - [http://localhost/](http://localhost/)           # -> I could not find that directory (/memories)

2. To include the Alias in the file /etc/apache2/sites-available/default
I modified the default file to include the same contents in /etc/apache2/conf.d/alias. I restarted Apache2, but the same symptom.

3. To include the Alias in the file /etc/apache2/sites-enabled/000-default
I also included the same contents in this file, but the same case.

When I tried the above cases, I did not exclusively but sequentially. I mean, when I tried number 2, there was alias file in number 1.
Did I something wrong or Do I have to something more?

Thanks.

---

### Post by LordHunter317 on 2005-05-13
[QUOTE=wntsea]Thanks for your reply.
I tried to do in three different ways you suggested.
1. To follow the <Unofficial guide: How to map URLs to folders outside /var/www/?>
    - sudo gedit /etc/apache2/conf.d/alias
    - Insert the following lines into the new file
          Alias /memories /home/pub/Memories/
          <Directory /home/pub/Memories/>  # here, I used quatation mark for the directory also.
          Order allow,deny
          Allow from all
</Directory>[/quote]This would work just fine, however it means that alias would appear in every virtualhost your server runs.  IF you're the only person running on the server, it doesn't matter.

If you're like me and host several sites off the same box, it's a big deal.  FWIW, the Ubuntu/Debian apache2 configuration caters to people like me, not you, because the right way to meet our needs meets your needs as well.


> - sudo /etc/init.d/apache2 restart
    - [http://localhost/]("http://localhost/") # -> I could not find that directory (/memories)You went to [http://localhost/memories/](http://localhost/memories/), right?  If you go to just [http://localhost/](http://localhost/), it's not going to show that directory automatically.

> 2. To include the Alias in the file /etc/apache2/sites-available/default
I modified the default file to include the same contents in /etc/apache2/conf.d/alias. I restarted Apache2, but the same symptom.

3. To include the Alias in the file /etc/apache2/sites-enabled/000-default
I also included the same contents in this file, but the same case.If you killed what was already in this file (They are the same file) you may have screwed up your configuration pretty badly.  In which case, you should post it so I can see what you did.

> Did I something wrong or Do I have to something more?Not sure.  Posting the access_log and error_log would help as well, if they have any relevant entries.

---

### Post by kraymore on 2007-12-04
my document root looks like this inside /etc/apache2/sites-enabled/mydomain DocumentRoot /var/www/apache2-default/ however it still goes to /var/www instead and displays the folders inside /var/www when i would prefer it to go to /var/www/apache2-default/domaindir and just get a / when i navigate to mydomain.com on the web.  can anyone help ?

---

