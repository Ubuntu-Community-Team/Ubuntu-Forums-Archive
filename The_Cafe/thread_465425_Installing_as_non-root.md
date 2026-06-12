---
title: "Installing as non-root"
date: 2007-06-05
forum: The Cafe
---

### Post by qweqwe on 2007-06-05
please excuse me if it's not the correct forum, first of all... but i coudnt find a better one, as their names are a bit... ambiguous..(and English is not my native language, so its a bit hard for me..)
I'm using a machine that has ubuntu installed.. but i am not root. becoming superuser is not possible (not  my machine) and asking for superuser privileges to the administrator isn't a viable solution.

the problem is that i have to install some packages and software in that  machine, that will be used only by me, so I want to install everithing to a subdirectory in my home folder.

As i cant do "apt-get install " because it askes for my superuser password, and i am not a "sudoer" hehe, so i wanted to install it from source, using "apt-get source --compile".

but that way i also had problem, because I had unsolved dependencies, so I ask (before I stard building all the dependencies from source and start getting mad):
-Is there any way to install a package in a non-default default directory without superuser privileges?(with apt-get)

-How can I install a .deb package in a non default place (downloading it and installing manually in that machine)?

-how can make a source package aware that it's dependencies are already installed in a non default directory?

Thanks!

---

### Post by bodhi.zazen on 2007-06-05
If you do not have root access you are best discussing the issue with your admin.

---

### Post by Crafty Kisses on 2007-06-05
> **bodhi.zazen said:**
> If you do not have root access you are best discussing the issue with your admin.

That's the best idea, for now. :p

---

### Post by qweqwe on 2007-06-05
auch"... and if it is not possible?

is there any way to have it done?

---

### Post by jvc26 on 2007-06-05
No as your system admin has disabled root access, presumably as part of a security model, only allowing you access to those files which won't cause issues for the rest of the system, and consequently you cannot do root tasks without the admin allowing you - can't you install the apps by asking the admin to do it for you? Its part of a security thing that if you arent allowed to do something, you're not allowed to do it.
Il

---

### Post by qweqwe on 2007-06-05
but if I can compile them from source!

(i would do it if it wasn't that i don't want to get dizzy wiht dependencies, etc....)

as it seems that ther first aproach is imposible:

if I have a .deb package, how can i install it in my home directory(it seems that it is done with dpkg...)

EDIT: doing "man dpkg" i reached some options:       --root=dir | --admindir=dir | --instdir=dir

are they related with my problem?

---

### Post by jvc26 on 2007-06-05
Wont your admin have banned the installation of files, regardless whether self compiled or .deb, to wherever to stop people putting hacks/cracks/keyloggers/etc onto the computer? I'm not honestly sure of your situation, but by the sound of it the admin doesnt want you to install things so I'm sure they will have made sure that you can't.
Il

---

### Post by qweqwe on 2007-06-05
.,..:(:(

well: 
other question: in **my machine**(have superuser facilities) i  want to install things to a subdir in my home folder, to make sure that other people don't step with programs that only I use.

-How can I tell It to apt-get?
-How will that get with dependencies?how to tell them where are they installed?

---

### Post by bodhi.zazen on 2007-06-05
> **qweqwe said:**
> .,..:(:(

well: 
other question: in **my machine**(have superuser facilities) i  want to install things to a subdir in my home folder, to make sure that other people don't step with programs that only I use.

-How can I tell It to apt-get?
-How will that get with dependencies?how to tell them where are they installed?

LOL

We all understand your plight, but the issue is between yourself and your sys admin. If your program is benign your sys admin will set you up.

====

At home on your own box,

There are ways of accomplishing what you ask. Look to Google and man pages. Look at how to build from source. You will find the information your seek ...

You can either make a /bin in your home directory OR make change the permissions on system files.

Change owner from root:root to root:<user_name>

chmod 770 /bin/program

---

### Post by revprez on 2008-04-08
I have to say, the question posed here is a valid one and deserved better attention than it received.  Consider this, you work in a large company that has a large, fluid, heterogeneous development/testing/production environment with small, understaffed administrator teams responsible for servicing up to two hundred developers and maybe four times as many other users.  On top of that, this company hasn't taken a serious look at it's IT strategy in a long time, resulting in severely balkanized practices not only across developer communities, but within system admin and support as well.  This produces understandably defensive and suspicious IT types likely to frustrate the legitimate and (often) time-critical work of the developers.  In many cases, the solution grasped at by the original poster is not only an acceptable work around, it's demanded as a means of implementing alpha environments and proving deployability in lieu of stable images of production.  In my particular case, my damned work order specifies that my Perl modules will build and install under a non-root user with only that user having permissions to execute them.

That said, I don't have an answer to his question, but I'm convinced the path lies in rolling source packages in order to leave prefixes, lib and man dirs, etc., free for the user to configure later.  It's an interesting learning experience, but this is not something I should have to spend time on, damn it.  Remember, not everybody works in a shop with a friendly, uber-l33t distro hacker who will talk your ears off for hours about all the sweet stuff you can do with Unicode.  Some of us work with Red Hat certs co-located half-way across the country (if not in India).

---

### Post by bodhi.zazen on 2008-04-08
Circumventing system administration is not supported on these forums.

To answer your question, re development environments, see chroot

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

and fakeroot

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

You may also find the development sub forums helpful :

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by scorp123 on 2008-04-08
> **revprez said:**
>  In many cases, the solution grasped at by the original poster is not only an acceptable work around ...  Where I work there are very very good reasons why some people may have access to some "sudo" functions and maybe even to the "root" account and why other's don't. And if e.g. I or any of the other admins catch you messing around with this or they find you've been installing stuff you're not supposed to install we will have you fired over this "attempted computer sabotage" <== because that's what it is! That's why "me root -- you not!". 

OP wants to install stuff ... fine, he should talk to the guys with access to the "root" account then and sweet-talk them into giving him the programs he needs so he can do his job. Bribing helps too ... e.g. a free beer, invitation to lunch, tickets for a rock concert, the phone numbers and e-mail addresses of all those sweet secretaries, and so on.

Bribing your admin so he gives more priority to your requests is acceptable. You messing around with programs and trying to get the system to install stuff for you behind your admin's back clearly is not and will cost you your job.

Besides + on a technical note: I don't know how OP's admins do it ... but I configure servers which are in in "critical environments" so that the **/home** directory is mounted with the **[COLOR="Red"]noexec[/COLOR]** option ... So even if someone can somehow install something in their /home directory e.g. by compiling stuff themselves, they still cannot start any programs. And this is good. It lets me sleep at night because I know that nobody can execute anything unless I installed it :)

So if OP's admins are serious about their job they will have most likely done the same and any attempts to install programs behind their backs into /home is totally futile ... even if e.g. compilation succeeds the program will not be executable if the **noexec** mount option for /home is set :)

---

### Post by bodhi.zazen on 2008-04-08
I agree with everything scorp123 said. If you need an application or resources to perform your task you need to contact your supervisor or IT department.

---

### Post by revprez on 2008-04-14
> **scorp123 said:**
> Where I work there are very very good reasons...

Blah, blah, blah...unless you're going to list them or at least address the specific problems I've presented, who cares?  There's ONE good reason why sysadmins are working with knowledgeable enough developers to throw up loopback devices; because in a heavily mixed environment company with hundreds of developers and barely a half dozen  sysadmins there simply isn't enough manpowe to support all taskings.  In many instances, it's the developer who has to take ownership of tht project just to get it done.  In our particular case, we were tasked by all parties involved to determine a way to package install software as non-root where a VM is too much overhead.  Your job isn't to sleep well at night, it's to make sure that my boss and your boss is happy.  So just try and get me fired

---

### Post by revprez on 2008-04-14
> **bodhi.zazen said:**
> I agree with everything scorp123 said. If you need an application or resources to perform your task you need to contact your supervisor or IT department.

I have a sneaking suspicion this conversation is headed towards "you need a better IT department."

---

### Post by Tatty on 2008-04-14
I would just like to add a +1 support for scorp123's post.  

I have previously worked for places where users could not be trusted to even keep their own passwords private, or to make sure they log out of their account when they leave a computer, or even to not shut a computer down by holding in the power button.

Unfortunately in large multi-user environments, there are always a large number of people who are determined to beat the system.  Through exchanging passwords with each other, circumventing website restrictions by using proxys, trying to install all sorts of different software which they should not even be using.  The list of things I have seen people try to do goes on and on.

Ultimately it is a network administrator's job to make sure that the system is safe and secure.  If it goes down through someone installing some software they shouldnt be using then it is their job on the line.

If your employers do not want you to have control of the ability to install software on your machines yourselves (which is a very sensible thing to do) then that is their decision.  Attempting to get around  this is not going to win you friends with the IT staff and ultimately, as scorp says, is an act of sabotage.

---

### Post by Zralou on 2008-04-14
Its not often I agree with scorp, but I have to say, this time, he is right and installation issues should be approached with the OP's admin.

Sara Lou

---

### Post by scorp123 on 2008-04-15
> **Zralou said:**
> Its not often I agree with scorp  Sometimes it seems you keep attacking whatever I say just for the heck of it, regardless if whatever you claim is factually true or not. Just to remind you of yesterday's firewall thread where you and hyper_ch kept claiming things which both demonstrated both your lack of understanding of what a firewall does or doesn't and stubborn refusal to accept the truth about Ubuntu's "safety" out of the box and where precisely that secure state really comes from or doesn't come from.

I am not your enemy. But I can't help it if you keep claiming stuff that are false and technically wrong. It's simple as that.

---

### Post by scorp123 on 2008-04-15
> **revprez said:**
>  Blah, blah, blah...unless you're going to list them or at least address the specific problems I've presented, who cares?  I bet your IT department does :)

In German they have a saying: "Too many chefs will ruin a soup ... " ... What it means is obvious: Too many people having too many priviledges on too many boxes simply is a bad idea. If everybody could do whatever they wanted on the many x-1000 computers in your company ... Seriously, how is anyone supposed to keep track of this stuff then? Your managers would come screaming and jumping at your throats: because this stuff costs money. Having such a chaos means there has been lots of money thrown out of the window. No serious manager will allow that, because if too much money is thrown out it will cost everybody's job, it's simple as that.

There are other reasons, let's say security. In every company there may be people present who only temporarily work for the company: Students who do a summer job or internship ... External contractors who were hired for specific tasks, temp replacements who have to take over for colleagues who are absent (e.g. pregnancies, sick leaves, military service, etc.).

You can't give "root" access to all those folks! Who can guarantee you that they wouldn't place backdoors (with root powers you can do that!) on your machines and then hack your company whenever they please? Depending on what these folks touched a backdoor may have very dire consequences for the company and ultimately for you, your job, your income and your reputation.

So giving "root" to external people is a big big big "NO!" unless a thorough background check was done on those selected few who really need it.

I could list more reasons, but I guess you should have understood now what I meant when I wrote "there are many reasons ... ". It's not "blah blah blah". Ultimately it's about proactive damage control. You always want only as little damage to ever happen to your IT infrastructure as possible. Thus keeping administrative priviledges to a very small group of people is imperative. You simply can't have e.g. 4000 people run about your company and each and everyone do as they please on your systems.

> **revprez said:**
>  There's ONE good reason why sysadmins are working with knowledgeable enough developers to throw up loopback devices; because in a heavily mixed environment company with hundreds of developers and barely a half dozen  sysadmins there simply isn't enough manpowe to support all taskings.  In many instances, it's the developer who has to take ownership of tht project just to get it done.  Hmmm, but then wouldn't you have a dedicated development machine where you as developer can indeed be "root" and do whatever you want? That's how we do it here. I mean those systems are not "live", they are not part of the "live environment" which is visible to the outside (customers!) and to the rest of the company. They are development machines dedicated to programmers, database developers, SAP folks, and so on so they can develop and write their programs and use those machines as test and demo platforms ... I mean you don't do development work on live machines? That'd be really sick .... if that's the case your IT admins deserve a thorough and deep kick into their rear ends.

> **revprez said:**
>   In our particular case, we were tasked by all parties involved to determine a way to package install software as non-root where a VM is too much overhead.   Well ... you could create tar.gz packages or write self-extracting archives ... But given how easy it is these days to have a VM (e.g. via free tools such as VirtualBox) and how powerful present-day CPU's are I kinda fail to understand why they don't give you a VM somewhere somehow or even a dedicated development machine. Pushing you down the road "get this stuff installed but without root" is not really reasonable or very helpful at all. I think I'd have jumped off my chair had I been in that meeting.

If I were in your position I'd insist they stop pushing you down this road because it's not doing any good to anyone and preventing progress in the right directions. It's a showstopper. So either they give you proper access to "root" on whatever computers they have, or they give you a VM (where you can be "root") or they give you a dedicated development machine (where you can be "root" as well) so you can finally do your job.

> **revprez said:**
>  Your job isn't to sleep well at night, it's to make sure that my boss and your boss is happy. It may not have occurred to you: But the two things are inter-connected :) ... The better I do my job and the happier all the bosses are the better I will sleep at night, because they will not ring me in the middle of the night and order me to take care of super-urgent problems that have appeared all of a sudden. More important: Nobody will ring them in the middle of the night to complain about me and whatever I have done. Let's face it: If there is one thing bosses really hate is if they receive phone calls in the middle of the night .....  And the better I sleep the more energy and brain capacity I will have the next morning to do whatever they wish me to do to keep them happy. So nobody has to call them and they don't have to call me ... 

Work well so you can sleep well. Sleep well so you can work well.

> **revprez said:**
>  So just try and get me fired  As I said: If we catch anyone tampering with things they will find themselves in a very serious situation. Depending on what you did you will get away with a warning ... or you will be called to a meeting with lots of angered managers and representatives from the security department where you will have to explain your actions ... Or you will be fired instantly, removed from the premises of the company and face legal charges. As I said ... It all depends. I once logged into a machine I was not supposed to login into (I mistyped the hostname and was on the wrong machine all of a sudden) and kept trying to make myself "root" via the "su -" command ... So yes, all of a sudden guys from IT security where standing next to me and wanted to know WTF I was doing on their machine ... Quick explanation cleared it up and everything was OK again. Another guy who worked for us had the "wisdom" to place a reverse SSH tunnel through a firewalled zone ... and of course our intrusion detection system caught him. He received a very strong warning and was given a very thorough "talking to" and we are sure he won't repeat that stunt again. In fact since then he's become a very valuable member who strictly plays by the rules no matter what. Another guy wanted to make a backup but was too lazy to make it in the office .... so he uninstalled a harddisk from a live system (which was in a "very secure zone") and took it home .... Big mistake! The security guys at the entrance always check the luggage of the people going in or getting out of our "high security zones" and so they caught him with a harddisk containing extremely sensitive data ... which he wanted to take home. Breach of contract, breach of a non-disclosure agreement, computer sabotage, theft, ... you name it. Poor guy, but that's what you get if you don't play by the rules.

Long story short: You need to get stuff done. You need "root" access. You need to talk to your admins and if that fails escalate the matter.

But under all circumstances: Forget about doing stuff behind their backs. Regardless of pressure you experience. Just forget it. If there isn't a rule in your contract which says it's OK that you do that whatever you do which isn't totally covered by the rules and your contract might be held against you sooner or later and it's simply not worth the hassles, the risks, and all the complications that will come from this.

Sorry for this long post :)

---

### Post by revprez on 2008-04-15
> **scorp123 said:**
> I bet your IT department does :)

You've bet wrong, which you probably wouldn't have if you'd step off the soap box long enough to process the problem I've described.  Our group was specifically tasked by *all* parties involved to develop this solution.

> In German they have a saying: "Too many chefs will ruin a soup ... " ... What it means is obvious: Too many people having too many priviledges on too many boxes simply is a bad idea.

Systems administration by truism is not only bad practice, in balkanized environment it's not like you'll stay in business very long.  Virtual hosting, for example, is the practice of managed permissions spooging.  You may backtrack to your heart's content.

> If everybody could do whatever they wanted on the many x-1000 computers in your company ... 

This is a red herring, since no one is talking about root permission on x-1000 computers.

> Seriously, how is anyone supposed to keep track of this stuff then?

You've never heard of ticketing?  How small is your environment, anyway?

> Your managers would come screaming and jumping at your throats: because this stuff costs money.

Which would be no different from them coming screaming and jumping at your throat for getting in their way.  Which is precisely how I ended up where we are right now.  If IT can't get away with getting a new box or cutting a VM, then they want us to be able to run specifically what we hand them, ONLY what we hand them, with the permissions that they hand us, and they want it to be installed with as few keystrokes as possible.

> Having such a chaos means there has been lots of money thrown out of the window.

Which is why the Good Lord gave us the genius of documentation.

> No serious manager will allow that, because if too much money is thrown out it will cost everybody's job, it's simple as that.

And I'm supposed to be convinced of you've got some skill in risk and reliability assessment with this unimpressive lack of numbers?  Give me a break.  You're hand-waving at this point.

> There are other reasons, let's say security. In every company there may be people present who only temporarily work for the company: Students who do a summer job or internship ... External contractors who were hired for specific tasks, temp replacements who have to take over for colleagues who are absent (e.g. pregnancies, sick leaves, military service, etc.).

You can't give "root" access to all those folks!

Blah, blah, blah.  Name ONE person in this thread who's advocated root access of any sort in this thread.  The whole point was to find out if there was a way to roll a package so that it install in an area where a non-root user had permissions.  There's a number of reasons why you'd want that capability, including rapidly standing up developer sandboxes.  If it's okay to pull it off of version control, why the hell is it problematic to do it using deb packages?

> Who can guarantee you that they wouldn't place backdoors (with root powers you can do that!) on your machines and then hack your company whenever they please?

Who can guarantee you and the half dozen monkeys working with you won't?  Give me a break.  If you're the first and last line of defense of corporate security, then I don't have much sympathy for your company in the first place.

> Depending on what these folks touched a backdoor may have very dire consequences for the company and ultimately for you, your job, your income and your reputation.

Which is a risk every company takes when they hire anyone to do any job that touches on the fiduciary or the core area of fulfillment.  A developer could sabotage any number of applications we have to write in a way that could place my employer in both financial and legal jeopardy, and there isn't a damn thing the script kiddies in IT could do about it without a helping hand from me or one of my team members.  Our IT department doesn't function as QA or IT.  They're just the poor bastards tasked with handling what handful of the thousand of server and desktop issues a day that make it out of our shithole India call center.

> So giving "root" to external people is a big big big "NO!" unless a thorough background check was done on those selected few who really need it.

Oh now you're starting to move the goalposts.  First it was no root, ever.  Now it's no root unless you can trust the guy to bring you home after the dance.  Tomorrow it'll be "root, but only in a lofi.  Maybe in a week or so you'll actually address the problem at hand.

> I could list more reasons...

You didn't list reasons, you made vague appeals to the sky falling if users are granted root permissions.  None of this has anything to do with the question asked by the original poster or specific problem I presented later.  In fact, it was more or less just a chance for you to make a speech you've obviously been practicing too much.

> Hmmm, but then wouldn't you have a dedicated development machine where you as developer can indeed be "root" and do whatever you want?

Didn't you read the problem?  We're handing off an application to QA, they forward it to IT, and IT pushes through through to production.  We'd like to do this as push button as possible, which is another way of saying that no one--least of all IT--trusts IT to do anything more than bare minimum competently.  The VM solution we have in place is prohibitively expensive in overhead.  A version control push to production is not available yet and won't be for some time.  The only cocnern anyone has is being able to separate out the application dependencies, which we will bundle along with it, from the vanilla production environment.  This is why a non-root package installation was immediately picked up on.

> That's how we do it here. I mean those systems are not "live", they are not part of the "live environment" which is visible to the outside (customers!) and to the rest of the company.

I know what a damn live environment is.

> Well ... you could create tar.gz packages or write self-extracting archives ... 

You're getting close.  But remember when I said mixed environment?  Our IT resources are Windows Server guys learning Red Hat as they go.  This solution has to be fool proof even for them.

> But given how easy it is these days to have a VM...

You really don't read, do you?&#12288;I've already pointed out that a VM solution is prohibitive for us.

> Pushing you down the road "get this stuff installed but without root" is not really reasonable or very helpful at all. I think I'd have jumped off my chair had I been in that meeting.

I think you'd've been out the door in a week if that's your attitude.  

>  It may not have occurred to you: But the two things are inter-connected :) ... The better I do my job  and the happier all the bosses are the better I will sleep at night...

The way you describe your job, I doubt it.  And if you'd come to that meeting, demanding to restart a month long discussion so you could sleep better at night, I doubt anyone would've been terribly happy with you.

> because they will not ring me in the middle of the night and order me to take care of super-urgent problems that have appeared all of a sudden.

So let me guess, you're the type of sysadmin who pushes a new procedure into production as soon as he thinks of it, right?  Or you at least think everyone but you is too stupid not to do so.

> As I said: If we catch anyone tampering with things they will find themselves in a very serious situation.

Good for you.  Have fun in Paradise.

> Forget about doing stuff behind their backs.

What part of *all parties* did you misunderstand?

---

### Post by Zralou on 2008-04-15
> **scorp123 said:**
> Sometimes it seems you keep attacking whatever I say just for the heck of it, regardless if whatever you claim is factually true or not. Just to remind you of yesterday's firewall thread where you and hyper_ch kept claiming things which both demonstrated both your lack of understanding of what a firewall does or doesn't and stubborn refusal to accept the truth about Ubuntu's "safety" out of the box and where precisely that secure state really comes from or doesn't come from.

I am not your enemy. But I can't help it if you keep claiming stuff that are false and technically wrong. It's simple as that.

DUH!!, who is attacking who?, I made a simple statement that we don't agree all the time on certain matters, and you make an issue over it?.
Your "hollier than thou" attitude is pretty pathetic at times, ohh and there's a saying in England too:  "empty vessels make the most noise".

Sara Lou

---

### Post by bodhi.zazen on 2008-04-15
Lets tone this thread down a little. I am moving it to the Cafe as it seems to have drifted off topic.

First, if you see an inappropriate post, please report it and the moderators will look into the situation.

Second, Linux offers options and the goal of these forums is to allow discussion of the options.

Third, there is more then one way to system administration. To keep this thread on topic, if you would like to install software in a non-root location you may do so in a chroot. I have already given a link on how to do so. You may also install from source and use prefix=/usr/local.

Last, firewalls are often hotly debated. Firewalls are an accepted means of security and may have a role to play depending on your network, installed servers, and level of paranoia or security concerns. On a default Ubuntu installation there are no servers and so a firewall mmay not be needed. However, it is easy to inadvertently install a server and firewalls on a LAN can help defend against a compromised host (on your LAN).

Rather then debate or insult each other lets learn from each other.

[http://tldp.org/HOWTO/Firewall-HOWTO.html#toc2](http://tldp.org/HOWTO/Firewall-HOWTO.html#toc2)

[http://tldp.org/HOWTO/Firewall-HOWTO-2.html](http://tldp.org/HOWTO/Firewall-HOWTO-2.html)

[http://www.linuxsecurity.com/docs/LDP/Security-HOWTO/network-security.html](http://www.linuxsecurity.com/docs/LDP/Security-HOWTO/network-security.html)

---

### Post by scorp123 on 2008-04-15
> **revprez said:**
>   You've never heard of ticketing?  How small is your environment, anyway?  Very large. ;) And ticketing won't help prevent chaos one little bit if your environment is already chaotic like hell. 

> **revprez said:**
>   Which would be no different from them coming screaming and jumping at your throat for getting in their way.  Which is precisely how I ended up where we are right now.  Well, I don't know about you but there are things that I can do, things that I have to do, things that I can be pushed to do, and then there are things which I cannot be pushed to do no matter what. Especially if it's kinda asinine and totally counter-productive to be pushed down such a road. That's where I'd say "No!" (and of course backup my argument with technical reasons). Seriously, in the situation you are in it's maybe really time you stood up and said "Gentlemen: Nope! Not like this! We can't work like that!"  ... 

> **revprez said:**
>  If IT can't get away with getting a new box or cutting a VM, then they want us to be able to run specifically what we hand them, ONLY what we hand them, with the permissions that they hand us, and they want it to be installed with as few keystrokes as possible.  So they are making the installations? So you in fact could hand them a *.deb or *.rpm package and then let them install it? You'd still need a development machine of some sorts, but e.g. VirtualBox running e.g. on your laptop (I suppose you have one?) would totally suffice.

> **revprez said:**
>  Which is why the Good Lord gave us the genius of documentation.  But the Lord Almighty also created all those busy people who constantly change stuff, who forget to update the documentation, and sometimes even don't write one at all .... That's why the Devils of the IT department came up with several commandments of which one says "Thou shallest not have root access and mess with my installation!" ;)

> **revprez said:**
>  The whole point was to find out if there was a way to roll a package so that it install in an area where a non-root user had permissions.  There's a number of reasons why you'd want that capability, including rapidly standing up developer sandboxes.   That's why people use VM's or dedicated development machines for ... So you can't do that. Too bad for you then. This really sucks. But as I wrote above you then should go to those folks and tell them you can't work like that ... ? 

> **revprez said:**
>  Who can guarantee you and the half dozen monkeys working with you won't?  Because I am one of the uber-monkeys here and I will shove my bananas and other objects into their cavities and make ash trays of their monkey skulls if they make too much BS on our systems ;)

> **revprez said:**
>  If you're the first and last line of defense of corporate security, then I don't have much sympathy for your company in the first place.  Firstly it doesn't need your sympathy whatsoever and secondly I am neither the first line of defense nor the last ... I am somewhere in the middle, taking care of the area I am responsible. Why this hostility?? :confused:

> **revprez said:**
>  Now it's no root unless you can trust the guy to bring you home after the dance.  Depends on the task at hand. 99% of those "monkeys" as you called them don't really need "root" even though more than 50% of them sure would not mind having access to "root". But there are rare circumstances which make it necessary to trust a specific guy and give him access to "root" even though he is an external guy. Take applications that have to do with financial transactions. Often those apps make heavy use of encryption and tons of certificates (PEM and only God knows what else) that for security reasons are stored away in locations only accessible to "root", not to normal accounts (because someone who could get hold of the certificates could easily fake transfers and things like that). So when these guys are in the house to help you adjust some crypto settings of the relevant machines and they need to mess with the private key stores, you have not much choice but give them "root" so they can do their jobs.

> **revprez said:**
>  Maybe in a week or so you'll actually address the problem at hand.  The issue at hand is that you agreed to do something that you seem not capable of doing. Maybe you should address that immediately? I mean ... hey, it's your job. :)

> **revprez said:**
>  The VM solution we have in place is prohibitively expensive in overhead.  Talking of overhead ... your insults are overhead too. So I assume you don't want any help? Fine then. This was my last posting here.

> **revprez said:**
>  The only cocnern anyone has is being able to separate out the application dependencies, which we will bundle along with it, from the vanilla production environment.  This is why a non-root package installation was immediately picked up on.  Good luck with that, then (LOL)

> **revprez said:**
>  I think you'd've been out the door in a week if that's your attitude.   Happily I am in a position where I can dictate the terms under which I work or will not work :-D

> **revprez said:**
>  And if you'd come to that meeting, demanding to restart a month long discussion so you could sleep better at night  Oh sure, so continuing to follow a moronic path that just doesn't seem to work and keeps everybody on their feet day and night is a better solution?? Now you give me a break. LOL.

> **revprez said:**
>  Have fun in Paradise. Absolutely :-D

> **revprez said:**
>  What part of *all parties* did you misunderstand?  Your job sucks. Have a lot of fun too then :-D

---

### Post by scorp123 on 2008-04-15
> **Zralou said:**
>  DUH!!, who is attacking who?  I never attacked you. You posted stuff which was technially false. It's simple as that. I tried to put things right but you in your stubborness kept claiming stuff which simply are not true and downright wrong ](*,)

> **Zralou said:**
>  I made a simple statement that we don't agree all the time on certain matters  You are the one making an issue of it. A simple sentence such as "I agree with scorp" would have been sufficient and I would have kept quiet. But show me one posting where you didn't jump on me and started to claim incorrect things, just for the heck of it? So the reality is you never ever agree with me and you had to mention it in a thread which so totally was not related to any of the other threads. You're the one with the issues, not me, my dear.

> **Zralou said:**
>  Your "hollier than thou" attitude is pretty pathetic at times  Yeah right, you're quite the right person to say that, LOL ... And I am not "hollier than thou" but rather "often enough better informed than thou". Your problem is that you can't stand being corrected even if whatever you claimed is technically downright false.

---

### Post by Zralou on 2008-04-15
> **scorp123 said:**
> 

 ... And I am not "hollier than thou" but rather "often enough better informed than thou".

I rest my case!!! \\:D/  :KS

Sara Lou

---

### Post by revprez on 2008-04-15
> **scorp123 said:**
> Very large. ;)

I'm gonna call BS on that one unless you intend to get more specific or define very large.  A friggin web board is very large if you count all your users.

> And ticketing won't help prevent chaos one little bit if your environment is already chaotic like hell. 

Oh really?  Keeping track of issues is useless in chaotic environments.  I didn't know they were still handing out diplomas at the Zen School of Systems.

> Well, I don't know about you but there are things that I can do, things that I have to do, things that I can be pushed to do, and then there are things which I cannot be pushed to do no matter what.

The things you won't do make me wonder how the hell you found work in the first place.  The ability to adhere rigidly to a best practices book isn't exactly most marketable skill set out there, and it isn't as if there isn't a glut of H-1B guys who can do your job and then some.

> So they are making the installations? So you in fact could hand them a *.deb or *.rpm package and then let them install it? You'd still need a development machine of some sorts, but e.g. VirtualBox running e.g. on your laptop (I suppose you have one?) would totally suffice.

Your inability to keep track of the issue from one post to the next suggests to me you're exaggerating a great deal about your experience.  I've already made it clear that their motivation was to keep the underlying system as vanilla as possible.  In this case, no root installation of new software whenever possible.  The whole point of this exercise is to provide this software for the use of only one user, and do it in a way that's easily transferable between a number of distros.

> But the Lord Almighty also created all those busy people who constantly change stuff, who forget to update the documentation, and sometimes even don't write one at all ....

This is why God invented turnover.  What's your point?

> That's why the Devils of the IT department came up with several commandments of which one says "Thou shallest not have root access and mess with my installation!" ;)

Your installation?  Last I checked, your sole purpose in life was to make people who use your services as happy as possible.  Not that anyone's expected your kind to do much of that outside a few niche communities for the past two decades.

> That's why people use VM's or dedicated development machines for ... 

So you've mastered the art of pointing out things I already have.

> So you can't do that. Too bad for you then. This really sucks. But as I wrote above you then should go to those folks and tell them you can't work like that ... ?

Or I could find a fairly simple alternative to dumping a tarball into a users directory, which is the solution we went with after the one mentioned in the OP turned up nil.  This you seem unable to get your head around.  Nobody's asking you for all the ways you can install crap that will make you happy.  You were asked for a specific way to do an install and whether or not it was possible and if so how.

> Because I am one of the uber-monkeys here and I will shove my bananas and other objects into their cavities and make ash trays of their monkey skulls if they make too much BS on our systems ;)

Yada, yada, yada...and playing the Internet tough guy is supposed to convince anyone of your credibility how?

> Firstly it doesn't need your sympathy whatsoever and secondly I am neither the first line of defense nor the last ... 

Then why'd you say you were?

> I am somewhere in the middle, taking care of the area I am responsible.

Basically responsible for nothing critical at all.  Got it.

> Why this hostility?? :confused:

If I have to waste time getting to at least one remotely reasonable amidst a bunch of armchair sysadmining, I might as well enjoy it.

> Depends on the task at hand. 99% of those "monkeys" as you called them don't really need "root" even though more than 50% of them sure would not mind having access to "root".

I don't recall asking you for made-up numbers about who you think "needs" root.  I'm simply making an observation that you're moving the goal posts.

> But there are rare circumstances which make it necessary to trust a specific guy and give him access to "root" even though he is an external guy. Take applications that have to do with financial transactions.

Yes, I know.  Next you can take emerging single sign ons across recently acquired companies, or anyone doing distributed scientific computation, or companies who purchase a crapload of legacy software and systems.  The list goes on and on and my IT staff isn't getting any larger.

> The issue at hand is that you agreed to do something that you seem not capable of doing.

The issue at hand is that the original poster couldn't get an answer to a question I also had.  We've gone another, less desirable route for the time being pending further investigation.

> Maybe you should address that immediately? I mean ... hey, it's your job. :)

I'm sorry, when did you get it in your head that people put their jobs on hold just to deal with your off the wall pontificating?

> Talking of overhead ... your insults are overhead too.

Dial back the unnecessary preaching, you might get a different result.

> So I assume you don't want any help? Fine then. This was my last posting here.

Outstanding.  Have fun diddling with phpBB, superhero.

---

### Post by scorp123 on 2008-04-16
> **revprez said:**
> I'm gonna call BS on that one unless you intend to get more specific or define very large ....   You're really starting to annoy me. I don't have to prove sh** to you, I know what I know, I know what I earn and who I work for, and that isn't a "web board" you fountain of wisdom. My previous employer was Hewlett-Packard (2000 - 2007) - so that should give you an idea of the size of the company I work for now. And if you go over the the Linux Mint forums and search for postings regarding me over there it is mentioned several times also by others who know me that I was an HP employee and that I changed my job and now work for one of their competitors ... so we shall simply assume that this is a fact. 

Oh, and welcome to my ignore list. ):P

---

### Post by ssam on 2008-04-16
> **qweqwe said:**
> please excuse me if it's not the correct forum, first of all... but i coudnt find a better one, as their names are a bit... ambiguous..(and English is not my native language, so its a bit hard for me..)
I'm using a machine that has ubuntu installed.. but i am not root. becoming superuser is not possible (not  my machine) and asking for superuser privileges to the administrator isn't a viable solution.

the problem is that i have to install some packages and software in that  machine, that will be used only by me, so I want to install everithing to a subdirectory in my home folder.

As i cant do "apt-get install " because it askes for my superuser password, and i am not a "sudoer" hehe, so i wanted to install it from source, using "apt-get source --compile".

but that way i also had problem, because I had unsolved dependencies, so I ask (before I stard building all the dependencies from source and start getting mad):
-Is there any way to install a package in a non-default default directory without superuser privileges?(with apt-get)

-How can I install a .deb package in a non default place (downloading it and installing manually in that machine)?

-how can make a source package aware that it's dependencies are already installed in a non default directory?

Thanks!

This is possible.

at uni we have linux work stations that we don't have root to. we have access to out home folder, and can be given access to directories stored on an AFS network drive. most people write and compile code in this environment.

(the only thing that may stop this is if the system administrator has mounted your home as noexec. or if it not allowed by some policy)

you will not be able to use apt, because that likes to put things in specific places. (you may be able to do something fancy with a chroot, but you would basically need to make an entire copy of the system in the chroot).

so you will need to download the tar.gz packages from project websites. if you have not installed things from source before, then have a look at [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) . at the configure stage use the you can set a prefix. typically a program wants to install things in places like bin/ lib/ share/, for packages in apt the prefix generally is /usr so things go in /usr/bin, /usr/lib etc.

you want the prefix to be something something like /home/username/software, so you can do something like
```
./configure --prefix=/home/username/software
```

then you will need to change you path so that when you run your new software you dont need to type in the whole path. so put
```
export PATH=$PATH:/home/username/software/bin
```
into you .bashrc file in you home dir.

---

### Post by pazuzuzu on 2009-06-09
This bitter debate is a disservice to the helpful reputation of the Ubuntu community.  Technical questions should not receive moral answers!  

For that matter, administrators who wish to prevent users from installing software would be wise not to rely on dpkg to prevent this.  There are many other mechanisms for installing software!

In response to the question: I faced this issue myself because the admin of a machine was out of town and building NumPy from scratch is quite difficult.  The only binary available was a .deb.  I didn't want to wait for his vacation to end so I could get some work done.

To install a package to your home directory, you want to use the following command:

```
$ dpkg -i --force-not-root --root=$HOME package.deb
```

this will complain:

```
dpkg: unable to access dpkg status area: No such file or directory
```

And possibly many other complaints, as most likely your home directory does not contain the various directory structures expected by dpkg!  Try the following, which creates a "dummy" ~/var/ structure for dpkg to use:

```
$ mkdir -p ~/var/lib/dpkg/
$ touch ~/var/lib/dpkg/status
$ mkdir ~/var/lib/dpkg/updates/
$ touch ~/var/lib/dpkg/available
$ mkdir ~/var/lib/dpkg/triggers/
```

I got this far:  

```
$ dpkg -i --force-not-root --root=$HOME python-numpy-dbg_1.2.1-2~ppa1~intrepid1_amd64.deb 
couldn't open log `/var/log/dpkg.log': Permission denied
(Reading database ... 0 files and directories currently installed.)
Unpacking python-numpy-dbg (from python-numpy-dbg_1.2.1-2~ppa1~intrepid1_amd64.deb) ...
dpkg: error processing python-numpy-dbg_1.2.1-2~ppa1~intrepid1_amd64.deb (--install):
 error setting ownership of `./usr/lib/python2.4/site-packages/numpy/numarray/_capi_d.so': Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 python-numpy-dbg_1.2.1-2~ppa1~intrepid1_amd64.deb
```

It appears the .deb file is attempting to chown each file it installs to be owned by root; since my user can't do 'chown root <file>' this fails.  This behavior may be fix-able if you are clever enough to modify the .deb file's contents.

I would actually advise that a ticket be opened for the dpkg maintainers to improve the behavior of --force-non-root.

Best of luck...!

---

