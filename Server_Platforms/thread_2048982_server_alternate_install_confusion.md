---
title: "server alternate install confusion"
date: 2012-08-27
forum: Server Platforms
---

### Post by bigsigh on 2012-08-27
I've installed server 12.04 a few times, boots to cli, go from there.

I installed Alternate and it booted to the Ubuntu desktop. Is this normal?

None of my 12.04 desktop installs have tasksel installed by default.

This Alternate server install has tasksel installed by default, with  print server and Ubuntu desktop, but according to tasksel basic server  is not installed.

Is this normal for Alternate?

If I run lsb_release -d, all 3 of the above installs return Ubuntu 12.04 lts, which is no help.

The fact that tasksel installed by default and is not in the default  desktop install tells me that I probably didn't get confused when  burning the iso to disc.

Confused.

---

### Post by papibe on 2012-08-27
Hi bigsigh.

A few pointers:

There is only one interface for installing the Server Edition: alternative or text mode.

There are two UIs available to install the Desktop Edition: graphics UI (normal), and alternate (text mode). Both will install the desktop edition, that is, the graphic UI.

tasksel is just a extra step on the alternative install that allow you to add extra meta packages. However, it does not change what version you are installing.

Does that helps?
Regards.

---

### Post by bigsigh on 2012-08-27
I have reviewed this again.

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

I think I get it now.

I created an Alternate install cd specifically for its raid support, but from what you've said, and rereading the above page, it's not really an Alternative Server install. Which is, apparently, why after its first boot, I was presented with the Ubuntu desktop graphical ui, instead of the server cli I expected, in fact, it appears the Alternate doesn't install server components except for print, weird.

I'll have to look at the server install iso again, I thought maybe it did support a raid install, which would mean I have no use for the Alternate install iso.

It'd be nice if there was an option to install the Ubuntu desktop without all the unneeded overhead of Libreoffice, games, etc, etc.

---

### Post by koenn on 2012-08-27
> **bigsigh said:**
> 
It'd be nice if there was an option to install the Ubuntu desktop without all the unneeded overhead of Libreoffice, games, etc, etc.

That's one of the things you can do with the Alternate CD, but you have to choose "Expert Mode" at the beginning of the install procedure (look behind the Function keys if the option's not there by default).

This gives you more control over the procedure, and allows you to skip steps such as the "install software" step, leaving you with a server-like environment where you can add stuff at will. 

The "mini iso" works in a similar way.

Or that's how it was the last time I installed Ubuntu, but I haven't tracked all versions since. I assume it still works that way.

---

