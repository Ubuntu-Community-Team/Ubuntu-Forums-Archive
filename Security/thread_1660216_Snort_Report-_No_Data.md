---
title: "Snort Report- No Data???"
date: 2011-01-05
forum: Security
---

### Post by Vigh on 2011-01-05
Hi, I have successfully configured and installed snort, but snort report appears to be not logging any info, there is obviously a problem with my sql database config I guess. It just says No Data. Running in vmware virtual machine.

Regards
Vigh

---

### Post by bodhi.zazen on 2011-01-05
How did you test snort ?

What makes you think there is a problem with your mysql database ?

If you are using BASE, does it show a sensor ?

---

### Post by Vigh on 2011-01-08
Hi what actually is Base? I have tested snort by successfully initialising it from the terminal using the command provided in the Snort Installation guide. And it reports that it is processing packets. But no-data in snort-report, if you need any outputs just let me know.

---

### Post by bodhi.zazen on 2011-01-08
sounds as if snort is working then, you can test it by hitting it with something.

for information on base, see the snort sticky.

---

### Post by akajee on 2013-04-26
Hi,

I have SnortReport 1.3.3 and also have the No Data issue. I can see the traffic when running:
[SIZE=1]
sudo /usr/local/snort/bin/snort -u snort -g snort \[/SIZE]
[SIZE=1]-c /usr/local/snort/etc/snort.conf -i eth0

[SIZE=2]Has anyone managed to resolve the issue? I am new to Linux so I used this project to learn command line, navigation, and tasks, etc.. So please excuse my dummy questions :-).

Thanks in advance[/SIZE][/SIZE]

---

### Post by wildmanne39 on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

