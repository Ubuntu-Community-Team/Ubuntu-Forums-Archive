---
title: "Creating an XP slipstream CD"
date: 2009-02-12
forum: Windows
---

### Post by TruthOrDare on 2009-02-12
Hi,

I would like to make an XP Pro SP3 slipstream CD from my original Windows CD and the service pack I have downloaded. I have copied the CD on to the hard disk, and integrated the service pack.

However, I can't find a program that will allow me to make a bootable CD out of it.

Can anyone suggest one (for Ubuntu)?

Thank you in advance.

---

### Post by hansdown on 2009-02-12
Hi TruthOrDare.

There are some really good tutorials here.

[http://www.google.ca/search?q=Creating+an+XP+slipstream+CD&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Creating+an+XP+slipstream+CD&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by TruthOrDare on 2009-02-13
Thanks for the reply, but I have already read them. What I am after is a program in Ubuntu that will allow me to make a bootable CD.

Maybe I put this in the wrong section. :p

---

### Post by HavocXphere on 2009-02-13
Use nlite. Best way there is. Careful with all the options though...its easy to make a dud cd if you try to be too fancy. I'd suggest just doing a plain slipstream without anything else for starters.

It's got the boot info included afaik. Else use powerISO (Win program). Not sure what *nix program can do that...

(vlite for vista)

---

### Post by SunSpyda on 2009-02-15
Ah, an area I know quite a lot about (For once.). :)

Since you can't modify the kernel and such on Windows, you have to modify configuration files, the registry and installation procedure.

nLite is a useful program for removing junk from a Windows installation disk. It can also integrate hotfixes and SPs and tweak Windows to how you prefer it. For example, you can use it to apply the 'Xtheme.dll' which allows third party themes. There are many more.

Bashrat's Driver Packs are a must have for a budding XP modifier. allow you to build driver into your XP disk (Including native SATA drivers.) so Windows detects all your hardware and installs all drivers automatically.

Learn how to make batch files and you can automate loads of things, for example I got Symantec Endpoint Protection to automatically install with Windows and automatically give the serial key without asking.

You can also modify the original files on the disk to give a different outcome. For example, you can modify the ini files to automate the installation and put a new picture in System Properties and stuff.

I made a version of XP that I put on Demonoid called Core XP v2. I can't give a link, seeing as it's a piracy site.

I was very good at modding Windows and stuff, But then I learnt about *nix.... Then I hardly ever used Windows again. :)

---

