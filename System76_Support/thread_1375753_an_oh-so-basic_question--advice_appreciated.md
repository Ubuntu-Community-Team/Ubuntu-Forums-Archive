---
title: "an oh-so-basic question--advice appreciated"
date: 2010-01-08
forum: System76 Support
---

### Post by eljayski on 2010-01-08
do people get anti-virus software for their linux machines?

laughter subsides . . .

i know that one of the huge advantages of linux vs. the other guys is the linux is more stable and not prone to malicious attack.

still, i've not seen this specific issue addressed.  many thanks for insights.  eljayski

---

### Post by MelDJ on 2010-01-08
personally i use avast. you can get the .deb from:
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

---

### Post by HotShotDJ on 2010-01-08
I haven't run AV's on my Linux systems in the 9 years that I've been using it as my primary OS.

Let me rephrase --- I HAVE run clamAV on my Linux systems -- but only to scan Windows partitions.

---

### Post by howefield on 2010-01-08
> **eljayski said:**
> i've not seen this specific issue addressed.

See it addressed here.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by HotShotDJ on 2010-01-08
> **MelDJ said:**
> personally i use avast.If one is going to insist on running AV on and for their Linux box, there is no need to resort to a closed source/proprietary product.  Just "apt-get install clamav" if you absolutely cannot break the habits you learned using Windows.

---

### Post by thomasaaron on 2010-01-08
I've never had any use for an av program. I see a lot of folks running it on email servers (to keep from spreading Windows viruses that pass through the server), but, at least for now, I don't see much of a need for it on most desktop systems.

I've been running Linux for many years -- even using it to log into my wife's webmail and examine files sent to her to see if they have a virus -- and I've never needed an av program.

---

### Post by jml on 2010-01-08
I agree with Tom.  I have never run an AV program on any of my Linux boxes, (or my Macs for that matter.)  Since I rarely send files or forward e-mails to other people, I don't have any real use for it.  I only use AV on my one token Windows box that I own.

Joe

---

### Post by revlimiter on 2010-01-09
In my short 2 years with Linux, I've also never run an AV program. In fact, I didn't know Avast even HAD a .deb of their product.

---

### Post by MelDJ on 2010-01-09
> **HotShotDJ said:**
> If one is going to insist on running AV on and for their Linux box, there is no need to resort to a closed source/proprietary product.  Just "apt-get install clamav" if you absolutely cannot break the habits you learned using Windows.

i used to use avast on windows, so i use it because i am more familiar with it than clamav

---

### Post by jdb on 2010-01-09
> **eljayski said:**
> do people get anti-virus software for their linux machines?

laughter subsides . . .

i know that one of the huge advantages of linux vs. the other guys is the linux is more stable and not prone to malicious attack.

still, i've not seen this specific issue addressed.  many thanks for insights.  eljayski

I've been using Linux for 12 years & have never used any AV software.
No problems yet :)

jdb

---

### Post by betrunkenaffe on 2010-01-09
I have used the best anti virus for both Windows and Linux. Brains.

---

### Post by Flyers2391 on 2010-01-09
> **thomasaaron said:**
> ... (to keep from spreading Windows viruses that pass through the server) ...

This is the only reason I have ClamAV running on my laptop at work, just makes my boss OK with me Ubuntu on it since jut about everyone else is on Windows

---

### Post by 3Miro on 2010-01-11
If a problem with Linux is found, they fix it. When a problem with windows is found, they make you buy an AV program that will watch and see if something is trying it use the vulnerability. There are no viruses under the windows definition and thus Linux does not need AV for itself.

To my knowledge, there is no AV program for Linux viruses, the ones that are listed as Linux AV programs only go after windows viruses. There is a mention for windows viruses running under wine, but my guess is that this would be very rare. In any case I have been running wine for couple of years w/o problems. I don't go on-line with wine anyway, I only play games off-line.

I run 3 computer purely Linux environment at home, so I don't bother with AV software. Let the windows machines fend for themselves. However, if you are connected with windows machines, you might consider AV to help not infect them.

---

### Post by jpv on 2010-01-11
I agree with 3Miro.  My usual .sig says:

"Microsoft Tax" = the additional hardware & yearly fees for the add-on software required to protect Windows from its own poorly designed and implemented self, while the overhead incidentally flattens Moore's Law.


But I'm not bitter...  :-)

My advice is:

1) Keep good offline/offsite backups (note RAID is *not* a backup!).  Check out UbuntuOne or something.  But make sure you can recover!  "No one cares about backups, they only care if you can recover data..."  See the excellent _Backup & Recovery_ book by Preston, from O'Reilly, from which I just stole & mangled that quote.

2) Don't run as root.  You have to go way out of your way to do that on Ubuntu anyway, but don't.  That way, even if you have a problem, you can only mess up yourself (e.g., ~/.wine perhaps?).  Then, see #1.

3) A/V is almost worthless, even on Windows.  It might prevent some really clueless users from running *some* pretty old malware, but...  Sure, you have to run it on Windows just so you can say you do, but how many people ever actually see it pop up and catch anything anymore?  I haven't seen a real Windows virus alert for at least 10 years, and when I've tested various Windows products the results...aren't good.  Google around for the "eicar" test and try it yourself (if you are authorized to do so; i.e., NOT at work).

---

### Post by Teasdale on 2010-01-11
> **jpv said:**
> how many people ever actually see it pop up and catch anything anymore?  I haven't seen a real Windows virus alert for at least 10 years, 

During the 8 years or so that I used Windows, it happened *once*. And what it removed to fix the "virus" was my web-building program.

---

### Post by samalex on 2010-01-12
Just to put my two cents in... if you run LOTS of applications through Wine (especially IE) then I would suggest running a virus scanner because a Windows virus can be just as dangerous under Wine as it is in Windows.  And if your virtual Windows environment has access to write to your Linux file system it can be just as destructive.

You can lock down Wine so nothing is shared between your virtual Windows C: Drive and Linux, but it can be restrictive if you need to share information between Wine and Linux.

But do as I say and not as I do because even though I run several applications in Wine, I've never installed any AV software under Linux, and that's using both Linux and Wine since around 1996.

Take care,

Sam

---

