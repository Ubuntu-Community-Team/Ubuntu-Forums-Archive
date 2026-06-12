---
title: "Apache 2.4 needs much more of resources"
date: 2012-06-20
forum: Server Platforms
---

### Post by A2llex on 2012-06-20
Hi,
i thought the new Apache 2.4 will take less of memory, but unfortunately it's not true.
over 800M only for Apache.

do you have any recommendations how to avoid taking so much resources?
I'll try to open some apache modules such as mem cache etc.

---

### Post by A2llex on 2012-06-20
i need your advice, i got 512M ram more, and now Apache2 sucks even this.

what should i do?

---

### Post by SeijiSensei on 2012-06-20
First, you do have swap enabled, right, either in a separate partition or in a swapfile?  If not, follow [these instructions](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/) to create and activate a swap file in the filesystem.  (Note that the commands in that article assume you're running as root; use sudo in front the commands instead.)

Were you running apache 2.2 before and only now upgraded to 2.4?  If so, presumably you didn't have this problem before?

Perhaps you have too many "children" defined. What values do you have in the "<IfModule mpm_prefork_module>" stanza in /etc/apache2/apache2.conf?  On my vanilla 2.2 installation I have these settings:

```

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

```

Those should be plenty for a normal server.

---

### Post by A2llex on 2012-06-20
> **SeijiSensei said:**
> First, you do have swap enabled, right, either in a separate partition or in a swapfile?  If not, follow [these instructions]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") to create and activate a swap file in the filesystem.  (Note that the commands in that article assume you're running as root; use sudo in front the commands instead.)

Were you running apache 2.2 before and only now upgraded to 2.4?  If so, presumably you didn't have this problem before?

Perhaps you have too many "children" defined. What values do you have in the "<IfModule mpm_prefork_module>" stanza in /etc/apache2/apache2.conf?  On my vanilla 2.2 installation I have these settings:

```

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

```Those should be plenty for a normal server.

as a separate partition.

and CPU is now 100% :O
idk but, looks like sites works pretty well.

Maybe apache now uses full potential of resources? 
there is about 30M ram always left. but CPU, 100% ? heh.

and mpm_prefork i have the same values.

---

### Post by SeijiSensei on 2012-06-20
If you run top, is apache the clear CPU hog?  Maybe there's something else that is the problem.  

On one of my virtual servers running 2.2, the parent process is using ~ 50 MB and the children each need about 13.  Even with 18 children at the moment, that still comes to less than 300 MB.

I've run Apache servers for years (though not yet 2.4) on machines as weak as old i386 boxes.  I can't recall a time when it pushed the CPU to 100% or ate all the available memory.

Are you running things like mod_perl with complex scripts?  Cgi-bin applications?

Linux will always use nearly all the available memory, though if you look at the "cached" figure that top reports all that is disk caching.  On my server caching currently runs about 30% of the total memory in use. Running more applications will reduce the amount of cache available as needed.

100% CPU is a different story.

---

### Post by A2llex on 2012-06-21
> **SeijiSensei said:**
> If you run top, is apache the clear CPU hog?  Maybe there's something else that is the problem.  

On one of my virtual servers running 2.2, the parent process is using ~ 50 MB and the children each need about 13.  Even with 18 children at the moment, that still comes to less than 300 MB.

I've run Apache servers for years (though not yet 2.4) on machines as weak as old i386 boxes.  I can't recall a time when it pushed the CPU to 100% or ate all the available memory.

Are you running things like mod_perl with complex scripts?  Cgi-bin applications?

Linux will always use nearly all the available memory, though if you look at the "cached" figure that top reports all that is disk caching.  On my server caching currently runs about 30% of the total memory in use. Running more applications will reduce the amount of cache available as needed.

100% CPU is a different story.

well. i think this is solved.

it was because of Segmentation fault due to APC cache.

so, do not use APC cache! it's my recommendation.

And thank you buddy for your help.

---

### Post by SeijiSensei on 2012-06-21
Please go to the Thread Tools link at the top and mark it solved.

---

