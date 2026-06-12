---
title: "PostFix + Dovecot + Webmin"
date: 2014-12-15
forum: Server Platforms
---

### Post by n_s_simpson on 2014-12-15
Hi Everyone

Well I've decided to configure my own web server for a website I'm putting together. I need emails but have been really struggling and could really do with some help. I'm using Webmin to configure various things with and that's been tough because instructions are extremely sketchy. So this is where I'm up to:

SMTP TLS/SSL - configured properly using my Comodo key
SMTP - I can email out from with Webmin but NOT within Outlook
Dovecot TLS/SSL - configured properly using my Comodo key
Dovecot - I can pick up emails within Webmin and Outlook
Port 587 - configured via "Server Processes" option, which wasn't well documented
Port 25 - disabled  via "Server Processes"

So the problem I have is that within Outlook I can only receive email. Setting outgoing server port to 587 with TLS as the encryption and turning authentication on let's Outlook connect but it won't accept my username and password.

FYI - If I turn off authentication then press the test button says everything is okay but that's because it then only allows mail to be sent within that mailbox. Trying to email to any other email address gives a "Relay access denied" error, which is good since authentication is off.

So I've been reading bits all over the show about getting PostFix to use Dovecot's SASL but can't find anywhere that explains how to configure this within Webmin.

Please can anyone give me some advice?

Cheers

Nick

---

### Post by n_s_simpson on 2014-12-15
FINALLY WORKED IT OUT!!!

Does anything think this eBook is worth buying because the snippets it's given me has massively helped -
[https://books.google.co.uk/books?id=CtgrAwAAQBAJ&pg=PT620&lpg=PT620&dq=webmin+smtpd_sasl_type&source=bl&ots=E_yNNdPCAi&sig=suKnILEsKRwoxtvDSzwyIBPUntQ&hl=en&sa=X&ei=usCOVMGRNsHT7AbWgoDADQ&ved=0CDUQ6AEwAw#v=onepage&q=webmin%20smtpd_sasl_type&f=false](https://books.google.co.uk/books?id=CtgrAwAAQBAJ&pg=PT620&lpg=PT620&dq=webmin+smtpd_sasl_type&source=bl&ots=E_yNNdPCAi&sig=suKnILEsKRwoxtvDSzwyIBPUntQ&hl=en&sa=X&ei=usCOVMGRNsHT7AbWgoDADQ&ved=0CDUQ6AEwAw#v=onepage&q=webmin%20smtpd_sasl_type&f=false)

It had just the snippet of instructions I needed :-D

Woohoo!!!

Nick

---

### Post by n_s_simpson on 2014-12-15
Aha, ebook version downloadable here: [http://it-ebooks.info/book/3516/](http://it-ebooks.info/book/3516/)

---

### Post by nerdtron on 2014-12-15
I'll just put this here.
Full set email server: [http://iredmail.org/](http://iredmail.org/)
Easy setup and install (about 30 mins): [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

Just try it on a fresh install of  Ubuntu 14.04 VM and test drive.

---

### Post by houstonbofh on 2014-12-15
Of course iRedmail has no GUI unless you pay them.  I am not a fan of crackware...  (The first components are free...)

---

### Post by nerdtron on 2014-12-15
> **houstonbofh said:**
> Of course iRedmail has no GUI unless you pay them. 

GUI for user administration? It has, but it's limited. Its good enough for small business. The Pro version is what you pay for more admin control.

Plus you can study the components installed together so next time you try to setup a mail server, you'll be familiar with postfix, dovecot,  etc.

---

