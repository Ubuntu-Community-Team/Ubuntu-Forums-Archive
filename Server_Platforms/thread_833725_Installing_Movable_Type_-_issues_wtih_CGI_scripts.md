---
title: "Installing Movable Type - issues wtih CGI scripts"
date: 2008-06-18
forum: Server Platforms
---

### Post by TheAddict on 2008-06-18
Okay, so I am trying to install Movable Type 4.1 onto my 7.10 LAMP server, and getting nowhere fast because what I'm reading is going over my head.

everything I read mentions the directory "/cgi-bin/" and scriptalias and the like. My issue is I can't find a directory anywhere on my system calls "cgi-bin/". Obviously first palce I looked was at the root of the file system, and no dice..

I'm completely confused and don't even know where to start...

I have added 
```

# To use CGI scripts outside /cgi-bin/:
#
AddHandler cgi-script .cgi
```

to my apache2.conf file, and it still simply parses the scripts as text... can anybody help me just a little bit?

---

