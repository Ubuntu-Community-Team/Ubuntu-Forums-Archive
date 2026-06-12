---
title: "Some of the concepts used in Vista"
date: 2007-06-09
forum: The Cafe
---

### Post by maniacmusician on 2007-06-09
I was reading an article yesterday, and it got me thinking. Vista is actually (mostly) built on good concepts that just have bad implementations. I was reading the article and thinking, "Wow, this sounds like a really good OS". On the other hand, I've actually used Vista, and it really is **not** a good OS. 

So, what then? Shouldn't we take some of those concepts and do them right? I mean, of course we should innovate and come up with our own stuff. But do we really have to refuse to use ideas that Microsoft came up with? They're good ideas, and if you think about it, Microsoft didn't come up with those ideas...the developers that it hires and pays came up with them. 

In addition to coming up with cool new things, I think we should really also learn from the mistakes of other OS's and do it right this time. 

Here's the article I was reading; [http://arstechnica.com/reviews/os/vista-under-the-hood.ars](http://arstechnica.com/reviews/os/vista-under-the-hood.ars)

---

### Post by kamaboko on 2007-06-09
Good post.  Interesting article.

---

### Post by kerry_s on 2007-06-09
okay, but the artical just basicly tells how vista is just now copying how ubuntu and mac os do security. there's no concept there. if your using ubuntu your already using a more advanced system. linux is already innovating more than any other os out there, yes even more than mac. microsoft have really never had a idea of there own, everything is stolen or bought.

---

### Post by Adamant1988 on 2007-06-09
> **kerry_s said:**
> okay, but the artical just basicly tells how vista is just now copying how ubuntu and mac os do security. **there's no concept there. if your using ubuntu your already using a more advanced system.** linux is already innovating more than any other os out there, yes even more than mac. microsoft have really never had a idea of there own, everything is stolen or bought.

If you're speaking of security, I cannot agree. UAC is superior to sudo, Microsoft's implementation was just flawed. Linux, actually, speaking of the kernel just kind of does it's own thing.  The complete operating system GNU/Linux really hasn't done that much to innovate at all, particularly with user interfaces.  To be honest, innovation in the software realm as we see it today is just a new way of looking at an old idea.  True "Wow, I've never seen that before" innovation simply does not happen very often at all. 

Also, Microsoft has never stolen any idea.  Stealing implies that the item (idea in this case) is removed from it's rightful owner and is no longer in that owner's possession.  The notion that ideas can be stolen is simply not true, nor can they be purchased.  The software can be purchased, however. 

I would certainly applaud using Microsoft's concepts, as I think they're a solid approach.

---

### Post by kamaboko on 2007-06-09
> **kerry_s said:**
> okay, but the artical just basicly tells how vista is just now copying how ubuntu and mac os do security. there's no concept there. if your using ubuntu your already using a more advanced system. linux is already innovating more than any other os out there, yes even more than mac. microsoft have really never had a idea of there own, everything is stolen or bought.

I love it when someone posts comments about an article they obviously haven't read.

---

### Post by Lem on 2007-06-10
UAC is a good idea. However, as the article hints - most users will happily enter their credentials to get the latest widget they've downloaded from the internet onto their machines.
And herein lies the main problem with windows - the varied number of software channels. Most linux users get their software from repositories. These are managed and details of any malicious code would cause a major posting outbreak on the community forums. Users will still add 3rd party repositories to their system which could open them to vulnerabilities but these are also generally discussed through the community forums.

Even the smallest windows program often wants to add registry keys, install new dlls etc. ,whereas a lot of handy scripts and widgets in Linux will happily run in the home directory simply levering the tools and code already available in the native OS.

It's my opinion that the repo system and general 'community' attitude of Linux users (who frequents a Windows forum?) does more to hinder the spread of malware than a specific security system.

---

### Post by kerry_s on 2007-06-10
> **Adamant1988 said:**
> If you're speaking of security, I cannot agree. UAC is superior to sudo, Microsoft's implementation was just flawed. Linux, actually, speaking of the kernel just kind of does it's own thing.  The complete operating system GNU/Linux really hasn't done that much to innovate at all, particularly with user interfaces.  To be honest, innovation in the software realm as we see it today is just a new way of looking at an old idea.  True "Wow, I've never seen that before" innovation simply does not happen very often at all. 

**Also, Microsoft has never stolen any idea.  Stealing implies that the item (idea in this case) is removed from it's rightful owner and is no longer in that owner's possession.  The notion that ideas can be stolen is simply not true, nor can they be purchased.  The software can be purchased, however. **

I would certainly applaud using Microsoft's concepts, as I think they're a solid approach.

x employee, they did/do take.

---

### Post by kerry_s on 2007-06-10
> **kamaboko said:**
> I love it when someone posts comments about an article they obviously haven't read.

i read it.

---

### Post by bapoumba on 2007-06-10
Hi there :)

---

### Post by kerry_s on 2007-06-10
> **bapoumba said:**
> Hi there :)

Letting it go, nothing to see here, move along. ;)

---

### Post by EndPerform on 2007-06-10
UAC doesn't really strike me as superior.  Basically, when you try to do something you need admin privileges for, it pops up and asks you to click continue if you're running as a user with admin rights.  If you aren't, it asks for the admin password.  Sudo asks for a password and temporarily grants admin rights.  Root is disabled by default in Ubuntu, so you wouldn't be running as a user with root privileges to begin with, so you get the password.  If anything, I'd say they are equal in their protection.

---

### Post by maniacmusician on 2007-06-10
I didn't mean to imply UAC was superior. I dislike it, because it really doesn't even have a potential of working out that well. The only thing that's good about it is the fact that it lasts only for one instance, where as sudo lasts for a certain amount of time.

But, this is inconsequential since even though sudo lasts for a while, it is restricted to the specific shell that it's run from. So unless the invading exploit can take over that specific shell, it can't use sudo.

---

### Post by mech7 on 2007-06-10
> **Lem said:**
> UAC is a good idea. However, as the article hints - most users will happily enter their credentials to get the latest widget they've downloaded from the internet onto their machines.
And herein lies the main problem with windows - the varied number of software channels. Most linux users get their software from repositories. These are managed and details of any malicious code would cause a major posting outbreak on the community forums. Users will still add 3rd party repositories to their system which could open them to vulnerabilities but these are also generally discussed through the community forums.


You don't want to know how many times I have had to add new repositories, or download files because either the repositories are out of date or they refuse to update it because the software contains new features... Repositories are a nice idea, but that is all it is in real life it doesn't work.

---

### Post by EndPerform on 2007-06-11
> **maniacmusician said:**
> I didn't mean to imply UAC was superior. I dislike it, because it really doesn't even have a potential of working out that well. The only thing that's good about it is the fact that it lasts only for one instance, where as sudo lasts for a certain amount of time.

But, this is inconsequential since even though sudo lasts for a while, it is restricted to the specific shell that it's run from. So unless the invading exploit can take over that specific shell, it can't use sudo.

Sorry, I should have quoted... someone else on the thread had mentioned it may be superior.  When I was trying out Vista when I first got my laptop, the first thing I researched was how to turn off UAC.  I find it annoying.

---

### Post by LaRoza on 2007-06-11
If you have to use Vista, creating a standard account in which to work in would probably be more beneficial than using the mandatory admin account. 

I did that; however, explorer keeps crashing more than usual in the new account. I don't know why.

---

### Post by runningwithscissors on 2007-06-11
> **maniacmusician said:**
> I didn't mean to imply UAC was superior. I dislike it, because it really doesn't even have a potential of working out that well. The only thing that's good about it is the fact that it lasts only for one instance, where as sudo lasts for a certain amount of time.

But, this is inconsequential since even though sudo lasts for a while, it is restricted to the specific shell that it's run from. So unless the invading exploit can take over that specific shell, it can't use sudo.
Even though I don't use sudo, I think the time limit is configurable. It was only set to 15 minutes because people whinge about typing in the password for every administrative command.

---

### Post by Nikron on 2007-06-11
> **runningwithscissors said:**
> Even though I don't use sudo, I think the time limit is configurable. It was only set to 15 minutes because people whinge about typing in the password for every administrative command.

Yeah, I personally have moved downed the window of time to 3 minutes.

---

