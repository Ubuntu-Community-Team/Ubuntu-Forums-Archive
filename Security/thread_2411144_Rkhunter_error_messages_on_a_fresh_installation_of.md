---
title: "Rkhunter error messages on a fresh installation of Linux."
date: 2019-01-25
forum: Security
---

### Post by peter712 on 2019-01-25
Hi,r
I am 71 years old and struggling with Linux as until recently I have been a Windows user.  After a few weeks on Linux I decided to run rkhunter today for the first time and  got several  warnings pointing to the possible existence of 3 rootkits. A cursory Google search led me to the conclusion that my system could be compromised and bearing that  in mind I decided to reinstall the system with the most up-to-date version of Linux, which I suppose to be version 18.04.

The problem is that after having just installed the new  version of Linux rkhunter is  giving me 2 warnings with the indication of 2 possible rootkits in the summary part, when 0 were expected. 

The relevant parts of the log file are shown bellow:

```
Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: Perl script text executable
[21:51:48]   /
 ] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
 [21:52:00]   /bin/fgrep                                      [ OK ]
 [21:52:00] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.

 Checking for suspicious (large) shared memory segments [ Warning ]
 [21:54:14] Warning: The following suspicious (large) shared memory segments have been found:
 [21:54:14]          Process: /usr/bin/nautilus-desktop    PID: 1758    Owner: peter    Size: 64MB (configured size allowed: 1.0MB)
 [21:54:15]          Process: /usr/lib/gnome-initial-setup/gnome-initial-setup    PID: 1755    Owner: peter    Size: 8.0MB (configured size allowed: 1.0MB)
  
System checks summary
[21:54:32] =====================
[21:54:32]
[21:54:32] File properties checks...
[21:54:32] Files checked: 149
[21:54:32] Suspect files: 1
[21:54:32]
[21:54:32] Rootkit checks...
[21:54:32] Rootkits checked : 479
[21:54:32] Possible rootkits: 2
[21:54:32]
[21:54:32] Applications checks...
[21:54:32] All checks skipped
[21:54:32]
[21:54:32] The system checks took: 3 minutes and 24 seconds
[21:54:32]
[21:54:32] Info: End date is Fri 25 Jan  21:54:32 AEDT 2019

```
I believe that I got the Linux Ubuntu distribution from the official site and so far apart from rkhunter I have only installed gufw, So my question is this:  what is going on?  Can  I ignore the warnings, or do I have to arrive to the conclusion that the version of Linux that I got has been compromised? 

.

---

### Post by pending... on 2019-01-25
Since 18.04, rkhunter's started to check shared memory segments, adding some more false positive (I get the same warnings, except it is with Dolphin instead of Nautilus as I'm on Kubuntu).

lwp-request is also another known false positive. I wouldn't worry with such warning. To complete your checks, even though I don't think it is relevant on an up-to-date desktop machine, you can run unhide or unhide.rb.

---

### Post by Irihapeti on 2019-01-25
I think that people run rkhunter in order to boost their security profile, but in the 10 years or more that I've been on these forums, I've never yet seen anyone helped by running rkhunter or chrookit. Instead, I've seen plenty of unnecessary anxiety caused by false positives.

I've come to the conclusion that, while these programs might be helpful for server administrators in some circumstances, most of us are best off ignoring them.

---

### Post by yetimon_64 on 2019-01-25
> **Irihapeti said:**
> I think that people run rkhunter in order to boost their security profile, but in the 10 years or more that I've been on these forums, I've never yet seen anyone helped by running rkhunter or chrookit. Instead, I've seen plenty of unnecessary anxiety caused by false positives.

I've come to the conclusion that, while these programs might be helpful for server administrators in some circumstances, most of us are best off ignoring them.

^^^ A big +1. ^^^

@ OP, [[COLOR=#0000ff]--here--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2385333") (link to a thread in blue text) is a posting I made almost a year ago on the subject that may be of some help to you.
My postings gave that user the instructions to whitelist the usual rkhunter false positives etc. 

From pending...'s post
> Since 18.04, rkhunter's started to check shared memory segments, adding some more false positive ...
I am not yet using 18.04, so basically have never dealt with that output; but as per the linked thread I gave above I would suggest you have no other applications open, like nautilus, while running the rkhunter checks to minimize such output from rkhunter.

**Edit:** just noted your post count and join date. Welcome to the ubuntuforums :-)

---

### Post by peter712 on 2019-01-25
Thank you guys.

I think that there may be some legal implications associated with having or not  having rkhunter installed in a machine. For instance, if you do your  banking online then you may be required to install anti-virus and anti-malware software just in order to CYA. 

I have reinstalled the system one more time using a reformatted UBS drive  and as expected got the same errors.  Curiously, after having installed my scanner and my printer using  a driver from the database that comes with the system and a driver downloaded from the manufacturer the number of possible rootkits doubled to six.

I am going to reconfigure the configuration file in order to eliminate the warning associate with t/usr/bin/lwp-request, but what about 
the "Checking for suspicious (large) shared memory segments"?  That will have to stay I presume as in the future it maybe not be innocuous.  

Base upon  your recommendations I am not going to worry too much about these specific warnings. Thank you very much for your assistance.

Best regards,

Peter

---

### Post by yetimon_64 on 2019-01-25
> **peter712 said:**
> Thank you guys.

I think that there may be some legal implications associated with having or not  having rkhunter installed in a machine. ...

As per Irihapeti's post you really need to know how Linux and in particular how rkhunter works before it could be regarded as a reliable tool.

Here is a link from a [noparse]serverfault.com[/noparse] site that may link to further information regarding the shared memory test and how it works. .[COLOR=#0000ff].[/COLOR][[COLOR=#0000ff].--link--[/COLOR]]("https://serverfault.com/questions/697865/rkhunter-suspicious-shared-memory-segments")
The link relates to a CentOS users question, but the whitelist option ALLOWIPCPROC may possibly also work in rkhunter in Ubuntu (never tried it myself though). 

Knowing what to whitelist will require you to do quite a bit of research to see what others have found with it, good luck. Just sorry I can't be more specific on such a technical question.

When I eventually get onto 18.04, I'll probably turn that particular test off altogether and rely on the rest of the program to find rootkit files etc. It seems to be a test that picks up too many false positives from what I've read and seen online. My opinion only for my usage case, I am not suggesting you do so but for you to do much more research if it continues to concern you.

Regards, yeti.

---

### Post by peter712 on 2019-01-26
Thank you Yitimon_64 for the link

My problem at the moment is that I am struggling with everything even with the vi text editor and its commands. I switched to Linux a few weeks ago after  having waked up one afternoon, I took a little nap on that day, to encounter  my machine unusable   as my windows OS was gone, a situation for which I could not find a solution as my 2 system backups failed to work properly due to damaged disks. What happened I don't know. What I do  know is that I was doing everything according to the books: I had a firewall working properly in its default mode, an anti-virus installed, Microsoft  software designed to look for rootkits, the system configured for automatic software and system updates, etc, etc.   

I used the link provided by you and my understanding is that there is software requiring a shared memory area for inter-process communication and that it is up to me to realize  when that is legitimate and poses  no danger, something that I presume to be beyond the capacity of the ordinary user. 

At the moment I am sure that the warnings can be safely ignored, and on that basis I will try to follow your advice as soon as I have my whole system up and running.

Once more, thank you.

Peter.

---

### Post by yetimon_64 on 2019-01-26
> **peter712 said:**
> ...My problem at the moment is that I am struggling with everything even with the vi text editor and its commands....

After 10+ years on linux, on both Ubuntu and Debian, I still won't use vi or vim text editors ... too hard and confusing for me. If I need to use a terminal based text editor I go with nano, but prefer to use GUI text editors like gedit or mousepad etc; there are many good ones to choose from. 

 > **peter712 said:**
> ...I used the link provided by you and my understanding is that there is software requiring a shared memory area for inter-process communication and that it is up to me to realize when that is legitimate and poses no danger, something that I presume to be beyond the capacity of the ordinary user... 
Yes that sounds about right. As per the "ordinary user" aspect I agree wholeheartedly with Irihapeti's comment ...
> ...while these programs might be helpful for server administrators in some circumstances, most of us are best off ignoring them.I do use rkhunter but found out very early in my time on Linux that it pays to turn off some of the more troublesome aspects of the program's testing, but only after doing a lot of online research. I find once the more troublesome tests are turned off the remaining aspects are worthwhile to keep on with but you do need to follow certain procedures and, more importantly, know why such procedures are needed.

I find the top section of tests, that is the executable file section, will regularly show errors from simply doing a system update/upgrade and will need regular updating the file properties with a specific command "sudo rkhunter --propupd" to clear them. The bottom rootkit files and system checks I find require more checking into if a result is found; but even some of the bottom section still requires you to be aware of system changes you make; sometimes inadvertently by simply installing a new program which alters the system users or groups.

Definitely not an easy program for a new starter to be trying to get a grasp of in my opinion.

**Edit**: just a bit of an afterthought OP, maybe rather than looking for some application to protect you from malware/rootkits etc like you would with Windows, it may be wiser to understand the Linux way/mindset rather than doing things as you normally have. The current programs like rkhunter and chkrootkit could be regarded as misleading and less than helpful for a new user on Linux, they take a lot of experience and/or research to be of any real use.

Here are a few links to get you started on linux securtiy, the first one by bodhi.zazen contains a section which is good read for you titled "Windows mindset"...
1. [[COLOR=#0000ff]Ubuntu Security[/COLOR]]("https://ubuntuforums.org/showthread.php?t=510812") 
2. [[COLOR=#0000ff]Security[/COLOR]]("https://help.ubuntu.com/community/Security") .. this one contains a further link to a user guide for rkhunter.
3. [[COLOR=#0000ff]Antivirus[/COLOR]]("https://help.ubuntu.com/community/Antivirus") ... contains some good info about viruses in Linux a new starter from windows should come to terms with.

Finally remember, "[[COLOR=#0000ff]Linux is not Windows[/COLOR]]("http://linux.oneandoneis2.org/LNW.htm")"... blue text is also a link to a good read for a new starter on linux coming from windows.

A lot of reading, but doing so may make your time on Linux a bit easier in the long run. You really don't have near as much of a worry as you do in windows regarding security if you take the time to learn how Linux works. 

Regards, yeti.

---

### Post by peter712 on 2019-01-27
Thank you Yeti for your sound advice and links to interesting stuff.,

 As it is stated somewhere,  security is not something that you can buy in a box, install and forget about i*t, but rather * *something that* needs *to* be worked upon, and personalized.

Best regards,

Peter

---

