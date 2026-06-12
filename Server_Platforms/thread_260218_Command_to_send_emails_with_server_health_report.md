---
title: "Command to send emails with server health report"
date: 2006-09-18
forum: Server Platforms
---

### Post by ssalman on 2006-09-18
Hi,

I'm setting up a server that I will be managing remotely most of the time. I want to setup a corn job to send a weekly report with key information about my server to my email address, so that I know that it is still alive and what it's latest IP address (using DSL with dynamic IP) so that I can shh into it.

In windows I used [Blat]("http://www.blat.net/"), what is the equivalent of that in linux?

Please note that blat does not require any mail server (like sendmail) to be installed, such as [this]("http://www.ubuntuforums.org/showthread.php?t=15128&highlight=send+email+command") solution. I pass my smpt address, account name, password in the command arguments. I'm trying to keep the server as lean as possible.

Thanks a bunch!!

---

### Post by etcpool on 2006-09-19
maybe, you can use monit


$sudo apt-get install monit

search for the doc on the internet, i saw one on howtoforge.

---

### Post by ssalman on 2006-09-19
Thanks etcpool, I will look it up now, but for the time being I found a simplistic solution in [this ]("http://www.linuxquestions.org/questions/showthread.php?t=204144&highlight=send+email+command")thread (post#7), its a short python script for sending text files via email, no email program/setup is required!

---

