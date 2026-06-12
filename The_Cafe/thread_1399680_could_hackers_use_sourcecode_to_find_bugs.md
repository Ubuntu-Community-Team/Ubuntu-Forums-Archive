---
title: "could hackers use sourcecode to find bugs?"
date: 2010-02-06
forum: The Cafe
---

### Post by samantha_ on 2010-02-06
something actually popped up in my mind a while ago. just as developers/programmers/users can look into the sourcecode of an app, whats to stop hackers from also looking at the sourcecode and finding bugs in the code to exploit? and im just curious....

---

### Post by juancarlospaco on 2010-02-06
*Its the way to find Security Bugs...*

---

### Post by samantha_ on 2010-02-06
> **juancarlospaco said:**
> *Its the way to find Security Bugs...*

hackers as in the bad guys....

---

### Post by Sef on 2010-02-06
> something actually popped up in my mind a while ago. just as  developers/programmers/users can look into the sourcecode of an app,  whats to stop hackers from also looking at the sourcecode and finding  bugs in the code to exploit? 

Yes, but you do not need the source code to create malware to hack into a system.

---

### Post by BuffaloX on 2010-02-06
You just stumbled upon the premier argument from closed source companies why they regard Open source as less secure.

Crackers can and probably do look at source code, but it is seemingly an inefficient way to crack security.

If they succeed in cracking the security, open source has many advantages that make it easier and faster to close holes, and so limit the damage.

Among the advantages are:

1. Open source systems, allow more people to know what's actually going on within their systems, which enable them to give higher quality reports of the security flaws, which enable developers to locate it faster.

2. Self interest will make many people investigate their own systems further, making the number of people working on it larger than an ordinary developer team.

3. A more open dialogue ease the cooperation between those working on the problem.

The above points have all been shown to work very well.

The opposite "security by obscurity" has turned out not to work so well.

---

### Post by Simon17 on 2010-02-06
Yes it is possible and not uncommon. One of the easiest ways to do it is to search the source for fixed-size buffers which can be overflowed.

---

### Post by Mike'sHardLinux on 2010-02-06
Looking at source code has got to be the absolute most difficult way to find bugs/vulnerabilities to exploit. I mean, if it were so easy to look at source code to find them, don't you think the programmers themselves would just as easily be able to look at the source code the same way and fix them before they ever got out??? There are far more easier/efficient/quicker ways....

---

### Post by BuffaloX on 2010-02-06
> **Simon17 said:**
> Yes it is possible and not uncommon. One of the easiest ways to do it is to search the source for fixed-size buffers which can be overflowed.

Yes but so can IBM, Red Hat, Novell, Oracle, Google, you, me, everybody.
So such bugs are rare.

---

### Post by cariboo on 2010-02-06
The biggest security problem is not vulnerabilities in the code, but the users themselves. If you check the [Security Discussion]("http:///ubuntuforums.org/forumdisplay.php?f=338") sub-forum, you'll find that most of the systems that are cracked are due to poor/weak or no passwords on services that are open to the world.

---

### Post by BuffaloX on 2010-02-06
> **cariboo907 said:**
> The biggest security problem is not vulnerabilities in the code, but the users themselves. If you check the [Security Discussion]("http:///ubuntuforums.org/forumdisplay.php?f=338") sub-forum, you'll find that most of the systems that are cracked are due to poor/weak or no passwords on services that are open to the world.

Most traffic accidents are caused by poor driving, and this is related to the Toyota gas pedal problems how?

---

### Post by Hallvor on 2010-02-06
> **samantha_ said:**
> something actually popped up in my mind a while ago. just as developers/programmers/users can look into the sourcecode of an app, whats to stop hackers from also looking at the sourcecode and finding bugs in the code to exploit? and im just curious....

You don`t need the source code to find exploits. If that was the case there would not be any malware for Windows.

I think the more eyes reading the code the better. It leads to fewer bugs and better security. And if security is good it doesn`t matter if the source code is open or not.

---

### Post by earthpigg on 2010-02-06
i think a lot of folks miss the ***cultural*** aspect of this.

im not going to use the word 'hacker' because it is to ambigious - for example, if you chisel paint with a flathead screwdriver, you are a screwdriver hacker... likewise, if you ask an innocent older person for their credit card number, you are a 'credit card hacker'. the term is useless, thanks to both Hollywood and the BBC.

moving on from that: culture.

our potential bad guy wants, above else, recognition. 

with Free Software, he reveals his discovery of a security vulnerability by doing something rediculous to a journalist's cell phone at the Black Hat Conference.

with proprietary software, he does this by selling himself to the highest bidder and maybe doing a little identity theft while s/he is at it.

with open source stuff, demonstrating your knowledge in a clever way and then submitting a patch is what is glorified.

with proprietary stuff, financial rape is what is glorified.

either way, the results are the same for our ***potential*** bad guy.

---

### Post by Linux_junkie on 2010-02-06
> **samantha_ said:**
> something actually popped up in my mind a while ago. just as developers/programmers/users can look into the sourcecode of an app, whats to stop hackers from also looking at the sourcecode and finding bugs in the code to exploit? and im just curious....

If you mean criminals then it is possible for them to access the source code and write something in to it to gain access to your system.  However, the way the open source environment works should stop this.  That is because you have to upload your amendments to the source code to the group responsible for that application and before they release to the masses they double check and test that the code you entered works and does not compromise security.

This way reduces the chance of the end user from installing any applications that compromises your system.

Linux_junkie

---

### Post by Eisenwinter on 2010-02-06
> **samantha_ said:**
> hackers as in the bad guys....
You should call them either crackers, or black-hat hackers.

The term "hacker", when applied to the concept of software development, refers to a computer programmer who builds programs, not one who cracks security and attempts to exploit holes.

So, in conclusion:

Good guys: "Hacker", "White-Hat Hacker"

Bad Guys: "Cracker", "Black-Hat Hacker"

---

### Post by Sporkman on 2010-02-06
> **Eisenwinter said:**
> You should call them either crackers, or black-hat hackers.

The term "hacker", when applied to the concept of software development, refers to a computer programmer who builds programs, not one who cracks security and attempts to exploit holes.

So, in conclusion:

Good guys: "Hacker", "White-Hat Hacker"

Bad Guys: "Cracker", "Black-Hat Hacker"


Nope. Language changes, and popular usage dictates the current state of the language and the meaning of words.

Today, "hacker" means a person who attempts to gain unauthorized access to computer systems. It may not have meant that *before*, but it means that *now*.

Have a nice day. :)

---

### Post by Icehuck on 2010-02-06
> **Sporkman said:**
> Nope. Language changes, and popular usage dictates the current state of the language and the meaning of words.

Today, "hacker" means a person who attempts to gain unauthorized access to computer systems. It may not have meant that *before*, but it means that *now*.

Have a nice day. :)

Listen to the spork.  He is quite wise even though he is a spork.

---

### Post by juancarlospaco on 2010-02-06
> **samantha_ said:**
> hackers as in the bad guys....

Yeah, the bad guys..., 
but when you look for security vulnerability on your systems,
basically you can do the same that does the bad guys,
to try to find out a security breach, but without breaking anything.
*I tested some vulnerability trought RDP, IP stack overflows, RPC on Windowz*

I.E. Read about **Penetration Test**.

---

### Post by ssam on 2010-02-06
there are chucks of windows source code available in certain circles,
[http://www.theregister.co.uk/2004/02/13/ms_windows_source_code_escapes/](http://www.theregister.co.uk/2004/02/13/ms_windows_source_code_escapes/)
or if you ask right
[http://www.microsoft.com/resources/sharedsource/default.mspx](http://www.microsoft.com/resources/sharedsource/default.mspx)

security bugs can also be found in an automated way, see [http://en.wikipedia.org/wiki/Coverity](http://en.wikipedia.org/wiki/Coverity)

---

### Post by earthpigg on 2010-02-06
> **juancarlospaco said:**
> Yeah, the bad guys..., 
but when you look for security vulnerability on your systems,
basically you can do the same that does the bad guys,
to try to find out a security breach, but without breaking anything.
*I tested some vulnerability trought RDP, IP stack overflows, RPC on Windowz*

I.E. Read about **Penetration Test**.

indeed, the only difference between a bad guy security cracker and a professional security auditor is who lines their pockets.

identical tools and methods are used - most of the software tools can be found in our very own repositories, accessible via 'sudo apt-get install'.

if some odd turn events resulted in all the worlds professional security auditors suddenly becoming unemployed, things like identity theft would become astronomically more common. one way or another, the children of our friendly security auditors ***will*** be fed.

---

### Post by samjh on 2010-02-06
> **earthpigg said:**
> indeed, the only difference between a bad guy security cracker and a professional security auditor is who lines their pockets.

No.  The only difference is not *who* lines their pockets (they both line their own pockets), but *how* they line their pockets.  Firstly, the bad guys do it illegally and without your permission, while auditors do it legally and with your permission.  Secondly, the bad guys do it by selling or otherwise exploiting your valuable information unlawfully, while auditors get paid for legitimate services.

---

### Post by JDShu on 2010-02-06
> **Sporkman said:**
> Nope. Language changes, and popular usage dictates the current state of the language and the meaning of words.

Today, "hacker" means a person who attempts to gain unauthorized access to computer systems. It may not have meant that *before*, but it means that *now*.

Have a nice day. :)

Time and place matter. *On this forum* it means **[this]("http://catb.org/%7Eesr/faqs/hacker-howto.html#what_is")**.

---

### Post by Sporkman on 2010-02-06
> **JDShu said:**
> Time and place matter. *On this forum* it means **[this]("http://catb.org/%7Eesr/faqs/hacker-howto.html#what_is")**.

Nope. If it did, then you traditionalists wouldn't have to spend so much time correcting people & trying to re-(or retro-)define "hacker".

:)

---

### Post by JDShu on 2010-02-06
> **Sporkman said:**
> Nope. If it did, then you traditionalists wouldn't have to spend so much time correcting people & trying to re-(or retro-)define "hacker".

:)

Not necessarily, people can be wrong. If it meant what you said, us traditionalists would not be correcting :P

---

### Post by lisati on 2010-02-06
> **BuffaloX said:**
> Most traffic accidents are caused by poor driving, and this is related to the Toyota gas pedal problems how?
... or the floor mat problem? ... or the problem with the brakes?

---

### Post by samantha_ on 2010-02-06
> **lisati said:**
> ... or the floor mat problem? ... or the problem with the brakes?

its called a problem with drive-by-wire.
besides, the floor mat problem doesnt exist...

---

### Post by lisati on 2010-02-07
> **samantha_ said:**
> its called a problem with drive-by-wire.
besides, the floor mat problem doesnt exist...

Then why is Toyota doing a recall?
[http://www.khabrein.info/news/Toyota_recall_January_2010__Toyota_recall_gas_pedal___Toyota_recall_floor_mats_1265519725/](http://www.khabrein.info/news/Toyota_recall_January_2010__Toyota_recall_gas_pedal___Toyota_recall_floor_mats_1265519725/)

---

### Post by tubezninja on 2010-02-07
> **BuffaloX said:**
> Most traffic accidents are caused by poor driving, and this is related to the Toyota gas pedal problems how?

And gas pedal problems are related to open source code, how?

---

### Post by CJ Master on 2010-02-07
> **scaredpoet said:**
> And gas pedal problems are related to open source code, how?

It just is. Trust us.

---

### Post by BuffaloX on 2010-02-07
> **scaredpoet said:**
> And gas pedal problems are related to open source code, how?

It's an analogy.
Each and every time someone ask a security question on these forums, someone has to enter the argument that security doesn't matter, because people are so stupid they are much more likely to infect their system by bad practices.

By the same logic, the quality of the brakes or the gas pedal on a car don't matter, because people don't know how to drive anyway.

Maybe I overreacted a bit, and I apologize for that.

---

### Post by paydaydaddy on 2010-02-07
It certainly is possible, and even probable that there are apps out there that have been deliberately constructed as to compromise a naive or reckless user's computer. That is why it is recommended that apps should come from the official repositories. When installing a tarball (for example) from an outside source it is essential to consider the source and know the potential risk. You know that your toyota may have a sticky accelerator but you can choose to drive it anyway. A fix is offered at the toyota dealership but you may choose to have your psychotic, alcoholic, tweeker brother-in-law shyster mechanic do the work. Whatever the decision you, as the driver, are an integral part of the outcome.

---

### Post by cammin on 2010-02-07
> **BuffaloX said:**
> It's an analogy.
Each and every time someone ask a security question on these forums, someone has to enter the argument that security doesn't matter, because people are so stupid they are much more likely to infect their system by bad practices.

By the same logic, the quality of the brakes or the gas pedal on a car don't matter, because people don't know how to drive anyway.

Maybe I overreacted a bit, and I apologize for that.

The throttle can stick or the brakes can fail regardless of if they're known to be bad.
Since the scale of the problem doesn't matter to you, (or else the original security argument would have made sense) Toyota's gas pedal problems have no bearing on overall security.

---

### Post by earthpigg on 2010-02-07
> **JDShu said:**
> Time and place matter. *On this forum* it means **[this]("http://catb.org/%7Eesr/faqs/hacker-howto.html#what_is")**.

well, by not using the term at all i thought i could avoid argument about it.

like many words in English, it has multiple definitions. all valid.


> No. The only difference is not who lines their pockets (they both line their own pockets), but how they line their pockets. Firstly, the bad guys do it illegally and without your permission, while auditors do it legally and with your permission. Secondly, the bad guys do it by selling or otherwise exploiting your valuable information unlawfully, while auditors get paid for legitimate services.

laws and permission don't matter when your kids are hungry.

furthermore, laws aren't identical across the planet. do you think Castro's regime is likely to prosecute someone for identity theft of an American, and then selling that identity to another American? ***all*** forms of trade with the US are 'illegal' according to the US...

and a Georgian violating the computer security of a Russian around, say, August of 2009? he is no bad guy, he is a national hero to Georgia, and disrupting the enemy economy without directly causing death is certainly allowed by any and all relevant laws of war.

legality and morality are not relevant to any technical discussion, because they aren't uniform.

---

### Post by doorknob60 on 2010-02-07
Yeah, but other can people can also look at the code and report bugs and security issues, evening things out, if not making it more secure than closed source software.

---

### Post by Warpnow on 2010-02-07
> **Sporkman said:**
> Nope. Language changes, and popular usage dictates the current state of the language and the meaning of words.

Today, "hacker" means a person who attempts to gain unauthorized access to computer systems. It may not have meant that *before*, but it means that *now*.

Have a nice day. :)

Not really. The meaning of words is dependent upon the social groups using those words. Language is not static, nor is it democratic. It changes from location to location, group to group.

To the uninformed, ignorant, technologically illiterate, "hacker" means what you think.

However, to those who know better, it means something entirely. Neither is right, neither is wrong. Language is adaptive, and largely dependent upon the social network (real ones not websites) they are used in. Lawyers, Doctors, and any specialized field have words they use in specific ways.

In Finance, Capital refers to money. In economics, it refers to production capacity. Word change. To a computer literate member of the free software movement, hacker has a legitimate non-malignant meaning. To others, it does not. This does not make either meaning wrong.

---

### Post by Sporkman on 2010-02-07
> **Warpnow said:**
> To the uninformed, ignorant, technologically illiterate, "hacker" means what you think.

But I am informed, non-ignorant, and technologically literate. How do you explain that?

According to your "different groups can have their own language" theory, then, it wouldn't make sense for that group who (wrongly) thinks "hacker" should be replaced with the word "cracker" to go around correcting people, right? After all, the cracker group has their own special language where cracker does not mean unleavened bread nor poor white southerner. Why would they wish to impose their language upon others?

---

### Post by Blacklightbulb on 2010-02-07
> **Sporkman said:**
> Nope. Language changes, and popular usage dictates the current state of the language and the meaning of words.

Today, "hacker" means a person who attempts to gain unauthorized access to computer systems. It may not have meant that *before*, but it means that *now*.

Have a nice day. :)

But me and I'm sure a lot of guys in here don't care about what the rest of the world think. That's what's right and that's what we intend.

I mean, how would I distinguish between a guy who can hack some Assembly,C code and some one who programs (scripts ?) something in HTML5??

---

### Post by Warpnow on 2010-02-08
> **Sporkman said:**
> But I am informed, non-ignorant, and technologically literate. How do you explain that?

According to your "different groups can have their own language" theory, then, it wouldn't make sense for that group who (wrongly) thinks "hacker" should be replaced with the word "cracker" to go around correcting people, right? After all, the cracker group has their own special language where cracker does not mean unleavened bread nor poor white southerner. Why would they wish to impose their language upon others?

You happen to be hanging out in one group, and using the language of another. Don't be surprised when you meet resistance.

---

