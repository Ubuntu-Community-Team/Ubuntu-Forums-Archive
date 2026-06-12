---
title: "Set up server to send Text messages on status?"
date: 2008-04-25
forum: Server Platforms
---

### Post by FeraTech on 2008-04-25
Is it possible to set up a server to send text messages with errors or if power is interrupted? 

Obviously this would only be possible if the internet is still up but has anybody done this?

---

### Post by Rohan Kapoor on 2008-04-25
The concept would be amazing but I doubt it would be possible. (Text Messaging costs money to sender and reciever)

---

### Post by terazen on 2008-04-25
If you could get the errors into some sort of text file you could do something in a script like this.  Text messages are just regular emails basically.  My phone's address is something like [email]1234567890@vtext.com[/email], I forget what it is exactly.  Just send a text from your phone to your email address to find out what it is.

uuencode $file.txt $file.txt | mailx -s $file.txt [email]phonenumber@domain.com[/email]

Some phone companies charge stupidly high amounts for text messages like Darth mentioned.  Might want to have it send emails to your normal email account first to make sure your scripts work correctly and you don't end up with a huge phone bill. :-)

---

### Post by cdtech on 2008-04-28
I have my server setup to send text to my cell if my backup drive gets low. Using a cron job to cat the output of a grep'd df -H command after a backup then append to ">>" a text file "root/scripts/df_info.txt" using a script to monitor the size of the backup partition and email to my cell if it gets below a certain level "cat /root/scripts/df_info.txt | mail -s 'backup drive info' [email]mycellnumber@vtext.com[/email]".

---

### Post by MJN on 2008-04-29
I use SMS message to alert me of a whole variety of things from my server - unplanned reboots, low disk warnings, daily weather updates, Zoneminder CCTV motion alerts etc. I use the [MercurySMS](http://www.mercury.uk.net/mercurysms/) Perl script to send via the [VGSMail](http://www.vgsmail.com/) SMS gateway.
 
It is very cheap - 6.6p per message - and extremely reliable. Indeed it is generally more reliable than any single network as it utilises multiple carriers and monitors for delivery - if it didn't arrive it is rerouted via another carrier. This has never had to happen with me, and indeed I've not had a single failure in the 4 or so years I've been using it (you can track every message sent online). Highly recommended.
 
I have used free gateways in the past but found them to be a bit touch-and-go - your mileage may vary. I only send a messages when needed so the 6.6p message cost is insignificant.
 
Mathew

---

