---
title: "C++ Development Environment and Tool Chain"
date: 2011-05-30
forum: Ubuntu Dev Link Forum
---

### Post by stefanadelbert on 2011-05-30
At work we're on Windows (Visual Studio - say what you like, it's an awesome IDE), but we're considering porting to Linux. I would like to set up a proof of concept Linux development environment.

Our C++ codebase is taking time (20 min) to clean build on powerful machines, so distributed compilation and incremental linking are important. We make fairly heavy use of templates which adds quite dramatically to the compilation times.

Our code is already in bzr, so that will stay as is.

This is how I'm thinking so far:

Eclipse CDT
build-essential (g++)
binutils-gold

distcc
ccache

Anyone got any recommendations? Anything obvious I'm missing out?

---

### Post by rpmp on 2011-05-30
you should try Code:blocks IDE.

---

### Post by tdrusk on 2011-05-30
This will not work(to my knowledge) as Visual Studio has a different compiler than Eclipse(g++). This will cause errors to arise when compiling your current programs and when executing your new programs in Visual Studio. I know because I have failed a few assignments due to this.

---

### Post by Npl on 2011-05-30
as you say, VS is a powerful IDE, and Id go so far to say that its still unmatched by OS IDEs.
Also I dont know what exactly do you want to archive? If you simply want a port to Linux then you can still keep developing under VS and just use an additional buildsystem/makefile for Linux. This would be the most flexible as Linux practically revolves around the gnu tools, its a bad idea to depend on IDEs.

I also heard good things about CMake, which supposedly can spit out VS and gnu-make projects/makefiles (amongst tons of other). This would likely be the most flexible approach.

And just to add for Linux IDEs, Code::Blocks is the best Ive tried so far for C/C++ development. Eclipse CDT was rather bad when I tried it, but I havent touched it in years.

---

### Post by stefanadelbert on 2011-05-30
Porting our existing code is a separate issue. Our codebase will need some work to get it compiling under Linux, but we've kept it mostly cross-platform (STL, Boost, Qt). What I'm trying to achieve is a working proof-of-concept of a feasible (possibly superior to VS on Windows) Linux-based development environment (IDE, tool chain, continuous build, packaging and deployment, etc.).

I've had a quick play with CMake and qmake before. Eclipse CDT generates makefiles probably using GNU make behind the scenes, but also has a CMake plugin. I don't mind which one is used. We would probably use Managed C++ projects anyway. I would prefer not to be monkeying with makefiles myself. CMake does look interesting and I should probably give it another look.

> you should try Code:blocks IDE.

> And just to add for Linux IDEs, Code::Blocks is the best Ive tried so far for C/C++ development.

I know about Code::Blocks, but why do you believe that it's the best? I've had it installed before, but wasn't crazy about it. I found the debugging difficult - simple features that VS has were lacking in Code::Blocks. I don't know that Eclipse has those features either. VS is AWESOME for debugging, I know that, and may just be superior.

Anyway, it's not so much about the IDE in this case as we could continue to use VS to edit and debug (on Windows) and then compile and run on Linux, but that would require that the codebase be absolutely cross-platform. It would be best to have everything Linux-based, including development.

Any thoughts on distcc, ccache, yasm? What about in-house application deployment (private apt repository)?

---

### Post by Npl on 2011-05-30
> **stefanadelbert said:**
> I know about Code::Blocks, but why do you believe that it's the best? I've had it installed before, but wasn't crazy about it. I found the debugging difficult - simple features that VS has were lacking in Code::Blocks. I don't know that Eclipse has those features either. VS is AWESOME for debugging, I know that, and may just be superior.Read my whole post, dont just quote me out of context, its the best C++ IDE for **Linux** I have tried. I dont know any IDE that comes close to VS.
> **stefanadelbert said:**
> Anyway, it's not so much about the IDE in this case as we could continue to use VS to edit and debug (on Windows) and then compile and run on Linux, but that would require that the codebase be absolutely cross-platform. It would be best to have everything Linux-based, including development.I dunno why it would be best to develop on Linux if you dont even know which tools to use :p

---

### Post by stefanadelbert on 2011-05-31
The whole point of this post is to find out from developers which tools they believe are best for developing C++ applications on Linux and why. The purpose is so that I can make some informed decisions when choosing the components for a Linux development environment. Of course I know which tool chain and ancillary tools I _could_ use, but I would like some feedback on which tools developers are using so that I can better inform myself.

> Read my whole post, dont just quote me out of context, its the best C++ IDE for Linux I have tried. I dont know any IDE that comes close to VS.

I had hoped that "for Linux" would be implicit when I said "I know about Code::Blocks, but why do you believe that it's the best?" given that we're talking about a development environment for Linux here. So allow me to rephrase:

Why do you believe that Code::Blocks is the best C++ IDE for Linux? What are its best features in your opinion?

I'm still more interested in the tool chain than I am in choosing an IDE though. As pointed out, it's not a good idea to be bound to an IDE so I would prefer the environment to be IDE agnostic.

To stay truly IDE agnostic I suppose it would be a good idea to steer clear of "managed" projects that automatically create/update makefiles in favouring of modifying them manually. I would prefer to spend my time writing code though rather than tinkering with makefiles. Is there a halfway house here? Or does it need to be one or the other? Maybe CMake is a halfway house in that CMakeLists.txt is a go-between the project and the makefile. You could manually modify CMakeLists.txt files or you could let an IDE do it.

So, any comments on the following (for Linux):

[LIST]
[*]CMake vs. other makefile generators
[*]gold and incremental linking in general
[*]distcc
[*]C++ template compilation (any ways to speed it up)
[*]ccache
[*]yasm
[/LIST]

---

### Post by Npl on 2011-05-31
> **stefanadelbert said:**
> I had hoped that "for Linux" would be implicit when I said "I know about Code::Blocks, but why do you believe that it's the best?" given that we're talking about a development environment for Linux here.Well you then continued to say that VS has more features and better debugging, sounded like you compared it directly to VS and not alternatives running on Linux
> **stefanadelbert said:**
> So allow me to rephrase:
Why do you believe that Code::Blocks is the best C++ IDE for Linux? What are its best features in your opinion?Its not about having the most features, I think Eclipse would win that. But the features that are in Code::Blocks are just working well, wheres the same cant be said for other IDEs. The most important feature for me is the ability to autocomplete and detect referenced classes/variables (able to show its members and jump to the definition/declaration).

---

