---
title: "Proposal: Ubuntu remixes worth making"
date: 2009-07-14
forum: The Cafe
---

### Post by aysiu on 2009-07-14
I don't want to get into debates about whether Ubuntu remixes that switch around the wallpaper and a couple of installed packages are "worth" making or not. That's not what this is about.

You know how most new Ubuntu users do not buy Ubuntu preinstalled, so they end up having to install and configure Ubuntu themselves? Sometimes, they can be extremely lucky and have everything work out of the box. Other times, they can be extremely *un*lucky and have four or five things not working. Usually, I think, it's something in between (most stuff working, one or two things require tweaking).

What if some of the Ubuntu veterans made Ubuntu remixes for their specific hardware configurations. Obviously, this wouldn't work for custom-built desktops, but it might be particularly useful for netbooks and laptops.

I created a Ubuntu HP Mini Remix for the HP Mini 1120nr, and a bunch of HP Mini owners found it very useful, as they didn't have to do any complicated configuration file editing or source recompiling. Everything just worked out-of-the-box.

EeeBuntu is a remix specifically for Eee PCs.

Anyone else want to step up and offer a remix to the community for a particular laptop or netbook model?

Sure, the ultimate goal is for the Ubuntu and upstream developers to have everything work out of the box (with no regressions) on all hardware configurations, but this is something we non-programmers can do in the meantime.

And, really, you do not have to be a programmer or anything even close in order to make a remix. Step-by-step instructions (with screenshots) here:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Bottom line: you set up Ubuntu exactly as you want it, copy the relevant user settings to /etc/skel, install and run Remastersys, then upload or seed your .iso for the community.

What do you all think about this idea? Anyone willing to step up?

---

### Post by hellion0 on 2009-07-14
After tweaking the Jaunty install on my old Thinkpad today, I've actually contemplated wrapping my version up as a remix. I've gone into the configs and fixed up some problems that preinstalled Ubuntu has with the hardware (cs4236 ring a bell?) and stripped it down to the bone for the sake of speed. It's not just newer laptops and netbooks that can benefit - older hardware needs the love as well.

Maybe I'll toss together a "U-Minimal 600" remix or something one of these days.

---

### Post by hanzomon4 on 2009-07-14
Was planning on doing this with my mac... most things work great, but the track pad, keyboard backlight, and um.. (is that it?) requires tweaking for perfection.

---

### Post by Yownanymous on 2009-07-14
I think LXDE should have a remix, it's really growing into a handy replacement for the outdated XFCE.

----------------
Now playing: [The Who - Join Togethr](http://www.foxytunes.com/artist/the+who/track/join+togethr)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by Warpnow on 2009-07-14
I use a remix called Kuki linux for the Acer Aspire One. Its a very complicated remix, though, from a minimal install.

[www.kuki.me](www.kuki.me)

---

### Post by tgalati4 on 2009-07-14
Excellent idea.  There should be a catalog system to drill down by manufacturer and model.  Thinkpads have their own website but no respins the last time I checked.

Redristribution of codecs and firmware may be problematic.

---

### Post by JordyD on 2009-07-14
> **Yownanymous said:**
> I think LXDE should have a remix, it's really growing into a handy replacement for the outdated XFCE

Dated XFCE? Disagree!
Remix for LXDE I can see,
but the other DE must still be.

Sorry, I saw a rhyme, although poor, and I had to carry it out.

---

### Post by aysiu on 2009-07-14
> **tgalati4 said:**
> 
Redristribution of codecs and firmware may be problematic. In theory, the non-redistributable codecs would be left out, and it would mainly be a remix for hardware compatibility. Or did you tink it's problematic because proprietary "blobs"? Does Nvidia actually not allow you to redistribute its drivers along with a distribution? I'd always thought certain drivers and firmware were left out because they were closed source and not because they were illegal to redistribute.

In general I believe we should follow the law, but...

1. Laws vary from country to country, and since these remixes would be a community effort and not official Ubuntu releases of any kind, it would be very easy to make sure the remix is legal in the host country and then leave the onus on the user to decide whether it would be legal in her country as well before downloading the remix.

Many codecs are left out of Ubuntu for ideological and not legal reasons, though.

2. Law is constantly up for debate and reinterpretation. It's kind of hard to say what exactly is legal or illegal until it has been challenged and then upheld or overturned by a court of law in at least one country. Since there have not been any court cases on Linux distros or remixes prepackaging codecs, we can only speculate as to what is probably legal or illegal and in which countries.

3. Frankly, from a strictly pragmatic perspective, the media attention from a court battle would be a big win for Linux if a company were to challenge the right of individuals to redistribute codecs in a remix. I don't fully subscribe to the idea of "Any publicity is good publicity" but there is some truth in it.

---

### Post by Grant A. on 2009-07-14
> **aysiu said:**
> 
2. Law is constantly up for debate and reinterpretation. It's kind of hard to say what exactly is legal or illegal until it has been challenged and then upheld or overturned by a court of law in at least one country. Since there have not been any court cases on Linux distros or remixes prepackaging codecs, we can only speculate as to what is probably legal or illegal and in which countries.


You bring up an interesting point. I'm not a lawyer, but I wonder if the codec patents really have a leg to stand on here in the United States, because of the In re Bilski case requiring a patent to be tied to a specific machine.

> 
3. Frankly, from a strictly pragmatic perspective, the media attention from a court battle would be a big win for Linux if a company were to challenge the right of individuals to redistribute codecs in a remix. I don't fully subscribe to the idea of "Any publicity is good publicity" but there is some truth in it.

Because of the RIAA court cases, a lot of people in the United States equate that if something is free on the Internet, then it is illegal. A court case could only bring this more so towards Linux.

---

### Post by Dougie187 on 2009-07-14
I think it's a decent idea, but I think it would get to the point that it would be a daunting task to find your applicable remix.

I mean, would you have a remix for a manufacturer? or for each model? and then in each model for each configuration that requires a change? So how far do these remixes go?

Would you try to maintain one remix for all thinkpads, or one for each model? or one for each model and configuration, ie. T61, T61 - Nvidia, T41... etc?

Otherwise it's a great idea. Though I think if you wanted to do the model and configuration thing, it would be a better idea to write setup-scripts that the user could run once they install ubuntu, and then it would take care of all they needed.

---

### Post by forrestcupp on 2009-07-14
Great idea.  Even if it is impossible to create one for everyone, it would be good to have some for the most popular netbooks, etc.

Now we just need to find someone to host them all for free.

---

### Post by jonian_g on 2009-07-14
Good idea. I can make one for eeepc 701 and one for think-pad z61m.
Also there should be versions only for the note/netbooks that don't work out of the box. I mean, don't get too exited and make a re-spin for every note/netbook on the market.

> **forrestcupp said:**
> Great idea.  Even if it is impossible to create one for everyone, it would be good to have some for the most popular netbooks, etc.

Now we just need to find someone to host them all for free.

Or we can use torrents. A website can point to the torrents.
Or dropbox (can be done? I haven't used it).

---

### Post by Pogeymanz on 2009-07-14
I don't think that we really need all these remixes. Why can't we just help improve regular K/X/L/Ubuntu to work better on Thinkpads and Macbooks and whatever?

I think that there should be 5-6 mixes of Ubuntu:
Ubuntu
Kubuntu
Xubuntu (although it still sucks in its current form)
Lubuntu (LXDE)
Eeebuntu
and maybe a smart-phone Ubuntu, or something.


Actually, I often finding myself thinking that there should only be one Ubuntu, to save Canonical money.

---

### Post by aysiu on 2009-07-14
> **Pogeymanz said:**
> I don't think that we really need all these remixes. Why can't we just help improve regular K/X/L/Ubuntu to work better on Thinkpads and Macbooks and whatever? Well, a few reasons:

1. We're not all programmers
2. Some proprietary stuff Ubuntu does not want to include by default
3. Some tweaks to get things working in one setup would not make sense to be in other setups. They are messy workarounds that are fine for particular situations but wouldn't be appropriate in a general distribution that is supposed to work on all hardware.

It's not as if the bugs weren't filed in time.

And it's not as if the people making remixes are Ubuntu developers. As a Ubuntu user, I can spend a few hours making a remix. As a non-programmer, I cannot spend a few hours patching upstream code.

So in answer to your question, "we" cannot help improve Ubuntu for these netbooks and laptops because "we" are not all programmers. If you know how to make patches to send upstream and triage and offer fixes for bugs, then go for it. I don't. The most I can offer now is a remix.

---

### Post by NightwishFan on 2009-07-14
More than say a light 'remix' using something like ICEWM, I would prefer if there were packages that set up a lightweight system. Such as 'Ubuntu-Standard-Legacy' packages. The Ubuntu standard metapackage sets up a full featured command line system, perhaps the lightweight one would link to a modified kernel and software selection patched for systems under 128mb of RAM.

If that is a bit hard to understand, I am saying that XFCE, although light, is still using the standard Ubuntu base, which even without a graphical desktop is still probably too heavy for 128mb of ram. Perhaps a patched or legacy kernel could be made specifically available for older systems. Similar to Puppy Linux, perhaps.

Edit: More relevant:

As for specific system images, such as getting the macbook to work, I would stress the most importance is compliance with the Ubuntu-Desktop metapackage, and a changelog. This is so that the user experience would not be much different, and the changes in the image from the standard desktop would be apparent.

---

### Post by aysiu on 2009-07-14
> **NightwishFan said:**
> 
Edit: More relevant:

As for specific system images, such as getting the macbook to work, I would stress the most importance is compliance with the Ubuntu-Desktop metapackage, and a changelog. This is so that the user experience would not be much different, and the changes in the image from the standard desktop would be apparent. That would be a great refinement eventually.

A first step would just be simple hardware functionality (mouse acceleration and multi-touch, F-keys, etc.).

---

### Post by koenn on 2009-07-14
sounds like a good idea. I'd probably do it but all i have around here is no-brand PC's with components from all over the place, pretty old, and a default ubuntu runs on it without any tweaking. Not much to do then.

hosting could be a problem. You don't want users to go search all over the web for a download that might match there system. too 'warez'-like. 

What if some character, the same type of character that would post malicious commands on a newbie support forum, starts offering doctored, backdoored and zombified remixes for popular models ? 

And I do think potentially illegal redistribution of certain software needs some extra attention. Ubuntu excludes some stuff for philosophical reasons, and some stuff for legal reasons. The  philosophical objections can wave aside, but you'll have to be clear on the legal stuff, for the redistributors as well as for the downloaders, especially if this catches on and becomes big.

---

### Post by aysiu on 2009-07-14
> **koenn said:**
> 
hosting could be a problem. You don't want users to go search all over the web for a download that might match there system. too 'warez'-like. 

What if some character, the same type of character that would post malicious commands on a newbie support forum, starts offering doctored, backdoored and zombified remixes for popular models ?  I guess we'd have a Wiki with links to torrent files people would have to seed.

> And I do think potentially illegal redistribution of certain software needs some extra attention. Ubuntu excludes some stuff for philosophical reasons, and some stuff for legal reasons. The  philosophical objections can wave aside, but you'll have to be clear on the legal stuff, for the redistributors as well as for the downloaders, especially if this catches on and becomes big. Yeah. I'd love to get some clear messages, though, about what exactly is legal and illegal to distribute and in which jurisdictions. The warnings Ubuntu itself gives when you install nonfree stuff is pretty vague.

---

### Post by Dougie187 on 2009-07-14
Are these legal issues only with respect to restricted drivers?

Also, I don't know but the more I think of it, I don't think this project needs to be this large. I really think you could do it with just a couple of setup scripts.

And this would be a lot more feasible when it comes to one for every configuration.

This way you wouldn't need hosting too. Also, for these new ubuntu users, where would you have a list of the remixes that would be easy to find? Is this something that would be listed on the home page or what? Because it has to be like "Hey, instead of downloading ubuntu, just download the remix for your hardware."

Also, I think these would be easier to maintain than a large group of remixes.

---

### Post by aysiu on 2009-07-14
> **Dougie187 said:**
> 
Also, I don't know but the more I think of it, I don't think this project needs to be this large. I really think you could do it with just a couple of setup scripts. I can't speak for other people's situations, but the HP Mini tweaks could not be done with a setup script. First of all, I can't find where the ALSA *user* settings exist as a text file. More importantly, to get sound working, after you recompile ALSA, you have to reboot the computer, and then do more tweaks. How does that work with a script?

Frankly, I don't consider remixes to be "this large." It's less work for me to configure it myself and then run Remastersys, **a fully point-and-click program**, than it is to figure out how to write a script and then give people instructions for how to run it.

I consider remixes to be "this small" and scripts to be "this large."

---

### Post by Dougie187 on 2009-07-14
> **aysiu said:**
> Frankly, I don't consider remixes to be "this large." It's less work for me to configure it myself and then run Remastersys, **a fully point-and-click program**, than it is to figure out how to write a script and then give people instructions for how to run it.

I consider remixes to be "this small" and scripts to be "this large."

I guess I am thinking of the largest scope. Because I don't fully understand the proposed scope. I was thinking in the sense, of every model (since models can have varying levels of configuration needed).

I have never had to do that much tweaking on a system before, however aren't the alsa user settings in .asoundrc? At least, this is what I would assume you are talking about.

[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

As far as I know, everything can be found in a text file somewhere. Also, To have it recompile alsa, then reboot and start another script, couldn't you just have it submit a cron job for when the computer finished rebooting?

I was just thinking of it in the sense, that you would have multiple remixes (one per model) that would also need to change or be updated every time a new version of ubuntu came out. And I was thinking this would be a very large project to try to coordinate. Also, you would have to make sure everyone of these remixes had someone seeding it, and if there were a lot of remixes then that could be a difficult task to. On top of not being completely useful because some of the remixes might never get used.

Either way, this is just my opinion, and how I was seeing things. I may have misunderstood your intentions, or the scope, and if so please correct me.

---

### Post by aysiu on 2009-07-14
> **Dougie187 said:**
> I guess I am thinking of the largest scope. Because I don't fully understand the proposed scope. I was thinking in the sense, of every model (since models can have varying levels of configuration needed). It wouldn't be the job of one person or even a team of people to do every model. Each person would be responsible for only the model she uses. So I use an HP Mini 1120nr and make a remix for that. That's it. Someone else uses a unibody Macbook Pro and makes a remix for that. Another person uses an Acer Aspire One and makes a remix for that.

Each person is responsible for a remix only for her particular hardware setup.

> I have never had to do that much tweaking on a system before, however aren't the alsa user settings in .asoundrc? At least, this is what I would assume you are talking about.

[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc) No. That's what I read every time I did a Google search for where they live, but I don't have that file in my home folder after showing hidden files.

> As far as I know, everything can be found in a text file somewhere. Again, that's what I've generally found to be the case, but not in this particular instance. > Also, To have it recompile alsa, then reboot and start another script, couldn't you just have it submit a cron job for when the computer finished rebooting? Sounds complicated. Why not just make a remix? Less work for me. Less work for the user downloading it.

> I was just thinking of it in the sense, that you would have multiple remixes (one per model) that would also need to change or be updated every time a new version of ubuntu came out. Well, the hope is that Ubuntu developers are actually working on our bug reports and creating permanent fixes for future versions. I hope ALSA and Network Manager aren't going to always be broken in Karmic and beyond. > And I was thinking this would be a very large project to try to coordinate. So would, by the same assumptions, creating a new script with every release. > Also, you would have to make sure everyone of these remixes had someone seeding it, and if there were a lot of remixes then that could be a difficult task to. Only the people with that hardware would seed, because only those people would care about it. A Sony Vaio owner probably wouldn't be seeding for a Dell Vostro remix. > On top of not being completely useful because some of the remixes might never get used. Of course they'd be used. If you could download regular Ubuntu that required all sorts of weird workarounds to get functioning on your laptop or if you could download a remix that works out of the box on your laptop, which would you download?

---

### Post by DeadSuperHero on 2009-07-14
I want to create a distro based on Ubuntu with mostly mono-based apps replacing the current ones. I think it'd be a hot piece of legal flamebait.

---

### Post by hellion0 on 2009-07-15
> **Dougie187 said:**
> I think it's a decent idea, but I think it would get to the point that it would be a daunting task to find your applicable remix.

I mean, would you have a remix for a manufacturer? or for each model? and then in each model for each configuration that requires a change? So how far do these remixes go?

Would you try to maintain one remix for all thinkpads, or one for each model? or one for each model and configuration, ie. T61, T61 - Nvidia, T41... etc?
In my case, it would be specifically for the Thinkpad 600. Considering how much of a PITA it is to get things like the sound and PCMCIA slots working after a "base" install of just about every distro, it'd be worth it if I could use my already-configured, everything works install to save even one user all those hours.

---

### Post by HappinessNow on 2009-07-15
Do people issue  remixes of Firefox on a regular basis?

Are there a couple of hundred Firefox remixes available (beyond the few re-branded browsers)?

How about just packages that load themes and special functions instead.

---

### Post by forrestcupp on 2009-07-15
> **&#20170 said:**
> Do people issue  remixes of Firefox on a regular basis?

Are there a couple of hundred Firefox remixes available (beyond the few re-branded browsers)?

How about just packages that load themes and special functions instead.

Are you really comparing Firefox to a whole OS?  Firefox doesn't need to deal with things on the hardware level, so it would be silly to think there is a need for something like that.

But nevertheless, there *are* several remixes of Firefox.  A couple of examples are Swiftweasel and Swiftfox, and those aren't the only ones.  They are compiled to run better on certain processors.

Really, what's the harm in people making remixes that are specific to a few popular systems?  If you don't need them, just don't bother yourself with them.

---

### Post by aysiu on 2009-07-15
> **&#20170 said:**
> 
How about just packages that load themes and special functions instead. I don't see how themes are relevant here. We're talking about hardware support.

And in terms of packages for special functions, it is **easier** to just make a remix with Remastersys than to create .deb packages for fixes and workarounds for outstanding bugs.

---

### Post by Dougie187 on 2009-07-15
> **aysiu said:**
> Of course they'd be used. If you could download regular Ubuntu that required all sorts of weird workarounds to get functioning on your laptop or if you could download a remix that works out of the box on your laptop, which would you download?

Well, I think this depends on how accessible the remixes are. I mean if they are listed on the ubuntu download page, then I might take the time to see if my hardware has a remix. But in general I would usually just download the base ubuntu and do the fixes myself. That way I know what I have to do to fix it or what to look at if it breaks. Also, if I care enough, I could potentially look into fixing it. Now, I understand this is not the mentality of everyone, and there are some users who just want their computer to work perfectly from the beginning and not have to mess with anything. And I respect that and think this is a good idea to solve that problem.

So basically, you would only have remixes for the models that have serious tweaks needed to fix vital aspects of the computer after installation. The only reason I was thinking it would take more to keep remixes current than it would take to keep scripts current, is that scripts can be modified very easily, you just have to change the text to do the new fixes, and re-upload the scripts. Whereas with a remix, you would have to install a base image, do your fixes, then use remastersys to create a remix, and then seed your image. Now I haven't used remastersys before, so I don't know if you have to reinstall after you make your remix or not.

Either way, I think it is a good idea. and if you can get the people to support the project as far as making/maintaining/seeding remixes, then it should be useful for a lot of people. I think the making part is going to be the easiest of those three.

---

### Post by aysiu on 2009-07-15
> **Dougie187 said:**
> Well, I think this depends on how accessible the remixes are. I mean if they are listed on the ubuntu download page, then I might take the time to see if my hardware has a remix. But in general I would usually just download the base ubuntu and do the fixes myself. That way I know what I have to do to fix it or what to look at if it breaks. Also, if I care enough, I could potentially look into fixing it. Now, I understand this is not the mentality of everyone, and there are some users who just want their computer to work perfectly from the beginning and not have to mess with anything. And I respect that and think this is a good idea to solve that problem. And my point wasn't that *every* user would use her hardware-specific remix but that remixes would be used. If only one other person uses my HP Mini Remix, I'm happy. I don't financially profit from it, but I've gotten several comments from grateful HP Mini Remix users, and it's nice to know that someone benefited from my little fixes and didn't have to futz around with them herself.

> So basically, you would only have remixes for the models that have serious tweaks needed to fix vital aspects of the computer after installation. Naturally. If everything really works out of the box, what's the point of the remix? I'm talking specifically about hardware fixes, not default software packages or theming. > The only reason I was thinking it would take more to keep remixes current than it would take to keep scripts current, is that scripts can be modified very easily, you just have to change the text to do the new fixes, and re-upload the scripts. Whereas with a remix, you would have to install a base image, do your fixes, then use remastersys to create a remix, and then seed your image. Now I haven't used remastersys before, so I don't know if you have to reinstall after you make your remix or not. No, with a remix, you do not have to keep reinstalling to keep the image up-to-date. If there's a problem, you fix the problem and just run Remastersys again and the .iso is re-created.

Sure, it takes up a lot more bandwidth than a script does (.iso, several hundred megabytes; script, maybe one hundred kilobytes at the most), but a script takes more work to produce well, and there's more room for user error in running it.

Also, presumably a new user would have to download an .iso to begin with anyway... so it's just a matter of making sure she downloads the correct .iso.

I have had HP Mini Remix users say to me that they've tried doing the fixes themselves and been unsuccessful, so they were happy to *redownload* an entire 630 MB .iso and do a clean reinstall just to have things working.

... but ...

Just so I'm understood, I'm not going to discourage anyone's efforts. If someone has the programming knowledge to write a "get everything working in a Macbook" script and *actually* writes it, I'm not going to say "Don't write that script. Throw away the script. Make a remix instead."

What I am saying, though, is "Hey, if you've done fixes on your own hardware model and want to save others (perhaps less experienced) the trouble of doing those same fixes, consider using a simple point-and-click tool like Remastersys to make a remix and share it with other people."

And the best thing is that you do not need to be a programmer to do it.

---

### Post by forrestcupp on 2009-07-15
> **aysiu said:**
> 
Just so I'm understood, I'm not going to discourage anyone's efforts. If someone has the programming knowledge to write a "get everything working in a Macbook" script and *actually* writes it, I'm not going to say "Don't write that script. Throw away the script. Make a remix instead."

Scripts would be a good option, but the problem I see with scripts is that you have to have a working install to even run one.  Also, you have to know how to make it executable and run it.

On the other hand, with a remix, you don't have to worry about any of that.  Just install it and it works, thanks to someone else who did all the setting up for you.

And I keep wondering, what's the harm in people making remixes?  There's certainly not anything negative enough about it to bother arguing against it.

---

### Post by Erik Trybom on 2009-07-15
I think it's a great idea. 

This way we could compete with Apple in the "just works" section. Apple's main advantage is that they only have to test their software and drivers on Macs, which means a very limited set of hardware configurations. It should be a lot easier delivering 100% working stuff (drivers, resolution, sound, mice/keyboards etc) if you can tailor it to a specific hardware setup.

One question though - if this idea is implemented and gets a torrent website, do we have any quality check or can anyone upload his/her own remix? Do we allow several remixes for each computer model?

---

### Post by aysiu on 2009-07-15
> **Erik Trybom said:**
> 
One question though - if this idea is implemented and gets a torrent website, do we have any quality check or can anyone upload his/her own remix? Do we allow several remixes for each computer model?
In the ideal world you would click on your hardware configuration and then get a list of remixes with various ratings attached to them based on user experience (Who has the best tweaks? If the default packages and theming *have* been changed, which is the most user-preferred change?).

Realistically, that is a problem that's way down the line. Right now, we just need people to make remixes. If we can get at least four remixes, I think that's worth starting a Wiki page for, and then we can go from there.

It would be important to distinguish hardware-focused remixes from other remixes (remixes with different default packages, different artwork, or some kind of religious or political theme).

---

### Post by djmh on 2009-07-15
well, ill upload my dell mini 9's netbook remix .
its not really changed much at all,just added some cloud apps to favorites, and set chrome to start on boot.

i was aiming at making it a cloud os.

so i dunno if anyone will like it, but ill still do it.

by the way, i have everything working on my mini 9(so this could be a good mini 9 remix), the biggest fix being a fix for a bug that really had me mixed up ( panels wouldn't load and just a whole bunch of problems) i didn't make the fix of course ...but it was slightly difficult to find...especially with my system screwed up.

---

### Post by djmh on 2009-07-15
on second thought, would my upload be something you would be looking for ?

---

### Post by aesis05401 on 2009-07-15
This is a really nice idea from the community standpoint, but the security side of implementing a system like this would be a nightmare.  

One of the Ubuntu selling points is 'sane defaults.'  This is not the case in the more bare-metal Linux circles, and that means security vulns for uneducated users - and I am not talking user-space spambot-virii - I am talking ring0.

So how would these remixes be vetted?  I don't see a way to catch malicious configs in a distribution scenario like this.

Any ideas?

---

### Post by aysiu on 2009-07-15
> **aesis05401 said:**
> This is a really nice idea from the community standpoint, but the security side of implementing a system like this would be a nightmare.  

One of the Ubuntu selling points is 'sane defaults.'  This is not the case in the more bare-metal Linux circles, and that means security vulns for uneducated users - and I am not talking user-space spambot-virii - I am talking ring0.

So how would these remixes be vetted?  I don't see a way to catch malicious configs in a distribution scenario like this.

Any ideas? Are you talking about malicious parties constructing remixes with malware purposefully installed? Or do you mean people might be employing what they consider good fixes but that really open up some security holes they themselves are not aware of?

The first I don't really consider a legitimate concern. If someone is an established forum member and creates a remix, it probably will not contain deliberate malware. I don't know who vets Crunchbang, Eeebuntu, Ubuntu Christian Edition, Ubuntu Buddhist Edition, or any of the other remixes. Is there anyone (besides the maintainers) who actually audits every config file and service in those remixes?

That's one of those things that's theoretically possible but currently improbable (maybe in the near future it may be more of an issue).

The second is far more probable, for example, if someone installs an OpenSSH server and activates other services without locking that stuff down or mentioning it on the remix webpage.

In the end, the idea behind these remixes is that it's a lot easier for someone to remove packages, add packages, change themes, configure the firewall, etc. than to do custom fixes and workarounds for hardware issues (regressions, incompatbilities).

> **djmh said:**
> well, ill upload my dell mini 9's netbook remix .
its not really changed much at all,just added some cloud apps to favorites, and set chrome to start on boot.

i was aiming at making it a cloud os.

so i dunno if anyone will like it, but ill still do it.

by the way, i have everything working on my mini 9(so this could be a good mini 9 remix), the biggest fix being a fix for a bug that really had me mixed up ( panels wouldn't load and just a whole bunch of problems) i didn't make the fix of course ...but it was slightly difficult to find...especially with my system screwed up.

> **djmh said:**
> on second thought, would my upload be something you would be looking for ? The bit about cloud apps and Chrome... not really?

If there really is a bug with panels not loading, and you fixed that... then, yes.

---

### Post by aesis05401 on 2009-07-15
> **aysiu said:**
> Are you talking about malicious parties constructing remixes with malware purposefully installed? Or do you mean people might be employing what they consider good fixes but that really open up some security holes they themselves are not aware of? ...*snip*

How about both?  You raise good points about the currently existing remix communities.  So on that note, what would I consider a sign of quality in a remix?

I would be willing to install and evaluate a remix that is supported by an active community, but I would want some sort of established track record to evaluate before installing.  

If a remix was recommended by an established community figure or was adopted by any sort of large organization for everyday use I would consider installing it.  Other than that, I would need to see dedicated forums with a diverse user base for each remix I wanted to evaluate - because that is what I get from my fully modifiable install of Ubuntu standard.  

So there is more effort in choosing a remix.  Currently I use forums like these to find instructions for making the changes myself to an officially vetted base install.  After my research is complete I know how to reverse whatever I have done to my system which seems just as important as knowing how to do it in the first place.

Maybe Canonical would be interested in hosting images of the standard install configured just for large vendor hardware profiles similar to the way VMWare puts out their appliance images.  That would be really nice.

Unfortunately, the security point is still scary when we apply the ideas of vulns through ignorance or malice to a large-scale community effort to boost remix usage.

Case in point: If I remixed the heavily modified system this post is being typed on I wouldn't feel safe passing it on to another user simply because I know how much time it took me to get comfortable with the modifications.  

I have virtch'd networking interfaces, locked down LAN services, custom filtering rules as a safety net in case I screwed up on either of the previous two, etc... and I had to read docs in depth for all those things just to get my own rudimentary knowledge.

The ignorance that leads to a problem could have been on my part, the person who downloaded my image without reading my docs, or simply in the fact that my remix may be implemented in a way that upstream patches don't actually fix newly discovered vulns on downstream remixes (ie: the remixer has to do anything statically to preserve functionality for legacy hardware or some other reason).

I hope you don't find this post overly negative.  I would love to see remixes traded like mix-tapes were back in the eighties, and this seems like a productive conversation.

---

### Post by djmh on 2009-07-15
> The bit about cloud apps and Chrome... not really?

If there really is a bug with panels not loading, and you fixed that... then, yes.

[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)

that is the bug, i found the fix..its actually on these boards...and its not really hard to do, its just a few lines of code.
but when you have no panels,and a bunch of other things missing it is slightly difficult to do.

the other thing i found a fix for is when saving websites to your favorites, it does not display an icon for your site...which is barely even an inconvenience...but having the icons just pulls it together a bit more ya know ?
all that was needed for that was to make the folder in the proper directory.

both of those fixes were not discovered or made by me...i just merely searched around and experimented with fixes until i found ones that worked.

---

### Post by wirepuller134 on 2009-07-15
aysiu, I would be more than willing to contribute storage space and bandwidth for downloading the remixes if needed.  Just email me if interested and I can set it up.

---

### Post by aysiu on 2009-07-16
> **wirepuller134 said:**
> aysiu, I would be more than willing to contribute storage space and bandwidth for downloading the remixes if needed.  Just email me if interested and I can set it up.
Thanks. That's great.

---

### Post by Grant A. on 2009-07-16
> **wirepuller134 said:**
> aysiu, I would be more than willing to contribute storage space and bandwidth for downloading the remixes if needed.  Just email me if interested and I can set it up.

No offense, but I would feel much better about downloading something from a well-known source, such as Canonical.

I'm sure that you're a great guy who means no harm, but you just never know these days. :-(

Perhaps using Windows for the majority of my life has just made me overly-paranoid.

------

About this idea: I would much prefer that someone puts up shell scripts that add/remove software. It would take up much less space on a server, and would be much safer security-wise, because you have a chance to audit it before you use it.

---

### Post by Riffer on 2009-07-16
I can definitely see a need for some sort of support for problem installs.  And while remixes could be a great solution, I wonder if the traditional method would be better.  That is to write a HOWTO for your particular hardware setup.

I can see a special folder being setup where people can post their HOWTO.  It would make it easier to find then doing a search of the whole forum and several posts to find that info you want/need.  

Just a thought

---

### Post by koenn on 2009-07-16
well, you can do both.

If the remastered isos are made available through links in a wiki, all it takes is that the people who made the remastered iso document their changes and the way they went about it in that same wiki ; users then have the choice between just downloading and running the iso, or try to implement the changes themselves. 

Documenting the remastered stuff would be a good idea anyway : it gives the prospective user an idea of what he's getting in to, like how close or how far that remastered system is to a default install, it would  show what additional software has been added and one would be able to check the licenses involved, it would allow people to comment (suggesting better ways to solve the same problem, point out possible problems that may result from the way the system was modified, ... à

---

### Post by Riffer on 2009-07-16
Good Point

---

### Post by aesis05401 on 2009-07-16
> **koenn said:**
> well, you can do both.

If the remastered isos are made available through links in a wiki, all it takes is that the people who made the remastered iso document their changes and the way they went about it in that same wiki ; users then have the choice between just downloading and running the iso, or try to implement the changes themselves. 

Documenting the remastered stuff would be a good idea anyway : it gives the prospective user an idea of what he's getting in to, like how close or how far that remastered system is to a default install, it would  show what additional software has been added and one would be able to check the licenses involved, it would allow people to comment (suggesting better ways to solve the same problem, point out possible problems that may result from the way the system was modified, ... à

OK.  If the community established an index through a wiki or other means to track remixes then they could also set a loose standard of documentation for remixes that want to be listed on the site.

If we made the standard documentation take the form of a commented script that could transform a base install step by step into the remix-config this would cover all my concerns.  And it sounds like a good idea.

It also sounds like users would be more likely to run the scripts than download an entire .iso, but that would be up to each user, and I like encouraging freedom.

At the very least, this would serve as a great repo for nuts and bolts knowledge related to customizing your own install, and I would probably spend more time browsing there than in the forums for my solutions.

So how real is the possibility of a group forming to congeal a game-plan?

---

### Post by aysiu on 2009-07-16
I don't think it has to be a group.

It's just a collection of individuals.

If you as an individual have a hardware setup that doesn't work with Ubuntu out of the box, you can create your own remix and/or script and just put it on the Wiki.

I don't like the idea of mandating a script, though, as not everyone who can make a remix can also make a script (I, for example, would not be able to make a script for my HP Mini Remix).

---

### Post by aesis05401 on 2009-07-16
aysiu,

Do you think documentation should accompany the remixes?  

Maybe one issue that comes into play is the variety of reasons an individual might make a remix.  I agree with you that a solution that only modifies the base install to achieve operation on certain hardware would be very useful to a wide range of people - and shouldn't require a whole lot of doc work.

Using the remix wiki as a resource to answer the multi-nic, hardware specific setup questions would(should?) require a greater level of documentation, right?  Just the volume of wireless adapter questions, general multi-nic operation, and specific wireless AP/LAN bridging questions would predict a huge market for networking specific remixes.

This is a different beast documentation wise, right?  Maybe the wiki would need to be restrictive for a while to see how things shake out - just host basic hardware compat mixes.

I guess the bright side is that people would want to use the wiki for all sorts of things - because people are using Linux for all sorts of crazy things and this community likes to share ;)  That is where I see the problem coming in.  

If this idea gets off the ground I will try to find time to put together a sample script for my host networking setup/and and associated sample remix.  Might be a little time, though, because I would need to research a bunch of incremental changes I have made over time.

---

### Post by aysiu on 2009-07-16
I've create a Wiki page for it:
[https://help.ubuntu.com/community/HardwareCompatibilityRemixes](https://help.ubuntu.com/community/HardwareCompatibilityRemixes)

---

### Post by aesis05401 on 2009-07-16
> **aysiu said:**
> I've create a Wiki page for it:
[https://help.ubuntu.com/community/HardwareCompatibilityRemixes](https://help.ubuntu.com/community/HardwareCompatibilityRemixes)

Bookmarked.  I'll look at this over the weekend.   Thank you.

---

### Post by koenn on 2009-07-16
> **aysiu said:**
> I've create a Wiki page for it:
[https://help.ubuntu.com/community/HardwareCompatibilityRemixes](https://help.ubuntu.com/community/HardwareCompatibilityRemixes)

Looking good. I almost wish I had a not entirely ubuntu compatible laptop, just to be able to post a remix. :)

I'm not to sure about this part:
> and sometimes it's because there are accidental regressions in the Linux kernel making something no longer work that had worked before.
I always thought these regressions were in ubuntu's modyfing, compiling and packaging of upstream code rather than in the kernel.

---

### Post by aysiu on 2009-07-16
> **koenn said:**
> Looking good. I almost wish I had a not entirely ubuntu compatible laptop, just to be able to post a remix. :) Well, up until this point, I've had pretty good hardware for Ubuntu compatibility. Now, ironically, with Ubuntu preinstalled (well, the specially tweaked HP version of Ubuntu), I have something that definitely needs a remix, at least for 9.04.

> I'm not to sure about this part:

I always thought these regressions were in ubuntu's modyfing, compiling and packaging of upstream code rather than in the kernel. Well, if you're pretty confident in that, feel free to correct the statement. It is a wiki, after all.

---

### Post by aesis05401 on 2009-07-16
> **koenn said:**
> I always thought these regressions were in ubuntu's modyfing, compiling and packaging of upstream code rather than in the kernel.

There are some contentious policies in place to prevent kernel regressions, but they do occur. 

One of these policies is the no pure refactoring policy.  While it sounds like the only way to manage a FOSS project as massive as the kernel, there are a lot of developers who get noisy about it. 

A recent minor issue in test kernels had to do with the modification of the I/O calls to deal with low latency storage devices.  So they do happen.

Should the statement just be made a little more vague?

Nice page, btw.  Alright, now I really have to get back to work ;)

---

### Post by koenn on 2009-07-16
> **aesis05401 said:**
>  
Should the statement just be made a little more vague?

I already did that.

---

### Post by benj1 on 2009-07-16
has any thought been given to maintaining these remixes? both for new installers and existing users, could a PPA be used?


also given that the remixes are going to be almost exactly the same as standard ubuntu would not be possible to combine them with the standard ubuntu iso and have an option at installation to choose a remix, so if for example you choose the dell mini 9 as your computer, it will make the required changes and proprietary drivers etc could be handled the same way as nvida and ati drivers (a notice popping up telling you they are available) with a slightly modified repository for updates etc?
im not sure about space on a cd, would that be an issue?

---

### Post by aysiu on 2009-07-16
> **benj1 said:**
> has any thought been given to maintaining these remixes? both for new installers and existing users, could a PPA be used?


also given that the remixes are going to be almost exactly the same as standard ubuntu would not be possible to combine them with the standard ubuntu iso and have an option at installation to choose a remix, so if for example you choose the dell mini 9 as your computer, it will make the required changes and proprietary drivers etc could be handled the same way as nvida and ati drivers (a notice popping up telling you they are available) with a slightly modified repository for updates etc?
im not sure about space on a cd, would that be an issue?
Part of the problem with this suggestion is that it goes against Ubuntu's development model.

Once Ubuntu has made an official release, it won't fix bugs for that release unless they are critical security flaws.

Also, a lot of times, bugs that have been identified have only workarounds and not official fixes available. A remix can employ a workaround, but the Ubuntu developers would want an official fix.

---

### Post by Twitch6000 on 2009-07-16
The only remix of ubuntu or any other distro for that matter I wanna see is a lxde and e17 version :D.

I have become a big fan of both lxde and e17.

---

### Post by aysiu on 2009-07-16
> **Twitch6000 said:**
> The only remix of ubuntu or any other distro for that matter I wanna see is a lxde and e17 version :D.

I have become a big fan of both lxde and e17.
Great. What does that have to do with this thread?

---

