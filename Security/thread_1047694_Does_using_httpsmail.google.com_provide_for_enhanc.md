---
title: "Does using https://mail.google.com provide for enhanced security?"
date: 2009-01-22
forum: Security
---

### Post by kevdog on 2009-01-22
Just wondering when using the secure login to gmail:
[https://mail.google.com](https://mail.google.com)

At what point in the process, does your sent email become unencrypted and passed in plain text?  I would assume nothing being passed from the actual user's machine (the sender of the message) is unencrypted!

---

### Post by Dr Small on 2009-01-22
The text from your browser doesn't become unencrypted and passed in plain text, if you are using HTTPS. That's the whole point of it. But to the real question of "Does using [https://[...]](https://[...]) provide for enhanced security?", No it doesn't. You are still connected to Google Servers. ;)

---

### Post by hyper_ch on 2009-01-23
Well, https will encrypt the traffic between you and google.

However google will still have access to your email in plain text (and index it - as they say they do).

Also once you send the email (through google) or an email arrives in your gmail account then the connection between gmail and the other mail server is no encrypted either. However there is such a huge amount data coming and going from google that it seems IMHO unlikely anyone could specifically eavesdrop the communication between gmail servers and the remote email server.

---

### Post by kevdog on 2009-01-23
So I am aware that once you send an email, a copy get put in the Send box.  This tranmission however takes place over https correct?  I am only asking since the reports of sniffing gmail that appeared several months ago (Tom's Hardware one location among several).  One proposed solution was to use https rather than the usual http.  I never saw any followup on this recommendation however.

---

### Post by hyper_ch on 2009-01-23
the connection between you and gmail is over SSL... but not the connection between Gail and the recipient mail server.

---

### Post by halovivek on 2009-01-23
You can find only the https login of the server but the other thing data transmission between the server and you will be in http.
You are not using banking site or something like that it should be full https till end of the transmission and the data should be expired which the security service id which is provided will be expired after you logout. But it is not applicable to Gmail. if you close the firefox browser you can restore it and you can able to login even in https. but it is not possible in Gmail like banking site so there is no security guarantee in Gmail and yahoo also.

---

### Post by Circus-Killer on 2009-01-23
> **halovivek said:**
> You can find only the https login of the server but the other thing data transmission between the server and you will be in http.
You are not using banking site or something like that it should be full https till end of the transmission and the data should be expired which the security service id which is provided will be expired after you logout. But it is not applicable to Gmail. if you close the firefox browser you can restore it and you can able to login even in https. but it is not possible in Gmail like banking site so there is no security guarantee in Gmail and yahoo also.

incorrect. if you go to [http://mail.google.com](http://mail.google.com) then username and password will be encrypted and the emails and stuff will be over plain http (the way you said it would).

however, if you type in the address bar [https://mail.google.com](https://mail.google.com), like the other way i mentioned, username and password is encrypted, but so is all the communication between gmail and yourself. to access the two different methods just means you change http to https when you first type in the initial address in the address bar.

try for yourself, first type in the address bar [http://mail.google.com](http://mail.google.com) and login.
then go to [https://mail.google.com/](https://mail.google.com/) and see the difference.

---

### Post by Paul Bramscher on 2009-01-23
The relevant RFC's for e-mail have, strangely, not been updated to include cryptographic transmissions.  I wonder whether this may be a deliberate omission?

If you drop to a terminal and issue a "traceroute {ip of the recipient's smtp mailserver}" you might get a general idea of the servers the email (in plain-text) will pass before your recipient can read them.  (It won't quite be accurate, though, since it'll be the route from your box to the distant mailserver, rather from your mailserver to the distant mailserver.)

One thing I've experimented with is the Enigmail Thunderbird plugin. Basically you can create a public/private trusted keyring, and get some extra buttons and functionality in Thunderbird to encrypt contents, make digital signatures, etc.  What's surprising is that this is not standard equipment in all e-mail programs at this stage.

I set up Google's POP client with Thunderbird and an SSL connection to login:
[http://mail.google.com/support/bin/answer.py?answer=86399](http://mail.google.com/support/bin/answer.py?answer=86399)

Then I downloaded the Enimail Thunderbird add-on:
[https://addons.mozilla.org/en-US/thunderbird/addon/71](https://addons.mozilla.org/en-US/thunderbird/addon/71)

---

### Post by halovivek on 2009-01-23
> **Circus-Killer said:**
> incorrect. if you go to [http://mail.google.com](http://mail.google.com) then username and password will be encrypted and the emails and stuff will be over plain http (the way you said it would).

however, if you type in the address bar [https://mail.google.com](https://mail.google.com), like the other way i mentioned, username and password is encrypted, but so is all the communication between gmail and yourself. to access the two different methods just means you change http to https when you first type in the initial address in the address bar.

try for yourself, first type in the address bar [http://mail.google.com](http://mail.google.com) and login.
then go to [https://mail.google.com/](https://mail.google.com/) and see the difference.

ok i will try and get back to you

---

### Post by pdtpatrick on 2009-01-23
If you are looking for security then use evolution or outlook using SSL to transmit username and password and for your messages you can encrypt them in attachments using public so the recipient would be the only able to able it with his private key :) 

otherwise -- you are open to the world like most people. Then again like one the colleagues mentioned, there is entirely too much communication going on between google servers that it would be difficult for someone to eavesdrop. But it can happen, however it is very unlikely and difficult.

---

### Post by brandon88tube on 2009-01-24
How would you go about setting up evolution like that?

---

### Post by kevdog on 2009-01-24
I'm only worried about wireless packet sniffing.  Justed wanted to ensure https allowed for end encryption from my computer to gmail.  The subject of using GnuPG is a totally different ball of wax.  This encrypts the actually contents of the transmission, but does not provide for an encrypted transport layer.  Two totally different things.

---

### Post by Dr Small on 2009-01-24
> **kevdog said:**
> I'm only worried about wireless packet sniffing.  Justed wanted to ensure https allowed for end encryption from my computer to gmail.  The subject of using GnuPG is a totally different ball of wax.  This encrypts the actually contents of the transmission, but does not provide for an encrypted transport layer.  Two totally different things.
Yeah, if you're using SSL, don't worry about packet sniffing. (When Wireshark wasn't broke) I used to do these types of tests on trying to retrieve the data out of the packets from SSH connections, SSL connections, Gajim (GnuPG connections), and OTR connections. They're all encrypted and anyone eavesdropping the connection won't be able to read it.

---

### Post by kevdog on 2009-01-24
When did Wireshark break??  I must have missed that update!

---

### Post by Dr Small on 2009-01-24
> **kevdog said:**
> When did Wireshark break??  I must have missed that update!
Wireshark is broke on my system (sorry, I should have specified that). I don't upgrade any of my systems, so when I install newer software, other things upgrade and break older packages. It happens once in a blue moon. I can upgrade Wireshark, but that requires a newer kernel which I'm unwilling to risk just yet :D

---

