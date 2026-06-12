---
title: "Why is Pidgin set to log by default?"
date: 2009-07-26
forum: The Cafe
---

### Post by AmyRose on 2009-07-26
I have been curious about this. Why did Ubuntu decide to patch Pidgin so that the default is to save all conversations by default? Isn't this a privacy risk? At the very least, the hard drive can fill up (I know people with older computers and smaller hard drives).

I am fully aware that I can change this setting. However, isn't Ubuntu at least partially targeted at people who are new to computers and won't go looking for this option?

Sorry if this has been posted already, or if it's in the wrong forum, but I would like to know this...

---

### Post by p0cky84 on 2009-07-26
> **AmyRose said:**
> I have been curious about this. Why did Ubuntu decide to patch Pidgin so that the default is to save all conversations by default? Isn't this a privacy risk? **At the very least, the hard drive can fill up** (I know people with older computers and smaller hard drives).

I am fully aware that I can change this setting. However, isn't Ubuntu at least partially targeted at people who are new to computers and won't go looking for this option?

Sorry if this has been posted already, or if it's in the wrong forum, but I would like to know this...

Thats where I lol'd : )

---

### Post by AmyRose on 2009-07-26
> **p0cky84 said:**
> Thats where I lol'd : )
What if you're on a netbook with a 4 GB SSD? Don't people run Ubuntu on those?

---

### Post by Ozor Mox on 2009-07-26
I have a whole ton of logs saved by Pidgin and the directory still barely makes it to half a megabyte, so I doubt the storage space would be a problem. Still though, I would have expected it to be off by default. I was quite surprised when I first discovered a directory full of chat logs.

---

### Post by darthmob on 2009-07-26
> **AmyRose said:**
> What if you're on a netbook with a 4 GB SSD? Don't people run Ubuntu on those?It's just text! My pidgin logfiles that go back to october 2007 amount to less than 4mb.

Logging should be disabled as default, though.

---

### Post by moster on 2009-07-26
My log is 20 MB. First log is from 2004! You will not save significant space I guess.

---

### Post by AmyRose on 2009-07-27
I have a lot of friends I talk to on-line every day, and those logs have gotten pretty big, especially when they're in HTML format (the default). My ~/.purple/logs directory has grown to 200 MB+ when I used to save all logs (for about a year or two).

But the main point is the privacy aspect. If you don't know you're saving all those logs, and someone steals your laptop (remember, the default is to allow you to drop to a root shell prompt, via recovery mode, in GRUB without a password!), they might end up knowing a lot more about you than you'd want a random stranger to know.

EDIT: I actually currently have 10 MB of logs from just one person, starting from last March. So these things can add up if your conversations last for a couple of hours every single day. But that isn't even the main issue here.

---

### Post by binbash on 2009-07-27
It is not about size but privacy.It should be disabled default

---

### Post by moster on 2009-07-27
Now when you mention it. I think it was disabled before. It is enabled by default in 9.4. Although, I could be wrong.

---

### Post by Sand &amp; Mercury on 2009-07-27
I don't see the problem. Logging is very very useful when you're chatting to folks and sharing information that you might need to refer to. And really... when you're on the internet, consider it a rule of thumb that anything you put out to it, is public domain and will probably be stored somewhere.

---

### Post by Mornedhel on 2009-07-27
> **AmyRose said:**
> But the main point is the privacy aspect. If you don't know you're saving all those logs, and someone steals your laptop (remember, the default is to allow you to drop to a root shell prompt, via recovery mode, in GRUB without a password!), they might end up knowing a lot more about you than you'd want a random stranger to know.

If someone stole your laptop, he has physical access to it. If he has physical access to it, no password, nothing short of full disk encryption, will prevent him from accessing your data.

If someone took the trouble of stealing *your* laptop, for the purposes of perusing *your* data, you can be sure he also has access to your mail account and other niceties. Saved passwords in Firefox also would be much more useful and interesting to him.

If that someone just took off with your laptop while you weren't looking, then he probably doesn't care about the data.

---

### Post by AmyRose on 2009-07-27
Why was it changed though? Sure, doing anything over the Internet is a privacy risk in itself, but why was the default explicitly changed by Ubuntu?

> I don't see the problem. Logging is very very useful when you're chatting to folks and sharing information that you might need to refer to.Yes, it is a very useful feature, but should it really be a default? I know a lot of people who forget that the right mouse button exists, would never go into their Pidgin config directories, and would never know that Pidgin is saving all their conversations (which is exactly why the upstream default is off). [http://pidgin.im/pipermail/devel/2008-November/007002.html](http://pidgin.im/pipermail/devel/2008-November/007002.html)

---

### Post by khc on 2009-07-27
(Pidgin developer here)

Internet browsers by default stores history, cookies, and pages from the websites that you visit, so it's not totally unreasonable to have logging enabled by default too. We suggested to the Ubuntu developers to try enabling it by default to see if people will object before doing this upstream, and so far this is the only instance that I know of.

---

### Post by jimrz on 2009-07-27
> **moster said:**
> Now when you mention it. I think it was disabled before. It is enabled by default in 9.4. Although, I could be wrong.

checked a box still running 8.04 and it was disabled (I beleive, by default) on it. not sure about 8.10

---

### Post by Tipped OuT on 2009-07-27
> **AmyRose said:**
> What if you're on a netbook with a 4 GB SSD? Don't people run Ubuntu on those?

Oh yeah, KB's of KB's of text sure is going to fill that 4 GB hard drive up. :rolleyes: The logs wouldn't fill a memory stick with 32 MB's of free space, until after 3 years or so.

> **AmyRose said:**
> Why was it changed though? Sure, doing anything over the Internet is a privacy risk in itself, but why was the default explicitly changed by Ubuntu?

Yes, it is a very useful feature, but should it really be a default? I know a lot of people who forget that the right mouse button exists, would never go into their Pidgin config directories, and would never know that Pidgin is saving all their conversations (which is exactly why the upstream default is off). [http://pidgin.im/pipermail/devel/2008-November/007002.html](http://pidgin.im/pipermail/devel/2008-November/007002.html)

Just turn it off then. Problem solved.

---

### Post by AmyRose on 2009-07-28
> **khc said:**
> (Pidgin developer here)

Internet browsers by default stores history, cookies, and pages from the websites that you visit, so it's not totally unreasonable to have logging enabled by default too. We suggested to the Ubuntu developers to try enabling it by default to see if people will object before doing this upstream, and so far this is the only instance that I know of.Thanks for your input. Most people I know are aware of what web browsers store on their hard drives, but most of them wouldn't check to see if Pidgin is logging all conversations by default.> **Tipped OuT said:**
> Oh yeah, KB's of KB's of text sure is going to fill that 4 GB hard drive up. :rolleyes: The logs wouldn't fill a memory stick with 32 MB's of free space, until after 3 years or so.Obviously you haven't read any of my other posts. (It's gotten into hundreds of megabytes for me.) Even though it's privacy, rather than size, that I'm primarily talking about.> **Tipped OuT said:**
> Just turn it off then. Problem solved.Way to miss my point. Are most computer users really going to check to see if Pidgin is saving every conversation by default? Seriously. I know physical access trumps all, especially with Firefox passwords and such, but for the average user, it probably is a good idea to store as minimal as possible without the user's knowledge.

---

### Post by Tipped OuT on 2009-07-28
> **AmyRose said:**
> Obviously you haven't read any of my other posts. (It's gotten into hundreds of megabytes for me.) Even though it's privacy, rather than size, that I'm primarily talking about.Hundreds of megabytes? Are you serious? What are doing? Typing novels per message? :P It's not any one's fault if you spend all your time on online, messaging people. Seriously, that's outrageous. I wouldn't be able to make a log so big with in 50 years! :shock:

> **AmyRose said:**
> Way to miss my point. Are most computer users really going to check to see if Pidgin is saving every conversation by default? Seriously. I know physical access trumps all, especially with Firefox passwords and such, but for the average user, it probably is a good idea to store as minimal as possible without the user's knowledge.

I missed the point? What point? There is no point, you're ranting over something that's not even a big deal. There's a easy solution. Turn it off. All the IM's I know, keep logs by default. Including Windows Live Messenger (used by millions of average users.) ](*,)


Oh, and the average user wouldn't really care. In fact, most would find it a rather useful feature. Logs are always important.


I'm Sorry if I sound aggressive. Going through a lot right now.

-**TT**

---

