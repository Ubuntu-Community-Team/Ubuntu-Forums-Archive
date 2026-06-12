---
title: "Most secure web-based email (against sniffers in my lan)"
date: 2009-09-05
forum: Security
---

### Post by Ulysses_ on 2009-09-05
What would that be?  I have hotmail and yahoo.  There must be something more secure against any sniffer running in my lan.

---

### Post by kevdog on 2009-09-05
I'd say any service that provides mail through https. That would be my two cents.  I know gmail and hotmail provide this service.  Possibly yahoo, but I'm not sure.

---

### Post by XCan on 2009-09-05
[http://www.hushmail.com/](http://www.hushmail.com/) ? I've no idea how strong encryption's used by hotmail and yahoo though.

---

### Post by Rob_H on 2009-09-05
> **kevdog said:**
> I'd say any service that provides mail through https. That would be my two cents.  I know gmail and hotmail provide this service.  Possibly yahoo, but I'm not sure.

Yes, any web mail provider that uses HTTPS is secure against sniffers on the LAN. Gmail can be configured to force the browser to use HTTPS by going to Settings > Browser connection and setting it to "Always use HTTPS". Others might offer that, too.

---

### Post by Ulysses_ on 2009-09-05
Isn't there anything stronger than the HTTPS of hotmail that I am already using?

---

### Post by Rob_H on 2009-09-05
> **Ulysses_ said:**
> Isn't there anything stronger than the HTTPS of hotmail that I am already using?

Stronger? How? What's the problem you're trying to solve?

---

### Post by Ulysses_ on 2009-09-05
> **Rob_H said:**
> Stronger? How? What's the problem you're trying to solve?

 It's in the title.  It's stopping sniffers in my lan from reading emails.

---

### Post by Nepherte on 2009-09-05
Using https is sufficient against sniffers on your network.

---

### Post by Ulysses_ on 2009-09-05
> **Nepherte said:**
> Using https is sufficient against sniffers on your network.  What do you know about my network? :D

---

### Post by cariboo on 2009-09-05
Have a look at this [article]("http:///en.wikipedia.org/wiki/HTTP_Secure"), it explains how https works.

---

### Post by Rob_H on 2009-09-05
> **Ulysses_ said:**
> What do you know about my network? :D

Nepherte doesn't need to know anything about your network. If no one has tampered with your computer/browser and the correct web site address appears with HTTPS in the address bar, then the connection is completely secure from local sniffing. The configuration of your local network is not a factor.

---

### Post by XCan on 2009-09-05
Lol, if people are this interested in your secret life Ulysses_, you're in trouble already. Good luck.

---

### Post by bear24rw on 2009-09-05
Hah you sound pretty paranoid about these 'sniffers' maybe you should start pgp encrypting all your messages :P

---

### Post by Nepherte on 2009-09-05
> **Ulysses_ said:**
> What do you know about my network? :D
I know nothing about your network, but more about http and ssl.

---

### Post by Ulysses_ on 2009-09-05
> **XCan said:**
> Lol, if people are this interested in your secret life Ulysses_, you're in trouble already. Good luck.

Haha. It's not very secret if it's posted here, is it. :)  Here's more about the local network then (those who feel they know everything about all lans in the world need not read further :) ).

I work for a company with some 200 employees, most not caring about security at all.  Therefore any of these 200 odd computers in this lan can get owned, by hackers or other malicious types.  A sniffer application can therefore be installed and someone can listen to where we are connecting, and try to steal not only our windows passwords but also our bank passwords, paypal passwords, whatever.  By listening, logging, and doing brute-force attacks for some encryption methods, or smarter attacks for others.  Not all encryption methods are hard to break.  

Now I do not remember reading anywhere that SSL is unbreakable.  All encryption algorithms are assessed in terms of their strength, and crucially most old encryption methods are now easy to break, even by brute force.  Is there someone here who can recommend something better than SSL?  If you are one, please say what it is.  If not, can we all please cut the crap about SSL being unbreakable, please.

---

### Post by bear24rw on 2009-09-05
You could also tunnel out to your house for an extra layer of security..

---

### Post by ddrichardson on 2009-09-05
> **Ulysses_ said:**
> If you are one, please say what it is.  If not, can we all please cut the crap about SSL being unbreakable by hackers in this lan, please.
Without starting a flame war, if your LAN security instils that little faith, why would you use it for secure information?

---

### Post by Ulysses_ on 2009-09-05
And I just found an email provider that appears to improve on SSL.    "Asynchronous Encryption  Asynchronous encryption is a process that uses public key and private key encryption to make messages unreadable without knowing a user's plaintext password. Presently we use Elliptical Curve Cryptography (ECC) with 512 bits of security to encrypt messages. The private, or decryption, key is then encrypted with a user’s password using the Advanced Encryption Standard (AES) and 256 bits of security. The result is that once a message is stored on our servers in this fashion, it can’t be recovered without knowing a user's password. This provides a priceless level of security, particularly for customers that use e-mail to exchange sensitive information. You can learn more about our asynchronous encryption technology by reading our white paper on the subject."  [http://lavabit.com/secure.html](http://lavabit.com/secure.html)

---

### Post by Ulysses_ on 2009-09-05
> **ddrichardson said:**
> Without starting a flame war, if your LAN security instils that little faith, why would you use it for secure information?

That's a valid point.  But then, we are supposed to be looking for technical solutions to such problems, aren't we.

---

### Post by Bachstelze on 2009-09-05
> **Ulysses_ said:**
> 
Now I do not remember reading anywhere that SSL is unbreakable.  All encryption algorithms are assessed in terms of their strength, and crucially most old encryption methods are now easy to break, even by brute force.  Is there someone here who can recommend something better than SSL?  If you are one, please say what it is.  If not, can we all please cut the crap about SSL being unbreakable, please.

SSL is not an algorithm.

---

### Post by ddrichardson on 2009-09-05
> **Ulysses_ said:**
> That's a valid point.  But then, we are supposed to be looking for technical solutions to such problems, aren't we.
OK that's me told :rolleyes:

---

### Post by bear24rw on 2009-09-05
The thing is if you go with an SSL alternative the server also has to support it..

---

### Post by Bachstelze on 2009-09-05
> **Ulysses_ said:**
> 
Now I do not remember reading anywhere that SSL is unbreakable.  All encryption algorithms are assessed in terms of their strength, and crucially most old encryption methods are now easy to break, even by brute force.  Is there someone here who can recommend something better than SSL?  If you are one, please say what it is.  If not, can we all please cut the crap about SSL being unbreakable, please.

SSL is not an algorithm. Also, if it were unsecure, why would banks use it to protect their websites? Or maybe you think you know better, but in that case, why do you ask?

---

### Post by Rob_H on 2009-09-05
> **HymnToLife said:**
> SSL is not an algorithm. Also, if it were unsecure, why would banks use it to protect their websites? Or maybe you think you know better, but in that case, why do you ask?

The guy (or gal) is trolling. Movin' on...

---

### Post by ddrichardson on 2009-09-05
I think you're also getting confused by some terminology. The article you link to I think is referring to symmetric and asymmetric cryptography.

These are actually the whole point of SSL, which uses both - the one time keys used to authenticate are asymmetric which is processing intensive but allows the key to be used once only for bulk transfer symettrically which is efficient.

---

### Post by ackanao on 2009-09-05
Ulysses_

You can use any web-mail service you want as long as you encrypt your messages - you don't need lavabit for that, just use Seahorse and create your own encryption keys.

---

### Post by Ulysses_ on 2009-09-05
> **HymnToLife said:**
> SSL is not an algorithm. Also, if it were unsecure, why would banks use it to protect their websites? Or maybe you think you know better, but in that case, why do you ask?

Nobody said SSL is unsecure.  Security is not "either you have it, or you don't".  There are all shades of gray in between.  No knowledgeable or honest security software developer claims unbreakability.

So we can improve on the SSL option simply by changing the underlying algorithms as lavabit.com seems to be doing.  They claim that they have "developed a system so secure that it prevents everyone, including us, from reading the e-mail of the people that use it".  Got myself an email account with them, if only they supported retrieving emails from external email accounts.  

So the question is, as it says in the title, "what is the most secure email provider to open an account with in terms of the encryption scheme, but also with support for retrieving emails from external accounts?"

---

### Post by ackanao on 2009-09-05
That's lavabit and hushmail but only for non-free accounts; If you use free accounts your emails are stored unencrypted on their servers; So, Even if you use anoynimisation/privacy networks/tools like Tor, Jap or even VPN networks like XeroBank you still need secure (SSL) connection to the website you visit - there's no way around this; And if you want to keep your emails private, just encrypt them.

And I think they only encrypt emails that are transmitted between lavabit/hushmail users.

---

### Post by Ulysses_ on 2009-09-05
By the way, this is for email exchanges with all people, not just specific people that we would swap keys with.

---

### Post by Ulysses_ on 2009-09-05
> **ackanao said:**
> That's lavabit and hushmail but only for non-free accounts; If you use free accounts your emails are stored unencrypted on their servers; So, Even if you use anoynimisation/privacy networks/tools like Tor, Jap or even VPN networks like XeroBank you still need secure (SSL) connection to the website you visit - there's no way around this; And if you want to keep your emails private, just encrypt them.

And I think they only encrypt emails that are transmitted between lavabit/hushmail users.

Thanks ackanao.  Why would I need SSL if I went through an anonymizer?  EDIT: I guess you mean just for encrypted sites.

---

### Post by ackanao on 2009-09-05
You want to protect yourself from sniffers don't you? For example, Tor exit nodes are often compromised that way so it's not good idea to use Tor for sensitive data (like emails) unless you have secure connection to your webmail server (SSL).

---

### Post by phillw on 2009-09-05
We seem to have an echo ?????

[http://www.linuxquestions.org/questions/general-10/most-secure-web-based-email-against-sniffers-in-my-lan-752882/#post3670809](http://www.linuxquestions.org/questions/general-10/most-secure-web-based-email-against-sniffers-in-my-lan-752882/#post3670809)

Does this look a little like this thread ?

:confused:

---

### Post by Ulysses_ on 2009-09-06
> **ackanao said:**
> Tor exit nodes are often compromised that way so it's not good idea to use Tor for sensitive data (like emails) unless you have secure connection to your webmail server (SSL).

It is only internet criminals operating off this lan that I want to stop from sniffing at my emails, not three-letter agencies somewhere along the way.  Can such criminals own the Tor exit node that I am connecting to?  

Does Tor use stronger encryption with its SSL than the standard scheme commonly used with SSL by hotmail for pop3?

---

### Post by ackanao on 2009-09-06
I'm not talking about "three-letter" agencies - anyone who runs exit nodes can sniff data so there's no difference between criminals on your lan and criminals who runs exit nodes:

[https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#Canexitnodeseavesdroponcommunications.3FIsn.27tthatbad.3F]("https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#Canexitnodeseavesdroponcommunications.3FIsn.27tthatbad.3F")

[http://www.torproject.org/download.html.en#Warning]("http://www.torproject.org/download.html.en#Warning")

[http://www.schneier.com/blog/archives/2007/09/anonymity_and_t_1.html]("http://www.schneier.com/blog/archives/2007/09/anonymity_and_t_1.html")

[http://www.smh.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html?page=fullpage#contentSwap1]("http://www.smh.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html?page=fullpage#contentSwap1")

To protect yourself from sniffing use webmail service that supports secure connection (SSL) and encrypt your emails.

---

### Post by Ulysses_ on 2009-09-06
> **ackanao said:**
> To protect yourself from sniffing use webmail service that supports secure connection (SSL) and encrypt your emails.

But I'm already using SSL, hotmail pop3 forces SSL, we're looking for something stronger here and at least two companies offer encryption that is stronger than the standard SSL scheme used in hotmail.  

Why not go to lavabit's encryption scheme? Why not look for other encryption schemes like that and email providers that support them?  ''Because I said so'' is not the correct answer, sorry but you are expected to substantiate any advise you give because your readers do not know if you are a university professor specialized in this subject or a teen-aged tekkie.  Even if the standard SSL scheme offered by hotmail is good enough for me, we can still search for something stronger that someone else needs.

So the question remains, does anyone know of an email provider with stronger encryption than the standard SSL scheme used by hotmail, but who also supports pop3 retrieval from external accounts, and provides some means of saving emails on the user's computer in a searchable format (eg pop3).

---

### Post by ackanao on 2009-09-06
I never said anything bad about lavabit so please stop putting words in my mouth; I'm done posting on this thread because it's obvious that you're not able to communicate in a civil manner.

---

### Post by Ulysses_ on 2009-09-06
You heard about lavabit and hushmail and after this you are still recommending ''use a webmail service that supports secure connection (SSL).''  In other words, you are repeating the same mantra we all know without learning anything from the new information presented, such as the existence of hushmail and lavabit, and without caring too much about the question being asked (it's in the title).

---

### Post by ddrichardson on 2009-09-06
You make reference to the cracking of SSL but haven't noted that the key is single use - I might be missing something here entirely but can't see why sniffers would be successful.

Would it not be analysing a key that has already been used?

As I understand it, TLS/SSL is most susceptible to man in the middle attacks. If the message is, say PGP encrypted then this is not an issue as the received message is encrypted on a different key anyway.

---

### Post by cariboo on 2009-09-06
> **Ulysses_ said:**
> Haha. It's not very secret if it's posted here, is it. :)  Here's more about the local network then (those who feel they know everything about all lans in the world need not read further :) ).

I work for a company with some 200 employees, most not caring about security at all.  Therefore any of these 200 odd computers in this lan can get owned, by hackers or other malicious types.  A sniffer application can therefore be installed and someone can listen to where we are connecting, and try to steal not only our windows passwords but also our bank passwords, paypal passwords, whatever.  By listening, logging, and doing brute-force attacks for some encryption methods, or smarter attacks for others.  Not all encryption methods are hard to break.  

Now I do not remember reading anywhere that SSL is unbreakable.  All encryption algorithms are assessed in terms of their strength, and crucially most old encryption methods are now easy to break, even by brute force.  Is there someone here who can recommend something better than SSL?  If you are one, please say what it is.  If not, can we all please cut the crap about SSL being unbreakable, please.

If your network is that insecure, why even bother doing personal business while at work.

---

### Post by ackanao on 2009-09-06
> **Ulysses_ said:**
> You heard about lavabit and hushmail and after this you are still recommending ''use a webmail service that supports secure connection (SSL).''  In other words, you are repeating the same mantra we all know without learning anything from the new information presented, such as the existence of hushmail and lavabit, and without caring too much about the question being asked (it's in the title).

Lavabit uses TLS\SSL to secure your connection: 

> [B]Privacy
Transport Layer Encryption[/B]

Here at Lavabit we take privacy and security seriously. To ensure that no one intercepts your e-mail while it is being downloaded or sent to our servers, we support and encourage the use of Secure Sockets Layer (SSL) encryption. SSL was created specifically to eliminate eavesdropping and ensure that information could be transported securely over an untrusted network.

And they keep your emails enrypted on their servers:

> **Asynchronous Encryption**

Asynchronous encryption is a process that uses public key and private key encryption to make messages unreadable without knowing a user's plaintext password. Presently we use Elliptical Curve Cryptography (ECC) with 512 bits of security to encrypt messages. The private, or decryption, key is then encrypted with a user’s password using the Advanced Encryption Standard (AES) and 256 bits of security. The result is that once a message is stored on our servers in this fashion, it can’t be recovered without knowing a user's password. This provides a priceless level of security, particularly for customers that use e-mail to exchange sensitive information. You can learn more about our asynchronous encryption technology by reading our white paper on the subject.

so what's your point?

Every single person here told you to use (TLS\SSL) to connect to your webmail and to encrypt your messages; There's only one difference here - lavabit/hushmail will create encryption keys for you so you don't have to bother with that; With GnuPG or PGP you can create your own key-pair and you can choose for yourself which ciphers and hashing algorithms you want to use and the size of your encryption keys. 

This is just a wild guess but I think you don't know what you are looking for - but I wish you a good luck with your quest.

---

### Post by jobst on 2009-09-07
> **Ulysses_ said:**
> What would that be?  I have hotmail and yahoo.  There must be something more secure against any sniffer running in my lan.

It worries me as a System Administrator and business owner when People ask these kind of questions, but wait, there is MORE!

Any person that send you email to the most secure website of this world with 50000 bit encryption has already breached YOUR security, because they send it in clear text for everyone to see.

Email is insecure. Period.

On top of all this if **I** would spend my time reading all the incoming/outgoing emails of my employees I would not have any time for anything else ...


jobst

---

### Post by Ulysses_ on 2009-09-07
> **ackanao said:**
> Lavabit uses TLS\SSL to secure your connection: 



And they keep your emails enrypted on their servers:



so what's your point?

Every single person here told you to use (TLS\SSL) to connect to your webmail and to encrypt your messages; There's only one difference here - lavabit/hushmail will create encryption keys for you so you don't have to bother with that; With GnuPG or PGP you can create your own key-pair and you can choose for yourself which ciphers and hashing algorithms you want to use and the size of your encryption keys. 

This is just a wild guess but I think you don't know what you are looking for - but I wish you a good luck with your quest.

 That's just playing with words, lavabit's SSL is not the same as hotmail's SSL, lavabit are changing the underlying algorithms to something stronger, but you are recommending ''just use SSL'', in other words ''any SSL will do''.  In other words, ''stay with hotmail's pop3''.

In other words, ''don't look for the state of the art, don't start discussions on the state of the art, because I do not know the answer, I do not know what is the most secure web-based email provider''.  

It is such as simple question in the title, and so specific - limited to sniffers in my lan, and nothing more.

---

### Post by Ulysses_ on 2009-09-07
> **jobst said:**
> Any person that send you email to the most secure website of this world with 50000 bit encryption has already breached YOUR security, because they send it in clear text for everyone to see.  Depends on what the user is trying to achieve, I do not believe anyone in intermediary routing servers along the way to the recipient would care to read my emails - they have millions of other emails to choose from.  But a sniffing criminal in my lan seems to be the only one that will ever likely get interested in my emails.

---

### Post by kevdog on 2009-09-07
Seriously -- if SSL is insecure -- everyone is in trouble.  PGP/GPG SSL use many of the same symmetric ciphers.  In fact most products in some form or another use symmetric ciphers such as AES, 3DES, Twofish, Blowfish, etc. I know of no paper or link that have proven any of these symmetric ciphers to be insecure.  In addition both SSL and PGP/GPG have asymmetric components as well (RSA,DSA keys).  For you to post to these forums and say SSL is insecure is truly a false statement.  Making such a statement just exposes your lack of knowledge of how the encryption process is setup.  Yes longer keys (2048,4096 bit keys) can be used as an alternative to standard 1024 bit keys, however I know of no process in the year 2009 capable of breaking 1024 bit keys.

If you're worried about the ArcFour cipher used in standard gmail you can turn disable this cipher and default to AES256 (through the cipherfox extension).  In addition gmail offers full time https connections through the [https://mail.google.com](https://mail.google.com) interface which not only secures the authentication process, but all communication afterwards.  In addition, if truly concerned start using GPG to encrypt/sign your emails.  The US Govt could be sniffing from inside your office, but trust me -- if using https and GPG -- no one is going to be able to decipher your communication.

---

### Post by ackanao on 2009-09-07
> **Ulysses_ said:**
> That's just playing with words, lavabit's SSL is not the same as hotmail's SSL, lavabit are changing the underlying algorithms to something stronger, but you are recommending ''just use SSL'', in other words ''any SSL will do''.  In other words, ''stay with hotmail's pop3''.

In other words, ''don't look for the state of the art, don't start discussions on the state of the art, because I do not know the answer, I do not know what is the most secure web-based email provider''.  

It is such as simple question in the title, and so specific - limited to sniffers in my lan, and nothing more.

No, just like any other clueless user you decided to go with lavabit and never bother to read their documentation - so let's see what they have to say about SSL:

> We should note that this encryption process is only secure if you select a strong password. If your password is weak, an attacker would only need to brute force the password to crack our encryption. We should also note that this feature only protects messages on the Lavabit servers. Messages can always be intercepted before they reach Lavabit or between Lavabit’s servers and your personal computer, if SSL is not used. Finally, messages can be retrieved from your local hard drive if encryption software isn’t used on your computer to protect the files. These vulnerabilities are intentional. Our goal was to make invading a user’s privacy difficult, by protecting messages at their most vulnerable point. That doesn’t mean a dedicated attacker, like the United States government, couldn’t intercept the message in transit or once it reaches your computer.

If you're still looking for something "stronger" than SSL then don't go with Lavabit because they're not using SSL by default (you still need to configure your e-mail clients to use SSL); And, as you said, SSL is not good enough so you should continue your search for "**something stronger than SSL**".

As someone pointed out already: "**The guy (or gal) is trolling. Movin' on...**"

---

### Post by Ulysses_ on 2009-09-07
> I know of no process in the year 2009 capable of breaking 1024 bit keys.  And if you do not know it, clearly it does not exist, right?  More on this attitude further down.  > **kevdog said:**
> For you to post to these forums and say SSL is insecure is truly a false statement.  I never said SSL is insecure. Even if an unbreakable algorithm were ever invented, flaws in its implementation would still be used by criminals.  Implementations that are widely used attract more internet wildlife because there is more return on investment for their effort.  Enter lavabit, where on top of adding to the strength of the encryption (when you pay them), they also provide their own proprietary implementation (when you pay them).

I get this pattern from people in forums over and over, when they do not know the answer to a question on the state of the art: they go ''don't do that'', ''it's not used by people (therefore don't use it)'', ''it's not... ethical''.

Well any opinion is welcome, especially if it is substantiated. Just accept though, that some people won't agree with you. Allow them to not agree with you. Lavabit do not agree with some people here that the standard encryption of SSL is good enough. Lavabit customers do not agree either. Maybe they are all mistaken. Maybe the other side is mistaken. Are you going to force your opinion? Are you going to demand that people stop looking for the state of the art?

---

### Post by kevdog on 2009-09-07
Seriously, my last comment will be this one.

You have no idea what you are talking about.  SSL *IS* good enough.  Maybe not in 20 years, however as of today in the year 2009 *SSL* is good enough, period.  Lavabit is just throwing daggers.  Why would you need to pay Lavabit for features that both SSL/GnuPG gives you for free?

Show me a link (anywhere) where SSL was broken -- an actual break and not a theoretical concern.

Topics such as is SSL good enough are discussed regularly on the GnuPG mailing list.  I suggest you consult the mailing list entries over the last 3 months and then make your conclusion.  Heck even post to the mailing list.  There are a lot of cryptographers that both read and respond to the list.  Email Bruce Scheiner -- who will respond -- if you're still skeptical.  Don't point me to some marketing claim made by some company called Lavabit.  Lavabit's own implementation of encryption with asymmetric keys sounds a lot like GnuPG/PGP.  I suggest you actually do some reading before making a lot of unsubstantiated claims and fearmongering.

---

### Post by cariboo on 2009-09-07
This thread really doesn't seem to be going anywhere, plus there seems to be some hostility here, so this thread is closed.

---

