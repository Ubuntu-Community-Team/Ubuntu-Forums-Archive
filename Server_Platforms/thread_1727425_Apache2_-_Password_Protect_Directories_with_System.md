---
title: "Apache2 - Password Protect Directories with System User"
date: 2011-04-12
forum: Server Platforms
---

### Post by geudrik on 2011-04-12
I want to password protect say a subdirectory, or a subdomain via vhost, with a username/password, but use the systems users and passwords as logins -> I want go avoid any and all .htaccess... as everyone should be doing anyway :P

How would I go about doing this?  

I know my way around the apache configs fairly well, so I'm not a total newb -> I now I can use .useraccess and .pwaccess but that's flat file driven, not based off of the systems users/passwords.

---

### Post by SeijiSensei on 2011-04-12
Take a look at [http://code.google.com/p/mod-auth-external/wiki/Configuration#3._Configuring_Web_Pages_to_Use_Authentication](http://code.google.com/p/mod-auth-external/wiki/Configuration#3._Configuring_Web_Pages_to_Use_Authentication)

---

