---
title: "Cannot Compile UnrealIRCD"
date: 2009-04-09
forum: Server Platforms
---

### Post by Zaraphrax on 2009-04-09
Hey all,

I'm trying to install Unreal 3.2.8 on Hardy server (8.0.4.2). I've downloaded and un-compressed the source, ran a ./Config. That's all good. The guide I'm using then said to type "make" and let it compile.

But, I get this:

```

ashton@battletoad:~/Unreal3.2$  make
make: ***No targets specified and no makefile found. Stop

```

I've already installed the package "build-essential" but that didn't fix my problem. Any help would be appreciated. Thanks.

---

### Post by windependence on 2009-04-10
You probably weren't in the directory where the makefile is stored. The command for config is ./config, not ./Config. There IS a difference. Also, you need to run ./make, not just make if you are already in the directory where the makefile is located. You can do a pwd to see what directory you are currently in. Do an ls -a to make sure the makefile is in the directory.

You may find that you will need some other developement packages. I would advise installing the complete development files if you are going to compile your own stuff.

-Tim

---

