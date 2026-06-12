---
title: "email virus"
date: 2011-08-24
forum: Security
---

### Post by CoyoteUK5 on 2011-08-24
Hi

I am a complete newbie at this and I d enjoy the system compared to winslows it is great .
This morining I woke up and on checking my emails I saw several failed emails deliverys now the last time I had this was on my old computer and I had to do a deep root clean using winslows software.
Now my system is completely linux so I was surprised to see this happen.
Right now I am using clamtk to do a scan but how deep will it go.

So I need help and advice on this:(

---

### Post by lisati on 2011-08-24
It might not be your fault. Malware has been known to forge email addresses: the non-delivery reports you received could be "backscatter", i.e. misdirected bounces.

---

### Post by uRock on 2011-08-24
Doesn't sound like a virus. 

What website is your email through and what application are you using to send your email? 

Can you copy and paste the fail message?

---

### Post by CoyoteUK5 on 2011-08-24
I use yahoo and I just use the interface at their site.
Sorry, we were unable to deliver your message to the following address.

<[sweetsen8on@yahoo.com]("http://uk.mc277.mail.yahoo.com/mc/compose?to=sweetsen8on@yahoo.com")>:
Remote host said: 554 delivery error: dd This user doesn't have a yahoo.com account ([sweetsen8on@yahoo.com]("http://uk.mc277.mail.yahoo.com/mc/compose?to=sweetsen8on@yahoo.com")) [0] - mta157.mail.sp2.yahoo.com [BODY]

--- Below this line is a copy of the message.

Received: from [217.146.183.211] by nm13.bullet.mail.ukl.yahoo.com with NNFMP; 23 Aug 2011 23:20:14 -0000
Received: from [217.146.183.72] by tm4.bullet.mail.ukl.yahoo.com with NNFMP; 23 Aug 2011 23:20:14 -0000
Received: from [127.0.0.1] by omp1033.mail.ukl.yahoo.com with NNFMP; 23 Aug 2011 23:20:14 -0000
X-Yahoo-Newman-Property: ymail-3
X-Yahoo-Newman-Id: [762523.89570.bm@omp1033.mail.ukl.yahoo.com]("http://uk.mc277.mail.yahoo.com/mc/compose?to=762523.89570.bm@omp1033.mail.ukl.yahoo.com")
Received: (qmail 39907 invoked by uid 60001); 23 Aug 2011 23:20:14 -0000
DKIM-Signature:  v=1; a=rsa-sha256; c=relaxed/relaxed; d=yahoo.co.uk; s=s1024;  t=1314141614; bh=TOAdvrHUuQrTofZngGyL3qyQWDyytjLksLkAo3lQqR4=;  h=X-YMail-OSG:Received:X-Mailer:Message-ID:Date:From:Subject:To:MIME-Version:Content-Type:Content-Transfer-Encoding;   b=IjKpWsDPhiunIKH6RqXD5FFRKJuocBjlkbQ3FmBHu8BnPmj8rGq2xRNu+gxnLrdPBB589Ox+xftLKWjr9AcaUIlTQXl9uOkx4FINqIIpBaxB7eNGYowlw4LcmeAHk5qlC8w5CNYdemwv6z6k4oT7RwTp4E3lCA4VVg/eH0HRZOU=
DomainKey-Signature:a=rsa-sha1; q=dns; c=nofws;
  s=s1024; d=yahoo.co.uk;
  h=X-YMail-OSG:Received:X-Mailer:Message-ID:Date:From:Subject:To:MIME-Version:Content-Type:Content-Transfer-Encoding;
    b=2+hL60mVoja2q3sETH/cu7svOea2gMlWLzKFCahFAlb9hGFY0UuLYI8ikdu/ilLhAi13nMEcHTh2jKWHdNuqYg7n6Z+osZTMAJmapNrkQwkoZmDTSA8e/+R/MV+CRxOWwFa7+h7a/RL0AUXvtx2Wz4/l3RRp+X2AvbaXRYMsTao=;
X-YMail-OSG: ysD0b6QVM1nEhiRGfOSzafZQ5OsYNDDkqyUZtkCvZfFnkPW
 0WgAfbIVkLLarmnci1uRN4GCer5QLJQOCSWjLaB1tlrgiL2mrhFDy74JQeeW
 Ps0TQtgQIL2VW2eIhub3dJkJyNpqnKud1q4OvU.kRC5ZSQfSEmaw2L1CXqQ_
 y8gJKRK4gskztSNnskQIYJnX6brm0IBTZ2HXRf3ysceLCMYJoovp0Eiuy1r3
 e08exJB5PRT997POCZwYx5rw3Cr8BPLI03lykGUTxcSiICJKUmvwRBC.SMQO
 A0rz_8oP70oVPI2mN.Po9MKpATVqoEzmj8jBrvjwsFf8F_Ue2z_78llPJjHl
 Wv.bdRLvpKYsoCu3l6nRym1mWW35OXs3AxInrYDnvnI52cXzSGScu2HPwCOf
 STDWl41_vfKWdjEPV7Sz.9PnCQJ4QnKBPfAVTqUfx5FMAm35.iI1dSC3GFb2
 y6I7A9K0CVTKELB9f2987OdtXK8BOFYndpoMKItvBqLxq3mfT3sD1m5.mOkH
 _RGJ2YTp.7qUpKUWPVp8rE3dM1mHr9I9osdKN
Received: from [201.230.108.88] by web27708.mail.ukl.yahoo.com via HTTP; Wed, 24 Aug 2011 00:20:14 BST
X-Mailer: YahooMailWebService/0.8.113.313619
Message-ID: <[1314141614.38386.yint-ygo-j2me@web27708.mail.ukl.yahoo.com]("http://uk.mc277.mail.yahoo.com/mc/compose?to=1314141614.38386.yint-ygo-j2me@web27708.mail.ukl.yahoo.com")>
Date: Wed, 24 Aug 2011 00:20:14 +0100 (BST)
From: Smoking Coyote <[mastersmokingcoyote@yahoo.co.uk]("http://uk.mc277.mail.yahoo.com/mc/compose?to=mastersmokingcoyote@yahoo.co.uk")>
Subject: tf2auk q8j0f7dm
To: [sweetsen8on@yahoo.com]("http://uk.mc277.mail.yahoo.com/mc/compose?to=sweetsen8on@yahoo.com")
MIME-Version: 1.0
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: quoted-printable

ugik2ahhdivr, nsxumx.
 [http://freetimeaperture.com/wp-content/themes/boast/img/lxje.html=20](http://freetimeaperture.com/wp-content/themes/boast/img/lxje.html=20)
66gvwrrjzc 4cma6v sq7tn, 4zze1 mo5jmf0w4tr. s5lw0q3id7 sx2lz5ceut1p.

Here is a copy of one of the mail.
As I never sent one to her and there are 3 others I am sure others have been sent.

---

### Post by CoyoteUK5 on 2011-08-24
I just spoke to a friend today and he got one.
He never opened it but it appeared in the info part as my name plus chinese.
Now I am concerned:(

---

### Post by IWantFroyo on 2011-08-24
Do other computers work? Do other Yahoo accounts work?

If it's in your browser, then it's likely Yahoo's fault.

---

### Post by uRock on 2011-08-24
Sounds like a Yahoo issue. Most likely your Yahoo password was cracked.

---

### Post by Frogs Hair on 2011-08-24
This address in the message <mastersmokingcoyote@yahoo.co.uk> leads to a fake login page .

---

### Post by uRock on 2011-08-24
My recommendation is to close the Yahoo and open a Hotmail or Gmail account.

---

### Post by CoyoteUK5 on 2011-08-24
I got so many people that contact me through my yahoo account it would a week to get to them all as it is also on my cards.
So I shall change my password and see what happens 
Thank all for your help

---

### Post by uRock on 2011-08-24
Be sure to tell them not to open emails from you containing attachments, unless it is something they are expecting.

---

### Post by lisati on 2011-08-24
Good luck if you choose to [report the email to Yahoo]("http://help.yahoo.com/l/us/yahoo/mail/yahoomail/abuse.html") - one of the reasons I chose to set up my own email server was dissatisfaction with the way Yahoo handles complaints.

---

