---
title: "Temperature alarm"
date: 2006-06-22
forum: Server Platforms
---

### Post by tisse on 2006-06-22
Hi,

I have an Ubuntu server in the closet and I would like to have some sort of temperature alarm system running on it. I have successfully installed mbmon, postfix, mailx. Now I would like the server to mail my work-mail if the temp runs to high. The second thing that would be great is if it turned itself off if the temp got even higher.

Does anyone know if this is easy to do? I was thinking about a small cron job or do you have any other suggestion?

---

### Post by tisse on 2006-06-25
To close this thread.. I solved it myself by making a small script that reads the temp from the cpu and motherboard, if it's high the script mails me the temperatures and if it's too high the server will shutdown itself. I put the script as a cron job and it works great.

So now I've learnt how to write bash-scripts :)

---

