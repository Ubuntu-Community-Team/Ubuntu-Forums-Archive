---
title: "libphp5.so is garbled"
date: 2007-05-22
forum: Server Platforms
---

### Post by Daniel_Walker on 2007-05-22
After runing a recent upgrade on one of our (less important) servers, it appears that PHP5 can no longer be started when restarting apache2. The message recieved is the classic:
> 
API module structure `php5_module' in file /usr/lib/apache2/modules/libphp5.so is garbled - perhaps this is not an Apache module DSO?

My assumption is that the version of PHP5 that intalled with the upgrade is incompatible with the version of Apache that installed. Not sure how that happened, but, removing and reinstallling PHP5 with apt-get simply removes and replaces the same, broken, version (it installs and removes cleanly, in all other respects, except I do notice that I get the message '1 not fully installed or removed', whenever I do this).

I assume it's a problem with my cache. I'm a bit new to Debian-based Linux, and am not aware of how best to sort this out, or which direction to even proceed. This is early days, for me, with this, but any suggestions as to how I should start solving things would be great. I'll be happy to provide full outpout from anything anyone wants me to run, to try and diagnose what's up.

I'd download and build a module from source, if need be - in fact, I would have, had this been a more critical server, for us - but I feel it would be better if I could provide a more permanent and less labour-intensive solution, since I'll be tied to doing that each time the package is updated.

Any suggestions very much appreciated
Dan

---

### Post by newhelan on 2007-05-30
I seem to be having the same problem. If you have already found the solution Daniel, could you let me know how you did it?

Thanks,
Neil.

---

### Post by newhelan on 2007-05-30
I seemed to have gotten it working. Not quite sure what I did.

Firstly, I went: 

apt-get install libapache2-mod-php5 php5-mysql 

instead of installing PHP5 manually.

Then I used the apachectl script instead of the apache2ctl one, and the httpd.conf file was accepted with the libphp5.so added and all.

Don't know if the problem was that I should have been using apachectl all along, or if in fact it even existed before I did the apt-get.

Hope this helps, it wasted me a day and a half anyway.

---

