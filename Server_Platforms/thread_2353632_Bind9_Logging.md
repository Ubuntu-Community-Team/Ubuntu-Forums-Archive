---
title: "Bind9 Logging"
date: 2017-02-23
forum: Server Platforms
---

### Post by boerak on 2017-02-23
Hi 

To learn more about Linux servers (used to be Win sys engineer) I tought I would start setting up some basic servers at home to replace my windows servers.
As I was trying to set up some logging for Bind9 I ran in to the following "issue":

I have scheduled **"rndc dumpdb -cache"** to be executed each 5 min so I can collect this information for logging purposes.

- Command I used to edit crontab: ** sudo crontab -u root -e ** (rndc dumpdb required root access)
- Content of crontab file: **"*/5 * * * * rndc dumpdb -cache"**

the dump file does not get updated each 5 minutes but it does get updated when I run the rndc dumpdb -cache command manually. 

Does someone have any idea whats going on? 
P.S.: first time using Bind9 and crontab.

Thanks!

---

### Post by darkod on 2017-02-23
I have never used rndc but first thing you should check is what is the full path of the command/file. The thing is that crontab always needs the full path even though you don't need it when running the same command manually.

And you don't need the -u root, when using sudo in front sudo crontab -e opens the root crontab by default.

For example, the sudo reboot is working manually but in crontab you would use /sbin/reboot.

---

### Post by boerak on 2017-02-23
Hi Darko 

Makes sense that it requires the full path. I will look in to this. 


Thanks for the reply!

---

