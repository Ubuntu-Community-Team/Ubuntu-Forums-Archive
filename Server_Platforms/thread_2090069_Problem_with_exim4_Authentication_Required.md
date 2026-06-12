---
title: "Problem with exim4: Authentication Required"
date: 2012-12-01
forum: Server Platforms
---

### Post by Methus on 2012-12-01
Hello all!

I installed exim4 on my Ubuntu 12.04 LTS server to serve as my MTA. I followed this tutorial to set it up:
[Configuring exim4 in Ubuntu to use GMail for SMTP]("http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/")

What's got me scratching my head is that I keep getting an "Authentication Required" error in exim4's mainlog. And to top it off, I did this exact same setup with another server, and it works just fine. I even went as far as copying the exim4.conf.template file over from the other server to see if that works, which it didn't. The only thing that's really different between the two servers is the hostname, but I don't see how that could come in to play here.

My main reason for having this setup is for notifications. This server will be in a remote location, and I would like mail sent to root to be forwarded to my e-mail that I have with Google. Like I said, this is what I did with another server without a problem.

Below is my /var/log/exim4/mainlog for review, with only personal edited out:
```
2012-12-01 02:45:01 1Teih3-0004zT-RP <= administrator@server U=username P=local S=480
2012-12-01 02:45:03 1Teih3-0004zT-RP ** myEmailAddy@gmail.com <root@server> R=send_via_gmail T=gmail_smtp: SMTP error from remote mail server after MAIL FROM:<administrator@server> SIZE=1518: host gmail-smtp-msa.l.google.com [2607:f8b0:400e:c00::6c]: 530-5.5.1 Authentication Required. Learn more at\n530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 tm8sm4453389pbc.48
2012-12-01 02:45:04 1Teih6-0004zW-4k <= <> R=1Teih3-0004zT-RP U=Debian-exim P=local S=1616
2012-12-01 02:45:04 1Teih3-0004zT-RP Completed
2012-12-01 02:45:05 1Teih6-0004zW-4k ** myEmailAddy@gmail.com <administrator@server> R=send_via_smtp T=gmail_smtp: SMTP error from remote mail server after MAIL FROM: <> SIZE=2680: host gmail-smtp-msa.l.google.com [2607:f8b0:400e:c03::6c]: 530-5.5.1 Authentication Required. Learn more at\n530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 o10sm4350484paz.37
2012-12-01 02:45:05 1Teih6-0004zW-4k Frozen (delivery error message)
```

If you need any more information just ask. Any help, advice, or pointing in the right direction is very much appreciated. I want to learn what's going on and why just as much as I want to fix it.

---

### Post by Methus on 2012-12-10
Does anyone have perhaps even a tiny little inkling of an idea as to what may be going on..?

---

### Post by nickmcg on 2012-12-20
I've got the same problem - it looks like the gmail credentials aren't being sent to the smtp server - in your case, it looks as if root@server and administrator@server have been used to try & login, rather than your gmail address.
I don't know if the password is being sent either.

I know it's of little comfort, but you're not the only one who'd like the answer to this.

Cheers

Nick

---

### Post by nickmcg on 2012-12-20
Good news. It seems to be working on my system (at last).

I did a clean install of exim4
> sudo apt-get -y remove exim4 exim4-base exim4-config exim4-daemon-light
sudo apt-get -y purge exim4 exim4-base exim4-config exim4-daemon-light
sudo apt-get install exim4
Then I followed the instructions on this site [http://tompurl.com/2011/09/17/exim-gmail-on-ubuntu/](http://tompurl.com/2011/09/17/exim-gmail-on-ubuntu/) or this one [http://php.quicoto.com/setup-exim4-to-use-gmail-in-ubuntu/](http://php.quicoto.com/setup-exim4-to-use-gmail-in-ubuntu/)

The only thing I did slightly differently was in passwd.client, where I used 2 lines
> *.google.com:myname@gmail.com:mypassword
*.gmail.com:myname@fmail.com:mypassword

I didn't do any of the other manual modifications in the other how-to's.

HTH

Nick

---

### Post by Methus on 2012-12-20
I can confirm that this works!

Well whataya know...seems the simple things (uninstalling, re-installing) is sometimes the best answer. I had thought I did do this, but I don't think I purged everything.
Regardless, thanks for the share!

---

