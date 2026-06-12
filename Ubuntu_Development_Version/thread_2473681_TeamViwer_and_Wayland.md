---
title: "TeamViwer and Wayland"
date: 2022-04-10
forum: Ubuntu Development Version
---

### Post by hairymoot on 2022-04-10
When I loaded the Beta of Jammy Jellyfish, Teamviewer stopped working because of Wayland. I did some research on their message board and they suggested logging out and clicking on your name and selecting the bottom right to login on XOrg.

But they also mentioned Jammy Jellyfish and that they are working to get Wayland to work with it. Yeah!

[TeamViewer Wayland news for Ubuntu 22.04]("https://community.teamviewer.com/English/discussion/122410/teamviewer-support-on-wayland-experimental-state-%F0%9F%A7%AA")

---

### Post by QIII on 2022-04-10
Another instance, one of many, indicating that Wayland is not really ready for the role.  That is in part due to the initial snotty attitude of the developers as they took it on themselves to decide what it is that a user should and should not do on their own machines.  That is why developers, like those of TeamView, are having to move mountains to make things work.  A better attitude from the Wayland developers would have gone a long way towards making this all more seamless.

The Wayland developers did finally dispense with their intransigence, but now they are behind the eight ball and trying to catch up, even as Wayland has been forced into the starring role -- and developers of other packages are trying to serve their target audiences.

The X ecosystem needed to go.  It was a kludge and very old.  Wayland would have been nice if, from the start, the developers had understood that their job was to provide the what user needs rather than dictating the rules.  That was a Microsoft-ish move.

End of rant.

Fairness disclosure:  I've been using Wayland for some time with Fedora and have had little trouble.

---

### Post by mIk3_08 on 2022-04-10
> **hairymoot said:**
> When I loaded the Beta of Jammy Jellyfish, Teamviewer stopped working because of Wayland. I did some research on their message board and they suggested logging out and clicking on your name and selecting the bottom right to login on XOrg.
But they also mentioned Jammy Jellyfish and that they are working to get Wayland to work with it. Yeah!
[TeamViewer Wayland news for Ubuntu 22.04]("https://community.teamviewer.com/English/discussion/122410/teamviewer-support-on-wayland-experimental-state-%F0%9F%A7%AA")

For me, I don't prefer to use Teamviewer as Teamviewer lately is very buggy. That's why I don't use Teamviewer anymore. I prefer to use Anydesk. Anydesk works smoothly to my Linux Ubuntu Desktop since 3 years ago and until this time without any hassle. Good Luck and Regards.

---

### Post by Paddy Landau on 2022-04-11
Thanks for letting us know.

Usually, companies only support LTS, so it's a bit worrying that 22.04 isn't yet supported; there are just 10 days before its release!

I'd better not upgrade until TeamViewer is working.
> **mIk3_08 said:**
> For me, … Teamviewer lately is very buggy.
Hmm, I haven't had this problem at all, but I don't use it extensively. What have you found to be the problem?

---

### Post by TheFu on 2022-04-11
Some of the programs I use won't be supported on 22.04 for a year or more as the underlying software packages are slowly updated to provide full system support.  I get the feeling the project team doesn't even look at the latest LTS until after the first .1 release for those enterprise packages.

A few of my workflows are completely dependent on security holes in X11 to work. These holes have been there 30 yrs and are well understood at this point.  The Wayland devs have assumed that users don't use remote X11 and X11 forwarding through ssh in sufficient numbers to have been a priority for their efforts, I'm guessing.  While I love the Gstreamer can handle Wayland for screen capture, there are so many issues with Gstreamer outside of that specific use that make it unacceptable.  OTOH, there are 15 other X11-based tools which work fine ... but not with Wayland.

Just because something is old, that doesn't mean it is flawed.  After all, we still use ls, du, df, mv, cat, grep ... and those are very old. That doesn't mean they cannot be improved.  When sort added the -h option, I nearly cried with joy.  In the last 15 yrs, lots of GNU tools added the -h option (human readable) which has completely changed how I work. Good things.

I have to wonder if the Wayland folks didn't consider making a local-system subprogram that could be used with X11 when the X/server and X/client were running on the same hardware, then all the remote stuff could still exist and work flawlessly as complex network agnostic sub-functions were replaced, overtime.  OTOH, being a F/LOSS developer in any long-used project has got to be tough with all the 'helpful' experts making uninformed comments.  I think I'm in that group.  I was an X/Windows programmer in the mid-1990s and wrote a number of X11 programs at the time, but the world has changed and X has changed since then.

I'm fully confident that the Wayland guys will get a stable, production-ready, version in the next 5 yrs.  Right now, I'm blaming the distros for forcing Wayland before it is ready to be used.  Canonical has a history of pushing new projects before they are ready just to see how bad it is. In 2017, they first tried to make Wayland the default. That ended badly.  Canonical has a N-I-H syndrome with many of their forced changes - I can't call some of them upgrades. They are downgrades.

As for teamviewer or any remote access tool that requires a third party to be involved.  Security people don't like RATs (remote access/administration tools) because the are almost always security failures and require trusting some 3rd party, who often isn't under any financial contract.  There's a difference between free and free with strings.  On Linux, we an have secure remote access without any 3rd party being involved to provide authentication. The tools are actually really good and reuse ssh for the authentication and security.  Alas, some of those GUI tools don't work with Wayland and likely will never support it. ;)

---

### Post by Paddy Landau on 2022-04-12
> **TheFu said:**
> A few of my workflows are completely dependent on security holes in X11 to work.
Youch! That feels quite bizarre!
> **TheFu said:**
> Security people don't like RATs…
I can understand this, but they are needed. For example, I support my father (he's on Windows), but he lives a few thousand kilometres from me — it's not practical for me to pop in whenever he has a problem!

The rest of your comments are interesting. I'm not a developer, so I tend to be unaware of all those background issues.

I have known that Wayland is controversial, but none of the details of the controversy. I visited [Wayland's website]("https://wayland.freedesktop.org/"), and the very first line reads, "Wayland is intended as a simpler replacement for X, easier to develop and maintain. GNOME and KDE are expected to be ported to it."

Isn't it a bit soon to release Wayland on Ubuntu 22.04 if Gnome and KDE are merely "expected to be ported to it", and not already ported?

---

### Post by mIk3_08 on 2022-04-12
> **Paddy Landau said:**
> Thanks for letting us know.
Usually, companies only support LTS, so it's a bit worrying that 22.04 isn't yet supported; there are just 10 days before its release!
I'd better not upgrade until TeamViewer is working.
Hmm, I haven't had this problem at all, but I don't use it extensively. What have you found to be the problem?

Before I usually use Teamviewer But since I encountered immediate exit/closing during my operation even its already updated and newly installed the problem still exist that's why I shift directly to anydesk without any hesitation. 
Since then I haven't use Teamviewer anymore. Maybe teamviewer is Okay now. Regards and Cheers.

---

### Post by TheFu on 2022-04-12
> **Paddy Landau said:**
> Youch! That feels quite bizarre!

I can understand this, but they are needed. For example, I support my father (he's on Windows), but he lives a few thousand kilometres from me — it's not practical for me to pop in whenever he has a problem!

The rest of your comments are interesting. I'm not a developer, so I tend to be unaware of all those background issues.

I have known that Wayland is controversial, but none of the details of the controversy. I visited [Wayland's website]("https://wayland.freedesktop.org/"), and the very first line reads, "Wayland is intended as a simpler replacement for X, easier to develop and maintain. GNOME and KDE are expected to be ported to it."

Isn't it a bit soon to release Wayland on Ubuntu 22.04 if Gnome and KDE are merely "expected to be ported to it", and not already ported?

I supported by Mother for years. She lived 7 hrs away by car.  I visited after her computer was hacked. She was running a version of Windows.  I'd been moving her off MSFT programs to F/LOSS versions for years. She was really frightened about Linux, because she'd seen my no-desktop setup.  I told her that her setup would be completely different and that the same programs she was using before would be there - Firefox, Thunderbird, a simple word processor, and a few games for the grandkids.  I brought an old router of mine which was stepup for her to allow remote ssh from my home into the Linux install.  99% of the time, I'd use ssh. I did weekly patching and backups of her stuff remotely.  It was just 1 more system in my weekly patch script, so not any big deal to me.  Once a year, I'd visit, which is when OS upgrades happened.  

It worked fairly well, until her computer died.  Another relative replaced the Pentium4 with a Core i7 - they looked exactly the same on the outside. Mom couldn't tell the difference after I swapped the HDD.

When I needed a remote GUI, I used FreeNX. Like x2go, all NX protocol tools, it uses ssh tunnels so ssh is both the encrypted channel AND the authentication method. When she got a new printer, I used freenx to remote in and use a GUI to set it up.  FreeNX was not extremely stable, but I hadn't heard of x2go back then. A few years later, I had and x2go was used until she died after a long, happy, life.

Software programs are never 'done'.  There's always more features or bugs to be addressed, especially for complex software.  Wayland is nearly as complex as X/Windows, so there will be missing features for decades and bugs. There will be tens of thousands of bugs.  X/Windows has bugs today and it has been under development since the mid-1980s.  

I've worked on software that was both highly complex and was believed to be bug free at some point.  It was also extremely expensive to develop due to all the extra steps in the process to attempt to make it bug free.  We measured almost everything - time, lines of code, function points, number of reviewers, if any issues were uncovered, where those issues were found and how many were determined to be a bug of some sort.  There were 7 levels of testing - 5 levels performed by different companies.  I was on the development and L1-L2 testing team.  The year I chose to leave the project (1994), we had 15 full-time developers all creating code and our team bug rate was 0.5 bugs per year for initial quality. That's 1 bug found outside our team every other year.  Anyway, we, our client, and their client all believed the code was finally bug free.  Jump forward to 2011 as the entire program was being closed, one of the program leaders (program means hardware, software, people, locations, vehicles, ...) who also tracked every bug in the software from the very first code created in the 1970s created a report about the quality of the software over time, using statistics.  After 1994, over 100 bugs were found that were already in the code at that point.  So the stance that it was bug free just wasn't true.  The program had 2 critical failures over the history that killed people, but software was not the cause of either of those.  There were software errors that did impact a few missions and broke the mission timeline. That impacted a few thousand people on the ground.  I was assigned to fix one of those issues. There was an error accumulator variable that wasn't reset after each calculation run and it was only single-precision.  The fix was to reset the value to 0 after an answer was provided AND to change the error accumulator from single to double precision.  I didn't cause the error and it hadn't been seen in any prior missions, but prior missions had only performed a few similar calculations. It was guidance code.  Guidance required iterating to a solution. During the calculations, either the error is getting smaller and smaller. That's called convergence. OR larger and larger.  Guidance solutions need to converge to be useful and the fewer cycles needed to get to an answer that is 'close enough', the better.

Anyway, Wayland will have bugs for the entire life of the project and it will have missing features. The trick for the team is to provide the features that most people use before they are needed.  That usually means making the stuff that grandma needs ready first and letting features that only 10% of users need have a lower priority.  Of course, the programming team people are usually advanced users too, but if they don't work the same way that other advanced users do, those needed features will always be bumped for some other needs.

That's the way of life.

---

### Post by Paddy Landau on 2022-04-12
> **TheFu said:**
> She was really frightened about Linux &#8230; Another relative replaced the Pentium4 with a Core i7 - they looked exactly the same on the outside. Mom couldn't tell the difference after I swapped the HDD.
That's one of the many beauties of Linux. I also swapped to Linux after having replaced MS apps with FOSS equivalents. I found them easier than MS's versions after MS converted to the "ribbon".
> **TheFu said:**
> &#8230; I used FreeNX. A few years later &#8230; x2go was used
I hadn't heard of either of those. I've searched a lot for FOSS, or at least free-of-charge, equivalents of TeamViewer and the like. There's Chrome's Remote Desktop, but I struggled with it. TeamViewer is free for personal use, but every so often it flags me as being a commercial user (I'm not), and I have to contact TeamViewer to ask them to remove the flag.
> **TheFu said:**
> Software programs are never 'done'.
100% true!
> **TheFu said:**
> I've worked on software &#8230; our team bug rate was 0.5 bugs per year for initial quality.
That's an extraordinary achievement!

---

### Post by TheFu on 2022-04-12
> **Paddy Landau said:**
>  That's an extraordinary achievement!

The achievement wasn't about any individuals.

It was all about the development process, the commitment to follow it, to ask questions when something wasn't fully understood, and the commitment by everyone involved to seek bug-free results. Even the client wanted that goal over everything else. There weren't any superstar programmers and we were all paid govt money (not much).

The trick to using x2go is to get ssh working first.  Key-based ssh authentication is needed (not required) for security. I've not heard of anyone successfully gaining access through ssh when keys were required. Never.

---

### Post by mIk3_08 on 2022-04-13
> **TheFu said:**
> The achievement wasn't about any individuals.
It was all about the development process, the commitment to follow it, to ask questions when something wasn't fully understood, and the commitment by everyone involved to seek bug-free results. Even the client wanted that goal over everything else. There weren't any superstar programmers and we were all paid govt money (not much).
The trick to using x2go is to get ssh working first.  Key-based ssh authentication is needed (not required) for security. I've not heard of anyone successfully gaining access through ssh when keys were required. Never.
I always believe in you TheFu your expertise when it comes to computing is extremely broad. That's why I love to follow you and read more about your replies because I know I will learn a lot from you by just reading some of your post/reply here in ubuntuforums. Thanks with you TheFu. yeah, not only you but others too. I get some ideas here by reading and matches the connections of problem in terms of computing. yeah I'm still noob but I keep reading some of the replies here in this ubuntuforums and it give me so many ideas on it by reading and following some of the threads here. Just wanna thank you guys. Hope you won't change for being very active here. Stay cool always. Regards and cheers.

---

### Post by TheFu on 2022-04-13
Anydesk?   [https://www.theregister.com/2022/04/14/ransomware_gang_network/](https://www.theregister.com/2022/04/14/ransomware_gang_network/)
Preinstalling any RAT is helping the bad guys.
> The ransomware gang left behind a record of various legit remote-access tools they installed on commandeered servers and desktops. At first, the miscreants showed a preference for ScreenConnect IT management suite, but then **they switched to AnyDesk**, which Brandt and Gunn noted was likely an attempt to evade countermeasures on the network.

The security researchers also **found RDP scanning, exploit, and brute-force password tools**, along with logs recording their successful uses. The gang appeared to want to set up multiple paths into the agency's machines to ensure the crew could connect back in if one or more access routes were closed.
Friends don't let friends us RDP without ssh tunnels either.  So ... if you have to use ssh (and you should!!!!), then there is little to gain by using other tools besides ssh and x2go (or some other NX-based GUI tool, though I'm not thrilled with the commercial license versions).

---

### Post by Paddy Landau on 2022-04-14
> **TheFu said:**
> Anydesk? …
Reading the article, it seems that the IT people made a few fundamental mistakes after having discovered the problem, including some really easy ones:

[LIST]
[*]They didn't use 2FA
[*]They didn't restrict access to authenticated accounts
[*]"In one case, they left a protective feature disabled after finishing maintenance work."
[*]"… 'the IT department didn't heed the warning' from the Sophos suite."
[*]"… the IT team had disabled their Sophos Tamper Protection during their rebuild of the network."
[/LIST]
In summary:
> "In the course of the investigation,' the Sophos duo worte, "one factor seemed to stand out: the target’s IT team made a series of strategic choices that enabled the attackers to move freely and to access internal resources without impediment.
So, AnyDesk wasn't the point of entry, nor is it clear that it had even been preinstalled: "It's not said exactly how the miscreants got in – via brute-forcing a weak password, using a stolen credential, tapping up a rogue insider, or exploiting a security bug, for example." Also, "The ransomware gang left behind a record of various legit remote-access tools they installed on commandeered servers and desktops. At first, the miscreants showed a preference for ScreenConnect IT management suite, but then they switched to AnyDesk." In other words, it appears that the gang themselves installed AnyDesk.

Still, you raise an important point.

---

### Post by mIk3_08 on 2022-04-14
> **TheFu said:**
> Anydesk?   [https://www.theregister.com/2022/04/14/ransomware_gang_network/](https://www.theregister.com/2022/04/14/ransomware_gang_network/)
Preinstalling any RAT is helping the bad guys.
Friends don't let friends us RDP without ssh tunnels either.  So ... if  you have to use ssh (and you should!!!!), then there is little to gain  by using other tools besides ssh and x2go (or some other NX-based GUI  tool, though I'm not thrilled with the commercial license  versions).

> **Paddy Landau said:**
> Reading the article, it seems that the IT  people made a few fundamental mistakes after having discovered the  problem, including some really easy ones:

[LIST]
[*]They didn't use 2FA 
[*]They didn't restrict access to authenticated accounts 
[*]"In one case, they left a protective feature disabled after finishing maintenance work." 
[*]"&#8230; 'the IT department didn't heed the warning' from the Sophos suite." 
[*]"&#8230; the IT team had disabled their Sophos Tamper Protection during their rebuild of the network." 
[/LIST]
In summary:

So, AnyDesk wasn't the point of entry, nor is it clear that it had even  been preinstalled: "It's not said exactly how the miscreants got in &#8211;  via brute-forcing a weak password, using a stolen credential, tapping up  a rogue insider, or exploiting a security bug, for example." Also, "The  ransomware gang left behind a record of various legit remote-access  tools they installed on commandeered servers and desktops. At first, the  miscreants showed a preference for ScreenConnect IT management suite,  but then they switched to AnyDesk." In other words, it appears that the  gang themselves installed AnyDesk.

Still, you raise an important point.
So, do you guys don't recommend this anydesk? it just so happen that I really need to use a substitute for this Teamviewer application for emergency reasons. That time was emergency that I need to use any alternative from Teamviewer as Teamviewer is not working well and it takes a lot of time to do research and ask for help when you knew that you only have few time left for the operation to be delivered and presented. The operation is only for the ssh and it can't be viewed by the client. I am the one who viewed the clients desktop But im not showing mine. The client has a presentation but the work is mine. The key is only from me nothing else. In terms of hiding, I know how to hide things when working via ssh.  And that time my operation was successful because I used any alternatives application. And I only use that once. Thanks Guys for the advice. I really love to work voluntarily to you guys.  Cheers.

---

### Post by Paddy Landau on 2022-04-14
> **hairymoot said:**
> Teamviewer stopped working because of Wayland.
I've just tried out the latest build of 22.04, and TeamViewer gives a conspicuous warning as shown in [your link]("https://community.teamviewer.com/English/discussion/122410/teamviewer-support-on-wayland-experimental-state-%F0%9F%A7%AA").

So, still not working fully for Wayland.

From what I can tell, on Wayland, TeamViewer fully works when acting as a supporter (outgoing link), but only partially when acting as a client (incoming link). In that case, XOrg could be used, perhaps on a second user to prevent "contamination" between the two environments for a specific user.

---

### Post by Paddy Landau on 2022-04-14
> **mIk3_08 said:**
> do you guys don't recommend this anydesk?
I don't think that you'll have a problem with AnyDesk, as long as you take the usual precautions.

---

### Post by TheFu on 2022-04-14
> **Paddy Landau said:**
> I don't think that you'll have a problem with AnyDesk, as long as you take the usual precautions.

I have a different opinion, but that's because all the RATs seem to have similar AND different security failures.  Some are in the code, some are in the 3rd party providing access and some are due to people making poor decisions when under pressure.  Happens all the time.

It is best to avoid all of this by using well-understood tools and can be secured without having to trust some un-paid, non-contract, 3rd party.

YMMV. IMHO.

---

### Post by Paddy Landau on 2022-04-14
> **TheFu said:**
> It is best to avoid all of this by using well-understood tools and can be secured without having to trust some un-paid, non-contract, 3rd party.
I hear you, but not all of us have the technical skill to be able to do this. That's why some people (including me) have to rely on third parties.

---

### Post by TheFu on 2022-04-14
If you can setup encrypted storage manually, then setting up ssh access is trivial in comparison.

---

### Post by Paddy Landau on 2022-04-14
> **TheFu said:**
> If you can setup encrypted storage manually, then setting up ssh access is trivial in comparison.
SSH is a different skill set from encrypted storage.

In my case, I use Ubuntu, and my father, who lives in a different continent, uses Windows.

To help him with problems, I currently use TeamViewer to connect to his computer and fix whatever has gone wrong.

But I wouldn't know even where to start with setting up SSH to his Windows computer and then having remote access to his screen. That is totally beyond me.

Encrypting a disk is way easier: it's just a couple of LUKS commands away — or I can use Gnome Disks!

---

### Post by mIk3_08 on 2022-04-16
> **Paddy Landau said:**
> I don't think that you'll have a problem with AnyDesk, as long as you take the usual precautions.
Thank you very much for the advice Paddy Landau. Regards and cheers. God Bless us all.

---

### Post by mIk3_08 on 2022-04-16
> **TheFu said:**
> If you can setup encrypted storage manually, then setting up ssh access is trivial in comparison.  Yes. well said The Fu. And it is very secure when using this ssh. The one of the most powerful tool I've ever known in computing in terms of internet data communication. The security is thicker than I've ever imagine and it is more stronger now and more hardened as its getting longer.  Thanks for the Linux Dev Community. Glad Being here then. God Bless us all always.

---

### Post by jbicha on 2022-04-18
There have been a couple Wayland fixes recently. Could you install all updates, restart your computer, and see if TeamViewer works like you expect?

---

### Post by Paddy Landau on 2022-04-18
> **jbicha said:**
> There have been a couple Wayland fixes recently. Could you install all updates, restart your computer, and see if TeamViewer works like you expect?
I updated and restarted the 22.04 computer as you asked.

Using Ubuntu 20.04 as the local computer (the one providing support) and 22.04 as the remote computer (the one being supported):

[LIST]
[*]The incoming connection on XOrg works properly.
[*]Unfortunately, the incoming connection on Wayland doesn't. The connection is established easily, but, on the support side (the outgoing connection), the screen is completely black, and no mouse movements or keypresses are recognised on the target machine.
[/LIST]
The other way around, with Ubuntu 22.04 as the local computer (the one providing support) and 20.04 as the remote computer (the one being supported), works correctly on Wayland.

---

### Post by jbicha on 2022-04-18
It works for me. Please read the [documentation]("https://community.teamviewer.com/English/discussion/122410/teamviewer-support-on-wayland-experimental-state-%F0%9F%A7%AA/") if you haven't already.

You'll need to use TeamViewer 15.29 or higher. I had to switch ```
/etc/apt/sources.list.d/teamviewer.list
``` to the preview channel instead of stable to get a high enough version today.

When you try to connect, you should see a prompt from xdg-desktop-portal. You'll need to click Share on that popup and it's up to you whether you want to turn on remote interaction or not.

Your xdg-desktop-portal version should be at least 1.14.3 since earlier versions would crash too frequently.

---

### Post by Paddy Landau on 2022-04-18
> **jbicha said:**
> You'll need to use TeamViewer 15.29 or higher…
That did the job, thank you!

I see that a few specific items (e.g. show remote cursor) aren't working yet, but according to the link that you gave, it should be here soon.
> **jbicha said:**
> Your xdg-desktop-portal version should be at least 1.14.3 since earlier versions would crash too frequently.
I love the wording, "too frequently" :D

---

