---
title: "Sendmail - Sending email directly to a networked printer ..."
date: 2009-03-23
forum: Server Platforms
---

### Post by whitegourd on 2009-03-23
Background - We have an individual that doesn't have a computer, but does have a network printer in his office.

Looking for some help/assistance w/ Sendmail.  I'm trying to get incoming emails to print directly to this networked printer. So far I am able to get everything in the email to print.  I added the following ...

in /etc/aliases

userprt: "| lp -d 'user_printer"

So when I get an incoming email it'll get printed directly to the 'user_printer', but haven't figured out how to create a filter to filter out the header info, etc.  I'd like to have the print job look as if it was printed out from a typical email client.

Tried searching for pre-built scripts, but nothing seems to come up.  Anyone have any ideas on how I can get this accomplished?

---

### Post by Bachstelze on 2009-03-23
I guess you could just use the standard tools like head, tail, sed, awk, grep, etc. to filter out the headers.

---

### Post by whitegourd on 2009-03-23
> **HymnToLife said:**
> I guess you could just use the standard tools like head, tail, sed, awk, grep, etc. to filter out the headers.

I could, but was hoping that there was some sort of pre-established program that can do this.

Took a look at 'formail' and it seems to work w/ the header portion, but will also need to remove some of the unnecessary items from the body of the email as well.  Anyone have any experience with 'muttprint'?  Wonder if that'll do the job.

---

### Post by brian_p on 2009-03-24
> **whitegourd said:**
> 

I could, but was hoping that there was some sort of pre-established program that can do this.

I picked this up from somewhere. You'll like it.

```
perl -ne 'if (/^\s*$/) {$b=1;} print if (/^(Subject|From|To|Date|Cc|Bcc):/||$b);' email
```

---

### Post by HermanAB on 2009-03-24
Hmm, it will take a nominally sane person about 6 weeks to figure out what that line does.

Cheers,

Herman

---

