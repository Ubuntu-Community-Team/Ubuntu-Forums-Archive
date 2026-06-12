---
title: "Any DSL Authorities Here?"
date: 2005-06-27
forum: The Cafe
---

### Post by polo_step on 2005-06-27
I'd like some info and explanations about some performance oddities I've been noticing, and everyone I've asked so far on other fora don't really seem to know as much as they wish they did.  :smile:

Anyone who really understands what DSL can and can't do, please step up and I'll start asking.

Thanks for any help with this...

---

### Post by antwerx on 2005-06-27
Hello - Well go ahead and ask away. 

I am pretty sure that with the number of folks on these forums you will get quality information and help.

First question?

---

### Post by polo_step on 2005-06-28
[QUOTE=antwerx]Hello - Well go ahead and ask away...First question?[/QUOTE]

OK, here's the one I've spent the past two hours screaming at SBC phone "technical support" [HA!] flunkies trying to get an honest answer to.  Try to stay with me here and pay attention so we don't get off on tangents:

Why, with a tested "good" DSL connection on a tested "good" line rated at around 1.3M download speed by every test engine, is there a practical **TOTAL** download speed limit of around 200K?

Yes, I understand that one's download speed is limited by the bandwidth at the source.  I understand that perhaps Oregon Widget's server can only upload files to me to me at a steady 200K, tops, so that's why I'm only seeing 200K download speed at my end.  I UNDERSTAND THAT, OK?

Wyoming Whatsit's server can also download to me at a steady 200K.

Arizona Amalgamated's FTP site can only give me a steady 200K.

Etc., etc. for other distinct separate sites in different locations.

OK, so what happens if I, with my 1300K of technical download capability, decide to download various material from all three of these different sites simultaneously?  I have lots of excess bandwidth, right? I'll be getting data at 600K total download speed, right? 3x200K=600K, right? 600K<1300K, right? I should be able to add download traffic from different sources until I reach 1300K right?

Wrong.

As soon as I start adding sources, the speeds from the individual remote servers start dropping and no matter how many different sites I'm downloading from, the TOTAL download speed at my end stays at around 200K. The speeds from the individual sites drop to around 70K.  No matter how many sources I download from, my total download speed is limited to around 200K.

WHERE IS THE BOTTLENECK?

I can't get any intelligent answer from SBC, or even any interesting BS.  They just tread water and make soothing sounds with no technical content.  "Oh, that's normal."  "Uh, you're limited by the download site.  If it can only send at 200K, then you can only get it at 200K." [YES, I ***KNOW*** THAT!!!] "Uh...I know the answer to that, but I don't know how to explain it."  Yes, these are real answers I've had today!

Somebody help me out here.  I've screamed myself hoarse at these people to no effect.  This seems to me to be an extremely simple and obvious question, but my response from SBC is like something out of a bad *Seinfeld* episode, I swear.

Thanks for any clarification, experts! :-|

---

### Post by gil-galad on 2005-06-28
I think you are REALLY confused.  The ~1.5 download speed is in megaBITS.  Things are stored on your hard drive in megaBYTES, and your download speed is also measured in BYTES.  A BYTE is 8 BITS.  200 kiloBYTES = 1.6 megaBITS.  So whether you are downloading from one site or multiple sites, you are maxing out your line.  It sounds like you are getting your full speed, if you want to check go to [http://www.dslreports.com/stest](http://www.dslreports.com/stest) and test it.   

By the way, SBC tech support sucks, never call them. ;)

---

### Post by polo_step on 2005-06-28
[QUOTE=gil-galad]I think you are REALLY confused. [/quote]
Maybe so, that's why I'm asking.

>  The ~1.5 download speed is in megaBITS.  Things are stored on your hard drive in megaBYTES, and your download speed is also measured in BYTES.  A BYTE is 8 BITS.  200 kiloBYTES = 1.6 megaBITS.  So whether you are downloading from one site or multiple sites, you are maxing out your line.  It sounds like you are getting your full speed, if you want to check go to [http://www.dslreports.com/stest](http://www.dslreports.com/stest) and test it.   

By the way, SBC tech support sucks, never call them. ;)

So, do you mean that something that simple is TOTALLY beyond SBC's ability to explain?

That's a TRIVIAL FIVE-SECOND ANSWER!

SHEESH!

---

### Post by polo_step on 2005-06-28
Yeah, I'm still sitting here shaking my head in utter amazement that no one I talked to at SBC knew the answer to that.  All anyone had to say was, "Dude, bits and bytes!" and I would have smacked my forehead and yelled "OF COURSE!"

But they -- the technical support supervisors -- honestly *did not know.*

Can you freakin' *believe* that?

The only one who even might have was the guy who said it was normal, but he didn't know how to explain why.

Anyhow, next question that I genuinely don't know the answer to (as opposed to the prior one which I should have if I hadn't been in a state of senile stupidity!) is this:

Does upload activity limit download speed as it does on dialup, or are upload and download capacities unaffected by each other?

---

### Post by sapo on 2005-06-28
[QUOTE=polo_step]Maybe so, that's why I'm asking.



So, do you mean that something that simple is TOTALLY beyond SBC's ability to explain?

That's a TRIVIAL FIVE-SECOND ANSWER!

SHEESH![/QUOTE]


Now you should call them and tell this:

"Please, take a paper or a notebook and a pen.. i ll wait.. got it? now take note:"

And explain them everything...

Them you say

"Now when another customer like me call you, just read that paper ok?"

 :roll:

---

### Post by polo_step on 2005-06-28
[QUOTE=sapo]
And explain them everything...[/QUOTE]
After talking to these people, I am absolutely convinced that it's beyond their comprehension.

No matter how hard I'd yell. :grin:

---

### Post by gil-galad on 2005-06-28
Hehe, thats sbc for you.  :)

To anwser your other question, download speeds and upload speeds are seperate.  The upload speed will be slower too.

---

### Post by sapo on 2005-06-28
[QUOTE=polo_step]After talking to these people, I am absolutely convinced that it's beyond their comprehension.

No matter how hard I'd yell. :grin:[/QUOTE]

rotf [img]http://www.ticats.ca/modules/PNphpBB2/images/smiles/rotf.gif[/img]

---

### Post by aragorn2909 on 2005-06-29
[QUOTE=polo_step]
So, do you mean that something that simple is TOTALLY beyond SBC's ability to explain?
[/QUOTE]

I'm not how SBC does things, but if its anything like up here in Canada with Bell Sympatico, "Customer Service" is nothing more than a call-centre employee reading off a script.  Guess thats just something new to add to their's.  (script that is)

---

### Post by WildTangent on 2005-06-29
[QUOTE=aragorn2909]I'm not how SBC does things, but if its anything like up here in Canada with Bell Sympatico, "Customer Service" is nothing more than a call-centre employee reading off a script.  Guess thats just something new to add to their's.  (script that is)[/QUOTE]
most of the Cogeco tech support staff know what theyre talking about :)

-Wild

---

