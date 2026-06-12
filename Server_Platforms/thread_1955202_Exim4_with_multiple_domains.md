---
title: "Exim4 with multiple domains"
date: 2012-04-09
forum: Server Platforms
---

### Post by unimatrix on 2012-04-09
Ubuntu/Debian systems allow for a quick and easy configuration of Exim4 using the following command:
> dpkg-reconfigure exim4-config

I have a very basic problem. I want to use multiple domains (or as Exim calls it "system *mail names*"):
[IMG]http://i.imgur.com/tbbpS.png[/IMG]

As we can see it only allows you to enter one domain name:
[IMG]http://i.imgur.com/OWG5x.png[/IMG]


Is Exim really so limited that it can only handle one domain?
How can I send and receive emails from more than one domain?
Exim forces me to choose one, which works, but when I try to send emails from another domain the receiver will still receive it from the main domain. GMail for example will display that email was sent "via <main domain>".

---

