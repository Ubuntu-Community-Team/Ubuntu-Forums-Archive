---
title: "Apache listing directory to denied users (!!)"
date: 2007-11-11
forum: Server Platforms
---

### Post by gianluigi.zanettini on 2007-11-11
Hi all!

I've a very weird problem with Apache..

I set up Apache to allow access only from a given IP: I want all the other clients to be "Forbidden You don't have permission to access".

It works pretty good except that **directories are still listed** (Options Indexes) to all the clients, while files are not, and if you directly type a file URL, you effective get "forbidden".

Now, [B]I don't want neither files (this already works) nor directories (this doesn't!) to be listed to denied clients!
[/B]

```
<VirtualHost *:80>
	ServerName mli2.nasdaq
    DocumentRoot "/usr/www/dev"

	<Directory "/usr/www/dev">
		Options Indexes
		Order Deny,Allow
		Deny from all
		Allow from 62.125.146.134
	</Directory>
</VirtualHost>
```

Any help is really appreciated, thanks!

---

### Post by conjur3r on 2007-11-12
Try getting rid of the Options Indexes part and restart apache for changes to take affect.

---

### Post by gianluigi.zanettini on 2007-11-12
Hi, thanks for your reply.

Of course it works that way, but  I want the allowed IP to have dir listing enabled!

---

### Post by conjur3r on 2007-11-12
Sorry, I really should learn to read the entire post before replying!

Have you got a default global config somewhere which has that Options Indexes part?  Try:

# grep -R Options\ Indexes /etc/apache2/

---

### Post by gianluigi.zanettini on 2007-11-12
Nope: I got a few Options Indexes, but are all related to totally different virtual hosts! :confused:

I tried to commet theem out (just in case..) but no luck (of course..)

---

### Post by conjur3r on 2007-11-12
I just gave it a go on my laptop here and it's working as expected on a clean install.  I only allowed indexing from 127.0.0.1 and denied everything else as a test.  The only thing I can think of is maybe you have a .htaccess file in that directory?

Are there any other apache configs on the /usr/www/ directory?

---

### Post by gianluigi.zanettini on 2007-11-12
Solved!! Your hint about htaccess give me the idea to add *AllowOverride none*: even if I actually don't have any htacess file in my dir, this did the trick!

If you come to Italy, don't forget to stop in Ferrara for a glass of wine!

---

### Post by conjur3r on 2007-11-12
Glad you solved it!

Sweet!  I'll bring the shrimp and the bbq :)

---

