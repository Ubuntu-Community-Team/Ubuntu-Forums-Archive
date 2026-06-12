---
title: "Install sendmail and configure to only send emails"
date: 2009-12-02
forum: Server Platforms
---

### Post by mrgordonz on 2009-12-02
I am setting up a server for a new client which will host about 8 separate Joomla sites (each with its own domain).  The server is a standard LAMP installation of 8.04 Hardy Heron.  The Joomla sites are all configured as Apache Named Virtual Hosts.  Everything works fine from that perspective.  The only thing that isn't working is email.  The requirement from the client is as follows:

[LIST]
[*]no mail should be delivered to the new server – the MX records for all the domains point to their Exchange server
[*]sendmail should be configured so that each of the Joomla sites can send mail to external machines
[*]but the server shouldn't relay mail for other servers (to prevent it from being used to deliver spam)
[/LIST]

In the past I have previously installed and configured Postfix, but I would prefer to use **sendmail** because all the Joomla sites are currently configured to use sendmail - the sites are all currently being hosted elsewhere and I am migrating them to a new server and if at all possible I want to avoid changing the configuration of the Joomla sites.

I've seen a bunch threads that have similar questions, but not exactly the same.  I gather the installation part is pretty straight forward:

```
sudo apt-get install sendmail
```

But is that all there is to it?  Do I need to do any config with PHP or Apache?

And once sendmail is installed, is there any special config I need to do in order to satisfy the requirements listed above?

I should also mention the new server is a dedicated server I manage in a data center and as such I don't have to worry about an ISP blocking port 25.

Cheers,

Paul

---

### Post by dgoosens on 2009-12-02
I believe the behavior you request is sendmail's default behavior...

Just install sendmail, restart Apache2 and you should be ok.

---

### Post by mrgordonz on 2009-12-02
> **dgoosens said:**
> I believe the behavior you request is sendmail's default behavior...

Just install sendmail, restart Apache2 and you should be ok.

Well, that seems to have done the trick!  Thanks for the quick reply.

I tested it using the command:

```
mail my.email.address@domain.com < text.file
```

and it worked fine - the email was delivered immediately.

I assume that (like Postfix) there are a gazillion settings which can be tweaked, but to be safe I should leave most of them alone.  The main thing I would want to be sure of is that the server can't be used by others as an SMTP relay for spam.  Is there a particular setting I should check?

Cheers,

Paul

---

### Post by Bachstelze on 2009-12-02
> **mrgordonz said:**
> The main thing I would want to be sure of is that the server can't be used by others as an SMTP relay for spam.  Is there a particular setting I should check?

You can test that here: [http://www.spamhelp.org/shopenrelay/](http://www.spamhelp.org/shopenrelay/)

---

### Post by dgoosens on 2009-12-02
I am not quite sure about that...
I think all the conf files should be located under /etc/mail/

I am pretty sure that, by default, sendmail only allows knows hosts to sendmail...
but I guess the easiest way to make sure is by running a test...

EDIT:
... too late... 
as Bachstelze says...

---

### Post by mrgordonz on 2009-12-06
Just a quick thanks to all who helped with my question - everything is working nicely now.

Cheers,

Paul

---

