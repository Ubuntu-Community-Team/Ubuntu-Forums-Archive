---
title: "Postfix redirect question"
date: 2017-07-06
forum: Server Platforms
---

### Post by lkopphsd on 2017-07-06
I have been tasked with a strange request on a server I support.  I currently have an internal only address set up through ACL's in postfix.  I'm being asked if I can redirect any attempt to email that address from an outside domain to a different address.  

Example:

[email]someone@outside.com[/email] sends email to [email]everyone@example.net[/email] -> message redirected to [email]realperson@example.net[/email]

[email]realperson@example.net[/email] sends email to [email]everyone@example.net[/email] -> message delivered to [email]everyone@example.net[/email]

I've done several google searches but I don't see any way to do it but maybe my search syntax is incorrect.  Is this even possible?

If it matters I am running postfix 2.9.6 on ubuntu 12.04.05

Thanks in advance

---

### Post by slickymaster on 2017-07-06
*Thread moved to **Server Platforms**.*

---

### Post by lisati on 2017-07-06
It has been a while since I've run a postfix server, but if I recall correctly, it is possible. 

Multiple methods come to mind, one of which is through the use of aliases, and another similar to what is described [here]("https://serverfault.com/questions/284702/redirect-specific-e-mail-address-sent-to-a-user-to-another-user"). Both these methods redirect to one user only.

Another way, if you want to redirect to multiple email adresses, might be to use some kind of mailing list, such as mailman or listserv.

---

### Post by lkopphsd on 2017-07-06
Awesome!  I think the PCRE method is what I need.  I will try it tomorrow when I am in the office and mark this solved if it works.

---

### Post by SeijiSensei on 2017-07-06
If you can't come up with a PCRE solution, another option is to install **procmail** as the delivery agent.  Use "sudo apt-get install procmail".  Procmail will let you place "recipes" in a file called /home/username/.procmailrc that control what to do with messages based on regular expressions.  I'm assuming your server is the primary MX for example.net and accepts delivery for that domain.

If "everyone" is an actual account name, then create a file called /home/everyone/.procmailrc.  If everyone is an alias that points to a real account, place the .procmailrc file in that user's home directory.  Now you can add this recipe to that file:
```

:0
# forward mail from someone@outside.com to everyone@example.net
* ^From:.*someone@outside\.com
! realperson@example.net


```
The symbol ":0" defines the start of a recipe, and the asterisk ("*") is a wildcard for all the message's headers.  (By default, only the headers are scanned, but there is an option to scan the body as welll.)  The default is to deliver all non-matching messages to the inbox for the account.  

The rule above matches only mail specifically from [email]someone@outside.com[/email].  If you want to forward all mail from external senders to realperson, you can use this recipe instead:

```

:0
# send all external mail for this account to realperson
* ! ^From:.*example\.net
! realperson@example.net

```
Note that the exclamation point plays two roles in procmail recipes.  In the regex part it means NOT, so that regex matches mail from anywhere other than example.net.  In the action part of the recipe, the "!" means forward to the address list that follows.

Procmail is a very powerful tool if you need to administer email servers.  You can see the detailed documentation for procmailrc by typing "man procmailrc" at a prompt.  Typing "man procmailex" gives you a variety of examples.

You can also create a file called /etc/procmailrc and create recipes that apply to all messages delivered to that server.  I've used this to route spam messages to specific folders for all accounts with a single rule.  (I use MailScanner+ClamAV+SpamAssassin to filter my mail.  SA adds specific headers that I can key on to create a procmail rule for spam messages.)

---

