---
title: "help configuring virtual hosts in apache2"
date: 2005-10-15
forum: Server Platforms
---

### Post by kthdsn on 2005-10-15
Hi, I host 5 sites from my computer using ubuntu and apache2.  I decided to do a clean install of breezy and tried to set up apache with virtual hosting by myself (a friend did it for me last time) but I have run into some problems.

I installed apache2 with php5 through synaptic and created a sites-available file for each of my domain names.  I then enabled them with a2ensite, and apache wouldn't start.  I disabled 2 of the sites and apache is now running again, but when i try to access the sites I get permission denied.

My sites are set up with thier own folder in /var/www/, eg /var/www/cowbags.co.uk/ with logs at /var/www/cowbags.co.uk/logs/.  The sites-available file for this site is 

<VirtualHost *>
ServerName [www.cowbags.co.uk](www.cowbags.co.uk)
ServerAlias cowbags.co.uk
DocumentRoot /var/www/cowbags.co.uk/
CustomLog /var/www/cowbags.co.uk/logs/access.log combined
</VirtualHost>

I am not sure that I have got this right, I copied an example I found online somewhere.

I changed /var/www/ so it is owned by my username and group, and used chmod to change the permissions to 764.  I am pretty sure thats how I had it set up before I upgraded to breezy.  I want write permissions for all users within my group.

The only other change I have made to apache is to enable mod_rewrite as I have .htaccess files to refer [www.site.com](www.site.com) to site.com for each of my 5 domains.

If anyone could tell me where I have gone wrong it would be greatly appreciated.  I am good with sites but clueless with configuring apache.

Thanks, Kate.

---

### Post by LordHunter317 on 2005-10-15
[QUOTE=kthdsn]I changed /var/www/ so it is owned by my username and group, and used chmod to change the permissions to 764.[/quote]That's you're problem.  On a directory bit '1' or 'x', the access bit, is required to get anything inside a directory.  Apache is dying for the exact reason it said.

> I am pretty sure thats how I had it set up before I upgraded to breezy.  I want write permissions for all users within my group.You want 775 permissions then, and likely 2775 permissions on folders.

---

### Post by kthdsn on 2005-10-15
Thank you so much, I knew it would be something silly I had missed.  I'm still learning I guess.

---

