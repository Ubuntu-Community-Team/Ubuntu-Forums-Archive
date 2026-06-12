---
title: "&quot;More suggestions&quot;, (unity-lens-shopping) should have a settings 'opt out'"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-20
Showed up today in proposed, maybe related to unity-webapps
While can be stopped if desired there doesn't seem to be a gui settings to do so if one finds it bothersome (I do
couple of random screens

Also to note - the upgrade has 'suggestions' showing in the video lens, after removing & the re-installing the lens the video lens no longer shows 'sugg'
Amazon results are Only shown in home lens & video lens with the remote scope installed

edit: MS blog on
[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)
J.Bacon  - 
[http://www.jonobacon.org/2012/09/25/more-information-about-online-dash-search-privacy/](http://www.jonobacon.org/2012/09/25/more-information-about-online-dash-search-privacy/)

bugs on just user control, nothing more
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054746](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054746)
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054656](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054656)

Regarding security, ect.
While this thread doesn't  ask about security/privacy concerns to put 1 that's been raised out front
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054677](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054677)
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1057162](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1057162)

---

### Post by Mr. Picklesworth on 2012-09-21
Please do file a bug report over here: [https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping)
This feature materialized very late, and it needs a lot of tuning. Hopefully either all the bugs will be fixed, or all the bugs will serve as ample demonstration for why you don't land features like this after feature freeze.

I'm trying to remember now, but I think there was a lot of discussion last cycle when a scope, added by default, was searching for software in the repository &#8212; in some cases talking to online services. It was changed to only happen in the Applications lens for a bunch of reasons, but I think "let's not surprise people by sending all their searches to random web servers" was one of those reasons. Sending everyone's searches to *Amazon* by default, a company famous for being quite aggressive with tracking people and learning their behaviour, seems a few orders of magnitude worse.

---

### Post by mc4man on 2012-09-21
will take a look tomorrow to see if there is a current bug, though I'm sure there must of been some discussion about.

It may also be that there is some revenue to be had, if so that's ok though wouldn't hurt to state that somewhere/sometime.

While the intent of this didn't happen on unity upgrade here, at least in this case  it's easily removed if desired
[https://bugs.launchpad.net/webapps-applications/+bug/1046840](https://bugs.launchpad.net/webapps-applications/+bug/1046840)


 (- As far as the current  unity upgrade - no icons were added & not sure that it's ok to do so in an existing dev, ultimately irrelevant anyway as only the current state or upgrade from earlier release matter

---

### Post by jbicha on 2012-09-21
Yeah, today's OMG!Ubuntu! article tells how to opt-out: just uninstall unity-lens-shopping. On the other hand, if you do buy stuff from Amazon and use those links or the new Amazon webapp launcher that should be arriving this weekend, Amazon will pay a commission to Canonical which they can use to pay for the substantial expenses of Ubuntu development.

---

### Post by mc4man on 2012-09-21
> article tells how to opt-out: just uninstall unity-lens-shopping
For those that don't want it totally gone it can be filtered from the apps lens on a per session or atm  basis by choosing "local" as a source. The 'home' lens has no filtering but that doesn't matter.

There are also dconf settings related to this.. (as to who or what can integrate, ect.

> Amazon will pay a commission to Canonical which they can use to pay for the substantial expenses of Ubuntu development.
Would be nice to know if that's only on a sale or does a click thru produce some $.

(see no reason to file a bug on as Canonical is free to & should try to make money any way they can..

---

### Post by cariboo on 2012-09-21
It does generate revenue for Canonical:

> Hi Everyone,

my name is Olli Ries (olli on IRC) and I am a Director of Technology at
Canonical, responsible for most of the Canonical client upstream
projects such as Unity and web apps. In addition to a long overdue
introduction of myself I also wanted to share some updates for 12.10
that my teams have been working on.

A few new features are appearing in Ubuntu 12.10 that relate to
searching offline and online content and in some cases, generating
affiliate revenue to helps us to support the Ubuntu project. Let me
share some further details about this work and invite you to give us
feedback.

Firstly, we have been building improvements around searching and
previewing content directly from the dash (you will have seen the dash
previews already in Quantal). A new feature we have introduced extends
what was already introduced in the Music and Video Lenses, with a =93more
suggestions=94 results category that is added to searches performed from
the home dash. This helps users find content available online in
addition to what already resides on their device (thus continuing the
maturation of the dash as a viewer to different types of offline and
online content). As with the other lenses, a preview section, accessible
by right clicking on the result, will allow users to instantly view
descriptions, app ratings, music previews, purchasing options when
relevant and more, directly from the dash.

For some of this content, if a user clicks the item and purchases it, it
will generate affiliate revenue that we can invest back into the project
(in a similar way to how we generate revenue from the Firefox search
bar). We have found affiliate revenue to be a good method of helping us
to continue to invest in maturing and growing Ubuntu.

Another addition is that we will be including Launcher web apps icons to
Amazon and the Ubuntu One Music Store by default. We feel that these
icons will provide convenient access to these resources for our users
and also benefit the project with the generation of affiliate revenue in
those cases that these resources are used. If our users choose to not
use these Launcher icons, they can be easily removed by the user by
dragging the icon to the trash.

These are features we have been working on throughout this cycle, and we
apologize that it was added after Feature Freeze. Unfortunately, we had
a few complications that occurred in the development of these features
(such as some staffing adjustments and scope adjustment) and some
technical issues we needed to resolve before we felt it was ready for
inclusion. We appreciate that it is suboptimal that it is landing late,
but we are confident it will be an interesting and useful feature for
our 12.10 users.

We have been sure to take care of the necessary documentation to get
these features included after Feature Freeze. We also appreciate that
these features have not had as much testing as we would like, but we are
coordinating with Nicholas Skaggs on the Community Team to get
additional manual testing and we are continuing to building extensive
automated tests for the feature (like we do for the others features our
team delivers).

Naturally, if you have any further questions, please let me know. I am
looking forward to working closer with you.

Thanks,
Olli

I quoted the whole email for those that haven't seen it yet. Some of the formatting may seem a bit wierd due to my disappearing email problem, I had to copy and paste it directly from the mail box.

---

### Post by stinkeye on 2012-09-22
Each default lens should have an easy way to toggle online/offline searching.
eg, when I use the music lens to search my music collection I don't want to bring up unnecessary links to the U1 music store or amazon.
I should be able to toggle online searches only when wanted.
Similarly, I don't want a shopping advert when searching from the home lens,
unless I want to go shopping.
The only lens I can see which has a local source filter is the video lens.
I want to be able to search offline **or** online not
offline **and** online.

---

### Post by EgoGratis on 2012-09-22
This is a bit problematic area yes and probably there is no real answer. Generally speaking i don't think users are against producing income for Ubuntu development but generally speaking users probably don't want data from every single search operation to be send to one of the big companies that sell stuff on-line and track users.

---

### Post by exploder on 2012-09-22
Features like this are appealing to new users and it's an added plus that they generate income. We are provided so much free of charge so I do not mind such a minor inconvenience myself. I have seen so many good things coming from Canonical lately and I want them to have the revenue they need and rightly deserve.

---

### Post by stinkeye on 2012-09-22
> **exploder said:**
> Features like this are appealing to new users and it's an added plus that they generate income. We are provided so much free of charge so I do not mind such a minor inconvenience myself. I have seen so many good things coming from Canonical lately and I want them to have the revenue they need and rightly deserve.
Not against the features and may even use them.
Just would like a simple way to turn them on and off.

---

### Post by EgoGratis on 2012-09-22
I don't know if this thing has any kind of "contract/agreement" how it should be used between Canonical and "content provider" but my thoughts on the matter:

 1.) Put all available "service provider" in Unity that you think can bring some income and users are interested.

2.) Tell users why you did this. For income and to bring services closer to them.

3.) In Filters area label every singe "content provider" with button (ON/OFF) and setting should stick. If ON then show results if OFF search data must not be sent to "content provider".

This could work and when Ubuntu user is interested in Amazon stuff it enables "content provider" named Amazon and finds what he/she wants and buy it and then if he/she does not wish to send any more search data to  "content provider" named Amazon can turn "content provider" named Amazon to OFF.

If this will not work like this i imagine two things will happen:
-After Ubuntu install  "content provider" named Amazon will be UNINSTALLED.
-If it will be "hard coded" in Unity then i guess a lot of negative press against Ubuntu will be made.

Give user total control and educate him/her how to use it to benefit both sides!

---

### Post by BigSilly on 2012-09-22
> **stinkeye said:**
> Not against the features and may even use them.
Just would like a simple way to turn them on and off.

My feelings too. I don't think even the missus would appreciate being bombarded with shopping suggestions when she's trying to use the laptop. In fact I know she won't. However, my feelings are that Ubuntu should be able to make a living from their creation as it gathers popularity, and I'm not against the idea completely. I just hope they figure it out to suit everyone.

---

### Post by mc4man on 2012-09-22
If filters were provided for lens that return both local & online results that would be fine here.

Though in any event that does lead to filter options in lens not being persistent over sessions which they've declined to support in the past.

test the waters bug
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054656](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054656)

---

### Post by EgoGratis on 2012-09-22
> Though in any event that does lead to filter options in lens not being  persistent over sessions which they've declined to support in the past.

And this usually leads to UNINSTALL and beats the purpose and if "hard coded" would be next step then i guess a lot of bad press would follow.

---

### Post by sammiev on 2012-09-22
An On/Off option should be added.

---

### Post by ndejonge on 2012-09-22
I've decided to make this post to voice my disapproval of and  disappointment with your plans to integrate/display Amazon search  results in Quantal.  I've been using GNU/Linux for almost 16 years now; started with  Slackware, then Red Hat, later used Debian for many, many years, and I  switched to Ubuntu about a year ago. When Ubuntu generates revenue by providing  services and support, I'm okay with that. However, opt-out-based changes, no matter  how small, to search results or third party websites, are unacceptable  to me. I cannot support a distribution that is doing this, so even though I'm  using Xfce and not Unity, I'm going to migrate back to Debian. I may  also discourage my friends to use Ubuntu any longer.  In all honesty, thinking of what your plans may theoretically lead to,  like querying a business when doing regular searches, scares me. I'm just a single person, but I think a lot of Ubuntu users out there share my sentiments. Anyways, time for bed; tomorrow time to reinstall Debian.

---

### Post by jacksonpollack on 2012-09-22
This really raises a host of problems, from privacy (e.g. transmission my desktop search terms to Amazon) to simple usablility (e.g. more crap to sort through when I search for something specific, or showing me stuff I can't even install like Windows software). 

I understand Canonical wanting to get some revenue, but this really should be made **_opt-in._**

---

### Post by cariboo on 2012-09-22
Instead of posting here, please create a bug, and post your reasons why you think this is a bad idea. Make sure to mark it as a security issue.

---

### Post by texasboy2084 on 2012-09-22
> **ndejonge said:**
> I've decided to make this post to voice my disapproval of and  disappointment with your plans to integrate/display Amazon search  results in Quantal.  I've been using GNU/Linux for almost 16 years now; started with  Slackware, then Red Hat, later used Debian for many, many years, and I  switched to Ubuntu about a year ago. When Ubuntu generates revenue by providing  services and support, I'm okay with that. However, opt-out-based changes, no matter  how small, to search results or third party websites, are unacceptable  to me. I cannot support a distribution that is doing this, so even though I'm  using Xfce and not Unity, I'm going to migrate back to Debian. I may  also discourage my friends to use Ubuntu any longer.  In all honesty, thinking of what your plans may theoretically lead to,  like querying a business when doing regular searches, scares me. I'm just a single person, but I think a lot of Ubuntu users out there share my sentiments. Anyways, time for bed; tomorrow time to reinstall Debian.


I have been wanting to try Debian for a while, now seems a good time.

---

### Post by mc4man on 2012-09-22
I seriously doubt there are any security issues here, anyone who Says there are should at least back it up.
(similar to the unity-scope-video-remote which some may have found annoying but no security issues at all.

When a package is created it can be  described to any extent, they could have done a better job there than the current -  
> This package contains the "shopping" lens which can be used
into Unity to shop online.

---

### Post by cariboo on 2012-09-22
> **mc4man said:**
> I seriously doubt there are any security issues here, anyone who Says there are should at least back it up.
(similar to the unity-scope-video-remote which some may have found annoying but no security issues at all.

When a package is created it can be  described to any extent, they could have done a better job there than the current -

I agree with you, but many will complain, just for the sake of complaining, and not do anything about it, witness the two posters that have said they will switch to Debian, instead of taking part in the community.

---

### Post by emdeem on 2012-09-22
> **mc4man said:**
> I seriously doubt there are any security issues here, anyone who Says there are should at least back it up.

Where can I find the privacy policy that explains if or how my searches are shared with Amazon and other 3rd parties?

---

### Post by mc4man on 2012-09-22
> **emdeem said:**
> Where can I find the privacy policy that explains if or how my searches are shared with Amazon and other 3rd parties?
Not a clue other than their default PP

Now with a little searching of the lens source  find this - "http://productsearch.ubuntu.com/" , which then leads to this report

[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054677](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054677)

(so it would appear that searches go to a canonical server, though the method of may cause some concern

---

### Post by cariboo on 2012-09-22
> **emdeem said:**
> Where can I find the privacy policy that explains if or how my searches are shared with Amazon and other 3rd parties?

Try [here]("http://www.ubuntu.com/contact-us"). Note the phone numbers at the bottom of the page.

---

### Post by stinkeye on 2012-09-22
Coincidence?
Does the privacy policy allow the sharing of my UbuntuOne email address
to [**_[COLOR="DarkRed"]ISV partners[/COLOR]_**]("http://webapps.ubuntu.com/partners/isv/") of which Amazon is one.
The reason I ask is because just recently I started receiving
emails from Amazon localdeals.
Never used amazon and never had emails from them before.

---

### Post by cariboo on 2012-09-23
> **stinkeye said:**
> Coincidence?
Does the privacy policy allow the sharing of my UbuntuOne email address
to [**_[COLOR="DarkRed"]ISV partners[/COLOR]_**]("http://webapps.ubuntu.com/partners/isv/") of which Amazon is one.
The reason I ask is because just recently I started receiving
emails from Amazon localdeals.
Never used amazon and never had emails from them before.

It probably is, check the Ubuntu One Privacy Policy [here]("https://one.ubuntu.com/privacy/")

---

### Post by jbicha on 2012-09-23
> **cariboo907 said:**
> Instead of posting here, please create a bug, and post your reasons why you think this is a bad idea. Make sure to mark it as a security issue.

Please don't encourage people to file security bugs unless there is an actual security issue. People unhappy with Canonical and distro-hopping is not a security issue. I don't think a privacy bug is necessarily a security bug either.

For instance, if you publish an embarrasing picture from Shotwell to Facebook, that's a privacy issue. If Shotwell were to make it easy to accidentally do that, that's a privacy bug but it's not really a security bug.

---

### Post by cariboo on 2012-09-23
> **jbicha said:**
> Please don't encourage people to file security bugs unless there is an actual security issue. People unhappy with Canonical and distro-hopping is not a security issue. I don't think a privacy bug is necessarily a security bug either.

For instance, if you publish an embarrasing picture from Shotwell to Facebook, that's a privacy issue. If Shotwell were to make it easy to accidentally do that, that's a privacy bug but it's not really a security bug.

I understand that this is a privacy issue, but I don't trust the way some people abuse the system, by using scripts to answer some bug reports, If marking the report as a security problem gets a real person to look at the report, even if it is just to change it. I'm all for it.

I also know my suggestion is an abuse of the system, and the developers are busy, but some times we the users feel ignored, so quick action on this issue would go a long way towards making the relationship between developers and users better.

---

### Post by effenberg0x0 on 2012-09-23
<This may be completely absurd>

I'd opt-in to this if I could choose where the money would go to. 

Example: Suppose I live in FlatLand and I want the revenue I generate to go to FlatLand's LoCo latest projects:
- Buy Ubuntu-based PCs for FlatLand public school;
- Buy books or hire instructors to LoCo members that want to get into developing for Ubuntu;
 
Or maybe I want to  support some Ubuntu OLPC project in some other country.

Wouldn't it make sense that people could fund Ubuntu-related projects, LoCo's, etc and not only Canonical, if they wanted to? IMO, people should have an option to support Ubuntu directly, not *only* indirectly (through Canonical).

Regards,
Effenberg

---

### Post by awaiko on 2012-09-23
> **jbicha said:**
> Please don't encourage people to file security bugs unless there is an actual security issue. People unhappy with Canonical and distro-hopping is not a security issue. I don't think a privacy bug is necessarily a security bug either.


I'm quite new to Ubuntu and the Linux world is general, and am far less comfortable with Launchpad than with forums in general, so I'm going to express my concerns here rather than on Launchpad.

I'm really not in favour of this move from Canonical. If I'm searching using a browser, then I know that that search is public.  However, if I'm searching my hard drive, I don't want that information being helpfully sent to Amazon, or anyone else.

If this is to be happen, please please please(!) make it opt-in rather than opt-out. I know what the command line code to remove the lens is, but that's not going to be the case in general. I'd like my searches on the desktop to be private.

I'm not going to throw my hands up and yell that I'm changing distros, but this has left something of a bitter taste for me.  Anyhow, these are just my opinions as a new Ubuntu/Linux-in-general user.  I figure that I'm the target demographic (those who just need that little bit of a push), and this has definitely clouded my opinion.

(Edit: very strange. Despite this being my sixth post according to "find posts by this user", I only have one bean.  A single, solitary, lonely bean.)

---

### Post by Elfy on 2012-09-23
> **awaiko said:**
> ...

(Edit: very strange. Despite this being my sixth post according to "find posts by this user", I only have one bean.  A single, solitary, lonely bean.)

This is the only post you have made in a support forum - the other's you've posted in don't count towards beans.

---

### Post by vasa1 on 2012-09-23
" ...Don’t trust us? Erm, we have root. You do trust us with your data already."
[Quoted by OMG Ubuntu]("http://www.omgubuntu.co.uk/2012/09/mark-shuttleworth-explains-ubuntus-new-amazon-adware-feature")

---

### Post by cprofitt on 2012-09-23
For my part I would not see this as an advertisement -- it is a search results with Amazon as a source. In the future perhaps there may be other commercial sources. Would it be nice to have this be an option to turn off in the GUI or in Control Panel - yes, it would. Is it evil; no.

As far as the data goes -- I would need to see more about the technical implementation to make a comment; would I be more comfortable with encrypted data transmission; yep. Do I want to put my tinfoil hat on and run around being overly worried because it does not; no. I need more data to be sure which answer is correct.

Mark's blog post on this is here:
[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

---

### Post by cariboo on 2012-09-23
> **cprofitt said:**
> For my part I would not see this as an advertisement -- it is a search results with Amazon as a source. In the future perhaps there may be other commercial sources. Would it be nice to have this be an option to turn off in the GUI or in Control Panel - yes, it would. Is it evil; no.

As far as the data goes -- I would need to see more about the technical implementation to make a comment; would I be more comfortable with encrypted data transmission; yep. Do I want to put my tinfoil hat on and run around being overly worried because it does not; no. I need more data to be sure which answer is correct.

Mark's blog post on this is here:
[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

Thanks for the link, I'm sure it will answer most of the questions in thei thread.

---

### Post by bizz101 on 2012-09-23
I'm perfectly fine with shopping lens but not with cluttering my home lens. 

There's a bug report here where all can decide whether they are affected by this:
Don't include remote searches in the home lens
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776]("https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776")

---

### Post by stinkeye on 2012-09-24
> **bizz101 said:**
> I'm perfectly fine with shopping lens but not with cluttering my home lens. 

There's a bug report here where all can decide whether they are affected by this:
Don't include remote searches in the home lens
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776]("https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776")

According to Shuttleworth the "*Dash should let you find *anything* anywhere*" and "*Of course, you can narrow the scope of that search if you want. For example, you can hit Super-A and just search applications*".

So it appears the solution is to change the way you search in dash or remove
the shopping-lens.
I still have to remove **unity-scope-musicstores** to not get online
searches in the music lens.

---

### Post by Vaphell on 2012-09-24
sorry to say that but ubuntu team are going to shoot themselves in the foot with this Apple-esque move.

anyone willing to take the bet that once flabbergasted masses flock to forums after upgrade/fresh install with all kinds of complaints (privacy doubts, unsuitable results, poor usability due to wasted space,...), in the first 3 replies tops there will be suggestion along the lines of:
'to solve your problem once for all uninstall x, y, z and this is how you do it
<code>'

the whole fiasco will generate a lot of bad will (as if unity alone was not controversial enough) and massive wave of uninstalled lens packages will backfire (no 'commercial' lenses present - no chance for monetization **ever**)

Ubuntu used to be a sweet spot where experienced people that don't feel like tweaking their systems too much met with nooblets and helpe them get familiar with linux. The patience of these more experienced users is now wearing thin and the health of the ubuntu ecosystem will suffer if too many migrate to less annoying distros.

---

### Post by philinux on 2012-09-24
> **bizz101 said:**
> I'm perfectly fine with shopping lens but not with cluttering my home lens. 

There's a bug report here where all can decide whether they are affected by this:
Don't include remote searches in the home lens
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776]("https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054776")

Personally if I want to search amazon I'll use Firefox

---

### Post by GreatDanton on 2012-09-24
> **philinux said:**
> Personally if I want to search amazon I'll use Firefox
+1 for this.

There is no need to have another browser built in OS.

---

### Post by philinux on 2012-09-25
[http://www.iloveubuntu.net/canonicals-senior-engineering-manager-online-services-team-john-lenton-explains-amazon-decision](http://www.iloveubuntu.net/canonicals-senior-engineering-manager-online-services-team-john-lenton-explains-amazon-decision)

---

### Post by emdeem on 2012-09-25
> **bizz101 said:**
> I'm perfectly fine with shopping lens but not with cluttering my home lens.

As I continue to play with this feature, this is my conclusion as well.  The lack of an option to disable this is perplexing to me, as is the casual manner in which its supporters say "you can just uninstall it".

I use Amazon often and would probably take advantage of the ability to search the site from my desktop.  However, I do not want these results (aka ads) cluttering my home lens.  If uninstalling is my only option, I will happily do that, and Ubuntu will lose any affiliate revenue.

---

### Post by EgoGratis on 2012-09-25
[http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works](http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works)

---

### Post by arpanaut on 2012-09-25
> **EgoGratis said:**
> [http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works](http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works)

+1 to that!
Seems like some reasonable compromises are being looked at.
Yay!

---

### Post by DogMatix on 2012-09-25
> **EgoGratis said:**
> [http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works](http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works)

That would pretty much placate my personal concerns. I, as others have voiced on here, am more worried over clutter in my search results rather than any privacy issues.

---

### Post by vexorian on 2012-09-25
> **EgoGratis said:**
> [http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works](http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works)

It should teach the meta-complainers. If nobody called this out, these improvements would not happen.

There is also work being done to actually encrypt the search data.

But I still think it is better to have it disabled by default.


> **frodowiz said:**
> these are not adverts.
Oh yeah!!11

They are just intrussive unrequested suggestions to purchase products from a third party in such a way that purchasing such products give money to the party showing you those suggestions!

They are not adverts!

---

### Post by effenberg0x0 on 2012-09-25
> **vexorian said:**
> Oh yeah!!11

They are just intrussive unrequested suggestions to purchase products from a third party in such a way that purchasing such products give money to the party showing you those suggestions!

They are not adverts!

You know what, you're 100% right. And I LOL'd. Thanks :)

Regards,
Effenberg

---

### Post by BigSilly on 2012-09-26
[I think this looks pretty good]("http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works").

---

### Post by Elfy on 2012-09-26
> **BigSilly said:**
> [I think this looks pretty good]("http://www.omgubuntu.co.uk/2012/09/is-an-off-switch-for-the-shopping-lens-in-the-works").

So did Egogratis :p

---

### Post by BigSilly on 2012-09-26
> **Elfy said:**
> So did Egogratis :p

D'oh!

---

### Post by arapaho on 2012-09-26
[http://www.iloveubuntu.net/canonicals-senior-engineering-manager-online-services-team-john-lenton-explains-amazon-decision](http://www.iloveubuntu.net/canonicals-senior-engineering-manager-online-services-team-john-lenton-explains-amazon-decision)
[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

Any comments on this?
[http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works](http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works)

---

### Post by jerrylamos on 2012-09-26
How much of the purpose of Ubuntu is to run Unity/compiz vs. applications?  Maybe in the future where all notebooks/tablets have lots of processors and lots of gigabytes of memory and very long life batteries and free internet traffic?

There are comments that today's battery life is being impacted by 12.10 as more and more Ubuntu cycles are spent in unity/compiz/lens to cut battery life as reported by their notebook drops from 5 hours to 3.5 hours while even more unity/compiz features are coming.  

Fans running noticeably more.  

Internet gigabytes going up which matters if internet service has upload/download costs.

Are these just "Beta" problems or are these to be expected?

Any idea what the Ubuntu developers plan for battery life with unity/compiz/lens vs, 12,04 LTS?

Maybe there could be "opt out" choices to trim back to an efficient desktop for those who are concerned about battery life and pay for the amount of internet traffic.

I split my time between looking at Unity/compiz whose features bedazzle me - there must be experts to test the limits of those capaibilities - and logging into keep it simple stupid (me) lxde desktop.

---

### Post by BigSilly on 2012-09-26
> **jerrylamos said:**
> How much of the purpose of Ubuntu is to run Unity/compiz vs. applications? Maybe in the future where all notebooks/tablets have lots of processors and lots of gigabytes of memory and very long life batteries and free internet traffic?

There are comments that today's battery life is being impacted by 12.10 as more and more Ubuntu cycles are spent in unity/compiz/lens to cut battery life as reported by their notebook drops from 5 hours to 3.5 hours while even more unity/compiz features are coming.

Fans running noticeably more.

Internet gigabytes going up which matters if internet service has upload/download costs.

Are these just "Beta" problems or are these to be expected?

Any idea what the Ubuntu developers plan for battery life with unity/compiz/lens vs, 12,04 LTS?


Simply put, if I had these concerns, I wouldn't look at Unity. You mention yourself that you use LXDE. There are options.

Ubuntu/Unity is not going to change. This is the direction they've chosen, for good or ill. I don't agree with everything they do, but at least there are community versions of Ubuntu that offer what you are looking for. I myself have moved onto Cinnamon, which offers a nice modern desktop with a future vision, but doesn't cost the earth to run.

---

### Post by vexorian on 2012-09-26
What's the direction they've chosen? The post you quoted talks about performance issues. You are not really going to say that these grave issues are intentional and won't be ever fixed.

But... just saying, unity 6.6 has a standalone version. You can run this standalone version in metacity. Compiz is the cultprit for the slowness and the battery draining. Make a connection.

Cinnamon is great but lacks innovation. Honestly, it is time to admit that the windows 95/gnome 2 layout has aged.

---

### Post by BigSilly on 2012-09-26
> **vexorian said:**
> What's the direction they've chosen? The post you quoted talks about performance issues. You are not really going to say that these grave issues are intentional and won't be ever fixed.

But... just saying, unity 6.6 has a standalone version. You can run this standalone version in metacity. Compiz is the cultprit for the slowness and the battery draining. Make a connection.

Cinnamon is all right but lacks innovation. Honestly, the Gnome 2 layout is aged and it is time to admit it.

There's really no need to be aggressive with me. Jerry was talking about performance issues related to Ubuntu. Of course he's talking about the direction Ubuntu has taken. It's directly related!

But you're honestly preaching to the converted. I've been using Gnome Shell for some time and really enjoyed it, then spent a wee bit of time with Unity again and have to admit that it's even better. In fact I've been all over the place as I'm finding it hard to set my hat upon one particular way. I love them all. But I have to admit that even though I find the new paradigms intriguing, I still find myself taking solace in Cinnamon on a desktop PC. It doesn't feel aged or lacking innovation to me. In many ways it's the perfect step on from Gnome 2. I don't know why it has to be one vs the other.

But that's all off topic. Mods, I only furthered this to defend my POV. Apologies.

---

### Post by jerrylamos on 2012-09-26
> **vexorian said:**
> ...unity 6.6 has a standalone version. You can run this standalone version in metacity. Compiz is the cultprit for the slowness and the battery draining.Interesting.

How do I do unity 6.6 with metacity?  Now?

Thanks...

---

### Post by effenberg0x0 on 2012-09-26
The way I see it, there are two main factors we must consider:

Many of us are experienced Linux users, which got used to things like accepting configuration complexity in exchange for complete customization capabilities, less GUI and a less polished UX in exchange for performance and autonomy, just to name a few of the trade-offs. We are a few in comparison to the number of PC users globally and, whether we accept it or not, we are technically-oriented. We find our way in Linux and achieve the results we want. 

But, let's face it, that's not something we can expect from ordinary users. That's not something and employer wants it employees wasting time with, instead of doing the business as usual. That's not something OEMs will ever endorse. 

And, contrasting to that,  many of us have engaged (and still do) is discussions regarding expanding Linux adoption, making it more relevant in terms of market share and market awareness. We are always those that are quick to explain why Linux is better than the other OSs and more people should be using it.

Canonical decided to address the Linux market share issue. They are a business and they need to succeed, there's no other alternative for them. And, in order to at least try to achieve that, they directly attacked the trade-offs I mentioned above. When it comes to the desktop, I can't see how we can compete with the leading OSs if we don't try to offer a similar experience. That includes compositing, effects. And that also includes exchanging some performance for UX. 

I don't think they have the whole plan outlined, a roadmap (which I ask about frequently). No one seems to have it. It's obvious to me that they will try a lot, push many things forward and then move back according to reception. But I don't see how we could have a finished product right now or in short-term. It's an ongoing process.

IMO, Quantal is a really good product so far. It is superior to previous versions of Ubuntu and to other Linux Distros. Unity is usable and becoming better in most aspects. If you think about it (and look at the code!) it's really impressive that Unity has achieved so much so fast (considering limited funding and limited resources). I would expect a lot of refactoring in Unity targeting performance issues once the code is more mature.

Regards,
Effenberg

---

### Post by philinux on 2012-09-26
Opt out targeted for beta 2

[http://www.iloveubuntu.net/option-enabledisable-commercial-suggestions-ubuntu-1210s-unity-land-after-quantal-beta-2](http://www.iloveubuntu.net/option-enabledisable-commercial-suggestions-ubuntu-1210s-unity-land-after-quantal-beta-2)

---

### Post by vexorian on 2012-09-26
The option is an improvement over asking to remove package manually. But I still think it is better to make it opt-in (or to make ubuntu announce what is going on). While the situation is not "optimal", I find it "acceptable" now.

But in the future, there really needs to be a way to customize the dash home and decide what results to place there.

> **jerrylamos said:**
> Interesting.

How do I do unity 6.6 with metacity?  Now?

Thanks...
I can't say this, I am only quoting a post from another section of the forum, and I verified by looking logs at launchpad that there is now a standalone launcher.

Planning to get 12.10 beta 2 or maybe the release candidate and will investigate further then.

---

### Post by philinux on 2012-10-05
[http://www.omgubuntu.co.uk/2012/10/ubuntu-adds-amazon-results-off-switch-fixes-nsfw-issues?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/10/ubuntu-adds-amazon-results-off-switch-fixes-nsfw-issues?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by jerrylamos on 2012-10-05
With B2 getting a lot of "solicitations" when I log on to various sites something like "integrated ap" I forget the wording.  So B2 has a bunch of anklebiters on my 3 pc's like slower, more clutter, loused up video on Dash on one of them, lock to launcher problematic, on two pc's with two different network adapters get an "automatic disconnect" to wireless WPA instead of automatic connect, Alt-tab to terminal doesn't get flashing cursor, I forget what all else.  Distinct regression from B1 for me and what I do on netbook, notebook, tower.

No showstoppers, just anklebiters. 

Easy fix.  12.04.  

I do have B2 partitions to check for bugs on update when I'm in the mood to do battle and look at all the added candy.

I'd like opt-out on unity-lens-shopping, opt-out in integrated apps, some other stuff when I try 12.10 again.  This is 12.04.1 2D running like a champ, re-installed on all 3 test pc's.

---

### Post by IanW on 2012-10-06
To stop the integrated app solicitations in Firefox:-

Open the Tools menu & select Add-ons.
Scroll down until you find "Unity Websites Integration"
Click on "Disable" & restart Firefox

---

### Post by Cheesemill on 2012-10-06
This may be of interest:

[http://www.webupd8.org/2012/10/unity-680-released-with-option-to.html](http://www.webupd8.org/2012/10/unity-680-released-with-option-to.html)

---

### Post by MythosLegend on 2012-10-11
This lens-shopping ordeal was the final push that made me uninstall unity and replace it with gnome 3.4.1

I don't want to wait for 12.10 and I don't like using non-LTS distros.

I originally got annoyed with the buggy keyboard shortcuts not working and the "suggested" programs in ubuntu one software center.

---

### Post by philinux on 2012-10-12
More info.

[http://www.jonobacon.org/2012/10/12/further-online-dash-clarifications/](http://www.jonobacon.org/2012/10/12/further-online-dash-clarifications/)

---

