---
title: "HOWTO: localhost subdomains"
date: 2007-10-26
forum: Tutorials
---

### Post by Stex on 2007-10-26
It's a very simple and very useful hack. This was done on Apache2 under Gutsy.

**1. Add your subdomain(s) to your hosts file:**
[LIST]
[*]Open up your network settings (System > Administration > Network)
[*]Click on the Hosts tab, select the localhost alias and click properties
[*]Add the subdomain(s) you want alongside localhost, separate with new lines
[/LIST]
e.g:
[COLOR="Sienna"]localhost
extra.localhost
another.localhost[/COLOR]

**2. Apply subdomains to folders:**
Open up a terminal or the Run Application diaogue (Alt+f2), then run the command: [COLOR="DarkGreen"]gksudo gedit /etc/apache2/httpd.conf[/COLOR]

For each subdomain you need to add a VirtualHost clause, **you also need to add one for the base localhost**. The clause for each uses the template:
[COLOR="Sienna"]<VirtualHost *>
ServerName **{Domain (e.g. localhost)}**
DocumentRoot **{Absolute path to folder for this domain (e.g. /var/www/)}**
</VirtualHost>[/COLOR]

Your file should end up looking something like this:
```
<VirtualHost *>
ServerName localhost
DocumentRoot /var/www/
</VirtualHost>

<VirtualHost *>
ServerName extra.localhost
DocumentRoot /var/www/extra/
</VirtualHost>

<VirtualHost *>
ServerName another.localhost
DocumentRoot /var/www/anothersite/
</VirtualHost>
```
Save and exit.

**3. Restart apache:**
Open up the terminal and run: [COLOR="DarkGreen"]sudo /etc/init.d/apache2 restart[/COLOR]
You should now be able to view your subdomains through whatever browser you use (but obviously only from your computer). All done!

**Making use of it:**
I write and test websites on my localhost before uploading them to my public sites and I don't want to go through my code renaming localhost to example.com every time I change something. Nor do I want to use relative URLs as they can get messy once you get folders involved. By putting each site I make on it's own local subdomain I can start all my URLs with a slash which means the URL starts at the base of the subdomain.

That's why I use it anyway.


**-- Notes:**
- I couldn't find a way to apply wildcards to the hosts file (e.g. *.localhost), does anyone know?
- There are ways to direct all subdomains to folders automatically (mod_rewrite is good for that) but that's less needed for this purpose and would require wildcards in the hosts file

---

### Post by meowsus on 2007-10-30
This will come in handy at work. Very useful tip, Stex. 

I'm pretty sure I've read that hosts files are unable to accept wild card entries. I know that wasn't the answer you were looking for, but at least now it won't keep you up at night.

Maybe theres another way. Hm. If anything pops into my brain I'll give you a holler.

---

### Post by Sarteck on 2007-11-25
For Kubuntu newbies like myself, there are slight alterations to steps 1 and 2.

[list=1][*]Add your subdomain(s) to your hosts file:[list][*]Open up your network settings (K Menu > System Settings > Network Settings)[*]Click the "Administrator Mode" button[*]Click on the Domain Name System tab, select the localhost alias in the bottom "static hosts" pane, and click "Edit"[*]For each subdomain you want (other than "localhost"), click "add" and enter the name.[*]"OK" everything and apply the changes.[/list][*]The command for us Kubuntu users is```
kdesu kate /etc/apache2/httpd.conf
```[/list]

Everything else remains the same, really.  :)  Happy website designing.



To the OP, thanks for this--I was unsure about the right format for step 2, and forgot the command to restart the apache server in step three.  XD  If you want to include the above in your HOWTO for us Kubuntu users, go right ahead.  :)

---

### Post by firmit on 2008-03-19
Of course - I found this post AFTER I made my own workaround. The subdomain trick is nice. However, I made my "multiple-virtual-local-servers"-thingy.

First, I added a couple of new hosts in /etc/hosts
```
127.0.0.1 localhost
127.0.0.2 alpha
127.0.0.3 beta
127.0.0.4 gamma
```

In /var/www, I added the folders *alpha, beta, gamma* containing index.php
```

<?php echo getcwd(); ?>

```

Then I added a new site in /etc/apache2/sites-availabe/
```
sudo touch greek
sudo nano greek

```

```

# alpha
<VirtualHost 127.0.0.2>
	DocumentRoot /var/www/alpha/
</VirtualHost>
# beta
<VirtualHost 127.0.0.3>
	DocumentRoot /var/www/beta/
</VirtualHost>
# gamma
<VirtualHost 127.0.0.4>
	DocumentRoot /var/www/gamma/
</VirtualHost>

```

And finished of with:
```

sudo a2ensite greek
sudo /etc/init.d/apache2 reload

```

```
firefox alpha
``` now showed /var/www/alpha :)

---

### Post by josemota on 2008-06-13
firmit's solution has green light in 8.04

Fantastic! Thanks firmit!

---

### Post by wootah on 2008-06-13
Great tutorial! This one's going in as a keeper :)

---

### Post by limcopy on 2008-07-09
> **Stex said:**
> It's a very simple and very useful hack. This was done on Apache2 under Gutsy.

**1. Add your subdomain(s) to your hosts file:**
[LIST]
[*]Open up your network settings (System > Administration > Network)
[*]Click on the Hosts tab, select the localhost alias and click properties
[*]Add the subdomain(s) you want alongside localhost, separate with new lines
[/LIST]
e.g:
[COLOR="Sienna"]localhost
extra.localhost
another.localhost[/COLOR]

**2. Apply subdomains to folders:**
Open up a terminal or the Run Application diaogue (Alt+f2), then run the command: [COLOR="DarkGreen"]gksudo gedit /etc/apache2/httpd.conf[/COLOR]

For each subdomain you need to add a VirtualHost clause, **you also need to add one for the base localhost**. The clause for each uses the template:
[COLOR="Sienna"]<VirtualHost *>
ServerName **{Domain (e.g. localhost)}**
DocumentRoot **{Absolute path to folder for this domain (e.g. /var/www/)}**
</VirtualHost>[/COLOR]

Your file should end up looking something like this:
```
<VirtualHost *>
ServerName localhost
DocumentRoot /var/www/
</VirtualHost>

<VirtualHost *>
ServerName extra.localhost
DocumentRoot /var/www/extra/
</VirtualHost>

<VirtualHost *>
ServerName another.localhost
DocumentRoot /var/www/anothersite/
</VirtualHost>
```
Save and exit.

**3. Restart apache:**
Open up the terminal and run: [COLOR="DarkGreen"]sudo /etc/init.d/apache2 restart[/COLOR]
You should now be able to view your subdomains through whatever browser you use (but obviously only from your computer). All done!

**Making use of it:**
I write and test websites on my localhost before uploading them to my public sites and I don't want to go through my code renaming localhost to example.com every time I change something. Nor do I want to use relative URLs as they can get messy once you get folders involved. By putting each site I make on it's own local subdomain I can start all my URLs with a slash which means the URL starts at the base of the subdomain.

That's why I use it anyway.


**-- Notes:**
- I couldn't find a way to apply wildcards to the hosts file (e.g. *.localhost), does anyone know?
- There are ways to direct all subdomains to folders automatically (mod_rewrite is good for that) but that's less needed for this purpose and would require wildcards in the hosts file

Dear Sir,

Thank you for the tutorial. I'm sorry that I new to this features

I had tried to set it and restart my apache server it prompt a message box request username and password ? May I know what is my username and password to login into the sub domain ?

---

### Post by Wallynm on 2011-10-18
> **-- Notes:**
- I couldn't find a way to apply wildcards to the hosts file (e.g. *.localhost), does anyone know?
Hello Guys, i found an post on the net teaching how to get wildcards working, and everything worked perfectly!
 This is the link [http://groups.drupal.org/node/16862](http://groups.drupal.org/node/16862)

Maybe, if you have NetworkManager installed on your Ubuntu, you will need to run this command to keep the changes when you restart:
# chattr +i /etc/resolv.conffor security reasons, NetwrokManager reset the resolv.conf file always when he is started...
Refference:
[https://wiki.archlinux.org/index.php/NetworkManager#Preserving_changes_to_resolv.conf](https://wiki.archlinux.org/index.php/NetworkManager#Preserving_changes_to_resolv.conf)

i´m runing the example on Ubuntu 11.10
I recommend it to anyone who wants to enable Wildcards!

---

