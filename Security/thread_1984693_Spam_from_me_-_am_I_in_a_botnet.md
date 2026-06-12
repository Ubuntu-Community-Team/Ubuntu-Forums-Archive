---
title: "Spam from me - am I in a botnet?"
date: 2012-05-22
forum: Security
---

### Post by Retor on 2012-05-22
Hi

I received this Message Delivery Failure email: [http://pastebin.com/JLAYbSSJ](http://pastebin.com/JLAYbSSJ)

It looks like it claims the original email came from me: 
[INDENT]From: name =?UTF-8?B?QmrDuHJuc2Vu?= <myemail@gmail.com>
[/INDENT]
When I googled the subject ("I just refuset to eat this.. @mail.com") it came up as a classic spam subject. 

When I checked Googles log for account access, it says that there were no logins at the time when the email was sent.  

The only service that is authorized to send email on my behalf, is Gnome: 

GNOME — Gmail, Google Calendar, Google Contacts, Google Docs, Google Docs, Google Docs [ Revoke Access ]

Is this a "Message Delivery Failure" spam email if such a thing exist? Or does my Ubuntubox have a trojan?

---

### Post by OpSecShellshock on 2012-05-22
If this is the only such message you've gotten, it most likely doesn't indicate that you have a spam bot. If you had a bot you'd be sending out many, many more messages. The options that leaves are that your Google account has been compromised (happens from time to time by a combination of third party breaches and brute forcing accounts) or the headers were spoofed on this message using your account name as the sender, which is pretty easy to do. I think the second situation is more likely, since the message came not from Google's servers, but from another domain entirely.

Something you can do is log into Gmail in a browser and check the settings, make sure your messages aren't set up to forward to anywhere else. I would say change your password no matter what, just as a precaution. Check your sent messages for anything unusual. Also check the spam folders on the web page itself, since a lot of desktop mail clients don't import those.

---

### Post by Retor on 2012-05-22
Ah, thanks! 

I'll have a look at my security settings, but your suggestion about using my name as sender seems the most plausible. For one thing I've never heard of the person in the to-field, the one that didn't get my email. 

Nice to know my name is used for pushing dubious ******, though. Finally I'll have my fame and fortune

---

