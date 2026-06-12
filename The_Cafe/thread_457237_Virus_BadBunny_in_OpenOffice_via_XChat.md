---
title: "Virus BadBunny in OpenOffice via XChat"
date: 2007-05-28
forum: The Cafe
---

### Post by morristhecat on 2007-05-28
Surfing the web early this morning I came across this announcement, BadBunny, a multiplatform virus which infects Windows, Linux and Mac OS, here are the links...

[http://www.securecomputing.net.au/news/badbunny-worm-attacks-openoffice-across-windows-mac-and-linux.aspx](http://www.securecomputing.net.au/news/badbunny-worm-attacks-openoffice-across-windows-mac-and-linux.aspx)

[http://mx.mcafee.com/virusInfo/default.asp?id=description&virus_k=142297](http://mx.mcafee.com/virusInfo/default.asp?id=description&virus_k=142297)

---

### Post by john_spiral on 2007-05-28
It would be great if someone could post the virus here for us to download & test.

Would the site admin's have anything against this?

---

### Post by starcraft.man on 2007-05-28
Far as I know, this is a proof of concept virus that has been made just to show that openoffice can be exploited too (like almost any other software in existence, all have bugs and exploitable code to my knowledge). Many were made for Mac's too. I don't see anyone panicking who owns a mac, nor should they. The reason is simple, none of these have made it to the wild. If their not in the wild, they don't pose a threat. That's pretty much the end of the story. I'm not downloading KlamAV or any other program. No one ever said linux/OO was bulletproof. Not to mention, even if they were wild, you would have to provide a vector for them to come onto your system, then allow them to run. 

So, don't worry about it. It's not worth the effort of worrying.

---

### Post by john_spiral on 2007-05-28
starcraft.man I don't think I'm worrying yet,

I think it will be a good security/educational exercise to give this virus a go.

Has anyone had a play with this beast?

---

### Post by starcraft.man on 2007-05-28
> **john_spiral said:**
> starcraft.man I don't think I'm worrying yet,

I think it will be a good security/educational exercise to give this virus a go.

Has anyone had a play with this beast?

Right, I wasn't implying you would worry, was kinda trying to stem any panic from less informed users reading this, didn't want them to rush out and dl an AV for no real reason.

I do quite agree, studying the concept virus should be done so we can quickly take steps to cut the vector for code injection off and render it useless. A good time for a VM...

I'll have to look into this a bit more myself, though I don't code for OO.

---

### Post by Polygon on 2007-05-28
and even then, the worst it can do (and even thats pretty bad) is basically delete your entire home folder, which is pretty bad but at least it cant get deeper in the system and wreck havok... unless you give it your root password

---

### Post by saphil on 2007-05-28
> **Polygon said:**
> and even then, the worst it can do (and even thats pretty bad) is basically delete your entire home folder, which is pretty bad but at least it cant get deeper in the system and wreck havok... unless you give it your root password

Maybe it could be written to grab your sudo password.  Then it could do some dangerous stuff.  The A-V industry would be so happy to provide solutions. :-)

---

### Post by Polygon on 2007-05-28
the thing is it CANT get your root password unless you specifically give it to the program, or enter it somewhere where the program can get it. thats why the screen darkens when you are asked to give the root password, so you know its only the foreground window that is the legit one.

---

### Post by morristhecat on 2007-05-28
> **Polygon said:**
> and even then, the worst it can do (and even thats pretty bad) is basically delete your entire home folder, which is pretty bad but at least it cant get deeper in the system and wreck havok... unless you give it your root password

Definitely that is something nobody would like, one can not be backing up the entire system and personal files every half hour (you never know when bad things are going to happen). From my personal point of view, the system is what matters to me the least, I wouldn't have any inconvenience to put my Live CD back in and reinstall... but my home folder, my personal files???

In any case, the point is we don't want to be part of that Windows game we used to play, that's why I moved to Ubuntu, security is what matters to me the most. It doesn't matter if a virus is categorized as LOW RISK, we simply don't want them around.

Regards....

---

### Post by BarfBag on 2007-05-28
I wouldn't worry.  As others have said, it isn't out and about.  Also, because of the whole concept of root; I don't think it could do a lot of damage anyway.  You'd have to purposely install it as well.

Windows is definitely not bullet-proof, and neither is Linux or BSD.  However, if you stay away from porn and P2P, use something other then IE, and scan for viruses and spyware regularly (in Linux, it would be rootkits); they can be pretty safe.  It all depends on the user.

---

### Post by Andrewie on 2007-05-28
does SELinux and AppArmor stop this?

---

### Post by Mairi on 2007-06-11
Latest on the critter.

[http://www.zdnetasia.com/news/security/0,39044215,62020320,00.htm](http://www.zdnetasia.com/news/security/0,39044215,62020320,00.htm)

Just don't open any badbunny attachments, I imagine.

---

### Post by kamaboko on 2007-06-11
But..but...but...THAT'S IMPOSSIBLE!  Everyone knows Linux is impenetrable. It can NEVER EVER be compromised.  Not in a bazillion, gazillion years.

---

### Post by bobbocanfly on 2007-06-11
> **kamaboko said:**
> But..but...but...THAT'S IMPOSSIBLE!  Everyone knows Linux is impenetrable. It can NEVER EVER be compromised.  Not in a bazillion, gazillion years.

If only......

Surely though, anyone with common sense isnt going to open an attatchment from a random email address, especially is it is called **Bad**Bunny. That is just asking for trouble!

---

### Post by saphil on 2007-06-11
Never underestimate the sleep-deprived, overcaffeinated and bored work-force.  hee hee hee

This is still not news.  I would like to see a copy of it.  None of my servers are picking it up.  I say the article is FUD as a "proof-of-concept" is not a live virus.

---

### Post by FuturePilot on 2007-06-11
I don't think there's anything to worry about. It was a **proof of concept** virus.

---

### Post by starcraft.man on 2007-06-11
> **kamaboko said:**
> But..but...but...THAT'S IMPOSSIBLE!  Everyone knows Linux is impenetrable. It can NEVER EVER be compromised.  Not in a bazillion, gazillion years.

Fact one: Nothing is impenetrable, there isn't any software that is 100% immune. Human's do the coding, human's aren't perfect, thus the coding isn't perfect.

Fact two: This is an OpenOffice exploit, **not** a Linux exploit, don't confuse the two. You actually have to open the file in OpenOffice to get infected, no OpenOffice no exploit (not all Distros/people use OO).

Honestly, people are making far too much of a deal out of this. The amount of active effort a person has to go to to open the file that they receive from an unknown source makes it so ridiculous that anyone would get infected, if a user just randomly opens files they are the problem that leads to the infection. Only open things you are expecting from friends.

Please stop trolling around and bashing Linux on our forums, you don't have to be here if you find Ubuntu/Linux so bad.

---

### Post by timcredible on 2007-06-11
so, the virus needs to be opened by openoffice, then, on linux, it creates a python script file and a perl script file.  the article specifically says that the virus runs another program on a windows machine, but the article didn't say the virus would run the newly created files on linux, looks like you'd then have to run those files manually before damage would be done.  if someone finds out otherwise, please post the info.

btw, this isn't a 'linux' virus, it's an openoffice virus.  there's been firefox viruses also.  i'm not saying there aren't linux viruses, but the point is that on windows, a virus can easily make your pc a bot for sending spam or ddos attacks, and there hasn't been anything like that on linux yet (hopefully there won't be).

---

### Post by kamaboko on 2007-06-11
> **starcraft.man said:**
> Fact one: Nothing is impenetrable, there isn't any software that is 100% immune. Human's do the coding, human's aren't perfect, thus the coding isn't perfect.

Fact two: This is an OpenOffice exploit, **not** a Linux exploit, don't confuse the two. You actually have to open the file in OpenOffice to get infected, no OpenOffice no exploit (not all Distros/people use OO).

Honestly, people are making far too much of a deal out of this. The amount of active effort a person has to go to to open the file that they receive from an unknown source makes it so ridiculous that anyone would get infected, if a user just randomly opens files they are the problem that leads to the infection. Only open things you are expecting from friends.

Please stop trolling around and bashing Linux on our forums, you don't have to be here if you find Ubuntu/Linux so bad.

Oh...so it's like a MS exploit whereby someone would have to be really stupid to open a file of unknown origin in the first place.  Got it.

---

### Post by michaelzap on 2007-06-11
Actually, I think perhaps people are being too dismissive of this. It's not very dangerous and there seem to be very few incidences of it in the wild, but it could serve as a model for similar multi-platform viruses in the future. I don't think that we should assume things like "you'd have to run the scripts manually" or minimize the damage that would be done if it "only" deleted your entire home directory (and what about shares on other machines?).

[http://www.zdnetasia.com/news/security/0,39044215,62020320,00.htm](http://www.zdnetasia.com/news/security/0,39044215,62020320,00.htm)
[http://www.symantec.com/security_response/writeup.jsp?docid=2007-052303-2513-99&tabid=1](http://www.symantec.com/security_response/writeup.jsp?docid=2007-052303-2513-99&tabid=1)

All software can have bugs and be exploited, and the more we use software like Firefox and OpenOffice that runs on multiple platforms the more we might get bit by something nasty.

---

### Post by juxtaposed on 2007-06-11
> **Polygon said:**
> and even then, the worst it can do (and even thats pretty bad) is basically delete your entire home folder, which is pretty bad but at least it cant get deeper in the system and wreck havok... unless you give it your root password

Is it just me, or is loosing my personal files worse then loosing my OS?

---

### Post by jrusso2 on 2007-06-11
If your opening attachments or files from unknown sources nothing can help you.  You can't fix stupid

---

### Post by michaelzap on 2007-06-11
> **jrusso2 said:**
> If your opening attachments or files from unknown sources nothing can help you.  You can't fix stupid

And why exactly would this virus have to come from an unknown source?

---

### Post by starcraft.man on 2007-06-11
> **kamaboko said:**
> Oh...so it's like a MS exploit whereby someone would have to be really stupid to open a file of unknown origin in the first place.  Got it.

Where in my post did I say it was an MS exploit? If you can point to that, I will give you a cookie. If not, don't insult me by putting unfounded words in my mouth. It is a cross platform virus that targets OO as a vector of infection for messing with the rest of your system.

You kinda answer your own question in the latter part of your comment. If a person opens files from attachments or chat rooms that have an unknown source/author (person or site they don't know or trust) they aren't being very smart (smart in the sense of savvy). That is an unsafe practice and that person should enlighten themselves and become less trusting of the world, there are thousands/millions of people out there who want to infect your machine and you have to be the screen that filters things. If you aren't expecting a file in an attachment or IM transfer you shouldn't accept/open it _EVER._ Thats being smart/safe with your behaviour.

Please refrain from posting such in future, it doesn't do anything except waste space on these forums.

---

### Post by michaelzap on 2007-06-11
The way I read kamaboko's post s/he's saying that it's like an m$ exploit - not saying that you said that. And that seems like a reasonable point to make to me. Just saying that people need to do something careless in order to become infected doesn't mean that it's not a potential problem (I do ten careless things before breakfast).

---

### Post by Wight_Rhino on 2007-06-11
Speaking as a fairly long-time (Warty) Ubuntu user, and definetely not a Troll, I have to say with all honesty that I am seeing many posts here that are regularly used in MS' Defense (The "You'd have to be an idiot to open that" - defense) and not a little over-defensiveness.  

Linux users in general have often chided them for that attitude, it seems a little disingenuous to be using it now. I don't know if there's anything to "Badbunny" or not, but some people's hasty leap to the defensive position is more damaging imo.

---

