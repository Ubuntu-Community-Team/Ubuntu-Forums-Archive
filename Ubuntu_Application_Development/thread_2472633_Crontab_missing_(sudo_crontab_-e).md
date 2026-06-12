---
title: "Crontab missing (sudo crontab -e)"
date: 2022-03-07
forum: Ubuntu Application Development
---

### Post by chris53 on 2022-03-07
Hi there. 

I set up Crontab on Ubuntu 20.04 a month or two ago.    I have several scripts executing from it.    One job I set up requires administrative priv's,   It mounts/unmounts an external drive to do a system backup.   I set up another script which also mounts/unmounts an external drive 
and when I went to add this script to my  Crontab which requires administrative privs  by entering "sudo crontab -e" it brings up an blank page!?    I must be doing something wrong..  How could my crontab just disapear?   That makes no sense!! 

Can someone tell me what I am doing wrong?    Its been a while since I've touched my root crontab and I'm thinking I'm missing something.    I went to [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)  and looked to see what I am doing wrong and cant find the answer.  
When I enter "[COLOR=#333333][FONT=UbuntuMono]crontab -e" it is there but the other one "sudo contab -e" seems to have vanished.   Please tell me what I am doing wrong.   

Thanks,
Chris[/FONT][/COLOR]

---

### Post by chris53 on 2022-03-07
Nevermind...   I just re-created it.   I saw the timestamp on the empty crontab, looks like somehow I wiped it out.   Oh well, not much there.   No biggie.    Thanks

---

