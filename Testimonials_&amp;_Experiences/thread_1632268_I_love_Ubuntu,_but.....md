---
title: "I love Ubuntu, but...."
date: 2010-11-27
forum: Testimonials &amp; Experiences
---

### Post by misguided monkey on 2010-11-27
All joking aside, this is not just a rant, not just a chance to vent so that I'll feel better. These are things that, if not genuinely broken, are bad enough that somebody needs to say something:

1. Grub. Take a look at (for example) Chameleon, then another look at Grub. Then try to configure Grub....

2. Update Manager. Why can't I politely say "no thank you" to some updates without it asking me again and again until I finally say OK just to get it off my back. I understand that there are super-geek ways to get it to stop offering updates for certain software packages, whatever, but I really just want to check a box next to any particular update that says "thanks for offering, really, but I don't want it and I'll let you know if I change my mind."

3. Messages during boot. OK this is might be really stupid, but it's one of those first-impression things that you don't forget easily. By 'first' I mean the first thing you see every time you boot up. Honestly, I absolutely love the fact that you can - IF YOU WANT TO - get a short report from each and every service and daemon that starts up. It makes it easier (possible) to trouble shoot a problem, but I don't want to see them every time I boot (unless it's a serious problem, of course.) And yeah, I know you're supposed to be able to turn them off in grub, but that never seems to work completely. See #1 above.

---

### Post by Zzl1xndd on 2010-11-27
1) Most boot loaders (even for Windows) are a little esoteric, however grub is rather good. I have seen Chameleon and it does look nice, but I don't think most people care much about the boot loader. (that being said, I do would like to see something more like Chameleon as well.) 

2)This is understandable and would likely be an easy fix, however speaking from a security stand point its probably better to do all the updates.

3)Can't say I have experienced this issue my self, All I every see is Ubuntu 10.10 and 4 dots.

---

### Post by wilee-nilee on 2010-11-27
If you don't like it don't use it. ;) Or write the code to fix it.

---

### Post by aeronutt on 2010-11-27
So all users have to know how to write bug fix code?

---

### Post by wilee-nilee on 2010-11-27
> **aeronutt said:**
> So all users have to know how to write bug fix code?

Lol, no its called adaptation, adapt too your environment. 

Believe or not Dichotomies are a made man system, very few things are either/or when looked at in a contextual manner. I was just answering in the mode of the post it is called mirroring.

---

### Post by vharishankar on 2010-11-27
As for update manager problem you can turn it off like I have done:

System -> Preferences -> Startup Applications

And turn off Update Notifier from there. I always do updates manually from Synaptic.

---

### Post by andymorton on 2010-11-28
> **misguided monkey said:**
> All joking aside, this is not just a rant, not just a chance to vent so that I'll feel better. These are things that, if not genuinely broken, are bad enough that somebody needs to say something:

1. Grub. Take a look at (for example) Chameleon, then another look at Grub. Then try to configure Grub....

2. Update Manager. Why can't I politely say "no thank you" to some updates without it asking me again and again until I finally say OK just to get it off my back. I understand that there are super-geek ways to get it to stop offering updates for certain software packages, whatever, but I really just want to check a box next to any particular update that says "thanks for offering, really, but I don't want it and I'll let you know if I change my mind."

3. Messages during boot. OK this is might be really stupid, but it's one of those first-impression things that you don't forget easily. By 'first' I mean the first thing you see every time you boot up. Honestly, I absolutely love the fact that you can - IF YOU WANT TO - get a short report from each and every service and daemon that starts up. It makes it easier (possible) to trouble shoot a problem, but I don't want to see them every time I boot (unless it's a serious problem, of course.) And yeah, I know you're supposed to be able to turn them off in grub, but that never seems to work completely. See #1 above.

For a solution to problem 3 try putting the following into the terminal

sudo -s

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

---

### Post by misguided monkey on 2010-11-28
> **tweakedenigma said:**
> 1) Most boot loaders (even for Windows) are a little esoteric, however grub is rather good. I have seen Chameleon and it does look nice, but I don't think most people care much about the boot loader. (that being said, I do would like to see something more like Chameleon as well.) 

I've heard that grub is very powerful, and I don't doubt that it's very good in many ways. Unfortunately, none of those ways are ways that I care about as a simple user (a user as opposed to a system programmer or somebody that plays with linux recreationally.) And it's not just pleasing graphics that I want; I also want to be able to configure it in meaningful ways. The only thing that grub allows normal mortals to do is hide memtest. I'm still stuck with two menu lines that say "Windows 7 loader on sdax" even though I have only one copy of Windows installed. So update-grub sees two Windows partitions, that's OK, but I'd like it to be possible to hide the meaningless one and change the text (or graphic) on the one I want to keep. Let's face it: grub is ugly and unobliging. 

> **tweakedenigma said:**
> 2)This is understandable and would likely be an easy fix, however speaking from a security stand point its probably better to do all the updates. 

Someone might choose to simply install all updates without review for security reasons, but I'd like to make a different choice. If I wanted the os make all the decisions for me I'd run OS/X.


> **wilee-nilee said:**
> If you don't like it don't use it. :wink: Or write the code to fix it. 	

I do see the wink, and I'm sure you don't really expect me to abandon Ubuntu or take on the immense project of 'fixing' grub. But I'll be honest and admit that I really don't know what you hope I'll take away from your comment. Most of the possibilities say more about you than the topic of the thread.

> **andymorton said:**
> For a solution to problem 3... 

Thanks Andy, that seems to have worked. What do we need to do to get all Ubuntu installations to work that way?

---

### Post by arunb on 2010-11-29
> What do we need to do to get all Ubuntu installations to work that way?

which other ubuntu installation??

I am surprised you got put off so easily by these minor problems. I wonder how you would react if you encountered some real major problems.

---

### Post by wilee-nilee on 2010-11-29
> **misguided monkey said:**
> 
I do see the wink, and I'm sure you don't really expect me to abandon Ubuntu or take on the immense project of 'fixing' grub. But I'll be honest and admit that I really don't know what you hope I'll take away from your comment. Most of the possibilities say more about you than the topic of the thread.

Common man spit it out what does it say about me. Here I will help just learn more about the OS, your only able to remove the mem test because you don't know enough about it here is a tutorial on just this topic.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Look in the signature for all things grub. I think  you have gotten the impression that you need X amount of skills when it is really just asking good questions and not posting threads like this one, which frankly I would say shows a lot about you except that would be a **projection** on my part.:popcorn:

---

### Post by mastablasta on 2010-11-29
> **tweakedenigma said:**
> 12)This is understandable and would likely be an easy fix, however speaking from a security stand point its probably better to do all the updates.

 
you have no idea how much troubles one of the latest updates caused me. thatnkfully an "easy fix" was shown to me so i neevr get those updates again. problem is the following. in order for the sound to work propperly on my computer (and sound connected programmes). this is easily solved by upgrading ALSA to latest version. 
 
Well updates decided it would be a good thing to give me an older version of the drivers and also to overwrite my newer ALSA. very clever indeed. in windows if there is a newer version you will always be notified or it might not even install an odler version unless you uninstall you newer version. 
 
not very intuitive if you ask me.
 
 
regarding Grub, it looks lame and even the LILO i had in the 90's looked better. then agian i see it only for a short time (and only on a dual boot computer) so i am not too much worried about the looks here.
 
also Chameleon looks nice. :-)

---

### Post by misguided monkey on 2010-11-29
> **arunb said:**
> which other ubuntu installation??

*ALL* of them! Well, all future installations at least. It was a rhetorical question. 

> **arunb said:**
> I am surprised you got put off so easily by these minor problems. I wonder how you would react if you encountered some real major problems.

Perhaps you didn't understand the point of my starting the thread. I was not looking for help solving problems that I have encountered. I was identifying some things that I think are essentially broken in Ubuntu and that I think need to be fixed. 

I feel that grub is ugly, miserable, and unpleasant to work with. Sorry if grub developers are offended by that comment, but I'm not retracting it or apologizing for it. I've been shown that some things can be configured by modifying the source code, but that doesn't change my opinion because I don't think it should be necessary to modify source code just to get a boot loader to display a text menu the way I would like.

Update Manager is broken. I implied in my first post that I might not consider it genuinely broken, but just really bad. I've changed my mind, I now think that it's genuinely broken. I'll submit a bug report.

---

### Post by vharishankar on 2010-11-29
> **misguided monkey said:**
> *ALL* of them! Well, all future installations at least. It was a rhetorical question. 



Perhaps you didn't understand the point of my starting the thread. I was not looking for help solving problems that I have encountered. I was identifying some things that I think are essentially broken in Ubuntu and that I think need to be fixed. 

I feel that grub is ugly, miserable, and unpleasant to work with. Sorry if grub developers are offended by that comment, but I'm not retracting it or apologizing for it. I've been shown that some things can be configured by modifying the source code, but that doesn't change my opinion because I don't think it should be necessary to modify source code just to get a boot loader to display a text menu the way I would like.

Update Manager is broken. I implied in my first post that I might not consider it genuinely broken, but just really bad. I've changed my mind, I now think that it's genuinely broken. I'll submit a bug report.

Thing is every Linux distribution has its own set of warts, only the distribution fans will never admit that it is a wart. We get so used to "our way" that it seems the most natural thing. Even bugs are worked around and they seem to be no big deal.

E.g. for me GRUB is nothing more than a simple way to boot into my Linux. So long as it does this job, I'm not worried of how it looks. That isn't to say that your concern isn't valid, merely that we aren't tuned to the same "warts." I've been with Linux long enough to know the "1024 cylinder problem" (google it) with LILO and how much of a hit and miss scenario it was to boot Linux from a floppy. (a floppy would go bad after every few boots and I'd need to re-create the boot floppy!)

The only way I found out this truth was by experience and experimenting with practically every single mainstream Linux distribution out there. No distribution is free of "warts", depending on the way you look at it. For some the "wart" may be a critical deal-breaking bug, for others a mere inconvenience and yet others not really within their radar.

So yes, we all learn to live with the warts or work around them hoping they get fixed some day. Certainly the pace of development of Linux is such that you can expect fixes in 6 months time, not 5 years or so like Microsoft.

---

### Post by Tamlynmac on 2010-11-30
> wilee-nilee
Lol, no its called adaptation, adapt too your environment. 

Well said.

Learning and adapting to one's environment is critical. Assuming one wishes to be productive and evolve (big assumption).

IMHO:
It's amazing how much information a simple internet search can reveal.  However, one must be "willing" to invest in seeking and assimilating  knowledge of said environment. Expectations of instant gratification, impacts motivation. :wink:

Just my $0.02

---

### Post by JamezQ on 2010-12-02
> **misguided monkey said:**
> 
2. Update Manager. Why can't I politely say "no thank you" to some updates without it asking me again and again until I finally say OK just to get it off my back.


Linux Mint 10, based on and fully compatible with Ubuntu 10.10, has this feature by default in a easy point and click fashion.


From [http://www.linuxmint.com/rel_julia_whatsnew.php](http://www.linuxmint.com/rel_julia_whatsnew.php):

"If you're not interested in receiving updates for a particular package, simply right click on it and tell the Update Manager to ignore updates for this package. The package will then be added to your "ignore" list and you won't receive any updates for it in the future."


You can install pretty much anything you want from Ubuntu into mint, including Ubuntu's menu and theme if you don't like the MintMenu, some things however like Ubuntu's software center, take a bit of tweaking(I really do mean a 'bit', there are easy steps online). 

However, after searching I found no way to install Mint's upgrade manager in Ubuntu.

---

### Post by AcidHawk on 2010-12-02
The problem for me is that Ubuntu (Linux actually) is like a drug.  There are certain things that are just better in other OSes (E.g. software that is designed for a particular OS, some games, plugging a USB2VGA adapter in to another OS) - the problem is that I get [COLOR="Red"]such[/COLOR] a [COLOR="Magenta"]good[/COLOR] [COLOR="DeepSkyBlue"]feeling[/COLOR] just [COLOR="Orange"]doing[/COLOR] the [COLOR="SeaGreen"]simple[/COLOR] [COLOR="Plum"]things[/COLOR] in any distribution that I can't stop using it!

Am I addicted ?... Do I see pretty colours ?... Too damn right.

Like a mate of mine says: ***"Linux is like an addiction for me; at times it feels a bit unhealthy, but I just can't resist it."***

---

### Post by 3rdalbum on 2010-12-03
> **misguided monkey said:**
> All joking aside, this is not just a rant, not just a chance to vent so that I'll feel better. These are things that, if not genuinely broken, are bad enough that somebody needs to say something:

1. Grub. Take a look at (for example) Chameleon, then another look at Grub. Then try to configure Grub....

Check out BURG - it at least looks nicer than GRUB and I think in future it will be easier to configure, should you actually need to (who does, anyhow?)

> 2. Update Manager. Why can't I politely say "no thank you" to some updates without it asking me again and again until I finally say OK just to get it off my back. I understand that there are super-geek ways to get it to stop offering updates for certain software packages, whatever, but I really just want to check a box next to any particular update that says "thanks for offering, really, but I don't want it and I'll let you know if I change my mind."

The best idea is to accept the updates, but if you have a particular need not to, then you can lock the package in Synaptic.

> 3. Messages during boot.

You're not meant to get any of them anymore - none during boot, none during logout, and none during shutdown. Mark Shuttleworth says to file a bug report if you see messages.

---

### Post by misguided monkey on 2010-12-04
Thanks 3rdalbum. Burg looks like it might address__ my issues with grub. I'll take a closer look. Is it based on Colin D. Bennett's Summer of Code 2008 project? [http://grub.gibibit.com/](http://grub.gibibit.com/) The themes look suspiciously similar, but it appears that burg takes it quite a bit farther.

And I'll try to put together enough info to make a useful bug report about text appearing during bootup and shutdown.

---

### Post by misguided monkey on 2010-12-04
I installed burg on my 'experimental' machine and it seems to work well and has (so far) been stable. If it doesn't cause too much trouble I'll try it on the computers that I actually use. With the addition of burg manager it's actually pretty close to what I want. It's my opinion that it should completely replace grub in the standard Ubuntu distribution (assuming it's stable) but that's just my opinion.

Anyone that wants to try it should just install burg manager; it can be used to install burg itself. [http://www.sourceslist.eu/burg-manager/](http://www.sourceslist.eu/burg-manager/)

---

### Post by fluxlizard on 2010-12-05
> If you don't like it don't use it. Or write the code to fix it.

Suggestions for improvement do not necessarily mean the user dislikes it. Opinions stated is one way of contributing and giving back to the community.

 If enough users complain or compliment something, hopefully it will get noticed by those who do have the ability to write the code or make the choices to keep or replace something in the OS.

Just a thought...

I just installed this the other day and wondered why it isn't standard for ubuntu- looks much nicer than grub-

[http://www.webupd8.org/2010/10/install-and-configure-burg-in-ubuntu.html]("http://www.webupd8.org/2010/10/install-and-configure-burg-in-ubuntu.html")

---

### Post by wilee-nilee on 2010-12-05
> **fluxlizard said:**
> Suggestions for improvement do not necessarily mean the user dislikes it. **Opinions stated is one way of contributing and giving back to the community.**

 If enough users complain or compliment something, hopefully it will get noticed by those who do have the ability to write the code or make the choices to keep or replace something in the OS.

Just a thought...

I just installed this the other day and wondered why it isn't standard for ubuntu- looks much nicer than grub-

[http://www.webupd8.org/2010/10/install-and-configure-burg-in-ubuntu.html]("http://www.webupd8.org/2010/10/install-and-configure-burg-in-ubuntu.html")

Yes if the opinions are informed which I see none of in this persons posts. This a frustrated inexperienced user complaining about grub and including a apple bootloader chameleon please.

Burg is not a standard because as nice as it is, it is just grub2 in drag and not updated like grub2 is.

Know what your doing before you do it, and if you don't and it breaks who is at fault eh.

---

### Post by Sef on 2010-12-05
Locked. Seems to be getting heated. If the op wants, I will reopen it after few days of letting people cool down.

---

