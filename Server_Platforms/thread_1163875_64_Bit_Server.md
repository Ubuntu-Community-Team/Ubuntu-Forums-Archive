---
title: "64 Bit Server???"
date: 2009-05-19
forum: Server Platforms
---

### Post by damo12 on 2009-05-19
I support a file server running Ubuntu server 8.04 32 bit version.  The server is only accessed by about 5 computers (Windows and Mac).  Would there be any advantage in upgrading the server to the 64 Bit version and if so how easy would it be to upgrade it?

The server is an i686 model so there would be no hardware issues.

Thanks is advance

---

### Post by Cheesemill on 2009-05-19
It's not possible to upgrade from a 32-bit to a 64-bit system, you would have to go for a clean install.

Cheesemill

---

### Post by smeerbartje on 2009-05-19
> **Cheesemill said:**
> It's not possible to upgrade from a 32-bit to a 64-bit system, you would have to go for a clean install.

Cheesemill

What are the advantages of running a 64 bit server edition instead of a 32 bit?

---

### Post by Cheesemill on 2009-05-19
64-bit will let you access more than 4GB of RAM, there are also slight speed gains to be had.

What processor do you have? i686 doesn't mean 64-bit. 

Cheesemill

---

### Post by smeerbartje on 2009-05-19
> **Cheesemill said:**
> 64-bit will let you access more than 4GB of RAM, there are also slight speed gains to be had.

What processor do you have? i686 doesn't mean 64-bit. 

Cheesemill

Thank you; I have an Intel Core2Duo E7300 2,66Ghz / 1066FSB. Will the 64 bit server edition run on it?

---

### Post by Cheesemill on 2009-05-19
According to [http://processorfinder.intel.com/](http://processorfinder.intel.com/)

Yes :)

---

### Post by scorp123 on 2009-05-19
> **Cheesemill said:**
> 64-bit will let you access more than 4GB of RAM With the "PAE" feature enabled a 32-bit kernel can access up to 64 GB RAM. Ubuntu Server (and many other 32-bit distros such as Fedora, RHEL, CentOS, SUSE ...) have "Physical Address Extension" (PAE) enabled.

[http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/](http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/)

Due to compatibility reasons (I have to use some closed source apps that only work on 32-bit Linux!) I have to use the "linux-server" kernel from Ubuntu Server. This allows me to see all of my 8 GB RAM. Sub-optimal, I know. But if for some reasons you can't use 64-bit then 32-bit+PAE is an OK solution too.

---

### Post by windependence on 2009-05-19
> **Cheesemill said:**
> 64-bit will let you access more than 4GB of RAM, there are also slight speed gains to be had.

What processor do you have? i686 doesn't mean 64-bit. 

Cheesemill

Quite the oppposite really. because the data path is now 64 bits instead of 32, there will be a slight SLOWDOWN in most cases going to 64 bit The only time this is an advantage is when you really need tons of RAM like one of my servers that has 16 GB. This is used for database access and needs the juice. Most other times, you are much better off staying with 32 bit.

-Tim

---

### Post by Vegan on 2009-05-19
How big of a MySQL database can I go with 32-bits before it chokes?

---

### Post by damo12 on 2009-05-20
Thanks for the advice, it has 1Gb of RAM and runs fine so I'll just stick with the 32 bit version.

---

### Post by smeerbartje on 2009-05-20
Is it really true that the 64 bit version is slower?

---

### Post by scorp123 on 2009-05-20
> **Vegan said:**
> How big of a MySQL database can I go with 32-bits before it chokes? That's impossible to answer as you didn't provide any details. If your tables are simple value pairs then you probably will be able to fill the entire memory without even noticing anything. On a pure 32-bit system that would be up to 4 GB RAM (in theory); with 32-bit+PAE that would be 4 GB per instance of up to 64 GB in total. But usually a MySQL database shouldn't grow so big. Database jobs that grow to such sizes are usually not encountered outside of corporate server rooms; and there it would most likely be Oracle or IBM's DB2 handling the job and not MySQL.

On the other hand if you do a lot of indexing, lookups, joining, sorting, views, and your table is overall badly designed (e.g. wrong field types and ranges) then your memory doesn't even need to be full and you will already notice bad slowdowns.

---

### Post by smeerbartje on 2009-05-20
> **scorp123 said:**
> That's impossible to answer as you didn't provide any details. If your tables are simple value pairs then you probably will be able to fill the entire memory without even noticing anything. On a pure 32-bit system that would be up to 4 GB RAM (in theory); with 32-bit+PAE that would be 4 GB per instance of up to 64 GB in total. But usually a MySQL database shouldn't grow so big. Database jobs that grow to such sizes are usually not encountered outside of corporate server rooms; and there it would most likely be Oracle or IBM's DB2 handling the job and not MySQL.

On the other hand if you do a lot of indexing, lookups, joining, sorting, views, and your table is overall badly designed (e.g. wrong field types and ranges) then your memory doesn't even need to be full and you will already notice bad slowdowns.

Thank you for your clear answer, however I'm not using any database at all :). I only use the server for home tasks like samba, sabnzbd, rtorrent, etc. Will it be of any use to run the 64 bit version instead of the 32 bit?

---

### Post by scorp123 on 2009-05-20
> **smeerbartje said:**
> Is it really true that the 64 bit version is slower? Depends on what you do. Early benchmarks that were done around 2006/2007 suggested that there was hardly any advantage in using a 64-bit OS. Recent benchmarks that I have seen now suggest that the situation has improved and depending on what you do or don't do with your system it may be worth using a 64-bit OS.

See here:

> "When it came to Linux gaming and exploring the 32-bit versus 64-bit performance with the AMD Phenom, in most cases Ubuntu x86_64 was slightly slower than the 32-bit version ..."

[http://www.phoronix.com/scan.php?page=article&item=998&num=1](http://www.phoronix.com/scan.php?page=article&item=998&num=1)

"Myths and facts about 64-bit Linux"
[http://forums.amd.com/devblog/blogpost.cfm?threadid=93648&catid=317](http://forums.amd.com/devblog/blogpost.cfm?threadid=93648&catid=317)

I suggest you read that, especially the "Benchmarks" section. As I understand it, 64-bit takes the lead when it comes to pure 64-bit arithmetics (I suppose you'd be using that if you do rendering a lot?) and media encoding (e.g. converting a few thousand files from one format to another).

But as the Phoronix test shows, 32-bit can still be faster in many areas because there is less overhead when compared to 64-bit.

I myself use 32-bit+PAE ... sub-optimal, but all my apps incl. the commercial closed-source ones that I have to use work.

---

### Post by scorp123 on 2009-05-20
> **smeerbartje said:**
> Thank you for your clear answer, however I'm not using any database at all :). I only use the server for home tasks like samba, sabnzbd, rtorrent, etc.  System Administration Rule No. #1:
Don't touch a running system. Don't fix it if it ain't broken.

So if you're happy with your system ... why touch it? :)

> **smeerbartje said:**
>  Will it be of any use to run the 64 bit version instead of the 32 bit?  I doubt it. 64-bit only really makes sense for you as home user if you are e.g. into rendering, e.g. via software packages such as "blender". 

Rendering movies can easily eat away gigabytes and gigabytes and gigabytes of memory. So if you're serious about movie rendering you will need RAM. Perverse amounts of RAM. And in that case 64-bit makes perfect sense, because with 64-bit your rendering program can eat away all the RAM it can get, there is no 4 GB limit. 

So if you want to render movies, edit really large videos in HD quality ... yes, then 64-bit is a "must have".

But for anything else I wouldn't bother and just stick to 32-bit, IMHO.

---

### Post by windependence on 2009-05-20
> I suggest you read that, especially the "Benchmarks" section. As I understand it, 64-bit takes the lead when it comes to pure 64-bit arithmetics (I suppose you'd be using that if you do rendering a lot?) and media encoding (e.g. converting a few thousand files from one format to another).

...And the kind of arithmetic they are talking about includes integers or other numbers that need a greater than 64 bit data path. Unless you are rendering on Maya in some render farm, you probably won't see much of a difference. I still run primarily 32 bit Linux and 64 bit FreeBSD because of what the machines do. Freebsd also seems to make better use of the 64 bit architecture. It's all about the right machine for the right job. In the OP's case, I don't think here will be any advantage to using 64 bit, and there are still some compatibility issues with certain applications.

-Tim

---

### Post by scorp123 on 2009-05-20
> **windependence said:**
>  and there are still some compatibility issues with certain applications.  Exactly.

---

### Post by smeerbartje on 2009-05-20
> **scorp123 said:**
> Exactly.

The only software I use is rtorrent, sabnzdb and vmware server. Are these packages compatible with the 64 bit edition?

---

### Post by scorp123 on 2009-05-21
> **smeerbartje said:**
> The only software I use is rtorrent, sabnzdb and vmware server. Are these packages compatible with the 64 bit edition? Does your server have more than 64 GB of RAM? Do you have several thousand users that might access your server simultaneously? Are you hosting several thousand virtual machines on your server? Does any of your virtual machines require more than 4 GB of RAM? 

If your answer to any of the above questions is "no" or "uhm, nope, not really" then you shouldn't bother as you gain no benefit whatsoever by switching to 64-bit.

---

### Post by smeerbartje on 2009-05-21
> **scorp123 said:**
> Does your server have more than 64 GB of RAM? Do you have several thousand users that might access your server simultaneously? Are you hosting several thousand virtual machines on your server? Does any of your virtual machines require more than 4 GB of RAM? 

If your answer to any of the above questions is "no" or "uhm, nope, not really" then you shouldn't bother as you gain no benefit whatsoever by switching to 64-bit.

Allright, clear answer. Thanks!

---

