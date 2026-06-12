---
title: "Square Root of RAM for swap space formula"
date: 2016-01-27
forum: Ubuntu, Linux and OS Chat
---

### Post by varenorn on 2016-01-27
I'm starting vague plans on how my next Linux installation could/should be, which includes working out what size of RUNTIME memory swap partition I should have, which may be encrypted. (To allow suspend to disk, I'm thinking of having a separate unencrypted swap partition).

To this end, [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) looks very useful.  However, I have one main question regarding it (to stay on topic).

The FAQ mentions having round(sqrt(RAM)) for the minimum swap space.  How was this formula derived?  How did it come into being?

Just curious to find out the different methods for working out swap partition space.

---

### Post by grahammechanical on 2016-01-27
> Hibernation (suspend-to-disk) The  hibernation feature (suspend-to-disk) writes out the contents of RAM to  the swap partition before turning off the machine. Therefore, your swap  partition should be at least as big as your RAM size. The hibernation  implementation currently used in Ubuntu, swsusp, needs a swap or suspend  partition. It cannot use a swap file on an active file system.

No formula. Just sense & experience. With Hibernation we need a swap partition large enough to hold the maximum amount of data that could possibly be held in RAM.

Depending on the user's work practices, machines with several GB of RAM may rarely use swap. If hibernation was never going to be attempted then a swap partition less than the amount of RAM would be acceptable.

Opinions about the size of swap have altered since the days when machines came with less than 1 GB RAM. In those days swap was very likely necessary and 2 x RAM was often suggested. Times changes and views change.
> 
For less then 1GB of physical memory (RAM), it's  highly recommended that the swap space should, as a base minimum, be  equal to the amount of RAM. Also, it's recommended that the swap space  is maximum twice the amount of RAM depending upon the amount of hard  disk space available for the system because of diminishing returns.


For  more modern systems (>1GB), your swap space should be at a minimum  minimum be equal to your physical memory (RAM) size "if you use  hibernation", otherwise you need a minimum of round(sqrt(RAM)) and a  maximum of twice the amount of RAM. The only downside to having more  swap space than you will actually use, is the disk space you will be  reserving for it. 


The  "diminishing returns" means that if you need more swap space than twice  your RAM size, you'd better add more RAM as Hard Disk Drive (HDD)  access is about 10³ slower then RAM access, so something that would take  1 second, suddenly takes more then 15 minutes! And still more then a  minute on a fast Solid State Drive (SSD)...

round(sqrt(RAM))?

No idea what that means. Bad spelling? Bad grammar? But if you like being baffled by science ...

[https://www.reddit.com/comments/2v8dty](https://www.reddit.com/comments/2v8dty)

Regards.

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
It seems pretty clear what it MEANS and of course it is a formula or at least implies one.  But why someone chose to express themselves so bizarrely instead of using English I can't imagine. I think it would be a legitimate expression in  some languages but my bash can't make anything of it. C, maybe.

And as to the logic of recommending the square root of the amount of RAM as the minimum amount of swap, that is even harder to fathom. Doing so and offering no explanation is . . . twisted.

If there really is sense to this, I'd love to see an explanation. Could this be someone's idea of a clever prank?

---

### Post by matt_symes on 2016-01-28
> round(sqrt(RAM))?

No idea what that means. Bad spelling? Bad grammar?

It means take the square root of the amount of ram you have installed and then round it (i suspect round up in this case) to the nearest whole number.

6B ram
sqrt(6) = ~2.45
round up = 3G swap.

Really though, swap space required depends on you usage.

You can create swap files on the fly and to this end the package *swapspace* may be useful for some. There was/is debate on the Ubuntu mailing list as to whether if it should be added by default in 16.04.

There's also the zram-config package; compressed swap in memory.

I hibernate this laptop so my amount of swap is the amount of RAM i have +1 G => 5G swap partition.

Drive's are cheap and so file or partition swap space size doesn't bother me.

> But if you like being baffled by science ...

[https://www.reddit.com/comments/2v8dty](https://www.reddit.com/comments/2v8dty)

Thanks for posting this.

---

### Post by Dreamer Fithp Apprentice on 2016-01-28
Right. The meaning is obvious. But none of this addresses OP's question, which I think is a darned good one:
> **varenorn said:**
>   How was this formula derived?  How did it come into being?Unless it's somebody's idea of a joke, there must be some logic behind it, and like OP, I'd really like to know what it is, especially since it is so at variance with everything I've read on the subject, and seemingly totally contrary to common sense.

---

### Post by matt_symes on 2016-01-28
> **Dreamer Fithp Apprentice said:**
> Right. The meaning is obvious.

Do you *really* think that round(sqrt(RAM)) is obvious to everybody who frequents this forum, everybody that might stumble across this forum or that page from a web search or everybody on the planet ?

The point being that because it obvious to you, that does not mean it's obvious to others.

> But none of this addresses OP's question, which I think is a darned good one:

Unless it's somebody's idea of a joke, there must be some logic behind it, and like OP, I'd really like to know what it is, especially since it is so at variance with everything I've read on the subject, and seemingly totally contrary to common sense.

The post has been answered.

> Really though, swap space required depends on you usage.

On a high end desktop, where hibernation is not required and swapping is never expected to happen then the swap space required is expected to be zero.

On a system where it is expected to hibernate then the swap size has to be at least the size of RAM plus some headroom to account for the worst hibernation case.  

Anywhere in between it's a heuristic, a rule of thumb and really does depend on how the system is expected to be used.

That formula gives an arbitrary lower limit. One that is not set in stone, but a sensible value for a given amount of total system memory.

Why was *that* specific formula suggested by the author of that section of the documentation page ? I've no idea. It gives a sensible lower limit but is not to be preferred over any other formula that also gives a sensible lower limit and it's designed for users that may be less experienced in running Linux. The rest of us have a pretty good idea what our swap usage is going to be and that, my friend, comes with experience.

---

### Post by Old_Grey_Wolf on 2016-01-28
=round(sqrt(RAM)) is an equation used in spreadsheets; such as, LibreOffice Calc. Substitute the amount of ram in GB units for "RAM". I have no idea where they came up with that equation though.

@matt_symes, re #4 above, the round function in spreadsheets don't round up to 3 as in you example. It would round down to 2 which is the closest integer. There are roundup and rounddown spreadsheet functions to force it to round up or down. ;)

---

### Post by matt_symes on 2016-01-28
> **Old_Grey_Wolf said:**
> =round(sqrt(RAM)) is an equation used in spreadsheets; such as, LibreOffice Calc. Substitute the amount of ram in GB units for "RAM". I have no idea where they came up with that equation though.

Interesting. I didn't know that.

> @matt_symes, re #4 above, the round function in spreadsheets don't round up to 3 as in you example. It would round down to 2 which is the closest integer. There are roundup and rounddown spreadsheet functions to force it to round up or down. ;)

That's the same as most round functions. I mentioned rounding up only because it's erring on the side of caution when it comes to swap, but rounding down is just as valid as it's a heuristic.

I'm glad you posted this :) 

Maybe you have solved the origin of that equation and if you have, 'hat tip'.

---

### Post by pauljw on 2016-01-28
The formula I've had success with is 2XRAM up to a 4G swap.  I have an 8G machine with a 4G swap and have never had a problem.  The odds of the average user loading up their RAM above 4G is slim at best.  Too large a swap file and performance begins to degrade as the system attempts to manage it, so I've read anyway.

---

### Post by Dreamer Fithp Apprentice on 2016-01-28
@ matt_symes:

I meant no disrespect to Grahammechanical and intended no offense to him. He is a level headed chap and I doubt if he took any.

> **matt_symes said:**
> Do you really think that round(sqrt(RAM)) is obvious to everybody who frequents this forumNo, but it seems clear that it was obvious to OP. He implicitly assumed the meaning was obvious. He did NOT ask what it meant. It seems clear that he knew what it meant. He even made that clear in the title of the thread. This is not a wiki. There are an immense number of threads on here that are not immediately clear to any random passerby. Finagle knows, there are plenty that are not clear to me. In responding to a query in a FORUM, I generally assume the main point is to try to respond to the individual poster which means to address what they are asking rather than re-explaining the question, when the question is clear enough that anyone able to answer it will understand it.

If his question is clear to me, it is certainly clear enough to anybody who has a ghost of a chance of answering it, which, I reiterate, none of us have done.

> **matt_symes said:**
> The post has been answered.You are apparently offended by my statement> **Dreamer Fithp Apprentice said:**
> But none of this addresses OP's question, which I think is a darned good oneI regret if you're offended but I do not apologize for a simple statement that is clearly true. The POST has been RESPONDED to, but the QUESTION has NOT been ANSWERED. I re-read it again, very carefully.  The ONLY questions were:
> **varenorn said:**
> How was this formula derived? How did it come into being?These are the same question, posed twice with different wording to make it as clear as possible. OP is a commendably clear writer. He even prefaces the question with this declarative sentence:
> **varenorn said:**
> However, I have one main question regarding it (to stay on topic).He could not possibly have been clearer. Those are the only sentences with question marks and he explicitly labels them as his "one main question".

Well, there is much in your post of interest & OP posted in a chat sub-forum, so if he gets discursive commentary, that is to be expected. And I need to learn to watch the right column in the "unanswered posts" list and avoid responding to the ones in "chat" sub-fora. But even so, I won't be taken to task for a simple true statement without responding. Well, at least once. I won't be baited into a flame war.

I stand by what I wrote. OP's question is very precise, explicit, and clear. And still unanswered. He isn't asking for advice on partitioning. There is a great deal of material here answering questions he did NOT ask, which is fine, since this is a chat sub-forum. But none of that invalidates the statement that the actual question has not been answered. It STILL hasn't been answered. I don't know the answer. I'd like to. Not because I'm looking for advice on partitioning any more than OP was, but for the same reason OP explicitly stated he was asking. I'm "just curious" about the basis of a very precise "official" statement that has no . . ., ahem, OBVIOUS explanation.

---

### Post by mastablasta on 2016-01-29
if you throw this into excel it gives out what is requested: =ROUND(SQRT(64);0)

in this case square toot of 64 rounded to 0 digits.

i dont' know how it is in libre Office but i do think the formula is sitll missing the digits part to be used there.

---

### Post by mastablasta on 2016-01-29
> **pauljw said:**
> The formula I've had success with is 2XRAM up to a 4G swap.  I have an 8G machine with a 4G swap and have never had a problem.  The odds of the average user loading up their RAM above 4G is slim at best.  Too large a swap file and performance begins to degrade as the system attempts to manage it, so I've read anyway.

you can also reduce swapineess to get arround this issue. e.g. that the OS only starts using swap once RAM has say 7 GB occupied in your case.

---

### Post by matt_symes on 2016-01-29
> **Dreamer Fithp Apprentice said:**
> @ matt_symes:

I meant no disrespect to Grahammechanical, who I suspect was being somewhat disingenuous, and intended no offense to him. He is a level headed chap and I doubt if he took any.

I can't comment on whether grahammechanical understood the meaning of the wording of that equation; only he can and i would not want, or even am i entitled, to speak for him.

He did posit what looked like a question about the equation and clarification of that equation does nothing to hinder this thread, and may be enlightening to others who don't understand that syntax of the equation.

> No, but it seems clear that it was obvious to OP. He implicitly assumed the meaning was obvious. He did NOT ask what it meant. It seems clear that he knew what it meant. He even made that clear in the title of the thread. This is not a wiki. There are an immense number of threads on here that are not immediately clear to any random passerby. Finagle knows, there are plenty that are not clear to me. In responding to a query in a FORUM, I generally assume the main point is to try to respond to the individual poster which means to address what they are asking rather than re-explaining the question, when the question is clear enough that anyone able to answer it will understand it.

This is a public forum. Many people visit this forum and read threads in it.

You have to understand that the opinions given in this thread, and they are opinions as this is not a support thread, are intended to enlighten and expand on the thread.

> Just curious to find out the different methods for working out swap partition space.

You see, the above quote could be interpreted as a request to proffer opinions (again not a support thread) about "the different methods for working out swap partition space."

> If his question is clear to me, it is certainly clear enough to anybody who has a ghost of a chance of answering it, which, I reiterate, none of us have done.

Again, that may be true but it does not help others that may not understand that equation.

It may be the case that everyone reading this thread does understand that equation, however that is not an assumption that i think should be made.

This still misses the point of whether  "Just curious to find out the different methods for working out swap partition space." is eliciting other opinions or not.

Once again, i will highlight that this is not a support thread. It's in the wrong sub-forum for that. This sub-forum was created with the specific intent of creating an area where discussions could be made *around* a topic and, as long as the thread does not drift too off topic and stays within the bounds of the CoC, then all opinions are welcome.

> You are apparently offended by my statementI regret if you're offended but I do not apologize for a simple statement that is clearly true. 

Offended ? No. Why should i be offended ? There is no need for you to apologise for stating your opinion, as long as it's within the forum's CoC.


> The POST has been RESPONDED to, but the QUESTION has NOT been ANSWERED. I re-read it again, very carefully.  The ONLY questions were:
These are the same question, posed twice with different wording to make it as clear as possible. OP is a commendably clear writer. He even prefaces the question with this declarative sentence:
He could not possibly have been clearer. Those are the only sentences with question marks and he explicitly labels them as his "one main question".

One main question, yes. However that does not insist that there are not implied questions or that the *main* question is the only question.

> Well, there is much in your post of interest & OP posted in a chat sub-forum, so if he gets discursive commentary, that is to be expected. And I need to learn to watch the right column in the "unanswered posts" list and avoid responding to the ones in "chat" sub-fora. But even so, I won't be taken to task for a simple true statement without responding. Well, at least once. I won't be baited into a flame war.

This area is for general chit chat and to talk through and about a topic.

You're stating your opinion and so am i. There's nothing wrong with that :) A flame war never even crossed my mind.

There are many other staff who monitor these forums. They'll take *both of us* to task if that's what they have to do. It's their role here.

> I stand by what I wrote. OP's question is very precise, explicit, and clear. And still unanswered. He isn't asking for advice on partitioning. There is a great deal of material here answering questions he did NOT ask, which is fine, since this is a chat sub-forum. But none of that invalidates the statement that the actual question has not been answered. It STILL hasn't been answered. I don't know the answer. I'd like to. Not because I'm looking for advice on partitioning any more than OP was, but for the same reason OP explicitly stated he was asking. I'm "just curious" about the basis of a very precise "official" statement that has no . . ., ahem, OBVIOUS explanation.

Please stop trying to limit discussion in an area of the forum which was created specifically for discussion.

If someone knows the answer to the OP's explicit question they'll post.

---

### Post by oldfred on 2016-01-29
My suggestion has been just 2GB for swap. (for most users)

I only now have seen the square root calculation and have read the swapfaq multiple times.

2GB is a little large if you only have 512MB of RAM.
It is per old rule of 2X correct for 1GB of RAM.

But once you get to 2GB of RAM it is per new rule of 1 times RAM. But really should be 2GiB if technically correct for hibernation.

But you normally do not want hibernation if dual booting. 
Or if you have a SSD, you boot very quickly and do not need hibernation.
Some system have issues with hibernation that will take longer to solve than the total boot time for the life time of system.

My older system had 4GB of RAM and I never used swap. 

Many users with over 4GB of RAM have posted they do not use swap and have not had issues. 
But I believe some swap saves a second or two on boot as it does not have to look for swap and not find it.

And with new hard drives, allocating whatever you want for swap does not use much of drive.

---

### Post by montag dp on 2016-01-29
I'll attempt to answer the OP's questions. Please be aware that these are just my guesses, though. 

1. How was this formula derived? I don't believe it was derived. It was most likely made up as a reasonable rule of thumb based on experience.

2. How did it come into into being? Someone decided it was a reasonable estimate of how much swap someone would need given a certain amount of RAM.

As for why it's a reasonable rule of thumb, I guess the assumption is that most users will not often use up all their RAM, and if they do, they will probably not need as much swap space as they have RAM. It makes sense that  the amount of swap space should increase with the amount of RAM available, since users with lots of memory are more likely to have lots of programs open at once. But it doesn't need to scale linearly with RAM; there is a kind of plateau where swap space doesn't need to increase much more when LOTS of RAM is available. Hence the sqrt(RAM) formula.

Of course, these statements are all based on various assumptions which might not be true for your particular usage and hardware. There are also a potentially infinite number of other valid rules of thumb one could alternatively use. And of course, as I said, these are just guesses on my part.

---

### Post by Old_Grey_Wolf on 2016-01-29
> **mastablasta said:**
> if you throw this into excel it gives out what is requested: =ROUND(SQRT(64);0)

in this case square toot of 64 rounded to 0 digits.

i dont' know how it is in libre Office but i do think the formula is sitll missing the digits part to be used there.

LibreOffice calls "digits" "count". This is from LiberOffice Calc help: "Returns Number rounded to Count decimal places. If Count is omitted or zero, the function rounds to the nearest integer."

---

### Post by pauljw on 2016-01-29
> **mastablasta said:**
> you can also reduce swapineess to get arround this issue. e.g. that the OS only starts using swap once RAM has say 7 GB occupied in your case.

You are correct, but as I say, I've not had any issues what so ever.  I'm sometimes a rather slow learner, but one thing I have learned over the years is that linux is extremely good at memory management, so I just let it do its thing and try not to even pay any attention to what it's doing.  :)

Paul

---

### Post by Dreamer Fithp Apprentice on 2016-01-30
+2 for Montag dp for actually answering the question.

OP seems intent on getting an answer - he's given up on us and gone on to ask elsewhere:
[http://wyldeplayground.net/square-root-of-ram-for-swap-space-formula/](http://wyldeplayground.net/square-root-of-ram-for-swap-space-formula/)

In the meantime, I researched this a bit:

==============================================
First, the expression itself:

As I suggested, round(sqrt(x)), being an intuitively natural syntax, not surprisingly, appears to be a legitimate expression in more than one language, including C:

-C (which I don't speak)
[http://ccm.net/faq/5734-how-to-find-square-root-in-c-program](http://ccm.net/faq/5734-how-to-find-square-root-in-c-program)
[https://stackoverflow.com/questions/2422712/c-rounding-integer-division-instead-of-truncating](https://stackoverflow.com/questions/2422712/c-rounding-integer-division-instead-of-truncating))

-Oracle SQL (which I don't speak)
[http://www.java2s.com/Code/Oracle/Numeric-Math-Functions/roundsqrtsal2.htm](http://www.java2s.com/Code/Oracle/Numeric-Math-Functions/roundsqrtsal2.htm)

-R (which I don't speak)
[https://stat.ethz.ch/pipermail/r-help/2011-September/289393.html](https://stat.ethz.ch/pipermail/r-help/2011-September/289393.html)

-ancient TI calculator language (which I used to speak circa K/T)
It is a legitimate way to WRITE an entry on paper describing what you do with the machine,, where "sqrt" means press a specific key.

I am sure there are more examples.
============================================
History of the idea:

In the beginning, there was Redhat

and the "original table" (by which name it is actually still known - how . . . original). This was their recommendations for swap size, published in antiquity:

Original table:

      RAM________|_______                                           Swap
4 gB or less............2 gB or more
4 to 16 gB..............4 gB or more
16 to 64 gB............8 gB or more
64 to 256 gB.........16 gB or more
256 to 512 gB.......32 gB or more 
   adapted from [https://serverfault.com/questions/5841/how-much-swap-space-on-a-2-4gb-system#](https://serverfault.com/questions/5841/how-much-swap-space-on-a-2-4gb-system#)

Note that, whether by intent or not, this table can be succinctly summarized as "the square root of the RAM in GB, rounded up to a power of two". If there is any math theory behind this, I have been unable to discover it. More likely, the table entries result from practical experience filtered through a programmer's tendency to think of powers of 2 as round numbers and the fit with the formula is more or less coincidence.

The first recommendation for swap expressed by this formula, as far as I have been able to determine, is this post in 2011:

"The square root of the RAM in GB, rounded up to a power of two. &#8211; starblue Jun 17 '11 at 7:57"
from
[https://askubuntu.com/questions/49109/i-have-16gb-ram-do-i-need-32gb-swap#](https://askubuntu.com/questions/49109/i-have-16gb-ram-do-i-need-32gb-swap#)

Starblue has the heaviest geek credentials imaginable. He is an IT pro and computer scientist with a doctorate in computer science. He has authored original research and was formerly with the Max Planck Institute for Computer Science. He has worked on the linux kernel and is fluent in more languages, human and programming, than I have fingers to count with, including an assembler language.

Regarding that post, he says
"I don't remember that comment, but I suppose I just translated the table (now called "original table") in the answer to a formula. So the actual sizes are not from me but from RedHat."
  from personal communication

The terse "round(sqrt(RAM))" recommendation was added to 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
on 2015-04-10 18:19:16 by fabrizio-marana. As far as I can find, this is the first occurrence of this expression used for this purpose.

=======================================
Summary:
The formula is an elegant description of what were, at the time, Red Hat's recommendations. Those recommendations appear to have been rules of thumb derived from practical experience and published in tabular form without awareness that they fit such an elegantly simple formula.

Whether that is coincidence or reflects unknown underlying math that results in the system behavior that was the basis of Red Hat's recommendations is a question that could be investigated, if one were so inclined, from 2 perspectives:

-If it were coincidence, just how big a coincidence would it be? Which would have bearing on how plausible the coincidence hypothesis is. Regarding this I'll make 2 intuitive judgments without attempting anything deeper:
      *with only 5 lines in the table, given the tendency of programmers to think of powers of 2 as round numbers, it's probably not that big a coincidence
      *this is a fairly tractable problem and someone who cared to, could probably put some real numbers in an answer with a few hours thought at most.

-Is there any underlying reason in information theory for these numbers to fit this pattern?
It is way too deep a question for me, but I will make 1 intuitive SWAG:
      *If someone qualified were to tackle this, it MIGHT be provable, if in fact it is true, but if in fact it is not true, it would probably be extremely difficult to disprove.

One more thing of note:

While this formula is a fossil of what Red Hat used to recommend, they no longer recommend this. Their current recommendation is:
"Swap should equal 2x physical RAM for up to 2 GB of physical RAM, and then an additional 1x physical RAM for any amount above 2 GB, but never less than 32 MB."
 from 
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html#s1-swap-what-is](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html#s1-swap-what-is)

=======================================
Non-topical postscript, merely meta-topical:

@ matt_symes

> **matt_symes said:**
> Please stop trying to limit discussion in an  area of the forum which was created specifically for  discussion.You seem determined to distort what I've written. Nothing I wrote was, or implied, such an attempt, nor  IMO, could such an attempt be reasonably inferred.  In the very part  you quoted I clearly wrote "which is fine, since this is a chat  sub-forum". I merely pointed out that despite a great deal of material  posted, the OP's substantively single (grammatically double) question  had still not been addressed, despite being both clearly expressed and  of significant interest, which was completely true at the time, although  Montag dp and I have since answered it.

Given the context, I can't see any reasonable interpretation of your  post> **matt_symes said:**
> The post has been answered.than  as a flat contradiction to my clearly true and clearly on topic  statement that OP's actual question had not been addressed - unless you  simply meant it to forestall any further discussion at all. So,  naturally I defended my statement, which I still regard as clearly true  and not reasonably disputable.

P.S.
For this, in my opinion, temperate, post, I received substantial infraction points and a threat of sanctions from howefield. Consider that my LANGUAGE is not objectionable, only the THOUGHTS expressed. That's enough for me. I think highly of some people here, but it isn't worth it. When I add the post script he'll probably ban me. But that's fine, because this is my last post here anyway.

---

### Post by oldfred on 2016-01-30
@Dreamer Fithp Apprentice
Great research on the swap issue.

And I thought I had not seen the formula in swapfaq before. And I have not followed Redhat's suggestions recently. I last installed Redhat when GB was large for a hard drive, much less RAM.

---

### Post by matt_symes on 2016-01-30
@Dreamer Fithp Apprentice

Not 20 minutes ago, i was commenting on how good i thought your post was. It's a shame you had to edit it.  

> ...question had still not been addressed....

Maybe next time make that kind of post your first post.

I'll, also, leave it at that.

---

### Post by QIII on 2016-01-30
The square root of a number rounded up by a power of two is ...  well ... the original number.  Pointless tautology even back when (if) RedHat recommended that.  A range beginning with the square root of the RAM and limited on the top end to the square root squared plus some arbitrary amount extra is also a silly and pointless calculation.

It appears to me that whoever proposed that as documentation for whoever the distributor was had nothing better to do than be obnoxious on a day when he/she was writing documentation and trying to look busy.

**For varenorn**:  Ignore it.  It's a silly exercise is useless computation.  Swap = RAM size (plus maybe 10% because I used to be a construction project manager) is appropriate for desktop machines if you plan to hibernate.  If you have 8GB+ and you don't plan to hibernate, there is probably little need for swap.  I don't run swap on any of my machines.

If you are running a server, you might either: Double the RAM as swap -- or better yet:  add RAM, since that is faster and better able to handle extra loads.

RAM used to be precious.  Now it's cheap.

That bit of the community wiki should probably go away quietly.  It is something from a bygone age that was silly even then.

---

### Post by Dreamer Fithp Apprentice on 2016-01-30
> **QIII said:**
> The square root of a number rounded up by a power  of two is ...  well ... the original number.  Pointless tautology . .  .You might want to rethink that.

Example:
square root of 100 = 10
10 rounded up to a power of 2 = 16

Look at the table.


@ Oldfred:

Thank you, old friend, Oldfred. You are indeed one of the main people I had in mind when I spoke of there being people here I think highly of in the post script I added to the post above. Hopefully, I'll bump into you on other fora. Farewell.

---

### Post by QIII on 2016-01-30
No.  I won't rethink it, but I did reread it more carefully.

Not rounded up "by" a power of two as I had read it, in which case it's back to 100.

Rounded up "to" a power of two is a different matter, i which case it is 16.

Misreading, not Math.

---

### Post by CharlesA on 2016-01-31
> **Dreamer Fithp Apprentice said:**
> 

OP seems intent on getting an answer - he's given up on us and gone on to ask elsewhere:
http://wyldeplayground.net/square-root-of-ram-for-swap-space-formula/


Not that it actually matters, but the site you linked to is just another site to scrapes data from multiple sources and uses it to get hits.

So far the OP has only posted here.

As far as using a specific formula for setting the amount of swap in use, I usually stick to the default which is twice the RAM unless I have an ungodly amount of RAM and then it is 1 X the amount of RAM, like oldfred mentioned.

---

