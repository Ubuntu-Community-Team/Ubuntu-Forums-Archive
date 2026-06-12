---
title: "How was it tested?"
date: 2013-11-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ardchoille422 on 2013-11-09
I love Linux and have learned many things over the  years, including application development. But lately it just seems like  the problems I'm finding are due to either lack of testing or lack of  programming knowledge/skills. Please read the following with an open mind. This post is not meant to upset anyone.

 **Launcher**
Symptom: Launching an app requires more work in Unity than was required in previous versions of Gnome. 

 In Gnome 2.x, opening an app was as simple as clicking  on Applications > Accessories > app_name. Unity requires more  steps - Click on Unity launch icon in the left panel > Click on apps  icon at the bottom of the unity launch window > click on "See $number  more results > scroll to find the desired app > click app_name. I  realize that the Ubuntu developers want people to use the HUD, but  people want the easiest method and that means point and click, not  typing and hope that the user gets the correct app name. The average  user doesn't want to type, the average user wants to point and click..  otherwise we'd still be using text-only operating systems. The mouse and  trackpad were developed to make things easier, but the Unity developers  seem to be stuck in a previous decade. However, I realize this is Ubuntu's pet project and itsn't going to change.. which is sad.

 **Eye of Gnome (EOG)**
Symptom:  Double-click a picture in a folder. The picture opens but pressing the  "Next" button in EOG sometimes skips pictures in the same folder. EOG  does not display pictures in the same order as they appear in a folder  (alphabetical). 

 Steps to reproduce:

[LIST=1]
[*]Open Nautilus 
[*]Double-click on a picture 
[*]Press the Next button in EOG and keep track of the file names as you page through pictures 
[/LIST]

I can just hear the end-user; "what happened to the picture I just put in that folder?" 

 **Nautilus**
Symptom: The background color of the right pane in Nautilus sometimes changes for no apparent reason. 

 Steps to reproduce: 

[LIST=1]
[*]Open Nautilus and note the background color of the right pane (file view) 
[*]Right-click a folder and choose "Open in new tab" 
[*]Now, note background color of each tab 
[/LIST]

It's not a huge bug, but it does detract from the professionalism of Ubuntu. 

 **Contacts**
Symptom: Missing text input field. 

 Steps to reproduce: 

[LIST=1]
[*]Open the Contacts app 
[*]Click the "New" button in the tool bar 
[*]Notice the missing text input field for "Address" 
[/LIST]

I don't think this app was tested prior to release.

 **System problem reported**
Symptom: At random times I get a message that pops up on the desktop with no way of canceling or reporting the problem. 

 The body of the popup states "System program problem  detected" and the popup window includes two buttons for "Cancel" and  "Report problem...". There is no error code or any type of hint as to  the nature of the problem. The Cancel button does not dismiss the popup  window and the Report problem button yields nothing that the user can  see. If the problem was reported then the popup window should be  dismissed, but this is not the case. It would have been nice of the  developers to at least give the user a hint as to what caused the  problem so the user could include that information in any online  discussion. 

 **Log out, Shutdown**
Symptom: Clicking the system icon and choosing Log Out or Shut Down does nothing.

 In the Unity desktop there is a system icon (gear in  the upper right corner) that yields a user menu. Two of the choices in  this menu are Log Out and Shut Down. However, clicking on either of  those menu items sometimes produces no action. How is the user to log  out or shut down the machine if these menu items produce no effects? 

 I've found many more bugs but I don't wish to waste  time and space listing them here just to be told to file bug reports  elsewhere. I'm sorry to have to tell you this, but it's not the job of the end-user to find and report bugs.. please don't rely on us this way. Do more testing and bug fixing prior to release. Some of the bugs that I found are the  result of a lack of testing prior to release, that's the only logical  conclusion. What else is the end-user supposed to think when they open  an app and there is a missing text input box on the main window? And  this app was chosen for inclusion in a major Linux distribution (Ubuntu)? How is the end-user supposed to trust an  operating system that includes amateur mistakes? The typical response is  "file a bug". But, that is not the  job of the end-user. It is the job of the developer to at least test  their software and attempt fix bugs prior to release. If developers spent more  time on proper software testing, the end-user could spend more time on  getting things done rather than reporting silly mistakes made by the  developers. 

 To the new Linux user, these problems are the fault of  Ubuntu developers. New Linux users don't realize that there are  countless developers all over the world working on the various apps  and/or contributing code. Perhaps that's the problem.. too many cooks in  the kitchen and the lack of a "head chef". 

 I hear the phrase "this will be the year Linux  overtakes the desktop", I've heard it every year since 2003 and every  year it never happens. Linux will never overtake the desktop until the  developers learn how to do a better job of testing their apps  prior to release. I love Ubuntu but it's a good thing Linux is free,  otherwise the user base would be much smaller.

---

### Post by deadflowr on 2013-11-09
I can not reproduce your EOG problem.
My pictures always show first numerically, then alphabetically.
They never skip.
And always in order.

---

### Post by tgalati4 on 2013-11-09
Perhaps Unity is not the best environment for you.  Try Linux Mint Mate and see if that addresses your issues.

---

### Post by ardchoille422 on 2013-11-09
Hmm.. curious. I haven't removed anything from my system, only added some apps. I wonder what I could have done to make EOG act the way it does.

---

### Post by lykwydchykyn on 2013-11-09
> **ardchoille422 said:**
>  I'm sorry to have to tell you this, but it's not the job of the end-user to find and report bugs.. please don't rely on us this way. Do more testing and bug fixing prior to release. Some of the bugs that I found are the  result of a lack of testing prior to release, that's the only logical  conclusion. 

Hate to break this to you... but it pretty much is the end-user's job.  Or at least, the end-users who volunteer to run the betas and report bugs.  

Speaking as a (non-Ubuntu, mind you) developer, developers are *the worst* people for finding bugs.  They only use their software according to the assumptions they built it with.  It takes people who aren't familiar with the design assumptions to really find bugs.

I don't use any of the programs you mentioned, so I have no idea if these bugs are reproducible on another system or not.  But if they're on your system, there's a good chance their due to some condition specific to your system, and if that's the case, only you can report the bug.

Give developers the benefit of the doubt; they aren't idiots, you know.  Maybe start your logic with that assumption, and see if you come to a different conclusion.

---

### Post by ardchoille422 on 2013-11-09
I've tried several distros, they all have their own set of problems.

I feel that most of the problems with Ubuntu would disappear if the following points were adopted:
* Put more effort into testing software before release (how was a missing text box overlooked?)
* Avoid relying on the user base to report bugs (developer accountability)
* Switch from a 6 month release cycle to a "release it when it's ready" cycle (perfection cannot be rushed)
* Concentrate less on being "cutting edge" and more on quality software (quality takes time)

Red Hat and Debian include older software, yes, but the reason for that is because they do more extensive testing before sending the release out the door. Perhaps Canonical could take a lesson from these two distros.

We don't have to be "the first", but we need to be "the best", and doing that takes time and attention to detail.

Just my $0.02

---

### Post by ardchoille422 on 2013-11-09
> **lykwydchykyn said:**
> Hate to break this to you... but it pretty much is the end-user's job.  Or at least, the end-users who volunteer to run the betas and report bugs.  

Speaking as a (non-Ubuntu, mind you) developer, developers are *the worst* people for finding bugs.  They only use their software according to the assumptions they built it with.  It takes people who aren't familiar with the design assumptions to really find bugs.

I don't use any of the programs you mentioned, so I have no idea if these bugs are reproducible on another system or not.  But if they're on your system, there's a good chance their due to some condition specific to your system, and if that's the case, only you can report the bug.

Give developers the benefit of the doubt; they aren't idiots, you know.  Maybe start your logic with that assumption, and see if you come to a different conclusion.

Yes, I understand developers aren't idiots, and I praise them for their coding knowledge. I develop some apps that I use and it takes a lot of time and effort. Developers are awesome! I just feel that someone at Canonical needs to do more testing before Ubuntu is released. A missing text input box for the Address field in the Contacts app? How was this missed? If this was overlooked, what other important items were overlooked?

I'm not trying to berate anyone, I'm just trying (hoping) to get Canonical to understand that more testing is needed before releasing Ubuntu. This is the best distro around, but some of the bugs detract from the value of the distro. If the distro improves I'm betting donations would increase.

---

### Post by ian-weisser on 2013-11-09
Please don't save up big rants like these. You can benefit much more from a separate thread for each issue.


> **ardchoille422 said:**
> **Launcher**
Symptom: Launching an app requires more work in Unity than was required in previous versions of Gnome. 

By the generally accepted definition of "more work" meaning more keystrokes or more mouse clicks, this is demonstrably not true. Common applications in the launcher bar: one click or keystroke. Occasionally-used applications: two clicks. Rarely-used applications: three clicks and/or a couple keystrokes. Unity gets easier as you use it in two ways - you discover more features, and Zeitgeist moves your most-used applications closer to the top of the search results.

If you don't *like* Unity, or you have imprinted on something else, that's okay. You don't have to like it. Nobody will force you to use it, and there are plenty of alternatives. But don't offer this they-are-just-wrong-and-unreasoning ranting. The Ubuntu designers publish their work, ask for feedback, are globally available at the online Ubuntu Developer Summits, and have done a huge amount of real usability research and testing in this field.

The average user *doesn't* want to point and click - that's Unity's point. The average user want the machine to be psychic, to adaptively understand what the user wants, and to provide the most common choices first. The point-and-click interface is the *hindrance* (and is tough on a tiny phone screen, too); the user wants the application at the end of the process, not the process itself.

It's okay to not like their work. But to reject their work with a rather childish political argument like "it's-merely-their-pet-project" really diminishes your credibility on the topic.

And I don't even use Unity very often. I imprinted on something else, and I still like something else.


> **ardchoille422 said:**
> 
 **Eye of Gnome (EOG)**
 **Nautilus**
 **Contacts**
**Log out, Shutdown**

Well, have your reported these bugs properly?
Have you helped to confirm other reported bugs? 
Have you helped triage bugs so developers can spend time fixing the bugs instead of clerical work?
Have you helped test pre-release software? The developers have *begged* for more testing volunteers, on as many platforms as possible.
Have you contributed patches? Updated documentation? Packaged? Backported? Joined a LoCo? Helped other users?







> **ardchoille422 said:**
> **System problem reported**
Symptom: At random times I get a message that pops up on the desktop with no way of canceling or reporting the problem. 
It's not reporting the problem to you. It's reporting the problem back to daisy.ubuntu.com.
You can check the apport logs to see what was reported.
You can check [http://errors.ubuntu.com](http://errors.ubuntu.com) to see the most common reported problems. The Ubuntu Bug Squad takes those reports very seriously.



 > **ardchoille422 said:**
> it's not the job of the end-user to find and report bugs
That seems like a paying-customer attitude that strongly damages your credibility in this community.
If you are a paying customer, you have the right to complain about a product or ask for a refund.
But  you're not a customer of the Ubuntu project. Canonical didn't earn a  penny from your purchase price. You're a member of this community, and  nobody in this community cares about unconstructive complaints or rants. Instead, we work  together to improve it. Constructive suggestions and discussion are always welcome.

Who, exactly, do you expect to do all this additional testing...for free? Volunteers. Community members. The testing team. In other words, us. 



> **ardchoille422 said:**
> Perhaps that's the problem.. too many cooks in  the kitchen and the lack of a "head chef".
I urge you to participate in next week's Ubuntu Developer Summit ( [http://summit.ubuntu.com](http://summit.ubuntu.com) ) and see exactly how Ubuntu gets put together. You may be surprised just how focused and disciplined many teams are, how strong the focus on quality and testing really is, the strategies for better testing, more testing, sustainable testing, better bug reporting, automated bug reporting, and how the feedback process really works (well) in this community.

Ubuntu's quality has *hugely* improved in the past few years. System crashes and X crashes are *way* down. Boot is faster, and printing and video are no longer arcane magic. Honestly, given a choice between the system-killing X and print and other bugs we used to have against the rather lightweight missing-text field and other application bugs of today...I'll stick with today's bugs. Maybe you can help us figure out how to test applications more and better before release.

We're open to new ideas and new contributors like you.

---

### Post by The Spectre on 2013-11-09
> **ardchoille422 said:**
> 
I feel that most of the problems with Ubuntu would disappear if the following points were adopted:
* Put more effort into testing software before release (how was a missing text box overlooked?)
* Avoid relying on the user base to report bugs (developer accountability)
* Switch from a 6 month release cycle to a "release it when it's ready" cycle (perfection cannot be rushed)
* Concentrate less on being "cutting edge" and more on quality software (quality takes time)

Red Hat and Debian include older software, yes, but the reason for that is because they do more extensive testing before sending the release out the door. Perhaps Canonical could take a lesson from these two distros.

We don't have to be "the first", but we need to be "the best", and doing that takes time and attention to detail.
You didn't specify what version of Ubuntu you are running but my guess is 13.10 or 13.04 which by design is to have some of the latest cutting edge features and is kind of used as a testing ground for the next LTS Release of Ubuntu.

If you don't want or need the latest features and want a rock solid version of Ubuntu that is well established and has gone through more testing then stick with the LTS Release.

Even Windows has many "unknown" bugs when it is first released that aren't discovered until it is released to the general public and it isn't free.

There are way to many hardware and software combinations that could potentially cause problems to pop up and it is user testing and feedback that helps fix them in a timely manner.

---

### Post by craig10x on 2013-11-09
Unity is certainly simple and intuitive to use...you put your favorite and most used apps on the dock for quick 1 click access...rarely used apps you simply open the dash and type the first few letters of what you want, there it is...click and it is open...can you get anymore simple and basic then that???

---

### Post by ardchoille422 on 2013-11-09
> **ian-weisser said:**
> Please don't save up big rants like these. You can benefit much more from a separate thread for each issue.




By the generally accepted definition of "more work" meaning more keystrokes or more mouse clicks, this is demonstrably not true. Common applications in the launcher bar: one click or keystroke. Occasionally-used applications: two clicks. Rarely-used applications: three clicks and/or a couple keystrokes. Unity gets easier as you use it in two ways - you discover more features, and Zeitgeist moves your most-used applications closer to the top of the search results.

If you don't *like* Unity, or you have imprinted on something else, that's okay. You don't have to like it. Nobody will force you to use it, and there are plenty of alternatives. But don't offer this they-are-just-wrong-and-unreasoning ranting. The Ubuntu designers publish their work, ask for feedback, are globally available at the online Ubuntu Developer Summits, and have done a huge amount of real usability research and testing in this field.

The average user *doesn't* want to point and click - that's Unity's point. The average user want the machine to be psychic, to adaptively understand what the user wants, and to provide the most common choices first. The point-and-click interface is the *hindrance* (and is tough on a tiny phone screen, too); the user wants the application at the end of the process, not the process itself.

It's okay to not like their work. But to reject their work with a rather childish political argument like "it's-merely-their-pet-project" really diminishes your credibility on the topic.

And I don't even use Unity very often. I imprinted on something else, and I still like something else.



Well, have your reported these bugs properly?
Have you helped to confirm other reported bugs? 
Have you helped triage bugs so developers can spend time fixing the bugs instead of clerical work?
Have you helped test pre-release software? The developers have *begged* for more testing volunteers, on as many platforms as possible.
Have you contributed patches? Updated documentation? Packaged? Backported? Joined a LoCo? Helped other users?








It's not reporting the problem to you. It's reporting the problem back to daisy.ubuntu.com.
You can check the apport logs to see what was reported.
You can check [http://errors.ubuntu.com](http://errors.ubuntu.com) to see the most common reported problems. The Ubuntu Bug Squad takes those reports very seriously.



 
That seems like a paying-customer attitude that strongly damages your credibility in this community.
If you are a paying customer, you have the right to complain about a product or ask for a refund.
But  you're not a customer of the Ubuntu project. Canonical didn't earn a  penny from your purchase price. You're a member of this community, and  nobody in this community cares about unconstructive complaints or rants. Instead, we work  together to improve it. Constructive suggestions and discussion are always welcome.

Who, exactly, do you expect to do all this additional testing...for free? Volunteers. Community members. The testing team. In other words, us. 




I urge you to participate in next week's Ubuntu Developer Summit ( [http://summit.ubuntu.com](http://summit.ubuntu.com) ) and see exactly how Ubuntu gets put together. You may be surprised just how focused and disciplined many teams are, how strong the focus on quality and testing really is, the strategies for better testing, more testing, sustainable testing, better bug reporting, automated bug reporting, and how the feedback process really works (well) in this community.

Ubuntu's quality has *hugely* improved in the past few years. System crashes and X crashes are *way* down. Boot is faster, and printing and video are no longer arcane magic. Honestly, given a choice between the system-killing X and print and other bugs we used to have against the rather lightweight missing-text field and other application bugs of today...I'll stick with today's bugs. Maybe you can help us figure out how to test applications more and better before release.

We're open to new ideas and new contributors like you.

I have an idea about the beta testing phase. Back when I was helping beta test Ubuntu the beta testers were reporting bugs as they were found. This is good, but I feel it can be better. Issues can be overlooked when a person is focusing on hundreds of items, but more attention to detail can be paid when a person is focusing on a few items.

Institute beta groups. Groups can be things like Office, Internet, File system, programming, etc.
Find volunteers to assign to a group, such as the Office group. The people assigned to this group should focus on testing office-related apps, such as the Contacts app or the Libre Office suite. These folks can report any bug they find but their primary focus is the apps that fall within their group. Have them use the app on a day-to-day basis and report what they find.

If you open the Contacts app that ships with Ubuntu and click the "New" button in the top left corner, you'll see that the text input box for the Address field is missing. I feel this issue would have been resolved prior to release had someone been focusing on Office apps during beta testing. If a large issue such as this cannot be resolved before release then that app is removed from the release, or replaced with a similar app.

I don't think I've beta tested anything since Dapper (Ubuntu 6.06) so this idea may have been implemented already without my knowledge. Has this type of thing been implemented? If not, can it be implemented? I would definitely be willing to volunteer to be a member of a group. 

The reason I don't do beta testing anymore is because I once looked for a bug report, didn't find one, so I tested an app. Upon finding bugs I attempted to report them only to find that there were several reports made just prior to mine. I feel beta groups would help avoid duplicate work/reports.

---

### Post by ardchoille422 on 2013-11-09
> **The Spectre said:**
> You didn't specify what version of Ubuntu you are running but my guess is 13.10 or 13.04 which by design is to have some of the latest cutting edge features and is kind of used as a testing ground for the next LTS Release of Ubuntu.

If you don't want or need the latest features and want a rock solid version of Ubuntu that is well established and has gone through more testing then stick with the LTS Release.

Even Windows has many "unknown" bugs when it is first released that aren't discovered until it is released to the general public and it isn't free.

There are way to many hardware and software combinations that could potentially cause problems to pop up and it is user testing and feedback that helps fix them in a timely manner.

Yes, I failed to specify the release I am using, I apologize for that. I am running Ubuntu 13.10.

Perhaps if as much focus and attention to detailed were paid in regular releases as is paid to LTS releases, then the regular releases would improve.

I wonder if this would benefit Ubuntu:
* switch from a 6 month release cycle to a yearly release cycle (more time for improvements)
* Implement a "beta" release alongside the regular releases (more focus on issues)
* The next regular release would include improvements from the current beta release

I know that sounds a lot like what Debian does, but have you ever used a stable Debian release? This type of thing seems to be working well for them. It also seems to work well for Red Hat - they use Fedora as the testing ground for the next RHEL.

---

### Post by ian-weisser on 2013-11-09
> **ardchoille422 said:**
> I have an idea about the beta testing phase. Back when I was helping beta test Ubuntu the beta testers were reporting bugs as they were found. This is good, but I feel it can be better. Issues can be overlooked when a person is focusing on hundreds of items, but more attention to detail can be paid when a person is focusing on a few items.

Institute beta groups. Groups can be things like Office, Internet, File system, programming, etc.
Find volunteers to assign to a group, such as the Office group. The people assigned to this group should focus on testing office-related apps, such as the Contacts app or the Libre Office suite. These folks can report any bug they find but their primary focus is the apps that fall within their group. Have them use the app on a day-to-day basis and report what they find.

If you open the Contacts app that ships with Ubuntu and click the "New" button in the top left corner, you'll see that the text input box for the Address field is missing. I feel this issue would have been resolved prior to release had someone been focusing on Office apps during beta testing. If a large issue such as this cannot be resolved before release then that app is removed from the release, or replaced with a similar app.

I don't think I've beta tested anything since Dapper (Ubuntu 6.06) so this idea may have been implemented already without my knowledge. Has this type of thing been implemented? If not, can it be implemented? I would definitely be willing to volunteer to be a member of a group. 

The reason I don't do beta testing anymore is because I once looked for a bug report, didn't find one, so I tested an app. Upon finding bugs I attempted to report them only to find that there were several reports made just prior to mine. I feel beta groups would help avoid duplicate work/reports.

I cheerfully withdraw my previous customer-attitude comment. From your detail, it's obvious that you have clearly thought about the matter and have a lot of constructive suggestions about how the community testing resources can be used more effectively.

THANK YOU for helping test!
THANK YOU for confirming bug reports!

There are a few Ubuntu Developer Summit (UDS) sessions coming up next week related to bugs, system quality, application quality, and related topics. Here is a sample:
[http://summit.ubuntu.com/uds-1311/meeting/21987/community-1311-quality-bugsquad/](http://summit.ubuntu.com/uds-1311/meeting/21987/community-1311-quality-bugsquad/)
[http://summit.ubuntu.com/uds-1311/meeting/22064/community-1311-quality-calls-for-testing/](http://summit.ubuntu.com/uds-1311/meeting/22064/community-1311-quality-calls-for-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22065/community-1311-quality-community-exploratory-testing/](http://summit.ubuntu.com/uds-1311/meeting/22065/community-1311-quality-community-exploratory-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22022/appdev-1311-getting-feedback/](http://summit.ubuntu.com/uds-1311/meeting/22022/appdev-1311-getting-feedback/)
[http://summit.ubuntu.com/uds-1311/meeting/22071/appdev-1311-core-apps-test-review/](http://summit.ubuntu.com/uds-1311/meeting/22071/appdev-1311-core-apps-test-review/)
[http://summit.ubuntu.com/uds-1311/meeting/22063/community-1311-quality-autopilot-image-testing/](http://summit.ubuntu.com/uds-1311/meeting/22063/community-1311-quality-autopilot-image-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22079/appdev-1311-sdk-apps-performance/](http://summit.ubuntu.com/uds-1311/meeting/22079/appdev-1311-sdk-apps-performance/)
[http://summit.ubuntu.com/uds-1311/meeting/21973/core-1311-lts-upgrade-testing/](http://summit.ubuntu.com/uds-1311/meeting/21973/core-1311-lts-upgrade-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22062/community-1311-coreapps-testing/](http://summit.ubuntu.com/uds-1311/meeting/22062/community-1311-coreapps-testing/)

UDS is online and open to all community members. Sessions can be highly technical and designed to get concurrence from as many stakeholders as possible - to make real decisions.

I really like the idea of coordinating a set of application-centered teams. But then, I like structure a bit more than some in the community....
I speculate that some applications may already have a set of ad-hoc testers...PPA users are one example. Specific teams like the Mozilla team are another example.

Perhaps we just need some volunteer cheerleaders to recruit more testers toward some applications? Or to train new testers? Or growing a few new leaders to coordinate existing testers?

I wonder if we lack data on how much testing is going on, what's being duplicated, and what's being missed?

---

### Post by lykwydchykyn on 2013-11-09
So, I got curious about these bugs, and booted to a live CD.  Couldn't reproduce the Nautilus bug, but the address bug is right there big as life.  It is a bit of wonder how things like that get through beta testing.  As far as I can tell, nobody has reported it as a bug either.  Which may be why it hasn't been fixed...

---

### Post by kostkon on 2013-11-09
> **ardchoille422 said:**
> Unity requires more  steps - Click on Unity launch icon in the left panel > Click on apps  icon at the bottom of the unity launch window > click on "See $number  more results > scroll to find the desired app > click app_name. I  realize that the Ubuntu developers want people to use the HUD, but  people want the easiest method and that means point and click, not  typing and hope that the user gets the correct app name. The average  user doesn't want to type, the average user wants to point and click..  otherwise we'd still be using text-only operating systems. The mouse and  trackpad were developed to make things easier, but the Unity developers  seem to be stuck in a previous decade.
The founders of Google would be interested to hear about this.

---

### Post by ardchoille422 on 2013-11-10
> **lykwydchykyn said:**
> So, I got curious about these bugs, and booted to a live CD.  Couldn't reproduce the Nautilus bug, but the address bug is right there big as life.  It is a bit of wonder how things like that get through beta testing.  As far as I can tell, nobody has reported it as a bug either.  Which may be why it hasn't been fixed...

The Nautilus bug isn't a big deal. However, the address bug is a deal breaker for that app. I'd be willing to bet that this bug would have been caught had there been teams of testers focusing on certain apps.

The address bug was brought to my attention by a new Ubuntu user, I helped get her off of Windows 7. I asked if she would be interested in filing a bug report and she said that she didn't have time. She also said she would simply use another app. This was one of my points, the average end user doesn't care about filing bug reports, it's easier to just use another app. This is one of the reasons that I feel developers shouldn't rely too heavily on the end user filing bug reports. One can only imagine the number of bug reports that never get filed because of this.

---

### Post by ardchoille422 on 2013-11-10
> **ian-weisser said:**
> I cheerfully withdraw my previous customer-attitude comment. From your detail, it's obvious that you have clearly thought about the matter and have a lot of constructive suggestions about how the community testing resources can be used more effectively.

THANK YOU for helping test!
THANK YOU for confirming bug reports!

There are a few Ubuntu Developer Summit (UDS) sessions coming up next week related to bugs, system quality, application quality, and related topics. Here is a sample:
[http://summit.ubuntu.com/uds-1311/meeting/21987/community-1311-quality-bugsquad/](http://summit.ubuntu.com/uds-1311/meeting/21987/community-1311-quality-bugsquad/)
[http://summit.ubuntu.com/uds-1311/meeting/22064/community-1311-quality-calls-for-testing/](http://summit.ubuntu.com/uds-1311/meeting/22064/community-1311-quality-calls-for-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22065/community-1311-quality-community-exploratory-testing/](http://summit.ubuntu.com/uds-1311/meeting/22065/community-1311-quality-community-exploratory-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22022/appdev-1311-getting-feedback/](http://summit.ubuntu.com/uds-1311/meeting/22022/appdev-1311-getting-feedback/)
[http://summit.ubuntu.com/uds-1311/meeting/22071/appdev-1311-core-apps-test-review/](http://summit.ubuntu.com/uds-1311/meeting/22071/appdev-1311-core-apps-test-review/)
[http://summit.ubuntu.com/uds-1311/meeting/22063/community-1311-quality-autopilot-image-testing/](http://summit.ubuntu.com/uds-1311/meeting/22063/community-1311-quality-autopilot-image-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22079/appdev-1311-sdk-apps-performance/](http://summit.ubuntu.com/uds-1311/meeting/22079/appdev-1311-sdk-apps-performance/)
[http://summit.ubuntu.com/uds-1311/meeting/21973/core-1311-lts-upgrade-testing/](http://summit.ubuntu.com/uds-1311/meeting/21973/core-1311-lts-upgrade-testing/)
[http://summit.ubuntu.com/uds-1311/meeting/22062/community-1311-coreapps-testing/](http://summit.ubuntu.com/uds-1311/meeting/22062/community-1311-coreapps-testing/)

UDS is online and open to all community members. Sessions can be highly technical and designed to get concurrence from as many stakeholders as possible - to make real decisions.

I really like the idea of coordinating a set of application-centered teams. But then, I like structure a bit more than some in the community....
I speculate that some applications may already have a set of ad-hoc testers...PPA users are one example. Specific teams like the Mozilla team are another example.

Perhaps we just need some volunteer cheerleaders to recruit more testers toward some applications? Or to train new testers? Or growing a few new leaders to coordinate existing testers?

I wonder if we lack data on how much testing is going on, what's being duplicated, and what's being missed?

I would be VERY interested in joining a beta testing team that has some focus. I don't do well when someone says "here's the Ubuntu release, let me know if there are problems". I work much better if someone says "please test this app or that app. Use it as much as possible and try all settings and feature. Then let me know if you have any problems". I can spend a couple days using only one app and then report back. But, trying to test everything in the distro would take months and bug reports would be filing just prior to the next Ubuntu release. I feel that app=-focused teams would be much more beneficial.

Good point! Maybe we need to find out exactly who is testing what and for how long. Are they trying all settings and features? When I beta test something, I attack it as if I'm trying to break it.. problems popup easier this way :)

How can I get the core Ubuntu folks involved in this thread?

EDIT: Also, I am hearing impaired. It isn't usually a problem unless videos/conferences lack subtitles or closed captioning, then I am unable to understand what is happening. Are the UDS videos typically subtitled or captioned?

---

### Post by Johan De Cauwer on 2013-11-10
> **ardchoille422 said:**
>  I hear the phrase "this will be the year Linux  overtakes the desktop", I've heard it every year since 2003 and every  year it never happens. Linux will never overtake the desktop until the  developers learn how to do a better job of testing their apps  prior to release. I love Ubuntu but it's a good thing Linux is free,  otherwise the user base would be much smaller.
There are a few reasons why Linux hasn't made it to the desktop but they have little to do with temporary bugs in a rolling distribution. Think about the fact that computers are preloaded with Windows, for instance.
The number of XP installations still in existence only demonstrate how unwilling people are to change, even if a lot of them are dependent on obsolete unmaintained proprietary software. Yet even an older Linux distribution performs better than XP.

Your grief is about Ubuntu (or Fedora or Opensuse or...) and the short release cycle. A distribution like Centos or Debian (or even the LTS of Ubuntu) doesn't have this problem.

Actually, there are paying Linux desktop distributions. I guess they sell, otherwise why bother to make a site like [https://www.suse.com/products/desktop/](https://www.suse.com/products/desktop/) but then of course this is an LTS solution.

And finally, Linux is winning in a major way because Android is a shell over Linux. On tablets and smartphones Linux rules.

So I tend to disagree with your assessment of the reason why Linux doesn't break through on the desktop. It's simply because end users are mostly afraid of ending up with a computer that doesn't work anymore.

---

### Post by coffeecat on 2013-11-10
> **ardchoille422 said:**
> 
 **Contacts**
Symptom: Missing text input field. 

 Steps to reproduce: 

[LIST=1]
[*]Open the Contacts app 
[*]Click the "New" button in the tool bar 
[*]Notice the missing text input field for "Address" 
[/LIST]

I don't think this app was tested prior to release.

Perhaps I'm missing what you are trying to say, but in my 13.10 system:

Envelope icon -> Contacts -> Click on New Contact button top-left -> New Contact window opens with 6 tabs. There are more than adequate address fields under the Private and Work tabs. I don't see the problem you are describing.

---

### Post by Elfy on 2013-11-10
> **ardchoille422 said:**
> I would be VERY interested in joining a beta testing team that has some focus. I don't do well when someone says "here's the Ubuntu release, let me know if there are problems". I work much better if someone says "please test this app or that app. Use it as much as possible and try all settings and feature. Then let me know if you have any problems". I can spend a couple days using only one app and then report back. But, trying to test everything in the distro would take months and bug reports would be filing just prior to the next Ubuntu release. I feel that app=-focused teams would be much more beneficial.

Good point! Maybe we need to find out exactly who is testing what and for how long. Are they trying all settings and features? When I beta test something, I attack it as if I'm trying to break it.. problems popup easier this way :)

How can I get the core Ubuntu folks involved in this thread?

EDIT: Also, I am hearing impaired. It isn't usually a problem unless videos/conferences lack subtitles or closed captioning, then I am unable to understand what is happening. Are the UDS videos typically subtitled or captioned?

Seems you're talking about the exploratory testing they're trying to get up and going.

[https://wiki.ubuntu.com/QATeam/Roles/Tester](https://wiki.ubuntu.com/QATeam/Roles/Tester)
[http://www.theorangenotebook.com/2013/10/quality-and-community-in-trusty-cycle.html](http://www.theorangenotebook.com/2013/10/quality-and-community-in-trusty-cycle.html)

You've seen the links to the vUDS - that's the best place to go to find what's expected to happen.

---

### Post by buzzingrobot on 2013-11-10
> **ardchoille422 said:**
> ... but it's not the job of the end-user to find and report bugs..

Well, yes, it is.

Most FOSS products are made by people and organizations who either receive no payment for their efforts or who lack the resources to fund in-depth in-house testing.

That's why FOSS products typically have public alpha and beta releases:  To let the public wring out early code and, developers hope, report bugs. Whether or not all bugs are found and patched before the general release is a matter of luck:  It is impossible for anyone -- even Apple and Microsoft -- to test software in every possible situation. 

The independent commercial developers who try to earn a living writing applications for OS X are in a very similar position.  

The picture for Ubuntu and other Linux distribution is further complicated by the fact that they are primarily packagers of other software released by developers that are not responsible to them.  

This is the nature of FOSS.  And, it's also the result of the reality that 20 years of history shows Linux users aren't prepared to pay for software.  Perhaps if a profit could be made selling Linux distributions, then those distributions could afford to do more in-house testing.

On the other hand, Linux bug tracking systems are typically public and open, and any user can participate.  That doesn't happen on the other side of the fence.

---

### Post by ardchoille422 on 2013-11-10
> **buzzingrobot said:**
> Well, yes, it is.

Most FOSS products are made by people and organizations who either receive no payment for their efforts or who lack the resources to fund in-depth in-house testing.

That's why FOSS products typically have public alpha and beta releases:  To let the public wring out early code and, developers hope, report bugs. Whether or not all bugs are found and patched before the general release is a matter of luck:  It is impossible for anyone -- even Apple and Microsoft -- to test software in every possible situation. 

The independent commercial developers who try to earn a living writing applications for OS X are in a very similar position.  

The picture for Ubuntu and other Linux distribution is further complicated by the fact that they are primarily packagers of other software released by developers that are not responsible to them.  

This is the nature of FOSS.  And, it's also the result of the reality that 20 years of history shows Linux users aren't prepared to pay for software.  Perhaps if a profit could be made selling Linux distributions, then those distributions could afford to do more in-house testing.

On the other hand, Linux bug tracking systems are typically public and open, and any user can participate.  That doesn't happen on the other side of the fence.

No, it's not the job of the end user to find and/or report bugs and the developers shouldn't make such an assumption that he or she is. At least I don't remember signing up for this. Can you see the implications here? Assume for a moment that I'm a developer. If it's assumed that the end user will find and report bugs, then why should I fix the bugs in my software before I release it? Why should I  do any bug hunting prior to release if I'm assuming that the end user will do my job for me? This gives developers an excuse to release less-than-perfect software. You're placing a burden on the end user that the end user did not voluntarily accept. With all due respect, that can easily be construed as slavery. This is part of the problem, some developers are making this faulty assumption and it's part of the reason that things like [this]("http://ubuntuforums.org/showthread.php?t=2186904&p=12843545#post12843545") end up in the final release. You can sugar-coat it all you want but it's a nothing more than a faulty assumption.

---

### Post by deadflowr on 2013-11-10
> **ardchoille422 said:**
> No, it's not, the end user is under no obligation to find and/or report bugs and the developers shouldn't make such an assume that he or she is. At least I don't remember signing up for this. You're placing a burden on the end user that the end user did not voluntarily accept. With all due respect, that can easily be construed as slavery. This is part of the problem, some folks are making this faulty assumption. You can sugar-coat it all you want but it's a nothing more than a faulty assumption.

Of course you're not under any obligation to report bugs.
But then you have no right to complain about the bugs you find if you don't.:p

---

### Post by ardchoille422 on 2013-11-10
> **coffeecat said:**
> Perhaps I'm missing what you are trying to say, but in my 13.10 system:

Envelope icon -> Contacts -> Click on New Contact button top-left -> New Contact window opens with 6 tabs. There are more than adequate address fields under the Private and Work tabs. I don't see the problem you are describing.

You must have launched the wrong app, there are no tabs in the Contacts app that ships with Ubuntu 13.10. Another user in this thread [found the bug I mentioned]("http://ubuntuforums.org/showthread.php?t=2186904&p=12843545#post12843545").

---

### Post by buzzingrobot on 2013-11-10
> **ardchoille422 said:**
> No, it's not, the end user is under no obligation to find and/or report bugs and the developers shouldn't make such an assume that he or she is. At least I don't remember signing up for this. You're placing a burden on the end user that the end user did not voluntarily accept. With all due respect, that can easily be construed as slavery. This is part of the problem, some folks are making this faulty assumption. You can sugar-coat it all you want but it's a nothing more than a faulty assumption.

It isn't obligatory.  it's entirely voluntary, as is almost everything in Linux, including writing software and creating distributions. If you don't want to report bugs, that's fine. No one expects it of you.

There is a hope -- not an assumption -- that users will file bug reports because, apart from them, there's no one else available to do that except other developers.  I used to earn a living managing and coordinating software development. I learned very early on that developers make poor testers. The only way to know how  users will *use* software is to give it to them, watch what they do, and ask them to tell you what they didn't like.

The fact is that even if I, as a user, report a bug in some application included in Ubuntu, and if that bug report is then reported back the chain to the developer currently maintaining it, no guarantee exists that the developer will fix the bug.   Most of what's in a distribution is *not* there because someone is paid to write it and fix it.  

The "slavery" remark is w-a-y over the top.

---

### Post by coffeecat on 2013-11-10
> **ardchoille422 said:**
> You must have launched the wrong app, there are no tabs in the Contacts app that ships with Ubuntu 13.10. Another user in this thread [found the bug I mentioned]("http://ubuntuforums.org/showthread.php?t=2186904&p=12843545#post12843545").

It seems that there are two contacts apps that come as default in 13.10, which is curious. If you type contacts in the dash and open that contacts apps, I can see what you mean. No address field. It's odd that wasn't picked up in pre-release testing.

However, I suggest you open the other contacts app from the notification area - from the envelope icon - as I describe in my earlier post. You'll find more fields than I know what to do with, including 6 fields for each of private and work addresses.

---

### Post by ardchoille422 on 2013-11-10
> **coffeecat said:**
> It seems that there are two contacts apps that come as default in 13.10, which is curious. If you type contacts in the dash and open that contacts apps, I can see what you mean. No address field. It's odd that wasn't picked up in pre-release testing.
This is a stand-alone contacts app that ships with Ubuntu 13.10. The reason it wasn't fixed prior to release may have been that a developer assumed that the end user will find and report bugs so the developer didn't have to do any bug-hunting before release.. which is part of the reason for this thread.

> **coffeecat said:**
> However, I suggest you open the other contacts app from the notification area - from the envelope icon - as I describe in my earlier post. You'll find more fields than I know what to do with, including 6 fields for each of private and work addresses.

If, in that Contacts app, you go to the menu bar at the top of the screen and click "About", you'll find that this is actually the contacts portion of the Thunderbird email app.

---

### Post by ardchoille422 on 2013-11-10
> **buzzingrobot said:**
> It isn't obligatory.  it's entirely voluntary, as is almost everything in Linux, including writing software and creating distributions. If you don't want to report bugs, that's fine. No one expects it of you.

There is a hope -- not an assumption -- that users will file bug reports because, apart from them, there's no one else available to do that except other developers.  I used to earn a living managing and coordinating software development. I learned very early on that developers make poor testers. The only way to know how  users will *use* software is to give it to them, watch what they do, and ask them to tell you what they didn't like.

The fact is that even if I, as a user, report a bug in some application included in Ubuntu, and if that bug report is then reported back the chain to the developer currently maintaining it, no guarantee exists that the developer will fix the bug.   Most of what's in a distribution is *not* there because someone is paid to write it and fix it.  

The "slavery" remark is w-a-y over the top.

You have a point, please accept my apologies for the slavery remark.

I just feel that the quality of our software will vastly improve if the developers at least run their apps and use the features prior to release. The missing Address field in the Contacts app tells me that even this practice wasn't followed with this particular app. If the quality of software increases, donations will increase. If donations increase, the developers feel better about developing apps. Product quality equates to happy customers.. and happy customers mean repeat customers as well as free advertising in the form of word-of-mouth praise.

---

### Post by lykwydchykyn on 2013-11-10
> **buzzingrobot said:**
> 
The "slavery" remark is w-a-y over the top.

Yeah; if anything, demanding that developers work harder to make the software meet our needs -- and then give it to us for free -- is slavery.

I would assume some developer ran that address book app before committing the code.  But it probably worked for him because of some assumption or previous configuration unique to his system.

But here's the kicker; supposedly 20 Million people use Ubuntu.  If that's true, than presumably there are at least a few tens of thousands running 13.10 and using that contact app.  Yet nobody reported this as a bug.  To me that's a bigger head-scratcher than why a developer didn't find this problem.

I'm willing to bet that, apart from some Canonical employees, every Ubuntu developer was an Ubuntu (or other Linux distro) user who decided to get involved and make it better.  That's how open source works.  Does every user have to step up and contribute?  Nope.  But if they can't be bothered, what obligation does anyone else have to bother?

---

### Post by ian-weisser on 2013-11-10
> **lykwydchykyn said:**
> [...]presumably there are at least a few tens of thousands running 13.10 and using that contact app.  Yet nobody reported this as a bug.  To me that's a bigger head-scratcher[...]

Yes, that is really puzzling.

---

### Post by ardchoille422 on 2013-11-10
> **lykwydchykyn said:**
> Yeah; if anything, demanding that developers work harder to make the software meet our needs -- and then give it to us for free -- is slavery.
Yes, huge mistake on my part.

> **lykwydchykyn said:**
>  I would assume some developer ran that address book app before committing the code.  But it probably worked for him because of some assumption or previous configuration unique to his system.

But here's the kicker; supposedly 20 Million people use Ubuntu.  If that's true, than presumably there are at least a few tens of thousands running 13.10 and using that contact app.  Yet nobody reported this as a bug.  To me that's a bigger head-scratcher than why a developer didn't find this problem.
I would be more willing to believe some people ran the app, assumed it was broken and found another app to do the job because they didn't have the time or the inclination to report the bug. The fact that there was no bug report means that (a) no one runs the app, or (b) no one was willing to file a bug report. I feel that developers can't just assume that users will file bug reports, this assumption is based on wishful thinking. But, that's just my opinion.

> **lykwydchykyn said:**
>  I'm willing to bet that, apart from some Canonical employees, every Ubuntu developer was an Ubuntu (or other Linux distro) user who decided to get involved and make it better.  That's how open source works.  Does every user have to step up and contribute?  Nope.  But if they can't be bothered, what obligation does anyone else have to bother?

---

### Post by buzzingrobot on 2013-11-10
> **ardchoille422 said:**
> 
Red Hat and Debian include older software, yes, but the reason for that is because they do more extensive testing before sending the release out the door.

Red Hat's RHEL and Debian are Stable not as free of bugs as they are because they use old software.  They get that way because the code base is frozen and the only permitted changes, as much as possible, are patches to remedy bugs and security issues *reported by users*. RH does backport new capabilities into the RHEL kernel.

---

### Post by ardchoille422 on 2013-11-10
> **buzzingrobot said:**
> Red Hat's RHEL and Debian are Stable not as free of bugs as they are because they use old software.  They get that way because the code base is frozen and the only permitted changes, as much as possible, are patches to remedy bugs and security issues *reported by users*. RH does backport new capabilities into the RHEL kernel.

No, they're not free of bugs, but they have undergone more thorough testing than does Ubuntu.

---

### Post by ardchoille422 on 2013-11-10
I have an idea. Canonical could do an anonymous poll and find out how many people actually file bug reports when they encounter a problem with an app. I'm betting that metric is much smaller than most people assume.

---

### Post by buzzingrobot on 2013-11-10
> **ardchoille422 said:**
> No, they're not free of bugs, but they have undergone more thorough testing than does Ubuntu.


You missed the point.

They reduce bugs by, first, trying to avoid the introduction of new code, and, second, patching bug and security issues *reported by users*.  These are the same users you think are being suckered to work for free.

---

### Post by buzzingrobot on 2013-11-10
I don't use contacts or an address book, so I had to go looking for it.  When I click "Contacts" on the panel dropdown, I'm shown Thunderbird's address book.  That's where I'd stop if I wanted to do contacts. Wouldn't surprise me if other folks stop there, too.

Obviously, a missing entry field is an error that should have been caught.  Equally obviously, bug reports will increase if they are generated and sent with little ot no user intervention. That will also result in flooding the system with duplicates and unecessary reports. Someone will need to spend time pruning them rather than fixing code.

The OP's remarks about app launching do not amount to a bug rpeort, but a complaint about a design he doesn't like.  In addition, he's confusing finding an application with launching an application.  The intended way to find an app in Gnome 2 was to move through the menu cascade.  The intended way to find an app in Unity is to tap the Windows key and search for it. Both designs have their good points and their bad points.  In both Gnome 2 and Unity, users are expected to pin the icons of frequently used applications to, in the former, a panel, or to the Launcher, in the latter.

---

### Post by ardchoille422 on 2013-11-10
> **buzzingrobot said:**
> I don't use contacts or an address book, so I had to go looking for it.  When I click "Contacts" on the panel dropdown, I'm shown Thunderbird's address book.  That's where I'd stop if I wanted to do contacts. Wouldn't surprise me if other folks stop there, too.

Good point. But, on the other side of the coin I didn't even know there was a Contacts menu item in the messages menu until someone mentioned it a few posts back.

---

### Post by lykwydchykyn on 2013-11-10
> **ardchoille422 said:**
> I have an idea. Canonical could do an anonymous poll and find out how many people actually file bug reports when they encounter a problem with an app. I'm betting that metric is much smaller than most people assume.

I'm sure it's quite small.  Probably in the hundreds at best.

Open source is kind of like public television.  Most viewers probably don't support public TV financially.  But the ones who don't have to accept that it is what it is.  You can't have it both ways.

Like you said, most people probably saw the bug and either ignored it or chose another app.  They aren't obligated to report a bug, but they can't expect better if they don't participate in the ecosystem.

---

### Post by ardchoille422 on 2013-11-11
I went ahead and reported the bug, it can be found here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-contacts/+bug/1249947](https://bugs.launchpad.net/ubuntu/+source/gnome-contacts/+bug/1249947)

I haven't reported a bug in years, I hope I did everything correctly.

---

### Post by cariboo on 2013-11-11
It may be something that isn't clear to the op, but I found a way to add home and work addresses to Contacts, with only a couple of clicks. Click the Edit menu in the upper right, then click New Details in the lower task bar. See the screenshot.

One thing I did find, on my system running Trusty, the app crashed when trying to remove a contact.

---

### Post by lykwydchykyn on 2013-11-11
> **cariboo907 said:**
> It may be something that isn't clear to the op, but I found a way to add home and work addresses to Contacts, with only a couple of clicks. Click the Edit menu in the upper right, then click New Details in the lower task bar. See the screenshot.

One thing I did find, on my system running Trusty, the app crashed when trying to remove a contact.

The basic problem is that you can't save these addresses until you've first same the contact.  The "new contact" for has part of the UI for addresses, but doesn't have the actual fields.  

I think the point is that there shouldn't need to be a workaround here, the new contact form should either contain address fields or not mention anything about address.

---

### Post by ardchoille422 on 2013-11-11
> **cariboo907 said:**
> It may be something that isn't clear to the op, but I found a way to add home and work addresses to Contacts, with only a couple of clicks. Click the Edit menu in the upper right, then click New Details in the lower task bar. See the screenshot.

One thing I did find, on my system running Trusty, the app crashed when trying to remove a contact.

Thank you for the work-around, it's very helpful.


> **lykwydchykyn said:**
> The basic problem is that you can't save these addresses until you've first same the contact.  The "new contact" for has part of the UI for addresses, but doesn't have the actual fields.  

I think the point is that there shouldn't need to be a workaround here, the new contact form should either contain address fields or not mention anything about address.

Agreed. And, at this point I'm wondering why this app exists at all in Ubuntu given that there is a better contacts-related app in Thunderbird. Thunderbird's contacts app ships with Ubuntu 13.10 and can be launched from the messages menu at the rop right corner of Unity.

I feel that the best way to resolve this particular bug is to remove this redundant, stand-alone contacts app from Ubuntu and use the Thunderbird contacts component.

---

### Post by alphacrucis2 on 2013-11-11
It seems that once a contact exists, it works correctly. At least that is what is happening on Fedora 20 I am running right now, so it could well be a different version to what you guys are running. Definitely a bug that has been around for a while I would say. I don't use it myself being a long time T'bird user - all my contacts are in there.

---

### Post by coffeecat on 2013-11-12
> **alphacrucis2 said:**
> It seems that once a contact exists, it works correctly. At least that is what is happening on Fedora 20 I am running right now, so it could well be a different version to what you guys are running.

I can confirm that happens in the version in Ubuntu 13.10 as well - it appears to be a gnome3 app which just happens to be used in Unity as well. It would be an upstream gnome3 bug. Also, if you delete all contacts, clicking on new presents you with a new contact window with the address fields in place. If you then open dconf-editor, org -> gnome -> Contacts -> untick did-initial-setup, then the contact window appears with the missing address fields again. Clearly a first-time use only bug, but a bug nonetheless.

> **alphacrucis2 said:**
> Definitely a bug that has been around for a while I would say. I don't use it myself being a long time T'bird user - all my contacts are in there.

If it's been around for a while and the combined millions of Fedora and Ubuntu users, and presumably users of other distros using gnome3, either haven't reported this bug, or the gnome people haven't responded to bug reports, it's very strange.

---

### Post by ardchoille422 on 2013-11-12
> **coffeecat said:**
> If it's been around for a while and the combined millions of Fedora and Ubuntu users, and presumably users of other distros using gnome3, either haven't reported this bug, or the gnome people haven't responded to bug reports, it's very strange.

When I filed the bug report the filing process asked me to complete a number of steps. I undertand why these steps are needed as it helps provide as much information as possible to get the bug report filed properly. However, I think many users simply aren't willing to spend the time required to perform all of those steps, it's much easier to just use another app. Half-way through the reporting process I started thinking the same thing.. "I'll just use another app". This is just a guess, but I'm thinking that for every bug report that is filed there were a number of users who saw the same bug but weren't willing to complete the process of filing the bug report.

I understand how the process works and it seems to be the best method for reporting bugs, it's just that some users may not be willing to complete the entire process. This is another reason that I feel developers should put more effort into testing their software prior to release and rely less on the end-user for filing bug reports.

---

### Post by ardchoille422 on 2013-11-12
I just had another idea. Perhaps Canonical should create a small group of people who are average users, not developers or power users. They could call this group the AUL, or Average User Liason group. This group would be average users and would be able to report directly to the core developer team with things such as:

* How I use Ubuntu
* What I normally do when I see a problem
* How I feel about different processes (bug reports, helping Ubuntu, etc.)
* Other items to be determined

I feel this would give Canonical a very useful set of metrics and perhaps some of that data would help improve Ubuntu overall.

---

### Post by ian-weisser on 2013-11-12
Canonical already does usability testing for much of that. Including new users and never-used-Ubuntu-before test subjects.
Big problem with such a group is that it's a self-selected sample - you cannot be sure that they map to the population.
The Canonical Design Team has a couple blog posts on how to run usability testing that gets useful, statistically valid, reproducible results...and welcomes LoCos and other non-Canonical entities to conduct and publish their own testing, too.

---

### Post by buzzingrobot on 2013-11-12
I'd bet most users make no connection between the popup reporting a bug and filing a bug report.  Given the number of explanations published about disabling the popup, most probably have no idea what filing bug reports is all about.

That said, the only way to increase testing prior to release is to increase resources, plus shift QA responsibility from the autonomous developers who create and maintain most Linux apps to the distributions that package them.   

Resources equals money and that's not going to increase. (Most distributions are all-volunteer. In any case, there's never been any money in desktop Linux.)  Those app developers are unlikely to turn over maintenance and QA responsibility. And that's without considering the quagmire of many multiple distributions patching, or not patching, the same bugs.

---

### Post by buzzingrobot on 2013-11-12
> **ian-weisser said:**
> Canonical already does usability testing for much of that. Including new users and never-used-Ubuntu-before test subjects.
Big problem with such a group is that it's a self-selected sample - you cannot be sure that they map to the population.


Very correct.  When I was being paid to worry about such things, I was able to dragoon employees of my choice to sit with developers. I had developers spend at least a day or two watching employees do their job with the existing software, and I had employees spend hours with developers testing software in-progress. By running a mix of employees through that drill, we tried to avoid the lack of objectivity generated by familiarity with both the software-in-development and the developers.  We got better software with fewer bugs.

---

### Post by ardchoille422 on 2013-11-12
Hmm.. it sounds like Canonical has already thought of everything that can be done. But, I'll keep brainstorming, maybe I'll come up with something useful someday.

---

### Post by cariboo on 2013-11-14
To add to what coffeecat said, gnome seems to be really slow when it comes to fixing bugs. I submitted a bug in the network utilities package about 4 years ago, and it took until just last year during the Raring testing cycle before a fix was released.

As for helping solve a problem, most of the testing and QA team members are pretty determined when it comes to tracking down a problem. The last major bug I reported during the Saucy cycle had me install 4 different kernels in order to track down the problem, and check to see if if the problem was solved when the kernel team came up with a solution. It took a little longer for the fix to be released then I expected, but it was close to the end of the development cycle, and a SRU had to be applied in order to get the fix in before Saucy was released.

I'm currently running Trusty as my day-to-day OS, and I'm looking forward to finding as many bugs as possible before release in April 2014.

---

### Post by ventrical on 2013-11-14
> **cariboo907 said:**
> 

I'm currently running Trusty as my day-to-day OS, and I'm looking forward to finding as many bugs as possible before release in April 2014.


As always, thanks for your persistence and dedication to Ubuntu. :)


Regards..

---

