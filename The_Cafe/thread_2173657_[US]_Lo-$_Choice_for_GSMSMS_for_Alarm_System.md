---
title: "[US] Lo-$ Choice for GSM/SMS for Alarm System?"
date: 2013-09-10
forum: The Cafe
---

### Post by 56es8lTI on 2013-09-10
So, I'm setting up an alarm system in my home and its dial-out function will probably be using a phone SIM card.  I'm trying to make this as inexpensive as I can.

The two choices I've had suggested are:

1:  Having it as a "second phone" on my regular mobile account.  I don't have a mobile, so that's out.

2:  Having it use a prepaid SIM card **with rollover**, which is apparently pretty rare.

Any bright suggestions will be appreciated! ;)

---

### Post by markbl on 2013-09-11
For my custom home alarm system I just send an email to a email/SMS gateway service. There are heaps of them and they are cheap and reliable.

---

### Post by tgalati4 on 2013-09-11
What is the model of the alarm system?  I have an old system with an analog phone dialer.  I just reprogrammed it with different beep tones depending on the fault/alarm condition.  I am assuming that you want to remove your analog land line and replace it with a second cell phone?  If you have any pc's in the house running 24/7 as a server, you could install a modem card to receive the call and then run a script when a call comes in to send an email/SMS/text message to your cell phone.

An alternative it to rewire the alarm's dry contacts into an Arduino or Raspberry Pi and use that to send the text message.

---

### Post by Kevin_Arnold on 2013-09-11
Depending on what exactly you are wanting to do, Ting.com can get you some dirt cheap cell service for small stuff like this.

---

### Post by sandyd on 2013-09-11
> **56es8lTI said:**
> So, I'm setting up an alarm system in my home and its dial-out function will probably be using a phone SIM card.  I'm trying to make this as inexpensive as I can.

The two choices I've had suggested are:

1:  Having it as a "second phone" on my regular mobile account.  I don't have a mobile, so that's out.

2:  Having it use a prepaid SIM card **with rollover**, which is apparently pretty rare.

Any bright suggestions will be appreciated! ;)

some phone providers actually have a address where you can send email to. Email that is sent there arrives on your phone as a txt message

---

### Post by markbl on 2013-09-11
> **tgalati4 said:**
> 
An alternative it to rewire the alarm's dry contacts into an Arduino or Raspberry Pi and use that to send the text message.
Well I just assumed the OP had replaced his alarm box with something that ran Ubuntu (e.g. Beaglebone Black), else why is he asking/posting here in these forums?

My alarm system is running on a Raspberry Pi (although that runs Raspian, i.e. essentially Debian) with a PiFace board which I have wired all the PIR and detector inputs into.

---

### Post by Paco_Wilson on 2013-09-16
1. If it's just dial out, you may connect it to traditional fixed phone line. You still can use the phone, when the alarm system is working.
Majority of GSM alarm system are supporting both SIM card and fixed phone line.

[http://www.hkvstar.com/pdf/g60.pdf](http://www.hkvstar.com/pdf/g60.pdf)

2. Buy a prepaid SIM card and insert it into GSM alarm system, making sure the SIM is activated and regularly to check the fee for keeping it active.

> **56es8lTI said:**
> So, I'm setting up an alarm system in my home and its dial-out function will probably be using a phone SIM card.  I'm trying to make this as inexpensive as I can.

The two choices I've had suggested are:

1:  Having it as a "second phone" on my regular mobile account.  I don't have a mobile, so that's out.

2:  Having it use a prepaid SIM card **with rollover**, which is apparently pretty rare.

Any bright suggestions will be appreciated! ;)

---

