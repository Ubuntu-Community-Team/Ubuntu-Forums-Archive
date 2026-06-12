---
title: "amavis Errors in Hardy Server"
date: 2008-10-20
forum: Server Platforms
---

### Post by igb on 2008-10-20
I have used amavisd-new for several years with very few problems. Over the last few months I have been getting errors like this in my logs and amavis stops:

```
ct 20 18:00:48 firewall amavis[7936]: (07936-03) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70, <GEN36> line 166. at /usr/sbin/amavisd-new line 2621, <GEN36> line 166.
Oct 20 18:00:48 firewall amavis[6983]: (06983-09) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70. at /usr/sbin/amavisd-new line 2621.
Oct 20 18:00:50 firewall amavis[7936]: (07936-04) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70. at /usr/sbin/amavisd-new line 2621.
Oct 20 18:02:08 firewall amavis[6983]: (06983-10) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70. at /usr/sbin/amavisd-new line 2621.
Oct 20 18:09:53 firewall amavis[6983]: (06983-11) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70. at /usr/sbin/amavisd-new line 2621.
Oct 20 18:09:54 firewall amavis[7936]: (07936-05) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70, <GEN46> line 166. at /usr/sbin/amavisd-new line 2621, <GEN46> line 166.
Oct 20 18:09:54 firewall amavis[6983]: (06983-12) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70. at /usr/sbin/amavisd-new line 2621.
Oct 20 18:09:54 firewall amavis[7936]: (07936-06) (!!)TROUBLE in check_mail: parts_decode_ext FAILED: run_command (open pipe): Can't fork at /usr/lib/perl/5.8/IO/File.pm line 70. at /usr/sbin/amavisd-new line 2621.
Oct 20 18:09:54 firewall amavis[6983]: (06983-12-2) (!!)TROUBLE in process_request: Can't create file /var/lib/amavis/tmp/amavis-20081020T180954-06983/email.txt: File exists at /usr/sbin/amavisd-new line 4856, <GEN159> line 85.
Oct 20 18:09:54 firewall amavis[7936]: (07936-06-2) (!!)TROUBLE in process_request: Can't create file /var/lib/amavis/tmp/amavis-20081020T180954-07936/email.txt: File exists at /usr/sbin/amavisd-new line 4856, <GEN51> line 80.

```

Deleting files in /var/lib/amavis/tmp works for a short while and then the problem happens again. Google throws up a few similar errors, but no solutions.

Anyone else had this problem?

Ian.

---

### Post by drejk on 2009-11-12
Hi,
i encountered the same error. Now it looks the problem is in the server having too little memory (command **free** shows that there is no swap neither physical memory left). 


I'm writing this just in case someone else googles this question...

Drejk

---

### Post by venol on 2011-04-14
> Hi,
i encountered the same error. Now it looks the problem is in the server having too little memory (command free shows that there is no swap neither physical memory left). 


I'm writing this just in case someone else googles this question...

Drejk

I think my server is ok. With 512 MB ram ubuntu server can send and receive email. But when I shutdown the server and turn on 3 days later, error detected.

what is problem?

---

### Post by agutierr on 2012-02-24
Hi all

Did someone solves this issue? I have the same problem with 4 GB of ram. When I receive a lot of emails, the memory quickly goes down, and I have this messages on the amavisd log. The problem is the queue postfix is increasing, and the memory goes down and down and down. When the load goes down, the messages starts to be delivered. I think that 4 GB of ram is still enough to run postfix+amavis and spamassassin...

Any ideas? 

Thanks.

---

