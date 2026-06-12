---
title: "Can use of adobe reader be a security threat in ubuntu?"
date: 2011-09-17
forum: Security
---

### Post by arroy_0209 on 2011-09-17
People generally agree that adobe reader is a powerful tool for viewing pdf files but at the same time complain of its bulky nature and that it may cause security problems. (I guess the security problem would be more with windows OS rather than with linux, but that's just a guess.) I am tired of getting security warning about almost every application I need to use. I would like to know whether others have really faced security problems due to use of adobe reader. I am using ubuntu 10.04 LTS.

In case it is better to control adobe reader using apparmor, please give me details of required configuration or tell me where such info is available.

---

### Post by Lars Noodén on 2011-09-18
Why use Adobe Reader when you have Okular and Evince?  They're much better than Reader.

---

### Post by Lars Noodén on 2011-09-18
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

---

### Post by OpSecShellshock on 2011-09-18
Vulnerabilities that are specific to Adobe Reader should probably be regarded as cross-platform, although *exploits* are not likely to be targeted to Linux systems. In order for it to be a security problem with your system, the code that is set up to be executed following the application crash in an attack scenario would have to be written for Linux. I have never heard of that happening outside of general proof-of-concept done by researchers, so I would regard the risk as very low, but non-zero.

---

### Post by arroy_0209 on 2011-09-19
> Why use Adobe Reader when you have Okular and Evince?  They're much better than Reader. 	

The reason I am not satisfied with evince is that it is unable to display pdf files properly at times. This is supported by some other users also. Recently I downloaded one application form from one university website where the logo (small picture) is not displayed at all and instead a dark square is displayed. When I printed another form which looked ok in evince, I found that some squares (for putting tick marks) did not come properly. This problem has also been faced by many users. This is why I am looking for some alternative pdf viewer. 

I have one confusion: Is there any difference between the terms: pdf-viewer and pdf-reader?

---

### Post by vasa1 on 2011-09-19
> **arroy_0209 said:**
> The reason I am not satisfied with evince is that it is unable to display pdf files properly at times. This is supported by some other users also. ...

Just a suggestion (that doesn't address your problem) ... but you should complain as loudly as you can when you encounter such files. Such peculiar files are used by Adobe to retain its failing monopoly.

It's especially sad to see universities blindly continue to utilize proprietary software when equivalent open source material is available.

---

### Post by Lars Noodén on 2011-09-19
> **arroy_0209 said:**
> The reason I am not satisfied with evince is that it is unable to display pdf files properly at times. This is supported by some other users also. Recently I downloaded one application form from one university website where the logo (small picture) is not displayed at all and instead a dark square is displayed. When I printed another form which looked ok in evince, I found that some squares (for putting tick marks) did not come properly. This problem has also been faced by many users. This is why I am looking for some alternative pdf viewer. 


That's worth writing a bug report for.  Does it happen also with Okular?

> **arroy_0209 said:**
> I have one confusion: Is there any difference between the terms: pdf-viewer and pdf-reader?

Two names for the same thing.

---

### Post by Paddy Landau on 2011-09-20
> **Lars Noodén said:**
> Why use Adobe Reader when you have Okular and Evince?  They're much better than Reader.
Not when it comes to options for printing!

---

### Post by Dangertux on 2011-09-20
> **OpSecShellshock said:**
> Vulnerabilities that are specific to Adobe Reader should probably be regarded as cross-platform, although *exploits* are not likely to be targeted to Linux systems. In order for it to be a security problem with your system, the code that is set up to be executed following the application crash in an attack scenario would have to be written for Linux.** I have never heard of that happening outside of general proof-of-concept done by researchers, so I would regard the risk as very low, but non-zero.**

Umm... While I hate to be the bearer of bad news, Adobe Reader can be exploited across different platforms and it is done quite frequently and moreso than just POC.  You have to remember , just because the majority of the home userspace isn't using Linux does not mean many corporations aren't. 

Generating a malicious .pdf and appropriate Linux shell code is not only an automated process, it's extremely easy to do with a variety of tools including but not limited to Metasploit Framework, SET, and FastTrack.

---

### Post by OpSecShellshock on 2011-09-20
> **Dangertux said:**
> Umm... While I hate to be the bearer of bad news, Adobe Reader can be exploited across different platforms and it is done quite frequently and moreso than just POC.  You have to remember , just because the majority of the home userspace isn't using Linux does not mean many corporations aren't. 

Generating a malicious .pdf and appropriate Linux shell code is not only an automated process, it's extremely easy to do with a variety of tools including but not limited to Metasploit Framework, SET, and FastTrack.

Oh no, of course the exploit code exists and is easy to execute, but it's not out there getting built into Black Hole and the like, the stuff your typical home and enterprise user is most likely to encounter out on the web regularly. In a direct contact (spam, spear phish) scenario, all bets are off. The risk of encountering malicious files in the first place is low, but the risk of opening them, well owned is owned.

As to the functionality issue, this is where users have to assess their own risks. A file that has fancy scripts and menus and forms and things that require Adobe Reader for use and which comes from a good source should be fine to open in Reader. It's perfectly possible to have more than one PDF reader, and just make Adobe the non-default, but available for use in situations that call for it. There really aren't many such situations.

---

### Post by Dangertux on 2011-09-29
Umm hate to be pedantic but actually CVE-2009-0927 CVE-2008-2992 and CVE-2007-5659 are all utilized with black hole frequently and all are reader vulnerabilities. 

I also disagree with you in that statistically file format exploits are one of the most common vulnerabilities in the home user space at the moment. As well your logic on social engineering attacks like spear phishing is flawed, since they are often commonly used in conjunction with file format exploits to increase effectiveness.

---

### Post by OpSecShellshock on 2011-09-29
Right, but the Black Hole kits that exist go after Windows, and most targeted attacks go for Windows or Macs. The exploit itself is one stage of the delivery process, but if the code execution that follows the heap spray (or whatever the technique is) is for Windows, then there's not much risk to a desktop Linux user (**important note: this does not mean that it should be considered safe to open a known-bad file just to see what happens**).

That said, I have seen tests performed by The H that have successfully followed up a crafted PDF opened with Reader to obtain a shell on Ubuntu. How much of a risk that represents just depends on how likely a user will be to encounter such an exploit for real, and on what happens after. My guess is an exploit would be followed up with a privilege escalation of some kind and then an effort to retrieve files from off site and/or establish recurring access. But that's not something that tends to happen within typical home user use patterns except on Windows. People should just keep in mind that it could, as in there is nothing technical stopping it from happening.

So if the question is whether it's safe enough to use Adobe Reader in those situations where that's the only application that will work (which itself is dumb on the part of the file's authors, but so are a lot of things) and where the user knows what the file is and where it came from, then I think it probably is. Reader is somewhat risky, but it's not Java risky.

---

### Post by Dangertux on 2011-09-29
> **OpSecShellshock said:**
> Right, but the Black Hole kits that exist go after Windows, and most targeted attacks go for Windows or Macs. The exploit itself is one stage of the delivery process, but if the code execution that follows the heap spray (or whatever the technique is) is for Windows, then there's not much risk to a desktop Linux user (**important note: this does not mean that it should be considered safe to open a known-bad file just to see what happens**).

That said, I have seen tests performed by The H that have successfully followed up a crafted PDF opened with Reader to obtain a shell on Ubuntu. How much of a risk that represents just depends on how likely a user will be to encounter such an exploit for real, and on what happens after. My guess is an exploit would be followed up with a privilege escalation of some kind and then an effort to retrieve files from off site and/or establish recurring access. But that's not something that tends to happen within typical home user use patterns except on Windows. People should just keep in mind that it could, as in there is nothing technical stopping it from happening.

So if the question is whether it's safe enough to use Adobe Reader in those situations where that's the only application that will work (which itself is dumb on the part of the file's authors, but so are a lot of things) and where the user knows what the file is and where it came from, then I think it probably is. Reader is somewhat risky, but it's not Java risky.

Ok, I will agree with that statement.  Bottom line here is yes -- if someone were to target Linux there is nothing particularly stopping it from working. Reality is , it's not targeted as often. Fair enough. 

Also just a couple of things about heap spraying for those reading along. It's a technique designed to allocate proper instructions for execution into the heap. It relies on the fact that the application can place a large amount of data on the heap, and it also often relies on utilizing internal scripting engines in applicatiosn (like reader) to generate a lot of the payload. Basically, it's used to counter ASLR by flooding registers with execution instructions since you don't actually know what the next pointer will be. It can also be used to manipulate pointers toward a controllable memory register.

---

