---
title: "Port level monitoring"
date: 2012-12-21
forum: Server Platforms
---

### Post by ImJasonH on 2012-12-21
Hi all. I'm new here and new to Ubuntu, so forgive me if I have posted this in the wrong section or I'm asking questions that have an obvious answer.

What I want to do is monitor bandwidth usage at the port level on my VPS. (Ubuntu Server 12.04)
I have looked around for a few tools/tutorials on how to do this, but I'm not sure what software to use, or how to do it(I have came across Bandwidthd, Cacti and a few others).


If anyone could give me some names, links or tips it would be greatly appreciated.

Thanks all, and Merry Christmas
~ Jason.

---

### Post by chadk5utc on 2012-12-22
Hi Welcome,
There are a number of apps you can use for monitoring from the command line and a few log programs
ntop iftop and top can be ran on the command line  top will show all processes and which ones are using the most resources ntop and iftop will show bandwidth use by connection. I also suggest logwatch which will or can be configured to email you log reports and also suggest webalizer which will generate HTML pages of similar reports showing number of hits perpage and Country.
to install any of them
> sudo apt-get update
sudo apt-get install logwatch
sudo apt-get install iftop Etc Etc
If your interested here is a good link for more information
[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

---

### Post by ImJasonH on 2012-12-22
I gave webalizer a go but didn't like it too mucn.

I installed Cacti and so far like it, but I can't seem to find any templates for port level monitoring :\

A web interface that quickly shows the in, out and total monthly bandwidth for specific ports is what I'm looking for.
Would that be this: [http://forums.cacti.net/about36264.html](http://forums.cacti.net/about36264.html)

---

### Post by koenn on 2012-12-23
have a look at ntop

[http://www.ntop.org/products/ntop/](http://www.ntop.org/products/ntop/)

it's in the repos

---

