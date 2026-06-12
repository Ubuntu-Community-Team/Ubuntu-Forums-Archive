---
title: "Nicotine+"
date: 2008-12-04
forum: The Cafe
---

### Post by sw1995 on 2008-12-04
Allo,

Is anybody else having trouble running Nicotine+ in Intrepid? When I open the program it just stalls and I have to force quit. This is frustrating because I NEEEEEED this program:)

Any help/suggestions would be greatly appreciated, I am not having much luck researching this on my own.

-S

---

### Post by kk0sse54 on 2008-12-04
Don't install the one from the repos instead download the svn version of the site or the alpha of 1.2.10 ( I suggest the svn since it has some bug fixes not in the alpha) as it's much more up to date and has a lot more features (private rooms as one) and might help solve your problem.
[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

---

### Post by sw1995 on 2008-12-04
Thanks! I just tried both of the versions you mentioned and when I still open Nicotine it just hangs. The window is there, but the text disappears and I get nowhere. Any other suggestions?

---

### Post by OffHand on 2008-12-05
> **sw1995 said:**
> Thanks! I just tried both of the versions you mentioned and when I still open Nicotine it just hangs. The window is there, but the text disappears and I get nowhere. Any other suggestions?

Can you start Nicotine+ from the terminal and post the traceback please.

And please use the svn version as it's the most current.

---

### Post by sw1995 on 2008-12-07
Hi there,

Thanks for you help - here is what I get:

stev@queequeg:~$ cd nicotine+/
stev@queequeg:~/nicotine+$ ./nicotine
Your X can handle RGBA, but your window manager cannot. Not enabling transparancy.

---

### Post by OffHand on 2008-12-07
> **sw1995 said:**
> Hi there,

Thanks for you help - here is what I get:

stev@queequeg:~$ cd nicotine+/
stev@queequeg:~/nicotine+$ ./nicotine
Your X can handle RGBA, but your window manager cannot. Not enabling transparancy.

Update to the latest svn please. This should be fixed now. 
```
svn up
```

Let me know how that works out. Should be [fixed]("http://www.nicotine-plus.org/changeset/779").

---

### Post by pt123 on 2008-12-07
How long has Nicotine+ 1.2.10alpha  been in alpha .9 was released in Sept. 07

---

### Post by OffHand on 2008-12-08
> **pt123 said:**
> How long has Nicotine+ 1.2.10alpha  been in alpha .9 was released in Sept. 07

Dunno... I always use svn and I can recommend anyone using that as well. It is the most current version and works perfectly fine.

[http://www.nicotine-plus.org/wiki/NicotineFromSubversion](http://www.nicotine-plus.org/wiki/NicotineFromSubversion)

---

### Post by pt123 on 2008-12-10
anyone chance of them releasing a DEB?

---

### Post by OffHand on 2008-12-10
> **pt123 said:**
> anyone chance of them releasing a DEB?

Possibly but no ETA. Running N+ from source is really [easy]("http://www.nicotine-plus.org/wiki/NicotineFromSubversion") though

I have attached a script to launch N+. Open the script in a text editor and put in the right paths (you will know what I mean if you see the script, if not ask). You can make a new menu item with Main Menu under System > Preferences. Point it to the script. The script will update N+ every time you launch it.

p.s. make the script executable (right click > properties > permissions)

---

### Post by pt123 on 2008-12-15
> **OffHand said:**
> Possibly but no ETA. Running N+ from source is really [easy]("http://www.nicotine-plus.org/wiki/NicotineFromSubversion") though
p.s. make the script executable (right click > properties > permissions)
Thanks but I prefer, DEBS much easier to uninstall them and hence maintain the system.

---

### Post by kk0sse54 on 2008-12-15
> **pt123 said:**
> Thanks but I prefer, DEBS much easier to uninstall them and hence maintain the system.

What so hard about just deleting the folder when you no longer want the program :confused: or in order to update just 
```
cd nicotine+ <or whever you stored the folder>
svn up
```

It's not like you have to compile the program, just download the source and run the executable.

---

### Post by OffHand on 2008-12-15
> **C!oud said:**
> What so hard about just deleting the folder when you no longer want the program :confused: or in order to update just 
```
cd nicotine+ <or whever you stored the folder>
svn up
```

It's not like you have to compile the program, just download the source and run the executable.

Exactly

---

### Post by pt123 on 2008-12-17
> **C!oud said:**
> What so hard about just deleting the folder when you no longer want the program It's not like you have to compile the program, just download the source and run the executable.

You still have to open the script and look into where it's going dump itself. Then later on you when you need uninstall it you have to remember the location. 
Absolutely inconvenient esp. when Ubuntu offers a unified package system. 

One of the reasons I swapped from Windows, as OS where programs defecate  anywhere they feel like.

---

### Post by OffHand on 2008-12-17
> **pt123 said:**
> You still have to open the script and look into where it's going dump itself. Then later on you when you need uninstall it you have to remember the location. 
Absolutely inconvenient esp. when Ubuntu offers a unified package system. 

One of the reasons I swapped from Windows, as OS where programs defecate  anywhere they feel like.

Whatever floats your boat mate but then you will have to wait.

---

