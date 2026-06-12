---
title: "apache2.2 htaccess"
date: 2007-05-01
forum: Server Platforms
---

### Post by dlehman on 2007-05-01
Well the upgrade to feisty broke my apache a bit and it took me a while to get it running good again TinayCA to the ssl working again.  but here is the situation I am running an application called churchinfo info that I am going to host at home because our church does not have net access, but i am testing other apps such as joomla and I  don't want people stumbling across my comp i want to make it as secure as possible, before I didn't worry to much because my Ip address changed every day but now I am registered with dyndns. 

I want to forbid directory browsing but .htaccess will not work I have tried 
IndexIgnore *
deny from all 

and neither work 

I like to use webmin but it does not work so well with apache 2.2 half the settings don't save  ](*,)

any suggestions](*,)  or point me to a good howto on locking my system down would be great 

Thanks

---

### Post by sirlancelot on 2007-05-01
Try using:```
Options -Indexes
``` in your .htaccess file.

Or if that doesn't work, add it to your main Apache config.

---

### Post by dlehman on 2007-05-01
No that didn't work is there something I have to do to tell apache to let me use .htaccess files and just to make sure I don't have to restart apache for the changes of a .htaccess file to take effect do I, I have been just in case but for future reference.  

also on a side note since I upgraded to feisty there are packages in synaptic listed but are not available for install   such as apache2-common 

Thanks

---

### Post by dlehman on 2007-05-02
I have it working I did some more reading for future reference if anyone else has the same problem in the site config file such as 

/etc/apache2/sites-enabled/000-default


AllowOverride None was set and with it set to none the .htaccess file is useless
but insted of using .htaccess files I just put in a per director section and made sure that Indexes were not listed in the options line for the root / and /var/www this prevents all directory browsing


hope this can help someone else out later

---

### Post by sirlancelot on 2007-05-05
Great job! That little option went right past me.

Oh, and no, you don't have to restart apache for .htaccess settings to take effect, that's the beauty of the file!

---

