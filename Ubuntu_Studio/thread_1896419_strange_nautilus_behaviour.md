---
title: "strange nautilus behaviour"
date: 2011-12-16
forum: Ubuntu Studio
---

### Post by Mutikasa on 2011-12-16
Hi, my dear friend has this problem. this is copy paste:

I run Ubuntu 10.10. At first, icons in Nautilus got smaller and zoom didn't work. Then when I started again it opens in only one window and lost his selections in "View". To show what I mean here is the screenshot

[http://i.stack.imgur.com/UfX8w.jpg](http://i.stack.imgur.com/UfX8w.jpg)

Last time I installed PHP-GTK and all sorts of libraries that is needed for that and was working fine, but the next time I turn on computer I got this nautilus behaviour  and bluethoot icon in panel which I removed long time ago.

When I do `sudo nautilus` it opens fine except icons which are still smaller than before. It opens with this message:

  ```
  Initializing nautilus-image-converter extension
    Initializing nautilus-gdu extension
    
    ** (nautilus:8100): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '8100'
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
    Please ask your system administrator to enable user sharing.
    
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    
    (nautilus:8100): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
    Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
    Please ask your system administrator to enable user sharing.
```    

How can I get back to old nautilus?

[URL="http://i.stack.imgur.com/UfX8w.jpg"]
[/URL]

---

