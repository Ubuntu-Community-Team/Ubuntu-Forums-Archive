---
title: "I need help - is this email a scam?"
date: 2013-12-26
forum: The Cafe
---

### Post by squakie on 2013-12-26
I recevved an email in my junk folder today but it said it was about Court Notice Chicago for Jan 14 and all it had was an attachment.  The attachment was a zip file of some sort but Ubuntu's default handler couldn't open the file.

I copied it to a flash drive, booted a small Windows XP installation I have, turn off all network connections, then let Windows unzip the file.  The result was a single file:

Court_Notice_Chicago_McDermott_Will_and_Emmery

Microsoft Security Essentials found nothing for the file.

Hovering over the file shows:

Setup PDF Watermark Creator
Cool PDF Software, Inc

When I checked the properties for the file it said the size was 159kb and type was application.

Not knowing if I'm being sued or something, I clicked the file.  My computer rattled around for a while, then Microsoft Security Essentials said it had found and was fixing something.  After all of that, no new documents, nothing on the desktop, zilch.

I ran a scan with SuperAntiSpyware and it reported nothing found.

I've sent an email as it turns out those names are a law firm in Chicago.  

However, since nothing showed up on my computer, I don't know what to do.

Has anyone heard of any type of scam/virus/trojan being disguised in this way?

Thank you very much!

---

### Post by QIII on 2013-12-26
Scam.  That sort of thing is always sent snail mail.

I'd gather up every anti-virus tool I had and start scanning.

---

### Post by Irihapeti on 2013-12-26
If I get a dodgy email, I look at the source. Ctrl-U in Thunderbird and Firefox; not sure what it is in other programs. That will tell you where it originally came from, along with a lot of other stuff.

Did it originate from the law firm? Or, as I've often found, was the original address something that has nothing to do with where the email is supposed to be coming from?

From what I've heard, pdf files are quite capable of containing malware. No doubt someone else more knowledgeable will chime in and confirm that.

Edit: I would think that kind of thing, when genuine, would be sent by registered mail (or whatever it's called where you live).

---

### Post by Iowan on 2013-12-26
Just my opinion - I don't think the court system uses email as official notice... yet.

---

### Post by CharlesA on 2013-12-26
> **Irihapeti said:**
> Edit: I would think that kind of thing, when genuine, would be sent by registered mail (or whatever it's called where you live).

This. Does Ctrl +U show headers in Thunderbird?

---

### Post by Irihapeti on 2013-12-26
> **CharlesA said:**
> This. Does Ctrl +U show headers in Thunderbird?

Ctrl+U shows the entire email source, which includes headers.

You can also use "view->headers->all" when reading a message, but I prefer not to load a message if I'm not sure what it is.

---

### Post by CharlesA on 2013-12-26
> **Irihapeti said:**
> Ctrl+U shows the entire email source, which includes headers.

You can also use "view->headers->all" when reading a message, but I prefer not to load a message if I'm not sure what it is.

Sweet! I've been doing the view > headers > all thing, but sometimes I forget to change it back to "normal" and print an entire page of headers on accident...

---

### Post by deadflowr on 2013-12-26
> **QIII said:**
> Scam.  That sort of thing is always sent snail mail.
or a guy with a badge comes to the door.

The court system won't send you email's unless you initiate it.
Like most government agencies.

---

### Post by stalkingwolf on 2013-12-27
notify the law firm im sure they would appreciate it.

---

### Post by mips on 2013-12-27
It's quite simple, if you have to ask then it's a scam ;)

---

### Post by Old_Grey_Wolf on 2013-12-27
From their [McDermott's website]("http://www.mwe.com/contact/uniGC.aspx?xpST=ContactUs") > We have recently received reports of a fraudulent e-mail incident (also known as spoofing) using McDermott and other law firms as the sender (e.g. [email]no_reply@mwe.com[/email]). The message could be identified by the subject heading &#8220;Notice to Appear at Court" and may contain instructions to obtain personal information.   Should you receive this message, please delete it immediately and do not open any attachment as it may contain a virus or other malware.


---

### Post by squakie on 2013-12-28
I don't know what to make of it.  I used to live in Illinois until mid-2009, so I thought this might  be legit.  I can't tell from the source just exactly where it's from.  Does this line indicate anything or do I need to look elsewhere?  Where is this from?

```

Authentication-Results: mta1250.mail.bf1.yahoo.com  from=mwe.com; domainkeys=neutral (no sig);  from=mwe.com; dkim=neutral (no sig)
Received: from 127.0.0.1  (HELO mwe.com) (24.172.186.234)
  by mta1250.mail.bf1.yahoo.com with SMTP; Thu, 26 Dec 2013 11:09:14 -0800
```

I never got a reply back from the law firm even though I requested one.

I also received another one of these today, except for a valid law firm in Washington.

I don't know what to make of it, and I don't want to miss something happening to me in a court.

I didn't have my network adapters enabled in Windows when I opened the zip file.  When it was executing the resulting file, Microsoft Security Essentials did say something about some err and fixing it automatically.  I ran SuperAntiSpyware afterwards with nothing found.

I seem to be having a problem with my Yahoo email since then, however, even via Thuderbird.  I try to send a message and get an error saying it couldn't validate my logon or some such thing to the server.  It shows connected to the server, but the message is never sent.  I don't see how anything could have happened - Windows is on a seperate partition, I never had the networking activated and grub works fine.  Is this just some sort of coincidence?

Thank you for all of your help!

---

### Post by CharlesA on 2013-12-28
You'd have to look at the entire header of the email. The part you just posted only tells you if the message is signed with DKIM (which it isn't).

---

### Post by PJs Ronin on 2013-12-28
> **squakie said:**
> 
I never got a reply back from the law firm even though I requested one.

I also received another one of these today, except for a valid law firm in Washington.

I don't know what to make of it, and I don't want to miss something happening to me in a court

Unless your name is Ted Bundy, no lawyer in the country is going to use email as first point of contact.

Your spam filter is working, let it do its job.

---

### Post by CharlesA on 2013-12-28
> **PJs Ronin said:**
> Unless your name is Ted Bundy, no lawyer in the country is going to use email as first point of contact.

Your spam filter is working, let it do its job.

+9001.

---

### Post by squakie on 2013-12-28
> **Old_Grey_Wolf said:**
> From their [McDermott's website]("http://www.mwe.com/contact/uniGC.aspx?xpST=ContactUs")

THANK YOU!!!!  That makes me feel much better knowing someone in Illinois isn't actually sueing me (it would not be an impossible thing unfortunately).

Sounds like I can get rid of the one from Washington as well!

You have made it so I can sleep much easier tonight!

Thank you SO much!

---

### Post by grahammechanical on 2013-12-28
These to links to news on the BBC web site make interesting reading.

Twelve cyber-scams of Christmas

[http://www.bbc.co.uk/news/technology-25200338](http://www.bbc.co.uk/news/technology-25200338)

> A virulent form of ransomware has now affected about a quarter of a million Windows computers, according to a report by security researchers.

[http://www.bbc.co.uk/news/technology-25506020](http://www.bbc.co.uk/news/technology-25506020)

> [COLOR=#333333][FONT=Arial]Early examples were spread via spam emails that asked the user to click on a Zip-archived extension identified as being a customer complaint about the recipient's organisation.[/FONT][/COLOR]

Forewarned is fore armed.

Regards.

---

### Post by deadflowr on 2013-12-28
Unless a law firm is an old curmudgeon guy, with a slight early morning drinking problem, who has employed only one spunky go getter whose whole existence seems to be helping some inner city kids save their favorite hangout from bad people, all law firms to me are [wolfram and hart]("http://en.wikipedia.org/wiki/Wolfram_%26_Hart").;)

---

### Post by Old_Grey_Wolf on 2013-12-28
> **squakie said:**
> THANK YOU!!!!  That makes me feel much better knowing someone in Illinois isn't actually sueing me (it would not be an impossible thing unfortunately).

Sounds like I can get rid of the one from Washington as well!

You have made it so I can sleep much easier tonight!

Thank you SO much!

I'm glad the information from the law firm helped.

However, I hope the attached file in that email didn't infect your Microsoft Windows install.

The law firm in Washington wouldn't have sent you email either. ;)

---

### Post by squakie on 2013-12-28
I ran full scans using SuperAntiSpyware and with Microsoft Security Essentials (admittedly 2-day old definitions as I didn't want to turn on the networking until things checked out) and they found nothing.

It interesting - I think the law firm posted that after I inquired about my mail - it didn't show when I went to their website - but that sure helped me a LOT!!  Thanks again!

I did check, and it is possible in some states to actually get court orders via email, and that is what really had me worried.  With this news I will now be filing any such emails in the bit bucket.

I suppose this thread has made me seem extremely stupid, but I was really worried due to the aforementioned possibilities of being sued in Illinois.  I am so glad that wasn't the case!

Thanks everyone!

---

### Post by 3rdalbum on 2013-12-29
> **squakie said:**
> I recevved an email in my junk folder today but it said it was about Court Notice Chicago for Jan 14 and all it had was an attachment.  The attachment was a zip file of some sort but Ubuntu's default handler couldn't open the file.

For me, I would have thought "Hmm, okay, so it appears to be a Zip file but it obviously can't because Ubuntu can't open it". Then I would have used the 'file' command to tell me what it really was.

Open a terminal (Control-Alt-T) and type the word "file " but with a space at the end. Then drag the file to the terminal, bring the terminal back to the front again and press Enter.

It would have shown me this:

```

chris@chris-desktop:~$ file '/home/chris/Desktop/courtnotice.zip'
/home/chris/Desktop/courtnotice.zip: PE32 executable (GUI) Intel 80386 (stripped to external PDB), for MS Windows, UPX compressed

```

Straight away you can tell it's not a Zip file. It's an "executable for MS Windows", which in other words is a Windows program.

A Zip file would read something like:

```
/home/chris/Desktop/courtnotice.zip: Zip archive data, at least v2.0 to extract
```

---

### Post by monkeybrain20122 on 2013-12-29
It would be freaky if said zip file opens in Wine. :) Wonder if WineHQ gives platinum rating to Windows viruses.

---

### Post by squakie on 2013-12-30
Well, it's nice to suspicious of a zipped attachment - hence why I ran Microsoft Security Essentials on the entire thing before unzipping it - and it found nothing.  Only after running it did Microsoft Security Essentials detect something a deal with it.  I would not normally open such thing, but see my aforementioned comments about the real possibility of a lawsuit from Illinois, coupled with what I researched first - it is possible in some instances to send court notices via email.  I took the precaution of turning off networking first and scanning the zipped file.  I left networking off while I executed the file.  It was the only things I could do given my circumstance.  If it had said something like "congradulations you're being sued" I still would have opened it.

With the aforementioned scans done after the execution, I am now going to boot Windows, turn on networking, download the latest updates and run complete scans again.

It's all I can do.

Thanks again everyone.  Thread has already been marked as solved.

---

### Post by 3rdalbum on 2013-12-30
> **squakie said:**
> Well, it's nice to suspicious of a zipped attachment - hence why I ran Microsoft Security Essentials on the entire thing before unzipping it - and it found nothing.

Few Windows users know this, and no anti-virus software vendor will tell you.

Every year, there are thousands or even tens of thousands of new viruses and malware released for Windows. An anti-virus program unfortunately can't tell whether a file is infected unless the pattern matches something that's already been programmed into its database.

I hear you ask: "How do the anti-virus software developers manage to keep up with adding new viruses to the database?"

The answer is, they don't (see attached graph). The most virulent viruses get put into the anti-virus databases, the less well-known ones don't get put into the database. A gap of some thousands of viruses. Oh, the better anti-virus programs these days can detect the kind of behavior that an active virus will create, but they are entirely toothless at stopping new viruses or lesser-known viruses from actually infecting your system in the first place.

Not only is it a bad idea to 100% trust your anti-virus software, but the idea has become even worse in the three minutes it took you to read this message.

[ATTACH=CONFIG]249027[/ATTACH]

---

### Post by CharlesA on 2013-12-30
> **3rdalbum said:**
> 
Not only is it a bad idea to 100% trust your anti-virus software, but the idea has become even worse in the three minutes it took you to read this message.

This. Heuristics can only go so far.

---

### Post by t0p on 2013-12-30
> **squakie said:**
> I did check, and it is possible in some states to actually get court orders via email

That is frightening - so people can get sued *in absentia* or have arrest warrants issued because they didn't look in the spam bin?  Or because they thought it must be a hoax because it's such a bizarre idea?  Plenty of people don't look in the spam folder very often... plenty of people don't bother checking their email very frequently.  I have email accounts that I use just for stuff like registering with web sites, I don't check them frequently because I don't expect to receive anything.  Insanity! (not you squakie - I mean the legislatures that allow this craziness.)

---

### Post by Old_Grey_Wolf on 2013-12-30
> **squakie said:**
> I did check, and it is possible in some states to actually get court orders via email, and that is what really had me worried.  

Where I live, if I get a letter notice of jury duty I can go on-line and register for them to sent me an email when I really need to show up at the court house. I can check every day on the website, call a phone number, or get an email during the 2 week jury summons time period. I have to initiate the interaction of using email. They don't just send me an email anytime they want to.

---

### Post by QIII on 2013-12-30
Same here.  Summons comes on paper in snail mail.  I can use the web to respond.

I've been subpoenaed for testimony a couple of times, and those were delivered by a Sheriff's Deputy in person.

---

### Post by squakie on 2013-12-30
If you research it on the net, it is possible in some cases to get a notice via email.  Documented legal cases.

As far as limitations of anti-viri and anti-trojan-rootkit etc., software, that I am also quite aware of.  As I mentioned, this is one case where I had to take the chance.  Better that than having the sherrif show up and throw my butt in jail.  I was aware of the risks and willing to take them in this case.  My Windows install is only used because Linux does not support any of the 3 seperate video capture devices and I am still finding more old VHS tapes to scan in for the 3 media centers.  I can reload it with no problem.  There is no personal data in that small install - because of this exact reason and the known holes in XP (soon to become flood gates come April).

Again, the thread is marked as solved.  Please direct additional comments elsewhere - perhaps the Cafe.

---

### Post by Iowan on 2013-12-30
> **squakie said:**
> Again, the thread is marked as solved.  Please direct additional comments elsewhere - perhaps the Cafe.I'll take that as a request to close...

---

