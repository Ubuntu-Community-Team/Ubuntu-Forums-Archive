---
title: "New type of spam"
date: 2009-05-18
forum: The Cafe
---

### Post by .Michael on 2009-05-18
Heres what I see in my inbox.

Original header as follows:
                                                                                                                                                                                                                                                               
> Delivered-To: [email]michael16@gmail.com[/email]
Received: by 10.216.72.7 with SMTP id s7cs177343wed;
        Mon, 18 May 2009 10:18:22 -0700 (PDT)
Received: by 10.224.19.131 with SMTP id a3mr6617102qab.23.1242667101778;
        Mon, 18 May 2009 10:18:21 -0700 (PDT)
Return-Path: <elizabethcampbell39140@yahoo.com>
Received: from web59509.mail.ac4.yahoo.com (web59509.mail.ac4.yahoo.com [76.13.12.183])
        by mx.google.com with SMTP id 30si5908101qyk.149.2009.05.18.10.18.21;
        Mon, 18 May 2009 10:18:21 -0700 (PDT)
Received-SPF: pass (google.com: domain of [email]elizabethcampbell39140@yahoo.com[/email] designates 76.13.12.183 as permitted sender) client-ip=76.13.12.183;
Authentication-Results: mx.google.com; spf=pass (google.com: domain of [email]elizabethcampbell39140@yahoo.com[/email] designates 76.13.12.183 as permitted sender) smtp.mail=elizabethcampbell39140@yahoo.com; dkim=neutral (body hash did not verify) header.i=@yahoo.com
Received: (qmail 55074 invoked by uid 60001); 18 May 2009 17:16:20 -0000
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=yahoo.com; s=s1024; t=1242666980; bh=hkO3Dr/OM0XzWEjFxmndLDhDlIpN0k45VYLVIlnRpK0=; h=Message-ID:X-YMail-OSG:Received:X-Mailer:Date:From:Subject:To:MIME-Version:Content-Type; b=fl6o77EptB3U3WntwHHnfkpzCs1iOYhkocm1hO5/qLbEADrbftRkx5c8a4RkM3x7CRP2vLUMpc9A41Sige/FNBoD2TOsVyMmJbAaXlJ1w5JYylQqgSeBtAyviqpvt9q0avx1ZmHHc2pjafN4bV/I3Grb9Kd+YESWSNAgU1K23tg=
DomainKey-Signature:a=rsa-sha1; q=dns; c=nofws;
  s=s1024; d=yahoo.com;
  h=Message-ID:X-YMail-OSG:Received:X-Mailer:Date:From:Subject:To:MIME-Version:Content-Type;
  b=iKBy4+/Z2OO8RvB3WNDE+LLrUzAt/ShwJxDvUhcTYnU8VeYJxhAy3HwkXdrxa6nhmkDXxlgA9eNGw/Jxamx8UcA+Qo65yWnBQB8aGBL/sceuqxcSlT//lwMmYDIuhHTn7rb+kO5G7vONOrUIU7li/HDQogLpw2of7m/va7ONidk=;
Message-ID: <365089.54234.qm@web59509.mail.ac4.yahoo.com>
X-YMail-OSG: 38emYlwVM1mN4LfFu_DfrBZ6RRfCw_d141dwItpSNoO8MHoeG66kc1EpR_l8DeE8VFjPUGRGaMUkEa0KX3RY5wcLDtjM19oDTFImWptTbhN1moz3pB5L8QcefxQEVjFdtQN4ZpvvTrg5LGEi32CS.Q55Etiv78qEWWrCGCjTgovxEnXdwx9NvOMxRxc0_yOVtomEk2KxjbXrgf.QQv5qppwUjOMOxxCl1CpBQmALFdabH.OrCYUE9kH0
Received: from [77.91.231.172] by web59509.mail.ac4.yahoo.com via HTTP; Mon, 18 May 2009 10:16:20 PDT
X-Mailer: YahooMailClassic/5.2.20 YahooMailWebService/0.7.289.10
Date: Mon, 18 May 2009 10:16:20 -0700 (PDT)
From: Elizabeth Campbell <elizabethcampbell39140@yahoo.com>
Subject: last
To: Kenneth Miller <rsuzyvolrcrjxn@hotmail.com>
MIME-Version: 1.0
Content-Type: text/plain; charset=us-ascii


[http://www.kathy8579.gtentaj.mobi/](http://www.kathy8579.gtentaj.mobi/)


      


It's not addressed to me in anyway as I can see.

---

### Post by lisati on 2009-05-18
I've had similar emails where it's not immediately obvious from the headers that it was meant for me.
I'm not sure of the full details but I believe there's a way of sending mail to people without explicitly mentioning them in the headers that you get to see in your email client - something to do with ENVELOPEs and things of that nature included in the protocols used for sending mail.

EDIT: By the way, the "from" and "reply-to" headers aren't a reliable guide to who actually sent the email. It's very easy to forge them if you know how. I've had spam supposedly from myself, but a quick look at the "received" headers shows that it probably wasn't from any of my machines.

---

### Post by billgoldberg on 2009-05-18
I got another new type of spam the other day.

Well note exactly spam, but still.

I was checking my email when gmail popped open a little IM applet in the bottom right corner and some women started chatting with me.

I replied saying I didn't know here and then she stated she could offer me SEO services for my blog for a good price. Insta-block.

What that feature called anyway, Gtalk?

---

### Post by .Michael on 2009-05-18
That's SPIM.

[http://en.wikipedia.org/wiki/Messaging_spam](http://en.wikipedia.org/wiki/Messaging_spam)

I also know about Domain Key which allows you to see if an email is actually from a said email service and not from someone's sendmail daemon.

---

