---
title: "JATQ (Just Answer The Question)"
date: 2011-05-23
forum: The Cafe
---

### Post by rcayea on 2011-05-23
Hi everyone,

I would like to start a thread, or maybe even call it a “movement” regarding a specific issue that really irks me. 

The issue is this. When someone asks a questions on these forums, someone will reply and not answer the question and basically say, “no, don't do that, just get this, that, and this and it is better”. 

For example,

_**QUESTION:**_
In a recent post someone asked (and I am paraphrasing)

Can I use one external drive to back up linux and windows operating systems? The person was concerned about not being able to access the external if the external was formatted in the wrong file system (or at least one that wouldn't work for both). 


_**ANSWER:**_
Someone replied with this statement (again paraphrasing):

No, build a NAS because no one uses external drives anymore and  a NAS is cheap and better.



_**Rationale:**_

My point is, the response does not answer the question at all and only makes the questioner feel like he/she doesn't know anything or isn't “in-the-now”. To me it is basically degrading. 


In my opinion, the person answering the question could have said all he wanted about using a NAS device or anything else, but should have at least answered the question directly first. 



The idea I have is, if you are in full support of trying to persuade people to at the very least, answer a poster's question and if need be, then supply an alternative idea, please reply by simply signing your name in your reply.

Thanks, 
Randy

---

### Post by Bandit on 2011-05-23
Hey Randy,
Wow dont know why someone didnt bother to explain what you was asking. Also they are a fool to say no one uses external drives to back up anything. But anyway to answer your question.

Yes and sorta yes.

Basicly yes for both there is a way to back up both linux and windows onto external drives. Most drives like my segate comes with windows software that you can schedule to back up your entire system , or select folders when you wish it to. In linux I am sure their is some GUI software, but you really dont need it. You can make a batch script to back up your home folder to a external drive and just schedule it in Cron to run at a time of your choosing. The only downside is you cant back up both OS's at the same time correctly. Well I say correctly as there is no way to do a incremental backup on the none running Windows OS and Windows cant read Ext# FS to do incremental backups of it as well.
But if you scheduled you backups on seperate nights, as long as you remember to boot the correct OS for that night before going to bed you should be good to go.

BTW most dont realize here that .Tar stands for Tape Archive and is originally what it was used for. 

Hope this helps,
Exo

---

### Post by Simian Man on 2011-05-23
"Hey my / partition is full, and I need to make some space.  It seems "/usr/" is the biggest space-waster.  What is the command to delete this directory recursively?"

Should you "just answer" this question???

---

### Post by rcayea on 2011-05-23
Well, as I pointed out in my original post, how about giving the answer followed by, in this case, a great-big warning about deleting. 

I would imagine a good response would include:
A. Answer
B. Explanation of other possible ideas or explanation of what a bad idea some might be thinking of doind.

---

### Post by nothingspecial on 2011-05-23
There is a thin line between assuming no knowledge and being insulting.

"I've stuffed up my system - how do I reinstall?"

"You don't need to reinstall - do this instead :)"

Your scenario doesn't apply in a lot of cases.

I tend to draw the line between Absolute Beginners and everything else.

---

### Post by 3Miro on 2011-05-23
> **rcayea said:**
> Well, as I pointed out in my original post, how about giving the answer followed by, in this case, a great-big warning about deleting. 

I would imagine a good response would include:
A. Answer
B. Explanation of other possible ideas or explanation of what a bad idea some might be thinking of doind.

Simian Man gives a hypothetical situation, but I in a similar scenario I will not tell the user how to delete /usr/. If one knows enough about the system to understand the consequences of deleting /usr/, then one wouldn't be asking.

To make an analogy, if you are a Doctor on a health forum would you answer a question on how to most successfully commit suicide, especially if the person on the other end doesn't understand what they are doing. Linux is not nearly as serious thing, but I still feel an obligation to keep people safe from themselves. Besides, if things go wrong, someone will complain "I asked a question and I did what the person told me to do ... why did my system break".

You should also remember that in many situations people can find the answers with Google or just search the Forum. If people are asking, then they probably have low tech skills. You have to judge by the type of a question and how it is asked.

Usually it is a good idea to answer people, but not always.

Can you get the exact thread so we can see exactly what was asked and how it was answered. Hypothetical situations don't alway work.

---

### Post by rcayea on 2011-05-23
> **nothingspecial said:**
> There is a thin line between assuming no knowledge and being insulting.

"I've stuffed up my system - how do I reinstall?"

"You don't need to reinstall - do this instead :)"

Your scenario doesn't apply in a lot of cases.

I tend to draw the line between Absolute Beginners and everything else.

You could still provide an answer as to how to reinstall, though, in that case. Then proceed to suggest another alternative.

---

### Post by rcayea on 2011-05-23
> **3Miro said:**
> Simian Man gives a hypothetical situation, but I in a similar scenario I will not tell the user how to delete /usr/. If one knows enough about the system to understand the consequences of deleting /usr/, then one wouldn't be asking.

To make an analogy, if you are a Doctor on a health forum would you answer a question on how to most successfully commit suicide, especially if the person on the other end doesn't understand what they are doing. Linux is not nearly as serious thing, but I still feel an obligation to keep people safe from themselves. Besides, if things go wrong, someone will complain "I asked a question and I did what the person told me to do ... why did my system break".

You should also remember that in many situations people can find the answers with Google or just search the Forum. If people are asking, then they probably have low tech skills. You have to judge by the type of a question and how it is asked.

Usually it is a good idea to answer people, but not always.

Can you get the exact thread so we can see exactly what was asked and how it was answered. Hypothetical situations don't alway work.


3Miro:

I didn't want to post the original thread to help keep names out of this.

I go back to the simple statement I made before. Answer the question, then provide alternative information. 

If someone provided information to a user and his system broke, then the question wasn't answered well enough or at all. 

I would simply like to see the original question answered, possibly educating a user and then a responder can throw in all he/she wants to in addition.

---

### Post by 3Miro on 2011-05-23
> **rcayea said:**
> 
I go back to the simple statement I made before. Answer the question, then provide alternative information. 

If someone provided information to a user and his system broke, then the question wasn't answered well enough or at all. 


Look at Simian Man's example:

Question: How do I delete /usr?

Answer 1: rn -fr ... However, you should not delete /usr as it will break your system.

Answer 2: Never delete /usr. What are you trying to do?

Which one do you think is a better response, answer 1 or answer 2?

I vote for Answer 2 as Answer 1 can easily lead to: "I did this and my system broke, how do I fix it?" And this is not just for the OP, but for anyone else that may stumble upon this thread.

Your initial point applies to things like: 

Question: How do I use the mouse-wheel scroll to change workspaces in Unity?
Answer: Unity is crap, use Ubuntu 10.10.

However, there are other situations. A real situation for me was when a person started with a rant on how nobody would tell him how to install Gnome 3 on 11.04; people were just telling the guy not to do it. I gave him the link to a tutorial and sure enough, it broke the system. We went back and forth trying to fix it and we may have succeeded it, however, he then suddenly gave up and installed 10.10 back on. This was waste of both our time.

---

### Post by rcayea on 2011-05-23
> **3Miro said:**
> Look at Simian Man's example:

Question: How do I delete /usr?

Answer 1: rn -fr ... However, you should not delete /usr as it will break your system.

Answer 2: Never delete /usr. What are you trying to do?

Which one do you think is a better response, answer 1 or answer 2?

I vote for Answer 2 as Answer 1 can easily lead to: "I did this and my system broke, how do I fix it?" And this is not just for the OP, but for anyone else that may stumble upon this thread.

Your initial point applies to things like: 

Question: How do I use the mouse-wheel scroll to change workspaces in Unity?
Answer: Unity is crap, use Ubuntu 10.10.

However, there are other situations. A real situation for me was when a person started with a rant on how nobody would tell him how to install Gnome 3 on 11.04; people were just telling the guy not to do it. I gave him the link to a tutorial and sure enough, it broke the system. We went back and forth trying to fix it and we may have succeeded it, however, he then suddenly gave up and installed 10.10 back on. This was waste of both our time.

I like answer number two, also. As stated, Tell the person to delete any directory or file and so on (thus explaining the answer) and then go on to explain how it is bad to do so and suggest alternatives. My suggestion applies for any possible response. Just answer the question. I would hazard a guess that the responses to this thread are exactly what I am referring to.

---

### Post by Simian Man on 2011-05-23
> **rcayea said:**
> I like answer number two, also. As stated, Tell the person to delete any directory or file and so on (thus explaining the answer) and then go on to explain how it is bad to do so and suggest alternatives. My suggestion applies for any possible response. Just answer the question. I would hazard a guess that the responses to this thread are exactly what I am referring to.

If I'm taking *my* time to answer a question, I'll do it how I want to.  Often times the actual answer is worse (as in my example), but other times it just takes longer to explain than a simpler, alternative.  Also sometimes a poster may not know the answer, but may know another alternative that may be even more helpful.

It just comes off as arrogant to tell people how you want to be helped.

---

### Post by rcayea on 2011-05-23
> **Simian Man said:**
> If I'm taking *my* time to answer a question, I'll do it how I want to.  Often times the actual answer is worse (as in my example), but other times it just takes longer to explain than a simpler, alternative.  Also sometimes a poster may not know the answer, but may know another alternative that may be even more helpful.

It just comes off as arrogant to tell people how you want to be helped.

Being arrogant was not my intention if that was what you mean in the last sentence. 

I simply was tired of people not answering questions of the posters on this board.

---

### Post by tgalati4 on 2011-05-24
I often ask a question in response to a question.  The OP's are usually so poorly written and lack any detail it's difficult (or impossible) to answer the question.

So yes, it's tedious to answer someone's question with another question.

---

### Post by Bandit on 2011-05-24
@rcayea,
Dont tell my I was polite enough to answer your question when you really didnt want a fn answer at all. That would seriously just **** me off.
There is a reason I rarely show up to these forums much anymore, and childish behavior is the prime reason. A simple "thank you" however would go a long ways.

If you want a rant, I can fill a page full of it.
I started using ubuntu about version 5.04. I remember when half of the Ubuntu Community depended on me to compile and package most all of the 64bit multimedia applications and they were very appreciative and everyone here respected each other. But two things have come with the growth of Ubuntu, one being its became the easiest distro to install and also most compatible with hardware across the board. The other being that it has attracted so many kids and smart mouths that have no respect, or understanding of computers its just sad. Wished most would just go back to windows where they belong.

---

### Post by rcayea on 2011-05-24
I try to help with a an offering to ask folks to answer questions when replying to posts and Bandit says,

"The other being that it has attracted so many kids and smart mouths that have no respect, or understanding of computers its just sad. Wished most would just go back to windows where they belong."

Some people would say it is disrespectful to make assumptions - I am not a kid, I have a Master's Degree (so I do understand) and I know computers quite well.

If this is the type of flame-throwing responses that are going to be generated just because I had an idea, I will be glad to stop making this suggestion and consider this thread over-and-done-with.

---

### Post by scouser73 on 2011-05-24
> **rcayea said:**
> Hi everyone,

I would like to start a thread, or maybe even call it a “movement” regarding a specific issue that really irks me. 

The issue is this. When someone asks a questions on these forums, someone will reply and not answer the question and basically say, “no, don't do that, just get this, that, and this and it is better”. 

For example,

_**QUESTION:**_
In a recent post someone asked (and I am paraphrasing)

Can I use one external drive to back up linux and windows operating systems? The person was concerned about not being able to access the external if the external was formatted in the wrong file system (or at least one that wouldn't work for both). 


_**ANSWER:**_
Someone replied with this statement (again paraphrasing):

No, build a NAS because no one uses external drives anymore and  a NAS is cheap and better.



_**Rationale:**_

My point is, the response does not answer the question at all and only makes the questioner feel like he/she doesn't know anything or isn't “in-the-now”. To me it is basically degrading. 


In my opinion, the person answering the question could have said all he wanted about using a NAS device or anything else, but should have at least answered the question directly first. 



The idea I have is, if you are in full support of trying to persuade people to at the very least, answer a poster's question and if need be, then supply an alternative idea, please reply by simply signing your name in your reply.

Thanks, 
Randy

**+1**

I have seen this type of "answer" also and it's extremely annoying, I think your post should be a sticky.

---

### Post by satanselbow on 2011-05-24
> **tgalati4 said:**
> I often ask a question in response to a question.  The OP's are usually so poorly written and lack any detail it's difficult (or impossible) to answer the question.

So yes, it's tedious to answer someone's question with another question.

This is a very common occurrence with new Ubu users. Simple misrepresentation of the facts due to lack of prior knowledge of "Ubuntu speak" and the differences between that and windows terms.

Your average windows convert is unlikely to have much knowledge of partitions and partitioning - let alone where grub should go... there are numerous posts on the forum that go into elaborate partitioning schemes for new users struggling to install - which can only serve to confuse for example and IMHO.

I think answering further questions to clarify the true meaning of the question is sometimes essential... though tedious... and may lead to a more useful answer than ploughing ahead with potentially incorrect or misinterpreted initial responses ;)

My favourites are always the capitalised, grammatically halucinating rants... :popcorn:

---

### Post by del_diablo on 2011-05-24
> **rcayea said:**
> Hi everyone,

I would like to start a thread, or maybe even call it a “movement” regarding a specific issue that really irks me. 

The issue is this. When someone asks a questions on these forums, someone will reply and not answer the question and basically say, “no, don't do that, just get this, that, and this and it is better”. 

For example,

_**QUESTION:**_
In a recent post someone asked (and I am paraphrasing)

Can I use one external drive to back up linux and windows operating systems? The person was concerned about not being able to access the external if the external was formatted in the wrong file system (or at least one that wouldn't work for both). 


_**ANSWER:**_
Someone replied with this statement (again paraphrasing):

No, build a NAS because no one uses external drives anymore and  a NAS is cheap and better.



_**Rationale:**_

My point is, the response does not answer the question at all and only makes the questioner feel like he/she doesn't know anything or isn't “in-the-now”. To me it is basically degrading. 


In my opinion, the person answering the question could have said all he wanted about using a NAS device or anything else, but should have at least answered the question directly first. 



The idea I have is, if you are in full support of trying to persuade people to at the very least, answer a poster's question and if need be, then supply an alternative idea, please reply by simply signing your name in your reply.

Thanks, 
Randy

+1, I have seen this myself.
In my memory:
"How do I setup Debian with pinning?"
"DUDE! Do NOT setup Debian with pinning! do not do that!"
"I am well aware of the risks(broken packages), and I have read a bit about bit, so how do I do it?"
"You do not do that!"
"Why not?"
"Because you do not do that"
*rinse repeat for another 10 minuttes*

Or when....
"X happened, and I run Debian with pinning"
"Dude! Do not run Debian with pinning!"
"Well, do you mind telling me how to solve this?"
"Not telling, run a normal system instead!"
*rinse and repeat*

I have actually seen this happen over IRC, and some times over forums. It is really really silly.

---

### Post by forrestcupp on 2011-05-24
> **rcayea said:**
> Well, as I pointed out in my original post, how about giving the answer followed by, in this case, a great-big warning about deleting. 

I would imagine a good response would include:
A. Answer
B. Explanation of other possible ideas or explanation of what a bad idea some might be thinking of doind.
I agree with the heart of what you're saying in most situations. It really is annoying to want an answer and have someone give you a completely different solution than what you're wanting. The poster probably already had an external hard drive and they weren't looking to go out and buy the equipment to set up an NAS. I've seen many times where people asked for help with certain software and everyone told them they should be using a different app. They just want help with the software they already have installed!

But on the other hand, there are situations where it's not right to just answer the question. Take Simian Man's example of deleting the /usr directory. It's actually against the forum rules to answer a question like that and people have been severely disciplined. Some of us have been around long enough to remember the time when a few people were maliciously telling people to issue **rm** commands that really messed things up. After that, the "powers that be" really didn't take kindly to people giving answers that can trash people's computers.

So in some cases, you're not just talking about a good idea; you're talking about possibly breaking the forum rules and getting banned for it.

---

### Post by satanselbow on 2011-05-24
And this thread is just too ironically good to be true :D

[http://ubuntuforums.org/showthread.php?t=1765899](http://ubuntuforums.org/showthread.php?t=1765899)

---

### Post by 3Miro on 2011-05-24
> **satanselbow said:**
> And this thread is just too ironically good to be true :D

[http://ubuntuforums.org/showthread.php?t=1765899](http://ubuntuforums.org/showthread.php?t=1765899)

Somebody has a business making money and needs a piece of software. Then that person comes to the forums expecting free programmers and/or free lessons in programming. Why in the world would any of us do that?

I don't teach people programming for free, I don't teach people how to become administrators for free and I don't program for free. I help people resolve simple issues on their systems, that I do for free. How arrogant of me!

---

### Post by forrestcupp on 2011-05-24
> **3Miro said:**
> I don't teach people programming for free, I don't teach people how to become administrators for free and I don't program for free. I help people resolve simple issues on their systems, that I do for free. How arrogant of me!

Lol. Nobody is forced to post anything on here. It's not that hard to point someone to some tutorials where they can learn to program for free, and you don't have to be the one to teach them. I kind of got the idea the OP in that thread was just wanting some pointers. And I didn't really see the irony in that thread; it had a few decent responses.

---

### Post by 3Miro on 2011-05-24
> **forrestcupp said:**
> Lol. Nobody is forced to post anything on here. It's not that hard to point someone to some tutorials where they can learn to program for free, and you don't have to be the one to teach them. I kind of got the idea the OP in that thread was just wanting some pointers. And I didn't really see the irony in that thread; it had a few decent responses.

I just got upset at some people's sense of entitlement. The thread did have pointers (i.e. use Python), the responders misses only a couple of links to good tutorials. Yet the OP seems to not really appreciate it and want programmers for free.

At any rate, we should go back to topic here, I shouldn't have ranted about other threads.

---

### Post by forrestcupp on 2011-05-24
> **3Miro said:**
> I just got upset at some people's sense of entitlement. The thread did have pointers (i.e. use Python), the responders misses only a couple of links to good tutorials. Yet the OP seems to not really appreciate it and want programmers for free.
Ha, ha. I just didn't read far enough into the thread.

I can understand both views, though. He wanted to learn how to program a simple app to automate something he needed to help himself out. People suggested interfacing with the database, which is obviously the best way to do it. But that's an advanced task and obviously *not* the best suggestion for someone who hasn't even begun to learn programming yet. Depending on the amount of data and how often that data changes, it would be much quicker for a beginner to write a simple input/print app and hardcode the data in than to learn to program *and* interface with databases. 

He shouldn't have gotten angry and stormed out. But if people are going to spend their valuable time helping someone out, why not be sensitive to the asker's unique needs instead of wasting your time giving them info that isn't really going to help?

---

### Post by spynappels on 2011-05-24
There are questions where JATQ would work, but as pointed out, there are also many places where that would not work.

Looking at the "Removing /usr" question, if you put the answer first and then qualify it, some numpty will just copy and paste what is in the code block and then whine about how his system is borked. 

A blanket rule would not work IMHO, but as a guideline it is valuable.

---

### Post by rcayea on 2011-05-24
> **spynappels said:**
> There are questions where JATQ would work, but as pointed out, there are also many places where that would not work.

Looking at the "Removing /usr" question, if you put the answer first and then qualify it, some numpty will just copy and paste what is in the code block and then whine about how his system is borked. 

A blanket rule would not work IMHO, but as a guideline it is valuable.

I appreciate what you are saying. If someone is willing to answer the original question as I would have hoped for, then the poster comes back and doesn't read all of the response and does something unwise, we can't control that. However, maybe someone two years from now happens onto the thread and actually reads the whole response and gains something from it, that is certainly a valuable response.

---

### Post by rcayea on 2011-05-24
I have decided to post the thread that started me thinking to write this post.


Original question:
"Can I use one external drive, with one partition to back-up Ubuntu, Lucid, and another computer with Windows 7? Example; I want to have one folder on the external drive for Pictures, and be able to back up to that folder from either PC. The Linux PC is using ext4 format, and the Windows 7 is NFTS, All I want to do this with is videos, music, and pictures. Things that need to be accessed from both computers, no applications.
Someone smarter than me has probably done this already, how did you do it?"

The Response lacking an answer to the question:
"no, build a NAS external file server.. they are dirt cheap, and it is just an external enclosure and a hard drive, and you can format it to whatever you like.. Hook it up with a gigabit router and you are good to go. Everything is over the networks these days. Why bother with USB or firewire anymore if don't have to??

Even reinstall Ubuntu in less than 10 minutes over a LAN network installation. That's what I do."

---

### Post by 3Miro on 2011-05-24
> **rcayea said:**
> I have decided to post the thread that started me thinking to write this post.


Original question:
"Can I use one external drive, with one partition to back-up Ubuntu, Lucid, and another computer with Windows 7? Example; I want to have one folder on the external drive for Pictures, and be able to back up to that folder from either PC. The Linux PC is using ext4 format, and the Windows 7 is NFTS, All I want to do this with is videos, music, and pictures. Things that need to be accessed from both computers, no applications.
Someone smarter than me has probably done this already, how did you do it?"

The Response lacking an answer to the question:
"no, build a NAS external file server.. they are dirt cheap, and it is just an external enclosure and a hard drive, and you can format it to whatever you like.. Hook it up with a gigabit router and you are good to go. Everything is over the networks these days. Why bother with USB or firewire anymore if don't have to??

Even reinstall Ubuntu in less than 10 minutes over a LAN network installation. That's what I do."

Yes, this is an example of a bad response.

---

### Post by tgm4883 on 2011-05-24
> **3Miro said:**
> Somebody has a business making money and needs a piece of software. Then that person comes to the forums expecting free programmers and/or free lessons in programming. Why in the world would any of us do that?

I don't teach people programming for free, I don't teach people how to become administrators for free and I don't program for free. I help people resolve simple issues on their systems, that I do for free. How arrogant of me!

I actually was going to help the guy out until he turned vicious. I have a working python script that does what he wants, shame he was such a PITA.

> **rcayea said:**
> I appreciate what you are saying. If someone is willing to answer the original question as I would have hoped for, then the poster comes back and doesn't read all of the response and does something unwise, we can't control that. However, maybe someone two years from now happens onto the thread and actually reads the whole response and gains something from it, that is certainly a valuable response.

How do I delete / and all subdirectories recursively without being asked repeatedly if I want to delete a file. (I think you will find it is against forum rules for you to answer this question)

My point is no, we shouldn't "Just Answer The Question". What if it's a generic question that needs more information to answer (as many of the questions are)?

Please just answer these questions
[LIST]
[*]How do I fix my wireless?
[*]Why does Ubuntu boot to a blank screen?
[*]Why can't I watch videos online?
[/LIST]

---

### Post by tgm4883 on 2011-05-24
I agree, it's a bad response. But there are always the exception (that response) to the rule (usually good responses)

---

### Post by Copper Bezel on 2011-05-24
It's a matter of just (1) not being adversarial and (2) not questioning the user's logic in terms of the thing that they're actually trying to do. I do think that this is important. Telling a user that they're simply doing it wrong and should install some other piece of software or hardware, or most certainly asking "Why are you trying to do that?" is not going to be taken as helpful advice, and I've spoken to people who decided against Linux specifically because of this sort of "support." However, if that's actually a real question - "Well, what exactly are you trying to do?" - that's often a needed step in actually finding the best solution for the person asking the question.

If someone wanted to install an old copy of Photoshop 7, I'd explain Wine, check to find out that, hey, Photoshop 7 has a gold rating for Wine compatibility, and get them started; at the same time, I'd certainly mention that the current version of Krita might actually be the better bet and would of course be easier to get running.  

I don't really care that I am or anyone else is "working" for free. Work that is detrimental to its own purposes isn't free anything; it's a waste of everyone's time.

For the /usr question, I certainly wouldn't feel the need to shout, and I wouldn't see any harm in explaining that the folder could only be removed with root privileges so long as, in the same post, I explained that this would completely destroy the OS and render it unusable. 

I don't know, where does [this]("http://ubuntuforums.org/showthread.php?t=1766184") fall on the JATQ scale?

---

### Post by tgm4883 on 2011-05-24
> **Copper Bezel said:**
> It's a matter of just (1) not being adversarial and (2) not questioning the user's logic in terms of the thing that they're actually trying to do. I do think that this is important. Telling a user that they're simply doing it wrong and should install some other piece of software or hardware, or most certainly asking "Why are you trying to do that?" is not going to be taken as helpful advice, and I've spoken to people who decided against Linux specifically because of this sort of "support." However, if that's actually a real question - "Well, what exactly are you trying to do?" - that's often a needed step in actually finding the best solution for the person asking the question.

If someone wanted to install an old copy of Photoshop 7, I'd explain Wine, check to find out that, hey, Photoshop 7 has a gold rating for Wine compatibility, and get them started; at the same time, I'd certainly mention that the current version of Krita might actually be the better bet and would of course be easier to get running.  

I don't really care that I am or anyone else is "working" for free. Work that is detrimental to its own purposes isn't free anything; it's a waste of everyone's time.

For the /usr question, I certainly wouldn't feel the need to shout, and I wouldn't see any harm in explaining that the folder could only be removed with root privileges so long as, in the same post, I explained that this would completely destroy the OS and render it unusable. 

I don't know, where does [this]("http://ubuntuforums.org/showthread.php?t=1766184") fall on the JATQ scale?

You seem to contradict yourself, it's OK to ask why a user wants to do something if you are trying to help, but not OK to ask a user why they are trying to do something? I'd say in most cases it is beneficial to know why a user is trying to do a particular thing. There may be a better way (not saying use other software) to do what they want, or they may not be asking about something that would actually fix the issue they are having. 

How do you answer these? (Actual thread's I have seen)
[LIST]
[*]"Can I just delete the .log files out of /var/log/ ? They are taking up too much space"
[*]"How do I install a .run file"
[/LIST]

To JATQ
[LIST]
[*]Yes, or rather you could do "echo '' > LOGFILENAME" to truncate the file. You could also just delete all of the .# files, as those are old.
[*]From a terminal, 'chmod +x FILENAME' then './FILENAME'
[/LIST]

While both of those would have been correct in answering the user's question, you haven't actually helped the user. In both of those cases he would have been back later with more questions. 

In the first issue, the user had multiple GB log files indicating an issue on his system. Deleting or truncating the log files temporarily helped the symptom (freeing up disk space), but the issue would have quickly returned.

In the second issue, the user wanted to install the nvidia driver for his video card. He didn't know about Jockey or that there were drivers packaged for Ubuntu. While that would have installed the driver for him, it would likely cause more work in the long run when it comes to upgrades. Not exactly in the best interest of the user. That would be his choice of course, but to JATQ wouldn't have found out what he was trying to do so that information couldn't be given to him.

So in conclusion, I will continue to ask for additional information when I deem it necessary and I will JATQ when the user provides enough information that I feel I can adequately answer the question in the best interest of the user. Unless the user is an #@!%*(!, in which case I won't be helping him at all.

---

### Post by Copper Bezel on 2011-05-24
I completely agree with you, and I certainly didn't say anything to contradict that approach. I don't have any problem with asking for more information or trying to identify the thing that the user is actually trying to do. As I said, that's generally a necessary stage; figuring out the problem in both of those cases is putting in the necessary effort to fix the problem, where just answering the literal question would not be.

I *have* seen responses in the support forums that question the logic of that thing the user is actually trying to do, the actual end goal, or offer little help in that direction. I think the example brought up in the OP is a good one, but let me expand on my hypothetical a bit, regarding Photoshop 7 (a 2001 product.) If someone were to ask how to run Photoshop 7 on Ubuntu, I could imagine seeing a response berating the user for using a terribly outdated piece of software. "Why are you trying to do that?" is also a confrontational question. That doesn't mean that I wouldn't ask what kind of work the user intended to do in a less confrontational way, or that I wouldn't suggest an alternative piece of software along with the direct answer to the question.

I know what you mean about confrontational users, as [here]("http://ubuntuforums.org/showthread.php?t=1730189"). It's kind of funny, because I was looking it up as a case where *I* had failed to JATQ, and I'd forgotten that you were involved at all. I think Stinkeye's response was the most productive, though.

---

### Post by 3Miro on 2011-05-24
> **Copper Bezel said:**
> 
I know what you mean about confrontational users, as [here]("http://ubuntuforums.org/showthread.php?t=1730189"). It's kind of funny, because I was looking it up as a case where *I* had failed to JATQ, and I'd forgotten that you were involved at all. I think Stinkeye's response was the most productive, though.

This is not a JATQ problem at all!

I must have unsubscribed from the thread before he answered, as it didn't look like it was going anywhere.

Look at my answer, the second on the thread. It contains all the information needed to diagnose the problem (lack of menu entry or failed install). If ratpoison had worked from the terminal, I would have told the guy how to use alacarte to edit the menu. That was hours before stinkeye (who obviously also gave a good answer).

If post 2 answers the original question, post 3 is perfectly fine to suggest alternatives and/or comment on someone's attitude.

This is an extreme case, but I hold the position that some people don't deserve help.

---

### Post by koenn on 2011-05-24
Here, 
[http://ubuntuforums.org/showthread.php?t=1765839](http://ubuntuforums.org/showthread.php?t=1765839)

Just answer the question 

you might end up writing a paper, though.

---

### Post by Copper Bezel on 2011-05-24
[QUOTE=3Miro]This is an extreme case, but I hold the position that some people don't deserve help.[/QUOTE]
Oh, I agree completely, and it is an extreme case. I'm trying to cause as little irritation as I can, here, and I know I'm failing miserably. = / Like I said, I'd originally looked that up for *my* answer, not yours or tgm4883's, as an example of an unhelpful response, and I know that the confrontational user adds another completely separate set of considerations. Your answer was helpful diagnosis, and tgm4883's was, if I can say so, simple refusal to be walked on.

Edit:

[QUOTE=koenn]Just answer the question 

 you might end up writing a paper, though.[/QUOTE]
Oh wow, that's fun. He should have just asked for suggestions on relevant coursework.

---

### Post by 3Miro on 2011-05-24
> **koenn said:**
> Here, 
[http://ubuntuforums.org/showthread.php?t=1765839](http://ubuntuforums.org/showthread.php?t=1765839)

Just answer the question 

you might end up writing a paper, though.

He doesn't have an issue with his machine, he wants to have a tech chat. This is fine, but I personally don't find the topic interesting and I will ignore such a post.

---

### Post by 3Miro on 2011-05-24
> **Copper Bezel said:**
> Oh, I agree completely, and it is an extreme case. I'm trying to cause as little irritation as I can, here, and I know I'm failing miserably. = / Like I said, I'd originally looked that up for *my* answer, not yours or tgm4883's, as an example of an unhelpful response, and I know that the confrontational user adds another completely separate set of considerations. Your answer was helpful diagnosis, and tgm4883's was, if I can say so, simple refusal to be walked on.


You are not causing irritation, the OP on that thread was. After the first post, he had enough information to diagnose the problem. After that, calling him out on his attitude is perfectly fine with me.

---

### Post by rcayea on 2011-05-24
> **Copper Bezel said:**
> It's a matter of just (1) not being adversarial and (2) not questioning the user's logic in terms of the thing that they're actually trying to do. I do think that this is important. Telling a user that they're simply doing it wrong and should install some other piece of software or hardware, or most certainly asking "Why are you trying to do that?" is not going to be taken as helpful advice, and I've spoken to people who decided against Linux specifically because of this sort of "support." However, if that's actually a real question - "Well, what exactly are you trying to do?" - that's often a needed step in actually finding the best solution for the person asking the question.

If someone wanted to install an old copy of Photoshop 7, I'd explain Wine, check to find out that, hey, Photoshop 7 has a gold rating for Wine compatibility, and get them started; at the same time, I'd certainly mention that the current version of Krita might actually be the better bet and would of course be easier to get running.  

I don't really care that I am or anyone else is "working" for free. Work that is detrimental to its own purposes isn't free anything; it's a waste of everyone's time.

For the /usr question, I certainly wouldn't feel the need to shout, and I wouldn't see any harm in explaining that the folder could only be removed with root privileges so long as, in the same post, I explained that this would completely destroy the OS and render it unusable. 

I don't know, where does [this]("http://ubuntuforums.org/showthread.php?t=1766184") fall on the JATQ scale?



The one question that I have found that a person can ask another person (no matter the situation) is, Can I help you with something? Or, What can I help you with? This questioning approach would work well when a responder isn't sure how to help or needs more info.

---

### Post by JDShu on 2011-05-24
People can just ignore the answers they find unhelpful.

---

### Post by Bandit on 2011-05-24
> **tgm4883 said:**
> I actually was going to help the guy out until he turned vicious. I have a working python script that does what he wants, shame he was such a PITA.

Fir real..





/THREAD [SOLVED]

---

### Post by rcayea on 2011-05-24
> **JDShu said:**
> People can just ignore the answers they find unhelpful.

True. However, these forums are intended to be helpful and posting useless(or however you would like to describe them) responses isn't helpful.

---

### Post by forrestcupp on 2011-05-24
> **rcayea said:**
> True. However, these forums are intended to be helpful and posting useless(or however you would like to describe them) responses isn't helpful.

But as a regular forum member, I can post whatever I want as long I don't break the rules. Sometimes answering the question breaks the rules. In those cases, it would be more acceptable to post something the OP sees as unhelpful.

---

### Post by Irihapeti on 2011-05-24
I doubt that there is a one-size-fits-all rule; each case has to be decided on its merits.

I do think that the style or tone of a message often gets overlooked. Some ways of saying things get better responses, while others tend to provoke defensiveness.

Of course, you'll get people who are hypersensitive to what they perceive as put-downs or attacks. Sometimes, just about anything you say will be wrong, which can be very frustrating.

---

### Post by 3Miro on 2011-05-24
> **Irihapeti said:**
> I doubt that there is a one-size-fits-all rule; each case has to be decided on its merits.


+1. There is no one size fit all approach! With that:

/thread

---

### Post by Copper Bezel on 2011-05-24
Agreed. = ) I think Irihapeti's post has just about the whole issue covered, there.

---

### Post by rcayea on 2011-05-24
I must say, as someone who has authority at my job, I agree every situation is different. Variables change and it would be silly to reprimand with a one-size fits all attitude - especially, as mentioned in these forums with tone being so sensitive. Hopefully in the future everyone will respond with a one-size fits all response - answering the question. :)

---

### Post by Copper Bezel on 2011-05-25
I don't think he claimed to be Spiderman, unless I'm misreading something.

---

### Post by forrestcupp on 2011-05-25
> **Macskeeball said:**
> 
I disagree with the JATQ idea. If there's a better solution to something I ask about, I want to know about it. I thus do the same for others.
Me too, as long as it really is a better solution. Sometimes I just want my question asked instead of people telling me why I'm dumb for even asking it.

A great example is when someone asks for help with Opera and everyone tells him that he should be using Firefox or Chrome and he wouldn't have that problem. If you don't know about Opera, then you're not qualified to help me with my particular problem so don't waste my time belittling me.

---

### Post by 5149.5 on 2011-05-25
Currently there is a poster asking how to eliminate having to sudo to do anything on his computer and he would like to eliminate any login if possible. I started a reply to explain why that was such a bad idea but I thought about this thread and stopped. Good thread.

---

### Post by Copper Bezel on 2011-05-25
I think that "You can't" would be JATQ enough on that, or "You can't, not really" if you're feeling generous, or, "You can't without opening up a number of possible problems" if you're feeling verbose.

> A great example is when someone asks for help with Opera and everyone tells him that he should be using Firefox or Chrome and he wouldn't have that problem. If you don't know about Opera, then you're not qualified to help me with my particular problem so don't waste my time belittling me.
+1.

---

### Post by yetiman64 on 2011-05-25
> **5149.5 said:**
> Currently there is a poster asking how to eliminate having to sudo to do anything on his computer and he would like to eliminate any login if possible. I started a reply to explain why that was such a bad idea but I thought about this thread and stopped. Good thread.

Yep, seen a couple of threads by the same poster and by his tone decided to "JATQ - just **avoid** the question**"**. I'm also now glad to have seen this thread, made me think twice. 

One post in one of the threads actually "disappeared" after "just answering the question" :)

> I think that "You can't" would be JATQ enough on that, or "You can't,  not really" if you're feeling generous, or, "You can't without opening  up a number of possible problems" if you're feeling verbose.Unfortunately the OP was very clear "he knew ALL the risks" and clearly pointed out he didn't want anyone talking him out of what he wanted. He wanted Linux to have "the same security as Windows just like he has always used it" (the quotes here are really paraphrasing from memory-as I didn't even bother subscribing to any of the threads I saw).

One staff member gave the link to Rootsudo documentation (which does JATQ, but while respecting the forum policy of supporting Canonical's security model etc).

---

### Post by koenn on 2011-05-25
> **5149.5 said:**
> Currently there is a poster asking how to eliminate having to sudo to do anything on his computer and he would like to eliminate any login if possible. I started a reply to explain why that was such a bad idea but I thought about this thread and stopped. Good thread.

and the next thing that's going to happen is that same poster posting a rant about how his threads go unanswered and what sort of micky mouse support forum this is where people can't answer a simple question ...

:)

---

### Post by koenn on 2011-05-25
> **forrestcupp said:**
> 
A great example is when someone asks for help with Opera and everyone tells him that he should be using Firefox or Chrome and he wouldn't have that problem. If you don't know about Opera, then you're not qualified to help me with my particular problem so don't waste my time belittling me.

Except in the (hypothetical) case that you're using Opera because it's the only browser you know about - so while you're asking about Opera, you're thread is really about "please help me get a browser going, any decent browser ".

So in that case, it would be appropriate for people to check whether is actually Opera you need/want, so they should ask about that, and not just answer the question.

---

### Post by 3Miro on 2011-05-25
> **5149.5 said:**
> Currently there is a poster asking how to eliminate having to sudo to do anything on his computer and he would like to eliminate any login if possible. I started a reply to explain why that was such a bad idea but I thought about this thread and stopped. Good thread.

Ignore is a good policy.

As for removing sudo, if you understood the risks, then you would know enough to remove it yourself. Removing sudo is about as bad as deleting /usr.

---

### Post by tgm4883 on 2011-05-25
> **koenn said:**
> Except in the (hypothetical) case that you're using Opera because it's the only browser you know about - so while you're asking about Opera, you're thread is really about "please help me get a browser going, any decent browser ".

So in that case, it would be appropriate for people to check whether is actually Opera you need/want, so they should ask about that, and not just answer the question.

Unless he is in the community cafe and not a support forum, in which case he may be requesting help singing opera (or going to the opera, etc)

---

### Post by forrestcupp on 2011-05-25
> **tgm4883 said:**
> Unless he is in the community cafe and not a support forum, in which case he may be requesting help singing opera (or going to the opera, etc)

In which case, I would recommend a vocal spray called Entertainer's Secret. :)

---

### Post by koenn on 2011-05-25
> **tgm4883 said:**
> Unless he is in the community cafe and not a support forum, in which case 

--- in which case the thread should be moved to the appropriate forum.

---

### Post by uRock on 2011-05-25
> **rcayea said:**
> The issue is this. When someone asks a questions on these forums, someone will reply and not answer the question and basically say, “no, don't do that, just get this, that, and this and it is better”.

I have seen a lot of that recently. Instead of helping with the problem, many people try to get the OP to do something else, like revert to Classic Ubuntu, when the OP wants help with Unity or people recommending the OP install Mint, because the OP is having trouble with Unity. I have seen many cases like that, where a fix could be done, but folks recommend something totally different from what the OP is asking. It happens and it is sad.

On a side note. I have nothing against Mint or any other distro, but I would never go to another distro's forums and recommend Ubuntu every time I see someone having problems with their install.

---

### Post by tgm4883 on 2011-05-25
> **koenn said:**
> --- in which case the thread should be moved to the appropriate forum.

...

---

### Post by Copper Bezel on 2011-05-25
Yeah, I mean, I don't *think* UF has a performing arts subforum. I mean, that'd be kind of cool, don't get me wrong.

---

### Post by lykwydchykyn on 2011-05-25
> **uRock said:**
> I have seen a lot of that recently. Instead of helping with the problem, many people try to get the OP to do something else, like revert to Classic Ubuntu, when the OP wants help with Unity or people recommending the OP install Mint, because the OP is having trouble with Unity. I have seen many cases like that, where a fix could be done, but folks recommend something totally different from what the OP is asking. It happens and it is sad.

On a side note. I have nothing against Mint or any other distro, but I would never go to another distro's forums and recommend Ubuntu every time I see someone having problems with their install.

Yeah, but to play devil's advocate -- suppose you had a problem with Ubuntu that you wrestled with for days or weeks, trying every suggestion you could find.  Then you went and tried $DISTRO and it all magically worked.  

Now you're back on the forums and you see someone having the same problem you had.  Would it really be un-helpful to point this person to a possible (if not ideal) solution?

I keep seeing these threads in the cafe about how everyone who's helping is doing it all wrong, and we need to stop doing this or that.  It sincerely has a chilling effect on my willingness to help, lest I do it wrong.

---

### Post by 3Miro on 2011-05-25
> **lykwydchykyn said:**
> Yeah, but to play devil's advocate -- suppose you had a problem with Ubuntu that you wrestled with for days or weeks, trying every suggestion you could find.  Then you went and tried $DISTRO and it all magically worked.  

Now you're back on the forums and you see someone having the same problem you had.  Would it really be un-helpful to point this person to a possible (if not ideal) solution?


What uRock is talking about is more along the lines of Unity haters just trolling. A simple issue about how to adjust effects with compiz does not warrant a response about another distro.

---

### Post by tgm4883 on 2011-05-25
> **3Miro said:**
> What uRock is talking about is more along the lines of Unity haters just trolling. A simple issue about how to adjust effects with compiz does not warrant a response about another distro.

It's getting bad enough that I'm starting to remember them by name.

---

### Post by lykwydchykyn on 2011-05-25
> **3Miro said:**
> What uRock is talking about is more along the lines of Unity haters just trolling. A simple issue about how to adjust effects with compiz does not warrant a response about another distro.

Fair enough, but the problem is that when we have threads where everyone is making vague complaints about people responding to questions a certain way, it can make well-intentioned people feel unnecessarily indicted.  And, frankly, the well-intentioned people are the only ones likely to change their behavior based on such complaints.

---

### Post by bodhi.zazen on 2011-05-25
This thread has gotten long and I got bored reading all the responses.

The quality of answers can be variable on the forums, such is the nature of the forums.

One advantage of Linux is that there is more then one way of doing something and sometimes the OP is going about matters a long or more difficult way.

In an ideal world, JATQ sounds good, but for reasons cited by others in this thread is going to be impractical.

---

### Post by koenn on 2011-05-25
> **lykwydchykyn said:**
> Fair enough, but the problem is that when we have threads where everyone is making vague complaints about people responding to questions a certain way, it can make well-intentioned people feel unnecessarily indicted.  

my simple black and white view on the matter : 
if there are people who actually give support, and then other people do nothing but talk about the ones doing the support, then the ones doing the support have right of way. Their way.

---

### Post by uRock on 2011-05-25
> **lykwydchykyn said:**
> Yeah, but to play devil's advocate -- suppose you had a problem with Ubuntu that you wrestled with for days or weeks, trying every suggestion you could find.  Then you went and tried $DISTRO and it all magically worked.  

Now you're back on the forums and you see someone having the same problem you had.  Would it really be un-helpful to point this person to a possible (if not ideal) solution?

I keep seeing these threads in the cafe about how everyone who's helping is doing it all wrong, and we need to stop doing this or that.  It sincerely has a chilling effect on my willingness to help, lest I do it wrong.
The situations where I have seen the things I mentioned were folks asking simple things such as placing the weather on the top bar or adding/removing icons to the Unity panel. Do you really think telling them to leave Ubuntu would be easier? People want fixes for their problems. I would rather see people be advised to reinstall 10.04, than have people tell others to go to Mint based on personal preference.

---

### Post by uRock on 2011-05-25
> **3Miro said:**
> What uRock is talking about is more along the lines of Unity haters just trolling. A simple issue about how to adjust effects with compiz does not warrant a response about another distro.
Exactly.

---

### Post by rcayea on 2011-05-25
This thread has many great responses. I know many of you, as I read this thread, say don't tell me how to answer or maybe answering the OP with a direct answer is not best at times. To those folks, I am not trying to ruffle feathers, but why not answer the original question first and then provide that other great idea? A responder would only be spreading two answers and thus twice as much knowledge.

Side Note: Totally funny was the "Just Avoid The Question" response.

---

### Post by el_koraco on 2011-05-25
> **koenn said:**
> my simple black and white view on the matter : 
if there are people who actually give support, and then other people do nothing but talk about the ones doing the support, then the ones doing the support have right of way. Their way.

/thread

---

### Post by forrestcupp on 2011-05-25
> **rcayea said:**
> but why not answer the original question first and then provide that other great idea? A responder would only be spreading two answers and thus twice as much knowledge.

I completely agree, except in the cases where the answer to the original question is harmful.

---

### Post by Thewhistlingwind on 2011-05-26
> **rcayea said:**
> I must say, as someone who has authority at my job, I agree every situation is different. Variables change and it would be silly to reprimand with a one-size fits all attitude - especially, as mentioned in these forums with tone being so sensitive. Hopefully in the future everyone will respond with a one-size fits all response - answering the question. :)

I'm not telling people how to bork their system in anything less then high-level terms. Period.

---

### Post by Antarctica32 on 2011-05-26
> **Simian Man said:**
> "Hey my / partition is full, and I need to make some space.  It seems "/usr/" is the biggest space-waster.  What is the command to delete this directory recursively?"

Should you "just answer" this question???

lawl
well obviously not in that case.

---

