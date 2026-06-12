---
title: "Slashdot: *nix has more vulnerabilities than Windows"
date: 2006-01-04
forum: The Cafe
---

### Post by jdong on 2006-01-04
[http://it.slashdot.org/it/06/01/05/0027219.shtml?tid=172&tid=218](http://it.slashdot.org/it/06/01/05/0027219.shtml?tid=172&tid=218)

Slashdot goes at a big debate again.... Does anyone actually *buy* security arguments based on these vulnerability counts?

---

### Post by jdong on 2006-01-04
[http://www.groklaw.net/article.php?story=20051231142317870](http://www.groklaw.net/article.php?story=20051231142317870)

has a good rebuttal to the argument, but I would also add in the fact that open source typically means that security vulnerabilities will get discovered (and therefore patched) faster and in the end you have a very secure product.

---

### Post by dickohead on 2006-01-04
Everytime someone comes out with a "Security" Article, I give it the usual eye roll, a quick look over and then lots of head slapping.

The number of vulnerabilities is no way to tell how secure or insecure a system is, it's the scope and severity of those vulnerabilities that should be used to decide whether one system is more or less secure than another.

---

### Post by jdong on 2006-01-04
It starts getting really sad when newspapers and "tech columns" start using this information to formulate ridiculous claims and recommendations.

I've worked with a few friends who are highly MS brainwashed, and recently it really did show. These are the people who'd tell you that Linux is more expensive than Windows, Firefox has more security issues than IE, and that their 25 AV+firewall+AT+AS setup is impermeable to even government hackers.

I would consider them Windows gurus, but their understanding of the WMF vulnerability just appalled me. Their opinion is that it's a very minor and unrealistic threat that Linux people put out their to slander Microsoft. A quick demo exploit that deletes a preset folder quickly changed their opinions :)

---

### Post by xequence on 2006-01-04
> Linux/Unix (including Mac OS) had almost three times the number of OS-specific vulnerabilities reported last year compared to Microsoft Windows.

Thats probably true. More reported vulnerabilities. But they get fixed on Unix. There are many many more windows ones not reported.

But its really hard with these things to say what OS is more secure. The only person id trust with that is some super hacker.

---

### Post by ardchoille on 2006-01-04
I like the first few threads in that post.. they make a lot of sense (especially the first one).

---

### Post by briancurtin on 2006-01-04
"I'm sure all the GM, Toyota and Honda cars between 1970 and 1990 put together had more design flaws than the Ford Pinto, but this comparison is not relevant."

^i liked that

---

### Post by jdong on 2006-01-04
[QUOTE=xequence]Thats probably true[/QUOTE]

Actually, I would go further to say that it IS true :)

The thing is, everyone who reads these things need to take a step back and avoid leaping to the almost natural "thus Windows has become more secure than Linux" conclusion after looking at these figures.

In addition, as you noted, it is phrased as **REPORTED** vulnerabilities.... heaven knows how many vulnerabilities are in the Windows codebase that MS isn't telling us... or don't know themselves....

---

### Post by dickohead on 2006-01-04
Be careful with that above statement: > heaven knows how many vulnerabilities are in the Windows codebase that MS isn't telling us... or don't know themselves....

The same can be said for Linux, Mac, BSD, Unix, Netware etc etc etc, the real issue is not that people compare Windows with Linux, which engulfs all Unix based or other systems, the problem is that Windows is much easier to analyse as a product due it's more limited product line, anyone attempting to compare Linux with Windows will NEVER succeed, because unlike Windows, Linux does not come in Media-Centre/Home/Pro and Server versions, it comes in thousands of different flavours, versions, colours, languages, can sport any design, logo or message you want. The only real way to measure the success of Windows vs Linux is to compare both the top 5 commercial and the top 5 community distributions against varying standard windows platforms (ie: XP Pro, Server 2003, XP Home, XP Media Centre).

But anyone who reads these reports will soon realise that there is always going to be an anti-Linux or anti-Windows sentiment in any figures quoted, leading to conclusions that will only better support the writers views and opinions.

---

### Post by ardchoille on 2006-01-04
[QUOTE=jdong][QUOTE=xequence]Thats probably true/QUOTE]
...In addition, as you noted, it is phrased as **REPORTED** vulnerabilities.... heaven knows how many vulnerabilities are in the Windows codebase that MS isn't telling us... or don't know themselves....[/QUOTE]
That is EXACTLY why no one should ever trust a closed source OS. For all the user knows, their name, address, social security number, bank account info, mother's maiden name and all other information that has ever passed through their Windows computer is sent back to Microsoft and added to a file/device that will sooner or later be sold, stolen or lost.

We all have heard of how businesses have "lost" client account info - or had it stolen.

---

### Post by jdong on 2006-01-04
[QUOTE=dickohead]The same can be said for Linux, Mac, BSD, Unix, Netware etc etc etc,[/QUOTE]

To a much lesser extent, due to the open source nature of Linux, BSD, and even to some degree OSX. There are plenty of independent reviewers auditing open source code, and lots of vulnerabilities discovered thanks to them (remember DJB's 500-level security course at U of Chicago? Find a security vulnerability or fail. 100+ found in various OSS programs)

---

### Post by mstlyevil on 2006-01-04
[QUOTE=jdong]To a much lesser extent, due to the open source nature of Linux, BSD, and even to some degree OSX. There are plenty of independent reviewers auditing open source code, and lots of vulnerabilities discovered thanks to them (remember DJB's 500-level security course at U of Chicago? Find a security vulnerability or fail. 100+ found in various OSS programs)[/QUOTE]

The biggest difference between Linux/Unix vulnerabilities and Windows vulnerabilities is that the ones in Windows are exploited more often/faster. Also the extent of damage in Windows is usually far greater because most users run as administrator.

---

### Post by dickohead on 2006-01-04
My point was that it's a gross generalisation to say that one OS could be hiding vulnerabilities or is just not aware of them, where the one you are closely tied with has less or has the possibility of having less. It's all relative in respect to these types of articles and reviews. We could quite easily perform an audit of a Windows system compared to a Linux system, say Ubuntu, and praise all the good points, neglect to mention the bad and provide an article that leads readers to conclude that because one Linux system has strong points over Windows, Linux must be better as a whole.

I'm well aware that closed source development models are less scrutinized and that vulnerabilities could be more easily overlooked, but that doesn't always mean that's true. Just as a lot of people would say that a system where you cannot install proprietry software would never take off - not for them no.... it's all relative.

---

### Post by jdong on 2006-01-04
[QUOTE=dickohead]

I'm well aware that closed source development models are less scrutinized and that vulnerabilities could be more easily overlooked, but that doesn't always mean that's true.[/QUOTE]

In the case of Microsoft, however, it has been verified true at least once in the relevant past (Win2k partial source leak), which leads me to be more concerned.

I remain more hopeful about the claims of Vista and truly hope for them to be true.

---

### Post by ardchoille on 2006-01-04
[QUOTE=jdong]In the case of Microsoft, however, it has been verified true at least once in the relevant past (Win2k partial source leak), which leads me to be more concerned.

I remain more hopeful about the claims of Vista and truly hope for them to be true.[/QUOTE]
Given Microsoft's track record, they can't be trusted, and neither can their products.. regardless of what they name the new OS. There is going to be something somewhere that they are going to hide.. and there are going to be bad things that they will not bring to light.. that's their nature.

Microsoft also seems very talented at spreading FUD and lies.. therefore their claims canot be trusted either.

---

### Post by catlee on 2006-01-04
My take on this is that, yes, more flaws are found in Linux because we've got thousands of people reading and updating the code on a daily basis.  If there is something that can be improved, we will find it.

Windows has far fewer items patched because they've got a few hundred people updating code 9-5, M-F.. and thats only when they are asked to.  I'm sure they don't have 1/10 of the emotional investment that the rest of us do.  Its a paycheck.

If you would like to really gauge *nix vs MS security get on the internet for 10 minutes with a bare installation of each.  Which system still runs as it should afterwards?

---

### Post by 23meg on 2006-01-04
It's all make believe. You can hire any think tank to produce any report and spit out any conclusion you want, yet it will never truly show objectively that one platform is "more secure" than the other by definition. I just ignore these debates completely and continue working with FOSS, which I trust for reasons beyond merely technical security.

---

### Post by Corvillus on 2006-01-05
You also can't neglect the fact that with Windows, regardless of when during the month the flaw was discovered, nothing gets released by Microsoft until "patch tuesday" in most cases, which leaves a long exploit window.With Linux, work tends to be done immediately done to fix the flaw and then patch gets released and can be applied right away when it is ready.

---

### Post by asimon on 2006-01-05
This vulnerability counting based on pure quantities is absolute meaningless when it comes to seriously compare the security of different systems. It's just a marketing instrument. And I think not a bad one.

---

### Post by Galoot on 2006-01-05
I've been stung by many bees in my life, yet here I am.

My allergic friend, on the other hand, was only stung once. God rest his soul.

---

### Post by drucer on 2006-01-05
Slashdot user "Pollardito" pointed it out:

"..here's some of the UNIX vulnerabilities :

    # Adobe Acrobat Reader mailListIsPdf() Buffer Overflow (Updated)
    # Adobe Acrobat Reader mailListIsPdf() Buffer Overflow (Updated)
    # Adobe Acrobat Reader UnixAppOpenFilePerform Buffer Overflow
    # Adobe Acrobat Reader UnixAppOpenFilePerform Buffer Overflow (Updated)
    # Adobe Reader / Acrobat Arbitrary Code Execution & Elevated Privileges
    # Adobe Reader For Unix Local File Disclosure
    # Andrew Church IRC Services LISTLINKS Information Disclosure

this isn't a list of OS vulnerabilities, it's a list of application vulnerabilities sorted by OS"

..

And Slashdot user "khasim" also made a very good point:

"TFA says that there were 2,328 reported vulnerabilities for *nix.

I counted the lines and there are 2,329 lines.

Here's an example of 10 of them:
# BZip2 File Permission Modification
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)
# BZip2 File Permission Modification (Updated)

Yep. BZip2 is listed 10 times, but the reference to each of them reads the same:

    A vulnerability has been reported when an archive is extracted into a world or group writeable directory, which could let a malicious user modify file permissions of target files.

And then they list 10 different distributions. Hmmmmm ..... it looks like the old "multiple reporting" problem.

So, one problem in BZip2 == 10 counts of "problems"."

---

