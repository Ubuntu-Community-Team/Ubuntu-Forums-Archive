---
title: "Apache url issue"
date: 2005-10-26
forum: Server Platforms
---

### Post by rthewissen on 2005-10-26
Hello,

I have to keep saying that I am really new to Linux and this is my 2nd day of running Ubuntu. 

Set up ubuntu (latest version) and am running apache 2 and interchange 5 for ecommerce.

I am able to open up the main page but when I click on a link to view a product, it attempts to go to the following url...

[http://localhost.localdomain/cgi-bin/ic/foundation/scan/st=db/co=yes/sf=category/se=Ladders/op=eq.html?id=DD594ALt](http://localhost.localdomain/cgi-bin/ic/foundation/scan/st=db/co=yes/sf=category/se=Ladders/op=eq.html?id=DD594ALt)


not if I replace the localhost.localdomain, then the page shows up.


Anyonw know what I need to do to have the server from trying to reference the localhost.localdomain ?


Thanks All !!!

---

### Post by Glut on 2005-10-26
This looks like it's a link problem, if you're not browsing from the server itself, then no link should include localhost. I'm not familiar with interchange, so if the link's on an interchange created page, you may need to read it's documentation to figure out what's going on.

---

