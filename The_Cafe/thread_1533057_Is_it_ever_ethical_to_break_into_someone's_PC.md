---
title: "Is it ever ethical to break into someone's PC?"
date: 2010-07-17
forum: The Cafe
---

### Post by anutjob on 2010-07-17
Here's the scenario:

I pasted an IP address of one of the P2P peers into my browser to see if he has a website because the address it resolved to was a humourous one. He had nothing but an "It works!" page. No contact info or anything. Knowing what client he was using, I checked out if he had the web interface enabled, and he did. This particular client is something I've been using for years and have written numerous mods and enhancements for it so I know a lot about the common mistakes people make that can enable a remote attacker to run any system command. This is exactly one such case.

What do you do? There is no way to contact this person to tell him to secure his box, and it is 100% possible to gain ssh access to his box in under a minute.

Do I:

1. Just forget it and leave his "naked PC" out there on the internet and make it someone elses's problem?
2. Break into his PC and leave a friendly note for him and logout? (I'll admit this is fun)
3. Write about it on my site which'll help people avoid such mistakes (but also let script kiddies exploit it.)

The P2P client in question is secure. It is the user who is at fault here because he decided to ignore the security warning.

Personally, I run a webserver myself and often see numerous attempts from malicious users so I won't be surprised if someone has done something harmful to this person's PC so I'd go with 2 even if it's the wrong the to do but then it's upto this person how he'll take it. Whether he wants to hunt me down or thank me. :)

If you were this person, would you prefer to be ignorant about it or prefer someone told you about it? And if you found one such vulnerable box without a way to contact its owner, what would you do?

---

### Post by KdotJ on 2010-07-17
Interesting, but difficult situation.
It depends on what kind of person they are. Best case, you "break in"and leave them a note,to which they are grateful and secure their box. But this will not always be the case, it might swing the other way and they get angry and question why you was snooping around in the first place. 

Most probably answer, leave it as its not your issue

The answer you're looking for, ssh it lol

---

### Post by bumanie on 2010-07-17
Unfortunately, many people refuse to learn the simplest things re securing their own computer - might sound harsh, but it their fault and it is up to the individual to secure their own computer or invite someone to do it for them. In this case 'breaking in', even if your intentions are altruistic, would likely be seen as a criminal act. The only time I can see it would be ethical, if one is involved in law enforcement or invited by a business owner who believes he/she has a rogue employee misusing work place computers, thus one would be getting paid to forensically investigate a computer by the owner of the computer, ie the boss, who has the right to ensure work infrastructure he/she owns is used appropriately.

---

### Post by markp1989 on 2010-07-17
i vote for  3, that way i would read it and it would help me  to secure my stuff.

---

### Post by Pizack on 2010-07-17
Philosophy Major here.  ssh ing in would be like walking into someone's house and leaving them a note that the door was unlocked.  I'd say if you could reach in and lock his door, then you should, but don't walk in and mess around.  Regardless of ethics, taking control of another person's computer is illegal.

---

### Post by anutjob on 2010-07-17
I guess you're right about there being the possibility of him getting angry but oh well.

Maybe I should write about securing this web application on my site and hope he sees it. I haven't seen it mentioned anywhere else. I guess it's also a nice way to get good traffic to my site.

---

### Post by WorMzy on 2010-07-17
Put goat porn all over his desktop as a friendly hello.

Maybe a little note too, explaining how to prevent someone else doing the same thing.

---

### Post by sisco311 on 2010-07-17
Don't think of it as an ethical issue, but a legal one. In many countries, unauthorized access to another persons computer is prohibited by law.

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
Yeah, if you live in the US that's cyber terrorism.

---

### Post by linux18 on 2010-07-17
I go with option number two, but only if you knew he has some sort of backup....."OMG! i've been hacked must reinstall" 

but option 3 is the best in 99.9999999999999 % of cases

unless you word the message very politely.

---

### Post by yaaarrrgg on 2010-07-17
IMO it's not unethical to warn/help someone in any manner, but how they will interpret your good will is a different matter.  S/He could freak out and blame you for anything anyone else has done to the box.   What's the expression... "no good deed goes unpunished." :)

---

### Post by Penguin Guy on 2010-07-17
That kind of stuff could get you into legal trouble, so be sure to use some kind of anonymity client when leaving the message.

---

### Post by Penguin Guy on 2010-07-17
> **WorMzy said:**
> Put goat porn all over his desktop as a friendly hello.
I've got to admit, that *would* be funny.

> **sisco311 said:**
> Don't think of it as an ethical issue, but a legal one.
I expect the OP is well aware of the law. He is asking specifically about ethics, however.

---

### Post by dschaller on 2010-07-17
> **sisco311 said:**
> In many countries, unauthorized access to another persons computer is prohibited by law.

I am not a lawyer, but I believe this statement is quite true. I have heard other computer security experts speak of the legality of entering systems as "white hat" hackers. It is not legal (in the USA anyway) to do what is suggested in number two of the original post, even if the intent is not malicious.

---

### Post by Malac on 2010-07-17
Number 2 for me.
With an express disclaimer in the note stating that in no way have you damaged the system nor rendered it unusable nor read any personal information nor denied the owner the use of said system. You are merely advising them on a potentially dangerous situation for them and others.

Option 4: contact your local law enforcement internet crime division and report the IP to them as a potentially exploitable computer. They can then legally find out the persons name and advise them to protect their computer.

Option 5: whois the IP and contact the ISP advising them one of their clients is running an exploitable computer.

---

### Post by prodigy_ on 2010-07-17
> **Malac said:**
> Option 5: whois the IP and contact the ISP advising them one of their clients is running an exploitable computer.

Heh, that was funny to read. Have you ever dealt with ISPs? Their abuse and support mailboxes are usually symlinks to /dev/null (or at least so it feels).

---

### Post by Malac on 2010-07-17
> **prodigy_ said:**
> Heh, that was funny to read. Have you ever dealt with ISPs? Their abuse and support mailboxes are usually symlinks to /dev/null (or at least so it feels).
Probably True but I'm trying to explore legal alternatives here . :)

---

### Post by Bachstelze on 2010-07-17
> **anutjob said:**
> 
What do you do? There is no way to contact this person to tell him to secure his box,

postmaster@domain

---

### Post by donkyhotay on 2010-07-17
Option 1, white hat hacking while maybe ethical is often illegal and I know people that have gotten in trouble with it. I had a similar issue awhile back where a friend of mine had a neighbor with not only a completely open WiFi network (no password at all) but had file sharing enabled for *everything* on his computer... Yes, that was the entire "C" drive, including the windows/system folders with full read/write access <shudders>. I just left it alone because I didn't know who would have been running the network (it was in the middle of a large apartment complex) and anything I could have done (like leaving a note ont he desktop) would have possibly gotten me in trouble (as I said I know people that have had problems with that). People are stupid, especially when it comes to computers. Chances are the person who owns the computer you can access doesn't know much about security, has no clue how to secure his stuff properly, *thinks* he knows something about computer security, *thinks* he's doing everything right and if you tried contacting him would probably go "OMGWTF? You've bypassed all of my l33t, high quality, perfectly running, properly configured security. Therefore you are an evil h4x0r installing "viruses" on my computer." Next thing you know you there is a knock on the door from some gentlemen wearing some sort of uniform.

---

### Post by tjwoosta on 2010-07-17
So long as you know how to cover your tracks nicely, so you dont get into trouble in the case that the owner is an ***, I would say get in and leave a friendly and detailed message somewhere that he'll see about exactly how you got in and how to prevent it next time.

---

### Post by forrestcupp on 2010-07-17
> **Pizack said:**
> Philosophy Major here.  ssh ing in would be like walking into someone's house and leaving them a note that the door was unlocked.  I'd say if you could reach in and lock his door, then you should, but don't walk in and mess around.  Regardless of ethics, taking control of another person's computer is illegal.

If you walked by a stranger's house/car and noticed that their door was unlocked, you would reach in and lock it for them?!  I don't think so.  The most I would do is shut a car door for someone after making sure that they aren't around anywhere.  And I probably wouldn't even do that.

Option 3 is the best option assuming you're not going to advertise that specific IP.  Writing anything that could direct "script kiddies" to that person's computer would be as bad as trashing his computer yourself.  Just write a blog or something that gives a general lesson showing people what they need to do in that situation.  Then stay out of that guy's business.

---

### Post by Malac on 2010-07-17
Script kiddies will be scanning for ports and vulnerabilities and will probably find it eventually unless something is done by someone. If not you then who?

Computers like this one provide spammers and other malicious people with a free computer to pollute the internet with spam or far, far worse a proxy through which they can run terrorist/criminal activities.

In that case it is your civil duty to report or notify this person. (only half joking)

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
The best option mentioned has been option #4, inform a law enforcement agency. Due to the fact that he's left his machine to be readily included in a botnet it is a security issue. There are agencies that would care enough about that to track it down.

---

### Post by Nano Geek on 2010-07-17
I know that if it was my computer I wouldn't want you messing around with it. Don't always assume you know better than others. Perhaps he knows about the problem but left it that way for some reason. If it gets hacked, it's his problem, not yours.

You're not responsible for fixing all the problems on the internet. ;)

---

### Post by wmcbrine on 2010-07-17
I'd do two and three, but I'd only do two if I was sure he wouldn't/couldn't trace it back to me and misguidedly retaliate. I've been there (a long time ago -- 1988, dialup BBS; once was enough).

---

### Post by Shining Arcanine on 2010-07-17
> **Pizack said:**
> Philosophy Major here.  ssh ing in would be like walking into someone's house and leaving them a note that the door was unlocked.  I'd say if you could reach in and lock his door, then you should, but don't walk in and mess around.  Regardless of ethics, taking control of another person's computer is illegal.

That is a poor analogy because physical location does not matter with computers. A much better analogy would to say that it is the equivalent of shining a flash light in a person's windows with morse code. If they happen to have a device that reacts to it, then that is not your fault.

---

### Post by earthpigg on 2010-07-17
i strongly vote ***against*** informing law enforcement. [police are not predictable]("http://www.youtube.com/watch?v=7AfKMaDhTjs"), and you never know who has a bong sitting on his kitchen table but is otherwise a respectable law abiding citizen that escorts old ladies across the street on a daily basis.

once you make a phone call and invoke law enforcement, you have no way of controlling what direction [that particular storm]("http://www.youtube.com/watch?v=RbwSwvUaRqc") will take. they may even decide that you have done something wrong - even if you are sure to "win" at trial, the trial itself would still be a large interruption to your life.

i vote for option number three. document it, write about it, hope he sees it or someone he knows sees it.

is there some way to contact him via your p2p client? built in chat feature or something?

(do i need to post more videos of the completely random, uncontrollable, and unpredictable chaos potentially caused by contacting law enforcement? Russian Roulette with Tasers is not a fun game.)

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
Russian Roulette with an automatic is less fun!
I see your point, and the fact that you found this exploit by knowing about it could incriminate you, OP.

---

### Post by tjwoosta on 2010-07-17
> **ST3ALTHPSYCH0 said:**
> Russian Roulette with an automatic is less fun!


No its so much more fun, you just stand in a circle and fire a full clip straight up in the air. Whoever stands their ground wins. :p

---

### Post by Superkoop on 2010-07-17
Legally, you should just blog about it.

Ethically, I say you fix his problem... without getting caught.

---

### Post by Malac on 2010-07-18
Actually one thing not mentioned yet is that it may be a "honey-trap" and belongs to an organisation and it's masquerading as a personal system so as to get hacked just so they *can* trace it back.
That organisation could be an anti-virus, firewall, anti-spam, security company or law enforcement agency anyway. In which case even hacking in to fix the problem may get you caught by the "trap" as it were.

Changed my mind now, I'd blog about it and hope the individual, if that's who it is, sees the blog.

---

### Post by kaldor on 2010-07-18
> **forrestcupp said:**
> If you walked by a stranger's house/car and noticed that their door was unlocked, you would reach in and lock it for them?!  I don't think so.  The most I would do is shut a car door for someone after making sure that they aren't around anywhere.  And I probably wouldn't even do that.

Option 3 is the best option assuming you're not going to advertise that specific IP.  Writing anything that could direct "script kiddies" to that person's computer would be as bad as trashing his computer yourself.  Just write a blog or something that gives a general lesson showing people what they need to do in that situation.  Then stay out of that guy's business.

When I was around 11, I was walking into a walmart with my dad in a huge parking lot. This one car had the headlights left on. My dad being how he always wants to help people, stopped and opened the unlocked door and turned off the lights and locked the door on his way out. 

His intentions were good, but holy crap... it was extremely awkward. I was just waiting for someone to come and accuse us of breaking in.

---

### Post by Stan_1936 on 2010-07-18
I fixed the problem.
The guy suspected that something had changed/improved/been fixed with his Windows XP SP2 installation.
He believed that I "meddled" with his personal property but obviously could not prove it.
He was relieved that the problem was fixed but sounded annoyed that he didn't know who fixed it.
He asked me directly if I knew who fixed the problem and how his system was accessed(his password was in a rather visible location, but that's besides the point).

In phrasing my reply/determining what sort of facial expression to put on, I recalled what George Costanza(a.k.a. Confucius) once said:
"**Just remember, it's not a lie if you believe it.**"

I'm still friends with him.

---

