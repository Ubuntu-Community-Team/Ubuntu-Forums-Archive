---
title: "mysql pipe times out"
date: 2013-01-23
forum: Server Platforms
---

### Post by cellurl on 2013-01-23
I am trying to move data.
One way it works, the other way times out.

What forum would be best for mysql pipe questions?
I asked on mysql.com, they blame unix-pipes.
I asked on Amazon, they don't see any money in it...
I can't post on stackoverflow because they are dictators.

Anyway, thanks for Ubuntu. It is wonderful.


WORKS (Amazon->Ubuntu): 
mysqldump signs -h signs.c3x4aregvxxx.us-east-1.rds.amazonaws.com -P 3306 -u carterxxx2 -pxxxxxx | mysql -u root -pxxxxxx signs 


FAILS (Ubuntu->Amazon): 
mysqldump -u root -pxxxxxx signs signs40 | mysql signs -h signs.c3x4aregxxxx.us-east-1.rds.amazonaws.com -P 3306 -u carterxxx2 -pxxxxxx 


It moves some data, but not all of it. 
Each time its a different amount.
If I use files, it works, but the pipe doesn't...

---

