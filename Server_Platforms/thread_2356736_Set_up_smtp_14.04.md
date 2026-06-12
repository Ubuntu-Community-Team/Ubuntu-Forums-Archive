---
title: "Set up smtp 14.04"
date: 2017-03-26
forum: Server Platforms
---

### Post by jhboards on 2017-03-26
I have zero experience in setting up SMTP. I want to set up SMTP on Ubuntu Desktop 14.04 LTS so I will get an email to confirm a certain cron job has run ```
sudo fstrim -v /
``` I see many references to using Postfix as SMTP:

[https://help.ubuntu.com/lts/serverguide/postfix.html](https://help.ubuntu.com/lts/serverguide/postfix.html)

From the guide, I see that Postfix is quite involved in set up, especially for such a simple task as emailing a cron job. And I am assuming that setting up Postfix in Ubuntu Server is similar to doing so in Ubuntu Desktop, but I stand to be corrected.

Can someone refer advise the simplest way to do this. Thanks!

---

### Post by alexandari on 2017-03-28
Well yes postfix will do fine. There will be no specific settings after setting it up I think, you just need to add:

MAILTO=email@domain.com

in your crontab. After a job has run, it will send you an email with the output.

---

### Post by again? on 2017-03-29
This example worked for me to send mail on 16.04 desktop.
[https://ariandy1.wordpress.com/2014/04/08/linux-send-email-when-ip-address-changes/](https://ariandy1.wordpress.com/2014/04/08/linux-send-email-when-ip-address-changes/)

---

### Post by jhboards on 2017-03-31
> This example worked for me to send mail on 16.04 desktop.
[https://ariandy1.wordpress.com/2014/...dress-changes/]("https://ariandy1.wordpress.com/2014/04/08/linux-send-email-when-ip-address-changes/")

I was hoping for something a little simpler to set up. Maybe I'm just out of my league. :)

---

### Post by howefield on 2017-03-31
Thread moved to the "*Server Platforms*" forum, possibly a better fit even though you are running a desktop version.

---

### Post by jhboards on 2017-03-31
> Well yes postfix will do fine. There will be no specific settings after setting it up I think, you just need to add:

MAILTO=email@domain.com

in your crontab. After a job has run, it will send you an email with the output.                 

OK. Mr. Newbie here. I am hoping to not have to install more software to accomplish this. I am thinking there may be a way that is already burned into the OS that can do this.

But, if I go the Postfix route, would you advise how I can access the cron file? I set it up using a GUI: Gnome Schedule 2.1.1
Obviously, I need some hand holding........

---

### Post by jhboards on 2017-03-31
> Thread moved to the "*Server Platforms*" forum, possibly a better fit even though you are running a desktop version. 				

Understood. Thanks.

---

