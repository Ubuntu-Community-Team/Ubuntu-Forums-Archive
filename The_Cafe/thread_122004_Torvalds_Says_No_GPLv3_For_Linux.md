---
title: "Torvalds Says No GPLv3 For Linux"
date: 2006-01-26
forum: The Cafe
---

### Post by DoeRayMe on 2006-01-26
> One of the General Public License's biggest supporters will not be converted to version 3 out of objections over its position on digital rights management. Linus Torvalds, the creator of Linux is the first to take issue with the first revision of the GPL in a decade and a half.

"I don't think the GPL v3 conversion is going to happen for the kernel, since I personally don't want to convert any of my code," he wrote on the Linux Kernel mailing list Wednesday evening.
 
 At issue for Torvalds is the provision within GPLv3 that opposes digital rights management and would apparently open up parts of the kernel to copying. He says that GPLv2 currently prevents this, but GPLv3 would not.
"The Linux kernel is under the GPL version 2. Not anything else. Some individual files are licensable under v3, but not the kernel in general," he argued. "I think it's insane to require people to make their private signing keys available."

The first draft of the revision has been released to the public, and the Free Software Foundation is inviting comment from the software community at large. A second draft of the license is expected in the summer, with a final draft set for fall. The final version of GPLv3 will be released no later than spring of 2007.

Some issues to be undertaken by the new version of the license include protection from companies who attempt to sue GPL developers over patent issues, GPL software use on DRM-capable devices, and modifications to policies surrounding how GPL licensed software can be used on the Internet.

"The guiding principle for developing the GPL is to defend the freedom of all users," Free Software Foundation founder Richard Stallman has said.

Source: [www.betanews.com](www.betanews.com)

Your thoughts on this?

---

### Post by Lovechild on 2006-01-26
well getting everyone to sign over the license from v2 to v3 was a long shot at any rate - I still have hopes long term that they will start releasing new code under v3 though.

---

### Post by raublekick on 2006-01-26
Honestly, I'm kinda glad that Linus says what he says. I don't have the full understanding of all the new and revised stuff in v3, and maybe Linus doesn't either (although he probably does way more than I). But Linus is at least giving it thought, and has reasons for making that decision right now. 

From what I've seen of v3 so far, it looks all good, so barring any major bad things that I haven't heard about, I hope that eventually Linus changes his mind.

---

### Post by prizrak on 2006-01-26
Converting to v3 would destroy Linux. Right now there isn't much DRM'ed content, but the amount of it is increasing. If Linux will have no support for DRM (which the v3 requires) then you will never see said content on Linux and that would definetly keep people from switching. While I disagree with DRM in general, if Linux cannot support it and do what Windows and OS X can it will not be a viable alternative to most people.

---

### Post by tufkakf on 2006-01-26
[QUOTE=prizrak]Converting to v3 would destroy Linux. Right now there isn't much DRM'ed content, but the amount of it is increasing. If Linux will have no support for DRM (which the v3 requires) then you will never see said content on Linux and that would definetly keep people from switching. While I disagree with DRM in general, if Linux cannot support it and do what Windows and OS X can it will not be a viable alternative to most people.[/QUOTE]
Ehm, GPL3 (or rather its first draft) does not require that DRM can't be supported.
Where did you get that from?

---

### Post by nerval on 2006-01-27
[http://www.gnu.org/home.html](http://www.gnu.org/home.html)
As you can check from their web-site; you can sign a pledge to boycott DRM which is presented in their page. 
link : [http://www.pledgebank.com/boycottdrm](http://www.pledgebank.com/boycottdrm)

you can check gpl v3 from here : [http://gplv3.fsf.org/gpl3-current.txt](http://gplv3.fsf.org/gpl3-current.txt)

it's still the first draft, off course there will be lots of changes.

it seems like it's goin' well, they will receive more feedback. you can say what you think as well. actually even linus could have contributed if he wanted to.

to me, i have no idea how this will effect. but i've heard people at debian are strongly discussing about it. (actually you can check them from their developper mailing list and forums) 

Linux structure sure should be developped, that's why you have other options such as bsd. yet, like mark shuttleworth explained once to the debian team ( watch this one, it's really good : [http://video.google.com/videoplay?docid=-1165754797197197496&q=mark+shuttleworth](http://video.google.com/videoplay?docid=-1165754797197197496&q=mark+shuttleworth) ) even if the freedom is limited at one point for any structure, some successors will come thru. that's why programming languages goes from c to c++, and lately the amazing python (what perfection, hopefully they don't **** up on their 3rd version)

so, let's hope gpl v3 is perfect as possible :)

---

### Post by prizrak on 2006-01-27
[QUOTE=tufkakf]Ehm, GPL3 (or rather its first draft) does not require that DRM can't be supported.
Where did you get that from?[/QUOTE]
Stallman himself said he was completely against DRM, and if you read Linus's response he said he doesn't want to go to v3 because it requires DRM keys to be made public.

---

### Post by BWF89 on 2006-01-27
Just because the GPLv3 doens't allow parts of the GPL'd program to be used in DRM doesn't mean that any piece of software running on the GPL'd Linux OS has to be GPL'd too. Otherwise we wouldn't have Doom 3, Crossover Office, or Cedega.

How exactly do you convert a program with a restrictive licence like the GPLv2 to the GPLv3? I thought that under the terms of the GPL you agreed that you had to follow the rules of the GPL exactly, no more, and no less. Wouldn't that make it very difficult or even impossible to re-licence your code?

---

### Post by tufkakf on 2006-01-27
[QUOTE=prizrak]Stallman himself said he was completely against DRM, and if you read Linus's response he said he doesn't want to go to v3 because it requires DRM keys to be made public.[/QUOTE]
What BWF89 said. And Linus was criticized for being wrong about the private keys on the lkml, to put it mildly.

And converting to GPL3 is no problem if it is your code. After all you can license your code under any licence you see fit. However, as Lovechild mentioned, many people contributed to the kernel and they all would have to agree to the change if the licence for the whole kernel is to be changed.
(Of course, this is all in my understanding and IANAL)

---

### Post by prizrak on 2006-01-28
[QUOTE=BWF89]Just because the GPLv3 doens't allow parts of the GPL'd program to be used in DRM doesn't mean that any piece of software running on the GPL'd Linux OS has to be GPL'd too. Otherwise we wouldn't have Doom 3, Crossover Office, or Cedega.

How exactly do you convert a program with a restrictive licence like the GPLv2 to the GPLv3? I thought that under the terms of the GPL you agreed that you had to follow the rules of the GPL exactly, no more, and no less. Wouldn't that make it very difficult or even impossible to re-licence your code?[/QUOTE]
I don't know how relicensing works but people switched from v1 to v2 somehow so there is obviously some kind of mechanism in place. I suppose one way it would happen is that you license any new code as v3. I'm not sure how the licensing works though so don't hit me :) 

Oh and yeah I agree to the first part of your post I thought about it AFTER I posted :)

---

### Post by doclivingston on 2006-01-28
[QUOTE=BWF89]How exactly do you convert a program with a restrictive licence like the GPLv2 to the GPLv3? I thought that under the terms of the GPL you agreed that you had to follow the rules of the GPL exactly, no more, and no less. Wouldn't that make it very difficult or even impossible to re-licence your code?[/QUOTE]

The copyright holders of code (the person/people who wrote it. usually) can relicense it however they want - however it requires the agreement of *all* the copyright holders.

If you release some code under the GPL, and then want to relicence it to something else, you can. **As long as you haven't accepted code from any one else**, because if someone else has contributed, they are a copyright holder too.


Most things that are licenced under the GPL, say "GPL version 2 or later" - which means they can switch to GPL 3 at any time. Some things, including Linus' code says "GPL version 2" - which means that it can't be relicenced under GPL 3 without the approval of everyone who contributes code under "GPL version 2".

If one of the copyright holders refuses to give permission (or can't because they are deceased), then the only options are: a) don't relicence, or b) rip out everything they contributed (which may not be possible, depending on how much and what they did).

---

### Post by Jucato on 2006-01-28
copyright, copyleft, GPL, DRM, keys... my mind is going dizzy from all these... I don't know if others share my position, but Linus' statement, and people's responses, have made the atmosphere around Linux quite uncertain and scary. I mean, it's hard enough for some people to try out/transfer to Linux, but now that all these issues are going to bog down the average person. As a new Linux convert, this period is really quite frightening. How will I be certain that my new favorite OS will still be around after GPL v3 takes into effect? I mean, sure Linux itself will remain GPL v2, right? But it's only the kernel. How about X, GNOME, KDE, and all the rest? Will there be conflicts with these licenses? And what about hardware support? Just when we are getting better hardware support, things might begin to change. The business community is not really known for it's moral/ethical standards, but mostly listen on economic cues.

Whether Linus (or Stallman, for that matter) is right or wrong, this implied divergence of vision from the two could hurt Linux for a while. Just my own fears. Hope I could see some reassurance that I'm greatly and absolutely wrong... Just when I was starting to love and be at home with Linux... :(

---

### Post by BWF89 on 2006-01-28
[QUOTE=doclivingston]The copyright holders of code (the person/people who wrote it. usually) can relicense it however they want - however it requires the agreement of *all* the copyright holders.

If you release some code under the GPL, and then want to relicence it to something else, you can. **As long as you haven't accepted code from any one else**, because if someone else has contributed, they are a copyright holder too.


Most things that are licenced under the GPL, say "GPL version 2 or later" - which means they can switch to GPL 3 at any time. Some things, including Linus' code says "GPL version 2" - which means that it can't be relicenced under GPL 3 without the approval of everyone who contributes code under "GPL version 2".

If one of the copyright holders refuses to give permission (or can't because they are deceased), then the only options are: a) don't relicence, or b) rip out everything they contributed (which may not be possible, depending on how much and what they did).[/QUOTE]
Ok, I See now. I thought with the GPL once a program was licenced under it that was it. Nobody not even the owner was allowed to relicence it under a different licence.

---

### Post by doclivingston on 2006-01-28
[QUOTE=BWF89]Ok, I See now. I thought with the GPL once a program was licenced under it that was it. Nobody not even the owner was allowed to relicence it under a different licence.[/QUOTE]

If they've distributes code under the GPL, they can't take away that licence - but they can distribute it under another licence if they want.

e.g. Netscape Communicator was distributed under whatever the EULA said. Because Netscape was teh copyright holder of the code, they could distribute it under a different licence, the MPL, and so it became Mozilla.

---

### Post by prizrak on 2006-01-28
[QUOTE=Fenyx]copyright, copyleft, GPL, DRM, keys... my mind is going dizzy from all these... I don't know if others share my position, but Linus' statement, and people's responses, have made the atmosphere around Linux quite uncertain and scary. I mean, it's hard enough for some people to try out/transfer to Linux, but now that all these issues are going to bog down the average person. As a new Linux convert, this period is really quite frightening. How will I be certain that my new favorite OS will still be around after GPL v3 takes into effect? I mean, sure Linux itself will remain GPL v2, right? But it's only the kernel. How about X, GNOME, KDE, and all the rest? Will there be conflicts with these licenses? And what about hardware support? Just when we are getting better hardware support, things might begin to change. The business community is not really known for it's moral/ethical standards, but mostly listen on economic cues.

Whether Linus (or Stallman, for that matter) is right or wrong, this implied divergence of vision from the two could hurt Linux for a while. Just my own fears. Hope I could see some reassurance that I'm greatly and absolutely wrong... Just when I was starting to love and be at home with Linux... :([/QUOTE]
Your fears are unfounded Stallman and Torvalds have been disagreeing since the beginning of time. The way the software is licensed generally makes little difference as far as end users go. The kernel can be v2 while everything that runs on top of it can be v3 or even some other license. The above licensing issues really only make a difference to programmers who are planning to contribute/release things under any of those licenses. For instance you probably have RealPlayer on your Ubuntu box, Real is proprietary software released under a different license from the rest of Ubuntu but it makes little difference to you ;)

---

### Post by doclivingston on 2006-01-28
As prizrak said, exactly what open-source licence gets used doesn't usually make a lot of difference to end-users - they normally only affect contributors and distributors.

The biggest way it affects end-users is if distributors can't ship certain things together, e.g. the Fluendo mp3 plugin and GPL'd things using it. That is a separate issue, as the version of the GPL used won't really affect it.

---

### Post by Jucato on 2006-01-28
Like I said, I'm not much knowledgeable about all these licensing and legal matters. I was just speaking how the situation looks like from a new end-user of Linux. I was hoping, and glad that my fears are unfounded. 

Just let me verify, that what you're saying is that, even if Linux stays GPL v2 and all the rest will have to go to GPL v3, end-users will be not be affected? That I will still be able to use some of my favorite programs (OpenOffice, GIMP, Blender) even if they change to GPL v3? That hardware manufacturers (for example, NVIDIA) will continue to support Linux come what may?

I'm sorry I asked too much. It's just that there's so much discussions on this issue around the web that Linux's future seems misty, for a new user that is (who is also quite unfamiliar w/ the Torvalds vs. Stallman bouts). It's like finally deciding to leave the shore (windows) to take a dive into the cool waters (Linux), only to find it unstable. But I still love Linux for what it has given me in these past weeks that I've started using it.

---

### Post by prizrak on 2006-01-29
> Just let me verify, that what you're saying is that, even if Linux stays GPL v2 and all the rest will have to go to GPL v3, end-users will be not be affected? That I will still be able to use some of my favorite programs (OpenOffice, GIMP, Blender) even if they change to GPL v3? That hardware manufacturers (for example, NVIDIA) will continue to support Linux come what may?
You are correct.

---

### Post by Jucato on 2006-01-29
thank goodness! thanks prizrac! I'll take your word for it and continue on my merry way... :D [/end_of_posts]

---

