---
title: "Making Ubuntu even OS(e)X:ier..."
date: 2011-10-27
forum: Ubuntu Dev Link Forum
---

### Post by VirtualOzelot on 2011-10-27
I wanted to try and see if I could implement one of my favourite OS X features in Ubuntu - the easy click and drag install of apps. I'm familiar with several of the different standards for standalone binary distribution, and tools such as autopackage and klick (is anyone using them anymore?). For this project however, I wanted to make use of a package format that is already out there and being used by millions (?) of users - the .deb package.

Simply put, my program (it's really more of a script at this stage) converts the .deb file into a mountable archive containing another, executable application archive. It does this on the fly when being fed a .deb file, as seen in the demonstration below:

[http://www.youtube.com/watch?v=3bHWtnF6hSw]("http://www.youtube.com/watch?v=3bHWtnF6hSw")

This is ideal for simple desktop applications, but not so great for system libraries, so the script employs a simple method for checking whether or or not the .deb is a desktop program or something else. If it's something else, it is automatically passed on to Ubuntu Software Center. One good thing about this approach is that you don't have to be root in order to download and run simple desktop applications. Also, you don't have to make changes to the system in order to try a piece of software.

Right now it's working with some simple applications like games and straightforward GTK apps. Dependency handling isn't quite there yet, so for testing purposes I have to install all requirements before running the application. I'm using a pretty crude chroot jail, embedding the program files in symbolic links pointing to the "real world" of the installed system. This is not a good way of doing things since many programs can't seem to handle symbolic links on that level. There is also the downside of making your X server slightly more vulnerable by accepting remote connections (a feature that might not be around for Wayland, from what I understand).

This is obviously not a very linuxy way of doing things, and so far quite unsafe, so keep in mind it's just a hobby project. My only aim is to see what I can manage in terms of programming for the Ubuntu platform.

Please give me your spontaneous thoughts and reactions.

:)

---

### Post by gsmanners on 2011-10-27
You obviously check to make sure the user is at least a member of admin, right?

---

### Post by VirtualOzelot on 2011-10-28
> **gsmanners said:**
> You obviously check to make sure the user is at least a member of admin, right?

Nope. Why - is that bad? :)

Just to be clear, everything that happens, happens in the /tmp folder. Nothing is ever really installed and no changes are made to system files. The target application runs with user-level authority.

---

### Post by gsmanners on 2011-10-28
I guess it could work, as long as you don't have anything go horribly wrong on your end. :D

---

