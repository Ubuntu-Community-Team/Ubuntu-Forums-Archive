---
title: "extending aptitude: Idea #2"
date: 2005-09-28
forum: The Cafe
---

### Post by brentoboy on 2005-09-28
The biggest weakness I can see with aptitude is that every package is of equal emphasis.  Packages, sub packages, stand alone stuff, documentation... whatever. Everything is created equal.

So, my ignorant self says: for my new Ubuntu, I want to set up an apache server, php, mysql, and samba.

And I find that there are 400+ php things, ditto for mysql, and apache has a whole bunch of crap too.  Samba doest install its own documentation, unless you ask for it, and there are a dozen and one packages that may or may not actually be needed in order to be a "generic" apache server.

The descriptions are sometimes really helpful, and sometimes quite worthless.  In some cases, only the programmer and uber-geeks have any idea what is excess and what is important.   We need collections of packages.

For instance, suppose I want the Java runtime, and the build tools necessary to compile Java apps.  Using my windows experience, and my newfound knowledge of synaptic (which I absolutely love) I search for java  -  and java compiler.  there are too many choices, half of which look like they are absolutely necessary, but probably just take up harddrive space, and don't add any menu items to gnome, so I wont even know they are there.

We need umbrella packages.  A package that lists is sub-packages and related packages and tells us what we need and what is optional, and what we need to know to select the "questionably necessary."

packages that represent “applications” would be bolded in the list (or the others wouldn't even show up unless you asked for “lesser” packages. )  When you select an application with subcomponents, it is actually a tree, that you can expand and select the subcomponents – which have default selections determined by the main component.

this is “sort of” implemented already – there are packages – like “gnome” that includes tons of other “dependencies” but a subcomponent is different then a dependency.

any comments?

---

### Post by Stormy Eyes on 2005-09-28
Umbrella packages, or meta-packages, are not aptitude's job. They are the job of the distribution maintainer. If the guy maintaining, for example, all of the GNOME packages wants to create a meta-package that treats all of the main GNOME packages as dependencies, then that is the maintainer's problem.

---

### Post by brentoboy on 2005-09-28
I can go with that, but here is where that becomes annoying.

suppose I don't need evolution.  If I unselect it, then it wants to remove the ubuntu-desktop which sounds kind of scary.  this is because evolution is part of the "umbrella" ubuntu- desktop - not a requirement.  it is a subcomponent.  it is totally optional, but a recommended part of the whole.

Like it or not, Synaptic is the "best" option for finding new packages and deciphering whether or not they will be of value for them. The more synaptic does to make life easier the more people will like it.

...

---

### Post by brentoboy on 2005-09-29
[QUOTE=Stormy Eyes]Umbrella packages, or meta-packages, are not aptitude's job. They are the job of the distribution maintainer. [/QUOTE]

The umbrella packages could be created by the distro maintainer.  Each distro could have its own.  In fact, you could either select the ubuntu PHP umbrella or the debian one - if you had both listed in your pool - each might have different defaults - depending on the goals of the distro.   That doesnt change the fact that there is too much to choose from, and not enough help from synaptic.

---

### Post by brentoboy on 2005-09-29
Ok, so im still thinking this out, and here is another thought.

I have mixed feelings about the wonderful, simplifed, package manager offered by ubuntu that is the "easy man's synaptic" the lets you choose from a few hundred apps and check the ones you want.

First off, let me say it is great.  It is easy as pie, I could show my grandma how to use it, and she could install software on her computer using it.  That is impressive. Job well done.  Also, I am gald to see the exponential growth of the list of packages in there.  - more games... must have more ... games ... 

On the other hand, it is somwhat counterproductive, because people will use it, and never even get to know how to use synaptic - which is also a wonderful tool.  It will be duanting by comparison.

In the ideal situation, people would select those apps in synaptic rather then in a seperate application.  So people could get used to the high power version.  The "high profile" packages - like the ones in the "easy package manager" could just be *bolded* so they stand out. or otherwise marked as "hey you, this is probably what you are looking for."

It is ussually best for people to have one tool that does a partiular function, rather than 2. Instead of making an easier one, change the existing one to make things easier. - I take that back - they should have 2 tools, 1 for the command line, the other as a gui.

---

### Post by UbuWu on 2005-09-29
[QUOTE=brentoboy]
In the ideal situation, people would select those apps in synaptic rather then in a seperate application.  So people could get used to the high power version.  The "high profile" packages - like the ones in the "easy package manager" could just be *bolded* so they stand out. or otherwise marked as "hey you, this is probably what you are looking for."[/QUOTE]

No, there is a difference between managing packages and installing programs, so it is great that it is split up in two programs.

---

### Post by brentoboy on 2005-09-29
[QUOTE=UbuWu]No, there is a difference between managing packages and installing programs, so it is great that it is split up in two programs.[/QUOTE]

im listening, what is the difference?
How can I tell what is a package, and what is a program?
As a noobie, synaptic is like the "google" of supported programs. Search here, install stuff that looks like what you want.

Other than the 1% of packages that show up in the "programs" installer, where do you get the other "programs"?

Your statement only works if there is a difference between packages and programs.  (which actually sounds very appealing).

---

