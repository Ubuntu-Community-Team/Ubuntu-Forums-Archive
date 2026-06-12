---
title: "Features before bug fixing?"
date: 2012-09-06
forum: Testimonials &amp; Experiences
---

### Post by pihbar on 2012-09-06
Why does Canonical insist on pushing new features every six months? 

Introducing new features is great, but they generally tend to break things and reduce stability. Let me tell you what I mean by highlighting some Canonical-controlled basic window management bugs:
[LIST]
[*] About one in 20 times, invoking Unity's Dash crashes compiz and freezes my system for about 30 seconds. There's a ton of bugs like this, due to many different graphics configurations (I have nVidia and it happens on both free and non-free drivers). And it is due to Canonical because it doesn't happen for Gnome 3 or Xfce or whatever.
[*] Snapped windows on workspaces other than the first get randomly moved when clicking on their icon on the Dock. Ugh.
[*] Alt-Tab fails to focus the selected window very often when quickly switching between windows. Do you realize how frustrating it is to work quickly and expect to type in an editor, say, and have nothing happen quite often? It forces me to either use the mouse or work slowly.
[/LIST]

You can find these bugs on Launchpad, but the point is that these are bugs affecting something as basic as windows control. These should, I think, absolutely be fixed before adding **any** new feature to the dash (like file previews -- so gimmicky; which is fine, but please add it after fixing basics).

Now, these examples are just the ones that came up in 12.04. There were many problems with indicator-messages and the sound menu in past releases.

In addition to this, there's a bunch of non-Canonical software bugs that take time to fix. For example, LaTeX is very popular software that I use all the time, and this is my experience with it on Ubuntu: gedit-latex-plugin crashes gedit, Lyx crashes on save. Again, this is due to poor testing from the application developers, but it highlights the general problem. Don't even get me started on PulseAudio selecting the wrong input in resume from suspend, wireless randomly not working after it, etc.

Finally, hardware support is still rather poor, with no nice way to look up what works. I am scared to buy a laptop for Ubuntu because I don't know what will work.

--------------------------

I like Unity and the day it takes me to make my system usable is better for me than paying the additional $500 I would have to dish out for a Mac, but is this true for a general user? I know how to find, read and use bug reports to fix bugs, but the general user doesn't want to or need to.

LTS releases being 2 years apart doesn't really fix this problem. The issue is that there's still more features pumped into Ubuntu than is sustainable. Why not make every other release focus only on bug-fixing, thus halving the number of new features (effectively), but increasing stability (both by Canonical fixing bugs and by letting other developers catch up with their own bugs). In addition, this would give hardware support time to get better, and would still leave the option of being "cutting-edge" to those who want it. Rolling releases?

What do you think? Do you agree, and if so, what can be done to make things better?

---

### Post by vasilbelarus on 2012-09-06
I have used all versions of Ubuntu from 10.04 to 12.04. Alltogeather they where working fine. I think you are right that the system become less stable from day to day but I think that is not because Canonical insist on pushing new features every six months. You should keep in mind that Ubuntu based on Gnome and Gnome3 now changes quickly. Canonical now have much more problems trying to make gnome3 stable and ready to use in Ubuntu. Didn`t you hear about nautilus? Ubuntu developers should do a lot to give users full-featured file manager.
I hope you understand the idea :)
Best regards.

---

### Post by mastablasta on 2012-09-06
> **pihbar said:**
> Why does Canonical insist on pushing new features every six months? 


no, pushing  new features every 6 months is OK. if you want a longer freeze, then that's what the LTS releases are for.

on LTS releases they should fix most of the bugs. for example this one is supported unitl 2017. now in 5 years most of the majors bugs should be ironed out.

but they wont be.

---

---

### Post by diesch on 2012-09-06
From my experience Ubuntu 12.04 is quite stable for most (but not all) users. Problems like yours are often caused  by left over configurations from previous versions  or incompatible settings. To you get this problems on a newly created user, too?

To please as much users as possible you usually need a good balance between fixing bugs, adding new features and providing up to date software.

If you want a distributions where bug fixing has a higher priority you may have a look at for example Debian stable.

---

### Post by Tamlynmac on 2012-09-06
If your objective is to maintain stability/functionality, once your  system is setup and stable (preferably with an LTS) stop upgrading until  support runs out.

For those users that require stability, IMHO it  makes little sense to risk constant upgrading. Unless, an upgrade  includes improvements or enhancements one finds necessary with respect to normal  usage. In other words, adopt the "if it's not broke - don't fix it"  mentality.

Also, test a release prior to committing and assure  said release is fully functional on your system. Don't rely on fixes or  updates to maintain stability/functionality. The reality IMHO is that  some users just feel the need to run the newest release of anything.  Then complain because it's buggy. :wink:

No  one or nothing mandates one upgrade every six months. It's optional and  I'm certain some will argue that new or upgraded apps may require  upgrading the OS. But again, one must decide if they wish to risk the  stability/functionality of if their existing system - especially, if said system meets their needs.

Just my $0.02

---

### Post by thatguruguy on 2012-09-06
> **pihbar said:**
> 
What do you think?

I think what you're looking for is [Debian]("http://www.debian.org/").

---

### Post by pihbar on 2012-09-06
I'm not sure Debian's the answer. Older packages just mean older bugs.

---

### Post by thatguruguy on 2012-09-06
> **pihbar said:**
> I'm not sure Debian's the answer. Older packages just mean older bugs.

I've yet to see any OS or program that was completely bug-free.

If what you want is a distribution that values stability over expanding the feature set, give Debian a try.

Canonical is trying to expand the adoption of the Linux desktop. The only way to do that is to try new things, since the old way wasn't working. It's possible that Ubuntu isn't for you, if you don't like the idea of new features being added to the OS. At the minimum, you should only use the LTS releases and hold on to them until EOL. If you really, really value stability over everything else, use Debian.

---

### Post by mastablasta on 2012-09-07
> **thatguruguy said:**
> I've yet to see any OS or program that was completely bug-free.

 
that's true.
 
but usually systems don't have such bugs that will stop your hardware to function propperly after a system security update. it happened once on windows and then turned out it was 3rd party's fault. i guess it could happen again, but at leats it doesn't happen regulary. 
 
in Ubuntu so far to me... sound stopped working (12.04LTS) after a month or two, hybernate and suspend stopped working (12.04LTS) after about 3 weeks since install, camera stopped working propperly (haven't go tthe time to truble shoot it yet, but it was working in 10.10), flash wasn't working propperly on some GPU chips including mine (in 10.04, but it was at least fixed after 2 weeks)... and well that's abotu it so far and it is quite a lot. the point is hardware was/is compatible but updates keep brekaing it. and checking the launchpad it's not just me with these issues.
 
and let's not even start with power management for notebooks or now for desktops. 
 
i don't mind if there are bugs on start but i do expect them to be doing everything they can to fix them.
 
Debian stable is an option, but the problem is linux package management. try to install a new programme on old stable kernel and it becomes very difficult hunting down all dependencies. offocurse unless you use backports in which case you basically abandon "stable" again.
 
it would be good to have a stable kernel (there is no reason really to upgrade if it works well and if only security holes are patched) and new programmes.

---

### Post by thatguruguy on 2012-09-08
> **mastablasta said:**
> 
Debian stable is an option, but the problem is linux package management. try to install a new programme on old stable kernel and it becomes very difficult hunting down all dependencies.

Any installation of new programs will run the risk of introducing new bugs. If you want stability, don't do that.

---

### Post by pihbar on 2012-09-08
> **thatguruguy said:**
> I've yet to see any OS or program that was completely bug-free.

If what you want is a distribution that values stability over expanding the feature set, give Debian a try.

Canonical is trying to expand the adoption of the Linux desktop. The only way to do that is to try new things, since the old way wasn't working. It's possible that Ubuntu isn't for you, if you don't like the idea of new features being added to the OS. At the minimum, you should only use the LTS releases and hold on to them until EOL. If you really, really value stability over everything else, use Debian.

No, no.. I *do* like features. I was very excited for Gnome 3 (which was a disappointment), and then Unity (which wasn't a disappointment, in theory). However, as I tried and failed to successfully convey above, I think Canonical just introduces more features than they can handle properly.

I also touched upon why sticking with LTS releases isn't a good solution above. To put it more concretely, I think LTS releases still have all the bugs that weren't fixed from past releases and sometimes don't get important bugs fixed because doing so requires effort outside of working on new releases.

My hypothesis here is that a lot of bug problems come from having too many features too quickly, but of course, my argument relies on anecdotal evidence and it could be that there are other reasons. The point of this thread is to discuss precisely that. Telling me to switch to something else is certainly not a solution. It doesn't address the issue at hand, and it misses the point: I like Ubuntu. This is why I want to see it get better.

Debian I tried in the past. Wireless didn't work, graphics had problems. All in all, it was a sub-par experience that required even more hassle than Ubuntu (I used Slackware and Arch Linux in the past, so it's really not about choosing different distros).

Yesterday I finally got fed up with the dash crashing and ALT-TAB not working, and I switched back to Windows. Maybe I install Lubuntu which doesn't have as many window management bugs. I'll revisit Ubuntu every now and then, hoping that the bugs are fixed (since I do a lot of programming, which is kind of painful without a proper shell for me). But in the meantime, I want to have this discussion...

Edit: Yeah, after a day on Windows, I decided that while bug-free, the experience is lacking. Jeez, how do people manage? Now I just hope things get fixed!

---

