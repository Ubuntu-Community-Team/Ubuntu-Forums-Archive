---
title: "Challenge/Declaration: June Is Documentation Month!"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by Stochastic on 2008-06-01
Okay, so recently Prismatic7 pointed out that the Community Documentation of UbuntuStudio [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio) is getting a little out of date in some spots (like manually entering the realtime permissions), and is completely absent in other spots (there's a link to music notation, but the page doesn't even exist - there ARE multiple notation programs in UbuntuStuio).

SO, to fix this, the whole community needs to chip in.  If the work load is spread evenly around then it will take no time at all to document the features of UbuntuStudio.  After all, this is the most popular multimedia-specific linux distribution EVER!!! (or at least according to distrowatch) In fact, when I put it in those terms, that community documentation truly seems sad and decrepit.  Thus,

\\:D/  \\:D/  **_I HEREBY DECLARE JUNE TO BE DOCUMENTATION MONTH FOR THE UBUNTU STUDIO COMMUNITY!!!!!_**  \\:D/  \\:D/

I, Stochastic, challenge every member of the community to step up and pitch in.  Edit that documentation to be a shining example of user-friendly help.  Even the newbiest of newbs can help by simply pointing out what they'd like to see, or even starting to write it themselves (it's a wiki, so others can correct any mistakes you make).

Here are some ideas to kick start you:
-take a look through what's there already, fill gaps and fix errors
-list some helpful hints on ladspa plugins (warbread, could you organize this listing to be user-friendly?)
-explain video...  ...anything! (the current video page is empty! :( )
-talk about firewire and ffado (it's in beta testing stages)
-explain workarounds for audacity/pulseaudio issues
-walk a beginner through a recording setup
-walk a beginner through a soft synth setup
-explain vst installation

Try to edit a page every three days (or more!!) for the month of June.  Beginners can do a page a week.  No actual commitment of time is enforceable, but set yourself a goal and try to help.

We can use this thread for discussion of more ideas, requests for pages, and other such general discussion.  I would suggest that we keep specific discussions on page-related topic to those page's respective "talk pages" but I couldn't seem to see any such pages (did I miss them?) so I guess that's kosher for this thread too, though that could get messy (we'll cross that bridge when we get there).

So I say unto you: Go forth and document!! :guitar:

---

### Post by prismatic7 on 2008-06-01
Well, I may have been a bit harsh and ranty, but dammit, that's a good idea, Stochastic! Have you announced it on the UbuntuStudio mailing list? (my email is out right now...)

---

### Post by Stochastic on 2008-06-01
I sent the announcement to the Ubuntu Studio mailing lists this morning, but I've yet to receive them.

---

### Post by prismatic7 on 2008-06-01
> **Stochastic said:**
> I sent the announcement to the Ubuntu Studio mailing lists this morning, but I've yet to receive them.

I think mailman disables distribution-to-sender by default. I saw the email this morning.

---

### Post by ronjouch on 2008-06-02
Hi,

I saw your announce on the mailinglist. Excellent idea IMHO, the lack of documentation was a real pain to get started with ubustu... I wish I had your idea :)

I think I can contribute on how to setup a functional firewire recording studio. Some ideas:
- hardware choices (I was very lucky to know a good music shop to make my initial choice)
- explanation of the JACK + BOB/ffado versus the familiar ASIO
- how to setup JACK
- routing possibilities of JACK
- some basics on ardour?
- ...

Any comment on this?

---

### Post by prismatic7 on 2008-06-02
> **ronjouch said:**
> Hi,

I saw your announce on the mailinglist. Excellent idea IMHO, the lack of documentation was a real pain to get started with ubustu... I wish I had your idea :)

I think I can contribute on how to setup a functional firewire recording studio. Some ideas:
- hardware choices (I was very lucky to know a good music shop to make my initial choice)
- explanation of the JACK + BOB/ffado versus the familiar ASIO
- how to setup JACK
- routing possibilities of JACK
- some basics on ardour?
- ...

Any comment on this?

Sounds good! I'm going to aim for better Wine/WineASIO documentation... as soon as I can get my soundcard working!

---

### Post by ronjouch on 2008-06-02
To gain visibility, could a moderator pin this topic ?

---

### Post by Stochastic on 2008-06-02
I noticed that the old ubuntu studio wiki (before the distro was built) has been migrated to here: [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) and many of those pages would do the UbuntuStudio documentation good.  How do you guys think it best to merge this?  Will links suffice?

---

### Post by prismatic7 on 2008-06-02
Given that they're part of [UserDocumentation](https://help.ubuntu.com/community/UserDocumentation), moving them might not be a good idea, but definitely a link on the main UbuntuStudio page. It's probably worthwhile to duplicate important or useful information anyway, so that there are multiple paths for users to find things that they need to solve a problem or improve something.

---

### Post by Stochastic on 2008-06-03
Bump.

Are we seriously the only three who think this is a good idea?  Where's the community spirit?

---

### Post by nalmeth on 2008-06-03
> **Stochastic said:**
> Bump.

Are we seriously the only three who think this is a good idea?  Where's the community spirit?
I can probably find time to contribute. Documentation (while not always fun to do) is ALWAYS beneficial, and sometimes the community just needs to be rallied into action.

<One more request to moderators - Please sticky this thread!>

---

### Post by ironflippy on 2008-06-03
I'll try to help, but my knowledge is fairly restricted. I'll look through and see if I can improve/add anything.

---

### Post by warbread on 2008-06-04
>  -list some helpful hints on ladspa plugins (warbread, could you organize this listing to be user-friendly?)

Funny you should ask - I had started this before you posted!

---

### Post by Stochastic on 2008-06-04
> **warbread said:**
> Funny you should ask - I had started this before you posted!

Really? you're editing up a documentation page on LADSPA plugins?  Post what you have so far, and I'll gladly help edit/add/organize.

---

### Post by warbread on 2008-06-05
For the past month or so, I've been trying out the plugins one by one, recording which ones crash, whether or not they're real time enabled and a short description of what they do.  It's mostly pretty straightforward. and I don't have a lot done due to other obligations, but I think it's a step in the right direction.  Unfortunately, one of those obligations has been battling carpal tunnel syndrome, so typing and using a mouse isn't so much fun lately.

I'll keep you posted on what I have when I have more, though.

---

### Post by ronjouch on 2008-06-07
Hi there,

My work kept me procrastinating this waaaay too long, but I finally got my hands there:
[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted) (some explanations about JACK and reorganization)
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) (a new section about Firewire with links to freebob and ffado)

to be continued

---

### Post by Stochastic on 2008-06-08
It'd be really nice if anyone with some video knowledge (no matter how basic) jumped in and added some app info on the video page.

---

### Post by prismatic7 on 2008-06-13
Hey guys - I've just added a HUGE chunk of USB device configuration info at [https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

Can someone check for clarity? It's not quite finished yet - I'm eating my own dogfood by testing it a few times!

---

### Post by ryanisablond on 2008-06-13
Dang! June is half over and I just found this thread. I'll help if I can.

An idea: I stayed up way too late last night because I found SFLogicNinja's amazing Logic 8 tutorials on youtube. Incredibly helpful to understand the workflow of the program and some of the basic principles of sound editing/mixing. 

Ardour "how-to" videos would be incredibly helpful, especially to show the workflow basics to ease the learning curve a bit.

Just throwing it out there.

---

### Post by Stochastic on 2008-07-02
Well the month has come to a close, and I personally think that the documentation has not grown to the level I was personally hoping it would, but in respect to the average monthly growth, it did change significantly.  I'd hope that those who partook in the documentation, would continue to do so, and possibly this event could repeat to gain more participation...

---

