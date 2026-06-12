---
title: "Postfix for failing drives/other system problems"
date: 2013-08-01
forum: Server Platforms
---

### Post by RobertKH on 2013-08-01
Can anyone help me out with setting up postfix for failing drives emails? I have read through the tutorials, however I seem to always get stuck on the email servers to use. So two things here. 1) can someone point me to an up to date guide? The one that I found was from back in 2006 and I am not so sure that this is still relevant. 2) someone direct me what to use for email servers. For example when it says [EMAIL="email@myemail.com"]email@myemail.com[/EMAIL] in multiple locations - should I be putting the same email in each one? Can I customize it to be coming from something fictional like [EMAIL="notification@myserver.com"]notification@myserver.com[/EMAIL]? or does that not work out so well and I need to use an actual smtp server in order to bounce my emails out and back? Does that make sense to anyone other than myself?

BTW glad to finally have this forum back up and running!

---

### Post by CharlesA on 2013-08-01
Check this out:
[http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing](http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing)

As far as other system notifications go, I've got apticron (for updates) and logwatch (for checking logs) running on my server.

---

### Post by RobertKH on 2013-08-03
Thanks for the link Charles. I will test this out and see how it works. Sorry for the late reply, it's been a busy week.

---

### Post by CharlesA on 2013-08-04
> **RobertKH said:**
> Thanks for the link Charles. I will test this out and see how it works. Sorry for the late reply, it's been a busy week.

No worries at all. I tried it out on another system, but ran into issues with smartd detecting the drives on my MegaRAID controller. It did work well for the single drives in the machine, though.

---

### Post by RobertKH on 2013-08-05
Well that makes sense. I started trying it but it would appear that I have to test each drive individually? What about the drives that I have in a mdadm raid? I was under the assumption that it wouldn't run SMART tests without stopping the array first. Is this the case here?

---

### Post by CharlesA on 2013-08-05
> **RobertKH said:**
> Well that makes sense. I started trying it but it would appear that I have to test each drive individually? What about the drives that I have in a mdadm raid? I was under the assumption that it wouldn't run SMART tests without stopping the array first. Is this the case here?

No. It'll check the SMART of the drives just fine when the array is assembled.

---

### Post by RobertKH on 2013-08-12
So let me ask you this. In these lines what is /dev/hd(a,b,c) ? Should that be replaced with my drives? Also where is says [email]admin@example.com[/email] I can just input my personal email address right? Started working on this last night and would like to get it finished. Just in case. 




# First (primary) ATA/IDE hard disk.  Monitor all attributes, enable
# automatic online data collection, automatic Attribute autosave, and
# start a short self-test every day between 2-3am, and a long self test
# Saturdays between 3-4am.
#/dev/hda -a -o on -S on -s (S/../.././02|L/../../6/03)

# Monitor SMART status, ATA Error Log, Self-test log, and track
# changes in all attributes except for attribute 194
#/dev/hdb -H -l error -l selftest -t -I 194 

# Monitor all attributes except normalized Temperature (usually 194),
# but track Temperature changes >= 4 Celsius, report Temperatures
# >= 45 Celsius and changes in Raw value of Reallocated_Sector_Ct (5).
# Send mail on SMART failures or when Temperature is >= 55 Celsius.
#/dev/hdc -a -I 194 -W 4,45,55 -R 5 -m [email]admin@example.com[/email]

---

### Post by RobertKH on 2013-08-13
Never mind the /dec/hdc comment. I don't have any IDE drives. So I suppose I should simply copy the lines for sda and use every drive path required for testing. I was going to use DEVICESCAN but I don't see where it will send me an email if there is a failure.

---

### Post by RobertKH on 2013-08-14
Anyone here setup postfix successfully? I have a dyndns account, but this is far from my field. From my understanding you have to have postfix setup prior to smartmontools. Is this true? Really would appreciate the help

---

### Post by RobertKH on 2013-08-14
I have used the same config as listed in the link provided by Charles, changed the email multiple times, and restarted smartmontools without it ever throwing an error in the syslogs. What am I doing wrong? The only thing I can figure is that I am messing up postfix for sending the email.

---

### Post by TheFu on 2013-08-16
> **RobertKH said:**
> Anyone here setup postfix successfully? I have a dyndns account, but this is far from my field. From my understanding you have to have postfix setup prior to smartmontools. Is this true? Really would appreciate the help

I run postfix for a few corporate email systems.
If you are at home, chances are that you'll need to setup a relay-host in the postfix conf to send email outside the machine. Your machine would be considered a "satellite" and you will want to rewrite the "FROM" to be your normal email account always.  You will not be able to receive emails, as almost every residential ISP blocks inbound SMTP traffic.

If you setup postfix as a stand-alone system, then you will be able to check the emailed output using a mail client on-that-mail - something like **Mail** or **elm** or **mutt** or **pine** would be my guess. These are CLI programs and the names may have changed slightly over the years.  Local email will be stored in mbox format.

It is possible to setup a main email box for your LAN and have all the other servers and desktops forward all email to that central server. That is a little easier than running an internet email server, but more complex than most home users would try.

Clear as mud?  Email isn't hard, but there are many moving parts that seem unrelated to running an email server.

---

