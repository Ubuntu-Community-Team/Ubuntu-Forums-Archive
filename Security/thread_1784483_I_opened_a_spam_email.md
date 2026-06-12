---
title: "I opened a spam email"
date: 2011-06-17
forum: Security
---

### Post by Libertydude on 2011-06-17
So, I was tricked into opening a spam email today (it looked legit), and I was wondering, are Ubuntu users immune to email viruses?

And I had the HTML set to automatically run.

---

### Post by amauk on 2011-06-17
You're safe

---

### Post by User3k on 2011-06-17
If you feel the need to check anyways check out Clamav (clamtk,) rkhunter and chkrootkit. But I agree with amauk, you should be safe.

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> You're safe
I once opened an email in Microcrap Windoze and the email itself gave me a virus (didn't download anything or follow any links).

Could it have run a script and infected firefox?

Sorry for all my questions lately folks, I am just trying to get to learn Ubuntu. :)

---

### Post by Libertydude on 2011-06-17
> **User3k said:**
> If you feel the need to check anyways check out Clamav (clamtk,) rkhunter and chkrootkit. But I agree with amauk, you should be safe.
I use clamtk already, which directory should I scan?

And what is rkhunter and chkrootkit?

---

### Post by amauk on 2011-06-17
> **Libertydude said:**
> And what is rkhunter and chkrootkit?They're rootkit finders
but beware, as they give lots of false positives

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> I once opened an email in Microcrap Windoze and the email itself gave me a virus (didn't download anything or follow any links).

Could it have run a script and infected firefox?

Sorry for all my questions lately folks, I am just trying to get to learn Ubuntu. :)

If you re worried about things like that in Ubuntu then I suggest you check out these links and slowly get use to these programs. Take it one at a time so it doesn't overwhelm you, it can be rough being new as it is.

All of these can be installed through Ubuntu's software center.

[http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)

[http://www.chkrootkit.org/](http://www.chkrootkit.org/)

[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)  and   [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)


Edit:>  amauk wrote: They're rootkit finders
but beware, as they give lots of false positives

True. chkrootkit and rkhunter (especially rkhunter,) They can give some false positives, so if you have any questions search for it with Google or this forum to find out if it is a false positive or start a thread and ask here at the forums.

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> They're rootkit finders
but beware, as they give lots of false positives
But has anyone ever heard of getting a virus by opening a spam email in firefox?

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> But has anyone ever heard of getting a virus by opening a spam email in firefox?

Anything is possible. However if you are using Ubuntu (or Linux) then you are probably safe. Get Clamav and clamtk set up and scan your home folder if you are that concerned.

Malicious code can be in html, pictures, java, flash and the list goes on. But like I said, you are probably safe. If you where running windows then that would be a bigger concern in my opinion.

---

### Post by Libertydude on 2011-06-17
> **User3k said:**
> Anything is possible. However if you are using Ubuntu (or Linux) then you are probably safe. Get Clamav and clamtk set up and scan your home folder if you are that concerned.

Malicious code can be in html, pictures, java, flash and the list goes on. But like I said, you are probably safe. If you where running windows then that would be a bigger concern in my opinion.
I am currently scanning my laptop with clamtk, if it finds nothing am I 99.99999% safe?

I hate viruses...

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> I am currently scanning my laptop with clamtk, if it finds nothing am I 99.99999% safe?

I hate viruses...

I trust Clamav very much. If it doesn't find anything then I wouldn't worry at all about it.

Did you check out the different settings for Clamtk? I usually check advanced>preferences and the first tab I have everything checked. It takes a lot longer but it is the left over paranoia from an Ex MS Windows user, so I have to do it, lol.

---

### Post by Libertydude on 2011-06-17
> **User3k said:**
> I trust Clamav very much. If it doesn't find anything then I wouldn't worry at all about it.

Did you check out the different settings for Clamtk? I usually check advanced>preferences and the first tab I have everything checked. It takes a lot longer but it is the left over paranoia from an Ex MS Windows user, so I have to do it, lol.
I will check out the settings. I can totally relate to the paranoia part, one time I was simply doing a google image search and I got infected by a rootkit, and then it stole my facebook password and the hacker posted stuff on my facebook wall. It was so embarrassing.

---

### Post by Libertydude on 2011-06-17
Also, which directory should I have clamtk scan?

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> Also, which directory should I have clamtk scan?

Just have it scan your /home or /home/<User_name> directory. Basically click the home button on Clamtk.

---

### Post by Libertydude on 2011-06-17
And also ya'll don't think I am infected, right?

---

### Post by amauk on 2011-06-17
> **Libertydude said:**
> Also, which directory should I have clamtk scan?If you want to scan your entire system, then scan /

But I really don't see the point of scanning for windows viruses on a non-windows system
Virus scanners in Linux are typically used on mail gateways and other servers that serve windows machines
This way, viruses are nabbed by the server before they get to the windows client

If you're machine is just an ordinary desktop, then there's no point in scanning for windows viruses, as you're not running windows

---

### Post by User3k on 2011-06-17
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> And also ya'll don't think I am infected, right?

It is possible but doubtful. But it doesn't hurt to run scans.

---

### Post by Libertydude on 2011-06-17
But what is my chances of getting Linux malware? Or getting a cross-platform firefox virus?

---

### Post by amauk on 2011-06-17
> **Libertydude said:**
> But what is my chances of getting Linux malware? Or getting a cross-platform firefox virus?so close to nil, you might as well call it nil

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> But what is my chances of getting Linux malware? Or getting a cross-platform firefox virus?

I posted this link above. Check it out. That should answer your questions.

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> so close to nil, you might as well call it nil
Sounds good to me! :)

But can opening up a spam email compromise my yahoo email password?

---

### Post by Libertydude on 2011-06-17
> **User3k said:**
> I posted this link above. Check it out. That should answer your questions.

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
So is Bad Bunny the only cross platform virus?

---

### Post by amauk on 2011-06-17
> **Libertydude said:**
> But can opening up a spam email compromise my yahoo email password?no

The only 2 realistic ways for someone to compromise your email account are:
- You tell them your password (you fall for a phishing scam, email comes in pretending to be from yahoo, pointing you to a fake site that requests your login details)
- Your password is insecure, and someone simply guessed / brute forced it

Neither of these are anything to do with the operating system you are running

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> no

The only 2 realistic ways for someone to compromise your email account are:
- You tell them your password (you fall for a phishing scam, email comes in pretending to be from yahoo, pointing you to a fake site that requests your login details)
- Your password is insecure, and someone simply guessed / brute forced it

Neither of these are anything to do with the operating system you are running
Can't a password be compromised by a virus? Or is that windows only?

---

### Post by amauk on 2011-06-17
> **Libertydude said:**
> Can't a password be compromised by a virus? Or is that windows only?Criminently...

A virus (if your system got one, which is next to impossible - you'd really have to put a lot of effort into it to contract one) could capture keystrokes from the keyboard (if you explicitly gave it permission to do so - root required to intercept keyboard events), and compromise your email password

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> Criminently...

A virus (if your system got one, which is next to impossible - you'd really have to put a lot of effort into it to contract one) could capture keystrokes from the keyboard (if you explicitly gave it permission to do so - root required to intercept keyboard events), and compromise your email password
What about a firefox only virus?

---

### Post by amauk on 2011-06-17
> **Libertydude said:**
> What about a firefox only virus?no

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> no
What about a flash virus?

---

### Post by amauk on 2011-06-17
[http://answers.yahoo.com/question/index%3b_ylc=X3oDMTVmM3BxcmZyBElfYWd1aWQDNEFNV1FUS0ZHS1dFUkJONFhRQ0ZRT0ZWTk0ESV9jZ3VpZAMESV9jcHJvcAN5YWhvby5zb2NpYWxibG9nLnljYS5jbGllbnQESV91Y250eAMESV91c3JjA3kudXMuYW5zd2VycwRJX3VzdWlkAzIwMTEwNjE2MjMzMDQ5QUFHMzBwSV96bTF6VVdIQ2FhBElfdXR5cGUDYXNrBF9TAzIwMjM0MzUyNjE-?qid=20110616233049AAG30pI](http://answers.yahoo.com/question/index%3b_ylc=X3oDMTVmM3BxcmZyBElfYWd1aWQDNEFNV1FUS0ZHS1dFUkJONFhRQ0ZRT0ZWTk0ESV9jZ3VpZAMESV9jcHJvcAN5YWhvby5zb2NpYWxibG9nLnljYS5jbGllbnQESV91Y250eAMESV91c3JjA3kudXMuYW5zd2VycwRJX3VzdWlkAzIwMTEwNjE2MjMzMDQ5QUFHMzBwSV96bTF6VVdIQ2FhBElfdXR5cGUDYXNrBF9TAzIwMjM0MzUyNjE-?qid=20110616233049AAG30pI)

[http://forum.cfbangor.com/f10/if-i-download-ubuntu-virus-infected-windows-computer-679/](http://forum.cfbangor.com/f10/if-i-download-ubuntu-virus-infected-windows-computer-679/)

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> [http://answers.yahoo.com/question/index%3b_ylc=X3oDMTVmM3BxcmZyBElfYWd1aWQDNEFNV1FUS0ZHS1dFUkJONFhRQ0ZRT0ZWTk0ESV9jZ3VpZAMESV9jcHJvcAN5YWhvby5zb2NpYWxibG9nLnljYS5jbGllbnQESV91Y250eAMESV91c3JjA3kudXMuYW5zd2VycwRJX3VzdWlkAzIwMTEwNjE2MjMzMDQ5QUFHMzBwSV96bTF6VVdIQ2FhBElfdXR5cGUDYXNrBF9TAzIwMjM0MzUyNjE-?qid=20110616233049AAG30pI](http://answers.yahoo.com/question/index%3b_ylc=X3oDMTVmM3BxcmZyBElfYWd1aWQDNEFNV1FUS0ZHS1dFUkJONFhRQ0ZRT0ZWTk0ESV9jZ3VpZAMESV9jcHJvcAN5YWhvby5zb2NpYWxibG9nLnljYS5jbGllbnQESV91Y250eAMESV91c3JjA3kudXMuYW5zd2VycwRJX3VzdWlkAzIwMTEwNjE2MjMzMDQ5QUFHMzBwSV96bTF6VVdIQ2FhBElfdXR5cGUDYXNrBF9TAzIwMjM0MzUyNjE-?qid=20110616233049AAG30pI)

[http://forum.cfbangor.com/f10/if-i-download-ubuntu-virus-infected-windows-computer-679/](http://forum.cfbangor.com/f10/if-i-download-ubuntu-virus-infected-windows-computer-679/)
How come you posted a link to the yahoo answers question?

---

### Post by amauk on 2011-06-17
To subtly inform you that it's a good idea to change your username when trolling multiple forums

saves embarrassment

---

### Post by Libertydude on 2011-06-17
> **amauk said:**
> To subtly inform you that it's a good idea to change your username when trolling multiple forums

saves embarrassment
I am not trolling. I did ask that question on yahoo. But for the life of me I can't remember posting on that other site. I did ask the exact same question here tho, that was in march, when I was infected with a rootkit. And it was a legit question

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> I am not trolling. I did ask that question on yahoo. But for the life of me I can't remember posting on that other site. I did ask the exact same question here tho, that was in march, when I was infected with a rootkit. And it was a legit question

Don't worry. Linux is much safer then Windows with everything. Just run Clam when you need to or want to and use rkhunter and chkrootkit, just keep in mind that, while the last two are useful, you may get some false positives.

---

### Post by amauk on 2011-06-17
All of your posts on this forum (all 51 of them) have been about viruses / malware

Anyway,
I hope your questions have been answered sufficiently
(on numerous sites, over numerous months)

---

### Post by Libertydude on 2011-06-17
> **User3k said:**
> Don't worry. Linux is much safer then Windows with everything. Just run Clam when you need to and use rkhunter and chkrootkit, just keep in mind that while the last two are useful that you may get some false positives.
Thanks. :)

But I will be honest, I suffer from an extreme case of OCD and I think my paranoia about viruses is because of my OCD. Especially after that rootkit infection.

---

### Post by User3k on 2011-06-17
> **Libertydude said:**
> Thanks. :)

But I will be honest, I suffer from an extreme case of OCD and I think my paranoia about viruses is because of my OCD. Especially after that rootkit infection.

No worries. Linux is much safer. That is one of the reasons why I use it and not MS Windows.

If you find anything then ask here at this forum. Otherwise sit back and enjoy Ubuntu :-)

---

### Post by Libertydude on 2011-06-17
> **User3k said:**
> No worries. Linux is much safer. That is one of the reasons why I use it and not MS Windows.

If you find anything then ask here at this forum. Otherwise sit back and enjoy Ubuntu :-)
Thanks, I feel much better now. :)

---

### Post by ehode on 2011-06-22
> **Libertydude said:**
> Thanks. :)

But I will be honest, I suffer from an extreme case of OCD and I think my paranoia about viruses is because of my OCD. Especially after that rootkit infection.

I've watched the ubuntu security forums for a while and see plenty of these type of posts and have yet to see anyone infected.

As a OCD sufferer myself, don't feed the beast by checking and rechecking (and then checking again! :)).

---

### Post by Thewhistlingwind on 2011-06-23
How about this. If you get compromised, your system rooted, documents trashed, [/usr destroyed]("https://github.com/MrMEEE/bumblebee/commit/a047be85247755cdbe0acce6#diff-1"), send me the binary, and it exploits a REAL vulnerability, I will buy you a steak dinner.;)  *

[I]
[SIZE=1]* Except not really[/SIZE]
[/I]

---

