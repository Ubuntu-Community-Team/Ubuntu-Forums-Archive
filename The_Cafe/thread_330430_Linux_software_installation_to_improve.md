---
title: "Linux software installation to improve"
date: 2007-01-03
forum: The Cafe
---

### Post by Mathiasdm on 2007-01-03
First things first: I like the way Linux applications are installed (apt-get, emerge, yum and such are great tools).

However, it would be nice if things were standardized a bit more (without taking away choice, of course!).

The Free Standards Group are discussing a standard API for package management. This way, if you wish to install a package that's not in the repositories, you could still easily install it (and have it registered in your package management program).

[http://www.linux-watch.com/news/NS4586903228.html](http://www.linux-watch.com/news/NS4586903228.html)

> Jan. 02, 2007

Installing a new application on Linux can be challenging, even for experts. Now, the LSB (Linux Standard Base) project and its parent organization, the FSG (Free Standards Group), have a plan for how to make it easier for both users and developers.

Last month, key people in the Linux software packaging world and ISVs (independent software vendors) got together in Berlin, Germany to discuss the future of Linux application packaging. The group decided to create a bridge between the various software package installment programs that the Linux distributions support and what the ISVs need to support Linux.

According to Ian Murdock, CTO of the FSG and chair of the LSB, what ISVs want is "to treat Linux as a single platform, which means they want to offer a single package for Linux, much as they do for Windows."

To give the ISVs what they wanted, the Red Hat and Novell maintainers of RPM and the authors and maintainers of APT, yum, alien, and klik quickly decided that the best real-world solution was to construct "a single API (application programming interface) that could be implemented across the various package systems, because APIs make for nice evolutionary steps and can, done right, mask underlying implementation differences," according to Murdock.

The Berlin group also decided that the API should have a limited scope, since "providing an API that spans all the functionality of, say, RPM and dpkg is overwhelming to the point of being unworkable," Murdock continued. This can work, according to Murdock, because, "Fortunately, the ISVs don't really need much. At the most basic level, an installer just needs to be able to query the system to see if it's LSB compliant, and if it is, what version of the LSB it's compliant with; and it needs to be able to 'register' with the package system, so the package system knows about it, including what files it has installed."

Then, since the assumption is that the distribution will be LSB compliant, "We don't have to worry about dependencies, because everything is covered by the single LSB dependency, and dependency management is 95% of the package systems right there. We still need minimal dependency support -- components can extend the LSB, and applications can depend on those other components being installed-but we're talking on the order of a handful of components, not the tens of thousands of components typical package systems have to deal with," added Murdock.

Given the limited duration of the meeting, the group didn't come up with a complete solution. For example, the issues associated with software un-installation were barely touched, and how applications go about changing the system configuration still needs discussion. Still, it was a start. Murdock reported that "Everyone is certainly motivated: The distros get more applications, which makes the shared platform more attractive; and ISVs get lower cost, which tilts the cost vs. benefit equation in their favor, making Linux versions more economically attractive and potentially opening new markets."

To further the development and support of this API, the FSG has created a Packaging Workgroup and is relaunching the LSB packaging mailing list. There is still, Murdock concluded, "plenty to be done."


-- Steven J. Vaughan-Nichols

Edit:
Ian Murdock's opinion on package management:
[The current state](http://ianmurdock.com/?p=388)
> Software installation on Linux: Today, it sucks (part 1)

As anyone who follows my blog knows, I&#8217;m fond of linking to other sites with brief little quotes that either get me thinking or reinforce points I&#8217;m trying to make elsewhere. (Credit where credit is due: Dave Winer and Doc Searls both do this very effectively, and I&#8217;m just shamelessly copying them, down to the quoting style they typically use.)

One of the quotes I&#8217;ve had queued up for a long time is this one from Jon Udell:

    I have a confession to make. Sometimes, when I&#8217;m trying out an unfamiliar open source component, I cheat. Even if the software I&#8217;m working on will deploy to Linux, I&#8217;ll sometimes develop it on Windows first. Why? Because on Windows, an open source component is likely to come with an installer that just works.

He&#8217;s right. Unless an application is included with your Linux distribution of choice, installing that application on Linux is a nightmare compared to Windows.

Here&#8217;s an example. To install Sun&#8217;s Java Studio Creator on Windows, I just click on the .exe on Sun&#8217;s web site, which downloads the file and places it on my desktop. I double click the .exe (after, of course, checking it for viruses) and am up and running in a few minutes.

In contrast, on Linux, I click on the .bin, which downloads the file and.. up pops a text editor showing me a /bin/sh script.

Nice. Fortunately, I know what that is, so I save the script to a file on my desktop. I double click the file, and.. up pops a dialog box telling me the file isn&#8217;t executable.

Nice. Fortunately, I know what that means, so I drop into a shell and run chmod +x ./creator-2_1-linux-ml.bin. I double click the file again, and there&#8217;s a nice graphical installer now.

Finally, it looks like everything is going my way. Halfway through, though, the installation fails, telling me I need to install the RPMs for compat-libstdc++ and compat-libstdc++-dev.

Nice. Assuming I even know what an &#8220;RPM&#8221; is, I then realize: I&#8217;m running Debian, and Debian doesn&#8217;t use RPM. Maybe I know about alien, but even if I do, where do I go about getting the compat-libstdc++ and compat-libstdc++-dev RPMs?

At this point, I&#8217;ll probably hit Google&#8212;that is, if I haven&#8217;t already thrown up my hands in disgust and gone back to Windows. After a bit of Googling, I find this page, which tells me on Debian what I really need is libstdc++2.10-glibc2.2 and libstdc++2.10-dev. Of course! I should have known that. (Note: I&#8217;m being sarcastic.)

After installing those two packages, I restart the installer (which, thankfully, knows how to deal with the fact that it&#8217;s already half installed, but that won&#8217;t always be true). The installation finishes this time, and the installer kindly offers to start the program for me. However, after poking around a bit and exiting back to the desktop, I don&#8217;t see a menu entry or a desktop icon, so I&#8217;m not sure how I&#8217;m going to find it again (and I hope I don&#8217;t have to explain why cd&#8217;ing to ~/sun/Creator2_1/bin is not an answer).

Anyone who has ever installed software on Linux is familiar with this song and dance. If it&#8217;s in your distro of choice, you&#8217;re only an apt-get or a yum install away from running it. But if not, you&#8217;d better know what you&#8217;re doing, have a lot of patience, and understand how to construct effective Google search terms. (And, no, moving everything into the distribution is not a very good option. Remember that one of the key tenets of open source is decentralization, so if the only solution is to centralize everything, there&#8217;s something fundamentally wrong with this picture.)

Oh, well. At least I didn&#8217;t have to check for viruses!

Fortunately, some of the problems I experienced are bugs. The above was done on a pre-release Debian etch system over the summer, so it&#8217;s likely the problems have been fixed. I repeated the experiment on an Ubuntu edgy system, and it didn&#8217;t open the text editor, nor did it complain about an incompatible C++ environment. However, there were still no menu entries or desktop icons, and there was an additional problem too in that when I double clicked the file, it opened it in CrossOver Office, which I also have installed. Regardless, even if it works better on some distros than others, there&#8217;s still no usable solution until ISVs and end users alike can depend on things consistently working regardless of the distro being used.

Again, fortunately, we have solutions to parts of the problem already. The LSB abstracts away the differences between the runtime environments of the various distros, so the Java Studio Creator installer could have simply said &#8220;you must install the LSB environment&#8221; rather than trying to deal with the hundreds of little variations in both the environments and the package namespaces that provide them (e.g., compat-libstdc++ vs. libstdc++2.10-glibc2.2). Better yet, on distros that provide the LSB environment in their default configuration, the installer doesn&#8217;t have to do anything. And Project Portland promises to give us a consistent interface for creating menu entries, desktop icons and such things.

However, far too few applications take advantage of the LSB today (though that&#8217;s changing), and Project Portland isn&#8217;t in any of the distros yet (though we&#8217;re looking at bundling its primary deliverable, xdg-utils, with the LSB 3.2 SDK to work around that). Finally, even though the LSB provides ISVs with a consistent way to create an LSB compliant executable, there&#8217;s no consistent way to deliver an LSB compliant application that&#8217;s easy to install and that integrates well with the distribution&#8217;s package system. Yes, the LSB includes RPM today, but for a variety of reasons, ISVs don&#8217;t want to use RPM, and as already mentioned, not all distributions support RPM natively.

Fortunately, once again, this isn&#8217;t just a rant. The LSB tackled these very issues at the LSB face to face and Packaging Summit last week in Berlin, Germany, and we think we have a way forward that&#8217;s acceptable to all involved: Linux distribution vendors who already have well established package systems and systems management tools built around them; ISVs who need to support multiple platforms and so don&#8217;t want to support the Linux specific RPM format or who otherwise want more control over the installation experience; and end users who want to use the software management facilities their distributions provide, whether that&#8217;s RPM or something higher level like APT and yum. More in part 2&#8230; 


[The future...](http://ianmurdock.com/?p=391) (pretty much the same as the original article)

---

### Post by Malac on 2007-01-03
I just had to get this in.
I've used Windows since 3.0 and this has happened right through to Win98. Stuff installing then not adding shortcuts or dumping them in the wrong place. Admittedly it got better as time went by and developers got more used to where Windows puts/expects stuff and so will Linux.

Unfortunately Linux does suffer from the "too many cooks" syndrome (IMHO) each having their preferred way or logical(to them) sequence that stuff happens in or where files go(/usr/local, /usr, etc). Standardization would be good but it will almost certainly fall to the individuals/teams packaging their software to cope with making the installer changes required to make a package work with apt-, dpkg, rpm, yast.......whatever.

And I don't want files to "just execute" like on Windows that's one of the reasons Windows is so insecure.

Just my two penneth.

---

### Post by Lord Illidan on 2007-01-03
Long overdue in my opinion. Software installation is ok as far as synaptic goes, but when you venture out of the repositories, you find that programs can be either super easy to install or else completely uninstallable.

---

### Post by Mathiasdm on 2007-01-03
I'm starting to think this would provide some interesting options.

If it would allow a basic API for every package management system, perhaps it would also allow multiple package management systems on 1 computer (This is already possible, but perhaps a combined API would allow for mixed packages).

Suppose you're running Ubuntu, and install a package. It has a dependency that's not in the apt-get repositories. The installer fires up yum and looks to see if the dependency is in there somewhere.

Okay, perhaps I'm dreaming, but it would be nice :p

---

### Post by prizrak on 2007-01-03
> **Mathiasdm said:**
> I'm starting to think this would provide some interesting options.

If it would allow a basic API for every package management system, perhaps it would also allow multiple package management systems on 1 computer (This is already possible, but perhaps a combined API would allow for mixed packages).

Suppose you're running Ubuntu, and install a package. It has a dependency that's not in the apt-get repositories. The installer fires up yum and looks to see if the dependency is in there somewhere.

Okay, perhaps I'm dreaming, but it would be nice :p
It's actually not necessary. The only dependancy you are going to have is LSB version w/e.

---

### Post by jdhore on 2007-01-03
i personally think this is unnecessary because there IS a standardized way of installing stuff that's not in the repositories...there's compiling from source and that always works pretty much the same way with pretty much the same commands

---

### Post by Mathiasdm on 2007-01-03
> **jdhore said:**
> i personally think this is unnecessary because there IS a standardized way of installing stuff that's not in the repositories...there's compiling from source and that always works pretty much the same way with pretty much the same commands
-What about closed source software?
-What about newbies that have programs not in the repositories?

---

### Post by EdThaSlayer on 2007-01-03
> **jdhore said:**
> i personally think this is unnecessary because there IS a standardized way of installing stuff that's not in the repositories...there's compiling from source and that always works pretty much the same way with pretty much the same commands

To tell you the truth, compiling from source only works 10% of the time for me. Other times it either says there is no install file or it cant "make" the file.

---

### Post by qalimas on 2007-01-03
I've never really had a problem with software.. I tend to compile a bit, and generally I can nit-pick where a problem is and how to fix it.  If not, the LUG I attend can generally help me.

Checkinstall is an amazing tool, it does a wonderful job of adding compiled programs into the Aptitude database.

As for RPM distros and the such... I couldn't care less =P  Fedora Core just seems dead, I know it is most likely far from it, but you don't hear about many home users running it as a main system, more just to play with.

Software installation is very easy in Kubuntu (once you learn to type ./configure - make - checkinstall), regardless of aptitude has it or I have to compile, it always gets installed.


I don't like the idea, personally.  Most Linux users can either do it or have a friend if a program is deathly neccessary.  Dev time could better be spent on other things, IMO.

---

### Post by prizrak on 2007-01-03
> **qalimas said:**
> I've never really had a problem with software.. I tend to compile a bit, and generally I can nit-pick where a problem is and how to fix it.  If not, the LUG I attend can generally help me.

Checkinstall is an amazing tool, it does a wonderful job of adding compiled programs into the Aptitude database.

As for RPM distros and the such... I couldn't care less =P  Fedora Core just seems dead, I know it is most likely far from it, but you don't hear about many home users running it as a main system, more just to play with.

Software installation is very easy in Kubuntu (once you learn to type ./configure - make - checkinstall), regardless of aptitude has it or I have to compile, it always gets installed.


I don't like the idea, personally.  Most Linux users can either do it or have a friend if a program is deathly neccessary.  Dev time could better be spent on other things, IMO.

You are missing the point entirely. 

It's not just about increasing market share and home users. I am more than confident that there is a good enough percentage of home users who would be able to do the compile thing if needed or wouldn't need any software that is not prepackaged. 

The issue in this case is organizational use and ISV's. Compiling from source is not possible in many cases in organizational setting, imagine having 3000 desktops all needing to have a program compiled on them by the Sys Admin any time something has to be installed. Or the Sys Admin having to learn how to package software for deployment. What happens if your company (that uses say Debian) merges with another (that uses SLED). Then the entire IT staff has to be trained to deal with both, or you have to replace the OS. Worse even if you have different (but necessary) software that was designed for different distro's and you have no source for it. 

This nicely brings us to the ISV issue. When Adobe writes their PDF reader/writer for Windows they make sure it works on XP. As NT based Windows is generally backwards compatible with itself they don't even have to worry about Vista until they are ready to ship the next version. When they do the same on Linux they need to satisfy all the dependencies of different distro's. They also need to provide a way to install their software on at least 3 different platforms (Debian, SuSE, RedHat). In this case compile from source approach is plain impossible since that software is proprietary. When it comes to a smaller company that doesn't have the same capital as Adobe and much smaller number of employees they might not even want to bother with Linux since the task seems too complicated. What LSG is trying to do is build upon LSB's common baseline for different distro's and create a common API for installation. Note that they are not trying to replace Apt, Yum, RPM, DPKG or anything else, simply create a middle layer that will be able to handle working with any of those back ends through a single interface. 

The other issue they are trying to tackle is what Project Portland (I think that's the name) is trying to do, which is create a unified way of creating menu entries for any DE/WM. That's a great thing as I ran into an issue of not being able to find my programs more than once. Searching for the name in /bin doesn't always work either. For an example Beneath the Steel Sky runs through ScummVM, after installing the game I couldn't find how to start it since I was looking for an executable that looked like the name of the game.

One thing I would love to see more effort towards is driver installation. As it stands right now, anything that doesn't come as part of your distro is a pain in the butt to install. (Please don't tell me how easy it is now, it's easier than it used to be but still a huge pain in the ***, especially if you compare to Windows)

---

### Post by earobinson on 2007-01-03
this looks reall sweet

---

### Post by qalimas on 2007-01-03
My apologies, I see what you mean now.  I misunderstood the purpose of this.  I can agree that it would definitely be a bonus for the companies merging...

---

