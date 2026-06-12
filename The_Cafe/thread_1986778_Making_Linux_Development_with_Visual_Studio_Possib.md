---
title: "Making Linux Development with Visual Studio Possible"
date: 2012-05-25
forum: The Cafe
---

### Post by bricklets on 2012-05-25
Meet VSLinux - ultimate solution for Linux code developers  that prefer to use Microsoft Visual Studio as code editor. VSLinux  provides means to generate Visual Studio project for arbitrary source  code tree, initiate builds on remote Linux machines and analyze  compilation errors produced by remote system exactly as if it was local  build with Microsoft compiler.  	[SLinux is a free tool published as a part of Daynix Bricklets project.
VSLinux home page: [https://github.com/daynix/bricklets/wiki/VSLinux-bricklet-documentation](https://github.com/daynix/bricklets/wiki/VSLinux-bricklet-documentation)
Bricklets project home page: [http://daynix.com/index.php?option=com_content&view=article&id=62&Itemid=71](http://daynix.com/index.php?option=com_content&view=article&id=62&Itemid=71)


What do you think?

---

### Post by forrestcupp on 2012-05-25
Wow! This is the first spam that I didn't want to report.

---

### Post by drdos2006 on 2012-05-25
Does this mean that programs written for Windows can be ported to linux ?? (Assuming you have the source code ??)

regards

---

### Post by forrestcupp on 2012-05-25
> **drdos2006 said:**
> Does this mean that programs written for Windows can be ported to linux ?? (Assuming you have the source code ??)

regards

No. Assuming it's real, it just means that you can use Visual Studio to write Linux programs. VS is the best IDE I've ever seen, but I don't think it would be ideal in this situation. You'd have to write the code in Windows and boot to Linux to compile it. That would make debugging a major pain in the backside.

---

### Post by georgelappies on 2012-05-26
> **bricklets said:**
> 
What do you think?

Why would anyone want to do this? Linux has a much better development chain set of tools for Linux development.

Sure, I do a lot of windows development and when I code for windows there is no better IDE then VS, its the best.

But one cannot make a direct comparison between VS and any one Linux IDE as Linux itself is an IDE, all those commands like awk, sed, grep combined with pipng and vim makes VS look severely limited.

---

### Post by overcast on 2012-05-26
I have seen some of the places where people in charge of the computer let you use the system way you want but they don't want you to tamper with OS. So for these people such tool can be useful. Considering cross platform libs like pygtk, ironpython and mono, i don't think we need VS Linux.

---

### Post by forrestcupp on 2012-05-26
> **overcast said:**
> Considering cross platform libs like pygtk, ironpython and mono, i don't think we need VS Linux.

Now that you mention it, that is exactly why we *do* need VS Linux. You can use a multitude of cross platform libs, like pyGTK (well, not that because it's Python), wxWidgets, Ogre3D, etc., and program them in VS to be compiled for Windows. In that case, you would do all your debugging in the Windows environment. But then, it's a pain in the backside to set it up to be compiled for Linux. You don't have to change your code because it's cross platform code, but you *do* have to come up with your own config and install files and set it up to compile in Linux. I assume VS Linux does that for you, which would be handy, in my opinion.

---

### Post by Bandit on 2012-05-26
> **forrestcupp said:**
> No. Assuming it's real, it just means that you can use Visual Studio to write Linux programs. VS is the best IDE I've ever seen, but I don't think it would be ideal in this situation. You'd have to write the code in Windows and boot to Linux to compile it. That would make debugging a major pain in the backside.

Cant it be run in WINE?

---

### Post by mehaga on 2012-05-26
> **georgelappies said:**
> Why would anyone want to do this? Linux has a much better development chain set of tools for Linux development.

Sure, I do a lot of windows development and when I code for windows there is no better IDE then VS, its the best.

But one cannot make a direct comparison between VS and any one Linux IDE as Linux itself is an IDE, all those commands like awk, sed, grep combined with pipng and vim makes VS look severely limited.

I've heard this before and I'd really love to know how you do some more advanced stuff in your Linux DE, like refactoring? Or like anything Resharper does in VS? How do you 'pull members up'? How do you find a class by typing only capital letters of its camel case name? What can you do in Linux that makes VS look 'severely limited'?

---

### Post by forrestcupp on 2012-05-26
> **Bandit said:**
> Cant it be run in WINE?

No. VS is garbage in wine. You have to run it in Windows.

---

### Post by rg4w on 2012-05-26
Have you considered using REALBasic?  They have an IDE with native compilation for Linux right out of the box.

---

### Post by BeRoot ReBoot on 2012-05-26
> **bricklets said:**
> Meet VSLinux - ultimate solution for Linux code developers  that prefer to use Microsoft Visual Studio as code editor. VSLinux  provides means to generate Visual Studio project for arbitrary source  code tree, initiate builds on remote Linux machines and analyze  compilation errors produced by remote system exactly as if it was local  build with Microsoft compiler.      [SLinux is a free tool published as a part of Daynix Bricklets project.
VSLinux home page: [https://github.com/daynix/bricklets/wiki/VSLinux-bricklet-documentation](https://github.com/daynix/bricklets/wiki/VSLinux-bricklet-documentation)
Bricklets project home page: [http://daynix.com/index.php?option=com_content&view=article&id=62&Itemid=71](http://daynix.com/index.php?option=com_content&view=article&id=62&Itemid=71)


What do you think?

[IMG]http://i.imgur.com/7LO17.jpg[/IMG]

---

### Post by bricklets on 2012-05-28
Because we find it cool and comfortable ;)

---

### Post by bricklets on 2012-05-28
> **rg4w said:**
> Have you considered using REALBasic?  They have an IDE with native compilation for Linux right out of the box.
Most interesting part is development for embedded platforms. You have to cross-compile for embedded platform with specific compiler and kernel. There is no other option (except using native Linux IDEs). Also, Visual Studio it just way better, especially for people came from Windows world.

---

### Post by bricklets on 2012-05-28
> **forrestcupp said:**
> No. Assuming it's real, it just means that you can use Visual Studio to write Linux programs. VS is the best IDE I've ever seen, but I don't think it would be ideal in this situation. You'd have to write the code in Windows and boot to Linux to compile it. That would make debugging a major pain in the backside.
Just give it a try. You should not boot to Linux to compile it, assuming Linux runs in parallel, say on virtual machine, Visual Studio with our extension logins via SSH and runs compilation automatically, just press F7. Also it could run the application being compiled and fetch output  to Visual Studio "output" window or show application windows (assuming it is a GUI application) on Windows Desktop with local Xserver. It's a matter of configuration.

And the most interesting part - yes, it is real.

---

### Post by neu5eeCh on 2012-05-28
Strange that they would SPAM here given that:

[Microsoft Delivers a Blow to Open Source with Visual Studio 11]("http://www.pcworld.com/businesscenter/article/256339/microsoft_delivers_a_blow_to_open_source_with_visual_studio_11.html")

Almost makes me think that whoever posted this did so with a whiff of sarcasm.

---

### Post by bricklets on 2012-05-28
> **VTPoet said:**
> Strange that they would SPAM here given that:

[Microsoft Delivers a Blow to Open Source with Visual Studio 11]("http://www.pcworld.com/businesscenter/article/256339/microsoft_delivers_a_blow_to_open_source_with_visual_studio_11.html")

Almost makes me think that whoever posted this did so with a whiff of sarcasm.
Pity to see word "SPAM" here.

We just announced a FREE and OPEN SOURCE tool WE developed. We believe it will be very useful for some people. We don't try to sell it. It's free and BSD-licensed!
Isn't it what open source about?

Moreover, it is in "[The Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11")" area open for announcements, so we behave fair.
We really surprised by your post which is pretty rude as we see it.

---

### Post by BrokenKingpin on 2012-05-28
If you are developing in .Net, MonoDevelop is a decent alternative to Visual Studio. It supports the same Visual Studio solutions and projects, so porting .Net applications is pretty easy.

That being said, it can be buggy and is no where near as feature complete as Visual Studio, but overall it is pretty damn good.

---

### Post by neu5eeCh on 2012-05-28
> **bricklets said:**
> Pity to see word "SPAM" here.

We just announced a FREE and OPEN SOURCE tool WE developed. We believe it will be very useful for some people. We don't try to sell it. It's free and BSD-licensed!
Isn't it what open source about?

Moreover, it is in "[The Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11")" area open for announcements, so we behave fair.
We really surprised by your post which is pretty rude as we see it.

Who is "we"? And unless I'm confusing products, the latest version of Visual Studio is anything _but_ free. 

> Specifically, it looks like the free, Express version of the upcoming new product--widely used by many developers to create [open source ]("http://www.pcworld.com/businesscenter/article/256189/want_freedom_from_vendor_lockin_survey_says_choose_open_source.html")desktop  applications for Windows--will no longer offer support for  desktop-style applications. Rather, users of Visual Studio 11 Express  will only be able to develop [Metro]("http://www.pcworld.com/businesscenter/article/240163/are_mobilestyle_interfaces_leaving_desktop_power_users_behind.html") applications.
                       
**Metro Only**
                       

&#8220;Visual Studio 11 Express for Windows 8 provides tools for Metro style app development,&#8221; notes Microsoft's Visual Studio [website]("http://www.microsoft.com/visualstudio/11/en-us/products/express"). &#8220;To create desktop apps, you need to use Visual Studio 11 Professional, or higher.&#8221;
                       

Visual Studio 11 Professional, of course, is far from free, with its $499 price.
In other words, this "Open Source" tool can't create open source software without a check for $499 (made out to Ballmer).

---

### Post by zombifier25 on 2012-05-28
> **VTPoet said:**
> Who is "we"? And unless I'm confusing products, the latest version of Visual Studio is anything _but_ free. 

In other words, this "Open Source" tool can't create open source software without a check for $499 (made out to Ballmer).

Actually, OP was talking about HIS tool, not VS. That is, if I read his post correctly.

---

### Post by neu5eeCh on 2012-05-28
> **zombifier25 said:**
> Actually, OP was talking about HIS tool, not VS. That is, if I read his post correctly.

OK, then it seems I misunderstood.

---

### Post by bricklets on 2012-05-28
> **VTPoet said:**
> Who is "we"? And unless I'm confusing products, the latest version of Visual Studio is anything _but_ free. 

In other words, this "Open Source" tool can't create open source software without a check for $499 (made out to Ballmer).
Pay attention that VSLinux extenstion we developed supports free Visual Studio 2011 Express. It does not matter that MS removed parts of libraries, we use Visual Studio itself only, not a compiler or particular libraries.
Code is compiled with gcc located on your Linux build server.

---

### Post by Bandit on 2012-05-28
> **bricklets said:**
> Pay attention that VSLinux extenstion we developed supports free Visual Studio 2011 Express. It does not matter that MS removed parts of libraries, we use Visual Studio itself only, not a compiler or particular libraries.
Code is compiled with gcc located on your Linux build server.

Its still mind numbing why anyone would want to do this. I have used VS since VS97 and to me its horrifying.

---

### Post by bricklets on 2012-05-29
> **Bandit said:**
> Its still mind numbing why anyone would want to do this. I have used VS since VS97 and to me its horrifying.
It's OK, just a matter of personal preferences :)

---

### Post by bricklets on 2012-05-29
The VSLinux bricklet isn't intended to replace the existing Linux development tools which are good and mature enough we believe.

It's rather a way to allow Windows developers to feel comfortable while making a transition to Linux world.

The "VS for Linux" bricklet should help people used to Visual Studio (or using it due to some environment limitations) to start developing for Linux with no pain.

[LIST=1]
[*]Developers/companies used to develop on Windows making transition/porting to Linux
They're afraid of Linux, console, vi, emacs and even Eclipse (as they have to learn it) and want to minimize the learning efforts to bring a project on time.
[*]Developers/companies used to/want to use extended VS IDE abilities (Visual Assist and the like)
It's worth to say, MS Visual Studio is a good IDE. And it brings even more extended by 3rd party add-ons like Visual Assist. Indeed, other IDEs provide generally the same features set - although there are people like the way MS Visual Studio does it.
[*]Developers/companies working simultaneously on Windows and Linux projects or projects consist of both Linux and Windows parts.
As there is no choice but use the MS Visual Studio for Windows, it could be pretty convenient to unify the development environment and use it for Linux as well.
[/LIST]

Also, other IDEs implements the same "build-on-remote" functionality developers need and use. For example, Eclipse has the [Remote System Explorer]("http://tmober.blogspot.com/2006/11/remote-system-explorer-10-is-released.html") plugin does exactly the same. So we don't invent a wheel. Rather, we just bring the same functionality to another common IDE - MS Visual Studio.

Another use case is Linux code browsing and learning.

Imagine, you're developing for the Windows but have to learn the code of a Linux project.

Indeed, you have the LXR allowing you to browse through the source of vanilla Linux kernel.

But what if you have to work with a customized kernel? BusyBox? Host APD? etc.

It becomes easy with the "VS for Linux" bricklet.

Just download/clone/checkout the code to either Windows or Linux, create a project using our batch or makefile - voila!

Now you just open the generated project with MS Visual Studio and browse the sources.

---

