---
title: "Will Click packages be DE-agnostic?"
date: 2014-11-06
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-11-06
I read [Click packages and how they&#8217;ll empower upstreams]("http://beuno.com.ar/archives/334"). It begins with> As the pieces start to come together and we get closer to converging mobile and desktop in Ubuntu, Click packages running on the desktop start to feel like they will be a reality soon (**Unity 8 brings us Click packages**).I emphasised the last few words because that leads me to wonder if Click packages, when available, are to be something limited to Unity. The rest of the blog doesn't give any indication as to whether users of other official flavors would be able to install such packages.

---

### Post by grahammechanical on 2014-11-06
Based upon my little knowledge of all of this, I say,

Unity 8 is Unity 7 re-written to run on Mir. The two go together. Click packaging is part of the Ubuntu SDK. The two go together. The main purpose of the SDK at the present time is to make it easy for developers to get apps into the Ubuntu phone/tablet app store because the potential customers for Ubuntu phones/tablets like lots of apps. And that of course, means apps that run on Unity 8.

I do not think that it is the intention to lock click packages to Unity 8. But I also do not think that at the present time the developers are spending too much time or effort worrying about getting click packages to run on anything other than Unity 8 and Ubuntu for Devices. They are concerned about getting applications in the app store to scale between phone> tablet>PC and even TV.

I am not a developer but I do not see applications as being dependent on the UI or even the DE. And Unity is a shell and not a Desktop Environment. What is the DE in Ubuntu? Is it not Gnome 3? And Gnome 3 must also be the underlying DE of Ubuntu for Devices. True?

Ubuntu is built upon Debian. That is not going to change. Ubuntu 16.04 will be based upon Debian and Gnome 3 and have Mir and Unity 8 and Debian packaged applications as well as Click packaged applications. The components for the Click package method are already in the Vivid Vervet archive.

It is up to the developers of the flavours and those distributions that are built on Ubuntu to decide if Click package components are to be part of their default install or to be something the user activates. Just as they also have the power to decide if their distribution is going to use Mir or continue with the Xserver or use some Wayland compliant compositor.

This is all in the future. The near future to be sure but a lot will depend upon how all these things turn out.

Regards.

---

### Post by vasa1 on 2014-11-06
> I am not a developer but I do not see applications as being dependent on the UI or even the DE. And Unity is a shell and not a Desktop Environment. What is the DE in Ubuntu? Is it not Gnome 3? And Gnome 3 must also be the underlying DE of Ubuntu for Devices. True?Well, aren't there things that work only on Unity and not elsewhere? But I listened to a Google Hangout with Michael Vogt and it does appear that Click packages can conceptually even be used on non-Debian systems.

My next question concerns duplication; will it be fair to consider a Click package "autonomous" or "self-sufficient"? In current terms, won't all the dependencies be bundled together with the actual application?

---

### Post by ian-weisser on 2014-11-06
> **vasa1 said:**
> won't all the dependencies be bundled together with the actual application?

Yes, all dependencies that are not already included with the standard install of Ubuntu should be included in the click package. If I recall correctly, click packages will have no way to trigger apt to install dependency debs from the Ubuntu repositories.

Most click packages (games, small apps) don't need (many) dependencies, and should be using the Unity API to interface with the system. Yes, the click-package software can use any DE's API...if that DE has an API for the software to use. There is no requirement for other DEs to support the Unity API, nor have I seen a freedesktop.org standard for what such an API should look like. So a game developed for the Unity API using the Ubuntu SDK might not work with KDE or Lubuntu. There is precedent: Unity scopes generally don't work outside of Unity.

Complex applications with lots of shared dependencies can be installed by click packages (if someone creates it), or by apt. The click package must include it's dependencies (which can include other click packages). If my cousin wants a video transcoder on her phone, it's going to be either a few really big click packages or many very small apt packages. But not a mix of the two.

But most phones I see don't have anything more complicated than Facebook installed, so I don't think the click package requirement to include dependencies is going to be a problem.

---

### Post by vasa1 on 2014-11-06
> **ian-weisser said:**
> ... But most phones I see don't have anything more complicated than Facebook installed ...Good one. I have only Jota text editor and What's App plus Google's and Samsung's mandatory stuff.

---

