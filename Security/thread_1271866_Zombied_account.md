---
title: "Zombied account?"
date: 2009-09-21
forum: Security
---

### Post by Samilong on 2009-09-21
I'm a Ubuntu 9.04 user, although I've been using Ubuntu for around four years now. I love Linux, simply because it's so much more secure than Windoze. 

Three weeks ago, my Yahoo account sent out a load of emails - one to everyone in my contacts - with a link to an ftp server. It looked like my computer had become a 'zombie', so I changed my password to prevent a repeat.

Today, it happened again. 

Now, my first thought was "I didn't think this was possible with a Linux machine". My second was "How can I stop this happening again?." I thought changing the password would be enough. How can I track down the malware script or process that is causing this?

Any suggestions?

---

### Post by NiN on 2009-09-21
Hi there!

Could you please explain you measures in more detail?

Did you change your yahoo password or your ubuntu account password?
If it was only your ubuntu account password, do the same for your yahoo account first.
Maybe you logged in to your mail account on some machine, that has been compromised and it stored the password.

Second: Did you install applications from some 3rd party repositories or directly from the net? This information would be helpful.

---

### Post by Samilong on 2009-09-21
> **NiN said:**
> Hi there!

Could you please explain you measures in more detail?

Did you change your yahoo password or your ubuntu account password?
If it was only your ubuntu account password, do the same for your yahoo account first.
Maybe you logged in to your mail account on some machine, that has been compromised and it stored the password.

Second: Did you install applications from some 3rd party repositories or directly from the net? This information would be helpful.

I changed my yahoo password, THEN my ubuntu password. I have only ever accessed my yahoo account from my home pc - never from friends' machines, internet cafes, or even a wifi hotspot whilst outside. And all my applications are installed using 'Add/Remove...' using the default Ubuntu repositories. Not only that, but absolutely NOBODY has keyboard access to my pc. 

How it happened, however, is largely immaterial; the fact that it happened twice seems to suggest that, somehow, somebody has managed to add a process or script to some part of the OS to cause this to occur. Whilst I know a fair bit about computers in general, I know next to nothing about how to spot a malicious script in Linux, because I never even realised they could exist.

---

### Post by cdenley on 2009-09-21
Malicious scripts can certainly exist. It would be next to impossible for someone other than you to run it, though. Are you using strong passwords? Are you running any servers? Are you sure the bulk e-mails are actually coming from your yahoo account, and not simply using your yahoo e-mail address? How are you accessing your yahoo account?

---

### Post by Samilong on 2009-09-21
> **cdenley said:**
> Malicious scripts can certainly exist. It would be next to impossible for someone other than you to run it, though. Are you using strong passwords? Are you running any servers? Are you sure the bulk e-mails are actually coming from your yahoo account, and not simply using your yahoo e-mail address? How are you accessing your yahoo account?

The bulk emails are definitely coming from my account, rather than being spoofed - I know, because I had one arrive in my primary (POP3) email account. 

I'm not running any servers. I access my yahoo account via firefox, logging in every time (rather than leaving it for two weeks, which is an option...

---

### Post by cdenley on 2009-09-21
> **Samilong said:**
> The bulk emails are definitely coming from my account, rather than being spoofed - I know, because I had one arrive in my primary (POP3) email account. 

I'm not running any servers. I access my yahoo account via firefox, logging in every time (rather than leaving it for two weeks, which is an option...

So you received a bulk e-mail in your primary (non-yahoo) account from your yahoo address, and the headers confirm it originated from a yahoo server? Does firefox remember your password? Is your password sent encrypted or plaintext?

---

### Post by Samilong on 2009-09-21
Yes, the email I received confirms that the email came from a yahoo server. 

Firefox does not remember my yahoo password. This is typed in every time I log in. AFAIK, the password is therefore plaintext.

---

### Post by cdenley on 2009-09-21
What IP address did the message come from? If you send the password in plaintext, then someone may very well be intercepting it. Are you sure the password isn't being posted to a page with SSL encryption? If the password isn't being remembered, then either you have some sort of keylogger, your password is being intercepted/guessed, or there is some sort of cross-site scripting attack sending bulk mail with your active session in firefox. Do you use noscript? Were you logged in to yahoo when the bulk mail was sent?
```

sudo apt-get install mozilla-noscript

```

---

### Post by Samilong on 2009-09-21
I'm not sure whether I was logged in when the bulk email was sent; I tend to check my emails 10-15 times a day, so it's possible I was - although it's equally possible that I wasn't.

Do I use noscript? I do now! Thanks for the suggestion.

The full header is as follows (it might help deciphering the problem):


[noparse]Received: (qmail 28666 invoked by uid 60001); 21 Sep 2009 15:40:59 -0000
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=yahoo.com; s=s1024; t=1253547659; bh=/LiIrktPB4gdjKutWzGj2LiYHUWwFTMLUcdjgEClM2k=; h=Message-ID:X-YMail-OSG:Received:X-Mailer:Date:From:To:MIME-Version:Content-Type:Content-Transfer-Encoding; b=KSpOrATEiz56FitaRJyr9RnO4KAotyougelCl9+5Em4HJQtiDsoizytu7pS+g6qJei/28cwu5iaG5b92eh2C40UQbL9JY8wBjWhUd1iqrJzv9j/cX2p0EmEbIRfCov/vc0j7ouzBHgRXzIn2NZ5dx7cwWiM/uHp3Qgepg6EXyMU=
DomainKey-Signature:a=rsa-sha1; q=dns; c=nofws;
  s=s1024; d=yahoo.com;
  h=Message-ID:X-YMail-OSG:Received:X-Mailer:Date:From:To:MIME-Version:Content-Type:Content-Transfer-Encoding;
  b=kVGsecvBDOpHjNg3GAmkvYpilAsQfM+ZWIED0b7XLtgSYS60FOntxjTm3djQ55SefDP6HoVxrriykLeowSLPEPoj8ToYP0TKBR6L64Y0B1gFg1xTABlgvjLFH10JIqW6yBXN9SEqVM4+d06XZAj02gs7IQ9QzpIbOru2r9cvTVE=;
Message-ID: <131073.28656.qm@web110715.mail.gq1.yahoo.com>
X-YMail-OSG: KWbwKfUVM1mqDCmOu2xorLmAZ82ruvehbijQOcbdgo9xSo4W.7HijbNrZ6Mv1.ehwOxf_EGlFuDEh_HcziG2F_5G6Umi36J6jVhn_FSIPdzkG.Ol1IY6gFDedYhXgR.TOd6dFujsUq3yjhhR36rnVaUtK3C4AuzYG1zbL2CRNT0hBMuvcctzqyYYLJudZY_ijJNmy6G0piLOuJPjnujs_0Od3DIsjtegp6z0zYBzOmJaUu3G6i9wUwR8Hg--
Received: from [93.66.70.85] by web110715.mail.gq1.yahoo.com via HTTP; Mon, 21 Sep 2009 08:40:58 PDT
X-Mailer: YahooMailClassic/7.0.14 YahooMailWebService/0.7.347.2
Date: Mon, 21 Sep 2009 08:40:58 -0700 (PDT)
From: Simon <********@yahoo.com>
To: to=********@********.com
MIME-Version: 1.0
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: quoted-printable[/noparse]



(THE MESSAGE TEXT WAS HERE)

(and I wish I knew how to turn off the emoticons... )

Edit: bodhi.zazen: I turned them off for you ;) - use [noparse][noparse][/noparse][/noparse]

---

### Post by cdenley on 2009-09-21
If you put text in a "CODE" tag, you don't have to worry about emoticons.
```
[noparse][CODE]
this is my code

```[/noparse][/CODE]

It looks like that is coming from Yahoo, although it doesn't look like your mail server shows the IP it receives the message from. I'm surprised Yahoo actually puts the user's IP address in the e-mail header. Is that your IP (93.66.70.85), the DSL subscriber in Italy?
```

wget -q -O - http://whatismyip.org/ && echo

```

---

### Post by macabrem on 2009-09-21
I'm sure you have already thought of this - but just in case, make sure your answers to security questions in Yahoo for retrieving your username and password are not obvious.

---

### Post by Samilong on 2009-09-21
Nope. My IP address is 213.107.66.46. So it appears that this email was sent from an IP in Italy using my account. Does that sound about right?

---

### Post by cdenley on 2009-09-22
> **Samilong said:**
> Nope. My IP address is 213.107.66.46. So it appears that this email was sent from an IP in Italy using my account. Does that sound about right?

Yes, that is correct.

---

