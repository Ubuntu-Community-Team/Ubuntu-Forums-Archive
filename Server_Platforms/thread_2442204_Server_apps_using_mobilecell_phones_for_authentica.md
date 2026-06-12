---
title: "Server apps using mobile/cell phones for authentication"
date: 2020-04-30
forum: Server Platforms
---

### Post by pengyou2 on 2020-04-30
I know this is a stretch posting this here, but I have posted it in webmaster forums and every other forum that I can think of.  I am creating a Moodle site for my Chinese students in Beijing.  If you lose/forget your password in Moodle, you need an email to recover it but most of my students do not have email.  They all have cell phones.  What does it take - in terms of hardware, software and networking to enable a webmail script (like Horde, Roundcube, etc) to do something like this?

---

### Post by LHammonds on 2020-05-01
The problem with setting an email destination to a phone is that they cannot reply "directly" because that would be an SMS-Text to nowhere.

You would have to configure it to send an email to their phone account (assuming their phone provider has email-2-sms conversion) and in the message you send them, you would need to include a link back to your site to complete the password change.  This also assumes they have web/internet access on the phone too.

The coding is possible for everything except the scenario where you cannot email them using an email-2-phone conversion if their carrier does not provide one.  For example, if your phone number 800-555-1234 and your carrier is AT&T, you can send an email to [EMAIL="8005551234@txt.att.net"]8005551234@txt.att.net[/EMAIL] and see if that email reaches the phone as a text message.

If you cannot email their phones where they receive it as txt, then I am not sure there is a way to do this.

Is their phone incapable of web browsing?  If they have a browser with Internet access, there are plenty of free mail sites they use such as gmail, yahoo, outlook, etc.

LHammonds

---

### Post by TheFu on 2020-05-01
Most cell phone providers in the world have an SMS gateway to accept SMS messages for their subscribers. Certainly, there are free email services in China that can be accessed using a smartphone.  qq.com, china.com comes to mind.

A quick google found this:
[LIST]
[*]@139.com - China Mobile. Just put the phone number as the username.
[*]@wo.cn - China Unicom
[*]@189.cn - China Telecom
[/LIST]
That's the big 3 cell plan providers.

---

### Post by pengyou2 on 2020-05-01
> **LHammonds said:**
> The problem with setting an email destination to a phone is that they cannot reply "directly" because that would be an SMS-Text to nowhere.

You would have to configure it to send an email to their phone account (assuming their phone provider has email-2-sms conversion) and in the message you send them, you would need to include a link back to your site to complete the password change.  This also assumes they have web/internet access on the phone too.

The coding is possible for everything except the scenario where you cannot email them using an email-2-phone conversion if their carrier does not provide one.  For example, if your phone number 800-555-1234 and your carrier is AT&T, you can send an email to [EMAIL="8005551234@txt.att.net"]8005551234@txt.att.net[/EMAIL] and see if that email reaches the phone as a text message.

If you cannot email their phones where they receive it as txt, then I am not sure there is a way to do this.

Is their phone incapable of web browsing?  If they have a browser with Internet access, there are plenty of free mail sites they use such as gmail, yahoo, outlook, etc.

LHammonds  Thank you for your very informative reply.  Their phones - even the cheapest ones - are capable of anything here, in large part because many of the games they play require extensive resources.  If I understand you correctly, the issue lies with the hosting service I will be using.  I am using aws - have sent them an email but not received an answer.  If I were to use China telecom's hosting service in HK, maybe it is more possible?  I cannot use a China domestic hosting service because I am not a Chinese citizen.

---

### Post by LHammonds on 2020-05-01
> **pengyou2 said:**
> Thank you for your very informative reply.  Their phones - even the cheapest ones - are capable of anything here, in large part because many of the games they play require extensive resources.  If I understand you correctly, the issue lies with the hosting service I will be using.  I am using aws - have sent them an email but not received an answer.  If I were to use China telecom's hosting service in HK, maybe it is more possible?  I cannot use a China domestic hosting service because I am not a Chinese citizen.
I was not talking about the hosting service of your web application, I am sure it supports sending out emails.

You need to find out if their phone numbers can receive txt message from an email...thus they need to know their email address which is specific to their phone carrier.  I gave you an example of what an AT&T email address would look like if that number was from AT&T.

Once you get a few of their phone numbers (with their associated sms email address...or you can do that research if they tell you who their carrier is) then you can use any 'ol email app to send a simple test email to their phone and see if that works.

That is the big hurdle I was trying to convey.  If there have a limited amount of carriers, you might be able to display that info during registration so that when signing up, they can put in their phone number and pick a dropdown saying what phone carrier they have (if they want validation sent to their phone) and even setup a test form to ensure it works.

LHammonds

---

