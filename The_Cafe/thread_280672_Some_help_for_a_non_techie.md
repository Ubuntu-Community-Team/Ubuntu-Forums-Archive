---
title: "Some help for a non techie"
date: 2006-10-19
forum: The Cafe
---

### Post by podunk on 2006-10-19
First of all understand &#8211; I like Linux, and have committed to changing over completely by the end of the year. But I swear &#8211; sometimes it looks like the community goes out of its way to make things hard on the non technical users sometimes.

I understand &#8211; the people that write these programs have many years of education and effort invested in Linux. Then do it because they want to do it, and I'm free to change it.

But you know, us folks who build houses for a living, or flip burgers, make automobiles etc don't go out of our way to make our products hard to use.

Every year I rehab some housing to help those that are less fortunate than I am. I enjoy doing this. I don't leave holes in their floor or put outlets with no wire in the walls and tell them &#8220;Well, I did it because I wanted to do it. It's free after all &#8211; and you can change it any way you want to.&#8221;

I have about a dozen movies that I just love. I backed them all up and the originals never get opened. I was going to watch one of my faves Saturday but it had been scratched. Well, no problem &#8211; right? I'll just use my spiffy new and very powerful Ubuntu Linux install and make a new backup and watch my movie.

It's Thursday now, and I just booted into XP to make a back up of my movie. Almost all my computer time between Saturday and now has been invested in a failed attempt to copy a movie.

I have followed guide after guide,  I have installed doc packages and read them. Every guide leaves out one important fact &#8211; a fact you find out at the end. Every guide assumes you have knowledge that in fact new users don't have &#8211; and have no way to find. Many of the guides are directly contradictory of each other.

I swear &#8211; some of it looks malicious. This is from the help document from the k9copy app:
```
k9copy 0.1 is a program that lets you do absolutely nothing. Please report any problems or feature requests to the KDE mailing lists.
```

How about this for a useful instruction:
[code}The Squiggle Tool Squiggle is used to draw squiggly lines all over the k9copy 0.1 main window. It's not a bug, it's a feature! [/code]
or:
```

Configuration:
Don't forget to tell your system to start the dtd dicer-toaster daemon first, or k9copy 0.1 won't work !

```

I have some DVD copy software in Windows that I paid for. But just for the halibut I searched the web. In less than 5 minutes I had a step by step howto and 2 free ware (as in beer) programs  installed.

Now I've never used these programs before.  In less than 2 hours the DVD has been ripped, decrypted, edited, enhanced, shrunk and is burning and will be done before I finish this post.

I took a break from typing, and looked on the web &#8211; and found 3 more howtos on using DVD Decrypter and DVD Shrink. Every how to largely agreed with each other. There were numerous screen shots. The possible errors you might encounter were discussed and solutions offered.

My DVD is burned by the way.

Is there section in the GPL that says our documentation has to be so cryptic and dry that you need a Masters Degree to understand it? Is there an unwritten tradition that our documentation be hidden away?

As I understand it &#8211; Linux is standards based &#8211; it's one of the bragging points for us. 

Why can't we come to some agreement on standard documentation? One that says ALL documentation will go to /this/directory/here  ? That each program will be installed and listed on the menu by it's start up command.

Take archive manager in Ubuntu for a prime example. Type in ```
archive manager
``` in the terminal to start it &#8211; it won't run. Try ```
man archive manager
``` and it won't be found. Try ```
locate archive manager
``` and you'll get no results.

Why? Because the name of the darn file is file-roller that's why! This isn't an exception, I can cite instance after instance of poor and missing or downright  misleading documentation.

I think it's a crying shame that Windows users can write better documentation than we can. They have none of our advantages. They don't have communities, they don't have source code to read, their applications aren't standards based. What they do have going for them is the willingness to write full sentences and paragraphs and include screen shots as they go.

I love RTFM. Really I do! The vast majority of my wood working and construction knowledge came from books. Most of my cabinet and furniture making skills were learned on the web.

I'd love to write some how tos and some docs &#8211; but right now &#8211; it looks like I'll be an old man before I know enough about Linux to share anything useful.

---

### Post by aidanr on 2006-10-19
half the fun is figuring stuff out;) i guess if you don't like that then theres always... windows?

---

### Post by Tomosaur on 2006-10-19
Most linux documentation goes into /usr/share/doc.

A linux program cannot have whitespace (which is why 'archive manager' is not recognised), but I agree that they shouldn't be named completely different things.

Documentation is usually done by users in open-source software. Very, VERY basic documentation is done by the developers right at the beginning, but that job is considered unimportant compared to actually getting a working product out. Users will then generally go through and contribute to the product's wiki/web-page/tutorials/whatever.

I dunno. A good program shouldn't need documentation imo, and usually there's basic documentation to get you started. I really hate to say it, but if you don't like it, do something about it :S

And yes, making backups of DVDs is horrible on linux. I still don't know an easy way to do it :/

---

### Post by calx on 2006-10-19
So what movie was it?

---

### Post by gn2 on 2006-10-19
Since it might be illegal I can't advise you to do a Google search for the Mr Bass guide to running DVD Shrink in Wine with Ubuntu.

---

### Post by podunk on 2006-10-19
It was &#8220;Bill and Ted's Bogus Journey&#8221;

Quote:
I dunno. A good program shouldn't need documentation imo, and usually there's basic documentation to get you started. I really hate to say it, but if you don't like it, do something about it :S

And yes, making backups of DVDs is horrible on linux. I still don't know an easy way to do it :/
end quote

Well &#8211; doing something about it is what I'm trying to do now.:-) In about 6 or 7 years I may know enough about Linux to write a bash script or something else useful. :-D

Why wouldn't a good program need documentation? How else will new users know how to use it? Good programs need good documentation much more than bad ones do &#8211; sort of a Darwinian approach. Good programs get good documentation and grow and evolve because new users are attracted and grow and evolve them.

Aren't a lot of apps written by teams? Isn't there someway to start doc teams? I don't know much about Linux &#8211; but I can proofread. I know how to ftp files to a server. I'm willing to take the time to try out instructions and post results and ambiguities to the team. I'm wiling to have my set up trashed in the name of good documentation.

I can write checks for server space with the best of them. :-) 

I'd be willing to bet that the DVD back up programs for Linux are very fast and powerful &#8211; once you find a way to make them run.  But one person on one machine will most likely be unable to write good universal documentation.

Every doc team should include at least one Linux dumb burro &#8211; like me. :-D

---

### Post by CatKiller on 2006-10-19
Documentation for most open source projects is crap. That's because it's tedious and it's difficult to get into the mindset of a new user when you're the person that designed the interface and wrote the program. If it's a one-person project then the only person available doesn't want to do it, and can't do it very well. If it's a small team it's not much better.

Commercial software houses need better documentation and fit-and-finish stuff because they need to convince people to part with money. They can also generally afford to have a documentation team who are good at writing documentation, or hire it out. That gives them the advantage in both desire and ability.

There are three main standards (don't ask :roll: ) for documentation - /usr/share/doc, the man pages, and the info pages. Some projects have some of this information, or different information, or none, on their websites.

DVD copying, in particular, is tricky, since it's illegal for how ever many Americans and Australians there are. Probably others, too. But for other discs that I've tried to copy I've only needed to right-click on the disc icon on my desktop and select "Copy Disc". I haven't tried it with a DVD - maybe they don't work that way.

EDIT:> The Squiggle Tool Squiggle is used to draw squiggly lines all over the k9copy 0.1 main window. It's not a bug, it's a feature! That's really funny.

---

### Post by thornomad on 2006-10-19
You should get a Mac.  

That is more-like Linux only very expensive -- but it copies disks really easily.

I went from Windows, to Mac, and now am using Ubuntu on occasion.  I only dare boot up windows when I need to see how a web page is being incorrectly displayed by internet explorer.  

Linux can be frustrating when you are starting out -- I still can't get it to what I want all the time.  But it is free, and it is open-source, and I like that.  

One day, perhaps, enough people will come along like you (and me, I guess) with the user-end perspective and we will contribute the time and energy to write all the meticulous documentation that should be provided.  Coders put in the hours for making the stuff -- someone will come along to do the rest eventually.

Stick with it.  It isn't all that bad.  More fun than watching movies, anyway.

---

### Post by mssever on 2006-10-19
To copy a DVD, right-click on the DVD icon and choose Copy Disc...

You should also be able to copy the contents of the DVD to your hard drive and burn them to another DVD just like you would do if you were making a data DVD. Video DVDs actually contain a filesystem, unlike audio CDs. Note that I haven't actually tried this, but it *should* work.

---

### Post by emarkay on 2006-10-19
*Spanking - well I prefer other taunts and punushments, but alas, remember this:*

Unix/Linux has grown from the black rimmed, buzz cutted, starched white shirt and dark tie geeks of the 60's to the longerhaired denim clad dudes of the 70's, to the pimply faced nerds of the 80's to the gothic slackers of the 90's to the pierced and tattooed whatevers of today; All twentysomethings, all with the desire to change the world, to have fun, and, well... you can see why there such cutsey names, lame humor, unprofessional documentation, and all the rest here in this corner.

But that does NOT mean the product (free in this case) is flawed.  It's the 'tude of the dude/dudettes that sets the mood.  But with some serious investment in standards, awareness and $$ to make Ubuntu great, the attention seekers will migrate off to the Linux neverwherelands, while the Ubuntu fold will grow professional, comprehensive, and intuitive.  It will get better.

This I believe, in my humble opinion.

MRK

---

### Post by calx on 2006-10-21
You forgot the beards **emarkay**, all those big bushy nerd beards bless 'em.
 [http://www.stallman.org/rms-bw.jpeg]("http://www.stallman.org/rms-bw.jpeg")
:D

---

### Post by Tomosaur on 2006-10-21
What I meant when I said 'good programs shouldn't need documentation' is that all of the functionality of the program should be easily accessible and intuitive. Hidden, obscure functionality should either be avoided completely, or made easily accessible through an 'advanced' dialog box or something. Take a look at the manual for a piece of software. There will be virtually nothing in there you couldn't have worked out for yourself.

---

### Post by jhenager on 2006-10-21
> **Tomosaur said:**
> What I meant when I said 'good programs shouldn't need documentation' is that all of the functionality of the program should be easily accessible and intuitive. Hidden, obscure functionality should either be avoided completely, or made easily accessible through an 'advanced' dialog box or something. Take a look at the manual for a piece of software. There will be virtually nothing in there you couldn't have worked out for yourself.

In a perfect world....
Programming is a lot of fun, and documentation takes all the fun out of it. That's what technical writers are for....
Anyway, you just have to hang in there for more spankings. It's worth it.

---

### Post by xpod on 2006-10-21
> First of all understand – I like Linux, and have committed to changing over completely by the end of the year. But I swear – sometimes it looks like the community goes out of its way to make things hard on the non technical users sometimes.

If THAT was the case then i certainly would`nt have come as far as i have in 3 months ....having only used pc`s full stop for a couple o months prior to getting ubu back in july.

It seems to me,as soon as someone comes across something THEY cant figure out then its time to tell all just how bad linux really is...mmmmm

Im the most un-technical person i know and shunned computers and all their wonders for many years until march when i finally took the plunge....

I probably have more confusion than a lot of folks about pc`s in general and not just OS`s but even i know that it aint the OS`s fault if i cant suss something out.
Really hope you get your "bogus" problem sorted out...good luck.

---

### Post by PriceChild on 2006-10-21
*moves to cafe*

---

### Post by .t. on 2006-10-21
If you want to rip DVDs, a simple, quick search would have revealed acidrip. It's one of the best out there; it's a front-end to the ever-popular MPlayer encoder.

---

### Post by fuscia on 2006-10-21
whip me. beat me. make me write bad checks.

---

### Post by JayTee on 2006-10-21
A lot of people like to drive comfortable sedans down nice smooth highways and avoid all the backroads and shortcuts. They like everything nice and tidy and spend half their free time cleaning or reorganizing their "stuff". Those are the kind of people that gravitate toward Windows. Then there are those adventurous types that buy 4X4 SUVs or dirt bikes and drive completely off the road and into the wilderness. They like the unexplored, the difficult and the road less travelled. They also hate writing documentation and they don't care if they get a little muddy now and then. These are the type of people that Linux in all it's flavors (flavours for you Brits and Aussies :D ) appeals to.
In the early 70's most of the Unix crowd at Berkely and other universities all wore jeans, flannel shirts and sported pony tails in stark contrast to the dark blue suit, white shirts, black ties and black oxford shoes of the IBM clone set. Now it's the 21st century and all I can think of is, "Damn! I wish I still had enough hair to grow a pony tail"
"Two paths lay diverged in a wood, I chose the one less traveled by and now I'm utterly lost!"

---

### Post by Imsati on 2006-10-21
> **podunk said:**
> But you know, us folks who build houses for a living, or flip burgers, make automobiles etc don't go out of our way to make our products hard to use.

It takes me roughly 2-3 hours (depending on model) to strip an engine on a older car down to the block. On a newer model year, anywhere from 6 hours to a whole weekend. Why? Because technology changed, and now we have electronic throttles, MPFI, engine covers, direct injection, coil packs, etc. instead of cable throttles, bare engines, carbourators, and fuel rails.

Does it take more time to fix if something goes wrong, 4 out of 5 times, yes it does. But do newer cars tend to last longer? They sure do. Auto makers din't do 'out of their way' to make them more complicated, they simply learned to adapt new technologies to make them better--that's what Linux is doing in a way. There was a time when I knew nothing about cars, now I'm a motor-head. There was also a time I knew nothing about Linux, now I'm sopping up more info every day.

It just takes time, is all. Over the course of 3 months, my knowledge base on Ubuntu has increased probably 600% from when I did my first install back in July. Part of the fun of it is trying new ideas and seeing if they work, maybe doing a bit of research. Nothing malicious or done from spite, just the way it works sometimes.

~Jay

---

### Post by PatrickMay16 on 2006-10-21
Absolutely. Also, stuff like this is going on in the ubuntu wiki, too. Just look at the part about mounting MS windows partitions:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Why on earth does it ask you to do
> 
for i in /dev/[hs]d[a-z]; do sudo fdisk -l $i; done

when all you really need to do is "sudo fdisk -l"? Some fool was probably trying to look like a clever guy wit' his redundant use of bash junk.

Also, to the OP: this is why RTFM is all the more insulting. People who tell you to "RTFM" are telling you to waste all your time trying to understand a crappy manual page thrown together in five minutes by a programmer.

---

### Post by argie on 2006-10-21
Haha podunk. So often I've had similar experiences with redhat. It wasn't redhat's fault, I just never used a forum. Now, I usually find what I want here on the forum.

Because linux moves so fast, a dated guide very often just won't work.

---

### Post by aysiu on 2006-10-21
I don't understand why you need to know the archive manager is called *file-roller*.

Most of the time it gets automatically invoked when you double-click a .tar.gz.

How many Windows users know Internet Explorer is *iexplore* or that Microsoft Word is *winword*?

---

### Post by Bloch on 2006-10-22
Documentation is pretty bad for a lot, if not most, software in linux. Add to that all the old programs hanging around in the repositories.

Like lingoteach. Two hours wasted trying to get it to work. Don't try to help me now - I will not try it again.

And nicotine. A great file-sharing program. But it does not work when you install it. Nothing - NOTHING - tells you that you need to go to preferences and specify a downloading and sharing directory, plus a couple of others.

"Quick Start Guide" is a phrase that does not exist in Linux documentation.

---

### Post by aysiu on 2006-10-22
> **Bloch said:**
> 
"Quick Start Guide" is a phrase that does not exist in Linux documentation. I'm sorry you haven't found good tutorials for *lingoteach* and *nicotine*, but you're not being fair to those of us who put hours into making good Linux documentation.

---

### Post by JayTee on 2006-10-22
Most of the Linux/Ubuntu documentation and How-To's I've read are excellent. I've found a few that were a bit obscure in some areas but most are clear and easy to understand. I've read many tech docs and how-tos for Windows that were totally off the mark or just plain wrong and I've been supporting Windows desktops and servers since Win 3.1 and NT 3.51. In defense of Linux, what difference does it make what you call an archiving program? Ever hear of Winzip? Is that an obvious program name for an inexperienced Windows user? NOT!!!!! One of the best How-To's I've read to solve a particular problem involving DVD authoring was written by a high school sophomore and I was amazed at the clarity and the clean format. Wish some of the college graduate "geniuses" that write documentation could learn a thing or two from this young man. I just got through installing XGL with Beryl which I'd tried a couple times earlier but it hosed my x-server in previous attempts. I found a link to a how-to off this forum that was much clearer than the ones I'd used in the previous attempts. The result was successful but it left my numlock and capslock keys non-functional. Did I panic or get angry? No. I just opened my browser and came to this forum where I did a search using the applicable keywords. Bam! Several threads. Browsed three and had a fix. Tried it. Success!!! That's way better than Microsoft. I've searched their knowledge base thousands of times with specific error codes and messages only to come up with nothing, zip, nada. I go to google and search with the same strings and get hundreds of hits. Some even point to links to Microsoft KB articles. Ever wonder why that happens? I now have a kickass system. Check out this screen shot. Ubuntu Rocks!!!! And so do all the people that put so much work into it on this forum and don't make a dime doing it.

---

### Post by Cynical on 2006-11-22
Have you tried dvd95? Its pretty straight forward.

---

