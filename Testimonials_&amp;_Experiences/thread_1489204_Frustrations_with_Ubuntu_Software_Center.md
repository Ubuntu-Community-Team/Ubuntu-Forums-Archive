---
title: "Frustrations with Ubuntu Software Center"
date: 2010-05-20
forum: Testimonials &amp; Experiences
---

### Post by jdege on 2010-05-20
OK, I'm playing around with a new install of Ubuntu 10.04.  I'd like to take a look at the Eclipse IDE, see if I can do some simple C++ programming, and get it to integrate with SVN.

So I bring up the Ubuntu Software Center, and type Eclipse into the search field.  I see 29 entries.  Some have nothing to do with the Eclipse IDE, but are not unexpected.  The Stellarium planetarium program, for example.  Some have nothing to do with the Eclipse IDE, and are anything but expected.  Why does prolog-el show up?

At least 20, though, clearly have something to do with the Eclipse IDE.  And there is no indication of which I need to install.  Do I want to install the "Extensible Tool Platform and Java IDE"?  The "Eclipse Integrated Development Environment"?  The "Eclipse platform without plug-ins to develop any language (data)"?

The lack of explanation on all of these is bothersome.  Now I know, using the command-line tools, I can examine the actual contents of these various install packages, view their dependencies, etc.  I can access none of these through the Ubuntu Software Center GUI.

We need to have someone who actually thinks like a user sit down in front of these applications and try to make them work.

In any case, I installed the "eclipse" package.  Then using its own install mechanisms, tried to install the Eclipse C/C++ Development tools.  The install failed.  So I went back to the Ubuntu Software Center and installed eclipse-pde, and retried the install.  Now it worked.  I'd thought that the whole point of including dependencies in repository packages was to avoid problems like this.  Still, it was working.  Or at least it installed.

Next, the subversion integration.  Some web browsing took me to the subclipse.tigris.org repository, and from there I installed the Subclipse plugin, from within Eclipse.  It doesn't work.  When I try to add an svn repository, I get a "Malformed Network Data" error.  Some browsing tells me I may need to install the JavaHL library.

So it's back to the Ubuntu Software Center looking for the JavaHL library.  I can't find it.  A search for javahl yields nothing.   In the process of looking around, I realize that  the Ubuntu Software Center provides for no search method other than the single field, single search value.  There's no way to look for packages  that include eclipse and java, for example.

All-in-all, a complicated, and bothersome experience, and I still don't have everything working that I want to have working.  (I haven't yet, for example, figured out where or how to get a correct copy of the JavaHL library.)

I understand the problems.  Why everyone involved in the chain made the choices they did.  And why these problems showed up in the cracks.  Still, if we're going to be able to meet the needs of the ordinary desktop user, we're going to need to do better.

---

### Post by MarcusW on 2010-05-21
It never occured to you to click "More info" when you wanted more info? When the C++ tools for eclipse pop up when searching, I would probably install them as well if I wanted to do C++ programming for eclipse. :P

---

### Post by jdege on 2010-05-21
> **MarcusW said:**
> It never occured to you to click "More info" when you wanted more info? When the C++ tools for eclipse pop up when searching, I would probably install them as well if I wanted to do C++ programming for eclipse. :P
Yes, it would make sense to install Ubuntu's C++ package for Eclipse.  Except that there isn't any such thing, anymore.  Eclipse contains its own plug-in installation mechanisms, and the C++ plug-in is installed with it.

As for the "More info", if you'd read more closely you'd have noticed that my complaint was that "More info" in the Ubuntu Software Center displayed only the bare info of the "more info" that was available to it.  I'd expect to be able to see the complete details of the package - authors, licenses, contents, dependencies, etc.  Instead, I just get a usually-less-than-clear descriptive blurb.

---

### Post by meho_r on 2010-05-21
Bro, you totally missed the point. All the time you're talking about "ordinary desktop user" while fiddling with tools for devs?! Don't worry, they won't have any problems.

BTW, Stellarium was enlisted probably because of "eclipse of the Sun" ;)

---

### Post by MarcusW on 2010-05-21
> **jdege said:**
> Yes, it would make sense to install Ubuntu's C++ package for Eclipse.  Except that there isn't any such thing, anymore.  Eclipse contains its own plug-in installation mechanisms, and the C++ plug-in is installed with it.

As for the "More info", if you'd read more closely you'd have noticed that my complaint was that "More info" in the Ubuntu Software Center displayed only the bare info of the "more info" that was available to it.  I'd expect to be able to see the complete details of the package - authors, licenses, contents, dependencies, etc.  Instead, I just get a usually-less-than-clear descriptive blurb.

I thought the main problem was it being unclear what to install, the "more info" clearly gives you information on the application. If you want more, and graphically, use synaptic. Well, I don't know how Eclipse work, all I know is if I was planning to program C++ with eclipse and I saw a package called "eclipse C/C++ tools" I'd install it.

---

### Post by Ms_Angel_D on 2010-05-21
jdege, thank you very much for your feedback. Since this isn't a debate/discussion section of the forums I'll be closing the thread.

Angel

---

