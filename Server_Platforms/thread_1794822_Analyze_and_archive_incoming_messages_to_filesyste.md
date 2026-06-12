---
title: "Analyze and archive incoming messages to filesystem"
date: 2011-07-01
forum: Server Platforms
---

### Post by luizvd on 2011-07-01
Where I work we're trying to create a mailbox where our employees sends messages to it and the mail server processess them. Much like the Support of some companies where you send an email a ticket is automatically opened, but instead we need to save the messages to the filesystem depending upon an identified ID in the message.

We're considering two options:

[B]1) Identify by *to:* header
[/B]
Messages are sent to *12345@domain.com* or *os+12345@domain.com*, where **12345** is out customer identifier, and the mail server processess messages and saves them to:

/data/os/**12345**/Customer contact.eml

[B]2) Identify by *subject:* header
[/B]
Messages are sent to *os@domain.com* and the customer identifier is specified in the subject *[12345] Customer contact*.

We need to do some other verifications as the user (*from:* header) is authorized to archive messages to that customer, but this is another story.

I tried searching for something along the line of AMaViS and ClamAV filters but had no success.

Do you have any clues on how to do this?

Thank you in advance.

Original post in [ServerFault.com]("http://serverfault.com/questions/286250/analyze-and-archive-incoming-messages-to-filesystem")

---

### Post by SeijiSensei on 2011-07-02
Take a look at [procmail]("http://www.procmail.org/"), the Swiss-Army-knife of mail delivery agents.  With a little effort you should be able to write "recipes" that will scan the headers for the customer number and other information you're using for filtering, then copy any matching message to a specified folder.  You might need to pipe the message to a simple bash script that uses awk to extract the customer's identifier then saves the message to the appropriate file.  After you've installed procmail, see "man procmailrc" and "man procmailex" for details.

Procmail may or may not have been installed by default on your server, but you can install it from the repositories yourself.

---

### Post by luizvd on 2011-07-04
Thank you SeijiSensei, I'll look into it.

---

