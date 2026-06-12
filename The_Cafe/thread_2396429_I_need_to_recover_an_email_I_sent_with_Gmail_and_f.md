---
title: "I need to recover an email I sent with Gmail and forwarded to myself"
date: 2018-07-14
forum: The Cafe
---

### Post by Gnusboy on 2018-07-14
First, please forgive me if I'm posting in the wrong forum, or
if I should not ask questions involving non-linux software. If so, I'll take it down.

I tried all the advice given from the Gmail help forums, but did not find out how to fix my problem without luck.

I am using Gmail for Firefox on Ubuntu Linux desktop


I  need to recover an email I sent to a person's Gmail address, that I also forwarded to myself at the same time. It's not in either my inbox, sent mail or trash folders.
It's only been a few days since it was sent and should not have been deleted by the Gmail 30 day purge.

 I often copy and send messages, or forward them to  myself to use at a later date. However, when I searched using all of  the suggested tools I am still unable to find the actual message. 

What I did  find was two messages that were marked as drafts, but had none of the missing message text inside. The email had the correct address line that was the accurate person's email address, and showed the correct address where I forwarded it to, (mine) and the proper subject line.

I followed the Gmail help sections and looked everywhere it could have gone. But I didn't find what I needed.  I have tried every solution to my issue without getting it solved so I'm hoping someone here can help figure it out.

I don't understand why I could find the heading of the message, but not the message itself. Especially since it should have gone to the original sent message folder and personal inbox, but it was not in either of those locations. 

Stranger still, is a bizarre piece of code that was buried inside of the email. This code, is attached below and it doesn't make sense for it to be there. I found it by accident when I checked the "original" message code.

It looks  like html markup, but it's still weird. I have attached it below.

I contacted Gmail, but there was no response by them or in the Gmail forum.

Can anyone here help me understand these issues or know what further steps I can take now? I've tried to make this request as concise as I can.

Thanks for helping me.

Thanks.

Jess Henryes

-----------------------------------------------------------------------------------------
This is the  strange code that I do not understand.

                         Received: by 2002:a50:941a:0:0:0:0:0 with SMTP id p26-v6csp1780943eda
 Mon
 X-Google-Smtp-Source: AB8JxZpnK6WAfgZ3dBvYjyTupy+nhX1jjuZtwJTJLYPlK9ESgsGhS2WBgYTpnpkvll/0QepKqaLz
 X-Received: by 2002:adf:8b02:: with SMTP id n2-v6mr12051679wra.282.1527530460557
 Mon
 28 May 2018 11:01:00 -0700 (PDT)
 ARC-Seal: i=1
 
```

a=rsa-sha256

 t=1527530460

 cv=none
 d=[google.com]("http://google.com")
 s=arc-20160816
 b=IrX5azr8F1xDQNHsj0uQtC8hZJcYnc2uSAlkWCKHLTe0FD3sPQcSG2fLKN8HF8kyqV
 A3/qwqbRUwKc529N+IFxdAHtdC8bzgSOvxbeEHGcnNO1+uXst+QrS9QBAhJx79hqAjdd
 GxiPfdwHVgq20gOQo0GO2yEUjLkLdWOgqyqxMNjnGCI3Sk/k6AP04qk7KD0M8UrE7lck
 D2E+Mmf+9b+bijkR3wpQPBbPULG7MpDBDBa/Er+IbBtbLDLzFmyaEiQMhVs8g8HKfzA0
 tSWw==
 ARC-Message-Signature: i=1
 a=rsa-sha256
 c=relaxed/relaxed
 d=[URL="http://google.com"]google.com
[/URL]
```[URL="http://google.com"]
[/URL]

 ```
 
s=arc-20160816

 h=to:subject:noreen-comet-******:message-id:worthiness-checker:date
 :preview-inhere-scope:mime-version:levelling-kline:from
 :list-unsubscribe:content-transfer-encoding:phelps-acidly-loose
 :arc-authentication-results:

```

```


 bh=92E4rvFAdcSi13z7MwsWsvJ+PdLzQyBkAmvBkCuNYnU=
 b=gWXaeJAm76+mQWsZ+2BJu4l52W/JUZY9JhCouTVgety9rjTQ8wJardUfcfhS4pgKce

 fzjiyTtnj9P7YVF81/zytrbaPsZO3YqV2NKH1CQcLuQAnOwddE1ozF4xF0tKFsIDOIw7
 jACcx4BvNuYAy8JSeRshPFtKk5DduwnLfQ4h7Kh2MA1Fq7TkG7npNXHIq4TYcENNfQWM
 HL1YIVWWFHo0X911H7GOgYs5C3+q2PVtSeUaghTawtqblujQnn0nMHrsrdAlIFdMH2sD

 ce/U7B5y/nrExj77SBzDoQLrPLowPewV5101JVeQ3bIGYyY6shdaV+w9jwB5hDKdbeX/
 iRyw==
 [mx.google.com]("http://mx.google.com")
 spf=neutral ([google.com]("http://google.com"): 88.198.70.168 is neither permitted nor denied by best guess record for domain of extrac...@lipyumi.com) smtp.mailfrom=extrac...@lipyumi.com
 Return-Path: (extrac...@lipyumi.com)
 Received: from [izone5.brawaa.com]("http://izone5.brawaa.com") ([izone5.brawaa.com]("http://izone5.brawaa.com"). [88.198.70.168])
 by [mx.google.com]("http://mx.google.com") with ESMTP id v14-v6si2836347wmf.143.2018.05.28.11.00.59
 for
 Mon
 28 May 2018 11:01:00 -0700 (PDT)

 Received-SPF: neutral ([google.com]("http://google.com"): 88.198.70.168 is neither permitted nor denied by best guess record for domain of extrac...@lipyumi.com) client-ip=88.198.70.168
 Authentication-Results: [URL="http://mx.google.com"]mx.google.com
[/URL]
```[URL="http://mx.google.com"]
[/URL]

 ```

spf=neutral ([google.com]("http://google.com"): 88.198.70.168 is neither permitted nor denied by best guess record for domain of extrac...@lipyumi.com) smtp.mailfrom=extrac...@lipyumi.com

 Phelps-Acidly-Loose: reap
 Content-Transfer-Encoding: 7bit
 List-Unsubscribe: (mailto:phcqkn...@lipyumi.com)
 From: Notification (extrac...@lipyumi.com)
 Levelling-Kline: c97a22191a7
 MIME-Version: 1.0
 Preview-Inhere-Scope: 546
 Date: Mon
 28 May 2018 22:01:00 +0000
 Worthiness-Checker: e3fc43fcf
 X-Mailer: Morbid
 Message-ID: (99e4df7f-ead...@lipyumi.com)
 X-Auto-Response-Suppress: None
 Noreen-Comet-******: 27
 Subject: Security alert for your account
 Content-Type: text/html
 charset=UTF-8
 format=flowed
 delsp=yes
 To: @[URL="http://gmail.com"]gmail.com

[/URL]
```[URL="http://gmail.com"]
[/URL]

 ```

[html lang=en

 meta name=format-detection content=date=no/
 meta name=format-detection content=email=no/
 style
 .awl a {color: #FFFFFF
 text-decoration: none
 }.abml a {color: #000000
 font-family: Roboto-Medium
 Helvetica
 Arial
 sans-serif

 font-weight: bold
 text-decoration: none
 } .afal a {color: #b0b0b0
 text-decoration: none
 } @media screen and (min-width: 600px) {.v2sp {padding: 6px 30px 0px
 }

 .v2rsp {padding: 0px 10px
 } (/style)

 tr align=center
 table border=0 cellspacing=0 cellpadding=0 style=padding-bottom: 20px, max-width: 600px, min-width: 220px,

 tr

 tr signal='4'

 table milestones=37 width=100% border=0 cellspacing=0 cellpadding=0 style=direction: ltr, padding-bottom: 7px,
 /i

 /td

 /tr
 /span
table coarse='3' class=v2rsp width=100% border=0 cellspacing=0 cellpadding=0

 tbody goto=gretchen

 tr nightclub='81'

```


If this is the wrong place to ask about this, please tell me where I should go to ask my question.
Any help is appreciated. Thank you. Jess

---

### Post by Gnusboy on 2018-07-14
First, please forgive me if I'm posting in the wrong forum, or
if I should not ask questions involving non-linux software. If so, I'll take it down.

I tried all the advice given from the Gmail help forums, but did not find out how to fix my problem without luck.

I am using Gmail for Firefox on Ubuntu Linux desktop


I  need to recover an email I sent to a person's Gmail address, that I  also forwarded to myself at the same time. It's not in either my inbox,  sent mail or trash folders.
It's only been a few days since it was sent and should not have been deleted by the Gmail 30 day purge.

 I often copy and send messages, or forward them to  myself to use at a  later date. However, when I searched using all of  the suggested tools I  am still unable to find the actual message. 

What I did  find was two messages that were marked as drafts, but had  none of the missing message text inside. The email had the correct  address line that was the accurate person's email address, and showed  the correct address where I forwarded it to, (mine) and the proper  subject line.

I followed the Gmail help sections and looked everywhere it could have  gone. But I didn't find what I needed.  I have tried every solution to  my issue without getting it solved so I'm hoping someone here can help  figure it out.

I don't understand why I could find the heading of the message, but not  the message itself. Especially since it should have gone to the original  sent message folder and personal inbox, but it was not in either of  those locations. 

Stranger still, is a bizarre piece of code that was buried inside of  the email. This code, is attached below and it doesn't make sense for  it to be there. I found it by accident when I checked the "original"  message code.

It looks  like html markup, but it's still weird. I have attached it below.

I contacted Gmail, but there was no response by them or in the Gmail forum.

Can anyone here help me understand these issues or know what further  steps I can take now? I've tried to make this request as concise as I  can.

Thanks for helping me.

Thanks.

Jess Henryes

-----------------------------------------------------------------------------------------
This is the  strange code that I do not understand.

                         Received: by 2002:a50:941a:0:0:0:0:0 with SMTP id p26-v6csp1780943eda
 Mon
 X-Google-Smtp-Source: AB8JxZpnK6WAfgZ3dBvYjyTupy+nhX1jjuZtwJTJLYPlK9ESgsGhS2WBgYTpnpkvll/0QepKqaLz
 X-Received: by 2002:adf:8b02:: with SMTP id n2-v6mr12051679wra.282.1527530460557
 Mon
 28 May 2018 11:01:00 -0700 (PDT)
 ARC-Seal: i=1
 
```

a=rsa-sha256

 t=1527530460

 cv=none
 d=[google.com]("http://google.com")
 s=arc-20160816
 b=IrX5azr8F1xDQNHsj0uQtC8hZJcYnc2uSAlkWCKHLTe0FD3sPQcSG2fLKN8HF8kyqV
 A3/qwqbRUwKc529N+IFxdAHtdC8bzgSOvxbeEHGcnNO1+uXst+QrS9QBAhJx79hqAjdd
 GxiPfdwHVgq20gOQo0GO2yEUjLkLdWOgqyqxMNjnGCI3Sk/k6AP04qk7KD0M8UrE7lck
 D2E+Mmf+9b+bijkR3wpQPBbPULG7MpDBDBa/Er+IbBtbLDLzFmyaEiQMhVs8g8HKfzA0
 tSWw==
 ARC-Message-Signature: i=1
 a=rsa-sha256
 c=relaxed/relaxed
 d=[URL="http://google.com"]google.com
[/URL]
```[URL="http://google.com"]
[/URL]

 ```
 
s=arc-20160816

 h=to:subject:noreen-comet-******:message-id:worthiness-checker:date
 :preview-inhere-scope:mime-version:levelling-kline:from
 :list-unsubscribe:content-transfer-encoding:phelps-acidly-loose
 :arc-authentication-results:

```

```


 bh=92E4rvFAdcSi13z7MwsWsvJ+PdLzQyBkAmvBkCuNYnU=
 b=gWXaeJAm76+mQWsZ+2BJu4l52W/JUZY9JhCouTVgety9rjTQ8wJardUfcfhS4pgKce

 fzjiyTtnj9P7YVF81/zytrbaPsZO3YqV2NKH1CQcLuQAnOwddE1ozF4xF0tKFsIDOIw7
 jACcx4BvNuYAy8JSeRshPFtKk5DduwnLfQ4h7Kh2MA1Fq7TkG7npNXHIq4TYcENNfQWM
 HL1YIVWWFHo0X911H7GOgYs5C3+q2PVtSeUaghTawtqblujQnn0nMHrsrdAlIFdMH2sD

 ce/U7B5y/nrExj77SBzDoQLrPLowPewV5101JVeQ3bIGYyY6shdaV+w9jwB5hDKdbeX/
 iRyw==
 [mx.google.com]("http://mx.google.com")
 spf=neutral ([google.com]("http://google.com"):  88.198.70.168 is neither permitted nor denied by best guess record for  domain of extrac...@lipyumi.com) smtp.mailfrom=extrac...@lipyumi.com
 Return-Path: (extrac...@lipyumi.com)
 Received: from [izone5.brawaa.com]("http://izone5.brawaa.com") ([izone5.brawaa.com]("http://izone5.brawaa.com"). [88.198.70.168])
 by [mx.google.com]("http://mx.google.com") with ESMTP id v14-v6si2836347wmf.143.2018.05.28.11.00.59
 for
 Mon
 28 May 2018 11:01:00 -0700 (PDT)

 Received-SPF: neutral ([google.com]("http://google.com"):  88.198.70.168 is neither permitted nor denied by best guess record for  domain of extrac...@lipyumi.com) client-ip=88.198.70.168
 Authentication-Results: [URL="http://mx.google.com"]mx.google.com
[/URL]
```[URL="http://mx.google.com"]
[/URL]

 ```

spf=neutral ([google.com]("http://google.com"):  88.198.70.168 is neither permitted nor denied by best guess record for  domain of extrac...@lipyumi.com) smtp.mailfrom=extrac...@lipyumi.com

 Phelps-Acidly-Loose: reap
 Content-Transfer-Encoding: 7bit
 List-Unsubscribe: (mailto:phcqkn...@lipyumi.com)
 From: Notification (extrac...@lipyumi.com)
 Levelling-Kline: c97a22191a7
 MIME-Version: 1.0
 Preview-Inhere-Scope: 546
 Date: Mon
 28 May 2018 22:01:00 +0000
 Worthiness-Checker: e3fc43fcf
 X-Mailer: Morbid
 Message-ID: (99e4df7f-ead...@lipyumi.com)
 X-Auto-Response-Suppress: None
 Noreen-Comet-******: 27
 Subject: Security alert for your account
 Content-Type: text/html
 charset=UTF-8
 format=flowed
 delsp=yes
 To: @[URL="http://gmail.com"]gmail.com

[/URL]
```[URL="http://gmail.com"]
[/URL]

 ```

[html lang=en

 meta name=format-detection content=date=no/
 meta name=format-detection content=email=no/
 style
 .awl a {color: #FFFFFF
 text-decoration: none
 }.abml a {color: #000000
 font-family: Roboto-Medium
 Helvetica
 Arial
 sans-serif

 font-weight: bold
 text-decoration: none
 } .afal a {color: #b0b0b0
 text-decoration: none
 } @media screen and (min-width: 600px) {.v2sp {padding: 6px 30px 0px
 }

 .v2rsp {padding: 0px 10px
 } (/style)

 tr align=center
 table border=0 cellspacing=0 cellpadding=0 style=padding-bottom: 20px, max-width: 600px, min-width: 220px,

 tr

 tr signal='4'

 table milestones=37 width=100% border=0 cellspacing=0 cellpadding=0 style=direction: ltr, padding-bottom: 7px,
 /i

 /td

 /tr
 /span
table coarse='3' class=v2rsp width=100% border=0 cellspacing=0 cellpadding=0

 tbody goto=gretchen

 tr nightclub='81'

```

If this is the wrong place to ask about this, please tell me where I should go to ask my question.
Any help is appreciated. Thank you. Jess

---

### Post by oldos2er on 2018-07-15
Moved to Cafe.

---

