---
title: "Unable to login on microsoftonline.com"
date: 2016-06-04
forum: Windows
---

### Post by Zawfish on 2016-06-04
Yesterday without warning I was unable to login to microsoftonline.com. I have tried to use Firefox and Google Chrome. I can connect to other websites on both browsers. I have also tested my internet connection with a windows machine and here the login works. 
The message on Firefox is “Secure Connection Failed. The connection to the server was reset while the page was loading”. The message on Chrome is “This site can’t be reached.The connection was reset.”
I have also tried to update my system with sudo apt-get update and sudo apt-get upgrade.
What can be the reason for problem?
It is very important I get this solved, because I use microsoftonline.com for work. Otherwise I am forced to change to windows, and this will be a disaster for me.

Best regards
ZF

---

### Post by SeijiSensei on 2016-06-04
This doesn't seem to be an Ubuntu problem as I just connected to that site now from my Kubuntu 14.04. machine.

---

### Post by pfeiffep on 2016-06-04
I suggest checking your network connections - my effort resulted in [https://login.microsoftonline.com/](https://login.microsoftonline.com/)

---

### Post by howefield on 2016-06-04
Thread moved to the "*Windows*" forum.

---

### Post by Zawfish on 2016-06-04
> **SeijiSensei said:**
> This doesn't seem to be an Ubuntu problem as I just connected to that site now from my Kubuntu 14.04. machine.
I can connect to the site, but when I use my login and password, the site doesn&#8217;t respond, and I get the messages mentioned above.
I also tried Ubuntu on a USB stick on my machine. This was an effort to see if a new Ubuntu install would solve the problem, but it made no difference.


> **pfeiffep said:**
> I suggest checking your network connections - my effort resulted in [https://login.microsoftonline.com/](https://login.microsoftonline.com/)
I tried to test my connection with another machine with windows installed. It worked fine.
I don&#8217;t know any other ways to check my connection.

Best regards
ZF

---

### Post by SeijiSensei on 2016-06-04
Possibilities:

1) You are using something that blocks cookies and scripts on the Ubuntu machine like Ghostery or AdBlock.  Disable them and try again.

2) Microsoft may not enable logins from a non-Windows machine.  I can't test this since I have no accounts at Microsoft.  You could try installing a User-Agent spoofer in Firefox and telling microsoftonline.com that you are using a Windows browser.  I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") with the User-Agent string:
```
Mozilla/5.0 (Windows NT 6.1; rv:41.0) Gecko/20131011 Firefox/41.0
```
when I need to spoof my OS to remote sites like Netflix.

If you have a licensed copy of Windows available, you can install VirtualBox in Ubuntu, then create a virtual machine and install Windows into that.  I recommend using the installation procedure at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).

---

### Post by Zawfish on 2016-06-04
> **howefield said:**
> Thread moved to the "*Windows*" forum.
I need all the help I can get, and I don’t mean to criticize, but is my question related to Windows as a OS?

Best regards
ZF

---

### Post by howefield on 2016-06-04
> **Zawfish said:**
> I need all the help I can get, and I don&#8217;t mean to criticize, but is my question related to Windows as a OS?

Seems sensible enough to me that the best people to talk to about logging on to a Microsoft site might be other Windows users. In all other respects your Ubuntu installation appears to be working. SeijiSensei is giving you good advice, try it.

---

### Post by Zawfish on 2016-06-04
> **SeijiSensei said:**
> Possibilities:

1) .....

I have a clean Firefox and Google Chrome install with cookies and scripts enabled.

I will try your suggestion with UAControl and return with the result.

I hope to try with a windows install on Monday. I may be able to borrow a license from my company.

Thanks for your help
ZF

---

### Post by Irihapeti on 2016-06-04
I'm fairly sure we can rule out 2) I have an Office 365 account via my university, with a login through microsoftonline. I have no problem logging in with Firefox and the standard Ubuntu user agent string. (Just tested it.)

---

### Post by Zawfish on 2016-06-04
> **SeijiSensei said:**
> 
2) Microsoft may not enable logins from a non-Windows machine.  I can't test this since I have no accounts at Microsoft.  You could try installing a User-Agent spoofer in Firefox and telling microsoftonline.com that you are using a Windows browser.  I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") with the User-Agent string:
```
Mozilla/5.0 (Windows NT 6.1; rv:41.0) Gecko/20131011 Firefox/41.0
```
when I need to spoof my OS to remote sites like Netflix..

I tried to use UAControl with the string and also tried to block UA, but unfortunately no luck. Thanks for the tip anyway.

> **Irihapeti said:**
> I have an  Office 365 account via my university, with a login through  microsoftonline. I have no problem logging in with Firefox and the  standard Ubuntu user agent string. (Just tested it.)
Could there be a difference between 14.04 and 16.04? I think the problem is related to certificates in the secure connection, but it is weird that it affects both Firefox and Google Chrome.
I am very fond of 14.04 LTS and would like to wait some time before upgrading to 16.04. I am not afraid of making a complete reinstall of 14.04, but previously when I have had troubles, people has advised against it, because Ubuntu doesn’t get broken without reason. I didnt change or install any programs the same day the issue arised, but I may have accepted an update. I will try to find the log for the update.

Best regards
ZF

Edit: I found a log in var/log/apt/history.log. The log is dated 2. June. I am sure i was able to login to microsoftonline on 3. June.

---

### Post by Irihapeti on 2016-06-04
> **Zawfish said:**
> ...Could there be a difference between 14.04 and 16.04? I think the problem is related to certificates in the secure connection, but it is weird that it affects both Firefox and Google Chrome.

I am very fond of 14.04 LTS and would like to wait some time before upgrading to 16.04. I am not afraid of making a complete reinstall of 14.04, but previously when I have had troubles, people has advised against it, because Ubuntu doesn’t get broken without reason. I didnt change or install any programs the same day the issue arised, but I may have accepted an update. I will try to find the log for the update.

Best regards
ZF

Edit: I found a log in var/log/apt/history.log. The log is dated 2. June. I am sure i was able to login to microsoftonline on 3. June.

I was using the login last year, when I was running 14.04 and I have documents there dated from that time.

I doubt it's of much relevance, but in both cases I've been using Xubuntu.

---

### Post by Zawfish on 2016-06-05
I have done a complete reinstall and upgraded to 16.04. But it didn’t help.
The next step is to install windows on my machine.

Best regards
ZF

---

### Post by Zawfish on 2016-06-06
Unfortunately I was not able to get hold of a windows install today. I will try again later this week, and there are also other possibilities i need to investigate.

Best regards
ZF

---

### Post by Zawfish on 2016-06-07
As if by magic the issue has disappeared. I made no changes to either hardware or software, but now it works. Microsoftonline was actually not the only place where the issue appeared. A large Danish portal called Borger.dk was also affected, and this is also solved.
I am convinced it has something to do with the secure connection in the browser. I talked to my ISP (a big Danish company) if they made any changes, but they denied. However, the person I talked to in the support didn't even know what Ubuntu was, so I wouldn't count on it.
Unfortunately I am not getting to the bottom of this issue, so it may reappear in the future.

  Best regards
ZF

---

