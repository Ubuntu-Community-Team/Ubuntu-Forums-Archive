---
title: "Visual Basic"
date: 2012-02-04
forum: The Cafe
---

### Post by whiterabbit23 on 2012-02-04
How can i program in visual basic on ubuntu?

---

### Post by Dragonbite on 2012-02-05
For Visual Basic (and not VB.net), look at Gambas.

For VB.net you can look at Mono (which is an open source .NET implementation).

---

### Post by 3rdalbum on 2012-02-05
> **Dragonbite said:**
> For Visual Basic (and not VB.net), look at Gambas.

For VB.net you can look at Mono (which is an open source .NET implementation).

These are similar languages, not drop-in replacements. You'll need to relearn a little here.

---

### Post by linoseros on 2012-02-05
don't use Visual Basic try Python you'll be in love with it and it's really very easy and powerfull

---

### Post by haqking on 2012-02-05
> **linoseros said:**
> don't use Visual Basic try Python you'll be in love with it and it's really very easy and powerfull

LOL yeah just change your programming language ?

Perhaps the OP likes VB, needs to use VB, required to use VB ?

Peace

---

### Post by forrestcupp on 2012-02-05
> **haqking said:**
> LOL yeah just change your programming language ?

Perhaps the OP likes VB, needs to use VB, required to use VB ?

Peace

Then the OP needs to use Windows because that's what you use if you want or need to program in VB. ;)

---

### Post by satanselbow on 2012-02-05
> **forrestcupp said:**
> Then the OP needs to use Windows because that's what you use if you want or need to program in VB. ;)

If anyone suggests W7 in Virtualbox i'll cry :popcorn:

---

### Post by haqking on 2012-02-05
> **forrestcupp said:**
> Then the OP needs to use Windows because that's what you use if you want or need to program in VB. ;)

I am aware ;-)

I just found it funny that it was recommended to change languages.

personally i use a VM

---

### Post by haqking on 2012-02-05
> **satanselbow said:**
> If anyone suggests W7 in Virtualbox i'll cry :popcorn:

any reason, whats wrong with Windows 7 in Virtual box ?

it works fine for me and others that i know

---

### Post by Supermouse on 2012-02-05
to OP:

It is easier for you to run Windows 7 on a VM and run Visual Studio inside it.

---

### Post by directhex on 2012-02-05
> **3rdalbum said:**
> These are similar languages, not drop-in replacements. You'll need to relearn a little here.

Mono has a full VB.NET compiler, which is a drop-in replacement (e.g. xbuild can compile a vbproj project from Visual Studio). However, related infrastructure may not be there, e.g. no WinForms designer

---

### Post by BrokenKingpin on 2012-02-05
I second Mono... works very well.

---

### Post by forrestcupp on 2012-02-06
> **directhex said:**
> Mono has a full VB.NET compiler, which is a drop-in replacement (e.g. xbuild can compile a vbproj project from Visual Studio). However, related infrastructure may not be there, e.g. no WinForms designer

> **BrokenKingpin said:**
> I second Mono... works very well.

Yeah, but doesn't Mono's visual form builder only work with C#? People don't use Visual Basic because they want to manually enter all of their code. They use it because it's easy and they don't *have* to write much code.

---

### Post by Dragonbite on 2012-02-06
> **forrestcupp said:**
> Yeah, but doesn't Mono's visual form builder only work with C#? People don't use Visual Basic because they want to manually enter all of their code. They use it because it's easy and they don't *have* to write much code.

Last I knew, only C# have a visual builder (Stetic?).  I've been hoping for a VB.NET, though I usually don't need it as I do a lot of my work in ASP.NET (if I do any programming at home).

There is also [_RealBasic_]("http://www.realsoftware.com/") (for VB Classic) and [_KBasic_]("http://kbasic.com/") (VB.NET) which are both pay-for programs and are "like" the official VB/VB.NET, but different.

---

### Post by directhex on 2012-02-06
> **forrestcupp said:**
> Yeah, but doesn't Mono's visual form builder only work with C#? People don't use Visual Basic because they want to manually enter all of their code. They use it because it's easy and they don't *have* to write much code.

Stetic is C# only. Nobody so far has cared enough to make it emit VB.NET. Probably wouldn't be too hard, it's really just XML input so a fancy XSLT is about as hard as it gets

---

### Post by forrestcupp on 2012-02-06
> **directhex said:**
> Stetic is C# only. Nobody so far has cared enough to make it emit VB.NET. Probably wouldn't be too hard, it's really just XML input so a fancy XSLT is about as hard as it gets

You should do it for us, then. :)

---

### Post by directhex on 2012-02-07
> **forrestcupp said:**
> You should do it for us, then. :)

My responsibility ended at producing the mono-basic package.

And for that I had to convert to Catholicism just so I could confess my sins

---

### Post by alexfish on 2012-02-07
As far as (basic) goes

also have a look at

PureBasic ,latest version (compiles standalone code)cross platform , has plenty of demo's to get started.
in linux can also implement most .so's  on the sytem , main one been libwebkitgtk , and other is database sqlite / sqlite3
also has in-line assembler, this is one powerful bit of kit for, basic orientated programmers

---

