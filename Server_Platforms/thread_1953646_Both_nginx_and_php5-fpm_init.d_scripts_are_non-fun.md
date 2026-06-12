---
title: "Both nginx and php5-fpm init.d scripts are non-functional.. ?"
date: 2012-04-06
forum: Server Platforms
---

### Post by olivertreend on 2012-04-06
Hi

I have been using nginx and php5-fpm on my Ubuntu box for a while now. Everything has been configured and setup correctly, and it ran like a charm.

I have been keeping the packages updated & upgraded as usual, but haven't touched the nginx OR php5-fpm config files at all (thus I;m pretty sure this isn't my fault... )

Basically, I noticed nginx wasn't running as it should be. I ran the command "sudo service nginx start", and the script did nothing. The same thing happens when trying to do anything - start, stop, restart or reload. This also happens for the "php5-fpm" init script - although all other init scripts seem to be functioning correctly.

When trying to start nginx OR php5-fpm, this is what happens:
```
root@HAL:/etc# service php5-fpm start
root@HAL:/etc# 
```

I can't understand what is going wrong. The script isn't returning errors, but similarly it isn't starting the daemon or reporting success as usual.

For reference, both installations are from the official nginx and php5-fpm PPAs. The fact that both started doing this at the same time has thrown me - since they are both unrelated packages.

I have since purged both sets of packages from my system with ```
apt-get purge ...
``` and also ```
apt-get remove --purge ...
``` both of which have successfully removed the packages, their config files, and their init.d startup scripts.

After having reinstalled nginx, I now have a functioning startup script again - I can start the web server as usual.
However, php5-fpm is still experiencing the strange premature exiting of the startup script.. and I really can't figure out what's causing it.

I have no idea what caused this to occur initially, but have managed to fix nginx. I now need to fix the php5-fpm startup script.

If anybody could shed some light on this situation, I would be very grateful! The chances are both these issues are related - and they were caused by me doing something stupid. But now I need to fix it. This time I was lucky - because these problems are just on my development server. But I have 2 other live servers which are configured in a similar way, and I am worried the same thing will happen to these two as well!

Has anybody else come across this? Do you have any words of advice? :confused:

Thank you

---

