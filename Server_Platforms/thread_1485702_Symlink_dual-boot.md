---
title: "Symlink dual-boot"
date: 2010-05-17
forum: Server Platforms
---

### Post by kashivis on 2010-05-17
Hi,

I am new to Ubuntu and am fascinated by it. 

I have been using IIS and have build an Intranet website using Dreamweaver CS3 with:

[LIST]
[*]a testbed (localhost) on my XP laptop
[*]synched to a production Win 2K virtual-server running ASP.net
[/LIST]
I made my XP laptop dual-boot with lucid lynx and installed LAMP, Kompozer and toolsets (thanks to trackerjon for this [fantastic post]("http://ubuntuforums.org/showthread.php?t=1469825")!) in it. The localhost test in firefox after apache2 installation says [B]It Works!

[/B]My objective is to use:

[LIST]
[*]Kompozer, with apache2 pointing to the XP (N[COLOR=Red]T[/COLOR]FS) Inetpub>wwwroot folder (symlink /var/www to the N[COLOR=Red]T[/COLOR]FS?)
[*]Get Firefox to recognize my default.aspx...such that it appears when I type localhost in the FF URL.
[/LIST]
How can I get apache2 to recognize IIS inetpub>wwwroot?

Thanks

---

### Post by volkswagner on 2010-05-17
I'm not sure what you mean by NFS.  Did you meant to write NTFS for that type of formated hard drive, or is the webroot actually on an NFS file share?

If you want Apache2 to open you webroot on an NTFS MS Windows partition, you will need to make sure NTFS file support is installed.

```
sudo apt-get install ntfs-3g
```

You will need to mount that partition somewhere on your system.

Before I go any further I just want to make sure I'm on the right track.

---

### Post by kashivis on 2010-05-18
Hi Volkswagner,

Thanks for your response. I meant NTFS (and not NFS). Sorry for the confusion.

I checked in Synaptic Package Manager that ntfs-3g is already installed. The MS Windows partition gets mounted, when I click on it in "Places" in the main menu.

a) How can I permanently mount it upon boot-up?

b) I understand from Apache's [Name-Based Virtual Host documentation]("http://httpd.apache.org/docs/2.1/vhosts/name-based.html") that a ServerName and and DocumentRoot are needed in httpd.conf. In the configuration desired, there is [COLOR=Red]no[/COLOR] ServerName and the DocumentRoot is [COLOR=Red]/media/OS/Inetpub/wwwroot.[/COLOR] What do I do to make apache2 recognize my mounted default.aspx file as the home page?

Thanks and Regards,
Kashi

---

### Post by Grenage on 2010-05-18
> **kashivis said:**
> I checked in Synaptic Package Manager that ntfs-3g is already installed. The MS Windows partition gets mounted, when I click on it in "Places" in the main menu.

a) How can I permanently mount it upon boot-up?

Create a mount point in /media, then add a line to /etc/fstab to automatically mount the partition.  You will need to replace /sda1 with whatever your partition is (it may be sda1):

```
sudo mkdir /media/windows
gksu gedit /etc/fstab
```

Add line:

```
/dev/***sda1*** /media/windows ntfs-3g users,exec,auto 0 0
```

Save it, then run the following line from a terminal, and check for errors:

```
sudo mount -a
```

---

### Post by kashivis on 2010-05-18
Thanks Grenage. It was sda2 and it worked without errors.

---

### Post by Grenage on 2010-05-18
Glad to hear it!

---

### Post by kashivis on 2010-05-18
Can anyone help with question b) ... how can I configure apache2 to recognize my [COLOR=Red]default.aspx[/COLOR] in [COLOR=Red]/media/OS/Inetpub/wwwroot [COLOR=Black]as the home page?[/COLOR]
[/COLOR]

---

### Post by Grenage on 2010-05-19
I have always changed the information in */etc/apache2/sites-available/default*.  I don't dabble with apache very much, so take that with a pinch of salt.

---

### Post by kashivis on 2010-05-19
I did the following, based on the [manual instructions]("https://help.ubuntu.com/9.10/serverguide/C/httpd.html"):

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/[COLOR=Red]urefmodel[/COLOR] 
```Modified /etc/apache2/sites-available as follows:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot[COLOR=Red] /media/windows/Inetpub/wwwroot[/COLOR]
    <Directory />
        Options FollowSymLinks
        AllowOverride [COLOR=Red]all[/COLOR]
    </Directory>
    <Directory[COLOR=Red] /media/windows/Inetpub/wwwroot/[/COLOR]>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride [COLOR=Red]all[/COLOR]
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
``````
sudo gedit /etc/hosts
```Added urefmodel to /etc/hosts, as follows:

127.0.0.1    localhost urefmodel

```
sudo a2ensite urefmodel
```Reloaded apache2 using:

```
/etc/init.d/apache2 reload
```...and I get the error:
```

httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```Where am I going wrong?

---

### Post by Grenage on 2010-05-19
Would you not need to reload apache with sudo/root?

---

### Post by kashivis on 2010-05-19
I did:

```
sudo /etc/init.d/apache2 reload
```...and the error went off... Thanks for pointing it out.
 
I also:
1. copied the /usr/www/index.html file to /media/windows/Inetpub/wwwroot
2. modified the heading to **It works in wwwroot** and 
3. renamed the /usr/www/index.html to index1.html, 

Finally, ran the firefox URL:
[HTML]http://localhost/[/HTML]Firefox somehow, still gets the contents showing **It works!** and not the new one :confused:
Where does it get it from?

Regards,
Kashi

---

### Post by Grenage on 2010-05-19
Unfortunately I don't really have the experience to help you here, but all of my machines running apache used /etc/apache2/sites-available/default.  Does that exist on your machine?

---

### Post by kashivis on 2010-05-19
Thanks for your constant help during a tough time!

Yes... I have used /etc/apache2/sites-available/default

I think I found out what the issue is.

On running ```
sudo /etc/init.d/apache2 restart 
```, I used to get:

[html] ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName [/html]I thought this was an error. To prevent this, I went and modified ```
sudo gedit /etc/apache2/httpd.conf
``` and added ```
ServerName localhost
```, as recommended by [this gentleman]("http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/").

This was the naughty little code that seems to have prevented me from accessing  index.html in my mounted windows Inetpub/wwwroot.

I think I am reaching the last lap of this journey....

The localhost defaults to index.html as the home page. If I use default.aspx, it just lists out the contents as an XML page, instead of rendering it. I need to find out how to change this. Perhaps, I need to play with MIME types somewhere...

Any help is appreciated.

Rgds, Kashi

---

