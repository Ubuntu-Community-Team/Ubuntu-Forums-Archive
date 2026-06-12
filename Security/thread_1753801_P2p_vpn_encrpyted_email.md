---
title: "P2p vpn encrpyted email"
date: 2011-05-09
forum: Security
---

### Post by coljohnhannibalsmith on 2011-05-09
Hello,

I have some ideas about how email could be made much more secure; by  merely modifying and using existing technologies in an unorthodox way.

Present email technology requires the transfer and storage of emails on  servers at many hops between the sender and recipient making it possible  for 'anyone' to view the contents of these emails at any waypoint.

Here are my ideas to resolve this situation:

Instead of using the server forwarding system, email could be sent P2P  over a VPN established between the sender and recipient hosts.  This  system should be designed 'without' PKI. Also a contact database could  be maintained on both systems; since such a system will 'not' be  able to use DNS.  I think current 'Chat' programs are already using  similar technology.  This VPN could employ all types of encryption  technology, opportunistically, to take advantage of the available  bandwidth.  Also, to resolve the problem of the recipient system 'not'  being available at send-time, an application could be created that will  store the email on the sender's system until the recipient system is  available.  This design would do much to limit MIM attacks; making the  only possible way of obtaining the contents of the email, interception  of the Diffie-Hellman key exchange, or the 'social' compromising of the  recipient; which 'no' encryption system can protect against.  Such a system could potentially make 'server' based email ***a thing of the past!***

***Existing email, chat, file-sharing clients and 'browsers' could be modified to add this 'feature' as a plug-in; and use of the TOR network, could be added as a default option!***  I'd love to see this as a Firefox plugin!

I would like to hear what you think of this idea.

[IMG]http://www.cs.virginia.edu/%7Emngroup/hypercast/images/network.jpg[/IMG]

Also, the following logo, which is an adaptation of the Ubuntu ***'Circle of Friends'*** logo could be used for this project:

[IMG]http://www.masternewmedia.org/images/p2p-cooperation-id5561121_size480.jpg[/IMG]
I apologize for using such BIG images.  I couldn't find smaller ones.  I'll also be careful to avoid using watermaked images.




Hannibal

---

### Post by perspectoff on 2011-05-09
Or, you could just use Thunderbird 3.1 with Enigmail (to facilitate PGP encryption).

It's pretty trivial to set up. It allows you to create a PGP keypair (with GPG, which is installed by default in (K)Ubuntu), upload it to a keyserver, and encrypt and sign your email by default, if you'd like.

It works with IMAP servers (including free Gmail and Yahoo Mail accounts).

I like the instructions at Ubuntuguide:

[http://ubuntuguide.org/wiki/Email_with_PGP](http://ubuntuguide.org/wiki/Email_with_PGP)

or Kubuntuguide:

[http://www.kubuntuguide.info/index.php/Email_with_PGP](http://www.kubuntuguide.info/index.php/Email_with_PGP)

A lot less hassle than what you are proposing.

If you want to keep your email in house, just set up an IMAP server in house (instead of using Gmail or Yahoo Mail or whatever).

---

### Post by coljohnhannibalsmith on 2011-05-09
> **perspectoff said:**
> A lot less hassle than what you are proposing.

If you want to keep your email in house, just set up an IMAP server in house (instead of using Gmail or Yahoo Mail or whatever).

Thank you for your kind reply and all the documentation links.  I'm flattered that someone of your stature responded.

BTW, I've already considered what your suggesting, and it doesn't eliminate the ***servers*** or ***PKI.***  My requirement is to eliminate the servers ***and*** PKI ***entirely.***  Also, my other requirement is to have encryption turned-on as a default, without requiring user intervention.  Also, the technical details of setting-up GPG require that 'both' users agree to have it turned on, which as a technical and social matter is very difficult in practice.

[B][I]My suggestion resolves 'all' of these issues.
[/I][/B]
Your suggstion about setting up an IMAP server ***inhouse***, is something I'd like to investigate more.  Ultimately, I don't think it will meet my requirements; since this appears to require pre-arranged cooperation on both ends, and doesn't appear to be a P2P solution, which is what I'm after. ***Your suggestion 'appears' to be an enterprise solution, which is not my angle at all.*** And, I think it will ultimately be ***more*** of a hassle than what I'm suggesting.  However, I suspect this research will teach me much about the technical details of what I'm proposing.

BTW, I don't think what I'm suggesting will be all that much of a hassle.  The solution I'm proposing provides the ***maximum*** possible security, and the distribution of the app/plugin is the only pre-arranged cooperation needed between the correspondents.

Of course the development time and effort involved in the creation of this app/plugin is where the bottleneck lies.  However development of 'all' kinds of projects are being done 'all' the time, and within our community.  [COLOR=Red]***Both Sourceforge and the TOR-Project are examples.***[/COLOR]

I'll educate myself more by reviewing the docs you generously provided.




Respectfully, Hannibal

---

### Post by rookcifer on 2011-05-10
How do you solve the problem of authentication (i.e. checking that the e-mail sent to Alice really was from Bob and not Mallory?)  Without authentication, encrypted e-mail is almost worthless.

Also you said you want to eliminate PKI, but then made mention of using Diffie-Hellman, which was really instrumental in public-crypto.

---

### Post by deconstrained on 2011-05-10
Without PKI or authentication exchanges of some sort, one cannot be certain that the host of the sender or recepient corresponds to the intended person, unless said person's computer and master key have been compromised (then all is lost). Furthermore, without a central tracking server or having to send a recipient/sender your IP address, the next best way of identifying/connecting to a host is with DNS, which is far from secure, and this is what makes PKI especially important.

I think a good model to base this on would be that of Bitcoin - a sort of distributed P2P key signing network.

---

### Post by coljohnhannibalsmith on 2011-05-13
I see your point; however, I believe the 'Zfone' project (Philip Zimmerman) has managed to devise a key-exchange system that doesn't use PKI.  ***Granted, this is for voice communications, not email.***  Just on the face of it, it seems to me that PKI might be a vulnerability.  The FBI's former Carnivore system was able to intercept the key-exchange; however, this may be possible even without PKI.

All said, I think P2P email will ultimately be more secure than the present server based system.  ***P2P email, would essentially use the host systems as the servers.***

Your replys have taught me that I have much to learn; to which end I will apply myself diligently.


Does anyone else have suggestions about which technologies I should research?




Thanks Hannibal

---

### Post by rookcifer on 2011-05-13
> **coljohnhannibalsmith said:**
> The FBI's former Carnivore system was able to intercept the key-exchange; however, this may be possible even without PKI.

Have any references for this?  The DH key-exchange protocol was meant to be secure even on an unsecured line.  From Wiki:
> 
The Diffie–Hellman key exchange method allows two parties that have no prior knowledge of each other to jointly establish a shared secret key **over an insecure communications channel.** This key can then be used to encrypt subsequent communications using a symmetric key cipher.

Furthermore, RSA and DSA (other popular public-key cryptosystems) both utilize public/private key-pairs, so if the public key gets intercepted, it really does the attacker no good.  There's no key-exchange for Mallory to intercept as it's done publicly with the assumption Mallory will be listening.

> All said, I think P2P email will ultimately be more secure than the present server based system.  ***P2P email, would essentially use the host systems as the servers.***

It sounds to me like you're trying to accomplish what has already been done with OTR -- it affords perfect forward secrecy whilst still allowing one to authenticate exactly who it is one is talking to (although one must authenticate the public key fingerprint some other way, like via a phone call or in person, etc.  The medium does not have to be secure, however.)  OTR as it stands is used only for chat protocols, though I see no reason it couldn't be used for e-mail.

I guess my only question is what does sending encrypted e-mail over an insecure channel really matter?  The whole purpose of PKI is to secure data over insecure mediums like the Internet.  I see no security benefit of sending e-mail over a decentralized BitTorrent like network.

> Does anyone else have suggestions about which technologies I should research?

Join ##crypto on Freenode.  You will get expert feedback (and criticism) there by people who know a lot more about this than me.

---

### Post by coljohnhannibalsmith on 2011-05-13
> **rookcifer said:**
> Have any references for this?  The DH key-exchange protocol was meant to be secure even on an unsecured line.

It sounds to me like you're trying to accomplish what has already been done with OTR -- it affords perfect forward secrecy whilst still allowing one to authenticate exactly who it is one is talking to (although one must authenticate the public key fingerprint some other way, like via a phone call or in person, etc.  The medium does not have to be secure, however.)  OTR as it stands is used only for chat protocols, though I see no reason it couldn't be used for e-mail.

I see no security benefit of sending e-mail over a decentralized BitTorrent like network.

Join ##crypto on Freenode.  You will get expert feedback (and criticism) there by people who know a lot more about this than me.

1. The system I'm thinking of is Magic Lantern not Carnivore:

[http://en.wikipedia.org/wiki/Magic_Lantern_%28software%29]("http://en.wikipedia.org/wiki/Magic_Lantern_%28software%29")

**Example deployment method**

 The FBI intends to deploy Magic Lantern in the form of an [e-mail attachment]("http://en.wikipedia.org/wiki/E-mail_attachment"). When the attachment is opened, it installs a [trojan horse]("http://en.wikipedia.org/wiki/Trojan_horse_%28computing%29") on the suspect's computer. ***The trojan horse is activated when the suspect uses [PGP]("http://en.wikipedia.org/wiki/Pretty_Good_Privacy")  encryption,*** often used to increase the security of sent e-mail  messages. When activated, the trojan horse will log the PGP password,  which allows the FBI to decrypt user communications.[[5]]("http://en.wikipedia.org/wiki/Magic_Lantern_%28software%29#cite_note-4")[[6]]("http://en.wikipedia.org/wiki/Magic_Lantern_%28software%29#cite_note-5") Spokesmen for the FBI soon confirmed the existence of a program  called Magic Lantern. They denied that it had been deployed, and they  declined to comment further.[[7]]("http://en.wikipedia.org/wiki/Magic_Lantern_%28software%29#cite_note-6")

***Carnivore (which was renamed DCS2000), was replaced by Narus Insight in 2005:***

[http://en.wikipedia.org/wiki/Narus](http://en.wikipedia.org/wiki/Narus)

2. Yes, OTR exactly, only with ***permanment*** rather than, or in addition to, ***instant ***messaging capability.  What I'm thinking of is basically a ***"permanent-message"*** plugin for OTR; however I didn't know what is was called before you replied.  Thank you for this.

3. I disagree with your assessment; ***but I can see that I'm way out of my league here. ***I'll research OTR as you suggested; and I'll also investigate the previous poster's suggestion of Bitcoin, which uses P2P encryption:

[http://en.wikipedia.org/wiki/Bitcoin](http://en.wikipedia.org/wiki/Bitcoin)

**Bitcoin** is a [digital currency]("http://en.wikipedia.org/wiki/Digital_currency") created in 2009 by Satoshi Nakamoto. The name also refers to the [open source]("http://en.wikipedia.org/wiki/Open_source")  software he designed that uses it, and the peer-to-peer network that it  forms. Unlike most currencies, bitcoin does not rely on trusting any  central issuer. Bitcoin uses a [distributed database]("http://en.wikipedia.org/wiki/Distributed_database") spread across nodes of a [peer-to-peer]("http://en.wikipedia.org/wiki/Peer-to-peer") network to journal transactions, and uses [cryptography]("http://en.wikipedia.org/wiki/Cryptography")  in order to provide basic security functions, such as ensuring that  bitcoins can only be spent by the person who owns them, and never more  than once.

 Bitcoin's design allows for anonymous ownership and transfers of  value. Bitcoins can be saved on a personal computer in the form of a *wallet file* or kept with a third party *wallet service*, and in either case Bitcoins can be sent over the Internet to anyone with a *Bitcoin address*.  [B]*Bitcoin's peer-to-peer topology and lack of central administration makes  it infeasible for any authority, governmental or otherwise, to  manipulate the value of bitcoins or induce [inflation]("http://en.wikipedia.org/wiki/Inflation") by producing more of them.[*[I][citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")]
[/I] [/B]
 Bitcoin is one of the first implementations of a concept called 'cryptocurrency', first described in 1998 by Wei Dai on the [cypherpunk mailing list]("http://en.wikipedia.org/wiki/Cypherpunk_mailing_list").[[1]]("http://en.wikipedia.org/wiki/Bitcoin#cite_note-0")[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*]

And yes, I'll definitely join ##crypto on Freenode.[B][I] I have much to learn...


[/I][/B]***I usually know where I need to go; but learning how to get there is what I usually have to ask for help with...***





Thanks Hannibal

---

### Post by mI13eo6PUn3CN0eP on 2011-05-13
I like that idea! I wonder how feasible it would be to create some kind of P2p "Internet" Wifi mesh whereby computers with real Internet function as exit nodes. Cut out the ISPs all together.

---

### Post by coljohnhannibalsmith on 2011-05-13
> **mI13eo6PUn3CN0eP said:**
> I like that idea! I wonder how feasible it would be to create some kind of P2p "Internet" Wifi mesh whereby computers with real Internet function as exit nodes. Cut out the ISPs all together.

Wow, I like the way you think...:D


I'm wanting to do this for cell phones as well...  Here's my other thread:

[http://ubuntuforums.org/showthread.php?t=1717966](http://ubuntuforums.org/showthread.php?t=1717966)


I also have a thread on P2P search engines:

[http://ubuntuforums.org/showthread.php?t=1719452](http://ubuntuforums.org/showthread.php?t=1719452)

[IMG]http://www.drweb.de/magazin/wp-content/uploads/2008/06/kaskelix.png[/IMG]


[COLOR=Blue]**Hannibal**[/COLOR]

---

### Post by rookcifer on 2011-05-14
Hannibal, I love it when a plan comes together.

---

### Post by coljohnhannibalsmith on 2011-05-14
> **rookcifer said:**
> Hannibal, I love it when a plan comes together.

***Thanks Face Man...***

[IMG]http://www.oocities.org/steph_private_collection/RETAIL/IMAGES/ateam.jpg[/IMG]

---

