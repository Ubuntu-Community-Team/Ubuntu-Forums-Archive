---
title: "Adding a specific mirror"
date: 2005-08-30
forum: Repositories &amp; Backports
---

### Post by Kyral on 2005-08-30
Got a stupid sounding question. My university has an Ubuntu Repo mirror (all the official ones). Now here is the stupid question. What would I add to my sources.list to make Apt use THAT mirror?

[http://mirror.clarkson.edu/pub/distributions/ubuntu/dists/](http://mirror.clarkson.edu/pub/distributions/ubuntu/dists/)

---

### Post by parktownprawn on 2005-09-01
I think that if you edit the file /etc/apt/sources.list and replace each occurence of

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) 

(you may have something slightly different like us.archive.ubuntu)  

with 

[http://mirror.clarkson.edu/pub/distributions/ubuntu/](http://mirror.clarkson.edu/pub/distributions/ubuntu/)

and run ```
sudo apt-get update
```

hopefully you should now  update from the clarkson mirror

---

