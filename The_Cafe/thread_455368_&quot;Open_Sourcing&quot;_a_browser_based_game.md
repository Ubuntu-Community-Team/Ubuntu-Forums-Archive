---
title: "&quot;Open Sourcing&quot; a browser based game"
date: 2007-05-26
forum: The Cafe
---

### Post by Luca1985 on 2007-05-26
Hiya,

I have been thinking about writing a browser based game and I have been pondering the idea of making it open source. The game it's still not even on paper yet, but the idea has been in the air for a few months and I would like to get on working on it properly during the lazy summer days.

I have no experience in developing open source games (or games for that matter), 0 knowledge of licensing and even less knowledge of the open source culture/community.

Right, now that I have put myself in place... here are the questions:

[LIST=1]
[*]How would I know what the most appropriate open source license should be?
[*]How do open source licenses apply to browser based games in comparison to other applications.
[*]Could I still charge for premium accounts for my servers?
[*]Would it be possible for anyone to take the code, improve it and run their own server in competition to mine...in other words what makes people contribute back to the main repository instead of forking off with their own better version? Is there anything stopping them doing this?
[*]If someone did take the source code and changed it without making the changes available, how would I know (given it's running on a webserver somewhere) and is there anything I can do about it.
[/LIST]

Thanks for the help

Ciao
Luca

---

### Post by Ebuntor on 2007-05-26
> **Luca1985 said:**
> Hiya,

I have been thinking about writing a browser based game and I have been pondering the idea of making it open source. The game it's still not even on paper yet, but the idea has been in the air for a few months and I would like to get on working on it properly during the lazy summer days.

I have no experience in developing open source games (or games for that matter), 0 knowledge of licensing and even less knowledge of the open source culture/community.

Right, now that I have put myself in place... here are the questions:[LIST=1]
[*]How would I know what the most appropriate open source license should be?
[*]How do open source licenses apply to browser based games in comparison to other applications.
[*]Could I still charge for premium accounts for my servers?
[*]Would it be possible for anyone to take the code, improve it and run their own server in competition to mine...in other words what makes people contribute back to the main repository instead of forking off with their own better version? Is there anything stopping them doing this?
[*]If someone did take the source code and changed it without making the changes available, how would I know (given it's running on a webserver somewhere) and is there anything I can do about it.[/LIST]Thanks for the help

Ciao
Luca

I'm sure there are members who can answer these questions a lot better than I can but I'll give it a shot. I can't answer the first two questions.

> 3. Could I still charge for premium accounts for my servers?Absolutely, I know the GNU GPL ([FONT=Arial, Helvetica, sans-serif][SIZE=2]General Public License) allows you to commercialize your product. You could even let people pay for the source code.


[/SIZE][/FONT]> Would it be possible for anyone to take the code, improve it and run their own server in competition to mine...in other words what makes people contribute back to the main repository instead of forking off with their own better version? Is there anything stopping them doing this?That's a very good question I have no idea, I'm sure the GPL would potect you against that.

> 
If someone did take the source code and changed it without making the changes available, how would I know (given it's running on a webserver somewhere) and is there anything I can do about it.I know that the GPL would protect you against someone doing that. Not sure about other [FONT=Arial, Helvetica, sans-serif][SIZE=2]licenses[/SIZE][/FONT]. But how you could find out? I don't know. Don't think that's possible.

Anyway sounds like a great idea! Good luck with your game.

---

### Post by Luca1985 on 2007-05-26
Thanks Ebuntor,

Just a couple of questions on what you have said:

> 
Absolutely, I know the GNU GPL (General Public License) allows you to commercialize your product. You could even let people pay for the source code.

If I did apply the GNU GPL and sold the source code on (which I do not want to do) according to wikipedia ([GNU_General_Public_License]("http://en.wikipedia.org/wiki/GNU_General_Public_License") in the Terms and conditions it says: "Any licensee who adheres to the terms and conditions is given permission to modify the work, as well as to copy and redistribute the work or any derivative version." Whis seems to mean that if I sell 1 copy, then the licensee can basically do what they like with it including improving it and selling it onwards. This is what I would like to avoid others from doing.

> Would it be possible for anyone to take the code, improve it and run their own server in competition to mine...in other words what makes people contribute back to the main repository instead of forking off with their own better version? Is there anything stopping them doing this? 
Reading from wikipedia (again) I believe that is completly the opposite :|

Is my English that terrible?

> 
Anyway sounds like a great idea! Good luck with your game

Thanks ;)!

Ciao
Luca

---

### Post by Anthem on 2007-05-26
Sounds like a job for the Affero GPL.

[http://en.wikipedia.org/wiki/Affero_General_Public_License](http://en.wikipedia.org/wiki/Affero_General_Public_License)

---

### Post by Polygon on 2007-05-26
I know you can commercialize your product

people who modify the source code has to have their product or your code under the same licence (gpl) , im not sure if they are "forced" to contribute back to your code but since their code is under the GPL you could always go look at what they changed.

and if someone violated the GPL, they are of course breaking the terms of your licence, im sure the FSF has something on their site on what to do if a person/companies breaks your licence

---

### Post by Hex_Mandos on 2007-05-26
> **Luca1985 said:**
> 
If I did apply the GNU GPL and sold the source code on (which I do not want to do) according to wikipedia ([GNU_General_Public_License]("http://en.wikipedia.org/wiki/GNU_General_Public_License") in the Terms and conditions it says: "Any licensee who adheres to the terms and conditions is given permission to modify the work, as well as to copy and redistribute the work or any derivative version." Whis seems to mean that if I sell 1 copy, then the licensee can basically do what they like with it including improving it and selling it onwards. This is what I would like to avoid others from doing.

That's the whole point of Open Sourcing software, you know... I think you might be mistaken about the meaning of 'Open Source'. It doesn't mean "Including source code that can't be modified or copied".  You should read the FSF's definition of Free Software and OSI's Open Source Definition before you decide to open up your program. They aren't EXACTLY the same, but there's a lot of overlap. The FSF's definition is simpler, so I list it first.

**FSF's Free Software Definition:**

“Free software” is a matter of liberty, not price. To understand the concept, you should think of “free” as in “free speech”, not as in “free beer”.

Free software is a matter of the users' freedom to run, copy, distribute, study, change and improve the software. More precisely, it refers to four kinds of freedom, for the users of the software:

    *  The freedom to run the program, for any purpose (freedom 0).
    * The freedom to study how the program works, and adapt it to your needs (freedom 1). Access to the source code is a precondition for this.
    * The freedom to redistribute copies so you can help your neighbor (freedom 2).
    * The freedom to improve the program, and release your improvements to the public, so that the whole community benefits (freedom 3). Access to the source code is a precondition for this.

**Open Source Definition**

The distribution terms of open-source software must comply with the following criteria:

1. Free Redistribution
The license shall not restrict any party from selling or giving away the software as a component of an aggregate software distribution containing programs from several different sources. The license shall not require a royalty or other fee for such sale.

2. Source Code
The program must include source code, and must allow distribution in source code as well as compiled form. Where some form of a product is not distributed with source code, there must be a well-publicized means of obtaining the source code for no more than a reasonable reproduction cost preferably, downloading via the Internet without charge. The source code must be the preferred form in which a programmer would modify the program. Deliberately obfuscated source code is not allowed. Intermediate forms such as the output of a preprocessor or translator are not allowed.

3. Derived Works
The license must allow modifications and derived works, and must allow them to be distributed under the same terms as the license of the original software.

4. Integrity of The Author's Source Code
The license may restrict source-code from being distributed in modified form only if the license allows the distribution of "patch files" with the source code for the purpose of modifying the program at build time. The license must explicitly permit distribution of software built from modified source code. The license may require derived works to carry a different name or version number from the original software.

5. No Discrimination Against Persons or Groups
The license must not discriminate against any person or group of persons.

6. No Discrimination Against Fields of Endeavor
The license must not restrict anyone from making use of the program in a specific field of endeavor. For example, it may not restrict the program from being used in a business, or from being used for genetic research.

7. Distribution of License
The rights attached to the program must apply to all to whom the program is redistributed without the need for execution of an additional license by those parties.

8. License Must Not Be Specific to a Product
The rights attached to the program must not depend on the program's being part of a particular software distribution. If the program is extracted from that distribution and used or distributed within the terms of the program's license, all parties to whom the program is redistributed should have the same rights as those that are granted in conjunction with the original software distribution.

9. License Must Not Restrict Other Software
The license must not place restrictions on other software that is distributed along with the licensed software. For example, the license must not insist that all other programs distributed on the same medium must be open-source software.

*10. License Must Be Technology-Neutral
No provision of the license may be predicated on any individual technology or style of interface.

**Useful links:**

[http://www.gnu.org](http://www.gnu.org) 
[http://www.opensource.org](http://www.opensource.org) 
[http://www.fsf.org](http://www.fsf.org)

---

### Post by Bachstelze on 2007-05-26
If you force people that download your code to contribute back, or even to tell you about it, that would be a restriction making your program non-free. But of course if someone uses your GPL code, he must GPL his one also, so you can get his source and use it to improve your original game, but you cannot force him to give it to you.

---

### Post by Ebuntor on 2007-05-26
> **Luca1985 said:**
> Thanks Ebuntor,

You're welcome
> 
If I did apply the GNU GPL and sold the source code on (which I do not want to do) according to wikipedia ([GNU_General_Public_License]("http://en.wikipedia.org/wiki/GNU_General_Public_License") in the Terms and conditions it says: "Any licensee who adheres to the terms and conditions is given permission to modify the work, as well as to copy and redistribute the work or any derivative version." Whis seems to mean that if I sell 1 copy, then the licensee can basically do what they like with it including improving it and selling it onwards. This is what I would like to avoid others from doing.
As Polygon already mentioned if people take your code and use it for their own project they'll also have to release it under the GPL (if I understand it correctly, please correct me if I'm wrong).  That means you could take a look at their code,  see what they changed and use the improvements. That's the idea behind it.

If you don't want people to take your code and use it themselves I'm sure there are other licenses that are GPLish and let you keep the code closed.


> Is my English that terrible?Not at all, although English isn't my native language ether.

---

### Post by Luca1985 on 2007-05-26
I see what you are all saying,

I had a read at both the AGPL and the GPL and they both seem fit for the job, but how would I tell if someone is ripping my code and reusing it somewhere else without making the code available to everyone? That's what worries me the most.

Ciao
Luca

---

### Post by Ebuntor on 2007-05-26
Might I ask why you actually want to make it Open Source? Is it because of the ethical aspect or because you'd like people to help you with programming? 

I've long been an active member of the [Urban Dead]("http://urbandead.com/") browser game community. The creator, Kevan Davis, originally kept the game closed source but after a few years he did give active/trusted members access to the code to help out.

So you could use a similar tactic. Not really make it open source just show parts to people you trust.

---

### Post by Luca1985 on 2007-05-26
> **Ebuntor said:**
> Might I ask why you actually want to make it Open Source? Is it because of the ethical aspect or because you'd like to people to help you with programming? 

I've been long been an active member of the [Urban Dead]("http://urbandead.com/") browser game community. The creator, Kevan Davis, originally kept the game closed source but after a few years he did give active/trusted members access to the code to help out.

So you could use a similar tactic. Not really make it open source just show parts to people you trust.

You do make a super valid point.
Why do I want to make it open source? I know that there are a lot of people out there that know a lot more than I do and could contribute greatly to the project.
I would like it to be mainly for ethical reasons, but hey... I am Italian... so I am exposed to "unethicalness" at every junction I TRY to drive through and every pedestrian crossing I TRY to cross... which is what pushes me most away from the open source route.

Maybe I could be scared to just not be good enough to maintain the project and see someone else thriving on the wings of my enthusiasm... but then I think that it would happen regarless if it's open source or not.

You guys have given me a lot to think about!

If I do decide to make it open source... is sourcefourge the best starting point?

Thanks
Ciao
Luca

---

### Post by Hex_Mandos on 2007-05-26
> **Luca1985 said:**
> I would like it to be mainly for ethical reasons, but hey... I am Italian... so I am exposed to "unethicalness" at every junction I TRY to drive through and every pedestrian crossing I TRY to cross... which is what pushes me most away from the open source route.

Hey, I'm Argentinian, so I'm in pretty much the same situation (or maybe even worse). However, I think free/open source software (and the Free Culture movement in general) is a better option because it enables people to help you: there will ALWAYS be people who use your stuff without compensating you, you might as well take some benefit from it by demanding attribution, copyleft, etc. and reaping the benefits of a more open development model. It's also good PR.

---

### Post by Luca1985 on 2007-05-27
> **Hex_Mandos said:**
> Hey, I'm Argentinian, so I'm in pretty much the same situation (or maybe even worse). However, I think free/open source software (and the Free Culture movement in general) is a better option because it enables people to help you: there will ALWAYS be people who use your stuff without compensating you, you might as well take some benefit from it by demanding attribution, copyleft, etc. and reaping the benefits of a more open development model. It's also good PR.

I believe you make a very strong point here...

May I just ask... is the GPL is a strong and full copyleft license?
I was trying to learn some more on these interesting topics on [Copyleft]("http://en.wikipedia.org/wiki/Copyleft")  and it does briefly touch on GPL.

The other question is that on [http://en.wikipedia.org/wiki/GNU_General_Public_License]("http://en.wikipedia.org/wiki/GNU_General_Public_License") there is no talk about images being released under GPL. More clearly:
Does GPL only apply to source code?

Thanks
Luca

---

### Post by Ozor Mox on 2007-05-27
Hey Luca, I can actually answer some of this :D

Yes, the GNU GPL is strong copyleft, in that it forces any software using your work to be released under the GPL as well (allowing you to take back the contributions from them as mentioned before), hence this particular freedom is sacrificed in order to keep the software free, unlike for example, the BSD license.

Secondly, yes I'm pretty sure the GPL does apply to art, music, and so on as well as source code. If you were to use the LGPL, that would allow the non-source code components such as these to be used in proprietary software. The standard GPL licenses everything as copyleft. Please, someone correct me if I'm wrong.

Something else that might be helpful:

[List of free software licenses](http://www.fsf.org/licensing/licenses/)

---

