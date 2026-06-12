---
title: "Brad Spengler and the Linux kernel"
date: 2010-08-10
forum: Security
---

### Post by witeshark17 on 2010-08-10
What is the general opinion on this [ article from esecurityplanet?]("http://www.esecurityplanet.com/features/article.php/3897711/LinuxCon-Exploits-Show-Why-Linux-Is-Vulnerable.htm")

---

### Post by OpSecShellshock on 2010-08-10
It's not really a matter of opinion. It's true that public exploits are necessary sometimes in order to spur fixes. It's also true that making memory access less predictable would make it more difficult to follow exploits up with arbitrary code executions.

Of course, it's still kind of abstract for the most part. Nobody's actually using exploits of this nature in actual crime as far as anyone knows. There isn't much value in it. I also don't think anyone makes the argument that Linux is perfectly secure, either. It would be a misconception if anyone really held it.

It's a good point about relying too much on access controls, but I'm not familiar with the exploits that supposedly go around them. Luckily not every exploit works remotely.

---

### Post by witeshark17 on 2010-08-11
> **OpSecShellshock said:**
> It's not really a matter of opinion. It's true that public exploits are necessary sometimes in order to spur fixes. It's also true that making memory access less predictable would make it more difficult to follow exploits up with arbitrary code executions.

Of course, it's still kind of abstract for the most part. Nobody's actually using exploits of this nature in actual crime as far as anyone knows. There isn't much value in it. I also don't think anyone makes the argument that Linux is perfectly secure, either. It would be a misconception if anyone really held it.

It's a good point about relying too much on access controls, but I'm not familiar with the exploits that supposedly go around them. Luckily not every exploit works remotely. Makes sense, and all concerns here seem quite addressable...

---

### Post by wacky_sung on 2010-08-11
> **witeshark17 said:**
> Makes sense, and all concerns here seem quite addressable...
To be exact,this is created by man and solved within themselves.It good to have exploits being made publicity that it force the affected company to come out with a patch to it asap.   

In fact, there are still exploits around went unreported which often used by malicious people.

---

### Post by rookcifer on 2010-08-11
> **witeshark17 said:**
> What is the general opinion on this [ article from esecurityplanet?]("http://www.esecurityplanet.com/features/article.php/3897711/LinuxCon-Exploits-Show-Why-Linux-Is-Vulnerable.htm")

If Spengler speaks, anyone involved with Linux security should listen.  The guy is an exploit finding phenom as well as one of the developers of grsecurity (a MAC system like SELinux and AppArmor).  He has released more than one exploit which is able to completely bypass SELinux (even though these exploits typically require a local user).  When it comes to the internals of access controls, there aren't many people with better credentials than him.

Here is [one example]("http://www.youtube.com/watch?v=KvREwhfQmbc") of him exploiting SELinux.  (He has a YouTube channel with numerous videos).

---

### Post by OpSecShellshock on 2010-08-11
I'd also say this: blaming the researchers when a vulnerability is discovered is a very bad move. On the other hand, so is the common phenomenon of tech journalists overstating the risks when they get discovered (for every Spengler there needs to be a Schneier, if you will). Trying to hide the problem doesn't help anyone, including developers, and it reeks of calculated misdirection to focus on the researchers instead of the patches.

---

### Post by Bachstelze on 2010-08-11
> **OpSecShellshock said:**
> (for every Spengler there needs to be a Schneier, if you will)

Pardon?

---

### Post by witeshark17 on 2010-08-11
I have an idea that among the suggetions, making some kernel items *read only* is excellent and likely to appear soon.

---

### Post by bodhi.zazen on 2010-08-11
Anyone who claims Linux is somehow invulnerable does not know much about security and you should not get security information from such people.

With that said, for the average desktop user coming from a Microsoft product, Linux is a breath  of fresh air and a relief.

What the article points out, IMO, is that Linux is designed from the ground up to be secure. The vast majority of "exploits" are potential cracks that have not yet been leveraged by crackers. So while there are exceptions to this rule, in general, IN Linux, flaws in the code are identified and patched BEFORE they are exploited and these potential exploits, in general, do not result in compromised systems.

Many people falsely expound that Linux security is somehow biased on obscurity or that Linux owns a small market share. While there is no doubt those are (minor) factors, Linux security is in fact much more proactive.

With Windows, the code is not available for review, so the number of potential exploits is unknown. Since the code is not available for review, flaws in the code are reported as a result of successful exploits. For example, flaws in windows are often reported as wide spread viruses or worms resulting in countless compromised systems. After the fact, more often then not, windows users rely on a third party to fix or remove the virus or worm (rather then Microsoft patching the code).

Windows security is much more reactive, after the damage has occurred.

Take care, there are exceptions to those guidelines.

By far and away the most common causes of security problems in Linux come from VNC or SSH servers with weak passwords or occasional social engineering (if anyone recalls the recent Gnome Look incident). Actual exploitation of flaws in the code is rare.

---

### Post by OpSecShellshock on 2010-08-11
> **Bachstelze said:**
> Pardon?

Ah, to clarify: what I meant was that there are certain tendencies in tech press, particularly surrounding security issues, that end up leading people to unfortunate conclusions through no fault of the researcher's. One of them is the constant need to set up and knock down the "Linux-is-secure" straw-ware.  Another is to immediately take a flaw's description to the worst thing that could possibly happen, without regard for how unlikely it is to happen (not saying the linked article does that, mind). That's where, to my mind, someone like Bruce Schneier can provide a good deal of clarity and value. He tends to advise against going into a panic over abstract (or completely imaginary) threats and instead suggests keeping the focus on things that are actually happening or likely to happen.

In the case of these kernel flaws, they don't seem to provide much additional risk on top of the general risks associated with legitimate local user access or with physical access in and of itself. We are still, thankfully, at a point where having to put your hands on the system itself is a greater risk to the intruder than to the owner. Migrating your processing power and storage off-site and putting it in the hands of a third party alters that dynamic, but we can't talk about those risks because it's the future and everything (but that's off-topic anyway).

Point is that not every new exploit represents a true net increase in risk, and it's important that someone mention that whenever other security-minded people start talking about vulnerabilities.

It's like all those articles from this past weekend about how "private mode in browsers isn't really private" with links to a study from Stanford's computer science people. First of all, the browsers themselves tell you that. Second, the articles are from last weekend, but the date on the university paper is July, 2009. The date was not mentioned in any of the articles I read, and the current versions of most of the browsers have changed since then. Also, the browser add-ons chosen in some cases seemed either arbitrary or incomplete. The main point remains true, but I wasn't aware that anyone thought otherwise.

---

### Post by rookcifer on 2010-08-11
> **OpSecShellshock said:**
> Ah, to clarify: what I meant was that there are certain tendencies in tech press, particularly surrounding security issues, that end up leading people to unfortunate conclusions through no fault of the researcher's. One of them is the constant need to set up and knock down the "Linux-is-secure" straw-ware.  Another is to immediately take a flaw's description to the worst thing that could possibly happen, without regard for how unlikely it is to happen (not saying the linked article does that, mind). That's where, to my mind, someone like Bruce Schneier can provide a good deal of clarity and value. He tends to advise against going into a panic over abstract (or completely imaginary) threats and instead suggests keeping the focus on things that are actually happening or likely to happen.

Yeah, but Schneier's area of real expertise is in cryptography.  He isn't up there with people like Spengler when it comes to Linux kernel internals and access controls, etc.  But I understand your point and agree with it.

---

### Post by tomdkat on 2010-08-11
Thanks for the link!  I had not heard of Brad Spengler before and I just finished reading a great interview with him.  :)

Peace...

---

### Post by spender_grsec on 2010-08-12
Hi guys,

I noticed this discussion about my recent presentation and thought I'd pop in to answer any questions you have.

I agree with the one poster's view of security journalists.  I've updated the article with my comments, concerns, and a link to the actual presentation.

As for whether local kernel exploits are a viable threat or not, do a google search for:
index of wunderbar_emporium

To someone not heavily involved in security, it may seem that local kernel exploits aren't a threat, but remember that it only takes one client-side vulnerability or a vulnerability in a webserver's php script, etc for a remote user to become a local user.

Of timely note is the fact that the recent iPhone jailbreak, where one only had to visit a website with their iPhone to have it completely compromised, was a combination of a remote vulnerability with a local kernel exploit as a return-oriented payload.

Finally, on the topic of Linux security I'd like to mention two things. It's important to recognize the motivations for public and/or wide-spread exploits.  As I mention in my presentation, the absence of public exploits doesn't necessarily mean a particular OS is secure.  As for where some of those touted security features of Linux came from, we created this illustration some time ago:
[http://grsecurity.net/~spender/grsecurity_pax-influence.png]("http://grsecurity.net/%7Espender/grsecurity_pax-influence.png")

Those are the only comments I have for now.  The direct link to the presentation is:
[http://grsecurity.net/spender_summit.pdf](http://grsecurity.net/spender_summit.pdf)
and again, feel free to ask me questions.

-Brad

---

### Post by bodhi.zazen on 2010-08-12
> **spender_grsec said:**
> Hi guys,

I noticed this discussion about my recent presentation and thought I'd pop in to answer any questions you have.

Brad - Thank you for taking the time to post in this thread, we are honored. And thank you for your cautions, I agree many users, across many OS, take security for granted.

---

### Post by witeshark17 on 2010-08-12
Yeah +1 very honored! I really enjoy the open nature of Linux discussion and development. Thanks for the visit and post! :popcorn:

---

### Post by spender_grsec on 2010-08-13
No questions? ;) Then I'll post some more relevant reading material from the recent BlackHat/Defcon conferences:

[http://downloads.unrevoked.com/defcon-talk.pdf](http://downloads.unrevoked.com/defcon-talk.pdf)
Joshua Wise took a vulnerability present from 2.6.18 to 2.6.33 in the bluetooth code.  The CVE description called it a denial-of-service only.  He turned it into a reliable local privilege escalation vulnerability, abusing one of the things mentioned in my presentation that Linux should protect against that it currently doesn't -- in this case, the fact that clobbering a function pointer with ASCII text not under his control would produce a userland address which would be under his control.  So he was able to place his kernel payload at that address and completely compromise the system.  It's exactly these kinds of methods that PAX_KERNEXEC/PAX_UDEREF mentioned in the presentation prevent.

Presented at CanSecWest/BlackHat by Julien Tinnes and Tavis Ormandy was:
[http://blog.cr0.org/2010/03/theres-party-at-ring0-and-youre-invited.html](http://blog.cr0.org/2010/03/theres-party-at-ring0-and-youre-invited.html)
[https://media.blackhat.com/bh-us-10/presentations/Tinnes_Ormandy/BlackHat-USA-2010-Tinnes-PartyRing0-slides.pdf](https://media.blackhat.com/bh-us-10/presentations/Tinnes_Ormandy/BlackHat-USA-2010-Tinnes-PartyRing0-slides.pdf)

I'm told the slides aren't the same as the ones that were presented (they're a few months old and so are missing some 64bit advances we've made), but it's a really nice albeit very technical discussion of a large swath of kernel vulnerabilities they discovered on both Windows and Linux.  Their conclusion (slide 56) matches what I talked about in my presentation.

-Brad

---

### Post by witeshark17 on 2010-08-13
One question, how many of your recommendations are implemented as the kernel is decribed in [ in this Intenet news article?](http://blog.internetnews.com/skerner/2010/08/linux-kernel-report-shows-lots.html)

---

### Post by rookcifer on 2010-08-13
> **spender_grsec said:**
> No questions? ;) 

Yes.  Where can one get a 64 bit version of paxtest?  I would be curious to run it against the default Ubuntu kernel to see how the built-in ASLR/NX/RELRO stuff fares.

---

### Post by spender_grsec on 2010-08-14
[http://grsecurity.net/~spender/paxtest-0.9.9.tgz]("http://grsecurity.net/%7Espender/paxtest-0.9.9.tgz")

It has 32/64bit x86, PPC, and SPARC support ;)
just run 'make linux64'

-Brad

---

### Post by spender_grsec on 2010-08-14
witeshark: other than what's already been implemented (see the influence .png I posted) there's been nothing new recently.

The  security summit I attended was very SELinux-focused, which is why I  made some specific points in my presentation about zooming out a bit,  seeing the big picture, and putting some effort into plugging up some  weaknesses in the system in a generic way.  If you look back five or six  years to what was being discussed at these summits, the topics were  very diverse.  A possible explanation is that the current people  involved in security are software developers/engineers just working on  security, not actual security people plucked from the industry.  So they  don't have the kind of connections or experience to spot trends and  know how to react to them.  If you don't actually write exploits and try  to see how to break the system, or know how others are breaking the  system, it's easy to get stuck in the niche of access control where you  can deal with theoretical attackers and theoretical attacks all day.

There's  also considerable commercial interest in access control, particularly  for SELinux but it exists to a lesser extent with some others as well.   There's an entire company, Tresys, which is mostly based around  SELinux.  They develop the reference policy used by distributions and  position themselves as "the experts" on SELinux.  Red Hat has also  invested considerable time/money into SELinux, so it was no surprise to  see these two groups being very defensive of SELinux at the security  summit.  Tresys was walking the fine line of saying how easy SELinux was  (so that people use it) while at the same time saying that people are  too dumb to write their own policies, and shouldn't write them (so  Tresys will write them of course).  There was a presentation done by a  PhD candidate on the usability of SELinux, AppArmor, and an access  control system he developed himself.  Of course, his own system came out  on top (I expect this from academic research ;)) but I found the  findings to be quite useful, even as someone who's written an access  control system he didn't study.  The SELinux folks got very defensive at  the fact that SELinux ended up with the worst scores in the study and  got into a very heated debate claiming that the presenter was testing  the wrong thing.  So I don't know if they'll be implementing any of the  useful suggestions.  I didn't notice any of that defensiveness from the  two Ubuntu AppArmor guys present.  The study showed that there was a lot  of promise for AppArmor if the suggestions were implemented,  specifically some things in the interface to help inform the user about  the severity and reason for a particular denial, so the user doesn't get  into the habit of allowing everything.

The speed of kernel  development can be very swift in some cases and very slow and painful in  others.  Security is far over on the slow and painful side ;)  Kees  Cook (one of your Ubuntu security guys) actually has been pushing hard  recently to get some optional security features merged into the kernel.   It's things you already have in Ubuntu, but he wants to see everyone  using Linux benefit from the features.  If you want to see some sad  entertainment, you should read the threads: it's rather Kafka-esque.   The developers tell Kees he needs to write the features a certain way or  they have no chance of going in, then they tell him that's all wrong  and he needs to write it this other way or it has no chance of going in,  then they tell him that's wrong and that he needs to rewrite it as the  way he had it written originally, then some important kernel developer  mails the security maintainer off-list and tells him to reject the  feature.

So if you happen to talk to Kees, tell him thanks for  his hard work.  The kernel mailing list can be a pretty  abusive/frustrating place.  The irony being that as Kees keeps trying to  get the code added in some form they'll accept, there's claims made by  the kernel developers that Canonical never contributes any code to the  kernel.  Development is done by people after all, so you see the same  kind of petty politics and NIH syndrome you see in any other kind of  group.

Upstream kernel development is pretty anti-security  actually, as even the security maintainer James Morris noted at the  summit.  It was also unfortunate that all of the other kernel developers  (who often voice their opinions on LKML and reject security patches)  didn't attend any of the security summit.  If you followed the events of  a few years ago, there was the issue of the official written policy of  the Linux kernel on the handling of security vulnerabilities: "to fully  disclose them as soon as possible" which ended up being completely  different from the effective policy, which was just to fix the bug and  not tell anyone about the security implications, even if it was known by  the committer.  This is quite dangerous for the distributions because  it unnecessarily wastes time and duplicates effort and makes it more  difficult to determine the important fixes that need to be backported to  vendor kernels.  As noted above, it's difficult to get security  features into the kernel that don't involve access control (and even in  the case of access control one might have to fight for months or more,  like in the case of AppArmor).  This may have the effect that the  security improvements will be seen in individual distributions instead.

So  to answer your question: nothing yet; you'll have to wait a (long)  while to see.  Why do you think I called the presentation "Linux  Security in 10 Years"? ;)

-Brad

---

### Post by spender_grsec on 2010-08-14
rookcifer: there's another nice tool for checking the security of userland on your system:
[http://www.trapkit.de/tools/checksec.html](http://www.trapkit.de/tools/checksec.html)

It checks for SSP/PIE/RELRO/etc on individual binaries or system-wide.

There was also an informative study done on the use of these protections here:
[http://labs.mwrinfosecurity.com/notices/security_mechanisms_in_linux_environment__part_1___userspace_memory_protection/](http://labs.mwrinfosecurity.com/notices/security_mechanisms_in_linux_environment__part_1___userspace_memory_protection/)

-Brad

---

### Post by witeshark17 on 2010-08-14
> **spender_grsec said:**
> witeshark: other than what's already been implemented (see the influence .png I posted) there's been nothing new recently.

 There was a presentation done by a  PhD candidate on the usability of SELinux, AppArmor, and an access  control system he developed himself.  Of course, his own system came out  on top (I expect this from academic research ;)) but I found the  findings to be quite useful, even as someone who's written an access  control system he didn't study.  The SELinux folks got very defensive at  the fact that SELinux ended up with the worst scores in the study and  got into a very heated debate claiming that the presenter was testing  the wrong thing.  So I don't know if they'll be implementing any of the  useful suggestions.  I didn't notice any of that defensiveness from the  two Ubuntu AppArmor guys present.  The study showed that there was a lot  of promise for AppArmor if the suggestions were implemented,  specifically some things in the interface to help inform the user about  the severity and reason for a particular denial, so the user doesn't get  into the habit of allowing everything.

The speed of kernel  development can be very swift in some cases and very slow and painful in  others.  Security is far over on the slow and painful side ;)  Kees  Cook (one of your Ubuntu security guys) actually has been pushing hard  recently to get some optional security features merged into the kernel.   It's things you already have in Ubuntu, but he wants to see everyone  using Linux benefit from the features.  If you want to see some sad  entertainment, you should read the threads: it's rather Kafka-esque.   **The developers tell Kees he needs to write the features a certain way or  they have no chance of going in, then they tell him that's all wrong  and he needs to write it this other way or it has no chance of going in,  then they tell him that's wrong and that he needs to rewrite it as the  way he had it written originally, then some important kernel developer  mails the security maintainer off-list and tells him to reject the  feature.**

So if you happen to talk to Kees, tell him thanks for  his hard work.  The kernel mailing list can be a pretty  abusive/frustrating place.  The irony being that as Kees keeps trying to  get the code added in some form they'll accept, there's claims made by  the kernel developers that Canonical never contributes any code to the  kernel.  Development is done by people after all, so you see the same  kind of petty politics and NIH syndrome you see in any other kind of  group.

Upstream kernel development is pretty anti-security  actually, as even the security maintainer James Morris noted at the  summit.  It was also unfortunate that all of the other kernel developers  (who often voice their opinions on LKML and reject security patches)  didn't attend any of the security summit.  If you followed the events of  a few years ago, there was the issue of the official written policy of  the Linux kernel on the handling of security vulnerabilities: "to fully  disclose them as soon as possible" which ended up being completely  different from the effective policy, which was just to fix the bug and  not tell anyone about the security implications, even if it was known by  the committer.  This is quite dangerous for the distributions because  it unnecessarily wastes time and duplicates effort and makes it more  difficult to determine the important fixes that need to be backported to  vendor kernels.  As noted above, it's difficult to get security  features into the kernel that don't involve access control (and even in  the case of access control one might have to fight for months or more,  like in the case of AppArmor).  This may have the effect that the  security improvements will be seen in individual distributions instead.

So  to answer your question: nothing yet; you'll have to wait a (long)  while to see.  Why do you think I called the presentation "Linux  Security in 10 Years"? ;)

-Brad So very nice to know! I was less than as aware as I'd like to be about how complicated the involvement of so many can interfere with progress and results. Since any more remarks here will tend to repeat things already posted, I'll end this post with a big thanks to Kees :)

---

### Post by OpSecShellshock on 2010-08-14
Wow, so it seems to me that security testing and fixing in kernel space is quite similar to anti-malware testing inasmuch as the parties whose work is being tested want to be able to define what a "legitimate" test is in the first place. That's unfortunate.

---

### Post by spender_grsec on 2010-08-14
shellshock: I'm not sure that was entirely the case here.  Red Hat would  like users of SELinux to basically use/trust the policies given to them  based off the ones from Tresys, only making minor changes in response  to setroubleshoot etc.  On the other hand, there are of course cases  where this is impossible (as there can't already exist a reference  policy for software or webapp your company is creating), so the  usability criticisms are valid in that smaller case, even if it's not  the primary way the system is intended to be used.  If the answer to  that problem though is to pay a company (it seemed to be suggested),  that's a broken system in my opinion.

Where it definitely is the  case is in the case of kernel exploitation.  It's the 500 pound gorilla  in the room; they hate to talk about it (none of them  commented/questioned during my presentation) because it ruins the  selling points for the system.  The security models used by SELinux have  their roots in military-funded research done by academia (and the  military itself), based off models created before the Internet even  existed, when the threats weren't funded/determined attackers but rather  clumsy administrators.

In philosophy, arguments are judged by  validity and soundness.  SELinux may in fact be a valid security model  (it was the job of the NSA/academia to prove that), meaning that given a  set of assumptions, apply some logic, and the conclusion follows  correctly from it.  The conclusion here in this context is "process  apache running at classification Top Secret can't divulge information to  process cat running at classification Secret".  The problem we run into  is when evaluating the soundness of the argument: are the premises, the  assumptions true?  They all have to be true for the argument to be  sound.  If it's unsound, then the benefit of the security model is  questionable.

An example of a valid but unsound argument: All  things made of electronics are secure.  A computer is made of  electronics.  Therefore, all computers are secure.  Obviously this is  false, and the problem is with the first assumption.

So if we  look at the assumptions of these old security models, again remembering  they were created before the Internet existed (and you can read about  the assumptions in the LSPP, the protection profile SELinux and other  access control systems are written to) you see a number of dubious  assumptions.  Among them:
The administrator is competent
The OS kernel is assumed to be trusted (it's part of what's called the TCB, trusted computing base)
All machines connected to the protected system use the same security system
(there are many others, like claiming the security system can detect itself being compromised, etc)

Right  off the bat, if the machine is connected to the Internet or virtually  any other network, it fails a major assumption, so we're already  operating under conditions not anticipated/handled by the authors of the  security model.
The implications of the kernel being in the TCB is  what I talked about in my presentation.  Because the kernel is far from  trusted, and trends show that it's becoming easier to compromise it  instead of some other userland application which does currently have  some protections applied to it, then the security model is unsound.

So it's something I complain about a lot because, because the claim of:
"process apache running at classification Top Secret can't divulge information to process cat running at classification Secret"
is  not only utterly false, but deceitful, and more importantly,  potentially dangerous.  People are unfortunately buying into the  snake-oil and replacing physical air-gaps with virtual wooden bridges  (to use the phrase from Kostya Kortchinsky's VMWare breakout exploit  called CLOUDBURST), putting the security of their data at risk at the  potential to save some money.  If the information you're trying to  protect isn't that important, this isn't a big deal.  But if you're  dealing with highly sensitive, highly valuable information that  attackers with plenty of time and money want to get their hands on, then  it's a big problem.

Some examples:
[http://onepeople.org/node/2268](http://onepeople.org/node/2268)
[http://magazine.redhat.com/2007/05/04/whats-new-in-selinux-for-red-hat-enterprise-linux-5/](http://magazine.redhat.com/2007/05/04/whats-new-in-selinux-for-red-hat-enterprise-linux-5/)
[http://press.redhat.com/2010/08/11/red-hat-enterprise-linux-6-kvm-to-pursue-security-certification/](http://press.redhat.com/2010/08/11/red-hat-enterprise-linux-6-kvm-to-pursue-security-certification/)

> By pursuing this new certification, we’re adding to our leadership in  this area and giving customers in security-sensitive environments, such  as government agencies and financial services organizations, added  confidence that our solutions meet their strict security requirements.In contrast, on our Wiki we state up-front the real-life limitations of our access control system:
[http://en.wikibooks.org/wiki/Grsecurity/The_RBAC_System#Limitations_of_any_Access_Control_System](http://en.wikibooks.org/wiki/Grsecurity/The_RBAC_System#Limitations_of_any_Access_Control_System)

but that's probably because we're not trying to fool anybody so we can acquire lucrative government contracts ;)

So  last year I demonstrated that the response to kernel exploits can't be  "that's not in our threat model" because it means that real life, a bored  attacker with an hour of time to write a kernel exploit, isn't in the  threat model of a security system so fine-grained and complex that the  people pushing it say their users are too dumb to write their own  policies for it.  It's a real problem that needs to be addressed with  actual work and code, instead of hand-waving and appeals to expert  opinion (see: [http://www.dougwalton.ca/papers in pdf/2002Reed.pdf]("http://www.dougwalton.ca/papers%20in%20pdf/2002Reed.pdf")).

-Brad

---

### Post by witeshark17 on 2010-08-14
> **spender_grsec said:**
> shellshock: I'm not sure that was entirely the case here.  Red Hat would  like users of SELinux to basically use/trust the policies given to them  based off the ones from Tresys, only making minor changes in response  to setroubleshoot etc.  On the other hand, there are of course cases  where this is impossible (as there can't already exist a reference  policy for software or webapp your company is creating), so the  usability criticisms are valid in that smaller case, even if it's not  the primary way the system is intended to be used.  If the answer to  that problem though is to pay a company (it seemed to be suggested),  that's a broken system in my opinion.

Where it definitely is the  case is in the case of kernel exploitation.  It's the 500 pound gorilla  in the room; they hate to talk about it (none of them  commented/questioned during my presentation) because it ruins the  selling points for the system.  The security models used by SELinux have  their roots in military-funded research done by academia (and the  military itself), based off models created before the Internet even  existed, when the threats weren't funded/determined attackers but rather  clumsy administrators.

In philosophy, arguments are judged by  validity and soundness.  SELinux may in fact be a valid security model  (it was the job of the NSA/academia to prove that), meaning that given a  set of assumptions, apply some logic, and the conclusion follows  correctly from it.  The conclusion here in this context is "process  apache running at classification Top Secret can't divulge information to  process cat running at classification Secret".  The problem we run into  is when evaluating the soundness of the argument: are the premises, the  assumptions true?  They all have to be true for the argument to be  sound.  If it's unsound, then the benefit of the security model is  questionable.

An example of a valid but unsound argument: All  things made of electronics are secure.  A computer is made of  electronics.  Therefore, all computers are secure.  Obviously this is  false, and the problem is with the first assumption.

So if we  look at the assumptions of these old security models, again remembering  they were created before the Internet existed (and you can read about  the assumptions in the LSPP, the protection profile SELinux and other  access control systems are written to) you see a number of dubious  assumptions.  Among them:
The administrator is competent
The OS kernel is assumed to be trusted (it's part of what's called the TCB, trusted computing base)
All machines connected to the protected system use the same security system
(there are many others, like claiming the security system can detect itself being compromised, etc)

Right  off the bat, if the machine is connected to the Internet or virtually  any other network, it fails a major assumption, so we're already  operating under conditions not anticipated/handled by the authors of the  security model.
The implications of the kernel being in the TCB is  what I talked about in my presentation.  Because the kernel is far from  trusted, and trends show that it's becoming easier to compromise it  instead of some other userland application which does currently have  some protections applied to it, then the security model is unsound.

So it's something I complain about a lot because, because the claim of:
"process apache running at classification Top Secret can't divulge information to process cat running at classification Secret"
is  not only utterly false, but deceitful, and more importantly,  potentially dangerous.  People are unfortunately buying into the  snake-oil and replacing physical air-gaps with virtual wooden bridges  (to use the phrase from Kostya Kortchinsky's VMWare breakout exploit  called CLOUDBURST), putting the security of their data at risk at the  potential to save some money.  If the information you're trying to  protect isn't that important, this isn't a big deal.  But if you're  dealing with highly sensitive, highly valuable information that  attackers with plenty of time and money want to get their hands on, then  it's a big problem.

Some examples:
[http://onepeople.org/node/2268](http://onepeople.org/node/2268)
[http://magazine.redhat.com/2007/05/04/whats-new-in-selinux-for-red-hat-enterprise-linux-5/](http://magazine.redhat.com/2007/05/04/whats-new-in-selinux-for-red-hat-enterprise-linux-5/)
[http://press.redhat.com/2010/08/11/red-hat-enterprise-linux-6-kvm-to-pursue-security-certification/](http://press.redhat.com/2010/08/11/red-hat-enterprise-linux-6-kvm-to-pursue-security-certification/)

In contrast, on our Wiki we state up-front the real-life limitations of our access control system:
[http://en.wikibooks.org/wiki/Grsecurity/The_RBAC_System#Limitations_of_any_Access_Control_System](http://en.wikibooks.org/wiki/Grsecurity/The_RBAC_System#Limitations_of_any_Access_Control_System)

but that's probably because we're not trying to fool anybody so we can acquire lucrative government contracts ;)

**So  last year I demonstrated that the response to kernel exploits can't be  "that's not in our threat model" because it means that real life, a bored  attacker with an hour of time to write a kernel exploit, isn't in the  threat model of a security system so fine-grained and complex that the  people pushing it say their users are too dumb to write their own  policies for it.  It's a real problem that needs to be addressed with  actual work and code, instead of hand-waving and appeals to expert  opinion (see: [http://www.dougwalton.ca/papers in pdf/2002Reed.pdf]("http://www.dougwalton.ca/papers%20in%20pdf/2002Reed.pdf")).**

-Brad Some peoples' sense of logic just *isn't!* Let's keep it short; all these organizations should just put you in charge.

---

### Post by earthpigg on 2010-08-14
Very interesting reading. Thank you for participating, Brad.

What's your take on binary blobs?

I'm assuming you do at least part of your work to find vulnerabilities by evaluating code, looking at how things work, and whatnot. That can't really be done with 1s and 0s, so one must rely on observing the blob working, and looking for oddities.

But, that would not address the possibility of malicious code that's been intentionally submitted to the kernel. Perhaps by a not-such-a-good-guy working for one of the companies that submits these blobs (maybe he was bribed, maybe he doesn't want his wife to see a video of something bad he's done, etc... many ways that people get turned.). 

The code could simply be dormant until such time as our hypothetical bad guy decides it ought to do things. Sleeping botnet type thing, that just waits for a message from the outside. One would then be able to observe oddities, but it would be to late.

I'll admit that I'm in a bit over my head with this discussion.

---

### Post by spender_grsec on 2010-08-14
Hi earthpigg,

Regarding binary blobs, I'll say this:

It depends on what exactly we refer to when we use this term, but in  general, they're not blobs at all.  At the lowest level, yes they're 1s  and 0s, but they're also a set of processor instructions and data that  can be analyzed, disassembled, decompiled into C-like pseudo-code, etc.   It's a different skill set, but one that many people possess, and there  exist many tools to help in the process.  One of these is probably  installed on your system right now: run objdump -d /bin/ls and you'll  see a disassembly of the code of the ls binary.

It's an important skill to have, especially for debugging purposes.   Recently there was an issue with paxtest reporting "Vulnerable" for a  particular test on a system with gcc 4.5.  On an identical system with  gcc 4.3, the test functioned properly and reported that it was killed.   By disassembling the binary used for the test, I found that gcc 4.5 had  optimized out the crucial instruction involved in the test.

Much of the Windows vulnerability research is done in this way, as the  researchers don't have access to the source code of Microsoft or Adobe,  for example.  It is true though that there's a lot of dynamic  vulnerability finding being done through fuzzing.  Usually the fuzzing  is followed up with some static analysis to determine if the crash  produced is exploitable or not.

But binary blobs can refer to things other than applications/kernel  modules that we don't have the source to: BIOS and firmware for example.

In the BIOS case, it's still code/data, though there are a few more  steps to get at it (it's compressed) and interpreting the code requires  some more specialized knowledge.

For firmware it's a little trickier, not so much because we don't know  what the blob is, but more because we don't necessarily know how the  hardware interprets the blob.  It can include some code for whatever  processor is used on the device (maybe MIPS or some other embedded  processor) or some data that will be interpreted specially by the  device.  There are people that can analyze this too, though the higher  we go in complexity the fewer qualified people there are to analyze it.   The question becomes how that can be accomplished in a way that does  something desirable to the attacker, and in a way that will be difficult  to detect.

There's also the case of binary blob kernel drivers that interface with  some hardware.  Again, the possibility exists for a backdoor, but if the  blob involves some code that runs within the kernel, then it's at least  interfacing with something that's known pretty well (the processor  architecture of your computer).  To advance the free-software effort,  some have reverse engineered these blobs (or inferred their contents by  observing output based on some crafted input) to provide open-sourced  drivers:
[http://kerneltrap.org/node/6497](http://kerneltrap.org/node/6497)
[http://nouveau.freedesktop.org/wiki/FAQ](http://nouveau.freedesktop.org/wiki/FAQ)

The more likely threat is attackers that understand the details of the  firmware and modify it as part of an exploit.  At the 2009 Black Hat  conference, there was a demonstration of a keylogger injected into the  firmware of a Mac keyboard:
[http://www.blackhat.com/presentations/bh-usa-09/CHEN/BHUSA09-Chen-RevAppleFirm-PAPER.pdf](http://www.blackhat.com/presentations/bh-usa-09/CHEN/BHUSA09-Chen-RevAppleFirm-PAPER.pdf)

If there's some dormant backdoor functionality, either it will be woken  up for a particular target, or it'll be activated for everyone.  The  latter case is very likely to be caught, so we're left with the former  case, which IMO is not something people need to worry about (unless  their computer is the key to billions of dollars or something).

If I were to weigh the possibility of something affecting me, I'd be  more worried about the possibility of someone under an assumed name  submitting an innocuous-looking patch to the kernel that contains some  subtle vulnerability the attacker knows how to exploit.  The approach  has plausible deniability as everyone makes mistakes from time-to-time,  and if it's caught it'd be no different than someone exploiting any  other bug in the kernel.  There's an increased threat here because it  doesn't need to be the patch-submitter that exploits the vulnerability:  someone else could spot it too and use it.

Probably it's best not to imagine these scenarios ;)

-Brad

---

### Post by rookcifer on 2010-08-14
> **spender_grsec said:**
> [http://grsecurity.net/~spender/paxtest-0.9.9.tgz]("http://grsecurity.net/%7Espender/paxtest-0.9.9.tgz")

It has 32/64bit x86, PPC, and SPARC support ;)
just run 'make linux64'

-Brad

Thank you.  Here are the results I am getting on Ubuntu Lucid x64:

```
Mode: blackhat
Linux 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

Executable anonymous mapping             : Killed
Executable bss                           : Killed
Executable data                          : Killed
Executable heap                          : Killed
Executable stack                         : Killed
Executable shared library bss            : Killed
Executable shared library data           : Killed
Executable anonymous mapping (mprotect)  : Vulnerable
Executable bss (mprotect)                : Vulnerable
Executable data (mprotect)               : Vulnerable
Executable heap (mprotect)               : Vulnerable
Executable stack (mprotect)              : Vulnerable
Executable shared library bss (mprotect) : Vulnerable
Executable shared library data (mprotect): Vulnerable
Writable text segments                   : Vulnerable
Anonymous mapping randomisation test     : 28 bits (guessed)
Heap randomisation test (ET_EXEC)        : 14 bits (guessed)
Heap randomisation test (PIE)            : 28 bits (guessed)
Main executable randomisation (ET_EXEC)  : No randomisation
Main executable randomisation (PIE)      : 28 bits (guessed)
Shared library randomisation test        : 28 bits (guessed)
Stack randomisation test (SEGMEXEC)      : 28 bits (guessed)
Stack randomisation test (PAGEEXEC)      : 28 bits (guessed)
Return to function (strcpy)              : paxtest: return address contains a NULL byte.
Return to function (memcpy)              : Vulnerable
Return to function (strcpy, PIE)         : paxtest: return address contains a NULL byte.
Return to function (memcpy, PIE)         : Vulnerable
```

28 bits of entropy = 2^28 = 268,435,456 possible addresses. 

I am wondering, Brad, the feasibility of brute-forcing this?  I know 28 bits is nothing when talking about brute forcing crypto algorithms, but is it as easy to brute-force 28 bits of entropy where ASLR is concerned?  A quick google search suggests 16 bits of entropy is trivial but 28 bits is too difficult for brute-forcing.  How true is this now?

---

### Post by earthpigg on 2010-08-14
Thank you for taking the time to respond, Brad. Very informative.

---

### Post by spender_grsec on 2010-08-14
rookcifer:

The answer is: it depends :)

First of all, it may not be necessary to bruteforce anything.  If the bug being exploited allows for the attacker to leak memory/addresses back (this applies to local/remote exploits) or if there exist weaknesses in the OS's ASLR implementation where information is allowed to be leaked locally about the layout of the process' address space, then there's no need to bruteforce.  The same goes for if there's something in the address space that isn't randomized, like if the main executable isn't a PIE binary.  An attacker can use what's now called "return-oriented-programming" to use bits of code in the main executable to perform its malicious operations.  PIE's important because the target always ends up being whatever isn't randomized: no attacker wants to give themselves away by bruteforcing if they can avoid it.  The same thing is being seen in the Windows world: every few months there's a new ASLR "defeat" that basically involves recognizing that Adobe's shipping some DLL with ASLR disabled, or Firefox ships with a DLL with ASLR disabled, etc.

There are also ways to reduce the number of bits that need to be bruteforced.  For instance, if you need an address to a "/bin/sh" string, the OS will also happily accept the string: "////////////////////////////////bin/sh" (you can use up to ~4k /'s) which allows you to shave off about 11 bits or so of that entropy.  This is just one example; there are many others.  Until last year the ASLR used in Linux was trivially bypassed locally.  They used a weak RNG based off time that didn't mix back in any of its output, so for 10ms or so the same randomization would be applied to whatever tasks executed in that period.  The attacker would execute their own binary then immediately execute a suid binary with the now-known randomization.  The article about it was pretty interesting:
[http://sophsec.com/research/aslr_research.html](http://sophsec.com/research/aslr_research.html)

As for time required to bruteforce, I think you probably saw the academic research paper that set up a specialized, almost best-case scenario for bruteforcing and found it to be possible to do very quickly.

Bruteforcing will tend to cause a lot of noise in the logs, as each failed attempt usually crashes the service.  If logging is only done locally, that's of course something an attacker would want to clean up after-the-fact.  This sets some parameters for a successful attack: the attacker will want full control of the system to clean up those logs; they'd also be unlikely to use an 0day against you unless they were confident they could escalate privilege and that you weren't remote logging.

Next question is, the OS is aware and the service itself can be aware that it's crashing many times very quickly; should it really be respawning itself so quickly after it detects this, or if it knows it's a termination from the OS suggesting an attempted exploit, should it be respawning at all?  Taking this route demotes a potential privilege escalation vulnerability to just a simple denial of service.  Personally I'd rather see my webserver stop respawning than see some 'new content' pop up on it.

In Windows this is the case; most Windows services are allowed to crash three times before they're prevented from respawning.  In grsecurity we have an automatic feature that slows down the respawning of a daemon when it's been killed due to an exploit attempt (such that bruteforcing 16 bits would take about 2 weeks I think).  It also has the ability to configure policy so that a daemon or suid binary is allowed to crash x number of times in y amount of time before taking some action (either preventing respawning or kicking that particular user out of the system and keeping them from logging back in for the timeout period).  I don't know if anything equivalent exists for Linux outside of grsecurity, maybe someone else could respond about that.  It was a pretty essential feature for Windows to have because the amount of entropy for their randomized areas is very low (8 bits I think for some areas).  It was always an essential feature for us as well, even though we make use of the highest number of bits of entropy.

Finally I should mention that there are many bugs where the attacker just can't bruteforce.  The term's a bit ambiguous, but we call these 'one-shot' because you only have one shot at compromising the thing ;)  Kernel bugs fall into this category if a failure causes a panic, vulnerabilities in document readers fit the bill (unless you can convince someone to open that document 200 million times ;)) as well as many other client-side vulnerabilities, including those in the browser.  This is why it's so important for ASLR to be used to its full potential for these client applications.

So to answer your question, it can be bypassed completely, be very quick, take a long time (long enough for an admin to notice, hopefully), or be prevented from achieving its full duration.  As with cryptography, implementation matters.  It's certainly the case with ASLR.

As for the 28 bits of entropy, I wouldn't attempt it remotely probably.  That's not a "it would take a really long time" thing but more of a getting caught thing (if I don't know who's watching the logs, where they're at, and what my chance of escalation is).  Locally against a suid binary, after exhausting opportunities at infoleaking and reducing the entropy size, I would do it.  It can be quite fast, no daemon monitors would come into play, and I'd know that after I was done I'd be able to clean up any evidence of the attempts.

-Brad

---

### Post by rookcifer on 2010-08-14
> **spender_grsec said:**
> Hi earthpigg,

Regarding binary blobs, I'll say this:

It depends on what exactly we refer to when we use this term, but in  general, they're not blobs at all.  At the lowest level, yes they're 1s  and 0s, but they're also a set of processor instructions and data that  can be analyzed, disassembled, decompiled into C-like pseudo-code, etc.   It's a different skill set, but one that many people possess, and there  exist many tools to help in the process.  One of these is probably  installed on your system right now: run objdump -d /bin/ls and you'll  see a disassembly of the code of the ls binary.

Yeah but there are code obfuscation techniques.  Indeed, there is actually a C code [obfuscation contest]("http://www.ioccc.org/years.html#1988_phillipps") held every year.  I would presume this could really put a monkey wrench into those decompiling the code (it's already difficult enough without obfuscation).

> If I were to weigh the possibility of something affecting me, I'd be  more worried about the possibility of someone under an assumed name  submitting an innocuous-looking patch to the kernel that contains some  subtle vulnerability the attacker knows how to exploit.  

Like [this one]("http://www.securityfocus.com/news/7388") from 2003?  Two lines of code that gave the attacker root.  Thankfully it was caught before put in the mainline kernel.

> The approach  has plausible deniability as everyone makes mistakes from time-to-time,  and if it's caught it'd be no different than someone exploiting any  other bug in the kernel.  

Or how about the Ken Thompson compiler backdoor (a story I am sure you're familiar with)? The backdoor was not in the Unix kernel itself -- nowhere in its source -- and it wasn't even in the C compiler code (it was at first, but then removed after compiling itself).  So you have essentially a completely undetectable backdoor that gave Thompson root to any Unix machine compiled with his compiler (whose source looks clean upon inspection).  The only way to combat this scenario is to use a 100% verified clean compiler (or better yet a number of different compilers) that can somehow be proved not to have been tampered with.  This is not as trivial as it seems and I would be surprised if much thought is put into this sort of thing by the Linux kernel devs.

> Probably it's best not to imagine these scenarios ;)



Indeed, but with the NSA lurking around with their multi-billion dollar budget and teams of PhD mathematicians and computer scientists, you can bet they have been working on ways to accomplish these things.  We already know ([as shown by Dan Shumow and Niels Ferguson]("http://www.schneier.com/essay-198.html")) that they probably have "magic numbers" that can act as a master key to an elliptic-curve PRNG that is actually a NIST standard (and found in Windows Vista).  And it's only a NIST standard because NSA says it should be. :( (Even though that PRNG is found in Windows, it is not the default PRNG, thank God).

And then you have the whole issue of hardware microcode, especially CPU microcode.  Can we trust Intel, AMD, et al?  NSA stopped trusting private companies a long time ago and now produce most of their sensitive CPU's in house.  

I guess my point is that at some point we all have to put "trust" somewhere.  But, I do think a good start to helping *software* security would be to start from the ground up with a new formally verifiable kernel written in a secure programming language like BitC, both of which are being worked on by Jonathon Shapiro (of the [Coyotos project]("http://www.coyotos.org/")).

---

### Post by rookcifer on 2010-08-14
Thanks for the response on brute forcing ASLR, Brad.  I will have to reread it and take a little time to digest it all. ;)

I can already tell this will be an "epic" thread here in the security forum, as it's not everyday that actual kernel hackers/security specialists post here.

---

### Post by spender_grsec on 2010-08-14
> Yeah but there are code obfuscation techniques.  Indeed, there is actually a C code [obfuscation contest]("http://www.ioccc.org/years.html#1988_phillipps")  held every year.  I would presume this could really put a monkey wrench  into those decompiling the code (it's already difficult enough without  obfuscation).

Definitely, obfuscation can be a problem.  To me it would suggest someone's trying to hide (or protect) something, so I'd envison backdoors as the hiding-in-plain-sight type.  Just as there are obfuscators though, there are deobfuscators ;)  Compilers themselves actually are pretty good deobfuscators.

> Like [this one]("http://www.securityfocus.com/news/7388") from 2003?  Two lines of code that gave the attacker root.  Thankfully it was caught before put in the mainline kernel.

IIRC that backdoor was inserted due to kernel.org being compromised; it wasn't introduced into the kernel via the normal channels (which is why the inconsistency was detected).  Maybe my imaginary scenario has already worked, since there's been no detected case of it being done intentionally yet.

Regarding compiler abuse, David Wheeler did a paper on detecting them.  The assumption being, like you said, there being at least one other compiler you consider trusted (it's from a different source, from a long time ago, etc).  It's not a real proof due to the trust issue, but at some point Occam's Razor applies.

Trust is always that lingering question ;)

-Brad

---

### Post by witeshark17 on 2010-08-14
> **spender_grsec said:**
> Regarding compiler abuse, David Wheeler did a paper on detecting them.  The assumption being, like you said, there being at least one other compiler you consider trusted (it's from a different source, from a long time ago, etc).  It's not a real proof due to the trust issue, but at some point Occam's Razor applies.

Trust is always that lingering question ;)

-Brad Truly the bottom line. But I suppose this remains true in the closed source world as well... maybe even more so.

---

### Post by Rubi1200 on 2010-08-17
I started a thread with a poll in the Community Cafe section of the forums because I was interested to find out what people do to secure their systems.
[http://ubuntuforums.org/showthread.php?t=1552762](http://ubuntuforums.org/showthread.php?t=1552762)

One of the options offered in the poll was grsecurity.

Thus far, it has received no votes.

My question to the community, as well as to Brad Spengler, is whether this is because users are unaware of this tool, are afraid to use it, or consider such measures unnecessary?

I am not a security expert, but I find the subject fascinating and would be very interested to read what people think about the need for grsecurity on a default desktop Ubuntu installation.

Thanks in advance.

---

### Post by bodhi.zazen on 2010-08-17
> **Rubi1200 said:**
> I started a thread with a poll in the Community Cafe section of the forums because I was interested to find out what people do to secure their systems.
[http://ubuntuforums.org/showthread.php?t=1552762](http://ubuntuforums.org/showthread.php?t=1552762)

One of the options offered in the poll was grsecurity.

Thus far, it has received no votes.

My question to the community, as well as to Brad Spengler, is whether this is because users are unaware of this tool, are afraid to use it, or consider such measures unnecessary?

I am not a security expert, but I find the subject fascinating and would be very interested to read what people think about the need for grsecurity on a default desktop Ubuntu installation.

Thanks in advance.

My impression, honestly, is that most people who use Ubuntu do not experience any security problems, so they do not feel the need to do more.

Those who do want to do more, IMHO, often come from windows, and so they want to configure antivirus and a firewall as #1 and #2 , then they often go on to securing their browser.

To go beyond that often involves a bit of a learning curve, and many people use Apparmor before grsecurity.

I would imagine grsecurity is in more potential use on servers.

---

### Post by Rubi1200 on 2010-08-17
> **bodhi.zazen said:**
> My impression, honestly, is that most people who use Ubuntu do not experience any security problems, so they do not feel the need to do more.

Those who do want to do more, IMHO, often come from windows, and so they want to configure antivirus and a firewall as #1 and #2 , then they often go on to securing their browser.

Thanks for responding bodhi.

The results from the poll I mentioned definitely indicate what you suggest; namely, setting up firewalls, antivirus, and, in many cases,  browser security.

Interestingly, only 2 votes for the option about whether people use AppArmor or not were posted.

---

### Post by witeshark17 on 2010-08-17
I think there needs to be more emphasis on the points Brad made about the kernel issues; a proven concept must be addressed, even if most people aren't gonna try it out ***most days**** in the real world!*

---

### Post by spender_grsec on 2010-08-17
> **Rubi1200 said:**
> I started a thread with a poll in the Community Cafe section of the forums because I was interested to find out what people do to secure their systems.
[http://ubuntuforums.org/showthread.php?t=1552762](http://ubuntuforums.org/showthread.php?t=1552762)

One of the options offered in the poll was grsecurity.

Thus far, it has received no votes.

My question to the community, as well as to Brad Spengler, is whether this is because users are unaware of this tool, are afraid to use it, or consider such measures unnecessary?

I am not a security expert, but I find the subject fascinating and would be very interested to read what people think about the need for grsecurity on a default desktop Ubuntu installation.

Thanks in advance.

As for the poll results, selection bias is probably the biggest contributor, followed by the existence of the "a combination of the above" option.  My focus is indeed more on server environments and protecting those;  I think it falls in line with where the general threat to Linux systems is as well.  BTW I noticed in the poll comments several posters had a '90s "firewalling ports keeps hackers out" mindset, which just doesn't match with reality.

Though the "threatscape" is constantly changing, there really isn't currently the same threat to Linux desktops as exists for Windows.  Very little of that has to do with the security of Linux though.  The threats Linux faces are targeted attacks, particularly against servers, and often not with the end goal of compromising just the Linux server, but to modify the content it serves in order to compromise visiting Windows users.

Unless the vulnerability involved is something like the Java ones that allow for an easy cross-platform exploit, the opportunity cost of developing reliable Linux client-sides is too great.  There simply isn't enough of a user base to justify the time and cost of development.  The few security advantages Linux does have over Windows (specifically, not having ASLR being opt-in per shared object), as well as its diverse nature, helps contribute to the opportunity cost.

We don't go around advertising grsecurity or PaX, though everyone is using some features of ours whether they know it or not, regardless of what OS they run (see previous influence png).  There are of course advantages to using grsecurity on the desktop (at the very minimum you'll have a much better NX/ASLR implementation protecting your userland applications), but I imagine people aren't driven to it unless they perceive a need for it.  I know of many people involved in infosec that use it; even "blackhats" use it -- I find this both interesting and ironic.

For myself and others in the security industry, there's a clear threat that doesn't exist for the average Linux user.  We're specifically targeted for reasons of gamesmanship/public embarrassment/research theft/etc.  The reasons are as varied as the people involved in the attacks.  Perhaps they want to obtain private exploits the person has, or if they're high-profile, like in the case of Dan Kaminsky, the goal will be public embarrassment (he had personal emails, embarrassing torrents, passwords, all disclosed publicly last year or so). One of the two Google guys (who were publishing high-profile Linux vulnerabilities, drawing the ire of attackers that want to keep the vulnerabilities secret) was also successfully attacked.  The attackers didn't manage to compromise his home system (which I believe runs grsecurity) but instead they were able to attack a Linux system run by his ISP that forwarded mail to him.  Despite the appearance when he logged into his webmail account that no mail was being stored on the ISP's server, all the mail being forwarded was actually stored in a secret database on the server, which the attackers obtained after compromising the system (and then published some of the emails).  So for those of us who have specific known threats against us, there's a big incentive there to use something like grsecurity.  Those of us involved in security are also more educated about threats and what we'd be capable of as an attacker, and thus recognize the need for protection beyond what Linux distributions provide by default.

But in general I would say the target audience and the majority of our user base comes from servers.  Probably for some of them it requires something bad to happen first that affects them or their company for them to start taking a more serious approach to security.

A little more about selection bias: we have lots of grsecurity users running it on all kinds of distros (including custom ones with grsecurity integrated) but when I did a survey recently of people using a particular feature, I only heard back from people using Gentoo Hardened and one person using Debian.  For some people, security is more of an active part of their computer usage, so they're more active in keeping tabs on improvements in the area and keeping things up to date.  So it wasn't surprising to me to see the distribution focused on security being the one most represented in the survey.  For many other users we won't receive any input until something breaks ;)

-Brad

---

### Post by witeshark17 on 2010-08-17
> **spender_grsec said:**
> As for the poll results, selection bias is probably the biggest contributor, followed by the existence of the "a combination of the above" option.  My focus is indeed more on server environments and protecting those;  I think it falls in line with where the general threat to Linux systems is as well.  BTW I noticed in the poll comments several posters had a '90s "firewalling ports keeps hackers out" mindset, which just doesn't match with reality.

So it wasn't surprising to me to see the distribution focused on security being the one most represented in the survey.  For many other users we won't receive any input until something breaks ;)

-Brad IMO proven concepts should never be retro fits... Again closing the barn door.... well you know... ):P

---

### Post by bodhi.zazen on 2010-08-17
> **spender_grsec said:**
> BTW I noticed in the poll comments several posters had a '90s "firewalling ports keeps hackers out" mindset, which just doesn't match with reality.

<clip>

-Brad

+100 

I have been on a "one-man mission" to break them of this mentality , as you can see I  have much work yet to do.

---

### Post by earthpigg on 2010-08-18
I just googled grsecurity because I wanted to see the website.

First Google result:

> [grsecurity]("http://www.grsecurity.net/")
Grsecurity is a set of security patches to the *_**2.4 tree of Linux kernels**_*. The goal of the project is to create the most secure system possible while ...

---

### Post by rookcifer on 2010-08-18
> **spender_grsec said:**
>  One of the two Google guys (who were publishing high-profile Linux vulnerabilities, drawing the ire of attackers that want to keep the vulnerabilities secret) was also successfully attacked.  The attackers didn't manage to compromise his home system (which I believe runs grsecurity) but instead they were able to attack a Linux system run by his ISP that forwarded mail to him.  Despite the appearance when he logged into his webmail account that no mail was being stored on the ISP's server, all the mail being forwarded was actually stored in a secret database on the server, which the attackers obtained after compromising the system (and then published some of the emails).  So for those of us who have specific known threats against us, there's a big incentive there to use something like grsecurity.  

Would one of these guys be Tavis Ormandy?  I don't know if he publishes Linux vulns, but I know he has found several critical Windows vulns, which you know has to tick off MS.

And when you say "they published Linux vulns the attackers wanted to keep secret," I am curious to know more about this.  What I mean is, did these Google guys independently discover the vulns *after* the "black hats" had already done so?

---

### Post by rookcifer on 2010-08-18
> **earthpigg said:**
> I just googled grsecurity because I wanted to see the website.

First Google result:

Old link.  Grsecurity/PAX both work with 2.6.x kernels.  When I used to use Gentoo, I ran both of them.

---

### Post by Rubi1200 on 2010-08-18
> **spender_grsec said:**
> As for the poll results, selection bias is probably the biggest contributor, followed by the existence of the "a combination of the above" option.  My focus is indeed more on server environments and protecting those;  I think it falls in line with where the general threat to Linux systems is as well.  BTW I noticed in the poll comments several posters had a '90s "firewalling ports keeps hackers out" mindset, which just doesn't match with reality.

A little more about selection bias: we have lots of grsecurity users running it on all kinds of distros (including custom ones with grsecurity integrated) but when I did a survey recently of people using a particular feature, I only heard back from people using Gentoo Hardened and one person using Debian.  For some people, security is more of an active part of their computer usage, so they're more active in keeping tabs on improvements in the area and keeping things up to date.  So it wasn't surprising to me to see the distribution focused on security being the one most represented in the survey.  For many other users we won't receive any input until something breaks ;)

-Brad

Thank you for taking the time to respond to my post. Obviously, I agree with you about selection bias. The goal of the thread was to try and get a general picture of what people here on the forums do, or consider important, regarding securing their computers.

Personally, I was a bit surprised about a couple of things; those who responded that they do nothing about security, and those who say they use a router firewall as well as the Ubuntu firewall. I have read numerous posts from highly experienced members such as bodhi.zazen, as well as others, who have consistently reminded people that, in most cases, if you have a router firewall there is no need to enable the firewall on Ubuntu since it does not add an additional layer of security (as some seem to believe).

Obviously, I realize that your program is aimed at servers, but since it is given mention in the security sticky by bodhi, I was just curious as to whether or not people were aware of and/or used it.

In hindsight, the options I offered people to choose from in the poll might have been better formulated. But, as I said, the idea was to get a sort of quick overview of people's thoughts on the subject.

Again, thanks for taking the time to explain some basic principles to a complete beginner in the field of Linux security.

:-)

---

### Post by movieman on 2010-08-18
> **Rubi1200 said:**
> TI have read numerous posts from highly experienced members such as bodhi.zazen, as well as others, who have consistently reminded people that, in most cases, if you have a router firewall there is no need to enable the firewall on Ubuntu since it does not add an additional layer of security (as some seem to believe).

While the router firewall will stop 99% of attacks, using the Ubuntu firewall can add security against people who are inside your network; otherwise if someone hacks into your wireless AP they immediately have access to everything.

Unfortunately I had to disable ufw on my server because it seems to like randomly dropping ISAKMP packets. One day I'll have to investigate that, because Firestarter was fine.

---

### Post by rookcifer on 2010-08-18
I see Brad has been at work on [another exploit.]("http://www.h-online.com/security/news/item/Root-privileges-through-Linux-kernel-bug-Update-1061563.html")

EDIT:  Upon further reading, it appears Spengler's name was brought up due to an unrelated exploit.  At any rate, it's still an article of interest to this thread (imo).  But I would like Brad's take on it.

---

### Post by witeshark17 on 2010-08-18
Am I right in saying that the sinlge most useful contribution firewalls offer is the dropping of all unrequested data packets, and some others based on general protocols like IP and destination port? What other truly helpful function do they offer?

---

### Post by bodhi.zazen on 2010-08-18
> **witeshark17 said:**
> Am I right in saying that the sinlge most useful contribution firewalls offer is the dropping of all unrequested data packets, and some others based on general protocols like IP and destination port? What other truly helpful function do they offer?

Although filtering is by far the most common use, firewalls have many uses. In addition to filtering, NAT allows internet sharing to a LAN. iptables also performs logging. There are additional features to iptables as well , see man iptables or any online tutorial.

---

### Post by OpSecShellshock on 2010-08-18
> **rookcifer said:**
> I see Brad has been at work on [another exploit.]("http://www.h-online.com/security/news/item/Root-privileges-through-Linux-kernel-bug-Update-1061563.html")

EDIT:  Upon further reading, it appears Spengler's name was brought up due to an unrelated exploit.  At any rate, it's still an article of interest to this thread (imo).  But I would like Brad's take on it.

If you follow the link to Rutkowska's blog there's a fairly interesting discussion in the comments. Well, interesting to me if not to its own participants for very long. I think essentially the discussion gets into how various protection mechanisms are supposed to be used vs. how they're actually going to be used, though that could just be me seeing the discussion I'd like to see.

---

### Post by spender_grsec on 2010-08-18
Well I had written a lengthy reply that was lost due to Firefox crashing on me, so here's a rewritten, condensed version:

opsec: Don't interpret those comments as any actual discussion.  Joanna selectively censored posts by myself and the PaX Team (while keeping her own posts of hype and hand-waving, and of course giving herself the last word) so it's missing some ideas she didn't want people to see.  These will be posted in a neutral forum where the marketer doesn't decide what ideas the readers are allowed to see.

rookcifer:  Yes, Tavis and Julien, though Julien was the only one known to be successfully attacked (they were both targeted).  Blackhats do find the bugs sooner and target researchers that publish vulnerability information because it ruins any public exploit the blackhats have for the vulnerability (to them it's like having spent months of hard work building a house, and having some guy come by and destroy it with a bulldozer).  The value of the exploit lies in the vulnerability it exploits staying private, as well as any special techniques used by the exploit.  When public, the bug will obviously be fixed by the vendors, and we (the PaX Team and I) will kill the techniques they used as well.

This is why the PaX Team and I took Linus and the other kernel developers to task about their hiding of security vulnerabilities (that was just done with the recent stack overlap vulnerability).  The culture upstream has only serves to hurt distributions and users, as not all of the vulnerability fixes get backported, even if the cases where upstream knows a particular bug is a security vulnerability.  How do you assess the risk for this: [http://seclists.org/oss-sec/2010/q1/45](http://seclists.org/oss-sec/2010/q1/45)  The vendors didn't know, and upstream wouldn't help.  People involved in security, especially blackhats, have no problem spotting these silent fixes, nor do they need to rely on them for the creation of their private exploits.  Only a few of the vulnerabilities end up getting CVEs assigned.

Unless someone's watching the watchers, of course.  Last year I made an experiment out of this by posting publicly on all the silent security fixes I saw, so that distributions would have no excuse for not assigning CVEs.  The result?  2009 was "The Year of the NULL Pointer Dereference", a vulnerability class I released the first public Linux kernel exploit for in 2007 (though I developed it and we already had UDEREF to protect against it in 2006).  [http://www.awe.com/mark/blog/20100216.html](http://www.awe.com/mark/blog/20100216.html)
It was not a good year for the kernel ;)  Not because it suddenly got bad (they knew about NULL pointer dereference vulnerabilities since 2007), but because I made sure things were handled more honestly.  Things improved for a bit afterward without me, but now we're back to a fraction of the vulnerabilities being assigned CVEs.  And the number of CVEs for the kernel drops to about 0 when Eugene Teo is out for vacation ;)

-Brad

---

### Post by rookcifer on 2010-08-18
> **spender_grsec said:**
> Well I had written a lengthy reply that was lost due to Firefox crashing on me, so here's a rewritten, condensed version:

Go get the Lazarus add-on.  It will automatically database everything you have written and recover it for you if FF crashes.  It's been a lifesaver for me in the past.

> opsec: Don't interpret those comments as any actual discussion.  Joanna selectively censored posts by myself and the PaX Team (while keeping her own posts of hype and hand-waving, and of course giving herself the last word) so it's missing some ideas she didn't want people to see.  These will be posted in a neutral forum where the marketer doesn't decide what ideas the readers are allowed to see.

Yeah, but she's hot. ;)

On a serious note, she does annoy me especially with her "new" OS that she is developing (which is just Linux with some VM technology thrown in).  Her ideas are nothing new and there have long been other projects doing similar things.  But, again, she is hot so most people tolerate her.

> rookcifer:  Yes, Tavis and Julien, though Julien was the only one known to be successfully attacked (they were both targeted).  Blackhats do find the bugs sooner and target researchers that publish vulnerability information because it ruins any public exploit the blackhats have for the vulnerability (to them it's like having spent months of hard work building a house, and having some guy come by and destroy it with a bulldozer).  The value of the exploit lies in the vulnerability it exploits staying private, as well as any special techniques used by the exploit.  When public, the bug will obviously be fixed by the vendors, and we (the PaX Team and I) will kill the techniques they used as well.


Thanks for the explanation.

> This is why the PaX Team and I took Linus and the other kernel developers to task about their hiding of security vulnerabilities (that was just done with the recent stack overlap vulnerability).  The culture upstream has only serves to hurt distributions and users, as not all of the vulnerability fixes get backported, even if the cases where upstream knows a particular bug is a security vulnerability.  How do you assess the risk for this: [http://seclists.org/oss-sec/2010/q1/45](http://seclists.org/oss-sec/2010/q1/45)  The vendors didn't know, and upstream wouldn't help.  People involved in security, especially blackhats, have no problem spotting these silent fixes, nor do they need to rely on them for the creation of their private exploits.  Only a few of the vulnerabilities end up getting CVEs assigned.

I remember reading some of your "exchanges" with people on the LKML about this.  Things got a bit heated, iirc.  I guess my question is why are they keeping the vulns secret?  What are they gaining by doing this?  Is it laziness, incompetence, or something more sinister?

---

### Post by Bachstelze on 2010-08-18
> **rookcifer said:**
> 

I remember reading some of your "exchanges" with people on the LKML about this.  Things got a bit heated, iirc.  I guess my question is why are they keeping the vulns secret?  What are they gaining by doing this?  Is it laziness, incompetence, or something more sinister?

My (very uninformed) guess is that the Linux people are not really interested in security.  Linus basically admitted he doesn't care about it when he called the OpenBSD folks "masturbating monkeys" because they care more about security than he does.  I think I see why: security doesn't bring new users, especially in Linux where a lot of people are under the impression that merely running it makes their systems iron-clad secure.  Even worse: if more vulnerabilities started being publicized, people would think "Well, this Linux thing is not more secure than Windows, after all, so why am I bothering with it?".  You know how they are, especially regarding security: they will read on some random blog that more vulnerabilities started to appear in Linux--because that's what your typical blogger will say, not "the vulnerabilities have always been there, only now do we learn about them"--and jump to conclusions.

Basically, despite what they publicly say, I think getting more users is much more important to Linus & Co. than delivering a good product.  To me, Linux kernel development seems to be a race to new features that will attract new users, not a quest for quality.

---

### Post by spender_grsec on 2010-08-18
It's not sinister.  It's a combination of a misguided belief (they're developers, not security people) that by hiding the information they're protecting users, and an attempt to hide/ignore the security implications of the current development model.  Linus has also managed to convince enough people of the sage wisdom of "a bug is just a bug" despite the fact that the entire rest of the world disagrees (he's obviously never worked in any enterprise environment).

The current development model is a security disaster, as their development focus isn't on building a reliable and secure OS, but instead on getting new features out to users as soon as possible.  It leaves users in a bit of a paradox: use the latest code and get their silent fixes but also the new wave of vulnerabilities they're constantly adding, or use older code without those new vulnerabilities, but also without some of those silent fixes.  Nobody wins.

There's also probably something to be said here about how the commercialization of Linux has contributed to this situation, and how (I feel) that the developers think they have no responsibility or obligation to users regarding security of the kernel.

As a researcher, these are all things I disagree with, so I refuse to cooperate with upstream in a way that supports or contributes to their backwards practices.  Their practices have won them numerous nominations and awards from the industry (not the good kind):
[http://pwnies.com/archive/2009/winners/](http://pwnies.com/archive/2009/winners/) (Lamest Vendor Response)
[http://pwnies.com/archive/2009/nominations/](http://pwnies.com/archive/2009/nominations/) (Most Epic Fail)
[http://pwnies.com/archive/2008/nominations/](http://pwnies.com/archive/2008/nominations/) (Lamest Vendor Response)

-Brad

---

### Post by witeshark17 on 2010-08-18
Developers that allow impatience to expose security *loss* in such huge blunders should be embarrassed by not only this failure, but their own absurd denial of reality.

---

