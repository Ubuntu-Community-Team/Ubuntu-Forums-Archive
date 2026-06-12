---
title: "Finances"
date: 2013-04-03
forum: The Cafe
---

### Post by capemayal on 2013-04-03
Not sure if this the right place for this.

I'm switching from W7 to Ubuntu.  I have a couple of questions, if anyone can help.

[LIST=1]
[*]I used Quicken.  One of the features I like is the ability to schedule a transaction on the first Wednesday of each month, etc.  However, none of the available titles in Ubuntu, including Kmymoney, GnuCash, etc, have this feature.  While monthly scheduling is possible, it's only for a particular date each month.
[*]Remember the milk - Milksync, the paid version for RTM, has a connector that allows entering new to-dos and editing others.  I can not find _any_ similar application within Ubuntu, even Evolution and TB.  I'm sure this is a RTM problem, but does anyone have any suggestion.  There was a TB pluging way back in TB2, but it's no longer available.  It's possible to read RTM in the applications but not make changes to them.  Gmail does have the compatibility, but I would like to use a dedicated email solution which has calendaring, etc.
[*]Regarding #2, does anyone know if the different email client files can be saved to UI or Dropbox for access on different computers - work, home, on the road, etc.
[/LIST]
Thanks in advance,
Al

---

### Post by oldfred on 2013-04-03
I installed Ubuntu in 2006, but kept XP until last year just for Quicken. I finally converted to KmyMoney, but it does not have all the features nor all my data from DOS quicken 20 years ago. I decided old data was not worth anything and I could live without all the features.

When dual booting XP I moved both Firefox & Thunderbird profiles into a shared NTFS data partition. I then had same bookmarks & email in both systems. Then when travelling I copy profile to my laptop and back when I return.

       [http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by schragge on 2013-04-03
Hopefully, the links in [post=12523641]this post[/post] may be of some help. There also were [two]("http://lwn.net/Articles/149383/") [installments]("http://lwn.net/Articles/153043/") about personal finance managers in the same series, but they are from 2005 with a [small follow-up]("http://lwn.net/Articles/347546/") in 2009. The comments on LWN are also worth reading.

---

### Post by capemayal on 2013-04-03
Thanks, I'll be checking out what I'm looking for.  As far as Kmymoney, I just have to pay all up to the next given payment date.   Easiest way I suppose would to set the reminder time far enough ahead to allow me to see those due.  I hope that makes sense.

As far as the email clients, I tried using U1, Dropbox and Google Drive.  However, Outlook's PST files can not be accessed that way.

I will try the other alternatives, and let everyone know.

Thanks,
Al

---

### Post by SophiaGrace46 on 2013-04-15
This is very precious and advanced information you provide. You have clear my all concepts and increase my decesion making ability.very appreciative to you.

---

### Post by mastablasta on 2013-04-16
> **capemayal said:**
> As far as the email clients, I tried using U1, Dropbox and Google Drive. However, Outlook's PST files can not be accessed that way.


why complicate? re: e-mail clients --> use SMTP mail. this means the e-mail will stay on server and won't get downloaded to your computer. meaning you can access it from other computers (web access) or from another mashcines (if their client is setup to read your account). 

i have gmail for example. i can access it from any computer via browser. i can also easilly access it from thunderbird from various maschines we have (eg. desktop, laptop, windows, linux...). since i have it set to SMPT all emails stay on server. nothing is downloaded to particular mashcine. well i could also make it that a copy get's downloaded so i could then work offiline.

same thing with hosted email on my domain. only there i only gave about 300 MB disk space to emails.

why would you need dropbox or any other cloud service? they are ment to store files. to be able to access data form various computers. but for emails it's far easier to simply use SMTP access.

re: rtm - will lIghtning do what you want to do?: [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

or do you need a more complex task manager (such as for projects and such)?

e.g. something like this: [http://taskcoach.org/](http://taskcoach.org/)

---

### Post by capemayal on 2013-04-16
I was under the impression that SMTP mail only stayed with the local client.   So, the sent email via SMTP will also be copied to the Gmail server?  Thanks, Al

---

### Post by forrestcupp on 2013-04-16
> **capemayal said:**
> Not sure if this the right place for this.

I'm switching from W7 to Ubuntu.  I have a couple of questions, if anyone can help.

[LIST=1]
[*]I used Quicken.  One of the features I like is the ability to schedule a transaction on the first Wednesday of each month, etc.  However, none of the available titles in Ubuntu, including Kmymoney, GnuCash, etc, have this feature.  While monthly scheduling is possible, it's only for a particular date each month.
[*]Remember the milk - Milksync, the paid version for RTM, has a connector that allows entering new to-dos and editing others.  I can not find _any_ similar application within Ubuntu, even Evolution and TB.  I'm sure this is a RTM problem, but does anyone have any suggestion.  There was a TB pluging way back in TB2, but it's no longer available.  It's possible to read RTM in the applications but not make changes to them.  Gmail does have the compatibility, but I would like to use a dedicated email solution which has calendaring, etc.
[*]Regarding #2, does anyone know if the different email client files can be saved to UI or Dropbox for access on different computers - work, home, on the road, etc.
[/LIST]
Thanks in advance,
Al
1. You could check out Acemoney Lite. It's free software for Windows that can do what you want, but it works pretty well in Wine. It's pretty good software, and it can import your quicken files. Note, the Lite version is free, but they also have a paid version. The only difference is that with the paid version, you can have multiple bank accounts in one file. If you're going to use Acemoney, make sure you test it out before you just get rid of what you're currently using.

3. What you want isn't SMTP, but IMAP. Setting it up in Dropbox, like you suggested, is just a nightmare waiting to happen. Just set up separate instances of Thunderbird on your computers, and set it up to access your email accounts via IMAP. IMAP leaves the messages on the server and works with them there, instead of downloading them to your local computer. If you have Gmail and your contacts saved with Google, there are Thunderbird plugins to sync your TB contacts with Google Contacts.

---

### Post by schragge on 2013-04-16
For Outlook PST files, there's an evolution plugin *pst-import* in package *evolution-plugins* and a set of command-line tools in package *pst-utils*.

---

### Post by mastablasta on 2013-04-17
> **forrestcupp said:**
> 3. What you want isn't SMTP, but IMAP. Setting it up in Dropbox, like you suggested, is just a nightmare waiting to happen. Just set up separate instances of Thunderbird on your computers, and set it up to access your email accounts via IMAP. IMAP leaves the messages on the server and works with them there, instead of downloading them to your local computer. If you have Gmail and your contacts saved with Google, there are Thunderbird plugins to sync your TB contacts with Google Contacts.

IMAP!!!! stupid me! yes IMAP is the functoon you are after. sorry for confusion. 

IMAP will provide offline copies only if you set it that way.[http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol](http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol)

---

### Post by forrestcupp on 2013-04-17
> **mastablasta said:**
> IMAP!!!! stupid me! yes IMAP is the functoon you are after. sorry for confusion. 

IMAP will provide offline copies only if you set it that way.[http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol](http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol)

I figured that's what you meant. We all make mistakes sometimes. :)

---

