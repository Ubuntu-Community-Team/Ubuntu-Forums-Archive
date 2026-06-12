---
title: "Mir versus XMir Security differences?"
date: 2016-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-07-17
Ubuntu Snappy-core using the Mir display server with Unity8 and snap-apps should be a pretty nailed down system, that offers new, unprecedented security for users.

What of the XMir part of the equation for X-Windowed systems. Those systems depend on the X display server running on XMir rather than using the Mir display server.

It is well documented that Mir and Wayland display servers are needed in part, to over-come the security deficits of the X-Windowed display server.

For maximum security of an Ubuntu OS, will it be that the Mir display server will offer more security than XMir with X-Windowed systems?

Some Desktops are committed to porting from X to the Wayland Server as an example. (KDE, Gnome, Enlightenment) and more. What of the Ubuntu family of official derivative OS's? Is there the support to initiate the same for them porting to Mir?

Xubuntu as an example, depends on what the Xfce project decides to do.

---

### Post by mc4man on 2016-07-17
I'm curious as to   how the current ubuntu is 'insecure' & is there some list of known malware affecting ubuntu users?

---

### Post by mikodo on 2016-07-17
> **mc4man said:**
> I'm curious as to   how the current ubuntu is 'insecure' & is there some list of known malware affecting ubuntu users?
One example is stated in this article discussing the potential malware aspects of X. See the part on Mathew Garrets demonstration:

[http://arstechnica.com/information-technology/2016/06/goodbye-apt-and-yum-ubuntus-snap-apps-are-coming-to-distros-everywhere/](http://arstechnica.com/information-technology/2016/06/goodbye-apt-and-yum-ubuntus-snap-apps-are-coming-to-distros-everywhere/)

---

### Post by mc4man on 2016-07-17
> **mikodo said:**
> One example is stated in this article discussing the potential malware aspects of X. See the part on Mathew Garrets demonstration:

[http://arstechnica.com/information-technology/2016/06/goodbye-apt-and-yum-ubuntus-snap-apps-are-coming-to-distros-everywhere/](http://arstechnica.com/information-technology/2016/06/goodbye-apt-and-yum-ubuntus-snap-apps-are-coming-to-distros-everywhere/)

That has nothing to do with the current ubuntu.

---

### Post by mikodo on 2016-07-17
> **mc4man said:**
> That has nothing to do with the current ubuntu.
I expect you are correct in pointing that out.

What remains is my question wondering if there will be security benefits using Mir over XMir. I dunno.

---

### Post by mc4man on 2016-07-17
> **mikodo said:**
> 

What remains is my question wondering if there will be security benefits using Mir over XMir. I dunno.
That I expect will be true. Ultimately I see ubuntu app install  more like lets say the google play store. In that case you're using non transparent, sometimes closed source, pre-compiled binaries with additional installed files into a read-only filesystem.
So in that case this new security is a must.. According to that blog by Mathew Garrets then mir is more secure than xmir (X)

---

### Post by mikodo on 2016-07-17
Thank you. I ponder these things.

---

### Post by grahammechanical on 2016-07-17
This blog post by a Canonical engineer explains things.

[https://bregmatter.wordpress.com/](https://bregmatter.wordpress.com/)

> Libertine consists of a *container* with a minimal Ubuntu system  installed in it, and a Mir client application that proxies the confined  application.  In the case of an X11 application, that proxy is called **XMir**,  and is actually an x.org server with a Mir-based DDX — which is to say,  it’s a bog-standard X11 server that ends up drawing its output on a Mir  surface.  Libertine also provides alternative proxies, such as a  terminal application for venerable terminal applications such as  Midnight Commander or good old **vi**.

As I understand it, and I am often wrong but rarely admit it, :)

 XMir allows the x.org,server to draw the application window on to Mir. Furthermore, as all this is running a Linux container the security benefit of Mir over X server is not compromised.

DDX = Device Dependent X driver. See Video Drivers

[https://wiki.ubuntu.com/X/Architecture](https://wiki.ubuntu.com/X/Architecture)

Regards.

---

### Post by mikodo on 2016-07-17
^^ There you go again Graham, quietening my fears for the flavours. :)

Let's see what you posted and what's in the links.

Addendum. Yikes. That is a lot to digest.:)  So in the libertine container the magic will occur. Secure and making decisions as to what needs to be run. Be it xorg, drivers or whatever. (maybe the problems with 3D for nVidia is in the implementation of the drivers needed within the Libertine process or it is not equipped yet).

So, some young, bright, enthusiastic, derivative programmers and maintainers should be able to push in the GTK and Qt libraries needed to run their flavour's Desktops to be drawn by Xorg with XMir for Mir to implement.(mind boggling). Then, security remains enhanced and the users get to play with the up and coming Snaps in their respective separate containers. 

So, I prolly have that all wrong but, what was not accounted for in that article by Mathew Garrett is the workings within Libertine to accommodate Xorg securely.

---

### Post by mc4man on 2016-07-17
> **mikodo said:**
> 

So, I prolly have that all wrong but, what was not accounted for in that article by Mathew Garrett is the workings within Libertine to accommodate Xorg securely.
I think apples & oranges - he was referring to snaps running in 16.04, not libertine

---

### Post by mikodo on 2016-07-17
> **mc4man said:**
> I think apples & oranges - he was referring to snaps running in 16.04, not libertine
Right!

I jumped to the conclusion he meant that Xorg couldn't be securely run for MIR. Of which I knew nothing of.

Addendum. No actually, I didn't jump to that erroneous conclusion. But, I never understood how XMir and Mir worked together before. And as far as the derivatives come along, it will remain to be seen. Seems, the dev of Ubuntu Mate intends to Snap it. I don't know if that means the whole desktop or what.

---

### Post by grahammechanical on 2016-07-18
What Matthew Garrett does not make clear is that the packaging format of an application is irrelevant. Any application that is specifically written to take advantages of security vulnerabilities in the X server will do exactly that  if it is installed on anyone's system and it matters not that the application is packaged as a snap or click or deb or rpm which is the RedHat packaging method and the company that Matthew Garrett used to work for. The packaging method is not designed to protect the user from security vulnerabilities of the X server.

For Matthew Garrett to be honest he would have to repeat the experiment and package that application as a Flatpak, which is the RedHat solution to the future of application distribution.

We come back to the wisdom of only installing from trusted sources. That wisdom is what Matthew Garrett has proved to be true. How does Canonical make sure that malicious applications are not going to be accepted into its app store? Ask the same question of RedHat and Fedora and Debian. And ask it of anyone else who is providing applications in one of these new application distribution methods. Whether it be Snap, Flatpak or Appimage or anything else.


Regards

---

### Post by mikodo on 2016-09-12
I needed to back away from this thread and from thinking about this. Too much of it was 'crystal ball gazing' for me.

All UNIX like OS's and distributions that wanted a graphical user interface have been using X.

Some engineers and maintainers of X, decided a replacement display server was needed and had started working on Wayland (display server protocol). Ubuntu decided upon using what works for them with Mir with XMir for Unity8. Both provide a means to provide for processes to run X reliant Desktops and Apps within them. The landscape is changing for X, I have no doubt. History will provide how it all plays out.

I'm not concerning myself with this any more. I will be following these changes and I have prepared myself to leave Xubuntu with its' desktop Xfce if, Unity on Mir, becomes more attractive for me. The choices available in Linux, affords me this 'luxury' of choice and for that, I am thankful.

---

### Post by montag dp on 2016-09-13
> **grahammechanical said:**
> We come back to the wisdom of only installing from trusted sources. That wisdom is what Matthew Garrett has proved to be true. How does Canonical make sure that malicious applications are not going to be accepted into its app store? Ask the same question of RedHat and Fedora and Debian. And ask it of anyone else who is providing applications in one of these new application distribution methods. Whether it be Snap, Flatpak or Appimage or anything else.


RegardsThis is one of the things I don't like about Snaps, Flatpaks, etc. It's not that they are insecure as a package format, it's the fact that they make it very easy for anyone to create a package. My concern is that people will start downloading snaps from who-knows-where on the Internet, many of which could be malicious or adware or just downright junk. Of course, that could happen now too, but it does lower the entry barrier. And to reiterate your question, what about the Snaps (Flatpaks, etc.) that make it into the official repositories? Someone is going to have to go through them all and screen them for quality, which makes it no more convenient than the traditional approach to software distribution in Linux.

I guess I like the traditional method and don't want to see Linux become inundated with junk software like Android and Windows.

---

