---
title: "ubuntu and spamassassin 3.2.5 open-whois.org false positive"
date: 2010-04-25
forum: Server Platforms
---

### Post by edgeconsults on 2010-04-25
Is there way to remove open-whois.org as an rbl from 
 /usr/share/spamassassin/50_scores.cf
 /usr/share/spamassassin/72_active.cf

It's creating a lot of false positives on a mail server i am using with ubuntu.  i noticed only ubuntu lucid is using updated spamassassin 3.3.1 and all others are using 3.2.5

i was on spamassassin's website and noticed this issue has been resolved on spamassassin 3.3.1 but not 3.2.5

i tried looking in those files but they are too complicated for me to understand.

i also tried running sa-update but not sure if that is going to help.

i am assuming they manually have to be removed.

can anyone help with the open-whois.org rbl removal from mail servers as it is currently squatted and creating false positives?

thank you

Edwin

---

### Post by edgeconsults on 2010-04-27
2.4 DNS_FROM_OPENWHOIS     RBL: Envelope sender listed in bl.open-whois.org.

how do i remove the 2.4 DNS_FROM_OPENWHOIS point rule?

thank you.

---

### Post by ian dobson on 2010-04-27
Hi,

Can't you just edit your local.cf and change the score to 0.

Regards
Ian Dobson

---

### Post by edgeconsults on 2010-04-29
there is nothing in the local.cf file under /etc/spamassassin/

there is however under /usr/share/spamassassin a file called 72_active.cf that lists open-whois.org but it is listed all over the place.

do you not have spamassassin installed on your ubuntu server?

---

### Post by edgeconsults on 2010-04-29
ok i figured it out.  i found it what was wrong.  turns out sa-update was downloading the new rules but not applying them.

if anyone needs help just ask and i can post a howto on manually updating your rules.

---

### Post by ian dobson on 2010-04-29
> **ian dobson said:**
> Hi,

Can't you just edit your local.cf and change the score to 0.

Regards
Ian Dobson

Yes, I'm running spamassassin on my ubuntu server. In my /etc/spamassassin directory there are several .cf files:-

65_debian.cf      backup    init.pre.dpkg-dist  PDFInfo.cf      v310.pre  v320.pre
70_zmi_german.cf  init.pre  local.cf            sa-update-keys  v312.pre  v320.pre.dpkg-dist

Did you install spamassassin using apt-get or manually?

Regards
Ian Dobson

---

