---
title: "thou shalt not lie, computer/software"
date: 2008-08-04
forum: Testimonials &amp; Experiences
---

### Post by inorganic on 2008-08-04
I consider my computer to be a tool - my tool - that I operate to do productive work. One reason I much prefer linux to windoze is that linux rarely tries to manipulate and scam me for the benefit of certain other joker/power/money-mongers. So I was rather annoyed to find the nautilus file browser LIED to me - and caused me to delete a couple man years of work. Yes, I did have a nearly up-to-date backup, but that's not the point. My computer, my operating system, my window-manager and the primary, fundamental tools that I work with every day should never, ever, LIE to me.

To what do I refer? Well, it is a bit complicated but the shortened story goes like this. I decided to switch from fedora to ubuntu because I was not able to get fedora9 working properly. So I bought a new 1TB hard drive and installed ubuntu 8.04.1 on the drive, which went rather nicely (though I still have lots of setup to do, including getting the new eclipse IDE and CDT installed and compiling/executing the application I am developing). After that was complete, I wanted to copy over my data from the hard disk drives that were in my fedora8 system (now the ubuntu system). So I plugged their SATAII cables into the motherboard and booted up the computer, back into ubuntu. The other three disk drives were visible inside the /media directory, just as they should be (though the names ubuntu chose might have been more consistent). I created archive, backup, document and download directories on the ubuntu hard drive per my usual practice (inside my user directory) and prepared to copy my important work from the other three drives (fedora8x32, fedora8x64 and fedora9x32) onto the newly created ubuntu drive.

The short story is, "the file manager lied to me". When I browsed to the folders that contained my work, the folders were visible.  When I opened the folders, the file manager (which is nautilus) explicitly displays "empty" (for example, for the workspace directory that contains all the software applications I am developing with eclipse/OpenGL/GLSL/etc).  As it turns out, that was flatly not true, and wasted lots of my time, and almost cost me years of work. It took me quite a bit of time to figure out I was being flatly lied to by nautilus. Pretty much, I imagined every other possibility first, including "the drive data must have been damaged", "it must have been on one of my other disk drives", etc.

I am NOT saying Linux should have no security or be like windoze. Just the opposite. I dislike the trend by linux apps to adopt windoze stupidities. Of course linux and apps should prevent users without appropriate permissions to read/write/delete files. And it is even okay to display messages like "hidden" or "unauthorized" as appropriate. It is okay to refuse. But it is NOT okay to lie.  Ever.  Not for a computer or software that is supposed to be serving and supporting its owner/owners. We need to know what are the facts, even when certain operations are prevented.

The problem is made worse by the existence of GUI applications. Certain functions cannot be [reasonably/efficiently/conveniently] performed by GUI methodologies, so sometimes users have a console/terminal window open as well as a GUI window. The difference in permissions or context between them can lead to disaster. True, the same can happen when two GUI applications are opened with different users (for example, I started one nautilus in a root terminal window and tried drag and drop between them).

So, that is my brief case for never, ever telling a LIE to a user. And this is my request to the nautilus developers (and all other developers) to inspect and modify their apps as necessary.

If any of you have the ear of the nautilus folks, please point them to this message.  Thanks.

PS: As an aside, normally to do massive operations like these where I need full access and permissions, I will login as root to prevent any permission issues from getting in my way.  However, when I installed ubuntu yesterday (my first exposure to ubuntu) I was surprised that it did not (and would not let me) create a root account as part of the setup.  How do I set the password for root, anyhow - or establish the root user if it actually doesn't exist yet (hard to believe)?

PS: I'm not trying to gripe or start a controversy - and I don't think this issue is or should be controversial.

---

### Post by ad_267 on 2008-08-04
I'm not exactly sure what you're saying happened. Sometimes you don't have permissions to view the contents of a directory so nautilus shows them as empty. If you tried the same from the command line it would give "permission denied"

To find out about root in Ubuntu read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by p_quarles on 2008-08-04
Not a support request, so moved to Testimonials & Experiences.

---

### Post by loell on 2008-08-04
heh, quite a long post there :D

I dunno, i think its more of a **Fail**  than a **lie** , either partly by nautilus or solely by you. ;)

---

### Post by steveneddy on 2008-08-04
Sounds like you just needed to change the file permissions?

---

### Post by maxreason on 2008-08-04
Gads, what a bunch of non-helpful, non-thoughtful people.  I'm guessing this is the opposite of what ubuntu stands for - or wants to.  Furthermore, if people cannot understand what "empty" means, I'm sure I've seen you along side of the road many times next to your car - scratching your heads cuz you don't know why it stopped.
 
My post was intended to address a real issue and lead to improvement in the way software works.  Every response I read was some varying degree of useless trivia, and most of you obviously didn't read the whole post cuz your comment proved it.  And others comments are so practical - like change the permission of every one of a few million files on 3 entire hard drives (just so I can see they exist).  Sheesh.
 
Perhaps ubuntu needs a form for "serious people".  Somehow let me guess - that won't happen.

---

### Post by p_quarles on 2008-08-04
> **maxreason said:**
> Gads, what a bunch of non-helpful, non-thoughtful people.  I'm guessing this is the opposite of what ubuntu stands for - or wants to.  Furthermore, if people cannot understand what "empty" means, I'm sure I've seen you along side of the road many times next to your car - scratching your heads cuz you don't know why it stopped.
 
My post was intended to address a real issue and lead to improvement in the way software works.  Every response I read was some varying degree of useless trivia, and most of you obviously didn't read the whole post cuz your comment proved it.  And others comments are so practical - like change the permission of every one of a few million files on 3 entire hard drives (just so I can see they exist).  Sheesh.
 
Perhaps ubuntu needs a form for "serious people".  Somehow let me guess - that won't happen.
What post? Do you have two accounts here?

---

### Post by loell on 2008-08-04
it seems two accounts, oops..:oops:

---

### Post by Oldsoldier2003 on 2008-08-04
> **maxreason said:**
> Gads, what a bunch of non-helpful, non-thoughtful people.  I'm guessing this is the opposite of what ubuntu stands for - or wants to.  Furthermore, if people cannot understand what "empty" means, I'm sure I've seen you along side of the road many times next to your car - scratching your heads cuz you don't know why it stopped.
 
My post was intended to address a real issue and lead to improvement in the way software works.  Every response I read was some varying degree of useless trivia, and most of you obviously didn't read the whole post cuz your comment proved it.  And others comments are so practical - like change the permission of every one of a few million files on 3 entire hard drives (just so I can see they exist).  Sheesh.
 
Perhaps ubuntu needs a form for "serious people".  Somehow let me guess - that won't happen.

While I can understand your frustration, responding to those posts in this manner only "feeds the trolls". What I would do in your case is file a bug report with: 

Action
Expected result
Result (buggy action?)

The thing is that not every developer reads the forums, and this issue you are experiencing with nautilus may or may not be a Ubuntu specific issue. you have to remember that nautilus is part of gnome, and Ubuntu is based on Debian - so there is a possibility of the buggy behavior being caused at any of the three levels.

By filing a bug or checking to see if this is a reported bug you can give it visibility or see the status.

ps: multiple accounts are in violation of the Forum rules...

---

### Post by munkyeetr on 2008-08-04
> **p_quarles said:**
> what post? Do you have two accounts here?

lol!

---

### Post by maxreason on 2008-08-04
You know what?  You'll be happy to know that I shall return to fedora again - simply and entirely because the average forum member is civil and helpful.  Too bad too, cuz ubuntu did appear promising.  You can all stick around and play with yourselves.  Adios, gringos.

---

### Post by p_quarles on 2008-08-04
> **maxreason said:**
> You know what?  You'll be happy to know that I shall return to fedora again - simply and entirely because the average forum member is civil and helpful.  Too bad too, cuz ubuntu did appear promising.  You can all stick around and play with yourselves.  Adios, gringos.
No problem. If you change your mind, please use the other account, as this one has now been disabled.

---

### Post by Jokimoto on 2008-08-04
Wow. As far as I can tell you only asked *one question* in that post, and *the very first response you got* pointed you in the direction of an answer. Who's not being civil?

---

### Post by steveneddy on 2008-08-04
Why would he need two accounts?

Anyone think he's gonna come back?

I would like to know the correct answer, actually.

---

### Post by 3rdalbum on 2008-08-05
He would have had more helpful replies if he took his time while writing that original post. I have no idea which directories were "empty", whether they were the source or the destination. I can't work out what action he took to rectify the situation either.

The original problem sounds a bit like a case of "The law of leaky abstractions" ([http://en.wikipedia.org/wiki/Leaky_abstraction]("http://en.wikipedia.org/wiki/Leaky_abstraction"))

---

### Post by hyper_ch on 2008-08-05
> **3rdalbum said:**
> He would have had more helpful replies if he took his time while writing that original post.
I thought this section here is not for support but for testimonials.

---

### Post by loell on 2008-08-05
it was posted in one of the support categories but was later move here to testimonials. which is actually a right move as you read the first post.

---

### Post by ad_267 on 2008-08-05
The post wasn't originally in the testimonials forum. It was moved there because it sounded like a testimonial.

---

### Post by kspncr on 2008-08-05
> **loell said:**
> I dunno, i think its more of a **Fail**  than a **lie** , either partly by nautilus or solely by you. ;)

lol I love this, thanks loell

---

### Post by bmac on 2008-08-06
Why the rant targeted at one of the most helpful and courteous forums on the net (try flaming Windows on a Windows forum)? 

Is it possible this individual was deliberately antagonizing forum members just to be annoying or that their so self absorbed that annoying this forum provides them with some form of satisfaction? This type of juvenile behavior may be indicative of a physiological dysfunction that needs to be evaluated immediately....

"The Ubuntu Envy Syndrome" or "TUES" I hear it's contagious....:lolflag:

---

### Post by ToFue on 2008-12-04
> **maxreason said:**
> Gads, what a bunch of non-helpful, non-thoughtful people.  I'm guessing this is the opposite of what ubuntu stands for - or wants to.  Furthermore, if people cannot understand what "empty" means, I'm sure I've seen you along side of the road many times next to your car - scratching your heads cuz you don't know why it stopped.
 
My post was intended to address a real issue and lead to improvement in the way software works.  Every response I read was some varying degree of useless trivia, and most of you obviously didn't read the whole post cuz your comment proved it.  And others comments are so practical - like change the permission of every one of a few million files on 3 entire hard drives (just so I can see they exist).  Sheesh.
 
Perhaps ubuntu needs a form for "serious people".  Somehow let me guess - that won't happen.


I've noticed that on nearly every post in these forums you have to sort through a gallery of penuts to get to a knowledgable post.. what ever happened to personal restraint when making comments..?  

I'm not trying to fuel fire, but I agree that it's a pain in the maximus-behindiss (creative license taken) to plea for help and get instead a critique of how you pled. Honestly I see less of that in other forums (like fedora), whereas pple take time more-so on the whole to discuss rather than just make a one-liner.

I say this here scince the post's now in the experience thread, but I think this should be addressed (if it hasn't already), because it(smart-arserse-comments) Really does turn people off to Ubuntu as well.. 

Sure- the guy has an issue- That's Why He's Posting!!   But instead you got people that rather enjoy the flames. yeah- this means you too, kspncr, and whoever else this applies. [/rant] .. (where was the "[rant]" to begin with?!? :p)

... I mean Really!!

---

### Post by snowpine on 2008-12-04
> **ToFue said:**
> I've noticed that on nearly every post in these forums you have to sort through a gallery of penuts to get to a knowledgable post.. what ever happened to personal restraint when making comments..?  

I'm not trying to fuel fire, but I agree that it's a pain in the maximus-behindiss (creative license taken) to plea for help and get instead a critique of how you pled. Honestly I see less of that in other forums (like fedora), whereas pple take time more-so on the whole to discuss rather than just make a one-liner.

I say this here scince the post's now in the experience thread, but I think this should be addressed (if it hasn't already), because it(smart-arserse-comments) Really does turn people off to Ubuntu as well.. 

Sure- the guy has an issue- That's Why He's Posting!!   But instead you got people that rather enjoy the flames. yeah- this means you too, kspncr, and whoever else this applies. [/rant] .. (where was the "[rant]" to begin with?!? :p)

... I mean Really!!

Welcome back! ;)

Finding the information you need here is largely a function of learning to ask the right question. Post number 1 of this thread was definitely not "the right question" if the poster was seriously looking for support...

---

### Post by ToFue on 2008-12-04
Oh, thank you! :D 

so what is the right question when one is ignorant to the solution?

---

### Post by snowpine on 2008-12-04
> **ToFue said:**
> Oh, thank you! :D 

so what is the right question when one is ignorant to the solution?

For example,

"I'm having a problem copying my files over from a previous Fedora installation. Nautilus is incorrectly reporting that certain folders are empty, but I know for a fact they are not. Can anyone help explain why the folder contents are invisible?"

---

### Post by ToFue on 2008-12-04
That's a great example- I suppose that's the sort of expert response/diagnosis that the poster could've been looking for..

 my point earlier is that about half of the thread is simply people critiquing instead of diagnosing..  It's a pattern I see on these boards often, and wanted to point out.

Should this be it's own thread?  ::shrug::

---

### Post by snowpine on 2008-12-04
> **ToFue said:**
> That's a great example- I suppose that's the sort of expert response/diagnosis that the poster could've been looking for..

 my point earlier is that about half of the thread is simply people critiquing instead of diagnosing..  It's a pattern I see on these boards often, and wanted to point out.

Should this be it's own thread?  ::shrug::

I think you might have a good point, but you chose a poor example to support it... this particular thread was pretty inflammatory and deserved the negative response, agreed? ;)

---

### Post by ToFue on 2008-12-04
It's easier to be helpful when someone's calm and clear, true.. though I personally don't think anyone really deserves to be flamed.

However I see your point concerning this particular thread.. his comments were inviting for negative feedback.  I only wish more people were mature about other people's anger when expressing in posts- after all the *community* is the sum of the whole, and every response is a representation of the community and that which it stands for: Ubuntu, then Linux..  I guess I'm being a bit philisophical and stuff.. sory for that, but I do tend to /root for the underdog :p

---

### Post by Tamlynmac on 2008-12-05
> ToFue 	 		**Re: thou shalt not lie, computer/software**
 		That's a great example- I suppose that's the sort of expert response/diagnosis that the poster could've been looking for..

 my point earlier is that about half of the thread is simply people critiquing instead of diagnosing.. It's a pattern I see on these boards often, and wanted to point out.

Should this be it's own thread?  ::shrug:: 	

One thing to keep in mind with regards to the original post was that the OP apparently had two accounts. Their response to the admins reaction was to leave the forum. They exhibited troll behavior and as you indicated

> However I see your point concerning this particular thread.. his comments were inviting for negative feedback.

the post was extremely inflammatory. Generally, when asking for assistance it's not a good idea to include derogatory or inflammatory remarks. Certainly not if you're expecting assistance from individuals that are serious about their involvement in the forum. No one here gets paid to assist or receives a benefit other than knowing they provided said assistance. Your absolutely correct when stating that the community is the sum of the whole. Question is, did the OP represent the community when violating community rules or posting in this manner? Don't misunderstand, like others I've had my moments of frustration. But refused to react in an imature manner when requesting assistance. Respect goes a long way - when asking for help.__

---

