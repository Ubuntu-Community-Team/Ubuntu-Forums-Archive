---
title: "Good IMAP server - any recomendations ?"
date: 2005-12-14
forum: Server Platforms
---

### Post by winnetou on 2005-12-14
Can someone recommend good IMAP server running under ubuntu ?
The best would be a server that allows virtual users (users don't have to have system accounts).
Any experience with extremail ?

---

### Post by Hube on 2005-12-14
I've always used courier-imap and been happy with it.  There could be a bunch of other options though...

---

### Post by cactus on 2005-12-14
I use dovecot. It rocks.

---

### Post by HS-L on 2006-01-28
[QUOTE=cactus]I use dovecot. It rocks.[/QUOTE]

Can you tell me what the advantages are for dovecot in comparison to courier?

---

### Post by Crimguy on 2006-01-28
I've been using courier-imap for 3 years without a hiccup.  Combination of imap, maildrop and fetchmail is a great combo for home server use.

How many users are you supporting?

---

### Post by Glut on 2006-01-29
To be entirely honest, there's not a great deal of noticable difference between the two (from my pov). I understand Dovecot can be faster and Courier can support additional features. I use Dovecot because Courier doesn't support mbox - only maildir.

---

### Post by MJN on 2006-01-30
Why would you want to use mbox?

I was forced into it by me using UW-IMAP on my old RedHat box but since moving to Kubuntu, and Dovecot, I also migrated across to Maildir (not too painful as I thankfully found some conversion scripts). I cannot fairly determine any performance benefits (or otherwise) as I've changed too many other variables (including the server hardware) however suffice to say it now flies and I feel a lot more secure with my messages being stored individually and in a standard format. Also good to have folders than contain other folders *and* messages, although granted that might be due to UW-IMAP limitations and not mbox.

Incidentally, there's an article comparing mbox and maildir performance at [http://www.courier-mta.org/mbox-vs-maildir/]("http://www.courier-mta.org/mbox-vs-maildir/").

With regards to the original question you won't go wrong with either Courier or Dovecot. I've no experience of the former however from what I've read of the latter I'm content with the claimed designed ethos being a combination of performance and security - two criteria which I appreciate.

Mathew

---

### Post by Glut on 2006-01-30
[QUOTE=MJN]Why would you want to use mbox?[/QUOTE]
We do for legacy reasons, and the cost of converting is too high to justify the returns. Just as an aside, I glanced at the comparisons and I do not believe that they are useful as they test two different programs - although maildir is almost certainly faster, it could be that just uw-imap is very slow - a better test would be maildir vs mbox where both are run by one program, e.g. dovecot.

Having said all that, I think that maildir is the way to go for new installations if only to get rid of locking problems.

---

### Post by MJN on 2006-01-30
I hear what you're saying, and couldn't agree more.

Mathew

---

### Post by plampione on 2006-02-05
What is a good imap server for: 

- Mailboxes containing several 1000's messages (up to 20000); 
- lots of searching, including full-text searching
- Thunderbird as email client 
- Must support spamassassin, procmail. 

I ask because I am having slight problems with uw-imap: if I leave thunderbird running at the office, go home, and reopen a thunderbird session from there, not all the changes done from the office have been committed.  For instance, unless I compact folders, sometimes I see messages that should have been deleted.  Is there anything to be gained by moving to dovecot or to another imap server?

Peter

---

### Post by Glut on 2006-02-05
You wont gain anything by changing server. I'm not sure when Thunderbird will commit a change, your best bet may simply to be making sure that you close it.

---

