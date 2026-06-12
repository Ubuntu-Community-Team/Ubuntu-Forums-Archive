---
title: "Beating Gmail and the rest"
date: 2014-07-12
forum: The Cafe
---

### Post by tijmen-peter on 2014-07-12
I have been thinking about this for a while now, but since my knowledge of the subject isn't too broad, it's kinda hard to look for information in the right places. That's why I'm interested to hear what you all have to say about this.

The idea I have is to start providing an e-mail service open to anyone (like gmail) but not give anyone's information to the NSA, not sell your information to advertisers and not scan/read your emails (not so much like gmail). The physical part is covered, I plan to use a server placed in a bunker (a cold war bunker built to survive a nuclear war) which guarantees 100% uptime. Also it's located in the Netherlands, so outside the formal jurisdiction of British, American, Chinese and other spies. The Dutch intelligence service is relatively harmless, so it's not too hard to keep them out.

I am however looking for the software part. I need to find secure (preferably open-source) software to host the email and enable sending them. Also I need the ability to provide email addressess. In addition to 'normal' email which works across platforms, I want to offer GPG encrypted email as an integrated option.Obviously also the server and the traffic to and from it need to be encrypted for maximum security. 

I'm aware this is going to be costly, that's not the point. I would just like to hear your thoughts, as well as any input on how to achieve this, which software or encryption is available or would need to be built, or if you have any ideas for additional features. 

Thanks!

---

### Post by TheGurkha on 2014-07-12
> **tijmen-peter said:**
> I plan to use a server placed in a bunker (a cold war bunker built to survive a nuclear war) which guarantees 100% uptime.

That in itself won't guarantee uptime. Solid mains power, UPS and generators; redundant load-sharing hardware and mirroring, etc. That gets you closer to 99.999 many nines uptime for the bits under your control. Connectivity to the outside the world is another matter.

---

### Post by mooreted on 2014-07-12
Ars Technica has a set of articles on this:

[http://arstechnica.com/information-technology/2014/02/how-to-run-your-own-e-mail-server-with-your-own-domain-part-1/](http://arstechnica.com/information-technology/2014/02/how-to-run-your-own-e-mail-server-with-your-own-domain-part-1/)

---

### Post by mooreted on 2014-07-12
And here's part 2:

[http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/](http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/)

---

### Post by buzzingrobot on 2014-07-12
I consider the internet a public space, a gigantic bulletin board anyone can see, so looking for privacy there seems futile.  We publish on it, we don't send point-to-point communications. The files we publish, including email, sit on servers until someone comes along and downloads them. 

You can't hide the content you publish in a public space.  And no government is going to blithely give up the ability of demand access to the records of our internet use and our phone calls because no government is going to permit people it considers hostile and threatening to acquire the advantage of communicating without leaving a trace.

So... I think time and money would be better spent convincing people to avoid publishing anything they want to remain private. If you don't want to run the risk someone else will know, don't put it in an email, don't tweet it, don't put it on Facebook.  Just keep it to yourself.

---

### Post by tijmen-peter on 2014-07-12
@TheGurkha You're right, I should've phrased that a bit differently. What I meant was I am planning to utilize the services of Cyberbunker, which is a datacenter in a bunker and guarantees 100% uptime with a 'no matter what' guarantee. I am aware it's impossible to actually guarantee 100% uptime, but the fact they haven't been down once ever, is a good track record. They use generators and such among other things. The website is [www.cyberbunker.com]("http://www.cyberbunker.com")

---

### Post by tijmen-peter on 2014-07-12
@Mooreted, thanks, those links are really useful! :)

---

### Post by mooreted on 2014-07-12
> **tijmen-peter said:**
> @Mooreted, thanks, those links are really useful! :)

You are welcome, good luck.

---

### Post by tijmen-peter on 2014-07-12
@buzzingrobot You make a fair point. However, there are times when it's just impractical to use other resources than the internet. Quick communication can be essential to both businesses and individuals around the world and sometimes online communication is the only practical solution. Also the Internet has become so integrated in society it's often unavoidable to use. If I choose to share certain information with a specific person, no-one has the right to steal that information. That includes the government.

---

### Post by sandyd on 2014-07-12
> **tijmen-peter said:**
> @buzzingrobot You make a fair point. However, there are times when it's just impractical to use other resources than the internet. Quick communication can be essential to both businesses and individuals around the world and sometimes online communication is the only practical solution. Also the Internet has become so integrated in society it's often unavoidable to use. If I choose to share certain information with a specific person, no-one has the right to steal that information. That includes the government.

Already being worked on.
EMail: [http://darkmail.info/](http://darkmail.info/) | Lavabit (shut down)
Non-Email: [https://silentcircle.com/](https://silentcircle.com/)

---

### Post by tijmen-peter on 2014-07-12
@Sandyd, both options look interesting, however darkmail is not an actual email service, but rather an attempt to implement end-to-end encryption among current email providers. I have little faith in mayor companies such as Google and Windows implementing this, especially as they depend financially on 'reading' your email. (Windows claims they don't do this, but evidence points to the contrary). The service I am planning will not 'read' or scan people's email and will offer both GPG encrypted and 'normal' email, which is quite different from what I gather Darkmail is proposing. 

The Silent Circle is also an interesting project, but as it only works for mobile and still doesn't allow secure email I think it's only part of the solution, and my email project could coexist peacefully, as another part of the solution.

---

### Post by sandyd on 2014-07-12
> **tijmen-peter said:**
> @Sandyd, both options look interesting, however darkmail is not an actual email service, but rather an attempt to implement end-to-end encryption among current email providers. I have little faith in mayor companies such as Google and Windows implementing this, especially as they depend financially on 'reading' your email. (Windows claims they don't do this, but evidence points to the contrary). The service I am planning will not 'read' or scan people's email and will offer both GPG encrypted and 'normal' email, which is quite different from what I gather Darkmail is proposing. 

The Silent Circle is also an interesting project, but as it only works for mobile and still doesn't allow secure email I think it's only part of the solution, and my email project could coexist peacefully, as another part of the solution.

If your wanting GPG encryption of emails, enigmail already provides this, and can be used in fact on any email provider that you want.

---

### Post by tijmen-peter on 2014-07-12
@sandyd Enigmail is an additional plugin/add-on for existing email clients. This is an inconvenient extra step in installing and can be confusing for many people. What I want to build is a complete solution including client, server, host, emailaddress etcetera.

---

### Post by sandyd on 2014-07-12
> **tijmen-peter said:**
> @sandyd Enigmail is an additional plugin/add-on for existing email clients. This is an inconvenient extra step in installing and can be confusing for many people. What I want to build is a complete solution including client, server, host, emailaddress etcetera.

Which means they will still have to install your client.

---

### Post by tijmen-peter on 2014-07-12
@sandyd, besides the client, I would like to make a webmail function as well, for added convenience. However, even if people have to install my client, it would be just the client, not a client and additional plug-ins and add-ons to get the security they are looking for. So that's still easier than the currently available options.

---

### Post by user1397 on 2014-07-13
> **tijmen-peter said:**
> @sandyd, besides the client, I would like to make a webmail function as well, for added convenience. However, even if people have to install my client, it would be just the client, not a client and additional plug-ins and add-ons to get the security they are looking for. So that's still easier than the currently available options.
Makes sense.   Have you looked into lavabit?  Seems like the same thing you're trying to do, except the feds shut it down because it was linked to Edward Snowden (Snowden apparently had a lavabit email address).

I would suggest really looking into lavabit and trying to basically copy/mirror what they did, but the fact that you would be hosting it outside the USA already makes it way safer than lavabit (poor guy, if you read up on it the feds came and shut his system down basically)

---

### Post by tijmen-peter on 2014-07-13
@Ubuntuman
Lavabit is pretty much exactly what I want to do, but like you said, outside the US and outside the legal reach of US intelligence. 
I'll be looking closer at what they were doing and how. Thanks!

---

### Post by tijmen-peter on 2014-07-13
Although Lavabit comes pretty close to what I want to do, my approach would be a bit different. Lavabit stored the encryption key to all messages on their server, I would keep it on the user's device. Lavabit could have read people's emails if they wanted to, as they had access to the encryption keys. Also the emails were sent to the device in plain text, and were therefore vulnerable to hackers. I would send the email to the user in encrypted format and then use the encryption key on the device to decrypt it. This system is safer for the user as it makes it physically impossible for me to read (or share) the content of the messages.

---

### Post by bapoumba on 2014-07-13
Although I can see your point, no one can escape the law and international agreements. Where are your servers based again ?

---

### Post by lads on 2014-07-13
I have used GMail for about 8 years. The past 18 months I have tried hard to quit it, but every other alternative seems to have a downside: be it cost, US based infrastructure, lack of encryption, limited storage, user interface.

I have recently started using [ProtonMail]("https://protonmail.ch/"), which so for is the closest to beating GMail. The downsides are limited storage (minor) and user interface (major but solvable). 

Instead of starting a project of your own from scratch, I would advise you to rather support an existing project such as ProtonMail.

---

### Post by lads on 2014-07-13
I have used GMail for about 8 years. The past 18 months I have tried hard to quit it, but every other alternative seems to have a downside: be it cost, US based infrastructure, lack of encryption, limited storage, user interface.

I have recently started using [ProtonMail]("https://protonmail.ch/"), which so for is the closest to beating GMail. The downsides are limited storage (minor) and user interface (major but solvable). 

Instead of starting a project of your own from scratch, I would advise you to rather support an existing project such as ProtonMail.

---

### Post by tijmen-peter on 2014-07-13
@bapoumba Obviously no-one can fully escape the law and international agreements, and no-one can guarantee 100% security. However, we can at least make it as hard as possible for hackers to gain access to our files. Wether these hackers are individuals, corporations or the government is irrelevant.
The servers will be based in the Netherlands, which is not a five-eye country, so that will increase protection from intelligence agencies. Also the server will be based in a datacenter which does not interfere with their client's business, and doesn't respond to governmental bullying. The Pirate Bay are among their customers, which is a site that would be suffering from plenty of attacks from governments and private organisations. 

I want to provide maximum protection for confidential information within the boundaries of the law. Anything related to terrorism or child pornography will be banned by the terms&conditions and I would comply with a warrant from a Dutch court for these cases, but lawful confidential information should remain just that - confidential.

---

### Post by tijmen-peter on 2014-07-13
@lads I am currently a gmail user myself and tried to quit it as well. I encountered much of the same issues you mention, which lead me to the ambition to create the best secure email solution possible. As you said, ProtonMail just doesn't cut it, so I want to create a better alternative.

---

### Post by buzzingrobot on 2014-07-13
How do you plan to provide "security" for customers who use your service to send email to people who use Gmail, Yahoo, etc.?  Once mail is on someone else's server, you and the sender lose control of it.

---

### Post by tijmen-peter on 2014-07-14
@buzzingrobot Of course as soon as someone passes a message through an unsafe website, the security is gone. However, I am looking into options allowing gmail users to read the message outside the gmail environment, although this would not be implemented in the first versions yet.

---

### Post by buzzingrobot on 2014-07-14
> **tijmen-peter said:**
> @buzzingrobot Of course as soon as someone passes a message through an unsafe website, the security is gone. However, I am looking into options allowing gmail users to read the message outside the gmail environment, although this would not be implemented in the first versions yet.

Mail I send sits on the servers of the addressee's mail provider.  The packets traverse an unknown number of routers en route, where, potentially, they are available to anyone who has acquired access.  

E.g., if I send mail to someone using Gmail, that email sits on Gmail servers. The only way for anyone to read it is to download a copy to their mail client.  That applies whether you are using Gmail's web interface or a traditional client.

If the concern is about usage data leaked via use of a web interface, that's one thing.  But, if the concern is about exploitation of the content of mail sitting on mail providers' servers, I don't think anything can be done about that other than always using encryption or never sending, and never replying to, mail from anyone who uses a provider you want to avoid.

---

### Post by /ADM on 2014-07-15
I never understand people's needs for total 'privacy' on the internet.  It is a public space used by hundreds of millions a day.  Gone are the days when you are 'elite' for having a 15kbs dial-up modem and being one of the few thousands having a net connection.

Email is the same, it is as private as regular physical mail.  When somebody is handling your mail, they probably know it is a card, or some clothes or a box of chocolates (dimentions, sound and feel).  You don't add a ticket to your postmail asking them not to try to identify what it is do you?  So why do it with email?

---

### Post by tijmen-peter on 2014-07-16
@abilbrou
Virtually every country on the planet has strict laws prohibiting the opening of anyone's physical mail. This ban postal service staff and law enforcement. Most countries have no specific restrictions when it comes to e-mail. In addition this service would not only keep the NSA out, but criminal hackers as well. Have you ever sent information such as social security numbers, phone numbers, addresses and date of birth through email? Most people have, even if it was in an attachment such as a form or resume. A hacker with information like that can make life very tough for you. Therefore it's important to protect your email as well as possible. In addition there are the ethical aspects such as the inherent right to privacy. Even though we might disagree on the issue, that doesn't mean people shouldn't have the option to use a secure service. I'm sure you would agree with me people have a free right to choose any service they want, regardless of your personal needs or opinions, (as long as they don't harm you or infringe your rights of course).

---

### Post by tijmen-peter on 2014-07-16
@buzzingrobot
I know how email works. Obviously a message sits on the receiver's server. However, it is possible to store the message in encrypted form on an external server (such as mine) and send the recipient an alert there is a message waiting for them. They can then log on to the external server through a seperate web portal to access and download the message. This is of course not as convenient as just receiving the email directly, but it is safe and still easier than installing countless plugins. If the recipient uses my service as well, of course they would just receive the email in their inbox. 

A main target market for my service would be companies (so they can send confidential company data securely and easily) so the receiver would have access to my service's client anyway, for private individuals they will have to decide wether they want to use the process outlined above, or just send the email in the normal way and risk it, which is fine for many emails which don't carry confidential information.

---

### Post by sandyd on 2014-07-16
> **tijmen-peter said:**
> @buzzingrobot
I know how email works. Obviously a message sits on the receiver's server. However, it is possible to store the message in encrypted form on an external server (such as mine) and send the recipient an alert there is a message waiting for them. They can then log on to the external server through a seperate web portal to access and download the message. This is of course not as convenient as just receiving the email directly, but it is safe and still easier than installing countless plugins. If the recipient uses my service as well, of course they would just receive the email in their inbox. 

A main target market for my service would be companies (so they can send confidential company data securely and easily) so the receiver would have access to my service's client anyway, for private individuals they will have to decide wether they want to use the process outlined above, or just send the email in the normal way and risk it, which is fine for many emails which don't carry confidential information.

You will probably want to look into the code that powers sites such as [https://quickforget.com/](https://quickforget.com/) and 0bin.

---

### Post by buzzingrobot on 2014-07-16
> **tijmen-peter said:**
> @buzzingrobot
I know how email works. Obviously a message sits on the receiver's server. However, it is possible to store the message in encrypted form on an external server (such as mine) and send the recipient an alert there is a message waiting for them. They can then log on to the external server through a seperate web portal to access and download the message. This is of course not as convenient as just receiving the email directly, but it is safe and still easier than installing countless plugins. If the recipient uses my service as well, of course they would just receive the email in their inbox. 

A main target market for my service would be companies (so they can send confidential company data securely and easily) so the receiver would have access to my service's client anyway, for private individuals they will have to decide wether they want to use the process outlined above, or just send the email in the normal way and risk it, which is fine for many emails which don't carry confidential information.

I think encryption is fine for the corporate scenario you describe, where both senders and recipents can be expected to be compelled to use it after it is set up by competent technicians.

Your first posts suggested to me you were looking, instead, to a consumer-targetted service to relieve generalized privacy angst. In that market, I think encryption is a nonstarter.

Also, wouldn't the mail alerting someone to the presence of an encrypted mail serve to establish the easily discoverable link showing that the two parties were in communication with each other?

---

### Post by tijmen-peter on 2014-07-16
@sandyd I'll look into those, thanks!

---

### Post by tijmen-peter on 2014-07-16
@buzzingrobot I would be offering the service to both consumers and businesses. Businesses are more likely to be willing to pay for the service, and I don't see any harm in sharing the service with consumers for free as well :)

Yes, the notification email would show both parties in communication, however, the content of the message would still be confidential, which is a huge plus in my opinion.

---

### Post by Habitual on 2014-07-18
email, was not designed to be secure.

---

### Post by bashiergui on 2014-07-18
> **tijmen-peter said:**
> Yes, the notification email would show both parties in communication, however, the content of the message would still be confidential, which is a huge plus in my opinion.
Um, that's metadata. And metadata is all the <insert law enforcement agency name> needs to prove a connection or conversation happened. 

Email is fundamentally flawed. You'd have to roll your own new protocol to achieve true privacy. I read about some researchers trying to implement a better solution but I can't remember who it was. [These guys]("http://m.computerworld.com/s/article/9249568/Encrypted_instant_messaging_project_seeks_to_obscure_metadata") are working on a truly private IM solution, might give you some food for thought (i.e. hooking into Tor solves the plaintext metadata problem). I believe they also want to tackle email at some point.

---

### Post by tijmen-peter on 2014-07-19
@Habitual 
I know it wasn't. However, the fact that a car wasn't designed to fly, and humans weren't designed to travel to outer space hasn't stopped anyone from trying has it? 
I want to improve and possibly (partly) redesign email software and the email process to ensure communication is as convenient as possible, while still maintaining a service which is as secure as possible.

---

### Post by tijmen-peter on 2014-07-19
@bashiergui
Of course metadata proves a conversation took place. It's not the fact that the conversation took place that I want to hide. I want to hide the contents of the conversation. Your link does look very interesting and maybe I'll incorporate a tor-integrated service into my package as well in time. At the moment I'm just gathering ideas and seeing what can and can't be done within reason. 
As long as computers (or any way to share information) are used, 100% security will never be possible. Pigeons can be intercepted, mail can be read, messagers can be tortured to release info, etcetera. I just want to make it as hard as possible to for outsiders to get to sensitive information, whilst still maintaining a reasonably convenient and fast way to communicate.

---

### Post by buzzingrobot on 2014-07-19
If I understand correctly, you basically proposing using regular email to alert customers to the availability of encrypted content held on a server which they would then access to download the encrypted content.  (Mail protocols aren't mandatory to move the encrypted files from the server to the customer.)

I see added value here for some users if you intend to handle the encryption configuration for them.  I.e., most folks do not understand encryption and will very likely avoid it until someone they trust -- that would be you -- provides a point-and-click tool to set it up. Even then, I'm not at all confident people understand keys or would  be able to handle and retain them in any secure fashion.  

On the other hand, anyone with the experience and technical competence to set up encryption and securely handle keys can do all this on their own.

As others, including myself, have mentioned, the alert emails would potentially alert intelligence agencies to the fact of an exchange between two or more parties, which is exactly the kind of metada the NSA and other agencies have been criticized for collecting. 

The actual content of an exchange, encrypted or otherwise, remains subject to subpoenas, court orders, etc., as do the keys to decrypt, depending on the laws in a given jurisdiction. Since you would be responsible for the servers that content resides on, you would be the target of such actions.

I believe that if use of widespread use of encryption successfully thwarted police and intelligence agency access to online content, then governments would move to curtail use of encryption. While that might be nearly impossible in a technical sense, governments could certainly dramatically increase the potential penalties for criminal activity involving use of encryption.

---

### Post by Webmasters_Pride on 2014-07-21
is gmail still more secured than others out there?

---

### Post by tijmen-peter on 2014-07-22
@Webmasters_Pride
No, Gmail isn't secure.

---

### Post by tijmen-peter on 2014-07-22
@buzzingrobot
Sorry for the late reply.
You understand correctly. Although technically the content of email is subject to court orders and the like, many countries have countless loopholes which enable law enforcement to get to the content without a warrant or court order. Therefore, I definitely see a benefit in keeping the content as secure as possible. Not only keep it secure from the NSA et al, but also from criminal hackers, companies, identity thieves, etcetera. I would want to work with a one-click type of encryption, somewhat reminicsent of the TrueCrypt software, which allows one to encrypt files or disk space with a few clicks. Ideally it would be even simpler than that, although that may take away from the level of security (easy to set up generally means easy to break down) so I may offer two or more options for transcription, with a noob's version and a more advanced option as well. Retaining encryption keys would be the user's responsiblity, although it's not unthinkable I may offer a seperate piece of software which can tie in to the mail client to make that easier, whilst still keeping the keys stored on the user's computer. 

It's true law enforcement could come after me for hosting encrypted material. I am however based outside the USA, and the local law enforcement is not much into technology (incredibly outdated in fact) so there's not much harm to be expected from them.

---

### Post by Habitual on 2014-07-22
> **tijmen-peter said:**
> as convenient as possible, while still maintaining a service which is as secure as possible.

Good luck with **that**.

---

### Post by aysiu on 2014-07-22
I'm not sure I really get this idea. Whom are you *sending* these emails to? All the recipients also host their email in these secure-bunker servers?

If you're sending to people with normal email accounts, your received emails are all subject to the same NSA stuff that they would have been had you just hosted with a regular email service in the first place.

If I'm understanding correctly what you're proposing, it'd be like my having a secure bunker I send postcards out of. Who cares if my bunker is secure? I'm sending out *postcards*. The recipient of those postcards isn't securing the postcards. Even the deliverer of those postcards isn't securing them.

---

### Post by buzzingrobot on 2014-07-22
> **tijmen-peter said:**
> 
Although technically the content of email is subject to court orders 

Court orders and subpoenas become very real when you are the recipient.  Since your alerting scheme would create the open and visible metadata establishing the links between individuals, various agencies could collect and peruse that data and then -- following the legalities of their particular jurisdiction -- use the legal system to compel you to turn over the content of mail of individuals they are pursuing. That content will be encrypted.  If you, in the interest of making life easier for customers, store the keys, you will be required to turn them over, as well.

Of course, you, too, can leverage the legal system to challenge such orders. That does not come free, though.

> Retaining encryption keys would be the user's responsiblity...

I have every confidence that people would lose encryption keys as fast and as often as they lose or forget passwords.  

> It's true law enforcement could come after me for hosting encrypted material.

As far as I know, they can't come after you for hosting encrypted content.  But, if "they" believe people enaged in criminal activites have been using your service to communicate, then "they" will require you to cooperate.

---

### Post by tijmen-peter on 2014-07-22
@buzzingrobot
I will not be hosting keys, so I can't surrender them either.
People will evidently loose keys, but as I said, I might also create an application to help them keep keys easier. In the end, there's only so much I can do though, and if people can't keep their keys safe, then apparently they don't care about their security enough, or they would make more of an effort. It's like the keys to your house. It's pretty essential to not lose those, and if you do, only you are to blame. 

I would not cooperate with law enforcement, unless I absolutely have to. Even then, as stated, they would only receive encrypted files, but again here goes: people have to take a certain measure of responsibility. It is up to them to ensure they use fake emails and the like if they want to remain completely private. Also I am looking into a Tor-tie in, to avoid the meta-data problem entirely, but that's just an idea at this moment.

I want to say however, I really appreciate your input, as you really force me to be critical about the project, which is good :)

---

### Post by tijmen-peter on 2014-07-22
@aysiu
This question has come up before. Ideally of course the receipient would also use my service if not, there is a workaround:

> **tijmen-peter said:**
> 
Obviously a message sits on the receiver's  server. However, it is possible to store the message in encrypted form  on an external server (such as mine) and send the recipient an alert  there is a message waiting for them. They can then log on to the  external server through a seperate web portal to access and download the  message. This is of course not as convenient as just receiving the  email directly, but it is safe and still easier than installing  countless plugins. If the recipient uses my service as well, of course  they would just receive the email in their inbox.

---

### Post by buzzingrobot on 2014-07-22
> **tijmen-peter said:**
> @buzzingrobot

I would not cooperate with law enforcement, unless I absolutely have to. 

Well, that's what court orders and subpoenas are for. Ignoring them brings, at least, civil penalties.  Challenging them means lawyers.

>  I want to say however, I really appreciate your input, as you really force me to be critical about the project, which is good :)

Good luck.  The internet was designed and built with little regard for privacy, and no expectation that billions of people would use email.  So, I think the only way to get that level of privacy would require reengineering and rebuilding the thing. 

You should explore that idea of creating a dead-simple app to create and store keys. When I've tried to explain how encrypted mail works to family and friends, their eyes glaze over and they don't want to be bothered with it. Too hard, they say.

---

### Post by jeehyun on 2014-07-23
It's really serious problem...
:???: Google, MS, Apple, Yahoo,...

---

### Post by tijmen-peter on 2014-07-23
@buzzingrobot
> Well, that's what court orders and subpoenas are for. Ignoring them  brings, at least, civil penalties.  Challenging them means lawyers.
Court orders are a risk yes, but as I (and my servers) would be based in the Netherlands, only a court order from a Dutch judge would be an issue. Seeing as how Dutch judges are highly critical of any foreign agency attempting to court order their way into Dutch information, this would be much less of an issue then if my servers were to be based in, say, the USA, UK or any of the other Five Eye countries. In addition, there is a relatively active Pirate Party in the Netherlands, which devotes itself to Internet freedom and privacy, so they may be able to assist in the legal field, although I haven't approached them yet. It's just an idea at the moment, much like the entire project. 

> You should explore that idea of creating a dead-simple app to create and  store keys. When I've tried to explain how encrypted mail works to  family and friends, their eyes glaze over and they don't want to be  bothered with it. Too hard, they say.

I'd say it's possible to build such an app, so I'll definitely look into that. People do tend to be lazy and in order to provide a truly successful service, it should be as convenient as possible. An app could help, as people would be able to access their keys through one master password, of perhaps even through a fingerprint scan, as more and more smartphones etc have fingerprint scanners. Then again, the government is collecting more and more fingerprints as well, so this is something I'd have to think about long and hard.

---

### Post by buzzingrobot on 2014-07-23
> **tijmen-peter said:**
> People do tend to be lazy...

I don't think it's laziness.  I think people find the idea and the implementation of keys difficult to understand. For most people, a computer is an appliance, and email is a service they expect to be available on that appliance. 

Corporate and institutional users pay knowledgeable people to do IT, so they'd be a market for your service.

Mainstream consumers, I think, will typically require a point-and-click tool that does everything for them. One that "Just Works". A lot of people are intimidated or confused by password managers, so it needs to be simpler than those.

(You'll need, I'd bet, a way to allow Windows users to restore their access after they blow away their drive with a reinstall.)

Anyway, I wish you well with this effort.

---

