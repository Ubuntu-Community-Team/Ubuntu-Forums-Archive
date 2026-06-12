---
title: "email attachment"
date: 2010-10-30
forum: Security
---

### Post by florus on 2010-10-30
I have received an email with a .csv attachment from a bank, and need to know how to view the attachment without risk. Using View>Message Source I see a large solid block of random upper and lower case characters, whereas I would expect to see some readable text mixed in. The email subject and the attachment name both contain data specific to me, but the text of the email consists largely of disclaimers with no mention of my name or any clue as to the nature of the attachment.
I am using Thunderbird as my email client.

---

### Post by squaregoldfish on 2010-10-30
You're unlikely to see any sensible data by viewing the message source, as attachments are encoded in some way.

The safest thing to do is not to look at it at all, naturally - you should probably have a go at your bank for sending unsolicited (and presumably unsecured) attachments via email. 

However, you should be able to save the file to disk and look at it using vi or your favourite text editor - there's no real chance of executing anything by mistake if you do that.

Steve

---

### Post by florus on 2010-10-30
Thanks, Steve, that worked nicely. It was a genuine email, but a very peculiar one from a bank I have no direct dealings with.:confused:

---

### Post by ajgreeny on 2010-10-30
By the way, a **.csv** is a text file known as "**c**omma **s**eparated **v**alues" and would normally open by default in a spreadsheet application, eg gnumeric or OOo Calc.

But very strange behaviour from a bank, I agree.

---

### Post by squaregoldfish on 2010-10-30
Naturally, but if I received an unsolicited attachment of any kind I wouldn't trust it further than I could throw it. Hence the suggestion of not auto-opening it in any way.

Just because it says it's a csv file, it doesn't mean it actually is.

Steve.

---

### Post by OpSecShellshock on 2010-10-30
> **florus said:**
> Thanks, Steve, that worked nicely. It was a genuine email, but a very peculiar one from a bank I have no direct dealings with.:confused:

If it's a bank where you don't have any accounts on top of all of the other suspicious stuff, I would really, really not open the attachment. On Linux it shouldn't be a big deal. Just right click, then select "open with" and go to your default spreadsheet application. If it's not really a .csv file, then it won't open. Likely, it's a Windows executable of some sort.

You can also check the headers (which someone who uses Thunderbird will have to explain because I'm not familiar with how it's done with that). It will contain, largely in reverse order from the top down, a list of the mail servers it's passed through on the way to you. There's bound to be some header spoofing if it's malicious in nature, but usually people who do that only mess with the ones in the middle, so the server on the very bottom of the list is probably the point of origin. Is it the domain of the bank in question?

Another handy trick with the headers is to make note of the time zones. I think most SMTP traffic between servers is expressed in GMT/UTC, but the local time of the server is also in there because there will be the GMT + or - a certain number of hours. You should be able to throw that into a Google search and find out what region of the world uses a particular time relative to GMT, which in turn will tell you (broadly speaking) what part of the world each server was in. As long as that line in the header isn't spoofed, I mean.

Anyway, that's not really necessary here since you know it's not your bank anyway.

---

### Post by florus on 2010-10-30
I thought it might be genuine as the body of the email contained the instructions:
> [SIZE=2]*** Please do not reply to this Message ***[/SIZE][SIZE=2]
[/SIZE]> [FONT=monospace]If the message is received by anyone other than the addressee, please return the message to the sender by replying to it[/FONT][FONT=monospace]
[/FONT]> [FONT=monospace]It is the responsibility of the recipient to ensure that the [/FONT][FONT=monospace]opening [/FONT][FONT=monospace]of this message [/FONT][FONT=monospace]will not adversely affect its systems or data[/FONT][FONT=monospace]
That can only be from a UK bank - no one else has that particular brand of stupidity. The attachment was not one I would have expected, and was presumably sent in error. Still, no harm done.
[/FONT]

---

### Post by OpSecShellshock on 2010-10-30
It's almost certainly a fake. First it says don't reply, but then it says to reply if you received it in error. I suspect that the line about not replying is included to create the appearance of authenticity, and the line about replying is there to confirm that the recipient's address is genuine so as to pave the way for more spam/phishing messages. The message appears to be intentionally designed to be received "in error" at which point the sender just sits back and waits to see who replies.

---

### Post by florus on 2010-10-30
> It's almost certainly a fake
No, sadly, it was genuine. I recognise the data in the .csv file. It was just not data that would be sent to me in that form or from that source. Just good old banking incompetence.:(

---

