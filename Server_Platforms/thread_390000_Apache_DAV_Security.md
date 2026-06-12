---
title: "Apache DAV Security"
date: 2007-03-21
forum: Server Platforms
---

### Post by szim90 on 2007-03-21
Hello.

I enabled webDAV on a specific folder inside my apache document root directory. Here is something similar to the directive I used:

<Location /dav>
        DAV On
        AuthType Digest
        AuthName "dav-password"
        AuthDigestFile "/var/apache/davdigest"
        Require valid-user
</Location>

From what I read on the apache website, I think the passwords are sent securely. Are the files transfered using webDAV are securely transfered? If not, how would I make it more secure?

Thank you for any help,
Sean

---

### Post by Frosty Cold Drink on 2007-03-21
Files are sent as plain-text. If you want to tighten things up, you can use WebDAV over SSL.

---

### Post by szim90 on 2007-03-21
Okay. Thank you.

Is there a special procedure for enabling ssl for dav, or should I just follow the directions at apache.org as if I was adding ssl to a regular website?

---

### Post by Frosty Cold Drink on 2007-03-21
> **szim90 said:**
> Okay. Thank you.

Is there a special procedure for enabling ssl for dav, or should I just follow the directions at apache.org as if I was adding ssl to a regular website?

The regular directions will work fine. There isn't anything special you need to do.

---

### Post by szim90 on 2007-03-21
Got it. Thank you for all of your help.

---

### Post by szim90 on 2007-03-22
I apologize for reopening this, but I was wondering:

I generated the ssl certificate, and told apache to use ssl with SSLEngine on. I am curious, does it matter that I am using port 8000 instead of port 443 (port 443 is blocked by my isp)? Also, is there a way to check that ssl is working correctly?

---

### Post by Frosty Cold Drink on 2007-03-22
> **szim90 said:**
> I apologize for reopening this, but I was wondering:

I generated the ssl certificate, and told apache to use ssl with SSLEngine on. I am curious, does it matter that I am using port 8000 instead of port 443 (port 443 is blocked by my isp)? Also, is there a way to check that ssl is working correctly?

So long as apache is listening on the right port, and your SSLEngine directive is in the proper scope (virtual host matching on your alternate port) you should be ok.

---

