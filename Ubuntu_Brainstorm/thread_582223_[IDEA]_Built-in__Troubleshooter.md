---
title: "[IDEA] Built-in  Troubleshooter"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by rickggreen on 2007-10-19
How about a simple troubleshooter in the System drop down menu.

I know "help and support"  is there right now, but to a "newb"  IRC, searching the forums, and  trying to read through "man" can be frustrating.

---

### Post by smartboyathome on 2007-10-19
How would you propose this troubleshooter to work, and how would you propose to keep it up to date with the current issues?

---

### Post by rickggreen on 2007-10-19
> **smartboyathome said:**
> How would you propose this troubleshooter to work, and how would you propose to keep it up to date with the current issues?

I knew someone would ask me that!

Something button based, with pointers/html to "man". 
Common problems, with pointers where one might find the answer.
 I know the answers are are out "there", it is trying to find them that is hard. 
Knowing  the "right" question to ask is part of the problem, the forums can be great, but having *all* the right info if helpful.

I'm trying to start a brainstorm here, so that when the time comes to submit a proposal, we might just have something worth while.

---

### Post by kripkenstein on 2007-10-20
This is a very good idea. Here is my contribution to the brainstorming.

Imagine this. You have a 'Troubleshoot' button in the system menu, as suggested. This brings up a little window that says
```

Please enter keywords that briefly describe your problem.
For example, if the issue is Azureus crashing, try
"azureus crash". If you have received a specific error
message, past it here inside quotes.

```
The user enters some keywords and receives a response of 'suggestions'. The suggestions could be
[LIST]
[*]Links to Ubuntuforums threads
[*]Links to Ubuntu Wiki pages
[*]A list of possible apps that might help with the issue [*]A brief, simple solution if short enough (for example, "to run the script, do 'chmod +x' first")
[*]A list of relevant bugs on Launchpad
[/LIST]
This gives sort of a 'first response' when a user has an app crash, or gets an error message. In fact, what I generally do is paste the error message in google, and often I get a thread on ubuntuforums ;)

Now, to get this to actually be useful, it needs a good database of keywords and suggestions to respond with. We would start with a hand-crafted database somehow, but later we could automate it as follows:

After the user gets the suggestions, they are given a 'feedback' window (perhaps after a minute or so). It asks whether the suggestions were helpful, and if the data can be anonymously submitted to the server to help other people.

On the server, we accumulate keywords and the effectiveness of solutions. We then manually - with community help - try to find good suggestions for common keywords with non-useful suggestions. As for suggestions that are ranked as useful, we would note them as such and make them appear first. This steadily improves the database over time. The client would have the option to, at a click, download the latest database.

I can help developing this, by the way, if people think it is a good idea.

---

### Post by smartboyathome on 2007-10-20
I see a couple of flaws in what you are talking about. What about people who can't get online? There should be a database of the most common solutions on the forums, and some from the wiki. This would all be updatable via a debian package. A problem with the package would be its size - it would probably have to be compressed and THEN uncompressed on the computer its going to.

---

### Post by kripkenstein on 2007-10-20
> **smartboyathome said:**
> I see a couple of flaws in what you are talking about. What about people who can't get online? There should be a database of the most common solutions on the forums, and some from the wiki. This would all be updatable via a debian package. A problem with the package would be its size - it would probably have to be compressed and THEN uncompressed on the computer its going to.

Of course, it should be compressed, downloaded, then uncompressed. And it should not depend on an internet connection for first installation (would be nice if it were on the Ubuntu CD).

---

### Post by Zdravko on 2007-10-20
Just don't make it like Win troubleshooter. It is terrible.

---

### Post by Mr.Auer on 2007-10-21
Hahaha...As soon as I read the title of the thread I started thinking OMG the Windows automated helper...Ive tried using that years back then, and boy all it did was make me even more mad than I already was...Trying to sort out some file permission issues on XP..and of course it was an utter waste of time.

Yea, it might be a good idea, but how to do it so it would actually be helpful to anyone? Perhaps improving the help documentation itself would be time better spent, and the "helper" could be just a way of pointing a newbie user to the right section of the help documentation itself. Hire some IT writer or someone whos done books on using Ubuntu to write a thorough manual thats included by default, that would be helpful for beginners. Translations in major languages...Not a small endeavour.

---

### Post by thtrgremlin on 2007-10-28
While I agree in principle, looking at history I think it is a bad idea. While windows has done so many things so poorly, I don't think this happened so much out of lack of planning, but that it is an impossibly perfectible project beyond what exists.

I'll say it again, I would love to see something like this, but I think it is the nature of troubleshooting. Once the computer has gotten it wrong, you really think it is going to be able to tell you how to fix it? Documentation and inline assistance with GUI tools helps avoid PICNIC issues (a realistically more perfectible endeavor) is something that should be the final finishes each GUI should focus on in its polishing stage.

I think "Tuxy" (Tux version of Clippy) would be death for ubuntu.

---

### Post by naught101 on 2007-10-29
I think this is a brilliant idea - we should put in a blueprint on launchpad.net.

I disagree that the windows trouble shooter is bad. I think it's actually a quite good system, for non-technical users. I always hated using it myself, but once or twice, it did work for me, and I know it worked for my parents numerous times. The whole "my printer isn't working... Ok, is it turned on? yes? is your computer turned on? no? oh, well there's your problem" approach is good - a simple tree heirarchy, within which each user can answer a simple yes/no, or multiple choice question, and move on to the next step, until a solution is found, or a man page, or web-based howto is given for further reading.

That said, of course this idea shouldn't replace any current or future systems. It should just complement them.

It might be possible to create the tree structure with a wiki, and then automatically convert it to html, package it up, and put it in the repositories for each new release. Obviously this means that a) it's going to be crap for a while, or b) a lot of hard work before hardy comes out.

---

### Post by ronacc on 2007-10-29
I think rather than an automated troubleshooter which would be complex and prone to breakage itself perhaps a better way would be a simple text file with step step instructions for troubleshooting and correcting common problems would be a better approach. If we keep it simple ascii text it should be small enough to fit on the cd , unadorned text takes up almost no space and is readable even from a minimal console. and it would also teach the user something about how things work.furthemore much of the work has already been done in this and other forums.

---

### Post by mabovo on 2007-10-29
I like this idea.
As new users come to Ubuntu whom never had contact before with Linux desktop, when the system display weird messages on logon screen this newbie gets terrified and don't have any idea how to solve it.
For instance, there are black holes in Linux like ICEauthority that someone needs to dig Howto's and docs to have an idea about what is happen with file permissions, etc.

---

### Post by 23meg on 2007-10-29
Moved to Ubuntu Idea Pool.

---

### Post by osx424242 on 2007-10-30
Here are some brainstorms after I read the initial couple posts.  After reading further, some form of #5 might be the best: a lot of websites now have a "Click here to chat online with a customer support representative" link.  Pre-installing IRC, then making the "Troubleshooting" link just do a /join #ubuntu might be the best troubleshooting tool available.  As some pointed out, maybe their Internet access isn't working: so the Troubleshooting link should do 'something' (ping a server? ping an IP address? check 'ifconfig'?) and then either point the user to some very detailed "Get online" documentation, or else just do the /join #ubuntu.

1) When I was having problems getting wireless to work, I tried starting a thread on ubuntuforums.org.  After I typed in the subject (something like: intel 3945abg wireless won't connect), a list of related threads popped up, and I spent some time searching through them (most of them I _hadn't_ found on previous searches), and they pointed me in a lot of new directions.  Maybe ask people to explain their problem, then do a search on ubuntuforums.org based on their question.

2) When I looked (very, very briefly) through the Help and Support pages it all seemed to be pretty generic: designed to help anyone with any problem.  BUT, once Ubuntu is installed on a computer, we now have some very specific information about that computer.  How about adding a database of common hardware (e.g. for wireless, Broadcom, RealTek, Intel) and doing a quick scan of their hardware (using ifconfig, lscpi, and other outputs) to see which one (or more than one) the user has.  For example, if they have an Intel wireless chipset there is no need to post the ndiswrapper page: it's just a red herring.  On the other hand if some basic utility outputs report that there is no wireless card, ndiswrapper might be exactly the information to show.  Most people who post a "wireless doesn't work" thread end up getting prompted to post those same outputs anyway, so the Troubleshooter should be able to figure out what hardware they have and give them targeted instructions or suggestions.  Pointing the user to sticky threads related to their hardware could be useful, too.

3) If the troubleshooter fails to fix things after two or three common problems, it can automatically set up a new thread on ubuntuforums.org.  Create a new user account for them if they don't have one (check cookies _first_ & _then_ ask them if they have one) and prompt them for a paragraph or two about their problem, then automatically attach all the relevant info (dmesg, iwconfig, Xorg.conf, Ubuntu version, etc.) so that anyone who looks at the thread doesn't have to ask questions and wait for a response (and potentially from someone who will try to type the '$').  When they are prompted for the paragraph about their problems, _give_them_a_template_.  "Uhhh, I turn it on and wireless doesn't work, but it works on my other computer, and this one is closer to the modem," doesn't help, but if they're prompted with "what have you tried," "describe step by step what happens," and "attach a screenshot (and here's how...)," they may be able to provide more useful information.

4) If you start creating posts on ubuntuforums.org for them, be sure to subscribe them to the thread (figure out their e-mail address automatically, if you can; otherwise ask them) so they'll be sure to get their responses.  Prepend and/or append every e-mail with "if your problem has been fixed, please click here to mark the thread as Solved, to help others in your situation," to get better feedback (read: job satisfaction! This plan would _not_ fly if responses to automatic support requests seem to fall into a black hole every time) for the people who are helping them.  Prompt them to add a paragraph with what they did to fix it, but don't make it mandatory.

5) When they are done with the troubleshooter, get them involved in the community!  Point them to ubuntuforums.org, or install an IRC client and send them to #ubuntu.  Having a whole community of people out there who are willing to help you out for no monetary gain is _completely_ foreign to most people.  I've been asked several times by friends, "why do they make software and then just give it away?"  Introducing new users to the community will hopefully help them understand the community _and_ get them to participate in and contribute to the community.

6) I can't resist :), maybe it's just a naming thing, would this help?
```
ln "Help and Support" Troubleshooting
```

7) Post #2 asked how to keep this up-to-date with current issues... yeah, I got nothing here.  I guess the best thing to do is find a couple people who are really detail-oriented and tenacious, and put them on the Troubleshooting 'team' and convince the lone-star developers to work with them and fix all the bugs they find.  Yeah, good luck there.  If I had a _good_ answer to that problem, I'd be delighted to share it with you.

---

### Post by osx424242 on 2007-10-30
Okay, re-reading my previous post, I realized that I made a lot of assumptions about the users of *Troubleshooting*.  Maybe a better question to ask is, "Who is going to use *Troubleshooting*," (my answer was, "Intelligent people who have used computers but not Linux")?  A good *Troubleshooting* module should determine the user's skill and/or understanding level, and adjust as appropriate (Is this their first computer? Are they moving from a Windows or OS X system? Have they used Linux before,) and respond appropriately.

---

