---
title: "Ubuntu 10.04 TLS Postfix Malformed mime type"
date: 2012-02-15
forum: Server Platforms
---

### Post by kyleh0000 on 2012-02-15
Hi All,

I have been hunting a round these forums and across the almighty google for a while now and not been able to resolve my problem, Im hoping someone in the community will be able to assist.

We currently have a postfix/dovecot email server setup and running on 10.04 x64 LTS release with latest updates. Everything is working well except for the fact we are having issues with users receiving messages from one particular address which seems to have a mail server that is sending mal formed attachments.

Normaly I would just say well to bad they need to correct there mail server, however this is coming to our Bussiness Director from a legal firm so its pretty important we get it working. 

For a bit more backup ground information we are an all MAC school and last year we were running the mail server that shipped with OSX 10.6 and these emails were working last year, now that not to say that this other domain didn't upgrade or change there mail servers over xmas which has broken it, so I'm not sure if this error happens on OSX 10.6 or not.

Anyway here is a sample of the code that gets messed up, basically this should be some text with a PDF attachment, i won't include the whole email as most of it is classified but I'm pretty sure the stuff I'm posting is the important bit.

--_005_F0A153B9B646B34B9E038899306D5EEB179F5224C7EMAADLDC01EMA_
Content-Type: multipart/alternative;
	boundary="_000_F0A153B9B646B34B9E038899306D5EEB179F5224C7EMAADLDC01EMA_"

--_000_F0A153B9B646B34B9E038899306D5EEB179F5224C7EMAADLDC01EMA_
Content-Type: text/plain; charset="us-ascii"
Content-Transfer-Encoding: quoted-printable

From what i can tell its the --_ at the start of mime attachment that is breaking this there are a few things i have tried to resolve this issue but so far it still seems to be not working...

I found this post...

[http://www.irbs.net/internet/postfix/0701/0624.html](http://www.irbs.net/internet/postfix/0701/0624.html)

which i tried and I thought it resolved the issue but it seems to have popped up again today.

I also have spammassisin and amavis installed as well, which I'm thinking i might try and disable for a while to see if the issue is fixed.

Im not getting any errors in the log files related to this user or this email.

however recently (must have only been the last few days) I have been getting the follow errors pop up in the log


Created dotlock file's timestamp is different than current time (1329298234 vs 1329298277)

this message is coming up on various user account quite frequently.

From reading this is due to the fact we have the mail store on an NFS volume and there is a time difference on the NFS server and mail server.

however they both have the same NTP server set.

I dont believe the NFS store is the issue as far as mime attachment goes, however I'm considering moving the mail store to a local drive  to try to resolve these error messages.

all your thoughts ideas and suggestions are welcome!

---

### Post by kyleh0000 on 2012-02-22
Still haven't managed to figure this one out yet but i have ruled out amavis-new as the cause

I did a test and uninstalled it from the mail server and the problem remains

I can reliably test it now, as it seems to be happening to the emails getting received from the iTunes password reset link

I think it must be something to do with emails when they have a plain text and html version in the same email but i can't be sure

any able to point me in the right direction?

---

### Post by kyleh0000 on 2012-02-22
ok just for anyone else that has this issue i THINK i have resolved the issue, it appears alter mime was to blame

it was my understanding that this only affected outgoing emails but apparently it also processes incoming mail as well.

After I disabled the alter mime content process in the master.cf file it all looks to be resolved

So far i have only tested receiving mail from id.apple.com and not the other address that were broken but they we both bringing out similar errors so I'm hopeful this will solve the issue!

cheers

---

