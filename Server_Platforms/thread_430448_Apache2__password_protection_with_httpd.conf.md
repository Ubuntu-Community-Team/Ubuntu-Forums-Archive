---
title: "Apache2  password protection with httpd.conf"
date: 2007-05-02
forum: Server Platforms
---

### Post by robert@debian on 2007-05-02
Hi folks,

I&#8217;m desperately trying to get my Apache2 password protection working. 
Since I&#8217;ve installed &#8220;mod_musicindex&#8220; the other day I&#8217;d like to keep my music directory private.

I&#8217;d like to secure my directory without using a .htaccess file. I&#8217;ve put my configuration in the /etc/apache2/httpd.conf. 
```
 
<Directory /var/www/musicindex>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/passwd/passwords
Require valid-user
</Directory>

```

As you can see I&#8217;ve placed my password file in /etc/apache2/passwd/passwords
I have used the htpasswd &#8211;c command to create the password file.
```
 -rw-r----- 1 www-data www-data   21 2007-04-10 10:18 passwords 
```

But when I restart apache2 and access the directory I&#8217;m not prompted to enter username nor password.

I&#8217;ve checked [http://httpd.apache.org/docs/2.2/howto/auth.html]("http://httpd.apache.org/docs/2.2/howto/auth.html"), without success however ;-(

So do you guys have any clue what I&#8217;m doing wrong?

---

### Post by jtc on 2007-05-02
> #</Directory>

What if you remove the #?

---

### Post by robert@debian on 2007-05-02
Ups my bad, I hit "#" accidentally. It's not in the httpd.conf.
Thanks anyway.
Do you have another hint?

---

### Post by jtc on 2007-05-02
Hmm... strange.

Well, it certainly look as if it should work. Obviously that isn't enough thought :) 

Personally I'd say a more logicall place to put the <Directory ...> setting would be inside the <Virtualhost ..> in question. Still, it should work in httpd.conf as well.

Running a default apache2 install in Ubuntu, or self compiled? Apache 2.0.x or 2.2.x?

Does your error_log say anything interesting?

Perhaps mod_musicindex and mod_auth doesn't get along? Tried testing the authentication without mod_musicindex enabled?

---

### Post by robert@debian on 2007-05-03
Thanks alot jtc. It seems there is a conflict with *mod_musicindex* and *mod_auth*. 
When I switch *mod_musicindex* off the password protection works flawlessly.

Is there another solution to secure this directory? I've also tried using .htaccess, however it
won't work as well.

---

### Post by MJN on 2007-05-03
Where is all your musicindex config? I've never used it myself but presumably there must be some... (check mods-available and sites-available) and that's where you should be putting your auth config otherwise if the musicindex config (specific to the musicindex directory) is getting loaded last it'll overwrite any of your earlier auth stuff in httpd.conf.

Mathew

---

### Post by robert@debian on 2007-05-04
Thanks MJN, 

I've followed [[COLOR="Red"]that[/COLOR]]("http://ubuntuforums.org/showthread.php?t=34359") HowTo.
The mdoule which loads mod_musicindex is the first line in my httpd.conf, after a few comments. Afterwards comes the password config.
Better post it :) 
 
```

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

#### Music Stream !!!!
LoadModule musicindex_module /usr/lib/apache2/modules/mod_musicindex.so

<Directory /var/www/musicindex>
  AuthType Basic
  AuthName "Restricted Files"
  AuthUserFile /etc/apache2/passwd/passwords
  Require valid-user
</Directory>

```

The directory config for mod_musicindex is located in the alias file in /etc/apache2/conf.d/

Thats all for mod_musicindex, there are no further config files.

I haven't changed a thing in sites-available and mods-available.

---

### Post by kvonb on 2007-05-04
The latest versions of Apache don't use the httpd.conf file anymore, they use /etc/apache2/apache2.conf.

This is from my apache2.conf file:

```
# Added by Kev, should make the folder /var/www/webshare/private require a password!
<Directory /var/www/webshare/private>
    AuthType Basic
    AuthName "Restricted area"
    AuthUserFile /var/www-passwords/passwords
    Require user private
</Directory>
```That is right at the end of apache2.conf.

I can't remember how I created the password though :D.

---

### Post by jtc on 2007-05-04
> **MJN said:**
> 
Where is all your musicindex config? I've never used it myself but presumably there must be some... (check mods-available and sites-available) and that's where you should be putting your auth config otherwise if the musicindex config (specific to the musicindex directory) is getting loaded last it'll overwrite any of your earlier auth stuff in httpd.conf.
Mathew

> **robert@debian said:**
> Thanks MJN, 
The directory config for mod_musicindex is located in the alias file in /etc/apache2/conf.d/


...and there we've got it. If you look in your apache2.conf you'll see that conf.d/ is loaded after httpd.conf, and therefor overwriting the auth settings. You could move things around, but I kind of agree with MJN on you putting the auth-settings together with your musicindex config.

Might also be nice to move things into mods-available/enabled, to get your settings more in style and structure with the way Ubuntu (and Debian) handles Apache. Then "LoadModule musicindex_module..." should go in mods-available/musicindex.load and the configuration into mods-available/musicindex.conf

Then you'll enable that module using the command: a2enmod musicindex

...which would in turn create symlinks inside mods-enabled, which apache2.conf reads.

---

### Post by robert@debian on 2007-05-04
Thanks both of you.

I removed all the config stuff from httpd.conf
Then I moved to /etc/apache2/mods-available and created musicindex.conf. 
musicindex.load already existed so I just confirmed that the command is correct. 

Finally I wrote the password protection config at the end of apache2.conf as you both suggested. 

I restarted the apache2 server, however there is still no password protection. Well at least it proofs, 
that the way with the mods-available folder works as well.

The error.log don't give me any clues either. 

Do you guys have any ideas left?

Robert

---

### Post by jtc on 2007-05-04
What if you, the way (I belive) MJN suggested, put the auth-settings in the same <Directory...> as your musicindex-settings?

Should be noted that I don't have any actual experience of mod_musicindex myself. These suggestions I've made are purely (educated?) guesses.

---

### Post by MJN on 2007-05-04
Agreed. I'm sure we're heading in the right direction here...
 
The goal really is to have all your config related to a particular directory (your music store in this case) all in the same place - seperating them out will at best lead to confusion and at worst runs the risk of bits being overwritten as they are loaded in.
 
To reiterate what JTC said, put your password stuff in the same <Directory> portion as the rest of your MusicIndex stuff.
 
Mathew

---

### Post by robert@debian on 2007-05-04
You guys are really giving me a hand here. Thanks
I've change something in the musicindex.conf and now it seems 
that I'm one step closer to success.

Lets look at the code here.
```

[COLOR="Red"]Alias /musicindex /home/ftp/pub/music/[/COLOR]
<Directory [COLOR="Red"]/musicindex[/COLOR]>
    Options Indexes MultiViews FollowSymlinks
    AllowOverride       Indexes
    MusicLister         On
    MusicSortOrder      album disc track artist title length bitrate freq filet$    MusicFields         title artist length bitrate
    MusicAllowDownload  Off
    MusicAllowStream    On
    MusicAllowSearch    On
####    MusicRssItems       Off
    MusicPageTitle      home
    MusicCssDefault     musicindex.css
    MusicCachePath      /tmp/musicindex
####    MusicIceServer     [ice.domain.my]:8000
####    MusicCookieLife    300
</Directory> 
```

The clue here seems to be using the alias in the <Directory> section rather than the
real path (marked red). I've used the real path till now. 
It's most likely that when I use /musicindex in the permission section I'll have to use it as well in the config for mod_musicindex it self, which is actually what you mean MJN. 

I've also put all the config stuff in my apache2.conf in one <Directory> section as both of you suggested, well that didn't solve the problem though.

Finally I'm stuck at a **Forbidden** screen though. All directories are set at 755 -R so everyone should be able to read and execute these files.

Robert

---

### Post by MJN on 2007-05-04
I'm getting confused now.... Where is that code snippet from?

Bottom line - have all the code related to your MusicIndex directory in the same place, in the same file. Whether that config be MusicMatch stuff, permission's stuff, anything, everything - all in the same file.

Also, your <Directory> directive should be **<Directory /home/ftp/pub/music>** as it must specify the absolute path *in the filesystem*.

Mathew

---

### Post by robert@debian on 2007-05-04
It WORKS !!!

All I had to do was just set the absolute path in both configuration files.

end of /etc/apache2/apache2
```

<Directory /home/ftp/pub/music>
  AuthType Basic
  AuthName "Restricted Files"
  AuthUserFile /etc/apache2/passwd/passwords
  Require user robert
</Directory>

```

and the /etc/apache2/mods-availabe/musicindex.conf

```

Alias /musicindex /home/ftp/pub/music/
<Directory /home/ftp/pub/music>
    Options Indexes MultiViews FollowSymlinks
    AllowOverride       Indexes
    MusicLister         On
    MusicSortOrder      album disc track artist title length bitrate freq filet$    MusicFields         title artist length bitrate
    MusicAllowDownload  Off
    MusicAllowStream    On
    MusicAllowSearch    On
####    MusicRssItems       Off
    MusicPageTitle      home
    MusicCssDefault     musicindex.css
    MusicCachePath      /tmp/musicindex
####    MusicIceServer     [ice.domain.my]:8000
####    MusicCookieLife    300
</Directory>

```

Thanks to your confusion MJN you put me on the right path to use the absolut path.

Thank you very much Mathew and jtc. Why haven't I tried this in the first place :confused: 

Robert

---

### Post by MJN on 2007-05-04
Not so fast...

Get rid of that config in apache2.conf and move it into the <Directory> section in musicindex.conf....

Leaving the config in two places is asking for trouble - sure it works now but if/when you start adding directives you could so easily end up in a mess.

You have been warned!

Mathew

---

### Post by robert@debian on 2007-05-07
Thanks for that hint MJN, however when I move the configuration in the 
musicindex.conf in mods-available the password protection won't work
anymore.

Seems the password protection can just be done within the apache2.conf 
and / or httpd.conf
Well I'll guess I've to leave it in the apache2.conf.
Momentarily I just need two directorys to be protected and these work. 
I hope there won't be a mess in the future though :D

---

### Post by MJN on 2007-05-07
Personally I'd put all the config in the relevant file in /etc/apache2/sites-available - that is after all what it's for.

If you're content, and it works, then I guess there's no harm done as long as you're aware of the parallel config for the same <Directory> section being in two seperate files (after all this you probably won't forget!).

Mathew

---

