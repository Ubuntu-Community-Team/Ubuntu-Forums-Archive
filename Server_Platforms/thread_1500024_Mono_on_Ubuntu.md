---
title: "Mono on Ubuntu"
date: 2010-06-02
forum: Server Platforms
---

### Post by srodia on 2010-06-02
I am running Ubuntu 9.10 Server. I am using using Apache to listen on port 80 and when I run 

sudo lsof -i tcp:8080

It shows something like

command  pid       user    FD   type     Device     Size/Off    Node   Name 
mono        16761  Me    4u       IPV4    52394        0t0          TCP   LocalHost:http-alt (Listen)

If I browse to [http://localhost:8080/default.aspx](http://localhost:8080/default.aspx) I am shown an aspx page that I wrote a while back as a test.

I want to use the server as a test for migrating some asp.net apps over to mono but I can't remember how to configure it and I don't even know where the default.aspx file that is being served to me is located.

How can I find where to put the aspx files I write?
and How can I further configure the app that is listening on port 8080?

---

