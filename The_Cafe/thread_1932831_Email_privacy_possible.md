---
title: "Email privacy possible?"
date: 2012-02-28
forum: The Cafe
---

### Post by johnd357 on 2012-02-28
Gmail is great, but in a world where online privacy is getting  harder and harder, I find it a priority to leave free webmail services.  Sadly, I can't see any great alternatives.


Running my own VPS  mailserver poses it's own risks. I certainly trust Google more than I  trust myself to be able to run a secure mailserver that won't get  compromised, or won't periodically fail to receive or send emails, or  won't get filled with spam. At the end of the day, you still have to put  your trust in someone. Why should I trust my VPS provider more than I  trust Google not to read my mail?


What are your thoughts? I'd love to run my own mail server, but I don't see the benefits outweighing the costs.


(And I know about PGP, but sadly that's just not practical to use everywhere.)

---

### Post by samalex on 2012-02-28
It's costly but collocating your own box or getting a business connection to your home and hosting there are really the only options.  Either way you control the box completely which will give you privacy at least on the server, especially if you encrypt the file system.  

Just remember that once the email hits the Internet there's no security that would prevent someone else from reading it except for as you mentioned GPG/PGP -- think of a postcard in the mail, everyone can see what it says.  But at least your repository of emails and data would be under your control and no one else's by hosting your own box.

---

### Post by aeronutt on 2012-02-28
lavabit.com and zoho.com advertise pretty good privacy policies. I recently changed from yahoo to zoho, and am happy so far. Might have chosen lavabit if I'd known about it, but zoho has a few million users, lavabit is less than 1/2 million last I checked.

---

### Post by samalex on 2012-02-28
Here's a question, would you change to another email provider if you had the same email address for years?  I've been with GMail since they rolled it out mid-2004, so I have 8 years worth of content on there.  I do keep local copies of it, but given my email address is pretty much my identity on so many sites at this point it's just not feasible for me to move to another server.  I can imagine lots of people being in this same situation, which I guess just proves that it's not a good idea to use a domain you don't own as your primary email account :-/

But can lavabit.com or zoho.com support your own domain?  If so this is something I may look at as well though I don't think I'd be able to drop my Google account if nothing else to prevent someone else from getting it and possibly reactivating accounts I've forgotten about.

Sam

---

### Post by aeronutt on 2012-02-28
I'd been with yahoo for 10+ years...was painful to change. I don't know if zoho or lavabit can host your own domain.

---

### Post by SeijiSensei on 2012-02-28
One model you might consider if you already have a VPS is to build an OpenVPN tunnel between a machine in your home or office and the VPS server.  Let the VPS machine handle the external mail traffic and deliver the mail over the tunnel to the box in your home.  That's effectively the system I've run for a few years now.  It's much cheaper than having a business-class IP connection into your home, too.

As for handling spam and viruses, I strongly endorse [MailScanner]("http://www.mailscanner.info/").  I've used it in conjunction with ClamAV and SpamAssassin to scan mail for about a decade now with great success.

---

### Post by Irregular Joe on 2012-02-28
I would think that setting up TLS certificates between the VPS and your local network might work just as well for encryption, but many people don't want to keep port open to their local network.

I route my mail to a VPS, then use uucp over ssh to relay it to my local network.  The uucp protocols have been around forever, and was used in the early Internet days, when everything was done over dial-up phone relays. Having ssh as the underlying protocol provides encryption and security, as you only need to have an ssh port (22 or other) open on your firewall.  Some information can be found at [http://www.bortzmeyer.org/uucp-over-ssh.html](http://www.bortzmeyer.org/uucp-over-ssh.html)

---

### Post by Slug71 on 2012-02-28
I just started giving Lavabit a try. Really liking it and may just make that my default here pretty soon.

---

### Post by blueturtl on 2012-02-28
Just start using PGP to decrypt your incoming and encrypt your outgoing emails and what provider you use will be pretty much irrelevant. Can't see all the fuss about who is keeping your emails when they are pretty much readable by anyone who can capture the message between the destination points. Of course it requires a little work from your major correspondents (they need to encrypt the messages they send you with your public key) but once it's set up it's quite easy.

---

### Post by Gremlinzzz on 2012-02-28
Email privacy possible? No:popcorn:

---

### Post by MasterNetra on 2012-02-28
Privacy as in no one else other then the sender can see the message? No, but I suppose you could always try for good old fashion writing encrytion where you write cryptly. Might garner some unwanted interest from the government though, unless they crack it and find its really nothing of interest to them.

---

### Post by Dry Lips on 2012-02-29
I just signed up for zoho.com just in order to check them out. I had some problems accessing my mail through thunderbird, so I asked a question on their forums. I was much surprised when I saw that my gravatar image was automatically selected as an avatar.

Wot?

So basically, there is some kind of sharing of information between gravatar and zoho.com.
I used the same email adress to sign up with gravatar and zoho, so I guess that's where they got the image. 

I think I'll just stick with lavabit from now on.

---

### Post by haqking on 2012-02-29
> **Dry Lips said:**
> I just signed up for zoho.com just in order to check them out. I had some problems accessing my mail through thunderbird, so I asked a question on their forums. I was much surprised when I saw that my gravatar image was automatically selected as an avatar.

Wot?

So basically, there is some kind of sharing of information between gravatar and zoho.com.
I used the same email adress to sign up with gravatar and zoho, so I guess that's where they got the image. 

I think I'll just stick with lavabit from now on.

thats the purpose of gravatar

---

### Post by Dry Lips on 2012-02-29
> **haqking said:**
> thats the purpose of gravatar

I thought it just applied for wordpress... Duh!

---

### Post by haqking on 2012-02-29
> **Dry Lips said:**
> I thought it just applied for wordpress... Duh!

when it asks you to create one it tells you what it is.

The G stands for globally

[http://en.gravatar.com/](http://en.gravatar.com/)

> Your Gravatar is an image that follows you from site to site appearing beside your name when you do things like comment or post on a blog

---

### Post by Dry Lips on 2012-02-29
I just replaced the primary email address registered with gravatar to another one that I don't use. I want gravatar for my wordpress account, but nothing else.

---

### Post by ph4nt0m117 on 2012-02-29
Thought, do you have a laptop/desktop with 2 gigs+ ram and 2.4 ghz+ processor with no use of it?

Depending on where your "mail" comes from, you could set up a mail server inside of PFSense, making it ten times harder to get to your mail, if you know (in fact) what you're doing.  Even though PFSense is miniBSD, I'm sure that SOMEWHERE there is a server app to run in BSD for a mail server.  Set the mail server behind the firewall(s) and your good for that.  Even moreso if you set up a honeypot inside of PFSense to route idiot hackers to a pile of viruses for all types of operating systems!  Make an email in a junk computer, attach a trojan.VUNdoo and you send it to the honeypots email account, if you will, and store it inside there.  Make about 12-20 for each virus you have made/acquired and send them inside the honeypot.  Program them right and they won't do a thing to your hardware, specifically, but tell them that MAC Address 29:94:58:37:92 or whatever address is an attacker when they enter the server to retrieve a file to peer on, then when "29:94:58:37:92" or whome ever that is -not- one of your machines, nor someone you set permissions for and that you trust, then when the file is downloaded, and opened, they get trojan.VUNdoo in return for their hard work and most of windows is deleted or corrupted.  Do this for BSD, OSX, Windows, LINUX, whatever you feel like, and people figure out that tapping this server is either a stupid idea, or, it eggs them on for several months, ruining operating system after operating system until they give up or botnet attack.  Since botnets are sort of expensive to rent and time consuming, it less than possible for a botnet to penetrate your system, if set up correctly.

Just a thought.

---

### Post by bouncingwilf on 2012-02-29
+1 for lavabit

Bouncingwilf

---

### Post by Lucradia on 2012-02-29
In the words of wisdom of Bubs' from Homestar Ruiner (Telltale Games):

Bubs : I'm your internet provider man! I read all yer emails!

---

