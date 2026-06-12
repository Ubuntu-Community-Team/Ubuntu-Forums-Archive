---
title: "How to confirm my system is clean"
date: 2012-01-19
forum: Security
---

### Post by clownius on 2012-01-19
Ive had an issue where my remotely hosted email service has been compomised and used to spam massive amounts.

Now i have had everything reset and it should be ok now.  What i was wondering is if there is a way i can give myself some piece of mind they didnt compromise it via my Kubuntu Desktop.

Im thinking it was 1000% more likely to be my 'doze laptop that they got through to be honest but until i can confirm this i would feel safer if someone knows a way to scan my Kubuntu System....

Edit:Kubuntu 11.10 64bit

---

### Post by cariboo on 2012-01-19
I'm assuming you meant Windows, when you wrote doze, if your windows computer checks out clean, I'd suggest your email account was compromised due to a weak, easily guessable password. Windows malware has no affect on your Ubuntu/Xubuntu/Lubuntu/Kubuntu/Edubuntu installation. If you really are worried, I'd suggest a clean install of both Windows and kubuntu.

---

### Post by clownius on 2012-01-19
> **cariboo907 said:**
> I'm assuming you meant Windows, when you wrote doze, if your windows computer checks out clean, I'd suggest your email account was compromised due to a weak, easily guessable password. Windows malware has no affect on your Ubuntu/Xubuntu/Lubuntu/Kubuntu/Edubuntu installation. If you really are worried, I'd suggest a clean install of both Windows and kubuntu.

The Windows 7 system is yet to be checked.  Its not with me and i got hit in the last 48 hours.  I suspect its at fault to be honest.

My hosting service just reset all the passwords for my email service and i dont want to log in and find it was actually a compromise on the Kubuntu machine (even though thats less likely by a long shot).

Was looking for some sort of peace of mind scan i can do on the Kubuntu machine before i use it to login.

Been looking at ClamAV.  Would this give you peace of mind if you were me?

---

### Post by dirtrider1 on 2012-01-19
Your account was most likely compromised through the email service it self like cariboo907 stated. With what little info you provided it would be impossible to tell you if your Kubuntu system is completely safe or not although its very unlikely Kubuntu was compromised. 

As far as security goes there is no "magic" scan or tool, security is an ongoing process not a product or single application, and Linux has a somewhat different process towards security. Windows maleware generally does not have any effect on Linux so ClamAV will do little good since it scans for Windows viruses. I highly recommend you read the Ubuntu security sticky and antivirus pages

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")  

[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")

---

### Post by clownius on 2012-01-19
> **dirtrider1 said:**
> Your account was most likely compromised through the email service it self like cariboo907 stated. With what little info you provided it would be impossible to tell you if your Kubuntu system is completely safe or not although its very unlikely Kubuntu was compromised. 

As far as security goes there is no "magic" scan or tool, security is an ongoing process not a product or single application, and Linux has a somewhat different process towards security. Windows maleware generally does not have any effect on Linux so ClamAV will do little good since it scans for Windows viruses. I highly recommend you read the Ubuntu security sticky and antivirus pages

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")  

[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")


Ok wasnt aware ClamAV only looked for windows viruses.  I feel somewhat less safe lol.  I agree totally with the very unlikely it was Kubuntu but as i said was looking for peace of mind.

Threads for me to read i guess and hope i understand them properly...
If i dont and it is the Kubuntu machine i guess im looking for a new email host.....

Edit:  Ok i seem to be secure as far as i can see already.  It never hurts to be a little parqanoid.  Thats most likely why this is the first time in years ive had any sort of intrusion ;)

Need to go kick that Win7 laptop a few times methinks.  See if a new AV on that turns up anything interesting.

---

### Post by bodhi.zazen on 2012-01-19
> **dirtrider1 said:**
>  Windows maleware generally does not have any effect on Linux

This part it true

> so ClamAV will do little good since it scans for Windows viruses.

That part is false. Clamav will do little good because Linux manages security differently, and as far as viruses are concerned, there are very few linux viruses and your system has been patched against the known viruses already, so it makes no sense to scan for them.

But ClamAV will ABSOLUTELY scan for Linux viruses, check the database

Go here : [http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

Enter "Linux" in the search box.

Linux security is different from windows security and you should check the stickies here.

---

### Post by dirtrider1 on 2012-01-19
> **bodhi.zazen said:**
> This part it true



That part is false. Clamav will do little good because Linux manages security differently, and as far as viruses are concerned, there are very few linux viruses and your system has been patched against the known viruses already, so it makes no sense to scan for them.

But ClamAV will ABSOLUTELY scan for Linux viruses, check the database

Go here : [http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

Enter "Linux" in the search box.

Linux security is different from windows security and you should check the stickies here.

Yes that is true I never said it did not, but besides scanning for Windows maleware in most cases there is no practical use of an AV on Linux and it will do little good as a solution for the OP's original problem.

---

### Post by mattxhand on 2012-01-19
Before this thread goes off-topic:

If the email account is with a third party  (say anyone like gmail, yahoo, etc.) and not hosted locally, you should be fine. Since the compromised account is not on your server, it has little to do with you.

Best advice I can give you is to change the password for the email account or drop it all together, change all of your other online/system passwords (regular password updates are a good idea anyhow :D) to something >14 characters with upper case, lower case, numbers and special characters. Finally, an AV scan wouldn't hurt but I'm not sure there is an application that can do it.

---

