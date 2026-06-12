---
title: "rkhunter can't figure out email reports"
date: 2008-02-22
forum: Security Discussions
---

### Post by starsheeep on 2008-02-22
hello !! :)

I'm trying to setup rkhunter scan daily a kubuntu 7.10 distro and report back to an email account
what i did so far is:

sudo apt-get install rkhunter sendEmail wget mailx 
sudo dpkg-reconfigure rkhunter

where i activated daily run and weekly updates

then i tried entering my email address in /etc/ and /etc/default/rkhunter

but im having difficulties understanding how those configuration files work along with the /etc/cron.daily/rkhunter binary, to set them up correctly

if anyone reading this, has an idea i would appreciate any help

edit: if i got it right, if i uncomment MAIL-ON-WARNING in rkhunter.conf the root and my account get mails that you can read with the mail app
in the same file i noticed a MAIL_CMD variable
ill try changing that in order to get the reports in my web mail account.

edit2: changed value in REPORT_EMAIL variable from the /etc/default/rkhunter file to "my@email.is" and i finally received the report (as spam and warnings only, pbly tweaking the MAIL_CMD variable could prevent the web mail classifying it as spam)

---

