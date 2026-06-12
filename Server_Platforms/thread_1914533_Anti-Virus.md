---
title: "Anti-Virus?"
date: 2012-01-24
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-01-24
Should I be running some kind of anti-virus on my webserver / sftp server? If so, what kind of recommendations does everyone have?

---

### Post by Tony Flury on 2012-01-24
Are you going to allow people to upload and execute arbitary binaries or other executables ?

If not - then I don't see a need for an Anti-Virus. A good firewall is a must though, as well as a very robust password policy.

---

### Post by ubudog on 2012-01-24
As long as you don't install stuff from unknown origins, you should be good.  :)

Check the link posted by 1clue for more info on what you can do.

Best,
ubudog

---

### Post by uteck on 2012-01-24
If people will be uploading files from a virus prone OS, then you may want to consider it to protect people that might download the infected file. 
It may not be a bad idea for a webserver on general principle just encase someone should upload some malicious code by some other means.

---

### Post by SeijiSensei on 2012-01-24
If you manage file uploads using scripts, like with PHP, you can scan the uploads before committing them to the server.  Just install clamav and have your script run clamscan against the uploaded file.  If it comes up positive, dump the file and warn the user.  I'd definitely take this route if you are going to provide a file-sharing service of any kind that includes Windows users. It's not just executable files that you need to scan; even a Word document can contain a "[macro virus]("http://en.wikipedia.org/wiki/Macro_virus")."

---

### Post by ubudog on 2012-01-24
> **seijisensei said:**
> if you manage file uploads using scripts, like with php, you can scan the uploads before committing them to the server.  Just install clamav and have your script run clamscan against the uploaded file.  If it comes up positive, dump the file and warn the user.  I'd definitely take this route if you are going to provide a file-sharing service of any kind that includes windows users. It's not just executable files that you need to scan; even a word document can contain a "[macro virus]("http://en.wikipedia.org/wiki/macro_virus")."

+1000

---

### Post by 1clue on 2012-01-24
> **ubudog said:**
> There is really no need for AntiVirus in Linux.  See this for stuff you can do to make it more secure:
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) 

As long as you don't install stuff from unknown origins, you should be good.  :)

Best,
ubudog

I Really, Really, Do Not Like generalizations like that.

And this is a better security link IMO:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by QIII on 2012-01-24
+1 to 1Clue.  Sitting on our arrogant haunches makes us sitting ducks for the PFY (pimply faced youth) who is even now uploading the Linux-killer from his computer in his mother's basement.

Let's not fall asleep on the perimeter.

---

### Post by ubudog on 2012-01-24
> **QIII said:**
> +1 to 1Clue.  Sitting on our arrogant haunches makes us sitting ducks for the PFY (pimply faced youth) who is even now uploading the Linux-killer from his computer in his mother's basement.

Let's not fall asleep on the perimeter.

+1 to 1clue as well, you have a good point.

---

### Post by 1clue on 2012-01-24
Since I have the attention of an official staff member, what would it take to get a link to the BasicSecurity wiki near the top of the Security wiki?

With something like, "If you don't understand the terms being used here, you might want to try the BasicSecurity wiki"

Thanks.

---

### Post by codmate on 2012-01-24
I haven't tried the Linux varient, but NOD32 has always worked well for me in the Windows world.

---

### Post by |{urse on 2012-01-24
If you're running a linux mailserver then it's a good idea so you can stop the spread of win viruses from user to user via email.

---

### Post by SeijiSensei on 2012-01-25
> **|{urse said:**
> If you're running a linux mailserver then it's a good idea so you can stop the spread of win viruses from user to user via email.

If you're running a mail server and not scanning *every message* with something like MailScanner, amavisd, or clamd, you should get out of the mail-serving business today.

My clients' MailScanner quarantines are smaller than they used to be, but new infected messages still arrive every day.

---

### Post by ubudog on 2012-01-26
> **1clue said:**
> Since I have the attention of an official staff member, what would it take to get a link to the BasicSecurity wiki near the top of the Security wiki?

With something like, "If you don't understand the terms being used here, you might want to try the BasicSecurity wiki"

Thanks.

It'd be best to contact an admin about that.

---

### Post by Vegan on 2012-01-26
clamav is available that can help secure a rig

---

