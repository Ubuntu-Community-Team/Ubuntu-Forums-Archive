---
title: "Encryption with IM messaging"
date: 2008-11-03
forum: Security
---

### Post by kevdog on 2008-11-03
Anyone use any of the two following encryption packages with Pidgin to provide for encrypted IM communication (both are available in the universe repositories):

1. OTR (Off-the-Record) Messaging : [http://www.cypherpunks.ca/otr/software.php](http://www.cypherpunks.ca/otr/software.php)
2. Pidgin Encryption : [http://pidgin-encrypt.sourceforge.net/](http://pidgin-encrypt.sourceforge.net/)


Thoughts or opinions on either project/plugin would be appreciated.  I use GnuPG alot along with some form of disc encryption (currently True Crypt).

---

### Post by Dr Small on 2008-11-03
I use Gajim with Jabber that support GnuPG encryption on the fly. I have, in the past, used OTR with Pidgin, but with most like everything, the person you are communicating with must have the OTR plugin installed.

All of my friends use Jabber, and we are just about use Gajim, so setting it up to use our GPG keys is simple.

I have never used Pidgin Encryption, but OTR worked alright as far as I am concerned.

---

### Post by kevdog on 2008-11-03
Gajim looks very nice -- too bad its only for Jabber.  Love the GnuPG functionality.  Thanks for telling me about a piece of software I didn't know about previously.

---

### Post by Gourgi on 2008-11-04
> **kevdog said:**
> Anyone use any of the two following encryption packages with Pidgin to provide for encrypted IM communication (both are available in the universe repositories):

1. OTR (Off-the-Record) Messaging : [http://www.cypherpunks.ca/otr/software.php](http://www.cypherpunks.ca/otr/software.php)
2. Pidgin Encryption : [http://pidgin-encrypt.sourceforge.net/](http://pidgin-encrypt.sourceforge.net/)


Thoughts or opinions on either project/plugin would be appreciated.  I use GnuPG alot along with some form of disc encryption (currently True Crypt).

only thing i can tell is that i noticed from site statistics Pidgin Encryption is less active in development, last commit 6 months ago .

---

### Post by Jozza The Wick on 2008-11-05
I use Pidgin & OTR with a few friends - one over the Y! protocol, and another over the AIM protocol. Both work well, and I've seen (when one of us has OTR enabled and the other one doesn't, e.g. after a unexpected disconnect from the network), the encrypted text messages, so I have seen with my own eyes that the messages are being encrypted as they pass back & forth.

Another point to consider is that OTR provides plasible deniability. From the Wikipedia page:

"The primary motivation behind the protocol was providing deniability for the conversation participants while keeping conversations confidential, like a private conversation in real life, or off the record in journalism sourcing. This is in contrast with the majority of cryptography tools which resemble more a signed writing on paper, which can be later used as a record to demonstrate the communication event, the participants, and the topic of communication. "

If you're not aware of these issues, have a look at the OTR and read the sources referenced by Wikipedia.

[http://en.wikipedia.org/wiki/Off-the-Record_Messaging](http://en.wikipedia.org/wiki/Off-the-Record_Messaging)
[http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)

I'm not an expert, so I would welcome comments & suggestions from others.

---

### Post by Tich666 on 2008-11-05
I'm currently using pidgin with the OTR plugins and it's working great with the few contacts I could get to use either pidgin or MirandaIM and install the plugin.

Convincing my contacts to use jabber is even harder than to convince them to use pidgin, so this is the best I can hope for.

As Jozza has pointed out there are a few other advantages of OTR over GnuPG so I'm hoping to see it implemented with other IM clients as well.

---

### Post by kevdog on 2008-11-05
I dont really understand the plausible deniability argument the cypherpunk people are trying to make.

---

### Post by AusIV4 on 2008-11-05
> **Tich666 said:**
> As Jozza has pointed out there are a few other advantages of OTR over GnuPG so I'm hoping to see it implemented with other IM clients as well.

OTR is already implemented in a number of clients. Mac users will find it built in to Adium. It's a simple plugin with Pidgin and Kopete. On Windows, Miranda and Trillian both have OTR plugins. AIM users can even install the localhost AIM proxy to get OTR without needing to change clients.

There really aren't many clients that aren't supported by OTR.

---

### Post by ua6icab7 on 2008-11-06
[WOW Gold](http://www.gold4power.com/) was released in 2000 and is part of the WOW Hits series.It was a single 2-CD/2-cassette collection of contemporary Christian music from the 1960s to the time it was released. Marketing & distribution responsibilities for this title in the WOW Hits series was relegated to Brentwood Records (now Provident Music Group). The album reached #111 on the Billboard 200 chart.

---

### Post by Dr Small on 2008-11-11
> **kevdog said:**
> I dont really understand the plausible deniability argument the cypherpunk people are trying to make.
I thought I responded to this thread (and maybe I did when the forums were having database problems and it never got submitted). Anyhow, the Plausible Deniability allows the user to have all log files encrypted (if I am correct). To me, this is pointless.

Let's look at a simple scenario real quick.
Suppose I am a news-reporter with breaking news and stop off at the local coffee shop that has WiFi where I will be connecting to the network and instant messaging my boss the confidential breaking news. 

1) The network in unencrypted
2) Anyone could be packet sniffing
3) If I have Samba setup incorrectly, or have no firewall rules, anyone can easily access my system and potentially read my instant message logs to my boss.

So, here is the real killer. If this is my job, I do this for a living, would I really want my instant messages logged period? I think that if it is truly confidential, I would turn logging off. That's just my take on it.

---

### Post by kevdog on 2008-11-11
Dr. Small

If this only implies that User Logs are encrypted as you say, wouldn't the most likely place where the logs would be stored, would be on the computer where pidgin is installed?   I haven't really tried this feature, however are you telling me there is no way to actually go back and read the logs with an encrypted password?

Even if the network was unencrypted and someone is packet sniffing -- isn't the fact that your IM's are being transmitted in an encrypted state -- good enough?  Unless there is a flaw with the RSA/AES cipher, I figured this encryption would be good enough?

And yes, keeping logs for no reason is pointless.

---

### Post by Dr Small on 2008-11-11
Yes, I know. I guess I wasn't really through with my news-reporter scenario, as I left out that they news-reporter is contacting his boss via instant messenger and using either OTR or GnuPG. So yes, packet sniffing would yeld an encrypted connection.

Really, the point behind it was (and maybe I am not very good at my explanations) is that point of Deniablity and encrypting your log files is really pointless if you are the paranoid. The paranoid shouldn't have logs at all.

As for as being able to read the encrypted logs after OTR has encrypted them, I don't really recall if it is possible. (It may be, I just haven't used OTR or Pidgin for a very long time).

---

### Post by kevdog on 2008-11-11
Actually I found this page discussing the merits of Plausible Deniability and OTR vs GnuPG.  Its quite interesting to me at least, since the signature mechanism of the protocol is actually the opposite of GnuPG.  GnuPG attempts to prove the identity of the individual sender (actually this is a totally flawed assumption since the only thing digital hashes actually prove is data integrity, and not originator identity).  OTR, once the session has ended, releases the private hash key so that its possible that the actual source of the messages could have been anyone!

Here is the link: [http://www.ai.rug.nl/mas/finishedprojects/2007/PieterMichiel/introduction.html](http://www.ai.rug.nl/mas/finishedprojects/2007/PieterMichiel/introduction.html)

I'm not sure if I completely understand the premise, but I do grasp the basics.  Its quite interesting.

---

