---
title: "Someone needs to make a decent Download Manager for Linux"
date: 2009-04-03
forum: The Cafe
---

### Post by toejamfootball on 2009-04-03
All the current ones are pretty crappy....

I've tried JDownloader, KGet, Downloader for X, and none of them have worked well.

I need one that can Schedule the downloads to start at a specific time. I was using IDM, but it can't be intergrated with Firefox running in wine, and it's a PITA to copy paste 8 links seperately....

Anyone got any suggestions?

---

### Post by Eisenwinter on 2009-04-03
wget with cron, or with a shell script.

---

### Post by jmszr on 2009-04-03
toejamfootball,

   You might try the DownThemAll! Firefox Add-on.

   Edit: I don't know that it schedules.

---

### Post by Rokurosv on 2009-04-03
KGet is, IMO, the best gui download manager for Linux, others are kinda sucky, specially Gwget, it's the worst.

---

### Post by kpkeerthi on 2009-04-03
I use torrents (deluge command-line) for large downloads.

When torrents are not available, I use aria2c (another command-line download manager)

I prefer to use command line tools so they can be easily integrated into cron or at schedulers.

For adhoc downloads, I use DownThemAll Firefox add-on.

---

### Post by lakersforce on 2009-04-03
Like someone said above: wget (command-line tool default part of the GNU operating system).

---

### Post by pt123 on 2009-04-03
multiget is the best can do multipart downloads too
[http://multiget.sourceforge.net/](http://multiget.sourceforge.net/) and doesn't crash like the others

---

### Post by toejamfootball on 2009-04-03
> **kpkeerthi said:**
> I use torrents (deluge command-line) for large downloads.

When torrents are not available, I use aria2c (another command-line download manager)

I prefer to use command line tools so they can be easily integrated into cron or at schedulers.

For adhoc downloads, I use DownThemAll Firefox add-on.
How do you Schedule with this method?

---

### Post by kpkeerthi on 2009-04-03
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

[http://phorolinux.com/fast-download-files-with-aria2.html](http://phorolinux.com/fast-download-files-with-aria2.html)

---

### Post by toejamfootball on 2009-04-03
> **kpkeerthi said:**
> [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

[http://phorolinux.com/fast-download-files-with-aria2.html](http://phorolinux.com/fast-download-files-with-aria2.html)
Cool thanks man, I will check it out.

---

### Post by dixon on 2009-04-03
Try [fatrat](http://fatrat.dolezel.info/) ;)

---

### Post by Johnsie on 2009-04-03
I like download them all too. It's  true there is a distinct lack of choice of software on Linux though. You usually get an ok version of something and then some not so good versions. This is because of the lack of application developers for Linux and because differences between packaging systems make it harder for developers to get their products to all the different distros. With Windows on the other hand you usually get several good versions, some ok versions and alot junk but there is alot more choice.

If you want more apps you need to get more developers migrating to Linux.

---

### Post by toejamfootball on 2009-04-03
> **dixon said:**
> Try [fatrat](http://fatrat.dolezel.info/) ;)
Doesn't look like it can schedule.

---

### Post by adamlau on 2009-04-03
You can make nearly anything schedule with a proper crontab. And there is a decent downloader for Linux. One which Arch and Mandriva users embrace for their repo downloads at the fastest possible rate. One with enough switches to keep you busy learning what is best for your application. One which is widely considered to download the fastest with the least amount of resources. aria2.

---

### Post by cb951303 on 2009-04-03
a nice frontend for aria2 would be great but I agree there is no application like flashget in linux. I use downthemall for now.

---

### Post by toejamfootball on 2009-04-03
> **adamlau said:**
> You can make nearly anything schedule with a proper crontab. And there is a decent downloader for Linux. One which Arch and Mandriva users embrace for their repo downloads at the fastest possible rate. One with enough switches to keep you busy learning what is best for your application. One which is widely considered to download the fastest with the least amount of resources. aria2.
So is it possible to have a saved list of downloads in Aria2, which only downloads between the times you specify with crontab?

---

### Post by binbash on 2009-04-03
wget + cron is good but i agree linux needs an excellent DM application.

---

### Post by adamlau on 2009-04-03
> **toejamfootball said:**
> So is it possible to have a saved list of downloads in Aria2, which only downloads between the times you specify with crontab?
Yes. Absolutely. Versus any other downloader for Linux, there is very little aria2 cannot do.

---

### Post by toejamfootball on 2009-04-03
> **adamlau said:**
> Yes. Absolutely. Versus any other downloader for Linux, there is very little aria2 cannot do.
Great! I will have to learn how to do this then. *Goes of in search of tutorials...* :)

I got the GUI frontend for cron, because I'm only OK in CLI, I am happy to use CLI for the Aria part of it though I guess.

---

### Post by izak on 2009-06-01
[Flashget in wine]("http://ubuntuforums.org/showthread.php?p=7380441#post7380441") works well out of the box.

---

### Post by Viva on 2009-06-01
Downloader for X works fine for me.

---

