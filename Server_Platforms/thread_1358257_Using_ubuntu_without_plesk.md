---
title: "Using ubuntu without plesk"
date: 2009-12-18
forum: Server Platforms
---

### Post by Btheone on 2009-12-18
I want to upgrade my ubuntu server which is running 8.04 to ubuntu 9.10 but plesk doesn't support at this time.

I'm wondering how much harder will it be to admin and use my server without using plesk, I would like to able to get stuck in to using the terminal. But i have only been using ubuntu for about 2months and im still learning alot. I know basic terminal commands.

I'm a little worried when it comes to adding stuff like, new domains, new ips and etc. I don't plan on adding any more though at the moment. It's also im a small server looking after about 4 small websites. And also security and other stuff like that.

Another bonus to not using plesk is it will save me about £6 per month. :-)

Do you think I would struggle or wouldn't have to much of a problem?

---

### Post by Jekshadow on 2009-12-21
I recommend trying Webmin, it is a web based admin panel (kind of like plesk), except open source and free.

---

### Post by Litachao on 2009-12-21
I found that administering without Plex wasn't too hard, especially since all the how-to's out there are for CLI anyways. I'd say give it a try if you're not on a production (or otherwise critical) server. 
A word of warning about updating to 9.10: I'm running 8.04 on a virtual server provided by a large web hoster. Updating to 8.10 wasn't a problem, system rebooted and ran without problems after that. Updating to 9.04 (necessary step to 9.10) however changed the config in a way that the vhost wouldn't boot anymore. Good for me my provider has daily backups. So, if you're in a similar situation make sure you're on the safe side.

---

### Post by BkkBonanza on 2009-12-21
If you want to get familiar with admin via terminal then I'd recommend that you try it out and learn as much as you can on your current 8.04 before going through an upgrade and forcing yourself to learn it under pressure. For each of the admin functions you think you'll need learn how to do them first.

Admin this way has it's own rewards and moves you up to a higher level of ability on your system but it isn't going to save you time. Will save you money though.

Is there a particular need you have for upgrading to 9.10? Or do you just feel it may be better to have a newer system? You are doing updates to 8.04 as you go now, right? You can keep it secure by keeping it up to date without needing to upgrade. 8.04 is a 5 year LTS version often used on servers for stability and will have updates coming until 13.04.

---

