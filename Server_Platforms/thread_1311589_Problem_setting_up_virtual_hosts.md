---
title: "Problem setting up virtual hosts"
date: 2009-11-02
forum: Server Platforms
---

### Post by habuchas on 2009-11-02
Just when I thought I was emerging from Nubee status I get pulled back.
I have enstalled Ubuntu 9.10 from an ISO CD......no problem.
then I performed:
sudo tasksel and did a LAMP install and set up the database....no problem
From Firefox  [http://localhost/](http://localhost/) came up .......no problem.
I set up a user account put in a public_html directory
sudo adduser username
cd /home/username
sudo mkdir public_html
set up a index.html in the public_html directory.
cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/userdir.conf userdir.conf
sudo ln -s ../mods-available/userdir.load userdir.load
sudo /etc/init.d/apache2 restart
At this point I thought I would be able to access the username
[http://localhost/~username](http://localhost/~username) but got 'Not Found'
Any suggestions would be appreciated....

---

### Post by Lars Noodén on 2009-11-03
Try 

sudo a2enmod userdir
sudo /usr/sbin/apache2ctl graceful

Also make sure that you have allowed access:

<Directory /home/*/public_html>
Order Deny,Allow
Allow from all
</Directory>

---

### Post by habuchas on 2009-11-03
LARS:
Thank you for responding, here is the error message I got from:
sudo a2enmod userdir

ERROR: Module userdir not properly enabled: /etc/apache2/mods-enabled/userdir.load exists but does not point to /etc/apache2/mods-available/userdir.load, not touching it

Here is what is in userdir.load:
<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>
Any suggestions?
habuchas......

---

### Post by habuchas on 2009-11-04
:redface:
Stupid operator error.  Proving once again that the Nubee tag is appropriate for me.
Thanks to Lars for responding, which put me on the path of going over my command line entries, where I found me mistake.........
habuchas........

---

