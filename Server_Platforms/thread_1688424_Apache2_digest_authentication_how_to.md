---
title: "Apache2 digest authentication how to"
date: 2011-02-15
forum: Server Platforms
---

### Post by Cyked on 2011-02-15
I have not been able to find this either on google or searching here.  Right now I'm using basic authentication and want to implement digest and just can not get it working.  

Basic is straight forward in that I just specify:

```
<Directory /var/www/.temp>
AllowOverride None
AuthType Basic
AuthUserFile  /etc/apache2/passwd/passwords/.htpasswd
AuthName "Restricted Files"
Require valid-user
</Directory>

```

I don't know what I am missing.  In examples I have found people run the htdigest command like I would imagine (password file, realm, username), but in httpd.conf they point AuthUserFile to something like "/something/something/.htdigest".  Do I have to use .htaccess files for digest auth?

Basically I'm not sure in httpd.conf what for AuthDigestFile/Domain is pointed where and where that *should* exist, if that makes sense.

---

### Post by hawkmage on 2011-02-15
You should not need an .htaccess to use Digest Auth but you do need to add the users to your .htpassword file you are pointing to.
Here is a link to the Apache 2 docs about authentication:[ http://httpd.apache.org/docs/2.0/howto/auth.html]("http://httpd.apache.org/docs/2.0/howto/auth.html")

BTW: Like the Arrogant Bastard Logo as your Avatar.

---

### Post by Cyked on 2011-02-15
> **hawkmage said:**
> You should not need an .htaccess to use Digest Auth but you do need to add the users to your .htpassword file you are pointing to.
Here is a link to the Apache 2 docs about authentication:[ http://httpd.apache.org/docs/2.0/howto/auth.html]("http://httpd.apache.org/docs/2.0/howto/auth.html")

BTW: Like the Arrogant Bastard Logo as your Avatar.

Is AuthDigestFile  the PW file created by htdigest -c?

---

### Post by hawkmage on 2011-02-15
Yes the "htdigest -c" creates the digest PW file.  Do not continue to use the "-c" with subsequent users you add because that will delete and recreate the Digest PW file each time causing the previous users to disappear.

---

### Post by Cyked on 2011-02-15
Weird, got it working.  I think I was making it more difficult than needed.  Had to change AuthDigestFile to AuthUserFile for one thing (that wasn't what was keeping this from working though).

So does Basic auth and Digest auth work in the same matter except for htdigest -c creates the file with the MD5 and htpasswd just creates a file with the id and PW?   I was thinking it was more complex than that.

---

### Post by hawkmage on 2011-02-15
No it is very simple.

---

### Post by Cyked on 2011-02-15
> **hawkmage said:**
> No it is very simple.


HA!  I see that now ;)

As an aside, have you had Stone's Imperial Stout?

---

### Post by hawkmage on 2011-02-15
I have had just about every beer they have produced.  The only ones I have missed are pre 06 Vertical Epic, pre 03 Double Bastard and pre 12th Anniversary Ale.  I live about 12 miles from the Brewery.

---

### Post by Cyked on 2011-02-15
Is there an apache variable to limit number of login attempts?
I'll have to google around a bit tomorrow.  Out of time today.

> **hawkmage said:**
> I have had just about every beer they have produced.  The only ones I have missed are pre 06 Vertical Epic, pre 03 Double Bastard and pre 12th Anniversary Ale.  I live about 12 miles from the Brewery.

I've had Double Bastard, Its crazy bitter.

---

### Post by hawkmage on 2011-02-15
I am not aware of any directives for limiting the login attempts.  

If you can find it try Stone Ruination IPA, over the top bitter hoppy bit tasty.

---

### Post by Cyked on 2011-02-16
> **hawkmage said:**
> I am not aware of any directives for limiting the login attempts.  

Not finding anything.  Sounds like I could tweak fail2ban to key off apache requests, probably could do the same thing in iptables I imagine.

> **hawkmage said:**
> 
If you can find it try Stone Ruination IPA, over the top bitter hoppy bit tasty.

Have not.  I wonder if its similar to double bastard, which I found to be way way bitter just for the sake of being way way bitter.  It was pretty much undrinkable for me.

---

### Post by Cyked on 2011-02-23
Weak.  I just found out there is a "bug" or something around android.  I can get into directories with digest auth with no issues, but if you try and download a file it prompts for the PW ever time and won't work.  Apache logs have "password mismatch" errors. :(

---

