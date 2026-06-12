---
title: "U+1 Team Discussion"
date: 2014-10-09
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-10-09
The U+1 Team has been fairly dormant over the last year or so, and the ISO testing team is doing most of what the team was formed for.

Effenber0x0 hasn't been back to the Forum since October 18, 2013, and he has stopped approving new members in the team. 

I'm willing to keep things going if there is still any interest in the team, so the question is, is there enough interest in the team to keep it going?

---

### Post by grahammechanical on 2014-10-09
QA Ubuntu has improved quite a lot over the last year or so. Some of the ideas discussed during the formation of U+1 have been adopted into QA. That is good.

I still think that there is a need for targeted testing not only of the release but of packages and bug fixes. By targeted testing I mean testing on a great variety of hardware combinations by specifically inviting testers to test because they have a specific hardware combination. I have a feeling that this kind of testing will become important as Ubuntu moves off of the Xserver and on to Mir. Uses will want the special effects that come with CCSM and any replacement and any special effects will need to be tested on Mir.

As regards the flavours, whether it is Mir or some Wayland compliant compositor, it will need testing on all kinds of hardware combinations.

To give an example. I have a Nvidia GT220. With Ubuntu Desktop Next and Nouveau I get login screen bounce but with the Nvidia driver I get passed both the LightDM login screen and the phone home page login screen. It is clear that Nouveau will need patching and the move from Xserver+lightdm to Mir will need testing even on such old hardware as I have. And then there are applications like Firefox that may not run on Mir and may have to run on Xmir. It all has to be tested. 

Machine testing is fine. And it would be all that was necessary if all users were machines. But we are not. And we mess things up in a way that a machine program cannot do.

Regards.

---

### Post by ventrical on 2014-10-09
> **cariboo907 said:**
> The U+1 Team has been fairly dormant over the last year or so, and the ISO testing team is doing most of what the team was formed for.


 This is true and many in the U+1 Team are basically seconded over to Q/A when time permits. One of the drawbacks of Q/A is that to develop and involved centralized discussion on an issue or bug is passed on to other links like launchpad for example. So , what I am getting at is that the U+1 Team not only represents part of a core of volunteers in Q/A but also act as seconders to contribute 'content', mostly at ubuntuforums, and has proven valuable enough in and of itself would you not agree?

  As for the wikis .. ahh yes. I should bear most of the blame  for not streamlining them and following through on  some of effenbergs core ideas. Also , as we had discussed last spring , we had decided to try and streamline the wikis and to get rid of some redundant content and subject headings that we are not using.

 Also I have been remiss in keeping up to date the Commonly Used SUDO Commands sticky at Ubuntu_Forums Development. What may appear to be dormancy is actually me be extremely busy with customers and other responsibilities. Also , maintaining 3 KVM with 8 towers + 4 rotating candidates is a lot of work and so what may be lacking in content in the wiki is being applied on hard installs of Ubuntu current development releases. That makes me a better trouble shooter (although others may disagree).

 As November apporaches I find myself with, perhaps, a little extra time to hopefully  do some editing and updating of what I committed to do.

 As for effenberg being gone from the core, temporary or permanent, nor accepting new members, do you not have the access to admit such new members?

  On another note I also appreciate that you have to do some housekeeping here and I too like to keep things tidy, so, if you think U+1 is defunct and just taking up space in the cloud then I would have to back your decision as you are one of the original frame holders of U+1s formation.

Regards..

---

### Post by ventrical on 2014-10-09
> **grahammechanical said:**
> QA Ubuntu has improved quite a lot over the last year or so. Some of the ideas discussed during the formation of U+1 have been adopted into QA. That is good.

I still think that there is a need for targeted testing not only of the release but of packages and bug fixes. By targeted testing I mean testing on a great variety of hardware combinations by specifically inviting testers to test because they have a specific hardware combination. I have a feeling that this kind of testing will become important as Ubuntu moves off of the Xserver and on to Mir. Uses will want the special effects that come with CCSM and any replacement and any special effects will need to be tested on Mir.



I agree for the most part. The thing is if we just  refer new testers over to Q/A without a sandbox, that just doesn't make sense. I think basically that Ubuntu Development Version echo encapsulizes that sandbox. It certainly has morphed a bit , but, it represents the core idea of U+1 and so even for that reason, it, (the U+1 concept) should be kept as a viable resource dynamically. Otherwise the data and research gets fragmented and shelved and makes it that much more difficult to authenticate real bugs and vulnerabilities.

Those of us that have wearwithall left from the last snoozer of a cycle :)  <jk> may feel more enthusiastic to tackle real breakage in the next dev cycle. If we break up the spirit of U+1 it could cause chaos in Q/A and the results comming from there would be more regimental and that would exclude a plethora of proof of concept test cases which I feel would be disasterous to the overall quality of Ubuntu as the peoples choice as a rock solid free and open source alternative to Windows or other commercially based OSes.

The other question, the elephant in the room so to speak, is, are current members of U+1 who have been contributing their free time to the project still willing to carry the ball? 

Regards..

---

### Post by grahammechanical on 2014-10-09
I allowed my membership of the U+1 team to lapse because I could not see U+1 as a team going anywhere. If this poll indicates that there is sufficient interest in being members of a team like U+1 then we will need to discuss how things are going to be done and what it is we think we can achieve. I know that teams need a formal structure but teams also need to do some work. A team of community testers needs to test and produce results.

EDIT: For those looking in and do not know what we are talking about, have a look at this:

[https://wiki.ubuntu.com/U+1](https://wiki.ubuntu.com/U+1)

If anyone thinks this concept is a good idea and may be want to be part of it, then vote in the poll.

Regards.

---

### Post by ventrical on 2014-10-09
I received an e-mail notice that my U+1 account would lapse.  I went to cariboo907' launchpad site and clicked 'Join'. I am interested in keeping it going. I test and report as best as possible  with what time I have. Q/A , report there. Ubuntu Development Version (formerly known as U+1), report there.
Easy. I don't need a philosophers stone to be part of U+1.

Regards..

---

### Post by ventrical on 2014-10-09
> **grahammechanical said:**
> 

EDIT: For those looking in and do not know what we are talking about, have a look at this:

[https://wiki.ubuntu.com/U+1](https://wiki.ubuntu.com/U+1)

If anyone thinks this concept is a good idea and may be want to be part of it, then vote in the poll.

Regards.

That link is designated to be obsoleted. I have been working  with cariboo907 in early spring and we had put forth a simple and more comprehensive description of what U+1 is representative of. I think it would eliminate a lot of confusion and duplicity.

[https://wiki.ubuntu.com/U%2B1/sandbox](https://wiki.ubuntu.com/U%2B1/sandbox)

Regards..

 Edit:

The new wiki would serve as "This wiki page serves as a home base for the U+1 testing team".

 My apologies for not notifying other members about this. It was because the original founder was absent that we decided to append and parse the original wiki , however, it was not that simple as there was some sort of bug with Moin Moin and we could not edit the original headers and had to start anew.

---

### Post by cariboo on 2014-10-09
> As for effenberg being gone from the core, temporary or permanent, nor accepting new members, do you not have the access to admit such new members?

I do have administrator access to the team, and I do still add new members. The only reason this really came up, is that Elfy noticed while renewing someone, that all the memberships were set to expire on October 14, 2014. Someone has renewed all the members until October of 2015, so nobody will expire in the near future.

---

### Post by ventrical on 2014-10-09
> **cariboo907 said:**
> I do have administrator access to the team, and I do still add new members. The only reason this really came up, is that Elfy noticed while renewing someone, that all the memberships were set to expire on October 14, 2014. Someone has renewed all the members until October of 2015, so nobody will expire in the near future.

Thank you.

 For clarification purposes, may I recommend that we adopt the reformed wiki which is currently sandboxed here  [https://wiki.ubuntu.com/U%2B1/sandbox](https://wiki.ubuntu.com/U%2B1/sandbox)  as the new representative wiki of U+1 or perhaps you would like to make this an item of the current discussion also ?

Regards..

---

### Post by grahammechanical on 2014-10-10
I have no objection to the previous U+1 wiki pages being deleted. But while they are still in existence they do at least show the kind of ideas that we had in mind. And the pages may stimulate onlookers to become interested in going beyond uncoordinated testing.

Regards

---

### Post by ventrical on 2014-10-10
Controlled test cases performed in virtual machines doesn't represent a sound model of real time testing. That was proved out in this thread here :  [http://ubuntuforums.org/showthread.php?t=2246601](http://ubuntuforums.org/showthread.php?t=2246601)

 So the current q/a model is incompetent if one thinks of all the vulnerabilities it has passed on through over it's inception.

 The original wiki had high hopes.  The new recommend does in fact coordinate a more substantive real time process that can put up data for examination  in the forums. That would depend  on the developers either trusting the q/a robo-tester or coming up to the forums and source mining the data here. It may not be as expedient as q/a but certainly it is more reliable. To each their own.:)

Regards..

---

### Post by cariboo on 2014-10-10
> **ventrical said:**
> Thank you.

 For clarification purposes, may I recommend that we adopt the reformed wiki which is currently sandboxed here  [https://wiki.ubuntu.com/U%2B1/sandbox](https://wiki.ubuntu.com/U%2B1/sandbox)  as the new representative wiki of U+1 or perhaps you would like to make this an item of the current discussion also ?

Regards..

Thanks ventrical, I'd forgotten all about that page.

---

### Post by ventrical on 2014-10-10
> **cariboo907 said:**
> Thanks ventrical, I'd forgotten all about that page.

If you look over the basic preambles , which btw you wrote :) , we haven't really been all that dormant. This *cycle* has been somewhat dormant and that may have a lot to do with the fact that utopic is more or less a transitional  cycle towards eventual convergence .. etc.. in the next cycle. Also, as evidenced out in the forum, unity8 has been all but co-operative but a lot of testers are waiting in the wings ready to follow up.

 It's relatively simple. There is a  U+1 group that works well with testing in the Ubuntu Development Version forum and another group that likes to use q/a and virtual machines. I think the content that you had published in the sandbox makes those two options abundantly clear and it leaves room for other add-ons and suggestions for more involved and sophisticated testing methods, procedures and concepts of the type of which I believe grahammechcanical was eluding to.

Regards..

---

### Post by Elfy on 2014-10-10
> So , what I am getting at is that the U+1 Team not only represents part of a core of volunteers in Q/A but also act as seconders to contribute 'content', mostly at ubuntuforums, and has proven valuable enough in and of itself would you not agree?

All I would say is - search the forum and look for "Dev's don't come here often" "Wrong place to post this" "Try the dev mailing list"

So while I obviously want the forum to be at the forefront of doing this work - and I applaud all that does go on in this forum - we do both ourselves and others who would benefit from the experiences of people here at the forum if it is just here ;)

We (moderation team) would love for the forum to become more up front about what we accomplish, if that means bug reports, m/l posts etc do that - point to where we're digging at the coalface.

Thanks.

---

### Post by ventrical on 2014-10-10
The coalface is the bugs we are reporting.  Most of the bug reports originate here and the developers read the bug reports. I am sure many devs anonymously visit here :) and of course we have mac4man who has the biggest pix-axe in all Ubuntuland :) lol I see your point though.  But at least here , while we are testing isos we can freely do thought experiments and dern thats fun :)

Regards..

---

### Post by ventrical on 2014-10-10
> **Elfy said:**
> All I would say is - search the forum and look for "Dev's don't come here often" "Wrong place to post this" "Try the dev mailing list"


:) Wrong key words :) lol

Try "launchpad".

 I rest my case :)

Regards..

---

### Post by ventrical on 2014-10-10
@cariboo907

Here is the wiki I created as the *new* testers wiki. All I did was copy&paste from the old testers wiki and created some new icons. All that has to be done is change the link in the current sandbox wiki.

[https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

---

### Post by slickymaster on 2014-10-10
> **ventrical said:**
> If you look over the basic preambles , which btw you wrote :) , we haven't really been all that dormant. This *cycle* has been somewhat dormant and that may have a lot to do with the fact that utopic is more or less a transitional  cycle towards eventual convergence .. etc.. in the next cycle. <...snip...>

This ^^^
LTS+1 releases tend to be quieter.

---

### Post by grahammechanical on 2014-10-10
I have been thinking. Yes, I know it is against doctor's orders. :)

I do not know what Sandbox is, but, hey, Go Ventrical. 

I do not want to examine QA looking for ways to improve QA. I do not want to start from a position of criticism. I do want to know how a U+1 team can bring added value to Ubuntu+1 testing. I am saying that as a request for knowledge.

I know that every team needs formal structure. I hope the work done last time goes some way to meeting this requirement. So, that we can make U+1 something useful. I am willing to accept other people's ideas. I think this recent blog by Michael Hall makes some very useful points about teams/communities.

[http://mhall119.com/2014/10/the-open-source-community-is-wonderful/](http://mhall119.com/2014/10/the-open-source-community-is-wonderful/)

I have one condition. Let it be fun. It does not have to be Awesome. The Ubuntu community is awesome. Let U+1 team be fun.

Regards.

---

### Post by ventrical on 2014-10-10
> **grahammechanical said:**
> I have been thinking. Yes, I know it is against doctor's orders. :)

I do not know what Sandbox is, but, hey, Go Ventrical. 

Graham.

 All the sandbox stuff started here:  [http://ubuntuforums.org/showthread.php?t=2221153](http://ubuntuforums.org/showthread.php?t=2221153)


> 
I do not want to examine QA looking for ways to improve QA. I do not want to start from a position of criticism. I do want to know how a U+1 team can bring added value to Ubuntu+1 testing. I am saying that as a request for knowledge.

I know that every team needs formal structure. I hope the work done last time goes some way to meeting this requirement. So, that we can make U+1 something useful. I am willing to accept other people's ideas. I think this recent blog by Michael Hall makes some very useful points about teams/communities.

[http://mhall119.com/2014/10/the-open-source-community-is-wonderful/](http://mhall119.com/2014/10/the-open-source-community-is-wonderful/)

I have one condition. Let it be fun. It does not have to be Awesome. The Ubuntu community is awesome. Let U+1 team be fun.

Regards.

 My sentiments exactly.
Regards..

---

### Post by ventrical on 2014-10-10
> **grahammechanical said:**
> I have been thinking. Yes, I know it is against doctor's orders. :)

I think this recent blog by Michael Hall makes some very useful points about teams/communities.

[http://mhall119.com/2014/10/the-open-source-community-is-wonderful/](http://mhall119.com/2014/10/the-open-source-community-is-wonderful/)

I have one condition. Let it be fun. It does not have to be Awesome. The Ubuntu community is awesome. Let U+1 team be fun.

Regards.

A good read of cyber etiquette reproof at which , from time to time, I may be lacking. :)

Regards..

---

### Post by ventrical on 2014-10-13
Bump.

Your vote counts.

---

### Post by effenberg0x0 on 2014-10-13
Hi Cariboo / Everyone,


> **cariboo907 said:**
> The U+1 Team has been fairly dormant over the last year or so, and the ISO testing team is doing most of what the team was formed for.


IMHO, ISO Testing team is NOT doing what U+1 was formed for. The original idea was to gather enough people and ideas to move testing away from automated testing and ISO testing and to a more human / personal level that demands different skills and engagement from testers. Also it was supposed to be a Ubuntu Community project, completely disconnected from Canonical leadership and existing QA-related groups. It's ideologically different. 


> **cariboo907 said:**
> 
Effenber0x0 hasn't been back to the Forum since October 18, 2013, and he has stopped approving new members in the team. 


Last Thursday night (Oct. 9th) Launchpad warned me that everyone's memberships were expiring. By Friday morning I had renewed the membership for each of the 97 members for another year. And, AFAIK, I have never stopped approving memberships: I'm really sorry if I have missed someone's request - I didn't do it intentionally. If I dropped the ball with someone, please pm / email me and I'll fix it ASAP. 


> **cariboo907 said:**
> 
I'm willing to keep things going if there is still any interest in the team, so the question is, is there enough interest in the team to keep it going?


I have been through some heavy stuff in my personal life and I *had to* be away for some cycles. Sadly I just had no other option. Things are BACK on track now, I still love Ubuntu and testing and I want to restart working on our team and plans. So, yeah, let's keep it running for now while we organize and regroup. 

I'm pm'ing everyone to set some date/time so we can talk on IRC and hear everyone's thoughts on the team viability. I'm sure there's still room for some fun. 

Regards,
Effenberg

---

### Post by effenberg0x0 on 2014-10-13
Forgot to ask: Please close this poll, I'm not ending the team right now, I'll personally talk to each member first.

Thanks,
Effenberg

---

### Post by ventrical on 2014-10-13
@effenberg

 Good to see you back. Carboo907 and I had discussed here  [http://ubuntuforums.org/showthread.php?t=2221153](http://ubuntuforums.org/showthread.php?t=2221153)  what we would like to do in regards to some of the templates you had proposed for U+1 wiki.  A lot of the information was backdated and so I suggested to cariboo907 that we parse out a lot of nomenclature from the wiki because it was just not being used. Cariboo907 attempted to parse out some of the subject headers .. etc.. but we could not get in so we decided to proceed with a newer, simpler and more direct wiki approach  with add-ons and addendums possible. That means if you want to carry over some of the projects you suggested at original U+1 wiki then please feel free to do so.


  I had suggested an Instructional Development area , as which I had worked at the University of Windsor during my ComSci years there, but I have been called away to jobs, more often than not, that puts bread on the table so my time has been limited (as which is the case for most of us probably) to  work on the wikis and add significant content.

  All of this aside .. I am still a staunch supporter of your proposed original concepts/ideologies but I am of the opinion now that we should streamline the process and present a more comprehensive format as opposed to one that others may seem to be too complex. Well, if they do not see it as more complex then they are certainly welcome to add the content required in those matrices and not let them backslide and get outdated (as so many of thousands of wiki projects do).

  I urge you to read the link provided above  to get a better understanding where cariboo907 and I were at with the project . If you have already read the link then of course , your input then would be most welcome.  If you want to keep it status quo from the original framework then you have my support.  I do not speak for grahammechanical nor cariboo907  or elfy but we have been mostly the ones trying to keep the wiki process going for U+1 and I hope you see it is obvious that in needs more contributors else the larger part of the work is shouldered by the few and not the greater part of the U+1 members. I will have time from now through December to hopefully contribute more time to the project

 Regards..

Ventrical

---

### Post by ventrical on 2014-10-13
@effenberg

Here is cariboo907s sandbox revision:

[https://wiki.ubuntu.com/U%2B1/sandbox](https://wiki.ubuntu.com/U%2B1/sandbox)

and here is the new testers wiki:

[https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

What do you think?


Regards..

---

### Post by grahammechanical on 2014-10-13
@effenburg

Welcome. Nice to see you posting again. Well, I had my say in an earlier post. All I will add now is to say: Go, effenburg!

Regards from graham

---

### Post by VinDSL on 2014-10-13
> **cariboo907 said:**
> I'm willing to keep things going if there is still any interest in the team [...]

Can you please update [this page]("https://wiki.ubuntu.com/U+1/staff") please?

Pretty please?  With sugar on top...  :cool:

I signed the CoC ages ago.

---

### Post by VinDSL on 2014-10-13
> **effenberg0x0 said:**
> Hi Cariboo / Everyone
WoW!!!  \\:D/

---

### Post by ventrical on 2014-10-13
> **VinDSL said:**
> WoW!!!  \\:D/

it's like a Van Halen revival :) lol (jk)

---

### Post by effenberg0x0 on 2014-10-14
> **ventrical said:**
> @effenberg

 Good to see you back. Carboo907 and I had discussed here  [http://ubuntuforums.org/showthread.php?t=2221153](http://ubuntuforums.org/showthread.php?t=2221153)  what we would like to do in regards to some of the templates you had proposed for U+1 wiki.  A lot of the information was backdated and so I suggested to cariboo907 that we parse out a lot of nomenclature from the wiki because it was just not being used. Cariboo907 attempted to parse out some of the subject headers .. etc.. but we could not get in so we decided to proceed with a newer, simpler and more direct wiki approach  with add-ons and addendums possible. That means if you want to carry over some of the projects you suggested at original U+1 wiki then please feel free to do so.
I have no idea why but I also struggled to get access to the wiki source today. It was not moin-moin hell, some SSO error I think. Anyway, I'm in now and I backed up all the old content so I can read it while I catch up with all the new stuff (a lot has happened!). I'm reading the thread you mentioned and I completely agree with what you guys are doing. I want to pick small/effective/doable stuff from all our old ideas and try to make things that still make sense happen, a step at a time. I have a couple contributions I can make in terms of tools, stuff we talked back then that never got out of paper, and I'm coding it now. But mostly I want to contribute to anything you guys need me to while I catch up with all the new stuff.

> **ventrical said:**
> 
  All of this aside .. I am still a staunch supporter of your proposed original concepts/ideologies but I am of the opinion now that we should streamline the process and present a more comprehensive format as opposed to one that others may seem to be too complex. Well, if they do not see it as more complex then they are certainly welcome to add the content required in those matrices and not let them backslide and get outdated (as so many of thousands of wiki projects do).
Exactly...keep things simple, fast, doable. Small tasks, clear concepts, etc.  

  > **ventrical said:**
> 
I urge you to read the link provided above  to get a better understanding where cariboo907 and I were at with the project . If you have already read the link then of course , your input then would be most welcome.  If you want to keep it status quo from the original framework then you have my support.  I do not speak for grahammechanical nor cariboo907  or elfy but we have been mostly the ones trying to keep the wiki process going for U+1 and I hope you see it is obvious that in needs more contributors else the larger part of the work is shouldered by the few and not the greater part of the U+1 members. I will have time from now through December to hopefully contribute more time to the project

You guys have been doing great, I have nothing but respect for everyone's work on this, I know how hard it is to find the time(we all have jobs, etc) and that it is hard to get more people to contribute. Bear with me while I catch up to things but I can tell you right now that I have absolutely no intention to change the direction you guys took or create any difficulty. I want to support the work you have already been doing. And, also, find more people to help.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2014-10-14
> **VinDSL said:**
> Can you please update [this page]("https://wiki.ubuntu.com/U+1/staff") please?

Pretty please? With sugar on top... :cool:

I signed the CoC ages ago.
Done! :) Thank you for signing the CoC lol.
That page is ridiculously outdated, and I can't find the script I had used back then, which reads from LP and outputs moin-moin syntax... (But I will).

Regards,
Effenberg

---

### Post by sudodus on 2014-10-14
Hi,

I'm reading this thread with great interest. Except for testing, maybe I can help with a tool to make bootable pendrives for the testing. 
[URL="http://ubuntuforums.org/showthread.php?t=2245020"]
mkusb - fast, simple and safe copy from iso file to pendrive for iso testing[/URL]

---

### Post by ventrical on 2014-10-14
> **effenberg0x0 said:**
> I have no idea why but I also struggled to get access to the wiki source today. It was not moin-moin hell, some SSO error I think. Anyway, I'm in now and I backed up all the old content so I can read it while I catch up with all the new stuff (a lot has happened!). I'm reading the thread you mentioned and I completely agree with what you guys are doing. I want to pick small/effective/doable stuff from all our old ideas and try to make things that still make sense happen, a step at a time. I have a couple contributions I can make in terms of tools, stuff we talked back then that never got out of paper, and I'm coding it now. But mostly I want to contribute to anything you guys need me to while I catch up with all the new stuff.


Graham was mentioning that any team/project/community needs a centralized structure. Simply  U+1 needs a team Captain/motivator, one that delegates out the workload so to speak :) I assume you are willing to be that de-facto designee? :) 

  This then goes to the current format of how the *old*  wiki was structured. I am all for it as long as some of the topic headings are parsed out and  as I suggested in the other link to cariboo907 and the rest of what we decide to keep is updated on a regular basis .

  Take your time Al. ;)

Regards..

---

### Post by ventrical on 2014-10-14
> **sudodus said:**
> Hi,

I'm reading this thread with great interest. Except for testing, maybe I can help with a tool to make bootable pendrives for the testing. 
[URL="http://ubuntuforums.org/showthread.php?t=2245020"]
mkusb - fast, simple and safe copy from iso file to pendrive for iso testing[/URL]

I'll second that. It's obvious you have a gift for coding script projects that not many others will take up.


Regards.

---

### Post by VinDSL on 2014-10-14
> **ventrical said:**
> Simply  U+1 needs a team Captain/motivator, one that delegates out the workload so to speak :) I assume you are willing to be that de-facto designee? :)

As far as the nomenclature goes, 'Champion' works for me...  :idea:

---

### Post by ventrical on 2014-10-14
> **VinDSL said:**
> As far as the nomenclature goes, 'Champion' works for me...  :idea:

We will , we will rock U ... :)  ok .. won't go there:)

Well, I'll nominate effenberg for team captain (champ!) :)

Seconders .. ??

edit:

Actually  in wiki speak it is Team Leader (as in Mark Shuttleworth is the Team Leader of the Unity Project) but champion works for me :)

---

### Post by slickymaster on 2014-10-14
I second your nomination, ventrical.

---

### Post by ventrical on 2014-10-14
> **slickymaster said:**
> I second your nomination, ventrical.

+1 thnx slicky

---

### Post by ventrical on 2014-10-14
> **effenberg0x0 said:**
> I have no idea why but I also struggled to get access to the wiki source today. It was not moin-moin hell, some SSO error I think. 


 [s]This is a big problem. I just tired to access your original wiki[/s]  [https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions](https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions)  oh ... and now I am logged in :) wha the  .. umm . .orignally it brought me to some obscure Home page .. but when I clicked the link from the forums it logged me in .

ok .. I'll get to my other point later.

---

### Post by ventrical on 2014-10-14
One of the items I would like to point out about our current wiki is ie; The Blog

[https://wiki.ubuntu.com/U%2B1/Blog#preview](https://wiki.ubuntu.com/U%2B1/Blog#preview)

 I just updated it but I had to log in to the wiki and edit it using Moin Moin. Thats all fine and dandy .. but what if we are on the move , on the go so to speak and we just want to drop off an updated msg or an addon or a quick edit.  Is there not  a more streamlined method that members of the  U+1 team or Ubuntu wiki teams at large can leave messages on the blog-section without having to drop down to the Moin moin editor?

@VinDSL .. I know you are a masterful coder :)  What do you think? Are you familiar with moin moin at all?

Regards..

---

### Post by zika on 2014-10-14
With SystemD entering Utopic and later (and even beside(s) that) [https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions](https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions) will need some changes/corrections.

---

### Post by ventrical on 2014-10-14
> **zika said:**
> With SystemD entering Utopic and later (and even beside(s) that) [https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions](https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions) will need some changes/corrections.


That was one of my original points and I made some corrections here:


[https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

 but I hadn't added anything related to SystemD as of yet and there are still some corrections to  be made there also.  If you see anything out of line with the sudo commands (or not yet included that should be included) then I sure would welcome your suggestions.

Regards..

---

### Post by grahammechanical on 2014-10-14
I am sure that we can agree on a couple of things,

a) the times they are a changing. To quote Bob Dylan.

b) any wiki will need correction over time.

For example, I know a command to reset Compiz and a command to restart Unity but what commands will we use for Mir and Unity 8? We certainly wont be able to use startx any more. I have studied the recovery mode scripts. I am baffled by most of the script lines but I know one thing, failsafeX wont work in 16.04. A utility called Whiptail draws the menu. Will it work on Mir?

I give these as examples of changes to come to illustrate the value that we may be able to add to testing Ubuntu+1 and to finding solutions to problems that people will be looking for on this forum.

I have a question. Why are we using Moin Moin when the Community wiki pages uses HTML? Open a wiki page and view the source.

[http://mhall119.com/2014/10/unity-8-desktop/](http://mhall119.com/2014/10/unity-8-desktop/)

Regards.

EDIT: Just found this blog. We could be testing the Unity 8 desktop during the 15.10 development cycle. Not also the default password for the Ubuntu-desktop-next live session.

---

### Post by VinDSL on 2014-10-15
> **ventrical said:**
> @VinDSL .. Are you familiar with moin moin at all?

No.  I've always used MediaWiki -- same wiki engine Wikipedia uses, minus Squid.

Are there a lot of differences in the templates, and so forth?

---

### Post by ventrical on 2014-10-15
> **VinDSL said:**
> No.  I've always used MediaWiki -- same wiki engine Wikipedia uses, minus Squid.

Are there a lot of differences in the templates, and so forth?

Moin moin is not hard to learn. If you know the slightest bit of markup then moin moin should be a breeze for you. When I worked for an antimalware company in Europe I edited all the English html files and at  that time they had to be done manually in Windows using notebook.:) We've come a long way since then. Moin moin has it's limitations though but there are certain scripts which give it an advantage to have some amazing interactive features.  The idea is getting the code right to embed those features, They are a little bit touchy and one has to apply themselves to the code so to speak - to get it just right. I guess what I am asking is for you to take a look at it. You have full access to edit.

 Thing is that anything created or edited has to be done in the editor .. but I think you can download the Moin program for free and do offline edits also. Moin Moin is also the standard when applying for Ubuntu Memberships so it is very popular in Linux circles.

  I never used MediaWiki. Mabey I'll take a look there.

edit

@vinDSL
[http://moinmo.in/](http://moinmo.in/)

---

### Post by ventrical on 2014-10-15
> **grahammechanical said:**
> 

I have a question. Why are we using Moin Moin when the Community wiki pages uses HTML? Open a wiki page and view the source.


Great question. Don't know the answer offhand. I am assuming it is because of the Ubuntu (wiki) templates.

edit:

Maybe because of GNU GPL v2

[http://en.wikipedia.org/wiki/MoinMoin](http://en.wikipedia.org/wiki/MoinMoin)

 [s]and it is still using SSL !! Yikes ..[/s]

not to worry  there

---

### Post by ventrical on 2014-10-15
@effenberg

[s]Moin is still using SSL ? [/s]

[http://moinmo.in/](http://moinmo.in/)

[s]Should we be concerned .. or has it been patched over ?[/s]

Regards..

belay my last

---

### Post by cariboo on 2014-10-15
I use the [moinmoin appliance ]("http://www.turnkeylinux.org/moinmoin")from Turnkey in a vm to do things locally before making any changes to a wiki page. That way there aren't any glaring mistakes or a page that won't load due to a mistake by myself.

I personally use mediawiki for personal projects, my personal feeling is that it is much easier to use, So far the main usage is for a database of all he DVDs I own.

---

### Post by grahammechanical on 2014-10-15
When I was adding stuff to the U+1 wiki I had a page for drafts. I got things looking the way I wanted them to look and then I copied and pasted the work into the U+1 wiki.

---

### Post by VinDSL on 2014-10-15
> **cariboo907 said:**
> I personally use mediawiki for personal projects, my personal feeling is that it is much easier to use, So far the main usage is for a database of all he DVDs I own.

OMG!  Birds_of_a_feather.  That's hilarious!  :D

I have an online MediaWiki site.  Why?

[LIST=1]
[*]I like to test Wiki software and CMSs, as well as Ubu +1. MediaWiki was my favorite.
[*]I wanted to practice Wikipedia markup on my site, rather than take a beating on their site.
[*]I needed a convenient place to store/serve my screenies, in these forums and elsewhere.
[*]It's fun and easy to use.
[/LIST]

I was going to mention this last night, but didn't want to say I use MediaWiki mostly to serve pics. Overkill, eh what?

I'd use MediaWiki for my production site, but if you get a lot of traffic it'll slow to a crawl without Squid and Varnish.

---

### Post by ventrical on 2014-10-15
Using Moin Moin on the wiki.ubuntu.com servers is probably a lot more expedient and I finally figured a way to get some animations up there. Nothing fancy yet :)lol Just scroll down to Mir Testing :)


[https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

---

### Post by zika on 2014-10-16
> **ventrical said:**
> Using Moin Moin on the wiki.ubuntu.com servers is probably a lot more expedient and I finally figured a way to get some animations up there. Nothing fancy yet :)lol Just scroll down to Mir Testing :) [https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)I'm sure people that have slow connections and others will love those very informative animations. Even on a fast(er) connection and fast(er) machine they do seriosly slow down scroll of that page. What's missing is some music.

---

### Post by ventrical on 2014-10-16
> **zika said:**
> I'm sure people that have slow connections and others will love those very informative animations. Even on a fast(er) connection and fast(er) machine they do seriosly slow down scroll of that page. What's missing is some music.

  I am just trying some tests, experiments... to eventually lead into <more informative> slideshows , hopefully.

 There is a way to make them work faster on slower connects .. as I say .. I'm just sandboxing a bit.

Thanks for your input and testing that. Much appreciated. Perhaps I can even make it optional. Yet another  item to figure out.  I tried every which way to imbed youtube tabs but havn't had much luck.  I would like to put a few of those up on SystemD that are already existing.  

Regards..

Edit.

Got rid of the offending .gifs methinks:)

---

### Post by effenberg0x0 on 2014-10-16
About MoinMoin: I'm not sure when Ubuntu adopted MoinMoin to it's wiki, or what was the rationale. MoinMoin relies on files instead of storing data in a DB. My *guess* is that it was harder or too expensive to scale a DB back in the beginnings of the Ubuntu project. Those were different (cloudless) times - scaling stuff was a problem. And now, with the huge legacy of MoinMoin pages, no one will step up to convert everything to some other wiki format, like MediaWiki. So, as any official team is expected to be on wiki.ubuntu.com/<TeamName>, we're stuck with MoinMoin for the time being, sorry guys :\

One can easily find many resources on Google about projects that migrated from MoinMoin to MediaWiki (like [this]("http://dev.w3.org/2008/moinmoin2mediawiki/README.html")). If you Google for it, you'll find that many people tried to create scripts to convert MoinMoin syntax to MediaWiki, which is in essence totally doable, of course (but I couldn't find something finished and very polished). Anyway, if we wanted to hack on that, we could have a MediaWiki hosted on the team domain and work on a script to automatically convert MediaWiki code to MoinMoin and update wiki.ubuntu.com/U+1. But would it be worth the effort? We'll probably find it easier to just put up with MoinMoin and use our limited time and resources on other issues...

BTW, I had some unfinished code getting dust in my old repo that I'm updating right now. It is supposed to automatically gather info from Launchpad (i.e. team members, team members bugs, etc) and, primarily, update the Team Bug Tracker NoSQL DB. I can probably make it spit some MoinMoin and automatically update stuff like the [members_table]("https://wiki.ubuntu.com/U%2B1/staff/members_table") wiki page. At least this won't be outdated then. I'll move this code from my private git repo to [U+1 Team Code on Launchpad]("https://code.launchpad.net/~u+1") in a couple days - hopefully people will be interested in working on it, it's basic Python stuff.

Regards,
Effenberg

---

### Post by ventrical on 2014-10-16
@effenberg

MoinMoin is not all that bad. btw.. I have been experimenting with  some animations with Moin Moin.

Check here if you have time [https://wiki.ubuntu.com/devel-tester-wiki#Experiment_with_Instructional_Development](https://wiki.ubuntu.com/devel-tester-wiki#Experiment_with_Instructional_Development)

and tell me what you think and if you would like to have that at the original testers wiki. It's just a concept still in infant stages :) lol

Regards..

---

### Post by effenberg0x0 on 2014-10-16
> **ventrical said:**
> @effenberg

MoinMoin is not all that bad. btw.. I have been experimenting with  some animations with Moin Moin.
Yeah, I mean, there are some differences from MediaWiki syntax, which is what most people are used to, but the syntax is not really the problem for me. As long as the thing render pages and allows us to edit them normally, it's fine. I was kind of worried with all the errors it was outputting when I tried to save edits yesterday, and the inability to login to edit. But it probably was some temporary instability or something.

> **ventrical said:**
> 
Check here if you have time [https://wiki.ubuntu.com/devel-tester-wiki#Experiment_with_Instructional_Development](https://wiki.ubuntu.com/devel-tester-wiki#Experiment_with_Instructional_Development) and tell me what you think and if you would like to have that at the original testers wiki. It's just a concept still in infant stages :) lol

I had a look at your work, I like it. [Trololo]I have noticed that, as time passes by, I'm becoming more accepting of visual bling and less "hax0ry" stuff. I made the switch from Vim/Emacs to IDEs, from pure .txt to formatted stuff. And I even found myself watching [YouTube programming courses]("https://www.youtube.com/playlist?list=PLFE6E58F856038C69") on my TV regularly.[/Trololo] What I mean is that I now understand that people like visual stuff, why they do, and that they probably learn better from it than from text-only stuff. So I wouldn't oppose giving animations/videos/screencasts/etc a try.

Regards,
Effenberg

---

### Post by ventrical on 2014-10-16
> **effenberg0x0 said:**
> Yeah, I mean, there are some differences from MediaWiki syntax, which is what most people are used to, but the syntax is not really the problem for me. As long as the thing render pages and allows us to edit them normally, it's fine. I was kind of worried with all the errors it was outputting when I tried to save edits yesterday, and the inability to login to edit. But it probably was some temporary instability or something.



I had a look at your work, I like it. [Trololo]I have noticed that, as time passes by, I'm becoming more accepting of visual bling and less "hax0ry" stuff. I made the switch from Vim/Emacs to IDEs, from pure .txt to formatted stuff. And I even found myself watching [YouTube programming courses]("https://www.youtube.com/playlist?list=PLFE6E58F856038C69") on my TV regularly.[/Trololo] What I mean is that I now understand that people like visual stuff, why they do, and that they probably learn better from it than from text-only stuff. So I wouldn't oppose giving animations/videos/screencasts/etc a try.

Regards,
Effenberg


Thanks very much for your comments.

 While I have your attention I need to ask if we (the U+1 team) are still status quo with this preamble: [https://wiki.ubuntu.com/U+1/team-faq](https://wiki.ubuntu.com/U+1/team-faq)

 Secondly, do you still plan to remain team leader?

 I would greatly appreciate a definitive answer so as I could continue to proceed to add contents to the  original wiki structure as fits within my schedule. (meaning that I have time set aside currently for U+1). That would mean that if the current status of U+1 will be the conventional wisdom from it's inception I can then continue to get along with contributing content. If there are changes to be made (or are being made) and there is idle time during this process then I may find myself called away to other work that would make concerted contributions more sporadic and less reliable on my part.  I apologize for my impatience but I think  the above are fair questions.

Regards..

My apologies for being way off topic here to the Polls :)

---

### Post by ventrical on 2014-10-16
> **effenberg0x0 said:**
> Yeah, I mean, there are some differences from MediaWiki syntax, which is what most people are used to, but the syntax is not really the problem for me. As long as the thing render pages and allows us to edit them normally, it's fine. I was kind of worried with all the errors it was outputting when I tried to save edits yesterday, and the inability to login to edit. But it probably was some temporary instability or something.



I had a look at your work, I like it. [Trololo]I have noticed that, as time passes by, I'm becoming more accepting of visual bling and less "hax0ry" stuff. I made the switch from Vim/Emacs to IDEs, from pure .txt to formatted stuff. And I even found myself watching [YouTube programming courses]("https://www.youtube.com/playlist?list=PLFE6E58F856038C69") on my TV regularly.[/Trololo] What I mean is that I now understand that people like visual stuff, why they do, and that they probably learn better from it than from text-only stuff. So I wouldn't oppose giving animations/videos/screencasts/etc a try.

Regards,
Effenberg


  [Trololo]  With me , it was filing contact points of game-mechs on electromechanical pinball machines in the early 70's and then there was Space Invaders and uicroprocessor controlled pinball machines. No VTs .. except for Space Invaders. Just loved the Edlin editor on Dos 1.25 on my Sanyo MBC550 with Wordstar :) lol  [/Trololo]

Regards..

---

### Post by effenberg0x0 on 2014-10-16
> **ventrical said:**
> While I have your attention I need to ask if we (the U+1 team) are still status quo with this preamble: [https://wiki.ubuntu.com/U+1/team-faq](https://wiki.ubuntu.com/U+1/team-faq)
***I*** am, as I think the reasons for U+1 existence and the team goals, as defined there, still make sense. But if anyone comes to me with new ideas that improve the team and, maybe more importantly, help us organize, start producing results, grow and thrive, I'll be more than willing to compromise here and there. I founded the team but I can't play the "supreme dictator for life" role that many projects adopt. I'm uncomfortable with pushing my own ideas without the support of at least some interested members. And I'm much more attracted to hearing ideas from members and then helping then come true than the other way around. So, for example, If you think there's stuff there that is wrong, makes no sense, should be deleted or changed, and you can convince me that it will be better for the team, I'll change it.  

> **ventrical said:**
> Secondly, do you still plan to remain team leader?
No, not on the long run. As I said above, I don't believe in the "SDFL" model. I'd like leadership to rotate amongst members, in a democratic way. Moreover: I sucked as a leader so far. You for example worked a lot more than me in the last 3 cycles, as I wasn't even here and thus you definitely deserve the role way more than me. Actually for me is not about members deserving roles: it is about the team deserving the best possible leader. So, I'm very happy (and actually proud) to have created U+1, great, but I'll be happier being a contributor of something that works for the great of Ubuntu than the leader of something that does not. 

Therefore, I'm willing to pass the torch right now if someone really committed to the team volunteers (interested? :p). I would only ask the new leader to work towards establishing a system to elect and rotate team leadership as soon as possible.

 > **ventrical said:**
> I would greatly appreciate a definitive answer so as I could continue to proceed to add contents to the  original wiki structure as fits within my schedule. (meaning that I have time set aside currently for U+1). That would mean that if the current status of U+1 will be the conventional wisdom from it's inception I can then continue to get along with contributing content. If there are changes to be made (or are being made) and there is idle time during this process then I may find myself called away to other work that would make concerted contributions more sporadic and less reliable on my part.  I apologize for my impatience but I think  the above are fair questions.

My real life work load became more acceptable now, and personal life is pretty much stable, which is why I'm dedicating time to U+1 now. I can probably spend 2 or 3 entire days/week on it on at least 3 weeks/month. As far as I can see into the future, I'm able to maintain that pace for at least one year more or less (and I am gonna invest that time in U+1 being the team leader or not). 

As I said earlier in this thread, I'm trying to catch up with everything that has happened in the last cycles. A lot has changed in QA, testers, other teams, bugs, tools, Ubuntu itself. It's a lot of threads, mail archives, blogs and IRC logs to read and a lot of people to talk to. I need to do that in order to have more solid view on how I can add to the team, what I can suggest/do to help it establish itself, etc. I'll have a more solid view on all that soon. Right now the only thing I'm already working on (because it's something I always felt like it was very important for the team to work) is the team tracker code.    

> **ventrical said:**
> My apologies for being way off topic here to the Polls :)
We're forum people, we like to discuss things in threads. Our people seem to hate mailing lists and only a small portion of members likes IRC. And our theme is broad. I think it's really important that we have a thread we can use to openly discuss the team stuff. I don't think it harms the forum in any way if we keep in a single thread. If no admin is against it, I'd ask for them to allow us to spam this thread freely with U+1 Team discussion, at least while we go through all the critical stuff we need to talk about. Maybe the thread title can be changed to U+1 Team Discussion or something like that. And that way we limit all our talk to this single thread and cause no trouble to others.

Regards,
Effenberg

---

### Post by ventrical on 2014-10-16
> **effenberg0x0 said:**
>  I'm uncomfortable with pushing my own ideas without the support of at least some interested members.   

Thanks for the frank reply. I  like your ideas and concepts.  I think others do also.

> 
No, not on the long run. As I said above, I don't believe in the "SDFL" model. I'd like leadership to rotate amongst members, in a democratic way. Moreover: I sucked as a leader so far. You for example worked a lot more than me in the last 3 cycles, as I wasn't even here and thus you definitely deserve the role way more than me. Actually for me is not about members deserving roles: it is about the team deserving the best possible leader. So, I'm very happy (and actually proud) to have created U+1, great, but I'll be happier being a contributor of something that works for the great of Ubuntu than the leader of something that does not. 

Therefore, I'm willing to pass the torch right now if someone really committed to the team volunteers (interested? :p). I would only ask the new leader to work towards establishing a system to elect and rotate team leadership as soon as possible.

 Thanks for the plug. Much appreciated, but I am a terrible taskmaster. I expect too much.  I'm working on that. I would be worse than Bill Gates and Steve Jobs combined , but I can learn. Ubuntu CoC and forums has tamed me , somewhat :)lol   You have a much wider scope of diplomacy in practice. It's a gift. Accept it. :) I think you should be the defacto Team Leader for 6 months until we get back an a roll here. Then perhaps nominate/vote after the next cycle is released?

 
> 
My real life work load became more acceptable now, and personal life is pretty much stable, which is why I'm dedicating time to U+1 now. I can probably spend 2 or 3 entire days/week on it on at least 3 weeks/month. As far as I can see into the future, I'm able to maintain that pace for at least one year more or less (and I am gonna invest that time in U+1 being the team leader or not). 

As I said earlier in this thread, I'm trying to catch up with everything that has happened in the last cycles. A lot has changed in QA, testers, other teams, bugs, tools, Ubuntu itself. It's a lot of threads, mail archives, blogs and IRC logs to read and a lot of people to talk to. I need to do that in order to have more solid view on how I can add to the team, what I can suggest/do to help it establish itself, etc. I'll have a more solid view on all that soon. Right now the only thing I'm already working on (because it's something I always felt like it was very important for the team to work) is the team tracker code.    


We're forum people, we like to discuss things in threads. Our people seem to hate mailing lists and only a small portion of members likes IRC. And our theme is broad. I think it's really important that we have a thread we can use to openly discuss the team stuff. I don't think it harms the forum in any way if we keep in a single thread. If no admin is against it, I'd ask for them to allow us to spam this thread freely with U+1 Team discussion, at least while we go through all the critical stuff we need to talk about. Maybe the thread title can be changed to U+1 Team Discussion or something like that. And that way we limit all our talk to this single thread and cause no trouble to others.

Regards,
Effenberg

I still think there is a firm partnership with Ubuntuforums Ubuntu Development Version and U+1 Team. All the tests I do at UDV is in the spirit of U+1.

@Cariboo907 and all,

 I move to adopt effenbergs suggestion and rename this thread U+1 Discussion and declare him team Leader until end of next cycle . The polls have maintained an over 80% margin in favour of  U+1 remaining a team.

Are there any seconders to this motion?

Regards..

---

### Post by Elfy on 2014-10-16
Thread title changed.

---

### Post by grahammechanical on 2014-10-16
> [COLOR=#000000]No, not on the long run. As I said above, I don't believe in the "SDFL" model. I'd like leadership to rotate amongst members, in a democratic way. Moreover: I sucked as a leader so far. You for example worked a lot more than me in the last 3 cycles, as I wasn't even here and thus you definitely deserve the role way more than me. Actually for me is not about members deserving roles: it is about the team deserving the best possible leader. So, I'm very happy (and actually proud) to have created U+1, great, but I'll be happier being a contributor of something that works for the great of Ubuntu than the leader of something that does not. [/COLOR]

This is why I said earlier that I accept that there has to be a formal structure to any team. I do not want to cover old ground. A formal structure can become a "dictatorship" or just a formality. Or something in between. At the start of U+1 Effenburg was the prime mover. Then I saw a need and I failed. I could not step up to the crease (cricketing term. Well, I am English). It has been noted that at past UDS there were plenty of people saying, this should be done and that should be done. But when the question was asked, who is going to do this item on the blueprint? nobody stepped up to the plate (Baseball term?). We will see this again at the coming Ubuntu Online Summit. Please do not think about going for this summit. Let us get to base camp first. (mountaineering term).

Lets us not fuss over labels and titles. If an idea is good, then it does not matter who came up with it. If someone wants to work, then it does not matter if I think it is a waste of time. Wasting time in this way is one way of learning. Provided it is fun. If tasks are set by the team then failure is not the fault of the individual but of the team.

Regards.

---

### Post by ventrical on 2014-10-16
Actually , as the wiki stands, it is not all in that bad of shape.  There are just some segments that are outdated and ToDos that have not been done - but the original core is all there. So it is not a matter of going back to square one - it's more like we can pick up where we left off.  I do not think that any of us should beat ourselves up [thats a Canadian thing that Canadians do to themselves] :) Onwards and upwards as .. ummm . who said that :) lol

---

