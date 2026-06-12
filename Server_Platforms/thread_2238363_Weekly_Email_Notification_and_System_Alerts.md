---
title: "Weekly Email Notification and System Alerts"
date: 2014-08-07
forum: Server Platforms
---

### Post by drexlock on 2014-08-07
I'm hoping the masses of Ubuntu Faithful can help out an Ubuntu Newbie with a unique to servers situation. 

I'm running an Ubuntu 14.04 Server at home providing some basic file sharing, VPN, Dynamic DNS and Media streaming for our house. It's run flawlessly so far but I'm thinking I want to take it a little farther. I want to setup an Email notification system that will email me once a week giving me a breakdown of the status of the server such as Up Time, UPS Status, Raid Arrays Status, Available Volume Capacity, etc as well as send me alerts for things that need my attention like if a drive in an array dies and needs to be replaced. 

I'm sure there is a tool or utility that can be setup to do this I just don't know where to look or what specifically to look for.

---

### Post by nerdtron on 2014-08-07
Better not to configure a whole email server just for that simple task. So I suggest you use the command line to send a email using an existing email account say gmail. [http://askubuntu.com/questions/12917/how-to-send-mail-from-the-command-line](http://askubuntu.com/questions/12917/how-to-send-mail-from-the-command-line)

Once you were able to use your account in gmail to send email, the next thing to do is to create a script that would collect the information you like, then save that info on a text file, and then send the file or text using your gmail account.

If you have problems on sending emails or writing the script, post them here.

---

### Post by TheFu on 2014-08-08
Logwatch?

---

### Post by nerdtron on 2014-08-10
+1 for Logwatch. Almost forgot about that one.

---

