---
title: "Ubuntu 9.10 - Facebook hacked"
date: 2010-02-14
forum: Security
---

### Post by Rocprof on 2010-02-14
It seems my ubuntu has got a virus or has been hacked. For some reason or another it has accessed my facebook and hotmail acount and is now sending out mail with a link to some false virus scanner. Any help here would be appreciated. Is there a good anti virus package available for the platform

Cheers all

---

### Post by CharlesA on 2010-02-14
Make sure you don't have the remote desktop enabled. Other then that, wipe the drive and reinstall, then change all yer passwords.

---

### Post by bruno9779 on 2010-02-14
It doesn't seem like your box has been cracked hacked or infected, it seems instead that you have installed some facebook app that is spamming using your data, that you have authorize it to use.

I had one of those last week

---

### Post by CharlesA on 2010-02-14
That wouldn't affect hotmail, would it?

---

### Post by bruno9779 on 2010-02-14
yes it would

If he registered to facebook using his hotmail account (as most likely he has)

---

### Post by Rocprof on 2010-02-14
Both my facebook and my hotmail account are sending messages does anyone know of a good anti virus or online scanner I can use to check my unit
and yes it was the hotmail account i used for facebook

---

### Post by CharlesA on 2010-02-14
You can try clamav, but you'll get a bunch of false positives. Maybe BitDefender, but I doubt it's yer machine that's the problem, probably a rogue app like bruno9779 said.

---

### Post by Rocprof on 2010-02-14
I havnt used any apps I only use face book as a form of communication with friends and family back home in SA so I dont think it can be a app

---

### Post by bruno9779 on 2010-02-14
Well, try to contain the possible rougue app thing anyway before reinstalling.

1. access your facebook account and remove all applications except the default ones.

2. change your facebook and hotmail passwords to strong ones, different from each other

3. get rid of, or change your hotmail and facebook secret question.

wait some hours, to see if any more messages are sent

---

### Post by 2hot6ft2 on 2010-02-14
About 2 weeks ago I either read or heard about something getting into facebook accounts and doing stuff like that. Then my Niece wanted to get on my laptop to do some things and I told her she could as long as she wasn't going to facebook. She wasn't.

Second link on a google search for "facebook infected"
[Facebook Hackers Refuse to Give Up]("http://news.softpedia.com/news/Facebook-Hackers-Refuse-to-Give-Up-119847.shtml")

---

### Post by OpSecShellshock on 2010-02-14
It's highly unlikely that malware on your local Ubuntu machine is responsible for this. It's probably your Hotmail and Facebook accounts that are compromised. Usually this is achieved through phishing, but it could also be a part of a data breach or a brute force conducted by someone who got your email address.

Things to consider:

Is your FB password the same as your Hotmail password? If so, it would be a good idea for them to be different. You'll have to change the passwords on both systems now anyway since your accounts might have been compromised. Make the passwords complex.

Does your Hotmail web page show full headers for sent messages? If so, you can compare the IP address it was sent from to your IP address and see if they match. Granted, the IP address it was sent from will probably be fake, but it will also be different than the one you have at home unless the intruder had the presence of mind to look for it and spoof it. Then you'll know it's not your local machine that is the problem.

In your email settings, is there anything in the signature field? I've seen situations where it looked like there was nothing there, but when I highlighted the whole text box and hit backspace, then saved the changes, the bizarre signature that was getting put in at the bottom of the user's messages went away.

In your FB privacy settings, is your profile set so that "anyone" can see everything you've put on there? You're just asking to get your info scraped when you do that, and if you have weak passwords or use the same password for multiple accounts you're in trouble.

---

### Post by bruno9779 on 2010-02-14
Have a read at this.

[https://www.facebook.com/topic.php?uid=2347471856&topic=10541](https://www.facebook.com/topic.php?uid=2347471856&topic=10541)

Many users have tried AV scans against this to no avail.

---

### Post by sgosnell on 2010-02-14
If you take any polls, answer questions about friends, or any of that stuff, you're using Facebook apps.  Notice that they all say that using them allows them to pull all your data.  Almost any of the crap on there could be doing it, and there are literally hundreds of them, popping up all the time.

---

### Post by bapoumba on 2010-02-14
I have edited the thread title, thanks for the suggestion bruno9779 :)

---

### Post by bruno9779 on 2010-02-14
:)

---

### Post by chriswyatt on 2010-02-14
I had an evil app on Twitter spamming people, at least I suspected one particular app.  I changed my password and removed that app and it stopped.

I have a contact on MSN and I'm always getting automated spam messages from him, this has been going on for, oh I dunno, 4 years!  I don't know whether he ever bothers to virus check his PC, it doesn't seem like it.

---

### Post by Richard1979 on 2010-02-14
I also doubt that your Ubuntu install has been hacked.
It's more likely some form of Web 2.0 worm.
Be careful what you click on.

---

