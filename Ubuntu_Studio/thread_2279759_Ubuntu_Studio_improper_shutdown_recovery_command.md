---
title: "Ubuntu Studio improper shutdown recovery command"
date: 2015-05-25
forum: Ubuntu Studio
---

### Post by Rex_Wilkinson on 2015-05-25
Hi I am new to Ubuntu and had the VLC player freeze on me , the only way I could get out of there was to power off , it now tells me something like "line 18 and 19 not found , " , ? , and I have no idea what line command to type to re-boot Ubuntu , I have used puppy 3 and 4 , and was able to reboot with commands like xorg wizard or xvesa , but nothing is working so far , can somebody tell me the right command , or is there a website or page I can go to to get a list of commands , ? , somebody please help , this is my second attempt to post this , the first attempt crashed my internet connection when I hit post , ?, and that was after a battle joining as I ended up with duplicate applications and it got very confusing , and took two days just to join ,?

---

### Post by jejeman on 2015-05-26
When do you get message "line 18 and 19 not found , " ?
You can shut down with
```
sudo shutdown -P now
```

---

### Post by Rex_Wilkinson on 2015-05-26
I powered off at the time , and now when trying to re-boot , I get that message , the reboot command I was looking for is ,, startx , thats all it was , so simple , yet so few seem to know this stuff about Linux

---

### Post by jejeman on 2015-05-26
Ha ha.
Well, there is a big difference in rebooting Ubuntu and restarting the X server. Ubuntu is not (just) X server. When one say "reboot" that means restarting OS or PC, not program or server. Programs or servers are just restarting.
On Ubuntu proper way to restart X server is by restarting the DM it uses. Command for restarting the DM and DM version depends on Ubuntu version.

---

### Post by Rex_Wilkinson on 2015-05-26
I am new to Linux and line command etc , I was introduced to it by a friend , who just happened to drop in yesterday , and he gave me the command , he also suggested xwin , but didn't need to try it as startx worked fine , I know my language is a bit vague , which comes from limited experience , but I thought I conveyed the problem fairly accurately , improper shutdown recovery ,?

---

### Post by jejeman on 2015-05-27
Are you trying to say that every time you start Ubuntu Studio you need to manually start X server?

---

