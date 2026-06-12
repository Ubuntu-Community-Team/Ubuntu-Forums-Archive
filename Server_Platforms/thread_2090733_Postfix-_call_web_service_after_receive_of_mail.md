---
title: "Postfix- call web service after receive of mail"
date: 2012-12-03
forum: Server Platforms
---

### Post by geturnithin on 2012-12-03
I have postfix installed in ubuntu. I want postfix/any other way(please suggest) to call the web service and provide the email in text format to that.

FYI: the web service contains the code to read the keywords in email and reply to that mail accordingly(so the headers must also be sent to the webservice)

what can i do? please help:confused:

---

### Post by SeijiSensei on 2012-12-03
You'd need to provide us with a lot more details about what you're trying to do.  "Web service" is pretty meaningless.

In the meantime I suggest you look into [procmail]("http://www.procmail.org/"); it may be what you're looking for.

---

### Post by geturnithin on 2012-12-03
The question is not what webservice will do, what I want is, whenever i get a mail, that mail's body and a sender id must be sent as a parameters in the http request.
for ex: I want postfix/something to call **[http://example.org/xyz.aspx?body=mail-body-content&senderid=adc@pqr.com](http://example.org/xyz.aspx?body=mail-body-content&senderid=adc@pqr.com)**
So the mail body and sender id must be inserted whenver the mail comes.
These are my requirements

---

### Post by chmac on 2013-03-06
Did you find a solution for this in the end?

---

### Post by SeijiSensei on 2013-03-06
As I suggested, I'd use procmail for something like this.  You can write a procmail "recipe" to hand messages to a script.  In the script he could build the HTTP request and invoke something like wget.

---

### Post by chmac on 2013-03-07
Certainly sounds like procmail can do the job. Personally, for low volume, I'd most likely use [Mandrill]("http://www.mandrill.com/"), from the folks behind [MailChimp]("http://www.mailchimp.com/"). It supports email to webhook, and is free for up to 12k emails per month. The hardest part is probably reliably parsing out the various header values you want, like subject and sender's address, which procmail won't do for you by the sounds of it.

---

### Post by SeijiSensei on 2013-03-08
No, procmail is simply rules-based delivery agent. Any parsing would have to take place in the script to which procmail pipes the message.  

However invoking a web request with a GET may run into all sorts of problems.  Some web servers have length limits on GET query strings, so he'd probably have to have the script use a POST.  He would also have to use URL-encoding or something like base64 to handle messages with special characters, attachments, and the like.

I'm putting the finishing touches on a PHP script to rewrite messages after being invoked by procmail.  I'm using the [mailparse]("http://php.net/manual/en/book.mailparse.php") libraries for PHP though it meant having to compile my own copy of the command-line client since mailparse is not a standard extension.  If I knew perl, I'd probably use that instead.

---

