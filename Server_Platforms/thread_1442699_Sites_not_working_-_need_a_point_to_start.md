---
title: "Sites not working - need a point to start"
date: 2010-03-30
forum: Server Platforms
---

### Post by wattaman on 2010-03-30
Hi!
Something wrong is happening to my server lately and I don't know where to start investigating. My linux knowledges are very limited. To make the picture clear and simple, this is what happens:
- the sites doesn't work, aparently those running on php; the static html seems to work;
- if I restart the server everything is fine again;
- I didn't make major changes to the server, Apache or anything else lately; the only thing I remember that should be important (I think) is that I've activated the mod_security in Apache;
- though the sites don't work - BTW, they're loading forever until the browser rejects the connection - the server runs fine and I have access to Webmin; there I can see there's enough memory and CPU resources left, so that's not the problem;
- I think all this started when I first activated the disk_cache mod in Apache, but I deactivated and is the same - every few days I see my sites are not running and I must restart the server.

I don't know what to say more. I know this is very blurred and I don't expect a sollution, but I'd like an advice from those experienced, so the only answer I'd like to hear, please, is to this question:

**- What would you investigate first if this would happen?**

Thank you!

PS. now the only error in Apache is this:
> Corrupt JPEG data: 2 extraneous bytes before marker 0xdb... have no idea what it means.

---

### Post by s_ø on 2010-03-30
Hi. I am bit unsure.
After restart everything works?
After a period of time php stops working? What is the error message?
I would start by looking in the /var/log/apache2/error.log

---

### Post by terazen on 2010-03-30
After you check your log files, can you verify that your html pages do actually work and aren't being cached?  Just clear the cache in your web browser, close the browser, and try to get to the site again.

Also check what time of day the problem starts to see if there a cronjob running at that time.  Is your php site something you did or a CMS that you installed?

---

### Post by wattaman on 2010-04-03
OK.

*s_ø*:
After restart, everything works. The Apache error log was that:
> [Tue Mar 30 09:56:31 2010] [error] server reached MaxClients setting, consider raising the MaxClients setting
 ... so I've raised the MaxClients to 150. Now my Apache settings look like this:
```
MaxKeepAliveRequests 150
KeepAliveTimeout 2
<IfModule mpm_prefork_module>
StartServers 5
MinSpareServers 5
MaxSpareServers 10
MaxClients          100
MaxRequestsPerChild  3000
</IfModule>
<IfModule mpm_worker_module>
    StartServers          5
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   3000
</IfModule>
```
My server has 2G memory and 2G cpu, should this be convenient? Let me know if you need other details.

*terazen*
I was thinking about cronjobs, and already deactivated some, just in case. I have some of those automatic feed posters for wordpress - if the crons are the problem, these are the leeches, I think.

Thank you both for helping me. I'm waiting for results now. I had the MaxClients set for 100 for a few days but yesterday freezed again (the server) so I'm guessing this is the issue; probably in weekend, when the traffic should be higher, 100 wasn't enough. Now is 150.
For my 2G memory and cpu server, what settings would you recommend, by the way. Apache, php, mysql (etc), if is not too much to write... just the most important settings, so I'll compare them with mine and eventually change a few lines.

Thank you again!

---

### Post by KB1JWQ on 2010-04-04
Something may be hanging sessions. Might see what they are and react accordingly.

---

### Post by wattaman on 2010-04-04
> **KB1JWQ said:**
> Something may be hanging sessions. Might see what they are and react accordingly.

I don't know what *hanging sessions* means. Care to explain or point me to where the problems is - if this will prove to be the problem.

---

### Post by terazen on 2010-04-06
Has the problem came back after the changes you made?

---

### Post by wattaman on 2010-04-06
> **terazen said:**
> Has the problem came back after the changes you made?

It appear so... however, until at least 2 weeks will pass I cannot tell for sure. The Apache seems to consume much more CPU, though it hasn't freezed in 2 days. I'll write again in one week, maybe will help others with my 'experiment'

---

### Post by wattaman on 2010-04-12
It appears that problem is solved, so I'll close this thread. I must open another one, unfortunately, since other issues appeared regarding (probably) Apache.
Thanks!

---

