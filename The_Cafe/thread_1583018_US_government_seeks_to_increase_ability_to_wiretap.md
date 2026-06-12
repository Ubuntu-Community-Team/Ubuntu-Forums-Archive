---
title: "US government seeks to increase ability to wiretap the internet"
date: 2010-09-27
forum: The Cafe
---

### Post by Cuddles McKitten on 2010-09-27
[http://www.nytimes.com/2010/09/27/us/27wiretap.html?pagewanted=all](http://www.nytimes.com/2010/09/27/us/27wiretap.html?pagewanted=all)

Essentially it comes down to the fact that the FBI seems to be rather sick of encryption.  Assuming such a bill were passed, wouldn't that completely invalidate things like SSL?  Who's going to go shopping online when your credit card information is getting intercepted by crackers who can then decrypt the data and steal it?

P.S.: Please keep to the topic of the article rather than anything related to the unspeakable P word that gets threads locked.

---

### Post by pwnst*r on 2010-09-27
This disturbs me on every level.

---

### Post by CJ Master on 2010-09-27
I doubt it'll pass.

---

### Post by Paqman on 2010-09-27
What are they going to do about software designed outside of their jurisdiction? Or are they suggesting that you would only be able legally able to run compliant software on a US network? Good luck with enforcing that!

On the surface it seems like a reasonable idea. Software would have to be written so that the users' communications could be coughed up if a lawful request was made for them. But I don't see how it would actually improve security. Hardcore criminals would just communicate using non-compliant software.

---

### Post by ironhoof on 2010-09-27
I agree completely. Thats why they call it crime. The lawful people will be easy to track. The criminals will use the encryption anyway. This is the same with any law. 

"Laws are like locks, and they are for honest people."

---

### Post by Shpongle on 2010-09-27
Team America World Police . . . . is what comes to mind . 

this "Hardcore criminals would just communicate using non-compliant software."

so what happens to pgp , truecrypt and the rest ?

---

### Post by Cavsfan on 2010-09-27
It also mentions this: "Several privacy and technology advocates argued that requiring  interception capabilities 
would create holes that would inevitably be  exploited by hackers."
I think it is a step backwards and hope it doesn't pass.  However China and some other countries have hired 
hackers to work for their govt. I do not know the ramifications if we do not stay ahead of them, nor how we could.

---

### Post by Paqman on 2010-09-27
> **Shpongle said:**
> 
so what happens to pgp , truecrypt and the rest ?

It seems to be aimed at "services that enable communications", rather than encryption per se. As it stands, the law can already demand the keys to decrypt anything anyway, and the penalties for refusing to cough up your keys are hefty. Major jail time.

Basically they want companies to make sure they build their services in a way that they actually can access a user's communications if required. That doesn't mean the communications can't be encrypted, just that the service provider has to be *able* to provide an unencrypted copy on demand.

---

### Post by PC_load_letter on 2010-09-27
> **pwnst*r said:**
> This disturbs me on every level.

++1. I was just reading this story on slashdot.org and this is very disturbing coming from this president.

Just to understand this better, so ,IF this thing passes, would this make ssh and ssl or https in their current form illegal? And for the brilliant a. hole who drafted this legislation, if there is a back door for the companies to decrypt its internet traffic, wouldn't hackers figure it out and then bye bye internet security? 

And what's stopping the bad guys from encrypting their messages BEFORE they send it, so this cavity search of a legislation will be useless anyway.

---

### Post by Roasted on 2010-09-27
LOL.

Oh Government. Stop being so silly.

---

### Post by Paqman on 2010-09-28
> **PC_load_letter said:**
> 
Just to understand this better, so ,IF this thing passes, would this make ssh and ssl or https in their current form illegal?

That's not at all clear, and if it was drafted to suggest this, it'd get shot down due to being unworkable. I suspect that what they would be aiming for would be that it would be illegal to operate a service using a protocol that prevented you from reading your users' data, but that such protocols themselves would not be illegal.

---

### Post by dmn_clown on 2010-09-28
> **Cuddles McKitten said:**
> Essentially it comes down to the fact that the FBI seems to be rather sick of encryption.  Assuming such a bill were passed, wouldn't that completely invalidate things like SSL?  Who's going to go shopping online when your credit card information is getting intercepted by crackers who can then decrypt the data and steal it?

Actually, it comes down to the FBI wanting to be able to do things it already has the authority to do on land lines.

---

### Post by Paqman on 2010-09-28
> **dmn_clown said:**
> Actually, it comes down to the FBI wanting to be able to do things it already has the authority to do on land lines.

And with your ISP. This really only extends current powers to companies providing a communication service over the internet that uses some sort of encryption, such as Skype and Blackberrys. 

Speaking of RIM, their CEO was in the news today talking about providing governments with a way of [intercepting Blackberry traffic]("http://www.theregister.co.uk/2010/09/28/rim_encryption/"). He's at risk of India banning his service the same way UAE did if he doesn't provide a way of them snooping into his users' emails.

---

### Post by Señor Banana on 2010-09-28
> **Paqman said:**
> And with your ISP. This really only extends current powers to companies providing a communication service over the internet that uses some sort of encryption, such as Skype and Blackberrys. 

Speaking of RIM, their CEO was in the news today talking about providing governments with a way of [intercepting Blackberry traffic]("http://www.theregister.co.uk/2010/09/28/rim_encryption/"). He's at risk of India banning his service the same way UAE did if he doesn't provide a way of them snooping into his users' emails.
Invasion of privacy, ho hum.
This is why I love decentralized communications, vpns, multi-layer encryption, key files, and shredding. They can go on forever if they want to decrypt the communications, and if they demand the key, you can't give it to em. Many VOIP encryption programs provide the function of shredding the keyfile after ending the session.

The more the government wants to invade people's privacy, the more I look for ways to beef up my security and privacy. I think the next step will be going to tokens and PSK, now I just have to find a way to implement those. The problem would be having a set PSK for all communications without it being intercepted by 3rd party members, probably steganography. Tokens would be needed as a way of authentication, on top of PKI...but I don't know of any software for storing the identity validation keys. Now, to find implementations of AES256 or stronger encryption protocols.

---

### Post by ubunterooster on 2010-09-28
I forsee [TOR]("http://www.torproject.org/") and such like proxies becoming more popular

---

### Post by Calash on 2010-09-28
I can not see how this would pass or even be taken seriously.  Half the politicians still seem to thing the Internet is this spooky place where kids chat and watch videos over their 2400 baud modems.

Never mind the simple fact that the US does not own the Internet, despite what Al Gore says.  Unless the bill is going to include provisions to firewall off the US and require foreign service providers to comply this law will be nothing more than a reason to visit non-US sites.

---

### Post by Paqman on 2010-09-28
> **Señor Banana said:**
> Invasion of privacy, ho hum.


Your right to privacy (quite sensibly) does not extend to illegal activities. Nobody is suggesting blanket surveillance of the innocent.

---

### Post by Paqman on 2010-09-28
> **Calash said:**
> Unless the bill is going to include provisions to firewall off the US and require foreign service providers to comply this law will be nothing more than a reason to visit non-US sites.

It's suggested that in order to provide a service in the US a company would have to open an office there (and presumably route traffic through it?). Quite how they'd enforce such a rule is another thing. They do seem to think that the US has it's own special internet that can be neatly fenced off and controlled.

---

### Post by Señor Banana on 2010-09-28
> **Paqman said:**
> Your right to privacy (quite sensibly) does not extend to illegal activities. Nobody is suggesting blanket surveillance of the innocent.
[http://en.wikipedia.org/wiki/NSA_warrantless_surveillance_controversy](http://en.wikipedia.org/wiki/NSA_warrantless_surveillance_controversy)
[http://www.dailytech.com/Whistleblower+Says+NSA+Monitors+Everybody+Targets+Reporters+and+Dissidents/article14038.htm](http://www.dailytech.com/Whistleblower+Says+NSA+Monitors+Everybody+Targets+Reporters+and+Dissidents/article14038.htm)
[http://www.crackerjax.org/index.php/defcon/54-defcon-15/122-portable-privacy](http://www.crackerjax.org/index.php/defcon/54-defcon-15/122-portable-privacy)

---

### Post by Dustin2128 on 2010-09-28
I don't see the point, when any person doing something secret who has a quarter of a brain stem encrypts communications BEFORE sending them.

---

### Post by Paqman on 2010-09-28
> **Señor Banana said:**
> [http://en.wikipedia.org/wiki/NSA_warrantless_surveillance_controversy](http://en.wikipedia.org/wiki/NSA_warrantless_surveillance_controversy)
[http://www.dailytech.com/Whistleblower+Says+NSA+Monitors+Everybody+Targets+Reporters+and+Dissidents/article14038.htm](http://www.dailytech.com/Whistleblower+Says+NSA+Monitors+Everybody+Targets+Reporters+and+Dissidents/article14038.htm)
[http://www.crackerjax.org/index.php/defcon/54-defcon-15/122-portable-privacy](http://www.crackerjax.org/index.php/defcon/54-defcon-15/122-portable-privacy)

I don't really want to get into a political debate and i'm not at all versed in the topic you link to, i'm just pointing out that what they're suggesting isn't an extension of their current powers or a further erosion of your rights. Whether or not you think that the current situation is desirable or not is another matter.

---

### Post by Paqman on 2010-09-28
> **Dustin2128 said:**
> I don't see the point, when any person doing something secret who has a quarter of a brain stem encrypts communications BEFORE sending them.

Criminals aren't renowned for being especially bright.

---

### Post by Señor Banana on 2010-09-28
> **Paqman said:**
> I don't really want to get into a political debate and i'm not at all versed in the topic you link to, i'm just pointing out that what they're suggesting isn't an extension of their current powers or a further erosion of your rights. Whether or not you think that the current situation is desirable or not is another matter.
That is just to show that those agencies are known to abuse their abilities.
What they suggest and what they do are two separate things, that's the problem.

---

### Post by Lucradia on 2010-09-28
> **CJ Master said:**
> I doubt it'll pass.

yes it will: [http://action.eff.org/site/MessageViewer?em_id=13241.0&dlv_id=26862](http://action.eff.org/site/MessageViewer?em_id=13241.0&dlv_id=26862)

---

### Post by Dustin2128 on 2010-09-28
> **Paqman said:**
> Criminals aren't renowned for being especially bright.
oh, I was under the impression this was going after larger targets than your average drug store robber. 
*sigh*

---

### Post by Calash on 2010-09-28
> **Lucradia said:**
> yes it will: [http://action.eff.org/site/MessageViewer?em_id=13241.0&dlv_id=26862](http://action.eff.org/site/MessageViewer?em_id=13241.0&dlv_id=26862)

I fully support the efforts of the EFF, however I do take exception with that page.  Specifically

> 
The U.S. government has made two proposals this week that threaten online speech and privacy in radical new ways. 


What week are we talking about?  What proposals?  There is no date to even know if the page is outdated.

That page just screams "Google landing page to get donations" to me.  It could be just bad page design.

---

### Post by Lucradia on 2010-09-28
> **Calash said:**
> That page just screams "Google landing page to get donations" to me.  It could be just bad page design.

Good thing I just got the email today in my gmail inbox.

---

### Post by KiwiNZ on 2010-09-28
Please remember the rules for this section.This thread is getting close to closure.

---

### Post by MasterNetra on 2010-09-28
> **CJ Master said:**
> I doubt it'll pass.

And even if it does, I expect politicians will be getting tons of flak. Especially if the news media points out what this means for online shopping and that it makes you considerably more prone to Identity theft.

---

### Post by Dustin2128 on 2010-09-28
> **MasterNetra said:**
> And even if it does, I expect politicians will be getting tons of flak. Especially if the news media points out what this means for online shopping and that it makes you considerably more prone to Identity theft.
you know, I'm kind of wondering how this would affect FLOSS peer to peer networks (they were also planning on mandating a gov't backdoor). Since the backdoor's source would have to be available (don't know how to phrase that much better), wouldn't that make it 10^9 times easier to get into CSS backdoors? If even a few lines of source have to be closed on a GPL program, the LoD clause means the program can't be distributed at all.

---

### Post by MasterNetra on 2010-09-28
> **Dustin2128 said:**
> you know, I'm kind of wondering how this would affect FLOSS peer to peer networks (they were also planning on mandating a gov't backdoor). Since the backdoor's source would have to be available (don't know how to phrase that much better), wouldn't that make it 10^9 times easier to get into CSS backdoors? If even a few lines of source have to be closed on a GPL program, the LoD clause means the program can't be distributed at all.

Dunno, I think the government just wants enough access so they can spy on people. Not create backdoors to everything.

---

### Post by Dustin2128 on 2010-09-28
> **MasterNetra said:**
> Dunno, I think the government just wants enough access so they can spy on people. Not create backdoors to everything.
I was talking about a different, though related, proposal.

---

### Post by earthpigg on 2010-09-28
How do you put a secret backdoor in Open Source communication software?

---

### Post by Ric_NYC on 2010-09-28
Oh, the "change"!

---

### Post by Dustin2128 on 2010-09-28
> **earthpigg said:**
> How do you put a secret backdoor in Open Source communication software?
my point exactly.

---

### Post by Calash on 2010-09-28
> **earthpigg said:**
> How do you put a secret backdoor in Open Source communication software?

Surround it with comments that say ****DO NOT READ BELOW THIS LINE!!  THANK YOU, THE GOVERNMENT COMMISSION ON INTERNET MONITORING****


;)

---

### Post by sdowney717 on 2010-09-28
> How do you put a secret backdoor in Open Source communication software?

you dont, you just make it illegal to use it.
how useful will that be?
I wonder.

say you want the encryption software so you go get it, the ISP notifies the FEDS and they come visit you and charge you with a downloading illegal software crime.

---

### Post by Dustin2128 on 2010-09-28
> **Calash said:**
> Surround it with comments that say ****DO NOT READ BELOW THIS LINE!!  THANK YOU, THE GOVERNMENT COMMISSION ON INTERNET MONITORING****


;)
:lolflag:

---

### Post by Señor Banana on 2010-09-28
> **sdowney717 said:**
> you dont, you just make it illegal to use it.
how useful will that be?
I wonder.

say you want the encryption software so you go get it, the ISP notifies the FEDS and they come visit you and charge you with a downloading illegal software crime.
That's why you use alternative methods of transmission.
They tried something like that, with PGP, so the creator published the algorithm in a book and people just used OCR to get the algorithm.
If it comes to this, then I can only hope for an end to the government.
I've got plans as it is to move out of the country.

---

### Post by Lucradia on 2010-09-28
I need to get some FLOSS to remove all this political junk from in between my topics.

---

### Post by Chronon on 2010-09-29
> **Paqman said:**
> It seems to be aimed at "services that enable communications", rather than encryption per se. As it stands, the law can already demand the keys to decrypt anything anyway, and the penalties for refusing to cough up your keys are hefty. Major jail time.
My reading is also that this is aimed at services.  I can still perform encryption on my box and transmit the result.

---

### Post by Johnsie on 2010-09-29
The "Land of the Free" never ceases to amaze me when it comes to this type of thing. The US is nearly as bad as china when it comes to restrictions, patents and other such controls.

---

### Post by Señor Banana on 2010-09-29
> **Johnsie said:**
> The "Land of the Free" never ceases to amaze me when it comes to this type of thing. The US is nearly as bad as china when it comes to restrictions, patents and other such controls.
You and be both, man.
This pisses me off to no end.
However, I'm going to stop talking, because this is becoming a political issue for me.

---

### Post by Primefalcon on 2010-09-29
The guys can't force Ubuntu to make backdoors can they? [http://www.salon.com/news/opinion/glenn_greenwald/2010/09/27/privacy/index.html](http://www.salon.com/news/opinion/glenn_greenwald/2010/09/27/privacy/index.html)

---

### Post by Bachstelze on 2010-09-29
Yes, we can!

inb4close

---

### Post by Dustin2128 on 2010-09-29
no, backdoors are literally impossible in a GPL licensed program. Since the users can see all the code, they see any backdoors immediatley, and they have the right to remove them. Section 7 of the GPLv2 (what linux is licensed under) says that his section says that if somebody has restrictions imposed that prevent them from distributing GPL-covered software in a way that  respects other users' freedom (for example, if a legal ruling states  that he or she can only distribute the software in binary form), he or  she cannot distribute it at all. (Paraphrased from wikipedia). It's basically liberty or death. 

I heard about this and asked a question like this on the net wiretapping thread (still open no thanks to Bachstelze), and the general consensus was that they would simply ban FLOSS communication and peer to peer software. Iceland, here I come!

---

### Post by Bachstelze on 2010-09-29
> **Dustin2128 said:**
> no, backdoors are literally impossible in a GPL liscensed program. Since the users can see all the code, they see any backdoors immediatley,

No, that's not how it works. Remember the Debian OpenSSL fiasco.

---

### Post by Primefalcon on 2010-09-29
> **Bachstelze said:**
> No, that's not how it works. Remember the Debian OpenSSL fiasco.
Thats kind of what I am worried about, is the company (canonical, or the makers of GnuPG being forced to do it, and then users not noticing it).

I hope I am worrying about nothing and that unlike Windows, we're safe in this area. Personally I live in the u.S parents in in Australia, and I want privacy when i talk to my own parents and family, without worry that I am able to be spied on....

Also backdoors cough, hackers, cough

---

### Post by Bachstelze on 2010-09-29
> **Primefalcon said:**
> Thats kind of what I am worried about, is the company (canonical, or the makers of GnuPG being forced to do it, and then users not noticing it).

That seems unlikely, because neither Canonical not the main (basically, the only) GnuPG developer are located in the US. They could in theory force a US contributor to push a malicious change, though...

---

### Post by Primefalcon on 2010-09-29
Or do it themselves

---

### Post by Bachstelze on 2010-09-29
> **Primefalcon said:**
> Or do it themselves

That's also unlikely. A US government change to a security critical piece of software would draw *a lot* of attention, and likewise for a change by an anonymous individual, so they can't use a bogus identity either.

---

### Post by Primefalcon on 2010-09-29
> **Bachstelze said:**
> That's also unlikely. A US government change to a security critical piece of software would draw *a lot* of attention, and likewise for a change by an anonymous individual, so they can't use a bogus identity either.
Good point, and if any individual contributer is caught complying to do it, they'd heavily be watched after that

---

### Post by Dustin2128 on 2010-09-29
> **Bachstelze said:**
> No, that's not how it works. Remember the Debian OpenSSL fiasco.
true enough. But I'm not exactly optimistic (pessimistic rather?) about the US's cyber capabilities. They ran XP at the pentagon for years and never turned off autorun...

---

### Post by Bachstelze on 2010-09-29
> **Dustin2128 said:**
> true enough. But I'm not exactly optimistic (pessimistic rather?) about the US's cyber capabilities. They ran XP at the pentagon for years and never turned off autorun...

Surely you jest. The NSA has the world's best cybersecurity experts working behind their walls.

---

### Post by Dustin2128 on 2010-09-29
> **Bachstelze said:**
> Surely you jest. The NSA has the world's best cybersecurity experts working behind their walls.
I'm just joking about the vast inequalities.

---

### Post by cgroza on 2010-09-29
Just in USA. If I am not mistaken Ubuntu is based in England right?

---

### Post by Dustin2128 on 2010-09-29
> **cgroza said:**
> Just in USA. If I am not mistaken Ubuntu is based in England right?
yes, but [political statements edited out to keep thread open] if you know what I mean.

---

### Post by cascade9 on 2010-09-29
They cant force backdoors in, but there is the option of declaring any OS/program/hardware which doesnt comply 'illegal'. 

> **cgroza said:**
> Just in USA. If I am not mistaken Ubuntu is based in England right?

Technically, no. Canonical is registered on the Isle of Mann. Which isnt part of the UK, even though the UK is responsible for foreign relations and defence, and the queen is the head of state  (as 'the lord of mann' which I always find amusing). Mann is also not a part of the EU.

---

### Post by Shining Arcanine on 2010-09-29
> **Bachstelze said:**
> That's also unlikely. A US government change to a security critical piece of software would draw *a lot* of attention, and likewise for a change by an anonymous individual, so they can't use a bogus identity either.

No one checks to see if your identity if bogus or not:

[http://www.theregister.co.uk/2007/05/17/social_networking_hack_risk/](http://www.theregister.co.uk/2007/05/17/social_networking_hack_risk/)


> **Bachstelze said:**
> That seems unlikely, because neither Canonical not the main (basically, the only) GnuPG developer are located in the US. They could in theory force a US contributor to push a malicious change, though...

You do not need to be a contributor to put a backdoor into the repositories:

[http://forums.unrealircd.com/viewtopic.php?t=6562](http://forums.unrealircd.com/viewtopic.php?t=6562)

If the source was modified, compiled and packaged, with the tainted packages put into Canonical's repositories and the md5 sums updated, no one would know. It is not like people verify that the binaries they download are the same binaries produced by the same version of the same compiler when passed the same compiler options. Anyone studying the official source code would never see the backdoor.

For all we know, there are already several backdoors like this in Ubuntu Linux. The only way to avoid this kind of backdoor would be to use a source based distribution like Gentoo Linux.

---

### Post by Primefalcon on 2010-09-30
Well to do business in countries like the uk and us you need to be registered there if I am not mistaken, so governments could say no companies can pay for support contracts unless you capitulate.

Another thing is the UK are now considering this too... All I can say is damm the Emirates, they started this with the Blackberry

---

### Post by ubunterooster on 2010-09-30
> **cascade9 said:**
> They cant force backdoors in, but there is the option of declaring any OS/program/hardware which doesnt comply 'illegal'
This^^^


[CENTER]You and 27 friends like this[COLOR=White]----------------------------------[/COLOR][COLOR=Blue]_Dislike_[/COLOR]                             






[/CENTER]

---

### Post by formaldehyde_spoon on 2010-09-30
> **Paqman said:**
> It seems to be aimed at &quot;services that enable communications&quot;, rather than encryption per se. As it stands, the law can already demand the keys to decrypt anything anyway, and the penalties for refusing to cough up your keys are hefty. Major jail time.

...

Demands only applicable to companies which are able to produce the keys, and penalties only applicable to people in the US...hence the new bill.

 > **Shining Arcanine said:**
> ...
For all we know, there are already several backdoors like this in Ubuntu Linux. The only way to avoid this kind of backdoor would be to use a source based distribution like Gentoo Linux.

Or check the md5 sums when you download. 
Or compile yourself.
It only takes one person being paranoid and checking to alert the rest of the community --> there are no existing backdoors. 


This whole thing is fairly pointless.  There are plenty of other options for people wanting to use encryption.  It can only affect large, mainstream companies.

---

### Post by Primefalcon on 2010-09-30
> **cascade9 said:**
> They cant force backdoors in, but there is the option of declaring any OS/program/hardware which doesnt comply 'illegal'. 
I'd like to see them try to make Linux Illegal, too many companies rely on it for server infrastructure. You know though this would hurt companies like Redhat

---

### Post by ubunterooster on 2010-09-30
> **Primefalcon said:**
> I'd like to see them try to make Linux Illegal, too many companies rely on it for server infrastructure. You know though this would hurt companies like Redhat
This would also hurt MS (yes they have linux servers), Comcast, Google.... pretty much every large company

---

### Post by tony van on 2010-09-30
Look at "joe the plumber", when he confronted pres-elect obama, people from the Ohio campaigners who were civil servants looked into his backround and found he was in back payment of a bill. this will allow them to even look at your internet messages to digup more dirt if you disagree with them.
 
the woman who did it comitted a felony, but was given a slap on the wrist.

---

### Post by MooPi on 2010-09-30
Civil disobedience ! Word of the day. Randomly encrypt messages, email, content, and let the authorities try and figure it out. It could be nonsense or my mothers recipe for baked macaroni and cheese. Good fun. It is better to be the hammer then the nail. :wink:

---

### Post by Señor Banana on 2010-09-30
> **MooPi said:**
> Civil disobedience ! Word of the day. Randomly encrypt messages, email, content, and let the authorities try and figure it out. It could be nonsense or my mothers recipe for baked macaroni and cheese. Good fun. It is better to be the hammer then the nail. :wink:

I'd just talk about that stuff in plain text, tell people to go secure to talk about something private, and then give them the recipe.
Going in and out of encrypted  communications would drive them up the wall.

---

### Post by 98cwitr on 2010-09-30
this bill passes Ill quit using the Internet (except online game play on the PS3).

---

### Post by sdowney717 on 2010-09-30
I could see people encrypting what appears to be a non encrypted text.
Something like where you run an algorithm thru the text and it picks up every third word and makes it something else with a revolving key scheme.
So it appears non encrypted but it is encrypted with a hidden message. 
So it is plain site all the time and no one would suspect at all.

---

### Post by mips on 2010-09-30
I could'nt care less, I don't live in the USA and I really don't care if they looked at my comms.

---

### Post by Paqman on 2010-09-30
> **98cwitr said:**
> this bill passes Ill quit using the Internet (except online game play on the PS3).

LOL, no you won't. Have you quit using the telephone because they can eavesdrop on that?

---

### Post by Dustin2128 on 2010-10-04
> **Paqman said:**
> LOL, no you won't. Have you quit using the telephone because they can eavesdrop on that?

you'd be surprised.

---

### Post by Linewbie on 2010-10-05
> **Primefalcon said:**
> The guys can't force Ubuntu to make backdoors can they? [http://www.salon.com/news/opinion/glenn_greenwald/2010/09/27/privacy/index.html](http://www.salon.com/news/opinion/glenn_greenwald/2010/09/27/privacy/index.html)

I've always wondered why I have to be online to install Ubuntu now!
An extra special bit of "Patriot" Act Malware if you live in the U.S., maybe??

(And WHY on earth is this discussion not in the security sub-forum?)

I think SOMEONE was dropped on their head as a baby. (Hint Hint) 
](*,)

---

### Post by whiskeylover on 2010-10-05
> **Linewbie said:**
> I've always wondered why I have to be online to install Ubuntu now!
You don't.

> **Linewbie said:**
>  An extra special bit of "Patriot" Act Malware if you live in the U.S., maybe??
I thought I downloaded my ISO straight from ubuntu.com. I doubt the US govt made them put Malware in the code. 

Stop being so paranoid.

---

### Post by Dustin2128 on 2010-10-05
> **whiskeylover said:**
> You don't.

yeah, I'm still wondering what they meant. Maybe its that its difficult to run a computer with only a the software included in a vanilla ubuntu install, and its difficult to install software without the repos?

---

