---
title: "Ubuntu Mobile OS Tablet/Phone ~ Can it run Apps from the Repository?"
date: 2016-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-08-06
Sorry if this has been asked before but... I keep reading that the app selection for Ubuntu Phone & Tablet doesn't compare to Android and iOS.

Not a problem since I use one or two android apps at most; but then I also read that Ubuntu's Mobile OS can't run most of the software in the Ubuntu Repository? Am I understanding that correctly? For instance, I can't download LibreOffice or Calibre on an Ubuntu Tablet or Phone?

Am I missing something?

**Edit:** Meant to write 'Can it ***run*** Apps from the Repository?'

---

### Post by grahammechanical on 2016-08-06
Ubuntu phones & tablets have their own app store and the apps are in the Click package format. The Ubuntu for Devices OS will in future have an app store that has apps packaged in the Snap format.

Debian package (deb) apps will not run on Ubuntu for devices because Debian packaged apps are written to run on the X server and Ubuntu for Devices which is used on the phones and tablets uses the Mir compositor and Unity 8.

There is a method being developed that will allow X apps to run on Mir & Unity 8. The method involves installing a snap app called Libertine. Which will allow us to install a deb application and run it in a Linux container using XMir to fool the X app into believing it is running on X and not Mir.

There are threads in the Development section of this forum on Unity 8 and Libertine recording the results of experiments using Libertine in a Mir/Unity 8 session on standard desktop machines. And someone has even snap packaged Libreoffice 5.2 beta which will run on 16.04 with Unity 7.

[https://bregmatter.wordpress.com/2016/07/04/x11-applications-and-unity-8/](https://bregmatter.wordpress.com/2016/07/04/x11-applications-and-unity-8/)

[https://bregmatter.wordpress.com/2016/07/04/previewing-the-new-unity/](https://bregmatter.wordpress.com/2016/07/04/previewing-the-new-unity/)

[https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/](https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/)

[https://ubuntuforums.org/showthread.php?t=2332558](https://ubuntuforums.org/showthread.php?t=2332558)

The point about convergence is that when a suitable Ubuntu phone or tablet is connected to a keyboard, mouse and monitor it switches into desktop mode and then we can use standard desktop apps like Libreoffice running in containers set up by Libertine. Or any that have been snap packaged.

If app developers building apps for other platforms such as Android packaged their apps in the Snap package format then they can be included in the Ubuntu snap store. Or they can set up their own snap store if they wish.

Regards

---

### Post by neu5eeCh on 2016-08-07
Thanks for the explanation. Cleared up all my questions. Am really looking forward to the next couple years & the transition to MIR.

The only downside I suppose, will be the interoperability of apps developed for Wayland vs. MIR.

---

### Post by mikodo on 2016-08-07
> **grahammechanical said:**
>  - Snippet -
There is a method being developed that will allow X apps to run on Mir & Unity 8. The method involves installing a snap app called Libertine. **Which will allow us to install a deb application and run it in a Linux container using XMir to fool the X app into believing it is running on X and not Mir.**


That highlighted statement is illuminating. I keep learning more and more about Mir and XMir . Somehow? I had thought X would be running on Xmir with Mir and had worried about the future security of X and X apps as, Xorg is phased out over the coming years with Mir and Wayland positioned to replace it on the horizon. The security for this I assume, happens in the containment of libertine snap apps.

So, as mentioned before by this author, security for the X app comes down to installing from safe sources such as, "trusted repos" and with that, comes reasonable assurances of security with running X apps on Xmir -> Mir. Great!

Addendum: Each time I read this page, I understand it a bit better. This time, the bits on the "read only" OS beneath it all, gelled more understanding of the security of these processes:

[https://bregmatter.wordpress.com/2016/07/04/x11-applications-and-unity-8/](https://bregmatter.wordpress.com/2016/07/04/x11-applications-and-unity-8/)

---

### Post by grahammechanical on 2016-08-07
> The only downside I suppose, will be the interoperability of apps developed for Wayland vs. MIR.

Time will tell but with open source code it is possible that code from the Wayland project can be used in Ubuntu and also the other way around if the relevant developers so desire.

A search for "wayland" in Synaptic Package Manager on 16.04 comes up with a long list of Wayland libraries in the Ubuntu repositories and it lists these libraries already installed: libwayland-client0; libwayland-cursor0; libwayland-egl1-mesa; libwayland-server0; & libxkbcommon0.

Regards

---

