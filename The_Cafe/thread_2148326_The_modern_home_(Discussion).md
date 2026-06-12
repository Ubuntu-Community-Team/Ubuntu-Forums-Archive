---
title: "The modern home (Discussion)"
date: 2013-05-24
forum: The Cafe
---

### Post by RadiationG0D on 2013-05-24
Hi everybody!
I've had this crazy idea for a while now of having a single top-of-the-line computer running linux standing at home in a room, waking up as soon as I got home.
This computer would then connect to all screens in the house (say 2/3 pc monitors, 1 tablet and a TV) and give them each a desktop interface that would not only be able to operate individually from each other, but also have access to the same files and a specifically fitted desktop interface.
Sending open programs to another screen with a it's own linked audiosystem would also be nice, as well as being able to activate all speakers with the same or with different songs at any given time without opening windows on all monitors, or even by using the phone. Voice control throughout the house would also be a nice feature.


So, here are the requirements:


[LIST]
[*]A single ubuntu (or other linux) computer capable of:
[LIST]
[*]Running 3 pc interfaces
[*]Running 1 tablet interface (android tablet)
[*]Running 1 TV interface
[*]controlling individual sound systems on their own and all at once
[*]Running 2 3d intense games on 2 diffrent screens
[*]Running multiple programs at once focused on one screen
[*]Understanding speech
[*]Waking quickly
[*]taking commands from mulitple keyboards, mouses, via a touchscreen and TV remote/cellphone
[*]shutting down as soon as I leave home
[*]sending messages to all screens at once
[/LIST]
[/LIST]

And the question (for discussion):[INDENT]If you wanted to accomplish all of this in a single home with today's technology in the cheapest possible way:[/INDENT]

[LIST=1]
[*=1]What kind of software and set-up would one need?
[*=1]What kind of hardware are we looking at (And what prices?)
[/LIST]
[INDENT][/INDENT]


----------------------------
&#9762; RadiationG0D &#9762;
----------------------------

---

### Post by whatthefunk on 2013-05-24
So you want a computer to run 3 different OSs on 5 devices at the same time that can understand speech and have a dozen different input devices.  Youll either be needing a time machine or a super computer.

---

### Post by deadflowr on 2013-05-24
I'd begin by reading through stuff like this

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Then when not reading, working to make lots of money to spend on all the stuff I would need.

---

### Post by georgelappies on 2013-05-25
Well this sort of home automation is semi doable. Have a look at this site:

[http://en.wikipedia.org/wiki/List_of_home_automation_software](http://en.wikipedia.org/wiki/List_of_home_automation_software)

The biggest issue is the speech recognition. Apple and Google have been pumping millions into trying to get it right and it is still not close to what you see on Star Trek ;) But as for the rest, it could be done with the right sensors and software. Could it be done however at a reasonable cost is another question altogether.

---

### Post by RadiationG0D on 2013-05-25
I'll have a better look at the wiki suggestiond when I get home, but it looks interesting!

However, regarding the interfaces: what would be the easiest way to run 2 or more screens with different desktop interfaces? (KDE, Unity, GNOME) 
And how would you stream one of these to a wifi connected tablet?

---

### Post by georgelappies on 2013-05-25
> **RadiationG0D said:**
> I'll have a better look at the wiki suggestiond when I get home, but it looks interesting!

However, regarding the interfaces: what would be the easiest way to run 2 or more screens with different desktop interfaces? (KDE, Unity, GNOME) 
And how would you stream one of these to a wifi connected tablet?

As for running Unity and KDE at the same time but on two different screens from only one box you would have to use vm software like virtualbox and run each instance as its own setup. But why would you want to do this??? Do you just want to 'look' at the screen or do you want to interact with it? If you want to interact with it from the tablet you would have to connect to the applicable vm on the server and use VPN / openssh software to control the vm's desktop. 

So you won't stream the screen as streaming implies only a one way interaction but you will actually log in to the vm running either Unity or KDE via the tablet.

---

### Post by vladster on 2013-05-25
That is looking complex

---

### Post by whatthefunk on 2013-05-25
Why would you want to stream an interface to a device which already has an interface?  That makes no sense at all.....

The best way to do this whole thing would be to just have a separate computer/device for each thing.  Running all these different DEs and screens through one computer is silly.

---

### Post by zer010 on 2013-05-25
What you're after is a few clients and a central server.  Although it would work for pretty much all of your requirements, it would not be ideal for gaming as you laid out.  I guess gaming could be done if the server was a $10000 beast, but it'd be best to let the clients carry that weight.  Also, why would you ever want your server to turn off when you leave?  You could access it and all of your files remotely and if you add a printer, you can even print remotely and have hard-copy waiting on you when you got home!

---

### Post by Paqman on 2013-05-26
> **RadiationG0D said:**
> 
What kind of software and set-up would one need?


Depends how close to your vision you want to get. Home automation is very possible, and can accomplish much of what you're looking for off the shelf. Take a look at projects like [Linux MCE]("http://www.linuxmce.com/") for an idea of where things stand. Unfortunately much of the home automation hardware like X10 is expensive.

To get all the screens in the house linked up all you need is a server that has all your data on it, that's trivially easy. You can get a pre-confgured server image that does that from Turnkey Linux and have it up and running in a few minutes. 

Smart TVs can access content shared via DLNA/UPnP, or you could add a small computer (RPi?) to the back of a dumb screen to enable it to access content over other protocols like NFS or SMB/CIFS. The other options for multi-screen computing would be thin clients, virtual machines or possibly a full-on multi-screen setup. 

I would suggest not using thin clients though if you want to have different interfaces. Better to boot off a local device (even if it's just an RPi) and connect to your data over the network.

Voice control would be nice, but doesn't work well in my experience. Micing up a whole house and expecting it to deal with ambient noise and commands from multiple sources would be a nightmare. There are cunning things you can do though, such as carrying a RF fob (something like bluetooth or zigbee?) in your pocket so that the system knows where you are and tracks you smoothly. It could have music or lights follow you, or send the current VM you were working in to the closest machine, so you wouldn't have to be far from a way of interacting. Smartphones are also an obvious option for an interface.

> 
What kind of hardware are we looking at (And what prices?)


Depends on what decisions you make to satisfy your demands.

What I would suggest is that you start with a single reasonably capable server that can be easily expanded as your requirements change. Don't try and do everything all at once. Prioritise what you want into a list of several stages of implementation. It's unlikely any one platform will be able to do everything out of the box. Pick the one that gets you most of the way there and implement that. You may be able to get started with the software side using a machine you already own, or a cheap second hand PC. Sharing data over a network and running some home automation needn't be resource intensive, it's only once you start wnating to do things like gaming that you're in trouble. 

Have you considered a streaming gaming service like Onlive to get your multi-screen gaming? Why reinvent the wheel if someone's already done it for you?

What you're trying to do is complex and there are a zillion little frustrations that could get in the way. Don't try and bite off more than you can chew. Divide it up into little stages and do them one at a time. That will smooth out the cost too.

---

### Post by georgelappies on 2013-05-26
> **Paqman said:**
> Depends how close to your vision you want to get. Home automation is very possible, and can accomplish much of what you're looking for off the shelf. Take a look at projects like [Linux MCE]("http://www.linuxmce.com/") for an idea of where things stand. Unfortunately much of the home automation hardware like X10 is expensive.

To get all the screens in the house linked up all you need is a server that has all your data on it, that's trivially easy. You can get a pre-confgured server image that does that from Turnkey Linux and have it up and running in a few minutes. 

Smart TVs can access content shared via DLNA/UPnP, or you could add a small computer (RPi?) to the back of a dumb screen to enable it to access content over other protocols like NFS or SMB/CIFS. The other options for multi-screen computing would be thin clients, virtual machines or possibly a full-on multi-screen setup. 

I would suggest not using thin clients though if you want to have different interfaces. Better to boot off a local device (even if it's just an RPi) and connect to your data over the network.

Voice control would be nice, but doesn't work well in my experience. Micing up a whole house and expecting it to deal with ambient noise and commands from multiple sources would be a nightmare. There are cunning things you can do though, such as carrying a RF fob (something like bluetooth or zigbee?) in your pocket so that the system knows where you are and tracks you smoothly. It could have music or lights follow you, or send the current VM you were working in to the closest machine, so you wouldn't have to be far from a way of interacting. Smartphones are also an obvious option for an interface.



Depends on what decisions you make to satisfy your demands.

What I would suggest is that you start with a single reasonably capable server that can be easily expanded as your requirements change. Don't try and do everything all at once. Prioritise what you want into a list of several stages of implementation. It's unlikely any one platform will be able to do everything out of the box. Pick the one that gets you most of the way there and implement that. You may be able to get started with the software side using a machine you already own, or a cheap second hand PC. Sharing data over a network and running some home automation needn't be resource intensive, it's only once you start wnating to do things like gaming that you're in trouble. 

Have you considered a streaming gaming service like Onlive to get your multi-screen gaming? Why reinvent the wheel if someone's already done it for you?

What you're trying to do is complex and there are a zillion little frustrations that could get in the way. Don't try and bite off more than you can chew. Divide it up into little stages and do them one at a time. That will smooth out the cost too.

Excellent reply Paqman, I like the way you think. Your idea with the Raspberry Pi's is great. Think I am moving this into my cool things to do when I have the time list :)

---

### Post by RadiationG0D on 2013-05-26
Agree with georgelappies. Extremely good answer Paqman!

As to the question why one would like to run diffrent interfaces at once: running GNOME 3 on a tablet would not be ideal.

And for everyone who thinks about why one would only want one computer for all this, just because! Also, it's hard to keep multiple clients up to date, with the same files and starting speakers in the entire house whenever you feel like it. Server, well sure but having to publish changes every single time and not having the same local file structure can be frustrating. (Especially when the files won't sync properly - happens to me all the time with U1)

So, to get the "right" idea: think about the Enterprises' main computer and the LCARS system reaching throughout the vessel.
(Star Trek reference for those who don't know.)

---

### Post by Paqman on 2013-05-26
> **RadiationG0D said:**
> it's hard to keep multiple clients up to date

That needn't be a big problem. LTS releases doing automatic security updates and a local APT mirror should make maintenance pretty minimal and be frugal on bandwidth (if that matters). The hardware would probably need updating before the software did.

Having centralised storage for your data doesn't mean doing absolutely everything on one machine. You only need one machine somewhere on your network that specialises in storage. Generally this is called Network Attached Storage. A server that does other stuff could also be a NAS, or you could go for one of the small low-power dedicated NAS boxes off the shelf. Like you say, syncing files between local machines by going through the internet is needlessly complicated and unreliable. Much easier to centralise all your data and just mount the shares on the other machines. Doing that also simplifies your backup and recovery plan, and allows for easy redundancy (never trust a hard drive!).

---

