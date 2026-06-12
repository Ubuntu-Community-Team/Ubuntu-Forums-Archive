---
title: "ClamTK found a virus HELP"
date: 2011-07-04
forum: Security
---

### Post by Libertydude on 2011-07-04
Hi, I thought ubuntu could not get viruses? Well I scanned with ClamTK and it found a virus. See screenshot:

[IMG]http://img19.imageshack.us/img19/1967/hkjhl.jpg[/IMG]

Were my passwords stolen?

---

### Post by doas777 on 2011-07-04
nah, just a windows trojan, and besides, it was quarantined. its the first stage of a "drive by download". 

btw, a piece of malware usually needs to be running at the time you enter a password, in order for it to overhear it.

---

### Post by Libertydude on 2011-07-04
> **doas777 said:**
> nah, just a windows trojan, and besides, it was quarantined. its the first stage of a "drive by download". 

btw, a piece of malware usually needs to be running at the time you enter a password, in order for it to overhear it.
No, it was not "caught" I decided to run an on-demand scan.

So, let me get this straight, my passwords were not stolen? And I never was infected? It was just siting there idly?

---

### Post by doas777 on 2011-07-04
certainly looks that way. you can do some additional research on the malware itself if you dig through the logs and find more about it. not seeing a lot for Exploit.PDF-28719 on google. probably has a more common name from norton or mcaffe or one of the others.

I would certianly use bleachbit to clear your ff cache, and consider changing your passwords (since its never a  bad idea to change passwords).

---

### Post by Libertydude on 2011-07-04
> **doas777 said:**
> certainly looks that way. you can do some additional research on the malware itself if you dig through the logs and find more about it. not seeing a lot for Exploit.PDF-28719 on google. probably has a more common name from norton or mcaffe or one of the others.

I would certianly use bleachbit to clear your ff cache, and consider changing your passwords (since its never a  bad idea to change passwords).
I installed bleachbit, what do I do now?

Are you absolutely sure it never executed? And do you think I should just reformat?

---

### Post by Libertydude on 2011-07-04
Come on people! :)

---

### Post by doas777 on 2011-07-04
> **Libertydude said:**
> I installed bleachbit, what do I do now?

Are you absolutely sure it never executed? And do you think I should just reformat?
  rebuilding is going overboard, but as to whether it ever executed, no one could tell you that. the likelyhood is that it executed but could not leverage teh windows only exploit.

infact it may be a false positive. 
This sample caused that exploit to be detected by clamav but no other AV system noticed anything:
[http://file.virscan.org/report/a420ed612e613b7b6ac366a4a4fd5f41.html](http://file.virscan.org/report/a420ed612e613b7b6ac366a4a4fd5f41.html)

---

### Post by createdcreature on 2011-07-04
If it has been quarantined, it doesn't matter, just get on with ordinary life and don't worry.

---

### Post by Libertydude on 2011-07-04
I think I will reformat and browse in virtual box from now on.

Also, does anybody know if viruses can transfer from virtualbox to the host os?

---

### Post by Libertydude on 2011-07-04
Anybody?

---

### Post by doas777 on 2011-07-04
yes, if and only if the specific malware has code to do so. one in a billion odds. do you have powerful enemies?

---

### Post by Libertydude on 2011-07-04
> **doas777 said:**
> yes, if and only if the specific malware has code to do so. one in a billion odds. do you have powerful enemies?
What do you mean by powerful enemies?

---

### Post by doas777 on 2011-07-04
> **Libertydude said:**
> What do you mean by powerful enemies?
well, most malware is written to hit a wide swath of the populous, so it will use widly distributed tools and platforms like adobe acrobat\flash on a windows os. 

unlike windows, just about any real malware in linux is the result of a targeted attack. the attacker has a specific target in mind, and has researched the targets platform and how to penetrate it specifically. a person with powerful enemies has a great deal to fear and should go to extreme lengths. this might include corporations, governments, or dissidents in countries with oppressive regimes.

the normal linux user however can just pass a windows exploit by, since they are amongst the special 1% of users that choose a non-mainstream os, and thus have no serious worry, as long as they practice safe computing.

---

### Post by Libertydude on 2011-07-04
> **doas777 said:**
> well, most malware is written to hit a wide swath of the populous, so it will use widly distributed tools and platforms like adobe acrobat\flash on a windows os. 

unlike windows, just about any real malware in linux is the result of a targeted attack. the attacker has a specific target in mind, and has researched the targets platform and how to penetrate it specifically. a person with powerful enemies has a great deal to fear and should go to extreme lengths. this might include corporations, governments, or dissidents in countries with oppressive regimes.

the normal linux user however can just pass a windows exploit by, since they are amongst the special 1% of users that choose a non-mainstream os, and thus have no serious worry, as long as they practice safe computing.
No I don't. :)

Also, which real time anti-virus do you recommend?

---

### Post by Libertydude on 2011-07-04
Anybody?

---

### Post by doas777 on 2011-07-04
tbh, I don't use antivirus on linux desktops. I do use [clam on my server]("http://www.techmalaya.com/2008/05/10/clamav-real-time-scan/"), and another product on my windows desktops. I've tried [bitdefender]("https://help.ubuntu.com/community/BitDefender"), and liked the interface. I just don;t need it.

to keep ubuntu secure:

[LIST]
[*]use a home router. disable upnp. don't forward ports on your router without good cause.
[*]do not add untrustworthy repositories or ppas.
[*]do not install untrustworthy .debs, rpms, tarballs, or compile untrustworthy source.
[*]install and use noscripts in firefox.
[*]apply an [apparmor profile to firefox]("https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?").
[*]Do Not enable remote desktop (its ok if you do not allow it on your router and disable upnp)
[*]install security updates automatically.
[/LIST]
Do that, and powerful enemies are all you need fear.

---

### Post by handy on 2011-07-04
**@Libertydude:** You are being overly paranoid & anxious.

If you don't believe what people are telling you - which is you DON'T need to format, reinstall & all that.

Then stop asking questions in the hope that someone will give you an answer that meets the desires governed by the paranoia & anxiety that you have let this situation fuel up. If you wait long enough & keep asking for replies you will get the ones you want from people that don't know what they are talking about.

Relax & carry on as usual.

---

### Post by Libertydude on 2011-07-04
I will use all your advice. :)

> use a home router. disable upnp. don't forward ports on your router without good cause.
What is upnp?

---

### Post by doas777 on 2011-07-04
> **Libertydude said:**
> I will use all your advice. :)


What is upnp?
universal plug 'n play.
when you have a program that needs to recieve unsolicited connections, a port must be forwared on your router.

upnp is a protocol that allows a peice of host software to request that the router open the port automatically without the administrator(you) having to do anything or even knowing about it.

a peice of malware on your system could use upnp to do things like open ports for attackers, poision or intercept dns requests, etc. 

since upnp allows things I consider to be of high security importance occure without notification or permission, I recommend disabling it. others will disagree. you;ll have to weight the pros and cons and decide for yourself.

---

### Post by Libertydude on 2011-07-04
> **doas777 said:**
> universal plug 'n play.
when you have a program that needs to recieve unsolicited connections, a port must be forwared on your router.

upnp is a protocol that allows a peice of host software to request that the router open the port automatically without the administrator(you) having to do anything or even knowing about it.

a peice of malware on your system could use upnp to do things like open ports for attackers, poision or intercept dns requests, etc. 

since upnp allows things I consider to be of high security importance occure without notification or permission, I recommend disabling it. others will disagree. you;ll have to weight the pros and cons and decide for yourself.
Do you have a link on how to disable it?

And if I do disable it, how does it effect my system?

---

### Post by doas777 on 2011-07-04
its a setting inside your router, so you will have to look it up for your specific make and model of router.

---

### Post by westie457 on 2011-07-04
Hi take a look at this [https://help.ubuntu.com/community/Linuxvirus]("https://help.ubuntu.com/community/Linuxvirus").

Personally I think you are being needlessly paranoid about something is very likely never going to happen. 

Most people using Linux/Unix have anti-virus software to check for viruses for when they pass or send files to Windows users. The security built in Linux/Unix systems means that for one (a system) to be infected it has to be targeted with a specific purpose in mind EG take a lot of sensitive information of a server. That is not a virus or malware. THAT IS HACKING.

Generally speaking over time all systems that use the Internet will pick something however the in-built security with Linux/Unix means that 99.99 something of all Malware available will never run because they are all written for Microsoft File-systems.

The one mentioned in your original post is specifically written for Adobe Reader (a Windows Application). You do not need to worry about it as Linux has a PDF reader built in which uses different coding.

If I have missed anything out it is because I have forgotten and others here will explain in more detail.

Hope this helps.

---

### Post by Libertydude on 2011-07-04
> **westie457 said:**
> Hi take a look at this [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus).

Personally I think you are being needlessly paranoid about something is very likely never going to happen. 

Most people using Linux/Unix have anti-virus software to check for viruses for when they pass or send files to Windows users. The security built in Linux/Unix systems means that for one (a system) to be infected it has to be targeted with a specific purpose in mind EG take a lot of sensitive information of a server. That is not a virus or malware. THAT IS HACKING.

Generally speaking over time all systems that use the Internet will pick something however the in-built security with Linux/Unix means that 99.99 something of all Malware available will never run because they are all written for Microsoft File-systems.

The one mentioned in your original post is specifically written for Adobe Reader (a Windows Application). You do not need to worry about it as Linux has a PDF reader built in which uses different coding.

If I have missed anything out it is because I have forgotten and others here will explain in more detail.

Hope this helps.
But it was sitting in my firefox folder. How would that have affected adobe reader?

---

### Post by westie457 on 2011-07-04
> **Libertydude said:**
> But it was sitting in my firefox folder. How would that have affected adobe reader?

It was in your firefox folder because it came over the internet. If when using firefox in Windows and downloaded a document in PDF format the expoit could run. By default in Windows PDF documents only open in Adobe Reader. In Linux they open in a different application that has coding the exploit cannot understand and so cannot run to do whatever is was designed to do.

Oh by BTW the best way to do a scan is with Clamtk on a LiveUSB stick with no file-systems mounted and therefore no OS running from the hard drive.
That way the nasties cannot hide themselves.

Clamtk will list any it finds and from there it is easy to delete them whatever OS you normally use.

---

### Post by doas777 on 2011-07-04
> **Libertydude said:**
> But it was sitting in my firefox folder. How would that have affected adobe reader?

what you are seeing is the first stage of a drive-by-download attack.

1) client (you) goes to web page. the web page includes a compromised ad in an iframe in the top right hand corner.

2) the add renders a javascript, that attempts to load a pdf document off the server.

3) the pdf is malformed, and when executed on your system, downloads and executes a trojan horse.

4) the trojan horse executes and downloads further material, or otherwise does its evil (perhaps by scaring the user into paying for fake antivirus.).

most infections these days start this way. the vector may be acrobat or flash, or an ms office document (those are the leading vectors). \

so what you see there is the remenant of the first stage of the attack. a script that is supposed to call down, or itself contains a malformed pdf.

---

### Post by Libertydude on 2011-07-04
> **westie457 said:**
> It was in your firefox folder because it came over the internet. If when using firefox in Windows and downloaded a document in PDF format the expoit could run. By default in Windows PDF documents only open in Adobe Reader. In Linux they open in a different application that has coding the exploit cannot understand and so cannot run to do whatever is was designed to do.

Oh by BTW the best way to do a scan is with Clamtk on a LiveUSB stick with no file-systems mounted and therefore no OS running from the hard drive.
That way the nasties cannot hide themselves.

Clamtk will list any it finds and from there it is easy to delete them whatever OS you normally use.
So let me get this straight, it was simply harmlessly sitting in my firefox directory? Not causing any harm at all?

I am going to transmit my social security number over the internet soon and I don't want it hacked. Would you trust your ssn with that virus siting in your firefox dir?

---

### Post by westie457 on 2011-07-04
TBH yes I would. As mentioned previously that piece of malware was written specifically for one program that runs on a non-Linux system. Also if I was running that program on a non-Linux system I would still send it as this particular threat was stopped with an update from Adobe in September 2010.

---

### Post by Libertydude on 2011-07-04
> **westie457 said:**
> TBH yes I would. As mentioned previously that piece of malware was written specifically for one program that runs on a non-Linux system. Also if I was running that program on a non-Linux system I would still send it as this particular threat was stopped with an update from Adobe in September 2010.
But if I was using Windows, would a pdf popped open?

---

### Post by doas777 on 2011-07-04
> **Libertydude said:**
> But if I was using Windows, would a pdf popped open?
no, probably not. the document itself probably has no visual components to it. a process would spawn though, if you were watching a process monitor.

---

### Post by Libertydude on 2011-07-04
> **doas777 said:**
> no, probably not. the document itself probably has no visual components to it. a process would spawn though, if you were watching a process monitor.
Ah, okay. So basically if I was using windows, my anti-virus would have gone off?

And I am completely secure from this would be threat?

---

### Post by westie457 on 2011-07-04
> **Libertydude said:**
> Ah, okay. So basically if I was using windows, my anti-virus would have gone off?

And I am completely secure from this would be threat?

Yes. 

Take a look at the link I posted. It lists all the known malware that has ever been known to affect Linux.

---

### Post by Libertydude on 2011-07-04
> **westie457 said:**
> Yes. 

Take a look at the link I posted. It lists all the known malware that has ever been known to affect Linux.
Great, also I have another question. Let's say I visited an exploit site in chrome, would this affect my os? Or is firefox more capable of handling these sorts of things?

Also, does clamtk detect all the linux malware? Or both windows and linux malware?

---

### Post by westie457 on 2011-07-04
> **Libertydude said:**
> Great, also I have another question. Let's say I visited an exploit site in chrome, would this affect my os? Or is firefox more capable of handling these sorts of things?

Also, does clamtk detect all the linux malware? Or both windows and linux malware?

Answers in order

1. Let's say I visited an exploit site in chrome, would this affect my os?  No

2. Or is firefox more capable of handling these sorts of things?  I would say they are about the same, it is something I have not worried about.

3. Also, does clamtk detect all the linux malware? Or both windows and linux malware? Yes, it detects both.

Take a look at this [https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus") to understand why you do not need to worry about malware in Ubuntu and Linux/Unix OS's

---

### Post by Libertydude on 2011-07-04
> **westie457 said:**
> Answers in order

1. Let's say I visited an exploit site in chrome, would this affect my os?  No

2. Or is firefox more capable of handling these sorts of things?  I would say they are about the same, it is something I have not worried about.

3. Also, does clamtk detect all the linux malware? Or both windows and linux malware? Yes, it detects both.

Take a look at this [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) to understand why you do not need to worry about malware in Ubuntu and Linux/Unix OS's
Thanks pal. :)

---

### Post by westie457 on 2011-07-04
I forgot to mention there is one overriding factor in all this.

That is down to user error. Normal usage with normal security settings mean you are safe. However overriding these settings is a deliberate act on your part and makes your system slightly to highly vulnerable.

Normal security setting by default is you do not have access to the root of the file-system without using a password to gain access.

---

### Post by Libertydude on 2011-07-04
> **westie457 said:**
> I forgot to mention there is one overriding factor in all this.

That is down to user error. Normal usage with normal security settings mean you are safe. However overriding these settings is a deliberate act on your part and makes your system slightly to highly vulnerable.

Normal security setting by default is you do not have access to the root of the file-system without using a password to gain access.
Yep, I never use root. :)

---

### Post by westie457 on 2011-07-04
> **Libertydude said:**
> Yep, I never use root. :)

Hopefully your mind is now at ease.

Go and enjoy your life with many days of Happy Ubuntu-ing.

Could you mark this as solved now please. It will help others in a similar situation to yours.

PS use the 'Thread Tools' link.

---

### Post by nomko on 2011-07-04
> **Libertydude said:**
> Yep, I never use root. :)
 
As long you're not logged in as root or start programs as root, there's no reason to get scared for trojans. Any program which tries to install itself (this also means a program from Software Center) needs approval by the root > as a user you must enter your password in order to start the installation. This is a part of the Linux security system, no prgram can install itself without permission. Although Ubuntu took this part in his own lane (Debian uses a dedicated root password which has to be entered during the installation), it is still a secure system for end-users. 
 
So, if you are logged in as a normal/regular user, don't worry. You will be warned by a pop-up if some program (regular programs/trojans/virusses) tries to install itself on your system. At the moment you're on a infected site and some malware get's on yopur computer and there's a pop-up on your screen asking for your password and you're very sure about not installing a program, then you have to watch out.

---

### Post by CharlesA on 2011-07-04
> **Libertydude said:**
> Anybody?

Friendly reminder - Please don't bump threads until 24 hours have passed.

Thanks.

As for the trojan, it's either a Windows bug, or a false positive, either of those are harmless on a linux box.

Did you install any extensions recently?

---

### Post by Libertydude on 2011-07-04
So if I visited a linux exploit site, I would have to give it my password?

Wow, linux is so secure it wants a password before installing malware. :D

---

### Post by Libertydude on 2011-07-04
> **CharlesA said:**
> 
Did you install any extensions recently?
Yes:
[https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

Is that a virus?

---

### Post by nomko on 2011-07-04
> **Libertydude said:**
> So if I visited a linux exploit site, I would have to give it my password?
 
Wow, linux is so secure it wants a password before installing malware. :D
 
In a certain perspective it's funny. But really, Linux uses a root to install software. So, like doing this, it prevents the installation of unwanted software like virusses, trojans and malware. As long a user is a user and not logged in as a root or starts programs as a root, not a single malware will harm a Linux system. This is what makes Linux a more secure operating system then Windows. It's not so secure as you stated, it's only more secure due to a better rigths management system.

---

### Post by CharlesA on 2011-07-04
> **Libertydude said:**
> Yes:
[https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

Is that a virus?
I don't know if it is or not, but judging from the number of downloads and the rating, it's probably not.

More then likely just a false positive.

---

### Post by handy on 2011-07-06
I've been using DownloadHelper for a long time. It is safe as houses.

Here is another good link on the Linux virus situation:

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by emiller12345 on 2011-07-06
For PDF malware, I've heard of using pdfid.py and pdf-parser.py, tools by Didier Stevens, to investigate raw properties of pdf files.  It doesn't exactly tell you absolutely if its malware but will give you hints.

---

### Post by klotz on 2011-07-06
I believe Exploit.PDF-28719 is a false positive.
It goes off on Firebug because Firebug uses a Base64 encoder.

Try running clamscan on this, which is the source for the Base64.js encoder embedded in the Firebug extension:

[http://www.webtoolkit.info/javascript-base64.html#more-65](http://www.webtoolkit.info/javascript-base64.html#more-65)
clamscan 

Sure looks like a false positive to me.  I reported it last week.

---

