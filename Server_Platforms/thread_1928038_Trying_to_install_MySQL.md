---
title: "Trying to install MySQL"
date: 2012-02-19
forum: Server Platforms
---

### Post by mike_abc on 2012-02-19
[SIZE=2]Hi there,

I am trying to install MySQL5 on Ubuntu 10.04. Synaptic gave me an error - something about broken packages (!?) - , so I tried downloading MySql from the website.

In the beginnining everything went well. Downloaded, untarred it, installed it to /usr/local[/SIZE]/ , [SIZE=2]made a link to the actual directory, ("ln -s mysql-version-so-and-so mysql" - dunno why I had to do this, but I did it, because the book says so) which contains the downloaded version (in /usr/local/), now there was one last thing to do: issue the (last) command : " ./configure".

Ubuntu terminal says : "-bash: ./configure: No such file or directory".

What now ?


Thanks,

Mike

[B]PS. If we're talking about broken Synaptic Package Manager files, is there anything to be done to correct this error ?
[/B]
[/SIZE]

---

### Post by nsnidanko on 2012-02-27
yes try running **apt-get install -f**, it will fix all broken stuff.

Please post log of what happens after you run **apt-get install mysql-server**

---

