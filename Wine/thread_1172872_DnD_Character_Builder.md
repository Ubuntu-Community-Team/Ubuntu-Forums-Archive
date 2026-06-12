---
title: "DnD Character Builder"
date: 2009-05-29
forum: Wine
---

### Post by &lt;iostream&gt; on 2009-05-29
I tried installing the DnD 4e character builder, and apparently wine doesn't support it for some reason. It wont run!
Just a heads up for anyone who wants to try or a beg for help if someone knows a solution.

---

### Post by asdfoo on 2009-05-29
> **<iostream> said:**
> I tried installing the DnD 4e character builder, and apparently wine doesn't support it for some reason. It wont run!
Just a heads up for anyone who wants to try or a beg for help if someone knows a solution.

not enough information... which wine --version? what do you mean won't run? what happens?

---

### Post by &lt;iostream&gt; on 2009-05-29
I am using wine v1.1.22 and I believe it doesn't support .NET framework apps. that is the reason the developers of the Character builder say the problem is. When I try to run it, the computer freezes for a minute or two and then simply fails to start the program. No error message, nothing.

---

### Post by asdfoo on 2009-05-29
> **<iostream> said:**
> I am using wine v1.1.22 and I believe it doesn't support .NET framework apps. that is the reason the developers of the Character builder say the problem is. When I try to run it, the computer freezes for a minute or two and then simply fails to start the program. No error message, nothing.

did you install .net2 with winetricks?

at a terminal:

wget kegel.com/wine/winetricks && sh winetricks dotnet20

---

### Post by &lt;iostream&gt; on 2009-05-30
I tried doing what you suggested, but when I tried to install the file it tried to install .net framework 3.5 sp1 and failed. stopping the installation. It says that it will not work without .net framework 3.5

---

