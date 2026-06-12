---
title: "Anyone using word press blog - Linux Commands method not implemented"
date: 2009-12-23
forum: The Cafe
---

### Post by ade234uk on 2009-12-23
Ok there must be a workaround you are using without having to contact your server admin. 

The issue I have is the old METHOD NOT IMPLEMENTED error when I create a new post on my blog. It only happens to certain posts that have some terminal commands in them. 

Question I want to ask is how have you got around this?

---

### Post by FuturePilot on 2009-12-23
> **ade234uk said:**
> Ok there must be a workaround you are using without having to contact your server admin. 

The issue I have is the old METHOD NOT IMPLEMENTED error when I create a new post on my blog. It only happens to certain posts that have some terminal commands in them. 

Question I want to ask is how have you got around this?

This usually has something to do with mod-security. I'm not sure of the level of access you have to the server but you would need at least FTP access or similar to be able to add or modify .htaccess. Something like this should work 
```
<IfModule mod_security.c>
SecFilterEngine Off
SecFilterScanPOST Off
</IfModule>

```

I would suggest perhaps only disabling it when making a post and then re-enabling it afterwards. Mod-security is really pretty awesome.

---

### Post by slakkie on 2009-12-23
I don't fully understand your problem. You want shell commands to run when you post something?

---

### Post by ade234uk on 2009-12-23
Thank you for the tip. I have already used an htaccess file without any luck. I have also contacted the hosts and they are not prepared to do anything. There must be another way. I could always try and dip in to the code of wordpress and try a str_replace in the code?

---

### Post by FuturePilot on 2009-12-23
> **ade234uk said:**
> Thank you for the tip. I have already used an htaccess file without any luck. I have also contacted the hosts and they are not prepared to do anything. There must be another way. I could always try and dip in to the code of wordpress and try a str_replace in the code?

I'm not sure how str_replace works but I don't know if there is really any other way around it. Basically, mod-security sees commands in your post, thinks they're malicious, and blocks it. If there was another way around it aside from modifying htaccess or Apache's configs, then mod-security wouldn't be doing its job ;)

---

