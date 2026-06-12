---
title: "Nudity in Shopping Lens"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by goldsniper on 2012-09-28
Hi guys,

I just wondering if you guys realize this? 

When i clicked Unity Button this morning, one of the suggested image showed is featuring a woman which I could say; in a state of full side nudity. I can't believe my eyes. I have been strict on nudity and I don't want it - EVER - to show up on my computer screen. Plus, my kids is sharing my computer daily! I tried to click the Unity Button again but the image still doesn't showed up. Then I tried searching for it's keywords; "jimmy ge". 

Well, the image below tells all.

[IMG]http://3.bp.blogspot.com/-eN_9jaOPgbw/UGUdnGQ5rbI/AAAAAAAABV0/kG0zbmS6J0c/s400/jge1.png[/IMG]

So, what say you?

I blog about this in my blog. Please share it if you are also concern about this.

[http://mindaict.blogspot.com/2012/09/omg-ubuntu-is-promoting-nudity-in-unity.html]("http://mindaict.blogspot.com/2012/09/omg-ubuntu-is-promoting-nudity-in-unity.html")

---

### Post by rai4shu2 on 2012-09-28
Nice. I may have to rethink my position on Unity.

Not that my desktop needs even *more* nudity. :D

---

### Post by effenberg0x0 on 2012-09-28
Yep.... this is relevant. Last week I thought it was just a matter of time before we started getting bad feedback regarding the "suggestions". I predict a flood of it soon. 

Not only an image can be inadequate: Children, people with specific faith and beliefs, etc might obviously see content they were not expecting when simply trying to launch a program or find a doc. 

That is the main case for making this dash integration disabled by default and opt-in... It's a serious problem. 

If possible, try to report this on Launchpad. It's important that other people see that it's not all about security and privacy, but also everyone's rights to use their PC with no intrusive content...

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-28
BTW, if you want another example. Suppose you want to search for a doc from the National American Insurance Company (NAICO) you have somewhere in your file structure. 

Try a search on the dash for NAICO.

Regards,
Effenberg

---

### Post by goldsniper on 2012-09-28
Huh! :mad: Not to be over exxagerating. I don't have problems with Shopping Lens. But please maybe something like google /yahoo methods please? Maybe a filter for kids?

---

### Post by cariboo on 2012-09-28
If this is a real problem for anyone, I'd suggest uninstalling the shopping lens, until the option to turn the shopping lens off lands sometime in the near future.

---

### Post by goldsniper on 2012-09-28
Any easy way to remove the shopping lens?

---

### Post by jokerdino on 2012-09-28
> **goldsniper said:**
> Any easy way to remove the shopping lens?
Easiest way would be to run this command:

```
sudo apt-get remove unity-lens-shopping
```

After that, log out and log back in.

---

### Post by goldsniper on 2012-09-28
Thanks jokerdino.

Might remove it if this doesn't resolve before final.

---

### Post by cariboo on 2012-09-28
@goldsniper, have you contacted the Ubuntu developers about this problem?

---

### Post by neo_1in on 2012-09-28
I just searched for the same phrase using firefox (which includes an amazon search plugin) on amazon mp3 search and i do see the picture you mentioned. Same happened on chrome and internet explorer. But clearly for you google, microsoft and mozilla are not in the "Shame on you Ubuntu! You disrespect greedy OS!" category. Look, amazon is no pr0n site either, but clearly the picture is a music cd cover and the guy actually promoting nudity here is the one you were looking for in the lens. Personally, i don't like the idea of an operating system as a constantly connected internet portal. But these days everone is obsessed with social networking and internet, and operating systems are just catering to their needs. Whats the guarantee that the same thing won't happen in iOS or Android OSes.

Your concerns are all entirely valid but i don't think sensationalizing and name calling are ways to go. Besides as far as i know isn't the whole shopping lens thing currently only available in 12.10 Beta? So either you are running a beta 1 OS on your home PC (which is weird) or you have deliberately installed the lens in 12.04 (hmmm!).

Seeing how many people have objections with this feature, i have a feeling it'll either get removed or disabled in the final release. Though you must file a bug as you mentioned in your blog post.

And if all elese fails, <sarcasm> you can always ask for your money back.</sarcasm>

---

### Post by Mr. Picklesworth on 2012-09-28
There is a bug report about this one:
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282)

It's currently marked as Won't Fix due to what looks like some completely unreasonable thinking going on over at Canonical. Your screenshot nicely demonstrates (as if it needs demonstrating) that a completely innocuous search can bring up some pretty unexpected results (sometimes things people probably don't want their computers telling them they should buy), and your story says exactly why this is a bug that needs to be fixed through whatever means are necessary. It violates peoples' trust in Ubuntu. We all have different views here (I don't really find that album cover shocking), but Ubuntu should respect that fact by not pressing it. It's for humans, after all: we're all a little bit different.

You might be interested to know the shopping lens was yanked out for Edubuntu:
[https://bugs.launchpad.net/ubuntu/+source/edubuntu-live/+bug/1055705](https://bugs.launchpad.net/ubuntu/+source/edubuntu-live/+bug/1055705)

While I'm on this topic, it's interesting to note [Amazon's terms of service]("http://www.amazon.com/gp/help/customer/display.html/?nodeId=508088"). Now, I'm not sure if using a search proxy constitutes "using an Amazon service," but if it *does*, people under 18 are breaching those terms of service as long as they use the dash home search without parental involvement. I'd be interested to know the legal perspective there.

---

### Post by effenberg0x0 on 2012-09-28
FOSS is wonderful, Ubuntu is great and so is Canonical. But I think we should drop the "use something else" approach when things are just wrong. This is wrong. 

We're used to the idea of seeing things we may not want to see (or we may not want our kids to see) when we turn on the TV, when we browse the web, when we go to to any store, etc. That's another problem, another companies to blame, a part of modern life. But IMO no one should be under the slightest risk of seeing stuff they don't want to when looking for a document.

Sure, one can uninstall a package, use Super+A (Search Applications), Super+F (Search files), maybe even block specific network traffic and domains. We can also trow the old "This is FOSS - you're free to go use something else". This last one is vicious IMO.  

And, although everyone will run to say that those are not ads, they are. Someone here (I think it was Vexorian) made it very clear. What do we call intrusive content, with price tags, that show in our screen when we were clearly not actively looking for them? Ads.

But it doesn't matter. What matters is that this was thrown in with no consideration whatsoever on the effects it could have on the users, their families, work environments. The community played no part in it, as it is becoming more and more usual. We didn't even understand how it came in apparently after the freeze.  

I don't want to be a part of the anti-everything group. I love FOSS, I like Ubuntu, it's been a part of my personal and professional life for years. I like Unity. I respect Canonical for all the money and work they put into this. I believe there are viable business models to fund FOSS. It's OK to make money with it. But the way things are being done is just wrong. 

Being very explicit, the way Canonical is doing things is wrong. I don't see a strong Community Council, thinking about the community. I don't see a strong technical board. I don't see the whole "supreme dictator for life" as something funny anymore. This is a professional OS - we should act accordingly. 

We must feel free enough to accept that this was wrong, openly discuss it. And not tell users to use something else. 

Sorry for the rant.

Regards,
Effenberg

---

### Post by @nne on 2012-09-28
I'm not using Unity but I think that, beside removing the shopping lens, you can customize the dash. As far as I've seen somewhere, there are boxes to uncheck.

Anyway, I consider this shopping lens a nuisance so, maybe if we compain a lot the dev will remove it definitively?

---

### Post by effenberg0x0 on 2012-09-28
> **@nne said:**
> I'm not using Unity but I think that, beside removing the shopping lens, you can customize the dash. As far as I've seen somewhere, there are boxes to uncheck.

Where? AFAIK there's no customization. It's a mandatory feature for ordinary users with no technical skills to disable it.

> **@nne said:**
> 
Anyway, I consider this shopping lens a nuisance so, maybe if we compain a lot the dev will remove it definitively?

No, not devs, because it was not something developed by the community and contributors, it came from Canonical, the company that owns Ubuntu. The only reason we *might* see a way to disable it in the near future is because users reception is creating bad branding. Not because they consider this was a mistake. Read this: [http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

Regards,
Effenberg

---

### Post by @nne on 2012-09-28
> **effenberg0x0 said:**
> Where? AFAIK there's no customization. It's a mandatory feature for ordinary users with no technical skills to disable it. egards,
Effenberg
Here: [http://www.iloveubuntu.net/option-enabledisable-commercial-suggestions-ubuntu-1210s-unity-land-after-quantal-beta-2](http://www.iloveubuntu.net/option-enabledisable-commercial-suggestions-ubuntu-1210s-unity-land-after-quantal-beta-2)

Maybe it's still "upcoming". :)

---

### Post by Mr. Picklesworth on 2012-09-28
> **@nne said:**
> I'm not using Unity but I think that, beside removing the shopping lens, you can customize the dash. As far as I've seen somewhere, there are boxes to uncheck.

Anyway, I consider this shopping lens a nuisance so, maybe if we compain a lot the dev will remove it definitively?

The bug report which says (quite reasonably) 'please move this stuff to a shopping lens instead of dumping these results unexpectedly in the home lens' is over here:
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776)

It's among the top 60 hottest bugs in Ubuntu. (Bug heat is based on duplicates, as well subscribers and people affected). The official response has danced completely around the topic. The more people clicking the 'affects me' button the merrier, but I'm getting the impression that the best solution is for this to actually continue along its current trajectory. If we're right, it'll result in at least one somewhat major PR screwup and people will learn a valuable lesson about testing and listening to users (which would not have been learned if they had simply 'given in' to us whinging). If we're wrong, I for one will happily eat my hat.

Hopefully, either way, there will be no long term damage.

---

### Post by effenberg0x0 on 2012-09-28
> **@nne said:**
> Here: [http://www.iloveubuntu.net/option-enabledisable-commercial-suggestions-ubuntu-1210s-unity-land-after-quantal-beta-2](http://www.iloveubuntu.net/option-enabledisable-commercial-suggestions-ubuntu-1210s-unity-land-after-quantal-beta-2)

Maybe it's still "upcoming". :)

Maybe. Right now it looks like this:

[ATTACH]224774[/ATTACH]

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-28
> **Mr. Picklesworth said:**
> [...]but I'm getting the impression that the best solution is for this to actually continue along its current trajectory. If we're right, it'll result in at least one somewhat major PR screwup and people will learn a valuable lesson about testing and listening to users (which would not have been learned if they had simply 'given in' to us whinging). If we're wrong, I will happily eat my hat.

Hopefully, either way, there will be no long term damage.

This makes a lot of sense. 

Regards,
Effenberg

---

### Post by @nne on 2012-09-28
> **effenberg0x0 said:**
> Maybe. Right now it looks like this:

[ATTACH]224774[/ATTACH]

Regards,
Effenberg
This feature must have a package. Maybe you can uninstall it? We don't have this in Gnome shell, so maybe you could also consider migrating to [Gnome shell remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2")? ;)

---

### Post by effenberg0x0 on 2012-09-28
> **@nne said:**
> This feature must have a package. Maybe you can uninstall it? We don't have this in Gnome shell, so maybe you could also consider migrating to [Gnome shell remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2")? ;)

I'll quote myself:
[http://ubuntuforums.org/showpost.php?p=12265667&postcount=13](http://ubuntuforums.org/showpost.php?p=12265667&postcount=13)

Regards,
Effenberg

---

### Post by @nne on 2012-09-28
> **effenberg0x0 said:**
> I'll quote myself:
[http://ubuntuforums.org/showpost.php?p=12265667&postcount=13](http://ubuntuforums.org/showpost.php?p=12265667&postcount=13)

Regards,
Effenberg
So, you do nothing? You just accept the situation, allowing Canonical to continue on the wrong way? Why would they change their way if everyone submits? :)

I've never liked Unity; I felt that abandoning Gnome was wrong, so I quit using Ubuntu until I fell on this link I posted earlier and gave it a try. Now I think I should inform Canonical about that and what I think about their shopping lens, even I'm not using Unity.

---

### Post by goldsniper on 2012-09-28
> **neo_1in said:**
> But clearly for you google, microsoft and mozilla are not in the "Shame on you Ubuntu! You disrespect greedy OS!" category. 

I am happy that I got your attention, and thank you for reading my article before commenting. You are so cool! :popcorn:

Anyway, I just want to get things straight. I love Ubuntu, i have been using it since version 6.06 and still fall in love with it every day. I like unity (yes, I do) and I like lens including the shopping lens. I love 6 months development cycle and I approve the idea Canonical getting money every time I use Ubuntu. Really, I don't mind looking at ads or even clicking it in exchange of a much improved Ubuntu version for free.

Enough said, I always use a new Ubuntu version (even betas) on my home computer. Same as my wife and my kids. We always like to get an early view of fresh Ubuntu version and talk about it once a while. But I'm using a Windows PC and a Mac at work and also like it. I like the idea we are free to choose and we are free to contribute (or not to) to anything we like. 

I'm a distro hopper. I like to test new distributions and get an insight of the latest technology the world can offer me. But I always get back to Ubuntu. Something about Ubuntu is just feel right to me.

Anyway, I am not a hardcore Ubuntu user neither a Ubuntu gurus. I'm just a very content user which is very happy of what I have and I just want to express my thought.

Okay, if you are still reading this, about the words you quote above, it is not personal and no, it is not about money. IT IS truely a sarcasm. Ubuntu should be ashamed because it shows disrespect and greedy when it comes to making decision, which is already known to everyone.

Again. I really hope that, Shopping Lens stays but with improved version with filter.

---

### Post by neo_1in on 2012-09-28
> **goldsniper said:**
> I am happy that I got your attention, and thank you for reading my article before commenting. You are so cool! :popcorn:

....

Again. I really hope that, Shopping Lens stays but with improved version with filter.

Apologies if i sounded (read.... :confused:??) like a jerk.
I would reiterate that i do get your concerns, but as far as filters go, and pardon may technical deficieneies, is it really possible to filter pictures or other multimedia items based on the content inside them, yet?
I mean google and all other filter the content based on the domain and the text on the page, isn't it?
Do a google image search for "jimmy ge", and you'll find that the aforementioned picture shows up (page 2, probably) even with strict safesearch enabled. Because it is not hosted on a pr0n site but on music and shoppping sites and they are not using 'report offensive pictures' or some other rating system for maturity content.
The thing is ubuntu dash or any other such program can only filter stuff if they are already filtered at the content provider's site.
Its a tough one.

---

### Post by vasa1 on 2012-09-28
> **goldsniper said:**
> ... Ubuntu should be ashamed because it shows disrespect and greedy when it comes to making decision, which is already known to everyone.

Again. I really hope that, Shopping Lens stays but with improved version with filter.

Blogger outrage is so tiresome. It's not "Ubuntu". Get the terms right. As the other posters have explained, you get what you searched for because there's isn't yet an alogrithm to screen for "% flesh". Or are you saying there is one but "Ubuntu" isn't using it?

---

### Post by ventrical on 2012-09-28
> **vasa1 said:**
> Blogger outrage is so tiresome. It's not "Ubuntu". Get the terms right. As the other posters have explained, you get what you searched for because there's isn't yet an alogrithm to screen for "% flesh". Or are you saying there is one but "Ubuntu" isn't using it?

  I think the issue is,  is that Unity Lenses are providing a pre-browser service by doing random searches. For example if you go to the "movie' lens and type in "***** cat" minus the "cat" then you have just opened wide a plethora of youtube videos (even though youtube cautions of content). Or just try 'nudity' etc.. and click some of those on.

  One has to look forward and think that if even mild non-pornographic nudity is  comming in then we have to think what else is going to slip through the net.!! Unity then is complicit in this fashion and bears a guilt by association. It puts a lot of heat on Canonical and possibly a lot of heat on it's users if it inadvertently redirects to a  triple x porn site. In Canada and the United States the legal authorities have a zero tolerance for certain types of porn. I think we have enough of it with Facebook already. Who needs more?

---

### Post by jerrylamos on 2012-09-28
People were around for a couple million years before cloth was invented.  Now what's the big deal?  Even in public at Miami beaches and Brazil etc.  the teeny bikini's don't hide much.  

Also note in some places where women are covered head to toe and veils the incidence of violence against women is much much higher than say Sweden or Denmark or Australia where topless bathing on public beaches occurs with no problem.

Now filters (censorship) of your own choosing may be of interest.  I really try to avoid bloodshed and gore to the extent I don't view movies whose theme is violence.

My personal opinion, video "shoot em up" games are far far more harmful to society.  My view, violence begets violence.

On that topic, seems every day peole are getting shot.  Far far more significant to society in my opinion than what people look like.

Anyone know if iPad or Nook or Kindle or Windows 8 employ filters?

---

### Post by vasa1 on 2012-09-28
> **ventrical said:**
>  ... Unity then is complicit in this fashion and bears a guilt by association. ...
I'm sorry. This type of argument of guilt by association can be taken to ridiculous extents. Think about it.
Basically, instead leading proper lives voluntarily, we're trying to remove temptations from our path.

---

### Post by vexorian on 2012-09-28
> **cariboo907 said:**
> If this is a real problem for anyone, I'd suggest uninstalling the shopping lens, until the option to turn the shopping lens off lands sometime in the near future.
This is a real problem for everyone. You don't know when a nude image is going to pop up in the worst moment possible. Suggesting to remove it won't help the people that would actually find the lens useful. It seriously needs an adult filter, and the adult filter really needs tweak options.

Shopping lens still needs major changes, as long as the main tip we can give about a feature is how to remove it, it would not seem like an appropriate feature.

---

### Post by philinux on 2012-09-28
This is going downhill. Please raise a bug ubuntu-bug unity-lens-shopping or sudo apt-get remove unity-lens-shopping.

---

### Post by ventrical on 2012-09-28
> **vasa1 said:**
> I'm sorry. This type of argument of guilt by association can be taken to ridiculous extents. Think about it.
Basically, instead leading proper lives voluntarily, we're trying to remove temptations from our path.

 I have thought about it. I do not want Unity doing a pre-browse for me especially in this experimental stage. There is no telling what might slip through. Look what happened to Pete Townsend  for just 'looking'.  In fact I think the current Unity PreBrowser search is a security risk.

Simple solution? Make those lenses optional from the repos, not default.

---

### Post by ventrical on 2012-09-28
> **philinux said:**
> This is going downhill. Please raise a bug ubuntu-bug unity-lens-shopping or sudo apt-get remove unity-lens-shopping.


Done.

[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1058087](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1058087)

---

### Post by vexorian on 2012-09-28
> **vasa1 said:**
> Blogger outrage is so tiresome. It's not "Ubuntu". Get the terms right. As the other posters have explained, you get what you searched for because there's isn't yet an alogrithm to screen for "% flesh". Or are you saying there is one but "Ubuntu" isn't using it?
On top of my head I can think of a couple of plenty filter algorithms that have been shown to work.
a) I bet Amazon itself does have a filter against NSFW results. If it doesn't then that really makes me doubt they were a good choice for this in the first place. So simply make the search use this filter.
b) Google search has like a 99% success rate. Thus a intelligent search that avoids results is possible.
c) Add a "Report inapropriate result" button. Ban results that get reported. This needs a work force but has worked in things like blogger.

The matter at hand is that when Canonical and Shuttleworth fantasized about turning unity into the gateway to the whole world, it seems they may have forgotten that search is a terribly non-trivial problem. It is no surprise Google went from a college project to a multi-billion monster that could by my country if it wanted. Because they could do search right. A NSFW filter is as basic a feature you can get in web searches. If even this basic feature is too costly or difficult for a small company like Canonical they will probably need to give up on the whole unity=search idea...

---

### Post by mips on 2012-09-28
I looked really hard but could not see any more nudity than what I see at the beach and there are plenty of little kids running around there.

Sometimes I wonder...

---

### Post by ventrical on 2012-09-28
> **mips said:**
> I looked really hard but could not see any more nudity than what I see at the beach and there are plenty of little kids running around there.

Sometimes I wonder...

Just go to the movie lens, type in 'marilyn' and , voila' !  Art or nude porn?


 I mean if you get that from just typing in a persons name , what else do you think is on the stack?

*note*

Only seems to work in Quantal Beta 2.

*edit*

No .. it brings up the nude pic after you close the dash and turn it back on again. It remembers where you left off.

---

### Post by cariboo on 2012-09-28
So how many tries, and how long did it take both of you, goldsniper and ventrical to come up with an image of a nude?

BTW, the moie linked to the Marilyn Munroe image is a spanish language documentary about her life and times, I didn't watch the whole thing, but the only nudity I saw, was a picture of a calendar that I've seen many times before.

To me this is mostly a blogger trying to get more page views, as he really hasn't done anything else. He hasn't contacted Canonical, he didn't create a bug, all he did was post a link to his blog.

---

### Post by ventrical on 2012-09-28
> **cariboo907 said:**
> So how many tries, and how long did it take both of you, goldsniper and ventrical to come up with an image of a nude?

BTW, the moie linked to the Marilyn Munroe image is a spanish language documentary about her life and times, I didn't watch the whole thing, but the only nudity I saw, was a picture of a calendar that I've seen many times before.

To me this is mostly a blogger trying to get more page views, as he really hasn't done anything else. He hasn't contacted Canonical, he didn't create a bug, all he did was post a link to his blog.


 I typed in 'marilyn' in the movie lens (first time) using quantal Beta 2. The nude pic was at top of the stack. I am not trying to change policy or anything. I am just adding my opinion as is everyone else. I too have seen that nude pic before , but not on my PC using the  existing desktop. I had to search through a browser and , although not looking for it specifically, it would often come up in side snippets while watching news articles. This whole issue is a horse of a different colour IMHO. I  help others (grade 1 school teachers) make a transition from Windows to Ubuntu Precise using Unity 2D. I haven't tested those lenses yet but some of the clients I work with will be a little bit shocked that the Unity Lenses are producing these  pics.


  I also filed a bug (as suggested by Phillinux) What good will it do? Really !?

---

### Post by ventrical on 2012-09-28
Yep .. same thing with Unity 2D Precise Pangolin. I dunno .. I'm in Canada here and it is tough enough to convince people to make a transition over to Ubuntu let alone Edubuntu.  One good thing  is that I now know that some of the lenses are pre-browsing (which is a good thing) All the browsers potentially can bring up a nude pic. I am not singling out Unity or Ubuntu. I had just thought that  Ubuntu held itself to a higher bar.

---

### Post by ventrical on 2012-09-28
> **effenberg0x0 said:**
> FOSS is wonderful, Ubuntu is great and so is Canonical. But I think we should drop the "use something else" approach when things are just wrong. This is wrong. 

We're used to the idea of seeing things we may not want to see (or we may not want our kids to see) when we turn on the TV, when we browse the web, when we go to to any store, etc. That's another problem, another companies to blame, a part of modern life. But IMO no one should be under the slightest risk of seeing stuff they don't want to when looking for a document.

Sure, one can uninstall a package, use Super+A (Search Applications), Super+F (Search files), maybe even block specific network traffic and domains. We can also trow the old "This is FOSS - you're free to go use something else". This last one is vicious IMO.  

And, although everyone will run to say that those are not ads, they are. Someone here (I think it was Vexorian) made it very clear. What do we call intrusive content, with price tags, that show in our screen when we were clearly not actively looking for them? Ads.

But it doesn't matter. What matters is that this was thrown in with no consideration whatsoever on the effects it could have on the users, their families, work environments. The community played no part in it, as it is becoming more and more usual. We didn't even understand how it came in apparently after the freeze.  

I don't want to be a part of the anti-everything group. I love FOSS, I like Ubuntu, it's been a part of my personal and professional life for years. I like Unity. I respect Canonical for all the money and work they put into this. I believe there are viable business models to fund FOSS. It's OK to make money with it. But the way things are being done is just wrong. 

Being very explicit, the way Canonical is doing things is wrong. I don't see a strong Community Council, thinking about the community. I don't see a strong technical board. I don't see the whole "supreme dictator for life" as something funny anymore. This is a professional OS - we should act accordingly. 

We must feel free enough to accept that this was wrong, openly discuss it. And not tell users to use something else. 

Sorry for the rant.

Regards,
Effenberg

 Nice rant effenberg.! +1

---

### Post by mc4man on 2012-09-28
I have to wonder where all the people complaining about this were in 12.04, maybe even 11.10
The 2 Ex. mentioned here have nothing really to do with the shopping-lens, you can see the same results for both in 12.04

So if you have issue with what is on cd or video covers/thumbnails & the fact the ubuntuone music store, youtube, Amazon, ect. display them then take up there. 
Or remove **all** the lens/scopes that display them.

Do note that the suggestion of removing the shopping lens to prevent **any** of this is incorrect. Amazon & ubuntuone music are also in scopes, you'll have To do more than just remove that lens packages

If ubuntu allowed filtering &  persistent filtering of all lens/scopes that returned online results that would slightly lesson some objections

---

### Post by nothingspecial on 2012-09-28
> **mc4man said:**
> 
If ubuntu allowed filtering &  persistent filtering of all lens/scopes that returned online results that would slightly lesson some objections

If Ubuntu used filtering in the lenses people would moan that their freedom was being impinged.

---

### Post by lucazade on 2012-09-28
oh.. finally something appealing in Unity :P

---

### Post by ventrical on 2012-09-28
> **mc4man said:**
> I have to wonder where all the people complaining about this were in 12.04, maybe even 11.10
The 2 Ex. mentioned here have nothing really to do with the shopping-lens, you can see the same results for both in 12.04


  I didn't realize that the lenses were pre-fetching web-sites until I had seen this thread. I always just used firefox browser/google/youtube. With the latter we pretty well know what to expect but I didn't realize that this stuff was being pre-fetched in the unity lenses. Now I know. Then that makes me wonder what zeitgiest is doing.

 Also , isn't this just plain duplicity of services? If it is, then what a waste.

---

### Post by ventrical on 2012-09-28
Also.. I tried an experiment in <movie-lens>. I typed in 'marilyn the wet elephant' and pretty well got nothing. Then I typed in 'marilyn the wet' and one of the results was so far out in left field that it will make you wonder (I won't mention it here).

THEN: I went to google and typed in the same and did not receive anything that was close to what came up in the lens.

  Pesonally I am not complaining and it's really none of my buisness. I'm just asking. I'm just asking where is Ubuntu going with this and what if a kid  (younger person) types somthing in inadvertently and gets a show-stopper-pic!?  I mean .. I am just asking, does Ubuntu think that those pics/movies are appropiate or is it out of their 'scope' to really be concerned (no pun intended).

What .. me worry !
Alfred E. Newman :)

---

### Post by vexorian on 2012-09-28
> **ventrical said:**
> I didn't realize that the lenses were pre-fetching web-sites until I had seen this thread. I always just used firefox browser/google/youtube. With the latter we pretty well know what to expect but I didn't realize that this stuff was being pre-fetched in the unity lenses. Now I know. Then that makes me wonder what zeitgiest is doing.

 Also , isn't this just plain duplicity of services? If it is, then what a waste.
There is one important difference between the youtube/ubuntu-one scopes and the shopping lens. In that their results don't appear in home lens. NSFW results in amazon ads are worsened by the fact they are there by default.

Let us be serious. This *need*s a filter. The argument that people would complain about censorship is quite frankly, very absurd (For starters, it assumes that all complaints are worth the same. But the reality is that lack of a parental control in these searches will displace the markets of professional people and parents. As long as the filter is toggleable, this wouldn't be any different to google image search. It does not matter what your views on unity are. Because really, some people don't have a choice. If nude images appear on your computer display while you are at work "But We all come nude to this world! Man!" arguments won't work. The last thing anybody serious wants is nude pics appearing unpredictably. And if there is something that the shopping lens is great at is being unpredictable.

---

### Post by philinux on 2012-09-28
Interesting diagram of how the lens might be working.

[http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works](http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works)

---

### Post by effenberg0x0 on 2012-09-28
> **philinux said:**
> Interesting diagram of how the lens might be working.

[http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works](http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works)

Thanks, this is good info.

By the way, about getting rid of the ads: this is obvious to us but might help people that just want to get rid of ads and don't want to uninstall packages and mess their install:

```
$ echo -e '127.0.0.1\tproductsearch.ubuntu.com' | sudo tee -a /etc/hosts
```
> 127.0.0.1	productsearch.ubuntu.com

```
$ cat /etc/hosts | grep productsearch
```
> 127.0.0.1	productsearch.ubuntu.com

Ping it just to test: it's 127.0.0.1
```
$ ping productsearch.ubuntu.com
```
> PING productsearch.ubuntu.com (**127.0.0.1**) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.058 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.061 ms
^C
--- productsearch.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.058/0.059/0.061/0.007 ms

After doing that the NAICO test shows me nothing on the dash now.

Regards,
Effenberg

**EDIT:**
Netstat is showing me a ton of connections to two canonical hosts:
$ netstat -tupal | grep -i canonical
There's a lot of connections to *alkes.canonical.com* and *achernar.canonical.com*, so I have added both to /etc/hosts as localhost too.

---

### Post by Jay MC on 2012-09-28
> **jerrylamos said:**
> People were around for a couple million years before cloth was invented.  Now what's the big deal...  My personal opinion, video "shoot em up" games are far far more harmful to society.  My view, violence begets violence.

Personally, I totally agree with your values here  :)  but some people don't like to see nudity, even mild nudity.

> Even in public at Miami beaches and Brazil etc.  the teeny bikini's don't hide much.

When you walk outside your own house in Miami or Brazil (and equally, when you go looking on the internet) you run the risk of seeing things you don't want to.  That's a feature of the fact that we share the world with other people, and some spaces (real and virtual) belong to all of us.

But you shouldn't have to run the same risk looking for files on your own computer.

It's like saying, "You see plenty of graffiti when you drive to work and back, so what's the problem if we spray some grafitti on your living room wall?"  The difference is it's your living room wall.  When you're sitting in your own house, you should have total control over what you're exposed to.

In computing terms, when you're looking for a file in your own folders on your own computer, you're "sitting in your own house".  Seeing an image there is not the same as seeing it on the internet, or on a beach in Miami - I humbly submit.

---

### Post by effenberg0x0 on 2012-09-28
<OT>
There were a couple posts about Brazil. I find it funny that people think we're naked here. I just wanted to point out that this is a 194 Million people country and we do buy clothes from the same brands available in US, Europe and Asia. All major global companies have offices here and people wear normal clothes. You can't really take your clothes off and expect the police to not arrest you. I live in the biggest city (Sao Paulo) which has 12 Million inhabitants. I haven't ever seen anyone naked in the street. 

Travel agencies here generally have pictures of Disneyland. Are all people in US using Mickey Mouse costumes? 
</OT>

Regards,
Effenberg

---

### Post by mips on 2012-09-28
Ok listen up. If you don't like the search results passed on from amazon then uninstall the shopping lense. What you get from the search results is the same as what you would get from doing a search on the amazon web page.

[B]Now in 12.10 you will get the option to disable the internet search function from your lense utility or whatever it's called and it will probably be backported to 12.04.
[/B]
It's not Ubuntu's fault the content resides in amazon and it's not ubuntus responsibility to uphold your puritan values. If you don't like it don't use it, simple as that. I abhor censorship of all forms, especially where minorities dictate to others what they can and cannot see. I would be p'ed off if I searched for a music album and got no result simply because someone decided the cover art is to risqué.

It's not Ubuntu's job to enforce your parental responsibilities, take responsibility for your own kids and enforce your own religious/puritan prejudices as you see fit. You are free to disable the function or install another distro, nobody is holding gun to your head saying you must use this. I for one don't use it but this does not mean I should enforce my beliefs on others.

Why is it that people need a nanny in their lives?

I would be interested to see the demographics wrt to the complaints but I already have my suspicions.

You have choices in life, exercise them.



**[COLOR="Red"]EDIT:[/COLOR]** **Let me copy and paste this here before more people have puppies,**

[http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works](http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works)

> **[SIZE="3"]Ubuntu 12.10 Amazon Shopping Results to be Made Optional[/SIZE]**
By Joey Sneddon, posted September 25, 2012


**Ubuntu’s last-minute decision to [COLOR="Blue"][[/COLOR]add shopping results to the Home Lens]("http://www.omgubuntu.co.uk/2012/09/online-shopping-features-arrive-in-ubuntu-12-10") of the Unity Dash proved controversial earlier this week - but is a compromise on the cards?**

It certainly seems so. The only question is whether the compromise will land in time for Ubuntu’s release next month.

[SIZE="2"][COLOR="DarkOrange"]Developer[/COLOR][/SIZE]

News of a change in tact came in a [COLOR="Blue"][Google+ update]("https://plus.google.com/110419250019099644591/posts/Yyme1K2M7iM")[/COLOR] from Unity developer Didier Roche. It was this update that first revealed a way to ‘disable’ online suggestions was coming, writing:

“First plumbing part (in libunity) done for optionally disabling all network communication for the unity lenses. Tomorrow will be the lenses work, and when I’ll get the design, the UI part…”

The [COLOR="Blue"][bug report]("https://bugs.launchpad.net/ubuntu/quantal/+source/gnome-control-center/+bug/1054746")[/COLOR] pertaining to this issue has since been marked as of “high” importance, and in “triage” (i.e. something I getting done about it).

The bug report relating to this issue marks all ‘network’ using Lenses and Scopes – Music, Video and Home – as ‘affected’.

So it seems that this solution is going to be a thorough one.

[SIZE="2"][COLOR="DarkOrange"]Code Exists[/COLOR][/SIZE]

Since then further clarification on where the feature will be available from, and how it’ll work.

The bug report reads:

We will add an option either in the appearance or privacy gnome-control-center panel (this is yet to be discussed with design).

This Commercial/Online suggestions on/off switch enables to remove all suggestions in the dash and default lenses.

A setting within the Privacy section of System Settings would make the most sense to me.

[SIZE="2"][COLOR="DarkOrange"]Offline or Online[/COLOR][/SIZE]

The work on an interim solution is running concurrent with discussion on the Ayatana Mailing list.

Over there, Mark Shuttleworth has been actively engaged with users in shaping up a “settings pane” from which various elements of the Dash/Lenses/Scopes would be configured – including the option to disable internet results for lenses.

Sam Hewitt kicked things off with a set of mock-ups that got a positive reaction. These have since been refined based on feedback and suggestion – could this be what we end up seeing in Ubuntu 13.04?

[IMG]http://cloudfront.omgubuntu.co.uk/wp-content/uploads/2012/09/unity-settings-panel-home.png[/IMG]

---

### Post by rai4shu2 on 2012-09-28
I think a more apt analogy would be:

You see lots of graffiti on the drive to work, so why the fuss over a little graffiti when you look out your bedroom window? If you don't like it, notify your neighborhood association.

---

### Post by mips on 2012-09-28
> **effenberg0x0 said:**
> <OT>
There were a couple posts about Brazil. I find it funny that people think we're naked here.

Oh no, we don't think you guys walk around naked at all. We do however know about very small tiny bikinis and some other things I won't mention here related to the word wax etc which grew a international following :lolflag:

---

### Post by ventrical on 2012-09-28
> **effenberg0x0 said:**
> <OT>
There were a couple posts about Brazil. I find it funny that people think we're naked here. I just wanted to point out that this is a 194 Million people country and we do buy clothes from the same brands available in US, Europe and Asia. All major global companies have offices here and people wear normal clothes. You can't really take your clothes off and expect the police to not arrest you. I live in the biggest city (Sao Paulo) which has 12 Million inhabitants. I haven't ever seen anyone naked in the street. 

Travel agencies here generally have pictures of Disneyland. Are all people in US using Mickey Mouse costumes? 
</OT>

Regards,
Effenberg

OT

 I have some old microchips from the late 70's that were made in Brazil. I'll look em up! :) I live in the automotive capital of Canada, just south of Detroit. Strip bars and Casinos all over the place.  But those are *other* spaces. Mycomputer is *myspace*. :)

---

### Post by mips on 2012-09-28
> **ventrical said:**
> I live in the automotive capital of Canada, just south of Detroit.

Thank goodness I looked at google maps before replying to this :biggring:

I was about to say how can you be in Canada when you are South of the USA but yeah we never did much geography wrt to the great lakes in school except for pin pointing them on a map and being told they are massive.

---

### Post by Jay MC on 2012-09-28
> **Mr. Picklesworth said:**
> The bug report which says (quite reasonably) 'please move this stuff to a shopping lens instead of dumping these results unexpectedly in the home lens'...

+1.

I haven't tried the latest version yet, but this really is something that worries me.

Having it in a separate dash is fine - useful, even - but I don't want it integrated with the home dash.

Imagine a journalist searching his own computer for "kinky bondage", because he's looking for a half-finished bit of copy called "Kinky bondage trial collapses due to police admin errors."  He probably wouldn't want to be offered books about kinky bondage.  He *certainly* wouldn't want Canonical to know that he'd searched his own computer for the phrase "kinky bondage", because without the context, that is a salacious-seeming fact.

Imagine a law student searching her own computer for a PDF called "extreme pornography: model legislation & global review".  Obviously, if the auto searches only fly off to Amazon, they won't find anything obscene - but I bet she wouldn't want searches like "extreme porn" or "extreme pornography" showing up in an access log somewhere, without any context to clarify her intent.

You formulate search terms based on what you're searching.  I'm guessing a Criminology undergraduate wouldn't search the internet for "snuff video" or "child porn" - but he might search his own hard drive for either phrase, had he been drafting an academic thesis about those topics.

I know these aren't the most common use cases, but let's face it - they're far from unthinkable.  Fundamentally, you should be able to search your own computer freely and without fear.  You should never have to think, "Do I really want to type this in...?" when it's your own PC.

So really, we need to be clear on this - someone seeing a saucy album cover that he didn't want to see, while trying to search his own PC, is just the tip of the iceberg.  By itself, it's a really minor incident, but everyone needs to use her or his imagination here.  If that's happening already, what else might happen?

---

### Post by cariboo on 2012-09-28
One thing many here are forgetting, is that there will be the ability to turn shopping off in the home lens, and that nothing is written in stone yet, as we are just short of a month away from final release. There has been a bug reported, and everyone that is worried about this, even though it has been doable since the previous release, and nobody mentioned it, should click the affects me button, subscribe to the it, and add your relevant comments. Posting about it here isn't going to do much more than get everyone riled up.

---

### Post by mips on 2012-09-28
If Shipit was still available people would be burning their CDs at the stake right now :biggrin:

---

### Post by Jay MC on 2012-09-28
> **mips said:**
> Ok listen up. If you don't like the search results passed on from amazon then uninstall the shopping lense. What you get from the search results is the same as what you would get from doing a search on the amazon web page...  it's not ubuntus responsibility to uphold your puritan values.

I don't have any puritan values.  I'm a fan of nudity.  Love it.

But people shouldn't have to opt *out* of seeing things that aren't on their own computers, when they try to search their own computers.

Ubuntu targets normal users and Linux newbies ("human beings"), so it's no good saying, "Oh, you can always type such-and-such into Terminal if you don't like it."  That's not compatible with the point of Ubuntu (I know you didn't actually say that, but is it instantly obvious to a Linux newbie how to uninstall the shopping results...?).

We should all be kings of our own hard drives.  People who don't have puritan values shouldn't be blocked by censorship.  But equally, people who *do* have puritan values shouldn't have them challenged or overruled when they just want to search for a file on their own hard disks.  That's just as bad as you getting censored, in my opinion.

I speak not as a puritan, but rather as someone who believes that people who spend hundreds of pounds on a computer shouldn't have to fight with it to avoid seeing things that they don't like when they're not even browsing the internet.

If we want to enable these shopping results by default, I hope it will be instantly obvious how to disable them.  The first time you get Amazon results, maybe Unity could pop up a message that says, "We've included relevant results from Amazon - do you want to keep on seeing these?  If you click 'no', you can always use the shopping lens."

I think what I'm saying here is self-evidently true.  The norm should be that when you search your own computer, you search your own computer - unless you opt in to other stuff.  I guess some people may disagree, but equally, I guess that some people may fundamentally disagree on what a PC should do?

---

### Post by Jay MC on 2012-09-28
> **rai4shu2 said:**
> I think a more apt analogy would be:

You see lots of graffiti on the drive to work, so why the fuss over a little graffiti when you look out your bedroom window? If you don't like it, notify your neighborhood association.

I don't agree with this counter-analogy  :)

When I'm looking for a file on my *own* computer, I'm not looking out of my bedroom window.  I'm looking through the drawers in my bedside cabinet - or leafing through my diary - or looking under my bed.  Some analogy like that.

If I want to look out of my bedroom window, I'll fire up Chromium, or a newsreader, or a mailer, or some other app that offers a glimpse of the world outside.

Yes, it's good that I can see what's outside when I'm sitting at home.  But it should be me that decides to open the curtains in the morning.

---

### Post by Jay MC on 2012-09-28
Just for clarity, I think an online shopping lens (starting with Amazon) is a fantastic idea.  And I can see myself using it a lot, and even opting to have Amazon results included in my home lens by default.  But it shouldn't catch anyone by surprise, and I think it should be "opt in" rather than "opt out".

---

### Post by ventrical on 2012-09-28
@effenberg

Sorry for being OT:

This is from one of the earliest XTs. It had the riser 8bit card with the 8088 on it. The microchips from Brazil are rare. They were contracted by Texas Instruments.

---

### Post by effenberg0x0 on 2012-09-28
> **ventrical said:**
> @effenberg

Sorry for being OT:

This is from one of the earliest XTs. It had the riser 8bit card with the 8088 on it. The microchips from Brazil are rare. They were contracted by Texas Instruments.

You have a lot of interesting hw there eh? :) Although there are manufacturing plants from vendors like Samsung, LG, Dell, Lenovo, Philips, HP, etc and (more commonly) Contract Manufacturers (like Foxconn, Flextronics, etc) manufacturing for Seagate, Western Digital, Sony, and all other IT brands here I believe most chips are imported from China nowadays... No one can compete with their prices.

Regards,
Effenberg

---

### Post by ventrical on 2012-09-28
> **effenberg0x0 said:**
> You have a lot of interesting hw there eh? :) Although there are manufacturing plants from vendors like Samsung, LG, Dell, Lenovo, Philips, HP, etc and (more commonly) Contract Manufacturers (like Foxconn, Flextronics, etc) manufacturing for Seagate, Western Digital, Sony, and all other IT brands here I believe most chips are imported from China nowadays... No one can compete with their prices.

Regards,
Effenberg

Pretty well, that is correct. Old hardware can be put to good use. Theoretically, a semiconductor has an infinite lifespan. It's good to know where our PC histories came from. ! :)

---

### Post by ventrical on 2012-09-28
Just for experimental purpose I entered 'sn74s11n' into the movie lens and got "sorry no matches.."

---

### Post by effenberg0x0 on 2012-09-28
> **ventrical said:**
> Pretty well, that is correct. Old hardware can be put to good use. Theoretically, a semiconductor has an infinite lifespan. It's good to know where our PC histories came from. ! :)

Yes, I love technology... always and forever.
[http://www.youtube.com/watch?v=w9ERiI1epI4](http://www.youtube.com/watch?v=w9ERiI1epI4)

Regards,
Effenberg

---

### Post by xebian on 2012-09-28
> **mips said:**
> Thank goodness I looked at google maps before replying to this :biggring:

I was about to say how can you be in Canada when you are South of the USA but yeah we never did much geography wrt to the great lakes in school except for pin pointing them on a map and being told they are massive.

That is if you are just considering the lower 48 states.  If you live in Alaska of the USA, then a good number of Canadians would be south of the USA. My Canadian friend tells me most Canadians live just past the border.

---

### Post by xebian on 2012-09-28
It must be a slow day.  At first I thought it was a new Unity version like GNUbuntu, a GNUnity or something.  lol.  :p

---

### Post by ventrical on 2012-09-28
Ha! :)

---

### Post by jbicha on 2012-09-28
> **mips said:**
> **Now in 12.10 you will get the option to disable the internet search function from your lense utility or whatever it's called and it will probably be backported to 12.04.**

It won't be backported to 12.04, as it would require a bunch of packages to be updated and it would break UI freeze.

---

### Post by effenberg0x0 on 2012-09-28
I just thought of something very easy to implement, which has the potential to solve the problems partially.

When we search the Dash for something, the results (Books, Videos, CD covers) images (the thumbnails) are a separate part of the process. 

If you add a checkbox in config/privacy:
[X] Show media thumbnails in the Dash search results.

- When checked it shows the media thumbnails. 
- When not checked, it shows a CD/Video/Book icon. 

I was too lazy to go further (Friday night and I'm tired). But replacing the thumbnails is totally doable. I used the "blank sheet of paper" icon.

[ATTACH]224806[/ATTACH]
 
That way, traffic is still generated by us so companies still get their money, users can choose to allow visual intrusion or not in their Dash, there's no need to ask ordinary users to uninstall packages.

Regards,
Effenberg

---

### Post by ventrical on 2012-09-28
> **effenberg0x0 said:**
> I just thought of something very easy to implement, which has the potential to solve the problems partially.

When we search the Dash for something, the results (Books, Videos, CD covers) images (the thumbnails) are a separate part of the process. 

If you add a checkbox in config/privacy:
[X] Show media thumbnails in the Dash search results.

- When checked it shows the media thumbnails. 
- When not checked, it shows a CD/Video/Book icon. 

I was too lazy to go further (Friday night and I'm tired). But replacing the thumbnails is totally doable. I used the "blank sheet of paper" icon.

[ATTACH]224806[/ATTACH]
 
That way, traffic is still generated by us so companies still get their money, users can choose to allow visual intrusion or not in their Dash, there's no need to ask ordinary users to uninstall packages.

Regards,
Effenberg

I just disabled 'Techno" in filters and those "a$$ups" are gone ! :) errr .. or did somebody already do this ? :)

---

### Post by jokerdino on 2012-09-29
I guess Won't fix is the reply you would get. 

See [https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282)

---

### Post by cariboo on 2012-09-29
> **jokerdino said:**
> I guess Won't fix is the reply you would get. 

See [https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282)

I guess some of us don't want to let facts get in the way of complaining, you will be able to turn of seeing these results in the home lens, in System Settings->Privacy, before Quantal is released.

You can disable it yourself right now, by removing the unity-lens-shopping package. Keep in mind that Quantal hasn't been released yet, and there are still changes coming.

What really surprises me, is that nobody that is running Precise is complaining about this as you will get the same results as the op of the thread and ventrical got when running the searches they tried, and there is no way to turn it off in the home lens in 12.04.

---

### Post by goldsniper on 2012-09-29
> I guess Won't fix is the reply you would get.

See [URL="http://https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282"]https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054282
[/URL]

> **cariboo907 said:**
> So how many tries, and how long did it take both of you, goldsniper and ventrical to come up with an image of a nude?

Just came back from my day-offs with my kids. Anyway, subscribed to the bug, (yes i tick the Affect me). :)
As I said in my first post, it was not a search. It was an image of suggested product. I clicked the unity button and it was already there. (I wanted to search for 'gedit')

Personally, I think Unity is great. Shopping lens is great. Nudity is not.

And as always, this community have done a great job discussing and suggesting good workarounds. I'll try to apply them.

Personally, there are few alternatives out there and I'm considering to test them if this issue cannot be well addressed and going down the drain. Well, it's going to be Won't fix vs. Won't use. Afterall, we are our own bosses when it come to personal computer, right. 

Thanks, all of you are really wonderful.:KS

p/s : My link to my blog does generate more (55 to be exactly) addition page views till this time frorm this thread. If this bug affected you, I'll remove them ASAP. :popcorn:

---

### Post by Bazon on 2012-09-29
The fact it's **commercial** seems to be much more offending to me than the fact it contains nudity.
(But anyway, I don't care, I'm happy with Gnome-Shell and XFCE :-) )

---

### Post by Jay MC on 2012-09-29
> **Bazon said:**
> The fact it's **commercial** seems to be much more offending to me than the fact it contains nudity.

Personally, to me, it's neither.  It's partly the principle - or as goldsniper said:

[QUOTE=goldsniper]Afterall, we are our own bosses when it come to personal computer, right.[/quote]

I also care about the privacy issue - the fact searches you run on your own computer, on your own files, will go off to Canonical by default, but without any context.  On page six I gave some examples that I hardly think are contrived, where legitimate activity could look dubious or even illegal.

---

### Post by jerrylamos on 2012-09-29
> **effenberg0x0 said:**
> <OT>
There were a couple posts about Brazil. Brazil is rather (!) famous for super models Giselle, Alesandra, ($) with lots of internet pics wearing not much.  There's a set of pics of an Australian super model wearing zero and a South African on a Miami beach with a teensy thin bikini. Big wow there is her -very- ripped boyfriend of 5 years. Links are in Huffington Post.

Difference is you have to actively look for those pics.

Just the opposite in our local Walmart.  As one of my fitness friends said "defies gravity".  Hardly believe it's the same species.

---

### Post by mips on 2012-09-29
Why don't you guys provide feedback to Amazon asking to included a search filter on their site to exclude adult content? If enough of you make a noise then then maybe they will comply.

This filter can then be used by ubuntu if selected by the user in settings (will require a software feature) to omit results with adult content.

---

### Post by philinux on 2012-09-29
At least it's using https now. [http://www.iloveubuntu.net/unity-shopping-lens-updated-https-support-ubuntu-1210](http://www.iloveubuntu.net/unity-shopping-lens-updated-https-support-ubuntu-1210)

---

### Post by Jay MC on 2012-09-29
> **mips said:**
> Why don't you guys provide feedback to Amazon asking to included a search filter on their site to exclude adult content? If enough of you make a noise then then maybe they will comply.

Firstly, that would address the problem of "accidental exposure" to adult material, but not the privacy implications.  In either case, if I were Amazon, I'd probably say "if you don't want to see what we sell, then don't search our site" - and then spit out my coffee when you explain that your OS searches the site automatically, when you're not even trying to use the internet.

Secondly, it's not just about adult content.  It's about unwelcome content full stop.  It's no good coming up with solutions to specific questions if you're not addressing the underlying problem, which will keep throwing up question after question.

If you're searching your computer for an mp3, and Unity shows you the latest albums from the same band on Amazon, then that's relevant and cool.

But if you're an alcoholic who's searching for a file you downloaded called "alcohol.pdf", you probably *wouldn't* want your own computer to start trying to sell products like [[COLOR="Blue"]this[/COLOR]]("http://www.amazon.co.uk/Mmwah-2cl-Test-Tube-Shots/dp/B004QIDDPQ/ref=sr_1_1?ie=UTF8&qid=1348930236&sr=8-1") or [[COLOR="blue"]this[/COLOR]]("http://www.amazon.co.uk/Gold-Vodka-Sparkling-200ml/dp/B0051XYAH0/ref=sr_1_2?ie=UTF8&qid=1348930236&sr=8-2") the minute you type in "alcohol" (those are the top two results on the UK Amazon, by the way).  Sure, an alcoholic has to put up with temptation every day, but not when he's trying to search his own hard drive.

If you're trying to find a letter to your divorce lawyer, or a missing persons notice to print out and put up where your teenage son was last seen, you might think Unity was being a bit tactless if it started showing you sensationalist novels about cheating housewives or missing people, based on your keywords.

I will always want to keep searching my own computer and searching the internet separate.  Ultimately, I've not tried this feature myself (I'm using 12.04 LTS) - and *as long as* it's obvious how to disable it, and it's clear to users that what they type in the home lens *isn't 100% private* (unless they've disabled it) then I don't suppose it matters a huge deal.

But I find it bizarre how people on this thread are failing to grasp why others are alarmed by the feature, and fixating on small red herring details (like whether mild nudity is or isn't offensive) rather than looking at the bigger picture.

This is what we're talking about:

- Your computer telling someone else what keywords you look for in your own private files on your own computer

- That information being used commercially

- Information and images that you didn't ask for (and might find unwelcome or offensive) being shown to you, when you're trying to search through your private collection of information and images

---

### Post by goldsniper on 2012-09-29
> **Jay MC said:**
> This is what we're talking about:
....

- Information and images that you didn't ask for (and might find unwelcome or offensive) being shown to you, when you're trying to search through your private collection of information and images

@Jay MC, thank you. Well explained. Should be no issue if users have control of their preferences which is what I'm talking about. 

Maybe it's an imposible term if the feed from Amazon can not be controlable by Ubuntu side though.

---

### Post by cariboo on 2012-09-29
This thread is just starting to repeat itself. Instructions on how to disable the feature have been posted in this thread.

Thread closed.

---

