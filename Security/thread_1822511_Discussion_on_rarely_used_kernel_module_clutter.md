---
title: "Discussion on rarely used kernel module clutter"
date: 2011-08-10
forum: Security
---

### Post by requeth on 2011-08-10
Ok everybody,

I want to start a conversation.

I just recently got back from DEFCON where I watched hack after hack of linux using unneeded and/or rarely used kernel modules to gain root of a system. Zero day exploits were shown to be so prevalent that a 10 year old was able to find nearly a dozen in 2 days time. I've been looking at unloading any kernel modules that I don't need and I stumbled across something odd.

My laptop has a built in webcam, like almost every one built in the last few years. UVCVIDEO is used to run the webcam, which I've never actually used on this laptop. UVCVIDEO uses kern modules: videodev and v4l1_compat. All three of these modules together is 128 megs of memory which I have never once used, and is potentially exploitable. I'm still tracking down what all of my modules do, they are supprisingly undocumented, but a lot are not being used.

Heres the conversation I want to have. Why is 128 megs of unused code being loaded when a less then 3 meg hook could be added and if the webcam is called then the module is dynamically loaded. I understand that someone could replace the code to be loaded and run, but I'd think that would happen less often then the code already running.

I also understand I can just unload them and blacklist them, but I don't know why these are turned on by default when webcams aren't used on a daily basis by the majority of users. I do admit I may just not know the users who use webcams daily. Loading the modules barely takes any time, users likely wouldn't notice the wait.

Requeth

---

### Post by cariboo on 2011-08-11
Ubuntu is about ease of use, so that new users have a good experience running the base installation. I know quite a few users, that use their webcams on a daily basis, so just because you never use your webcam, doesn't mean that others don't.

Obviously going to defcon, threw a good scare into you, if you are really worried, about someone cracking your system through unused modules, I'd suggest you build a custom kernel, just create the modules you need to run your system, and don't add anything you don't need.

---

### Post by bodhi.zazen on 2011-08-11
All distros, including gentoo, use a "generic" kernel with many many unnecessary drivers. This is immediately obvious when you build your first custom kernel.

If you stop panicking and think for a minute the reason is obvious, distributions want the Live CD to boot on a wide range of hardware, same for the kernel you distribute. One of the biggest complaints or problems Linux has is hardware compatibility. Many of the support threads, especially wireless, have to do with compatibility.

Building a custom kernel with only the modules you use is one method of hardening your server or desktop. Such a hardened kernel would run on one machine, yours. Clearly inappropriate for distributing with any kind of Live CD or as the kernel for any distro.

With that said, yes there are still many unnecessary modules. If you are really interested I suggest you post your suggestions on Launchpad as a bug report against the kernel.

The kernel team is not known for looking at the forums for questions such as yours (they use Launchpad and mailing list).

[https://wiki.ubuntu.com/KernelTeam/](https://wiki.ubuntu.com/KernelTeam/)

---

