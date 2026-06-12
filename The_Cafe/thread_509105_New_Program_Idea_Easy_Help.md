---
title: "New Program Idea: Easy Help"
date: 2007-07-25
forum: The Cafe
---

### Post by samurailink3 on 2007-07-25
Well.. I wasn't quite sure where to put this, so I decided to throw it here.

Basic Idea:
What if in the notification area, there was an automagical question mark. You click it and a small, very simple menu comes up. 
[IMG]http://img.photobucket.com/albums/v678/SamuraiLink3/DropDown.jpg[/IMG]
Three choices:

Connect to Live Help:
This will connect the user to the #ubuntu IRC room. No config needed, just jumps into the room. Maybe a small dialog box asking for the user to specify a name to be used in the chat room. I doubt they want to be referred to as Guest29102896. Connect and go. I want it to be a seamless and transparent as possible. My goal for the applet is to make it easy for anyone to get help as soon as possible. Even the grandma's out there :shock:. 
[IMG]http://img.photobucket.com/albums/v678/SamuraiLink3/LiveHelp.jpg[/IMG]

Post a Question:
It posts to the forums in the help section, but its totally transparent.
All the user see's is an automagical savior window. To forum users, they see the first sentence as the subject. They reply to it, and it works kind of like a delayed chat. When a reply is found by the applet (keep track via rss?), it lights up. When the user then clicks on it, the reply pops up. Then they can reply to that. A transparent interface to the forums.
[IMG]http://img.photobucket.com/albums/v678/SamuraiLink3/PostaQuestion.jpg[/IMG]

Why?? : 
To some linux users, forums, IRC, google searches on every possible tech subject just come natural. To others, they either don't know about these kinds of support, or they don't want to take the time to search them out, sign up, or go through any effort to use them. The purpose of this app is to bring helpful resources to the users on a silver platter. Well... not really silver... kind of grey really... but its.. well.. a window. Not really a platter. But you get the point ;)

Obviously it would need to be licensed under the GPL, and I would want somewhere buried in the credits "Original idea by Tom Webster" or something like that.

I would code this myself, but I haven't yet started school for that, and I don't know how. I figured, what better way to get this idea to other people that do know how to code, than to post it on the Ubuntu forums.

I mocked up all the images using the gimp.

Any feedback, code, projects started would be very helpful. Thanks!  :)

---

### Post by 23meg on 2007-07-25
You may want to post this to the [Idea Pool]("http://ubuntuforums.org/forumdisplay.php?f=253").

---

### Post by DoctorMO on 2007-07-25
Good idea, create a launchpad project to do the project and invite others.

---

### Post by samurailink3 on 2007-07-25
Posted to the Gusty idea pool. And a launchpad group has been created.
[https://launchpad.net/easy-help](https://launchpad.net/easy-help)

Thanks for the idea! I've got pretty much nothing done except for the screenies and the launchpad group.

---

### Post by Bou on 2007-07-25
Something very similar to this was proposed during the dapper development cycle. Guy even had a working version of it, I really don't know why it wasn't implemented.

Check it out here: [http://joelbryanonsoftware.blogspot.com/2006/05/2-ubuntu-live-chat-support.html](http://joelbryanonsoftware.blogspot.com/2006/05/2-ubuntu-live-chat-support.html)

---

### Post by Kent84 on 2007-07-25
great idea!

---

### Post by amadeus266 on 2007-07-25
Try submitting this idea again. I would have used it for sure. In fact I would probably still use it from time to time as I am not fully versed in Linux yet.

---

### Post by Depressed Man on 2007-07-25
I like this idea. Even though I'm use to using google and asking for help on these forums already. And I'd be happy to help too with what knowledge I have.

---

### Post by bread eyes on 2007-07-25
It would be pretty simple to make and might be useful.

---

### Post by Tomosaur on 2007-07-25
Great idea, nice work :D

Although I'm not sure whether the #ubuntu IRC channel is such a great place to get help - it can be very busy at times, and isolating a single conversation can be incredibly tricky unless you go to PMs, which many do not like, especially when new users do it accidentally or without cause - I'm thinking we'd need dedicated teams to provide the support. Even this in itself could, I assume, be possible. You could make a 'support provider' client available, which would log in to a master server and thus the master server would pick randomly from a pool, connect the support provider and the support requestor, and so on. The obvious downside to this is finding people willing to be support providers - Canonical make money from providing support, and you'd essentially rely on people being generous enough with their time to download the support provider client and make themselves available while using their machines. That, and there's no guarantee about the quality of the support using this method.

Perhaps the 'support provider' client would feature a 'walk through' problem solver. Provider asks what the problem is, inputs the subject into the software, then responds with the solution. The Ubuntu wiki could be utilised for such a purpose.

---

### Post by mostwanted on 2007-07-25
I must say I really like your mock-up. I think some qualified developer should seriously consider starting a project like that for inclusion in Gutsy +1.

---

### Post by samurailink3 on 2007-07-25
Thanks for all the suggestions. I do agree with Tomosaur on his ideas. IRC may not be the way to go with live help, it is quite crowded in there. I like the idea of random people lending their time, although I know most aren't on their computer as much as I am. A walk through problem solver via the wiki. Great idea! That will also give a hand in helping people help themselves with the tools given to them. Bou is right though, a project like this has been started (first I've heard of it), it looks to be a bit more complex, but its focus is help through IRC. [https://wiki.ubuntu.com/UbuntuLiveChatSupport]("https://wiki.ubuntu.com/UbuntuLiveChatSupport") Maybe the focus of this project should be to create a gui interface to the forums and wiki, as IRC is being addressed already.

---

### Post by jimcooncat on 2007-07-27
A couple of suggestions :

Make it obvious that the user is going to be communicating with humans. Though I've found #ubuntu and ubuntuforums to be well-moderated, the occasional a** slips in to make a rude comment. I wouldn't want grandma thinking I set up her computer to spit out automatic rude comments to her. A one-time welcome screen would suffice -- perhaps in conjunction with the nickname dialog.

Especially if you go with a dedicated channel, have a quick link "provide help to others" to launch the channel in a favorite IRC program (or forum reply, wiki editing).

---

### Post by DoctorMO on 2007-07-27
It would be nice if canonical could set up a support IRC server and have volenteers keys used for authentication so that we can tell the difference between guests and proven helpers. We already have a wiki dedicated to helping people, but maybe we ort to have a few pages dedicated to helping the helpers find answers or details to questions they've been asked?

---

### Post by graabein on 2007-07-27
Not a bad idea but maybe use something like **#ubuntu-help** instead of the regular **#ubuntu** so not to flood the room with total newbies?


> 
Main Entry: **au·to·mat·ic**
Pronunciation: "o-t&-'ma-tik
Function: adjective
Etymology: Greek automatos self-acting, from aut- + -matos (akin to Latin ment-, mens mind) -- more at MIND
1 a : largely or wholly involuntary; especially : REFLEX 5 <automatic blinking of the eyelids> b : acting or done spontaneously or unconsciously c : done or produced as if by machine : MECHANICAL <the answers were automatic>
2 : having a self-acting or self-regulating mechanism <an automatic transmission>
3 of a firearm : firing repeatedly until the trigger is released
**synonym** see SPONTANEOUS
- **au·to·mat·i·cal·ly** /-ti-k(&-)lE/ adverb
- **au·to·ma·tic·i·ty** /-m&-'ti-s&-tE, -ma-/ noun

---

### Post by samurailink3 on 2007-07-27
Good idea, and yea, I've run into the occasional rude person in #ubuntu. Those things just happen sometimes. Using #ubuntu-help would be a good idea, but I think it would get flooded with noobies anyway, since that's kinda the main point of the program ;) . A button to provide support is an excellent idea. Why not provide a just as easy way to help people out. I think we've got a good features list so far, how do we go about recruiting coders and such. I don't know how to program just yet, heading to school in the fall for that, myself. There is a launchpad group, but to be completely honest, I'm not quite sure what I'm doing ;) . As always, thanks for the feedback, any suggestions at all are helpful. :)

---

### Post by bobbocanfly on 2007-07-27
Really like the idea. Would certainly have helped me when i first started (though whenever  get stuck the first thing i do is google it (must be some sort of genetic thing)). I especially like the delayed forum request idea. 

Probably wouldnt be a brilliant idea just to dump them into the standard #ubuntu room. That place is permanently packed. Maybe a special room on irc.freenode.org specifically for this.

Would certainly be a great inclusion for Gutsy or Gutsy+1

---

### Post by rich.bradshaw on 2007-07-27
It's a genius idea!

---

### Post by ZacDavis on 2007-07-27
I don't think it would be a problem getting volunteers to provide support.

---

### Post by bobbocanfly on 2007-07-27
> **ZacDavis said:**
> I don't think it would be a problem getting volunteers to provide support.

I would certainly try and help out. 

One of the ways that you could do it, (if you had loads of time, which obv. you dont if you want it to be in Gutsy) is to write a special server, so take it off the IRC networks, which handles it in a specified way, so the volunteer could be sitting at his desk and the icon starts flashing when a question gets routed to him (via the server obviously). Probably very complex and a bit of an overkill for this sort of app but just an idea.

---

### Post by Hippu on 2007-07-27
I think that you should use launchpad answer, instead of these forums. Since they are propably much easier to integrate into this program (see: [https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)). And I guess we are making this a gnome-panel plugin?

---

