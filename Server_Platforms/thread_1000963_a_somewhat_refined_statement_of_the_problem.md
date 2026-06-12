---
title: "a somewhat refined statement of the problem"
date: 2008-12-03
forum: Server Platforms
---

### Post by Tohasu on 2008-12-03
I've come to the conclusion that the original problem I posted earlier is still at the root (haha) of my errors as I try to build and run OpenSim. Here's a recap.

The instructions on the web site for Ubuntu install include this line

**sudo apt-get install subversion nant mono-gmcs libmono-microsoft8.0-cil \libmono-system-runtime2.0-cil libgdiplus libmono-i18n2.0-cil ruby**

I'm told every time I run it that libmono-microsoft8.0-cil is not available, and has been replaced by mono-dbg. But libmono IS available and I've got a whole page of mirror sites where it may be had. 

[B]Package libmono-microsoft8.0-cil is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
mono-dbg
E: Package libmono-microsoft8.0-cil has no installation candidate[/B]

I've tried to indicate were libmono is to the apt-get program by modifying sources.list and then running apt-get upgrade. Here's the new line in sources.list:
**deb [http://ubuntu.secs.oakland.edu/](http://ubuntu.secs.oakland.edu/) hardy main**

My build still fails with this message

[B][csc] /root/opensim/OpenSim/Region/Communications/OGS1/OGS1GridServices.cs(37,40): error CS0234: The type or namespace name `Tcp' does not exist in the namespace `System.Runtime.Remoting.Channels'. Are you missing an assembly reference?
[csc] /root/opensim/OpenSim/Region/Communications/OGS1/OGS1GridServices.cs(37,1): error CS0246: The type or namespace name `Channels.Tcp' could not be found. Are you missing a using directive or an assembly reference?
[csc] Compilation failed: 2 error(s), 0 warnings
BUILD FAILED - 0 non-fatal error(s), 2 warning(s)
[/B]

I got this software to run on my intel-based Mac laptop and I even have copies of the elusive libmono file on that machine, but I can't seem to configure apt-get on my server to do the install there. So that's my question. 

**How do I get libmono-microsoft8.0-cil installed on a VPS server running Ubuntu 8.04?**

And thanks.

Tom

---

### Post by directhex on 2008-12-03
That backslash in what you pasted....... you're not including that are you?

Also, you need universe as well as main (not all of Mono is in main)

---

### Post by Tohasu on 2008-12-03
That backslash in what you pasted....... you're not including that are you?
Also, you need universe as well as main (not all of Mono is in main)

=========================================

Yep - I was including the backslash.  So if I follow you, my line in **sources.list** should be >>

**deb [http://ubuntu.secs.oakland.edu](http://ubuntu.secs.oakland.edu) hardy main universe**

And thanks!

---

### Post by directhex on 2008-12-04
Filename: pool/universe/m/mono/libmono-microsoft8.0-cil_1.9.1+dfsg-4ubuntu2_all.deb

That should be it then.

---

