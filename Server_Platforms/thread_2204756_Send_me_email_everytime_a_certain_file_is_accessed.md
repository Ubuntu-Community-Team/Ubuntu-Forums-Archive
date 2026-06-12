---
title: "Send me email everytime a certain file is accessed from my apache server"
date: 2014-02-10
forum: Server Platforms
---

### Post by Robert_Reid on 2014-02-10
I want to have my server send me an email every time someone accesses a PDF file on my webserver.


Perhaps:
```
tail -f /var/log/apache.log | grep pdf > ??something??
```

How would I generate a new email message each time this tail/grep outputs something?
How could I have that running as a background script?

---

### Post by TheFu on 2014-02-10
**Mail** is the cli program to use, but you need to wrap in an if [] block.  I would check the count from the grep and use an exact name of the PDF file - long is more exact - don't forget that people can ASK for any PDF file they want and it will show up in the logs, even if it isn't available.

There must be an existing tool that does what you want ... **logwatch**?  There are lots of other things to be monitored on servers and logwatch makes that trivial.

Mail needs an MTA - **postfix** is normally what I'd recommend.  Your ISP may or may not make sending email easy.  You might just need to setup your MTA as a satellite of their outbound email server and it will work ... or you might need authentication. 

The format of an Mail use is:
**echo "hello" | Mail -s "Hello Test" you\@domain.com**
I would test that first.

The great thing about using an MTA is that every program on the box can now send emails easily.  So, test that email can be sent before you work on the rest of the problem.

I googled - found [https://stackoverflow.com/questions/4656886/tail-and-grep-log-and-mail-linux](https://stackoverflow.com/questions/4656886/tail-and-grep-log-and-mail-linux)

---

### Post by nerdtron on 2014-02-10
You should create an endless loop script the continually checks you log for a certain filename, then fire up an email.
You can also use mutt to send email. Syntax is almost the same as mail.
echo "This is the body of the email" | mutt -s "subject is here" -a "attachment filename" -- [email]user@email.com[/email]

---

### Post by tgalati4 on 2014-02-10
If the files are static (that is not changing) wouldn't it be easier to add the mail script inside the html file that allows the file to be selected?  Otherwise, use a content management system (CMS) for dynamic content and there are tools built in for this within page statistics.

---

### Post by TheFu on 2014-02-11
@tgalati4 that is brilliant. 
Or use **awstats** to track downloads via apache/nginx/lighthttp  whatever.  It is like google tracking .. without violating the privacy of your users .... which I always appreciate.

I've been using awstats for  ... 9 yrs maybe longer.

---

