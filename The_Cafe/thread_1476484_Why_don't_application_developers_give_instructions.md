---
title: "Why don't application developers give instructions?"
date: 2010-05-07
forum: The Cafe
---

### Post by rfry11 on 2010-05-07
I've noticed that in a lot of programs that are packaged and distributed in ways that aren't .DEB or .RPM files, no instructions are given. I tend to try a bit of sh, then ./, maybe make and then make file if I can remember it, before I finally Google it for someone who's also wondered how to install the program. 
Now, it's not like any of these installation methods are long or complicated, and they all basically work the same way on every Linux distro, so I'm sitting her wondering, "Why didn't they just put the instructions in the readme?" 

If Windows developers can have the patience to write, "Double click on exe. Click next. Click next. Click finish", can't Linux devs have the patience to tell you to key in a few lines in the terminal?

Sorry if this is in the wrong place.

---

### Post by ubunterooster on 2010-05-07
It belongs in the "Community Cafe" I'll ask a mod to move it. :D


I "Yahoo it" before anything else because default instructions stink many times

---

### Post by cariboo on 2010-05-07
This isn't a support question, moved to the Cafe.

---

### Post by rfry11 on 2010-05-07
Thanks for the move, sorry I placed this in the wrong board.

> **ubunterooster said:**
> I "Yahoo it" before anything else because default instructions stink many times


But why exactly do they stink? I could understand that because of the countless setups thousands of possible errors could pop up, but it seems that many do not even attempt to include default instructions. One example I found just today, I bought the Humble Indie pack from Wolfire, and for all but World of Goo I needed to Google for some simple commands. Not even a commercial game can include instructions?

---

### Post by ubunterooster on 2010-05-07
They spend all of the time working until..."it works! Let's make a sequel now", not thinking of the documentation.

---

### Post by Diabolis on 2010-05-08
It is boring. Also, many assume that if you use Linux, you probably know how to deal with the software even if instructions are not given. Of course, that'll change with time, hopefully.

---

### Post by lykwydchykyn on 2010-05-08
I assume we're talking about sourcecode here; it's conventional to have a document called INSTALL in the root directory of the code with basic compiling instructions, dependencies, etc.  Sometimes it's also in README.

Since most free software devs are using automake or cmake or something like that, and since most free software isn't going to be compiled by the end user but packaged by a distro maintainer who knows what he/she is doing, the instructions are usually boilerplate and non-specific.

Of course, it's true that writing this kind of documentation (and updating it when things change) is kind of a drag, so it doesn't always get written.

---

### Post by PurposeOfReason on 2010-05-08
Because it's either:
./configure
make
make install (clean)

OR

[check extension] ./setup (install)

If you find a program like that, let me know.

---

### Post by jkxx on 2010-05-08
As ubunterooster put it, the answer is because documenting the how-to process stinks. And part of the reason is that it really isn't done the same way on every Linux distro, much less across different ones. There is no guarantee that any base components (other than perhaps the kernel) will be installed although there are dozens available usually, some of which are inevitably installed on the system in question.

So on Linux, reconciling what is available and how to make do with it is a more difficult task than on Windows where the system is guaranteed to have certain DLLs and capabilities included for sure. So as a workaround different distros have created different packaging systems (Debian's DEB being an example you gave).

That said it isn't *that* difficult to compile a program, the "standard" set of commands is


extract .tar.gz or .tar.bz2 file
cd content_of_tar_gz_file

```

./configure
make
sudo make install

```

though if something needed to compile is missing, you'll get errors and this is where a lot of people run into a brick wall. If you get stuck in that situation, just post exactly what you were trying to do and what went wrong. Chances are someone will know how to install said app and will help you out with it, people around here are nice like that :)

---

### Post by ubunterooster on 2010-05-08
see Kdirstat and compare it to the Windows' windirstat. "What is green?" WinDirStat tells you right away on the screen what green is. Kdirstat? Not at all; you have to figure it out and remember for yourself

---

### Post by Ebere on 2010-05-08
Aside from installation, they could sometimes do a bit of explaining about the program itself, as well.

I lost years of backed up data when I used WinPP to clone a laptop to my backup drive.

There was absolutely nothing, anywhere that explained that when you make a clone, it will wipe out the destination drive.

---

### Post by aysiu on 2010-05-08
My understanding is that since the primary way for Windows users to install programs is to go to the program's website and download an installer file that that's how Windows programs come--as installer files.

And since the primary way for Linux users to install programs is through software repositories that the projects' websites are not mainly for users but for developers to package the source code into the .deb or .rpm packages for software repositories.

---

### Post by rfry11 on 2010-05-08
Hmmm, a lot of interesting replies to this.

I wasn't just narrowing this down to compiling from source though, a lot of this was a bit of a rant about how I was handed a .DEB file, a .SH file, a .BIN file, an uncompiled archive, and what I think is a compiled archive from the Humble Indie bundle without any documentation about how to install them.

---

### Post by aysiu on 2010-05-08
> **rfry11 said:**
> Hmmm, a lot of interesting replies to this.

I wasn't just narrowing this down to compiling from source though, a lot of this was a bit of a rant about how I was handed a .DEB file, a .SH file, a .BIN file, an uncompiled archive, and what I think is a compiled archive from the Humble Indie bundle without any documentation about how to install them.
My point is that you shouldn't be handed anything.

You should be installing applications through the Ubuntu Software Center.

A manual download of a .deb file is if it's not in the repositories, in which case **you double-click the .deb file to install it**.

.sh, .bin, and .tar.gz are not standard installation techniques for Ubuntu users. **They are last resorts**.

---

### Post by madjr on 2010-05-08
> **rfry11 said:**
> Hmmm, a lot of interesting replies to this.

I wasn't just narrowing this down to compiling from source though, a lot of this was a bit of a rant about how I was handed a .DEB file, a .SH file, a .BIN file, an uncompiled archive, and what I think is a compiled archive from the Humble Indie bundle without any documentation about how to install them.

we should really talk this out with the Humble indie developers

now that they raised enough funds, they should be able to at get a person to do this work.

linux users like to learn, but most ubuntu users come from windows and expect an similar method of installation (.debs)

they should do like World of goo (a deb and a rpm)

or at least include the instructions in the download site like you mentioned.

---

### Post by ubunterooster on 2010-05-08
I think the real problem being mentioned was lack of instructions in the operation of programs

---

### Post by phrostbyte on 2010-05-08
I have yet to encounter a source binary that doesn't use some kind of Makefile to build itself. As other people said, compilation of applications is pretty standard regardless of what it is, it just that GNU make doesn't do dependency resolution which is the problem. You often don't know you are missing a dependency till halfway through the build (ie, if they aren't using Autotools).

---

### Post by del_diablo on 2010-05-08
> they should do like World of goo (a deb and a rpm)

Diety forbid, what if i am running something other than Fedora and Ubuntu/Debian?

---

### Post by aysiu on 2010-05-08
> **del_diablo said:**
> Diety forbid, what if i am running something other than Fedora and Ubuntu/Debian?
Deity?

Mandriva and PCLinuxOS also use .rpm. Mepis and Xandros also use .deb.

If you use Arch Linux, Gentoo, or Slackware, you should be able to figure stuff out on your own. Otherwise, stick with the distros that use .rpm and .deb.

---

### Post by swoll1980 on 2010-05-08
> **del_diablo said:**
> Diety forbid, what if i am running something other than Fedora and Ubuntu/Debian?

Do you expect people to package executables for every Linux package manager? Seems a little unreasonable. I can't think of any distro, that has a half way decent user base, that doesn't use this format. If you're using a distro like Arch, why complain about it now? You knew what you were getting yourself into.

---

### Post by aysiu on 2010-05-08
swoll1980 said it much better than I could.

---

### Post by del_diablo on 2010-05-10
swoll1980: What is wrong with normal binary packages?

---

