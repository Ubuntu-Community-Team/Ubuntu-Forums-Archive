---
title: "Stamp out the Ubuntu guide?"
date: 2005-11-06
forum: The Cafe
---

### Post by essexman on 2005-11-06
I'm concerned about the [users mailing list]("http://www.ubuntuforums.org/showthread.php?t=86441&highlight=ubuntuguide"), a forum to which I am unable to repond using phrases such as "we have been working hard to stamp out the "Ubuntu guide".

[Ubuntuguide]("http://ubuntuguide.squarecows.com/doku.php") is not perfect or 100% accurate. but neither are these forums or Ubuntu. Perfection and accuracy are not reasons I use Ubuntu. The Ubuntuguide and ubuntu forums _are_ reasons I use Ubuntu.

The mailing list folk seem to be upset that the Ubuntu guide author stopped communicating with them. I do not understand why anyone should be pointed away from the Ubuntu guide or [pointed away]("http://www.ubuntuforums.org/showthread.php?p=468857#post468857") from anything on the forums, surely that is for Ryan and the Moderators to decide.

I feel that the Docs team would better spend their time attracting people. Instead of just telling people 'We are in charge now' 'you must read or documentation', they could try posting links, help and advice.

Help and advice seems to me, to carry more 'Humanity' than 'Stamping out'.

Must go and clean the house now, my girlfriend is getting impatient.

It is important to keep One's own house in order.

---

### Post by imagine on 2005-11-06
I go with the doc-team here. It's confusing especially for new users to have two or more guides which all cover mainly the same questions. Everybody can help with the Official Guide so I don't understand why we need another guide with different authors. Maybe you can give me some reasons. Two I know of is 1) missing non-free software and 2) the use of Synaptic instead of the command line.

1) Non-free stuff is indeed not directly included in the Official Guide, but it would be enough then to create a "Unofficial UbuntuGuide about non-free software", where only things like Win32 Codecs, Sun Java, etc is explained.

2) I agree with that, although I think many new users prefer Synaptic over the command line, so maybe both can be included into the Guide. And as far as I remember members of the doc-team were open to adding command-line statements.
```
How can I bla bla...?

A. With the command-line
echo deb-src... >> /etc/apt/sources.list

OR

B. With Synaptic
Click here and there...
```
Just an idea...

---

### Post by essexman on 2005-11-06
[quote=imagine]I go with the doc-team here. It's confusing especially for new users to have two or more guides which all cover mainly the same questions. Everybody can help with the Official Guide so I don't understand why we need another guide with different authors. Maybe you can give me some reasons. Two I know of is 1) missing non-free software and 2) the use of Synaptic instead of the command line.

1) Non-free stuff is indeed not directly included in the Official Guide, but it would be enough then to create a "Unofficial UbuntuGuide about non-free software", where only things like Win32 Codecs, Sun Java, etc is explained.

2) I agree with that, although I think many new users prefer Synaptic over the command line, so maybe both can be included into the Guide. And as far as I remember members of the doc-team were open to adding command-line statements.
```
How can I bla bla...?

A. With the command-line
echo deb-src... >> /etc/apt/sources.list

OR

B. With Synaptic
Click here and there...
``` Just an idea...[/quote]

The Ubuntu guide started out as "the unofficial ubuntu guide" and grew because there was nothing else.

The non-free stuff is being well handled by easyubuntu and others.

the 5.10 starter guide uses yelp.

This is difficult to search, poorly maintained, and not regularly updated.

And...

Exactly what part of "Stamping out" expressed by the doc team do you agree with?

Prehaps there is only room for one debian based Distibution?  All these various distibutions with different packages is very confusing.

---

### Post by az on 2005-11-06
I think the mailing list thread you point out clearly shows the evolution of the situation.

I think the end-users are what is in mind.  I think the goal is a long-term solution.  Sometimes it is uncomfortable to work as a team.

I think by and large a great deal of people appreciate the work that has gone into the unofficial guide.  I aggree that that does not show in the mentioned thread.

---

### Post by Brunellus on 2005-11-06
the GUI versus CLI issue has been discussed at length on these forums. The GUI method may make newbies feel better, but it is notoriously difficult to write decent directions for GUI steps.  Here's a more concrete example for you:

>  NEWBIE:  how do I install program-x?

GUI GUY:  OK.  First go up, click on SYSTEM.  Then go to Administration, then to Synaptic Package Manager.  Wait for it to get going.  Then, click the "search" button and type "program-x" into the box.  Then, click the box on the left of where "program-x" appears in the list.  Go up, hit ACCEPT CHANGES, and wait for it to complete.  Close Synaptic.

CLI GUY:  Open a terminal.  Copy and paste the following onto the command line:

sudo apt-get install program-x

Give it your password, hit yes.  when it finishes, program-x is there.



See how much faster the CLI method is?  It certainly doesn't give the newbies much confidence in their own abilities, I will grant, but it sure as hell saves work for the people trying to help the newbie, because it leaves very little room for misinterpretation.

---

### Post by essexman on 2005-11-06
I agree with your points about CLI C&P.  I found this very easy to use and it think it would be good as an interim to have both systems.

Watch out for this though - you signiture points to Buffalo Soldiers excellent post (which needs updating from March)   				> there's no crying in *nix.

Need Help?
[http://www.ubuntuforums.org/showthread.php?t=13042]("http://www.ubuntuforums.org/showthread.php?t=13042")

This post points to the ubuntuguide and it is pointing to the ubuntuguide and possibly any other howtos that the docs team are trying to eradicate or "Stamp out"

I'm now in a [discussion]("http://www.ubuntuforums.org/showthread.php?p=470923#post470923") on the forum with a docs team member who doesn't believe that the docs team have to follow any guidelines other than thier own.  I think it is unlikely that they will follow comunity requests or suggestions if they disregard community guidelines.
[]("http://www.ubuntuforums.org/showthread.php?t=13042")

---

### Post by Brunellus on 2005-11-06
My .sig is my business.  If I'm to be stamped out, then let them fire up the bloody gas chambers.

---

### Post by essexman on 2005-11-06
[quote=Brunellus]My .sig is my business.  If I'm to be stamped out, then let them fire up the bloody gas chambers.[/quote]

I hope your .sig remains your business.

It really does seem that they are "firing up the chambers".

---

### Post by imagine on 2005-11-06
[QUOTE=essexman]The Ubuntu guide started out as "the unofficial ubuntu guide" and grew because there was nothing else.[/QUOTE]Yes, as so many things, eg backports.
But notice the past tense.

[QUOTE=essexman]The non-free stuff is being well handled by easyubuntu and others.[/QUOTE]Right, but Easy Ubuntu is a script, not a guide. There are users who rather install things manually than with a script, so I don't think everything in Easy Ubuntu should be excluded from the guide(s) - although Easy Ubuntu is a nice application.

[QUOTE=essexman]the 5.10 starter guide uses yelp.[/QUOTE]If that means you don't like Yelp, fair enough. However the Guide can also be accessed with an ordinary webbrowser: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

[QUOTE=essexman]This is difficult to search,[/QUOTE]The website of the Official Guide can be searched through as every other site.

[QUOTE=essexman]poorly maintained,[/QUOTE]What exactly do you mean?

AFAIK that was the main concern with the Unofficial Guide. Eg the Unofficial Guide tells you to add the breezy-extras repository and then installing software from it. However that repository is empty, in fact there was never anything in it. Even worse it goes on by recommending inexperienced users to add repositories with packages in alpha or beta state: extras-staging and backports-staging. One being empty, the other with one package which is broken.

I bet there are also things in the Official Guide which should be updated, changed or improved, but then it only looks reasonable to me to join forces in one Guide instead of two or more.

[QUOTE=essexman]Exactly what part of "Stamping out" expressed by the doc team do you agree with?[/QUOTE]Hmm was it only the wording which offended you? I agree that some statements weren't exactly what I consider nice and friendly, maybe some developers are just tired of the same topic brought up again, but I don't know.

What I agreed with was that there shouldn't be two or more Guides which cover the same questions.

Btw if you want to continue that discussion on the mailing list you should join it. If you use the forum software to send messages to the mailing list, your HTML-messages may look strange in the mailing list and the sendername is always some anonymous "Forum post". This in itself annoys some users on the list, regardless of the content of the message.
You should be aware that that discussion is not taking place in the forum but on the mailing list. The administrator of ubuntuforums.org just mirrors the mailing list with a script.

[QUOTE=essexman]Prehaps there is only room for one debian based Distibution?  All these various distibutions with different packages is very confusing.[/QUOTE]I don't think so.
However if that was just some cynical note I'm not bother replying to it. The discussion should be kept in a good athmosphere, without sarcastic remarks about forbidden signatures and gas chambers. That gets us nowhere.
Everybody can link to every UbuntuGuide in his signature he likes to, the same way everybody can maintain as many guides as he wants. I'm just saying that I don't think it's a good idea to work on multiple guides about the same topics.
Yes the UbuntuGuide started as a third party project, but then it became official and got his place on the Ubuntu servers. I consider this a good move and not a problem and my question why I should be wrong on this is still not answered.

---

### Post by essexman on 2005-11-06
Imagine

This is a great post, if only we could all follow your example.

You have covered all my points well, and provided extra information that will be helpful to me and others who read this.

> **imagine]

Hmm was it only the wording which offended you? I agree that some statements weren't exactly what I consider nice and friendly, maybe some developers are just tired of the same topic brought up again, but I don't know.[/quote]

Yes, the wording offended me.  I'm far too sensitive.  I feel that this was distrespecful to me and most important the Ubuntuguide creators whose hard efforts seem to have been carelessly disregarded.  If it had been one idle post I would not have picked up on it, but I did a quick search for ubuntuguide and was quite angry at what I saw, hence this thread (with angry icon  said:**
>  What I agreed with was that there shouldn't be two or more Guides which cover the same questions.

I agree with the result, but not the process. I like the truly evolutionary/naturally selective nature of FOSS and the fact that little  projects grow out of big ones, and the old ones come back.  Linux grew out of Minix newgroup, as developers migrated. and I do not see this as a problem.  I do not object to the notion of "this is obviously better than that so we sould put all our efforts into this".  I object to "this is better than that, so let us kill that off so that this will have more resources to grow into something even better"
 
>  Btw if you want to continue that discussion on the mailing list you should join it. If you use the forum software to send messages to the mailing list, your HTML-messages may look strange in the mailing list and the sendername is always some anonymous "Forum post". This in itself annoys some users on the list, regardless of the content of the message.
You should be aware that that discussion is not taking place in the forum but on the mailing list. The administrator of ubuntuforums.org just mirrors the mailing list with a script.

Yes.

I have just found this out and apologised.  I replied to a post from a newbie and got totally flamed, that is how the whole thing started.  The fence was down and I wondered into the angry neighbour's garden.  If I have realised that I was 'an anomynous smartarse', I would have left it right there.  We live and learn.
 

>  Yes the UbuntuGuide started as a third party project, but then it became official and got his place on the Ubuntu servers. I consider this a good move and not a problem and my question why I should be wrong on this is still not answered.

The last point was rhetorical, but not intended to be cynical.  But I don't think rhetorical works on a forum.

I'm not sure if you meant that **Brunellus** point was cynical, you'll need to ask him for that.

Your final point about rights and wrongs goes deep and it is hard to express how strongly I feel.

There is no need for a second guide at the moment,  but there might be.  I do no think it is wrong for you or anyone else to want more effort diverted on to what you consider to be the better system.  Projects have worked in parallel take KDE and Gnome for example, and it is quite possible that if one of these desktops were stopped then all attention would divert to the other. Pretty soon the remaining Desktop would become unbeatable and end up going on Apple and Microsoft.

I would be sad if either of these great projects stopped but providing it dwindled of its own accord, rather than a concerted effort to stamp it out I would switch to the survivor.  Then again, if one were stamped out, would the resources automatically migrate?  I don't believe they would.

Worse still what if Apple or Microsoft started offering their desktop free on a linux platform?  Mark Shuttleworth recently stated that he felt OSX was the #1 desktop and the bench mark for all desktop systems.

I will keep an eye on the Ubuntuguide and still refer people to it.  I will drift with the coummunity (forum) as I am not a leader.  But my first encounter with the doc team has not encouraged me to side with them.

---

### Post by manicka on 2005-11-06
I believe we have room for both types of help. 

help.ubuntu.com is the best place to start for many users and I try to send people in it's direction as much as possible, but there is also room for community driven advice/help like the how-tos in the customization forum or the archive of how-tos being developed at docs.gwos.org

To me it's the best of both world's. I agree that the docs team are being a bit overzealous on this one.

---

### Post by az on 2005-11-06
[QUOTE=manicka]I believe we have room for both types of help. 

help.ubuntu.com is the best place to start for many users and I try to send people in it's direction as much as possible, but there is also room for community driven advice/help like the how-tos in the customization forum or the archive of how-tos being developed at docs.gwos.org

To me it's the best of both world's. I agree that the docs team are being a bit overzealous on this one.[/QUOTE]
And then there is the UserDocumentation page on the wiki.

---

### Post by Master Shake on 2005-11-06
[QUOTE=manicka]I believe we have room for both types of help. 
[/QUOTE]

Hear, hear!

---

### Post by manicka on 2005-11-06
[QUOTE=azz]And then there is the UserDocumentation page on the wiki.[/QUOTE]

Yes, of course, thanks for correcting the slipup :)

---

### Post by TravisNewman on 2005-11-06
I would like to see a wiki project by the doc team to post the ubuntu guide, quick and dirty as it is, and then link to pages that better describe the situation. I don't think we need to move on from the ubuntu guide, I certainly don't think we need to stamp out the ubuntu guide, I think we need to integrate.

---

### Post by essexman on 2005-11-06
Thanks manicka

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

I installed beagle with this HOWTO

---

### Post by davidgypsy on 2005-11-06
Unhealthy rhetoric like "stamp out", "wipe out", "exterminate", etc. make me nervous. It is normally uttered by despots and dictators like Hitler, Stalin, Pol Pot, Robert Mugabe and crew. It is usually followed up with freedom limiting behaviour, contrary to what God intended for humans... and software.

---

### Post by cowlip on 2005-11-06
THe ubutuguide does get pretty outdated though.  I like how easy [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) is to follow too

---

### Post by Brunellus on 2005-11-06
I don't take too kindly to someone telling me that a resource that was particularly useful--the ubuntuguide--is now to be "stamped out", as if it were some sort of poisonous heresy, and its adherents burnt at the stake.

Whatever reasonable arguments on the matter could have been presented to me are lost on me now, as I have no desire to deal with people whose agenda seems patently to stamp out any resources that are not immediately under their direct control.   There is a distinctly Bolshevik tinge to that sentiment.

---

### Post by TravisNewman on 2005-11-06
[quote=Brunellus]I don't take too kindly to someone telling me that a resource that was particularly useful--the ubuntuguide--is now to be "stamped out", as if it were some sort of poisonous heresy, and its adherents burnt at the stake.

Whatever reasonable arguments on the matter could have been presented to me are lost on me now, as I have no desire to deal with people whose agenda seems patently to stamp out any resources that are not immediately under their direct control.   There is a distinctly Bolshevik tinge to that sentiment.[/quote] deja vu ;) (Brunellus just said basically the same thing in #ubuntuforums)

---

### Post by auburn on 2005-11-06
man, this "stamp[ing] out" thing is unraveling me too. I told more than one person that my favorite thing about ubuntu was the ubuntuguide. The format is soooo good and concise. I weened myself off windows thanks to that writer. I'm going to go email and thank him (/her) now.

---

### Post by TravisNewman on 2005-11-06
I'm sure your gratitude will be appreciated too.
I've had to go to the ubuntuguide many times before myself. 

The only problem I can see with it is that if you don't know a little bit about what you're doing, you can mess things up with it (like isntalling alpha packages, as mentioned), and it doesn't explain why you're pasting the commands into the terminal, etc. But it's STILL a fantastic resource.

---

### Post by davidgypsy on 2005-11-06
[quote=panickedthumb]I'm sure your gratitude will be appreciated too.
I've had to go to the ubuntuguide many times before myself. 

The only problem I can see with it is that if you don't know a little bit about what you're doing, you can mess things up with it (like isntalling alpha packages, as mentioned), and it doesn't explain why you're pasting the commands into the terminal, etc. But it's STILL a fantastic resource.[/quote]

It helped me out many a time, pity such a great resource gets such a bum rap.

---

### Post by janne5011 on 2005-11-06
I think as a new user best would be ONE place to look. Im only one user of course but,but my impression is  maybe a "getting started-guide" should be good?
major concerns first week is: install right kernel,install right kernel in right place, get monitor work,get network up (especially wifi is hard),get updates...
If those first  guides is good one learn principles from them and can later on apply thoose principles...

after that one can start learn the command-line and learn little more how it works and so on.


This forum is good :) but information is important and improvment can make it better.
Of coure all his is hard work..

---

### Post by Brunellus on 2005-11-06
[QUOTE=panickedthumb]I'm sure your gratitude will be appreciated too.
I've had to go to the ubuntuguide many times before myself. 

The only problem I can see with it is that if you don't know a little bit about what you're doing, you can mess things up with it (like isntalling alpha packages, as mentioned), and it doesn't explain why you're pasting the commands into the terminal, etc. But it's STILL a fantastic resource.[/QUOTE]
the sort of user that needs ubuntuguide most, thumb, doesn't care about the meaning of those commands.  He does however care that his computer is made whole.

---

### Post by Yagisan on 2005-11-06
[QUOTE=Brunellus]the sort of user that needs ubuntuguide most, thumb, doesn't care about the meaning of those commands.  He does however care that his computer is made whole.[/QUOTE]
So what do you do when they follow ubuntuguide and it doesn't work ? or worse still breaks their computer ?

At the very least, the Ubuntuguide should make optional, and clearly explain why and why not to do some things, such as adding the non-ubuntu repositries.

Using my box as an example, every time I see an Ubuntuguide command starting with wget, I know it will fail on my system.

---

### Post by TravisNewman on 2005-11-07
[QUOTE=Brunellus]the sort of user that needs ubuntuguide most, thumb, doesn't care about the meaning of those commands.  He does however care that his computer is made whole.[/QUOTE]
I'm saying it would be nice to have at least optional explanation that they can click on. If things were explained, then after they did things on the ubuntu guide, they'd have a much easier time of doing other things because they'd understand the workings of the system more.

I agree that most people want quick and dirty, but having a link to show more info would be super nice.

---

### Post by lerrup on 2005-11-07
Excuse my stupidity in this, but doesn't [this]("http://help.ubuntu.com/starterguide/C/faqguide-all.html") look familiar to anyone.

Perhaps a little thinking before posting might help sometimes...

---

### Post by mrtaber on 2005-11-07
I, for one, owe a debt of gratitude to the unofficial Ubuntu Guide.  It helped make Ubuntu usable on my machine, at a time when the official documenation was piss-poor (at best).

Things have changed, and now the official documentation is usable.  Has anyone offered the author of the unofficial guide a place on the official documentation project?  All this talk of "stamping out" is ungracious and unworthy of the Ubuntu project.

Mark

---

### Post by Burgundavia on 2005-11-07
I really hope this debate will just go away. It has nothing to do with the ubuntuguide itself. It is about the quality of information in the guide. The Documentation Team had legitimate concerns about the quality and made the hard decision to stop recommending it. This was after a long period of working with the author and also having some of our issues unanswered.

I truly wish the author of the guide the best. He means well. It is hard to write good docs for all classes of users.

Please put this to bed once and for all,

Corey

---

### Post by TravisNewman on 2005-11-07
what are some of the issues that went unanswered?

---

### Post by vayu on 2005-11-08
The Ubuntu Guide rocks.  I don't know if I would be using Ubuntu or Linux if it weren't for that guide.  It may be terse but it is also concise.  I really like the all on one page list of all the major issues it has.  It is a great reference.  I still use it when doing a fresh install.  No doubt there should be other guides for different levels of users, but there shouldn't be one guide for all users.

---

### Post by davidgypsy on 2005-11-08
[quote=mrtaber]I, for one, owe a debt of gratitude to the unofficial Ubuntu Guide. It helped make Ubuntu usable on my machine, at a time when the official documenation was piss-poor (at best).

Things have changed, and now the official documentation is usable. Has anyone offered the author of the unofficial guide a place on the official documentation project? All this talk of "stamping out" is ungracious and unworthy of the Ubuntu project.

Mark[/quote]

I agree! Also makes a bit of a joke about the supposed freedom side of Ubuntu... 

If someone makes something related to Ubuntu that is useful to so many people and the Ubuntu team thinks it sucks, so what! I was really looking forward to getting the Breezy version, and now I can't.

The damn thing WORKED for goodness sake!

---

### Post by Yagisan on 2005-11-09
[QUOTE=davidgypsy]I agree! Also makes a bit of a joke about the supposed freedom side of Ubuntu... [/quote] People have a right to express their opinion, however unpleasant it may be. If you truely believe in the freedoom of Ubuntu, then you also believe that others opinions also matter, otherwise - pot, kettle, black.

[QUOTE=davidgypsy]If someone makes something related to Ubuntu that is useful to so many people and the Ubuntu team thinks it sucks, so what! I was really looking forward to getting the Breezy version, and now I can't.

The damn thing WORKED for goodness sake![/QUOTE]
The issue is more that it didn't work. It didn't work on hoary for me, it doesn't work on breezy for me. It just doesn't work period. If it did work, I'd sing it's praises too, but until it is fixed, as in it does work, I recommend people avoid it.

If ubuntuguide is so important to you (plural), then guys/girls fix it so it works for the non-i386 users too.

---

### Post by delphi on 2005-11-10
[QUOTE=panickedthumb]what are some of the issues that went unanswered?[/QUOTE]

Looks like your question is not going to be answered...the irony of it...;)

---

### Post by Burgundavia on 2005-11-10
To respond to the above point, what are some of the issues that did not get answered:

1): Instructions with no explanations or links to explanations
2): Editor bottleneck, ie. only one person could change the actual site. This is a not a terrible huge thing when the person is active, but when they disappear for several months due to illness, it becomes a bigger issue
3) Does not fit in with Ubuntu best practices, which include things like sudo and emphasizing graphical solutions over cli solutions. (Which some will attack me for, but those peoples parents/sisters/grandparents probably won't)

Hopefully that sheds some more light on the issue.

Corey

---

### Post by bulldogzerofive on 2005-11-10
[QUOTE=essexman]

Must go and clean the house now, my girlfriend is getting impatient.

It is important to keep One's own house in order.[/QUOTE]

I feel your pain.  Wow, do i ever feel your pain.  Can't even find the time to upgrade to 5.10 because the kids keep me running at 100 km/h.

---

### Post by lerrup on 2005-11-10
[QUOTE=bulldogzerofive]I feel your pain.  Wow, do i ever feel your pain.  Can't even find the time to upgrade to 5.10 because the kids keep me running at 100 km/h.[/QUOTE]

That's why I upgraded at 5.30 in the morning.

---

### Post by Brunellus on 2005-11-10
[QUOTE=Burgundavia]
3) Does not fit in with Ubuntu best practices, which include things like sudo and emphasizing graphical solutions over cli solutions. (Which some will attack me for, but those peoples parents/sisters/grandparents probably won't)
[/QUOTE]

Consider yourself attacked.  GUI instructions are much harder to write and give, and irritate me to no end when something doesn't work right anyway.  The Guide's CLI-heavy approach is stark, yes, but it is definitely efficient.  About half an hour after skimming the guide for things that need doing after an install...I'm done.

While I understand the need to offer warm and fuzzy GUI instructions, and I appreciate good GUIs, I do not see why a CLI-centric guide should be so objectionable.  Your "editorial bottleneck" is point is well-taken, but surely there is plenty of room in the community for the guide's way of doing and teaching things.  

On calmer, second reflection, this discussion will be mooted as people develop better and better scripts for post-install configuration (like, say Automatix).

But again, what irritates me most about this debate is the truculence of the anti-Guide rhetoric.  If I wanted to be in a community with purges and counterpurges, I'd have joined the communist party.

---

### Post by TravisNewman on 2005-11-10
*[COLOR=dimgray]"3) Does not fit in with Ubuntu best practices, which include things like sudo and emphasizing graphical solutions over cli solutions. (Which some will attack me for, but those peoples parents/sisters/grandparents probably won't)"[/COLOR]*
 
I think that both ways should be described. I think that having a wiki page laid out like the ubuntuguide with cli and gui answers, with links to deeper description (to keep the main page clean) would work wonders.
 
Other than that, I've always seen the doc team's point on this. Corey, you haven't always left a pleasant taste in people's mouths, but I've always gotten your point and understood. I think that the problem here comes from the way that the original poster in the mailing list spoke of it, as if it were an abomination.

---

### Post by adamb10 on 2005-11-10
I like Ubuntu guide because it cuts to the chase.  I don't go there to know how to do something, I go there to see what apps I need.  I don't know the names of the codecs or adobes pdf reader.  Thats whee ubuntu guide comes in.

---

### Post by agger on 2005-11-10
Just one comment.

First of all, when I first installed Hoary, the Ubuntuguide helped me get everything in place and MP3s and MPEGs and so forth up&running.

I think the CLI instructions a plus, at least for me: But then I've been working with Unix for more than ten years, so ...

Secondly, a problem with the UbuntuGuide is the lack of explanations: It tells you what to do, but in some cases you really don't know what it is that it explains or whether or why you'd want it.

Thirdly, the built-in online Help (yelp) in Breezy actually now features a "Getting Started" guide which - lo and behold - takes you through exactly the same steps of installing codecs, fonts etc. as the UbuntuGuide does.

So, for me: Kudos to the UbuntuGuide, and kudos to the documentation team. I am grateful to the guy behind the Ubuntu Guide, and I'm grateful to the people from the doc team for building the instructions right into the Getting Started guide in the online help.

---

### Post by mattheweast on 2005-11-27
[QUOTE=essexman]
I'm now in a [discussion]("http://www.ubuntuforums.org/showthread.php?p=470923#post470923") on the forum with a docs team member who doesn't believe that the docs team have to follow any guidelines other than thier own.  I think it is unlikely that they will follow comunity requests or suggestions if they disregard community guidelines.
[]("http://www.ubuntuforums.org/showthread.php?t=13042")[/QUOTE]

Please stop associating people with the Ubuntu Documentation Team: it gives the team a bad reputation on the forums, which is not deserved.

1. the person to whom you refer does not work on the team
2. the team does not have any collective opinion on the subject matter currently in question
3. any opinions expressed by team members are simply individual opinions.

Matt

---

