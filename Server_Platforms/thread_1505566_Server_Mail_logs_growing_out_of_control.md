---
title: "Server Mail logs growing out of control"
date: 2010-06-09
forum: Server Platforms
---

### Post by itsbrink on 2010-06-09
for some reason logrotate or whatever it is that rotates the logs
doesn't seem to be working. I've read everything I can find on this
but I'm still baffled.

my old server ( feisty ver 7 ) used to automatically rotate the mail logs
automatically every morning.

I'm not sure if something disabled log rotation or if I've installed something
that broke it.   

 if I run logrotate -dfv /etc/logrotate.conf

the program runs and does something but it's not rotating and starting a 
new mail.log.

 what am I missing ?

much thanks.

-Ron

---

### Post by volkswagner on 2010-06-09
Check to see if anacron entry is located.

See [my thread here]("http://ubuntuforums.org/showpost.php?p=9285888&postcount=4"), or you may need to offer more info.

---

