---
title: "Why doesn't Java overtake Mono?"
date: 2009-10-15
forum: The Cafe
---

### Post by Dragonbite on 2009-10-15
Just thinking, Mono and Java are the most like each other, aren't they?  Shouldn't the anti-Mono people put their efforts into building and improving Java and Java applications to replace Mono and provide a real (cross-platform) replacement?

Mono has made its way into Gnome with some good applications that arguably fill a gap. Why doesn't somebody make some equivalent applications in Java?  Java and C# are supposed to be fairly similar languages so the conversion should not be that bad?

Actually, I don't think I use any Java applications on any systems (*oh, ok, only on 1 website for our school that has a $^*# banner for announcements that uses Java, other than that as far as I know I don't touch/use Java*).  I use .NET (Paint.NET) on Windows and Mono (F-Spot, Banshee) on Linux, but no Java except for this one website.

Otherwise, this is looking to run similar to Gnome vs KDE; 

Gnome stared out while KDE was built on the Qt which was "owned" by Trolltech.  Mono has been open sourced from the beginning while Java is only recently (or is still in the process of becoming) open sourced.

Gnome, due to being free(er) got the support from Red Hat and other distros that basically made Gnome the unofficial "default" for Linux.  Mono has made some applications without any current Gnome-native big-name competitors such as F-Spot and Tomboy (and Banshee is doing a great job of competing).

KDE has done a great job of late, but still lags behind Gnome use for Linux.  Will Java likewise always fall behind Mono adoption for Linux?

---

### Post by CJ Master on 2009-10-15
Well, Java has the advantages of having applets, so I do use Java more then mono, just not as a desktop application.

---

### Post by -grubby on 2009-10-15
Why would the anti-mono people do anything constructive?

And no, Java and C# are not just drop in replacements for each other.

---

### Post by Dragonbite on 2009-10-15
> **-grubby said:**
> Why would the anti-mono people do anything constructive?

And no, Java and C# are not just drop in replacements for each other.

Ha, I laughed at that anti-mono people comment, but I'm hoping to avoid the pro/anti-Mono flame wars (at least for a while).

Maybe Java development is more focused on Enterprises and don't make so many desktop applications?  I have tried a couple Java desktop applications (if my memory serves me right), one is a graphic management application or something. Anyway my experience with Java has been slow and buggy.

But wouldn't Java, if improved, be a possible contender for Mono?  I mean it is used by Enterprises, includes web or desktop applications, is cross platform and is (possibly) backed by a huge corporation.  Heck, even NetBeans and Eclipse is cross-platform (don't know about Apple though, but they have X-Code I think) which means as the IDE improves, all developers would get the beneift instead of the Visual Studio vs. Monodevelop arguments.

The C# and Java comparison, I admit, I have to go by what I've heard since I'm a VB.NET programmer.  I once considered trying to teach myself C# (helped by converting everything I have in VB.NET into C#) before moving from C# to Java.  That's never come to pass.

---

### Post by toupeiro on 2009-10-15
Java is a Ford, Mono is a Chevy.  


Java is a big sandbox from a security standpoint.  Mono/.NET offers much more than Java on that front, really making it more appealing for enterprises.  However, Java clearly has the visibility and footprint in the enterprise.  Mono could be an enterprise choice but its the worst posterchild for cross-platform support EVER.

---

### Post by nmccrina on 2009-10-15
I don't have any experience developing in Mono, but what has always puzzled me is that using Java you always have access to the entire, up-to-date Java API. With Mono, they just got 100% compliance with .NET 2.0 which is so, like, 2003. Correct me if I'm wrong, but surely there has to be some kind of downside to always playing catch-up with a closed-source framework?

Personally, I just code the fastest with Java. I have no idea why, but it's true. So that's what I go with. That being the case I would like to see more widespread use of desktop Java, but I certainly have no problem with people using Mono.

---

### Post by Dragonbite on 2009-10-15
Does anybody know of some desktop Java applications that are pretty good?

---

### Post by directhex on 2009-10-15
Okay, this touched upon a few points, which are easier to look at independently

Firstly, why don't desktop people typically use Java? There are a few reasons.

[LIST]
[*]It only became usable Free Software in mid-2007 (it took about 6 months from the initial announcement to the mostly-Free release of all required components)
[*]Non-Sun implementations have traditionally been pretty ropey
[*]It's a hundred meg big - a very large dependency for an app.
[*]Java is very RAM-hungry compared to many of the alternatives
[*]Swing (the normal Java GUI toolkit) looks very alien on every OS; native toolkit wrappers such as SWT haven't seen much adoption
[*]If it's not in Java, it's a pain in the *** to use (Java has poor interop with existing C-based libraries)
[/LIST]

It has a bunch of plus-points, of course, and is very popular in Enterprise places where a little speed loss is completely mitigated by the ability to run the same app on things like AIX or Solaris, without any of the usual worries regarding security thanks to being JITtered. It's also needed for Eclipse, which is bafflingly popular as an IDE.

So. Why would people have any interest in using Mono?

[list]
[*]It's been Free since day one, in 2001 - giving it several years' head start amongst Free Software developers
[*].NET in general makes it very easy to plug gaps by using existing C libraries (JNA in Java 7 should give Java a similar ability)
[*]From day 1, Mono has focused on the 100% native Gtk# toolkit, so Mono apps feel completely at home on a Linux desktop (support for the Windows-native System.Windows.Forms toolkit is newer - and looks like ***)
[*]The class library is much less spaghetti-esque, meaning apps require a MUCH smaller footprint than if they use Java (e.g. F-Spot and Tomboy together need 20-ish meg of Mono, not 100 meg of OpenJDK)
[/list]

There are, of course, downsides - not least of which is the politics surrounding it.

So. Why doesn't Java overtake Mono? Basically there just hasn't been any real push for new apps being written with Java - and the vast majority of people who protest about Mono don't develop in *any* language. Stuff like Banshee or GNOME Do are made by independent developers who have had the choice in front of them - and picked Mono. Which headline apps does Java have? Eclipse and Azureus? Both are poster children for bloat.

It would be nice to see more apps using Java, if anything because competition drives innovation, but I just haven't observed any movement towards it.

---

### Post by openfly on 2009-10-15
Java is a steaming pile of crap.  It's alpha release software.

No one should be using java in a production environment.  If you are using java in a production environment you should be fired.

---

### Post by directhex on 2009-10-15
> **nmccrina said:**
> I don't have any experience developing in Mono, but what has always puzzled me is that using Java you always have access to the entire, up-to-date Java API. With Mono, they just got 100% compliance with .NET 2.0 which is so, like, 2003. Correct me if I'm wrong, but surely there has to be some kind of downside to always playing catch-up with a closed-source framework?

This is a common misconception. Mono has features today currently scheduled for .NET 5.0 only, and other features it will never have. Many of the most popular apps (e.g. GNOME Do) make use of features from .NET 3.5 such as LINQ.

The *class library* doesn't contain every library Microsoft have made, but that's because we pretty much don't need or want them (e.g. why would we want WPF, when we have Gtk#?)

---

### Post by nmccrina on 2009-10-15
> **Dragonbite said:**
> Does anybody know of some desktop Java applications that are pretty good?

Limewire, Netbeans, and Eclipse come to mind immediately. EDIT: Ok, so it seems the consensus is that Eclipse may or may not be a "good" app. 

I'm writing an as-yet-unnamed home school planning and record keeping application that will surely join the list of Great Java Apps when it is released. :P

---

### Post by nmccrina on 2009-10-15
> **directhex said:**
> This is a common misconception. Mono has features today currently scheduled for .NET 5.0 only, and other features it will never have. Many of the most popular apps (e.g. GNOME Do) make use of features from .NET 3.5 such as LINQ.

The *class library* doesn't contain every library Microsoft have made, but that's because we pretty much don't need or want them (e.g. why would we want WPF, when we have Gtk#?)

Ah, I see. That makes sense. :)

---

### Post by Simian Man on 2009-10-15
Java is designed for managers.  C# is designed for developers.  Enterprise is full of managers, so Java gets used a lot.  OSS is full of developers, so C# gets used a lot.  Pretty Simple.

> **Dragonbite said:**
> Does anybody know of some desktop Java applications that are pretty good?

Tuxguitar is another one.  It is a guitar tab editing and playback tool, and is really awesome.

---

### Post by Dragonbite on 2009-10-15
> **nmccrina said:**
> Limewire, Netbeans, and Eclipse come to mind immediately. EDIT: Ok, so it seems the consensus is that Eclipse may or may not be a "good" app. 

I think it's interesting that 2 of those are apps used to MAKE Java applications. ;)  Although I don't get why one of the requirements for Monodevelop on Windows is .NET 3.5?  

Was hoping to put Mono on the system (and Monodevelop) and skip putting in Microsoft's .NET since I heard (long ago, not sure if it is true) Mono is lighter on the system than .NET.

Makes me wonder just how much further Mono would make it if it weren't for the "political backlash"?

---

### Post by Slug71 on 2009-10-15
> **toupeiro said:**
> Java is a Ford, Mono is a Chevy.  


In that case we should defs go Java. :P

---

### Post by nmccrina on 2009-10-15
> **Dragonbite said:**
> I think it's interesting that 2 of those are apps used to MAKE Java applications. ;)  

Yeah, isn't that kind of how viruses behave? :)

---

### Post by juancarlospaco on 2009-10-15
**Angry IP Scanner** its a good Java App :)

**Sockso** is very nice too, **Vuze**, and others

---

### Post by Bad Sector on 2009-10-15
> **Dragonbite said:**
> I think it's interesting that 2 of those are apps used to MAKE Java applications. ;)  Although I don't get why one of the requirements for Monodevelop on Windows is .NET 3.5? 

And one of the major reasons i prefer Java to some other altenative, is the quality of the development environments. Basically Eclipse. I also use NetBeans now and then, because of the GUI designer, but NB is awfully slow (which is not a surprise - Swing is the slowest toolkit ever made, and in my opinion the major reason why Java is perceived as slow since SWT is very lightweight).

---

### Post by argor on 2009-10-15
> **Dragonbite said:**
> Does anybody know of some desktop Java applications that are pretty good?
the best java program that i hve seen is ArtOfIllusion

---

### Post by Warpnow on 2009-10-15
Vuze is an amazing app. Bloated, but...it definitely shows what can be done.

---

### Post by directhex on 2009-10-15
> **Dragonbite said:**
> I think it's interesting that 2 of those are apps used to MAKE Java applications. ;)  Although I don't get why one of the requirements for Monodevelop on Windows is .NET 3.5?  

Because it's a more common use-case. To transform MD-for-Windows, then install Mono, edit the shortcut, and set it to run "mono c:\foo\monodevelop.exe" rather than "c:\foo\monodevelop.exe" - Mono will run it just as well

---

### Post by Firestem4 on 2009-10-15
FreeMind is a pretty cool application written in Java.

---

### Post by keiichidono on 2009-10-16
I want to know why there isn't much uptake of new languages like Vala and Genie as opposed to Mono. They're supposed to have the same advantages of Mono but actually be easier to use and have no 'politics' involved.

---

### Post by Dragonbite on 2009-10-16
> **CalvinB said:**
> I want to know why there isn't much uptake of new languages like Vala and Genie as opposed to Mono. They're supposed to have the same advantages of Mono but actually be easier to use and have no 'politics' involved.

I think one which has helped Mono rise so much in popularity are the visible, usable and popular applications that can be pointed to as "that is Mono".

The language the applications are written in is not of major consequence (like what is Pidgin written in?) or interest except for the developer looking for a specific language.

Honestly, though, there are so many languages that I've just never heard of floating out there and most of them are of little use or interest to anyone outside of programmers.

---

### Post by forrestcupp on 2009-10-16
> **Dragonbite said:**
> I think one which has helped Mono rise so much in popularity are the visible, usable and popular applications that can be pointed to as "that is Mono".

I don't think it's the apps, but the power behind the power behind the apps.  It has nothing to do with Mono, but the .Net behind Mono.  Microsoft has been pushing developers pretty heavily to move to C# and .Net.  They push it to the point that even Visual C++ programmers are encouraged to use managed C++ with .Net.  I'd say the majority of company dev teams probably use Visual Studio, and they're being railroaded that way.

Since the majority is being railroaded that way, the Linux community has to try to keep up with some kind of cross-platform alternative, just like everything else the Linux community does.

Java has been around much longer than Mono or .Net.  They have had their opportunity to become a giant for desktop apps, and they missed their chance.  We're not being railroaded toward Java, so there's no need to mess with it.

---

### Post by BrokenKingpin on 2009-10-16
I much prefer coding in Mono/.Net than Java.

---

### Post by fevans on 2009-10-17
> **Dragonbite said:**
> Shouldn't the anti-Mono people put their efforts into building and improving Java and Java applications to replace Mono and provide a real (cross-platform) replacement?

Any effort that involves actual code is a valid rebuttal. For example, gnote is good because it gives users a choice, regardless of any pro/anti mono sentiments.

Java is good for some back-end activities. I'm sure the mono team could improve it. But given that the combined force of Sun, Oracle, and IBM have already spent the last 20 years on java, we need to consider the possibility that java is reaching a point of diminishing returns. 

Java exists, and will always remain a valid option, but I don't want to be forced to use java or C#. I want options and the ability to select the right tool for the job.

Also people often forget that IKVM runs very well in mono, allowing developers to leverage C# and java in the same runtime.

---

### Post by forrestcupp on 2009-10-17
> **fevans said:**
> I want options and the ability to select the right tool for the job.

Great point.  Why restrict ourselves?  It's crazy to limit ourselves just because either we're mad that Mono is an alternative to something MS created, or we're mad that it's led by Novell.  Compiz was released by Novell, too, and you don't hear nearly as many people mad about that.

---

### Post by jonmartin on 2009-10-30
> **Dragonbite said:**
> Does anybody know of some desktop Java applications that are pretty good?

Well, most Java IDE's are written in Java, JDeveloper, Eclipse, Netbeans ... and yes, they're pretty good.

Other than that, there aren't that many Java desktop apps around. Wuala, Limewire comes to mind though ...

---

### Post by jonmartin on 2009-10-30
> **Simian Man said:**
> Java is designed for managers.  C# is designed for developers.  Enterprise is full of managers, so Java gets used a lot.  OSS is full of developers, so C# gets used a lot.  Pretty Simple.
...


Uh, how many C# apps in the apache projects? Hm ... think you're mistaken here...

---

### Post by Dragonbite on 2009-10-30
> **jonmartin said:**
> Uh, how many C# apps in the apache projects? Hm ... think you're mistaken here...

You mean like [[COLOR="Blue"]MojoPortal[/COLOR]]("http://www.mojoportal.com/home.aspx")?  That's a C# (and Mono-friendly) CMS ASP.NET application.

EDIT: whoops.. looked up Apache projects, and now I see the list.  Although I'm not sure how indicative it is, though.  Those don't look like client applications.

---

### Post by jonian_g on 2009-10-30
> **Dragonbite said:**
> Does anybody know of some desktop Java applications that are pretty good?

Well you can find some here: [http://www.java-apps.org/](http://www.java-apps.org/)

The ones I know are: limewire/frostwire, vuze, jdownloader, eclipse, netbeans, visual paradigm

Also OpenOffice uses java a lot. And there are many games created in java. One that comes in mind is [Tribal Trouble]("http://tribaltrouble.com/").

The java apps I use are limewire, jdownloader and visual paradigm. As for mono, I don't use any mono apps. I don't need Tomboy, F-spot and Gnome Do and my music organiser is Listen.

---

### Post by Dragonbite on 2009-10-30
Oh, one thing I do like about Java is their logo... mmm... coffee..... I mean, it's not like I can drink or want a Monkey (Mono's logo)!? ;)

@jonian_g: thanks for the link.

---

### Post by YeOK on 2009-10-30
> **CalvinB said:**
> I want to know why there isn't much uptake of new languages like Vala and Genie as opposed to Mono. They're supposed to have the same advantages of Mono but actually be easier to use and have no 'politics' involved.

I've just started with Vala. I love it so far. The downside is a lack of good documentation for some of Vala's bindings. For example, I can't seem to find any information on MySql bindings in Vala. 

It took me a while to find a good IDE too, I'm using monodevelop with the Vala plugin, it seems to be working well so far. I'm sure Vala will take off, its got a huge advantage over mono and java in having no runtime libs (so uses a lot less memory) mobile devices and older computers will love it.

[http://live.gnome.org/Vala]("http://live.gnome.org/Vala")

---

### Post by zekopeko on 2009-10-30
> **YeOK said:**
> I've just started with Vala. I love it so far. The downside is a lack of good documentation for some of Vala's bindings. For example, I can't seem to find any information on MySql bindings in Vala. 

It took me a while to find a good IDE too, I'm using monodevelop with the Vala plugin, it seems to be working well so far. I'm sure Vala will take off, its got a huge advantage over mono and java in having no runtime libs (so uses a lot less memory) mobile devices and older computers will love it.

[http://live.gnome.org/Vala]("http://live.gnome.org/Vala")

As I understand Vala is some king of a higher level wrapper to base C libraries. You write in a C#/Java-like language and it compiles C then to binary.
The problem that I remember is that you have to have GObject Introspection or something to probe C libs for function/classes, so that you can use them in Vala.
Am I getting this right?
How does it compare to Mono/Java? Pluses and minuses would be appreciated.

---

### Post by zekopeko on 2009-10-30
On the topic:

From my casual understanding of Java and anecdotal evidence Java is pretty bloaty on the desktop.
I trust directhex when he says that it's a mess to package Java apps. There was that whole "packaged Eclipse is ancient in Ubuntu" thing that pretty much pointed how absurdly difficult it was to package the app for Ubuntu thanks to circular dependencies and what not.

Mono is far less hungry for memory then Java and it has great apps on Linux (and soon on Windows and Mac OSX). Not to mention that it's getting really good really fast, most likely due to heavy commercialization by Novell and other software vendors.

---

### Post by Dragonbite on 2009-10-30
> **zekopeko said:**
> Mono is far less hungry for memory then Java and it has great apps on Linux (and soon on Windows and Mac OSX). Not to mention that it's getting really good really fast, most likely due to heavy commercialization by Novell and other software vendors.

Plus, I think the desktop apps help in pushing development. While an Enterprise has certain speed requirements, they may be more accepting of some performance hits, while users using apps that suddenly become unresponsive, or jumpy music playback are going to scream and scream loud!  This helps keep the development focused.

---

### Post by Alpaca? on 2009-10-30
> **directhex said:**
> 
[LIST]
[*]Java is very RAM-hungry compared to many of the alternatives
[/LIST]
I tottally agree with that, I find Java way to slow when I'm developing something.
> **directhex said:**
> 

[LIST]
[*]Swing (the normal Java GUI toolkit) looks very alien on every OS; native toolkit wrappers such as SWT haven't seen much adoption
[/LIST]


You can skip the whole swing thing, and tell Java to use the System default look and feel. However, getting Java to do anything OS specific makes me cry.

> **directhex said:**
> 

[LIST]
[*]If it's not in Java, it's a pain in the *** to use (Java has poor interop with existing C-based libraries)
[/LIST]


Again, super frustrating in that regard. Can't do anything OS specific without having to code it specifically.

> **directhex said:**
> ...Eclipse and Azureus? Both are poster children for bloat.

Again, I agree, however, Netbeans is still one of the most well written pieces of software I have ever seen, even if it gets slow sometimes.


If Java had better OS integration, and wasn't frustratingly slow, I would totally be in on it.


*Knock Knock*

Who's there?
















Java!

---

### Post by YeOK on 2009-10-30
> **zekopeko said:**
> As I understand Vala is some king of a higher level wrapper to base C libraries. You write in a C#/Java-like language and it compiles C then to binary.
The problem that I remember is that you have to have GObject Introspection or something to probe C libs for function/classes, so that you can use them in Vala.
Am I getting this right?
How does it compare to Mono/Java? Pluses and minuses would be appreciated.

I have only just started using it, so I can't give you many plus / minus points. Many bindings for GObjects are already in Vala, so you don't have to make them yourself. Yes, Valar is a C# like language that first converts your source into C, then compiles. Genie uses the same Compiler as Vala, but its a more perl like language. 

Its very easy to use, a lot like mono is now. 

hello.vala;
```

using GLib;

public class Test.HelloObject : GLib.Object {

    public static int main(string[] args) {

        stdout.printf("Hello, World\n");

        return 0;
    }
}

```

Vs hello.cs (Mono)
```

using System;

namespace hello
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Console.WriteLine("Hello World!");
		}
	}
}

```

Vala compile command is also easy, 'valac -o hello hello.vala' gives you a bianry, you can add '-C' to get the generated C source code. Downsides are like I said, its still quite new so Docs are a little hard to find. I've also not found the perfect IDE for it yet, monodevelop works well for now though.

---

### Post by mehaga on 2009-10-30
I am no zealot. I use and like both Java and .NET, Linux and Windows. That said...

Just for being one of the first software products to treat Linux as equal to Windows and Mac, I will always love Java (and respect Sun). Also, I think people should help Java work better on Linux, instead of porting .NET to it. Swing too slow for you? Make Java+GTK or Java+Qt work better. Why would you port entire platform?

---

### Post by directhex on 2009-10-30
> **vekaz said:**
> Why would you port entire platform?

Because some of the suck is built directly into the platform. Fr'example, the library interop is only now being fixed in Java 7 using JNA - it's been in .NET (and Mono) since day 1, over 5 years ago. For the entire length of Mono's life, you would need to write JNI nonsense in order to invoke a C library. If you're wrapping a GUI toolkit, that's a lot of C invoking. Can you blame devs for not wanting that pain?

---

### Post by mehaga on 2009-10-30
> **directhex said:**
> Because some of the suck is built directly into the platform. Fr'example, the library interop is only now being fixed in Java 7 using JNA - it's been in .NET (and Mono) since day 1, over 5 years ago. For the entire length of Mono's life, you would need to write JNI nonsense in order to invoke a C library. If you're wrapping a GUI toolkit, that's a lot of C invoking. Can you blame devs for not wanting that pain?
So, they were thinking 'this JNI stuff is awful. let's fix that by porting .net to linux.'? Or is there some other suck that is built into the platform?

---

### Post by Dragonbite on 2009-10-30
> **vekaz said:**
> So, they were thinking 'this JNI stuff is awful. let's fix that by porting .net to linux.'? Or is there some other suck that is built into the platform?

Ultimately either nobody noticed, or nobody cared enough to fix that, while other people for numerous reasons focuses on Mono and has built it to what it is today.

That's why I say visible apps do have an impact because non-developers will see and argue about things and they are harder to calm down than developers.

---

### Post by directhex on 2009-10-30
> **vekaz said:**
> So, they were thinking 'this JNI stuff is awful. let's fix that by porting .net to linux.'? Or is there some other suck that is built into the platform?

Microsoft were sued for making their own JNI replacement (JDirect), which is the reason . NET was created in the first place. So, um, who would be stupid enough to make their own incompatible Java and risk being sued by Sun?

---

### Post by hobo14 on 2009-10-30
I have to admit, I'm out of my depth in this thread, because I've never heard of Mono.

I take it it's a language, used in a somewhat similar fashion to Java???

If so, I don't really understand the title of this thread; Java is by far the most used language...

I think, from memory, second and third most used are C and C++.

---

### Post by Frak on 2009-10-30
> **hobo14 said:**
> I have to admit, I'm out of my depth in this thread, because I've never heard of Mono.

I take it it's a language, used in a somewhat similar fashion to Java???

If so, I don't really understand the title of this thread; Java is by far the most used language...

I think, from memory, second and third most used are C and C++.
"Most used" is a flaky statement. If you mean "Most used on wide platforms", C and C++ tie each other. The source code of a non-disclosed-operating-system mixes C and C++ heavily. Gnome is written in C, but KDE is written in C++ (QT, but there's a line blur). Mac OS X is mostly written in ObjC, which is neither C or C++, and equally resembles each (IMHO).

If you recognize what language is used more by default in say Ubuntu or Windows, C# (Mono) easily overtakes Java. Some apps, such as Tomboy, come preinstalled on Ubuntu and are written in C# and run on the mono interpreter. Windows has many, *many* tools by default that are written in C# (as of Windows 7).

---

### Post by hobo14 on 2009-10-30
> **Frak said:**
> "Most used" is a flaky statement. If you mean "Most used on wide platforms", C and C++ tie each other. The source code of a non-disclosed-operating-system mixes C and C++ heavily. Gnome is written in C, but KDE is written in C++ (QT, but there's a line blur). Mac OS X is mostly written in ObjC, which is neither C or C++, and equally resembles each (IMHO).

If you recognize what language is used more by default in say Ubuntu or Windows, C# (Mono) easily overtakes Java. Some apps, such as Tomboy, come preinstalled on Ubuntu and are written in C# and run on the mono interpreter. Windows has many, *many* tools by default that are written in C# (as of Windows 7).

Here is the ranking table I was looking for: [TIOBE]("http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html")

Looks like I was wrong; PHP is higher than C++ this year.


Apologies for my misunderstanding the thread, I was thinking, as per the TIOBE chart, about which language is currently being used in development more than others.
You guys were (apparently) talking about which has more "presence" in current OS user interface code.

---

### Post by phrostbyte on 2009-10-30
> **zekopeko said:**
> As I understand Vala is some king of a higher level wrapper to base C libraries. You write in a C#/Java-like language and it compiles C then to binary.
The problem that I remember is that you have to have GObject Introspection or something to probe C libs for function/classes, so that you can use them in Vala.
Am I getting this right?
How does it compare to Mono/Java? Pluses and minuses would be appreciated.

The problem is C has no syntax for objects. Vala is C with syntactical sugar for the GObject object model (a really advanced object model that Gnome uses extensively). Anything you can do with C you can do with Vala, but when are dealing with GObject enabled libraries, Vala makes working with them really intuitive.

And you are right Vala's current compiler spits out C code. The C code can then be automatically compiled with a C compiler like gcc. It might be possible to have Vala spit out GCC IL or LLVM IL in the future, but this isn't really necessary.

---

### Post by Frak on 2009-10-30
> **phrostbyte said:**
> It might be possible to have Vala spit out GCC IL or LLVM IL in the future, but this isn't really necessary.

I always wondered what the big push for this was.

---

### Post by Warpnow on 2009-10-31
Python seems to be becoming a very heavily used application in more and more desktop linux applications.

---

### Post by Frak on 2009-10-31
> **Warpnow said:**
> Python seems to be becoming a very heavily used application in more and more desktop linux applications.
Easy to learn, easy to use, and supported on nearly every Linux installation.

---

