---
title: "Is Skype safe to install ?"
date: 2015-09-09
forum: Security
---

### Post by oygle on 2015-09-09
Skype being proprietary software; is it safe to install ? The Kubuntu is sitting behind a NAT firewall and safe in that respect. Although I may have to open a port or two to get Skype running. Any method/s to ensure Skype is not sniffing around the computer for specific information, or doing other unauthorised tasks ?

Possibly the issue here would be to somehow run Skype in a 'closed environment' where it can't have access to any of the data stored ? I want to use it (not my choice, but people with MS wish to use Skype) for video/audio, and have the ability to record the video/audio to a file.

---

### Post by kerry_s on 2015-09-09
just enable the canonical partner repo & you can install skype from there.

---

### Post by oygle on 2015-09-09
Thanks for that. What about the security concerns ?

---

### Post by mystics on 2015-09-09
Microsoft clearly outlines their privacy policies, including stuff in direct relation to Skype: 

[http://www.microsoft.com/en-us/privacystatement/default.aspx](http://www.microsoft.com/en-us/privacystatement/default.aspx)

As far as I can tell, they are not scouring the computer looking for personal data (unless I missed something in my tiredness). There is some data collection that goes on, but it seems entirely isolated to your Microsoft account and their services and won't affect the rest of your computer.

---

### Post by oygle on 2015-09-10
Okay thank you. Anything in the *buntu repositories that functions like Skype on this end, yet can 'talk' to Skype on the other end ?

---

### Post by mystics on 2015-09-10
The closest thing I can think of is the Skype plugin for Pidgin, but from what I have read, it still requires the Skype client to be open to use voice chat.

---

### Post by oygle on 2015-09-14
Thanks for those replies. As I still had a security concern (especially if Skype is associated with MS), I booted into a windows xp drive that has no data on it. I was very quickly reminded why I don't use MS operating systems. In a short while, there were error messages, things being downloaded without my consent, ..arrghh MS.

So, wondering now if I can setup a user that **cannot** view or modify any of the data. Then can I run Skype on Kubuntu as a shell, so that I can still drop out of the shell and do other (privileged) tasks. When I'm in the shell running Skype, it cannot get to any of the data because of the permissions.

Or, can't I have 2 users running at the same time like that ?

---

### Post by CharlesA on 2015-09-14
Why do you want to use Skype if you do not trust it?

There are other VoIP services that aren't run my Microsoft, such as Ventrilo, Mumble, etc.

Why are you running Skype from a shell anyway? It shouldn't be run as root. A normal user shouldn't have any problems getting Skype to launch.

---

### Post by oygle on 2015-09-14
If the person on the other end wants to use Skype, then I'm obliged to use Skype on my end. Shell is not always root.

---

### Post by brian-mccumber on 2015-09-14
I don't think Skype is programmed to search your computer and steal your data. I use it to communicate with clients and friends/family and I have never noticed it doing anything suspicious, it does what it was programmed to do which is let me communicate with other people. I wouldn't be using a user account that has root privileges all the time anyway, but that's your bag. If you are then Skype should be the least of your worries.

---

### Post by oygle on 2015-09-14
> **brian-mccumber said:**
> I wouldn't be using a user account that has root privileges all the time anyway, but that's your bag. If you are then Skype should be the least of your worries.

I'm the only person that uses this computer.   :)

Also, I don't run shell "as root". Somehow this has been assumed ??

---

### Post by brian-mccumber on 2015-09-14
[quote="brian-mccumber"][COLOR=#000000]*that's your bag*[/COLOR][/quote]

:) Well if you weren't running as root all the time you wouldn't be so worried about installing a program.

---

### Post by oygle on 2015-09-15
[bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054"), would the use of Skype in a controlled environment, indicate that [AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906") would be a suitable solution ?

---

### Post by CharlesA on 2015-09-15
> **oygle said:**
> I'm the only person that uses this computer.   :)

Also, I don't run shell "as root". Somehow this has been assumed ??

You did mentioned privileged applications. :)

> **oygle said:**
> [bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054"), would the use of Skype in a controlled environment, indicate that [AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906") would be a suitable solution ?

That would probably work fine. AppArmor can be a bit of a pain to configure, but once you get it set up, it should be fine.

---

### Post by cogset on 2015-09-15
I used Skype for a while, then, in the post-microsoft phase, it misbehaved on me a few times: all of a sudden it started do swap a massive (and I mean massive) amount of data to disk while idling, I wasn't even talking to anyone or downloading anything.
 It *really* trashed the disk in a way that I haven't seen any application doing, let's just say that I wasn't a fan even before that happening -so I cured the issue in the most natural way, getting rid of it. 
It may have been just coincidence, however I'm not a strong believer in coincidences in such cases.  

Since you actually need Skype to talk with other people who are using it, maybe another solution could be to run it in a virtualbox, it wouldn't be as isolated as one would hope, but it would add another layer as opposed to running it directly in your OS. 
That's of course just my 2 cents, I would leave to the experts to clarify if that may possibly be as secure or even  more secure than using it in your OS confined by a well-tailored apparmor profile, or actually do nothing good.

---

### Post by oygle on 2015-09-15
Thanks "cogset" for sharing your experiences with Skype. Seems the only way I'd feel okay about Skype on Kubuntu is to set it up with an AppArmor layer.

---

### Post by HermanAB on 2015-09-17
Skype does what it is designed to do.  It forwards voice, video and text via MS servers between you, your family and friends, which then allows the NSA to snoop if they want to, but the snooping doesn't affect the performance of the program and it doesn't seem to enable other security issues.  So it is par for the course for any MS software I suppose.

---

### Post by markodd on 2015-10-12
I too share the same concerns as OP. I've to use skype but I'm not fond on using closed-source software, specially from the big companies that actively provide the US government with backdoors.

One good software that I've recently come across is Firejail: [https://l3net.wordpress.com/projects/firejail/](https://l3net.wordpress.com/projects/firejail/)

Sadly, it does not yet support skype out-of-the-box so one would need to create config files for it. That's way out of my league though, so if manage to do it.. Let me know!

---

