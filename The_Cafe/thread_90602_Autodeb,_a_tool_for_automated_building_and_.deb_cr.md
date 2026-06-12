---
title: "Autodeb, a tool for automated building and .deb creation from source"
date: 2005-11-15
forum: The Cafe
---

### Post by LjL on 2005-11-15
I am looking for testers for a program I'm writing, that can be found at
[https://wiki.ubuntu.com/Autodeb](https://wiki.ubuntu.com/Autodeb)

The purpose is basically to let people download a source .tar.gz and have them feeding it to autodeb, which will download the needed 'dev' dependencies, compile it, install it and create a .deb package for it, with all the runtime dependencies correctly listed.

THE SOFTWARE IS VERY EXPERIMENTAL, SO TRY IT AT YOUR OWN RISK.

If you do try it, please give me some feedback, either on the Wiki page or by email or here or something.
If you have comments that aren't strictly "known problems and bugs", as it says on the Wiki, just go ahead and add them to the page, I don't quite care right now -- just write whatever you feel like writing.

Also, I'd be glad if someone could point me to a more appropriate and specific place where I could post about this.

---

### Post by UbuWu on 2005-11-16
Sounds very good, will test it later.

---

### Post by Havoc on 2005-11-16
Since this seems pretty cool, I'll be your lab rat.I'm gonna post some feedback soon.

Good going!

---

### Post by Havoc on 2005-11-16
Well, I tested it on a couple of (small) packages, and these are my first thoughts:

1) Package name selection is quite good.It nicely detected the names of three or four packages I fed it.As I understand, it reads the string before the "-" for the name and after the "-" for the version number.The only problem with this method is that, for instance, when I write:

*havoc@Nosgoth:~$ ./autodeb.sh paco-1.10.2/*

It adds the "/" in the version name suggestion.Small problem, but worth noted.

2) While you say that it downloads the "configure" dependancies automatically, that did not happen for me.The only thing that happened was an error message saying "Check autodeb-configure-log."
The dependancies were easy to identify, in both cases.One was:

```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
```

the other was:

```

checking for library containing lua_pushboolean... no
liblua50 or liblua required!
```

Both are quite readable, at least for a human.Configure was pretty fast though.

3) More output, please.Since this tool is targeted at people that would benefit from maximum output, why not add it! The logs are a good idea though.

3) Installation worked OK.As I understand, this area is still "under construction", so I won't comment on anything more.The only "problem" I found is that makeinstall installs the program from source, and then makes a nice .deb package.Many would not know that and would instaid go straight to installing the .deb file, overwriting the already installed files, possibly creating problems.So, either stop "make install" from installing anything and instaid focus on creating a package, or have a note posted on screen staing that "The program is installed on your system.Please keep the .deb file for backup purposes" or whatever.I think the first solution is better though, because there is no way of tracking the files created by "make install", after you delete the directory used for compiling.

Hey, I'm not ranting! :p

---

### Post by lerrup on 2005-11-16
I would agree with Havoc. 

The best way would be to create the.deb package and then install with dpkg.  You then are making the best use of the Pm system.

---

### Post by Kyral on 2005-11-16
This smells like CheckInstall

---

### Post by Havoc on 2005-11-16
Well, in reality It's a script that uses some packages as "dependancies", to get the job done, and one of them is checkinstall.Quite a good idea, and with a nice gtk interface, it could be a nice solution for those too bored of manually compiling.If the whole process becomes automated enough, we could have multiple packages "made" automatically.

Anyways, I've moved away from checkinstall as a solution for organising my source-compiled software.I find [paco]("http://paco.sourceforge.net/") a much better solution, and it has a nice GTK interface to boot!

---

### Post by GeneralZod on 2005-11-16
[QUOTE=Kyral]This smells like CheckInstall[/QUOTE]

No, that really doesn't do it justice, in my opinion - as far as I am aware, checkinstall does not resolve and install dependencies for you.  

Anyway, good luck to the OP - the theory seems quite sound, so I guess we'll have to wait and see if there are any real-life gremlins to throw a spanner in the works.

---

### Post by Kyral on 2005-11-16
I apologize for my attitude towards this project. Its really a great idea for local packages, but IMO, if you intend to give the Package out, the only way is to follow the Debian New Maintainers Guide. Now if you can make this thing comply to the New Maintainers Guide and the Debian Policy, then you are a GOD

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=Kyral]Its really a great idea for local packages, but IMO, if you intend to give the Package out, the only way is to follow the Debian New Maintainers Guide. [/QUOTE]

That guide is the best way, but its a pain in the rear.

---

### Post by xequence on 2005-11-16
This is a great idea and I hope you can get it working :)

---

### Post by Kyral on 2005-11-16
You have no idea how much harder it gets. I mean if it(whatever you are packaging) uses AutoConf, then its cake, dh_make does 90% of the work for you. You just have to edit copyright, control, and changelog. Otherwise its a pain in the arse.

---

### Post by heineken on 2007-05-26
I can't connect to [http://ljl.150m.com/autodeb](http://ljl.150m.com/autodeb)  so I can't down autodeb from this.
If You have, please share for me. Reupload autodeb and share with me. Thank so much.
 I very need it.

---

