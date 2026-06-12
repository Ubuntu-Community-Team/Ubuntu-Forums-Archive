---
title: "Jackal: tar.gz GUI installer for Ubuntu"
date: 2008-01-06
forum: Ubuntu Brainstorm
---

### Post by Mazza558 on 2008-01-06
I know there's ideas similar to this floating around, but here's my interpretation...

---

### Post by smartboyathome on 2008-01-06
Like I said before, the hard part about compiling a program on Linux is dependancies, and unfortunately it would be a pain in the butt to try to write a program which interprets those dependancies and installs them for you, since the dependancies can have many packaging names.

---

### Post by Mazza558 on 2008-01-06
> **smartboyathome said:**
> Like I said before, the hard part about compiling a program on Linux is dependancies, and unfortunately it would be a pain in the butt to try to write a program which interprets those dependancies and installs them for you, since the dependancies can have many packaging names.

But usually for me it's only 3 terminal commands (configure, make, sudo make install) - no dependencies here. Surely that's not hard to implement? Thinking about it, I've NEVER had to do anything more than those 3 steps when compiling. Perhaps if it checked for dependencies and if you didn't have them, it refused to install (and I've NEVER had any warnings about missing dependencies on Ubuntu)?

---

### Post by smartboyathome on 2008-01-06
I've compiled tons of programs on ubuntu, and a lot of them I had to install dependancies. I guess it depends on the program you are installing, but with this, you would still run the risk of not all dependancies, and I wouldn't include something that only installed some apps.

---

### Post by lexen on 2008-01-07
I would bend over backwards to get this in motion.  I would love to install programs from source, but I have never been able to do it.  I know it is my fault for not knowing how to do it, but I think there are others like me that can't figure it out.

I don't think the dependencies will be a problem.  With GDebi, if there is a dependency missing, it will download it and install it along with the .deb file.  If you just altered GDebi so it could compile source, you wouldn't run into those problems, unless the dependency wasn't in your repositories.

Again, I would LOVE this.  I really hope someone picks this up.

---

### Post by [h2o] on 2008-01-07
The problem liesnot with downloading and installing the dependancies, but in programatically finding out what they are.
If there was a way to decide exactly which libs and what version a program needs by looking at its source code (without requiring them to use a specific markup) then this would indeed be useful.

---

### Post by lexen on 2008-01-07
How does synaptic know what dependencies to download?  Is it in the file or does synaptic need a database?

---

### Post by smartboyathome on 2008-01-07
> **lexen said:**
> How does synaptic know what dependencies to download?  Is it in the file or does synaptic need a database?

The dependancies are in the precompiled binary packages that synaptic distributes.

---

### Post by nhandler on 2008-01-07
Part of the process of packaging the programs into debs is creating a control file. The control file among other things lists all of the required, suggested, and recommended packages. This is how Synaptic, Apt, and all other package managers know what dependencies are needed. If you have to compile a .tar.gz, it most likely means that it has not been packaged yet. Therefore, there is no control file listing the dependencies. This is why it would be difficult to integrate with something like Synaptic or gdebi.

Now, here is my own comment. It is quite trivial to get a list of all files in a .tar.gz. What if we were to search the archive for scripts written in various languages. We could use either the file extension or the mime-type to identify the language used. We could then parse the various scripts to identify additional libraries/modules that are used (We probably couldn't catch all of them, but we should be able to find some of them, especially the more common ones). From there, we could check to see if they are installed on the computer. If not, we check if they are included in any package in the repos. If they are, we install the package. If not, we abort and alert the user of the missing library/module/etc. If they have all of the needed libraries, we could extract the archive, and do the ./configure, make, sudo make install. But we need to be sure to offer the advanced users a way to pass additional parameters to these commands. Could someone explain to me if this is possible. I know it would be a difficult thing to do (especially finding ways to identify libs and other dependencies used by scripts), but is it possible?

We could also allow users to specify dependencies of the script in a specific file located in the archive. This would allow the package manager to read this file like it reads a control file in a .deb.

---

### Post by smartboyathome on 2008-01-08
Your first idea could be easier to do (we could have it run ./configure, and if it has an error and aborts, it tells the error output). The second would be harder for the user, since they would have to look up all the dependancies themselves.

---

### Post by pronik on 2008-01-08
It's not always "./configure && make && sudo make install". More often than not it's "./setup.py build && sudo ./setup.py install" or similar now. There are many more build systems than just autotools on the market, so it's rather difficult to implement.

---

### Post by smartboyathome on 2008-01-08
I have never come across a program that does that, but ok. There is sometimes a ./autogen.sh file, too.

---

### Post by nhandler on 2008-01-08
> **smartboyathome said:**
> Your first idea could be easier to do (we could have it run ./configure, and if it has an error and aborts, it tells the error output). The second would be harder for the user, since they would have to look up all the dependancies themselves.

By "user" in regards to my second idea, I was referring to the developer. Most developers will know the dependencies of their own program.

---

### Post by FuturePilot on 2008-01-08
It looks like a nice idea, but when you really look into it, I don't think it would ever work. As others have mentioned one of the things is the dependencies. Usually when you compile something you need various -dev packages. I'm not sure how installing those would be implemented especially if you have no idea which ones are needed. The other thing is the number of compile options. One of the biggest reasons someone might compile a program is to enable some extra feature that's not in the Ubuntu packages. The problem with a point and click approach to compiling is there's really no way to know what the options are for any random application and to enable them at compilation.

---

### Post by Ub1476 on 2008-01-09
I just don't understand why devs wont make a .deb file? Is there any reason (except for being open-source), or is it just lazines?

---

### Post by smartboyathome on 2008-01-09
> **Ub1476 said:**
> I just don't understand why devs wont make a .deb file? Is there any reason (except for being open-source), or is it just lazines?

Because some don't have time to make a deb file.

---

