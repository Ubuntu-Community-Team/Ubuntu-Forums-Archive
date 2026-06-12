---
title: "Automatix, Easy Ubuntu, or something else?"
date: 2007-03-30
forum: System76 Support
---

### Post by shaft350x on 2007-03-30
My wife's Darter just arrived today!  It's a sweet little machine.  It is her first experience with Linux and I want it to go as smoothly as possible for her.  So I was wondering if I should use Easy Ubuntu or Automatix to get all the codecs and DVD and Flash and stuff to work on her Darter.  I've used Automatix but I've seen Easy Ubuntu and it seems like it may be a bit more straight forward.

Just wondering what would be the suggested way to go about installing all this stuff.  Thanks a bunch!

---

### Post by Shay Stephens on 2007-03-30
I have been using automatix for a year now, and really enjoy it.  I have not tried easy ubuntu yet.  So I don't know anything about it.  But I have not gone wrong with automatix and keep using it.

---

### Post by Punker on 2007-03-30
nice sweet system I like this one more my price range [http://system76.com/index.php/cPath/1_10](http://system76.com/index.php/cPath/1_10)

but about automatix I learned the hard way this all I'm going to say

---

### Post by shaft350x on 2007-03-30
ok, I'll bite, what was the "hard way" about Automatix?

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

### Post by ScotchontheRocks on 2007-03-31
I just went with Automatix went I jumped feet-first into Linux. I've read about Easy Ubuntu thought that it wasn't worth switching for basically the same thing.

---

### Post by Shay Stephens on 2007-03-31
> **compiledkernel said:**
> Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

Why the apparent vendetta against automatix?  Did automatix kill the forums puppy or something?  Seems like many of the forum staff make a point of alluding to how "dangerous" automatix is, and yet, I have never had a problem with it.  Is this just a personal thing between ubuntuforums and automatix or something?  Bad blood somewhere along the line? :confused:

And where does that quote come from?  Is that some kind of official statement?  Who said that?  When?

---

### Post by compiledkernel on 2007-03-31
There are easier way to accomplish what you want than by using a script like A-X. A-X does a variety of unhappy things, depending on the version your using to your system. Bleeder (for those who actually risk using it) can cause Synaptic to break, and cause your system to break (based on the nature of the packages it installs). Outside of that A-X Depends on repositories of its own, aside from the official repositories. Automatix goes down, the application itself fails. A-X additionally does screw around with your sources.list , something that breaks the concept of a functioning system in some cases.

---

### Post by Shay Stephens on 2007-03-31
> **compiledkernel said:**
> There are easier way to accomplish what you want than by using a script like A-X. 

My question was a bit more involved than that.  Would you care to answer any of it?  I checked your profile and you have sent the same message over and over and over again.  One after the other after the other.  I don't understand it.  And besides, I have had ubuntu updates kill my machine more times than I am pleased with, automatix never.  Not saying it couldn't happen, all software is bound to break, but the focused attack on automatix is just kind of weird and doesn't feel right.  That is why I asked the specific questions I did.  I was hoping for more than a form letter response, if you will pardon the expression.

---

### Post by compiledkernel on 2007-04-01
Phew....ok....well here we go. I have no vendetta against A-X. I hate seeing requests for support of the application because its NOT SUPPORTED BY THESE FORUMS. Something that was decided some time ago. No puppy kililng here, merely that the application isnt supported here , not supported by the community and , even more clearly, only supported by its developers. 

I stand to logic that is that as Ubuntu progresses  that ease of use is becoming more and more apparent. The need for automatix becomes unnesseary. Fiesty in its beta form is a clear sign of this. The gstreamer-ugly package provide MP3 and other codec support. Flash is installed via the firefox automated system, and binary drivers exist on the repos that are fairly current. 

Gnome-app-install and synaptic both provide a much cleaner interface. The only reason that Automatix came into existence was because it installed stuff that wasnt easy to install or had no install candidate on the repos.

---

### Post by Shay Stephens on 2007-04-01
> **compiledkernel said:**
> Phew....ok....well here we go. I have no vendetta against A-X. I hate seeing requests for support of the application because its NOT SUPPORTED BY THESE FORUMS. Something that was decided some time ago. No puppy kililng here, merely that the application isnt supported here , not supported by the community and , even more clearly, only supported by its developers. 

I stand to logic that is that as Ubuntu progresses  that ease of use is becoming more and more apparent. The need for automatix becomes unnesseary. Fiesty in its beta form is a clear sign of this. The gstreamer-ugly package provide MP3 and other codec support. Flash is installed via the firefox automated system, and binary drivers exist on the repos that are fairly current. 

Gnome-app-install and synaptic both provide a much cleaner interface. The only reason that Automatix came into existence was because it installed stuff that wasnt easy to install or had no install candidate on the repos.

Yes, I am with you on one point, the need for automatix is dimishing, and I may not even use it for fiesty, as you mention.  However, who says that the community can't talk about it?  Why does any talk of automatix have to be hushed up and swept under the carpet?  It just comes across very odd and disingenuous.  If automatix becomes pointless, people will stop using it and it will die out naturally.  But to try and force it, well, like I said, it look suspicious.

I mean really, there are forums for nearly everything here, even Windows, and I have seen very little else if anything dealt with in the same manner as automatix.  You have to admit that it is treated like some ugly stepchild that keeps trying to peek out the air ducts only to get stuff thrown at it by the staff at every opportunity.  And so far, I have not heard a real reason why.

---

### Post by compiledkernel on 2007-04-01
enough of us , Shay, have experienced what it did in the  past.  There was at one time here a support forum for A-X on these very forums. I dont have an issue talking about it, or discussing it. I have an issue with users that come to these forums requesting help for a system thats broken during which time they Used A-X, expect us to diagnose their problem while they are using an application that ubuntu doesnt support, the community doesnt support, and most importantly, WE as a FORUM do not support. I have fixed my share of systems that were borked horribly by A-X installs. Im not saying that it borks all systems, but Ive seen enough of them to say in my own mind, that its not supported here. Its support for AMD64 is just utterly bad. Talk all you like , have at it. Ill even talk with you about it. 

Support it. No. They have their own forums, you take your issues there. Not here.

---

### Post by Shay Stephens on 2007-04-01
I can understand not wanting to support it, I totally understand that.  But you seem to be forum searching for any mention of automatix and form letter responding to it in ways that are not appropriate.  Look at your list of posts, I mean dang, that is close to all you do.  I think the one with the issues is you at this point (speculation).  

What I am beginning to realize is that maybe you should just let the talk about automatix happen naturally.  If you feel the need to respond to such posts or are under instructions to do so, simply point them to the automatix forum without resorting to the bashing, it doesn't come across as genuine and it is what caught my attention, especially coming from staff.  What problems automatix had in the past doesn't have a lot of weight today, just as the problems with the ubuntu updates and such are not a problem anymore, at least for me.  Let the past go, let automatix go.

I do appreciate you taking the time to respond and talk with me about it, thank you :-)

---

### Post by TravisNewman on 2007-04-01
If I could throw in an opinion here...
Around the time of Dapper, I was testing automatix and it caused at total system hose on me, and I reproduced the steps in a vmware image later to make sure it wasn't something else.

The problem becomes providing support for an operating system that automatix may or may not have been installed on. Since automatix pulls in things from different repositories than the official ones, problems that users come here with could be hard to diagnose if they don't provide the information that they HAVE used automatix (because why should they, it shouldn't cause any problems... that does make sense).

EasyUbuntu on the other hand gets things from Ubuntu's repositories, so this danger isn't applicable.

Personally, I would prefer users dive into Ubuntu head first and learn the ways of doing things using synaptic, or if needed, doing them manually. I know this isn't what everyone feels and that scripts such as a-x and easy ubuntu have filled a gap for many users, but learning the process of installing through synaptic, etc, gives more understanding about the system.

That said I know plenty of people who use A-x who are very skilled at Ubuntu and just use it out of convenience, so this rule doesn't always apply.

But no, nobody is suggesting that discussion of automatix stop. We're just suggesting that it may not be the best alternative due to the possibility of breakage, since it's using external repositories, and the fact that support can be harder to provide because of it.

All that said, I do understand the other side who says we shouldn't dissuade people from installing it. It's a sticky situation.

---

### Post by shaft350x on 2007-04-01
well that's an interesting aside, I suppose.  I wasn't asking for support on it, but rather opinions about which is better.  However, that strong of an opinion from what it has done to your systems in the past does merit some thought.  The specific question though is which would be better to get things setup quickly and easily on my wife's new Darter from System76.  From what I am gathering Automatix is possibly used more often, but Easy Ubuntu stays more within the realm of the official (or accepted) repositories.  Whereas Automatix may modify the source.list and mess with other things.  It isn't that I'm looking for something to replace synaptic, but rather just to get the mp3 codecs, and stuff so she can listen to her music and watch DVDs and Flash in Firefox.  I could probably learn to do this manually (I've done some already for my system, and used automatix for some on my system), but I would much rather just have it done and ready to go.  This is pretty much my wife's first experience with Linux (I'm really new to it as well) so I want her to be able to just use her laptop how she wants to, and not have to hassle with downloading a bunch of stuff and attempting to modify source.list and update and all sorts of other things that might just make her frustrated.

So Easy Ubuntu will likely be the safer choice?  This is what I am assuming I am hearing from the moderators of the board at least.

---

### Post by dracomordag on 2007-04-01
i dont really know if Automatix fscked up my old system, but it was pretty messed up before i wiped my drive for Feisty... now that I know how to get all the codecs and programs without Automatix, i see no need for it.

one specific issue that i know was related to Automatix was i couldn't uninstall some programs because they Automatix for no apparent reason listed them as a dependency...

---

### Post by r4ik on 2007-04-01
If automated scrips do not work you can blame it.
If you mess up yourself there is only the mirror.

---

### Post by unique on 2007-04-02
I have been useing Automatix from Breezy to Edgy... I got my System76 Gazelle Performance Laptop a few days ago and it came shipped with Edgy. I have been useing Feisty on my desktop and other laptop so I decided to wipe edgy of the new System76 lappy and put Feisty on. Everything worked out of the box even the webcam. If I where you I would load up fesity you gonna want in soon enuff anyways. It has been real stable for me & with Feisty you don't even need to use Automatix or any other scripts to get Feisty up to snuff. Feisty has everything you would get with Automatic right in the Repo!  If fact the only thing I had to do was add a repo for playing back DVD's.

Also keep in mind that if you want to upgrade from Ubuntu to a new version of Ubuntu when you use Automatix all that stuff will break and you will be forced to reinstall anyways. If you go with Feisty and get everything from the Feisty repo come time to upgrade to what ever is comming after Fesity will go smooth.  I remeber upgrading from Dapper to Edgy and because i used Automatix my system was hosed.

---

### Post by shaft350x on 2007-04-02
Did you have to use the CD that came with your laptop to reinstall the System76 drivers?

I may have to wait a while even after Feisty is officially released, part of the reason we went System76 was so I wouldn't have to install the OS for her, and we would know that it was checked and supported.  I'm not so worried about it being supported because there was a thread somewhere that Carl said they would support any released version.

---

### Post by unique on 2007-04-02
> **shaft350x said:**
> Did you have to use the CD that came with your laptop to reinstall the System76 drivers?

I may have to wait a while even after Feisty is officially released, part of the reason we went System76 was so I wouldn't have to install the OS for her, and we would know that it was checked and supported.  I'm not so worried about it being supported because there was a thread somewhere that Carl said they would support any released version.

I didn't have to use the System76 Driver at all Feisty just worked....

---

