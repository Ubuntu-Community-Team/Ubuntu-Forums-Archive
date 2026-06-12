---
title: "Spam Assassin / Procmail"
date: 2008-02-29
forum: Server Platforms
---

### Post by kiplingw on 2008-02-29
I am using an IMAP based mail server. I've created an IMAP mail folder called "Junk" with SpamAssassin on the server side as well. It works by being wired into a procmail recipe:

```

# Spam filter using lock and for files no larger than 256K...
:0fw: spamassassin.lock
* < 256000
| spamassassin

# Message was tagged as at least level 8, file as spam. See also 
#  ~/.spamassassin/user_prefs
:0
* ^X-Spam-Level: \*\*\*\*\*\*\*\*
.Junk/

# All mail tagged as spam (eg. with a score higher than the set threshold)
#  is moved to "Junk".
:0
* ^X-Spam-Status: Yes
.Junk/

# Work around procmail bug: any output on stderr will cause the "F" in "From"
#  to be dropped.  This will re-add it.
:0
* ^^rom[ ]
{
  LOG="*** Dropped F off From_ header! Fixing up. "
  
  :0 fhw
  | sed -e '1s/^/F/'
}


```


This manages to catch quite a bit of spam and deliver it into my Junk folder. But it misses quite a bit as well and that ends up in my inbox folder.

My question is, after I move the junk that it missed from my IMAP inbox to IMAP junk folder, is there any may that I can get SpamAssassin on the server to update its training with the new messages in the junk folder?

Kip

---

### Post by rapiscan on 2008-02-29
I'm not all that familiar with spam assassin, but this looks like a pretty good how-to:

[http://faisal.com/docs/salearn](http://faisal.com/docs/salearn)

---

### Post by kiplingw on 2008-02-29
Thank you. This is precisely what I require.

Kip

---

