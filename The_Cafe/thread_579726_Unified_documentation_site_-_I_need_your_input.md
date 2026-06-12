---
title: "Unified documentation site - I need your input"
date: 2007-10-18
forum: The Cafe
---

### Post by az on 2007-10-18
Hello.

I have been thinking about this for a while and I would like your ideas.

The "problem" is that there are many different sources of documentation for Ubuntu.  And many of them are excellent.  I believe there is no hope to unify them upstream.  People are going to contribute in the way they want to and there is nothing wrong with that.

We should not fight it, we should celebrate it.

What would you think of a site that would be a reference Ubuntu documentation from all the different sources, along with their articles?  For example, you could visit the site to search for the most popular articles (or best rated) pertaining to a particular subject.  You could also search for all the content that is contained in one site.  Or, you would search for a list of all the different sources of documentation.

Entries would contain the link to the original article as well as a short description.

All these site entries would be submitted by users.  You could log in and submit a site or just an article from a site.  You would enter keywords which best would help someone find the article.  

I would be inclined to leave the access control very open, so that if you think someone should have used different keywords to describe an article, you can go ahead and edit someone else's entry.

The entries could be ranked by popularity.  So, if one week, the best article describing how to enable desktop effects happens to be a forum post, it would "bubble up" in the popularity scale and be more prominent.  Perhaps another week, the same topic would have a more popular source from another site altogether.  Wherever the actual article is, any user can visit the documentation site and find references to what they need.

So, I would like your ideas.  Is this an idea that you would like to see implemented.  What features do you think would make a big difference in the end-user's experience?  What should the site be called?

I'm thinking maybe:

ubuntu-reference.org
ubuntu-library.org
thebrownpages.org


ref:
[https://lists.ubuntu.com/archives/ubuntu-doc/2007-August/009083.html](https://lists.ubuntu.com/archives/ubuntu-doc/2007-August/009083.html)

---

### Post by lyceum on 2007-10-18
I like "ubuntu-library.org" or ubulibrary if you want to shorten it. Sounds like a Wikipedia for ubuntu. I like it.

:guitar:

---

### Post by bruce89 on 2007-10-18
library.ubuntu.com just like [library.gnome.org]("http://library.gnome.org").

---

### Post by az on 2007-10-18
Thanks for your input.

> **bruce89 said:**
> library.ubuntu.com just like [library.gnome.org]("http://library.gnome.org").

My only problem with the library name is that a library is typically a very quiet place.  A library is pretty much static.  I reckon there are more than a thousand relevant documentation articles spread over dozens of projects and they all change, evolve, get better or depreciate with time.  What I'm trying to describe is more like a buffet or a party rather than a library.

That being said, if that's what people prefer or would find the most useful and friendly, then I'll go with that.  

As for the .ubuntu.com subdomain, I would gladly hand off the project to the official site if it were to become popular.  But I don't think approaching them and asking them for a subdomain (and consequently hosting) would be the thing to do at this point.

---

### Post by aysiu on 2007-10-18
Would this be something like Digg but for documentation instead of news stories/blogs?

I really like this idea, by the way. It is far more in the spirit of open source to leave the scattered documentation scattered but collected in an easy-to-find way than to try to impose some kind of artificial unification--just as Synaptic and Add/Remove make it easy to find scattered projects without forcing those projects to all be the same project.

---

### Post by k33bz on 2007-10-18
I like the ubuntu-library.org

sounds good

or maybe even Ubuntu-Archives.org

---

### Post by CaptainTux on 2007-10-18
I think it is a fine idea....or as my favorite innovators say....

Brilliant!!!

[IMG]http://www.mustangmods.com/data/10900/brilliant.jpg[/IMG]

---

### Post by az on 2007-10-19
> **aysiu said:**
> Would this be something like Digg but for documentation instead of news stories/blogs?


Pretty much.

As for the naming, how about something with a little more bite, like RTFM-ubuntu.org?  Just an idea...

---

### Post by bonzodog on 2007-10-19
Yes, we like the idea of this here at the UDSF. We would be happy to be part of putting this together.

Simon

---

### Post by Frak on 2007-10-19
manual.ubuntu.com
or
ubuntu-library.org

---

### Post by Tom Mann on 2007-10-19
bookfair.ubuntu.com ?

---

### Post by az on 2007-10-23
I have the basic functionality started:

[http://demo.ubuntu-rescue-remix.org](http://demo.ubuntu-rescue-remix.org)

The theme sucks, as well as the rating scheme is based in some places on hits, while others on the fivestar rating.  But anyway, this is what I am thinking of.

Currently, you don't need to link your article to a site, but maybe I'll enforce that eventually.  Maybe I'll make it a dropdown list.  That would be ugly, though.


Thoughts?

---

### Post by Frak on 2007-10-23
Kind of going technical into it, but you could use Flash to do some of the work for you, and by flash I mean using [Flash4Linux]("http://f4l.sourceforge.net/") and the Gnash player. Both are open implementations of each other and fully GPL compliant.

And from using Flash before, IMHO, the interface is familiar to Flash 8-CS3. (It looks nearly the same, except for the button style, but that would be the only difference)

---

### Post by az on 2007-10-23
Since there is no open standard for Flash, I try to avoid it whenever possible.  Anyway, I am not a developper.

---

### Post by az on 2007-10-23
> **Tom Mann said:**
> bookfair.ubuntu.com ?

What about Ubuntu-top-forty.org?

---

### Post by picpak on 2007-10-23
> **az said:**
> I have the basic functionality started:

[http://demo.ubuntu-rescue-remix.org](http://demo.ubuntu-rescue-remix.org)

The theme sucks, as well as the rating scheme is based in some places on hits, while others on the fivestar rating.  But anyway, this is what I am thinking of.

Currently, you don't need to link your article to a site, but maybe I'll enforce that eventually.  Maybe I'll make it a dropdown list.  That would be ugly, though.


Thoughts?

A nice start, but a little confusing. An excerpt from the post would be great. I mean, a topic called "LAMP server" doesn't mean anything to the new user.

Think something like the Ubuntu documentation equivalent of [elbo.ws](http://elbo.ws/).

---

### Post by az on 2007-10-24
> **picpak said:**
> A nice start, but a little confusing. An excerpt from the post would be great. I mean, a topic called "LAMP server" doesn't mean anything to the new user.

Think something like the Ubuntu documentation equivalent of [elbo.ws](http://elbo.ws/).

Yes, I could put a very short teaser.  But for now, it's really ugly when I do that.  To make it pretty, I would need to work on themeing.  I won't do the theming, until the usability is there since I would have to work on the theming every time I change the usability....

---

### Post by mattheweast on 2007-11-04
(editing this post due to a initial misunderstanding about the site's aims)

It's a nice idea but I'd like to see a way to integrate this sort of approach into the main Ubuntu help website. Obviously, links to external sites can be used on the wiki to supplement existing articles and some kind of rating system might be productive if implemented in the right way. It might help to give an idea of reliability as described here - [https://wiki.ubuntu.com/HelpWikiQualityAssurance](https://wiki.ubuntu.com/HelpWikiQualityAssurance)

Have you got any ideas about how to improve the help wiki so that it can become include the functionality you are looking to create in your site?

---

### Post by az on 2007-11-05
> **mattheweast said:**
> (editing this post due to a initial misunderstanding about the site's aims)

It's a nice idea but I'd like to see a way to integrate this sort of approach into the main Ubuntu help website. Obviously, links to external sites can be used on the wiki to supplement existing articles and some kind of rating system might be productive if implemented in the right way. It might help to give an idea of reliability as described here - [https://wiki.ubuntu.com/HelpWikiQualityAssurance](https://wiki.ubuntu.com/HelpWikiQualityAssurance)

Have you got any ideas about how to improve the help wiki so that it can become include the functionality you are looking to create in your site?

Hi Matthew!

Not really.

I don't really know if the wiki can offer the features that are needed.  But who cares?  I think the wiki does what it is supposed to do very well - that is to be a wiki.  The problem is that a wiki doesn't serve all the different needs.

What is needed is for folks to think of one place when they are searching for help.  I think that a dynamic site (similar to digg, as mentioned) where people can rate content would work best.  The best-rated or most popular content is shown more prominently than the less popular ones.  This would allow for a Darwin-type quality-control effect.

It doesn't matter whether the upstream web site is run by mediawiki, wordpress or Moin Moin.  Documentation is backend-agnostic.

You wouldn't be able to have complete control over that upstream content, but the alternative is to completely ignore it.  And that won't prevent people from creating it, nor prevent them from using it and finding it helpful.

Is there any chance the docteam would want to run a CMS like this?  Can you think of a good name for it?  I am reluctant to register an "ubuntu-library" domain name, since that is exceptionally boring (apologies to those who prefer it...)

---

### Post by mattheweast on 2007-11-05
> **az said:**
> Hi Matthew!
What is needed is for folks to think of one place when they are searching for help.  I think that a dynamic site (similar to digg, as mentioned) where people can rate content would work best.  The best-rated or most popular content is shown more prominently than the less popular ones.  This would allow for a Darwin-type quality-control effect.


I'd like the place for people to think of when searching for help to be the help website. And I agree that rating and comments can be useful for improving documentation pages, if used properly. I do think that it can be made part of a quality control process for the help wiki.

> 
It doesn't matter whether the upstream web site is run by mediawiki, wordpress or Moin Moin.  Documentation is backend-agnostic.


I agree

> 
You wouldn't be able to have complete control over that upstream content, but the alternative is to completely ignore it.  And that won't prevent people from creating it, nor prevent them from using it and finding it helpful.


Not completely ignore it. I think the best approach is via discussion, and where possible, integration. See [https://wiki.ubuntu.com/DocumentationTeam/IndependentDocEfforts](https://wiki.ubuntu.com/DocumentationTeam/IndependentDocEfforts)

> 
Is there any chance the docteam would want to run a CMS like this?  Can you think of a good name for it?

I don't think so - the docteam doesn't have the resources to do so, and personally I think the best approach is to create a single resource which address all the needs that people have. I believe that is possible. It needs efforts to be focused in the right place though.

---

### Post by aysiu on 2007-11-05
> **mattheweast said:**
> I think the best approach is to create a single resource which address all the needs that people have. I believe that is possible. Some of us don't believe that *is* possible, though. That's why we've created other resources.

---

### Post by az on 2007-11-05
> **mattheweast said:**
> I'd like the place for people to think of when searching for help to be the help website./QUOTE]

Well, the first step is to make the help website satisfy everyone's needs, all the time.

Although this idea would compete the official help, do you think it would harm it?


[QUOTE=mattheweast;3712405] And I agree that rating and comments can be useful for improving documentation pages, if used properly. I do think that it can be made part of a quality control process for the help wiki.

All I am suggesting is that providing the documentation and pimping it are two different things.  And both things probably need different tools.

> **mattheweast said:**
> 
Not completely ignore it. I think the best approach is via discussion, and where possible, integration. See [https://wiki.ubuntu.com/DocumentationTeam/IndependentDocEfforts](https://wiki.ubuntu.com/DocumentationTeam/IndependentDocEfforts)

Assimilation is futile.  You will be resisted. (*)

> **mattheweast said:**
> 
I don't think so - the docteam doesn't have the resources to do so, and personally I think the best approach is to create a single resource which address all the needs that people have. I believe that is possible. It needs efforts to be focused in the right place though.

So it will take less manpower to seek out and convince all the independent documentors to follow the official guidelines and resources?  It's hard enough to keep up-to-date with the actual content!

> **aysiu said:**
> Some of us don't believe that *is* possible, though. That's why we've created other resources.

There are probably lots of reasons why people do it.  What's relevant is that you can't stop them.  I think that's the key to the success of "open source"  I think the "open source" thing to do in that case is to let them do the work.


(*) [http://www.worthynews.com/news-features/resistance-is-futile.html](http://www.worthynews.com/news-features/resistance-is-futile.html)

---

### Post by mattheweast on 2007-11-06
Free software and free documentation are both about collaboration. As with software, new ideas and new aims are healthy to improving things.

Unfortunately people don't think as carefully about creating a new documentation site as they would about forking software - the latter they will only do when the fork has a different aim, but the former they do often without considering that their work would be more efficient and more helpful to users if they collaborated with existing resources and made their work open to others to edit, correct, improve and so on.

It's not a major part of the documentation team's work to identify such resources, so not much manpower is taken up by doing that. But if we can convince people to collaborate, then it's a positive thing. If someone is running a resource that genuinely has a different aim to the official site, I absolutely accept that. However in talking to many many different people running separate resources, I've come across very few who have genuinely considered whether they can use the help website and are able to give a good reason why they don't. That's fine, people have a right to do their own thing, but it's not in the best interest of users in my opinion.

I think your idea is an interesting one because it is aiming at some kind of integration of other people's work on documentation. However, it's problematic  in the way it goes about addressing the issue. It will end up actually promoting the beginning of new independent resources rather than encouraging collaboration on the help wiki, which will fragment effort and remove consistency. Lastly I fear that you'll find unreliable resources there which are essentially closed source in that it's not necessarily easy to get mistakes corrected.

---

### Post by az on 2007-11-06
> **mattheweast said:**
> Free software and free documentation are both about collaboration. As with software, new ideas and new aims are healthy to improving things.

Unfortunately people don't think as carefully about creating a new documentation site as they would about forking software - the latter they will only do when the fork has a different aim, but the former they do often without considering that their work would be more efficient and more helpful to users if they collaborated with existing resources and made their work open to others to edit, correct, improve and so on.

It's not a major part of the documentation team's work to identify such resources, so not much manpower is taken up by doing that. But if we can convince people to collaborate, then it's a positive thing. If someone is running a resource that genuinely has a different aim to the official site, I absolutely accept that. However in talking to many many different people running separate resources, I've come across very few who have genuinely considered whether they can use the help website and are able to give a good reason why they don't. That's fine, people have a right to do their own thing, but it's not in the best interest of users in my opinion.

Waste of resources or choice?

No matter how good your intentions are, your model will be perceived as a dictatorship.  I doubt that anyone will tell you that to your face because it really isn't arguable.  But people will always prefer to do their own thing.

I know the Docteam is not a dictatorship.  I'm a big fan of the Docteam. I am describing what the person who is not involved in the community thinks.  It's a lot of work to get involved.  Most people want to get in, shoot their load and get out.

The fact is these third-party resources are very successful.  Who's to say their reasons are invalid or that their aims are divergent enough?  I think it's irrelevant.  

Instead of trying to persuade them to conform to a community, I think they already are part of that community by virtue of the fact that they are in use.  My idea is to persuade the userbase to direct other users to the "good" (okay, popular) sites and away from the bad ones.


> **mattheweast said:**
> 
I think your idea is an interesting one because it is aiming at some kind of integration of other people's work on documentation. However, it's problematic  in the way it goes about addressing the issue. It will end up actually promoting the beginning of new independent resources rather than encouraging collaboration on the help wiki, which will fragment effort and remove consistency. Lastly I fear that you'll find unreliable resources there which are essentially closed source in that it's not necessarily easy to get mistakes corrected.

You can't have it both ways - you can't have fine-grained control over all the content that is out there, nor can you only make the official documentation popular.  

What I am promoting is integration of the independent contributions instead of competition.  No one wants bad documentation.  I doubt that a third-party site that is spreading inaccurate information will be very popular.

---

### Post by bonzodog on 2007-11-06
> **az said:**
> Waste of resources or choice?

No matter how good your intentions are, your model will be perceived as a dictatorship.  I doubt that anyone will tell you that to your face because it really isn't arguable.  But people will always prefer to do their own thing.

I know the Docteam is not a dictatorship.  I'm a big fan of the Docteam. I am describing what the person who is not involved in the community thinks.  It's a lot of work to get involved.  Most people want to get in, shoot their load and get out.

The fact is these third-party resources are very successful.  Who's to say their reasons are invalid or that their aims are divergent enough?  I think it's irrelevant.  

Instead of trying to persuade them to conform to a community, I think they already are part of that community by virtue of the fact that they are in use.  My idea is to persuade the userbase to direct other users to the "good" (okay, popular) sites and away from the bad ones.

You can't have it both ways - you can't have fine-grained control over all the content that is out there, nor can you only make the official documentation popular.  

What I am promoting is integration of the independent contributions instead of competition.  No one wants bad documentation.  I doubt that a third-party site that is spreading inaccurate information will be very popular.

Andrew, I think you have just struck on the very reason for the existence of the UDSF- it's a 3rd party resource that is proving very popular (we have put an end to the attacks, and hopefully we are up now for the long term).

These same arguments apply to us as a resource, and there is no way in hell that you can make the user base ONLY use one area of documentation - I know as a user myself that I often won't take just one documents word that the method described absolutely works, and will also Google for other documentation that supports the method described.

It's bad practice as an experienced linux user to take one authors word as the absolute way a problem should be solved. Most things in Linux have more than one approach, and thus, in a way, the more documentation there is that can be seen by the search engine spiders (now **THATS** interesting...help.ubuntu.com does not spring up on the list of initial hits for problems with ubuntu, but the forums **DO**), the better it is for all of us. 

Having only one place to go for documentation on Ubuntu would be a Very Bad Thing IMO, and 3rd party sources and ideas should be positively encouraged, and I am fairly sure that Mark would back me up on this.

So, we fully back Az on this effort to provide a collaborative area for all the docs and a fun way of possibly voting on the better documentation.

---

### Post by aysiu on 2007-11-06
This approach is more organic and less awkward and forced.

Google didn't organize information for users by forcing website content to fit a certain schema or to cooperate with each other. They took what was there and made it easy for users to find what they're looking for.

Likewise, with documentation, as long as people have easy ways to find things, those things do not all have to be located in one place.

---

### Post by Chrisj303 on 2007-11-06
I think ANYTHING that helps people find the info they need is a good thing.


One of my pet hates with Ubuntu/Linux has been the need to spend a lifetime scouring the net for bits and pieces of information. This *should* sort that out somewhat..

---

### Post by PartisanEntity on 2007-11-06
I think this is an excellent idea.

Some features I would like to see:

Search by tag, keyword, site, ubuntu version
Sort by date, rating, ubuntu version(s)

---

### Post by MetalMusicAddict on 2007-11-07
I'm sorry but I can't help be see this as a fork in the potential resources for documentation.

It is not hard at all to work with the DocTeam and the WIKI to generate documentation.

[LIST]
[*]For DocTeam only info: [https://help.ubuntu.com](https://help.ubuntu.com)
[*]For community info: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[*]For community info coming from the forums: [https://help.ubuntu.com/community/forum](https://help.ubuntu.com/community/forum)
[/LIST]

Now the last 2 are used as peer-review systems to become official documentation. Why create another place that takes away from this effort?

Really, we need to come together more as a community and stop fragmenting things.

az - I would really like to see you become involved in the DocTeam to help address some of your perceived shortcomings of the current system. I'm sure the DocTeam would be welcome for the help. ;)

---

### Post by ubuntu-geek on 2007-11-07
> **az said:**
> Waste of resources or choice?

No matter how good your intentions are, your model will be perceived as a dictatorship.  I doubt that anyone will tell you that to your face because it really isn't arguable.  But people will always prefer to do their own thing.


You got a valid point there az. I think that style of thinking only segments the community farther from the actual goal. In many cases multiple document sites will actually help the new user because more resources will be available potentially describing processes in different ways.

More options are always better. :)

---

### Post by John.Michael.Kane on 2007-11-07
> **ubuntu-geek said:**
> You got a valid point there az. I think that style of thinking only segments the community farther from the actual goal. In many cases multiple document sites will actually help the new user because more resources will be available potentially describing processes in different ways.

More options are always better. :)

Spot on. Why have all your eggs or in this case documents in one basket. 

As to the theory of it being a fork in the potential resources. The same could be said of those who went out and made remixes of Ubuntu. Being those who did so could have easily pooled their resources,and collaborated with the devs to make Ubuntu more universal in what it does etc

---

### Post by compiledkernel on 2007-11-07
I have to aggree with Az here. There are too many sources of viable documentation that exist for Ubuntu itself to actually attempt to contain them all in one centralized area. Rather just give a reference point on where to find it all. 

By the rationale of centralization, then an entire section of the HowToForge should be assimilated. So should the ubuntugeek blog. So should the UDSF.  So should the Ubuntuguide dot org. So should the forums themselves for that matter. While its admireable to have process control over the documentation thats provided (for authenticity as well as proving whatever process it provides actually works and can be supported) its asinine to assume that all forms of documentation should be regulated.

---

### Post by MetalMusicAddict on 2007-11-07
MANY people have expressed their confusion as things are now with our documentation. ie: Why do we have 3 WIKI's for it? Which one is official?

Adding another will just continue the confusion.

In the end, I think its better to work within Ubuntu than outside. Its easier that one might think.

> **az said:**
> What would you think of a site that would be a reference Ubuntu documentation from all the different sources, along with their articles?
This can easily be a WIKI page.

---

### Post by aysiu on 2007-11-07
While I agree that it's impossible to have documentation unified, I also don't know if it's even a goal to strive for.

Some tutorials seek to create understanding. Others are about simply getting things done. Still others want to combine the two. Some are focused on screenshots, others on the terminal. Some tutorials are web pages. Some tutorials are videos.

It's impossible for one set of documentation to address the needs of every type of user. And if it did, the pages would be so long as to be overwhelming.

Show me how to combine into one page all of these tutorials on installing software, and I'll show you what was lost along the way:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.youtube.com/watch?v=bnOFzyf9D0o](http://www.youtube.com/watch?v=bnOFzyf9D0o)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

By aggregating the different documentation into a search/ranking system, however, you at least have one-stop "shopping" for the new user to find everything--even if those sources of documentation are spread out.

---

### Post by compiledkernel on 2007-11-07
But interestingly enough MMA, this isnt about adding ANOTHER wiki, its merely adding a proxy site to point to existing documentation, both official and not. There are a lot of docs out there, some of which arent Official.  

Its easier to work with official? Does Till Brehm work specifically with Ubuntu Proper? Probably not, and id easily point any user to some of his documentation out on HowToForge before Id send them anywhere else.

---

### Post by John.Michael.Kane on 2007-11-07
> **MetalMusicAddict said:**
> MANY people have expressed their confusion as things are now with our documentation. ie: Why do we have 3 WIKI's for it? Which one is official?

Adding another will just continue the confusion.

In the end, I think its better to work within Ubuntu than outside. Its easier that one might think.


This can easily be a WIKI page.

I don't see the many doc's sits as creating confusion. it gives the user a means of verification allowing them to compare what is written by each team, and decide for themselves who is right, and who needs to edit their info.  

The idea of one doc to rule all would mean that the end user has to trust that one team writing the info correctly.

As for working with within Ubuntu or a team is one thing, it's another to work on a project that seems geared toward absolute control, and centralization.


In the end we all want the best for Ubuntu some of us just choose do it differently, and outside it's umbrella.

---

### Post by MetalMusicAddict on 2007-11-07
> **compiledkernel said:**
> But interestingly enough MMA, this isnt about adding ANOTHER wiki, its merely adding a proxy site to point to existing documentation, both official and not.

In my last post I said it can be a simple WIKI page. :)

See, to me its simply about education. "The word" would have to be spread about this "proxy" site right? So why not make it a WIKI page and point people to that?

---

### Post by compiledkernel on 2007-11-07
> **MetalMusicAddict said:**
> In my last post I said it can be a simple WIKI page. :)

See, to me its simply about education. "The word" would have to be spread about this "proxy" site right? So why not make it a WIKI page and point people to that?

That would hinge on the wiki's ability to provide the functionality that Az is talking about. If the wiki could provide such functionality, then I assume it would be a supportable thing. but if the wiki is not capable, then certainly other considerations should/could/would be made.

---

### Post by MetalMusicAddict on 2007-11-07
> **SD-Plissken said:**
> I don't see the many doc's sits as creating confusion. it gives the user a means of verification allowing them to compare what is written by each team, and decide for themselves who is right, and who needs to edit their info.
Sure. This is basically what these forums do. Sad thing is, often there's good HOWTOs that get dumped here and need changes. I only feel about half of the HOWTOs are well maintained by their original maintainers. Having documentation like that moved to a WIKI would solve this as it could then be edited and subject to peer-review. There is already a effort to do this though it has received little attention.  

> The idea of one doc to rule all would mean that the end user has to trust that one team writing the info correctly.
Since anyone can write crackfull documentation a user NEEDS a place they can trust thats subject to review. This is help.ubuntu and the "community" subsection.

It's crazy the amount of supposedly good documentation around just the forums are severely harmful because of instructions to do things as su and such. Things like that need to be freely editable especially when a HOWTO is unmaintained.

> As for working with within Ubuntu or a team is one thing, it's another to work on a project that seems geared toward absolute control, and centralization.
"seems" is the operative word there. And if you're implying that the DocTeam is about "absolute control" I'd say you're making a big assumption. ;)

What's wrong with "centralization"? :)

> In the end we all want the best for Ubuntu some of us just choose do it differently, and outside it's umbrella.
Sure, but realize that this fragmentation also effects us. Choice isn't the end-all-be-all and does negatively effect us as a community.

I think some DocTeam guys should chime in on this so Ill sit back for now. ;)

---

### Post by aysiu on 2007-11-07
Forcing centralization isn't more efficient than organizing decentralization.

If you coerce all documentation writers to work on the same Wiki, you'll spend more energy fighting about how to best represent or organize the information than you'll spend on actually writing the good documentation.

The other problem is licensing. I had someone approach me about moving my Psychocats stuff to the Wiki. I said someone's welcome to do it, and I said it's unofficially the non-commercial share-alike Creative Commons license, and then I was told that it had to be able to be used for commercial purposes in order to be on the Wiki.

Well, I'm sorry, but I don't want my Psychocats documentation being used for commercial purposes. I want it to be free for all users all the time, not included in a Ubuntu book that someone else makes money off of.

Wikipedia is successful because it is a good resource, not because it tries to assimilate all other sources into Wikipedia and disallow their existence outside of Wikipedia. Wikipedia entries, in fact, tend to have a bunch of links to external sources at the end of each article.

If the Ubuntu Wiki is impressive enough, people will naturally be drawn to working on it. Forcing people to work on the same Wiki for documentation is as futile as getting all Linux developers to work on the same "unified Linux distro." Documentation sites, like distros, serve different purposes and different target audiences.

---

### Post by bonzodog on 2007-11-07
> **MetalMusicAddict said:**
> 
Since anyone can write crackfull documentation a user NEEDS a place they can trust thats subject to review. This is help.ubuntu and the "community" subsection.

It's crazy the amount of supposedly good documentation around just the forums are severely harmful because of instructions to do things as su and such. Things like that need to be freely editable especially when a HOWTO is unmaintained.
Oh dear, oh dear. Why not let the users decide what is harmful? Sometimes the alternative 'unapproved' methods work better than the 'official' ones. 
Like I say, you should NEVER trust one source alone for doing something within linux. I ALWAYS look up at least 2 sources, sometimes more. This is now why not every how-to gets moved to the UDSF - we like to review the method used and double check it for usefulness.
Also, it's rude to go fscking with someones work of documentation just because you Do Not Approve of the method suggested like using absolute superuser. If that method works for them, and they wish to tell people how they did it, then let them tell it the way it is. When we move a doc to the UDSF, the only alterations made are grammatical and layout. We NEVER try to change the method the user came up with. 

> 
What's wrong with "centralization"? :)

Sure, but realize that this fragmentation also effects us. Choice isn't the end-all-be-all and does negatively effect us as a community.


No Centralization is Bad Thing IMO. At the risk of repeating myself, the more docs there are about the way somethings work in Ubuntu there are, the better. 
Oh, and while you are at it, can someone suggest to Canonical that they let google into the Ubuntu main servers? 
Yeah its a royal pain in the rear trying to get google to give me results from ubuntu themselves..like it's too much to expect. A lot of people google for solutions to their problems, and the ubuntu.com domain sites NEVER come up as the google spiders appear to be banned from there. Useful, NOT.

Linux NEEDS choice. Get real MMA. You are being immature.
Yeah, I said it, but I have a temper. And you just crossed the line.
I'm sorry, but Ubuntu.com is USELESS as a resource. Yeah totally useless. Don't use it people.

---

### Post by compiledkernel on 2007-11-07
You know, its not really the wiki that is at fault, but searching the wiki , and searching for stuff from the wiki that really bothers out. The UDSF didnt get popular by blocking the google bots (and primarly why a large porition of the UDSF Mediawiki install still remains in Google's cache). 

But I think the concept of total centralization, while admireable for its Quality Assurance concepts , is a fools errand to run on. It wont happen. Users will blog, Users will forum post, Users will post on other resources where the USER feels comfortable to do so, whatever information they see choose fit to express. I dont see how creating a proxy for such information creates any duplication of effort, but rather creates a one stop shop for doc searching. 

Bonzodog is right, the Google think always annoys me. 

Searching for LDAP ubuntu breeds A forums post, a vulnerability report, and some other stuff. The actualy wiki link to the LDAP howto off of the help.ubuntu.com site doesnt show up until about page 4. That needs to be fixed, or the need to search for documentation needs to become more clear or in another form.

---

### Post by az on 2007-11-07
> **MetalMusicAddict said:**
> I'm sorry but I can't help be see this as a fork in the potential resources for documentation.

It is not hard at all to work with the DocTeam and the WIKI to generate documentation.

[LIST]
[*]For DocTeam only info: [https://help.ubuntu.com](https://help.ubuntu.com)
[*]For community info: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[*]For community info coming from the forums: [https://help.ubuntu.com/community/forum](https://help.ubuntu.com/community/forum)
[/LIST]

Now the last 2 are used as peer-review systems to become official documentation. Why create another place that takes away from this effort?

Really, we need to come together more as a community and stop fragmenting things.

The world is not perfect.  There is fragmentation.  People who blog a helpful idea instead of contributing it to the official documentation are not going to stop.  Sure, the best thing for everyone would be if they took the extra few minutes to get more involved, but that ain't gonna happen.

Shunning them doesn't help.

A crazy idea is to just give up.  Suddenly, give every single little scrap of Ubuntu-related documentation the thumbs-up.  You instantly eliminate fragmentation and gain a few hundred people who are helping out with documentation.

This idea is exactly what you propose - for all the different efforts to come together as a community.  It's just a different perspective.

> **MetalMusicAddict said:**
> 
az - I would really like to see you become involved in the DocTeam to help address some of your perceived shortcomings of the current system. I'm sure the DocTeam would be welcome for the help. ;)

I have been subscribed to the docteam mailing list since may 2005.  I'm also a contributer to the wiki.  I think there are a number of pages of which I am the sole subscriber.  I like the style guide and I try to stick to is as much as possible.

AFAIK, this topic has been done to death in the early days of the docteam.  I don't know of anyone who had every tried to make a proof-of-concept, so I did.

> **MetalMusicAddict said:**
> 
In the end, I think its better to work within Ubuntu than outside. Its easier that one might think.


This can easily be a WIKI page.

I used to say the same thing.  I have been (and still am) a really big fan of the wiki.  And sure, all this could be one big wiki page.  And that would probably suit me just fine.

The problem is, a lot of people wouldn't feel the same way.

How popular would Digg be if it were just a wiki page?

> **aysiu said:**
> 
By aggregating the different documentation into a search/ranking system, however, you at least have one-stop "shopping" for the new user to find everything--even if those sources of documentation are spread out.

And nothing is there to prevent a "seal-of-approval" or a "preferred" tag to be used.

> **MetalMusicAddict said:**
> In my last post I said it can be a simple WIKI page. :)

See, to me its simply about education. "The word" would have to be spread about this "proxy" site right? So why not make it a WIKI page and point people to that?

MoinMoin, wikimedia, a CMS, who cares?  How about we use whatever works best?  Does a wiki page best serve the purpose?

> **MetalMusicAddict said:**
> Sure. This is basically what these forums do. Sad thing is, often there's good HOWTOs that get dumped here and need changes. I only feel about half of the HOWTOs are well maintained by their original maintainers. Having documentation like that moved to a WIKI would solve this as it could then be edited and subject to peer-review. There is already a effort to do this though it has received little attention.  


Since anyone can write crackfull documentation a user NEEDS a place they can trust thats subject to review. This is help.ubuntu and the "community" subsection.

It's crazy the amount of supposedly good documentation around just the forums are severely harmful because of instructions to do things as su and such. Things like that need to be freely editable especially when a HOWTO is unmaintained.

Then those unmaintained docs would sink to the bottom of the pile, to seen less than the better, more complete, and therefore more popular ones which would "bubble up" to the top of this aggregator.

Maybe, by putting the official docs head-to-head with some third-party docs, that would improve their popularity, or at least point out the reasons for which they are less popular.

> **MetalMusicAddict said:**
> 

I think some DocTeam guys should chime in on this so Ill sit back for now. ;)

I would certainly hope the docteam doesn't deem this idea undesirable.  I really find it hard to believe that this would promote anything other than making all of the Ubuntu documentation (official as well as unofficial) easier to find.

> **aysiu said:**
> 
Well, I'm sorry, but I don't want my Psychocats documentation being used for commercial purposes. I want it to be free for all users all the time, not included in a Ubuntu book that someone else makes money off of.


Although I disagree with the concept of non-commercial because it's too vague and based on assumptions that are generally not true, you bring up an excellent point;  that's a good reason for some people to want to avoid contributing to the wiki.

---

### Post by maybeway36 on 2007-11-07
Why not just use an existing site, like thelinuxvault.org?

---

### Post by az on 2007-11-07
> **bonzodog said:**
> 
I'm sorry, but Ubuntu.com is USELESS as a resource. Yeah totally useless. Don't use it people.

That's a little harsh.  The official wiki is my preference, but it clearly isn't everyone's.  Let's just leave it at that...

---

### Post by MetalMusicAddict on 2007-11-07
> **bonzodog said:**
> Linux NEEDS choice. Get real MMA. You are being immature.
Yeah, I said it, but I have a temper. And you just crossed the line.

LOL! Thanx for the giggle. ;)

az, Thanks for dealing with a (kinda) opposing view in a "mature" manner. ;)

There are MANY issues surrounding documentation that need addressed. I really wished we had you at UDS. :)

---

### Post by 23meg on 2007-11-07
[QUOTE=bonzodog]Why not let the users decide what is harmful?[/QUOTE]

Can they, in all cases, without being harmed? If the user needs to get harmed first in order to understand that a particular source of documentation is harmful, is that a good way to do documentation? I don't think so, especially considering Ubuntu's target audience.

"Let the users decide" shouldn't be used as an apology for mediocre work, not just in documentation. Don't get me wrong; I'm not saying it is here; just that it's a pitfall that should be avoided.

---

### Post by aysiu on 2007-11-07
Perhaps bonzodog isn't phrasing it correctly, but if you check two or three sources, and they all give similar instructions, those instructions are probably standard. If you notice discrepancies, that may raise enough of a red flag for you to check the instructions with some forum members to see what might be the best approach.

---

### Post by p_quarles on 2007-11-07
> **23meg said:**
> "Let the users decide" shouldn't be used as an apology for mediocre work, not just in documentation. Don't get me wrong; I'm not saying it is here; just that it's a pitfall that should be avoided.
Agreed. And one of the nice things about the forums and the wikis is that harmful instructions can easily be moderated. 

As others have pointed out, though, it's impossible to stop people from posting bad guidance on the internet. From my perspective, I think a <web2.0>"crowd sourced"</web2.0> (ick) guide to online documentation would be very useful. I frequently point people I'm attempting to help to online tutorials -- some on the wikis, some at HowToForge, and others on personal web sites. I do my best to verify that the instructions are good, but since my knowledge is limited, having a central place where I can find ratings and comments on these instructions would be a great thing.

---

### Post by az on 2007-11-07
[QUOTE=PartisanEntity;3718527
Some features I would like to see:

Search by tag, keyword, site, ubuntu version
Sort by date, rating, ubuntu version(s)[/QUOTE]

Tags are tedious for users to enter when they submit an item.  Do you have any examples of sites that make this easy?

Searches and sorting are easy to implement in Drupal.

If anyone has any other ideas, please let me know.

---

### Post by PartisanEntity on 2007-11-08
> **az said:**
> Tags are tedious for users to enter when they submit an item.  Do you have any examples of sites that make this easy?

Searches and sorting are easy to implement in Drupal.

If anyone has any other ideas, please let me know.

I don't think tags are tedious to enter. The latest version of Wordpress uses tags, and using a plugin you can select tags from a drop down list.

---

### Post by az on 2007-11-09
> **PartisanEntity said:**
> I don't think tags are tedious to enter. The latest version of Wordpress uses tags, and using a plugin you can select tags from a drop down list.

In Drupal, tags are handled using taxonomy.  In Wordpress, if no tags fit the topic, is it easy to add a new tag on-the-fly?

Also, other features I am looking into:

Content Recommendation Engine
[http://drupal.org/project/cre](http://drupal.org/project/cre)

Drupalit (like digg)
[http://drupal.org/project/drupalit](http://drupal.org/project/drupalit)

Hall of fame:
[http://drupal.org/project/hof](http://drupal.org/project/hof)

Metrics:
[http://drupal.org/project/metrics](http://drupal.org/project/metrics)

and
Smackdown (for head-to-head comparisons between two items) (heh heh)
[http://drupal.org/project/smackdown](http://drupal.org/project/smackdown)


Any help/ideas/experience is appreciated.

---

### Post by compiledkernel on 2007-11-09
Hmmm. 

The Drupal mods look good. Those would seem to provide the needed input and output results to achieve the specific end. 

[Pligg]("http://www.pligg.com/") is the only relatively decent Digg clone I know of, and after looking at its code, it appears to be a bit messy. Im not sure how implementation would work for something like this.

---

### Post by Derek Djons on 2007-11-09
It's not a bad idea at all. You should maybe consider to make it as newbie-proof as possible. The experienced users usually find their sources quickly because of IRC / Forums. But for starters the problem lies in knowing what to ask or where to search.

Especially with the help of the readers / visitors themselves a rating system would work splendid. The same goes for submitting links, information and misc.

You might want to think about how to set something up like this. I can imagine that the easiest step would be for every user to be able and submit content / info him or herself. Since people can be very unclear the content on the site can transform into understandable linking and redirecting. In my opinion a team of experienced moderators should be reviewing submitted information, renaming the titles, reviewing the correctness etc. before it gets online.

---

### Post by az on 2007-11-09
> **Derek Djons said:**
>  In my opinion a team of experienced moderators should be reviewing submitted information, renaming the titles, reviewing the correctness etc. before it gets online.

I would be more of a fan of almost no restrictions.  Wide open - obviously with the ability to easily revert changes if someone wanted to deface an item.  That's the best way to get the community involved;   keep the bar really low and make it easy for someone to jump in.

---

### Post by aysiu on 2007-11-09
I think the rating process would automatically weed out incorrect information, for the most part.

If a tutorial borks your system, it's less likely to rise to the top.

---

### Post by Griffiss on 2007-11-09
I like this idea. I don't see how it would compete with the ubuntu.com wiki any more than, say, the forum competes with it - presumably if a piece of documentation on the official pages is good then it will be accessible from this portal.

The above analogies between software and documentation in being closed- and open-cource made me think of the repos - perhaps you could introduce a broad distinction into:

i) 'canonical' material that is moderated/peer-reviewed by experts (analogous to 'main' repo), 

ii) a looser, more comprehensive community-generated section like wikis or the forums (universe), 

iii) as well as the panoply of third-party 'closed-source' (i.e. non user-editable) docs (restricted/multiverse)

You can extend the analogy with the repos by thinking about a dynamic where material eventually flows from category iii to ii to i.

Another thing that I think would be useful to a resource like this is if you could have the option to browse it through a hierarchical structure determined by the topic in which someone is looking for help. So you would have broad divisions similar to the forum's main support catergories, but then a couple categorised levels below that where someone could 'zoom in' more specifically on the problem they're having.

---

### Post by HermanAB on 2007-11-09
So, what is wrong with [http://www.tldp.org](http://www.tldp.org) ???

---

### Post by aysiu on 2007-11-09
> **HermanAB said:**
> So, what is wrong with [http://www.tldp.org](http://www.tldp.org) ???
Nothing's wrong with it.

If this project takes off successfully, TLDP tutorials will be included as well.

---

### Post by az on 2007-11-09
> **Griffiss said:**
> 
Another thing that I think would be useful to a resource like this is if you could have the option to browse it through a hierarchical structure determined by the topic in which someone is looking for help. So you would have broad divisions similar to the forum's main support catergories, but then a couple categorised levels below that where someone could 'zoom in' more specifically on the problem they're having.

It's a "tags" versus "advanced search" problem.  I'll use whatever works best.


I'm still looking for an exciting name for this project... Anyone?

I got permission to use the ubuntu-rescue-remix domain name after discussing it with the Canonical Trademark people.  I am in the process of doign that for this project.   Once I get the trademak people's okay, I will register the domain name and put the site up.

---

### Post by aysiu on 2007-11-09
> **az said:**
> 
I'm still looking for an exciting name for this project... Anyone? How about UbuntuDoc?

---

### Post by compiledkernel on 2007-11-09
how about The U List, dont get on the A List, get on the U List.

---

### Post by aysiu on 2007-11-09
> **compiledkernel said:**
> how about The U List, dont get on the A List, get on the U List.
That's cool too.

Or maybe *UDocFind*

---

### Post by Griffiss on 2007-11-09
Docubuntu?

Ubuntupedia?

Howbuntu?!

Howtubuntu?!!!

Of these Ubuntupedia was my favourite, but on googling it seems there's already a [Portuguese]("http://ubuntupedia.info/index.php/Página_principal") Ubuntu wiki called this.

---

### Post by SpiritIsReality on 2007-11-11
thankyou all (that's not a name suggestion)

---

### Post by az on 2007-11-12
> **compiledkernel said:**
> how about The U List, dont get on the A List, get on the U List.

Already taken.

> **aysiu said:**
> That's cool too.

Or maybe *UDocFind*

Too Dr. Who.

> **Griffiss said:**
> Docubuntu?

Ubuntupedia?

Howbuntu?!

Howtubuntu?!!!

Of these Ubuntupedia was my favourite, but on googling it seems there's already a [Portuguese]("http://ubuntupedia.info/index.php/Página_principal") Ubuntu wiki called this.

*buntu domain names are no longer permitted by the most recent version of the Ubuntu Trademark.  I can understand that.  I've had it up the Whazzoobuntu with creative spins on "Ubuntu".

What about all-ubuntu-docs.org?

---

### Post by John.Michael.Kane on 2007-11-12
> **az said:**
> Already taken.



Too Dr. Who.



*buntu domain names are no longer permitted by the most recent version of the Ubuntu Trademark.  I can understand that.  I've had it up the Whazzoobuntu with creative spins on "Ubuntu".

What about all-ubuntu-docs.org?

az instead of making it distro specific why not a universal name something like univerisal-docs.org, As you are bound to have docs listed that are compatible with distro's other than Ubuntu.

---

### Post by maybeway36 on 2007-11-12
something like [http://www.thelinuxvault.net/]("http://www.thelinuxvault.net/")?

---

### Post by aysiu on 2007-11-12
> **maybeway36 said:**
> something like [http://www.thelinuxvault.net/]("http://www.thelinuxvault.net/")?
Not if I understand it correctly.

This site wouldn't actually *host* documentation but would act a bit like a search engine, news site, or directory.

So instead of competing with other documentation sites, it would aggregate them and allow people to browse through links and ratings of available documentation.

---

### Post by az on 2007-11-12
> **SD-Plissken said:**
> az instead of making it distro specific why not a universal name something like univerisal-docs.org, As you are bound to have docs listed that are compatible with distro's other than Ubuntu.

For a couple of reasons.  
1.  The Ubuntu community is relatively cohesive.  The aims of the distro appeal to a large number of users with a relatively small focus (a friendly-to-use free-libre desktop).  That being said, the documentation reflects that and I think a project like this would suit it perfectly.

I think if the goal was too broad, the project wouldn't work.

2.  I think the Ubuntu community needs this.  I think the attitude of "us" and "them" in reference to official documentation versus third-party documentation efforts is specific to the Ubuntu community.  And that's the "problem" I want to address.  

If it can also apply to other distros, that's great.  Maybe someone else would like to take up such a project.  I'm just not interested.

3.  I don't know much about other distros and what their documentation challenges are.  I wouldn't presume to offer them a solution for a problem I don't know anything about.

> **maybeway36 said:**
> something like [http://www.thelinuxvault.net/]("http://www.thelinuxvault.net/")?

No.  Not at all.  Something more like digg but for documentation.

---

### Post by John.Michael.Kane on 2007-11-12
az Then you will need to make it known that you will only accept documentation that is for Ubuntu only. 

You will also have to make it known that if the info is cross compatible that the doc writer or link poster will have to re-post that info on the respective distro sites that it works with.

I also don't see how this us vs them theory is addressed with your idea. You make it so that the info is universal for Ubuntu, and cut out helping any other distros. I thought it was about sharing information. It seems more about control, and consolidation.

In any case hope the plan works for you.

---

### Post by aysiu on 2007-11-12
I don't know if I'm a fan of the idea of making it Ubuntu only. We could just start with Ubuntu documentation, and then if documentation that isn't Ubuntu-specific pops up, we could always tag those as being something else (similar to how the Ubuntu forums are focused on Ubuntu but have an Other OS Talk section).

If there are tutorials that are distro-generic, that'd be nice to be able to tag as well (installing themes in Gnome is the same for all distros, as far as I know, but installing applications is not).

---

### Post by az on 2007-11-12
> **SD-Plissken said:**
> az Then you will need to make it known that you will only accept documentation that is for Ubuntu only. .

No.  I won't.  I certainly would not want documentation that works on many distros to be refused!  That would be ridiculous.  What sense is there in that?

What I would like to achieve simply has a much more narrow focus than the ensemble of all GNU/Linux documentation.  I think aiming for that (certainly at this stage) is not realistic.

I don't have to be exclusionary to have smaller goals.  Is it exclusionary of your town's phone book to not list numbers from all telephone subscribers around the world?  Does that prevent people who live outside of your town to phone those numbers?

> **SD-Plissken said:**
> 
You will also have to make it known that if the info is cross compatible that the doc writer or link poster will have to re-post that info on the respective distro sites that it works with.


I don't think you understand what I want to do.  There will not be any documentation on this site.  Only links with associated tags, rating and popularity.  If someone writes a text on their blog and someone else finds it relevant to Ubuntu, they can add that blog entry's link to this site.  Nobody has to re-post anything, since this has nothing to do with the original article.  

> **SD-Plissken said:**
> 
I also don't see how this us vs them theory is addressed with your idea. You make it so that the info is universal for Ubuntu, and cut out helping any other distros. I thought it was about sharing information. It seems more about control, and consolidation.

In any case hope the plan works for you.

I guess I want to start by taking the first step.  If this is a success and someone wants to scale this to include all FLOSS, I would be glad if they did.  

I would be thrilled if this took off and a community built around the project so that I wouldn't have to do anything.  I certainly don't want to do this to control anything.


> **aysiu said:**
> I don't know if I'm a fan of the idea of making it Ubuntu only. We could just start with Ubuntu documentation, and then if documentation that isn't Ubuntu-specific pops up, we could always tag those as being something else (similar to how the Ubuntu forums are focused on Ubuntu but have an Other OS Talk section).

If there are tutorials that are distro-generic, that'd be nice to be able to tag as well (installing themes in Gnome is the same for all distros, as far as I know, but installing applications is not).

Sure.  I'm working at getting this off the ground at this stage.  As these kinds of needs come up, I (and whomever else wants to help) will work to implement these features.

---

### Post by SpiritIsReality on 2007-11-12
[http://ubuntuforums.org/showthread.php?t=484846&page=8](http://ubuntuforums.org/showthread.php?t=484846&page=8)

---

### Post by az on 2007-12-12
This just in:

[I]Hi Andrew,

Thanks for your email and apologies for my late response.

As a non-commercial project we don't have a problem with you using a 
second level.org domain name.

Kind regards,
Michelle
[/I]

---

### Post by forrestcupp on 2007-12-12
The good thing is that everyone can do what they want.  If az wants to make a site like this, he can.  If anyone wants to use az's site, they can.  If someone else wants to promote the official wiki, they can do that.  If someone wants to use the official resources for help, they can do that.  If someone wants to use az's site to find help that includes the official resources *and* other good sources, they have the right to do that.

You will never get everyone to want the same thing.

Just like it's been said lots of times before, you can't make everyone try to get their tutorials, etc., in the official wiki.  Why not have a place that it is easily accessible.

Maybe one thing you could do is have some way to show that an entry is from the official support.

Congratulations on getting a second level domain name.  I think that whatever you name it should not just be exciting, but definitely reflect the purpose of the site.

---

### Post by zesty on 2007-12-12
I'm sorry, I didn't read all of the posts in this thread, but I would like to offer my noob opinion.

My problem has not been finding information.  In fact, there's a ton of information to be found on any subject by using simple google searches.

My problem has been trying to find information that is still relevant.  For instance: Is this partitioning guide written in 2006 still applicable?  Well, that was just 2 years ago, but turns out things have changed.

The rating system would be great.  I think that it should somehow be time sensitive though.  A 10/10 rating given to an article written in 2005 perhaps shouldn't be as prominent as a 8/10 rating given to an article written a month ago.  At the same time, if that old article still is the best, there should be some mechanism to keep it on top.

Could I be more vague?  I hope you get my point, best of luck, and thanks!

---

### Post by aysiu on 2007-12-12
Well, I guess the idea is that people would keep rating... the ratings would never stop... so if a guide from 2004 is still relevant, it would keep getting great ratings and more votes. If the guide from 2006 is no longer relevant, it will not keep getting votes and will eventually work its way down to the middle (probably not the bottom).

Also, depending on how sophisticated this site is, you may be able to mark a guide as outdated or contact the author to update it.

---

### Post by az on 2007-12-14
> **aysiu said:**
> Well, I guess the idea is that people would keep rating... the ratings would never stop... so if a guide from 2004 is still relevant, it would keep getting great ratings and more votes. If the guide from 2006 is no longer relevant, it will not keep getting votes and will eventually work its way down to the middle (probably not the bottom)..


Yes, that's the advantage of combining a documentation index with a popularity contest.

> **aysiu said:**
> 

Also, depending on how sophisticated this site is, you may be able to mark a guide as outdated or contact the author to update it.


Free tagging, baby!  Articles can be marked in any way by anybody.  You will be able to search and sort by those tags.


So, I registred the domain:

[http://ubuntuknowledge.org](http://ubuntuknowledge.org)


It is BETA right now....  Any help is appreciated.

---

### Post by Frak on 2007-12-14
> **az said:**
> Yes, that's the advantage of combining a documentation index with a popularity contest.




Free tagging, baby!  Articles can be marked in any way by anybody.  You will be able to search and sort by those tags.


So, I registred the domain:

[http://ubuntuknowledge.org](http://ubuntuknowledge.org)


It is BETA right now....  Any help is appreciated.
I like the site, I'm submitting an article right now. :)

---

### Post by information_entropy on 2007-12-14
az:

Very good idea, I give your concept 10 stars,
And your implementation 9.5 stars,
(because nothing is perfect):p

This is really a very useful addition to the widely
scattered collection of Ubuntu documentation.

Good luck with this site.

---

### Post by p_quarles on 2007-12-15
@az: I've tried to add an article twice now, and both times I got a "success" message. But, it doesn't show up. :(

---

### Post by az on 2007-12-15
> **information_entropy said:**
> 
Very good idea, I give your concept 10 stars,
And your implementation 9.5 stars,


Actually, I give the implementation a two.  It's really at a proof-of-concept stage right now.  

I am only using Drupal modules with no custom code.  

*Release early, release often *

Any help is welcome...
> **p_quarles said:**
> @az: I've tried to add an article twice now, and both times I got a "success" message. But, it doesn't show up. :(

Sorry about that.  Everything works fine for me because but when I clear my cookies, everything is screwy, with lots of denied access.  I will try to fix this ASAP.

EDIT:  I rebuilt the content permissions and everything should be working now....  Thanks.

---

### Post by p_quarles on 2007-12-16
Works swimmingly now. I've added three articles, and a link to my sig. I really like this idea, and hope it gets off the ground.

EDIT: One thing I just noticed is that every time I view a thread, its hit count goes up. This could lead to bot-spamming. Is it possible to change the hit count to unique visitors?

---

### Post by psyopper on 2007-12-16
How about reference.ubuntu.com.

More importantly than the name is the content management system. It seems that the vast majority of the information that the Ubuntu community references is actually from this forum. A possible solution is a plug-in for the v-bulliten system with an actual usable search. 

It's easier to use Google to search this forum than it is to use the built in search function.

---

### Post by p_quarles on 2008-01-09
I've noticed that the sorting feature is currently not working. In other words, it automatically sorts articles/sites by the number of hits the page has received. Clicking on different columns *indicates* that it attempts to re-sort by name or rating, but the actual order doesn't change.

---

### Post by az on 2008-01-09
> **p_quarles said:**
> I've noticed that the sorting feature is currently not working. In other words, it automatically sorts articles/sites by the number of hits the page has received. Clicking on different columns *indicates* that it attempts to re-sort by name or rating, but the actual order doesn't change.

Thanks.  I will get to work on fixing that.

---

### Post by az on 2008-01-09
Fixed.

Any suggestions are welcome!

---

### Post by p_quarles on 2008-01-09
> **az said:**
> Fixed.

Any suggestions are welcome!
Sweet. 

May I suggest that the Rating column be made the default sorting criterion? Some of the pages have a decent number of hits, but almost no one is voting. I would guess that people may be more motivated to do so if it affects the page's default position.

---

