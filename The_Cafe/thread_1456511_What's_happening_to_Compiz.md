---
title: "What's happening to Compiz?"
date: 2010-04-17
forum: The Cafe
---

### Post by Xorlathor on 2010-04-17
Is it just me, or has development for Compiz stopped? No new plugins are being developed, and no big announcements, either. I still get updates for Compiz from the update manager, but nothing new's added - what's up with this?

Compiz is a huge advantage of Ubuntu over stinky Aero and the lame effects in Apple - why don't we take advantage of this and improve Compiz like crazy?

---

### Post by howefield on 2010-04-17
> **Xorlathor said:**
> Is it just me, or has development for Compiz stopped?

Not so much stopped, merely slowed to the extent that one developer remains...

[http://forum.compiz.org/viewtopic.php?f=89&t=12285&sid=ec9bce010aaf75f3dd262b340ce76b98](http://forum.compiz.org/viewtopic.php?f=89&t=12285&sid=ec9bce010aaf75f3dd262b340ce76b98)

---

### Post by Xorlathor on 2010-04-17
> **howefield said:**
> Not so much stopped, merely slowed to the extent that one developer remains...


Is there any difference between that and stopped? How can we get more devs?

---

### Post by howefield on 2010-04-17
> **Xorlathor said:**
> How can we get more devs?

Become one.

---

### Post by Xorlathor on 2010-04-17
> **howefield said:**
> Become one.

Sure, anyone wanna teach me to code?

---

### Post by Kerin on 2010-04-19
> **Xorlathor said:**
> Sure, anyone wanna teach me to code?

That sort of thing isn't liable to help much, Xor.  The loudest voice one can speak with in the Linux community is code, and if you can't produce it you are more or less at the whim and mercy of those who write the software.  

To wit, either learn to code it yourself or make it worth the while of someone who can.  Cash incentives are nice! :KS

---

### Post by aviedw on 2010-04-19
What else do you want compiz to do. It seems to add great function but if you turn too much on you will just slow down your system and create clutter and lose function. I wish had time to learn how to code.

---

### Post by Xorlathor on 2010-04-19
> **aviedw said:**
> What else do you want compiz to do. It seems to add great function but if you turn too much on you will just slow down your system and create clutter and lose function. I wish had time to learn how to code.

Compiz doesn't slow down my computer whatsoever, and if anything, it helps me gain function, not lose it. I could think of plenty of things to add to Compiz - easy plugin installation (easier than now), steady plugin development, streamlining, complete OS integration, etc. 

I just wish I could help...

---

### Post by Xorlathor on 2010-04-19
> **Kerin said:**
> That sort of thing isn't liable to help much, Xor.  The loudest voice one can speak with in the Linux community is code, and if you can't produce it you are more or less at the whim and mercy of those who write the software.  

To wit, either learn to code it yourself or make it worth the while of someone who can.  Cash incentives are nice! :KS

What would be the best language to learn for this kind of area? C++? Java?

---

### Post by SmSpillaz on 2010-04-20
Thought I'd post here as the developer in question.

Basically, there are about 2 of us left, one of us maintains the 0.8.x (mainstream, the one that everyone uses) branch and I do most of the work that does into 0.9.x.

Development has been slow recently for the following reasons:
[LIST]
[*]I made a bit of a silly decision to study a bacherlor of law / bachelor of arts + double overload this semester which had the unintended consequence of having a bazillion assignments due
[*]98% of the work is actually done, I'm just bugfixing and as any programmer would know bugfixing often takes far longer than the original implementation
[*]The other 2% is working in areas of the code that I have little / no experience with (such as the settings system and cmake build system). These areas also have very little documentation. As such, I'm having to learn new areas from scratch in order to rewrite them for the 0.9 branch, so it's taking me forever to do that :(
[/LIST]

The real issue at hand though is the fact that I although I try to be, I'm not a particularly good developer and I don't have experience with a lot of the code that no longer has any maintainers. The other problem is that the developers who wrote the sections I am dealing with at the moment  are practically unreachable, so there is no chance of me asking them what  something does or for help in a particular section. Additionally, the code is virtually undocumented, which amplifies the previous problem. [I'm currently trying to resolve this]("http://docs.compiz.org"), but I can only document as far as I understand the code. Since I started doing the bulk of the work, I've learnt about some significant new areas, including how the decorators work, how reparenting works, how non composited X based drawing works, how a large part of the opengl vertex interface compiz provides works, how the settings system works etc etc. It's been a big job and for one person too.

A lot of people have offered to help out with development and that's great! (The more the merrier really). Unfortunately what we have is a  bit of a chicken  and egg scenario where the bits that need to get done are the bits I don't understand and without my understanding of them there is no way I would be able to teach any new developers of them.

I know, it sucks. [Although, if Canonical likes compiz then I sure wouldn't mind a paid developer to work upstream with me].

Otherwise, not to worry - there are heavy strides of development being made in projects like Mutter / GNOME Shell and KWin such that you can get your development outside of compiz. In any case, a key goal of the entire 0.9.x series was to turn compiz into a library that these window managers could use (Well, KWin at least, I know that clutter, which mutter is based on does not like raw opengl scene manipulation).

---

### Post by wkulecz on 2010-04-20
I'm not very familiar with compiz, only recently getting a graphics card that would really support the "full effects".

But, so far I've not seen anything that would help productivitity and most are just visually annoying -- like the shakey windows thing.

Am I missing something here?

---

### Post by Grenage on 2010-04-20
> **SmSpillaz said:**
> Otherwise, not to worry - there are heavy strides of development being made in projects like Mutter / GNOME Shell and KWin such that you can get your development outside of compiz. In any case, a key goal of the entire 0.9.x series was to turn compiz into a library that these window managers could use (Well, KWin at least, I know that clutter, which mutter is based on does not like raw opengl scene manipulation).

Kudos on the work; I love compiz, and use it on all my desktops.  Good luck with your degree!

---

### Post by mcduck on 2010-04-20
> **wkulecz said:**
> I'm not very familiar with compiz, only recently getting a graphics card that would really support the "full effects".

But, so far I've not seen anything that would help productivitity and most are just visually annoying -- like the shakey windows thing.

Am I missing something here?

Yes, you are. :D

Just install the CompizConfig Settings Manager, if you haven't got it, and check all the available plugins. The "Window Rules"-plugin alone adds a lot of nice functionality, and with a bit of creativity and the options available in the different plugins, you can do lost of very neat stuff.

Just ignore most of the things in the Effects section, and everything else is pretty much about productivity and customization options.

---

### Post by mcduck on 2010-04-20
> **SmSpillaz said:**
> Thought I'd post here as the developer in question.
Thanks for the heads-up. :)

To be honest I've been wondering about the state of Compiz myself, especially compared to the early days of Compiz/Beryl when new plugins and features popped out just about every other day. I wonder what happened to Quinn and all the others who worked with the code around then....

I'd be happy to help myself, but I'm just a multimedia/graphics designer with hardly any programming skills so I bet we'd be running computers connected directly to brain before I'd be able to do any useful stuff to Compiz code... :D

---

### Post by drreed on 2010-04-20
> **mcduck said:**
> Yes, you are. :D

Just install the CompizConfig Settings Manager, if you haven't got it, and check all the available plugins. The "Window Rules"-plugin alone adds a lot of nice functionality, and with a bit of creativity and the options available in the different plugins, you can do lost of very neat stuff.

Just ignore most of the things in the Effects section, and everything else is pretty much about productivity and customization options.

Maybe that was part of my problem. I tried using effects and it just bogged everything down after I rebooted, big-time.  I'll try it again now that I know how to get rid of it and get Xfwm2 working again.

Which window manager do you suggest? Do we have to/need to use Emerald?

---

### Post by mcduck on 2010-04-20
> **drreed said:**
> Maybe that was part of my problem. I tried using effects and it just bogged everything down after I rebooted, big-time.  I'll try it again now that I know how to get rid of it and get Xfwm2 working again.

Which window manager do you suggest? Do we have to/need to use Emerald?

I prefer using the default decorator, GWD, as it supports Metacity themes and integrates very well with Gnome.

---

### Post by asddf on 2010-04-20
> **Xorlathor said:**
> What would be the best language to learn for this kind of area? C++? Java?

C, C++, Assembly

Any low level language will give you enough experience to do......anything.

Avoid Java, C#......etc

---

### Post by forrestcupp on 2010-04-20
> **SmSpillaz said:**
> 
Otherwise, not to worry - there are heavy strides of development being made in projects like Mutter / GNOME Shell and KWin such that you can get your development outside of compiz. In any case, a key goal of the entire 0.9.x series was to turn compiz into a library that these window managers could use (Well, KWin at least, I know that clutter, which mutter is based on does not like raw opengl scene manipulation).

Thanks for all that inside info.  I feel for you.  Trying to figure out other people's undocumented code really bites.

But like you said, Mutter/Gnome Shell and KWin seem like they are kind of on their way to taking over in this arena.  It almost seems like Compiz will become obsolete because the main DEs will have that functionality built in.  I wonder if that is discouraging for you?

---

### Post by Shpongle on 2010-04-20
for those wondering its in C++ , just looked at the docs there. I have a year of c++ under my belt but I need lots of practice and a refresh as im doing java now . I might try help if I can over the summer

---

### Post by TheNessus on 2010-04-20
> **wkulecz said:**
> I'm not very familiar with compiz, only recently getting a graphics card that would really support the "full effects".

But, so far I've not seen anything that would help productivitity and most are just visually annoying -- like the shakey windows thing.

Am I missing something here?

scale and expo and great, I set scale (it shows all your open windows in equal size at once) and expo to start when mouse pointer is at right or left edges, or on specific key combinations. Its great for when dealing with multiple desktops. for one example.

---

### Post by forrestcupp on 2010-04-20
> **DillByrne said:**
> for those wondering its in C++ , just looked at the docs there. I have a year of c++ under my belt but I need lots of practice and a refresh as im doing java now . I might try help if I can over the summer

I'm betting it's going to take a lot more than just knowing C++.  You'll probably have to know opengl and how X and window managers are implemented, among other things.

But if you can learn C++, you can probably learn the other necessary things, too.

---

### Post by asddf on 2010-04-20
OpenGL is just a libary for C++,

As long as you know C++ you already know OpenGL, it's just the heavy math side you will require to be good at OpenGL, Mainly Trig but also Calculus.

---

### Post by Simian Man on 2010-04-20
> **asddf said:**
> OpenGL is just a libary for C++,

As long as you know C++ you already know OpenGL, it's just the heavy math side you will require to be good at OpenGL, Mainly Trig but also Calculus.
Wrong.  Learning libraries is easier than learning languages, but you don't already know OpenGL if you know C++.  Also of the maths that is need for 3D graphics, linear algebra is by far the most useful, but OpenGL hides most of that from you.

> **asddf said:**
> C, C++, Assembly

Any low level language will give you enough experience to do......anything.

Avoid Java, C#......etc

Even more wrong.

---

### Post by asddf on 2010-04-21
Weird, I write C++ using OpenGL everyday.

You don't learn libraries, you reference them.

---

### Post by SmSpillaz on 2010-04-21
> **forrestcupp said:**
> I wonder if that is discouraging for you?

Things could always be better, but never say die.

(BTW, finally figured out why a huge bug was occurring just then :P)

---

### Post by forrestcupp on 2010-04-21
> **asddf said:**
> OpenGL is just a libary for C++,

As long as you know C++ you already know OpenGL,Lol.

> **asddf said:**
> Weird, I write C++ using OpenGL everyday.

You don't learn libraries, you reference them.
You really didn't have to apply any time at all learning how to "reference" opengl?

I've worked with a lot of different libraries and frameworks, and I've never just been able to begin programming in any of them without learning anything about them at all.  

Learning C++ syntax is pretty easy.  If you have any programming background at all you should be able to learn C++ pretty quickly.  But you can't possibly just immediately understand how thousands of developers implement their custom libraries just because you know C++.  You have to spend time learning what classes,methods, functions, and properties are for and what arguments and declaration settings you have to use.  And a lot of libraries implement some of their structure using macros, which just throws C++ syntax out the window.

Just because you understand C++ doesn't mean you are automatically fluent in every library out there that is created for C++.

---

### Post by asddf on 2010-04-21
Your really find it hard looking up a reference for any library? especially one as supported as OpenGL?

---

### Post by Simian Man on 2010-04-21
> **asddf said:**
> Weird, I write C++ using OpenGL everyday.

You don't learn libraries, you reference them.

And I'm sure your programs are great.  A bunch of hacked together API calls without any understanding behind it :).

---

### Post by forrestcupp on 2010-04-21
> **asddf said:**
> Your really find it hard looking up a reference for any library? especially one as supported as OpenGL?

I never said it is hard.  I'm saying that it does take time to learn how they implement things.  You don't just *know* it because you know C++.

Yes, OpenGL is well supported and documented.  But you do have to actually read and understand that documentation before you can just start referencing it.  Reading and understanding is what learning is.  Learning takes time.

---

### Post by wkulecz on 2010-04-21
> Learning C++ syntax is pretty easy. If you have any programming background at all you should be able to learn C++ pretty quickly. But you can't possibly just immediately understand how thousands of developers implement their custom libraries just because you know C++. You have to spend time learning what classes,methods, functions, and properties are for and what arguments and declaration settings you have to use. And a lot of libraries implement some of their structure using macros, which just throws C++ syntax out the window.


Absolutely correct, and the learning is made far more difficult by the near total lack of documentation about how the various parts are expected to play together.

Occasionally you get lucky and find some effective sample code to illustrate, but more common, for especially things like Gnome and GStreamer you get lost in the C macros that poorly reinvent C++.

I'm not a big fan of C++, preferring C, as I generally find the objectization of things more confusing that helpful, but if you fully buy into the object oriented paradigm, use an OO language instead of badly reinventing one with macros!

Don't believe me, look into the GTK+ "interfaces".  This abomination exists because the initial object oriented re-invention didn't implement multiple inheritance, turned out they actually needed it, and came up with this crap as a "solution".

To me this is the worst of all worlds situation.  I prefer the look, feel, and philosophy of Gnome, but find KDE is far easier to learn and develop for because it is based on C++ and TrollTech actually produced effective documentation, tools and sample code for the underlying QT C++ object system.

--wally.

---

### Post by madjr on 2010-04-21
> **asddf said:**
> C, C++, Assembly

Any low level language will give you enough experience to do......anything.

Avoid Java, C#......etc

so no python?

---

### Post by Kazade on 2010-04-21
> **madjr said:**
> so no python?

I can sense another language war coming...

With any project, it's a case of using the right tool for the job. 

Generally speaking if you are writing a high performance or embedded application you would tend to prefer a closer-to-the-metal language for example C, C++, D or if you are really tight on resources (e.g. mega low level) then ASM. 

Of course the downside of lower level languages is extended development time and more scope for shooting yourself in the foot. Also the above languages have a steeper learning curve than higher level languages. C++ for example is so massive and multi-paradigm that even after using it for 8 years, I'm still learning stuff about it. C++ specifically has an endless supply of gotchas (undefined behaviour, scoping rules, memory management, proper operator overloading etc.)

Most of the time though, you aren't working with limited resources or need that extra power at the sacrifice of development time. For these cases you would use higher level languages such as C#, Java, Python, Ruby etc. Python and Ruby are interpreted (whereas C# and Java are compiled to bytecode) so you probably wouldn't use them where you are using CPU heavily but they are good for most general programming.

Java performance can be very close to C or C++ performance, sometimes arguably faster. But that comes at the cost of increased memory usage and JVM start up time. C# is probably similar. These languages are popular because they fall in the middle ground. 

That's not to say that you can't use combinations. For example, you could build your application core in C++ and then use Python plugins to extend functionality. Or build your app in Python and code performance critical parts in C or C++.

At the end of the day, it's about the balance between development time vs resource usage and apply it to the specific situation.

Regarding learning a language to help with Compiz, well then you'd need to learn the language Compiz is written in most likely (I heard it's moved to C++ but I may be wrong). At the end of the day it is good to learn several languages, that way you know how to make the right decision depending on the project.

Slightly OT: Personally, I tend to write games in my spare time and C++ is a good fit for me (although I know C, Java, and Python well too). I tend to use C (or at least C-linkage) for reusable libraries that I intend to package separately. I use Python for web development at work. I'm not a massive fan of Java's syntax (I find it constrictive for some reason) so I tend not to use it unless it really is the most suitable solution, but it's rare for me to find a situation where either C++ or Python are not suitable.

---

### Post by Xorlathor on 2010-04-21
> **Simian Man said:**
> Wrong.  Learning libraries is easier than learning languages, but you don't already know OpenGL if you know C++.  Also of the maths that is need for 3D graphics, linear algebra is by far the most useful, but OpenGL hides most of that from you.



Even more wrong.

I think I'll stick to believing the person who is actually spending his own time working on Compiz, whether you are more experienced or not. If you want people to listen to you on Compiz issues and how they code it, go join the dev team for a couple months, and then I'll listen.

---

### Post by Xorlathor on 2010-04-21
Well it looks like I struck a nerve! 4 pages worth of posts within 1 day after the thread was made!

From what I can tell, the main goal right now is to:

1. Let Canonical that people most certainly Do use Compiz, they love it, and it's a big advantage over Windows and OSX. (Just look up Compiz on Youtube - 90% of the videos are ones titled, "Compiz vs. Aero - Compiz kicks butt, Compiz Rocks, Insane Compiz Effects, etc. And many of them have 10,000+ hits!"

2. I'm not a dev, nor do I have next to any experience in coding (I'd love to learn!), but it doesn't take coding experience to realize there are a bunch of (dare I say expert?!) coders in this thread, only **_*one*_** of which is actually helping with coding/debugging Compiz. I daresay if any of you posted in here, you had some kind of degree of interest for Compiz - so surely you wouldn't mind either finding someone who'd be willing to help with it, or help with it yourself? 

Does that make any sense? I know it can't possibly be that easy, but we have to do *something* to get the Compiz project going again, it's such a great feature of Ubuntu and it shouldn't just go down the drain! Who's with me?

---

### Post by Simian Man on 2010-04-21
> **Xorlathor said:**
> I think I'll stick to believing the person who is actually spending his own time working on Compiz, whether you are more experienced or not. If you want people to listen to you on Compiz issues and how they code it, go join the dev team for a couple months, and then I'll listen.
I don't see where asddf said he was working on the development team of Compiz.  If he is, then I won't be upgrading because he quite clearly doesn't know what he's talking about :).

> **Xorlathor said:**
> 2. I'm not a dev, nor do I have next to any experience in coding (I'd love to learn!), but it doesn't take coding experience to realize there are a bunch of (dare I say expert?!) coders in this thread, only **_*one*_** of which is actually helping with coding/debugging Compiz. I daresay if any of you posted in here, you had some kind of degree of interest for Compiz - so surely you wouldn't mind either finding someone who'd be willing to help with it, or help with it yourself? 

There are tons of projects I want to work on, but unfortunately programmers has to division their time between stuff they get paid to work on and stuff they work on for fun.  For most of us the "part we have to do" takes up most of our time, so you have to be pretty passionate about the things you *do* work on for fun.

You can't expect anybody who just uses Compiz to care enough to jump on board the development team.  If you care that much you should just get busy learning to program.

---

### Post by Xorlathor on 2010-04-21
> **Simian Man said:**
> I don't see where asddf said he was working on the development team of Compiz.  If he is, then I won't be upgrading because he quite clearly doesn't know what he's talking about :).



There are tons of projects I want to work on, but unfortunately programmers has to division their time between stuff they get paid to work on and stuff they work on for fun.  For most of us the "part we have to do" takes up most of our time, so you have to be pretty passionate about the things you *do* work on for fun.

You can't expect anybody who just uses Compiz to care enough to jump on board the development team.  If you care that much you should just get busy learning to program.

SmSpillaz is a dev, not asddf - I guess I got confused there, sorry 'bout that. You're right, even from what I can tell asddf doesn't have much knowledge of OpenGL and C++, he just thinks he does...

I can completely understand that not many programmers are waiting in line to sacrifice their free time to help on a confusing project like Compiz, but there are always a few people (SmSpillaz) that are willing to do so for the good of others. 

I'm basically looking for people that *are* passionate enough about Compiz to spare some time for it. I happen to care enough about Compiz that I'd love to help with it, but as I'm in my first year of highschool and am yet to learn coding (I'm working on it, planning to take a Java class next spring and work up from there), there's nothing much I can do other than to try to get other people to help. I know it might seem leech-ish to be getting other people to work when I'm currently unable to, but it's for a good cause and I'm certainly not forcing anybody to do anything - just giving them reasons why they should consider it. 

I totally understand if you don't help, but it can't hurt to give it a little thought.

---

### Post by tica vun on 2010-04-21
> **wkulecz said:**
> I'm not very familiar with compiz, only recently getting a graphics card that would really support the "full effects".

But, so far I've not seen anything that would help productivitity and most are just visually annoying -- like the shakey windows thing.

Am I missing something here?

I hate the "WOBBLY WINDOWS ARE USELESS" argument. You do realise there are a ton of plugins other than wobbly windows and spinning cubes, right?

Just to list the plugins that I use, that add functionality, increase usefulness, and AREN'T wobbly windows:

-Taskbar preview
-Expo
-Window snapping hotkey
-Tabbes windows
-Transparent moving windows
-Wallpaper plugins (for precise wallpaper positioning on multiple displays)
-Static application switcher

---

### Post by drreed on 2010-04-21
> **mcduck said:**
> I prefer using the default decorator, GWD, as it supports Metacity themes and integrates very well with Gnome.

Thanks.

I now have compiz running and I'm flipping through windows el-quicko. 
It's interesting to add effects, then watch my CPU graph screenlet on the panel.

Normally, there's barely a line there when inactive, using the cube, half of the graph is filled, using the other "switchers", the effect is barely visible. Cool.

I now have some added productivity features, without killing my super-fast Xfce4.
If i need to crunch something that's going to take awhile, I just turn it off to get every little cycle back.

Thanks McDuck.

** core temp goes from about 94F to 105F within 30 sec's of turning on cube, cube rotate, and deformation - not good if your just sitting there, heating up cpu for no reason

---

### Post by forrestcupp on 2010-04-21
> **Xorlathor said:**
> 
I'm basically looking for people that *are* passionate enough about Compiz to spare some time for it. I happen to care enough about Compiz that I'd love to help with it, but as I'm in my first year of highschool and am yet to learn coding (I'm working on it, planning to take a Java class next spring and work up from there), there's nothing much I can do other than to try to get other people to help.

But the problem is that according to the one guy working on it, it was very poorly documented and the people who originally worked on it are unreachable.  Because of that, he doesn't have a clue how everything works, so the one person who could show other people what to do, can't.  So even if people wanted to jump on board, there is little they can do.

asddf was talking about OpenGL and how well supported it is.  But Compiz isn't OpenGL.  According to the only present dev, it isn't documented or supported at all.

Not to mention that people just aren't as hyped about the advancement of Compiz anymore.  Why don't people care?  First, because it's already about as good as it's going to get.  Also, because the main DEs are implementing their own built-in solutions so Compiz won't be needed anymore at all.  It's like, why would I work so hard to fix up my 10 year old car when I know I'm getting a brand new one next week?

---

### Post by chris4585 on 2010-04-21
Don't forget about the zoom function super+scroll.  It helps me since I'm hard of seeing sometimes. To add more functionalities I've made custom launchers before to do simple things like Scale.  I personally love compiz and I hope it lives on.

---

### Post by SmSpillaz on 2010-04-22
> **forrestcupp said:**
> But the problem is that according to the one guy working on it, it was very poorly documented and the people who originally worked on it are unreachable.  Because of that, he doesn't have a clue how everything works, so the one person who could show other people what to do, can't.  So even if people wanted to jump on board, there is little they can do.

Maybe I'll clarify - I know about how 80% of it works and I need to know about how the other %2 works in order for me to get some kind of 0.9.0 release out the door (The other 18% are things that I'd rarely need to touch since they are to do with XServer <--> WM communication and texture binding, stuff that has been there for millions of years and never needs to change because it is all based on specification (stuff that KWin and Mutter both implement as well)

> 

asddf was talking about OpenGL and how well supported it is.  But Compiz isn't OpenGL.  According to the only present dev, it isn't documented or supported at all.



Compiz uses OpenGL as its primary rendering backend. But you can load other backends too.

It is true that the code is not-well documented but that is changing. Compiz is supported. Has been since U71.0 I think.

> 
Not to mention that people just aren't as hyped about the advancement of Compiz anymore.  Why don't people care?  First, because it's already about as good as it's going to get.  Also, because the main DEs are implementing their own built-in solutions so Compiz won't be needed anymore at all.  It's like, why would I work so hard to fix up my 10 year old car when I know I'm getting a brand new one next week?

The argument to  do with "we don't need another revolution" is right. The 0.8 series has seen little development (other than supporting desktop related hints and integration) and I really don't think there is any more feature development that we could do (save for MPX which is #1 on my post 0.9.0 todo list) that are within the limits that we can work in.

To do with the other window managers - I think that building upon a stable code-base is far better than re-inventing the wheel. Your car analogy only applies in the case that the frameworks, interface, API etc are millions and millions of years old and based on assumptions that don't cater for what people want to do with their desktops. As far as I can see that is not the case with compiz - since all plugins work at a very low level. In fact, libkwineffects has a very similar API and structure to compiz and I've discussed quite a lot about how it is possible (not necessarily trivial) to merge interfaces.

---

### Post by d3v1150m471c on 2010-04-22
i'm going to assume you mean why doesn't someone else do it for you.

---

### Post by pt123 on 2010-04-22
Compiz owns, gnome-shell is like going 10 steps behind. It has limited features, limited configuration, slow and the development is also slow.

The problem with open source is that they re-invent the wheel many times, and often it is of poorer quality. 

Gnome couldn't even fix Nautilus to let Compiz take over displaying different wallpapers for the workspaces. These same people want to go out and create an advanced windows manager.

---

### Post by forrestcupp on 2010-04-22
> **pt123 said:**
> 
The problem with open source is that they re-invent the wheel many times, and often it is of poorer quality. 


The crazy thing is that one of the advantages the open source community brags about is *not* having to re-invent the wheel.

---

### Post by P4man on 2010-04-22
Im rather shocked to find out Compiz is currently kept alive by just one dev.  Expo, Scale and zoom are things I just wouldnt want to be without ever again.

SmSpillaz I hope you are not going to take up any dangerous hobbies, we need Compiz! Oh and dont graduate and get a highly paid job offering :)

As a side note, can we keep the "my C++ is bigger than yours" out of this thread pls? It somehow strikes me as disrespectful towards the only working and breathing compiz developer who made the effort of posting here. My 2 cents.

---

### Post by pt123 on 2010-04-22
> **forrestcupp said:**
> The crazy thing is that one of the advantages the open source community brags about is *not* having to re-invent the wheel.
yes it hilarious, if you combined all the  effort for the music players that have been written for Gnome, you would have the greatest music player. But what we are left with is Rhythmbox which is a solid player that has changed very little in the last 3 years, and Banshee which is a slow resource hog. 

Open source is great when when it used to create components and libraries, which application developers can use. This is what Gnome should concentrate on. They should have collaborated with Compiz than trying to rewrite (copy) everything from scratch.

---

### Post by forrestcupp on 2010-04-23
> **pt123 said:**
> yes it hilarious, if you combined all the  effort for the music players that have been written for Gnome, you would have the greatest music player. But what we are left with is Rhythmbox which is a solid player that has changed very little in the last 3 years, and Banshee which is a slow resource hog. 


True, but that's one big difference between Free Software and Open Source Software.  It's OSS's goal to not have to reinvent the wheel.  The Free Software movement doesn't care about that; they just care about philosophy.

---

### Post by mcduck on 2010-04-23
> **forrestcupp said:**
> The crazy thing is that one of the advantages the open source community brags about is *not* having to re-invent the wheel.

I suppose the point is that you don't *have to* re-invent the wheel, but you still *can* do it if you *want to*. And, for some reason or other, quite many seem to prefer the latter option. :D

---

### Post by drreed on 2010-04-23
> **mcduck said:**
> I suppose the point is that you don't *have to* re-invent the wheel, but you still *can* do it if you *want to*. And, for some reason or other, quite many seem to prefer the latter option. :D


> **mcduck said:**
> I suppose the point is that you don't *have to* re-invent the wheel, but you still *can* do it if you *want to*. And, for some reason or other, quite many seem to prefer the latter option. :D

It's the nature of things.

When I discover a new library, I want to come up with something that implements it. Often, my need for the application is merely as a vehicle that implements a library, so that I can see how it works, and get comfortable with the objects, their methods, etc.

It's rare that I take it as far as making something reusable for the public at large, but that others do is a good thing. It's not the most efficient process - you and I might not need the code for all those music players, or newsreaders, or whatever, but that doesn't take away from the people who created them, or Ubuntu. They're there if I want them. If we all join someone's collective, then I'm sure we'll get "farther along" by some yardstick. But, I shun collectivism .. .

---

### Post by Simian Man on 2010-04-23
Just because people create multiple applications that do the same thing doesn't necessarily go against the open source philosophy.  Look at music players.  There are tons of popular music players for GTK: Rhythmbox, Banshee, Exaile, Quod Libet, Listen, etc.  But they all actually use the same open source components such as GTK+, Gstreamer, MySQL lipmtp, libgpod and so on.

Without all of these great things wrapped up nicely in libraries, it would be much harder to write good desktop software.  And I applaud Compiz's decision to segregate a lot of the code into a library to allow others to use it.

---

### Post by MaxIBoy on 2010-04-23
Haven't really read the entire thread yet, just skimmed it, so I apologize if someone else has already said this. 

Compiz is moving pretty much a mile a minute. The reason why you weren't seeing new plugins is because they were rewriting the entire codebase, including all plugins, in C++ (a complete rewrite was necessary due to issues with the old code.) But the port is pretty much finished now, so you can expect 0.9.0 out the door soon. See the [dev blog](http://planet.compiz.org/), although the two most recent posts are April Fools jokes.

While there is one guy, Sam Spilsbury, who is doing the majority of development work lately (although he's had to deal with a flood where he lives recently,) there are still a few others on the dev team. And the rewrite will probably encourage new developers because the new codebase is a lot cleaner. 

Not to mention, Compiz can now act as a 2D window manager as well, and the performance is a lot better.

Compiz is not dead at all, although it looked that way for a while-- after the problem was vocalized by one of the developers, action was taken.

---

### Post by SmSpillaz on 2010-04-25
> **MaxIBoy said:**
> 
While there is one guy, Sam Spilsbury, who is doing the majority of development work lately (although he's had to deal with a flood where he lives recently,)

Slightly OT, but floods suck. Just found out yesterday that it's going to take another 4 weeks to deliver my laptop's AC adapter (I had to get it replaced since it was on the ground ....). This is where my props go to virtualbox - I am working on a mac with VB and developing in that. :lolflag:

Guillaume was speaking of releases next week. I think that's possible.

---

### Post by pete_m on 2010-04-26
Respect to you Spillaz and to all the others whose works are bringing rich visual experiences to the waiting world of users ranging from media professionals to those who mightn't know X-server from X-rated. . .

i  was pleased to read your post as responsible developer for compiz

by way of expressing solidarity with open source and my readiness to help out if i can

With a background in music production and video i've been a developer and programmer for some years . .originally in C/ C++ for realtime audiovisual control systems where our touchstone was not to touch the ( then analogue !! ) waveform, with our clumsy digital fingers.
At that time i became familiar with makefiles and
my last experiments in C were with DirectX and openGL 3D in the days of vml . . .

subsequently i've been programming in perl and javascript for the Web . .

i first caught wind of Compiz round about the time of getting my eeePC 1000. in August 2008, and was already dreaming of the kinds of rich visual experience offered . .

the intervening period has seen me learn more than i ever thought i would want to know about Debian-based systems, while i got a good Lamp environment with gimp n blender to work on the Xandros-based eeePc distro . . . a process i whose fruits i intend document to help others with their individual Linux learning curve.

i have lately taken the plunge to move to 'a 'buntu-based system and wish i'd done it sooner; though it seems fortuitous to be doing this at the time of Lucid's imminent release . .

i'm presently taking first steps in python for blender and gimp . . with a view to implementing the kinds of realtime displays i specialised in using opensource tools.

i believe the basis of the compositing engine of compiz is also in blender 2.5 so i'm thinking n dreaming of putting them together programatically
[http://blenderartists.org/forum/showthread.php?t=108675](http://blenderartists.org/forum/showthread.php?t=108675)

now that even a humble netbook can deliver rich visuals it seems like the kit is now mature enough to start manipulating the waveform with a vengeance. . .

did i catch up with the systems or vice versa ?


all this by way of expressing solidarity with open source and my readiness to help out if i can

You wrote . .

> areas of the code that I have little / no experience with (such as the settings system and cmake
> build system)

. .from which i'd guess you're more on the raw opengl scene manipulation side of things, which is what most interests me, i'm hoping eventually to use python in Blender to orchestrate displays of video, still and graphic imagery.

i haven't got far enough with compiz to know of the settings system, but i might be able to help navigate make and dive into understanding and even writing C source . .

> These areas also have very little documentation. As such, I'm having to learn new areas from scratch in order to rewrite them for the 0.9 branch, so it's taking me forever to do
.. on your own

i 'm looking forward to getting on further with both compiz and blender- two heads are bettter than one so if there is anything i can help with... please let me know

meanwhile all the best for compiz and for your law degree, and assignment deadlines... nil carborundum


3 random quotes from Jeremy Bentham ( Utilitarian Philosopher and Activist. 1748-1832)

“The power of the lawyer is in the uncertainty of the law”

“It is vain to talk of the interest of the community, without understanding what is the interest of the individual"

“The greatest happiness of the greatest number is the foundation of morals and legislation”

---

