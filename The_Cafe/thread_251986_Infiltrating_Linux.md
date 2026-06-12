---
title: "Infiltrating Linux"
date: 2006-09-06
forum: The Cafe
---

### Post by bfakefree on 2006-09-06
I read soem posts about how secure Linux is and found these webpages

[http://www.acm.org/classics/sep95]("http://www.acm.org/classics/sep95")

[http://www.ghs.com/linux/manyeyes.html]("http://www.ghs.com/linux/manyeyes.html")

I'm no expert, but it does sound quite convincing and I will admit the one webpage sounds more like an advert flogging it's own secure OS, but it does bring up valid points.

The fact is that it is not a question of Can Linux be attacked, but when. I read an article where MS won't support Windows 98 anymore and it will effect somewhere in the region of 70-80 million users, that amount is staggering not to mention the many more millions using 2000,XP etc. There are alot of clever poeple in the world and more importantly their combined effort (like parrlel processing) when they talk amongst themeselves in their own secret forums sharing the latest weaknesses not to mention rougue goverments.

When Linux DOES take more market share then these poeple will turn their attention to Linux. Don't get me wrong, I've been convinced in the UBUNTU forums that Linux is better by design and more secure(I'm using work laptop at moment with XP, can't wait to get my own PC to actually try UBUNTU for first time), but this Post is dedicated to those Linux die hards that have blinkers on and are lining up to board the Titanic ](*,)

---

### Post by Tomosaur on 2006-09-06
Think of it this way - there are more people developing and securing linux than there are people seriously trying to find security holes and attack it. Most crackers aren't black-hat - they have absolutely no interest in making you suffer. All they want to do is point out a security hole so someone can fix it and stop the moronic bad crackers. The real problem with other OS's (alright, Windows :P) is that development is closed. Crackers are treated with impunity and often completely ignored when they point out a potentially serious problem, and Microsoft will withold patches and fixes to release when it suits them and their biggest customers, rather than releasing them as and when they're ready.

So in short: I wouldn't worry. I have confidence in the people developing Linux in general that most holes will be patched up ASAP.

EDIT: As for the Russia / China debate: the Cold War ended years ago, and the commies still prefer Windows (which they pirate anyway, so who gives a damn?) because the vast majority of people don't know any better. You can choose who you trust with Linux, and only use their version. Sure, the very core will be the same across systems, and yes this does present a potential risk, but with Windows you **have** to trust in Microsoft, and with stuff like WGA and DRM, I don't think I'll be doing that any time soon. Microsoft is a sleazy company, whereas Linux prides itself on its open, trusting standards. I'm confident that even if a malicious developer submitted some dodgy code, it would be caught and fixed by someone else. That's the absolute best way to deal with these kind of problems imo.

---

### Post by bfakefree on 2006-09-06
> So in short: I wouldn't worry. I have confidence in the people developing Linux in general that most holes will be patched up ASAP.

I've never been too worried, usually when I had major problems with Windows, I saved important files, reformatted hardrive and re-installed everything - it sucks of course and hated it but never worried, this Post is more dedicated to those that blindly believe Linux can't be cracked.

there is the Trojan horse thing that those links mention thats sounds quite interesting

---

### Post by SoundMachine on 2006-09-06
Indeed, being lulled into some false sense of security leaves a market open for hackers, phishing works equally well on Linux and Windows for example and people run or install applications from untrusted sources are always an easy target regardless of what OS they run.

As the Apache worms which were extremely successful proved, patches only patch the holes if you apply them. ;)

---

### Post by prizrak on 2006-09-06
Very few Linux die hards would tell you that it is uncrackable as Linux die hards tend to be very technically proficient and therefore understand that nothing is without flaw.

It is quite a bit harder to get into a Linux system and with tools like SELinux (actually included with Ubuntu but lacking any policies) it's much easier to secure than the counterpart. 

The real issue is users anyway, OS X is a pretty secure OS being BSD based and all yet there are OS X viruses that people do get. As mentioned above phishing is as likely to work on Linux as it would on Windows or OS X. The only thing making Linux less phishing prone is the generally more educated userbase.

---

### Post by ago on 2006-09-06
The first article involves messing up the C compiler code to mess up programs without any trace in the source of those programs... All very nice... Except that there will still be a big trace... in the compiler... You are simply moving the bug from one source tree to another one. But you have not solved the problem of how to hide it.

The compiler is itself an open source project. How exactly do you plan to mess it up without anybody else noticing? If anything, there are more (competent) eyes on the compiler than on most other projects. Patches are forwarded to all mainteners, and even if you somehow fool them, once the code is in CVS anybody can see that, not to mention that any developer that is working on the same page will downlad the changeset and will go thorugh the code changes.

If someone manages to change the C compiler code unnoticed, he deserves to crack my machine.

---

### Post by ago on 2006-09-06
The second argument, is very similar to the first one. It assumes that you can easily mess-up code, unnoticed. This time in the kernel instead of the C compiler. Just try it...

---

### Post by ago on 2006-09-06
The reality is that it is very, very difficult to introduce malicious code in the kernel or in the compiler. You can't just go in and change the code. That is not how it works. You have to fool the best coders in the world, and you can bet that any single line changed in those projects, is going to be scrutinized by several people, highly competent, and it will be visible to the rest of the world for ever.

---

### Post by M7S on 2006-09-06
Isn't that first article about why you never can trust closed source programs at any level? I've seen people link to it before and then it was iirc used as a argument for opensource.

---

### Post by ago on 2006-09-06
It would work for open sorce IF the compiler used to compile open source projects was a compromised closed source compiler, but it does not work that well with an open source compiler (which is what OSS projects use). Or an open source kernel. 

On windows most projects use closed source compilers... Same thing for the kernel... You really need to trust MS, as a company (the one that installed WGA...) and MS developers individually and whoever provided the compiler used in the programs you installed... On top of it, for each and every binary program you install, you have to make an additional new leap of faith... And even then, most downloads are not signed in windows, someone could swap files on the fly, yet another leap...

---

### Post by ago on 2006-09-06
And by the way, it is far easier to infiltrate MS, even assuming you can trust them in the first place... 

In MS I am quite sure that the sourcecode of the kernel/compiler is compartmented, to protect IP. Therefore for each block of code, outside of the specific team, you have very few eye-balls, and often those are the eye-balls of persons high-up in the ranks who do not have the time to check each new line of code. If you have control on the hiring of one of the compiler/kernel teams you can control virtually all the eye-balls involved in your slice of the compiler/kernel, and you can do whatever you want with it... By its very nature, it is impossible to control eye-ball access for OSS projects.

---

### Post by Tomosaur on 2006-09-06
Christ. Ever heard of the edit button?

---

### Post by ago on 2006-09-06
> **SoundMachine said:**
> for example and people run or install applications from untrusted sources are always an easy target regardless of what OS they run.

All my Ubuntu apps come from Ubuntu repositories, and all the downloads are signed. I only have to trust one party, which is not too difficult considering that the binaries are compiled from sources (which as mentioned is difficult to tamper with) and any infiltration during the compilation phase can be verified when other developers independently recompile a package.

Unlike windows I do not fetch the packages from 200 websites and pray. As mentioned, in windows you have to trust, in order: 

[list]
[*]MS, 
[*]MS developers, 
[*]the company developing the compiler of each of the apps you run, 
[*]the developers of that compiler, 
[*]the companies writing the software you installed (for each single piece of software you install), 
[*]the developers of those companies (for each single piece of software you install)
[*]the websites hosting the files (for each single piece of software you download)
[*]hope that nobody is going to swap the files on the fly (for each single piece of software you download)
[/list]

---

