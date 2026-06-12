---
title: "Off-site network backup"
date: 2009-01-23
forum: The Cafe
---

### Post by mssever on 2009-01-23
I've decided I *really* need to get serious about backing up my data. Furthermore, since I'm going to be spending quite a lot of time traveling in the near future, I'm going to need off-site Internet-based storage, which I won't be able to host myself. My Google searches didn't turn up anything relevant (I was probably using the wrong terms).

At the minimum, a suitable service must:

[LIST=1]
[*]Be inexpensive
[*]Be reliable--preferably with some sort of cash guarantee against data loss
[*]Work with Linux
[*]Be schedulable--ideally from cron
[*]Avoid sending login credentials in clear text
[/LIST]
I'd prefer a service that also:

[LIST=1]
[*]Preserves permissions
[*]Works with rsync and/or other standard tools
[*]Uses end-to-end encryption
[/LIST]
Anybody know of such a service?

---

### Post by mssever on 2009-01-23
bump

---

### Post by Nepherte on 2009-01-23
Any hosting with ssh access would do.

---

### Post by mssever on 2009-01-23
> **Nepherte said:**
> Any hosting with ssh access would do.
Not necessarily. For example, a number of hosting plans make no data-preservation guarantees.

---

### Post by Nepherte on 2009-01-23
In my opinion, data preservation guaranty is an illusion. If you have one copy on an external hard disk and another on a remote place besides the original, you're pretty safe.

---

### Post by brucewagner on 2009-03-11
I too am looking for such a service...  Any ideas, anyone?

---

### Post by frrobert on 2009-03-11
I am currently using Amazon Simple storage. I use the s3cmd tool to transfer the files.  It is a command line tool.  It allows encryption of data with PGP if desired.  Transfers can be done by http or https.

---

### Post by beercz on 2009-03-12
I use this all the time: [rsnapshot.org]("http://rsnapshot.org")

Once configured, stick it in a cron job and enjoy.

I have the output redirected to a log file which is then copied to my machine using scp.

Been using it for about 4 years, never let me down.

---

### Post by t0p on 2009-03-12
I'm afraid I don't have a link for this... but there's a project that enables one to use the storage space of a Gmail account as online storage for files.  The user can even mount the space as a drive.  There's a book about it, called *Hacking Gmail* by Ben Hammersley.  Google should help you find the details, if you're interested.

---

