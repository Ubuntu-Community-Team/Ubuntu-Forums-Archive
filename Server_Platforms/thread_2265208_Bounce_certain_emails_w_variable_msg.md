---
title: "Bounce certain emails w/ variable msg"
date: 2015-02-13
forum: Server Platforms
---

### Post by Mark_Moran on 2015-02-13
I'm using postfix and procmail on a non gui server. Using squirrelmail to server mail accounts. I'm looking to bounce email msgs to certain accounts with a reply specific to that account. A procmail recipe or something simple like .forward? Any suggestions.

---

### Post by SeijiSensei on 2015-02-13
That's not much to go on, Mark.  Are the replies canned text, or do they have to adapt to the content of the incoming message?  If the former you could use a procmail recipe with pipes.  Look at the examples in "man procmailex" that use formail, echo, and cat to compose a message derived from the incoming one.  I presume you know how to trigger the appropriate recipe.

If the message is too complex for a simple recipe, you'll need to write a script and pipe the messages to that.  As an example, the listservers I manage now have problems delivering mail to Yahoo and AOL which use [DMARC]("http://www.dmarc.org/faq.html").  I wrote a script in PHP to process the incoming message, identify the sender, rewrite the sender's address to obfuscate the original domain like aol.com, then check that the sender was a legitimate subscriber before forwarding it on to the list's subscribers.  That was way too complex to handle in a simple procmail recipe, so instead I have:
```

# rewrite addresses from DMARC providers
:0
* ^From:.*aol\.com|^From:.*cs\.com|^From:.*yahoo\.com
{
    :0
    | /usr/local/bin/dmarc-handler
}

```

---

### Post by Mark_Moran on 2015-02-13
Thanks for the quick reply, and you're right I could have filled in a few more blanks. The situation is we have a .com and .net both of the same name. Most of our email goes to the .com address. There will be five or so addresses that need to goto the .net address. IE., [EMAIL="mark@abc.net"]mark@abc.net[/EMAIL]. So if someone sends the email to [EMAIL="mark@abc.com"]mark@abc.com[/EMAIL]. I want that server to bounce back the email and say sorry blah, blah, blah, you need to resend your email to [EMAIL="mark@abc.net"]mark@abc.net[/EMAIL].

Hopefully this makes more sense. You ask why? Long story that deals with medical regulations, HIPPA and a unusual requirements by a secure email provider that we're locked into.

P.S. I hope you've dug out of the snow. :)

---

### Post by lisati on 2015-02-13
You might want to check out Postfix's [relocated users table]("http://www.postfix.org/ADDRESS_REWRITING_README.html#relocated").

---

### Post by Mark_Moran on 2015-02-13
Thanks for the postfix option. That could do the job. I would like to send a little more info just than the user has moved. It will be an unsophisticated audience and the different between abc.net and abc.com may allude them. If I can't come up with a better solution I'll probably use the postfix option.

---

### Post by SeijiSensei on 2015-02-13
If you just want to send a notice, that's pretty easy in procmail.  Here's the recipe I use to send a reply when a listserver subscriber sends an oversized message:
```

# autoreply to large message senders
:0
*$ B ?? > 15000
| (formail -rt -A"From: admin@example.com"; cat $HOME/oversized.reply) | $SENDMAIL -t

```
The recipe tests to see whether the body exceeds 15K characters.  If so, it generates a reply from the administrator address containing the contents of $HOME/oversized.reply.

More snow on the way this weekend, I'm afraid. I, too, have some experience with HIPAA rules as I consult to a local community health center.  One task was writing a HIPAA-compliant web application to let patients schedule appointments online.  For email, we use [MailScanner](http://www.mailscanner.info) on the border server.  Along with inbound spam and virus scanning, MailScanner has a facility to scan outbound messages as well.  I wrote some rules to intercept messages that might contain violations of patient privacy like the inclusion of SS# or patient IDs.

---

### Post by Mark_Moran on 2015-02-14
Thanks that should do it. I'll just change the 15000 to 1 and I can run scripts to just delete any mail that has arrived. We have a web based portal for scheduling etc now and actually I'd like to direct most of the traffic there instead of email.

Enjoy the white stuff. :p

---

### Post by SeijiSensei on 2015-02-14
You can just delete the test entirely:
```

:0
| (formail -rt -A"From: admin@example.com"; cat $HOME/oversized.reply) | $SENDMAIL -t

```
Make that the default rule at the bottom of .procmailrc.

---

