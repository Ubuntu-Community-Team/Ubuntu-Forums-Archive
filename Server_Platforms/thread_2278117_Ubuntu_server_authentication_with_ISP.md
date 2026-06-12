---
title: "Ubuntu server authentication with ISP"
date: 2015-05-14
forum: Server Platforms
---

### Post by argonx on 2015-05-14
Greetings,

I need help with authentication to my ISP network with ubuntu server, they require HTTP login, and so far I have done that by installing desktop environment and than login with some IE on ubuntu. 

I'm looking for command line to login (post data) to their page, and to keep connection alive, I have tried so far 
wget --user=xxxx --password=yyyyy [https://www.bhtelecom.ba/webtv_postavke.html](https://www.bhtelecom.ba/webtv_postavke.html)
Or
curl -d "userId=xxxx&pass=xxxx"
And did not have success so far

ISP is 
[https://www.bhtelecom.ba](https://www.bhtelecom.ba)

Thank You for any help 
BR

---

### Post by Ron_Greve on 2015-05-14
I think you need to post error details. Did it tell you the certificate was untrustworthy or something.

---

