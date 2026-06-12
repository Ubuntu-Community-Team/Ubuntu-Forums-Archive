---
title: "Privacy threat due to 2 out-of-the-box bugs in ubuntu 13.10 Unity Tor Browser"
date: 2014-01-21
forum: Security
---

### Post by Damico on 2014-01-21
Are the ubuntu 13.10 Unity developers aware of these two security bug that shows up when using Tor?
 How do we properly report such anonymitythreats, that only show up on Ubuntu?    

1. The Tor Browser launcher is confusingly mixed up with Firefox.
2. The Vidalia Control Panal doesn't get its own launcher.

Both these bugs only show up in Ubuntu as there are no known reports of them occurring on any other operating system.

The first bug results in inevitable privacy violations (because the Unity desktop doesn't distinguish between the non-secure Firefox and the secure Tor browser). 
 The second bug prevents necessary changes to the Vidalia settings (except on the very first invocation of the Tor Browser Bundle at installation time).    

The main workaround is to use another operating system when anonymity is desired.

A secondary workaround is to modify the *.desktop settings, but that will only *_partially_ disengages* the (secure) Tor Browser from the (insecure) Firefox browser.  
And, that still doesn't help with the Vidalia control panel problem.

The problem is that I'm almost certainly not the technical guy to report these two bugs - but - since they clearly exist, someone has to report them. 
  **How do we know whether the developers are aware of these two bugs?**

---

### Post by QIII on 2014-01-21
Verbiage sounds familiar ...

[Here]("http://ubuntuforums.org/showthread.php?t=2182827") maybe?

---

### Post by cariboo on 2014-01-22
> **Damico said:**
> I'm almost certainly not the technical guy to report these horrid bugs - but - since they haven't been fixed since Ubuntu 13.10 came out, someone has to report them.
Do we know whether the developers are aware of these two bugs?

You don't have to have a lot of technical knowledge to report Ubuntu bugs, the developers have made bug reporting fairly easy for everyone, no matter what your skill level. To report a bug against vidalia for example, just press Alt-F2 and type:

```
apport-bug vidalia
```

and follow the prompts. You will have to have a Launchpad account, which you can register quite easily by going to [http://launchpad.net](http://launchpad.net), and click the [Login or create an account]("https://login.launchpad.net/+login") link in the upper right.

---

### Post by Damico on 2014-01-23
> **cariboo907 said:**
> You don't have to have a lot of technical knowledge to report Ubuntu bugs

I appreciate your confidence in me, but, I only know what the bug 'is' and its repercussions. I don't know WHERE the bug lies.
Is it in the desktop? In Unity? In Ubuntu 13.10 only? In Nautilus? In Tor? In Vidalia? 

Luckily, the bug happens to EVERYONE on Ubuntu (and nobody on any other operating system), so, I can "assume" (although we all know what that means) that it's an Ubuntu problem alone.

Moving on, and searching on my Windows laptop for tor browser bugs in the suggested location ([https://bugs.launchpad.net](https://bugs.launchpad.net)), I see bugs when I search for "Tor" or for "Vidalia"; but I don't see this bug reported.
I grepped for both "Tor" and "Vidalia" in the [Saucy Salamander Release Known Issues]("https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes#Known_issues"), with similar negative results.

I can only assume one of three things:
a) Everyone is too busy with more important things to worry about than privacy issues, or,
b) I'm the only one on the planet who cares about such privacy issues, or, more likely,
c) I'm doing the search incorrectly.

Rather than just assuming my search was bad and giving up, I'll file the bug report from my Windows computer, but, I'm really not the guy to provide technical details to Ubuntu developers. 
I just know usability issues, as they relate to privacy.
What I know, for sure, is that it doesn't work right on Ubuntu 13.10, such that, any user using the Tor Browser Bundle on Ubuntu 13.10 is taking an additional risk that is not found in all other operating systems for which the tor browser bundle is available.

EDIT: 
I'm logged into Launchpad, but, at least on Windows (which is all I have right now), pressing Alt+F2 does nothing.
All I need is a link to file a bug report.

EDIT:
OK. That was a royal waste of time. I gave up trying to find the bug reporting button in Launchpad at the suggested URL.

EDIT:
Resorting to Google, and typing the obvious: "how to file a bug in ubuntu", this comes up first: 
 [How to file a bug in Ubuntu]("http://www.omgubuntu.co.uk/2012/02/how-to-file-a-bug-in-ubuntu") (but I don't have flash installed on the Windows work computer I'm at).

Next on google is [bug-reporting etiquette]("https://help.ubuntu.com/community/ReportingBugs"), and [How do I report a bug]("http://askubuntu.com/questions/5121/how-do-i-report-a-bug"), both of which seem to contain the detailed steps to report the bug (but, that strange Alt+F2 shows up again, which, again, doesn't do anything while logged into Launchpad).

EDIT: Woo hoo. I finally found [a link to file a bug report]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect") on Launchpad!

**I filed the bug report:**
Title: [Privacy leak ONLY on Ubuntu 13.10/Unity using default official Tor Browser Bundle (including Vidalia)]("https://bugs.launchpad.net/ubuntu/+bug/1272025")

---

### Post by cariboo on 2014-01-23
Apport-bug only works when running an Ubuntu distribution, I assumed that seeing as you are posting here that you are at least running Ubuntu.

---

### Post by Damico on 2014-01-25
> **cariboo907 said:**
> Apport-bug only works when running an Ubuntu distribution, I assumed that seeing as you are posting here that you are at least running Ubuntu.

I have multiple computers. Not all operating systems at all locations. When I was reporting the bug, I wasn't on ubuntu. Probably 10% of the time I'm on Ubuntu, the rest on Windows.
Of course, EXACTLY what I thought would happen to the bug, happened.
A bot appended that I didn't add enough information, even though I painstakingly explained every single bit of information that I knew.
Here's what the bot said:
> 
                        Thank you for  taking the time to report this bug and helping to make Ubuntu better.   It seems that your bug report is not filed about a specific source  package though, rather it is just filed against Ubuntu in general.  It  is important that bug reports be filed about source packages so that  people interested in the package can find the bugs about it.  You can  find some hints about determining what package your bug might be about  at [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage).  You might also ask for help in the #ubuntu-bugs irc channel on Freenode.
 To change the source package that this bug is filed about visit [https://bugs.launchpad.net/ubuntu/+bug/1272025/+editstatus](https://bugs.launchpad.net/ubuntu/+bug/1272025/+editstatus) and add the package name in the text box next to the word Package.
 

So, do any security experts know which PACKAGE to file the bug against?

---

### Post by QIII on 2014-01-25
Did you install the tor Browser Bundle from the Canonical repo?

---

### Post by Damico on 2014-01-25
> **QIII said:**
> Did you install the tor Browser Bundle from the Canonical repo?  Well, that's an interesting question, if only, the answer was assumed to be that it doesn't exist in the Canonical repo. 
**Does a Tor Browser Bundle actually EXIST in the Canonical repo?** 
*(If so, that's new welcome news to me - because it would indicate that Canonical is interested in protecting their user's privacy - and - if so - that's a great step forward for Canonical - but I've never seen it.)*  [HR][/HR]Note: The Tor Browser Bundle is not just an assemblage of Tor, Privoxy, Firefox, and Vidalia.

---

### Post by QIII on 2014-01-25
That is exactly my point.  It doesn't exist in the Canonical repos. And I know that the TBB is not just several things assembled.  I know exactly what it is and where it comes from.

Did you install it from a PPA from some place like webupd8.org? Did you install it after getting it from torproject.org?

---

### Post by Damico on 2014-01-25
> **QIII said:**
> That is exactly my point.  It doesn't exist in the Canonical repos. And I know that the TBB is not just several things assembled.  I know exactly what it is and where it comes from.

Did you install it from a PPA from some place like webupd8.org? Did you install it after getting it from torproject.org?

How it was installed was described in the bug report but I'll repeat here, the installation procedure is simply to untar the package. 
That's it. 

Nothing more than that, is all you should EVER need to "install" the Tor Browser Bundle, since it's DESIGNED to be portable, from the start.

[LIST]
[*]So, on Windows, to install it, you simply unpack it and then run it.
[*]Likewise, on Apple, you simply unpack it, and run it.
[*]It works the same way on Linux (all but Ubuntu).
[/LIST]

Here's the web page with those simple instructions:
[https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)

---

### Post by QIII on 2014-01-25
I asked you that in this thread purposely so the answer would be here and not in a link somewhere else.  You will have to forgive me, because it was a deliberately leading question.  You installed it from a third-party source over which Canonical has no control.  Is it reasonable to assume that if a third-party package does not work, then the fault is with Ubuntu?  That the Ubuntu developers have some fault?

If  you buy an aftermarket product at an auto parts store and find that it  does not fit your Ford, is there a problem with your Ford?

The fact is that installing the TBB on Ubuntu *does cause* a problem.  It is *not *the case that the problem is Ubuntu's nor is it the case that the Ubuntu developers are responsible to address that problem.  That it does not work on Ubuntu and "only" Ubuntu is not particularly surprising, since Unity is only used on Ubuntu as installed by default.

The correct place to report this is torproject.org -- which is exactly what is stated at the bottom of the bug report.  The Ubuntu developers are under no obligation to design Ubuntu in order to be sure that the TBB, or any other particular piece of software, works with it.

Whether or not blatantly *not *making sure it works with some particular piece of software is *wise *is a different matter entirely.

On the other hand, should torproject.org have to do a lot of extra work to make sure the TBB works with a DE like unity that is unique to one distro?  Probably not, and I wouldn't blame them for not expending the effort.

---

### Post by deadflowr on 2014-01-25
You should go back to your bug report and fill in what package was affected.
You only named Ubuntu.
hence the invalid.
Click the arrow on the bugs line (the line with Ubuntu > invalid > blah, blah)
then add the package name affected to the package line.

---

### Post by QIII on 2014-01-25
The problem is that the package involved is a third-party package over which Canonical has no control.  There is no Canonical repo package to report the bug against.

---

### Post by deadflowr on 2014-01-25
[tor]("http://packages.ubuntu.com/search?keywords=tor")'s in universe repo.
same with [vidalia]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=vidalia&searchon=names").

If another version is installed that's another matter.

---

### Post by QIII on 2014-01-25
This is the Tor Browser Bundle from torproject.org, not the tor and vidalia packages from the Canonical repo.

Which is why the last comment before the bug report was closed as invalid said that it should be reported to torproject.org.  If there were a MOTU packaging the Tor Browser Bundle for the Universe repo, that would be different.

But it is clear that there *is definitely *a big problem that affects Ubuntu users here.

---

### Post by deadflowr on 2014-01-25
> **QIII said:**
> This is the Tor Browser Bundle from torproject.org, not the tor and vidalia packages from the repo.


In that case, the OP should follow the advice in post #3 in the invalid bug report.:D
Upstream is always better anyway.

---

### Post by Damico on 2014-01-25
The only comment in the Ubuntu bug report said to file it to Tor, so, as always dutifully following instructions, I ran a search, and didn't find the bug reported, so, I then filed the bug report with that organization, as referenced below:
URL = [https://trac.torproject.org/projects/tor/ticket/10730](https://trac.torproject.org/projects/tor/ticket/10730)
Title = Privacy leak ONLY on Ubuntu 13.10/Unity using default official Tor Browser Bundle (including Vidalia issues)

---

### Post by QIII on 2014-01-25
Which is exactly where the report needed to go.

My point is not that this isn't a problem.  It most certainly is.  Ubuntu users should be alerted to it.

 But this is a condition that arises as a result of the installation of a third-party package that Canonical can't fix.  It's not a bug with Ubuntu/Unity.

The fact that this is the third thread I've been in that started out almost exactly the same with such similar verbiage leads me to suspect that there is some misinformation or misunderstanding circulating out there in the ether which has been incorrectly laid at the feet of the wrong party.

A warning is certainly appropriate.  Calling it a bug with Unity/Ubuntu is not.  Everyone would be better served if this were dealt with appropriately.

---

### Post by Damico on 2014-01-25
> **QIII said:**
> I asked you that in this thread purposely so the answer would be here and not in a link somewhere else.  You will have to forgive me, because it was a deliberately leading question.  You installed it from a third-party source over which Canonical has no control.  Is it reasonable to assume that if a third-party package does not work, then the fault is with Ubuntu?  That the Ubuntu developers have some fault?

Thanks for explaining, because, for a second there, I had thought that Canonical might have a tested repo for the Tor Browser Bundle (which would have been welcomed with open arms).

** Yes. I shall be very clear with a few things:**
1. The Tor Browser Bundle is a very specific combination of things, with settings and other customizations, such that it's not the same as just installing Tor + Privoxy + Vidalia + Firefox (although if you were really competent, you could probably make it very similar by installing those separate packages, and customizing them the same way - but nobody does that because the TBB does it for you).
2. My Tor Browser Bundle tarball was obtained from the standard Tor web site (and not from Canonical).
3. The moment I unpacked and ran it, I could see that things were not right (I've been using the TBB for years on a variety of platforms - so I know how it's supposed to work).
4. I googled first as always, and I read everything I could find on this, which seemed to indicate the problem was in Ubuntu (but who am I to say, as I'm really just the victim, and the messenger, at the same time).
5. Let's be up front that I am not really the guy to report these things. I care. I see the problem. Everyone on Ubuntu 13.10 sees the same problem. But still, I'm not technical enough to be the guy reporting this to anyone. But, if it's me, it's me. (I'm ok with that; I just want to be honest that I've never filed a Canonical or Tor bug report in my life before this week!).
6. Let's also be just as clear that I said, from the beginning, that I have no firm idea WHERE the bug lies. I just know it exists on Ubuntu 13.10, and it does not exist on my RHEL6, CentOS6, and Windows installations.
7. So, I said, from the beginning, that I "assume" (knowing full well what that word indicates and what it can do to you and me) the bug is in Canonical's code. 

At the moment, there is a bug opened (and I think immediately invalidated) to Canonical; and another one to Tor that I just opened a few minutes ago.
UBUNTU: [https://bugs.launchpad.net/ubuntu/+bug/1272025](https://bugs.launchpad.net/ubuntu/+bug/1272025)
TITLE: Privacy leak ONLY on Ubuntu 13.10/Unity using default official Tor Browser Bundle (including Vidalia) 

TOR: [https://trac.torproject.org/projects/tor/ticket/10730](https://trac.torproject.org/projects/tor/ticket/10730)
TITLE: Privacy leak ONLY on Ubuntu 13.10/Unity using default official Tor Browser Bundle (including Vidalia issues)

I really don't know what more I can do to get this bug addressed by whomever it belongs to.

---

### Post by Damico on 2014-01-25
> **QIII said:**
> 
My point is not that this isn't a problem.  It most certainly is.  Ubuntu users should be alerted to it.
 But this is a condition that arises as a result of the installation of a third-party package that Canonical can't fix.  It's not a bug with Ubuntu/Unity.

I apologize that I just saw this, so, it's good that we agree that this "issue" can easily compromise a Ubuntu user's identity (and it's a usability issue even without that as a repercussion).
So, at the moment, we'll just have to see what the tor project folks say about the bug I filed a little while ago to them.

It may be worth noting there is one other Tor-related bug that I filed to Canonical today, which appears to actually have roots in Debian code - but again - I'm just the messenger and not the guy to flesh this out any further than I already have:

** Here is that Canonical bug report:**
Title: [Tor Browser Bundle on Ubuntu 13.10 is useless until/unless one manually kills the ibus process]("https://bugs.launchpad.net/ubuntu/+bug/1272032")
Url: [https://bugs.launchpad.net/ubuntu/+bug/1272032](https://bugs.launchpad.net/ubuntu/+bug/1272032)

** And here is the corollary report at the Tor Project:**
Title: [Keyboard does not work in 64-bit TBB 2.3.25-10 and 3.0 when ibus is running]("https://trac.torproject.org/projects/tor/ticket/9353")
Url:  [https://trac.torproject.org/projects/tor/ticket/9353](https://trac.torproject.org/projects/tor/ticket/9353)

In both these bugs, it "appears" to me, the problem is in the operating system, but, that's an assumption on my part which I am NOT technically astute enough to accurately make.
So, I will just have to let the bug reports speak for themselves, over time - as I'm really just the victim here - and I'm simply being a messenger - but one who isn't qualified to flesh these out further.

---

### Post by bashiergui on 2014-01-25
> **Damico said:**
> 1. The Tor Browser launcher is confusingly mixed up with Firefox.
2. The Vidalia Control Panal doesn't get its own launcher.
I don't understand the issue. Are you using a regular browser simultaneously with a Tor browser? That's a bad idea because it's easy to confuse the two browsers and there are various attacks that could identify you.


When I start up the Tor browser bundle I do it on the command line with ```
./start-tor-browser
``` That launches the vidalia control panel and then the firefox Tor browser. I have no issues or concern with this setup.

---

### Post by Damico on 2014-01-27
> **bashiergui said:**
> Are you using a regular browser simultaneously with a Tor browser? 

All three scenarios are bad on ubuntu:
1. Using both Tor Browser Bundle & native Fireofox (they're mixed up together)
2. Using just Tor (you don't know if you're using Tor or if you're using Firefox without doublechecking every single time)
3. Using just Firefox (again, you can't tell - since only on Ubuntu, they're mixed up together).

Of course, the safest thing to do, since Ubuntu mixed them up, is to install one or the other. 
That necessitates having to boot to two different operating systems, one with JUST Firefox, the other with JUST the Tor Browser Bundle.
From a security standpoint, that might not be a bad idea (having a separate OS just for privacy); but the point is that it shouldn't have to be this hard to keep Tor separate from Firefox.
And, it's only this hard, on Ubuntu.

> **bashiergui said:**
> That's a bad idea because it's easy to confuse the two browsers and there are various attacks that could identify you.
Not on all other operating systems.
On Windows, for example, the two icons don't look at all the same. So, you KNOW which one you're opening up from the get go.
Plus, if both are running and iconified, the icons are extremely different, so, again, you KNOW which one you're opening up.
Once you open them up, they look similar - but switching between them is clear on all other operating systems other than on Ubuntu.
> **bashiergui said:**
> 

[QUOTE=bashiergui;12910439]When I start up the Tor browser bundle I do it on the command line with ```
./start-tor-browser
``` That launches the vidalia control panel and then the firefox Tor browser. I have no issues or concern with this setup.
OK. So now you have the Tor Browser Bundle started.
Let's say you're a busy man, and you have a few windows open, some of which are Firefox windows.
How do you tell the difference between them? 
(And, it's cheating to say you only have a single browser window open - because if we all used only one application at a time, we don't need launchers and graphical desktops in the first place.)

Also, do you realize that you can't pin the Tor Browser Bundle to the desktop on Ubuntu?
So, sure, you can launch it from the command line - but what is the point of the desktop icons then? For show?

Also, do you realize that you can't discern between an existing Firefox and an existing Tor browser when both are iconified?
There is no way to tell the difference between the two on Ubuntu, but, they're clearly different on all other operating systems.
It's mostly at this point that Ubuntu becomes the problem instead of the solution.

If you're not clear what I'm pointing out, it's best to open up a couple Firefox processes and then a Tor Browser Bundle process.
Then simply try to tell the difference between them, as you switch from one to the other.
Then, do that same feat on all other operating systems.

The moment you try it on any other operating system, you'll see what the problem is. Instantly.

---

### Post by seth-arnold on 2014-01-27
> **Damico said:**
> 
The moment you try it on any other operating system, you'll see what the problem is. Instantly.

Can you attach screenshots to one of the bug reports? I can't figure out what you're trying to say and I suspect a handful of screenshots will elucidate much. Spending a few hundred dollars on a Windows license isn't on the top of my todo list..

---

### Post by Damico on 2014-01-27
> **seth-arnold said:**
> Can you attach screenshots to one of the bug reports? I can't figure out what you're trying to say and I suspect a handful of screenshots will elucidate much. Spending a few hundred dollars on a Windows license isn't on the top of my todo list..

OK. I will snapshot a run on Windows and then another run on Ubuntu and show the difference and attach the screenshots to the bug report.

---

### Post by bashiergui on 2014-01-27
I've used the Tor browser bundle on Windows & Ubuntu. I understand what you're saying. If you want to create a shortcut/ icon for starting the TBB on Ubuntu, I'm sure you can find a tutorial somewhere (I remember seeing one a while back, probably stackexchange but can't remember). The beauty about Linux is that you can customize it as you want. 

Seems like more of a feature request than a bug report, but nonetheless it should be filed with Tor, not Ubuntu, as others have said.


As for keeping the browsers separate I am suggesting that you consider your practices when you use a Tor and non-Tor browser simultaneously. You could be compromising your privacy because there are some timing attacks that could reveal your identity.

---

### Post by Frogs Hair on 2014-01-28
> [COLOR=#000000]As for keeping the browsers separate I am suggesting that you consider your practices when you use a Tor and non-Tor browser simultaneously. You could be compromising your privacy because there are some timing attacks that could reveal your identity.[/COLOR]

Exactly !  From the website and notice it states helps rather than promising anonymity. 

> [COLOR=#1A1A1A][FONT=Helvetica]Tor is free software and an open network that helps you defend against traffic analysis, a form of network surveillance that threatens personal freedom and privacy,[/FONT][/COLOR]

---

