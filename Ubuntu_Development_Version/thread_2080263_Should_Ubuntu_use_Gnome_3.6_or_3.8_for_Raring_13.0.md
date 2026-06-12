---
title: "Should Ubuntu use Gnome 3.6 or 3.8 for Raring 13.04 ?"
date: 2012-11-03
forum: Ubuntu Development Version
---

### Post by Stinger on 2012-11-03
Here we go again, the never ending debate ;)

[http://www.webupd8.org/2012/11/ubuntu-1304-only-some-gnome-components.html]("http://www.webupd8.org/2012/11/ubuntu-1304-only-some-gnome-components.html")

What do you want from Ubuntu between the long term releases ?

Stability would mean to follow Gnome releases one step behind.

Progression would mean to keep up the pace with the Gnome releases and use the current development version (which eventually will become 3.8 )

I personally would like progression because I use the [UGR]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/") and would be sad to see UGR following Gnome one step behind Fedora.

I can understand, from the Ubuntu perspective, it would be better to follow one step behind and concentrate the development on Unity, but I dislike the fact that Unity will be locking the Gnome version in Ubuntu.

Maybe it's time to jump ship to follow Gnome ?
I used to love Ubuntu when Gnome was the default desktop, but that all changed with Unity.

What do you want from Ubuntu ? Gnome 3.6 or the current development version that will become 3.8 ?

---

### Post by Chdslv on 2012-11-03
None of them. They should either make the extension by themselves or go back to 3.4.1, which has lot of extensions which make the gnome-shell work. They should make an Ubuntu based Gnome distro, rather than a Fedora one, which is always buggy. The Fedora one would say "Oh no!Something has gone wrong."

On the other hand, if Ubuntu is not going to help/sponsor the Ubuntu-Gnome Remix, it can use any Gnome 3 variant.

---

### Post by grahammechanical on 2012-11-03
This is the main point of your reasoning is it not?

> I used to love Ubuntu when Gnome was the default desktop, but that all changed with Unity.

You want Ubuntu to be a Gnome distribution through and through, including Gnome shell for the user interface. Notice these point:

> tracking unstable GNOME is taking lot of resources

GNOME unstable series and Ubuntu "working every day" are hard to conciliate goals

GNOME is not communicating early enough on what is coming for us to discuss next cycle at UDS (see nautilus 3.6 in quantal)

GNOME is shipping stables with transitions half done (see gstreamer 1.0 this cycle) which is not something we want in Ubuntu

Our "feedback loop" with GNOME is not really working nowadays

I do not understand why you claim that Gnome 3.8 is the current release. 

According to this link, Gnome 3.7 is the unstable development series meant for testing and hacking purposes. It does not turn into stable Gnome 3.8 until 27th March 2013. Which leaves very little time to integrate it into Ubuntu 13.04.

[https://live.gnome.org/action/show/ThreePointSeven]("https://live.gnome.org/action/show/ThreePointSeven")

Cooperation has to work both ways. Otherwise it is not cooperation. If the Gnome organisation people had been a little more cooperative 18 months ago then Ubuntu would now be available with a choice of UI - Gnome shell or Unity as a standard offering. In my opinion.

---

### Post by Mr. Picklesworth on 2012-11-03
I was opposed to this at first but the reasons discussed in the session made me a lot happier. Ubuntu's number one focus needs to be the users, and if we can build a better operating system by following GNOME a release behind, it's the right choice, and a non-LTS release is the right time to test that.

Of course, it remains to be seen if that will happen. I'm still concerned that we could end up with something unsustainable as Ubuntu-specific projects continue in their own directions irrespective of GNOME, possibly resulting a worse technical situation than we started with as the negative effects take a whole release to materialize.

On the other hand, this provides a great opportunity to integrate stuff properly so Unity stops being so brazenly incompatible with GNOME. Now Nautilus and Control Centre are being updated to 3.6, and there's a whole six months to consider how Unity copes with these things and get it all nice and tidy. (For example: try to look for settings in the same place as upstream; behave sensibly with GApplication menus; add new settings panels instead of patching existing ones to behave completely differently; and turn some of those old settings applications into proper settings panels). Since collaboration is a little limited, that could be a lot more manageable when GNOME isn't a moving target.

I'm certainly hoping for the latter possibility, even if it means old GNOME for a while ;)

---

### Post by screaminj3sus on 2012-11-03
My longest standing problem with ubuntu has always been: bugs, bugs, bugs. They need more stable, polished releases badly, and if this helps with that then I am for it.

---

### Post by sammiev on 2012-11-03
> **screaminj3sus said:**
> My longest standing problem with ubuntu has always been: bugs, bugs, bugs. They need more stable, polished releases badly, and if this helps with that then I am for it.

+1 Very well said.

---

### Post by Stinger on 2012-11-03
> **grahammechanical said:**
> This is the main point of your reasoning is it not?

You want Ubuntu to be a Gnome distribution through and through, including Gnome shell for the user interface. 

One can always hope that Mark wakes up one day and embraces Gnome instead of pulling it to pieces ;)
But one has to be realistic too and that's not gonna happen in near future.:rolleyes:

No you are quite wrong, that's not the main point, the main point is, why not let us play with a upstream Gnome development release between the long term releases from Ubuntu ?
This would benefit both Unity ( for Gnome compatibility and integration ) and Gnome for better bug reporting ( more users to test Gnome ).


I think it could be a win win scenario :D But I might be wrong.

---

### Post by Chdslv on 2012-11-03
> **grahammechanical said:**
> According to this link, Gnome 3.7 is the unstable development series meant for testing and hacking purposes. It does not turn into stable Gnome 3.8 until 27th March 2013. Which leaves very little time to integrate it into Ubuntu 13.04.

Oh, someone would make a gnome 3.8 ppa within hours and would be ready with that ppa, before the Ubuntu release date.:)

Gnome 3.7.1 is in the Raring repos already.

---

### Post by Harry33 on 2012-11-04
> **Chdslv said:**
> Oh, someone would make a gnome 3.8 ppa within hours and would be ready with that ppa, before the Ubuntu release date.:)

Gnome 3.7.1 is in the Raring repos already.

Actually it is Gnome 3.6.1 - 3.6.2 which is in Raring official repos ATM.

However, the git versions of some Gnome 3.7.1 applications can be found from certain PPA's, like Gnome Testing PPA (Ricotz).

Gnome 3.7.1 is the development route leading to the final 3.8.0.

---

### Post by serdotlinecho on 2012-11-04
ubuRR with gnome-shell 3.6 for quality and stability throughout development cycles. Or adding ricotz testing ppa if you want to use bleeding edge gnome 3.7. But I'm still like and using Unity as main desktop :D

---

### Post by ronacc on 2012-11-04
There are valid arguments to favor both possible paths .Since 13.04 is not an LTS my preference would be to go the 3.8 way , otherwise Ubuntu will be 2 steps behind (as far as Gnome is concerned ) at release . By starting the work of getting things polished with the version of Gnome that will be the current one at release time we will have a head start on getting things right for the next LTS which is the whole point of these testing releases .

---

### Post by Stinger on 2012-11-04
> **Harry33 said:**
> Actually it is Gnome 3.6.1 - 3.6.2 which is in Raring official repos ATM.

However, the git versions of some Gnome 3.7.1 applications can be found from certain PPA's, like Gnome Testing PPA (Ricotz).

Gnome 3.7.1 is the development route leading to the final 3.8.0.
Exacly my point.
Why not have 3.7.1 in the main repos to test ? We already have gnome 3.6 in Quantal.
I feel Unity is holding development back, I don't think we need stability between the long term releases.
Earlier we learned that: 
"The Release schedule has dropped all alphas, and the first beta, resulting in a beta and then final release milestone only."
[You can see the post here under 'releases']("http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html")
AFAIK that's not indicating stability.

---

### Post by ronacc on 2012-11-04
exactly the point  I was trying to make in my post just above but you stated it better;)

---

### Post by dino99 on 2012-11-04
Why all these comments ? Decisions have been already made:
RR is for bringing quality, getting time to resolve not yet fixed issues with the specific ubuntu archives, like unity, compiz, upstart, ..., and not to be disturbed by bleeding edge stuff asking too much efforts while upstream is still moving ahead.
I fully agree with such decisions, they are needed, and will let go ahead via ppas anyway.

---

### Post by kansasnoob on 2012-11-04
IMHO every final release should be "stable". Quite often we look at LTS as something it's not. LTS means "long term support" - not more stable out-of-box!

As mentioned previously we're changing test cycles drastically, I still don't quite understand "cadence testing", but if Ubuntu is still going to use a "gnome base" then maybe we should also change our release cycle.

Maybe we should go something more like 13.06 / 13.12 / 14.06 etc.

Would that put us closer into sync with Gnome dev :confused:

Remember that Dapper was an ".06" :)

OTOH maybe Ubuntu would rather be far removed from Gnome dev ...... I dunno :confused:

---

### Post by dino99 on 2012-11-04
If you think and look back a bit, let say, since karmic where we started to do huge changes (hal, udev, apparmor,...) Ubuntu has always used the latest/upstream packages, and sadly have cumulated ton of reports, with alot of "expired" due to lack of time to investigate these bugs, waiting for new version instead of fixing.

So i does not be scared by a little pause using "stable" packages by default; and setting the upstream availlable via ppas is the best choice IMHO.

---

### Post by Stinger on 2012-11-04
> **dino99 said:**
> Why all these comments ? Decisions have been already made:
RR is for bringing quality, getting time to resolve not yet fixed issues with the specific ubuntu archives, like unity, compiz, upstart, ..., and not to be disturbed by bleeding edge stuff asking too much efforts while upstream is still moving ahead.
I fully agree with such decisions, they are needed, and will let go ahead via ppas anyway.
Well Unity has been along for quite a while now, please tell me how long do we have to put up with 'stabilizing unity' and compiz for that matter.
I think those decisions are wrong and will only lead to further breakage ( and maybe more commercial lenses ), you are just putting off issues that you sooner or later will have to deal with.
As a side effect of that, [UGR]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes") will have to follow Gnome one release behind too.

---

### Post by kansasnoob on 2012-11-04
> **Stinger said:**
> Well Unity has been along for quite a while now, please tell me how long do we have to put up with 'stabilizing unity' and compiz for that matter.
I think those decisions are wrong and will only lead to further breakage ( and maybe more commercial lenses ), you are just putting off issues that you sooner or later will have to deal with.
As a side effect of that, [UGR]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes") will have to follow Gnome one release behind too.

And some package breakage is almost unforgivable:

[http://ubuntuforums.org/showthread.php?t=2074321](http://ubuntuforums.org/showthread.php?t=2074321)

Canonical can't use the "stability" excuse when they still release broken packages like that.

The fact is that we've always just played "pick-n-choose" when it comes to what version of what package get's included ............ quite often with inadequate testing.

And I personally believe the new testing sequence is bound to make things much worse :cry:

---

### Post by grahammechanical on 2012-11-04
It became Ubuntu policy before the Precise development cycle for the development branch to be stable throughout the cycle. This failed during Quantal. It led me to the conclusion that Ubuntu has Quality Assurance but not much Quality Control.

This would not be much of a problem if there was not an open invitation for anyone to download the development branch. It could lead to the perception that latest release of Ubuntu is buggy even before it is released. And it could also be buggy after it is released if experimental packages from upstream are put in the repositories without being fully tested.

I think that more use should be made of community volunteer testers to put code under test before it gets into the update repositories. I read somewhere, I have tried to find where, but have failed) that during RR packages will go into the proposed repository before being brought into the main repository.

I have noticed that some of us are able to bring in experimental kernels, video drivers, and stuff like that. So, why insist that this be done officially? 

Regards.

---

### Post by ventrical on 2012-11-04
I hear a little bit of anti-unity tones here in this thread. I'm not complaining,[I]I'm just making a note. Unity (on my units) has worked exceptionally well. Unity 2D is just amazing (and will continue to be along with the rest of the Precise cycle.)  I would have hoped that they would not have to  eliminate it  from  the cycles thereafter but it is something I have to accept. In the meantime I run Unity 3D on all my upgraded testing boxes and it is a delight and through the past two releases has only become better. If  and when this fails I always have Kubuntu which I am growing quite accustomed to.  If I need to run GNOME I can always use Lucid  perhaps  well past its EOL cycle. Testing GNOME 3 (as I do from time to time in these cycles) really doesn't show me anything innovative or assistive in the way that whole desktop concept works.  Perhaps then GNOME is becoming a preference?

 If it were not for Unity  I think Ubuntu as a whole would struggle with trying to present itself as a developing OS.  GNOME Classic  is a great DE. Perhaps  some feel rather strongly about gnome-shell and it's development also but taking side-shots at unity to promote more gnome testing is futile at this stage of the game.
[/I]

---

### Post by Stinger on 2012-11-05
@ventrical
This is _not_ a Unity versus Gnome thread.

You can't compare Unity and Gnome, Gnome is a complete DE an Unity is only a UI or shell if you prefer (a lot of people assume Unity is a DE).
If you want to compare, you can compare Unity and Gnome-Shell, but that's not the intention of this thread.

To quote myself from earlier:
"the main point is, why not let us play with a upstream Gnome development release between the long term releases from Ubuntu ?"

And yes, Unity seems to be 'the bad guy' here, holding back the Gnome version, so of course it will be part of the debate. ;)

---

### Post by ventrical on 2012-11-05
> **Stinger said:**
> 
I can understand, from the Ubuntu perspective, it would be better to follow one step behind and concentrate the development on Unity, but I dislike the fact that Unity will be locking the Gnome version in Ubuntu.

Maybe it's time to jump ship to follow Gnome ?
I used to love Ubuntu when Gnome was the default desktop, but that all changed with Unity.


 I am not trying to compare the two different experiences. My apologies if you read it that way. I just wanted to note how you suggested in the form of a question that it may be time to "jump ship" and I took that as a slight against the ubuntu-desktop (Unity). I just feel that  it is generally non-productive  to rip one DE to favour another, but, however , you are correct in that Unity will be part of your debate topic. :)

  I was just offering my opinion .

Regards,
Ventrical

---

### Post by Stinger on 2012-11-05
@ventrical
First, you don't need to apologize, you are entitled to your own opinion. I just don't want this thread to go off topic.

Second, Unity relies heavily on Gnome components to deliver a complete DE, so why not work with the latest Gnome between LTS ?
The alternative is to fork and maintain the needed Gnome components for a complete Unity DE, but Ubuntu appears not to have the resources to do so ? Else I think it would have been forked in 11.04

I wrote "Maybe it's time to jump ship to follow Gnome ?"
Because of my devotion to the Gnome desktop and the fact that Ubuntu is trying to ride two horses going in each their own direction, maybe even three horses if you count compiz too, but Ubuntu seems to be controlling compiz-development nowadays.
Gnome cannot be controlled, so if Ubuntu still wants to use Gnome components I think it's essential to use the latest version to keep up with Gnome development.
And if Ubuntu chooses not to follow upstream Gnome in any way, be it main repo or Gnome3 ppa.... Well then it's time for me to jump ship  and follow Gnome. ;)

---

### Post by ventrical on 2012-11-05
> **Stinger said:**
> @ventrical
First, you don't need to apologize, you are entitled to your own opinion. I just don't want this thread to go off topic.

Second, Unity relies heavily on Gnome components to deliver a complete DE, so why not work with the latest Gnome between LTS ?
The alternative is to fork and maintain the needed Gnome components for a complete Unity DE, but Ubuntu appears not to have the resources to do so ? Else I think it would have been forked in 11.04

I wrote "Maybe it's time to jump ship to follow Gnome ?"
Because of my devotion to the Gnome desktop and the fact that Ubuntu is trying to ride two horses going in each their own direction, maybe even three horses if you count compiz too, but Ubuntu seems to be controlling compiz-development nowadays.
Gnome cannot be controlled, so if Ubuntu still wants to use Gnome components I think it's essential to use the latest version to keep up with Gnome development.
And if Ubuntu chooses not to follow upstream Gnome in any way, be it main repo or Gnome3 ppa.... Well then it's time for me to jump ship  and follow Gnome. ;)

  I really do appreciate  what you are saying, especially with you being a veteran contributor, but I also noticed how the whole distribution/ testing/release process has changed dramatically (which appears to be a sound decision directed towards efficiency) and, as a tester, I was first taken aback but, I am learning to adjust quickly with how fast the ubuntu vision for the future is changing.

  I think with Jeremy at the helm with UGR that  this situation can only get better.

Regards

---

### Post by ronacc on 2012-11-05
It is difficult these days to discuss anything about Ubuntu without unity being mentioned . To point out the consequences of unity being the main focus of Ubuntu is not bashing unity but merely stating the situation as it is .

---

### Post by ventrical on 2012-11-05
> **ronacc said:**
> It is difficult these days to discuss anything about Ubuntu without unity being mentioned . To point out the consequences of unity being the main focus of Ubuntu is not bashing unity but merely stating the situation as it is .


Thank you for that clarification.

Regards,

ventrical

---

### Post by Stinger on 2012-11-05
> **ventrical said:**
> I also noticed how the whole distribution/ testing/release process has changed dramatically (which appears to be a sound decision directed towards efficiency) and, as a tester, I was first taken aback but, I am learning to adjust quickly with how fast the ubuntu vision for the future is changing.

  I think with Jeremy at the helm with UGR that  this situation can only get better.

Regards
Well efficiency maybe, but quality ? I think grahammechanical hit the nail on the head [when he wrote]("http://ubuntuforums.org/showpost.php?p=12336755&postcount=19"):
> It led me to the conclusion that Ubuntu has Quality Assurance but not much Quality Control.
(I know this is taken out of context but just follow the link to read the entire post, it has a lot of valid points)

I don't know much about the Ubuntu vision but it doesn't seem to improve the Gnome relationship. 

Jeremy is doing a lot to make UGR succeed but even the UGR developers can't go against Ubuntu's decision to stay with stable Gnome if they want UGR to be official supported.
So right now I can only hope that Gnome 3.7-3.8 makes it into the Gnome3 ppa, but it seems quite uncertain ATM :-k

---

### Post by ronacc on 2012-11-05
although my personal preference for the testing cycles would be to start out as near the bleeding edge as can be done with a reasonable hope of delivering
a sufficiently stable product at release , I think for this and maybe the next the focus shoud be more on stability and polish than cutting edge . My reason for this is that MS just released Windows 8 and I believe it will drive many Windows users to explore alternatives and we should provide the best one , I believe this is an opportunity to gain many converts .

---

### Post by ventrical on 2012-11-05
> **Stinger said:**
> Well efficiency maybe, but quality ? I think grahammechanical hit the nail on the head [when he wrote]("http://ubuntuforums.org/showpost.php?p=12336755&postcount=19"):

(I know this is taken out of context but just follow the link to read the entire post, it has a lot of valid points)

So right now I can only hope that Gnome 3.7-3.8 makes it into the Gnome3 ppa, but it seems quite uncertain ATM :-k

Yes .. I read grahammechanical's post. If you read Guitara's  blog here: 
[http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html](http://www.theorangenotebook.com/2012/10/uds-r-rise-of-the-quality-machines.html)

then that is in contradistinction to the precept of no quality control.

However, as you have stated "I can only hope" and one thing I have found for sure is that with Ubuntu, there is always hope ! :)

Regards,
Ventrical

---

### Post by Stinger on 2012-11-05
> **ronacc said:**
> although my personal preference for the testing cycles would be to start out as near the bleeding edge as can be done with a reasonable hope of delivering
a sufficiently stable product at release , I think for this and maybe the next the focus shoud be more on stability and polish than cutting edge . My reason for this is that MS just released Windows 8 and I believe it will drive many Windows users to explore alternatives and we should provide the best one , I believe this is an opportunity to gain many converts .
I have to differ, polish and stability is for the LTS, between LTS Ubuntu should be innovative and exploring new technologies including the latest Gnome, maybe even invent own tools or applications as the softwarecenter which happens to be a trend setter.
Windows should never be a concern. If you deliver a OS that's innovative and has trendsetting apps you'll gain users automatically.

---

### Post by ronacc on 2012-11-05
> **Stinger said:**
> I have to differ, polish and stability is for the LTS, between LTS Ubuntu should be innovative and exploring new technologies including the latest Gnome, maybe even invent own tools or applications as the softwarecenter which happens to be a trend setter.
Windows should never be a concern. If you deliver a OS that's innovative and has trendsetting apps you'll gain users automatically.

I agree with you in general but for the reason I stated I think that they are critical over the current cycle and the next one . Windows is not my concern I have not used it for more than 12 years . I do however keep track of where it is going ( know thy enemy ) and I think that with windows 8 MS has "stepped in it" and this presents us with a good opportunity to gain users .

---

### Post by Stinger on 2012-11-05
@ventrical
I did read Guitara's blog, it has a lot of good ideas that have to be implemented and tested before we can tell if they are improving quality control or not.

It also says:
"Flavors will now have complete control over there releases" but apparently no control when it comes to versions as in Gnome 3.8 ?

Regarding hope.
I can only hope for Ubuntu that the quality of Raring rises to a level where it justifies stability, polish and the exclusion of the upstream Gnome version.

---

### Post by nuttzo31 on 2012-11-06
> **screaminj3sus said:**
> My longest standing problem with ubuntu has always been: bugs, bugs, bugs. They need more stable, polished releases badly, and if this helps with that then I am for it.

I agree ubuntu 12.10 struggles badly because compiz is so slow and buggy  when you are minimizing/maximizing windows or closing windows from the spread view. There is still the nvidia bug where the windows are blank when maximizing and that bug is over a year old. 

I have an asus p8p67 pro with an i5-2500k with 8gb ram,ssd drive  and a nvidia g210(which is no powerhouse but runs windows 7 with full effects just fine) and ubuntu shouldn't struggle so much. They need to work on unity so it is up to the same  speed as gnome-shell , 13.04 really needs to be a polish only release in my opinion.

---

### Post by mc4man on 2012-11-07
> **ronacc said:**
>  I do however keep track of where it is going ( know thy enemy ) and I think that with windows 8 MS has "stepped in it" and this presents us with a good opportunity to gain users .I thought I'd pick up a new laptop today, current one almost 5 yrs.
After spending 30 min with Win 8 it has to be the worst OS I've ever used, couldn't make much sense of it 
(nor the laptop which is going back tom., once windows was used for a little while it refused to boot to bios or boot from usb.. without resetting to the factory/as shipped state.

---

### Post by ronacc on 2012-11-07
I think the boot problem there may be a bug MS let get loose . The install I have on one of the hd's in my test box sometimes takes 2,3,or even 4 trys to boot .

edit: I completely agree with your impression , it really is that bad .

---

### Post by addegsson on 2012-11-08
UGR should be built upon the standard Ubuntu repos (IMO) because of the stability you gain with the well tested packages. If you want newer versions you just have to add the Gnome 3 PPA. :)

---

### Post by Stinger on 2012-11-08
@addegsson
I beg to differ, UGR should follow the Gnome releases and so should Ubuntu to benefit from the upstream Gnome releases.
The packages with the never Gnome would be just as well tested as with the older one as it has the same audience. 

I don't think there is any stability issues with Gnome, but because Ubuntu chooses to have it's own versions of the 'System Settings' , onlinie accounts (UOA vs. GOA), compositing window manager (Compiz) and it's own Shell (Unity) etc.
There will be a process of patching and tweaking the involved Gnome components to meet Ubuntu's needs.
This process, I think, is what you all refer to as 'stabilizing' and 'polishing'.
It's an adaption process where Ubuntu has to adapt to the Gnome components because Ubuntu has not produced a complete DE yet and still relies heavily on Gnome to have a complete DE.
  
It has _nothing_ to do with the quality of the current Gnome version, and I really can't see that UGR would gain any stability at all from such a decision, but it'll gain less users as it looses it's appeal to Gnome fans because of an old Gnome version.

ATM there is no guarantee that Gnome 3.8 will make it into the Gnome3 ppa, because of incompatibility with Unity. :(

---

### Post by kansasnoob on 2012-11-08
> **Stinger said:**
> @addegsson
I beg to differ, UGR should follow the Gnome releases and so should Ubuntu to benefit from the upstream Gnome releases.
The packages with the never Gnome would be just as well tested as with the older one as it has the same audience. 

I don't think there is any stability issues with Gnome, but because Ubuntu chooses to have it's own versions of the 'System Settings' , onlinie accounts (UOA vs. GOA), compositing window manager (Compiz) and it's own Shell (Unity) etc.
There will be a process of patching and tweaking the involved Gnome components to meet Ubuntu's needs.
This process, I think, is what you all refer to as 'stabilizing' and 'polishing'.
It's an adaption process where Ubuntu has to adapt to the Gnome components because Ubuntu has not produced a complete DE yet and still relies heavily on Gnome to have a complete DE.
  
It has _nothing_ to do with the quality of the current Gnome version, and I really can't see that UGR would gain any stability at all from such a decision, but it'll gain less users as it looses it's appeal to Gnome fans because of an old Gnome version.

ATM there is no guarantee that Gnome 3.8 will make it into the Gnome3 ppa, because of incompatibility with Unity. :(

I totally agree with that sentiment. If the Unity devs need more time to adjust work around changes in Gnome then Canonical should tweak it's release cycle :)

Remember that Dapper was 6.06! With all of the changes in testing - eliminating alphas, etc - it shouldn't be impossible to tweak our release schedule so the gnome and ubuntu devs can truly work in unison again :)

---

### Post by philinux on 2012-11-08
I'm in the wait and see camp at the moment as things may well change, but just to reiterate the reasons.

> The UDS GNOME Plans Review session notes talk about the reasons why Ubuntu 13.04 won't use the latest GNOME by default: [Session Notes]("http://summit.ubuntu.com/uds-r/meeting/21388/desktop-r-gnome-plans-review/")

    tracking unstable GNOME is taking lot of resources
    The Ubuntu desktop is quite less "stock GNOME" than it used to be
    GNOME unstable series and Ubuntu "working every day" are hard to conciliate goals
    GNOME is not communicating early enough on what is coming for us to discuss next cycle at UDS (see nautilus 3.6 in quantal)
    GNOME is shipping stables with transitions half done (see gstreamer 1.0 this cycle) which is not something we want in Ubuntu
    Our "feedback loop" with GNOME is not really working nowadays


---

### Post by Stinger on 2012-11-08
@philinux
> tracking unstable GNOME is taking lot of resources that we don't invest in our desktop (packaging a new stack every 3 weeks, dealing with transitions, regressions, etc)
That should not be new to the developers, they have been tracking Unstable Gnome for quite a few years now.
News are that they are now using a lot of resources patching and tweaking the gnome components to meet Unity's needs, leaving much less resources to track unstable Gnome. 
> our desktop is quite less "stock GNOME" than it used to be, which means we have extra integration work to do and it's less trivial to do those "on the way" during the cycle
Same as the above, Ubuntu is using too many resources on 'extra integration work' because it's lesser stock Gnome.
> GNOME unstable series and Ubuntu "working every day" are hard to conciliate goals
Yes of course, it's like riding two horses going in each their own direction (I posted that earlier on this thread).
Either you follow Gnome or You fork the needed components and make your own Unity DE.
But Ubuntu doesn't seem to have the resources to do so ?  
> GNOME is not communicating early enough on what is coming for us to discuss next cycle at UDS (see nautilus 3.6 in quantal)
Well Gnome is going through a lot of changes itself so thats not gonna happen before Gnome3 development calms down later in the release cycle, but that was the same with the changes from Gnome1 series to Gnome2 and should be expected in such big change from one series to another. Changes not known at UDS cannot be communicated.
> GNOME is shipping stables with transitions half done (see gstreamer 1.0 this cycle) which is not something we want in Ubuntu
Outch ! that one you can blame on Gnome :biggrin:
> our "feedback loop" with GNOME is not really working nowadays, they don't have time to look at most bugs and we hit regressions and sit on them until somebody on our side has time to look at them, which means neither GNOME or us benefits much from tracking unstable GNOME...
I am really sad if that's the whole truth, but I guess that's the kinda  reaction you get when you expect cooperation from someone that feels your are trying to control and limit their developer freedom.

Cheers ;-)

---

### Post by jbicha on 2012-11-08
> **Stinger said:**
> 
I don't think there is any stability issues with Gnome, but because Ubuntu chooses to have it's own versions of the 'System Settings' , onlinie accounts (UOA vs. GOA), compositing window manager (Compiz) and it's own Shell (Unity) etc.
There will be a process of patching and tweaking the involved Gnome components to meet Ubuntu's needs.
This process, I think, is what you all refer to as 'stabilizing' and 'polishing'.
It's an adaption process where Ubuntu has to adapt to the Gnome components because Ubuntu has not produced a complete DE yet and still relies heavily on Gnome to have a complete DE.
  
It has _nothing_ to do with the quality of the current Gnome version, and I really can't see that UGR would gain any stability at all from such a decision, but it'll gain less users as it looses it's appeal to Gnome fans because of an old Gnome version.


It sounds like you are saying that GNOME stable releases are stable when they are released and that there are no benefits to waiting a bit for bugs to be fixed.

For instance, GNOME 3.6 depends on a still-not-released version of ibus (a risky move for those who need alternate input methods). It also depended on gstreamer-1.0 which was only released 2 days before GNOME 3.6 and was not API-compatible with gstreamer-0.10 which had been used for years.

Ubuntu's integration work does shield users from certain controversial GNOME decisions. Examples include continuing to offer an easy way to change what happens when you close your laptop lid, allowing you to right-click on the desktop to change the wallpaper (this is part of having nautilus continue to draw desktop icons), and being able to change the theme. Those kinds of patches take time to keep working.

A bit off topic, but it is interesting that [Fedora 18]("http://fedoraproject.org/wiki/Releases/18/Schedule") won't be released until 2013. That's about 3 months after Ubuntu 12.10 was released. (I think a lot of that is because of their complex installer rewrite but still.)

---

### Post by Stinger on 2012-11-08
@jbicha
Yeah I guess it could sound that way, I'm not saying that Gnome releases are free of bugs.
I said earlier, Gnome is going through a lot of changes, Gnome3 and Gnome-Shell are still evolving (you mentioned ibus and gstreamer) but still very useful and comparable with a 'stabilized' Ubuntu ;)

I know that "Ubuntu's integration work does shield users from certain controversial GNOME decisions" and that's good in the sense of 'stability' but it also shields users, like me, from having the latest version of Gnome even if it is a bit 'unstable', it's IMO a small price to pay for having one of, if not, the most innovative DE(s) running.

Regarding Fedora, well they are always behind schedule and Gnome might just be one reason among many others but I think Fedora is more about innovation than it is about stability. :lol:

Ps. I appreciate all your work with Gnome and UGR, it's amazing to see how much has been achieved in just one release cycle, if you and the other dev's can bring Gnome 3.8 in the next I'll be even more amazed. I wish the best of luck for you and all other developers involved in UGR

---

### Post by grahammechanical on 2012-11-09
Does this news change anyone's views?

[http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html#more]("http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html#more")

> Ubuntu users don't have to worry about this just yet, since the next Ubuntu version - 13.04 Raring Ringtail -, will continue to use GNOME 3.6 for the most part and not the latest GNOME 3.8 which will ship without the fallback mode.

> The GNOME developers didn't forget about the users who prefer a GNOME 2-like layout, and it looks like they will compile and _maybe_ help maintain a list of GNOME Shell extensions that provide such a layout.

That is where the responsibility lies. Yet people always blame the Ubuntu developers for not staying with the past.

---

### Post by kansasnoob on 2012-11-09
> **grahammechanical said:**
> Does this news change anyone's views?

[http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html#more]("http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html#more")





That is where the responsibility lies. Yet people always blame the Ubuntu developers for not staying with the past.

To me that means I need to shift 100% of my efforts towards Lubuntu, particularly since they mention dropping Metacity altogether :(

In the meanwhile I'll be using Ubuntu 12.04 in classic (no effects) mode ........... I'm glad it's supported until April 2017 :)

---

### Post by Stinger on 2012-11-09
@grahammechanical
I saw the announcement at worldofgnome and Muktware:
[Gnome 3.8 is dropping Fallback Mode]("http://worldofgnome.org/gnome-3-8-is-dropping-fallback-mode/")**********                   [Gnome 3.8 To Drop Fallback Mode: Oops! I Did It Again]("http://www.muktware.com/4777/gnome-38-drop-fallback-mode#.UJ0o7JvJMn0")
The guy's at Muktware have humor :lol:

Well it shouldn't really matter nowadays, Ubuntu already dropped Unity 2D and basically Gnome is doing the same.
I think it's the right decision and you can read more about it in the links provided above.

I really don't know why you are talking about responsibility and 'blaming Ubuntu developers' ?

It's a Gnome decision and of course they are responsible for making this decision and if you want to 'blame' anybody for this necessary decision, you can blame Gnome.
But then again you can blame Ubuntu for still relying on Gnome fallback mode ;)

I can see that Ubuntu now has to use the old Gnome version (because of Unity and 'stability') but at the same time Ubuntu could benefit from having Gnome 3.8 in UGR for further testing it for the next release. 

What about that proposal ?  

And as a side effect UGR would be much more appealing to Gnome fans :D

BTW, did you see that [Linus Torvalds is actually back on Gnome 3!]("http://worldofgnome.org/linus-torvalds-is-actually-back-on-gnome-3/") That guy never stops to amaze me :biggrin:

---

### Post by grahammechanical on 2012-11-09
@Stinger

The other month I proposed that Ubuntu have a special testing branch where registered testers could test experimental packages, from wherever, before they were merged into the development release.

The situation as it is now, is that Raring may get Gnome 3.8 when it is too late to do anything about any bugs testers may report. Or, Gnome 3.8 goes into the SS development branch after next April and then we get to test it.

If Gnome Remix is going to keep up the developers will need lots of help. They will need testers.

I do not accept the Linux tradition of letting the user be the tester and then responding, or not, to bug reports. If Ubuntu has to be a little bit out of date in order to release versions with few bugs, then I accept that as a necessity. I do think that more use could be made of community volunteer testers to try out the experimental stuff.

Regards.

---

### Post by 0011235813 on 2012-11-09
> **Stinger said:**
> Here we go again, the never ending debate ;)

[http://www.webupd8.org/2012/11/ubuntu-1304-only-some-gnome-components.html](http://www.webupd8.org/2012/11/ubuntu-1304-only-some-gnome-components.html)

What do you want from Ubuntu between the long term releases ?

Stability would mean to follow Gnome releases one step behind.

Progression would mean to keep up the pace with the Gnome releases and use the current development version (which eventually will become 3.8 )

I personally would like progression because I use the [UGR]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/") and would be sad to see UGR following Gnome one step behind Fedora.

I can understand, from the Ubuntu perspective, it would be better to follow one step behind and concentrate the development on Unity, but I dislike the fact that Unity will be locking the Gnome version in Ubuntu.

Maybe it's time to jump ship to follow Gnome ?
I used to love Ubuntu when Gnome was the default desktop, but that all changed with Unity.

What do you want from Ubuntu ? Gnome 3.6 or the current development version that will become 3.8 ?
No, because the devs can't make a distro that ships with an interface which decides to break every theme, applet and extension with every new release. Imagine the headaches that will cause (yes, I know Fedora uses it, but... It's Fedora, y'a know?). 

You can certainly guess why I switched. Maybe they should go the Mint way and put Cinnamon as the main environment with MATE as a light-weight alternative. XFCE ain't bad either, if you can find a decent menu with a proper search function. Oh and a sound applet. Don't know why those devs decided to omit that.

---

### Post by Stinger on 2012-11-10
@grahammechanical
I am willing to test any Gnome 3.8 packages for Ubuntu / UGR, if that's what it takes to get Gnome 3.8 in UGR, just show me where to sign up, where to get the packages that needs to be tested and where to report the results. ;)
And I think a lot of other Gnome fans are willing to do so too, testing 'experimental stuff' from the Gnome development branch.

Just think of it, UGR will then be the leading Gnome release, even Fedora won't be able keep up the pace :biggrin: (just kidding)

---

### Post by ronacc on 2012-11-10
I can squeeze it onto my test box too , count me in .

---

### Post by dino99 on 2012-11-10
The decision made is the best, as gnome 3.8 will be out about only 1 month before RR release (if not delayed), and we can expect some good for 13.04.1
So where is the problem ?

---

### Post by zika on 2012-11-10
This might be interesting to those who use radeon driver and can not enter GnomeShell 3.7.1...
Try forcing SW render:
in ~/.xsessionrc put```
export LIBGL_ALWAYS_SOFTWARE=1
```It worked for me.
GS does work also with Glamor for radeon...
(GDM is not necessary, simple startx can do, with LightDM GS didn't work, I've not tried that in weeks...)

---

### Post by Stinger on 2012-11-10
> **dino99 said:**
> The decision made is the best, as gnome 3.8 will be out about only 1 month before RR release (if not delayed), and we can expect some good for 13.04.1
So where is the problem ?
Are you saying that Gnome 3.8 will be in 13.04.1 ? :-k

---

### Post by qamelian on 2012-11-10
> **Stinger said:**
> Are you saying that Gnome 3.8 will be in 13.04.1 ? :-k
There won't be a 13.04.1. We only get .1 version for LTS releases, and 13.04 isn't LTS.

---

### Post by Stinger on 2012-11-10
@qamelian
Thank's:)
Well dino99, then the problem would be no 13.04.1 and no Gnome 3.8 for RR, right ? :???:

---

### Post by Stinger on 2012-11-12
> **jbicha said:**
> 
A bit off topic, but it is interesting that [Fedora 18]("http://fedoraproject.org/wiki/Releases/18/Schedule") won't be released until 2013. That's about 3 months after Ubuntu 12.10 was released. (I think a lot of that is because of their complex installer rewrite but still.)
A quick follow up on that from [distrowatch weekly ,Miscellaneous News]("http://distrowatch.com/weekly.php?issue=20121112"):
> The Fedora distribution typically ships a new release about once every six months. While small delays are common with such a tight schedule, usually the Red Hat sponsored project is only held back a week or two. _Fedora 18 will become an exception as blocking bugs in its installer and installation upgrader will delay the distribution's upcoming version until January 2013._ At present, the developers plan to get a final Beta release out at the end of November with a final release of Fedora 18 scheduled for January 8th. Information on the blocking issues can be found on the Fedora developers' mailing list.
As you can see from the [accepted blockers]("http://qa.fedoraproject.org/blockerbugs/milestone/18/beta/buglist"), the delay has nothing to do with Gnome.

@grahammechanical
Regarding the drop of fallback mode in Gnome 3.8.
This seems not to be a surprise to the ubuntu dev's as they have created a ['Stop relying on GNOME fallback code for Unity' blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-gnome-fallback") on 2012-10-22. 
The goal is set for Raring and the milestone target is 13.04 Beta1.
So basically, if solved, it would allow Gnome 3.8 on Raring I think. :D

---

### Post by Stinger on 2012-12-18
Question:
Will UGR follow the Gnome releases one step behind in future releases like Ubuntu? 

UGR QQ=Gnome 3.6, UGR RR=Gnome 3.6 (makes little sense)

Personally I think it would make more sense for UGR to have it's own release schedule

Maybe wait until Gnome 3.8.1 and follow the Gnome .1 releases instead.   :-k

---

### Post by rrnbtter on 2012-12-18
Greetings,
After reading all of this I am beginning to more than before agree with Chdslv in [http://ubuntuforums.org/showthread.php?t=2095113](http://ubuntuforums.org/showthread.php?t=2095113).  This in spite of the fact that I think that 13.04 is just great even in this pre-released state.  One can only hope that the powers that be are able to make these interests intersect. Should be really good when (and if) it does!  Mean time I don't have any complaints and don't know enough to give direction.

rrnbtter
Life is good! Live it to the Ubuntu-ist! Until Friday!

---

### Post by kevpan815 on 2012-12-20
Pardon me but, I thought that Ubuntu now uses Unity instead of Gnome?

---

### Post by craig10x on 2012-12-20
It's been on Gnome 3 since Ubuntu 11.10...I think you are confusing it with the Desk Top Environment that runs on top of it, such as Unity, Gnome 3 Shell, Cinnamon, Gnome 3 fallback, etc...

Ubuntu's "shell" as it were, on gnome 3 is the Unity Interface...

Hope that clears it up for you...

---

### Post by Stinger on 2012-12-21
> **kevpan815 said:**
> Pardon me but, I thought that Ubuntu now uses Unity instead of Gnome?
Wrong !! _**Ubuntu uses Unity instead of Gnome-Shell**_

[LIST]
[*]Unity is only a UI (or shell if you prefer) not a complete DE.

[*]Unity can be compared to Gnome-Shell (Gnome's own UI)

[*]Ubuntu uses Unity as UI and all the Gnome app's to make a complete DE.

[*]Gnome is a complete DE with Gnome-Shell as UI.
[/LIST]

Does that make sense to you ? (or do I have to explain UI and DE too ? :rolleyes:)

---

### Post by Stinger on 2012-12-24
> **Stinger said:**
> 
Just think of it, UGR will then be the leading Gnome release, even Fedora won't be able keep up the pace :biggrin: (just kidding)

Pardonne moi, but Fedora seems to have plans for a [&#8220;Speedy Gonzales&#8221;-release]("http://worldofgnome.org/fedora-19-will-catch-up-gnome-3-8-with-a-4-months-release-cycle/") in just 4 months after Fedora 18.

Do Ubuntu and UGR want to compete or play it safe ?
Come on guys, where is your competitive spirit ? ;)

---

### Post by Stinger on 2013-03-12
> **Stinger said:**
> Do Ubuntu and UGR want to compete or play it safe ?
Come on guys, where is your competitive spirit ? ;)

Well, well color me happy :D

Ubuntu Gnome has now been [approved as an official flavour]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000035.html")
and.... has shown it's competitive spirit ;)
> Ubuntu GNOME 13.04 will be released with GNOME 3.6, since Ubuntu held back on GNOME this cycle. [B]We are however making GNOME 3.8 available from
the gnome3-team PPA.[/B]

Can't wait to the ISO's are released.

Congratulations to the developer team, keep up your excellent work and your competitive spirit. 

Stinger

---

### Post by Stinger on 2013-03-14
> **Stinger said:**
> 
Ubuntu Gnome has now been [approved as an official flavour]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000035.html")

A quote from the above link:
> Daily image builds are currently being set up and we except that they will be available within a few weeks.

Time is flying by real quickly these days, because ["Ubuntu GNOME daily images now available!"]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000050.html")

Go get your hands dirty ;)

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/")

Kudos to the team, I'll start downloading right away :D

And of course I'll try the Gnome 3.8 version from the [GNOME3 Team ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring")

---

### Post by ronacc on 2013-03-14
all I have to say about this is NONE of the 3.6 kernels worked on my amd64 box and ALL of the 3.8 kernels do ., now at 3.8.0-12

---

### Post by woxuxow on 2013-03-14
Right decision.

---

### Post by sgage on 2013-03-14
> **ronacc said:**
> all I have to say about this is NONE of the 3.6 kernels worked on my amd64 box and ALL of the 3.8 kernels do ., now at 3.8.0-12

Talking about Gnome versions, not kernel versions... ;)

---

### Post by ronacc on 2013-03-14
oops , my bad

---

### Post by Stinger on 2013-03-14
> **ronacc said:**
> all I have to say about this is NONE of the 3.6 kernels worked on my amd64 box and ALL of the 3.8 kernels do ., now at 3.8.0-12
Ubuntu GNOME is running kernel 3.8.0-12-generic on my box from today's live CD.
Very snappy and light on the rescurces compared to Quantal Gnome Remix.

---

### Post by Stinger on 2013-03-28
Gnome 3.8 has been released as you might have noticed.

Read about it here: [GNOME 3.8 RELEASED - SEE WHAT'S NEW [VIDEO, SCREENSHOTS]]("http://www.webupd8.org/2013/03/gnome-38-released-see-whats-new-video.html"), please take the time and watch the nice video.

Lets all hope that it will land in the [Gnome 3 ppa for Raring]("https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring") in near future ;)

As soon as it does I'll try to do an upgrade using the [Ubuntu GNOME daily live]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/") and the Gnome 3 ppa for Raring.

So long ( hope not too long ;) )

---

### Post by Stinger on 2013-03-29
And while I'm waiting for Gnome 3.8 in the Gnome3 ppa, Here is another great video and walk-through of the new and AWSOME Gnome 3.8 :cool:

 [GNOME 3.8, One Day After]("http://worldofgnome.org/gnome-3-8-one-day-after-2/")

Even the Legacy mode is covered at the end ( 9:43 )

Cheers ;)

---

### Post by Stinger on 2013-04-02
Well, still waiting but I don't mind I think Gnome 3.8 is worth waiting for, as you can se in yet another nice review from Muktware.

[Gnome 3.8 review: it's almost there]("http://www.muktware.com/5449/gnome-38-review-its-almost-there") :D

Still cant use it though due to my GDM bug ['GDM wont start on Ubuntu GNOME using Gnome3 ppa' bug #1162466' ]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466"), but 'someone' is working on it ;) 
Please add yourself if you are trying Gnome 3.8 from Gnome3 ppa, and you are affected too. 
I can see that three more are affected [here]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000101.html"), [here]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000102.html") and [here]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466/comments/7") so there may be more.

---

### Post by dino99 on 2013-04-02
you should use Apport to get more complete info; and add the required tags to populate the bug's queues

---

### Post by Stinger on 2013-04-02
> **dino99 said:**
> you should use Apport to get more complete info; and add the required tags to populate the bug's queues

I would have done if I could login, can't even get a terminal working, sorry.
Will of course provide Jeremy or others with all the info they find necessary.

---

### Post by Rukiri on 2013-04-02
If you're using Gnome 3.8 for just classic please just use XFCE, personally XFCE is an awesome project that's active and already does everything Gnome2 did and is going further so eventually either by XFCE5 we should see what gnome should have been but gnome 3.8 is a solid release.

I never found gnome-classic in any settings... is it a session only?  I had gnome-shell-extensions installed oh well.

I would personally give the classic mode a few more releases, until I can customize it like xfce or the original gnome 2 I'll stick to xfce but will keep it around mainly as GTK3 has awesome shell themes.

---

### Post by Stinger on 2013-04-03
> **Stinger said:**
> Well, still waiting but I don't mind I think Gnome 3.8 is worth waiting for, as you can se in yet another nice review from Muktware.

[Gnome 3.8 review: it's almost there]("http://www.muktware.com/5449/gnome-38-review-its-almost-there") :D

Still cant use it though due to my GDM bug ['GDM wont start on Ubuntu GNOME using Gnome3 ppa' bug #1162466' ]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466"), but 'someone' is working on it ;) 
Please add yourself if you are trying Gnome 3.8 from Gnome3 ppa, and you are affected too. 
I can see that three more are affected [here]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000101.html"), [here]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000102.html") and [here]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466/comments/7") so there may be more.

Bug solved.
When adding the Gnome3 ppa, you need to sudo ```
apt-get dist-upgrade
``` to resolve the dependency problems.

---

### Post by dino99 on 2013-04-03
> **Stinger said:**
> Bug solved.
When adding the Gnome3 ppa, you need to sudo ```
apt-get dist-upgrade
``` to resolve the dependency problems.

That is not true: the problem was due to the so many packages not installed on your system, meaning that some normal missed dependencies  have pushed out that trouble; so finally a dis-upgrade was required to get a stable installation.

---

### Post by Stinger on 2013-04-04
@ dino99
I downloaded the Ubuntu-GNOME daily live CD and and installed it.
I would expect the Ubuntu-GNOME daily live to be updated and containing all the packages needed to install Ubuntu-GNOME, right ?

Can you please explain to me how the problem can be "so many packages not installed on your system" ?

Furthermore, when I add  the Gnome3 ppa I would expect to do 'apt-get-update' and 'apt-get upgrade' 
No where on the Gnome3 ppa page it says any different.

---

### Post by jbicha on 2013-04-04
> **Stinger said:**
> @ dino99
Furthermore, when I add  the Gnome3 ppa I would expect to do 'apt-get-update' and 'apt-get upgrade' 
No where on the Gnome3 ppa page it says any different.

I've added that information now to the PPA page. This will also be added to the Beta 2 Release Notes.

Part of the problem is that this is the first time since Natty that the GNOME3 PPA has shipped a completely different version of GNOME than is shipped in the corresponding Ubuntu release.

---

### Post by sgage on 2013-04-04
> **jbicha said:**
> I've added that information now to the PPA page. This will also be added to the Beta 2 Release Notes.

Part of the problem is that this is the first time since Natty that the GNOME3 PPA has shipped a completely different version of GNOME than is shipped in the corresponding Ubuntu release.

I did a regular apt-get upgrade, and all seems to be working fine. Should I issue an apt-get dist-upgrade command?

---

### Post by Stinger on 2013-04-04
@ jbicha 
Thanks again much appreciated :)

@ sgage
What does ```
gnome-shell --version
``` give you ? it should say ```
GNOME Shell 3.8.0.1
```
If it says GNOME Shell 3.6.3.1 , you should do 'sudo apt-get dist-upgrade' to avoid conflicting packages.

---

### Post by zika on 2013-04-04
Why do I get:
```
:~$ gnome-shell --version
gnome-shell: error while loading shared libraries: libandroid-input.so: cannot open shared object file: No such file or directory
```
with all three GS PPAs up-to-date...?

---

### Post by Stinger on 2013-04-04
@ zika
"Three GS PPAs" ? I can only count two, Gnome3 ppa and Gnome3 Staging. I only use Gnome3 ppa.

Did you by any chance experiment with Mir ? I found this bug when googling for "libandroid-input" [Bug #1164253]("https://bugs.launchpad.net/mir/+bug/1164253")
I can't find any libandroid packages or any libandroid related packages on my Ubuntu-Gnome only installation.

You could install apt-show-versions and run 'sudo apt-show-versions gnome-shell' instead.

---

### Post by zika on 2013-04-04
> **Stinger said:**
> @ zika
"Three GS PPAs" ? I can only count two, Gnome3 ppa and Gnome3 Staging. I only use Gnome3 ppa.

Did you by any chance experiment with Mir ? I found this bug when googling for "libandroid-input" [Bug #1164253]("https://bugs.launchpad.net/mir/+bug/1164253")
I can't find any libandroid packages or any libandroid related packages on my Ubuntu-Gnome only installation.

You could install apt-show-version and run 'sudo apt-show-version gnome-shell' instead.
1. Gnome3-Team-Gnome3
2. Gnome3-Team-Gnome3-Staging
3. Ricotz-Experimental-Testing
4. Mir PPA... Busted!

---

### Post by Stinger on 2013-04-04
@ zika
lol, gotcha :biggrin:

Ricotz ppa's never did me any harm, so you should probably just be more updated than I am ;)

Did you try apt-show-versions ? 
Ps. sorry bout the missing 's' in versions, corrected now.

---

### Post by zika on 2013-04-04
> **Stinger said:**
> @ zika
lol, gotcha :biggrin:

Ricotz ppa's never did me any harm, so you should probably just be more updated than I am ;)

Did you try apt-show-versions ? 
Ps. sorry bout the missing 's' in versions, corrected now.I've just divorced from Mir and its PPA and I get:```
:~$ gnome-shell --version
GNOME Shell 3.8.0.1
```
Thank You for saving my tomorrow morning... I had to restart X and was unable to get into it. If You did not have told me about the bug in Mir I would have taken all my hair tomorrow morning... ;)
Serendipity? Who knows...
Einstein said: God hides his deeds in serendipity...

---

### Post by Stinger on 2013-04-04
Happy to have been of assistance ;)
> **zika said:**
> If You did not have told me about the bug in Mir I would have taken all my hair tomorrow morning... ;)
You would have had quite a busy day tomorrow  judging from your profile picture :biggrin:

Clever fellow that Einstein, but even he realized that you need a bit of luck once in a while when you run out of skills.

---

### Post by zika on 2013-04-05
> **Stinger said:**
> Happy to have been of assistance ;)

You would have had quite a busy day tomorrow  judging from your profile picture :biggrin:

Clever fellow that Einstein, but even he realized that you need a bit of luck once in a while when you run out of skills.What skills? I'm not even aware I had any...

---

