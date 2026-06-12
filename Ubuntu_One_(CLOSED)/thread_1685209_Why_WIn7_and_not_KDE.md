---
title: "Why WIn7 and not KDE?"
date: 2011-02-10
forum: Ubuntu One (CLOSED)
---

### Post by teh603 on 2011-02-10
So, I just noticed that Ubuntu One is being released for Win7. Wow. Yay. Except that I've been unable to run Ubuntu One natively on Kubuntu without installing the entire Gnome desktop, and that's not something I'm going to be doing unless Unity is completely purged from existence and history.

Anyway, it looks like Kubuntu users who don't want Gnome and Unity will be having to run the Win7 version of Ubuntu One thru WINE. And even that will require us to install .Net from M$.

Yes, I know there *was* a PPA that allowed Ubuntu One to run on KDE. No, it no longer exists and all that remains is stuffed into a rather difficult to use tarball instead of a .deb package.

So does anyone else see a bloody huge problem here?

---

### Post by perspectoff on 2011-02-10
Unity was being developed, I'm sure, to allow capture of the mobile market and to lessen the development headache of making sure Gnome and KDE were interoperable on Ubuntu. (Unity is not Gnome, AFAIK.)

I'm sure Shuttleworth was pitching to Nokia.

Unity will have to incorporate Qt heavily (which KDE does in many cases, already).

It boggles me that Ubuntu One doesn't accommodate KDE, but I'm not an UbuntuOne user and don't advocate online storage of files for anyone anyway (risk of theft, hacking, government scrutiny, wikileaks, etc. etc. (lol) no matter who is storing your files).

Besides, anyone can easily set up their own WebDAV server and keep their entire music library on their own home server while having access to it while mobile.

As to buying music from UbuntuOne (a la the Apple iTunes Store), well, it's a business decision for Canonical whom they want to accommodate. If they don't accommodate their own users, that's silly, of course.

---

### Post by Grenage on 2011-02-10
> **teh603 said:**
> So does anyone else see a bloody huge problem here?

Yes and no; I imagine that most people using Ubuntu are using Ubuntu - as in not Kubuntu. They're likely aiming for the maximum user base as a means of revenue, which would prioritise Windows and pure Ubuntu (assuming Mac isn't in the fray).

Still, I find it surprising that UO won't install easily in Kubuntu...

---

### Post by Joe of loath on 2011-02-10
Are you sure it's not installing the metapackage ubuntu-desktop, but not all the contents, only a couple? I notice Debian/Ubuntu does this sometimes.

---

### Post by teh603 on 2011-02-10
> **Joe of loath said:**
> Are you sure it's not installing the metapackage ubuntu-desktop, but not all the contents, only a couple? I notice Debian/Ubuntu does this sometimes.
When I tried installing it, it was downloading a honking big mess of dependencies and sub-dependencies before I canned it. I didn't actually see the ubunut-desktop metapackage, but I did see almost all of Gnome going in there.

The main reason I wanted it was so I could synchronize writing projects (lots of small .txt files written in Kate) amongst my mini-mac (which is also running Kubuntu) and my laptop.

Edit: I know Gnome is not Unity, but it looks like it will be permanently integrated with Gnome-based Ubuntu installations starting in Natty. I've already made my thoughts about Unity known in the Natty board, so there's no real reason for me to bore everyone with them again.

---

### Post by perspectoff on 2011-02-10
"There's no place like ~/ "

And my favorite bumper sticker:

"There's no place like 127.0.0.1"

---

### Post by Dragonbite on 2011-02-17
Unity is supposed to become more Qt-friendly than Gnome is though I still doubt this means UbuntuOne will be available to Kubuntu.

I don't know the technical aspects, but I wish they would make it more generic (Gnome, KDE, *box, etc.) and expand it to work on Macs as well.  

If on Windows it is so .NET connected, maybe they could compartmentalize it with Mono so only the Gtk and Qt bindings need to be different to handle the different file managers.  I thought, though, that in Gnome it is more Python based, while Windows is .NET.

---

### Post by oldos2er on 2011-02-19
I switched to Kubuntu from Ubuntu last year. I still have a couple Gnome apps I'm using, including Ubuntu One (via CLI), but I think it's really unfortunate that Kubuntu is the odd stepchild in this case. 

I suppose you've considered Dropbox?

---

### Post by Alejandro Nova on 2011-03-02
The truth is: to install Dropbox and make it work under Kubuntu is a breeze. To install Ubuntu One and make it work under Kubuntu is the Hell revealed.

To install Ubuntu One under KDE, I have to compile the code that remains in a tarball, see if it compiles against KDE 4.6, and pray that it has kept up with changes in Ubuntu One itself (hint: it didn't keep up). Also, I can install the entire GNOME desktop with Unity and switch to that. Interesting.

To install Dropbox, it's easy. It's only 2 DEBs away (beware: the last one doesn't install against KDE 4.6, that will change soon)

[http://sourceforge.net/projects/kdropbox/files/kfilebox-0.4.7/Kubuntu%2010.10/](http://sourceforge.net/projects/kdropbox/files/kfilebox-0.4.7/Kubuntu%2010.10/)
(Pick your poison: AMD64 and i686 are provided)

[http://dl.dropbox.com/u/9840690/dolphin-box-plugin/dolphin-box-plugin_0.1-1_amd64.deb](http://dl.dropbox.com/u/9840690/dolphin-box-plugin/dolphin-box-plugin_0.1-1_amd64.deb)
(Only available for AMD64; i686 and KDE 4.6 users need instructions from [here]("http://trichard-kde.blogspot.com/2010/12/introducing-dropbox-integration-for.html"))

After that, open Dolphin, select "Preferences | Configure Dolphin...", switch to the "Services" panel, and, where it says "Version Control Systems", check the "Dropbox" box. You'll have the full range of Dropbox support: icons showing you your Dropbox status in every file, a client to manage the proprietary daemon, and even a Monochrome theme, to make the thing fit in your KDE desktop.

---

### Post by duanedesign on 2011-03-14
> Unity is not Gnome, AFAIK.

Ubuntu Natty will still use Gnome. Unity is only a different shell that replaces Gnome Panel. Ubuntu will still be a Gnome platform.

---

### Post by Dragonbite on 2011-03-14
I'm beginning to doubt they plan on moving U1 to Kubuntu because their focus is going to be making everything work with Unity.  With the focus on Unity, developing/porting it to Kubuntu moves users from their favored child (Unity).

Maybe eventually they will make it usable in KDE but that would be an offshoot of if they begin using Qt for UbuntuOne or not (not likely).

---

