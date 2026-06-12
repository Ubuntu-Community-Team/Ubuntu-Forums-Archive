---
title: "Hacked?  What's going on."
date: 2011-01-03
forum: Security
---

### Post by AutumnPhoenix on 2011-01-03
I have a 6yo laptop...z60m.  Solid little thing that I knocked around so much the hinge broke. My dad jerryrigged it so it can stay open.

So now I use it as a glorified DVD player.  Then, around february the hard drive died.  I put it in fresh, loaded a couple of regular games and the DVD modifications to play DVD's.  So, besides the basic upgrade to 9.1 not much as been done.


Well, last week my panel disappeared.  I procrastinated and last night I got on the computer.  I did F2 and "xfce-panel" and my panel reappeared exactly how I'd last tweaked it.

With on exception.  This blue globe, "Akonadi" had mysteriously appeared.

Thing is that I haven't installed or updated anything for 8 months...why?  becuase I haven't had this thing connected to the internet.  The wireless tower has been on. (my bad) but all of the signigals in my neck of the wood are encripted so I just let it be.

I don't know where this program came from.  Is it loaded in xubuntu?  Why would it show up?  And furthermore if there was someone with malicious intent (unfortunatly I do have to take that into consideration) have put this on for data collection?

---

### Post by bodhi.zazen on 2011-01-03
There is nothing in what you posted that suggests you have in any way been "hacked".

---

### Post by AutumnPhoenix on 2011-01-03
I have a program that, to my knowlege, I did not install.  I'm pretty careful about what I do/don't install.  Furthermore it's really a kubuntu program, not an xubuntu program, so it's not something that could of "accidentally" gotten installed.

I'm still only vagulely clear on what this program does...and am concerned someone could of installed it remotely to run it and collect data.

---

### Post by Rubi1200 on 2011-01-03
[This]("http://en.wikipedia.org/wiki/Akonadi")?

You might want to check through your dpkg logs.

---

### Post by AutumnPhoenix on 2011-01-03
Yep, that's what showed up.  How can I check my dpkg logs?

---

### Post by bodhi.zazen on 2011-01-03
> **AutumnPhoenix said:**
> Yep, that's what showed up.  How can I check my dpkg logs?

I think you are jumping to conclusions without doing your footwork =)

In addition you have not posted sufficient information. Have you checked you logs ? Are there any new users on your system ?

What service are you running that would have been cracked ?

Why would a cracker do something so obvious as to install an icon on your panel ? Why not simply change your wallpaper to announce his or her presence ?

It is much more likely you installed some application that pulled this in as a dependency, Ubuntu tends to do this (list excessive dependencies).

How do you know you have not kde apps installed ? did you search with dpkg ? synaptic ?

---

### Post by cariboo on 2011-01-03
Probably the easiest way is to go to System->Administration->Synaptic Package Manager->File->History.

---

### Post by AutumnPhoenix on 2011-01-03
The icon showed upon a panel refresh.  My panel when missing (for no apparent reason) while I was watching a DVD one night.

I'll have to go on and pull up the dpkg installs.

It's pretty much a fresh install of xubuntu 9.10 with the acception that I installed "mines", "majong" and a few things to make the DVD player work.  I really haven't done alot in this install, as it's pretty much a DVD player.

---

### Post by bodhi.zazen on 2011-01-03
> **AutumnPhoenix said:**
> The icon showed upon a panel refresh.  My panel when missing (for no apparent reason) while I was watching a DVD one night.

I'll have to go on and pull up the dpkg installs.

It's pretty much a fresh install of xubuntu 9.10 with the acception that I installed "mines", "majong" and a few things to make the DVD player work.  I really haven't done alot in this install, as it's pretty much a DVD player.

Start by identifying what you have installed when and see if it is a dependency.

---

