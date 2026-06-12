---
title: "Need some explanation about BIND9 cache"
date: 2015-11-08
forum: Server Platforms
---

### Post by Grigoriy on 2015-11-08
Hello!
                            
                            Cache of BIND is kinda of a "Black hole" for  me. I know about TTL and that it can be overridden. I know that there's  a way to dump cache into a file that could be viewed in a text editor.  But, still, lots of things are in the dark. I've read that once you  reboot, the cache is lost. Then why to build the cache from scratch each  time you turn on your computer? What, like BIND's building its cache  for a few hours when the server is on and then simply loose it? That  doesn't make sense. Why it can't be kept in a file or in a database? Is  it a limitation or something good? Unfortunately, I didn't find in books  or on the Internet clear information about all of this. So please  explain it to me in simple English OR just provide the links to the  relevant source of information.
P.S. I think I know the answer to my own question. I mean, normally you would have a production DNS server in some server  farm where it's very rarely happens when the DNS servers would be shut  down. Most likely queries' TTL's expire faster than that.

---

