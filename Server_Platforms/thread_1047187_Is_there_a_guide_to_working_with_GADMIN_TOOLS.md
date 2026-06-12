---
title: "Is there a guide to working with GADMIN TOOLS?"
date: 2009-01-22
forum: Server Platforms
---

### Post by hashbrowns on 2009-01-22
I'm new with Ubuntu Server, having been started out with the simple GUI interfaces of Windows Server 2003, so I'm not quite ready to dive into samba management with just a command line.

[GADMIN TOOLS]("http://gadmintools.flippedweb.com/") (more specifically, GADMIN-SAMBA) looks interesting, but I can't seem to find a detailed faq on how to use it.

Does anyone have any experience with using it? For example, I'm on the "shares" tab of it and I can't see any way to actually to make allow/deny permissions on the shares within the GUI. It really looks promising for a n00b like myself, though. :)

---

### Post by hyper_ch on 2009-01-22
> **hashbrowns said:**
> so I'm not quite ready to dive into samba management with just a command line.

why not?

---

### Post by hashbrowns on 2009-02-03
> **hyper_ch said:**
> why not?

I feel like it just might be too much for me right now, especially when I'm trying to teach classes at the same time as I manage this server. I mean, I'd love to learn, but it's about the level of time I can dedicate to it.

I mean, if there's only guides to the command line available, I guess I'll take what I can, of course. :P

But GADMIN seems to just be modifying the samba.conf file itself, but I don't know what the commands actually mean.

Is there a guide you might recommend? I know there are a lot available but that's the problem - there's so many that I don't know where to start.

---

### Post by hyper_ch on 2009-02-04
I'd start with the man pages.

---

### Post by hansdown on 2009-02-04
Hi hashbrowns.

There is a configuration guide pdf.

[http://www.google.ca/search?q=GADMIN+TOOLS+manual+for+ubuntu+server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=GADMIN+TOOLS+manual+for+ubuntu+server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Scroll down the list to find it.

---

### Post by HighlyDubious on 2009-09-05
> **hyper_ch said:**
> why not?

Because, believe it or not, not every one wants to be a Linux Guru. Not every one has the time or desire to become so proficient in Linux that they can do it in their sleep.

That describes me precisely.  As the OP originally stated, 

> **hashbrowns]... I'm not quite ready to dive into samba management with just a command line.[/quote]

Which, literally means -- **for reasons he is not required to give**, he is not currently ready to tackle samba from a command line. Period. End of sentence.

Your attitude towards those of us who are not CLI Gods is offensive and clearly conveys contempt for those who choose to have a different focus in life than becoming Linux Brainiacs.

Back 20 some odd years ago, I was an Amiga Guru. There was virtually nothing I didn't know, or couldn't do with my Amiga. And, like most power users, I rarely used the Workbench (Amiga's GUI), because I knew the 'real power' was in the CLI. Mind you, I'm not claiming past glory based on an inflated ego. Back then being "*The local guy who knows everything about Amiga*" was my day job. I was the head of Technical Support at the largest Amiga store in Houston, and I made regular trips to Commodore and to Amiga Conventions to keep constantly up to date. And when I wasn't learning in my day job, I'd go home and spend another 8-12+ hours a day learning and doing new stuff on my own time as a hobby. For a while, Amiga was my whole life. So I know very well what it's like to be an expert for a certain OS, and what it takes to both get to that level, and maintain it.

But that was 20 some odd years ago. Now I'm in a different part of my life, and knowing every tiny minutia about the current OS flavor-of-the-month is neither a goal, nor enjoyable to me. Now I have a life outside of my PC, and when I sit down to do things, I just want to have the resources and tools to get the job done. That includes using a GUI if such tools are available, AND reading easy to comprehend docs for how to use it.

I came to this thread from a Google search, because I too need to setup Samba, and Gadmin-Samba looks like a very useful GUI tool for doing that. And, like hashbrowns, I too am looking for useful documentation. So comments such as yours not only serve no purpose, they also convey contempt for newbies. Which is a great way to push people AWAY from Linux. When newbies go looking for answers, and all they get is attitude like yours, it leaves a bad impression, and it makes them wonder if maybe they'd be better off in the MS world. So, if your goal is to keep Linux as your own private little playground, then keep right on ahead with the attitude. On the other hand, if you want Linux to become more broadly accepted among "the average user" (read: non-techie), then maybe you could re-think such responses.

And btw, likewise, such non-helpful answers as:
[quote=hyper_ch said:**
> I'd start with the man pages.
also show both lack of empathy, as well as lack of effort. If you'd taken the time yourself to look at the man page for Gadmin-Samba, then you would know it gives no clue as to its options, and at best only points to a website, where there is also, again, no helpful information.

Likewise, hansdown, I appreciate that you tried to take a tiny step towards helping with your advice of :
 [quote=hansdown]There is a configuration guide pdf.

[http://www.google.ca/search?q=GADMIN...ient=firefox-a]("http://www.google.ca/search?q=GADMIN+TOOLS+manual+for+ubuntu+server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")

Scroll down the list to find it.[/quote]
 but I scrolled down nearly 100 results  with that search, and didn't find a single mention of a pdf configuration guide. So perhaps, next time, rather than simply point towards an endless list of non-helpful results, and telling them to look for a tiny needle among a large haystack of worthless junk, maybe you could take the tiny extra step and post the direct link to the relevant and useful URL.

And if I sound peeved... it's coz I too need these same docs, and I too have spend a fair amount of time searching, only to come up with squat. At best, all I can find is other people asking the for the same information.

Regards,
HighlyDubious

---

### Post by HighlyDubious on 2009-09-05
Btw, I've still not found any docs for Gadmin-Samba, but for those who are (like me), needing to set up Samba, I've found the following search seems to have many different results for HOWTO's on setting up Samba manually. And no doubt, much of what is discussed might be (with some mental acrobatics), applied to the options in Gadmin-Samba. 

I'm just starting this set-up, so I've not yet read any of the links in the following results. But a quick glance looks like almost any of them will be better than the utter lack of docs for Gadmin-Samba. And, I'm posting the search results here, because if someone is like me, and finds this page because they are looking for Gadmin-Samba docs, then maybe these search results could help them too.

[http://www.google.com/custom?...samba+howto&btnG=Search&cx=014345598409501589908%3Amplknj4r1bu]("http://www.google.com/custom?hl=en&safe=off&client=pub-2070091971271392&channel=0262445351&cof=FORID%3A13%3BAH%3Aleft%3BCX%3AStart%2520Search%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BVLC%3A%23551a8b%3BGFNT%3A%23666666%3BDIV%3A%23cccccc%3B&adkw=AELymgWJ3jIlo2GVPd4FPzxRd8N4kjm8y36gN1yj8sCnwkV5pYBbDdZnDdZuz2dVQRHflWQ7-omJ6dYb-KjA7kopM4NCX9n3aw4MyjvG_cJpSmPxC9gd6LU&q=samba+howto&btnG=Search&cx=014345598409501589908%3Amplknj4r1bu")

Regards,
HighlyDubious

---

