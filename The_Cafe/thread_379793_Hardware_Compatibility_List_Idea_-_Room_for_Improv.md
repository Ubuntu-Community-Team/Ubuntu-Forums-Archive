---
title: "Hardware Compatibility List Idea - Room for Improvement?"
date: 2007-03-08
forum: The Cafe
---

### Post by Yfrwlf on 2007-03-08
While the hardware compatibility lists on the Ubuntu website and elsewhere on the net are very useful, I have yet to find a list that gives simple recommendations for what pre-built systems to buy except for a few Linux computer vendor sites.  I'm sure someone else has suggested this before but I want to suggest it because I can't find anyone else talking about this.  I think a lot of people could benefit from it.

I believe many consumers would follow recommendations for which new desktops and laptops to buy that are Ubuntu compatible.  A system for a beginner that works out-of-the-box.  Perhaps some extremely minor tweaks allowed, but completely working out of the box is really preferred.  I think those manufacturers who use Linux-compatible hardware deserve to get the Linux consumers.  I know there are some computer companies which sell Linux, but they are often more on the expensive side.

For example, if someone buys a new computer from Dell (and can get a discount for returning or not having Windows pre-installed would be a bonus), and everything works out of the box, I think it's worthy to be mentioned loudly.  Put it on a platinum/gold/premium/perfect/award/whatever list that's fairly visible on the Ubuntu site, so that if users want to purchase a computer for running Ubuntu they have a quick and easy one-stop list to visit, and it helps encourage computer vendors to be Linux friendly.

The world is filled with those who know next to nothing about computers.  I think this could possibly really help out a lot of people by steering them in the right direction.  As of now, it's like "well...try out the live CD, and hope that it all works OK on your new machine" instead of "I recommend this model here, it works perfectly with Ubuntu".  I think many people wanting to recommend Ubuntu to others would love to be able to say the latter statement.  I like building my own system, but 80% or more of the rest of the world doesn't.

With the talk that Dell and HP are thinking about offering Linux to the normal masses on desktops and/or laptops (not counting the stuff that is buried on their sites instead of being visible and in the "home users" section), but *really* giving average people a chance to select Linux with *visible* savings by doing so, I think now is an even better time to promote those vendors who do provide compatibility.

What do ya'll think, or is someone working on such a project already?  Good idea, bad idea, useless idea, wrong forum? :)

---

### Post by DoctorMO on 2007-03-09
I'm working on it.

The dohickey project will allow anyone with an existing system from say Dell or HP to rate the compatibility of each of the components; from information supplied from all users we work out how well a specific model is expected to work.

then another user only has to do a search to find the most compatible models and/or extra hardware.

[http://dohickey.sourceforge.net](http://dohickey.sourceforge.net)

---

### Post by Mathiasdm on 2007-03-09
What happens if the model becomes more compatible?

Perhaps it would be good to only show to most recent comments by other users (but of course with an option to 'show all').

---

### Post by DoctorMO on 2007-03-09
The rating would be improved further ratings. the fact that the ratings are weighted in favour of your distribution and your linux version means that if a device is now supported then you will see a higher rating in your search for Ubuntu Feisty Fawn than for a search for Ubuntu Edgy Eft or Dapper Drake.

---

### Post by Yfrwlf on 2007-03-09
> **DoctorMO said:**
> The rating would be improved further ratings. the fact that the ratings are weighted in favour of your distribution and your linux version means that if a device is now supported then you will see a higher rating in your search for Ubuntu Feisty Fawn than for a search for Ubuntu Edgy Eft or Dapper Drake.

Sounds awesome ^^  Of course, you could use any rating system, but maybe it could  be like WineHQ where you'd have the model listed (even a link to where you can buy it would be cool too), and then you'd have the distros it's been tried on and they could be color coded like on WineHQ where if it's platinum it works perfectly, if gold it works with a few small tweaks, etc etc.  [http://appdb.winehq.org/appview.php?iVersionId=315](http://appdb.winehq.org/appview.php?iVersionId=315)

Maybe have the main page list the distro or distros that have been given the highest rating, then have a sub page for that particular model, like on WineHQ, showing you what needs to be done to get it working.

Or, some other layout, I dunno.  Good luck on the project ^^

I might try to help out with your project if it weren't for the fact I'm already working on one, a big one, and I only have one other person to help so far since it's not even really public yet. :)

---

### Post by DoctorMO on 2007-03-09
> Sounds awesome

I hope so, but the amounts of data are quite large and the ability to fit the computer information with entered information is the true power.

> Of course, you could use any rating system, but maybe it could be like WineHQ where you'd have the model listed (even a link to where you can buy it would be cool too), and then you'd have the distros it's been tried on and they could be color coded like on WineHQ where if it's platinum it works perfectly, if gold it works with a few small tweaks, etc etc. [http://appdb.winehq.org/appview.php?iVersionId=315](http://appdb.winehq.org/appview.php?iVersionId=315)

Nah WineHQ is far too inefficient, they only have a few thousand entries each single entry is managed by a single person and most entries don't work and aren't up to date. so no, winehq would be a really bad idea, I have much grander systems in mind where data management is done for you and the tools empower users with information instead of asking for so much work. 

> Maybe have the main page list the distro or distros that have been given the highest rating, then have a sub page for that particular model, like on WineHQ, showing you what needs to be done to get it working.

The search will have a list of distro's which have the largest ratings as part of their information sheets.

---

### Post by Yfrwlf on 2007-03-09
> **DoctorMO said:**
> I hope so, but the amounts of data are quite large and the ability to fit the computer information with entered information is the true power.

Nah WineHQ is far too inefficient, they only have a few thousand entries each single entry is managed by a single person and most entries don't work and aren't up to date. so no, winehq would be a really bad idea, I have much grander systems in mind where data management is done for you and the tools empower users with information instead of asking for so much work. 

The search will have a list of distro's which have the largest ratings as part of their information sheets.

The easier it is for users to see what systems work the best and also allow them to add information, the better I guess. ^^  Good luck!  As soon as you get a good setup going, it'll be the users that make it popular and supply your site with information. :)  It's the framework that takes all the work of course :P  That's why in my case I'm using a CMS to get something with lots of features up quickly, then modify things from that point.

---

### Post by DoctorMO on 2007-03-09
Ah I figured a typical CMS wouldn't do because you never really get people on board that way. no one has pride in their system if the information is some place else and you have to manually enter id codes for hardware and system types.

Far better to have the system ship with the tool (python based) which links up hardware detection and information from the server and allows the user to enter information wiki style where missing (admin reviewed when sent back to server)

Working on the language translations at the moment so not just english is available. have you tried the client by the way? it's still alpha o'course.

---

### Post by Yfrwlf on 2007-03-09
> **DoctorMO said:**
> Ah I figured a typical CMS wouldn't do because you never really get people on board that way. no one has pride in their system if the information is some place else and you have to manually enter id codes for hardware and system types.

Far better to have the system ship with the tool (python based) which links up hardware detection and information from the server and allows the user to enter information wiki style where missing (admin reviewed when sent back to server)

Working on the language translations at the moment so not just english is available. have you tried the client by the way? it's still alpha o'course.

After installation, a hardware information tool thingy comes up asking if you want to send back your hardware information to Ubuntu or whatnot, I do believe.  However, it doesn't ask if you want to report which things are working and which aren't, to my knowledge.  Perhaps you could have a simple optional questionnaire: Is your video working correctly?  Is your sound working correctly?  Etc.  This would be more useful than just showing what hardware most people are running.

The client is a good idea, but it would need to be included in the distro and run after installation for it to see a lot of use, right alongside the hardware reporting tool perhaps.  Like I said though, maybe you will have to combine your project with another project or jump onto the right bandwagon for it to get a lot of use.  I'm wondering if there is a way to combine my project with Click 'n Run because of it's similar goals.  I was thinking about making something similar for my project, a downloadable client, as well as a web interface, so that it could get more attention.

---

### Post by tgm4883 on 2007-03-09
> **Yfrwlf said:**
> After installation, a hardware information tool thingy comes up asking if you want to send back your hardware information to Ubuntu or whatnot, I do believe.  However, it doesn't ask if you want to report which things are working and which aren't, to my knowledge.  Perhaps you could have a simple optional questionnaire: Is your video working correctly?  Is your sound working correctly?  Etc.  This would be more useful than just showing what hardware most people are running.

The client is a good idea, but it would need to be included in the distro and run after installation for it to see a lot of use, right alongside the hardware reporting tool perhaps.  Like I said though, maybe you will have to combine your project with another project or jump onto the right bandwagon for it to get a lot of use.  I'm wondering if there is a way to combine my project with Click 'n Run because of it's similar goals.  I was thinking about making something similar for my project, a downloadable client, as well as a web interface, so that it could get more attention.

It does ask you what is working and what is not, goes through a little wizard testing different things (ie plays a sound and asks, did you hear a sound)

---

### Post by Yfrwlf on 2007-03-09
> **tgm4883 said:**
> It does ask you what is working and what is not, goes through a little wizard testing different things (ie plays a sound and asks, did you hear a sound)

So DoctorMO, what about using that information somehow?  Wouldn't it be useful for your project if you could integrate with it, or would that be too much work?  The only information perhaps that is missing is the overall model of the computer if it's pre-built.

---

### Post by DoctorMO on 2007-03-09
Oh the emails I've had with the developer of that tool. the main problem for that tool is: all the data is being stored in flat files *wops*; the data is scant and non specific; it assumes users are thick which is why it doesn't reap very much data other than *works*  *doesn't work*

No the idea is to attract the tech segment to the tool in order to fill in the data gaps, this provides the techs with a sense of achievement, completion and identification (they can see their results) all this then provides two advances to other users. 1) allows them to have to hand information about their hardware 2) allows them to search the online database for not only information but computability listings.

I just wish I had some help, like everything complex it's a hard punt to get the first leg standing; and you don't see much until all legs are ready.

As for the model, yes that is also in there; we should be able to pick out what kind of computer you have if it's prebuilt or a laptop.

---

### Post by Yfrwlf on 2007-03-11
> **DoctorMO said:**
> Oh the emails I've had with the developer of that tool. the main problem for that tool is: all the data is being stored in flat files *wops*; the data is scant and non specific; it assumes users are thick which is why it doesn't reap very much data other than *works*  *doesn't work*

No the idea is to attract the tech segment to the tool in order to fill in the data gaps, this provides the techs with a sense of achievement, completion and identification (they can see their results) all this then provides two advances to other users. 1) allows them to have to hand information about their hardware 2) allows them to search the online database for not only information but computability listings.

I just wish I had some help, like everything complex it's a hard punt to get the first leg standing; and you don't see much until all legs are ready.

As for the model, yes that is also in there; we should be able to pick out what kind of computer you have if it's prebuilt or a laptop.

If you try to design the project so that some of the visible aspects of the project are shown to the public, I think you may be able to get a little more attention for the project that way.  I'd think most developers would be much more interested in the technical details though instead of anything visual, and sometimes trying to do it that way is counter-productive, but it still may help some.

I think your project is a very worthy goal though.  I think it'd put more pressure on OEMs to think about Linux compatibility more.  I hope you can find more help :)

---

### Post by DoctorMO on 2007-03-11
technical specifications?

python client using xml data sheets with a direction structure fields configuration, communicating over http to a server running perl to sort, review and translate hardware information. detection in the client is provided by Dbus and HAL with the merging of devices into solid hardware (such as motherboard)

Anything else worth noting technically? it's not very complex, not so much. or do you think a full essay and website on the technicalities would help?

[http://dohickey.wikispaces.com/](http://dohickey.wikispaces.com/)

---

### Post by Yfrwlf on 2007-03-14
> **DoctorMO said:**
> technical specifications?

python client using xml data sheets with a direction structure fields configuration, communicating over http to a server running perl to sort, review and translate hardware information. detection in the client is provided by Dbus and HAL with the merging of devices into solid hardware (such as motherboard)

Anything else worth noting technically? it's not very complex, not so much. or do you think a full essay and website on the technicalities would help?

[http://dohickey.wikispaces.com/](http://dohickey.wikispaces.com/)

I think it might attract some developers to it by mentioning the specifics about your project, yeah.  I don't know how by how much though.  I just think that since it's community driven, one of the most important things is getting the word out, and being more open or transparent about what is going on and how it works I'm sure would help some.  That's all I was trying to say really, I haven't hung around developers enough to know what they really want though. ^^  With the project concept I'm working on, I may end up finding out though, unless it turns out to be a horrible idea.

---

### Post by darrenm on 2007-03-14
I'll have a look at dohickey. Are you sure about the name? I would have been there earlier but the name doesn't really say what its about...

I recently purchased ubuntucompatible.org with a view to doing this kind of thing. I would be willing to donate it to the project if you are interested?

---

### Post by DoctorMO on 2007-03-14
> ]I'll have a look at dohickey. Are you sure about the name? I would have been there earlier but the name doesn't really say what its about...

dohickey is a word which means an unknown device, not only a play on words (because the software tries to do the opposite)  but does give a clue to the function. plus the icon is good no?

> I recently purchased ubuntucompatible.org with a view to doing this kind of thing. I would be willing to donate it to the project if you are interested?

This would be a good domain to have over dohickey-project.com, perhaps an ubuntu specific search box which simply does a search on dohickey-project.com for ubuntu results?

---

### Post by darrenm on 2007-03-15
Well you learn something new every day :) I like the icon, nice and simple. Let me know how you want the domain set up and I'll get on it. My original idea was to have a kind of winedb style site but this project far exceeds that so I have no use for it. (apart from keeping it until Ubuntu rules the world and it will be worth as much as windowscompatible.org ;) )

---

### Post by DoctorMO on 2007-03-15
> Well you learn something new every day I like the icon, nice and simple. Let me know how you want the domain set up and I'll get on it. My original idea was to have a kind of winedb style site but this project far exceeds that so I have no use for it. (apart from keeping it until Ubuntu rules the world and it will be worth as much as windowscompatible.org 

Perhaps it's a British term :-)

Well it's up to you if you want to host an ubuntu search page or if you just want me to make a few skinned pages specifically for ubuntu. we can have a look at it in further depth when everything is working and it's in Beta.

BTW did you try the client? I'm still trying to get people to try and give good feedback here: [http://ubuntuforums.org/showthread.php?t=376000](http://ubuntuforums.org/showthread.php?t=376000)

---

### Post by Yfrwlf on 2007-03-16
> **DoctorMO said:**
> Perhaps it's a British term :-)

Well it's up to you if you want to host an ubuntu search page or if you just want me to make a few skinned pages specifically for ubuntu. we can have a look at it in further depth when everything is working and it's in Beta.

BTW did you try the client? I'm still trying to get people to try and give good feedback here: [http://ubuntuforums.org/showthread.php?t=376000](http://ubuntuforums.org/showthread.php?t=376000)

Actually I thought it came from some weird Western American period, but maybe it was from the UK originally.  I think it still is used a lot by US farmers and ranchers (aka hicks).

---

### Post by DoctorMO on 2007-03-18
> Actually I thought it came from some weird Western American period, but maybe it was from the UK originally. I think it still is used a lot by US farmers and ranchers (aka hicks).

It seems to come from the word hickey which is a term for an unknown skin lesion. dohickey (doohickey) "an unspecified thing" perhaps because devices where seen to be a blemish or because it sounds good in the mouth.

If i'd had called it 'thiny-ma-bob' or 'thingy-ma-jig' it might have been better I guess.

---

### Post by Yfrwlf on 2007-03-19
> **DoctorMO said:**
> It seems to come from the word hickey which is a term for an unknown skin lesion. dohickey (doohickey) "an unspecified thing" perhaps because devices where seen to be a blemish or because it sounds good in the mouth.

If i'd had called it 'thiny-ma-bob' or 'thingy-ma-jig' it might have been better I guess.

So many more consonants though, doo-hickey is much quicker to say :)

---

### Post by DoctorMO on 2007-03-20
Yes, although I should add a translated title for other languages otherwise it won't be obvious. this neatly avoids the problem of name confusion.

I'll be on #dohickey in irc if anyone wants to see me about bugs or ask questions.

---

