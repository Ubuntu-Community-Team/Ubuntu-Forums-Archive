---
title: "Fetchmail Daemon Interval"
date: 2017-06-20
forum: Server Platforms
---

### Post by howard14 on 2017-06-20
Hi. I am using fetchmail on 14.04 LTS. Fetchmail is run in Daemon mode, and is used to collect email from multiple accounts.

Now my problem is the interval that it is checking accounts. I have set the interval to 180 seconds, but typically the fetchmail is collecting mail at upwards of 15 minutes.

In the fetchmailrc file I have the lines

set daemon 180

And the majority of my poll commands are of the form:

poll mailserver protocol pop3 username "xxx" there with password "yyyy" is localuser here ssl

There are also lines like

poll mailserver protocol pop3 interval 2 username "xxx" there with password "yyyy" is localuser here ssl

Any ideas why the poll interval taking so long?

Thanks

---

### Post by howard14 on 2017-06-22
Hi - Fixed my own problem so will post the answer here in case anyone else has a similar problem.

There are two issues here.

Firstly my understanding of the interval (either the "fetchmail -d" option, or the "set daemon xxx" in fetchmailrc. These do not indicate the interval between collection from each email account in the fetchmailrc file, but is the "rest period" between cycles of fetchmail. Fetcmail does not collect email from the various accounts in parallel but fetches the email sequentially from each account listed in the fetchmailrc file.

Fetchmail is fairly quick however, so the long intervals were not normal for my situation. The fetchmail cycle was taking 12 minutes minimum followed by the 180 second interval. 15 mins in total. By stopping fetchmail running in daemon mode (sudo service fetchmail stop) and restarting in debug mode (sudo service fetchmail debug-run) I was able to spot the second issue...

Fetchmail was trying to deliver a large email to the local postfix account. However postfix had a message size restriction and was therefore rejecting the message that fetchmail was collecting. However, fetchmail keeps trying to collect the overly large email and therefore every cycle it was downloading the massive 30MB email from the POP account and trying to deliver. 

There are two ways to fix this. The first option is to set the fetchmail message size limit so that it does not try and download the message. This is fine but the email remains on the remote server and you may not see that it is hung there. The other option is to change the message size limit on the MTA (postfix) by editing the /etc/postfix/main.cf file and setting the message_size_limit to something bigger. I chose 35000000 bytes. 

Problem solved!

Thanks to those that viewed!

---

