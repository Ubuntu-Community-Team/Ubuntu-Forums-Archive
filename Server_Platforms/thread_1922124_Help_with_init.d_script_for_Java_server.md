---
title: "Help with init.d script for Java server"
date: 2012-02-08
forum: Server Platforms
---

### Post by jacksonliam on 2012-02-08
Ubuntu Server 11.10

I'm really in over my head and I wondered if anyone could help me.

I need to run these lines at startup, presumably with init.d:
```

cd /home/liam/echonest/echoprint-server/solr/solr
java -Dsolr.solr.home=/home/liam/echonest/echoprint-server/solr/solr/solr/ -Djava.awt.headless=true -jar start.jar

```Obviously it would be useful if I could start/stop this too
They need to be run before ttserver, which is started using this, so I assume the script would need a lower number?:
```

update-rc.d ttservctl start 51 S .

```
Sigh... In windows I would place a shortcut to the exe in the startup folder...

If I just make a script called echonest with those two lines in, put it in init.d, made it excutable then did "update-rc.d echonest start 50 S ." would that work?

---

