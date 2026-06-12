---
title: "User accounts for Apache web space?"
date: 2011-02-10
forum: Server Platforms
---

### Post by Wolf_22 on 2011-02-10
What I'm trying to do here is simple to understand but apparently difficult to do as everyone I've asked for help from seems to approach it from different angles...

I need to provide web space for my friends where they can access their web space accounts via "http://123.123.123.123/~username". They already have access to it through the use of the main admin account, but I would like for them to use their own designated access level accounts to prevent possible problems in the future (i.e. - accidental type accidents, like removal of files and directories, etc., not to mention malicious intent...)

Here's what I need for these accounts:

1.) SSH / SFTP access. I need to provide each user with the capability to use their preferred application, like WinSCP, PuTTY, SharePoint, etc. This is mandatory.

2.) I can't allow them the ability to edit, delete, or write to folders and or files outside their own user directories because that will lead to obvious problems. This, too, is mandatory.

3.) Right now, the server is on a static IP address with no domain name. So what this means is that the user accounts will be accessed through the following URL form: "http://123.123.123.123/~username", but what it would equate to on the Ubuntu side is something like "/home/username". I'm not sure if this is a good thing or not, but in whatever case, feel free to provide any insight into what a preferred way is for creating user accounts like what I'm trying to do here... I just need it to work!

I'm at my wits end with all this as I'm wasting time with sorting through the various links and tutorials people have suggested in stride. It's so frustrating. I would appreciate any help you all can provide me and if you're unsure about anything, please let me know and I'll elaborate and clarify. :)

---

### Post by tredegar on 2011-02-10
I have read your other threads in your 6-post posting history.
Eg [here]("http://ubuntuforums.org/showthread.php?t=1640261") (which you have not followed-up on, instead you started this new thread).

The problem seems to be that you do not understand the concepts of linux permissions [**r : w : x**] to **owner : group : world**

I appreciate that you are frustrated, and feel sorry for you, but you need to understand that it is impossible for us to hand-hold you through all of this, because every user's requirements are different. Please read up on linux permissions, and groups and how they are handled until your personal light bulb lights up.

Then you'll be:

"Yes. I'll create a group called ..... and assign the following users this group and make these files part of that group, and assign the right permissions, and then all will be both sweet and secure.

Then you have got it :)

I know you can do it. You just need to read, digest, and _understand_  how it all works. 

Please learn to walk before you try to run. Homework is needed here.

Good luck.

---

### Post by Wolf_22 on 2011-02-11
> **tredegar said:**
> I have read your other threads in your 6-post posting history.
Eg [here]("http://ubuntuforums.org/showthread.php?t=1640261") (which you have not followed-up on, instead you started this new thread).

The problem seems to be that you do not understand the concepts of linux permissions [**r : w : x**] to **owner : group : world**

I appreciate that you are frustrated, and feel sorry for you, but you need to understand that it is impossible for us to hand-hold you through all of this, because every user's requirements are different. Please read up on linux permissions, and groups and how they are handled until your personal light bulb lights up.

Then you'll be:

"Yes. I'll create a group called ..... and assign the following users this group and make these files part of that group, and assign the right permissions, and then all will be both sweet and secure.

Then you have got it :)

I know you can do it. You just need to read, digest, and _understand_  how it all works. 

Please learn to walk before you try to run. Homework is needed here.

Good luck.

Was half of that really even necessary?

---

### Post by Habitual on 2011-02-13
based on tredegar's first 2 lines of his reply, I'd say it was totally necessary.

"I have read your other threads in your 6-post posting history.
Eg [here]("http://ubuntuforums.org/showthread.php?t=1640261") (which you have not followed-up on, instead you started this new thread)."

If you never follow through, you will never meet with success.

[http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html](http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html) will help you keep users in their home directories AND Allow editing of their apache content.

Good Luck.

---

### Post by Wolf_22 on 2011-02-13
I beg to differ.

Nobody on Earth has the right to belittle someone with condescending and unsociable remarks like the ones that person made to me just because I forgot to respond to something on some online forum. If I forgot to post my own found solution to a problem nobody is likely to even encounter due to its unique user requirements, then is that justification to act like a jerk off? Nope, sorry: it's not.

The situation presented in that unfinished thread (that is now almost 2 months old and gaining popularity by the hour through continual whining) had absolutely nothing to do with permissions anyway (as was pompously asserted by tredegar, the master sensei of Ubuntu Zen). 

Thankfully, I'm not, but if I were as OCD as tredegar, I would bet anything I have that my perusal of his entire posting history would reveal a rap sheet comprised of belittling remarks made to users in similar straights I was in. These same users should be accepted into this community with open arms and smiley faces, regardless of their technical prowess level, all important "bean count", or acceptable follow-ups some 20 year Ubuntu vet would drop jaw to. As a matter of fact, I still can't believe that person even took the time needed to review my entire history on here only to pucker lip about something they could have simply ignored altogether, but instead of changing the radio station to avoid bad music... 

If they had to be adament about slapping my hand, the very least they could do is post a tactful reminder like so:

"*Hey Wolf. I noticed that you posted something similar in another thread. The link is here: <link>. Is this the same situation? In whatever case, would you mind letting the users over there know what you came up with? It would help the forums out a lot and if it's the same thing, then we'll go ahead and close this thread. Thanks.*"

But no... We couldn't do that. Instead, we had to reinforce someone's accidental radio silence with remarks like "hand-holding", "walk before you run", and "homework is needed here" because we all love that underground referent rep point that comes with putting people down for the sake of cliche hackitude. Congratulations, someone earned a trophy for being this year's most unacceptable *** clown. Moving along...

Don't get me wrong, I can appreciate the annoyance of "unfinished forum threads" and how much excruciating pain and sheer agony it causes for this "friendly community of Linux deities" to siphon through when trying to either answer or post about their own issues. I get that. But oh well. Crap happens. Some stores don't have the candy bar or coffee brands we all like, but you don't see people going ape over it...

:)

But I know that everything I've said up to this point will be for nothing. You'll continue to chastise and berate me for apparently leaving an "Instant e-mail response..." option unchecked upon creating 2 threads. I'll attract an elite pack around here for being "rambunctious on the forum" and stirring up chaos in the midst of a perfect Ubuntu forum equilibrium. Everything I've said is ludicrous and no matter how much Einstein I have in me, my logic will be irrational in your mind and for no other reason than forgetting to respond to some erroneous post that will be forgotten in another week when we finally blow our loads about this little happenstance...

Oh, and thanks for the "Good Luck" wish, Habitual (as well as the link to a resource that takes a somewhat different approach as that of tredegar's perfect solution...)

---

### Post by Habitual on 2011-02-14
So, I shouldn't expect a Christmas Card this year?

---

### Post by lisati on 2011-02-14
Moved to "Server Platforms"

Let's settle down a bit here, folks!

---

### Post by Wolf_22 on 2011-02-14
> So, I shouldn't expect a Christmas Card this year? 	

As much as I don't want to admit it, that was pretty funny. :D

> Let's settle down a bit here, folks! 	

I agree. Maybe I lost my temper a bit. Either way, I'll try to make sure I respond to all my posts henceforth. ;)

---

### Post by Habitual on 2011-02-14
and I'll take a Pill.

---

