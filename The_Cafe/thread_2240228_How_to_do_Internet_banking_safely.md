---
title: "How to do Internet banking safely ?"
date: 2014-08-18
forum: The Cafe
---

### Post by linuxyogi on 2014-08-18
Hi,

Yesterday morning I enabled Internet banking for my savings account. I use only Firefox to login to mt bank's website. I have two security addons, Noscript and Bluhell.

Both Lubuntu and Manjaro are up to date.

I have use KeepassX to create a complex password for the site.

Although I have enabled transaction capability for my account I really don't need it. I enabled it just in case I need to pay something while shopping online. Usually I always choose the COD (Cash on Delivery) facility but problem is COD is available for only those items which has origins within my country. 

Anything else I need to do to maintain security ?

---

### Post by uRock on 2014-08-18
Just keep your system up to date. I am jealous you were able to use a complex password, as Bank of America only allows numbers and letters, which is very frustrating for me.

---

### Post by markodd on 2014-08-18
If your bank allows for two factor authentication, definitely use it. You could also consider using a VPN, for some extra-security. 

I'm not sure what bluhell does, but are you absolutely sure it does what it states and that it does not have any "security hole"?

---

### Post by linuxyogi on 2014-08-18
> **markodd said:**
> If your bank allows for two factor authentication, definitely use it. 


No, AFAIK my bank doesn't support two factor authentication. I also think its critical and is a must.


> **markodd said:**
> You could also consider using a VPN,  for some extra-security.  

Frankly, I don't wanna pay for a VPN service coz the payments are all in dollars and when converted to rupees it exceeds my mothly ISP cost. I can use a free service like vpnbook.

But tell me something, how can using a VPN make my Internet banking more secure ? I mean all I know about VPN is once you establish a connection you are part of their local network. So my banking site's credentials will pass through their network. Doesn't this make it less secure ? 


> **markodd said:**
> 

I'm not sure what bluhell does, but are you absolutely sure it does what  it states and that it does not have any "security hole"? 

Bluhell is a fork of Adblock plus. Some people say that Adblock Plus has become too bloated these days while others disagree.

If it has security hole ? I have no idea but a lot of people are using it.

---

### Post by markodd on 2014-08-18
I'm testing bluhell.. I've disabled my "Adblock Edge" and "Disconnect" while using it.. Seems to be nice.

I wouldn't use a free VPN service if I were you, they've no incentive to keep your information private, they probably keep logs, etc..

Your banking site credentials will pass through their network encrypted. First, because banks use SSL, secondly because VPNs encrypt your data. If somewhere along the line someone has the decryption tools to decrypt your bank info, then a VPN will help, as it'll encrypt the data.


 If I'm saying something completely ridiculous, please let me know.

---

### Post by ajgreeny on 2014-08-18
I have seen some people suggesting booting to a live system specifically to run their bank accounts online.

I can see how that might increase secvurity as long as you shutdown straight after banking, but I think the inconvenience of doing that would be just a bit too much for me.

My bank in the UK uses a small electronic device which creates a new number each time I login to their site, and this changes each time I login, so there is no PIN or password that remains the same, that any net-snooper could use to login as me.

---

### Post by uRock on 2014-08-18
> **linuxyogi said:**
> how can using a VPN make my Internet banking more secure ? I mean all I know about VPN is once you establish a connection you are part of their local network. VPNs are normally encrypted with strong algorithms, then again, so is SSL.

> **markodd said:**
>  "Disconnect"

Disconnect calls home to Amazon with every search. I first figured this out when using Disconnect while running PeerBlock. Peerblocked Disconnect every time and displayed an IP for Amazon.

---

### Post by linuxyogi on 2014-08-18
> **markodd said:**
> I'm testing bluhell.. I've disabled my "Adblock Edge" and "Disconnect" while using it.. Seems to be nice.

I wouldn't use a free VPN service if I were you, they've no incentive to keep your information private, they probably keep logs, etc..



One thing is "Security by Policy" and the other thing is "Security by design". In case of VPN services, even the paid ones its the former. Remember you are choosing to trust whatever they are claiming. There's no way to be exactly sure if there are monitoring your traffic or not. Tor on on the other hand is "Security by design". AFAIK they cannot retrieve logs even if they want to. Coz they is no such system in place. Now if something like Tor can be used for banking ? I wanna know that too. 


> **markodd said:**
>  Your banking site credentials will pass through their network encrypted.  First, because banks use SSL, secondly because VPNs encrypt your data.  If somewhere along the line someone has the decryption tools to decrypt  your bank info, then a VPN will help, as it'll encrypt the data.

If I'm saying something completely ridiculous, please let me know.

I understand what you are saying. VPN adds a secondary layer of security. I will definitely consider subscribing to one.

---

### Post by linuxyogi on 2014-08-18
> **uRock said:**
> VPNs are normally encrypted with strong algorithms, then again, so is SSL. 

So, it means if I use a VPN the extra advantage will be my ISP will not be able to track my activity right ? Also another layer of protection.

---

### Post by markodd on 2014-08-18
> **linuxyogi said:**
> So, it means if I use a VPN the extra advantage will be my ISP will not be able to track my activity right ? Also another layer of protection.

Correct

---

### Post by uRock on 2014-08-18
> **linuxyogi said:**
> So, it means if I use a VPN the extra advantage will be my ISP will not be able to track my activity right ? Also another layer of protection.

True. They will only be able to see the parts of the header for the connection between you and the VPN carrier. Without the VPN, the bank can see what site you are going to, but the data within the packets are still encrypted from your machine to the bank's server using SSL, aka https.

---

### Post by linuxyogi on 2014-08-18
> **ajgreeny said:**
> I have seen some people suggesting booting to a live system specifically to run their bank accounts online.

I can see how that might increase secvurity as long as you shutdown straight after banking, but I think the inconvenience of doing that would be just a bit too much for me.



I really don't understand this theory. If I am using a Live CD all my packages are old and therefore the system is vulnerable. 

Now if they are ready to go for a 350MB + update every time they need to login to their banks' site. I got nothing to say. 

But even then, what about the kernel ? If he reboots all changes are lost.

---

### Post by CharlesA on 2014-08-18
> **linuxyogi said:**
> I really don't understand this theory. If I am using a Live CD all my packages are old and therefore the system is vulnerable. 

Now if they are ready to go for a 350MB + update every time they need to login to their banks' site. I got nothing to say. 

But even then, what about the kernel ? If he reboots all changes are lost.

Persistent live USB, but then what's the point of running live?

Just keep your system up-to-date and you will be fine.

---

### Post by linuxyogi on 2014-08-18
> **CharlesA said:**
> Persistent live USB, but then what's the point of running live?

Just keep your system up-to-date and you will be fine.

I read [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") about how to create a persistent Live usb, just out of curiosity.

But I am bit confused about what does the word "Live" mean in this case coz the changes persists.

The only difference that I see is the interface that storage device is using. In case of an usual HDD installation its SATA and

in this case its USB.

Is there any difference ?

---

### Post by CharlesA on 2014-08-18
> **linuxyogi said:**
> I read [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") about how to create a persistent Live usb, just out of curiosity.

But I am bit confused about what does the word "Live" mean in this case coz the changes persists.

The only difference that I see is the interface that storage device is using. In case of an usual HDD installation its SATA and

in this case its USB.

Is there any difference ?

You can boot it "live" from any computer instead of it being installed on a simple machine.

---

### Post by vasa1 on 2014-08-18
> **linuxyogi said:**
> ...
Bluhell is a fork of Adblock plus. Some people say that Adblock Plus has become too bloated these days while others disagree.

If it has security hole ? I have no idea but **a lot of people are using it**.
I posted a link in one of your previous threads about someone who had doubts about Bluhell. Even if Adblock is bloated, I'd still prefer it. I make my own filter lists and don't use any of the readymade ones.

As for a lot of people using it, a lot of people still use WinXP and then there's the Yo! app.

To come back to your question, isn't it just a variant of "how do I use my PC securely?"?

One thing, as already suggested, is to get a bank account that does TFA. Most self-respecting banks even in India offer a login password as well as a transaction password although complex passwords may be disallowed. Also, depending on what one is doing, a one-time code is sent by SMS (or email) which also has to be entered for the transaction to be completed.

From what I read, much of the insecurity arises from bank staff passing on confidential data. So one effective precaution is to change at least the login password as frequently as possible assuming that the stolen data is "frozen" in time and thus would be useless if the user change a password after the theft of data but before someone misuses it.

---

### Post by markodd on 2014-08-19
> **uRock said:**
> 
Disconnect calls home to Amazon with every search. I first figured this out when using Disconnect while running PeerBlock. Peerblocked Disconnect every time and displayed an IP for Amazon.

Alright, thank you. I'm already looking for an alternative to disconnect.

---

### Post by linuxyogi on 2014-08-19
@[**[COLOR=#DD4814][B]uRock**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1018339")

I didn't even know that something like peerblock exists. I went to their download page and it seems like peerblock is a Windows only app. Is there anything like peerblock for Linux ?

---

### Post by markodd on 2014-08-19
> **linuxyogi said:**
> @[**[COLOR=#DD4814][B]uRock**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1018339")

I didn't even know that something like peerblock exists. I went to their download page and it seems like peerblock is a Windows only app. Is there anything like peerblock for Linux ?

I know you're not asking me but... I know for a fact that you can block IP lists in several torrent software (deluge, transmission, etc). You can find those lists if you do a search for "IP block list".

For normal day to day internet browsing, I'm not sure how it would help.. Maybe you want something like "Web of trust"?

EDIT: Up until 2007 or so, there was PeerGuardian 2, but it seems to have been discontinued.

---

### Post by markodd on 2014-08-19
> **markodd said:**
> Alright, thank you. I'm already looking for an alternative to disconnect.

To update on this, I'm now using the Fanboy's Social Blocking List, in adblock-edge. Hopefully it blocks everything.

---

### Post by Lars Noodén on 2014-08-19
> **linuxyogi said:**
> Now if something like Tor can be used for banking ? I wanna know that too.

Tor is for privacy.  Using it to log into your bank would negate any privacy advantages.  It's kind of the opposite of what you are trying to do and shoud, in this context, be avoided.  

Back on the topic of security, your bank needs to use multi-factor authentication.  That is much more than just adding a second password which, if you think about it, does nothing.  Multi-factor would instead be also using an extra device like ajgreeny described, or pre-arranged transaction authentication codes aka one-time passwords, or confirming via SMS, etc.  The idea is to prevent a replay attack.  If it cannot do that, it is not secure.

---

### Post by linuxyogi on 2014-08-19
> **vasa1 said:**
> I posted a link in one of your previous threads about someone who had doubts about Bluhell. Even if Adblock is bloated, I'd still prefer it. I make my own filter lists and don't use any of the readymade ones.

As for a lot of people using it, a lot of people still use WinXP and then there's the Yo! app.

To come back to your question, isn't it just a variant of "how do I use my PC securely?"?

One thing, as already suggested, is to get a bank account that does TFA. Most self-respecting banks even in India offer a login password as well as a transaction password although complex passwords may be disallowed. Also, depending on what one is doing, a one-time code is sent by SMS (or email) which also has to be entered for the transaction to be completed.

From what I read, much of the insecurity arises from bank staff passing on confidential data. So one effective precaution is to change at least the login password as frequently as possible assuming that the stolen data is "frozen" in time and thus would be useless if the user change a password after the theft of data but before someone misuses it.

I am little confused about the purpose of adblocking addons. I am not talking about Adblock vs Bluhell. Why do people use adblock plugins ? I use it to block ads simply because they are annoying. But I want to know if blocking ads actually improves security.

I got a login and password and my bank calls the transaction password pin. Now, I read about the login id, password, pin in their FAQ but I found no mention about the one time code. I was asked to enter my mobile number during the registration process may be its there but they didn't mention it.  



> **markodd said:**
> I know you're not asking me but... I know for a fact that you can block IP lists in several torrent software (deluge, transmission, etc). You can find those lists if you do a search for "IP block list".

For normal day to day internet browsing, I'm not sure how it would help.. Maybe you want something like "Web of trust"?

EDIT: Up until 2007 or so, there was PeerGuardian 2, but it seems to have been discontinued.

WOT is installed. Just added a blocklist to Deluge from [here]("https://www.iblocklist.com/lists.php"). 

BTW, in Deluge's IP block list plugin window it says "Type : PeerGuardian" .

---

### Post by linuxyogi on 2014-08-19
@[**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643") / [**[COLOR=#000000]vasa1[/COLOR]**]("http://ubuntuforums.org/member.php?u=449866")

I just talked with my bank's CC. Yes, they send a (OTP) one time pin during the time of transaction.

---

### Post by vasa1 on 2014-08-19
> **linuxyogi said:**
> ... But I want to know if blocking ads actually improves security.
...
I'm pretty sure blocking ads can improve security. There have been recent cases where the ad provider used by "reputable" sites has been hacked to make ads serve malware. Someone will post links to back that up.

[http://en.wikipedia.org/wiki/Malvertising](http://en.wikipedia.org/wiki/Malvertising)
[http://www.pcworld.com/article/2084160/malware-delivered-to-thousands-via-ads-on-yahoocom.html](http://www.pcworld.com/article/2084160/malware-delivered-to-thousands-via-ads-on-yahoocom.html)

---

### Post by buzzingrobot on 2014-08-19
> **linuxyogi said:**
> Hi,

Yesterday morning I enabled Internet banking for my savings account...

Anything else I need to do to maintain security ?

Bookmark the bank's correct URL.  Then, use that bookmark as the only way you access the site. This prevents being fooled by phishing sites that register and use typoed domain names.

Your bank should not be sending email to you with links it asks you to click on, so if something shows up it its almost certainly a fake.  If the bank needs to communicate with you, it should use the messaging facility on its site. Sending you mail -- without links -- asking you to log on and check your messages is legit.

Don't access the site from *any* public PC.  Don't trust the security of free wifi at cafes, coffee shops, etc., no matter what they say.

Install the EFF's "HTTPS Everywhere" extension which enables HTTPS by default whenever possible.

---

### Post by linuxyogi on 2014-08-19
> **buzzingrobot said:**
> Bookmark the bank's correct URL.  Then, use that bookmark as the only way you access the site. This prevents being fooled by phishing sites that register and use typoed domain names.

Your bank should not be sending email to you with links it asks you to click on, so if something shows up it its almost certainly a fake.  If the bank needs to communicate with you, it should use the messaging facility on its site. Sending you mail -- without links -- asking you to log on and check your messages is legit.

Don't access the site from *any* public PC.  Don't trust the security of free wifi at cafes, coffee shops, etc., no matter what they say.

Install the EFF's "HTTPS Everywhere" extension which enables HTTPS by default whenever possible.

Bookmarked and added a keyword for convenience.

Actually when I visit my bank's website the first page says the same points which you have mentioned.

All my Internet activity is limited to my home broadband connection.

This site always selects https by default but I am installing https everywhere anyways.

---

### Post by uRock on 2014-08-19
> **linuxyogi said:**
> @[**[COLOR=#DD4814][B]uRock**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1018339")

I didn't even know that something like peerblock exists. I went to their download page and it seems like peerblock is a Windows only app. Is there anything like peerblock for Linux ?

> **markodd said:**
> I know you're not asking me but... I know for a fact that you can block IP lists in several torrent software (deluge, transmission, etc). You can find those lists if you do a search for "IP block list".

For normal day to day internet browsing, I'm not sure how it would help.. Maybe you want something like "Web of trust"?

EDIT: Up until 2007 or so, there was PeerGuardian 2, but it seems to have been discontinued.

I have imported my Peerblock list (transmission only allows one list) to Transmission, but it doesn't have the GUI that allows you to see everything being blocked.

---

