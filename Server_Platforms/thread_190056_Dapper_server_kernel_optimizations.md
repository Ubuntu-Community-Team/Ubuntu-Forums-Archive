---
title: "Dapper server kernel optimizations"
date: 2006-06-05
forum: Server Platforms
---

### Post by ubuntu_demon on 2006-06-05
Does any one know in what way the new Dapper server kernel is optimized ? 

I know it's optimized for typical servers like webservers and database servers. But is it also optimized for samba and/or gateway ?

I have a pc with xubuntu Dapper which is my gateway and samba server. I also work on it sometimes using vnc. Would it make sense to install the linux-server package on it ? 

On a related note :
I've read that Debian Sarge is compliant with compliant with Carrier Grade Linux (CGL) 2.0.2

[http://trends.newsforge.com/article.pl?sid=06/06/05/1911255&from=rss](http://trends.newsforge.com/article.pl?sid=06/06/05/1911255&from=rss)
[http://en.wikipedia.org/wiki/Carrier_Grade_Linux](http://en.wikipedia.org/wiki/Carrier_Grade_Linux)

---

### Post by gimpologist on 2006-06-22
I would also like to know any details as well...anybody?

---

### Post by ubuntu_demon on 2006-06-28
I heard this kernel is more focused on transactions than on driver support. So I suppose it makes sense to install this kernel on a gateway / fileserver. I don't think it would be a major performance gain though.

strange that there is no linux-server-686 kernel available. I think the linux-server kernel is optimized for 686 because :

$uname -a 
hostname 2.6.15-25-server #1 SMP Wed Jun 14 11:52:05 UTC 2006 **i686** GNU/Linux

---

