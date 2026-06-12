---
title: "Trying to run sh progs at reboot"
date: 2010-09-13
forum: Server Platforms
---

### Post by wkdboi10 on 2010-09-13
Hi all,

I'm new here :P

Okay so im trying to do something which i've been told is very simple 

Okay now im wonder if I can add both bots to start up with the box,  incase of power failure, such as the other day where I was out of town  and bots were down for 3 days, could I somehow add it to the init.d  file.

Although i'd probably need to name each chatbot.sh different. 

Or can someone explain how to make a bot.d or something

Thanks

So first I run this command

sudo crontab -u sparks -e

Then open nano and add the "@reboot" line like so?

**Quote:**
25 8 * * * /etc/webmin/cron/tempdelete.pl #Delete Webmin temporary files
@reboot cd /home/budabot/; ./startall.sh;


Then open nano and make startall.sh and add?

**Quote:**
#!/bin/bash
#org bot
cd /home/budabot/0.6/
screen -S bot1 -L -d -m ./chatbot.sh

#alliance bot
cd byfour/budabot_0.6.6/
screen -S bot2 -L -d -m ./chatbot.sh


Is that correct or have I missed / forgot something

Also if I could somehow build a webpage so that if the progarm goes wrong someone can just reboot the program ?

Thanks alot

---

