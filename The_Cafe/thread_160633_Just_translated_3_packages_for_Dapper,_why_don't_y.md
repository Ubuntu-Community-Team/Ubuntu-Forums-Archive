---
title: "Just translated 3 packages for Dapper, why don't you do the same?"
date: 2006-04-15
forum: The Cafe
---

### Post by mostwanted on 2006-04-15
If you know other languages besides English obviously ;)

Translations are always needed and it's really easy to do. I just translated the following modules into Danish: about-ubuntu, preface and website-index which are the  main "about"-pages in Ubuntu. Granted, two of them were small packages, but important nonetheless! Currently getting ready to help translating the desktop guide and Inkscape into Danish.

Why don't we all make an effort in translating the most important applications completely into our native tongues?

If you want to translate the about pages for Dapper they're located here: [https://launchpad.net/distros/ubuntu/dapper/+source/ubuntu-docs/+translations](https://launchpad.net/distros/ubuntu/dapper/+source/ubuntu-docs/+translations)

Other packages can be translated on the same website, you just need to register with launchpad (which you'll have done if you've ever ordered CDs at shipit).

---

### Post by Lovechild on 2006-04-15
Please don't ever use Rosetta to translate, work is not merged upstream (thus it's wasteful) also there are language teams out there and if you do not adhere to their standards you are introducing inconsistencies that confuse the users.

I'm a translator (Danish team) myself and I strongly recommend translation work as an FOSS entry level way of helping out - it's fun, and useful - but please don't use Rosetta, work with your translation team instead - I beg you.

---

### Post by mostwanted on 2006-04-15
Well well, I don't think there are any application developers who mind (eller, undskyld mig udtrykket, får ondt i røven af) the users translating the Ubuntu documentation into their native languages.

I was under the impression that the Ubuntu translations were shared with all of Debian derived distributions in the launchpad system...? Isn't that good enough? I'm not going to track down individual free software projects for translation when a working system such as Rosetta exists.

---

### Post by Lovechild on 2006-04-15
[www.dansk-gruppen.dk](www.dansk-gruppen.dk) is the home for the danish team.

This is a matter of coordinating application translation in the right place, and launchpad currently isn't it.

---

### Post by mostwanted on 2006-04-15
Regardless of what policies anyone else might have about translations, the ubuntu-docs package I linked to in my first post is not subject to outside translations, so if you want to make a difference, do translate it :)

---

### Post by fuscia on 2006-04-15
apperday rakeday (that's as far as i've gotten.)

---

### Post by dolny on 2006-04-15
How can I help translating somthing to polish?

---

### Post by mostwanted on 2006-04-15
[QUOTE=dolny]How can I help translating somthing to polish?[/QUOTE]

Look at the link in my first post.

---

### Post by stoeptegel on 2006-04-15
I translated ktorrent1.2 last month, but not in launchpad but for kdei18n in general using kbabel. But i'll dive into some dutch docs, thanks for pointing this out. :)

---

### Post by Mathias-K on 2006-04-15
I have translated around 500 karma worth of danish via Launchpad and Rosetta, mainly for Breezy and Dapper. I think it is a very easy, user friendly and beautiful system to work with.

[QUOTE=Lovechild]Please don't ever use Rosetta to translate, work is not merged upstream (thus it's wasteful)...[/QUOTE]

The translation goes right into the Ubuntu, Kubuntu, Xubuntu and Edubuntu releases. Debian and Nexenta are on Launchpad too. Mark Shuttleworth has pointed out that the system will be open sourced and thus we could imagine a situation where all major distributions were joined on one platform. That is an ideal I'm more than willing to work towards, an I believe that can be done nicely by translating in Rosetta. 

[QUOTE=Lovechild](...)also there are language teams out there and if you do not adhere to their standards you are introducing inconsistencies that confuse the users.[/QUOTE]

In January and February, I was in contact with the danish language team. I never really got into it, because i found it so confusing and ill organized. Noone ever told me how the translation work is done (a program, by text, on a website?), but perhaps you can shed some light on it?

Also, the danish language group had some an profoundly aggressive attitude towards english tech words. In Denmark, the word "firewall" is common knowledge for almost anyone using computers, yet apparently it has been decided that the term "brandmur" (litteraly "burning wall" in danish) was more appropriate.

I must admit that i started out working on Rosetta to improve the Ubuntu experience. To that end, i was repelled by some of the stances of the translation team.

I'm sorry if anyone was hurt by my honesty. I must admit that i was a bit offended by the post that discouraged people to use what i think is a great tool for translating open source software.

---

### Post by Lovechild on 2006-04-15
[QUOTE=Mathias-K]I have translated around 500 karma worth of danish via Launchpad and Rosetta, mainly for Breezy and Dapper. I think it is a very easy, user friendly and beautiful system to work with.

The translation goes right into the Ubuntu, Kubuntu, Xubuntu and Edubuntu releases. Debian and Nexenta are on Launchpad too. Mark Shuttleworth has pointed out that the system will be open sourced and thus we could imagine a situation where all major distributions were joined on one platform. That is an ideal I'm more than willing to work towards, an I believe that can be done nicely by translating in Rosetta. 

In January and February, I was in contact with the danish language team. I never really got into it, because i found it so confusing and ill organized. Noone ever told me how the translation work is done (a program, by text, on a website?), but perhaps you can shed some light on it?

Also, the danish language group had some an profoundly aggressive attitude towards english tech words. In Denmark, the word "firewall" is common knowledge for almost anyone using computers, yet apparently it has been decided that the term "brandmur" (litteraly "burning wall" in danish) was more appropriate.

I must admit that i started out working on Rosetta to improve the Ubuntu experience. To that end, i was repelled by some of the stances of the translation team.

I'm sorry if anyone was hurt by my honesty. I must admit that i was a bit offended by the post that discouraged people to use what i think is a great tool for translating open source software.[/QUOTE]

Don't get me wrong I'm not insulted by your words, more the fact that you piss on the effort of hundreds of people to make translations consistent without understanding the reasons why we work the way we do.

Rosetta is a decent tool, however the simple fact that work is not peer reviewed and the fact that it benefits only projects registered with Launchpad. 

The danish team works hard to be open, if you or anyone is unhappy with the chosen wording, we hold monthly meetings to discuss such matters amongst other things. We are very open to suggestions, any assertion otherwise is a downright lie. 

We elect certain wordings because:

a) We strive for compliance with the official danish dictionary (if we just translated literally the programs would NOT be able to be used in schools and government for legal reasons).
You would be surprised how big an issue this is and how much work goes into this part of the translation effort.
b) We target a certain audience and we cannot assume prior knowledge of technical terms with roots in English.

Untill Launchpad is open sourced, it will have ZERO adoption outside of Ubuntu related projects. That is the simple fact - no matter Marks promises of an eventual code release. It's either open sourced or it's not and right now it's not.

My main issues with Rosetta:
a) Work has not forced peer review which means consistency and correctness is not ensured.
b) Work is not contributed in anyway upstream to the translation teams.

There is a reason we have translation teams, they solve problems that are not addressed by tools like Rosetta.

Now you asked about tools, personally I use vim because I like to review all strings to catch tiny alterations. However there are fine tools available, I know quite a lot of translators who use the po mode in EMACS, another fine tool is gtranslator. On the website I linked to earlier are a number of guides you can look at, also my blog contains a posting I often link to when newcomers ask questions. 
[http://lovesunix.net/blog/?p=43](http://lovesunix.net/blog/?p=43)

Aside this I am delighted that people are interested in translation work, it's an often underestimated artform and a much needed contribution to FOSS.

---

### Post by zubrug on 2006-04-15
Yikes, I will just keep quiet.
(ignore the "Yikes" if you wish, its not in the dictionary)

---

### Post by Mathias-K on 2006-04-17
[QUOTE=Lovechild]Don't get me wrong I'm not insulted by your words, more the fact that you piss on the effort of hundreds of people to make translations consistent without understanding the reasons why we work the way we do.

Rosetta is a decent tool, however the simple fact that work is not peer reviewed and the fact that it benefits only projects registered with Launchpad. 

The danish team works hard to be open, if you or anyone is unhappy with the chosen wording, we hold monthly meetings to discuss such matters amongst other things. We are very open to suggestions, any assertion otherwise is a downright lie. 

We elect certain wordings because:

a) We strive for compliance with the official danish dictionary (if we just translated literally the programs would NOT be able to be used in schools and government for legal reasons).
You would be surprised how big an issue this is and how much work goes into this part of the translation effort.
b) We target a certain audience and we cannot assume prior knowledge of technical terms with roots in English.

Untill Launchpad is open sourced, it will have ZERO adoption outside of Ubuntu related projects. That is the simple fact - no matter Marks promises of an eventual code release. It's either open sourced or it's not and right now it's not.

My main issues with Rosetta:
a) Work has not forced peer review which means consistency and correctness is not ensured.
b) Work is not contributed in anyway upstream to the translation teams.

There is a reason we have translation teams, they solve problems that are not addressed by tools like Rosetta.

Now you asked about tools, personally I use vim because I like to review all strings to catch tiny alterations. However there are fine tools available, I know quite a lot of translators who use the po mode in EMACS, another fine tool is gtranslator. On the website I linked to earlier are a number of guides you can look at, also my blog contains a posting I often link to when newcomers ask questions. 
[http://lovesunix.net/blog/?p=43](http://lovesunix.net/blog/?p=43)

Aside this I am delighted that people are interested in translation work, it's an often underestimated artform and a much needed contribution to FOSS.[/QUOTE]

Wow. To me, telling people that their efforts and work towards better free software is "pissing on" anyone is showing a major lack of respect towards other people. You might say that as it is right now, Rosetta has not yet become the perfect tool that some believe it will be, but swearing and talking rude to people dissapoints me. 

With all the effort you have made in regard to promoting freedom in computing, why is it so hard to respect the freedom of other persons to see things differently? 

I like Rosetta and the promises that Mark Shuttleworth has given on open sourcing and the whole vision of combining forces across distributions. When i  got to know it, i was not only impressed by the simplicity and ease of the system, but also by the way the system is made:

- People can see the newest work that has been done, and they can review it. I have done that myself, and others moderated some of my work.

- There are no "assigning tasks" between members. There is free cooperation and it is very easy to get started. You don't have to plunge into mailiing lists and 

- There are built in measures for ensuring consistency, for example you can see similar translations from the other translation work. This means that by the effort of a translation team, top quality work can be made - also with the help of bystanders, who just do some junior jobs or repetetive tasks like copying translations.

My impression with the translation work that has been done inside Rosetta and what has been imported from upstream work, some of it from the danish team (maybe even done by you), is that the general quality could be near perfect if the translation team gave Rosetta a chance.

It is posts like the one you made that makes me choose not to translate. It saddens me that such attitudes are found within the open source community.

---

### Post by Lovechild on 2006-04-17
For the _final_ time.. work down in Rosetta is NOT merged upstream, no matter your impression. I have done Rosetta translations in fact I think I was the first guy who signed up on the danish team within Rosetta.

And yes bypassing the translation teams who have after all worked on this for years is pissing on their efforts - it's not done intentionally but I think it's all the same in the end and who suffers... yes the user.

I will restate the issue for the slow ones:

In case of an odd translation, you bet ya there's a reason and not understanding that reason is damaging the work of a bunch of very serious people.

Just walking in off the street and changing stuff without understanding why it is like that in the first place is a BAD idea, in the case of danish and probably other languages this ends up hurting Linux as you piss on the effort to make it compliant with use in places like schools.

Now how do I know this, because I once started out with the same assertion that we could just change the wording to make sense to a technical minded person - and the same issues were explained to me.

It's funny how a distribution that treasures merging with upstream when it comes to code has so little regard for translation merging. 

In the end this means that translations in Ubuntu will be vastly different from everywhere else - and would someone explain to me how that is a good thing?

---

### Post by mostwanted on 2006-04-17
[QUOTE=Lovechild]For the _final_ time.. work down in Rosetta is NOT merged upstream, no matter your impression. I have done Rosetta translations in fact I think I was the first guy who signed up on the danish team within Rosetta.

And yes bypassing the translation teams who have after all worked on this for years is pissing on their efforts - it's not done intentionally but I think it's all the same in the end and who suffers... yes the user.

I will restate the issue for the slow ones:

In case of an odd translation, you bet ya there's a reason and not understanding that reason is damaging the work of a bunch of very serious people.

Just walking in off the street and changing stuff without understanding why it is like that in the first place is a BAD idea, in the case of danish and probably other languages this ends up hurting Linux as you piss on the effort to make it compliant with use in places like schools.

Now how do I know this, because I once started out with the same assertion that we could just change the wording to make sense to a technical minded person - and the same issues were explained to me.

It's funny how a distribution that treasures merging with upstream when it comes to code has so little regard for translation merging. 

In the end this means that translations in Ubuntu will be vastly different from everywhere else - and would someone explain to me how that is a good thing?[/QUOTE]

I'm not going to sign up as an official translator in any case; I'm doing this to help Ubuntu. If you want to use my files upstream you can just use the PO file from Ubuntu, shouldn't be that difficult.

And I don't think the official Danish team is doing *that* good a job anyway. I frequently see compound errors (sammensatte ord) in some of the Danish team translations =/

For example, in a default Ubuntu installation the launcher for Gaim is labeled "Gaim - internet beskeder". There are several mistakes here:

1) first of all, Internet is not capitalised as it should be (the Internet is a name of a specific network)

2) second it should be a compound word. Either Internet should be interpreted as an English word, so it becomes Internet-beskeder or Internet should be considered a Danish word so that it becomes Internetbeskeder (possibly, that last one should be uncapitalised, I'm not sure here).

If the official translations suck, I'm not going to have any problems messing up *their* standards.

---

### Post by Lovechild on 2006-04-17
[QUOTE=mostwanted]I'm not going to sign up as an official translator in any case; I'm doing this to help Ubuntu. If you want to use my files upstream you can just use the PO file from Ubuntu, shouldn't be that difficult.

And I don't think the official Danish team is doing *that* good a job anyway. I frequently see compound errors (sammensatte ord) in some of the Danish team translations =/

For example, in a default Ubuntu installation the launcher for Gaim is labeled "Gaim - internet beskeder". There are several mistakes here:

1) first of all, Internet is not capitalised as it should be (the Internet is a name of a specific network)

2) second it should be a compound word. Either Internet should be interpreted as an English word, so it becomes Internet-beskeder or Internet should be considered a Danish word so that it becomes Internetbeskeder (possibly, that last one should be uncapitalised, I'm not sure here).

If the official translations suck, I'm not going to have any problems messing up *their* standards.[/QUOTE]

Gaim is not maintained by us, the translator who does the majority of the work is a part of the team but he does not submit work for review like the rest of us - in the past 2 years I think I've seen 1 posting on that translation set. This is a problem and I'll see what I can do about addressing it, I don't use Gaim so I honestly haven't done anything except review the changes when they have been submitted. If I have time the coming weeks I'll have a crack at the Gaim2 po file and submit it for review.

So in any case Gaim is a special case, it does not comply fully with our preferred translation list (other programs that aren't currently under that umbrella for various reasons would be Firefox and OpenOffice which like gaim have seperate translation efforts) - not that we claim to be perfect but we do a lot of work to ensure compatability with RO, we also try to get influence on various IT boards that decide wording, hold workshops, etc.

We try very hard to do a good job, if we make mistakes please report them as bugs we are very open, just like the rest of the community surrounding FOSS. This is not a valid reason to play upstream especially in the context of benefiting only one group of people (Ubuntu users in this case).

You are in effect forking the translations, I fail to see the benefit of doing that rather than working with upstream.

I won't go into specifics of compound words but errors do happen we are but human - that is exactly why we need peer reviewing - something Rosetta completely discourages.

---

### Post by Mathias-K on 2006-04-18
[QUOTE=Lovechild]For the _final_ time.. work down in Rosetta is NOT merged upstream, no matter your impression.[/QUOTE]

I am perfectly aware of that. I don't mean to be arrogant, really, but please read my post thoroughly. Launchpad has not yet really realized itself. Don't you think that Shuttleworth would like to merge with upstream when a sizeable part of the translation teams eventually move on to using Rosetta?

[QUOTE=Lovechild]And yes bypassing the translation teams who have after all worked on this for years is pissing on their efforts - it's not done intentionally but I think it's all the same in the end and who suffers... yes the user.[/QUOTE]

Noone is saying that Rosetta has to be used so that the translation teams are bypassed. It is perfectly possible to have a preferred translation policy, the Rosetta system even encourages this.

[QUOTE=Lovechild]I will restate the issue for the slow ones:[/QUOTE]

Are you saying that when people disagree with you, it's automatically because they haven't understood your post? I must ask you, why is it so hard to respect the opinion of others?

[QUOTE=Lovechild]In case of an odd translation, you bet ya there's a reason and not understanding that reason is damaging the work of a bunch of very serious people.

Just walking in off the street and changing stuff without understanding why it is like that in the first place is a BAD idea, in the case of danish and probably other languages this ends up hurting Linux as you piss on the effort to make it compliant with use in places like schools.[/QUOTE]

The difference between Rosetta and what i have learned about the danish team's way of working is that Rosetta is *open* like a Wiki. It shares the same problem of potential vandalism, but there are even better tools in Rosetta to review the changes - not only within a small team, but from a massive number of users.

[QUOTE=Lovechild]Now how do I know this, because I once started out with the same assertion that we could just change the wording to make sense to a technical minded person - and the same issues were explained to me.[/QUOTE]

Everybody in Denmark knows what a firewall is, just like they say "computer" and not "datamat" anymore. I have never seen a school computer that said "brandmur" instead of "firewall", and they weren't removed for being illegal.

[QUOTE=Lovechild]It's funny how a distribution that treasures merging with upstream when it comes to code has so little regard for translation merging. 

In the end this means that translations in Ubuntu will be vastly different from everywhere else - and would someone explain to me how that is a good thing?[/QUOTE]

This is the place where i agree with you. I hope that Launchpad will be open sourced very soon so that also your distribution of choice is supported. In fact i'm thinking about asking Mark Shuttleworth on the matter.

You ask me if forking translations is a good thing. My answer to that is a definite no. That's why i'm not translation in Rosetta until it's open sourced - or at least until all other distros are invited into the system freely. 

My question to you will be if you have considered the idea of the danish translation team commiting itself 100% to Rosetta if it was open sourced. Would the massive amount of peer reviews and the automatic encouragement for consistency not be a good thing?

---

### Post by newbie2 on 2006-04-18
[QUOTE=dolny]How can I help translating somthing to polish?[/QUOTE]
[https://wiki.ubuntu.com/UbuntuPolishTranslators](https://wiki.ubuntu.com/UbuntuPolishTranslators)
[https://launchpad.net/people/ubuntu-l10n-pl](https://launchpad.net/people/ubuntu-l10n-pl)

---

### Post by Lovechild on 2006-04-18
[QUOTE=Mathias-K] Would the massive amount of peer reviews and the automatic encouragement for consistency not be a good thing?[/QUOTE]

That is not for me to decide, I have strong technical issues with Rosetta in it's current form though.

If it was open and it provided us with a means of enforcing peer review, say leaving all translations in a queue untill 2 additional translators verify the correctness of the work. Rosetta does offer some interesting possiblities, one I've cited previously would be merging the official wordlist for danish from SSLUG into the Rosetta system so translators would be able to have live spellchecking of translations and the ability to update the wordlist so users would have a correct wordlist for aspell, etc. 
That would solve real problems and lessen the workload significantly.

Rosetta isn't currently a perfect tool, but I believe it can be made really good - if it was opened and my technical concerns were solved I would definately consider it. I'm still very concerned with vandalism but if we have a work queue and the translation work becomes a meritocracy (meaning to get in you'd have to sign an agreement and be sponsored by an existing member) I believe we can mediate the problems.

But yes - I see no reason to not urge adoptation if the political and techincal issue were addressed and I do believe that a system like Rosetta would bring new blood to the teams, which would be nice - I'm always pleased when I see new faces on our mailing list learning their way around the art, I'm also happy to report that recently we have gained quite a few new members who are all doing fine work.

Back to debating:
You mention common usage vs. official wording - yet you seem completely blissfully ignorant to the fact that if we do not stick to the standard set forth by DSN - in effect we are cutting FOSS out of the race to be used in schools, governments, etc.  That is why we are doing that.. 
Yes it seems somewaht silly that email has to be e-post (or alternatively e-mail which was recently allowed by RO) but that is not up to us to decide if we want to be compliant, the best we can do to ensure this getting a sane solution is lobbying the correct organisations (and this is where having an official translation team comes in handy btw. we do a lot of that kind of legwork - you need structure to do that)

---

### Post by Mathias-K on 2006-04-18
[QUOTE=Lovechild]If it was open and it provided us with a means of enforcing peer review, say leaving all translations in a queue untill 2 additional translators verify the correctness of the work.[/QUOTE]

Well, that could be interesting, but it seems that your current system doesn't provide that feature either. After all that's what's written in your blog:

[QUOTE=Lovechild's blog] This is the single flaw in our model as during hard pressed times for the rest of the team, a translation might go unreviewed for quite some time.[/QUOTE]

Well, that is exactly the situation of Rosetta. You can view the work by date and review any new work - but of course only if you have the time.

[QUOTE=Lovechild]Rosetta does offer some interesting possiblities, one I've cited previously would be merging the official wordlist for danish from SSLUG into the Rosetta system so translators would be able to have live spellchecking of translations and the ability to update the wordlist so users would have a correct wordlist for aspell, etc. 
That would solve real problems and lessen the workload significantly.[/QUOTE]

I agree. This is why I feel that giving Rosetta a chance to realize itself might very well be worth it in the long run.

[QUOTE=Lovechild]Rosetta isn't currently a perfect tool, but I believe it can be made really good - if it was opened and my technical concerns were solved I would definately consider it. I'm still very concerned with vandalism but if we have a work queue and the translation work becomes a meritocracy (meaning to get in you'd have to sign an agreement and be sponsored by an existing member) I believe we can mediate the problems.

But yes - I see no reason to not urge adoptation if the political and techincal issue were addressed and I do believe that a system like Rosetta would bring new blood to the teams, which would be nice - I'm always pleased when I see new faces on our mailing list learning their way around the art, I'm also happy to report that recently we have gained quite a few new members who are all doing fine work.[/QUOTE]

Once again I agree. As I'm not by any means an expert on Rosetta and Launchpad, I don't know how capable the system is of fighting vandalism. That's another topic I should mail Mark Shuttleworth for.

[QUOTE=Lovechild]Back to debating:
You mention common usage vs. official wording - yet you seem completely blissfully ignorant to the fact that if we do not stick to the standard set forth by DSN - in effect we are cutting FOSS out of the race to be used in schools, governments, etc.  That is why we are doing that.. 
Yes it seems somewaht silly that email has to be e-post (or alternatively e-mail which was recently allowed by RO) but that is not up to us to decide if we want to be compliant, the best we can do to ensure this getting a sane solution is lobbying the correct organisations (and this is where having an official translation team comes in handy btw. we do a lot of that kind of legwork - you need structure to do that)[/QUOTE]

Could you sum up the rules of DNS? Is it really illegal for a school to use software that's not translated? 

It might very well be true in theory, but that's not what I'm seeing in the real world. On my high school (gymnasium, whatever you'd call it) all the computers that run Windows XP SP2 have the "danish" word firewall. I'm asking because i don't know it - does Microsoft sell a special version of Windows XP to schools and governments where the many linguistic flaws that exist in our XP SP2 CD's at home are gone?

---

### Post by Lovechild on 2006-04-19
You are indeed right that Windows does not meet the criteria, going by the letter of the law it would not be deemed to meet the demands - I have often wondered why they are allowed in such use when the rules are quite clear. MS Office e.g. do not in any way meet the demands AFAIK, which is probably the worst issue so far. I have however not used Windows in nearly 8 years, let alone seen a danish version so maybe the dutch company they used to use for the danish translations have improved.

But the short answer is that Windows the last time I checked was in direct violation. This does however not impact the the law nor the demands we have to set. Hell we might even be able to push Windows/MS Office out of certain markets when we have compliant software.

You also seem to misunderstand how we work, once a piece of work is submitted to the mailing list peer review is automatic and mandatory - I read every single line send to me and comment on it, so do the other translators - this ensures a high general standard. You wouldn't believe how many stupid little mistakes this catches. Even if there's a slight delay on the review it's definately worth it compared to just chucking it in to CVS. I'm personally really grateful for the peer review it significantly raises the bar.

tidbit:
"Brandmur" incidently is a perfectly legal and valid word to use, I believe it's the same term firefighters use to describe what is the origin of the word firewall. The only reasons it sounds silly would be that people with a technical background are used to firewall and I guess common products like Windows calls it that, which is a mistake - it doesn't make it right.

---

### Post by Mathias-K on 2006-04-19
[QUOTE=Lovechild]You are indeed right that Windows does not meet the criteria, going by the letter of the law it would not be deemed to meet the demands - I have often wondered why they are allowed in such use when the rules are quite clear. MS Office e.g. do not in any way meet the demands AFAIK, which is probably the worst issue so far. I have however not used Windows in nearly 8 years, let alone seen a danish version so maybe the dutch company they used to use for the danish translations have improved.

But the short answer is that Windows the last time I checked was in direct violation. This does however not impact the the law nor the demands we have to set. Hell we might even be able to push Windows/MS Office out of certain markets when we have compliant software.[/QUOTE]

Windows XP SP2 does not, as i have written, comply with the rules, you are talking about. Apparently, it makes no difference in real life.

[QUOTE=Lovechild]You also seem to misunderstand how we work, once a piece of work is submitted to the mailing list peer review is automatic and mandatory - I read every single line send to me and comment on it, so do the other translators - this ensures a high general standard. You wouldn't believe how many stupid little mistakes this catches. Even if there's a slight delay on the review it's definately worth it compared to just chucking it in to CVS. I'm personally really grateful for the peer review it significantly raises the bar.[/QUOTE]

I have not misunderstood your way of working, i just don't think that it has to be better.

If you are willing to review the work being done on a mailiing list, i certainly can be done in Rosetta as well. To me you seem really keen on the concept of enforcing reviews. I think doing it freely and massively in CVS can be just as good. Rosetta does in no way dissallow discussion and consistency.

[QUOTE=Lovechild]tidbit:
"Brandmur" incidently is a perfectly legal and valid word to use, I believe it's the same term firefighters use to describe what is the origin of the word firewall. The only reasons it sounds silly would be that people with a technical background are used to firewall and I guess common products like Windows calls it that, which is a mistake - it doesn't make it right.[/QUOTE]

I don't think we should judge how people think and what is a mistake and what's not. For me it's just a matter of accepting that some foreign words find their way into our language. Computer. Email. Antivirus. Harddisk. Processor. CD-ROM. RAM. The list is endless.

It is my understanding that the danish translation is being done to help people understand the system better. It is my experience that completely non tech-savvy people know Firewall better than Brandmur.

---

### Post by Lovechild on 2006-04-19
[QUOTE=Mathias-K]
I have not misunderstood your way of working, i just don't think that it has to be better.

If you are willing to review the work being done on a mailiing list, i certainly can be done in Rosetta as well. To me you seem really keen on the concept of enforcing reviews. I think doing it freely and massively in CVS can be just as good. Rosetta does in no way dissallow discussion and consistency.
[/QUOTE]

Rosetta allows every single user on the face of the earth to throw their changes DIRECTLY into CVS, tell me why this is a good idea.. forcing peer review gives us a chance to catch mistakes, stupid mistakes even the best translator can make.
Catching them before they are pushed to users mind you.

I strongly believe in that this kind of work should rest on a meritocracy, it's the only way to ensure a quality product. 

You are not being realistic in proposing that reviews should be done after the fact - not the least bit.. I think out of all the team there's maybe one guy I have never been able to catch making slight mistakes (and I make plenty - our mail archives are available so my level of suckiness is all in the open). Everyone makes mistakes, I think correcting mistakes is important - it ensures a better product, it teaches you to learn from your mistakes and it builds a community.

---

### Post by mostwanted on 2006-04-19
[QUOTE=Lovechild]Rosetta allows every single user on the face of the earth to throw their changes DIRECTLY into CVS, tell me why this is a good idea.. [/QUOTE]

Not quite true. Only one user can be the translator of a package, the rest can just make suggestions.

---

### Post by Mathias-K on 2006-04-19
[QUOTE=mostwanted]Not quite true. Only one user can be the translator of a package, the rest can just make suggestions.[/QUOTE]

That's actually quite a nice feature. I have just made suggestions here and there in Rosetta. I can't really remember any signing up for packages?

---

### Post by Lovechild on 2006-04-19
[QUOTE=mostwanted]Not quite true. Only one user can be the translator of a package, the rest can just make suggestions.[/QUOTE]

Then that changed since I used it last, I applaud that btw.

---

