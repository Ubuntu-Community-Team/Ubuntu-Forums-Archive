---
title: "Unity 3D 5.1 experimental game engine for Linux has been released!"
date: 2015-08-31
forum: The Cafe
---

### Post by flaymond on 2015-08-31
Hey Ubuntu community, and especially to game developers that want to use Unity 3D game engine (editor) to develop on Linux.

There's a good news,

Finally, Unity 3D 5.1 experimental build has been released for Linux. Thus, Unity 3D 5.1 Experimental build is available for 64-bit system as Debian package. Yes! You can download it, and run

```
sudo dpkg -i unity-editor-5.1.0f3+2015082501_amd64.deb 
``` to install it, while drinking a cup of coffee. This might be the chance for most game developers on Linux to try a good quality game engine (editor), and widely available on different platforms. C++, C#/Mono, and UnityScript? Now, you can use them with the game engine (editor) on Linux without tinkering to launch a virtualization software or using emulators to run Unity 3D game engine! 

Now what you're waiting for? Download and try it now! - [http://download.unity3d.com/download_unity/unity-editor-5.1.0f3+2015082501_amd64.deb](http://download.unity3d.com/download_unity/unity-editor-5.1.0f3+2015082501_amd64.deb)

*Don't forget to leave your feedback after using it to this thread! :)*


Source - [http://blogs.unity3d.com/2015/08/26/unity-comes-to-linux-experimental-build-now-available/](http://blogs.unity3d.com/2015/08/26/unity-comes-to-linux-experimental-build-now-available/)

---

### Post by monkeybrain20122 on 2015-09-01
I don't know much about Unity3d and game engines except that wine is the only way for Linux users  to access Unity3d player. Is this only for developers so that  Linux developers can finally design games on Linux that they cannot access as normal users on the same platform? Or is there actually a Unity player for Linux? If it is the former I can't see why Linux users in general should get excited about it.

---

### Post by mcduck on 2015-09-01
It's the editor. The engine itself has been able to run on Linux for a long time now, so the only change is that now people making games on Unity can do their work on Linux if they want to.

The Unity web player plugin isn't available for Linux, and most likely won't ever be since it's being phased out as WebGL suport is taking it's place (and that will of course run on any browser, regardless of your OS, and without requiring any plugin to work). 

Does this matter to people who only play games instead of making them? Not much, although I'd assume the quality of Linux builds will improve a bit, being able to run the editor and debugging tools etc. on Linux makes it easier to test the builds and spot any possible issues quicker. It's always nice to have the tools available for the same platform you are building for.

...and as a indie game dev who prefers Linux desktop over Windows/Mac, this is of course great news. Pretty much all the other tools I use for my work already run on Ubuntu, so Unity was the last missing piece of the puzzle. After a quick test even this early release seems to work surprisingly well. :)

(For anybody trying this, the .deb bundles MonoDevelop with it, but it doesn't actually work at least for now. So you'll still need to install MonoDevelop separately from Ubuntu's repositories if you want to use it)

---

### Post by Portaro on 2015-09-01
No plans for 32 bits?

Because my machines have this architecture, but if I can see the tool I like .

Thanks .

---

