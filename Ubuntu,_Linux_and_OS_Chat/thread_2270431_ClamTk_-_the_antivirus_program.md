---
title: "ClamTk - the antivirus program"
date: 2015-03-22
forum: Ubuntu, Linux and OS Chat
---

### Post by michael-piziak on 2015-03-22
Interesting, most of the files that ClamTk finds when I run it are in the cache of Firefox or in the cache of Google Chrome.

Since it's no big deal to clear a cache, I guess it won't hurt anything to quarantine these files.

I guess these are suspicious Windows files that one gets while surfing the net.

---

### Post by Tar_Ni on 2015-03-23
I don't see the point of having an antivirus software on Ubuntu since the vast majority of Windows viruses & malware are helpless against a Linux system. The amount of viruses developped specifically to target Linux computers is so small that it's not really not worth to bother, IMO.

---

### Post by bardo2 on 2015-03-23
Hum, would you admit, that scanning for viruses when there are none is a behavior, Windows users adopted and bring into the 'nix world?
a good system (with a vigilant user behind the screen) is quite safe. And just in case you werent: design a procedure for recovery (like rotating backups, making sure, that you are able to restore from it, if need be).
All scanning for viruses can only be useful AFTER having messed up already, AFTER allowing some malware into the system. But who would do that willingly?
Such routine makes sense, and i do scan for viruses, but only inside my windooze virtual machine. And i am being cautious, even overprotective, against LSO's, cookies, browser cache can easily be made temporary. And i dont trust any automatic (!). IMHO it can be considered the biggest breach in computer industry to have software, that needs frequent updates to work properly and that requires full access to all my files/secrets. How can a user allow those scans & internet connections?
If i were a malicious user/company, i would use one update to "open the door" on all the pc's using the software while updating it... and extract whatever i want from there to send the info back on next update. And i do not trust any company to be absulutely safe from "employees mistakes".

---

### Post by QIII on 2015-03-23
That's all well and good until you get an email from a Windows friend, you chuckle at the cute-kitty attachment and unwittingly send it along to another Windows friend complete with its virus payload.  Carelessness can make you a vector even if you are immune.

Don't bank to heavily on Linux being unassailable.  While the mechanism of Windows viruses may be foreign to Linux, that does not mean that something similar isn't being cooked up by some PFY (Pimply-faced youth) in his mother's basement in Des Moines, Iowa.

Windows virus scanners may not help you much, but using them may help your Windows buddies if it keeps you from sending them a time bomb.

Some habits of Windows users are exactly the same as the ones Linux users should practice.  I scan attachments for Windows viruses as a courtesy to those Windows users with whom I may communicate.

I have been preaching against this cavalier attitude of many Linux users for years.  As if the world wanted to give me a perfect "I told you so", we had the "Bash Bug" and "Heartbleed" coming on each other's heels.  There was also the October of Java Linux exploits a year or so ago.  While not "viruses", they point out that Linux is not as secure as many would like to believe.  The "Bash Bug" and "Heartbleed" were back-to-back black eyes to Linux and belied the whole "thousands of eyes on open source code makes it more secure" meme.  Between them, in the opinion of some researchers, they may have caused more financial and identity damage than all the Windows viruses combined up to that point.

"What, me worry?" has no place in the Linux community any longer.  

The "has to be updated often and has the keys to the kingdom" argument is void.  You do that every day when you do your Ubuntu updates.  Who knows what Heartbleed waits around the corner for you?  Do you trust those "thousands of eyes" still?

---

### Post by Tar_Ni on 2015-03-23
> **QIII said:**
> That's all well and good until you get an email from a Windows friend, you chuckle at the cute-kitty attachment and unwittingly send it along to another Windows friend complete with its virus payload.  Carelessness can make you a vector even if you are immune.

I always advise friends and relatives to scan their email's attachments on a Windows machine regardless of who is sending it to them. Whether a person is sending an attachment from Ubuntu or a Chromebook is irrelevant, IMO. That's not for me to scan files for them, they are the ones who should ensure that their computers remain virus-free and so do I on my side.

BTW, the most popular email services like Gmail, Outlook, Yahoo and Yandex all scan attachments for the most common threats out there. That combined with a trusted antivirus program like Avast or Malwarebytes should help them take the right decisions on Windows.

> **QIII said:**
> Don't bank to heavily on Linux being unassailable.  While the mechanism of Windows viruses may be foreign to Linux, that does not mean that something similar isn't being cooked up by some PFY (Pimply-faced youth) in his mother's basement in Des Moines, Iowa.

Of course but let's be honest, a fair assessment for desktop OSes would be that at least 85% of all viruses and malwares roaming the Internet are specifically targeting Windows installations while 14% may be targeting OSX and a remaining tiny 1% is probably intented for Linux. The very small probability that I get infected on Ubuntu doesn't justify the need of an antivirus software and the scanning of my files, personally.

---

### Post by SeijiSensei on 2015-03-23
> **Tar_Ni said:**
> BTW, the most popular email services like Gmail, Outlook, Yahoo and Yandex all scan attachments for the most common threats out there. That combined with a trusted antivirus program like Avast or Malwarebytes should help them take the right decisions on Windows.
Any email provider that does not scan and quarantine mail with viral attachments should not be your email provider.  I run my own servers and scan every message with MailScanner+ClamAV+SpamAssassin.  I would consider it highly unprofessional to deliver infected emails to my customers, and so should you.

---

### Post by craig10x on 2015-03-23
I don't buy the "linux is a small target so they don't bother with it" arguement...fact of the matter is, that most servers run on linux these days (including microsoft's) and there are also many major used devices that run on it also (like android for example) and let's not forget Chrome Os which is also linux... I'm sure the hackers would love to crack into them...but apparently, a lot has to do with the way linux is built, that keeps the all that crap away from us...

---

### Post by pmi2 on 2015-03-23
Not all harmful viruses are trying to install themselves in the OS.   Some can simply steal information like user names and passwords directly from the  browser.  They do not aim to "infect" your system, just drain some cash from one of your accounts.

The original post has a screen shot of quarantined files, with the PUA prefix (Potentially Unwanted Application).  I think most of those are probably trackers.  One however is marked as PUA.Phishing..., I assume that is potentially a piece of nasty code which includes the capability to intercept a login and password to a web site by masquerading as your email provider or bank. (not definitely, but the virus scan thinks it has the looks of one).

---

### Post by mikodo on 2015-03-26
> **pmi2 said:**
> Not all harmful viruses are trying to install themselves in the OS.   Some can simply steal information like user names and passwords directly from the  browser.  They do not aim to "infect" your system, just drain some cash from one of your accounts.
You just scared me, again.

Like most linux people, (well, lots of other system people too), I am pretty darn careful with my one desktop set up with security and internet use. I try to be very diligent. But, I did slip once that I know of. I can't remember what was going around me, that I hadn't used a url paste in FF Browser to go to my bank. Why I didn't I don't really know, I have it and passwords in a encrypted file I have to open anyways so, the correct link is there to copy and enter into FF and it is always good. Instead, I did a search and clicked on what I thought was my bank. The site looked identical to my bank's. BUT, it had a request to click on a link, for verification and I dutifully droned on and hit it. A message said "thank you".

I woke up then, and Alt & F4 out of the site. Scared as ,,,,, I called the bank, told them about what happened, and mentioned just what you said. Changed all the passwords with my second browser (chromium) for the bank. Then started googling Linux and click-jacking. Found a post by HermanAB here, and commands to run to test for it, and did it. Now, of course I trust him. He's well known here, especially in the security forums. Geeze, this is getting long, Contacted Herman, he analysed the results, and told me to not worry. Ran a ClamAV recursive scan, for my whole ~/ with nothing found.

[B]Really, what I wanted to put across, is that mental lapses happen, and it is better to be as prepared as one can be, just in case one has a brain-flatulence, like me. No ill, has come from my stupidity yet, from a year ago.
[/B]
I apologize, for the longggg post.

---

### Post by bardo2 on 2015-03-26
Oh, so this turned into a security discussion of some sorts? ;-)

Well, i am a dinosaur almost unable to change old habits. So what i do is basically: rotating backups and being prepared to restore from those (which involved logging relevant activities to make the latter easier). So to breach my infrastructure, some malware would need to intrude unnoticed for months. - Not impossible, but difficult.

Of course that also involves to act as a different Identity in different places on the net, requiring a local database of accounts and "virtual privacy information". Or does anybody like me even exist? ;-)

And i am aware, that this behavior just makes it more difficult, not impossible to track me, especially not for governmental agencies or the communication providers.

On top of that, i reset my browsers profile directories several times a day, which is different from clearing cookies, LSO's, aso. I just reset everything to known and well thought about values.

And then we die...

---

### Post by mikodo on 2015-03-26
Well, after reading bardo2's post, I need to stop saying this about myself, "*I am pretty darn careful with my one desktop set up with security and internet use. I try to be very diligent*".

;)

---

