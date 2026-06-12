---
title: "Getting discouraged"
date: 2009-12-05
forum: Testimonials &amp; Experiences
---

### Post by rmcd on 2009-12-05
Yesterday using Karmic I tried to open this document at MakerShed: 

[http://makezine.com/images/store/MECHAMO%20Centipede%20English.pdf](http://makezine.com/images/store/MECHAMO%20Centipede%20English.pdf)

It's an english translation of a Japanese manual. It was unreadable in evince, xpdf, epdfview, okular. Acrobat popped up a blank dialog box. By contrast it opened right away in OS X. In XP there was a dialog box telling me I needed to install the Japanese language pack, after which it rendered beautifully. Solution: apt-get install poppler-data. Huh? It took a *lot* of googling and apt-cache searching to figure this out. Why isn't poppler-data part of the default install? (If it's too big for the CD why can't it be installed on first update?) This cost me well over an hour.

And then there is pdf printing: Karmic broke it badly. There are bug reports about this that seem to go in circles. But I can't print over a network to a postscript printer using gnome. I installed Okular. It prints, but the okular print dialog is broken, with some items greyed out and selectable, others greyed out and not selectable. I needed to print a 2-page letter and there seemingly was no way to not print duplex (the okular print dialog told me duplex was off and in any event it wasn't selectable). I ended up using pdftk to create two one-page documents so I wouldn't have duplex output.

I've been a Debian user for 5 years (home servers) and a ubuntu user for 1. And I use command line redhat on research servers. (I *love* the command line, btw.) After all the battling with wireless, power management, and video over the last year, the poppler-data issue feels like some kind of last straw.

And finally: yes, I know that the non-long-term-releases are cutting edge. But the omission of poppler-data was an architectural decision, not a bug. And broken printing is, in my opinion, a show-stopper. 

I appreciate the good work that Ubuntu volunteers do. I also think that problems such as I've described can render much of that good work for naught in a hurry. Curious to know what others think.

Bob

---

### Post by gordintoronto on 2009-12-05
> **rmcd said:**
> Yesterday using Karmic I tried to open this document at MakerShed: 

[http://makezine.com/images/store/MECHAMO%20Centipede%20English.pdf](http://makezine.com/images/store/MECHAMO%20Centipede%20English.pdf)

It's an english translation of a Japanese manual. It was unreadable in evince, xpdf, epdfview, okular. Acrobat popped up a blank dialog box. By contrast it opened right away in OS X. In XP there was a dialog box telling me I needed to install the Japanese language pack, after which it rendered beautifully.Bob

Using Acroread in Ubuntu, I was told I needed to install the Japanese language pack, and where to find it.  Without the language pack, the PDF was unreadable.  I don't think this is unreasonable.

---

### Post by Ms_Angel_D on 2009-12-05
rmcd, thank you for sharing your experience, I'm sorry for the troubles you have had and hope your able to resolve them.

---

### Post by wojox on 2009-12-05
I just opened it right up in evince. Schematics to build a mechanical centipede. There isn't even any Japanese characters.

---

### Post by Chame_Wizard on 2009-12-05
Strange,it works fine to me.

---

### Post by jdrodrig on 2009-12-05
> **Chame_Wizard said:**
> Strange,it works fine to me.

+1

I am even already half-way through constructing this Centipede....once done, it will go directly under my christmas tree! :D

btw, how can I use a centipede?

---

### Post by jdrodrig on 2009-12-05
> **Ms_Angel_D said:**
> rmcd, thank you for sharing your experience, I'm sorry for the troubles you have had and hope your able to resolve them.

@Ms_Angel_D
After struggling about thinking of the proper role of T&E in these forums, I am getting to conclude your type of response is the most appropiate one to most of these postings.....mind if I copy it and reuse it later on? 

(as a side benefit, I will get an increase in beans!)

---

### Post by Ms_Angel_D on 2009-12-05
> **jdrodrig said:**
> @Ms_Angel_D
After struggling about thinking of the proper role of T&E in these forums, I am getting to conclude your type of response is the most appropiate one to most of these postings.....mind if I copy it and reuse it later on? 

(as a side benefit, I will get an increase in beans!)

Copy & Post away ;)

---

### Post by solwic on 2009-12-05
> **Ms_Angel_D said:**
> rmcd, thank you for sharing your experience, I'm sorry for the troubles you have had and hope your able to resolve them.

I see what you're trying to do, but I wonder if this excessive hand-holding is productive and/or beneficial to the OP, in the long run.  To me, it seems that these types of responses are designed to mollify a ranting OP, and I can't see how pandering to their bad behavior is any more of a benefit than arguing with them.

That's not to say *this* OP is/was ranting; I haven't even read the original post.  But I've seen these types of responses from you all over the T&E and, (as I said) while I get what you're trying to do, I wonder if a bit more thought ought be put into the direction this T&E team is moving itself in.

Just a suggestion, not a criticism.  And I'm not discussing your motives, but rather your methods.  

Have a great day!  :biggrin:

---

### Post by Ms_Angel_D on 2009-12-05
> **solwic said:**
> I see what you're trying to do, but I wonder if this excessive hand-holding is productive and/or beneficial to the OP, in the long run.  To me, it seems that these types of responses are designed to mollify a ranting OP, and I can't see how pandering to their bad behavior is any more of a benefit than arguing with them.

That's not to say *this* OP is/was ranting; I haven't even read the original post.  But I've seen these types of responses from you all over the T&E and, (as I said) while I get what you're trying to do, I wonder if a bit more thought ought be put into the direction this T&E team is moving itself in.

Just a suggestion, not a criticism.  And I'm not discussing your motives, but rather your methods.  

Have a great day!  :biggrin:

Solwic this is my job as a member of the testimonials team if you have any further questions or suggestions please look here [https://wiki.ubuntu.com/Testimonials_Team#Joining%20the%20team](https://wiki.ubuntu.com/Testimonials_Team#Joining%20the%20team)

---

### Post by solwic on 2009-12-05
> **Ms_Angel_D said:**
> Solwic this is my job as a member of the testimonials team if you have any further questions or suggestions please look here [https://wiki.ubuntu.com/Testimonials_Team#Joining%20the%20team](https://wiki.ubuntu.com/Testimonials_Team#Joining%20the%20team)

I've read it.  Again, I'm not attacking.  Just...well, just pointing out the obvious.  And asking questions.  That's all.  

I'm not suggesting you cease and desist...just wondering if catching flies with honey is any different than catching them with sh**.  

No offense meant...again, just asking questions.  :)

[COLOR="Red"]EDIT:  This isn't meant to be offensive to anybody in any way, shape or form...imaginary or otherwise.  Any inferences made from this post are solely the responsibility of the inferring party, and were not in any way implied by me.  I'm seriously just asking questions.  I hope we all can see the difference between an alleged personal attack and constructive spitballing.[/COLOR]

---

### Post by Jefferythewind on 2009-12-05
Keep the dream alive!

---

### Post by Irihapeti on 2009-12-05
@solwic
I kinda see where you are coming from, and if you and I and a few other people operated in a vacuum, it would make good sense. We would ignore some people and they'd get the message and go off and post a request in the tech forums.

Unfortunately, we don't operate in a vacuum. If you or I don't rise to the bait, someone else surely will. So, I see it as a choice between a post like Ms_Angel_D's or one of the flame-provoking responses that we see so often.

If anyone has a strategy that might work in preventing these pyrogenic replies, then it would be interesting to hear it. My own suspicion is that "negative" posts in this forum get the same reaction as bad news in the media, because that's the sort of thing that many people pay attention to.

---

### Post by chillicampari on 2009-12-05
> **solwic said:**
> I see what you're trying to do, but I wonder if this excessive hand-holding is productive and/or beneficial to the OP, in the long run.  To me, it seems that these types of responses are designed to mollify a ranting OP, and I can't see how pandering to their bad behavior is any more of a benefit than arguing with them.



The OP is neither ranting nor exhibiting "bad behavior". They are sharing their experience. And it was a straightforward and polite post. 


> 
That's not to say *this* OP is/was ranting;** I haven't even read the original post.  **But I've seen these types of responses from you all over the T&E and, (as I said) while I get what you're trying to do, I wonder if a bit more thought ought be put into the direction this T&E team is moving itself in.
(Bolded for emphasis).

Perhaps that would be a good idea (to read the OP). While I haven't been looking through T&E for Ms_Angel_D's responses specifically, if this one is representative of the majority, I think that's a very good direction! The response:

-acknowledges there is/was an issue.

-doesn't assign blame.

-offers the OP gentle encouragement and hope for resolution without being pushy.

(as an aside- if I had a nitpick I guess I'd try to find another way to be sympathetic without being apologetic, but that's really tricky).

I do see what you mean generally about hand-holding (fish for a day) but it doesn't apply at all to this OP (seasoned Linux user), I think the response from  Ms_Angel_D was appropriate, not pandering and as far as I can tell Ubuntu is *the* new Linux user introduction distribution right now, so I think a more than usual amount of hand-holding on these forums is to be expected.

---

### Post by 73ckn797 on 2009-12-05
> **Ms_Angel_D said:**
> Solwic this is my job as a member of the testimonials team if you have any further questions or suggestions please look here [https://wiki.ubuntu.com/Testimonials_Team#Joining%20the%20team](https://wiki.ubuntu.com/Testimonials_Team#Joining%20the%20team)


And a good job you are doing! A completely appropriate and, I feel, encouraging response to the OP.

---

### Post by solwic on 2009-12-05
> **Irihapeti said:**
> @solwic
I kinda see where you are coming from, and if you and I and a few other people operated in a vacuum, it would make good sense. We would ignore some people and they'd get the message and go off and post a request in the tech forums.

I'm not saying ignore them, I'm just saying that this hand-holding, molly-coddling that's going on is no different, in my mind, to arguing with them.  :)

> **Irihapeti said:**
> 
Unfortunately, we don't operate in a vacuum. If you or I don't rise to the bait, someone else surely will. So, I see it as a choice between a post like Ms_Angel_D's or one of the flame-provoking responses that we see so often.

Aren't they the same thing, though?  Doesn't either type of post elicit the same end, which is the perpetuation of pointless threads?

> **Irihapeti said:**
> 
If anyone has a strategy that might work in preventing these pyrogenic replies, then it would be interesting to hear it. My own suspicion is that "negative" posts in this forum get the same reaction as bad news in the media, because that's the sort of thing that many people pay attention to.

The answer is simple:  limit the T&E posts to the OP only.  Don't let anybody else reply.  That way, the testimonial (good or bad) is still shared, and we eliminate all the bad behavior in the T&E.  But that won't happen, for various reasons that I've already discussed elsewhere.  

IMO, of course.  :biggrin:

> **chillicampari said:**
> The OP is neither ranting nor exhibiting "bad behavior". They are sharing their experience. And it was a straightforward and polite post.

I didn't say they were, which is why I said directly afterward that I hadn't even read the original post.  I was discussing a type, not that OP in particular.  :) 

> **chillicampari said:**
> 
Perhaps that would be a good idea (to read the OP). While I haven't been looking through T&E for Ms_Angel_D's responses specifically, if this one is representative of the majority, I think that's a very good direction! The response:

-acknowledges there is/was an issue.

-doesn't assign blame.

-offers the OP gentle encouragement and hope for resolution without being pushy.

(as an aside- if I had a nitpick I guess I'd try to find another way to be sympathetic without being apologetic, but that's really tricky).

I do see what you mean generally about hand-holding (fish for a day) but it doesn't apply at all to this OP (seasoned Linux user), I think the response from  Ms_Angel_D was appropriate, not pandering and as far as I can tell Ubuntu is *the* new Linux user introduction distribution right now, so I think a more than usual amount of hand-holding on these forums is to be expected.

Like I said, I was talking about a type.  Her response was fine by itself, but it sets a precedent of putting on the kid gloves for the rants and flame-bait posts.  In the end, to use the derogatory phrase used on these very forums, we're still "feeding the trolls", even if we feed them sweets instead of garbage.  

And you're right about not being apologetic.  It's not her fault the OP had issues, and apologizing, to me, is condescending and patronizing.  That's not to say that that was Ms_Angel_D's intention, or even that that's what she did...it just came across that way.

Ultimately, they can do what they like.  Unless I'm mistaken, the T&E team has the support of the mods, so really the decision is up to the administration, not a team of users.  Any pretensions to the contrary, again, strike me as condescending and patronizing.

Just my opinion, and I'm not trying to be offensive, antagonistic, or difficult.  :)

Also, these will be my last words on the subject.  Besides, a thread in T&E isn't the right place to discuss the issue, anyway.  :)

---

### Post by 73ckn797 on 2009-12-05
Tooth paste with shoe polish is an invention I have long pondered for those who tend to stick their foot in their mouth.

---

### Post by solwic on 2009-12-05
> **73ckn797 said:**
> Tooth paste with shoe polish is an invention I have long pondered for those who tend to stick their foot in their mouth.

???  Who are you speaking of here?  I haven't seen anybody put their foot in their mouth in this thread.

---

### Post by cariboo on 2009-12-06
This thread  has veered way off topic. Closed.

---

