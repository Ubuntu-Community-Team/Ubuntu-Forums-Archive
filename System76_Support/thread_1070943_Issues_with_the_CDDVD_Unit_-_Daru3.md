---
title: "Issues with the CD/DVD Unit - Daru3"
date: 2009-02-15
forum: System76 Support
---

### Post by arepaking on 2009-02-15
Hello,
My Daru3 has problem when trying to read CD's. When a insert a CD it doesn't read the media. First of all I receive a "Unable to mount media" error message and then when I try to eject it a new different error message saying:"Unable to Eject CD-RW/DVD RW Drive".

I attached to this post the two error messages.

```
Unable to mount location
Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

As a side note, I was able to burn a data CD properly but after it finish it cannot open the content. I tried opening the CD in a different computer and it work fine.

Does anyone knows what could be causing this issue? Could it be that something is wrong with the CD/DVD Unit? I bought this Daru3 two weeks ago.

Thanks in advance for your help and support.

Kind Regards,
AK

---

### Post by ctsdownloads on 2009-02-15
> **arepaking said:**
> Hello,
My Daru3 has problem when trying to read CD's. When a insert a CD it doesn't read the media. First of all I receive a "Unable to mount media" error message and then when I try to eject it a new different error message saying:"Unable to Eject CD-RW/DVD RW Drive".

I attached to this post the two error messages.

As a side note, I was able to burn a data CD properly but after it finish it cannot open the content. I tried opening the CD in a different computer and it work fine.

Does anyone knows what could be causing this issue? Could it be that something is wrong with the CD/DVD Unit? I bought this Daru3 two weeks ago.

Thanks in advance for your help and support.

Kind Regards,
AK

Looks like it might be a bug?

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/296021](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/296021)

---

### Post by arepaking on 2009-02-15
Thanks ctsdownloads for your input.

Does anyone with a Daru3 laptop has this problem? These are the steps I did:

a) I used Brasero Disc Burning to write a Data CD
b) CD was successfully burned and at the end of the process was successfully ejected
c) I closed the lid again with the CD inserted to check the written files.
d) CD/DVD Drive couldn't load the CD content and started to show the error messages attached in my first post.

I would really appreciate if a Daru3 user could check this on their system.

Regards,
AK

---

### Post by Guille Damke on 2009-02-16
Can you play any other type of CD, for example, music CDs?

---

### Post by arepaking on 2009-02-16
> **Guille Damke said:**
> Can you play any other type of CD, for example, music CDs?

Hi Guille,
Thanks for your help.

I am able to play music CD's. This is the test that a I did:

a) Insert a music CD
b) System prompt me to open Rythmthbox 
c) Music CD successfully played
d) Pressed Eject button and disc was ejected.
e) Inserted a data CD (a different one)
f) CD wasn't able to load and I got a new error message (never seen before) that is attached to this post below.
g) Eject button stopped working.


I then ran the dmesg command and this is the output:

```
[ 1878.028701] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1878.028713] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1878.028719] sr 1:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 1878.028727] end_request: I/O error, dev sr0, sector 1367872
[ 1878.028735] Buffer I/O error on device sr0, logical block 170984
[ 1884.582945] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1884.582956] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1884.582963] sr 1:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 1884.582970] end_request: I/O error, dev sr0, sector 1367872
[ 1884.582978] Buffer I/O error on device sr0, logical block 170984

```


As a side note, I took the same CD that was burned in my Daru3 (the data CD that cannot be loaded) and tried it in a different computer running windows and it was able to load it. This proof that the Data CD is fine).

---

### Post by Lee_Machine on 2009-02-16
hi,

I dont really have a solution to your problem, but my Pangolin was having the same issues, upon a system update it went away. Then a few days later came back. The only way I could fix it was to reinstall ubuntu.

---

### Post by thomasaaron on 2009-02-16
This one is being handled now via email.

---

### Post by Guille Damke on 2009-02-16
Hi Thomasaaron,

When you solve this issue, is it possible that you post into this thread how you did it? I think the posibility of searching for other user's previous threads is one of the strengths of forums.
Thanks.

---

### Post by thomasaaron on 2009-02-16
Absolutely.

I've seen this one other time, but so far have not been able to duplicate it in-house. I've got a few more tests to run, and then I'll report back -- probably tomorrow afternoon.

If you don't see something from me tomorrow evening, please bump.

---

### Post by arepaking on 2009-02-16
Thanks Thomas,
Let me know if there is anything that I could do to help you knock down this issue (Testing, research.. etc).

I discovered something else, if you leave the Data CD that is not able to load in the tray, and then you reboot your computer then it will freeze when Ubuntu tries to boot.

I had to do a hard reset and take out the CD in order to have Ubuntu back.

---

### Post by thomasaaron on 2009-02-16
OK. Thanks. I'll try that too.

---

### Post by arepaking on 2009-02-18
> **thomasaaron said:**
> OK. Thanks. I'll try that too.

Hi Thomas,
Any updates in regards to this?

Thanks in advance,
AK

---

### Post by thomasaaron on 2009-02-18
Yeah, only that I can't duplicate it at all. And I've only had one other complaint that was similar. I replaced that drive and haven't heard back yet. (Which usually translates into: Problem solved.)

Please fill this out...
[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)
...and I'll get a drive out to you.

---

### Post by arepaking on 2009-02-18
Done.

Thanks Thomas.

---

