---
title: "WGET Error"
date: 2013-09-08
forum: Server Platforms
---

### Post by mar1 on 2013-09-08
Hi,

I'm trying to use a cron job (wget, php and script using curl, etc.) to run module code in the front end. Everything works fine when visiting the url in my browser and the module runs fine updating the DB. However when I use wget or curl+script manually nothing seems to work.

Is there a reason for this? Why wouldn't wget and the url work the same as my browser?

the code requires no login or session and it's on the front end, I'm not worried about users or bots hitting it themselves as it will just initiate tasks which isn't a bad thing and actually relieve server load with more processing of tasks more frequently.

I have tried using wget with -O but when I look at the DB nothing changes, it only changes when I visit from a browser on the front end. I run wget from a linux terminal and although the output makes me thing it worked, I see no change in the DB which the script should update.

I closely inspected the output of wget and at a glance it looked like it was working, but when I look closer I see a discrepency. I dumped out a php date time to see and when I use browser it's real when I use wget it's old...how do I get it to run properly and not from cache?

Thanks.

PS. This is actually kind of weird, it's a multi-lingual site and it tries to store cookies. The output in wget and lynx suggests it is working...but the DB does not update at all.

---

### Post by TheFu on 2013-09-08
Javascript and ajax on that website?
Did you change the client signature?  Some websites block curl and wget - I do.

---

