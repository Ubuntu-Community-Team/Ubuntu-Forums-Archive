---
title: "Building an AI for Linux and I need help!"
date: 2009-03-24
forum: The Cafe
---

### Post by AICollector on 2009-03-24
Alright, heres my problem; I'm trying to connect Linux to my AI for a desktop client. We want to fully integrate her into the system.

But we have a few problems, big problems.

1. No 'one' system.

There are multiple desktop environments, multiple file managers, multiple file search bots, multiple multimedia systems, etc...we can put 10x the work into the Linux version and expect to get the minority market share.

2. Security

This AI would have access to the CLI and as a consequence be attached to system sensitive files. She's too big for anything but our server to handle, so she needs a web connection to her brain. That worries me as well and I'm not sure how we can work around that. Theoricatlly a virus could get down her connection and find itself in a system with full root permissions. We'd also need to find a way to stop the system from asking for the password.

3. Ethics

Our AI is closed source, not because we want to make money from her, but because we feel the technology can be easily corrupted for malicious purposes. This means we're more or less looking at either being ignored or shunned by those who would help us.


Listen, I adore Linux and I don't want Linux users to miss out. I'm just not sure how I can work with all this.

---

### Post by finer recliner on 2009-03-24
I think we're going to need more detailed questions so we can tackle one problem at a time. When I think of AI (artificial intelligence), i think of a bot I can chat with, and it would respond like a normal human being. so why does your AI system need access to my files, media players and entire desktop environment? please elaborate further for us :)

---

### Post by GepettoBR on 2009-03-24
More information on the nature of this AI would indeed be nice. Depending on its intended purpose it may be possible to do everything with just CLI tools, and so the choice of DE, file manager, etc would become irrelevant. That also means less work for you.

---

### Post by albandy on 2009-03-24
This really kick my balls:

> 3. Ethics

Our AI is closed source, not because we want to make money from her, but because we feel the technology can be easily corrupted for malicious purposes. This means we're more or less looking at either being ignored or shunned by those who would help us.



The most secure operating systems are open source, this grants the security for the user and for the developer.

A closed source program grants nothing. You can't know if it works like it's spected to work.

---

### Post by alex2399 on 2009-03-24
So what exactly are the goals of this AI? Create poetry, make art, understand language, learn or whatever?

And on what theoretical framework are you building it?

---

### Post by AICollector on 2009-03-24
Its an AGI. It learns from conversation, reading Wikipedia (and other sources) we're starting to implement visual and audio data.

It would turn any system into an AIOS of sorts, able to sort, organize and assist the user.


Define theoritical framework. We have the AI, it's just a matter of getting into Linux.


We keep her closed source because an eariler job of mine was taking down malicious bots (ones used for ID theft, or paedophila were common not so long ago) and they were based on ALICE. I'd rather not let our AI system be the next generation of these bots.


Basically, on the Windows one, I tell the system to activate a DOS shell at  c:\windows/system32 and load the window invisible, for our AI to work through it.

How can this be done here? (keep in mind we're transferring her from .NET to Mono)

---

### Post by GepettoBR on 2009-03-24
> **AICollector said:**
> We keep her closed source because an eariler job of mine was taking down malicious bots (ones used for ID theft, or paedophila were common not so long ago) and they were based on ALICE. I'd rather not let our AI system be the next generation of these bots.

I never heard of that. Source?

---

### Post by binbash on 2009-03-24
Ended reading after seeing close source part

---

### Post by AICollector on 2009-03-24
Ok, forget it, then. I'm not going to get any help because of my choice. I'm only willing to release Jeeney as closed-source because of the potentional of this tech. This isnt a word processor or anything like that, she talks and acts autonomously. She's more like family then a program.

This isnt because we want money out of her, it's because we dont want her corrupted. I acknowledge that most of you here arnt going to do that, thats no promise that others wont.


We do not wish her forked or otherwise altered. We have a strict philosophy in her design that we do not want altered. We are between the philsophy of closed source and open-source. Open-source cannot guarantee our philosophy will remain intact. We do not want a billion copies of her (as there is in ALICE).

For her to work, her database requires completely unbiased peices of information. Open-source cannot gaurentee that, either.


So, if theres a way to prevent her code from being taken, but allowing for improvments and suggestions, I'm all for it.

---

### Post by alex2399 on 2009-03-24
Well there is no mutually agreed upon defenition of (human) intelligence, most of the explanations are descriptions that can't predict a lot, and if they do then it is with varying success. An intelligence test can't even predict a lot. It can only give you a description of what your "intelligence" was at the moment you took the test. 
Example. You could let a native Chinese that has never learnt another language take an American Intelligence test, the outcome would probably be a low IQ since he can't understand the test. Though he might be the next Einstein. But what does the test then actually measure? Language skills? Is that a part of intelligence? Would this Chinese be more intelligent if he had learned American also? And what if the learns ten other languages, will his score on the intelligence test also improve? Can you even learn intelligence? Is it innate?

So, with theoretical framework I mean on what grounds is this AI build. How do you verify it is intelligent in any way? There are many models that try to "simulate" some human qualities. For instance PAM (Plausability Analysis Model) tries to find plausability between two sentences. This is just one of the many models that can simulate a tiny aspect of human behaviour/intelligence.
So what exactly are you trying to do and how do you verify it works? Thats what I mean with theoretical framework, since they give the boundaries in what you predict an AI can do and can't do.

Take for example learning in your reply, exactly what is meant with learning? making connections between constructs? Observation? Connection strengths in neural networks? Production rules? Reasoning without any new input? Dreaming? Rational thinking? Reaching goals?the list goes on.

---

### Post by finer recliner on 2009-03-24
> **AICollector said:**
> Ok, forget it, then. I'm not going to get any help because of my choice. I'm only willing to release Jeeney as closed-source because of the potentional of this tech. This isnt a word processor or anything like that, she talks and acts autonomously. She's more like family then a program.

so you get 80+ people who read this thread, and 2 of them complained of the closed source solution, so you're ready to give up on the entire linux port?!

you have to meet us half way. you still havent given us any specific functionality that you're trying to recreate in linux. you havent even said what language your system is in (.NET is not a language). If your windows version uses a batch script to start the process, then you can write a bash script for the linux version (bash is installed on just about every linux distribution). from the bash script you can make other system calls and navigate the file system.

---

### Post by Bölvaður on 2009-03-24
> **AICollector said:**
> Alright, heres my problem; I'm trying to connect Linux to my AI for a desktop client. We want to fully integrate her into the system.

But we have a few problems, big problems.

1. No 'one' system.

There are multiple desktop environments, multiple file managers, multiple file search bots, multiple multimedia systems, etc...we can put 10x the work into the Linux version and expect to get the minority market share.

2. Security

3. Ethics
1. you should open source it to let people add in how thunar, nautilus, dolphin.... is manipulated.
file search is same for all in bash, grep, locate and find are good friends.
Multimedia systems would also be a problem on windy and macos, as most young people that watch films often use vlc, mediaplayer classic (well windy only), itunes, winamp... etc. Opensource that file as well ;)
It could be pretty cool if the AI is opening multiple songs in rythmbox but a single song in mplayer or vlc and films in vlc but multiple smaller files in mplayer.
It really isnt minimal market share, because most windows users will not search for your program. People that are comfortable with the way they do things arent going to use new things without a big push.
Also if you release a good product on Linux or Mac it will be easy for you for your interviews, reviews and blogs about your product to spread.. while on the windy world it is like throwing a needle in a haystack, hide it somewhere on the bottom of the ocean and then wait for hope some one to get stung.

2. You can access bash (that would be the only requirement) from different user levels (ctrl+alt+f1..f7 in gnome), or just execute the command directly, not though a program (what a weird way to go. AI &#8594; gnome-terminal &#8594; bash).
It would be easy to let the AI log into super user and then just log out again directly after that. It would be *sudo su* on ubuntu and opensuse but just *su* on distros like arch. That would be detectable on setup and would use same commands. Or you can add sudo in front of all opensuse and ubuntu based distros... (the sudo package is detectable on search btw).
You can let the user inter his password at initial setup and encrypt it locally, making sure there is no *string getUserPassword(){return userPassword};*

3. the foss community cares, the linux community doesnt ;) You could do a mixture of going the open source way and the close source. So that you allow developers that have high karma on launchpad.
Or _open source some parts of the program_, but not enough for malicious people to bother with doing the rest.
If you keep it close source at first you can always later try to think if it is possible to open source it completely without bad things happening.

---

### Post by estyles on 2009-03-24
Umm...  you're developing a program that needs to run with constant root access and is distributed binary-only with no source?  Don't expect many people to run that...  Without access to the source, where's the assurance that your program isn't malicious or just a huge security risk?  Just your say-so?

I hope you do get the help you're looking for, programming-wise - it sounds like an interesting project, but...

---

### Post by smbm on 2009-03-24
> **estyles said:**
> Umm...  you're developing a program that needs to run with constant root access and is distributed binary-only with no source?  Don't expect many people to run that...  Without access to the source, where's the assurance that your program isn't malicious or just a huge security risk?  Just your say-so?

I hope you do get the help you're looking for, programming-wise - it sounds like an interesting project, but...

A bit like the Nvidia drivers then?

---

### Post by estyles on 2009-03-24
> **smbm said:**
> A bit like the Nvidia drivers then?

Those are released by Nvidia (not that I use Nvidia - I use the open source ati drivers), and are signed and available in the repositories.  I'll take Nvidia and Ubuntu's say-so before some random guy.

---

### Post by AICollector on 2009-03-24
Ok, I over-reacted there. I apologize.


she's in VB.Net

we cant have her processing locally, we have her on a duel-core server with 14gb of RAM, and she's stressing that already.


Would it be possible to take a string from a webservice and relay it to the linux terminal? (dont ask why, I'm relaying the message)

The client and all that would be open-source, but Jeeney herself (who would only control, not reside upon) would remain closed source


As for her abilties; 

Semantic bot. Natural langauge processing ability. Neural networks are used, hence 'learning'. Recognition of emotion is currently being developed. Semi-autonomous sentence generation.

---

