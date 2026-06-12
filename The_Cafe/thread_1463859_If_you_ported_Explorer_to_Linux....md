---
title: "If you ported Explorer to Linux..."
date: 2010-04-27
forum: The Cafe
---

### Post by swoll1980 on 2010-04-27
You could switch 90% of the world to Linux with out them knowing it.

---

### Post by doas777 on 2010-04-27
and since explorer would appear to be a slew of API calls, the effort would likely complete wine as well.

---

### Post by Doctor Mike on 2010-04-27
First you'd have to have 90% of the world using I Explorer... It's pre-packaged, doesn't mean it's used...

---

### Post by doas777 on 2010-04-27
> **Doctor Mike said:**
> First you'd have to have 90% of the world using I Explorer... It's pre-packaged, doesn't mean it's used...
I think we are talking about explorer.exe (the desktop and window manager), not iexplore.exe the web browser.
but you are right, i'm sure that there are features and usecases for explorer that no human has ever used.

---

### Post by swoll1980 on 2010-04-27
> **Doctor Mike said:**
> First you'd have to have 90% of the world using I Explorer... It's pre-packaged, doesn't mean it's used...

Explorer is the window's desktop environment not the browser.

---

### Post by 98cwitr on 2010-04-27
No start menu...people would be freakin lost. I hope he's talking about Internet Explorer too b/c 90% of windows user have no idea what Windows Explorer even is or have ever used it.

---

### Post by doas777 on 2010-04-27
> **98cwitr said:**
> No start menu...people would be freakin lost. I hope he's talking about Internet Explorer too b/c 90% of windows user have no idea what Windows Explorer even is or have ever used it.
but thats exactly the beauty of the idea (and explorer.exe does contain the start menu, though most of it's functions are calls to user32.dll and shell32.dll). if you were to pull it off, most users would never know. most of the windows system they know is in explorer and the assorted cpl/msc panels that they invoke on occasion. since they use explorer all day everyday without knowing it, that makes it all the easier to pull the wool over their eyes.

---

### Post by Confuzius on 2010-04-27
Solitaire.
Minesweeper.

---

### Post by Doctor Mike on 2010-04-27
> **swoll1980 said:**
> Explorer is the window's desktop environment not the browser.OK, I have Windows, but use Linux 90 % of the time. I was wondering if you were talking about E or IE...:confused:

---

### Post by swoll1980 on 2010-04-27
I'm surprised the poll is going the way it is. What is it that would make them notice they weren't using windows. Some one said mine sweeper. Wouldn't they just think mine sweeper was uninstalled? That's what I think they would think.

---

### Post by Chronon on 2010-04-27
Inability to install all of the shiny box software in stores would break the illusion.

---

### Post by 98cwitr on 2010-04-27
> **doas777 said:**
> but thats exactly the beauty of the idea (and explorer.exe does contain the start menu, though most of it's functions are calls to user32.dll and shell32.dll). if you were to pull it off, most users would never know. most of the windows system they know is in explorer and the assorted cpl/msc panels that they invoke on occasion. since they use explorer all day everyday without knowing it, that makes it all the easier to pull the wool over their eyes.

what happens when a user downloads an .exe and just doubleclicks on it? I don't know man, the missing DLLs are what's making this concept kinda hazy.

---

### Post by doas777 on 2010-04-27
> **98cwitr said:**
> what happens when a user downloads an .exe and just doubleclicks on it? I don't know man, the missing DLLs are what's making this concept kinda hazy.
well presumably that would be part of the portin'. thats why i originally brought up wine. it can run exe installers, and has the framework for whatever dlls you need, so porting explorer to sit atop the wine runtime would be pretty full featured. 

not that any of this would ever happen, for technical, manpower, financial, and legal reasons, but it's fun to imagine.

---

### Post by 98cwitr on 2010-04-27
WINE would have to get much much much further than they have developed it, plus when a linux system becomes that reliant on WINE it, imho, defeats the purpose of linux in the first place.

Getting the aesthetics right would be an option though, and Mint has done a good job in moving that direction :)

---

### Post by swoll1980 on 2010-04-27
> **Chronon said:**
> Inability to install all of the shiny box software in stores would break the illusion.

Would it? Or would they think their Winders was broke?

---

### Post by swoll1980 on 2010-04-27
Anyways the large majority of computer users I know, all of them as a matter of fact including myself, only use their PC to surf the web, and check their email. I think people don't understand the situation. If they can't install a file they're not going to say Hey someone switched my operating system kernel, they're going to think it's a virus, or something. If they can't find mine sweeper they're not going to say, hey some one switched my operating system. They're going to say Hey what happened to mine sweeper? I didn't say it would work the same I said the average user  wouldn't realize it was a different OS.

---

### Post by Chronon on 2010-04-27
> **doas777 said:**
> well presumably that would be part of the portin'. thats why i originally brought up wine. it can run exe installers, and has the framework for whatever dlls you need, so porting explorer to sit atop the wine runtime would be pretty full featured. 

not that any of this would ever happen, for technical, manpower, financial, and legal reasons, but it's fun to imagine.

I was considering porting in the traditional sense of modifying the source code so that Explorer would compile as a native Linux binary, not patching more Win32 API functionality into Wine so that Explorer will run on top of it.

I guess that was part of your earlier point: Since Explorer is almost exclusively WinAPI calls, the only sane way to port it is to add support for these WinAPI calls into WINE.

---

### Post by scottuss on 2010-04-27
As far as I'm aware, Internet Explorer is heavily used to this day within the core Windows desktop experience anyway. I know I can browse directories using the MS Web browser control and vice versa, meaning they're so far intertwined, you'd get a whole load of junk... no thanks! :)

---

### Post by conradin on 2010-04-27
koisks, and labs where most users arent Admins. 
[http://www.thevarguy.com/2010/01/05/ubuntu-linux-clone-looks-like-windows-xp/](http://www.thevarguy.com/2010/01/05/ubuntu-linux-clone-looks-like-windows-xp/)

---

### Post by Groucho Marxist on 2010-04-27
> **Doctor Mike said:**
> First you'd have to have 90% of the world using I Explorer... It's pre-packaged, doesn't mean it's used...

Exactly; Internet Explorer is like every "Came with the Frame Family" photograph that comes pre-packaged with the frame(s) you bought... Just because it's there does not mean that you will use it.

---

### Post by swoll1980 on 2010-04-27
> **Groucho Marxist said:**
> Exactly; Internet Explorer is like every "Came with the Frame Family" photograph that comes pre-packaged with the frame(s) you bought... Just because it's there does not mean that you will use it.

Wow. I give up.

---

### Post by K.Mandla on 2010-04-27
> **swoll1980 said:**
> If you ported Explorer to Linux...
It would be XFE.

[[img]http://omploader.org/tMjRmdQ[/img]](http://omploader.org/vMjRmdQ)

---

### Post by MCVenom on 2010-04-27
> **swoll1980 said:**
> You could switch 90% of the world to Linux with out them knowing it.
You extrapolated a reply to a thread on Gubuntu into a topic? :lolflag:

[http://ubuntuforums.org/showthread.php?t=1458674&page=5](http://ubuntuforums.org/showthread.php?t=1458674&page=5)

---

### Post by MCVenom on 2010-04-27
> **Groucho Marxist said:**
> Exactly; Internet Explorer is like every "Came with the Frame Family" photograph that comes pre-packaged with the frame(s) you bought... Just because it's there does not mean that you will use it.

> **swoll1980 said:**
> Wow. I give up.

I don't! :p

Let's get this outta the way....

[SIZE=3]NOT IE NOT IE NOT IE NOT IE NOT IE NOT IE NOT IE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1[/SIZE]

[SIZE=3]Windows Explorer is, for all intents and purposes, the Windows Desktop Environment.[/SIZE]

---

### Post by madjr on 2010-04-27
[IMG]https://addons.mozilla.org/en-US/firefox/images/p/30930/1238348591[/IMG]

oh lookye is FF with ie theme
[https://addons.mozilla.org/en-US/firefox/addon/4129](https://addons.mozilla.org/en-US/firefox/addon/4129)


[IMG]https://addons.mozilla.org/en-US/firefox/images/t/11684/[/IMG]



[https://addons.mozilla.org/en-US/firefox/addon/4327](https://addons.mozilla.org/en-US/firefox/addon/4327)

oh this one is Fugly, but is what you;re looking for

I dont know what you;re smoking again, but i thought you quit :)

---

### Post by chessnerd on 2010-04-27
Interesting idea. 

This would work for most people for some time, but eventually someone would try to install a Windows application and they would figure out they weren't in Redmond. You need full, near-native Windows application support if you want to trick people and that isn't going to happen unless ReactOS has a breakthrough.

Windows biggest strong-suit is that it is the de facto standard for applications. If you want it, Windows can run it. If this goes away, Windows will lose its market dominance, but until Windows loses its market dominance, this isn't going to change. It's a cycle and it's one of several factors that is keeping Windows where it is. People make applications for Windows because most people use Windows, which pushes people to use Windows, which causes people to make their applications for Windows.

---

### Post by swoll1980 on 2010-04-27
For some reason I thought people would know what Windows Explorer was. It looks like at least half have no clue. Looks like I was wrong.

---

### Post by toupeiro on 2010-04-27
Explorer (the GUI shell) is crap.  No incentive here.

---

### Post by swoll1980 on 2010-04-27
The other half don't bother to read the thread.

---

### Post by toupeiro on 2010-04-27
> **swoll1980 said:**
> The other half don't bother to read the thread.

I read it, and, I see no incentive in doing it.

---

### Post by swoll1980 on 2010-04-27
> **toupeiro said:**
> I read it, and, I see no incentive in doing it.

There is no incentive. The point was to illustrate that most average users think the desktop environment **is** the  operating system, but people can't take it for what it is. Everyone wants to add there own little spin to it. I deal with PC users several times a week. If they try to install something, and it doesn't work. They are not going to think it's because someone switched their operating system. The fact that, so many people are saying that makes me wonder what kind of average computer users they deal with on a day to day basis. Half the people on the forum think that Explorer = Internet Explorer, and half don't read the thread, or spin it in some way. I have to say this has been a pretty frustrating thread.

---

### Post by chessnerd on 2010-04-27
> **swoll1980 said:**
> For some reason I thought people would know what Windows Explorer was. It looks like at least half have no clue. Looks like I was wrong.

I knew exactly what you were talking about as soon as I read the title, and I immediately thought that this problem would come up (I'm not kidding, those were my first and second thoughts).

Now, a report from Captin Obvious's young-ward, Coporal Should-Be-Obvious:

> **Corporal Should-Be-Obvious]In this post you are referring to explorer.exe, the process name of the Windows file manager/desktop environment. You are proposing that the taskbar, desktop, and file manager be ported to Linux to convince users that they are still using Windows when, in fact, they are not.

The problem you are running into is that "Explorer" is often used as a shortened version of "Internet Explorer" and it seems like people are getting confused. Also, and this is true of all posts on there, some people don't like to read the whole OP (shocking, I know, but true). They read the first couple of sentences and then comment, and I'm guilty of this too. That seems like the bulk of your problem.

And yes, there are some that have no idea what Windows Explorer is, but my guess (my hope) is that they are in the minority and that most were just confused.[/QUOTE]

[QUOTE=swoll1980 said:**
> If they try to install something, and it doesn't work. They are not going to think it's because someone switched their operating system..

No, but they'll be upset and will realize that *something* is wrong. They just won't know what it is.

---

### Post by swoll1980 on 2010-04-27
> **chessnerd said:**
> 

No, but they'll be upset and will realize that *something* is wrong. They just won't know what it is.
Exactly. They would call their PC guy. One look at the file system, or the command line would be enough for someone that knew what they were doing to understand what was going on, but average people would be clueless.

---

### Post by Jay Car on 2010-04-27
I know the difference between IE and Windows Explorer, and I've read the thread.  But what would be the benefit of fooling people into thinking they're using Windows when they aren't?  

To the comments that computer users would just assume something was wrong, or that they had a virus, if something didn't work as expected, that would be doing a disservice to everyone. Especially to those who have worked so hard to create the great Free software we use. 

Maybe, like some of the others, I've misunderstood the purpose of this thread...but I believe people need good software and good information, not dishonesty.

---

### Post by chessnerd on 2010-04-27
> **swoll1980 said:**
> Exactly. They would call their PC guy. One look at the file system, or the command line would be enough for someone that knew what they were doing to understand what was going on, but average people would be clueless.

You don't even need to port Explorer to fool people in this manner. XPGnome is good enough. 

Last year I was able to fool two of my cousins into thinking that Linux was Windows. I used XPGnome, enhanced it a bit with Windows fonts and other modifications and what did they notice first? Both pointed out that the computer used a Gateway monitor with a Dell mouse!? One of them clicked the Start button and didn't realize anything was different, then proceeded to browse the web via the Firefox icon I put on the desktop.

Post where I talk about this (fifth one down): [http://ubuntuforums.org/showthread.php?t=1258215&page=4](http://ubuntuforums.org/showthread.php?t=1258215&page=4)

You can easily fool people in this manner. The hard part would be to keep them fooled for an extended period of time...

---

### Post by swoll1980 on 2010-04-28
> **Jay Car said:**
> I know the difference between IE and Windows Explorer, and I've read the thread.  But what would be the benefit of fooling people into thinking they're using Windows when they aren't?  

To the comments that computer users would just assume something was wrong, or that they had a virus, if something didn't work as expected, that would be doing a disservice to everyone. Especially to those who have worked so hard to create the great Free software we use. 

Maybe, like some of the others, I've misunderstood the purpose of this thread...but I believe people need good software and good information, not dishonesty.
This is a spin. When did I ever say there would be a benefit to this? If you read the thread how could you possibly make this post? This thread turned out to be pretty fascinating really. If anything it's a behavioral experiment to see how many words can be put in someones mouth that they never said.

---

### Post by swoll1980 on 2010-04-28
> **chessnerd said:**
> You don't even need to port Explorer to fool people in this manner. XPGnome is good enough. 

Last year I was able to fool two of my cousins into thinking that Linux was Windows. I used XPGnome, enhanced it a bit with Windows fonts and other modifications and what did they notice first? Both pointed out that the computer used a Gateway monitor with a Dell mouse!? One of them clicked the Start button and didn't realize anything was different, then proceeded to browse the web via the Firefox icon I put on the desktop.

Post where I talk about this (fifth one down): [http://ubuntuforums.org/showthread.php?t=1258215&page=4](http://ubuntuforums.org/showthread.php?t=1258215&page=4)

You can easily fool people in this manner. The hard part would be to keep them fooled for an extended period of time...

I didn't realize those gnome look a likes were that good.

---

### Post by sxmaxchine on 2010-04-28
Explorer is not Internet Explorer.
Also i think people would notice because ubuntu has a completely different layout, however i think that maybe 90% of average users wouldnt care

---

### Post by swoll1980 on 2010-04-28
> **sxmaxchine said:**
> Explorer is not Internet Explorer.
Also i think people would notice because ubuntu has a completely different layout, however i think that maybe 90% of average users wouldnt care

The people I deal with on a day to day bases have no clue how a Windows file system works. Even people in my IT classes are still clueless. I have to walk people, who have been using windows for years, through getting to their programs folder, and things like that.

---

### Post by chessnerd on 2010-04-28
> **swoll1980 said:**
> I didn't realize those gnome look a likes were that good.

They're good. XPGnome is very convincing with only a few minor things that most people wouldn't notice. However, it's more about normal people being ignorant to the intricacies of how their computer looks. If it has a button that says "Start" and a list of application types instead of the big XP Start menu they're just going to use the list of application types. They aren't going to say "Hey, this isn't right. Where are the 'My Documents' buttons and frequently used programs?" unless they are a power user or someone who pays attention to these things.

Worst case example: my mother can't tell the difference between default Ubuntu and Windows XP. 

Sadly, I'm not joking. 

I put an Ubuntu Live CD on the desktop, loaded up Firefox, and asked her to use it. She didn't see any difference until she tried to get one of her documents off of the desktop and wondered where it was, asking me if I deleted it. She couldn't understand that it was a different operating system from Windows and was mad that I needed to reboot it for her to get at her desktop. I feel a physical pain when I try to explain computers to her and go around and around in circles about it. I did, at least, get her to understand the general idea of why RAM is important via an analogy about a kitchen with limited counter-top space, but other than that its been an uphill battle that I know I won't win.

---

### Post by scottuss on 2010-04-28
> **swoll1980 said:**
> There is no incentive. The point was to illustrate that most average users think the desktop environment **is** the  operating system, but people can't take it for what it is. Everyone wants to add there own little spin to it. I deal with PC users several times a week. If they try to install something, and it doesn't work. They are not going to think it's because someone switched their operating system. The fact that, so many people are saying that makes me wonder what kind of average computer users they deal with on a day to day basis. Half the people on the forum think that Explorer = Internet Explorer, and half don't read the thread, or spin it in some way. I have to say this has been a pretty frustrating thread.

Um, but to go over what I said in my first post to this thread, actually I think you'll find that on a deeper level, Windows Explorer is much more closely linked to Internet Explorer than you may be giving it credit for.

---

### Post by Jay Car on 2010-05-01
> **swoll1980 said:**
> This is a spin. When did I ever say there would be a benefit to this? If you read the thread how could you possibly make this post? This thread turned out to be pretty fascinating really. If anything it's a behavioral experiment to see how many words can be put in someones mouth that they never said.

You are right, of course. This whole thread shows quite clearly that "ordinary users" don't understand "spin". So they cluelessly attempt to fill-in missing information as best they can.  

What can I say? I can only bow my head in shame.  Your awesome cluefullness and superior ability to "spin" is obvious and wonderous.  

I shall now go stand in the corner with my clueless user dunce cap firmly planted on my pointed little head while you point and laugh. You have put me in my place. I am ever so grateful. 

:)

---

### Post by Khakilang on 2010-05-01
The reason I switch to Linux is Nautilus, Gnome and among other things. We don't need to fool the users. I mean they have to know what OS they are using and their usefulness. Porting Explorer or Internet explorer to Linux is not going to work. Sooner or later they going to find out that they been taken for a ride. I don't think anybody likes that.

---

### Post by Le-Froid on 2010-05-01
The biggest problems I'd see with that is the file browser and windows apps. :|

If someone wants to run a program installed normally in C:\Program Files, they would have no idea where to look under the *nix filesystem layout (and probably be confused about /home)

Then if someone tries to download freeware for windows they'd smash the computer or something when it doesn't work

---

