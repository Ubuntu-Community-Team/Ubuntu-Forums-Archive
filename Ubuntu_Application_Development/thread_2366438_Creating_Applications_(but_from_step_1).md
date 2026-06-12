---
title: "Creating Applications (but from step 1)"
date: 2017-07-17
forum: Ubuntu Application Development
---

### Post by scoutchorton on 2017-07-17
Hello forums!

I am new to the whole package development, and I want to develop applications now. The idea I had is like a command line desktop manager (alternative to lightdm and the like). I haven't written code, and I want to know the whole process before I do it (I mean you don't take a road trip before you have directions on how to get there, right?). I planned to develop this in Bash and/or Python. I already set up an OpenPGP Key and SSH Key and I've signed the Ubuntu Code of Conduct.

When I actually write all the code (which this question isn't about), what do I do with it? Put it in a folder, write a Bash script to move files, put it in a tarball and publish it to a PPA? Do I have to convert it to a .deb? Do I need to add a makefile and how do I do it? Does there have to be a tarball that is converted to a .deb?

I have no idea what I'm doing. I got a start, but that's it. If you need any details about my computer, plans, profiles, command outputs, installed software, or anything else, just let me know and I will provide them. I really want to be able to start publishing packages, so I appreciate any help!

Thanks!
-scoutchorton

---

### Post by TheFu on 2017-07-17
You are months away from dealing with packaging or PPAs.  A PPA is just a personal repo that holds .debs. Don't get hung up on that aspect - especially when you don't know how to code.  You'll never get anywhere.

How do you eat an elephant?  That is the necessary attitude with what you say you want to do.  Being with step 1.  Code it.  You will make mistakes.  Sometimes throwing away a first working prototype is best.  Recode it smarter then 2nd time.  Use TDD, use fewer hard-coded values. Get strings from resource file to make multiple language support easier.  Deal with UTF8 encoding always - that's hard to add later.  Python is a much better choice than bash.  IMHO.

I wouldn't use bash for anything beyond a 50 line script. Bash is just too hard to do some things.  Try doing arrays of arrays in bash. Certainly someone will post a work-around for it, but good luck with that.  Python can and much more.  BTW, I don't normally code in Python.  

There are lots of different types of application. Depending on what you are trying to accomplish, it might be best to completely ignore packaging until the code has become popular.

There are thousands of examples for how to do all these things already.  If you find a project written in the same langauge you use, find the packaging, then find the github (or other) repo where they use VCS, you'll get a quick idea looking through their entire repo.  Be certain to look for their packaging scripts.

Makefiles aren't normally used by bash or python.  They are usually only for C or other non-Java compiled languages.  These days it is common to see cmake, not gmake used as well.  I use gmake Makefiles for my C++ code.  I've never packaged it in a .deb.  For an unpopular project, packaging is just too much trouble for very little payback, IMHO.
Start with a solid README and an INSTALL file which clearly tells people the purpose of the project, who's involved, and where you could use help.  The INSTALL file should clearly say which versions of any dependencies are needed and if a normal packaged version of any dependencies doesn't work.

A simple, 1 file, script, that you could look at is the youtube-dl script. I think it is python. They have a public git repo.

---

