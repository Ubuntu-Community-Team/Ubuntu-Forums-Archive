---
title: "Linux Mail Server to MS Exchange"
date: 2006-03-15
forum: Server Platforms
---

### Post by faulkner132 on 2006-03-15
The skinny on what I want to do is the following:

Network Configuration:
Firewall (running Linux) which also acts as DHCP Server, DNS, and "Mail Filtering" SMTP.
Windows 2003 Domain Server running Exchange 2003.

Since Exchange has practically 0 virus and spam filtering features and subscription services are pretty outrageous, here is my idea.

I would like to have incoming mail hit the firewall machine (which acts essentially as a "filter") and have tools such as ClamAV and various anti-spam tools run against incoming mail on the Linux box and then forward "good" mail to my Windows box running Exchange.  Outlook can then connect directly to Exchange and my users will not even notice the change.  Outgoing mail will also be routed through the firewall, such that sending a message goes like the following: Outlook > Exchange > Firewall > Internet.

Is this do-able and if so what tools are best?
fetchmail?

Thanks.

---

### Post by Koybe on 2006-03-15
Fetchmail? If you'r using an external pop3 mail or something like that. But it doesn't seem to be the case.

I'd like using Postfix/Courier... whichi is (in my mind) easier and more "interfacabl" then exim is the default smtp server.

---

### Post by brok3n on 2006-03-15
[QUOTE=faulkner132]The skinny on what I want to do is the following:

Network Configuration:
Firewall (running Linux) which also acts as DHCP Server, DNS, and "Mail Filtering" SMTP.
Windows 2003 Domain Server running Exchange 2003.

Since Exchange has practically 0 virus and spam filtering features and subscription services are pretty outrageous, here is my idea.

I would like to have incoming mail hit the firewall machine (which acts essentially as a "filter") and have tools such as ClamAV and various anti-spam tools run against incoming mail on the Linux box and then forward "good" mail to my Windows box running Exchange.  Outlook can then connect directly to Exchange and my users will not even notice the change.  Outgoing mail will also be routed through the firewall, such that sending a message goes like the following: Outlook > Exchange > Firewall > Internet.

Is this do-able and if so what tools are best?
fetchmail?

Thanks.[/QUOTE]


Yes it is do-able. 

Currently we are running a MS2K3 Exchange mail solution, but all the mail is filtered through a RH EL box running trendmicro interscan suite.

Once apon a time I read about how to set up ClamAV and SpamAssasin to work in conjuction and essentially provide the same service without having to worry about trendmicro licences and RH EL support.

What I'm really trying to say here is, yes it is possible. It will require alot of know how and how to, however.
There is an extensive amount of custom configuring that you will have to do in order to get ClamAV to scan the messages, and then pass them onto SpamAssasin for content filtering, and then you also have to get the 'nix box to forward the mail to the M$ box.

---

### Post by faulkner132 on 2006-03-15
Thanks for the replies.

Koybe: I meant to say sendmail... not fetchmail.  My mistake.

brok3n: This sounds exactly like what I want to do.  I've actually looked into Devil-Linux to handle this as the diskless model it uses looks perfect for what I want to do.  Also it comes with Postfix and SpamAssassin as preloaded and configured packages.

I know how to do all the network stuff which it will require and hopefully this will aleviate some of the burden my 2003 machine has.

If anyone else has some words of wisdom as well, I would love to hear them.

---

### Post by derelict on 2006-03-15
[QUOTE=faulkner132]I would like to have incoming mail hit the firewall machine (which acts essentially as a "filter") and have tools such as ClamAV and various anti-spam tools run against incoming mail on the Linux box and then forward "good" mail to my Windows box running Exchange.  Outlook can then connect directly to Exchange and my users will not even notice the change.[/QUOTE]

A nice solution indeed :) My vote also goes to Postifx + SpamAssassin, you'll get a very efficient and configurable solution. Configure Postfix first, get it running and forwarding mail correctly, only then head to integrating SpamAssassin with it (won't hurt much, it's mainly done in master.cf).
I never tried ClamAV, post back how good it is later! :)

---

### Post by Koybe on 2006-03-15
[QUOTE=faulkner132]Koybe: I meant to say sendmail... not fetchmail.  My mistake.[/QUOTE]
If you're fool enough ;) Just use Postfix, it's fully sendmail compatible a lot easier to use/administer.

Here are some informations/howto :
- [http://www.marlow.dk/site.php/tech/postfix](http://www.marlow.dk/site.php/tech/postfix)
- [http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/)
- [http://www.littleboboy.net/?2005/04/15/54-postfix-courier-imap](http://www.littleboboy.net/?2005/04/15/54-postfix-courier-imap) (french)
- [http://high5.net/postfixadmin/](http://high5.net/postfixadmin/) (This is a nice tool for managing postfix from a webinterface)

Then you'll have to check what you really needs. As it's just relaying/filtering without deserving to any local mailbox, it should be slightly different then these howto's.

If i add to do it, i would use postfix to get the mail, amavis to filter them (with clamav and spamassassin) and then I don't know which is best :
- Taking them to a local account and pop them with a Exchange connector.
- Forward directly to the exchange server.

GL ;)

---

