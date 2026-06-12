---
title: "How to Set Up and Secure Ubuntu as a Virtualization Host"
date: 2024-08-26
forum: Virtualisation
---

### Post by tlkristensen on 2024-08-26
Hello Ubuntu Community,

I'm planning to use Ubuntu as a virtualization host for my organization's infrastructure and would appreciate some advice on the following:

**Setting Up Ubuntu as a Virtualization Host:**

[LIST]
[*]Which Ubuntu version and configurations are best suited for hosting virtual machines? 
[*]What are the recommended virtualization technologies to use on Ubuntu (e.g., KVM, LXD, OpenStack), and what are the pros and cons of each? 
[*]Are there any detailed guides or resources that explain how to set up and manage a virtualization environment on Ubuntu? 
[/LIST]

**Security Best Practices:**
[LIST]
[*]What are the best practices for securing an Ubuntu-based virtualization host? 
[*]Any tips on hardening the system to protect against potential threats? 
[*]Can anyone recommend tools or services for monitoring and maintaining security on an Ubuntu virtualization host? 
[/LIST]

I'd greatly appreciate any insights, documentation, or links to relevant resources that can help me ensure a secure and efficient setup.

Thanks in advance for your help!

Best, Thomas

**[Edit/update]**
First of all, I am not a LLM but ChatGPT has been used to improve the quality of the question. You could argue that it did not work. 

Let me try a more specific question instead: 

We are evaluating using Ubuntu for a virtualization host and expecting up to max 15 host. We are using the CIS hardening benchmark to harden the Ubuntu guest (and hosts). We are not limited in the choice of virtualization and can use KVM, OpenStack etc. but we need to document that we are hardening and securing it using the best-practice and we cannot find any authoritative source for hardening and/or securing it.

Can everyone provide authoritative references? or at least good references?

---

### Post by TheFu on 2024-08-28
You are asking very big questions that all depend on many aspects to your deployment.  Pick one specific security issue and ask about that. Use specific tools and specific threats because how a home server that is never accessed from outside needs to be secured completely differently than a server the military runs that is internet facing.  

There are standards for how a military server should be configured.  They are not for beginners and will break some parts of most server deployments.  Those take years to be worked up and released, so I think 20.04 is the newest specification that is completely.  22.04 was due out this year, but when I looked a few months ago, it wasn't yet available.

Anyway, there is foundational knowledge that is required first to understand any of this.  I think Bob Toxen's, Real World Linux Security: Intrusion Protection, Detection, and Recovery, book is a good introduction still even though it is over 20 yrs old.  There aren't "best practices" for security random hosts doing random things.  It depends on the server workload.

Details change constantly, so very few of those guides exist since they will become out of date in less than 1 yr when things change.

With all that said, my #1 security technique is still daily, automatic, versioned, backups that are "pulled" from the system, never "pushed."  Good backups with sufficient retention periods are mandatory.  For high risk servers, I keep over a year of these backups.  As the risk for a system is reduced, the number might get down to  90 days, but no lower.  Sometimes nobody notices issues for a few months.

How many physical and virtual instances are you thinking about?  There are options that have lots of hassles until you have 20 physical servers and hundreds of virtual systems.

I've been deploying Linux servers for nearly 30 yrs.  I would caution anyone against using the current Ubuntu servers for LXD, because Canonical only provides it as a snap package with introduces lots of good things, but also many hassles.  There are times when I feel I don't really have control over my lxc instances managed by lxd.  Debian would be a better choice for those, I hate to say.  If you really care about security, perhaps deploying on RHEL would make the most sense?  There are some core security features in RHEL systems that aren't in Debian/Ubuntu systems.  Just something to consider.

And don't forget. All the details will be different in a year.

---

### Post by currentshaft on 2024-08-28
s

---

### Post by stephan4 on 2024-08-28
It sounds you miss the basics.

Go with Proxmox, rock solid and under the hood it's Debian.

---

### Post by TheFu on 2024-08-28
> **currentshaft said:**
> My man writing novels for AI bots over here.

"Thomas" is clearly an LLM. I really don't understand why so much AI generated spam is tolerated here.

I type really fast.

It isn't clear to me. Perhaps you'd be kind to create a post on recognizing those posts?  If it is so clear, that should be easy?  Bet the forum managers would appreciate any guidance too. Perhaps they could add a filter before posts are accepted?

---

### Post by Rubi1200 on 2024-08-28
I tend to agree with **TheFu **on this one.

Sometimes it is fairly obvious if text is AI generated.

I do not see this here.

Please enlighten us: what gives it away?

I also don't think it is fair to suggest that the staff are letting users get away with this type of content.

Spammers are sometimes very clever and it is not always so clear.

Also, please consider using the Report Post button in future. You can leave a brief description of what content you find problematic. That way, more than one staff member will see the report and can respond to it.

Bear in mind, that staff are on at different times and some only monitor certain sub-forums. But if you use the Report Post feature, more people will see your report.

---

### Post by TheFu on 2024-08-28
> **Rubi1200 said:**
> I tend to agree with **TheFu **on this one.

A first post in these forums with correct advanced edits is a bit odd.  

Bold headers and bullet points?  Is that it?  Or is AI trying to get humans so solve a question that has been asked, but to which it cannot find an obviously acceptable answer?   "Why" answers are always harder than "how" or "what to type" answers when sufficient details are provided.  Some background has to be assumed in the reader, which is almost always incorrect.

Or perhaps the answer is never respond to a user with only 1 post?  How would any user feel welcomed if nobody responds, ever?

---

### Post by currentshaft on 2024-08-28
ai

---

### Post by werewulf75 on 2024-08-30
> **Rubi1200 said:**
> Spammers are sometimes very clever and it is not always so clear.
I have almost two decades experience as a moderator and also as an administrator in a variety of forums (although hoping to reduce to one or two private ones). In all this time I've never really come across any such thing as a "clever spammer" - I've always thought that to be an oxymoron. They tend to be quite the opposite - dumb as hell. And LLM generated spam also tends to stick out like a sore thumb IME. I can almost smell spammers/spam bots. Including the "sleepers". Yeah, spammers try all sorts of 'tricks' with placing their spam, like hiding it by making it the same colour as the background, 'hiding' it in a full stop, placing it in quoted text from a previous post, and a whole lot more. Whatever they try, it doesn't get past me.

Sometimes, just sometimes, I might be inclined to give a post the benefit of the doubt but keep a very close eye on it. Sometimes it does turn out perfectly innocent and legit, but most times the stench did prove too strong. ;)

In this particular case, I'm inclined to give the benefit of the doubt, with a 50/50 weighting. Let's wait and see.

[Edit] Didn't see that last post by currentshaft, which went up after I'd started on this post. Well, there we have it. It is a stinking bot! [/Edit]

---

### Post by tlkristensen on 2024-09-02
Thanks for the feedback.

I have a very good understanding of the concepts and processes need to support it &#8211; As well as the constant changes in this area.

I have looked at the CIS hardening benchmarks to start the hardening the OS but it does not include guidance on hardening KVM or LXD &#8211; But based on your feedback, I should look at Redhat and KVM, correct?

CIS has a hardening guide for Redhat but none for KVM. Can you point me towards good resources on this?

---

### Post by tlkristensen on 2024-09-02
> **currentshaft said:**
> My man writing novels for AI bots over here.

"Thomas" is clearly an LLM. I really don't understand why so much AI generated spam is tolerated here.

I am not an LLM but a human but you are correct in that I am using ChatGPT to improve the quality of my question

---

### Post by tlkristensen on 2024-09-02
> **stephan4 said:**
> It sounds you miss the basics.

Go with Proxmox, rock solid and under the hood it's Debian.

We have been looking and evaluating Proxmox but we are not able to find any good reasons on how to hardening and securely configure it. Can you point to any good resources on this?

---

### Post by tlkristensen on 2024-09-02
> **Rubi1200 said:**
> I tend to agree with **TheFu **on this one.

Sometimes it is fairly obvious if text is AI generated.

I do not see this here.

Please enlighten us: what gives it away?

I also don't think it is fair to suggest that the staff are letting users get away with this type of content.

Spammers are sometimes very clever and it is not always so clear.

Also, please consider using the Report Post button in future. You can leave a brief description of what content you find problematic. That way, more than one staff member will see the report and can respond to it.

Bear in mind, that staff are on at different times and some only monitor certain sub-forums. But if you use the Report Post feature, more people will see your report.

Just to be clear here and as already mentioned. I am not a bot or LLM but I am trying to improve the quality of my question with ChatGTP. You could argue if that succeeded ;-)

---

### Post by tlkristensen on 2024-09-02
> **TheFu said:**
> A first post in these forums with correct advanced edits is a bit odd.  

Bold headers and bullet points?  Is that it?  Or is AI trying to get humans so solve a question that has been asked, but to which it cannot find an obviously acceptable answer?   "Why" answers are always harder than "how" or "what to type" answers when sufficient details are provided.  Some background has to be assumed in the reader, which is almost always incorrect.

Or perhaps the answer is never respond to a user with only 1 post?  How would any user feel welcomed if nobody responds, ever?

If nothing else, I am glad that you took the time to answer.

---

### Post by tlkristensen on 2024-09-02
I have updated the question to be a more specific question. I hope, that someone is able to answer that question instead.

---

### Post by coffeecat on 2024-09-02
> **tlkristensen said:**
> I am not an LLM but a human but you are correct in that I am using ChatGPT to improve the quality of my question

> **tlkristensen said:**
> Just to be clear here and as already mentioned. I am not a bot or LLM but I am trying to improve the quality of my question with ChatGTP. You could argue if that succeeded ;-)

Then please say so clearly at the outset when you use AI. There is a veritable flood of AI-generated posts these days, and if you don't make the use of AI clear you are in danger of being mistaken for a spammer and being banned from the forum, or at least dismissed as a bot by the forum membership. Contrary to what one member states in this thread, we do not tolerate AI generated text when this is not used for genuine purposes. See our rules under "Spam" in the [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules"), and some further clarification in our [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"):

> ...Similarly, it is acceptable to consult AI resources such as ChatGPT in order to complement your own original thoughts, or to see if there is an aspect of the issue under consideration that you have forgotten. You may include a short partial quote or paraphrase from AI-generated output, so long as it clarifies or illuminates what the help requester has written, and you attribute the quote to the AI source. But simply regurgitating AI-generated answers is not allowed, and may very well lead to your account being banned.

**Addendum**: we have recently seen a significant number of posts posing as requests for help, but which consisted substantially or entirely of unattributed ChatGPT output. The text immediately above applies equally to questions as well as answers. To be clear: whatever the motivation for using AI to formulate a question, we have a zero-tolerance approach to unattributed AI-generated text.

Good luck with your task.

---

