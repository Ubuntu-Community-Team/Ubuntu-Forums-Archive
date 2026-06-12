---
title: "Javascript/flash tracking"
date: 2012-12-12
forum: Security
---

### Post by bjngchn on 2012-12-12
(This is  more about privacy rather than security, and about big professional sites than small naive sites, and about general public rather than me.)  I heard, big blayers like G, FB track users with js, flash etc (disabling cookies have no effect) using one pixel images and other such things (at least 200 of them).  So for example maybe, when I login to a Y email, and logout, close browser and erase all private info with firefox, and then login with a different username at Y, Y will know these users are the same, or at least they use the same computer. Maybe this doesn't work when js is disabled, but when js is enabled at another time, such past info can be collected easily(?)  So here it seems using  opensource (firefox and linux) doesn't help, using linux doesn't help, erasing info doesn't help.   Questions:  -Do you agree that this kind of tracking is done, and this is the reason many sites require JS to track users?  -I also heard it is very difficult to erase such tracking data placed on computers while browsing webpages.  Can some files on computers be erased or some firefox folders can be chmoded to to block this kind of tracking? Can about:config (prefs.js) or other firefox files be configured to minimize this kind of tracking? In short can anything be done against this (say, when everything is open source)?   Is the only way to block this kind of tracking, formatting the computer before each use?   -Can creating different user logins for different uses help? I guess answer is no.

---

### Post by Hungry Man on 2012-12-12
> Do you agree that this kind of tracking is done
Yes, Facebook will track you on various sites that host "Like" buttons. So will other companies that get websites to host their content.

> and this is the reason many sites require JS to track users?
No, most websites need Javascript to work for legitimate reasons. Virtually every page uses Javascript for something.

> In short can anything be done against this 
Sure. You can block the sites that track you.

This can be done in a few ways.

1) Add an Adblock Plus filter aimed for privacy:
[http://adversity.uk.to/](http://adversity.uk.to/)
[https://secure.fanboy.co.nz/fanboy-tracking.txt](https://secure.fanboy.co.nz/fanboy-tracking.txt)

2) Use a host file to block known ad-serving agencies:
[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

I also suggest you disable third party cookies in your browser, though this alone is not enough to prevent tracking.

---

### Post by DuckHook on 2012-12-13
> **Hungry Man said:**
> 1) Add an Adblock Plus filter aimed for privacy:
[http://adversity.uk.to/](http://adversity.uk.to/)
[https://secure.fanboy.co.nz/fanboy-tracking.txt](https://secure.fanboy.co.nz/fanboy-tracking.txt)

2) Use a host file to block known ad-serving agencies:
[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

I also suggest you disable third party cookies in your browser, though this alone is not enough to prevent tracking.

++++1

Also, if using FIrefox, install *NoScript*, turn off all scripting by default, and allow (whitelist) only those sites and, even then, only those *exact* scripts that you are absolutely, positively sure about. If even more paranoid like me, enable only temporarily for that session. Example: Linux Journal site tries to run eight scripts when visited. I allow only two: linuxjournal.com itself and cloudfront.net. Everything else is blocked. If missing functionality, too bad.

*BetterPrivacy* or equivalent is also useful.

I actually get a little irked about modern sites re the above... if more of us would simply refuse to cooperate with all of the scripting that is run invisibly on websites, maybe more of them would stop abusing our trust and start taking better care of our privacy. I know I'm pushing against a rope, but one can always daydream.

---

### Post by bjngchn on 2012-12-14
Thanks for answers.......................................................... "legitimate reasons" might be just "excuses'................................ I prefer elementary ways of doing this, like erasing some files: finding the folder where those 1-pixel images are stored and delete them manually........Why should I trust those noscript, adblock programs........ These sound like trojans which say "your computers at risk, download this and get protected.."......... How can I know that noscript program is not controlled by those big guys, or that program doesn't collect info? Maybe one program is used to store info another to collect it... I believe linux is great, but it is not enough. Can't we edit firefox to remove any aspects that do things which are not absolutely necessary. In firefox preferences there are two options for WebFeeds: "Preview" and "Add bookmark". I prefer "None" but it is not in the list........ Why doesn't anyone edit firefox to eliminate all junk stuff, and turn it into a browse-only browser... When privacy is lost globally, competition is also lost.

---

### Post by cariboo on 2012-12-15
There are other browsers that aren't as full featured as Firefox. I'd suggest you give them a try, if you don't trust browser add-ons.

Have a look [here]("http://www.junauza.com/2011/11/alternative-web-browsers-for-ubuntu.html") for a few available alternate web browsers

---

### Post by DuckHook on 2012-12-15
Given that Firefox aims to be a mass-market browser (used literally by millions), it cannot come with defaults too heavily weighted towards privacy/security. If it did, millions who prefer easy functionality to privacy or security would deem it "dysfunctional" and reject it. In the world of apps, it is an unfortunate reality that one must design for the lowest common denominator. The developers have no other choice, and there's nothing you or I can do about such default behaviour either. What we *can* do is harden our own installation to fill in the holes. The recommended add-ons do exactly this.

I suppose that it is just remotely possible that *NoScript* is itself a Trojan. I've deemed this to be so unlikely that I have no problem installing and using it. You have to make your own determination. Keep in mind that there is a point at which "security-conscious" becomes "paranoid". This point varies for each person. Not calling you paranoid. Just pointing out that we all have different tolerance for risk. But unless you are knowledgeable enough to comb through the source code, change to your liking and compile from scratch, at some point you have to just take a chance and go on trust. Personally, I already consider it fortunate that Firefox is sufficiently open to easily allow hardening.

I use *links2* for all general browsing. It can't run scripts, nor support cookies. Ergo, instant solution to the two worst privacy/security holes in a typical browser. But it is bare-bones, butt-ugly and will raise howls of sneers and laughter from the eye-candy crowd. As much as I like it and love its philosophy, it will never be anything other than a niche browser loved by tin-foil-hat paranoid kooks like me. If you are concerned about installing a Trojan, you can download the source code, go through it with a fine-toothed comb and compile it yourself. For those slightly less paranoid:

```
sudo apt-get install links2
```

Edit:

*links2* does sustain frames and images, but you must run it in graphics mode with the *-g* switch to get this functionality.

---

### Post by Hungry Man on 2012-12-15
NoScript is open source and the developer is out in the open.

---

### Post by DuckHook on 2012-12-15
> **Hungry Man said:**
> NoScript is open source and the developer is out in the open.

I know this and it's one of many things to like about it. I think the OP's position (and mine, to much lesser extent) is that source is one step removed from the typical user because we lack the skill to review and detect. For better or worse, we rely on the binary from some repository. My point is: we therefore must take some things on trust. As only one example, 99% of people download Firefox itself as a binary. Could it be a Trojan?

---

### Post by Hungry Man on 2012-12-15
[http://cm.bell-labs.com/who/ken/trust.html](http://cm.bell-labs.com/who/ken/trust.html)

tl;dr: Compiling your own software doesn't negate potential issues with that software being compromised. He demonstrates a C compiler that was backdoor'd and then any time it compiles a C compiler it compiles ti to include the backdoor in anything the second compiler compiles (that sentence nearly got away from me).

There's a point, for all of us, where we have to just trust that the package isn't backdoor'd.

---

### Post by JKyleOKC on 2012-12-15
Also worth mentioning is the fact that everything found in the official repositories has been gone over by experts and deemed to be as secure as it's possible to get (keeping in mind that total security, like perfection, cannot be achieved).

While browser add-ons do not come via the repositories, those which are listed in the browser itself are usually safe. If in doubt, Google searches using the name of the add-on package are a good way to learn the reputation of the program.

As always, security is a process rather than a program. The same heads-up attitude required to pilot an airplane or to handle a car in NASCAR competition is necessary!

---

### Post by DuckHook on 2012-12-16
> **hungry man said:**
> [http://cm.bell-labs.com/who/ken/trust.html](http://cm.bell-labs.com/who/ken/trust.html)

there's a point, for all of us, where we have to just trust that the package isn't backdoor'd.

+1

> **JKyleOKC said:**
> The same heads-up attitude required to pilot an  airplane or to handle a car in NASCAR competition is necessary!

+++1

...not to mention that their helmets have insanely effective tin foil.

---

