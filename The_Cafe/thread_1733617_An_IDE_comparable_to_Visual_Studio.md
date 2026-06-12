---
title: "An IDE comparable to Visual Studio?"
date: 2011-04-19
forum: The Cafe
---

### Post by cyb3r_sn4k3 on 2011-04-19
So I've been using visual studio for quite some time, before I migrated to Ubuntu :D and I love it. All I actually miss is Vegas, visual studio and also photoshop(which runs on wine great now). And I dual boot ubuntu with Windows 7 but its a pain to reboot each time I want to do some programming in visual studio(I rarely video edit so that aint a problem, but I use visual studio alot so....). I tried monodevelop but it was very hard to do the GUI part of it. (Don't know whether its because of the IDE or its default with GTK)


So what I am asking is that, is there another IDE or plugin for mono, which has similar GUI editing to that of Visual Studio? I mostly use C# and ASP.NET.

---

### Post by RiceMonster on 2011-04-19
For .NET, MonoDevelop is as close as you're going to get, unfortunately.

---

### Post by Dragonbite on 2011-04-19
I'm currently doing ASP.NET development in Monodevelop and Visual Studio.

I have Dropbox installed and that's where my solution files go. That way when I work on one, it gets transfered to the other the next time I go into it.

The only thing that hasn't worked is publishing it, because I'm publishing it locally (C:/Inetpub/www/...) and Monodevelop doesn't like that :lolflag:

But with XSP I am able to debug and see my site in Monodevelop as well as VS.

Oh, and I am using a MySql database which I backup, put the .sql file in the dropbox, and can restore any changes/data on either environment.

This is also handy for me because I have my dual-boot laptop as well as using my large-screen desktop.

I'm not sure how well UbuntuOne in Windows works, but I guess it can do the same thing.  I'm just thinking I may keep this type of setup even when I am not using Ubuntu (Fedora, openSUSE, heck, even OS X).

---

### Post by Legendary_Bibo on 2011-04-19
Gambas2

---

### Post by directhex on 2011-04-19
> **cyb3r_sn4k3 said:**
> So I've been using visual studio for quite some time, before I migrated to Ubuntu :D and I love it. All I actually miss is Vegas, visual studio and also photoshop(which runs on wine great now). And I dual boot ubuntu with Windows 7 but its a pain to reboot each time I want to do some programming in visual studio(I rarely video edit so that aint a problem, but I use visual studio alot so....). I tried monodevelop but it was very hard to do the GUI part of it. (Don't know whether its because of the IDE or its default with GTK)


So what I am asking is that, is there another IDE or plugin for mono, which has similar GUI editing to that of Visual Studio? I mostly use C# and ASP.NET.

MonoDevelop has a GUI designer, for GTK# apps written in C#

You are likely struggling because you've never used a container-based layout system before. WinForms is pixel-based, GTK+ is container-based.

There are a multitude of reasons why pixel-based is wrong by design, but the two main ones are "pixel-based layouts cannot scale properly to handle font size or theme size changes", and "pixel based layouts do not work with right-to-left (hebrew etc) users".

Think of it like using <table> in HTML to design a page - use a combination of various container widgets, mainly VBox, HBox and Table, to lay out your widgets how you want them. Just drag widgets and containers from the toolbox into the design view, and your UI will appear before your eyes. You can right-click on elements to alter them (e.g. add or remove entries in a VBox/HBox)

---

### Post by arunb on 2011-04-20
Try Lazarus IDE for FreePascal [http://www.lazarus.freepascal.org/]("http://www.lazarus.freepascal.org/"), its like Visual Studio has a Form designer like Visual Basic, with all the UI controls, its multi-platform.

FreePascal (open source) is similar to Delphi, most of the source code in Delphi can be easily re-used in FreePascal.

Support for FreePascal is well provided in various forums.

FreePascal has a large range of components for various jobs, for example SerialPort access, HTTP,FTP control etc.

The programming style in FreePascal is different from Visual Basic, or C, C++, but is very easy to learn. 

The source code is easily readable and easy to learn, unlike C or C++ which is more cryptic.

I have switched from Visual Basic 6.0 to FreePascal ever since Microsoft dropped support. I found it easy to adapt to FreePascal. I think Lazarus IDE is one of the best available for FreePascal.

Your choice of programming language will of course depend on what exactly you want to do, but for most uses FreePascal comes up very well.


thanks
a

---

### Post by Johnsie on 2011-04-20
Interesting thread. I'm a big fan of Visual Studio and think it's one of Microsofts better products. It's also the scourge of many {}; diehards (php, c++ , java etc). I guess it's just a different way of programming and it helps to know both styles. 

Eclipse is probably closest for experienced developers, but not quite as detailed as VS.

+1 for Gamabas2, I really like Gambas for RAD on Ubuntu. I think it's highly underrated and should be promoted more. Don't write it off just because it's a VB-type language.


I'm going to try this free pascal thing in work today. At the  moment a mixture of PHP and Visual Studio Express is meeting my needs for developing the Windows applications  that our company uses. We can't switch to Ubuntu because of external software requirements, customised hardware and the fact that the Windows licenses were bought before I came here. I do run the server end of the apps on Ubuntu server though ;-)

---

### Post by Majorix on 2011-04-20
Hate to say this, but speaking from experiences with other IDEs, nothing matches VS when it comes to C#/VB.NET/ASP.NET development. Monodevelop is rather poor.

If you plan on learning Java, you could try Netbeans.

---

### Post by Dragonbite on 2011-04-20
It's doing alright for ASP.NET development for me at this point, but that may also be attributed to me not using the drag-and-drop GUI builder.  Rather, I type it in the source view and rely on the auto-complete of options to help me with what that #$%^ actual attribute is called ;) !

Then again, the front end doesn't get into that fight over WinForms vs GTK+

---

### Post by forrestcupp on 2011-04-20
> **Majorix said:**
> Hate to say this, but speaking from experiences with other IDEs, nothing matches VS when it comes to C#/VB.NET/ASP.NET development. Monodevelop is rather poor.In my opinion, VS is better than anything else at everything that it can do.

> **Majorix said:**
> If you plan on learning Java, you could try Netbeans.
Even though it's a lot more of a pain to get working, I personally like Eclipse a little better for Java.

---

### Post by BrokenKingpin on 2011-04-20
MonoDevelop does have a GUI editor for GTK, but I find it harder than the VS WinForms editor (mainly because GTK is container driven as mentioned above).

There is however a WinForms editor that you can get that just is not packaged with MonoDevelop. It is not 100% complete, but apparently usable:
[http://www.mono-project.com/WinForms_Designer](http://www.mono-project.com/WinForms_Designer)

---

### Post by directhex on 2011-04-20
> **forrestcupp said:**
> Even though it's a lot more of a pain to get working, I personally like Eclipse a little better for Java.

In my personal circle of hell, I can hack all day on awesome projects, but only if I use Eclipse.

---

### Post by cyb3r_sn4k3 on 2011-04-20
> **BrokenKingpin said:**
> MonoDevelop does have a GUI editor for GTK, but I find it harder than the VS WinForms editor (mainly because GTK is container driven as mentioned above).

There is however a WinForms editor that you can get that just is not packaged with MonoDevelop. It is not 100% complete, but apparently usable:
[http://www.mono-project.com/WinForms_Designer](http://www.mono-project.com/WinForms_Designer)

The screenshots looks promising, I'll try it and get back to you guys :).

---

### Post by wrtpeeps on 2011-04-21
As has been said Monodevelop is probably the best but Visual Studio is by far the greatest IDE around.

---

### Post by NovaAesa on 2011-04-21
There's nothing "comparable" to VS on linux. The closest you will get is probably Eclipse. I think the reason is that many of the hardcore coders (and even non-hardcore such as myself) like to use emacs. I'll be the first to admit that it's a total pain and non-user friendly if you aren't used to it, but once you learn how to use it properly it's amazing!

---

### Post by Dragonbite on 2011-04-21
Netbeans 7 is releasd

> [NetBeans 7.0 arrives with Java 7 support]("http://www.h-online.com/open/news/item/NetBeans-7-0-arrives-with-Java-7-support-1231080.html") 
Oracle has announced the availability of NetBeans 7.0.The major feature of 7.0 is the support for the Java 7 features in JDK 7; this includes handling the Project Coin language enhancements and appropriately extending code completion and hinting. JDK 7 is currently being released as early access snapshots and, once released in late July, the NetBeans developers will release a NetBeans 7.0.1 which will synchronise with the final version of the JDK, and then NetBeans 7.1 in October.

---

### Post by BrokenKingpin on 2011-04-21
> **NovaAesa said:**
> I think the reason is that many of the hardcore coders (and even non-hardcore such as myself) like to use emacs.
Um... no. I don't dispute the fact that a lot of programmers use emacs, but it is not the reason why there is nothing "comparable" to VS. I think there are a few IDE that are comparable and well suited for profession programming. The Form Designer in VS is hard to match though.

And VIM > emacs :P

---

