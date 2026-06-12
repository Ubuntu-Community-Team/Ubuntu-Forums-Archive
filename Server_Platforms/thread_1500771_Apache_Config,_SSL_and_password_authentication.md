---
title: "Apache Config, SSL and password authentication"
date: 2010-06-03
forum: Server Platforms
---

### Post by asynchronous13 on 2010-06-03
Currently, all http requests are redirected to https.

I would like to have a 'secret' directory such that a group of users could have access to that directory, but NOT to the main directory.

For example, group A and group B.

[https://www.example.com/](https://www.example.com/)  - group A only
[https://www.example.com/secret](https://www.example.com/secret) - group B only

With my first attempts at this, group B *must* be given access to / to be able to connect. 

Any recommendations on how to set up Apache to achieve the results I described? preferably without needing two passwords.

---

