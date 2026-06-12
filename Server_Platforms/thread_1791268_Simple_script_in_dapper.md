---
title: "Simple script in dapper"
date: 2011-06-26
forum: Server Platforms
---

### Post by Alan87i on 2011-06-26
Looking for some help writing a simple script  on my dapper server. 
I want the script to play a short 5 second wmv sound file. 
So I can tell another program to run the script. 

What player can or should I use 
and how can I set permissions on the file and script so my program has access to it . 
Total newb here . 
Thanks 
Allan

---

### Post by sanderd17 on 2011-06-26
Dapper has reached the end of life, so the repositories are taken offline and you can't install anything new. See this wiki page: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

But if you upgrade your server, you can install mpg123:
```

sudo apt-get install vorbis-tools mpg123

```

than use
```

ogg123 <filename>

```
to play an ogg file or
```

 mpg123 <filename>

```
to play an mp3 file

EDIT: for upgrading end of life releases, see this page: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Alan87i on 2011-06-26
Thanks Sanderd17 
mpg123 plays an pm3 file just fine . 
Allan

---

