---
title: "Unwillingness to learn or just laziness?"
date: 2005-12-26
forum: The Cafe
---

### Post by veloct on 2005-12-26
I think that the backport project is great, don't get me wrong on this. I have the  source on my source.list and I use it.

But why are some many linux users so unwilling or lazy to compile things or read a HOWTO? It's not like the HOWTO's are that hard, just plug the commands and go. Heaven forbid that somebody may actually learn something. When I first tried linux 5 years or so ago, the thing that attracted me was the ability to make the system do what I  want it to do, but mainly having the ability to change the system by compiling it myself.  Maybe now people just want a windowesque feeling from everything they do, that's really sad. Just my thought on it. Oh well.

---

### Post by sapo on 2005-12-26
Its not lazyness.

When you compile something, sometimes you need a LOT of dev libs that you will NEVER use, you just use them to compile and thats all, and uninstalling stuff is difficult too.. also you can break your system if you dont know wth are you installing.. so the backports is the SAFEST way to have new apps installed.

And sometimes you try, try and cant compile.. buf you install a lot of libs in these process.. so you system become dirty for nothing.

My firsts ubuntu installations, i broke everything compiling stuff and installing debs that werent made for ubuntu (from debian unstable, converting from rpm, etc).

I compile stuff cause sometimes i want the bleding edge version, like i m using gaim 2.0 right now, but it would be better if i didnt have to compile anything, so i could have a CLEAN system.

---

### Post by 23meg on 2005-12-26
A common reason is that many people have an elementary fear of entering commands due to the fact that they're accustomed to the GUI-only way of doing things. Whenever they see ```
$ something enclosed in code tags
```a feeling of "it's too complicated, I can't do it" strikes them, where all they have to do is copy and paste, which is in most cases easier than following "click here, click there" instructions.

---

### Post by KiwiNZ on 2005-12-26
Remember not everyone has the same ability , desire or need to learn .We must accept that the face of Linux is changing as is the user base.

It is not a bad thing .

---

### Post by aysiu on 2005-12-26
As I understand it, having something available as a package in the repositories has distinct advantages to compiling from source:

1. When it updates to a newer version, you don't have to recompile *again*
2. You don't need to worry about dependencies
3. You don't have to hunt down the .tar.gz

I don't think it's a command-line thing, as I'm not "afraid" at all to ```
sudo apt-get update
sudo apt-get install packagename
``` What's the big deal? If people want to compile, no one's stopping them.

---

### Post by veloct on 2005-12-26
[QUOTE=KiwiNZ]Remember not everyone has the same ability , desire or need to learn .We must accept that the face of Linux is changing as is the user base.

It is not a bad thing .[/QUOTE]

I can agree with that :)

---

### Post by mstlyevil on 2005-12-26
The beautiful thing about Linux is the abundant choices those who choose to run it have over Windows. If one wishes to compile and play with their OS, that is awesome. Others just want a stable desktop that works and they see no need in having the latest unstable packages. For those people the debs are just fine with them and they see no need to compile. I fall in the middle of these two. I have no problem compiling from a how to after others have done it first and tested it's stability. There is nothing wrong with either one of these points of view. Having both kind of users is what makes this community so strong.

---

### Post by KiwiNZ on 2005-12-26
[quote=mstlyevil]The beautiful thing about Linux is the abundant choices those who choose to run it have over Windows. If one wishes to compile and play with their OS, that is awesome. Others just want a stable desktop that works and they see no need in having the latest unstable packages. For those people the debs are just fine with them and they see no need to compile. I fall in the middle of these two. I have no problem compiling from a how to after others have done it first and tested it's stability. There is nothing wrong with either one of these points of view. Having both kind of users is what makes this community so strong.[/quote]

Very true

---

### Post by 23meg on 2005-12-26
The OP isn't talking just about compiling; neither am I.

[QUOTE=veloct]But why are some many linux users so unwilling or lazy to compile things or read a HOWTO? [/QUOTE]

---

### Post by prizrak on 2005-12-26
Alot of people come here for the wrong reasons really. Compiling is not a requisite in the Ubuntu world, there is only one program I had to compile and only because there is no binary for it yet (of any version). There are plenty of people who hear "Linux is a better OS than Windows and doesn't get viruses/malware/spyware". When they run it they don't realize that Linux is not Windows and that in order to use it you WILL have to learn SOME things so they get dissapointed when they realise you have to open some Synaptic thing and read the description of a program and then there is no automatic shortcut on your desktop or even C:/Program Files to look through stuff. To make matters worse since there is the 6 month release cycle you are more or less stuck with w/e comes with your CD for 6 months. So all the people who want something newer (FF 1.5 for instance) and can't get it in the repos get unhappy. When it is explained to them that the software only makes to the repos when it is sufficiently tested to make sure it doesn't break your system they go "Pfft, on Windows a new program doesn't break my OS, Linux must suck" When said that they can compile things using How-To's on the forum if they in fact want the said program you  see the "Well how come I can just click on it in Windows and it works, Linux must suck" attitude. Those people do tend to be the minority but they the ones you hear, you don't hear the open minded ones because we tend to search through the forum, follow the how-to, happily use the software or break the system and redo it. Those of us who feel comfortable enough give advice to noobies but we are not really vocal :)

---

### Post by ardchoille on 2005-12-26
[QUOTE=veloct]I think that the backport project is great, don't get me wrong on this. I have the  source on my source.list and I use it.

But why are some many linux users so unwilling or lazy to compile things or read a HOWTO? It's not like the HOWTO's are that hard, just plug the commands and go. Heaven forbid that somebody may actually learn something. When I first tried linux 5 years or so ago, the thing that attracted me was the ability to make the system do what I  want it to do, but mainly having the ability to change the system by compiling it myself.  Maybe now people just want a windowesque feeling from everything they do, that's really sad. Just my thought on it. Oh well.[/QUOTE]
Why should I go thru the time and trouble to compile something that is in backports? Doing so would be a waste of my resources, would it not?

---

### Post by xequence on 2005-12-26
For me, it is so much simpler and more conveinent to just do "sudo apt-get install _______" then having to get all the gcc compiler versions right, and doing make install or checkinstall, or make make install, and installing X sources/binaries/whatever. Its just so complicated and annoying. There are 1000 different ways to compile things, and 1000 different things you need to have working perfectly.

---

