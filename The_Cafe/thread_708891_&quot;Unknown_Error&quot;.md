---
title: "&quot;Unknown Error&quot;"
date: 2008-02-26
forum: The Cafe
---

### Post by Vadi on 2008-02-26
Many of us have ran into one before. You want to do something, try, but you get an "unknown error", each time. You have no idea what's wrong, and Google is so not helping you today. That, or maybe because "unknown error" can stand for many things. In the end, you are, frustrated.

Well, this happened to me today. I try and add a buddy on Pidgin, and I get "Buddy <blah> couldn't be added because an unknown error has occured.". Each time. Well, great - but what in the world am I supposed to do now?

So I hop onto the IRC. The magic place that can either cool you down & give a solution, or, at worse, make you think - what's worse, developers arguing against fixing a issue, claiming it's correct, or the issue just getting added onto a huge pile bugs...

> Conversation with #pidgin on Tue 26 Feb 2008 09:48:03 PM EST:
(09:48:03 PM) The topic for #pidgin is: MSN's servers are busted for some people || 2.3.1 is out, be sure you are using it (NOT MTN) and have read [http://d.pidgin.im/wiki/FAQ](http://d.pidgin.im/wiki/FAQ) before you seek support || This is a PG channel || Pastebin: pidgin.im/nopaste/ || Pidgin does NOT support voice or video || FSUES is discouraged. || Your problem is probably your musictracker plugin.  Seriously
(09:48:05 PM) nosnilmot: please make sure any check is for gtk > 2.10.14 :)
(09:49:14 PM) Vadi: I'm trying to add a friend in AIM, but it says "could not be added for an unknown reason." everytime. Does anyone have any more specific ideas...?
(09:49:42 PM) seanegan: Vadi: The most common reason is that you have too many buddies on your list.
(09:50:03 PM) Vadi: Ehm.. too many?>
(09:50:14 PM) Vadi: I did delete my msn account and move everyone over to aim today, yeah...
(09:51:00 PM) seanegan: you're currently allowed 1000 buddies
(09:51:06 PM) Vadi: Oh. I had the contact name before, that's why
(09:51:14 PM) Vadi: (they added me and it asked to merge)
(09:51:21 PM) Vadi: Nope, don't have that many, heh.
(09:51:44 PM) Vadi: I do wish Pidgin was more informative in errors though :(
(09:52:59 PM) nosnilmot: you tried to add the same contact again (to the same group?) and it reported an unknown error?
(09:53:58 PM) seanegan: Vadi: It told you it didn't know what the error was: how can it be more informative if it doesn't know what's wrong? ;)
(09:54:36 PM) nosnilmot: seanegan: heuristics!
(09:56:21 PM) Vadi: nosnilmot: I can't replicate the problem anymore, but maybe that's because the contact is on now. I did run into this "unknown error" on several occasions today though (but I never had it before), so something might be up with the servers. In any case, it should place the blame on the server (or whatever), not look silly and report an "unknown error" ;)
(09:57:42 PM) nosnilmot: heh, I wouldn't support that though, unless we can actually pin the blame on the server
(09:58:16 PM) Vadi: nosnilmot: well, I'm certainly not a happy user when I can't diagnose the problem or know what to do at all.
(09:58:52 PM) nosnilmot: and you'd be happier if we said "it's AOL's fault" than when we say "we don't know quite what went wrong" ?
(10:01:31 PM) nosnilmot: maybe it should say, in addition, "if you're able to reproduce this error, and willing to help diagnose the cause, please join us on irc in #pidgin on freenode.net", but you already did that without prompting :)
(10:02:47 PM) Vadi: nosnilmot: You don't say you don't know what went wrong. It's just "unknown error". If it even said "An error has occurred, but we don't quite know what went wrong." that would be better. But I'm not sure how can you tell what went wrong to begin with, if you know an error happened. If it's something that's outside Pidgin that just said "unknown error", then, say that told it. Or you try and diagnose to give the user a clue.
(10:02:47 PM) Vadi:  
(10:02:47 PM) Vadi: And I only joined here because I tried adding a contact a bunch of times and each time it said "unknown error", at which point I was really unhappy. It's worse than Google's "Error code dfsdf807AES has occured." messages.
(10:02:55 PM) seanegan: Maybe it should say, "We couldn't add this buddy and we don't know why because we're all giant morons. If we were smarter, we'd surely know the cause, but as it is, it's a mystery to us. If you know why this error occurred, good for you. You're surely smarter than us."
(10:03:41 PM) Vadi: seanegan: Well, what about the 1000 buddies limit? Is it an AIM limit, or Pidgin?
(10:03:52 PM) seanegan: AIM
(10:03:57 PM) nosnilmot: Vadi: you really think "we don't quite know what went wrong" is better than "unknown error" ?
(10:04:01 PM) elb: doesn't an unknown error pretty much mean we don't know what went wrong?
(10:04:21 PM) seanegan: elb: I think "unknown error" makes it sound like we didn't even try.
(10:04:23 PM) ***elb leaves this in nosnilmot's hands
(10:04:25 PM) Vadi: seanegan: Great, then say, 'AIM has given an unkown error.'
(10:04:45 PM) elb: seanegan: well, if the shoe fits ... ;-)
(10:04:46 PM) seanegan: You know, if "we don't quite know what went wrong," you know we at least looked into it
(10:04:46 PM) Vadi: Because as it stands, I was thinking that Pidgin was being stupid. 
(10:04:47 PM) nosnilmot: Vadi: but it didn't give an error, we don't know what went wrong
(10:05:11 PM) Vadi: nosnilmot: AIM didn't do what it was supposed to do. Say that at least in a pleasing form.
(10:05:18 PM) elb: we don't know that
(10:05:22 PM) elb: we might have tried to do something unreasonable
(10:05:26 PM) nosnilmot: Vadi: how do you know that?
(10:05:29 PM) seanegan: That's actually more likely.
(10:05:30 PM) seanegan: by far
(10:05:58 PM) elb: we should just pop up a dialog that says "Worked: no"
(10:06:04 PM) nosnilmot: yeah, pidgin is often stupid, because we have no way of knowing what is the right thing to do in many cases
(10:06:18 PM) nosnilmot: elb: hell yeah!
(10:07:10 PM) seanegan: We should just make a big array of silly error messages and pick one at random.
(10:07:17 PM) seanegan: Printer on fire.
(10:07:18 PM) sadrul: doesn't something give a 'Failure: success' message on error?
(10:07:30 PM) elb: I've gotten the printer on fire message
(10:07:35 PM) elb: sadrul: yeah, Windows :-P
(10:07:48 PM) sadrul: hah!
(10:07:50 PM) elb: there's some stuff Windows doesn't set errno for that we used to check via errno
(10:07:52 PM) elb: or something
(10:08:15 PM) seanegan: that's what you get if you call strerror(0), then?
(10:08:22 PM) elb: yeah
(10:08:48 PM) elb: or g_strerror
(10:08:48 PM) nosnilmot: evolution is doing an astoundingly good job at competing with outlook, I frequently get "Error: success" from it
(10:08:49 PM) elb: or something
(10:09:27 PM) seanegan: How about "couldn't delete file: not enough disk space"? ;)
(10:09:35 PM) Vadi: Well, have fun guys. I appreciate the work you did, but hope Pidgin doesn't end up in thedailywtf.com's "Error'd" section.
(10:09:36 PM) elb: Worked: no
(10:09:47 PM) seanegan: Vadi: Been there. Done that
(10:09:56 PM) Vadi: Pity.

It goes to say that, well, a good developer would be able to understand the user. A good teacher must understand the student, and so on. But this little IRC chat just re-confirmed Pidgin developers goals - they're making a client for their personal use. They said that themselves, they go by it, and back it up with their actions.

Sad, eh? But what can you do... well, nothing. Or not a lot, thinking realistically.

---

### Post by 23meg on 2008-02-26
[QUOTE=Vadi]But what can you do... well, nothing. Or not a lot, thinking realistically.[/QUOTE]

You can try to locate the source of the problem and submit a patch, so that it at least actually reports the correct error. Or better, you can fix it. 

Or you can prepare a patch that replaces all the "Unknown error" strings with a human-readable "Something went wrong but we're not sure what" kind of message, open a bug, submit it, and see if it gets merged.

---

### Post by Vadi on 2008-02-26
> **23meg said:**
> You can try to locate the source of the problem and submit a patch, so that it at least actually reports the correct error. Or better, you can fix it. 

**No, that's what I meant by realistically. It would take me weeks to even understand how Pidgin works, which I don't have time for.**

Or you can prepare a patch that replaces all the "Unknown error" strings with a human-readable "Something went wrong but we're not sure what" kind of message, open a bug, submit it, and see if it gets merged.

**I did propose that. Did you read the responses?**


.

---

### Post by 23meg on 2008-02-26
> **Vadi]No, that's what I meant by realistically. It would take me weeks to even understand how Pidgin works, which I don't have time for.[/QUOTE]

I wasn't considering you in person said:**
> I did propose that. Did you read the responses?

Yes. You *proposed* the change in a conversation. What I mean is actually *implementing* the change and submitting a patch. It can be met by a different set of people and evoke a different kind of discourse. Also, since the work is already done and all that's left is applying it, just going ahead and applying it can be seen as an attractive option.

Diving into an IRC channel and proposing a change is somewhat less formal than opening a bug and optionally submitting a patch. You're met by an arbitrary set of people who happen to be in the room at the time, who may or may not represent the project's official stance on the issue. A bug report or mailing list post, on the other hand, slows the process down, formalizes it, and can lead to a different outcome.

---

### Post by Vadi on 2008-02-27
Everything can be done in theory... in theory, Linux could be the best OS too (bitter).

I'll give it a try with a bug report, but I really hope I don't make a fool of myself. Because the attitude expressed on the IRC channel -does- reflect the attitude expressed of some of the developers of Pidgin.

---

### Post by 23meg on 2008-02-27
Good luck.

---

### Post by Vadi on 2008-02-27
Okay, lets hope I worded it right:

[http://developer.pidgin.im/ticket/4931#preview](http://developer.pidgin.im/ticket/4931#preview)

---

### Post by 23meg on 2008-02-27
No patch?

---

### Post by Vadi on 2008-02-27
I... don't even know what file to patch? And, well, don't know what how the error circumstances are checked also.

(not everybody is a professional-grade coder. This is what I meant by "realistically" for me)

---

### Post by 23meg on 2008-02-27
You don't need to be a coder at all, let alone a professional-grade coder, in order to produce a patch that replaces one string with another. 

You can find what file you need to patch by downloading the source, and doing a search in all the files for the string you want to replace (here's one way: choose the source folder in Places / Search for Files / Look in folder & enter "Unknown error" in Select more options / Contains the text).

---

### Post by Vadi on 2008-02-27
Right. But I don't know why can an unknown error happen, so I don't know what to recommend to the user to do (and as you saw in the log, people there weren't really telling me).

---

### Post by p_quarles on 2008-02-27
> **Vadi said:**
> Right. But I don't know why can an unknown error happen, so I don't know what to recommend to the user to do (and as you saw in the log, people there weren't really telling me).
What seems evident from that log is that the developers don't know what causes unknown errors either. I see you asking for two separate things:
1) A better error-checking mechanism. Based on your description of your skill set, this probably isn't something you can help with.

2) An error message that is more descriptive than "unknown error." This is something which you certainly can do, as it only requires you to write a new message.

---

### Post by Vadi on 2008-02-27
No, I don't even know a more descriptive error message. The only ones I learnt of are the 1000 buddies limit (but... that's easily checkable within Pidgin, no?), and, well nothing else specific.

While I certainly can submit phasing the error better, that would be effectively useless as a) it would not provide more information, and b) make someone think the issue was solved, when it really wasn't.

---

### Post by 23meg on 2008-02-27
> **Vadi]No, I don't even know a more descriptive error message.[/QUOTE]

You do said:**
> (10:02:47 PM) Vadi: nosnilmot: You don't say you don't know what went wrong. It's just "unknown error". If it even said "An error has occurred, but we don't quite know what went wrong." that would be better.

[QUOTE=Vadi]While I certainly can submit phasing the error better, that would be effectively useless as a) it would not provide more information, and b) make someone think the issue was solved, when it really wasn't.[/QUOTE]

But you've argued in the quote above that even a better non-specific error can be better than the current situation. Actually, having read the whole conversation, I don't think there's anything else that can be done, short of locating the problem and/or fixing it.

---

### Post by p_quarles on 2008-02-27
> **Vadi said:**
> No, I don't even know a more descriptive error message. The only ones I learnt of are the 1000 buddies limit (but... that's easily checkable within Pidgin, no?), and, well nothing else specific.

While I certainly can submit phasing the error better, that would be effectively useless as a) it would not provide more information, and b) make someone think the issue was solved, when it really wasn't.
Then is the issue about the error message itself, or the fact that Pidgin isn't able to identify the type of error? 

The developers you talked to said that they don't know what the error is either. A computer program would have to be incredibly large and complex if it were to have the ability to identify any possible error. This is just the nature of software. 

If this particular error is frequently encountered, I imagine the developers would want to fix it. I think the reception you got on IRC, however, is due to the way you presented the problem. No programmer is going to want to get rid of an "unknown error" message, since it is certainly better than no message at all, and based on the responses in the log, this is what the developers thought you were asking of them.

---

### Post by Vadi on 2008-02-28
That's nice, but no user is happy with an "unknown error". Even google gives you a randomly-generated error code...

---

### Post by p_quarles on 2008-02-28
> **Vadi said:**
> That's nice, but no user is happy with an "unknown error". Even google gives you a randomly-generated error code...
I have to admit I've never encountered any such random error messages on Google. 

I have to say that I agree 100% with the developers on this part. Making up errors is completely counterproductive, and actually harms the usability of a project.

---

### Post by Vadi on 2008-02-28
blogger.com, owned by google, generates them. At least to me, "dsa87r1" does seem random.

And no, obviously I was not suggesting a random error to be displayed. Argh. An error that says "An unknown error has occured.", is repeating, not allowing me to do what I want, and not telling me how to fix it does harm the usability of a project. Hence, my gripe.


But whatever, Pidgin is not for me, it's for them. And they surely know what an unknown error is when one happens, so it's fine.

---

### Post by popch on 2008-02-28
I would like to point out a few things:

In the conversation included in your first post you stated that pidgin reported 'could not be added for an unknown reason'. Only later in that conversation someone changed the wording to 'pidgin reported an unknown error'. That's not quite the same.

'could not be done for an unknown reason' should be produced either 
[LIST]
[*]when part of the application is executed which will be called only when another branch of the same software failed to properly terminate
[*]or when after completion of some process the result of that process is not present.[/LIST]while 'reported an unknown error' would be adequate for
[LIST]
[*]an exception within the application occurred which is not identifiable or not anticipated
[*]another software system returned a return code which was either not anticipated, not documented or had no message text in the resource file.[/LIST]Though, both of these cases for 'unknown error' could have been reported using a somewhat more telling message text.

Also, I do not see what the developers at pidgin's should do once you told them that the problem did not occur again, and that you have achieved what you wanted to do. 

I agree, though, that the developers could have tried to find out which part of the program produced that message under which circumstance. However, that's neither here nor there since you can't reproduce the error.

---

### Post by aaaantoine on 2008-02-28
I'm assuming that the software actually catches a specific exception, and is not just a black box returning an error state of TRUE/FALSE.

On that assumption, how about this?

> An unknown error has occurred.  Please submit this error code to the Pidgin development team along with what you were doing in the moments before you received this error.

Error Code: 0B3F
Source: AIM server

---

### Post by 23meg on 2008-02-28
[QUOTE=Vadi]But whatever, Pidgin is not for me, it's for them.[/QUOTE]

You've made this case at the beginning, and looking at the evidence and arguments you've provided, I remain unconvinced that the Pidgin people are taking a kind of "This is our software and we don't care what you say about it" kind of attitude. What a couple of people on IRC have told you, albeit not very courteously, is essentially that if the cause of the error is unknown, there's no magical way to make it known. 

 [QUOTE=Vadi]And they surely know what an unknown error is when one happens, so it's fine.[/QUOTE]

They don't. Nobody can reproduce every possible exception a piece of software as complicated as Pidgin can raise on their own, simply because they won't have access to every possible permutation of all the components involved, such as protocols, hardware, OS, you name it. Free software gets better with people who use it in different ways filing bugs and taking care of them. If you turn your back at the first sign of disagreement and don't care what happens afterwards, you're not being a good FOSS citizen.

---

### Post by Vadi on 2008-02-28
[http://www.pcworld.idg.com.au/index.php/id;1641709366;pp;1;fp;2;fpid;4](http://www.pcworld.idg.com.au/index.php/id;1641709366;pp;1;fp;2;fpid;4) :

> (For instance) Tons of people want support for voice and video over IM. Almost none of those people are willing to invest any time or any effort into seeing it happen. Until some are, we will likely keep pushing it to the back burner.

I don't have the time to learn all the information needed, so instead, I donated [money for a bounty]("http://www.cofundos.org/project.php?id=89").

[http://www.schierer.org/~luke/log/20071010-1125/i-appear-in-print#comment-2403](http://www.schierer.org/~luke/log/20071010-1125/i-appear-in-print#comment-2403) :

> Why should &#8220;coding types&#8221; work on it? Why should I spend my free time working on something I have no use for [voice & video]? What motivation is there? These are honest questions.

Nothing wrong with that, it's just a point of view.

Also, check out this ticket - [http://developer.pidgin.im/ticket/34](http://developer.pidgin.im/ticket/34). It was opened over a year ago, and has a lengthy discussion. There, you really do realize that Pidgin is not for you, it's for them. It's an open-source project, but unless you're a coder, please go away, you're wasting our time:

> Users, please do not comment on this ticket further unless you have something to contribute to the actual development of this feature. "Me too"s and other comments not directly helping the development of voice and video features are only going to pollute this ticket unnecessarily and take time away from those caring to contribute.


And no, I do not feel like fighting anyone over -their- program on how it should work. I was merely doing what any developer who wants to have a successful project have - user feedback. The people for whom the project is for. Pidgin is not that, hence, user feedback is not needed (confirmed by IRC).

Not convinced? Here's what #pidgin's topic states: "FSUES is discouraged.". Their wiki defines it as "Free Software User Entitlement Syndrome". More than self-explanatory.

---

### Post by popch on 2008-02-28
@vadi:

While the story about the developers not wanting to hear from users may or may not be true, it has little relevance to the particular problem with pidgin you encountered.

Again: you reported an error message saying either 'could not be added for an unknown reason' or 'an unknown error has occured.' You then added that the situation which might have been used to reproduce the error did not exist any more, and that your problem in essence was solved.

That's just not enough information to go on with, and the chances of even reproducing the error might be very slim, let alone of finding the cause. 

Also, since you apparently did not verbatim report the actual wording of the error message you received, you imposed the burden of searching the program code for the most likely message on the developers.

Were I one of the developers, I would assign a very low priority to this problem because you were able to work your way around it, and because the chances of finding and fixing it were so slim. Investing time into that problem would just have taken time away from things which hinder more people and which have a greater probability of being fixable.

This is not to say that it is your fault that they can not make a reasonably accurate diagnosis from your report. Accurately reporting software is a skill which has to be learned, too.

But then, this does not give you any rights concerning that software. It is their software and their time.

---

### Post by 23meg on 2008-02-28
> **Vadi]Also, check out this ticket - [http://developer.pidgin.im/ticket/34](http://developer.pidgin.im/ticket/34). It was opened over a year ago, and has a lengthy discussion. There, you really do realize that Pidgin is not for you, it's for them. It's an open-source project, but unless you're a coder, please go away, you're wasting our time:
[/QUOTE]

That's not the point of that text at all. It doesn't mean to say "We don't want user feedback" said:**
> And no, I do not feel like fighting anyone over -their- program on how it should work. I was merely doing what any developer who wants to have a successful project have - user feedback. The people for whom the project is for. Pidgin is not that, hence, user feedback is not needed (confirmed by IRC).

As I said, it's not confirmed by the IRC dialog, and neither by that ticket. You don't seem to be very well informed on the purpose and scope of bug trackers in general, so naturally you're misinterpreting things.

---

### Post by Vadi on 2008-02-28
... exactly.

I only solved the issue by telling the person "My messenger is acting up, could you please add me instead?". Of course, I wouldn't be recommending Pidgin to them anytime soon now. Nor did I feel like removing them, attempting to replicate the problem, and asking them it to add again.

I posted the story because you said "I remain unconvinced that the Pidgin people are taking a kind of "This is our software and we don't care what you say about it" kind of attitude.". Now, you say "it has little relevance to the particular problem with pidgin you encountered.", Okay, jumping back and forth, but I'm not sure what are we talking about now.

@meg23: Why is it not confirmed by the IRC, and the comment? Where else can it be confirmed? Of course not in the bug tracker, it's not for that, as you say.

At any rate, I'm just waiting on to see what happens with the ticket. At worse, it'll be lost in the bug tracker.

---

### Post by 23meg on 2008-02-28
[QUOTE=Vadi]
I posted the story because you said "I remain unconvinced that the Pidgin people are taking a kind of "This is our software and we don't care what you say about it" kind of attitude.". Now, you say "it has little relevance to the particular problem with pidgin you encountered.", Okay, jumping back and forth, but I'm not sure what are we talking about now.[/QUOTE]

Different people said those two things. 

[QUOTE=Vadi]@meg23: Why is it not confirmed by the IRC? Where else can it be confirmed? Of course not in the bug tracker, it's not for that, as you say.[/QUOTE]

What I meant was that the dialog you presented as proof of your assertion that the Pidgin people are developing Pidgin just for themselves and don't want any user feedback doesn't confirm that assertion.

---

### Post by 23meg on 2008-02-28
[QUOTE=Vadi]At any rate, I'm just waiting on to see what happens with the ticket.[/QUOTE]

Are you going to submit a patch? That will make a resolution of the kind you want more likely.

---

### Post by Vadi on 2008-02-28
Yes, I will submit a completely useless patch, with only better wording - because I do not know the common reasons for the errors.

But I will hope that -at least- that goes through! Or maybe the "printer on fire" will get before mine.

---

### Post by Vadi on 2008-02-28
> **23meg said:**
> Different people said those two things. 

My apologies, you're right. I got mistaken. Sorry popch!

---

### Post by p_quarles on 2008-02-28
> **Vadi said:**
> Or maybe the "printer on fire" will get before mine.
That would make a darn good easter egg, in my not-so-humble opinion. 
:lolflag:

---

### Post by 23meg on 2008-02-28
[QUOTE=Vadi]Yes, I will submit a completely useless patch, with only better wording -[/QUOTE]

As I said before, you argued yourself in that conversation that it wouldn't be completely useless. I'll quote again:

> (10:02:47 PM) Vadi: nosnilmot: You don't say you don't know what went wrong. It's just "unknown error". If it even said "An error has occurred, but we don't quite know what went wrong." that would be better.

[QUOTE=Vadi]because I do not know the common reasons for the errors.[/QUOTE]

And nor does anyone else. The only reason it's expected that you're the most likely one to know or be able to help pinpoint the reason is that the problem occured on *your* computer.

---

### Post by Vadi on 2008-02-28
Er, I was being serious:

> (10:07:10 PM) seanegan: We should just make a big array of silly error messages and pick one at random.
(10:07:17 PM) seanegan: Printer on fire.

;)

@meg23: It is useless to me now. It was useful when I didn't think of the project to be so apathetic and 'elite', and really, I wanted to help. Now, I don't care about it, because their attitude turned me off. I'm not paid to do this either.

---

### Post by 23meg on 2008-02-28
Your opinion of the project is based on a very small sample set, and it seems there's a lot of misinterpretation involved on both sides, but it's still your opinion, to which you're entitled. The good part is that you still filed a bug and will submit a patch regardless of it.

---

### Post by Vadi on 2008-03-06
I changed my mind.

'seanegan' and 'nosnilmot' are listed as one of the top developers of Pidgin. This comment ([click]("http://developer.pidgin.im/ticket/34#comment:57")) shows that Pidgin is not for us, but them (ie, it's not useful to us, so we won't do it). They even branded "FSUES", which stands for "Free Software User Entitlement Syndrome", and their IRC topic states "FSUES is discouraged.". 

Get the idea? You aren't entitled to the software.

As such, I don't feel like helping them improve it. I'm not entitled to it anyway.

---

