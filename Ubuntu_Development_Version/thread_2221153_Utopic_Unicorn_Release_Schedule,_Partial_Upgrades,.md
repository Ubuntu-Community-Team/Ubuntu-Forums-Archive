---
title: "Utopic Unicorn Release Schedule, Partial Upgrades, and Common Questions"
date: 2014-04-30
forum: Ubuntu Development Version
---

### Post by cariboo on 2014-04-30
This is where you will find the Vivid Vervet release schedule, as well as the answers to frequently asked questions.

[Release Schedule]("https://wiki.ubuntu.com/VividVervet/ReleaseSchedule")

If you are asked to do a partial upgrade, please read this first:

[Partial upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")

There always are many questions about what to do and how to do thngs during a release cycle:

[Common problems]("https://wiki.ubuntu.com/U%2B1/common-problems")

Warning: Unless you are willing to have a broken system, please make sure that that Pre-released updates are disabled in Software & Updates, as this repository is now used as a holding area while packages are waiting for dependencies to be built. See attached thumbnail.


If you are looking for the Daily iso's, have a look here:

[Ubuntu]("http://cdimage.ubuntu.com/daily-live/current/") 
[Kubuntu]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/") 
[Xubuntu]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/")
[Lubuntu]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/") 
[UbuntuGnome]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/") 

As many of you may know we have created a U+1 testing team to do a better job of reporting bugs, and generally to make things better for all during the testing cycle. To that end, we have created a wiki where a lot of information regarding testing is available. You don't have to be a team member to be able to test , testing is open to everyone regardless of your experience level. That being said, to get the most possible feedback from your bug reports, check this out, before creating a bug report:

[Create a good bug report]("https://help.ubuntu.com/community/ReportingBugs") 

Here are some more useful links:

[Vivid Changes Mailing List]("https://lists.ubuntu.com/mailman/listinfo/vivid-changes") 

[Ubuntu Developers]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") 

[Unity Design Discussion]("https://unity.ubuntu.com/getinvolved/")

---

### Post by ventrical on 2014-05-02
> **cariboo907 said:**
> 

As many of you may know we have created a U+1 testing team to do a better job of reporting bugs, and generally to make things better for all during the testing cycle. To that end, we have created a wiki where a lot of information regarding testing is available. You don't have to be a team member to be able to test , testing is open to everyone regardless of your experience level.

 Are you referring to :

[https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions](https://wiki.ubuntu.com/U+1/tester-wiki#Sudo_Code_Definitions)

because I did not see it linked.

I don't mind maintaining  the page but I am not sure if it is getting much traffic/visits.

Your thoughts?

@grahammechanical

 Are you still interested in contributing to the testers wiki or do you think it is redundant?

Regards..

---

### Post by cariboo on 2014-05-02
I plan on revising that section, but I thought I'd get the sticky up asap.

---

### Post by ventrical on 2014-05-03
@elfy

Thanks for updating the .iso daily-live :)

@cariboo907

I can make the wiki info intensive or keep it honed down. Please keep me apprised.

Thanks

---

### Post by ventrical on 2014-05-03
My recommend for parse:

Blog
News
Agenda
Reports
Brainstorming

---

### Post by ventrical on 2014-05-03
I am not familiar how to edit this section.

---

### Post by Elfy on 2014-05-03
> **ventrical said:**
> @elfy

Thanks for updating the .iso daily-live :)

...

/me has a note to go back and fill in for the flavours :)

---

### Post by ventrical on 2014-05-03
> **Elfy said:**
> /me has a note to go back and fill in for the flavours :)

:)

While I have your attention, could you give me a pointer about how to edit the  header  section?

I want to sort of trim it down (my recommend).

It's this one here. 

It's all very well with me if we do not choose to parse out those other sections. When I get some extra time I can revise them.

---

### Post by Elfy on 2014-05-03
I was just having a quick looking actually- not at all sure, didn't have time to dig very deep tbh just at the moment.

---

### Post by ventrical on 2014-05-03
@elfy,cariboo907


> **ventrical said:**
> My recommend for parse:

Blog
News
Agenda
Reports
Brainstorming


Actually , if I may recommend, that we can change these to other pertinent and more current topics such as 'Mir' , 'Unity8' , 'Wayland' and 'Weston'.   I could easily put these up in the testers-wiki area but I would rather keep that section more for  noob testing , sudo commands and links to current Utopic subjects.

 My reasoning to want to have these parsed out or changed is that they are not getting much traffic or interest by the team in general. Perhaps others anonymous may have found them helpful but I see that other areas within the wiki in general can be utilized to cover those remaining items.  It is just a knack with me .. my training in Com-Sci many years ago ingrained economics and efficiency .. ya know .. "smaller is better" :) lol

---

### Post by ventrical on 2014-05-03
> **Elfy said:**
> I was just having a quick looking actually- not at all sure, didn't have time to dig very deep tbh just at the moment.



 I think only the team leader (cariboo907)  can change those.

---

### Post by Elfy on 2014-05-03
I'm not the best person to ask - I've not seen that wiki for ages :p

I spend more time in IRC,trackers and bzr of late ...

---

### Post by ventrical on 2014-05-03
Ok.. I found where to edit the "NavBar". effenberg used  a Kubuntu style flavor to <include> the navbar.

[https://wiki.kubuntu.org/U%2B1/Resources/NavBar](https://wiki.kubuntu.org/U%2B1/Resources/NavBar)

However, I am getting verbose script rolls every time I try to log-in.

---

### Post by ventrical on 2014-05-03
> **Elfy said:**
> I'm not the best person to ask - I've not seen that wiki for ages :p

I spend more time in IRC,trackers and bzr of late ...


Thanks for your reply. I know you are up to your ears in it all :) lol err ..pointed ears that is ! :)

---

### Post by Elfy on 2014-05-03
that looks like an openid login fail if ever I saw one :p

---

### Post by ventrical on 2014-05-03
> **Elfy said:**
> that looks like an openid login fail if ever I saw one :p


 Unless anybody else has a fix I  (or someone else) could perhaps create a new Ubuntu navbar wiki, exclude out the old one and include the new one. It would be the most expeditious way. I would have to read up on creating a navbar. I am assuming that the old navbar wiki is nonfunctional because it has not been updated ?

Any ideas.

My aplogies if I am off topic.

---

### Post by ventrical on 2014-05-03
> **Elfy said:**
> that looks like an openid login fail if ever I saw one :p


 I created a new account on a different system , then, it at least led me to the login window. After entering my info I got the verbose script page again.

---

### Post by cariboo on 2014-05-03
I can have a look at it either later today, or if not then on my days off, Tuesday or Wednesday. I know Effenberg0x0 checks in once in a while, but I think he is still dealing with personal (real life) problems.

---

### Post by ventrical on 2014-05-03
> **cariboo907 said:**
> I can have a look at it either later today, or if not then on my days off, Tuesday or Wednesday. I know Effenberg0x0 checks in once in a while, but I think he is still dealing with personal (real life) problems.

Thanks for your help cariboo907.

Regards..

---

### Post by cariboo on 2014-05-05
@ventrical, I had a look at the NavBar code, and it looks like a bit of a dogs breakfast, it's going to take a bit of time to sort it out, I'll have to install a local instance of Moin-moin in order to make any sense of it.

---

### Post by ventrical on 2014-05-05
> **cariboo907 said:**
> @ventrical, I had a look at the NavBar code, and it looks like a bit of a dogs breakfast, it's going to take a bit of time to sort it out, I'll have to install a local instance of Moin-moin in order to make any sense of it.


 Thanks for getting back. In the meantime I have started the process of creating a new wiki page which will deal only with testing aspects of this (14.10) cycle. It is simple copy and paste of what I had already put up in the testers-wiki area but I'll have to redo some parts of it and upload some new attatchments. (moving and copying current attachments doesn't seem to work atm). I will most likely  include some subjects such as Mir, Weston , Unity8 and Wayland testing.

 I'll keep an eye on this and if you come up with an edit  to the navBar I'll contribute there also. Whether or not it makes any sense at this duplicity  it does keep my MoinMoin skills sharpened :)

Regards..

---

### Post by ventrical on 2014-05-05
I copied this subject and created a new wiki called devel-testers-wiki.  It is sort of like a back up. I know you are busy   so take your time deciphering that NavBar. :)

[https://wiki.ubuntu.com/devel-tester-wiki](https://wiki.ubuntu.com/devel-tester-wiki)

---

### Post by Smask on 2014-05-06
I decided to switch to devel on one of my computers. I forgot that I loaded the updates from the Swedish server (se.*). The usual sed trick on sources.list got me partial upgrades galore when I upgraded. I upgraded what I could. There was a handful of packages that weren't authenticated and therefore wouldn't install. 

Software-properties-gtk said that I loaded packages from the main server but going thru the Other Software tab told me that I still loaded my packages from the Swedish Server. After removing a bunch of "se." from the repository URLs and reloading the database, I got 380 packages waiting to be upgraded.

Maybe put a note in the wiki to make sure you load the packages from the main server.

---

### Post by ventrical on 2014-05-06
> **Smask said:**
> I decided to switch to devel on one of my computers. I forgot that I loaded the updates from the Swedish server (se.*). The usual sed trick on sources.list got me partial upgrades galore when I upgraded. I upgraded what I could. There was a handful of packages that weren't authenticated and therefore wouldn't install. 

Software-properties-gtk said that I loaded packages from the main server but going thru the Other Software tab told me that I still loaded my packages from the Swedish Server. After removing a bunch of "se." from the repository URLs and reloading the database, I got 380 packages waiting to be upgraded.

Maybe put a note in the wiki to make sure you load the packages from the main server.

Yes .. that happened on one of my installs where I got the Canadian server. I had to switch to Main to get all the updates. Many servers are somewhat behind. 

Will do .. your suggestion.

Regards..

---

