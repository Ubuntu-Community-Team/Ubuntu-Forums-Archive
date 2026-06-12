---
title: "Apache config file ownership"
date: 2007-09-01
forum: Server Platforms
---

### Post by eddieroger on 2007-09-01
I just finished installing Apache/PHP on my Slicehost slice, and in the process of setting up some virtual servers, I had a question. This may be more rhetorical than anything, but should root own the sites-available and sites-enabled folders? I don't have a problem sudo-ing to create files here, but it seems a little opposite of the ways things are done in Ubuntu, and maybe even a little insecure on its own. I've been tossing the idea around of changing the owner to www:www, and since my user is in the www group, giving it 775 permissions. Would this be bad practice? I've got the box well secured against unwanted SSH visitors, and I'm the only user with permission to log in, so box-side access to this folder isn't a concern. Am I right to think its weird for root to own this folder, or is that just practice? Thanks.

---

### Post by kidders on 2007-09-02
Hi there,

> **eddieroger said:**
> I've been tossing the idea around of changing the owner to www:wwwPretty much the *last* thing you want is to have a web server that owns (and ergo may well be able to modify) its own configuration files. Even a minor bug in, say, a PHP app you might be running would have the potential to expose your entire filesystem over HTTP.

> **eddieroger said:**
> I'm the only user with permission to log inTo keep your box stable and secure, it's important not to let that tempt you to be lax with your filesystem access controls.

> **eddieroger said:**
> Am I right to think its weird for root to own this folderNo.
[LIST]
[*]Without exception, both the user and group that own all apache configuration files must be root.
[*]Additionally, all files must be "chmod 644", at their most permissive.
[*]Directories should be "chmod 755", again, at their most permissive.
[*]Access to some of the contents of your apache's SSL configuration directory may need to be more tightly controlled (eg "chmod 600").[/LIST]As a general rule, no mechanism should exist that might theoretically allow your apache server to write to anything on your system, unless there is simply no other way of achieving a particular effect you happen to want. Read access to certain things should also be jealously guarded. The most effective ways of ensuring this include...
[LIST]
[*]Not adding the user your web server runs as to any groups, other than its own private group.
[*]Making sure you web server user is the sole member of its private group.
[*]Not doing anything silly ... eg allowing your web server user to own anything in the www root (often located somewhere like /var/www/htdocs).[/LIST]Anyhow... sorry for being so long-winded. I hope something in there answers your security questions. The important thing to note, I suppose, is that by deviating from the established norms in areas like this one, you strip away built-in protection your system offers you against bugs in its own software.

---

### Post by eddieroger on 2007-09-02
Thanks for the reply. I'm not security ignorant, but I didn't consider the things you've mentioned. So, my permissions stay, and I'll sudo when creating virtual server config files. I do keep better security around my files on my system, and didn't intend to let it seem that my lack of users was a mitigation for lax security. Again, thanks for the reality check.

Just to be safe, though, I won't be sharing my server's IP address. :)

---

### Post by kidders on 2007-09-02
No worries. :-)

---

