---
title: "apache and https"
date: 2007-05-11
forum: Server Platforms
---

### Post by namelessone on 2007-05-11
So I finally got ssl working with apache, but now I need to make all people who try to use http instead of https to be rerouted to https (this server is for webmail).

I did a some searching on it and ended up enabling the mod_rewrite and adding the following to my virtual hosts file: ```

        RewriteEngine On
        RewriteCond %{HTTPS} !=on
        RewriteRule ^(.*) https://%{SERVER_NAME}1$ [R,L]
        <Directory />
```
but it still doesn't work.

here's the output of the apache log file:
> [Fri May 11 11:02:05 2007] [error] [client 127.0.0.1] File does not exist: /var/
www/home, referer: [http://127.0.0.1/](http://127.0.0.1/)

can anyone help me?

---

### Post by MJN on 2007-05-11
Put a slash after the ^

(URI matching in the main server config will always start with a slash - your config would've worked fine in a .htaccess file)

Incidentally, that </Directory> directive suggests you've put this config inside a <Directory> section - better to put it in the parent <Virtualhost> then it'll definitely apply to all access requests (it could've been in <Directory /> but it'd still be good practice given it's a virtualhost-wide configuration and not directory specific).

Mathew

---

### Post by namelessone on 2007-05-13
well, I added the slash, and then I took it out of the <directory> part, and then I used SSLRequireSSL in the <directory /var/www>, but it still didn't work...

It's rather frustrating...it appears to work for everyone else...

well, anyway, I'm gonna do the quick and dirty way and make mail.whatever.com page just have a link on it that says "click here to continue" and have that link be https...

---

### Post by MJN on 2007-05-13
No! That's naff - it needs to be automatic! Come on, don't give up.... (I know how you feel though, but if everyone else's is working then there's no reason yours shouldn't).

Post what you've got now and we can start from there...

Mathew

(P.S. Or, go to [http://mail.newtonnet.co.uk](http://mail.newtonnet.co.uk) and see if that 'effect' would meet your needs. It's not *exactly* your original intent but at least it's automatic, simple for users, and doesn't allow non-SSL access. If this'll do (ignoring the cert error of course) then I'll post my config)

---

### Post by MJN on 2007-05-13
Just noticed your original config had 1$ instead of $1 - that might be worth changing also! ;)

Mathew

---

### Post by namelessone on 2007-05-13
Thanks for not letting me give up! :grin: I'm away from my machine now, but I'll try the 1$ thingy...


> (P.S. Or, go to [http://mail.newtonnet.co.uk](http://mail.newtonnet.co.uk) and see if that 'effect' would meet your needs. It's not exactly your original intent but at least it's automatic, simple for users, and doesn't allow non-SSL access. If this'll do (ignoring the cert error of course) then I'll post my config)

I'd really like to see your config for this. I'm still very new to apache, and seeing someone else's config that works will really help me (especially since I'm using squirrelmail too).

---

### Post by MJN on 2007-05-15
Sorry for the delay... Here's the relevant config extract :

```

#
# Redirect for mail.newtonnet.co.uk:80 > secure.newtonnet.co.uk:443/mail/
# Note it strips the full path as it is meaningless at the destination
# and probably not intended by the user
#

<VirtualHost *:80>
     ServerName mail.newtonnet.co.uk:80
     RewriteEngine On
     # Redirect with code of 302 (temp redirect - don't update records) and then stop proce
ssing rules
     RewriteRule ^/(.*)$ https://secure.newtonnet.co.uk/mail/ [R,L]
</VirtualHost>

#
# Redirect for secure.newtonnet.co.uk:80 > secure.newtonnet.co.uk:443
# to trap intended accesses to secure NewtonNet but omitting https or :443
# Note it maintains the full path as this is likely desired by the user
#

<VirtualHost *:80>
     ServerName secure.newtonnet.co.uk:80
     RewriteEngine On
     Options +FollowSymLinks
     RewriteRule ^/(.*)$ https://secure.newtonnet.co.uk/$1 [R,L]
</VirtualHost>

```It works well - users simply need to enter **[COLOR=Blue][mail.newtonnet.co.uk]("http://mail.newtonnet.co.uk/")[/COLOR]** and get automatically directed to the SSL webmail page without having to faff around with https/port modifiers and/or having to remember an unwieldy URL.

The second config portion simply deals with the case of when (if) someone uses an intended-SSL URL but forgets/omits the https/port modifier. The logs show this never happens but it does no harm it being there just to help if it does.

Mathew

---

