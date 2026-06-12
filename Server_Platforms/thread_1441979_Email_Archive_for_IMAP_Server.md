---
title: "Email Archive for IMAP Server"
date: 2010-03-29
forum: Server Platforms
---

### Post by polc1410 on 2010-03-29
Hi guys, I'm not sure this is the right forum to post this in but I'll give it a go and if a mod wants to kick it someplace else then I wont be offended.

I have a small server which runs an IMAP Server (Dovecot).

Myself in particular I don't ever delete virtually any email.  Some of the other users on the box are similar.  In addition there are one or two automated scripts which generate an email every hour to confirm or report any errors.  Those scripts are probably only needed for say 1 month but we have probably 3 years!

Several users with large inboxes have commented that they are getting slow mail checking.  In addition I have an ASUS netbook and just checking IMAP mail with it while on the move can take an age and seems to have filled the hard disk with about 0.5Gb of what I think is just the mail headers!!

So I think there must be some way to archive this.  Of course I googled and there are a few options.  But hoping someone can tell me the best way:

1. to archive this to get the best use of space
2. to allow people still to access the old mail (not via admin)
3. to allow me (and users) to reasonably quickly locate an email sent say 2 years ago on the basis of sender email address, subject line or receipient email address.  Note - I may not know the date an email was sent even to the month...
4. to allow me if necessary to locate an old email by date or by body content

We have users who are within the local network and some users out in the wild so this should ideally be something we can access without a local net connection (we don't currently have a VPN.)  We also have Windows users - some of whom have software installation restrictions placed by their orgnisations so ideally needs to be something server based.

Ideally automated

Ideally configurable to do different archiving for users

So suggestions please on the best applications out there. (for buntu server obviously)

Thanks

---

### Post by HermanAB on 2010-03-29
Howdy,

This is where the men gets separated from the boys...

To handle really large amounts of email, you need a mail server with a database back-end.  I use Citadel.  It can handle up to 256 Terabytes of mail with the Oracle BerkeleyDB backend.

Other options are Zimbra, or heaven forbid, MS Exchange, but it uses an order of magnitude more computing resources than Citadel or Zimbra for the same amount of email.

If you use Citadel, then you need not archive the old stuff - just keep it - but there are some configuration tweaks that you need to do when the database or number of users get very large (in the FAQ).  It should be OK for multiple lifetimes.

---

### Post by polc1410 on 2010-03-29
OK - lets assume I'm not going to change to a database driven server.  The IMAP server works and there is no issue with storage capacity on that server its simply the volume of mail headers that are being held on client machines that is the issue. 

Even if I went to a database driven system - I'd still have half Gig of headers on my netbook which is 1/8th of the total drive size!!

---

### Post by KB1JWQ on 2010-03-29
Overkill.  Dovecot is fine.

What I do is have an Archives folder, with subfolders broken down by year.  That way you don't wind up with half a million messages in a single folder, but your mail is still online.

---

### Post by jrssystemsnet on 2010-03-29
> **KB1JWQ said:**
> Overkill.  Dovecot is fine.

What I do is have an Archives folder, with subfolders broken down by year.  That way you don't wind up with half a million messages in a single folder, but your mail is still online.This.

If necessary, you can even get fancy and write a script using **find** and **xargs** to move messages into year folders from the shell - a Maildir folder looks like this:

/path/to/user/Maildir/.INBOX.2008/

and contains three folders from there:

/path/to/user/Maildir/.INBOX.2008/new
/path/to/user/Maildir/.INBOX.2008/cur
/path/to/user/Maildir/.INBOX.2008/tmp

This will show up in the user's mail client as a folder called "2008" directly underneath their Inbox.

What you want to do is move all the messages more than n days old (or between m days and n days, if you're getting fancy and automatically doing multiple archive folders) into the **cur** folder for that particular maildir.  **man find**, **man xargs**, and experiment safely before doing something rash *en masse*. :)

---

### Post by polc1410 on 2010-03-30
> **KB1JWQ said:**
> Overkill.  Dovecot is fine.

What I do is have an Archives folder, with subfolders broken down by year.  That way you don't wind up with half a million messages in a single folder, but your mail is still online.
But if I want to access the 2008 archive do I not need to pull all the headers from 2008?  So that'll still take a while and fill the local drive on my netbook?

---

### Post by jrssystemsnet on 2010-03-30
> **polc1410 said:**
> But if I want to access the 2008 archive do I not need to pull all the headers from 2008?  So that'll still take a while and fill the local drive on my netbook?
Yes to pulling all the headers from 2008, "I doubt it" to filling the local drive on your netbook.  Headers don't take up much space (generally well under 1K per header - so under 1MB per 1,000 emails), and you should be able to configure your mail client to limit the local cache to an acceptably sized maximum value.

---

### Post by dwarfolo on 2010-03-30
I had exactly the same problem.
I have qmail   + courier imap and over the years I've tryed several solutions:

1) A replication courier imap server. Each user had a different Maildir for each archived year.
This solution showed to be difficult to handle, because of the high number of user and, above all, because of the difficulties encountered when backing-up archives and searching e-mails across different years (as you mentioned, when accessing previous years, the users were forced to download all the headers and even the e-mail bodies in case of full text searches)

2) An "home made" solution based on qmail-log, some script to parse the log and MySQL to store the parsed e-mails. The database was accessed by the users through a web based (PHP) interface consisting of a simple search form.
As the previous solution, even this one failed due to the high number of users compared to the hardware at disposition (mostly because of storage issue and attachements retrieving over the file system)

3) Growing again the number of users, I was forced to find a new solution. And I decided to search for some "specialized" solution.
The only affordable solution I've found is a dedicated appliance.
[http://www.barracudanetworks.com/ns/products/archiver-overview.php?L=en](http://www.barracudanetworks.com/ns/products/archiver-overview.php?L=en)

If you are strongly oriented toward a Maildir like solution, you will always face the header/body download issue. AFAIK there's not a simple and reasonable solution for this.
If you are dealing with a relatively low number of users (say from 20 to 100) I suggest to use a database solution.
If you have an higher number of user I suggest to consider a dedicated hardware solution.

---

### Post by jrssystemsnet on 2010-03-30
Dovecot scales a lot better than courier, IMO, for high message counts.

On one client server I've got more than 150,000 messages in a *single account* that 20 different users all access simultaneously, and it's lightning fast.

Dovecot also indexes the messages for search, so it's not like a client search is either pulling tons of raw data off the server *or* imposing the kind of load a plain grep on the Maildir would.

Also, **n-o-t-h-i-n-g** you can do on the back end is going to have any impact on client caching; that is a client-specific issue and has to be addressed on the client.  Futz around with a db back end all you want, the clients are *still* going to download headers.

---

### Post by polc1410 on 2010-04-01
I guess I was thinking of a web backend for the archive rather than using my normal mail client.  So say the last 6 months of mail is in my active directories but if I need older I got to xx.xx.xx.xx/mailarchive and perhaps see something like a webmail ap that lest me search it.  While that puts all the load on the server I'm not expecting 100's of users to be searching archives simultaneously.

But the web mail apps I've played with (horde {probably the best}, squirrel & roundcube)  seem to balk at large in boxes and thats before I ask them to try anything complex like searching a message body.

As for Dovecot indexing -n that sounds like it should be good but how does the client use its index instead of getting its own.

My own inbox is the largest of all my users and it shows as having 13,000 emails in the inbox, 29,000 in a subfolder of a discussion group, 44,000 in another discussion group.  So yes - in theory that shouldn't use that much space!  In the subfolder structure on the local machine i have files called eg Inbox and Inbox.msf -- the MSF file for the group with 44,000 posts in it is 24Mb and the file with no extension is 250Mb

I suspect al the MSF files come to over 100Mb - which I assume are the header cache files.  On a netbook with 4G drive and 512Mb memory thats a fairly heavy overhead...  Even if I strip them off each time when I have found and dealt with what I need - it will mean downloading say a 20Mb header before I can even start to search the mail.

---

### Post by jrssystemsnet on 2010-04-01
You've got some misconceptions about the way IMAP works.

A proper IMAP client *always* does searches on the server side; there's a search command built in to the IMAP protocol.  Nothing needs to be downloaded ahead of time for the client to do searches locally, instead, the client sends a query to the IMAP server to be run there, and the results (in the form of message headers matching the query) are returned.

```
search [Charset => $charset,] @searchkeys

Searches the mailbox for messages matching the criteria contained in @searchkeys. This method is valid only when the session is in the selected state.

The @searchkeys list contains strings matching the format described in Section 6.4.4 of RFC2060.

If successful, the server send zero or more search responses. Lack of a search response means the server found no matches. Note that the server can send the results of one search in multiple responses.
```

That's an excerpt from the documentation for Perl's Mail::IMAP module, demonstrating how you use IMAP search methods when writing a client.  AFAIK any IMAP client you are likely to encounter today already does this, which, as I said, leaves the burden of the search on the IMAP server, not the workstation.

As for speeding up those searches... again, 1. use Dovecot or another IMAP server which incorporates built-in indexing and uses it effectively, and 2. SPLIT YOUR MESSAGES INTO FOLDERS and only search the folders you need to, not the entire mailbox.  If you have ten years of mail broken into folders and you think a mail came in "2006 or 2007", searching the 2006 folder and the 2007 folder to look for the mail will go LOTS faster than running a search on the entire mailbox and all subfolders.  Organize intelligently, search intelligently.

> In the subfolder structure on the local machine i have files called eg Inbox and Inbox.msf -- the MSF file for the group with 44,000 posts in it is 24Mb and the file with no extension is 250MbThat's a problem with your client, and no amount of screwing around with the server will fix it - you need to fix it where the problem is, **at the client**.  Since you mention MSF files, I assume you are using Thunderbird.  You need to go into the "Offline & Disk Space" section of the settings for the IMAP account in Thunderbird, then you can adjust local caching to your preference to avoid using excessive disk space locally.

---

