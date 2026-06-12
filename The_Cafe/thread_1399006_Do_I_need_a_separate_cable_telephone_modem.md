---
title: "Do I need a separate cable telephone modem?"
date: 2010-02-05
forum: The Cafe
---

### Post by Psumi on 2010-02-05
I have cable internet, but do I need a different kind of cable modem for cable telephone? Or can I use the same modem?

---

### Post by juancarlospaco on 2010-02-05
You can use VoIP :)
I dont think your modem is properly detected by Ubuntu *(any version)*.

---

### Post by Psumi on 2010-02-05
> **juancarlospaco said:**
> You can use VoIP :)
I dont think your modem is properly detected by Ubuntu *(any version)*.

The problem with VoIP is, I need to pay for it if I use a service like Skype or MagicJack (but not Ooma.) However, ooma is not something I'd consider until it has lasted for at least 5 years.

---

### Post by juancarlospaco on 2010-02-05
I was talking about Voip kinda Asterisk, not Skype and such...

---

### Post by Psumi on 2010-02-05
> **juancarlospaco said:**
> I was talking about Voip kinda Asterisk, not Skype and such...

So are there EASY TO READ/USE/IMPLEMENT instructions on how to use Asterisk to have a phone number that can make real calls to real people on their landline phones?

These instructions: [http://www.asterisk.org/docs](http://www.asterisk.org/docs)

Too many instructions, etc.

These instructions: [https://wiki.ubuntu.com/AsteriskOnUbuntu](https://wiki.ubuntu.com/AsteriskOnUbuntu)

haven't been updated for karmic.

---

### Post by juancarlospaco on 2010-02-05
Search for a ready-to-deploy VM if you dont want to learn...

---

### Post by ghostborg on 2010-02-05
[http://revision3.com/systm]("http://revision3.com/systm")
An old show about Asterisk, Sytm Episode 5 with Kevin Rose.
It's revision3.com under archived shows.

My 2 cents:
I have been using Vonage Unlimited $24/month for 5+ years after the Government gets done with taxes it's about $33/month.
The biggest problem is keeping your phone number or switching because its a pain to update everything. With a family it makes it difficult to just go Cell.

A friend of mine uses ooma he got from Costco.

FYI if you drop your land-line check with services like Alarm,Directv if compatible if you use pay-tv. AT&T requires a phone subscription if you want their DSL service, you would probably do a package deal anyway.

---

### Post by forrestcupp on 2010-02-05
I'm pretty sure that cable phone is just voip that is offered by your cable company using your current internet connection.  If you get it through your cable company, they will provide whatever hardware you need.  It's like their own version of Vonage.

If that's not what you're talking about, I don't know what you mean by "cable phone".

---

### Post by TBABill on 2010-02-05
Hopefully I can clarify for you. Your cable modem is a single modem with its own MAC address so the main router for the cable company knows how to communicate with your home modem. When you purchase voice phone from a cable company it is normally provided over a second modem, but that second modem is contained within the same housing as your Internet modem. You can search the Motorolla site for examples of Internet/phone modems.
 
That modem normally must be provided by the cable company and is not generally available over the open market, unlike regular cable modems. 
 
If you purchased phone service through your cable provider you should have been given an appointment for a technician to bring the modem to the house and configure it to work both with your computer and with your inside telephone wiring. The house wiring for telephone is back-fed from the modem to a nearby walljack, or one is installed, so they can disconnect your wiring from the telephone provider's interface and reconnect you to your modem (the phone side of that modem). The ones I have seen have 2 telephone outputs, a "line 1" and a "line 1/2" in case you purchase 2 phone numbers.
 
This service is nothing like Vonage or other true Internet VOIP services. Yes it is voice over IP because, obviously, your modem has an IP address and your voice signal is digitized and communicates with the local phone switch over the cable network instead of phone lines. Once it arrives at the local phone switch it is on the PSTN (public switched telephone network). Never is that signal "over the Internet" like Vonage or others (assuming you are using a cable phone service like Cox or Comcast).
 
If you did not get this modem and someone to configure it, contact your provider. There are additional steps that the average homeowner will not know to take in order to get everything configured properly. There is work at your end that must be done in addition to provisioning the modem from the cable company end. If your cable modem does not have telephone outputs (regular phone jacks) on it, you are not yet equipped for telephone service as described.
 
If your service you purchased is similar to Vonage, please disregard. That's totally different but most cable companies (larger ones) do not sell that type of service. 
 
For what it's worth, cable phone service is nothing like Internet phone services like Vonage because it does not rely on the Internet for service capability or quality. Here in my area the local provider has a telephone switch that is connected to Verizon's access point to the PSTN via multiple DS-3 connections. I would suspect your provider is similar in configuration because Comcast, Cox and other major providers have paved the way for cable phone service from many companies to follow.

---

### Post by Psumi on 2010-02-05
Thanks everyone. Yes, I do need a separate cable modem, and apparently, it is included with my 14.99 USD/mo price.

---

### Post by sudoer541 on 2010-02-05
or you can just install ubuntu on a VM and keep windows as your main OS or install ubuntu as a secondary OS like I do.
This way you will avoid compatibility problems.

---

