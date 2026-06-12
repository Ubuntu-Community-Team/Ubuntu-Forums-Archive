---
title: "APT-CACHER [502 error]"
date: 2010-08-27
forum: Server Platforms
---

### Post by thiefofwisdom on 2010-08-27
Hi Guys!
Im new to this forum. I just killed my windows yesterday and im having a  great time building (starting.. its a long shot) a cluster.
Well.. my first attempt was to build a repository, once my connection sux hard and i have to update so many machines. Well... i choose the APT-CACHER to do the job. It was almost to easy to configure on my server...... also to import the packages that i already had.... 

But....

I'm getting a weird error and i just couldn't Google the answer...
When i try to get some packages, i get this error :

```
W: Failed to fetch http://192.168.1.102:3142/apt-cacher/br.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.6.6-1ubuntu4_all.deb
  502  apt-cacher: libcurl error: Failed connect to br.archive.ubuntu.com:80; Operation now in progress
W: Failed to fetch http://192.168.1.102:3142/apt-cacher/br.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.6.6-1ubuntu4_i386.deb
  502  apt-cacher: libcurl error: Failed connect to br.archive.ubuntu.com:80; Operation now in progress
W: Failed to fetch http://192.168.1.102:3142/apt-cacher/br.archive.ubuntu.com/ubuntu/pool/main/p/pidgin-libnotify/pidgin-libnotify_0.14-1ubuntu14_i386.deb
  502  apt-cacher: libcurl error: Failed connect to br.archive.ubuntu.com:80; Operation now in progress

```
The weird thing is that just some packages give me that error... i got the error getting the pidgin and some web packs... other stuff worked fine with no errors.
I followed this tutorial : [http://wiki.ubuntu-br.org/apt-cacher](http://wiki.ubuntu-br.org/apt-cacher)

I did notice that a bunch a ppl have the same issue... but i could only find posts that were from 2008 and all with no answer that i could understand.
Please give me a hand on the issue.
I'm using the latest version of the Ubuntu (Server for the server and Desktop for the clients) and also the latest version of apt-cacher.

Thanks!

---

### Post by Lars Noodén on 2010-08-29
HTTP Status codes are defined in [RFC 2616](http://tools.ietf.org/html/rfc2616) and code [502](http://tools.ietf.org/html/rfc2616#section-10.5.3) means trouble connecting from the proxy to the server (in this case the repository).

Can you reach the server you point to, br.archive.ubuntu.com with other tools?
If yes, then can you load manually with a web browser one of the packages, such as the first one in your log example above?
What about another repository?

 [http://br.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.6.6-1ubuntu4_all.deb](http://br.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.6.6-1ubuntu4_all.deb)



 When I use apt-cacher, I prefer to add it to [apt.conf](https://help.ubuntu.com/community/Apt-Cacher-Server#Use as a proxy to APT), but the result is the same as modifying sources.list.

---

### Post by christofoo on 2011-01-19
I had exactly the same problem. I checked /var/log/apt-cacher/error.log and found:

Tue Jan 18 23:26:47 2011|error [3468]: Unable to create libcurl socket /data/apt-cacher/libcurl.socket: Permission denied at /usr/sbin/apt-cacher line 1158.

Sure enough, the folder /data/apt-cacher/ was owned by root without write access for others. (I having changed the dir in the apt-cacher config.) Fixed it with:

chown www-data:www-data /data/apt-cacher

---

