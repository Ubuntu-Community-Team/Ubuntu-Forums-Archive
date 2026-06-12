---
title: "Can Ubuntu be compromised by launching file (jpg for example)?"
date: 2019-08-15
forum: Security
---

### Post by setonic on 2019-08-15
If someone will send me a file (for example jpg) and I will launch this file on my Ubuntu desktop  - could be this action a risk for my Ubuntu?

Can you share with me ways of how Linux (Ubuntu) can be compromised with me accidently involved?

---

### Post by #&amp;thj^% on 2019-08-15
> **setonic said:**
> If someone will send me a file (for example jpg) and I will launch this file on my Ubuntu desktop  - could be this action a risk for my Ubuntu?


Possible, but highly unlikely.
> **setonic said:**
> 
Can you share with me ways of how Linux (Ubuntu) can be compromised with me accidently involved?
Keep in mind these are **ONLY**examples, no need for over thinking this.
{Examples only}As a un-knowing user,Via Email.
it is possible for a user to be affected by using Wine.
Wine emulates almost every behavior of the Windows environment, the worm or virus can actually try to find ways on how it can affect you. The worst case scenario is that depending on the direct access wine has to your Ubuntu system, some or all parts of your home will be affected (I Did not fully test this though.)
Wine emulates almost every behavior of the Windows environment, the worm can actually try to find ways on how it can affect you. The worst case scenario is that depending on the direct access wine has to your Ubuntu system, some or all parts of your home will be affected (Did not fully test this.)
**Our company policies:**
[list]
    [*]Use Linux.
    [*]Don't use shares.
    [*]Use a password safe and do not save passwords outside the safe.
    [*]Use online mail.
    [*]Use online storage for documents.
    [*]Only use Windows inside virtualbox for things Linux can not do. We have some VPNs our clients use that are Windows only. You can prepare a vbox and copy it over when you have all the software in it you would need.[/list]
    Windows systems that are used inside our company [B][U](personal notebooks for instance) are not allowed on the company network.
[/U][/B]
Sophos provides on access linux antivirus that is free for non-commerical purposes. While I haven't looked, I would expect it to have been updated for even ransomware. [https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx](https://www.sophos.com/en-us/products/free-tools/sophos-antivirus-for-linux.aspx)

In all reality though, as long as you keep current with updates, you should be safe. (12 year user here and no virus with Linux or BSD spins)
Here is a good read, and I highly recommend this to newer users: [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by TheFu on 2019-08-15
> **setonic said:**
> If someone will send me a file (for example jpg) and I will launch this file on my Ubuntu desktop  - could be this action a risk for my Ubuntu?

Can you share with me ways of how Linux (Ubuntu) can be compromised with me accidently involved?

There are thousands of ways to trick you into compromising your files.    Way too many to list.  

One way ... Be very careful copy/pasting commands from any website.  What you see isn't always what the copy/paste will get.  I tricked one of my beginning Linux classes into doing a copy/paste with some extra  embedded commands.  Half of them didn't notice.  The other half learned to never paste directly into a shell, always paste into an editor first.

Just because a file has .jpg as an extension, that doesn't mean it is a jpg file.  It could easily be a program or a script.
[https://hackaday.com/2015/11/06/stegosploit-owned-by-a-jpg/](https://hackaday.com/2015/11/06/stegosploit-owned-by-a-jpg/)
more explanation: [https://thehackernews.com/2015/06/Stegosploit-malware.html](https://thehackernews.com/2015/06/Stegosploit-malware.html)  But it could be done to other types of files that are often assumed safe, like PDFs.
Follow the *Ubuntu Basic Security Guide* to do what you can. [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Rubi1200 on 2019-08-15
Why do you think someone would send you a file with a malicious payload?

If in doubt, delete anything that comes in whether by email or other means unless you are 100% certain the sender can be trusted.

---

### Post by SeijiSensei on 2019-08-16
If you're using a major email provider, I'd say the chances of someone sending you a message with an infected file are close to zero.  And if such files get through, they're almost certainly likely to be carrying a payload that is designed to attack Windows. There just aren't enough Linux users to attract the interest of the people who distribute malware this way.

If, on the off chance you're running your own mail server, I strongly recommend installing [MailScanner]("http://mailscanner.info/") and using it in conjunction with [ClamAV]("http://www.clamav.net/") and [SpamAssassin]("http://spamassassin.apache.org/").  As it happens, my implementation of MailScanner intercepted this message today:

> 
Warning: This message has had one or more attachments removed (DETAILS.rar, DETAILS.exe). Please read the "Attachment-Warning.txt" attachment(s) for more information.

Dear Sir,

Good day,
Refer to the attached bank slip for payment for invoice INW-SG11 arranged today.

Please confirm safe receipt of our payment.

Thank you.

Best Regards,
Gina I. Zuniega
Accounting Manager
(for and on behalf of owners only)

This is a message from the MailScanner E-Mail Virus Protection Service
----------------------------------------------------------------------
The original e-mail attachment "DETAILS.rar"
is on the list of unacceptable attachments for this site and has been
replaced by this warning message.

At Thu Aug 15 22:55:53 2019 the virus scanner said:
   MailScanner: Executable DOS/Windows programs are dangerous in email (DETAILS.exe)
   No programs allowed (DETAILS.exe)


The message contained a .rar that included a compressed .exe.  Running an .exe on a vanilla Ubuntu machine would have no effect.  Even if you have Wine installed, at worst it would only infect Wine which you can blow away at any time.

More importantly, would you believe a message like this in the first place? Most of the time common sense is the first line of defense.

---

### Post by setonic on 2019-09-01
Thanks to all for valuable replies and opinions.

---

### Post by haplorrhine on 2019-09-02
I found that emails are their own can of worms.  In theory at least, the images embedded in the email can execute some kind of cross-site scripting attack, so Tutanota blocks the images by default.  Bad actors can spoof legitimate email addresses/domains.

---

### Post by sevendogs1337 on 2019-09-07
Which is one reason I hate html email. Email should be text with attachments.  Just my .02.

---

