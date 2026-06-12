---
title: "Ubuntu &amp; Android - Any way to remotely send SMS?"
date: 2010-09-05
forum: The Cafe
---

### Post by allannk on 2010-09-05
Hello people

As the description says, I really could use some way to send SMS messages, but from my computer. 

I know there exists software, to do this from Windoze (e.g. PDANet), but I can't seem to get that working in Ubuntu, neither find any alternatives for Linux.

I don't have access to paid apps on the Android Market in my region, so commercial apps will be pointless from my point of view. 

Anyone know some way to do this? :)

Regards, 
-Allan

---

### Post by mendhak on 2010-09-05
Simplest way - install [Desktop SMS](http://sites.google.com/site/desktopsmsforandroid/en)

Another simple way - [EasySMS](http://www.androlib.com/android.application.org-fireblade-easysms-pwzx.aspx) which sets up a web server (?) on yourAndroid and you then use its web interface to send SMSs from your machine.

Then there's telnet - if you root your phone, you can install a telnet daemon on it.  You can then telnet to it from your PC, and send and sms using this command:

sms send <senderPhoneNumber> <textmessage>

---

### Post by allannk on 2010-09-05
Mendhak, thanks a lot. 

I actually had heard of DesktopSMS, but it didn't work when I tried it earlier. 
Now, however, it works like a charm :-)

Might want to use the root-method later on, but for now this will do. Thanks again

-Allan

---

