---
title: "How to interpret the 'dates' in rkhunter.log??"
date: 2010-10-06
forum: Security
---

### Post by ken300 on 2010-10-06
Hi,

I've got rkhunter installed and regularly do scans immediately before & after updates & if I get warnings about 'file property updates' after the update I use 'rkhunter --propupd' to give me a clean run.

I'm about to setup a ubuntu computer for my nan, I want to enable automatic security updates so she doesn't have to do anything to keep her system secure. I was planning on running rkhunter when I go to her house (about once a month) and check the dates in the resulting rkhunter.log warnings with those in the var/log/apt/history.log to see if legitimate updates caused any rkhunter warnings. I've noticed though that the 'Current file modifiation time:' in the rkhunter.log warnings are incorrect.

My system seems to be about 15 days behind the actual date, I've now run rkhunter --propupd so I have no warnings but got this one off another forum post to show what I mean:

Current file modification time: 1283341157 (01-Sep-2010 06:39:17)

I believe that the '1283341157' is the time in some strange format and the date in brackets is what rkhunter thinks it might be in human format.

Does anyone know:
1) How to interpret the 'strange date format' (1283341157 in the line above)?

2) If there's a way of configuring the date in rkhunter so that they're correct in rkhunter.log?

3) If there's a better way of keeping her system up-to-date & secure, it's her first computer & she's 86 so I think setting up automatic security updates is the way to go, it'll be one less thing to overwhelm her!

Thanks,

---

### Post by robert_pectol on 2010-10-06
That's epoch time.  Unix calculates time as starting January 1, 1970 at 12:00.  Epoch time is how many seconds have elapsed since then.  So with a little math or a handy utility, you can easily convert it to a more, "human readable" format.  The datecalc command can do it but I prefer a more geeky alternative... with gawk!  For instance, running the following command with your string of numbers:

```

gawk 'BEGIN{print strftime("%h-%d-%Y %H:%M:%S",1283341157)}'

```

gives you:

```

Sep-01-2010 14:39:17

```

As to why rkhunter is not converting the date as expected, I don't know.  But the string of numbers you give does correspond with the correct converted date so not sure where you're getting your 15 day discrepancy.  The hours discrepancy is a timezone thing though.  Hope that helps.

---

### Post by ken300 on 2010-10-08
Thanks rob,

I wondered how to decipher the 'date'!

At the moment I've not got any warnings in rkhunter.log so i cut & pasted the line 'Current file modification time: 1283341157 (01-Sep-2010 06:39:17)' in my post above from another forum post.

Again thanks for the info!

---

