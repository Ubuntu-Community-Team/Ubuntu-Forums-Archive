---
title: "Fetchmail and Gmail"
date: 2012-02-28
forum: Server Platforms
---

### Post by MauroKTM on 2012-02-28
Good Day,

i'm using a Ubuntu Server with Zarafa CP. I'm using fetchmail for grab the emails and deliver it to Zarafa MDA.

The problem is Fetchmail. Using with IMAP on Gmail I'm not able to grab the folders.

I Tried to fetch the Sent folder configuring fetchmail as follow:
```

poll "imap.gmail.com"
with protocol imap service 993
user "USERNAME"
folder "[Gmail]/Sent Mail"
password "PASSWORD"
nofetchall
ssl
mda "/usr/bin/zarafa-dagent USER -F Sent Items"
```

but returns the following error:

```

Feb 27 23:36:57 cnsat fetchmail[24476]: mailbox selection failed
Feb 27 23:36:57 cnsat fetchmail[24476]: client/server synchronization error while fetching from USERNAME@imap.gmail.com
Feb 27 23:36:57 cnsat fetchmail[24476]: Query status=7 (ERROR)
```

Any Idea?

Thank you
M.

---

### Post by ruffEdgz on 2012-02-28
Just want to share this bit of information about fetchmail and Google Mail:

[http://www.fetchmail.info/fetchmail-FAQ.html#I9](http://www.fetchmail.info/fetchmail-FAQ.html#I9)

Just want to make sure before moving on with helping you that fetchmail says to avoid using their service with Google because of MIME-encoded headers:
> 
Google's IMAP servers, as of April 2008, are broken and re-encode MIME-encoded headers improperly and are not feature-complete yet. The model how their servers organize mail also deviates in significant ways from what the POP3 or IMAP protocol 'fathers' conceived. This means all sorts of strange effects, for instance, your sent mail may show up in the mail that fetchmail fetches. It's best to avoid fetching mail from Google until they are using standards-compliant software.


---

### Post by MauroKTM on 2012-02-28
Thank you for the answer.

So... What kind of email fetcher can be used?

Thank you,
M.

---

