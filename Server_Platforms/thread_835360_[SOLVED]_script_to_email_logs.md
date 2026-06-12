---
title: "[SOLVED] script to email logs"
date: 2008-06-20
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-06-20
Hi, I'm looking to make a python script to email various logs (samba, ssh, proftpd, etc...) to a gmail account daily.  This would give me a snapshot of everything that's happened on my server for each individual day.  I've looked into writing this script in python, and one very easy way seems to be using Sendmail.  Would this be a good approach, and if so, what do I need to do to set up sendmail?  If not, what would be some good alternative approaches?  Would there be any major security risks with sending out log files to gmail?

Thanks!

UPDATE(For those that may check this):
I am using logwatch to generate a parsed log file, then I'm using a python script (link below) to email the link to myself.  I set up a crontab job to get a new logfile from logwatch, then email it out.

---

### Post by diaa on 2008-06-20
If you mean sendmail the program, I wouldn't recommend that because you'll have to set it up and it'll be a dependency for your python script, on the other hand if you use sendmail function, which exists in smtplib module you'll need to configure this in the script and since this is a standard module in Python, your script will have no dependencies.

Whether you use the sendmail program or the function you'll have to provide an SMTP server and login, you can use your gmail SMTP server and its login.

---

### Post by magicplayr2000 on 2008-06-20
Oh wow!  I was thinking about the first option, but after looking at the smtp package, that's definitely the way to go.  I guess I'll just take all the text from the log file and dump it straight into the message body.  Pretty straightforward.

---

### Post by weryl on 2008-06-20
Could you please post the script or send it to me if you manage to get it working please? I'd like to do exactly the same thing and that would help :)
Mike

---

### Post by MJN on 2008-06-20
Have you considered something like Logwatch? It parses the logs and summarises their contents - I find this much better than raw logs for daily perusal. It is pre-configured for most, if not all, of the main packages you'd likely have installed and hence is able to 'understand' the majority of what they log (anything it doesn't understand gets reported too in case this is important).

Mathew

---

### Post by magicplayr2000 on 2008-06-20
I actually hadn't heard of that.  Is it easy to set it up to email the information?  If so, that'll be a great way to go, since it will make it a bit more readable.

weryl, I found this page: [http://kutuma.blogspot.com/2007/08/sending-emails-via-gmail-with-python.html](http://kutuma.blogspot.com/2007/08/sending-emails-via-gmail-with-python.html) that has a script to send emails to a gmail account.  I can't seem to get it to work, but it might just be because of where I am at the moment.  Once I get home, I'm going to try it again, unless Logwatch can be set up to send emails easier.

---

### Post by MJN on 2008-06-20
> **magicplayr2000 said:**
> I actually hadn't heard of that.  Is it easy to set it up to email the information?  If so, that'll be a great way to go, since it will make it a bit more readable.

Sure. Just install it and it will e-mail you (root) every day with the log summaries. You can of course configure it to your hearts content, including sending the summaries to an off-net e-mail address (you will need suitable mail server installer, however give 'nullmailer' a go as this is the most basic and will give you just enough to get messages off your machine).

Mathew

---

