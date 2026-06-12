---
title: "Virtualization? Different settings for each site"
date: 2009-05-27
forum: Server Platforms
---

### Post by LepeKaname on 2009-05-27
I want to setup a test server so the final users can test changes to their web systems as a mirror of their production servers (somehow).

The problem is that their production servers have different versions, for example some have php4 others php5, etc.

Because they will not access so often to this test server, I don't think that having more than one server for this task is necessary. I thought in using vmware (or alike) but I will need to a complete OS for each one. 

Is there anyway I can setup this server so I can have a different setting (mainly apache2-php, mysql, tomcat, postgresql) for each domain? for example:

hostexample1.com        php4, mysql4
hostexample2.net        php5, mysql5

I have read that I could use php4 as cgi and php5 as module, but I'm afraid it would not be exactly the same setting from php4-cgi as with php4_mod ... right?

Any idea appreciated.

---

### Post by LepeKaname on 2009-05-27
Server virtualization is something that I'm not that familiar with... reading through several sites I found Linux-VServer ([http://linux-vserver.org](http://linux-vserver.org)) that was exactly what I was thinking of... (at least for now).

Linux-Vserver shares the same kernel and local files (linked) but creates a separate environment to setup your applications, users, etc. independently from each other, reaching a native performance. I just installed it and I will give it a try.


Other sources:
[http://linux-vserver.org/Installation_on_Ubuntu](http://linux-vserver.org/Installation_on_Ubuntu)
[http://en.wikipedia.org/wiki/Linux-VServer](http://en.wikipedia.org/wiki/Linux-VServer)
[http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines)

Closed.

---

