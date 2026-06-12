---
title: "Saffire LE + Jack Automatic Connections"
date: 2009-05-18
forum: Ubuntu Studio
---

### Post by dawiba on 2009-05-18
I was wondering if there was any way to change the default automatic connections in Jack?

I'm now using a Saffire LE and everything works fine, including the automatic connections when I start Jack. The thing is, I normally plug everything into my keyboard, use that as a mixer and then send the signal to the LE using the s/pdif connection. On the LE this means inputs 5+6. Jack however, defaults to inputs 1+2. This is fine as long as I remember to change the connections in Jack :oops:.

What I'm after, if possible, is a way to make Jack default to inputs 5+6 for automatic connections.

Can anyone point me in the right direction?

---

### Post by kayosiii on 2009-05-19
Currently it seems to be a design limitation of Jack - hopefully when jack 2 comes out there will be a sane way around this problem... IT depends on how the apps are connecting - some can be configured to work differently...

---

### Post by dawiba on 2009-05-19
> **kayosiii said:**
> Currently it seems to be a design limitation of Jack - hopefully when jack 2 comes out there will be a sane way around this problem... IT depends on how the apps are connecting - some can be configured to work differently...

It looks as if my brain has a design limitation because I keep forgetting to change the connections :)

Perhaps I can be configured differently!

Thanks anyway.

---

### Post by thorgal on 2009-05-19
dawiba, what is connecting automatically to in1 and in2 ?

---

### Post by dawiba on 2009-05-19
Thorgal:

In Jack Connections window, under 'system', 'capture 1' and 'capture 2' are connecting automatically to whatever audio track that I create.

Because of the way I normally do things, I want to use 'capture 5' and 'capture 6' to connect to tracks.

I've attached a screenshot to show what I mean as my explanations aren't always too good.

I should say, that it's not really a problem as long as I remember to change the connections when I first create a track. Also, I could just use inputs 1+2 on the Saffire LE.

I've also noticed that the connections seem to persist from one session to another, so it's only at the first time of asking that I have to remember.

Thanks

---

### Post by Stochastic on 2009-05-20
There is an option in Ardour to not automatically connect the inputs (not sure if that will help you remember).  It's under Options->Autoconnect->Manually Connect Inputs

Hope that helps.

Edit: whoops, it looks like that option isn't persistent across all ardour projects; it needs to be set for every new project created so it's no help.

---

### Post by AnWe on 2009-06-15
You could use either qjackctl ur jack.plumbing to automate this. The easiest by far is qjackctl; open "patchbay" and add the input and output sockets of clients you want to control. The "clients" listed are the ones that are currently active, so if you want to make connections between e.g. Ardour and the Saffire LE, just make sure FFADO (driver) and Ardour is loaded.

When you've added the appropriate sockets, just select them and connect them. Then save and activate the preset, and it should run every time there is a "connection graph change" e.g. a client appears/dissapears. You can have multiple presets for different activities, e.g. recording, mixing, DJ:ing, watching movies or whatever you do with your system.

There is a slight learning curve with the patchbay, but just fiddle around with it a little and it gets pretty obvious. Having the "connections" window open while you load presets and start/stop clients helps.

You can go on and make connections for every audio app in your system i you want/need to. I find it works very well. Sometimes you might need to adjust the matching pattern for a client/socket because they have dynamic names, but most of the time it "just works".

/Andreas

---

### Post by kayosiii on 2009-06-15
> **Stochastic said:**
> There is an option in Ardour to not automatically connect the inputs (not sure if that will help you remember).  It's under Options->Autoconnect->Manually Connect Inputs

Hope that helps.

Edit: whoops, it looks like that option isn't persistent across all ardour projects; it needs to be set for every new project created so it's no help.

The way to deal with that is to set up a template... that is create a new project make your settings changes, how many tracks by default, what they are connected to, stuff like midi bindings and save that to a template file.

When you create a new project you select the template from a drop down list and you get all your routing,bindings,settings ready to go.

---

### Post by dawiba on 2009-06-15
Thanks for all the helpful replies on this one, but I've actually managed to get the hang of it now!

---

