---
title: "Amazingly Great Simple Idea Improves user friendliness!!"
date: 2008-10-26
forum: Ubuntu Brainstorm
---

### Post by dolomite792 on 2008-10-26
Better Category organization through the implementation of new sub categories within the Add/Remove program in the main menu.

Scenario:  Jill wants to install a music program in Ubuntu.  She fires up Add/Remove in the main menu.  She types in music and is flooded with huge amounts of files that have nothing to do with what she is looking for and is overwhelmed.

Scenario 2:  John is looking for a specialized program he tries to search for it in synaptic but produces no results.  The program does exist but is not sure what to put in for search query, so he clicks some of the different file categories to search through hundreds of programs, he soon realizes there is no order to make it easier to narrow down his search.

Why not have sub menus within the main menus in Add/Remove?

like under music have a codecs sub menu, a music player sub menu etc.
The internet catagory is grossly disorganized and needs many more sub categories for some sanity.

Just dumping everything with a music or internet tag (for example) into one category is pretty messy.  It might have been cool back in the good old days but with the advances linux is making.  This type of user friendliness is non existent.  Plus it would be simple to implement.

What this would do is it would make it easier to sort through everything to find the programs that you are looking for instead of scrolling through hundreds of programs or fumbling on the proper search keywords.  


Having lots of programs in the repositories is great but with no great way to make sense of them all, does it really do them any justice?

Here's a poll do you like this Idea 

Yes or no?

---

### Post by aysiu on 2008-10-26
What's wrong with Add/Remove instead of Synaptic?

---

### Post by gnomeuser on 2008-10-26
Stuff will increasingly be installed by demand, look at what Fedora have spearheaded with regards to integration of gstreamer and packagekit. Once a media file is attempted to be played packagekit will offer to pull in the correct package - since you can split up the gstreamer packages down to individual components you could then get a very clean install base where only the codecs you actually need are installed and only as you need them. 

There are many other areas where this would work one suspects, empathy e.g. might pull in protocol support as needed or additional software might be pulled in as hardware is added (such as say a fingerprinter reader, once detected might pulling the required pam modules and go through the fingerprint registration process automatically).

This idea in comparison seems sorta 1995 to me, we don't need better division of an already broken process, we need the process to go away entirely. For the hardcore package wanglers we still have very powerful tools, for the user as much as possible really should happen as if by magic. PackageKit helps us do this, as well as upstream paticipation and standardization.

Another scenerio worth considering, sometimes apport is not able to capture a good backtrace, it could then offer to temporarily pull in the debug symbol packages needed, ask the user to rerun the scenerio that causes a crash followed by the regular bugreporting approach and uninstall of the symbols to avoid overhead. (Conary with it's rollback feature would be ideal here, but it will likely be a while before we see distributions migrating, alternatively btrfs snapshotting could be used to easily get back without leaving behind debrie)

PackageKit now also ships a browser plugin, what if we could slowly help every distro standardize on naming (FreeDesktop.org is trying to get such distro cooperation going, I wish Ubuntu would join up firmly, till then we pave over the problem by keeping a list of the different correct names), then if say I write a review of Banshee and you like enough to want to try Banshee. I can then add a button at the end of my review that allows one click invokation of PackageKit to pull in the package and offer to run it. This would work on any distro a user might be on where the package is available (I believe the plugin could support a callback to give a true/false state on availability to report to the user). This approach might also be interesting for creating a nice web 2.0 application interface, kinda like a shopping center for apps, something which has been attempted before but only tied to one distro.

---

### Post by dolomite792 on 2008-10-28
> **aysiu said:**
> What's wrong with Add/Remove instead of Synaptic?

Dude did you read my post carefully?  I want new sub folders to be added to add/remove or as its called synaptic.  Doesn't matter what its called anyway.  All that matters would be to have a better way to navigate it in a relatively simple way

---

### Post by dolomite792 on 2008-10-28
> **gnomeuser said:**
> Stuff will increasingly be installed by demand, look at what Fedora have spearheaded with regards to integration of gstreamer and packagekit. Once a media file is attempted to be played packagekit will offer to pull in the correct package - since you can split up the gstreamer packages down to individual components you could then get a very clean install base where only the codecs you actually need are installed and only as you need them. 

There are many other areas where this would work one suspects, empathy e.g. might pull in protocol support as needed or additional software might be pulled in as hardware is added (such as say a fingerprinter reader, once detected might pulling the required pam modules and go through the fingerprint registration process automatically).

This idea in comparison seems sorta 1995 to me, we don't need better division of an already broken process, we need the process to go away entirely. For the hardcore package wanglers we still have very powerful tools, for the user as much as possible really should happen as if by magic. PackageKit helps us do this, as well as upstream paticipation and standardization.

Another scenerio worth considering, sometimes apport is not able to capture a good backtrace, it could then offer to temporarily pull in the debug symbol packages needed, ask the user to rerun the scenerio that causes a crash followed by the regular bugreporting approach and uninstall of the symbols to avoid overhead. (Conary with it's rollback feature would be ideal here, but it will likely be a while before we see distributions migrating, alternatively btrfs snapshotting could be used to easily get back without leaving behind debrie)

PackageKit now also ships a browser plugin, what if we could slowly help every distro standardize on naming (FreeDesktop.org is trying to get such distro cooperation going, I wish Ubuntu would join up firmly, till then we pave over the problem by keeping a list of the different correct names), then if say I write a review of Banshee and you like enough to want to try Banshee. I can then add a button at the end of my review that allows one click invokation of PackageKit to pull in the package and offer to run it. This would work on any distro a user might be on where the package is available (I believe the plugin could support a callback to give a true/false state on availability to report to the user). This approach might also be interesting for creating a nice web 2.0 application interface, kinda like a shopping center for apps, something which has been attempted before but only tied to one distro.

I sure hope you submitted this idea.

But as it stands, ubuntu is probably going to keep its packaging system, so in that case it would be a simple fix to add in sub menus in the add/remove gui app.  It would be cool too

---

### Post by ericesque on 2008-10-28
Dolomite, Aysiu is not calling Synaptic by another name.  If you click the Applications menu there is an  Add/Remove application at the bottom.  

The Add/Remove application is a well designed implementation of your idea.  Great minds think alike, right? :)

---

### Post by gnomeuser on 2008-10-28
> **dolomite792 said:**
> I sure hope you submitted this idea.

But as it stands, ubuntu is probably going to keep its packaging system, so in that case it would be a simple fix to add in sub menus in the add/remove gui app.  It would be cool too

PackageKit overlays on the existing packaging system, it's no problem, all Ubuntu would have to do was follow upstream as they are increasingly adding PackageKit. It would not require replacing dpkg, though one day when dpkg (hopefully soon) gets replaced, PackageKit allows that process to be very smooth and the user experience should stay the same in that we have the same tools available.

So no, not submitted, this is work that is going to be included in the various applications as fitting. All Ubuntu has to do is make it a priority to default to including and using PackageKit. This should have happened for Ibex to be honest but if we don't see it by Jaunty someone high up seriously has a screwed up idea as to working with upstream.

---

### Post by kostkon on 2008-10-28
> **ericesque said:**
> dolomite, aysiu is not calling synaptic by another name.  If you click the applications menu there is an  add/remove application at the bottom.  

The add/remove application is a well designed implementation of your idea.  Great minds think alike, right? :)
+1

---

### Post by Choad on 2008-10-29
> **ericesque said:**
> Dolomite, Aysiu is not calling Synaptic by another name.  If you click the Applications menu there is an  Add/Remove application at the bottom.  

The Add/Remove application is a well designed implementation of your idea.  Great minds think alike, right? :)
but it's blatantly NOT what he is wanting. at least not my add/remove on 8.04. still just got a broad "internet" category with a metric assload of programs that do something on the internet.

---

### Post by scaine on 2008-10-30
> **Choad said:**
> but it's blatantly NOT what he is wanting. at least not my add/remove on 8.04. still just got a broad "internet" category with a metric assload of programs that do something on the internet.

I'm not sure how much more categorised add/remove could get without devaluing its categories.

Yeah, there's a lot of stuff in "internet", you're right.  But what internet-related function do you need?  Download?  Then type "Download" into the search while the Internet category is highlighted - now you've only got 20 apps to chose from.  You can go even further - search for e.g BitTorrent instead of just Download.

Or click on Sound and Video, then type "Streaming".  It works really well already.

In fact, the only thing that's annoying about this app is that I can't find a way to say "Don't show me KDE apps".  If I knew more about this app (is it gnome or ubuntu and what's it actually called), I could submit that idea for sure.

---

### Post by dolomite792 on 2008-10-31
> **ericesque said:**
> Dolomite, Aysiu is not calling Synaptic by another name.  If you click the Applications menu there is an  Add/Remove application at the bottom.  

The Add/Remove application is a well designed implementation of your idea.  Great minds think alike, right? :)

Re read my post, I know you didn't. 

Thw entire idea is to add more sub catagories within the Add/remove and not the more complex synaptic program found in the admin.

For instance in the games catagory you could split it up into

Card games
Role playing
Racing

etc.

Simple little additions like that to organize things so games of the same type aren't all spread out through the whole unorganized catagory.

---

### Post by dolomite792 on 2008-10-31
> **scaine said:**
> I'm not sure how much more categorised add/remove could get without devaluing its categories.

Yeah, there's a lot of stuff in "internet", you're right.  But what internet-related function do you need?  Download?  Then type "Download" into the search while the Internet category is highlighted - now you've only got 20 apps to chose from.  You can go even further - search for e.g BitTorrent instead of just Download.

Or click on Sound and Video, then type "Streaming".  It works really well already.

In fact, the only thing that's annoying about this app is that I can't find a way to say "Don't show me KDE apps".  If I knew more about this app (is it gnome or ubuntu and what's it actually called), I could submit that idea for sure.


Try searching for specific things and you'll notice that you have to reword your search terms alot.
You should be able to quickly click into the catagories to find what your looking for.  Instead of having to sort through alot of programs.

The point of the matter is that things like download or streaming are basic and not where the issue arises.  That oversimplified and kind of a narrow minded opinion.  The point of this is to make things easy and appeal to alot of people and not just "what you think is good". 

In the thread I noted that its time to further add some polishes to the Add/Remove and not change its basic function.  The argument is not over whether people can find stuff in it by typing in search query but rather that they can more easily sort through what is already there.  

If you could click internet and have sub catagories like

Ftp programs
html editors
messengers
web browsers
etc

You could have all of the programs display like they are now, but put a heading with the sub category name and then list all of the programs underneath, then the next category heading would be underneath those all the way down the page.


In essence smart category choices wouldn't do a lot of damage to the type of system that is there right now.  Just as long as there is some sort of sorting involved, even being able to have the option of things being sorted into sub catagories and then have people able to not have anything sorted at all would be cool,

---

### Post by dolomite792 on 2008-10-31
> **gnomeuser said:**
> PackageKit overlays on the existing packaging system, it's no problem, all Ubuntu would have to do was follow upstream as they are increasingly adding PackageKit. It would not require replacing dpkg, though one day when dpkg (hopefully soon) gets replaced, PackageKit allows that process to be very smooth and the user experience should stay the same in that we have the same tools available.

So no, not submitted, this is work that is going to be included in the various applications as fitting. All Ubuntu has to do is make it a priority to default to including and using PackageKit. This should have happened for Ibex to be honest but if we don't see it by Jaunty someone high up seriously has a screwed up idea as to working with upstream.

Sorry dude stop hijacking the thread, if people care about it then they will implement it. Make your own topic 

I know I said to add your own ideas but, they should be ideas dealing with this topic of sorting through the mess of applications in the broad categories.

Thanks

---

### Post by SunnyRabbiera on 2008-10-31
> **dolomite792 said:**
> Re read my post, I know you didn't. 

Thw entire idea is to add more sub catagories within the Add/remove and not the more complex synaptic program found in the admin.

For instance in the games catagory you could split it up into

Card games
Role playing
Racing

etc.

Simple little additions like that to organize things so games of the same type aren't all spread out through the whole unorganized catagory.

I follow you, and it seems to be a good idea.
Mandriva has a feature like this, it not only displays categories like internet, but it has sub categories like "browsers"
Would be great for newcommers.

---

### Post by dolomite792 on 2008-10-31
> **Choad said:**
> but it's blatantly NOT what he is wanting. at least not my add/remove on 8.04. still just got a broad "internet" category with a metric assload of programs that do something on the internet.

Thank you

that's exactly what I'm describing

---

### Post by Eclipse. on 2008-10-31
Well, if you want the developers to have a look at it, head over to launchpad, create a blueprint and assign it for UDS Jaunty.

---

