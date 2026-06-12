---
title: "Fairly good installer, but everything else..."
date: 2009-03-13
forum: Testimonials &amp; Experiences
---

### Post by soon2bbacktoXP on 2009-03-13
I thought I'd take a moment to comment on my experience with 8.10 while it is fresh on my mind, and before I reinstall windows XP.

I have to say, the installer and gnome are a lot better than the previous version of linux I had tried many years ago.  However, there is still too many issues that prevent me from using it.  I really wanted to use it as my CVS repository without having to settle for cvsnt, but the pain isn't worth the effort.

1. I get an error saying I'm in "low graphics mode", but it refuses to install the recommended driver.  Ok, I don't need good graphics...I'll go with the low settings.  Ugh, the screen blinks like a strobe light...I go to change the refresh rate and the only accepted value is 0!

2. I plug in my external USB drive and it works right off the bat!  Awesome!  Uh, wait a minute, I can only read?  I don't have authority to write?  I spend an hour or so researching this, and trying to give myself "root" access and nothing works.  I find a post that says linux can only READ ntfs formatted drives.  One comment even said it was windows fault that linux has this problem.  Little hubris there.

3.  I try to figure out how to use something like tinyVNC to control linux remotely, but the installation instructions are just too much work to install software.

4.  I decide to test tomcat, since that and cvs were the main items I was going to use anyway.  Manager password?  don't know.  No problem, I'll update the user.xml file.  Nope, I don't have authority to it.  

I didn't even bother with cvs.  For all the complaining about vista authority problems, I have to say this was much more annoying.

I know the response to this is that I didn't know what I was doing.  True, but that is the real problem isn't it?  I don't want to learn unix commands to use my computer.  It's the same as asking me to use DOS to use windows.  

I think this version is better than before, but the developers need to think in terms of avoiding the dos prompt to solve all problems.  If I have to open the terminal window then I'm already halfway down the road to MS land again.

---

### Post by binbash on 2009-03-14
If you are not going to learn linux commands, please save everyone's time and stick to windows.Good luck with that.

---

### Post by ugm6hr on 2009-03-14
Indeed, the problem is you didn't know what you were doing; more importantly, you didn't ask someone who does.

In case anyone else finds this:

**ntfs-3g** can be installed with a few clicks, and allows write access to NTFS drives

Ubuntu has a built in VNC / Remote Desktop server (you don't need to install anything) - a few clicks in System -> Preferences -> Remote Desktop.  In fact, it also has 2 remote desktop viewers built in.

Graphics drivers can be a little trickier, but most are resolved with a few clicks using **envy-ng**

Opening a Terminal is often faster to install drivers / software etc, but is not the only way.

---

### Post by moster on 2009-03-14
Ubuntu release new version every 6 months. Is more better with every release. Just try it again later, they will eventually fix everything. I hope, at least.

---

### Post by betrunkenaffe on 2009-03-14
I almost laughed at the VNC comment. I just replaced Ubuntu with Dreamlinux on my desktop to test something out, I had to install vncserver and then get it set up to work with my laptop over the internet (add to the complications that I refused to open the port and wanted to ssh tunnel it).

4 hours later it works, how many minutes did you actually spend looking through the menus because as was pointed out, Ubuntu has vncserver built in.

Enjoy reinstalling your drivers in Windows and getting all the updates, I'm sure it'll be a 15 minute process like your Linux install (and apparently test).

---

### Post by z.s.tar.gz on 2009-03-14
> I think this version is better than before, but the developers need to think in terms of avoiding the dos prompt to solve all problems. If I have to open the terminal window then I'm already halfway down the road to MS land again.

So, cars shouldn't having steering wheels because you have to learn to drive?

Good riddens.

---

### Post by stalkingwolf on 2009-03-14
[FONT="Comic Sans MS"][SIZE="5"]**Well,Bye**[/SIZE][/FONT]

---

### Post by wolfen69 on 2009-03-14
> **soon2bbacktoXP said:**
> I thought I'd take a moment to comment on my experience with 8.10 while it is fresh on my mind, and before I reinstall windows XP.

I have to say, the installer and gnome are a lot better than the previous version of linux I had tried many years ago.  However, there is still too many issues that prevent me from using it.  I really wanted to use it as my CVS repository without having to settle for cvsnt, but the pain isn't worth the effort.

1. I get an error saying I'm in "low graphics mode", but it refuses to install the recommended driver.  Ok, I don't need good graphics...I'll go with the low settings.  Ugh, the screen blinks like a strobe light...I go to change the refresh rate and the only accepted value is 0!

2. I plug in my external USB drive and it works right off the bat!  Awesome!  Uh, wait a minute, I can only read?  I don't have authority to write?  I spend an hour or so researching this, and trying to give myself "root" access and nothing works.  I find a post that says linux can only READ ntfs formatted drives.  One comment even said it was windows fault that linux has this problem.  Little hubris there.

3.  I try to figure out how to use something like tinyVNC to control linux remotely, but the installation instructions are just too much work to install software.

4.  I decide to test tomcat, since that and cvs were the main items I was going to use anyway.  Manager password?  don't know.  No problem, I'll update the user.xml file.  Nope, I don't have authority to it.  

I didn't even bother with cvs.  For all the complaining about vista authority problems, I have to say this was much more annoying.

I know the response to this is that I didn't know what I was doing.  True, but that is the real problem isn't it?  I don't want to learn unix commands to use my computer.  It's the same as asking me to use DOS to use windows.  

I think this version is better than before, but the developers need to think in terms of avoiding the dos prompt to solve all problems.  If I have to open the terminal window then I'm already halfway down the road to MS land again.

like 90% of the people in the world, you should not even be using a computer. shame on you.

go ahead, run back to the "safety net" POS OS known as windows. you are obviously not smart enough to grasp linux. you deserve windows.

go ahead and run back to the windows community and tell tales of how the mean, non-understanding linux people made me feel like i was a bad person. go ahead. i personally could not care less what OS you use. but you HAD to make it public, as if it was going to solve anything. IF YOU DON'T LIKE IT, DON'T USE IT. did i post in the windows forums that i was leaving windows? no. people like you make me sick.

---

### Post by soon2bbacktoXP on 2009-03-14
I was attempting to provide the developers with my "user experience" so that they might attempt to continue working positively on their os.

Your juvenile reply just furthers the perception that linux is only for a minority of people.   

As for my "qualifications" for using a computer, I've been a computer developer for longer than you have been alive.  I've worked on os's that you've never heard of and know a little about those that work and those that are just a pain in the neck.

In the 21st century, I believe we should be well past the DOS prompt operating system.  tty teletype terminals are pretty ancient.

At any rate, your comments do nothing to further linux as anything but a cult os.

---

### Post by wolfen69 on 2009-03-14
> **soon2bbacktoXP said:**
> I was attempting to provide the developers with my "user experience" so that they might attempt to continue working positively on their os.

Your juvenile reply just furthers the perception that linux is only for a minority of people.   

As for my "qualifications" for using a computer, I've been a computer developer for longer than you have been alive.

if you were attempting to provide the developers with feedback, you picked the wrong place to do so. that in itself tells me you don't know much about how to go about things.

[B]"Your juvenile reply just furthers the perception that linux is only for a minority of people."
[/B]

and that's ok. because it's only the minority of people that actually use their brains.

so you've been a developer for 46 years? seems to me that someone with your infinite knowledge should have no problem adjusting to linux. maybe you're not the hacker you claim to be. i never have a problem with ubuntu, or ever have to use the comand line. it just works beautifully. you are obviously not smart enough to make an OS dance for you. i can make *anything* work for me, be it windows, mac, or linux. you can not say the same. please go back to school and learn some basics.

you are only making yourself look stupid by claiming to be a developer since the beginning of time, and then saying linux does not work for you. there are many people with less qualifications that can wrap their head around linux. what's your excuse? please, do the world a favor and develop for the anti-virus community. that's the only thing you might understand.

---

### Post by Riffer on 2009-03-14
While wolfen is very blunt in his reply, I have to agree with him.

Low graphics mode, means you have to install a driver, same as in windows.  A quick search in these forums will tell you how to do that.  Just let people know what GPU you need the driver for.

Root access, a person with your "experience" should understand permissions and why we have them.  You should also understand the difference between doing things as superuser as oppose to root.  You should also understand that the main reason that windows is so unsecure is it having root access as the default.  To change permissions for files is a simple process involving typing 2 words in at the terminal, "gksudo nautilus", finding the file(s) you want to change permissions for and doing so using properties in the right click context menu.

Your other 2 items were covered previously in this thread or by me.  As to your comments about the command line, you're wrong.  95% of the time you can use a GUI for all your programs, the times that you need the terminal is for instances like I explained above.  This gives you that extra layer of security.  Also the CLI makes troubleshooting and support really easy.  Being able to give a command that the person can cut and paste into their terminal is tons better then trying to help them navigate through menus, context menus and buttons to find their solutions.  And if you're like me and try things out that results in crashing your desktop, having a prompt come up and being able to use commands to troubleshoot and if necessary rebuild your desktop is a great feature. 

Whats irksome for a lot of long time users of Linux is new users that expect Ubuntu to be exactly like Windows and then think its flawed because its not.  I suggest that you come at Linux as a different OS with its own way of doing things, and learn those things, you might be pleasantly surprised.

---

### Post by Tamlynmac on 2009-03-14
> soon2bbacktoXP
I was attempting to provide the developers with my "user experience" so that they might attempt to continue working positively on their os.

Another thing you didn't bother learning is this isn't a developers forum. They rarely use this forum.

Your theory appears to be based on ignorance. Being a "developer", you should understand that when investigating any software one must RTM and comprehend the intricacies or said software. It appears all you did was attempt to install, setup and use the software without any fundamental knowledge of the OS. Had you spent time investigate the OS and/or reading through this forum, you would have realized the errors of your ways. When evaluating any software one must do so in a controlled environment under controlled conditions. Instead, you haphazardly endeavored to install, setup and run a completely foreign OS. Ask yourself if that would be viewed as the professional actions of a dev?

The minority of people you talking about, enjoys the freedom of Ubuntu and of course the lack of virus & malware protection needed in Windows. They also enjoy the freedom of creativity and personalization built into the OS. You never bothered to mention that or a number of other benefits. I suspect your motives to be questionable regarding your irrational assessment of Ubuntu. 

But the truly sad part is your lack of understanding the community. I would never waste time explaining the community involvement to you, as I believe it would simply fall on deaf ears.

Unlike others, I truly appreciate your posting and responses, as all statements made about Ubuntu/Linux open peoples eyes to an alternative. Since many don't know a Windows alternative exists, even your pathetic attempt at an assessment spreads the word. When someone compares Ubuntu to Windows they inadvertently provide awareness to individuals and often inspire them to investigate. Comparing a free alternative to Windows, suggests Ubuntu/Linux has come a long ways. Or why would you feel threatened enough to even post on this forum.

Thank You again and please continue spreading the word - doesn't matter if you opinion is positive or negative, the word gets out. Keep up the good work. Open your horizons and spread it to other forums, especially Windows forums.

Your support is appreciated. I (like some others) will no longer argue or provide you with gratification and will simply unscribe to this thread, in hopes you go elsewhere and enlighten others. I suggest other members do the same and inspire this individual to go spread the word.

---

### Post by Dan_Dranath999 on 2009-03-14
> **soon2bbacktoXP said:**
> As for my "qualifications" for using a computer, I've been a computer developer for longer than you have been alive.  I've worked on os's that you've never heard of and know a little about those that work and those that are just a pain in the neck.


So, you were a computer developer back in the 70's WHEN UNIX WAS CREATED? And still you can't use a simple terminal in linux?


I'm 29. The first computer enviroments i remember were DOS and IBM OS/2... i was 12 or 13 years old. All the kids in my class learned how to navigate folders and copy floppies using commands, *copy a: b:, dir /w, cd..* and everybody was ok with that. Some knew more than others, but not one said typing commands was hard...

It just don't make sense, when you claim to be a computer developer who's older than me and not being able to manage this OS. I thought every geek older than 30 would love the terminal.

I smell Trolls.

---

### Post by moster on 2009-03-14
Uh... You must understand this is hostile territory except for someone who praise linux. You are not first and last who said similar and you are certanly not last who these guys bashed. If you stay expect insults. I recommend that you just leave and come back in better time. Or go to your country forum. It seems that local territory is always better than this wolfes...

---

### Post by wolfen69 on 2009-03-14
i like how people come on here claiming to be some great developer, and they've been doing it for years, (longer than you've been alive) yet, all they know is windows. 

i am a computer person, not a windows person. i can make any OS sing and dance for me on any hardware. the original poster is still thinking in a windows mindset as if it were the only OS on the planet. sad. 

please, go back to windows land and tell everyone about the bad, bad, linux people, and how they hurt your feelings. you are a 1 trick pony.

---

### Post by betrunkenaffe on 2009-03-14
Wolfen can be a little overcritical in his reactions but at the same time you have to look at the OP and his comments. They pretty much smack of 15 minutes of fiddling, 10 minutes of "research" and generally assuming they knew everything they needed to know from that point on (maybe they do, if so, that saddens me more for them).

As for the developer comment, all I can say is "Really? Are you really? Really?" because I personally can't see it based on what you did/said.

PS: Really?

---

### Post by wolfen69 on 2009-03-14
> **betrunkenaffe said:**
> Wolfen can be a little overcritical in his reactions

thanks, i'm doing the best i can. ;)

---

### Post by issih on 2009-03-14
I quite agree that the OP didn't put in anywhere near the necessary effort to give Linux a chance. Frankly, any non windows OS would have failed his test, in fact switching windows versions would fail that perfunctory a glance. If you are not willing to approach Linux on its terms and attempt to learn the differences then you might as well not bother, it is not windows, and it does not work like windows. That doesn't make it worse, it makes it different, you just have to accept that there is a learning curve ahead of you.

We should, as a community, however, accept that the terminal scares new users..its ridiculous, but its true. Therefore those of us that would like to see increased adoption of linux have to take that on board, and find a way to minimise how much new users are exposed to it. Generally terminal use is not needed to solve most tasks, but the forums will send you there in seconds, for obvious and well understood reasons.

Finally, at the risk of slightly offending a few here, it does us no favours to slag off people who behave like this. Yes its annoying, yes people who are ignorant about how things are done and unwilling to learn are frustrating, yes the continual drone of people coming in and complaining that it isn't windows is maddening, but if you rise to it, they have won. Just point out where and how they are wrong, and walk away. Slinging mud just means some of it sticks on us.

---

### Post by betrunkenaffe on 2009-03-14
> **issih said:**
> Finally, at the risk of slightly offending a few here, it does us no favours to slag off people who behave like this. Yes its annoying, yes people who are ignorant about how things are done and unwilling to learn are frustrating, yes the continual drone of people coming in and complaining that it isn't windows is maddening, but if you rise to it, they have won. Just point out where and how they are wrong, and walk away. Slinging mud just means some of it sticks on us.

I have to agree and personally I generally prefer to be helpful, but sometimes you just have to call them for what they are ;)

---

### Post by dhysk on 2009-03-14
soon2bbacktoXP I understand your complaints.  I was a little shocked that you couldn't wright to a usb back when I installed 7.10 i could read and write to all my NTFS file systems just fine although I do know from installs on different hardware every computers experience is a little different.

The only reason I stuck with Linux was because I came into it wanting to learn more about computers in general and found that i was able to fix most my problems and the ones I couldn't fix where less irritating to me than virus scans windows update reboots auto restarting the computer ect.  

Despite what so many people think Linux is not better than windows nor is windows better than Linux.  It's who's troubles are you willing to deal with.  Linux is getting better all the time and different distros all have their pros/cons.  I got tired of having to install all the codes and java and every thing else so on the kids new comp I installed Linux Mint, much easier. Since I'm the one who gets everything working my wife (not a computer person) prefers linux because she feels its easier than windows.  She has been on windows 10+ yrs linux 1 yr.


Basically I feel bad that your experience wasn't good however I'm glad you took the time to give the community your input.  Linux is not for 'everybody' unlike some people believe.  In able to change anything one must be first willing to learn alot of people simply dont have the time to learn a new way to use, maintain, or configure a completely new animal that is an OS.


I'd like to finish with saying I am truly embarrassed with the ways some of even 'senior' members of the form has reacted toward your post.  I've been off the forums for awhile however I remember a time where, at least the posts I read, where dealt with more professionalism and tact.

Thank you for your comments and if you ever have time to play and learn give it another try on a casual basis.  If i tried to continue life from the get go with Linux without windows as my primary I would have been much more frustrated.

---

### Post by 3rdalbum on 2009-03-14
Before you read this post, I'd just like to make it clear that I'm not annoyed with your post. I'd just like to clarify things for you.

I apologise if nobody explained this to you, but Linux is fundamentally a completely different operating system to Windows. As a result, your Windows knowledge doesn't automatically make you a Linux whizz, and my Linux knowledge doesn't mean that I can find my way around Windows. I'm great with Mac OS 9 and I'm pretty good with Linux, but the most basic of problems on Windows cause me to scuttle to the Microsoft Knowledgebase :-)  Linux isn't even designed to imitate Windows - if it was, then I wouldn't like it!

The issues you have complained about are easily resolvable. Your problem with VNC is one case of the difference between Linux distributions and Windows - on Linux, you get "batteries included". Your problem finding how to mount NTFS drives on Linux is a case of "Linux changes quicker than Windows" - if you read that Linux can't write to NTFS partitions, then the post you have read is ancient by Linux standards. A Windows HOWTO from 2006 might still work perfectly well on XP SP3, but a Linux HOWTO from 2006 is probably too old to work on today's distributions.

Linux can write to NTFS partitions very well with an optional download, but flash drives always come formatted as Fat32 for out-of-the-box compatibility with all operating systems. In this case, it appears that you didn't read up about the implications of reformatting your flash drive, before you did it.

The permissions "problem" is an issue that gets posted to this forum every day and answered in roughly 15 seconds :-)  You regard this as a "problem with Vista too", which shows a big lack of understanding. I'm not having a go at you; you're certainly not alone in your frustration with UAC on Windows and sudo on Ubuntu. For security reasons, Linux seperates the user account from the administrator account - in fact the main difference between Windows and Linux is that Linux has always done this, and Windows has only just started doing it and Windows users aren't used to it. Programmers who write Windows programs are having a hard time thinking about how to work within this "new" security system. They are not alone - there are few programmers at Apple who can work within OS X's security system, and they've been at it for almost a decade!

You can easily open a file browser as administrator on Ubuntu. Install the "nautilus-gksu" package from the Synaptic Package Manager. After you have logged out and logged back in again, you can right-click on a folder or a file and choose "Open As Administrator". If you are typing terminal commands that require administrator privileges, just put the word "sudo" before them, which is the command-line equivilant.

I imagine you program in C or C++. I like Python. Your attitude to Linux is a bit like me writing the following:

```

for x in range(0,100):
     print "The number is " + str(x)
sys.exit()

```

Then trying to run it through a C compiler and complaining when it won't compile, then looking up a C tutorial and saying "You have to declare the type of a variable? That's archaic! They need to adopt dynamic typing if they want more people to use C!".

I hope you stick with Linux. If it helps, you can always run it as a dual-boot with Windows and take things slowly. Once you've learnt a bit about why Linux is the way it is, you'll probably appreciate things a lot more. We can always use more programmers!

---

### Post by bowens44 on 2009-03-14
> **soon2bbacktoXP said:**
> 
As for my "qualifications" for using a computer, I've been a computer developer for longer than you have been alive. 


Yeah , right. 

LOL.

---

### Post by solwic on 2009-03-14
I'm going to go ahead and say what everybody ought to be wondering:  isn't it odd that a person tries Linux, hates it, and then goes to the trouble of registering on what is clearly a pro-Linux forum with a name like "soon2bbacktoXP", giving out an e-mail address to create that account, just to complain and whine about an OS that, by their own words, they are no longer using?

Why bother?

Makes me wonder if somebody isn't creating accounts and starting these threads just to keep the forum active.  I mean, I have a pretty cynical (realistic?) view of the world, but even I have a hard time believing there are this many people this - ah - "challenged".  

Besides, if all we're going to do is tell the guy to bugger off, can't we do that by not deigning to reply in the first place?  Isn't a snub, in that sense, better than sinking to the OP's level and slinging mud at one another?

They do this for a reaction.  Me, I say don't give it to them.  Let them look like an idiot, ranting and whining while the rest of us breeze past the post with a good chuckle.

---

### Post by cariboo on 2009-03-15
I think some of these people work for Microsoft, it is well know that they are on [Slashdot]("http://slashdot.org"). The reason they do this is to bring out people like jrock612, wolfen69 and others, and then point fingers and say see, this is what typical Linux users are like.

After all according to Steve Balmer, Microsft see Linux on the desktop as a bigger threat than OS X.
I wouldn't be surprised if some of the comments here show up on a Microsoft blog sooner or later.

Jim

---

### Post by Thanh-BKK on 2009-03-15
Hi :)

Sorry i can only touch one of the mentioned issues..... but when i switched from Windows Vista to Ubuntu some 11 months ago i did it "cold turkey" - the HDD that held Vista and the installed programs  was taken out, a virgin HDD was installed, an Ubuntu-CD was inserted and off i went. 

Never returned to Windows since, and not planning to.

HOWEVER my computer has a second HDD - which holds all of my data. It's a 500 GB HDD with four identically sized partitions, and of course (having used Vista before) this is in NTFS.

Needless to say, now, 11 months later, this is STILL in NTFS and no issues whatsoever - Ubuntu reads and writes this not only "just fine" but certain tasks such as deleting large files (movies, after burning them to DVD) or copying between partitions works a LOT faster than under Vista. 

So yeah, a bit of googling and testing a new OS before stating "it's all shite" is in order, even for a "computer developer" (which i am not, i am just a simple user).

Best regards......

Thanh

---

### Post by solwic on 2009-03-15
> **cariboo907 said:**
> The reason they do this is to bring out people like jrock612, wolfen69 and others, and then point fingers and say see, this is what typical Linux users are like.

Jim

We would be lucky, I think, if the typical Linux user were more like myself and wolfen69, and others.  Far better to be on the straight and narrow, frank about Linux's capabilities, than to sugar-coat everything, trading truth and honesty for an airy Horatio Alger philosophy that's about as deep as the nearest mud puddle. 

But hey, think what you like.  The beauty of freedom is that you're just as free to be wrong as you are to be right.  

Cheers!

---

### Post by Tamlynmac on 2009-03-15
> cariboo907
I think some of these people work for Microsoft, it is well know that they are on [Slashdot]("http://slashdot.org/"). The reason they do this is to bring out people like jrock612, wolfen69 and others, and then point fingers and say see, this is what typical Linux users are like.

Your response suggests that users similar to jrock612 and wolfen69 are being exploited by Microsoft fanboys. 

Most products fail (IMHO) due to a number of variables. However, it's been my experience that product failure is rarely caused by individuals satisfied with the product. If MS views Linux/Ubuntu as a threat, it may be a direct result of individuals like wolfen69 and jrock612. 

The response by jrock612 (I believe) was targeted at this forum and/or it's members. I could be wrong and am certain jrock612 will correct my error. LOL  But one must ask if the behavior exhibited is characteristic of an attempt to provide "Entertainment". 

I refuse to believe that the opinions expressed by a few could be construed as that of all users. Certainly, some on the site you acknowledged may act like Lemmings. If it's a majority, then the site is already infested with individuals that share in the ideology. Thus, anything posted regarding Linux on that site is inherently anti-Linux. Suggesting that individuals here are in some way responsible or are being exploited only diverts attention away from that which jrock612 is proposing and may lend credence to his theory. IMHO, any diversionary attempt to admonish jrock612's theroy might be construed as complicit behavior and suggests deliberate posturing.

Additional Disclaimer:
The above statement are only my opinions. I'm not a marketing, behavioral or entertainment expert and in no wish to represent myself as one.

---

### Post by solwic on 2009-03-15
> **Tamlynmac said:**
> 

The response by jrock612 (I believe) was targeted at this forum and/or it's members. I could be wrong and am certain jrock612 will correct my error. LOL  

Not really at anybody in particular.  But wolfen69 and myself do have a tendency to be straight forward and frank.  No coddling, no hand-holding.  Linux is what it is, and you have to get off your rear and learn if you want it to sing and dance for you.  

Better than than the alternative, which is what both Microsoft and Apple try to sell you. Linux isn't a perfect OS, so why pretend that it is? 

In any case, specifically targeting a single user, or group of users, would be a violation of the CoC.  I've read that thing thoroughly, and you'd have to interpret it very broadly to think I was being insulting to anybody specific with my statements.  :)

But hey, I'm unsubscribing from this thread.  You guys enjoy yourselves.  :)

---

### Post by mdsmedia on 2009-03-15
The OP complains about immature posts, yet his first and second posts on this forum come across as immature, inflammatory, and quite frankly questionable.

He's made 2 posts (in total) on this forum and I think he's taken more time in making these posts than he took in trying to LEARN a NEW OS.

Good luck with Windows, and I have to say, if you're a "computer developer", who's been using computers for so long, I wonder which BC (before computers) version of DOS you used, to be calling the CLI a "DOS prompt".

---

### Post by longtom on 2009-03-16
> **jrock612 said:**
> ... But wolfen69 and myself do have a tendency to be straight forward and frank.  


For me there is a thick line between "straight forward and frank" and "blunt and insulting".
For you there doesn't seem to be - it's all the same to you.

I must admit, I consider myself very lucky that, so far, everybody who helped me in this forum, could see that line very well.  
But than you and wolfen don't get into the Beginners forum very often, I assume.

> But hey, I'm unsubscribing from this thread. You guys enjoy yourselves.

Why would you do that?  Running away?  I must admit - I don't understand....

longtom

---

### Post by lisati on 2009-03-16
> **mdsmedia said:**
>  I wonder which BC (before computers) version of DOS you used, to be calling the CLI a "DOS prompt".

And using a teletype (mentioned by the OP something like 2 days ago) does have a certain noisy charm. Haven't seen or used one of those since the 1980s - wasn't keen on them then, probably wouldn't want one now.

---

### Post by Tamlynmac on 2009-03-16
> longtom
Why would you do that?  Running away?  I must admit - I don't understand....Should you remain in this section for long and respond - you will. ;)

I might suggest that when searching for faults in others, we make sure not to overlook our own. I doubt taunting jrock612 to return will yield a positive result, as I've never seen him react to that. Of course, I could be wrong. 

Both jrock612 & wolfen69 appear to be a very unique individuals, in that they generally express their opinions without fear. This in my opinion is healthy, but can be misinterpreted. They both seem to have excellent written skills and often convey knowledge to those who choose to listen.

Many don't come to this section of the forum seeking guidance, instead they endeavor to disrupt or deliberately undermine the community. These two individuals refuse to permit that activity and have shown a propensity to react. Some may not approve of their methods, but I for one appreciate and enjoy their participation. I have seriously sparred with jrock612 and found him to be intelligent, witty and insightful. I've interacted with both wolfen69 & mdsmedia and would never underestimate either with regards to Ubuntu/Linux functionality and/or their knowledge base.

Simply because someone chooses to be blunt at times, shouldn't suggest they have an altered view of reality, "Perhaps" many of their response are partially based on lessons learned in this forum. :-k

---

### Post by wolfen69 on 2009-03-16
> **Tamlynmac said:**
> 
Both jrock612 & wolfen69 appear to be a very unique individuals, in that they generally express their opinions without fear. This in my opinion is healthy, but can be misinterpreted. They both seem to have excellent written skills and often convey knowledge to those who choose to listen.
just like many others, i still have a lot to learn about computers and tech in general. but i do know enough to have my own pc repair business, and i do it well. that, coupled with the fact that i have installed ubuntu/other distros on almost every conceivable type of computer there is, gives me much more insight in regards to what works (generally speaking) and what does not. while some may not like my style of posting, (right mods?) i feel it is necessary to give a little tough love when i feel it is appropriate. sometimes you need more than just a cup of coffee to open your eyes. i give them a 6 pack of Red Bull.

> **Tamlynmac said:**
> Many don't come to this section of the forum seeking guidance, instead they endeavor to disrupt or deliberately undermine the community. **These two individuals refuse to permit that activity and have shown a propensity to react.** 
someone has to make a stand.
> **Tamlynmac said:**
> Some may not approve of their methods, but I for one appreciate and enjoy there participation. I have seriously sparred with jrock612 and found him to be intelligent, witty and insightful. I've interacted with both wolfen69 & mdsmedia and would never underestimate either with regards to Ubuntu/Linux functionality and/or their knowledge base.
thank you. it's nice to be appreciated once in a while. my intentions are good, i can assure you.
> **Tamlynmac said:**
> **Simply because someone chooses to be blunt at times, shouldn't suggest they have an altered view of reality**, "Perhaps" many of their response are partially based on lessons learned in this forum. :-k
most people that know me well will tell you that i'm a very grounded person, and see things for what they are. i refuse, however, to pull punches to avoid hurting someone's feelings. this whole "politically correct" thing can get out of hand sometimes. but i digress.

cheers.

---

### Post by mdsmedia on 2009-03-17
> **Tamlynmac said:**
>  I've interacted with both wolfen69 & mdsmedia and would never underestimate either with regards to Ubuntu/Linux functionality and/or their knowledge base.

I'm not sure how I got in there, and I WOULD underestimate myself with regards to Ubuntu/Linux functionality. I wouldn't, however, underestimate that of wolfen69 and jrock612.

---

### Post by bendib on 2009-03-17
Get out of our community. Anyone who will not learn linux because it forces them to get off their butt and actually do something else besides eat cheese curls is not welcome here. You should have given it another try, but you didn't. You were too lazy to learn how to use linux when you would have loved it if you really gave it a good try. We are not mad you are going back to windows. We are mad at your poor character.
I'd better go take a nap before I end up going to redmond and choking Gates.

---

### Post by hyper_ch on 2009-03-17
[http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102)

---

### Post by Dandalf on 2009-03-17
I don't believe the attitude of the community as reflected in this thread. This is the kind of thing I tell my friends about when they ask something like "If linux is so good why doesn't everyone use it" or somesuch. It's horrible! I can't believe the elitism. Can you all take a few steps back and look at what you're doing? "If you can't learn how to do things manually that other operating systems do for you you're not good enough". This stubborn, closed, elitist community is what's stopping - and what has stopped - Linux from becoming truly mainstream.

It's not a case of "I don't want to learn to use the steering wheel" it's "I don't want to build a vehicle from scratch to drive"

---

### Post by Therion on 2009-03-17
> **soon2bbacktoXP said:**
> ... If I have to open the terminal window then I'm already halfway down the road to MS land again.
That's why there will, hopefully, always be choices available to people.  

If you're not prepared to do things the "Linux Way" then by all means, stick to Windows.  

I'm about as concerned with your choice of Operating System as I am your choice of breakfast cereal.

---

### Post by darksideforge on 2009-03-17
> **ugm6hr said:**
> Indeed, the problem is you didn't know what you were doing; more importantly, you didn't ask someone who does.

In case anyone else finds this:

**ntfs-3g** can be installed with a few clicks, and allows write access to NTFS drives

Ubuntu has a built in VNC / Remote Desktop server (you don't need to install anything) - a few clicks in System -> Preferences -> Remote Desktop.  In fact, it also has 2 remote desktop viewers built in.

Graphics drivers can be a little trickier, but most are resolved with a few clicks using **envy-ng**

Opening a Terminal is often faster to install drivers / software etc, but is not the only way.

First, I respect anyone's decision to use Micro$hit Windoze instead of Linux. Back in October I got so pissed at Vista dumping me all of the time, running my laptop hot all of the time, and constantly running out of virtual memory, not to mention giving me the BSOD on more than one occasion, that I simply downloaded an .iso Image Burner program (k3b as i recall) and then downloaded the .iso-386 for Ubuntu. I also downloaded a DSL distro as well as a Fedora (8, maybe?). I ended up with Ubuntu and haven't looked back since. When I started, I didn't know Linux from Unix from Fortran...nothing! I found this message board and have loved almost every minute of it (with the small minor exception of an a$$hole on the Server forum who no longer bothers me).

ugm6hr, the reason I quoted you here was to say THANK YOU for posting those little quick-fixes. I learn something new every time I'm on here it seems...I've often wondered about a flash-drive fix and this worked perfectly for me....took me 35 seconds to download via CLI and would have probably only taken a minute or two via Synaptics. I still have issues with ssh and vnc so if you have any words of wisdom for me in that area, please feel free to throw them my way. :-)

I now run 3 workstations and a laptop on 9.04 Jaunty and 1 workstation on 8.04 Hardy and one workstation on 8.10, as well as an in-production server on 9.04_x64....and i love every minute of it. They're not perfect yet, but they will be.

---

### Post by PukingPenguin on 2009-03-17
> **Dandalf said:**
>  This stubborn, closed, elitist community is what's stopping - and what has stopped - Linux from becoming truly mainstream.

No, it isn't. What has stopped Linux (if, indeed, something has!) is the fact that until a couple of years ago it was IMPOSSIBLE to buy a tier-one manufactured computer with Linux installed. Can you spell MONOPOLY? Sure, I knew you could.> 
It's not a case of "I don't want to learn to use the steering wheel" it's "I don't want to build a vehicle from scratch to drive"
Hyperbole rears it's ridiculous head again. It's more like not being willing to learn to drive a different car than the one you got your license on.
Pfft. Wolfen69 and the others were right to spank the troll.

---

### Post by darksideforge on 2009-03-17
> **hyper_ch said:**
> [http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102)


hyper,
I don't think I've ever had an opportunity to thank you for anything or any of your posts, so I wanted to thank you for posting this link...IT'S AWESOME!

So, Thank You!  :-)

---

### Post by mdsmedia on 2009-03-17
> **Dandalf said:**
> I don't believe the attitude of the community as reflected in this thread. This is the kind of thing I tell my friends about when they ask something like "If linux is so good why doesn't everyone use it" or somesuch. It's horrible! I can't believe the elitism. Can you all take a few steps back and look at what you're doing? "If you can't learn how to do things manually that other operating systems do for you you're not good enough". This stubborn, closed, elitist community is what's stopping - and what has stopped - Linux from becoming truly mainstream.

It's not a case of "I don't want to learn to use the steering wheel" it's "I don't want to build a vehicle from scratch to drive"

Quite a closed minded, selective but generalist at the same time, response, considering the (well I'm not sure if you even considered the) post of the OP.

He has made TWO posts in the forum, both in this thread. The replies are not elitist, the opening post was closed minded, from someone who is not willing to acknowledge that he is trying to use a NEW OPERATING SYSTEM without bothering to learn anything about it.

Do you think he just picked up Windows and used it without learning anything about it, either as he went along, or before starting? That's what he wants from Linux. 

It's not elitist, it's realistic.

---

### Post by solwic on 2009-03-17
> **mdsmedia said:**
> 
It's not elitist, it's realistic.

Wisdom flies from your fingers, sir.  

+1.

---

### Post by ren48185 on 2009-03-17
> **soon2bbacktoXP said:**
> I was attempting to provide the developers with my "user experience" so that they might attempt to continue working positively on their os.

Your juvenile reply just furthers the perception that linux is only for a minority of people.   

As for my "qualifications" for using a computer, I've been a computer developer for longer than you have been alive.  I've worked on os's that you've never heard of and know a little about those that work and those that are just a pain in the neck.

In the 21st century, I believe we should be well past the DOS prompt operating system.  tty teletype terminals are pretty ancient.

At any rate, your comments do nothing to further linux as anything but a cult os.

I normally would not respond...but if you are a "computer developer" you would think that you would have learned Linux or Unix. I am only a CCNA and I have discovered several linux distros in my experience, especially with servers. I hope to not run into any product you have developed. If I can figure Ubuntu out, anyone can. If they want to.

---

### Post by Tamlynmac on 2009-03-17
> Dandalf
I don't believe the attitude of the community as reflected in this thread. This is the kind of thing I tell my friends about when they ask something like "If linux is so good why doesn't everyone use it" or somesuch. It's horrible! I can't believe the elitism. Can you all take a few steps back and look at what you're doing? "If you can't learn how to do things manually that other operating systems do for you you're not good enough". This stubborn, closed, elitist community is what's stopping - and what has stopped - Linux from becoming truly mainstream.

It's not a case of "I don't want to learn to use the steering wheel" it's "I don't want to build a vehicle from scratch to drive"

After two years and all of twelve posts you've come to this conclusion. :-k

I think we've all heard the foolish phrases - it's not ready for prime time or because of the elitists it will never be mainstream, etc. Maybe you should spend some time reviewing the help sections of this forum and then reconsider your statement.

This elitist community helps people everyday (in the assistance sections) to resolve issues by sharing information and knowledge. I've not seen any new user snubbed or refused assistance in those sections, by the so called elitist. They do this for free and ask nothing in return. Not even worshipers. :)

When passing judgment or endeavoring to profile an entire group of people (community), one really should investigate before generalizing.

---

### Post by wolfen69 on 2009-03-18
> **Tamlynmac said:**
> After two years and all of twelve posts you've come to this conclusion. :-k

I think we've all heard the foolish phrases - it's not ready for prime time or because of the elitists it will never be mainstream, etc. Maybe you should spend some time reviewing the help sections of this forum and then reconsider your statement.

This elitist community helps people everyday (in the assistance sections) to resolve issues by sharing information and knowledge. I've not seen any new user snubbed or refused assistance in those sections, by the so called elitist. They do this for free and ask nothing in return. Not even worshipers. :)

When passing judgment or endeavoring to profile an entire group of people (community), one really should investigate before generalizing.

that was a great read. i didn't know it was you until the end. 

anyway, thanks for that great story.

---

### Post by hyper_ch on 2009-03-18
> **darksideforge said:**
> hyper,
I don't think I've ever had an opportunity to thank you for anything or any of your posts, so I wanted to thank you for posting this link...IT'S AWESOME!

So, Thank You!  :-)

I did not write that post but it is awesome ;)

---

### Post by Ericyzfr1 on 2009-03-18
If you already tried linux many years ago and came back with the same attitude....Why bother? you just wasted yourself valuable time...and ours..But we had a good laugh!!

---

### Post by BrendanMark on 2009-03-18
A Developer of many years unwilling to perform the most basic Tech Support task and howling at the moon that it isn't already set up for him? Business as usual. :P

Seriously though, there is an attitude there that pervades the market: if I have to touch a command line/terminal then it's bad juju.

I'm a Tech Support guy (I have done development, so the above comment really only applies to the precious few - but they do exist in DevelopmentLand amongst cocooned larvae) so welcome the terminal - my few complaints with Ubuntu are more system-level why-isn't-this-real-Unix kinda trivia.

But for so many in/from the MS desktop world, Touch Command Line = Bad Juju. :(

---

### Post by betrunkenaffe on 2009-03-18
> **BrendanMark said:**
> A Developer of many years unwilling to perform the most basic Tech Support task and howling at the moon that it isn't already set up for him? Business as usual. :P

Seriously though, there is an attitude there that pervades the market: if I have to touch a command line/terminal then it's bad juju.

I'm a Tech Support guy (I have done development, so the above comment really only applies to the precious few - but they do exist in DevelopmentLand amongst cocooned larvae) so welcome the terminal - my few complaints with Ubuntu are more system-level why-isn't-this-real-Unix kinda trivia.

But for so many in/from the MS desktop world, Touch Command Line = Bad Juju. :(

That's funny, I did tech support with the public a little over a year ago for a few years, I mostly had them in the dos prompt doing things. Most I ever had was people not understanding that the text was moving up in the black screen (so would read everything off, everytime).

---

### Post by BrendanMark on 2009-03-18
Tech Support for the public or clients is different from Tech Support for developers - at least in my experience. And I was only referring to the precious few. ;)

---

### Post by betrunkenaffe on 2009-03-19
The people that announced they were developers or "professionals" tended to be annoying, never wanted to listen because "they knew best".

I will admit it was easier with 99% of those that didn't know anything :)

---

### Post by solwic on 2009-03-19
> **hyper_ch said:**
> [http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102)

I'm not sure which is more disturbing...that such an article was written, or that a forum administrator wrote it.

It scares me to think there's such rampant pigeonholing and profiling and segregating in a community supposedly dedicated to "humanity towards others".

No offense intended to anybody involved in the conception, writing, posting, or linking of that article.  Just my opinion.  I'm sure nobody here agrees with me (although this community surprises me every day, so...).

---

### Post by jwbrase on 2009-03-19
> **Tamlynmac said:**
> Being a "developer", you should understand that when investigating any software one must RTM and comprehend the intricacies or said software.

To be scrupulously fair, I've found the documentation on Ubuntu (or 8.10, at least) so poor that reading the manual is no help at all. I could probably find ten windows in ten minutes whose "help" buttons bring up a help file that mentions tabs and options that aren't even in those Windows.

Otherwise, Ubuntu rocks.

---

### Post by Tamlynmac on 2009-03-19
> jwbrase
To be scrupulously fair, I've found the documentation on Ubuntu (or 8.10, at least) so poor that reading the manual is no help at all. I could probably find ten windows in ten minutes whose "help" buttons bring up a help file that mentions tabs and options that aren't even in those Windows.

Otherwise, Ubuntu rocks. 	

To be perfectly honest, I can't speak to 8.1, as I'm still using 8.04 and will continue to do so until the next LTS release. I can state, that documentation for Hardy has met all my requirements. I've found that everything I need to accomplish can either be located by Googling or searching here. Worst case, I could simply ask a question in one of the help sections of this forum. That's what makes this community outstanding. Don't know - just ask.

IMHO if one isn't satisfied with the documentation, logic might suggest they get involved in the community and assist in the production of future user guides instead of simply pointing it out. Just a thought.

---

### Post by jwbrase on 2009-03-19
> **Tamlynmac said:**
> To be perfectly honest, I can't speak to 8.1, as I'm still using 8.04 and will continue to do so until the next LTS release. I can state, that documentation for Hardy has met all my requirements. 

Well, what I suspect is that the documentation for Hardy has just been ported over to Intrepid without being updated. It simply doesn't match my system.

For example, the Help file for the Mouse Preferences window claims that there are three tabs: "Buttons" "Pointer" and "Motion." I have two tabs: "General" and "Accessibility." Most of the options listed for "Buttons" and "Motion" are on the "General" tab, one of the options from the pointer tab has been moved to Appearance > Theme > Customize > Pointer, and the other "Highlight pointer when you press Ctrl," seems to have disappeared, though you might think it would be on the "Accessibility" tab. 


> I've found that everything I need to accomplish can either be located by Googling or searching here. Worst case, I could simply ask a question in one of the help sections of this forum. That's what makes this community outstanding. Don't know - just ask. 

True. But documentation that seems to have been written for a different version is still a bit annoying. And if out-of-date documentation is typical for Linux, it probably contributes to Linux's *reputation* for user unfriendliness, regardless of its actual user friendliness or lack thereof. I can handle it or I would've written Ubuntu off a month ago. But some people might find it a real barrier.

> 
IMHO if one isn't satisfied with the documentation, logic might suggest they get involved in the community and assist in the production of future user guides instead of simply pointing it out. Just a thought.

True, although those who most want/need good documentation are generally the least qualified to write it.

---

### Post by Tamlynmac on 2009-03-20
jwbrase

> Well, what I suspect is that the documentation for Hardy has just been ported over to Intrepid without being updated. It simply doesn't match my system.

As I indicated earlier I have no idea with regards to 8.1 documentation. You really need to address this with other users of 8.1.

> True. But documentation that seems to have been written for a different version is still a bit annoying. And if out-of-date documentation is typical for Linux, it probably contributes to Linux's *reputation* for user unfriendliness, regardless of its actual user friendliness or lack thereof. I can handle it or I would've written Ubuntu off a month ago. But some people might find it a real barrier.


As stated, I've had zero problems with 8.04 documentation and have heard all the references to Ubuntu not being ready for prime time, an elitist OS, user unfriendliness, etc. Yet, it's been my experiences and those I've assisted (including installs) that the documentation issue only seems to be a platform for those that wish to spout negativity with regards to Linux/Ubuntu. When considering all the available support in this forum alone, I find it hard to accept this as a motive for bashing Linux/Ubuntu. Beyond the need to find fault. 

We should also keep in perspective the fundamental fact that Ubuntu is Free. When individuals compare Ubuntu to other profit motivated OS, I'm always impressed. Even when they spend time bashing it. For this reveals the threat Ubuntu poses. Or they wouldn't waste time attacking it. When they bash it, some that read their rants may investigate and realize Ubuntu's potential. It's all good in my opinion.

> 
True, although those who most want/need good documentation are generally the least qualified to write it. 	

Last I checked, one of the best ways to become enlightened is to get involved. Of course some may only wish to stand on the sidelines, but shouldn't they be the first to show humility? I'm a humble person and have found in my life that the gifts I receive from others are treasures and have significant value. Ubuntu/Linux is a gift, there's no charge or commitment and yet many find fault and/or seek excuses to complain. I would strongly suggest you get involved and in doing so - "make a difference". For example check this site out:
[http://www.stchman.com/](http://www.stchman.com/)

If you truly believe Ubuntu rocks (as I do) then join the community and become active. If my health permitted - I certainly would do more. As I believe it's a worthy cause. I still attempt to help in the assistance sections when possible and if that is all I can do, at least I'm actively endeavoring to participate and not just finding fault. Finding fault with anything is simple, helping to resolve issues and making a difference - that can be a lot tougher.

---

### Post by longtom on 2009-03-20
> **jrock612 said:**
> I'm not sure which is more disturbing...that such an article was written, or that a forum administrator wrote it.

It scares me to think there's such rampant pigeonholing and profiling and segregating in a community supposedly dedicated to "humanity towards others".

No offense intended to anybody involved in the conception, writing, posting, or linking of that article.  Just my opinion.  I'm sure nobody here agrees with me (although this community surprises me every day, so...).

+1

I was also just a bit...I don't know...queezy.  Is that how the forum administration is seeing us users?

I can see the funny side of it so, however, some of it wasn't funny.

---

### Post by Perfect Storm on 2009-03-20
[img]http://www.imageviper.com/displayimage/131307/0/troll.png[/img]
...aaaand we're closing the thread of the troll.


Please use the report if you see a thread/post that the forum staff should take a look at.
Thanks.



regards
A.I.
Ubuntu Forum Staff

---

