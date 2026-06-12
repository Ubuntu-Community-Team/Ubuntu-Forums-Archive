---
title: "Virus Alert &quot;Surprise.exe&quot;"
date: 2010-01-26
forum: Security
---

### Post by Keith Fox on 2010-01-26
Recently my email address has sent this file "Surprise.exe" to all my contacts.  I'm running Ubuntu 9.10 and haven't quite figured out how it did it, or where it got in.  I did not personally send this message but everybody in my contacts received it.  My Evolution window was running (open) but there is no similar sent message in my Sent outbox, so it must have came from the server somehow.  I checked Hotmail on the server, and it was in that Outbox folder, so I've narrowed it down to the Hotmail server. I have not  given my password to anybody, nobody else was in my home.  I'm wondering if there is some kind of either Hotmail leak in security or if it's Ubuntu that has a security link. The only thing I have done different to my machine recently is install a virtual machine (VirtualBox) that has XP and Windows 7, but those virtual machines don't even have network access, I just use those for testing purposes only.  This happened today 01/26/2010. 
Since this, have _changed_ my hotmail password. I will make a _switch to Gmail permanently_ for this **Hotmail Server security breech**. After doing some research this seems to be one of the most highly infected viruses to date. I feel sorry for all my windows users in my contact list. 99% of my contacts use Windows and was sent to at least 150-200 people.

Do _**not**_ use/click the link:
htt://ww.rapidshare.com/files/*341348122a$/Surprise.exe 
*(i've changed some characters to make it not the same)*


Anybody with more information feel free to post in this thread.
I would like to post a bug to virus security if anybody could provide links I would appreciate knowing where to send this information.

---

### Post by cariboo on 2010-01-27
If you have had the same email address for a while, someone is spoofing your email address. I had this happen with an email address that I had for several years, I was getting messages about spam I had supposedly sent, even though the didn't originate from my system or my isp's email system.

---

### Post by keith little on 2010-01-27
This virus has targeted me as well... it has sent out a mass email from me twice, about 6 hours apart.
I have had a hotmail account with the same password for many years and it looks like it is only targeting my hotmail contacts. Wondering if changing your password really helps?
I cannot seem to find a program to catch it yet, avg, microsoft security essentials, spybot, windows defender are all missing it!!!
Is the virus to new? or just contained to my hotmail account?
 
My name is keith as well... curious if it is targeting keith's?
 
anybody who has found a solution to this one, please let me in on the secret!

---

### Post by cdenley on 2010-01-27
If a copy of the message appears in your hotmail sent box, but not your evolution sent box, then it must have been sent from hotmail. This means they gained access to your hotmail account somehow, whether it is a hotmail hack or someone figured out your password, or someone is hijacking your account with a cross-site scripting attack. Have you been using hotmail in your browser? Does the account have a strong password? Could you have been tricked by an e-mail into providing your password to a site disguised as a hotmail one?

---

### Post by S2UIRR3L on 2010-01-27
I'm guessing that you might have a virus that records addresses and passwords and then goes into your account when your computer is idle? Do you have the option to remember passwords active in your browser?

Just for the sake of this conversation, do I really need an anti-virus with Linux Ubuntu? I've been going un-protected since 2 years and have never caught anything. But then again, I never open email from people I don't know.

-Squirrel

---

### Post by Ceiber Boy on 2010-01-27
> **S2UIRR3L said:**
> I'm guessing that you might have a virus that records addresses and passwords and then goes into your account when your computer is idle? Do you have the option to remember passwords active in your browser?

Just for the sake of this conversation, do I really need an anti-virus with Linux Ubuntu? I've been going un-protected since 2 years and have never caught anything. But then again, I never open email from people I don't know.

-Squirrel

i've been using Ubuntu for 2 years also and never had any security issue, however like youeself i am also extremely cautious. i came to linux from windows and did a huge amount of research on whether or not one should run an anti-virus on Linux, the short answer is NO. however having and running one dose have advantages, perhaps the first thing is Linux anti-virus programs scan for WINDOWS viruses so the advantages are if a virus is on your machine somehow you can remove it, second you can protect your friends who use windows.

---

### Post by cgb on 2010-01-27
Doesn't sound like you really are infected on your local PC as such.  Most likely just hacked your hotmail password and retrieved you contact list that way.

---

### Post by Keith Fox on 2010-01-27
> **cgb said:**
> Doesn't sound like you really are infected on your local PC as such.  Most likely just hacked your hotmail password and retrieved you contact list that way.

I agree with you on this.

---

### Post by Keith Fox on 2010-01-27
> **cdenley said:**
> If a copy of the message appears in your hotmail sent box, but not your evolution sent box, then it must have been sent from hotmail. This means they gained access to your hotmail account somehow, whether it is a hotmail hack or someone figured out your password, or someone is hijacking your account with a cross-site scripting attack. Have you been using hotmail in your browser? Does the account have a strong password? Could you have been tricked by an e-mail into providing your password to a site disguised as a hotmail one?
I never use browser to read or compose emails. Only thing I can think of is either Hotmail server was hacked, or "LastPass" plugin for firefox was hacked. probably not LastPass, because none of my other accounts were messed with on any other site.

---

### Post by keith little on 2010-01-27
HaHa!!!
Got ya...
I finally found a program that could find it [http://www.malwarebytes.org/](http://www.malwarebytes.org/) the free version caught it so bonus!
I am not really a computer guy, but from what I can tell (my experience) it is a trojan that had two entries in my registry keys.
 
I wish everyone luck!!!

---

### Post by keith little on 2010-01-27
Here is the log I recieved in case anyone knows what to do with it.
 
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Ext\Stats\{549b5ca7-4a86-11d7-a4df-000874180bb3} (Trojan.Agent) -> Quarantined and deleted successfully.
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Browser Helper Objects\{549b5ca7-4a86-11d7-a4df-000874180bb3} (Trojan.Agent) -> Quarantined and deleted successfully.

---

### Post by witeshark17 on 2010-01-27
Edited registry keys... Imagine that! :popcorn:

---

### Post by CharlesA on 2010-01-27
> **witeshark17 said:**
> Edited registry keys... Imagine that! :popcorn:

Was that really necessary?

I'm still curious how the OP got something on the VM, since they stated that they have no network accesses.

---

### Post by Keith Fox on 2010-01-27
> **CharlesA said:**
> Was that really necessary?

I'm still curious how the OP got something on the VM, since they stated that they have no network accesses.

LoL... I'm not sure if it's from the virtual machine, i'm leaning more towards a spoofing technique used to by a bot to mask their sent emails to look like it came from me, but it had to have used my hotmail server because it's in the Sent box on the server, but not my Empathy email client which is what I personally use to write and read emails. So definitely Hotmail server was hacked somehow, because nobody knows my password other than "LastPass" plugin for firefox... unless that plugin was hacked but I don't know how that would happen personally. I'm still leaning towards hotmail server got hacked, but as I have seen in my research somebody had this happen to their Yahoo account on the server side.

---

### Post by Barrybarry on 2010-01-28
[COLOR=black][FONT=Verdana]Hi, finally some information on this thing.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have had the email sent out from my hotmail account too. The windows live help center was no use they merged a heap of posts about similar problems then answered the post with change your password! then locked the thread![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Unfortunately one of my relatives clicked on the link. His computer froze up for 15 mins then he restarted. After the restart his computer couldn&#8217;t find his HDD. Does any one know how he can fix this? It won&#8217;t boot up in safe mode or anything![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I think he&#8217;s going to look at the HDD when it&#8217;s plugged into another PC that is a working to see if he can find a problem. If any one has any ides of how to save his computer it would be greatly appreciated[/FONT][/COLOR]
 
Thanks
 
* EDIT i just realised that this isnt for windows. But would still like as much information as Possible!

---

### Post by S2UIRR3L on 2010-01-30
I hope it's not the infamous blue screen of death? I've heard of it and I'm lucky to have never seen it in person. It's one of the main reasons that I've switched over to Linux. So I'll never get to see it... EVER!!!

---

### Post by Rob@ThePCWiz.info on 2010-01-31
haha, i think i might have found one of these friends of yours.
[http://tehparadox.com/forum/f28/surprise-exe-virus-305033/](http://tehparadox.com/forum/f28/surprise-exe-virus-305033/)

**Recent Finds:**
[http://answers.yahoo.com/question/index?qid=20090402165937AAA6Dyf](http://answers.yahoo.com/question/index?qid=20090402165937AAA6Dyf)
[http://forums.techguy.org/general-security/815794-solved-surprise-exe.html](http://forums.techguy.org/general-security/815794-solved-surprise-exe.html)


The following link may be a bit helpful:

[http://tools.cisco.com/security/center/viewAlert.x?alertId=17965](http://tools.cisco.com/security/center/viewAlert.x?alertId=17965)

This page Reads:
> Cisco Security Intelligence Operations has detected significant activity related to spam e-mail messages that appear to come from a personal user e-mail account.  The subject of the e-mail is just a number and the message body contains only a link.  The link directs the recipient's browser to download the file surprise.exe.  When executed, this file attempts to infect the user's system with malicious code. 

E-mail messages that are related to this threat (RuleID2283) may contain a link to the file surprise.exe. 

The surprise.exe file has a file size of 24,064 bytes. The MD5 checksum, which is a unique identifier of this executable file, is the following string: 0xBE712C4A1BB14317C19C5DBED3438A79

The following text provides samples of the e-mail messages that are associated with this threat outbreak: 

Subject Line: 0,9604228

Message Body:  hxxp://good1soft.com? 0.8283419

The  malicious code associated with this threat outbreak shares the characteristics of a downloader trojan.  The trojan attempts to establish connections to the 195.88.80.15 and loyaldown99.com domains.  The trojan then requests a page that directs the user's browser to download the files file.exe and 161.exe, which contain additional malicious code.  The new code creates the files qmgr0.dat, qmgr1.dat, asd.bat, and ieocx.dll.  Additionally, the trojan terminates the Security Center service.  The trojan also uses the Background Intelligent Transfer Service to create a task that issues a GET request to the tube-loyal.com domain for the file videosz.php. 

Cisco Security Intelligence Operations analysts examine real-world e-mail traffic data that is collected from over 100,000 contributing organizations worldwide. This data helps provide a range of information about and analysis of global e-mail security threats and trends. Cisco will continue to monitor this threat and automatically adapt IronPort systems to protect customers. This report will be updated if there are significant changes or if the risk to end users increases. 

Cisco IronPort Virus Outbreak Filters protect customers during the critical period between the first exploit of a virus outbreak and the release of vendor antivirus signatures. E-mail that is managed by Cisco and end users who are protected by Cisco IronPort web security appliances will not be impacted by these attacks. Cisco IronPort appliances are automatically updated to prevent both spam e-mail and hostile web URLs from being passed to the end user.

---

### Post by OpSecShellshock on 2010-01-31
I could see this happening if you accessed your webmail from a PC other than your home computer (like a Windows box at work or some public computer) that was infected with a password-stealer or key logger or something. There have also been some Hotmail breaches reported recently, but most of what I've read about those has focused on password frequency statistics (essentially showing how many people use the exact same, rather obvious and lazy passwords). From what you've said here, your password sounds unique enough that it wouldn't have been of interest to the researchers who obtained the list of stolen passwords.

I don't have one of these accounts personally, but it might be worth checking to see if their servers preserve the full headers of outbound messages (and if they allow users to look at them). You might be able to see where it was sent from. I really, really don't think it was your local machine based on what you've described. Still, you may want to look into saving your mailing list locally within Empathy and removing it from the Hotmail server.

---

### Post by gangstafoo! on 2010-04-22
You dont need the password, you can just create an email phisher.. i built one and i can spam using other people's addresses.. i dont do this unless im just doing it to one of my friend and i tell them that im gonna do it btw, haha
and as for making it look like its coming from your IP... the IP is sent in the headers, which are sent from the email client, all the "hacker" had to do is change that to yours.. could be someone that is pissed off at you or something. 

hope you to have the best of luck

PS.. forgot to say this...

the name of the sender is also a header

---

### Post by cdenley on 2010-04-22
> **gangstafoo! said:**
> You dont need the password, you can just create an email phisher.. i built one and i can spam using other people's addresses.. i dont do this unless im just doing it to one of my friend and i tell them that im gonna do it btw, haha
and as for making it look like its coming from your IP... the IP is sent in the headers, which are sent from the email client, all the "hacker" had to do is change that to yours.. could be someone that is pissed off at you or something. 

hope you to have the best of luck

PS.. forgot to say this...

the name of the sender is also a header

You don't need an "e-mail phisher". All you need is the sendmail command, or anything that can establish a basic TCP connection like netcat. However, this has nothing to do with this thread, since they indicated a copy of the e-mail's were in their hotmail account's sent box. Your e-mail phisher cannot accomplish that without the user's password.

---

### Post by 2hot6ft2 on 2010-04-22
I seem to remember something about surprise.exe a few years ago making the news and info. about it flooding the net. I think it was around 2007 or 2008. You'll have to do some research to find out what all is affected then try recovering his windows. You may need to replace some system files with clean ones from a pc with the same OS that's not infected.
That's always fun.

---

