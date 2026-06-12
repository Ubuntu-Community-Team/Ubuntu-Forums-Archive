---
title: "looking for a cheap voip/softphone"
date: 2012-09-27
forum: The Cafe
---

### Post by sona1111 on 2012-09-27
Hello, i came here to ask if anyone had tried any voip providers meant to be run primarily as a softphone. I plan to use either 3G/4G or wifi with a laptop running ubuntu to make and receive calls. I don't care very much about features, except caller id, which i assume is pretty much standard. I am looking for the cheapest available plan that has loosely limited or unlimited call length and no ads. (i don't see myself talking for more then 30 minutes at the most) And of course the app should run natively in ubuntu. 

Has anyone had time to try some of these? Thanks in advance for any input.

---

### Post by sona1111 on 2012-09-28
bump

---

### Post by sandyd on 2012-09-29
skype if you can make it work.
Has problems with some mics

---

### Post by Primefalcon on 2012-09-29
google voice?

free calls and sms to the us and canada and very cheap to the rest of the world.... 

comes with customized voice mail and whatever else [https://voice.google.com](https://voice.google.com)

---

### Post by HermanAB on 2012-09-30
The problem with VoIP and SIP is that it is no use unless the people that you want to talk to also use the same thing.  So, in general these days, Skype is best, since it started many years ago and now has many millions of users.

---

### Post by Lars Noodén on 2012-09-30
That's one more reason why open standards like SIP should be encouraged.  It is not mutually exclusive with other options which people may or may not have already installed.  Also, SIP has better sound quality so it is worth encouraging.

---

### Post by Docaltmed on 2012-09-30
I use diamondcard.us. They charge a per-minute fee with varying rates around the world, but because it's my second line, the costs come out to being far cheaper than paying a monthly flat fee. Even as a primary line, I would use it instead of my local carrier, if I didn't need the listing.

As an example, a 5-minute call in the U.S. just cost me $0.086.

I've never paid much for any call, even overseas (I mostly call cellphones in the U.K.).

And the previous poster was incorrect. I can call any phone number, whether or not they have SIP or not.

---

### Post by mips on 2012-09-30
> **HermanAB said:**
> The problem with VoIP and SIP is that it is no use unless the people that you want to talk to also use the same thing.

99.99% of SIP providers provide gateways/breakouts to normal telephone networks.

My understanding from the OPs post is that he would like to call 'normal' phone numbers from a softphone hence him mentioning lowest call charges as softphone-softphone is usually free.

---

### Post by sona1111 on 2012-09-30
i could never figure out google voice. it seems like it is not a phone plan but some kind of redirection service. 

diamondcard looks promising but the softphone is an exe file. did you have any luck using it with wine or do they have a native one available?

---

### Post by Lars Noodén on 2012-09-30
Can't you use Diamondcard with Ekiga or Jitsi?  Or am I misunderstanding the service they sell?

---

### Post by Scott Goodgame on 2012-09-30
You should really look into google voice, assuming you are in the us or canada. I use it on my laptop and bought a device called an obi100 for home. saves me around $30 a month for a home phone.

---

### Post by zerubbabel on 2012-10-15
> **Lars Noodén said:**
> Can't you use Diamondcard with Ekiga or Jitsi?  Or am I misunderstanding the service they sell?

I use Jitsi in combination with a SIP account provided by localphone.com, and I am very pleased with it. I pay 99 cents per month for a phone number, with caller-id, forwarding, voice mail, etc., and the cost for outgoing phone calls is very inexpensive -- $.005/minute for the USA, $.007/minute for Germany, etc. You can also send SMS text messages via their web interface, but so far Jitsi doesn't have a mechanism for sending or receiving SMS, as far as I know.

Besides SIP, Jitsi also supports almost every messaging protocol there is, except Skype, as well as video and desktop sharing, so it really is the best open-source alternative to Skype, and is more secure than Skype. Recently they added the Opus codec, which provides the clearest calls I've ever enjoyed on a softphone. 

(Opus is only supported in the nightly builds, however, but will be included in the next stable release, which is just around the corner. Having said that, I have found the nightly builds to be quite stable. That's all I use.)

Hope this is helpful.

---

### Post by Scott Goodgame on 2012-10-15
That service sounds nice. The Obi service is just using your google voice account so it is free. You can also use sip with Obi.

---

### Post by zerubbabel on 2012-10-15
> **Scott Goodgame said:**
> That service sounds nice. The Obi service is just using your google voice account so it is free. You can also use sip with Obi.

Yes, I am aware of Google Voice, but I have avoided it because I am unwilling to have Google mine all my communications for advertizing tips (and heaven only knows what else). I don't know that they do this with audio communications, as they do with Gmail, but I'd be surprised if they didn't, since that's where their revenue comes from. I'd rather pay the small price for more secure connections.

---

