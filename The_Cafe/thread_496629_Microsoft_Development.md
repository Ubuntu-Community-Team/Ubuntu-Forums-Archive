---
title: "Microsoft Development"
date: 2007-07-09
forum: The Cafe
---

### Post by LaRoza on 2007-07-09
Here is an interesting article about Windows development. I always wondered how Windows was coded. (Being a programmer, I was curious).

[http://moishelettvin.blogspot.com/2006/11/windows-shutdown-crapfest.html](http://moishelettvin.blogspot.com/2006/11/windows-shutdown-crapfest.html)

---

### Post by 23meg on 2007-07-20
Interesting read, thanks. Next time someone comes up with the "open source is a forking mess / too many blahblahs" line, I'll give them this. 

Somewhere in [his Google Tech Talk on git]("http://www.youtube.com/watch?v=4XpnKHJAok8"), Linus Torvalds describes his ideal "network of trust" mode of collaboration that distributed revision control systems allow, which unsurprisingly is the polar opposite of how things work at Microsoft. (emphasis mine)

[QUOTE=Moishe Lettvin]In small programming projects, there's a central repository of code. Builds are produced, generally daily, from this central repository. Programmers add their changes to this central repository as they go, so the daily build is a pretty good snapshot of the current state of the product.

In Windows, **this model breaks down simply because there are far too many developers to access one central repository**. So Windows has a tree of repositories: developers check in to the nodes, and periodically the changes in the nodes are integrated up one level in the hierarchy. At a different periodicity, changes are integrated down the tree from the root to the nodes. In Windows, the node I was working on was 4 levels removed from the root. The periodicity of integration decayed exponentially and unpredictably as you approached the root so it ended up that it took between 1 and 3 months for my code to get to the root node, and some multiple of that for it to reach the other nodes. It should be noted too that the only common ancestor that my team, the shell team, and the kernel team shared was the root.

So in addition to the above problems with decision-making, **each team had no idea what the other team was actually doing until it had been done for weeks**.[/QUOTE]

---

### Post by a12ctic on 2007-07-20
Is this even a remote surprise? Do you realize that windows vista is a UI lift on XP with a few more major changes that look several years to develop?

---

### Post by 23meg on 2007-07-20
I don't know, since I haven't used Vista (no XP either in a year or so), but the model described here sounds very much like the "stupid" models that Linus describes in that talk.

---

### Post by Tundro Walker on 2007-07-20
That quoted text almost sounds verbatim like the [blogged complaint]("http://moishelettvin.blogspot.com/2006/11/windows-shutdown-crapfest.html") one of the Vista Shutdown/Logoff UI programmers had.  He talked about how nightmarish it was to get things done, because it was sometimes weeks before you'd find out your code was broken due to changes up the line.

Tracing the root of the problem, he determined that the huge code trees was an "effect" of a much greater problem "cause"...that being the over-administration of everything.  Layers and layers of management want to stick their nose into everything, but don't want to take accountability or make firm decisions on things.  So, you have these annoying meetings where more than half the folks in the room shouldn't be there (and folks that should be there aren't allowed to be there lest they say something that, God Forbid,  might actually solve a problem, get something done, or hold someone to something.)

Joel Spolsky (his article linked from the dev's blog) was a bit harsh on feature the dev worked on.  But, I think Joel remembers the days when he was at MS, when Bill would come in and review all projects, make firm decisions, and one person, usually the team lead of the project, was basically "God", and had firm say-so on things.  That's not the case anymore, and Microsoft gets snowballed in over-managezation.

---

### Post by @trophy on 2007-07-20
> **23meg said:**
> I don't know, since I haven't used Vista (no XP either in a year or so), but the model described here sounds very much like the "stupid" models that Linus describes in that talk.

What talk?  Are there MP3's/vids available?

---

### Post by bonzodog on 2007-07-20
23meg did already provide a link, but here you go:

Linus Torvalds talks about the GIT development model:

[http://www.youtube.com/watch?v=4XpnKHJAok8](http://www.youtube.com/watch?v=4XpnKHJAok8)

---

### Post by 23meg on 2007-07-20
[QUOTE=Tundro Walker]That quoted text almost sounds verbatim like the blogged complaint one of the Vista Shutdown/Logoff UI programmers had. [/QUOTE]

Perhaps because that's where I quoted it from :) The OP linked to that article, as you can see in the first post.

---

### Post by lecanardzero on 2007-07-21
I used to work there, so I know exactly why and how this happens.  The "wheel" for the lack of a better term gets re-invented soooo many times it's pretty ridiculous.  But hey, they still make money, and that's all the counts.

---

### Post by DoctorMO on 2007-07-21
> But hey, they still make money, and that's all the counts.

Totally **** backwards thinking; you do NOT earn money for the sake of it, you earn money so that you can put that social value into production to get something useful done for either yourself or others. a large accumulation of money simply warps society and devalues work as well as increasing inflation. trickle down be damned. Microsoft need to start providing users with solutions again instead of barriers if they want to enter the market a new.

---

### Post by dptxp on 2007-07-21
I always wonder how Windows works. I am surprised that it still works. With 50% of code as patches, it works. With 50% of rest as error messages, it works. With so little useful code, it works.

---

### Post by MetalOverlord on 2007-07-23
> So, you have these annoying meetings where more than half the folks in the room shouldn't be there (and folks that should be there aren't allowed to be there lest they say something that, God Forbid, might actually solve a problem, get something done, or hold someone to something.)

I used to work for a large insurance company. At one point in my career there I was the lead engineer for a group of products used company-wide by a number of application development teams. On one memorable occasion I found out that a meeting had been held involving my supervisor and a group of application reps regarding an upgrade. My manager had *NO* knowledge of the product beyond it's name and a 2 sentence description of what it did. The purpose of the meeting was to inform the application reps about changes necessary to their apps for the upgrade based on a memo I wrote. I was not invited to the meeting and found out about it a day later only when one of the app reps at the meeting asked why I wasn't there. I asked my supervisor why I wasn't part of the meeting. I was told, and I quote, "because you would've bogged the meeting down with technical detail." The particular upgrade involved changes to compile libraries, compile and run-time option changes, changes to source code, fairly technical stuff in nature. Most of the reps ended up emailing or calling me because my manager couldn't answer their questions.

I guess that's the way large corporations work. We don't want them darn techies around to muddie things up. More accurately, I don't want anyone at a meeting that knows more than I do about a particular subject lest I look stupid.

That kind of stuff is why I left IT and bought a restaurant.

---

