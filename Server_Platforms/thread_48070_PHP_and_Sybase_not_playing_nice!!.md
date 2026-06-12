---
title: "PHP and Sybase not playing nice!!"
date: 2005-07-11
forum: Server Platforms
---

### Post by nverhaar on 2005-07-11
I have Sybase running on an old NT server which is our main database server here at work, and we are trying to get PHP to talk to it on our ubuntu server.

Using the FreeTDS package we have been able to establish connections, make queries to the database and extract data and it works great!!

However, anytime we try to perform an INSERT or UPDATE to the database, things start to go haywire. Either we recieve a strange error message that appears as "Changed database context to aesd." or PHP thinks the query has completed successfully, however there has been no data written to the database.

I have done some rather extensive reading on this and still haven't been able to come any closer to solving this problem. From what I can gather, the problem is only affecting PHP 4.3.10. So either I need to downgrade to 4.3.9 or upgrade to 4.3.11 if possible.

If anyone has come across this problem in the past or has any suggestions, PLEASE feel free to let me know.

---

