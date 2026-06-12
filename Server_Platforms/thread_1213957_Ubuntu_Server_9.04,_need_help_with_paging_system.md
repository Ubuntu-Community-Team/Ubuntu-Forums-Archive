---
title: "Ubuntu Server 9.04, need help with paging system"
date: 2009-07-15
forum: Server Platforms
---

### Post by Jago6060 on 2009-07-15
Runnung:
Ubuntu Server 9.04
Nagios
(all required packages for my goal)

What I'm trying to do: Initially, send a page/SMS/email via command line.  I really need to be able to send all types.  Once I can do it via commandline, I should be able to fairly easily implement it on Nagios.  I've tried using QPage, sendemail, hylafax, etc.  Haven't ahd any luck.  This is my first time attempting this so please be merciful.

What I'm looking for:  An explicit HowTo for any program that can do what I'm looking to do(i.e. send pages/sms/email).  Or an in depth explanation for a program that can do what I need.  I just some advice on how to do what I'm looking to do.

Much appreciated!

---

### Post by Jago6060 on 2009-07-17
Anyone?

---

### Post by UbuKunubi on 2009-07-20
For SMS via a bluetooth phone check this: [http://ubuntuforums.org/showthread.php?t=1204414](http://ubuntuforums.org/showthread.php?t=1204414)

As for email/fax/etc I am still working on this.

Hope this helps,
Ubu

---

### Post by Jago6060 on 2009-07-20
Thanks for the input.  Unfortunately this isn't quite what I'm looking for.  The end goal is to have a page sent to a hospital employee's pager, send an SMS over a network(AT&T, Verizon, etc.), or send an email via shell script from an Ubuntu Server 9.04 computer.

---

### Post by grantemsley on 2009-07-20
Well, for sending an email, use the mail command. (You may have to install the mailx package).  You may also need postfix or some other mail server setup and configured.

For sending an SMS, the easiest (and only free AFAIK) way is to send an email to the appropriate address.  This varies depending on provider, there are lists out there to help.  For my phone with bell canada, I can send an email to <10digitnumber>@txt.bell.ca and it will go to my phone as an SMS.  Most providers let you do this.  Some charge the receiver extra for it.

---

### Post by Jago6060 on 2009-07-20
Could you give an example of the mail command please?

---

### Post by weather15 on 2009-07-20
mail [email]user@user.com[/email]

---

### Post by Jago6060 on 2009-07-20
Hmmm.  Still no luck.  Here is what I did...

```
mail [area code][phone number]@txt.att.net
Subject: test
.
EOT
root@local:~#

```

AND


```
mail [area code][phone number]@cingularme.com
Subject: test
.
EOT
root@local:~#

```


My phone has yet to receive an SMS and its been ~10 minutes since I executed the commands.

---

### Post by kustomjs on 2009-07-20
just let you know it might not come on cingularme.com try mms.att.net or txt.att.net since cingluar is not in service anymore since att bought them out.

---

### Post by Jago6060 on 2009-07-21
No luck :(  I tried mms.att.net and sms.att.net

~Any suggestions?

---

