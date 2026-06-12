---
title: "Defference between UBUNTU &amp; unr..?"
date: 2009-11-04
forum: Ubuntu Moblin Remix
---

### Post by Harshana on 2009-11-04
Hi everybody.....
I want to know the exactdefferent between UBUNTU 9.04 & UNR 9.04
in detail.Can anyone teach me...........?
Thanx...:p

---

### Post by which ones pink on 2009-11-04
UNR is Ubuntu Netbook Remix.

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

---

### Post by Harshana on 2009-11-04
Thanx.But i knew it.I exacty want to know what is the difference between UBUNTU 9.04 and UBUNTU NETBOOK REMIX 9.04.Technical and featured difference detailedly.....

---

### Post by Jackyboy86 on 2009-11-04
UNR is specifically designed for use with Intel Atom processors.
At first, I thought it was going to be just the same with a different shell, but I've found Ubuntu to be about 15-20% faster on my Mini 10 (once I had wrestled with the lack of GMA500 support)
On older versions, UNR was just a netbook friendly shell for Ubuntu, which could be downloaded from the repository.
This time, Canonical say they've started from the bottom and worked up to create UNR.
And, it shows.
It's also a lot easier on smaller 

Techspecs?
Not much difference, just optimised for Atom processors.
The lack of GMA500 support makes Karmic a no-go for users without a reasonable degree of technical knowledge, however.

Are you thinking of installing it?

---

### Post by snowpine on 2009-11-04
Ubuntu 9.04 and Ubuntu Netbook Remix 9.04 are the exact same core system. They differ in two ways: the user interface (Ubuntu uses the Gnome desktop; UNR uses a special "launcher") and which applications are pre-installed (UNR omits a few apps so that it will fit on a 4gb drive).

You can convert an Ubuntu install to UNR by typing 'sudo apt-get install ubuntu-netbook-remix' or vice-versa with 'sudo apt-get install ubuntu-desktop'.

You can see the exact differences by comparing these lists:

[http://packages.ubuntu.com/jaunty/ubuntu-desktop](http://packages.ubuntu.com/jaunty/ubuntu-desktop)
[http://packages.ubuntu.com/jaunty/ubuntu-netbook-remix](http://packages.ubuntu.com/jaunty/ubuntu-netbook-remix)

---

### Post by Dooms_day on 2009-11-04
its got a weird desktop tho

---

### Post by Harshana on 2009-11-05
> **Jackyboy86 said:**
> UNR is specifically designed for use with Intel Atom processors.
At first, I thought it was going to be just the same with a different shell, but I've found Ubuntu to be about 15-20% faster on my Mini 10 (once I had wrestled with the lack of GMA500 support)
On older versions, UNR was just a netbook friendly shell for Ubuntu, which could be downloaded from the repository.
This time, Canonical say they've started from the bottom and worked up to create UNR.
And, it shows.
It's also a lot easier on smaller 

Techspecs?
Not much difference, just optimised for Atom processors.
The lack of GMA500 support makes Karmic a no-go for users without a reasonable degree of technical knowledge, however.

Are you thinking of installing it?

Ofcource i did and i installed it.It is great with interface.
I think it is effective than windows.Isn't it?
Didn't you try?
Any way thanx to your post Jackyboy86  ;)

---

### Post by Harshana on 2009-11-05
> **snowpine said:**
> Ubuntu 9.04 and Ubuntu Netbook Remix 9.04 are the exact same core system. They differ in two ways: the user interface (Ubuntu uses the Gnome desktop; UNR uses a special "launcher") and which applications are pre-installed (UNR omits a few apps so that it will fit on a 4gb drive).

You can convert an Ubuntu install to UNR by typing 'sudo apt-get install ubuntu-netbook-remix' or vice-versa with 'sudo apt-get install ubuntu-desktop'.

You can see the exact differences by comparing these lists:

[http://packages.ubuntu.com/jaunty/ubuntu-desktop](http://packages.ubuntu.com/jaunty/ubuntu-desktop)
[http://packages.ubuntu.com/jaunty/ubuntu-netbook-remix](http://packages.ubuntu.com/jaunty/ubuntu-netbook-remix)


Really ?........
I thought they were different from the bottem.Will UNR 9.10 be so?
Thanx snowpine.........:D

---

### Post by Jackyboy86 on 2009-11-05
Snowpine - no you cant!
In Jaunty it was a different shell, now it's a different OS.

I'm currently using UNR - found it better for a 10" screen than Gnome - stuff fits on my screen now! It's also proving a hell of a lot faster than Desktop.
I ran Jaunty Desktop, Karmic Desktop, Moblin and Karmic UNR side by side for a week, UNR blew me away. Moblin was beautiful but too buggy.
When Moblin's finished, it's going to be one severely mattressable OS...

---

### Post by snowpine on 2009-11-05
> **Jackyboy86 said:**
> Snowpine - no you cant!
In Jaunty it was a different shell, now it's a different OS.


ubuntu-netbook-remix is simply a metapackage (like ubuntu-desktop, xubuntu-desktop, etc.) that can be installed on top of an i386, amd64, or lpia Ubuntu "base". 

More details here:

[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

If it's faster for you, it's due to the interface and package selection, not because it uses a different kernel or architecture.

Type 'uname -a' if you don't believe me. :)

---

### Post by Jackyboy86 on 2009-11-05
Why does it only work on Atom based machines?

I see your link and I raise you
[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

;)

---

### Post by snowpine on 2009-11-05
> **Jackyboy86 said:**
> Why does it only work on Atom based machines?

I see your link and I raise you
[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

;)

That's a typo. (UNR works fine on, for example, Asus eee's with Celeron processors, and I've even tested Karmic UNR on a Pentium 4 desktop!)

The Atom-specific Ubuntu version is called "lpia" (low power Intel architecture) and is available here: [http://cdimage.ubuntu.com/ports/releases/9.10/release/](http://cdimage.ubuntu.com/ports/releases/9.10/release/)

(edit) Here's a link: [http://brainstorm.ubuntu.com/idea/19409/](http://brainstorm.ubuntu.com/idea/19409/)

---

