---
title: "My lab partner has Ubuntu..."
date: 2010-09-07
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-09-07
We were sitting in a study room kind workingish on our lab report sort of and one of my lab partners began to complain how my other lab partner sent her the lab report in some messed up file (.odt she was unaware that MS Office can read these which means she didn't even double click on it). He then mentioned how he uses Ubuntu and he couldn't connect to our schools Citrix server even though they have the client software for Linux, but it doesn't seem to work. So I was like "I use Ubuntu!". He told me he was just using it to learn Linux. I can't believe I would meet someone else who uses it in the world much less my school besides my programming teacher. Turns out there's others at my school that use it according to my lab partner.

---

### Post by pwnst*r on 2010-09-07
> **Legendary_Bibo said:**
> (.odt she was unaware that MS Office can read these **which means she didn't even double click on it**). 

And why would she if she doesn't recognize the extension or it's not associated with Office on her PC yet?  She did the smart thing, in my opinion.

---

### Post by kaldor on 2010-09-07
> .odt she was unaware that MS Office can read these which means she didn't even double click on it

Wait what? Office can open those?

---

### Post by Cam42 on 2010-09-07
> **kaldor said:**
> Wait what? Office can open those?

Yeah, Office 2007 SP2 and Office 2010.

---

### Post by Dustin2128 on 2010-09-07
> **kaldor said:**
> Wait what? Office can open those?
I believe they were pressured into it by ISO. Anyway, that's cool. I've only met 3 people who knew about linux before I told them about it, and none of them use it.

---

### Post by smellyman on 2010-09-07
> **Legendary_Bibo said:**
> We were sitting in a study room kind workingish on our lab report sort of and one of my lab partners began to complain how my other lab partner sent her the lab report in some messed up file (.odt she was unaware that MS Office can read these which means she didn't even double click on it). He then mentioned how he uses Ubuntu and he couldn't connect to our schools Citrix server even though they have the client software for Linux, but it doesn't seem to work. So I was like "I use Ubuntu!". He told me he was just using it to learn Linux. I can't believe I would meet someone else who uses it in the world much less my school besides my programming teacher. Turns out there's others at my school that use it according to my lab partner.
 
 
I have no trouble with Ubuntu connecting to citrix.

---

### Post by Legendary_Bibo on 2010-09-07
> **smellyman said:**
> I have no trouble with Ubuntu connecting to citrix.

How'd you do it? With ours we're given a shell script that I've ran through, and yet it still won't connect.

---

### Post by Thryn on 2010-09-07
I was complaining about how all the tutorials they've been giving us are useless for me since they're Windows XP only and I have 7 and Ubuntu (and mostly use Ubuntu...) and it turned out the girl next to me uses Ubuntu as well. So now we're lab partners. And we make fun of the school for being Windows-centric and ourselves for trying to use common Linux/Unix commands like cd and ls on the Windows command line (the only part of our lab so far that wasn't trivially easy... the rest was pretty much 'resize the window' 'use the Print Screen key' 'make a folder' etc.).

---

### Post by dfreer on 2010-09-07
> **Thryn said:**
> And we make fun of the school for being Windows-centric and ourselves for trying to use common Linux/Unix commands like **cd** and ls on the Windows command line

What version of windows 7 are you using that doesn't allow you to use the cd command?

---

### Post by smellyman on 2010-09-08
> **Legendary_Bibo said:**
> How'd you do it? With ours we're given a shell script that I've ran through, and yet it still won't connect.
 
 
I just went to the Citrix site and installed the Deb from [here]("http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755")

---

### Post by Legendary_Bibo on 2010-09-08
> **smellyman said:**
> I just went to the Citrix site and installed the Deb from [here]("http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755")

I tried it, and I had to force the dpkg on it because they only had i386, and I have an AMD 64. What I did to get it to work was to go into usr/share/ca-certificates/mozilla and I just copy and pasted all the certificates into the keystore file of my Citrix file, and it worked!

I only found out this solution from a comment on a blog post talking about how to get citrix to work which involved a bunch of commands.

---

### Post by smellyman on 2010-09-08
Citrix can be a pain even on windows too if you dont use IE.

I have had to copy all the dll's to the mozilla profile directory to get it to work.

Has worked great on Linux for me.

---

### Post by Dragonbite on 2010-09-08
I have one of those black Ubuntu baseball caps and have gotten a number of people commenting on it (if they know what it is, most don't even notice).

One guy, during a Christmas tree lighting, next to me asked "how many people do you think knows that that [Ubuntu] means?"  or a person I saw in the library who rolled her eyes and said her dad uses it.

What I love is that I don't have to be obtrusive at all. If somebody recognizes it they seem to say something, otherwise to everybody else it's just a hat.

Oh, and I'll be testing the Citrix when our company switches over in the coming months.

---

### Post by MasterNetra on 2010-09-08
> **dfreer said:**
> What version of windows 7 are you using that doesn't allow you to use the cd command?

+1 
I have Win7 and I can use cd to change directory on the command line.

---

### Post by del_diablo on 2010-09-08
> **smellyman said:**
> Citrix can be a pain even on windows too if you dont use IE.

My only encounter with Citrix was when I forced her to use JAVA instead of Active X(which default does not exists on IE8).
And then it worked, magically.

---

### Post by jpeddicord on 2010-09-08
> **Cam42 said:**
> Yeah, Office 2007 SP2 and Office 2010.

Quite well too -- I've yet to find an OpenDocument file that 2010 won't open correctly. They actually did a pretty good job supporting it.

---

### Post by themusicalduck on 2010-09-08
> **jpeddicord said:**
> Quite well too -- I've yet to find an OpenDocument file that 2010 won't open correctly. They actually did a pretty good job supporting it.

You'd think if Microsoft were pressured into supporting .odt, they could be pressured into helping Open Office to support .doc fully.

---

### Post by Bölvaður on 2010-09-08
in my formal language class there are many ppl that are using ubuntu and I know there are many linux users there, for me it is starting to be the standard.

---

### Post by annoyingrob on 2010-09-08
Most of the Engineering and Computer Science computer labs at my university are Linux based. It was quite a shock to 99% of the students to walk into a computer lab, and be expected to navigate Fedora Core rather than Windows XP. That was probably 7 years ago now. These days, I don't see a lot of complaining.

I think it was a great choice for the university to switch.

---

### Post by Dragonbite on 2010-09-09
> **themusicalduck said:**
> You'd think if Microsoft were pressured into supporting .odt, they could be pressured into helping Open Office to support .doc fully.

I'm supposed to help MY competitor be compatible with MY product even though I had to spend MY time making MY product compatible with theirs?  

That doesn't sound like good businesses, it sounds like charity.

---

### Post by NCLI on 2010-09-09
> **Dragonbite said:**
> I'm supposed to help MY competitor be compatible with MY product even though I had to spend MY time making MY product compatible with theirs?  

That doesn't sound like good businesses, it sounds like charity.

Isn't capitalism great? :p

---

