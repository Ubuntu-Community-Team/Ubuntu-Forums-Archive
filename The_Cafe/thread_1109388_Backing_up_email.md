---
title: "Backing up email?"
date: 2009-03-28
forum: The Cafe
---

### Post by TBOL3 on 2009-03-28
Ok, I put this thread in here because it's not technically a ubuntu problem, and I can't find anywhere else to put it.

I want to back up all of my email (i'm currently using gmail).  So, I downloaded it all to Thunderbird, and found out that thunderbird stores all of the email in one huge .txt file, which is unacceptable, I really want it in separate files (so I don't have to worry about the file getting corrupted, and poof there goes everything, rather than one message).

So I thought about Evolution, yes, it allows you to back it up, but it looks like it backs it up to a non stranded format (if it does, please remade me), which again, is unacceptable, I want to be able to access my email from any program that uses standards.

So next I try kmail, it's ok, but I can't get it to download anything that's older than a couple of months ago, but I need everything, not just recent mail.

So, can any of you recommend me a good way to back up my email.  I want it to be a standard format.  I would PREFER to be have the email's be stored in some human readable format (so I don't need to use a program to be able to read it, this helps me as I can be truly independent of any program, and I can make these emails be portable to places where I won't have internet access).  However, this is not a deal breaker, just a factor in deciding what to use.

Also, I want to know about attachments.  Do any of you know if pop downloads attachments, and if not, how can I get them as well, they are very important.

Thanks!

---

### Post by jo4hnc on 2009-03-28
Hi,

I had the same problem a while ago. If you use Thunderbird, there is an add on called Smart Save. It does allow you to save emails to the folder of your choice. What it does is export to whatever file you designate. Here's a link.

[https://addons.mozilla.org/en-US/thunderbird/addon/2887](https://addons.mozilla.org/en-US/thunderbird/addon/2887)

Check it out and see if it might work for you.

John

---

### Post by TBOL3 on 2009-03-28
I tried the extension, and I keep getting a "successfully exported 0 messages". Also, what is the .eml format, it looks like an outlook format.

Oh, and for some reason, I'm only getting messages newer than November in Thunderbird now too, do any of you know why?  Thank you.

---

### Post by jo4hnc on 2009-03-28
The .eml format is an email format. In Smart Save you can save to a different file format but I don't know what effect it would have.

Usually if I'm going to save a message or messages, I highlight it(them), right click, and choose export with Smart Save. You can then choose where you want to save the message. If you want to export an entire folder, just right click on the folder and do the same thing. I've been using it for several years now and have never really had a problem. It exports copies of the messages and leaves the originals in the email program, so that you can delete whatever you don't want to keep.

As to your question about getting messages newer than November, I'm not sure I understand the question. Did you set up IMAP? It's probably the easiest way to get all of your G-Mail messages into your email client.

To save attachments in Thunderbird all you have to do is go to File>Attachments and choose an option then a location to save the attachment.

---

### Post by TBOL3 on 2009-03-28
Ok, I think I might know what my problem is, apparently gmail will only send messages via pop3 to you once, which is my problem (I'm guessing do to using multiple email programs).

So you say imap is better (I was using pop3), I thought that wouldn't actually download the messages, but rather, just a database of them.  I really need to actually download them.

As for the File->Attachments, that seems to only work for the current email I have open, I want to save ALL of my attachments, I've seen the Attachment Extractor Add on, which allows me to download them all, but it doesn't leave them synced to what emails they came from.  So, do I need to download them all separately?

---

### Post by jo4hnc on 2009-03-28
Here's the G-Mail IMAP getting started page. Seems to me like it might work. At least it might help you decide.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)

Regarding the attachments, I looked through Synaptic and there didn't seem to be anything there that would do what you need. Perhaps someone else has an idea.

---

### Post by HermanAB on 2009-03-29
You can use formail (part of the fetchmail package) to convert between mailbox and maildir formats.  The traditional Unix mail format is mailbox and that is what Tbird use by default, but formail will convert it for you.  Install fetchmail and then read the formal man page.

---

### Post by Irihapeti on 2009-03-29
The extension ImportExportTools gives you the option of exporting messages as individual .eml files, plus other formats. It's available from [http://nic-nac-project.de/~kaosmos/mboximport-en.html](http://nic-nac-project.de/~kaosmos/mboximport-en.html)

Attachments are saved with their original messages.

---

### Post by TBOL3 on 2009-03-29
Thanks, it works perfectly!

Anyway, it makes me curios to know why this is not on the thunderbird add on page, is there some license it's under that's incompatible with it?

Again, thanks.

---

### Post by Irihapeti on 2009-03-29
I don't know why the extension isn't on the Mozilla site. In fact, I'd forgotten that it isn't there and had use Google to find the link. It updates itself the same as any other extension, so nothing different there.

I guess one would need to ask the developer for the reasons. :)

Anyway, glad it works.

---

### Post by TBOL3 on 2009-03-29
Oh great, maybe this is the wrong place to ask, but it seems like it will only store part of my emails.  It starts out very fast, then slows down, and eventually stops.  Do you have this same problem?

---

### Post by Irihapeti on 2009-03-29
I haven't used it a lot for storing emails - mainly for importing them - so I'm not the best person to ask.

Probably your best option would be to contact the developer. There's an option on his website to contact him.

Irihapeti

---

