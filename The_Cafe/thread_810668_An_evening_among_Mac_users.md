---
title: "An evening among Mac users"
date: 2008-05-28
forum: The Cafe
---

### Post by aysiu on 2008-05-28
I wasn't quite sure where to put this, so another moderator can move it to a more appropriate subforum if it gets reported.

I had an interesting experience recently, in which I spent the evening with four Mac users. All of them griped about how many problems they had had with Windows (or "PCs," as they say) and how everything "just works" now that they've moved to Macs. 

Oddly enough, two of the Mac users seemed to be into open source programs (WordPress, Firefox, NeoOffice, etc.), and one (the less tech-savvy of the two) asked the other how open source can make money, and he tried his best to explain (he is a designer and has been involved in developing open source CMSes) how open source can be profitable. I tried my best to explain it, too, but for some reason the point didn't sink home. Eventually she just accepted that it was cool to have open source programs available, whether they make money or not.

She also had recently received an old Powerbook and needed help transferring her documents from one hand-me-down laptop to another hand-me-down laptop, as she had thought copying the files to an external drive, copying them over to a folder in /Users/*herusername* would work as long as she later created a user called *herusername*.

So my wife, I, and this designer guy all were huddling around her computer trying to figure out how to get the permissions all set properly in a new user. Problem is that the person she got the laptop from had the laptop set to auto login to his own account and didn't tell her the password. I tried booting into single-user mode, but I didn't realize you had to remount the drive in order to make it read-write, so I couldn't change the password through single-user mode. Eventually, she called the guy who gave her the laptop and got the password, and she used it to make her user an administrator, but they had trouble recursively changing ownership of all the copied files through the GUI, so I had to use the terminal and *sudo* to move everything over to her account's ownership, and then I ran the Disk Utility *Repair Permissions* function just to be safe.

Through this all, it came out that she Macs did not "just work," not for the user in question. She still perceived them to "just work," as did the three other Mac users there, but she'd had weird problems. For example, something happened on her old hand-me-down laptop that corrupted her account so that new windows and menu dropdowns all appeared behind the current window. The only fix was for someone else to create a new account for her. She also had problems ejecting CDs (it was an old laptop, granted). Worse yet, to all you Mac users who think Macs are intuitive, she had no clue how to install software. She thought you had to drag the white disk to the Applications folder instead of dragging what's inside of it there (I had a similar problem when I first encountered Mac OS X - I didn't realize I had to drag anything. I didn't know what to do with the white disk).

Eventually, everything got all sussed out. I showed her how to use iTunes and iPhoto, and she was very excited about it all. The bummer of it all is that she'd be the perfect Ubuntu user (all she does is email, use Firefox, organize photos, listen to music, and type the occasional Word document), but I didn't have a spare Ubuntu laptop to give her, and configuring Ubuntu on a Powerbook isn't fun.

What did I take away from all this?

[list][*]A lot of Mac users think Macs are better than PCs.[*]Happy Mac users can think everything "just works," even when it doesn't. [*]Bash/terminal knowledge doesn't directly transfer from Ubuntu to Mac. [*]Macs are not intuitive. For a user who isn't into exploring, no user interface is intuitive - things need to be taught, even software installation, even adding songs to the iTunes library (yes, I had to teach her that).[/list] Overall, if Mac users are happy with their Macs, that's great. I'm glad they're happy with their Macs. I just think it's funny how they keep insisting Macs have no problems while at the same time commiserating about corrupt user profiles and the need to run Disk Utility Repair Permissions operations. 

I'm sure Ubuntu users do something similar.

---

### Post by bsharp on 2008-05-28
I really used a Mac for the first time in a graphical design class last semester, and the only reason they "just work" is because everything is done for the user, to the point where it is unhealthy. In order to effectively use a computer, the user has to have *some* understanding how it works and believing that the end-user is too stupid to learn to do more than drag-and-drop is Apple's major shortcoming, IMO.

Since I was considered the "computer guy", I was tasked with fixing the problems even though I made it clear to the teacher that I had never used a Mac before, and I found that "Windows rot" applies to Macs as well (even though technically it should be "Apple rot" :)). Apple markets their OS as superior in every way, with no apparent weaknesses, and this just isn't true.

---

### Post by toupeiro on 2008-05-28
Cool read :)  I find myself in a lot of casual social situations like that, but admittedly never 4 mac users at one time.  Kudos to you on that one ;)

The one I still hear a lot is how Macs have no parallel when it comes to graphics..  I wish I could show those people what my userbase can do graphically on Linux at my work...  I think when people talk about their respective OS of choice and cannot be objective to the fact that it can be paralleled, or surpassed, those are the loyalists.  There is nothing wrong with loyalists.  Loyalists are good in that they can usually list the comparative points about their OS better than most people can, but they fall short in accepting where their product falls short or has problems.  I'll be the first person in a conversation to say that Linux has problems, but I can usually follow that up with, however the problems you are currently having I do not experience because *<insert explanation here>*...    

I used to try to challenge any loyalist, be it windows, Mac, or linux, just to see how unfaltering their case is when certain points are discussed. I don't anymore because I've come to realize that they are loyal to their choice because it works for them, obviously as well as my choice works for me.

---

### Post by aysiu on 2008-05-28
> **bsharp said:**
> I really used a Mac for the first time in a graphical design class last semester, and the only reason they "just work" is because everything is done for the user, to the point where it is unhealthy. In order to effectively use a computer, the user has to have *some* understanding how it works and believing that the end-user is too stupid to learn to do more than drag-and-drop is Apple's major shortcoming, IMO I prefer not to use the term *stupid* in this context, but the user I was helping out that evening had difficulty even using drag-and-drop. I think sometimes advanced users and even intermediate users sometimes forget (regardlesss of platform - Ubuntu, Windows, Mac) how many little things they take for granted that beginner users need to be shown step by step (even dragging and dropping).

---

### Post by Ub1476 on 2008-05-28
Well, I must admit that I'm glad we don't get pop-ups every second telling us how to do things..

---

### Post by aysiu on 2008-05-28
> **Ub1476 said:**
> Well, I most admit that I'm glad we don't get pop-ups every second telling us how to do things..
I really hate those, because I don't really know anyone who makes use of them.

Everyone I know figures things out for themselves or asks someone else (a real person) how to do things. I don't know anyone who relies on pop-up messages to figure out how to do things.

---

### Post by notwen on 2008-05-28
> **Ub1476 said:**
> Well, I most admit that I'm glad we don't get pop-ups every second telling us how to do things..

LOL, those are the best.

---

### Post by blueturtl on 2008-05-28
The Mac's alleged ease of use can mostly be attributed to how complex some tasks are once you have the necessary background information. I don't think any operating system can be intuitive to it's user until the user knows a key amount of principles for it's use.

I was an expert Windows user once, but I still thought the system was hard to use. Not hard because I didn't know how, but because I thought there were too many ways to do things with too many steps and way too much overlapping. Essentially the system allowed for itself to be broken in ways that to a user would seem like normal use of the operating system.

Apple in turn does it's best to disguise the computer as an appliance (which it is not since it's a gateway technology). You don't want to know how a toaster works, you just know that you put bread in it and pull a lever or push a button. The same philosophy is supposed to apply to Macs. Once you know what to do, it's really easy and quick. You still have to know though. Unfortunately users can always come up with something they want to do that the Apple techs didn't and that's when those odd situations in OS X happen.

"Just work" I think in computer world means the same as "set and forget". Once you learn it's easy, or something like that. Pretty much any OS but Windows can provide that... The Mac versus PC debate is really the Mac versus Windows debate, I don't think the average Mac user knows about any other PC operating systems.

But how does one compare something designed as an appliance with a limited set of use cases to something which is clearly not tailored to suit any number of use cases and has less control over how those uses are approached?

---

### Post by smoker on 2008-05-28
> **aysiu said:**
> ... The bummer of it all is that she'd be the perfect Ubuntu user (all she does is email, use Firefox, organize photos, listen to music, and type the occasional Word document), but I didn't have a spare Ubuntu laptop to give her, and configuring Ubuntu on a Powerbook isn't fun...

pity you never had a laptop with ubuntu with you, you could have showed them a 'real' touch of class:)

---

### Post by aysiu on 2008-05-28
> **smoker said:**
> pity you never had a laptop with ubuntu with you, you could have showed them a 'real' touch of class:)
I just say it's a bummer because rarely do I see the perfect opportunity to show someone Ubuntu. People either have weird, quirky computing habits or aren't open-minded enough to try something new.

She seems happy with Mac OS X, though.

---

### Post by Koori23 on 2008-05-28
The thing that throws me.. Always has.. When we talk about "Mac Users" or "Windows Users" it's almost like we're talking about racial or religious groups.. They get profiled the same way. Almost like a stigma is attached to each group.

---

### Post by madjr on 2008-05-28
> I showed her how to use **iTunes** and iPhoto, and she was very excited about it all. The bummer of it all is that she'd be the perfect Ubuntu user (all she does is email, use Firefox, organize photos, listen to music, and type the occasional Word document)

too bad you showed her how to use itunes, now she going to get used to it.

it's a road block if she ever wants to use ubuntu in the future.

anyway, when kde**4.2** is out i'll be installing that to a mac beginner. It's far more intuitive then the mac interface and trains them on a linux interface without they even realizing it :)

also in my experience, 90% of users willing to switch to mac are great candidates for Ubuntu. They'll just use what they try/learn first (either be ubuntu or macOS)

i was about to get a macbook before i knew about ubuntu. But since am tech savvy i decided to see how linux was coming along, so after some googling and distro testing (i tested about 4 distros) i finally found ubuntu. Saved me a buttload of $

---

### Post by tdrusk on 2008-05-28
Good read. 

I rarely bother trying to convert people, just because I don't want to deal with their hassles, which I sometimes do anyway. Sometimes Windows and Mac are just easier to fix. Other times, I wish I just gave them Linux.

---

### Post by LaRoza on 2008-05-28
> **aysiu said:**
> 
What did I take away from all this?

[list][*]A lot of Mac users think Macs are better than PCs.
[*]Happy Mac users can think everything "just works," even when it doesn't. 
[*]Bash/terminal knowledge doesn't directly transfer from Ubuntu to Mac. 
[*]Macs are not intuitive. For a user who isn't into exploring, no user interface is intuitive - things need to be taught, even software installation, even adding songs to the iTunes library (yes, I had to teach her that).[/list] 

Overall, if Mac users are happy with their Macs, that's great. I'm glad they're happy with their Macs. I just think it's funny how they keep insisting Macs have no problems while at the same time commiserating about corrupt user profiles and the need to run Disk Utility Repair Permissions operations. 

I'm sure Ubuntu users do something similar.

Having some degree of experience in many OS's, I see this a lot also. I have seen that happen to many people. A guy (sort of related) uses Windows (although he is entirely against Corporations and won't shop at FYE even, let alone Walmart) and justifies it. Ubuntu is on his PC (it is a family computer, so he isn't the only user) along with XP. I configured both of them. They both "just work". XP is fast, Ubuntu has its codecs and all the cool stuff. I even have Google Earth on both PC's. The printer works in both (out of the box in Ubuntu, lengthy driver install in XP). Both have OpenOffice and Firefox.

Yes, this guy still finds reasons to use Windows and MS Office although he does nothing that requires that. (Also note I had to show everyone how to use the printer and do things in XP)

Ubuntu has all the desktop icons ready. It has the IM accounts in Pidgin. Compiz works like a dream and all the Flash/Java things are ready. In fact, it is faster than XP. The only reason they actually use it (to date) is to play the games on it. (For all those that say Windows is great for its games, keep in mind this story)

I guess it is part of some humans to stick with what they are used to, even if their knowledge of it isn't any greater. Surprised me because of his extreme anti-corporate views.

---

### Post by Kinst on 2008-05-28
I'm confused. I thought macs and linux both used bash and had a pretty much identical terminal?

What's the difference?

I have no experience with the mac operating system.

---

### Post by aysiu on 2008-05-28
> **Kinst said:**
> I'm confused. I thought macs and linux both used bash and had a pretty much identical terminal?

What's the difference?

I have no experience with the mac operating system.
There are random subtle differences.

For example, in Mac OS X's terminal, you can't run ```
sudo fdisk -l
``` In Mac OS X's single-user mode, if you want to change a user's password you first have to ```
mount -uw /
``` before you can ```
passwd *username*
``` In Ubuntu's recovery mode, you can just ```
passwd *username*
``` without remounting the drive.

---

### Post by zmjjmz on 2008-05-28
Pretty much 90% of everyone I know is switching to Mac OSX.
They need my advice on things, and I usually give them free software (like GnuCash or NeoOffice), I **don't** recommend Safari and either way most people like FF more.

---

### Post by Dragonbite on 2008-05-29
This is a good read.

My most recent Mac experience was about 3 years ago (just under) in the Library and I wasn't impressed. I wanted my Gnome or KDE back.

I'm curious about Macs. In the beginning I drooled over the Macs like many of my friends. I started with Linux in part because I needed something more up-to-date than Windows 98 and couldn't afford a Mac (or buying Mac versions of all of my software). Since then I've gotten into Linux I have no desire for a Mac anymore.

---

### Post by NikoC on 2008-05-29
Said it a million times before: every system has it's goods and it's bads! And to make it more complicated: what is 'good' for one user, might be 'bad' for another one! I myself have an old desktop with XP, a laptop with Ubuntu (Hardy, which has shown no flaws and runs very stable despite the experience of many other users) and a MacBook Pro with Leopard. Yet I can't really say one OS is better than the other, they're just different... (of course, XP is a bit outdated now :) )

---

### Post by ZarathustraDK on 2008-07-24
[IMG]http://thegreatgeekmanual.com/images/humor/motivational/february/motivational-poster-mac-users-market.jpg[/IMG]

Just stumbled over it. :popcorn:

---

### Post by TBOL3 on 2008-07-24
I remember that when I used a mac, it was like that. (I used a mac for a year of my life).  Everything was 'Microsoft's or windows'" fault.  Even when there was no way I could blame it on something else, I would say, "I'm running OS X on a G3, of course it's not 'perfect'". I even blamed the user, even when I realized it was the computers fault.

Although, to be fair, the computer was old, thus it didn't work as well with newer hardware.

---

### Post by koji042 on 2008-07-24
Good read. I think it would make a nice article.

I remember the first time I used a Mac. Before then, I had always thought that Macs were easy to use, but that was only from word of mouth and the internet. I was tinkering with my teacher's Mac, and first thing that caught me was the fact that I couldn't navigate the UI at all. It actually felt counter-intuitive, I had no idea how the menus functioned, and the 1-button mouse drove me crazy. But like everyone has said, I probably wasn't comfortable with it because it was unfamiliar and I had not taken the time to effectively learn it.

---

### Post by Lord Xeb on 2008-07-24
This is great read. I though there would be a lot of flaming  here, but so far, it has been really good and has given me an insight into how people think and why it so hard to switch people.




I will now give my experience with the "Works" (Mac, windows, an Linux):


From my experience, Windows is like this:

For the everyday user who has known only windows and wants something that gets them from point A to point B and so one. It is a nightmare somethimes when things go wrong and when you do not have an AV, it becomes even worse.... Even with the AV, for an average user who knows little about computers and the treats that come with them, it still get them into trouble. It breaks with less than a whim and can sometimes never be right after fixing it. Reinstalls are a ********* and finding drivers is even worse. Great for gaming and such, great compatibility. People need to be educated before using it about the risks. :/

Linux;

I love this OS. Though I have had problems, the freedom to go about fixing it without restrictions is amazing. It took me about a week to get use to Ubuntu after going cold turkey (not intentionally) and after that, it has been an amazing experience and I have learned so much about computers just from it alone. It isn't for the "average user" since some programs have to be installed manually and you cannot just go to the local tech store and get help. Its compatibiliy is great and I love since it runs fast and stays running fast. Fixing this easy and fun (even when it gets frustrating). Also, I do not have to bother with those damn AV :D

Mac:

I think a mac is just a really over priced, well made version of Linux (well, they are based on the same thing). Macs have been around since the early 80s so they have great quaily, but also a great price. Most of the time, it is plug and play, but there is not as much stuff out there for it (hardware wise). It isn't really for the average user either since the drag and drop thing. There inovation is great and intersting. I just think Mac is great for those who like it.


Personally, what OS you choose is your choice. I Like going to a cyber cafe and start whiping out the old compiz fusion and expo. Then I start opening and using multiple programs and people start raising eye brows an they ask "what is that" I just say it is Linux. They just look at me funny and walk off.

---

### Post by cprofitt on 2008-07-24
Great story...

I will have to contemplate sharing my story when I am done...

(yeah I like using '...')

I will give you the basics of it and if I decide to later I will make my own thread...

I am currently assisting a Mac 'Sys Admin' to manage his OS X clients, build his servers, and connect 20% of his clients to Windows via AD and SAMBA... it has been interesting... and to post more I would have to lower my emotional level towards the project and learn to be like aysiu.

---

