---
title: "I am SOOO happy I use Ubuntu"
date: 2007-07-16
forum: The Cafe
---

### Post by Talaman72 on 2007-07-16
[SIZE="4"]So I got this bone to pick.  

The other day I was in #ubuntu doing about nothing one moment and getting booted the next.  I Will have to state that at the time I got booted I DID NOTHING.  Here's the problem (as I was informed AFTER getting booted), I had a script running.  When I was informed that this was the reason I got booted I was a bit confused.  I have to acknowledge that I have several scripts running at any given time do several things. It's one of the things that makes IRC more appealing than say Yahoo!

I have a script that boots people from my channels when needed, one that logs messages of specific nature, one that plays and controls my music, one that sets ignore automatically, and one that gives last seen info.  The latter being the script in question.  As you can see from the #ubuntu-ops (where I actually asked about how to get back into #ubuntu): 

[elkbuntu] according to the logs, you had a bot or AI script going.
[elkbuntu] 2007-07-12T11:46:54 <nikin> !seen p99
[elkbuntu] 2007-07-12T11:46:54 <ubotu> Sorry, I don't know anything about seen p99 - try searching on [http://bots.ubuntulinux.nl/factoids.cgi](http://bots.ubuntulinux.nl/factoids.cgi)
elkbuntu: +2007-07-12T11:46:55 <Talaman72> p99 was last seen Thu Jul 12 01:52:56 2007 changing nick from afk|p99 in #ubuntu

Now according to this elkbuntu person ubotu is ok, but my seen reply isn't.  Also note  Talaman72, spam is not just advertising, it is useless noise as well.  Now go figure on which reply is actually useless in this case.

Here's a novel if you're going to make crappy rules, lead by example.  I had also run accros this on my way to the forum:

Code of Conduct

Ubuntu is an African concept of 'humanity towards others'. It is 'the belief in a universal bond of sharing that connects all humanity'. The same ideas are central to the way the Ubuntu community collaborates. Members of the Ubuntu community need to work together effectively, and this code of conduct lays down the "ground rules" for our cooperation.

We chose the name Ubuntu for our distribution because we think it captures perfectly the spirit of the sharing and cooperation that is at the heart of the open source movement. In the Free Software world, we collaborate freely on a volunteer basis to build software for everyone's benefit. We improve on the work of others, which we have been given freely, and then share our improvements on the same basis.

That collaboration depends on good relationships between developers. To this end, we've agreed on the following code of conduct to help define the ways that we think collaboration and cooperation should work.

If you wish to sign the code of conduct, you can sign the Canonical copy online.
Ground rules

This Code of Conduct covers your behaviour as a member of the Ubuntu Community, in any forum, mailing list, wiki, web site, IRC channel, install-fest, public meeting or private correspondence. The Ubuntu Community Council will arbitrate in any dispute over the conduct of a member of the community.

    *

      Be considerate. Your work will be used by other people, and you in turn will depend on the work of others. Any decision you take will affect users and colleagues, and we expect you to take those consequences into account when making decisions. For example, when we are in a feature freeze, please don't upload dramatically new versions of critical system software, as other people will be testing the frozen system and not be expecting big changes.

      Be respectful. The Ubuntu community and its members treat one another with respect. Everyone can make a valuable contribution to Ubuntu. We may not always agree, but disagreement is no excuse for poor behaviour and poor manners. We might all experience some frustration now and then, but we cannot allow that frustration to turn into a personal attack. It's important to remember that a community where people feel uncomfortable or threatened is not a productive one. We expect members of the Ubuntu community to be respectful when dealing with other contributors as well as with people outside the Ubuntu project, and with users of Ubuntu.

      Be collaborative. Ubuntu and Free Software are about collaboration and working together. Collaboration reduces redundancy of work done in the Free Software world, and improves the quality of the software produced. You should aim to collaborate with other Ubuntu maintainers, as well as with the upstream community that is interested in the work you do. Your work should be done transparently and patches from Ubuntu should be given back to the community when they are made, not just when the distribution releases. If you wish to work on new code for existing upstream projects, at least keep those projects informed of your ideas and progress. It may not be possible to get consensus from upstream or even from your colleagues about the correct implementation of an idea, so don't feel obliged to have that agreement before you begin, but at least keep the outside world informed of your work, and publish your work in a way that allows outsiders to test, discuss and contribute to your efforts.

      When you disagree, consult others. Disagreements, both political and technical, happen all the time and the Ubuntu community is no exception. The important goal is not to avoid disagreements or differing views but to resolve them constructively. You should turn to the community and to the community process to seek advice and to resolve disagreements. We have the Technical Board and the Community Council, both of which will help to decide the right course for Ubuntu. There are also several Project Teams and Team Leaders, who may be able to help you figure out which direction will be most acceptable. If you really want to go a different way, then we encourage you to make a derivative distribution or alternative set of packages available using the Ubuntu Package Management framework, so that the community can try out your changes and ideas for itself and contribute to the discussion.

      When you are unsure, ask for help. Nobody knows everything, and nobody is expected to be perfect in the Ubuntu community (except of course the SABDFL). Asking questions avoids many problems down the road, and so questions are encouraged. Those who are asked should be responsive and helpful. However, when asking a question, care must be taken to do so in an appropriate forum. Off-topic questions, such as requests for help on a development mailing list, detract from productive discussion.

      Step down considerately. Developers on every project come and go and Ubuntu is no different. When you leave or disengage from the project, in whole or in part, we ask that you do so in a way that minimises disruption to the project. This means you should tell people you are leaving and take the proper steps to ensure that others can pick up where you leave off.

I don't know why people come up with this stuff if they have no intention of following it themselves.


Man I got to find a better linux, where people are actually helpful and not full of ego trips.  You know, where if you're being helpful in ANY form people are going to go into a power trip because it wasn't the way they wanted to help someone.

[/SIZE]

---

### Post by tcoffeep on 2007-07-16
[edit] DELETED. Not wasting good words [/edit]

---

### Post by aysiu on 2007-07-16
I don't get it.

---

### Post by PrimoTurbo on 2007-07-16
I think ubotu is the official channel bot that answers questions and such. They don't want you to run a last seen script because while it's useful it can spam the channel with a lot of requests. They should just incorporate last seen info using ubotu and private msg.

---

### Post by bonzodog on 2007-07-16
As a long time IRC user (11 years this year), and someone that has ops on the #ubuntu-gwos channel, Yes, ubotu should be the only operative bot in there. 

If you run a script, run it in such a way that it does not display output to the public channel but opens a PM to yourself in response to your questions. We do not need other people scripts blocking up the main public area, and, also, once other users cotton on to the idea that there is another script or bot in the channel, they *will* try to abuse it.

You will be welcome in #ubuntuforums as well as long as you abide by this. Bot abuse can be bad at times, people get bored easily, and start throwing silly commands at the bot. In #ubuntuforums, ubotu will respond to a few other commands that it doesn't in #ubuntu.

I will ask Seveas (Dennis Kaarsmaker) about maybe including a @seen function into ubotu. That particular function would be useful. Most things that start with ! are requests for package information. Ubotu will accept direct commands using the @ before the command., but 'seen' is not one of them unfortunately.

---

### Post by Talaman72 on 2007-07-16
"If you run a script, run it in such a way that it does not display output to the public channel but opens a PM to yourself in response to your questions."

UM, WHAT?

We do not need other people scripts blocking up the main public area,

Um, one line is blocking up the channel?
[http://www.arklinux.org](http://www.arklinux.org) is your friend

---

### Post by bonzodog on 2007-07-16
When you run the bot or script, it does not need to output to the channel window.

There is a well known XChat script (xlack) that when you ask it certain things, it opens a 'query' or PM window in response to your commands, so only you can see the output.

---

### Post by Tomosaur on 2007-07-16
> **Talaman72 said:**
> "If you run a script, run it in such a way that it does not display output to the public channel but opens a PM to yourself in response to your questions."

UM, WHAT?

We do not need other people scripts blocking up the main public area,

Um, one line is blocking up the channel?
[http://www.arklinux.org](http://www.arklinux.org) is your friend

If they made an exception for you, they'd have to make an exception for everyone, thus invalidating the rule. While one line of text certainly can't be construed as 'spamming the channel', if other people see that you have a script running, then they too will run their own, or try to abuse yours, and eventually there WILL be channel spamming. Acting fast and acting decisively ensures such a situation never arises. While it's certainly annoying to be booted from a channel, if you'd followed the rules, it wouldn't happen. Scripts such as yours are absolutely useless to others, and make it more difficult for people to get the help they need. Short answer? Make your scripts PM you, or don't use them in that channel.

---

### Post by Talaman72 on 2007-07-16
it opens a 'query' or PM window in response to your commands, so only you can see the output.

That would be kind of pointless wouldn't it?

I mean if someone triggered and to have it only output to me?!

---

### Post by maniacmusician on 2007-07-16
> **Talaman72 said:**
> it opens a 'query' or PM window in response to your commands, so only you can see the output.

That would be kind of pointless wouldn't it?

I mean if someone triggered and to have it only output to me?!
Why not make it so if people trigger it, it responds just to them? This can be done too. FCM bot on #fullcirclemagazine can do this, and if you don't know how, ask it's creator (mrmonday) how he accomplished it. as it is, your script is ineffective.

---

### Post by Talaman72 on 2007-07-16
> **Tomosaur said:**
> If they made an exception for you, they'd have to make an exception for everyone, thus invalidating the rule. While one line of text certainly can't be construed as 'spamming the channel', if other people see that you have a script running, then they too will run their own, or try to abuse yours, and eventually there WILL be channel spamming. Acting fast and acting decisively ensures such a situation never arises. While it's certainly annoying to be booted from a channel, if you'd followed the rules, it wouldn't happen. Scripts such as yours are absolutely useless to others, and make it more difficult for people to get the help they need. Short answer? Make your scripts PM you, or don't use them in that channel.

WOW, <snip>.   "Acting fast and acting decisively" makes me feel like an insurgent or something.  Hurry, we must put them down now before they uprise against us. <snip>

Furthermore, "Scripts such as yours are absolutely useless to others," in this case, was not the case.  AS was illustrated (yeah), my script provided the requested info where as the "room bot" (nope) couldn't. 

Now I had contemplated setting it to PM the person activating it.  However, PMing someone before asking them is considered bad form.

---

### Post by Talaman72 on 2007-07-16
> **maniacmusician said:**
> Why not make it so if people trigger it, it responds just to them? This can be done too. FCM bot on #fullcirclemagazine can do this, and if you don't know how, ask it's creator (mrmonday) how he accomplished it. as it is, your script is ineffective.

 as it is, your script is ineffective. 

It works, and produces the output required as designed, how is that ineffective?

in·ef·fec·tive      /&#716;&#618;n&#618;&#712;f&#603;kt&#618;v/ Pronunciation Key - Show Spelled Pronunciation[in-i-fek-tiv] Pronunciation Key - Show IPA Pronunciation
–adjective
1.	not effective; not producing results; ineffectual: ineffective efforts; ineffective remedies.
2.	inefficient or incompetent; incapable: an ineffective manager.
3.	lacking in artistic effect, as a literary work, theatrical production, or painting.

---

### Post by Tomosaur on 2007-07-16
> **Talaman72 said:**
> WOW, let it be known fascism still lives.   "Acting fast and acting decisively" makes me feel like an insurgent or something.  Hurry, we must put them down now before they uprise against us.  What tyranny.  What bull.

Furthermore, "Scripts such as yours are absolutely useless to others," in this case, was not the case.  AS was illustrated (yeah), my script provided the requested info where as the "room bot" (nope) couldn't. 

Now I had contemplated setting it to PM the person activating it.  However, PMing someone before asking them is considered bad form.

If you think that's Fascism, wait til, I don't know, you read a book or go to school or something. Grow up. Society works because you accept certain rules. One of the rules of the ubuntu IRC channel is that you don't use stupid scripts which nobody cares about. **One line** doesn't spam the channel, but if everyone used such scripts, then there **would** be spam. The only way the channel ops can be sure it doesn't happen is to remove anyone who breaks the rule as soon as they notice the rule has been broken. Believe me, I've opped on IRC channels before, and a trickle of harmless scripts quickly degenerates into a flood of spammy crap which has no real purpose other than to show off your leet scripting skillz. Either make the script PM the person activates it, or don't use it at all. It's not fascism to suggest that you abide by the rules of te channel. If you don't want to, then don't go there.

---

### Post by Talaman72 on 2007-07-16
> **Tomosaur said:**
> If you think that's Fascism, wait til, I don't know, you read a book or go to school or something. Grow up. Society works because you accept certain rules. One of the rules of the ubuntu IRC channel is that you don't use stupid scripts which nobody cares about. **One line** doesn't spam the channel, but if everyone used such scripts, then there **would** be spam. The only way the channel ops can be sure it doesn't happen is to remove anyone who breaks the rule as soon as they notice the rule has been broken. Believe me, I've opped on IRC channels before, and a trickle of harmless scripts quickly degenerates into a flood of spammy crap which has no real purpose other than to show off your leet scripting skillz. Either make the script PM the person activates it, or don't use it at all. It's not fascism to suggest that you abide by the rules of te channel. If you don't want to, then don't go there.

Wow, I get my post snipped (thanks for quoting me on that one) for being disrespectful, but "you read a book or go to school or something. Grow up."  WOW!  You say "I've opped on IRC channels before" and so have I..and?!?!

fas·cism
Oppressive, dictatorial control.

---

### Post by bapoumba on 2007-07-16
Sorry, thread locked.
I'll have other staff review this thread.

---

### Post by PriceChild on 2007-07-16
Hi there.

I am a #ubuntu operator, part of the ubuntu-irc team and hopefully will be on the ubuntu-irc Council.

I removed you personally       Jul 12 2007 10:47:16 with the remove message "no bots/talking scripts" as can be seen by the bantracker here: [linky]("https://bots.ubuntulinux.nl/bans.cgi?query=Talaman72&kicks=on&oldbans=on&bans=on&oldmutes=on&mutes=on").

Firstly, the forums are **NOT** the place to complain about things like this. The correct place is #ubuntu-ops on irc.freenode.net

Secondly, public away scripts, unauthorised (talking) bots and public talking scripts are not welcome in the majority of #ubuntu. Can you imagine if there was two or three people with a !seen script on? It would start flooding the channel very quickly. I would advise you to use /whois or even better, "/msg seenserv <nick>"

Feel free to contact me on irc if you have any questions, I will be online as PriceChild, Pricey or PriceChi1d and almost always available in #ubuntu-ops.

And finally, I refer you to the Irc Guidelines: [https://wiki.ubuntu.com/IrcGuidelines](https://wiki.ubuntu.com/IrcGuidelines) & [https://wiki.ubuntu.com/IrcTeam/OperatorGuidelines](https://wiki.ubuntu.com/IrcTeam/OperatorGuidelines)

---

