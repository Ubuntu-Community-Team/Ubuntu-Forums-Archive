---
title: "Encryption weaknesses"
date: 2009-04-03
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-04-03
I was thinking about encryption for Internet based communications, it's weaknesses, and how these weaknesses could possibly be overcome. I'm by no means an expert in the art of cryptography but here are some of my thoughts about the weaknesses of currently existing encryption systems and some suggestions on how they could be made more secure.

The only downside to encrypting your email or instant messaging conversations through protocols like OpenPGP (PGP and GPG) and Off-the-Record Messaging is that it would extremely obvious to any third party that might be watching (ie authoritarian governments) that you were using encryption. I'm no expert but it seems as though the same software that can be used to scan for certain key words or phrases and red flag emails/IM's that contain those key words or phrases could also be used to scan for encryption. Because instead of being a series of recognizable words the encrypted email or IM would be a string of seemingly random letters and numbers. A metaphor for this might be if everyone who was sending letters through the physical mail using encryption put their letter in a red envelope instead of the standard white. Anyone who saw the red envelope would instantly know that the person sending the letter cared enough about other people not being able to know it's contents that he encrypted the message instead of sending it clear text like most people do. Giving rise to the suspicion that the sender had something to hide. Just as anyone who might be viewing the conversation of two invididuals using encryption would be able to instantly tell that they were using encryption because the text would appear to be a bunch of gibberish instead recognizable of words and sentences.

So although encryption will make your conversations private to people who might try to intercept them, the fact is that the overwhelming majority of Internet users don't use encryption. So the people who do use it will stick out like sore thumbs among the rest of their peers who don't use it. Giving rise to the suspicion that they have something to hide. Which might cause (in the case of authoritarian governments) the persons house to be raided, their computer confiscated, and their encryption keys taken from them. Or the person being threatened with prison time (or worse) if he didn't turn over his keys to the authorities.

But I have thought of two possible solutions to the above mentioned problem.

**Idea #1:** A solution for filters being setup to red flag encrypted communications between individuals could be to artificially increase the number of encrypted messages being exchanged over a given network to make the people who are using encryption blend in more with the crowd. For example, if you were charged with finding a single person out of a crowd of 100 people that might be a difficult task. But if you knew the person you were looking for was wearing a red hat that would make looking for him significantly easier. But the greater the percentage of people in that crowd who were also wearing red hats the greater the time it would take to find that person would be. Likewise, if you were tasked with finding people who were using encryption over a given network to flag as "persons of interest" the more people who were using encryption the more people who would be red flagged and the more time would be wasted on wild goose chases. Possibly not the best metaphor but hopefully you've gotten the point. Anyway, perhaps distributed computing like software could be developed that people could install on their computers and delicate a portion of their bandwidth to having the software send encrypted messages to other people using the software. This would have the effect of flooding the email and IM networks with a greater percentage of encrypted conversations. Making it much harder for eavesdropping third parties to figure out which conversations were actual people using encryption and which were just bots meant to distract them and waste their time.

**Idea #2:** Instead of using encryption based on strings of seemingly random letters and numbers being sent between the parties involved which could be vulnerable to filtering software as mentioned above. Maybe a new type of encryption algorithm could be invented that instead of using random letters and numbers used random words or phrases in place of actual words. For example the word "the" might be encrypted and transferred over the network as the phrase "kittens are cute". This would make it much harder to filter and red flag conversations where encryption was suspected to be in use because the encrypted conversations in question would require greater scrutiny to determine whether or not they were encrypted.

Those were just some ideas floating around in my head. Feel free to critique and thank you to everyone who actually bothered to read the entire message. I'm not a programmer so I have no means to actually implement any of the the ideas I have suggested. But perhaps this message will be read by someone who does. Or at the very least spark some debate. I'm aware that political discussions are banned in the Ubuntu Forums and my examples of authoritarian governments arresting people for using encryption was just an example used to illustrate a point. Not to spark a political debate about the role of government.

---

### Post by MikeTheC on 2009-04-03
Idea #1 seems vaguely similar in premise to something I read sometime within the past 12-24 months in 2600's periodical. I didn't buy that particular issue, so I don't know which one it was, but it was something to the effect of pushing data out from multiple sources to obscure what the individual in question wanted to do.

I can tell you that the latest issue of 2600 talks about inserting data in between the frames of audio data in an MP3 file. This would enable (assuming you kept what you wanted to communicate to a reasonable amount per file) transmitting of data in such a way as to not draw any particular notice. You could even use uuencode to turn the plain ASCII into 7 bit encoded data, so that it wouldn't immediately be obvious what the data in between the frames actually was.

Remember, the first rule of not being seen is to not be seen. How you choose to go about that is up to you, but that's the fundamental tenet.

---

### Post by AdotB on 2009-04-04
One possibility is to encrypt your messege in a text file, archive it using zip or tar or 7zip, and send that via attachment. Then you can place whatever giberish in the test of the email. You could also password protect the archive in addition.

Its probably not the best solution, and I have no idea how well it would work, but its there.

Also linux.com has an article on some stenography programs, what MikeTheC mentioned:
[http://www.linux.com/feature/45440]("http://www.linux.com/feature/45440")

---

### Post by blueshiftoverwatch on 2009-04-20
> **MikeTheC said:**
> I can tell you that the latest issue of 2600 talks about inserting data in between the frames of audio data in an MP3 file. This would enable (assuming you kept what you wanted to communicate to a reasonable amount per file) transmitting of data in such a way as to not draw any particular notice. You could even use uuencode to turn the plain ASCII into 7 bit encoded data, so that it wouldn't immediately be obvious what the data in between the frames actually was.
That's a good idea some types of communication. But I don't know how well that would work out for instant messaging where two or more people are sending each other messages in real time though.

To communicate efficiently using steganography over IM you would have to have a program that would automatically take your text based message, insert it into a picture or audio file, send it to the other person, then on the recipients end of the conversation have his computer automatically extract the hidden message and translate it back into a Human readable text based message all automatically. Plus the fact that if people were suddenly exchanging hundreds of pictures or audio files over IM protocols with no accompanying text it would look very suspicious and defeat the purpose of using steganography. Not to mention all of the lag time between messages while you waited for the latest picture or audio file to transfer.

---

### Post by jflaker on 2009-04-20
> **AdotB said:**
> One possibility is to encrypt your messege in a text file, archive it using zip or tar or 7zip, and send that via attachment. Then you can place whatever giberish in the test of the email. You could also password protect the archive in addition.

Its probably not the best solution, and I have no idea how well it would work, but its there.

Also linux.com has an article on some stenography programs, what MikeTheC mentioned:
[http://www.linux.com/feature/45440]("http://www.linux.com/feature/45440")

password protected archives are far from secure...It is secure from the casual computer user, but if someone wanted in, that lock is very easy to pick.

---

### Post by swoll1980 on 2009-04-20
I find that a good, old fashioned, tinfoil hat, keeps the government out of my business pretty well. If it ain't broke, don't fix it.

---

### Post by kevdog on 2009-04-20
Lets think about the end game here -- if everything is encrypted (using gpg of proven mechanism) -- who cares of the consequences!  I send gpg mail all the time -- I wish more people did.  And OTR with pidgin -- that rocks as well!

---

### Post by Lateforgym on 2009-04-20
Encrypt all you want. If someone puts a keylogger on your computer, your encryption means nothing. 

I would start with making sure no one can load something on your computer, then IF its loaded you somehow know every communication that leaves your computer (and monitor it regularly, including all open ports), lastly they need to come up with a way to thwart sniffers at back bone providers.  Oh and make sure your cant accidentally download software on your computer by clicking on a link.

Encryption is great, but till the above is addressed, I dont see the point. This is like a great episode of Cops where someone had 10 dead bolts on their door only to have the cop jump in the open porch window 5 feet down.

---

### Post by jflaker on 2009-04-20
> **Lateforgym said:**
> Snipped

Encryption is great, but till the above is addressed, I dont see the point. This is like a great episode of Cops where someone had 10 dead bolts on their door only to have the cop jump in the open porch window 5 feet down.

Most intruders come in through windows
[http://www.youtube.com/watch?v=_Sah-94wHJo&rel=0](http://www.youtube.com/watch?v=_Sah-94wHJo&rel=0)

---

### Post by Dr Small on 2009-04-20
> **kevdog said:**
> Lets think about the end game here -- if everything is encrypted (using gpg of proven mechanism) -- who cares of the consequences!  I send gpg mail all the time -- I wish more people did.  And OTR with pidgin -- that rocks as well!
and I wish all of my contacts had GnuPG keys...

---

### Post by Yashiro on 2009-04-21
When Ubuntu is installed a setup wizard should launch that allows people to quickly 
amend their profile data, 
create a GPG key,
and create a launchpad account.

The creation of the key needs to use non geeky language and impress upon people that creating this key will allow them to mail people securely.

At the moment the problem is not convincing people they need a secure key, but in creating it without too much technical jargon.

---

### Post by blueshiftoverwatch on 2009-04-22
> **Dr Small said:**
> and I wish all of my contacts had GnuPG keys...
> **Yashiro said:**
> At the moment the problem is not convincing people they need a secure key, but in creating it without too much technical jargon.
I've convinced a few of the people that I email and instant message to use GnuPG and OTR Messaging. But most don't want to bother with it. Mostly because they think it's unnecessary and that I'm just overly paranoid. But I also think that a big barrier to more people using IM encryption is the fact that it can't be used with the official IM clients (AIM, Yahoo, MSN, Google Talk, etc) that most people use. Which requires that they have to switch to an unofficial third party (Pidgin, Adium, Miranda, etc) one they've probably never heard of.

There is a service that allows people with unsupported IM clients to make use of OTR by having their unencrypted messages sent to a proxy which encrypts them. But the fact that your still sending unencrypted messages over the internet before they get to a proxy which encrypts them kind of seems like it's defeating the purpose of using encryption in the first place.

---

### Post by Daveski on 2009-04-22
> **jflaker said:**
> password protected archives are far from secure...It is secure from the casual computer user, but if someone wanted in, that lock is very easy to pick.

So the solution to the original problem is to send a mail with a boring body: "Hi, how are you. Got drunk last night, etc. etc". Attach the real message as an **Encrypted** attachment.

Any sniffing software just wouldn't be able to figure out what the attachment was, or indeed if it were encrypted data.

---

### Post by jflaker on 2009-04-26
> **Yashiro said:**
> When Ubuntu is installed a setup wizard should launch that allows people to quickly 
amend their profile data, 
create a GPG key,
and create a launchpad account.

The creation of the key needs to use non geeky language and impress upon people that creating this key will allow them to mail people securely.

At the moment the problem is not convincing people they need a secure key, but in creating it without too much technical jargon.

Have you suggested this?
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

When the gpg key is created, it should also create a public key copy in your home folder as well as prompting you to save your secret key and revocation key off-system for later use.

---

### Post by Daveski on 2009-04-29
With the UK Government hell-bent on logging all electronic comms, I would have though that most criminals must already be using encryption - I think we should all join them.

[http://www.theregister.co.uk/2009/04/27/isp_imp_reaction/](http://www.theregister.co.uk/2009/04/27/isp_imp_reaction/)

---

