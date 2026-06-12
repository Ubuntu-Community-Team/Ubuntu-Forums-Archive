---
title: "What is mono?"
date: 2007-02-08
forum: Utah Team - US
---

### Post by thenetduck on 2007-02-08
Hi, 
 I was wondering if anyone could shed some light about what Mono is? Im talking about the patent the Novell and Microsoft worked out? Thanks, 
 The Net Duck

---

### Post by qamelian on 2007-02-08
> **thenetduck said:**
> Hi, 
 I was wondering if anyone could shed some light about what Mono is? Im talking about the patent the Novell and Microsoft worked out? Thanks, 
 The Net Duck

Mono is an open-source implementation of Microsoft's .NET development platform. It is compatible with most of .NET 1.0 and 1.1, so many .NET (things coded in C#, etc), will run on Mono with little or no effort.

---

### Post by snowpalmer on 2007-02-19
> **thenetduck said:**
> Hi, 
 I was wondering if anyone could shed some light about what Mono is? Im talking about the patent the Novell and Microsoft worked out? Thanks, 
 The Net Duck

The patent they worked out has nothing to do with Mono does it?  I thought Microsoft's language on the whole matter was simply "Peace of mind" but never gave specifics as to what they felt was being violated.  I seem to remember someone on here sending a letter to microsoft and they still couldn't list what was violated.

---

### Post by atoponce on 2007-03-09
No. the patent has nothing to do with mono at all.  Not that I have read at any event.

Mono is on open implementation of Microsoft's .NET framework, including compilers for C#.NET and VB.NET.  It uses the same development libraries on Linux that exist on Windows.  This means that if you code and compiled some mono code on Linux, it will compile on Windows as well.  It is cool stuff.

Check out [http://www.mono-project.com](http://www.mono-project.com)

---

### Post by bretticus on 2007-04-02
> **atoponce said:**
> No. the patent has nothing to do with mono at all.  Not that I have read at any event.

Mono is on open implementation of Microsoft's .NET framework, including compilers for C#.NET and VB.NET.  It uses the same development libraries on Linux that exist on Windows.  This means that if you code and compiled some mono code on Linux, it will compile on Windows as well.  It is cool stuff.

Check out [http://www.mono-project.com](http://www.mono-project.com)

Well...sort of. If you are building a window application for Gnome, for example, you can't just pull source code from Visual Studio into Monodevelop and build. I understand that the mono project is working on System.Windows.Forms for use with X11 (anybody tried this?) However, I had to use Glade to create my IU forms (for  a silly woot.com application for Gnome) and access the Gtk# repository to code the UI interface.  Now, Gtk# is available for Windows, and you can, apparently,  build windows forms based on GTK (for download with the many tools that come for installing gimp on Windows no doubt.) Having coded in .NET Visual Studio, building an app in mono was a challenging transition (not quite as easy as dropping csharp files from Monodevelop into Visual Studio and building.) However, it appears that's where the mono project is heading (very cool.)

---

