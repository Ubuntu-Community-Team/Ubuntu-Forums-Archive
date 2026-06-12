---
title: "Email Database"
date: 2007-06-05
forum: Server Platforms
---

### Post by Chayak on 2007-06-05
I'm looking for a way to archive email in a database and be able to search/retrieve it from a web client and foward it to an email address if needed.  This will be in the range of 2000+ messages daily.  My database skills are not flexed very often so any help would be appreciated.

---

### Post by kidders on 2007-06-06
Hi there,

I would suggest storing only limited metadata in a database, rather than entire emails. If this were *my* problem (and assuming the mail was arriving via Postfix or something), I would configure the SMTP gateway to pass incoming mail through a script. The script could pull interesting information (eg sender, subject, size, the presence of attachments, etc.) out of each mail, and throw it into a database table.

Doing that (assuming you even *like* the idea!) would create two problem though...

** - I -**
Piping mail through scripts creates all sorts of security issues, the most significant of which is probably bottle-necking ... which, aside from anything else, would cause performance issues. 2,000 mails per day (less than 2 per minute) may not seem like a concerning workload, but it would be a shame to design a system that (a) isn't scalable, and (b) might buckle under the strain of an attack.

For this reason, I would suggest running two mail servers (possibly on the same machine). The second server would be hard-wired to accept mail only from the first (ie the "real" one), and would handle your database operations.[LIST]
[*]This type of thing is commonly done with servers (eg Postfix) that are performing computationally intensive (eg virus scanning) or unreliable (eg database manipulation) tasks.
[*]By making your scripting/database ops asynchronous, you separate the failure of your mail server from that of your database server. Without this layer of protection, one of two things would happen if something about your database-based service were to break...[LIST=1]
[*]Your database-driven service would start losing email.
[*]Your mail server's delivery queue would back up, and mail would start to bounce.[/LIST] 
[*]Using a pair of mail servers would also disconnect the performance of your database from that of your mail delivery system, because the server handling the delivery of incoming mail would not have to wait for post-processing to complete.[/LIST]** - II -**
Besides performance, another reason for only storing metadata in your database is that standard IMAP/POP servers could continue unaffected ... since (obviously) your mail would still wind up being stored on a normal filesystem. This creates the possibility of inconsistencies arising between what's on your hard disk and what your database *thinks* is on your hard disk. Finding graceful ways of handling things like "missing" emails shouldn't be too tough a job, but I would still recommend using cron to schedule regular (although perhaps infrequent) large-scale cleanups, to rid the two parallel systems of any oddness that might have crept in.



Anyhow, sorry for rambling! In brief, my best suggestion would be something like this ...[LIST=1]
[*]Set up a second mail server (if you haven't already got one running!) that is only visible to "localhost", running on eg port 10025.
[*]Move all time-consuming activity (spam filtration, virus scanning, etc.) to that server & hard-wire the pre-existing (externally accessible) one to blindly forward all mail with a local destination to its running mate.
[*]Create a basic (ie a placeholder) script in a language of your choice, and configure the second mail server to pipe all mail through it.
[*]Set up a database (perhaps with MySQL) to store your mails' metadata.
[*]Gradually build up your placeholder script's functionality, testing as mails arrive. This will give you a nice opportunity to observe & manipulate what happens when (or if) your database gizmo tangles itself up in knots.[/LIST]In terms of the database itself (since you mentioned you're not so hot with them), I would strongly recommend the following:[LIST]
[*]Avoid using too many tables, or performing joins on non-numeric fields. These are traps that people familiar with "textbook" relational databases sometimes fall into.
[*]Make use of indexes where appropriate, to prevent the large volumes of data that will, no doubt, accumulate over time causing a corresponding drag on performance.
[*]Particularly in the case of engines like MySQL's ISAM model, try to avoid storing very large chunks of text in tables.
[*]Try not to design tables that will never do anything but increase in size as time goes on (eg a table of all mail ever received). That type of design (which is _not_ always avoidable) builds a brick wall into your database that you will inevitably hit, sooner or later.[/LIST]Anyhow, I hope something here is useful.

**Edit:** A note about security:
[SIZE=1] You may know this already (in which case, I apologise for making this post even *longer*!), but if you do decide to pass mail through a script you write yourself, it's very important to remember to code with extreme paranoia.
[/SIZE][LIST=1]
[*][SIZE=1] Never write anything that assumes mails will be properly formatted.[/SIZE]
[*][SIZE=1] Always, always, always escape anything (no matter how innocuous) that's been extracted from a mail & is headed for an SQL statement or command line argument.[/SIZE]
[*][SIZE=1] Don't do anything that makes assumptions about the sizes of things, eg reading an entire email into a single variable, all in one go. If there is no way around doing so, be sure to build in some way of preventing too many similar processes from executing simultaneously, and manually invoke garbage collection where possible.[/SIZE]
[*][SIZE=1]Try to anticipate points of failure in your code, but keep whatever code handles them light and easy to execute. (Try to imagine what impact several thousand identical failures in 60 seconds might have.)
[/SIZE][/LIST][SIZE=1]
These suggestions are aimed mostly at DoS attacks and code injection (into your database engine).

[/SIZE][[SIZE=1][COLOR=Silver]UAResolved[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by Chayak on 2007-06-10
Thanks for the reply.

All of the mail coming through the system will be in a very defined format (military messages) and on a secure network that doesn't even touch the internet.  I don't have to worry about virii or spam on that network.

I basically need three fields.  DTG (date time group), Subject, and body.  All of the messages have to have a valid DTG or they'd never be sent out and thats 99.9%  of what's searched for when looking for a specific message.

This is essentially  an archive.  I am on the other hand thinking about just setting up a deadicated machine that just sucks in email and stores it locally and just use evolution to search for it when needed.

The current solution is to use rules to send all the messages to an Outlook PST file as an archive and search them when needed.  It takes a while and the occasional crash from it having to process huge .PSTs doesn't help the situation any.

---

### Post by Mr. C. on 2007-06-10
Chayak,

Using Outlook's PST file for archiving email is, as you've found out, an unreliable solution.  It is far to error prone, especially when approaching the 2Gig boundary.  It is also consumes many times the size of the actual email in disk space.

There are many reliable, robust mechanism to create email archives, but this depends on a) your mail server, b) how your mail get's to the server in the first place, and how your mail is being delivered.

Can you explain more clearly the inbound and outbound paths of the email you want archived, what MTA's you are using, etc.?

MrC

---

### Post by Chayak on 2007-06-11
I know the flaws, it's why I'm looking for a more robust alternative ;) ( and taking the chance to get linux into the spot. )

Well basically is goes from various means to Exchange servers and then to client desktops.  The message handling machine is much the same but email is sent to it and then it uses software to route it to the people it's suppost to get to.

1 message to machine -> machine emails it to all users on matching lists (200+ users)

I basically want the archive to be one of end user machines and simply archive the mail and make it searchable so months down the line I can look it up by its DTG (Date Time Group) and then foward it to the person needing it.

---

