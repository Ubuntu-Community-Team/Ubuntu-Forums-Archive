---
title: "fetchmail+gmail+fax"
date: 2016-02-15
forum: Server Platforms
---

### Post by atux on 2016-02-15
hello everyone. i do have an installation of ubuntu 12.04 LTS server edition 32bit. In that server i do run my office PBX and by making use of iaxmodem and hylafax i can receive faxes directly to emails. if i want to sent faxes i have to use the CLI with the sendfax command.
i would like to automate the process by sending emails with an attachment and then the sendfax command will be issued to send the fax.
_**the following email addresses are fakes ones, just for the sake of the simplicity**_
i have created some email address 
[email]atuxA@gmail.com[/email]
[email]atuxB@gmail.com[/email]
[email]atuxC@gmail.com[/email]
[email]atuxD@gmail.com[/email]

I would like to setup the email address [email]atuxA@gmail.com[/email] to the server. when it receives an email with the format
to:atuxA@gmail.com
subject:the_fax_number
attachment:a_pdf_file.pdf

It will receive only from the following email addresses [email]atuxB@gmail.com[/email], [email]atuxC@gmail.com[/email], [email]atuxD@gmail.com[/email] 
the user that sends the email need to get a report back with the success or failure of the fax.
i do need some help on how to set it up on the system please. i am lost.

---

### Post by SeijiSensei on 2016-02-15
Have you read this? [http://www.hylafax.org/content/Email_to_Fax_Gateway](http://www.hylafax.org/content/Email_to_Fax_Gateway)

---

### Post by atux on 2016-02-17
hello and thanks for the reply. ii have seen the thread, but i have not a clue on how to setup fetchmail to handle the email and then send it to sendfax.

---

### Post by SeijiSensei on 2016-02-17
I haven't used either hylafax or fetchmail for a very long time, so I can only give you some general ideas.

Fetchmail itself isn't that hard to set up.  You'll also need to install an SMTP server like Postfix or sendmail.  See this guide for details: [https://help.ubuntu.com/community/GmailPostfixFetchmail](https://help.ubuntu.com/community/GmailPostfixFetchmail)

You would configure fetchmail to get the messages from GMail and deliver them to a local user account.  Now the fun begins.  First you should install the **procmail** package, the "Swiss army knife" of email accessories.  You would then create a .procmailrc file in that same user account that invokes sendfax for messages that meet a specific criterion.  In your case it might look something like this:
```

# sample .procmailrc to hand messages to sendfax if phone number in subject line
:0
* ^Subject:.*\/[\+\ 0-9-]+
| /usr/bin/sendfax -n -m -R -f 999-999-9999 -d "$MATCH"

```
That "recipe" tells procmail to pipe messages with a subject line of numbers, the plus, spaces and hyphens to the sendfax program.  The "\/" construct will put everything that matches the regular expression on the right into an environment variable called MATCH.  The regex should match things like 777-777-7777, +011 7777777777, or 777 777 7777.  The all-nines entry should contain your fax number.  I cribbed the sendfax command line from the document I linked to above.

This is really bare-bones and probably will require a lot of massaging to actually work as you want.

I'd attack this problem in pieces.  First get fetchmail working so it polls GMail and delivers the messages to the user account(s).  Then I'd start playing with procmail and sendfax.  I'd start by having it fax messages in plain text before you start dealing with attached PDFs and the like.  If you haven't done anything like this before, expect to spend at least a couple of days getting all the pieces to work properly.

---

