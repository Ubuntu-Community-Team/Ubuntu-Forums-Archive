---
title: "Apache2.conf Syntax error when rebooting Ubuntu 12.04 Server"
date: 2013-07-08
forum: Server Platforms
---

### Post by tdisalvo on 2013-07-08
Hi,

Let me start off by saying I am new to Linux.  I have 10 + years experience on Windows, but changing platforms is something that I have just started undertaking.  

I have a server that is on a VM.  It was working fine, untill I rebooted the server today becasue the .xsession-errors log filled up the hard drive.  Once I rebooted it, I can no longer get into the gui.  There is an error booting apache2.  

"Syntax error on line 205 of /etc/apache2/apache2.conf: Syntax error on line 1 of /ect/apache2/mods-enable/proxy_html.load: Cannot load /usr/lib/libxml2.so.2 into server: /user/lib/libxml2.so2: cannot open shared object file: no such file or directory

Action "start"failed.

It now just sits here.  I can tell that there is a file missing or corruput but I have no idea how to get past this error to work on fixing it.  

I need some basic help on what to do.  

Thanks

---

### Post by tdisalvo on 2013-07-08
FYI, I am able to enter in text so I tried to run 
nano /etc/apache2/mods-enabled/proxy_html.load but it did not do anything.  I also tried
vi /etc/apache2/mod-enabled/proxy_html.load  and
nano /etc/apache2/mods-enabled/proxy_html just in case the .load is some sort of command as opposed to a file name.  

No luck, please help

---

### Post by CharlesA on 2013-07-08
What version of Ubuntu are you using? I found a bug report on the proxy_html.load thing:
[https://bugs.launchpad.net/ubuntu/+source/mod-proxy-html/+bug/964397](https://bugs.launchpad.net/ubuntu/+source/mod-proxy-html/+bug/964397)

I've never used Apache as a proxy, so I don't know if that works or not.

As far as the .xsession-errors go, have you looked into what is causing the errors? If it's stupid stuff, you could just redirect the output to /dev/null:
[http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable](http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable)

Run this please:

```
ls -l /etc/apache2/mods-enable/
```

---

### Post by tdisalvo on 2013-07-08
Ok in a, solve your own problems manner, I think that I have fixed it.   A lot of times I just need to type out my thoughts on a forum in order to get them down. 

So the real problem was that I was out of disk space, which was due to the fact that .xsession-errors file had filled up the hard drive.  Typically when there is space, I can reboot the server, and it will clear out the old file .xsession-errors.  This time there was no disk space, which apparently meant that the os could not create a file that it needed during boot to have the apache2 webserver start.  

This was what was really happening.  So I restarted the server and held down shift in order to get a boot menu. 
Once I did this I selected Ubuntu, with Linux 3.2.0-23-generic (recover mode)
Then from the recovery menu I selected clean
I let this process run then when I was returned to the Recovery Menu I selected resume

This process cleaned up enough space for me to boot.  Then once I was able to log in, I selected restart again.  
With this restart the .xsessions-error log was cleared.  

I am now back to my initial error of the .xsession-error.  I will close out this thread and start searching for how to fix that.

---

### Post by CharlesA on 2013-07-08
> **tdisalvo said:**
> Ok in a, solve your own problems manner, I think that I have fixed it.   A lot of times I just need to type out my thoughts on a forum in order to get them down. 

Done that too many times to count. ;)

> I am now back to my initial error of the .xsession-error.  I will close out this thread and start searching for how to fix that.

Put a link here, in case someone else has the same problem. :)

---

### Post by tdisalvo on 2013-07-08
> **CharlesA said:**
> What version of Ubuntu are you using? I found a bug report on the proxy_html.load thing:
[https://bugs.launchpad.net/ubuntu/+source/mod-proxy-html/+bug/964397](https://bugs.launchpad.net/ubuntu/+source/mod-proxy-html/+bug/964397)

I've never used Apache as a proxy, so I don't know if that works or not.

As far as the .xsession-errors go, have you looked into what is causing the errors? If it's stupid stuff, you could just redirect the output to /dev/null:
[http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable](http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable)

Run this please:

```
ls -l /etc/apache2/mods-enable/
```

Thanks for the info on the .xsession-errors.  I am going to follow this now and hopefully I will not see this problem again.  

Great forum.

---

