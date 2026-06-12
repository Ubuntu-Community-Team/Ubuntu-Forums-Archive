---
title: "My Adventures with Arch Linux"
date: 2006-12-10
forum: The Cafe
---

### Post by picpak on 2006-12-10
Looks like Arch is the distro Ubuntu experts 'graduate' to. I wanted to switch for a while, but it was a post in the Feisty forums extolling its virtues that pushed me over the edge.

First, let me explain why I did it. After more than enough crashes with Feisty and a broken Internet, I decided to go back to Edgy. However, the Internet wouldn't even connect during a reinstall. I was ready to spend a week with a crippled computer until I could get the XP CDs off my sister, but then I looked behind the router and found my cable light burned out. ](*,) Oops.

I switched the cables around, installed Xubuntu, and all was well. However...I felt it was *too* easy. I needed a challenge. I'm not Gentoo material yet, so I opted for Arch.

The installation was easy, with a copy of the Installation Guide available. Partitioning was done with cfdisk, the only partitioner I ever understood. I nuked my Ubuntu install, because I had no idea how well the /home partition would cooperate with each other (for instance, Arch puts its program files in /opt).

The installation went very well. If the Installation Guide told me anything, I was on my way to a workable kernel. ...I wasn't. After tons of GRUB errors and kernel panics, I searched the forums for a backup kernel, a la Ubuntu. I found it, put it in my /boot/grub/menu.lst, and used that (until a few days ago, when I realized to switch initrd26.img to kernel26.img in /boot/grub/menu.lst).

Keep in mind, the default Arch install only installs enough to get a kernel and a login screen. It makes Ubuntu's server install look bloated. After two days in a console and learning more about links2 then ever before, I got myself a workable Xfce4 and Xorg. Just like Ubuntu, extra repositories are needed to get more programs (in this case, Xfce4's svn version). I generated my xorg.conf with hwd -xa (hwd, of course, wasn't installed by default), but this only gave me a lousy vesa driver. After even more searching, I found the obscure name of my driver: xf86-video-i810. How obvious.

After all the setup, though, it's a breeze. You can install almost anything through *pacman -S <packagename>*, and if it's not in there, it's probably in [AUR](http://aur.archlinux.org/) (the exceptions being Audacity 1.3.2 and localepurge).

Now, after a *lot* of reading through their forums and their [wiki](http://wiki.archlinux.org/index.php/Main_Page) (their wiki is your friend...seriously), I've got it feeling just like Ubuntu. The hype about the speed in i686 is overrated, but it is noticable with Java applications.

And now, the obligatory screenshot:

[[img]http://smg.photobucket.com/albums/v37/picpak/th_2006-12-10-113031_832x624_scrot.png[/img]](http://img.photobucket.com/albums/v37/picpak/2006-12-10-113031_832x624_scrot.png)

In case you're wondering, that pink dog is the 'picpak' in question. I created him when I was little, the background was a little plain, I threw him in. I guess you could call it a 'Picmac'.

And there you have it!

---

### Post by coder_ on 2006-12-10
I've wanted to use Arch Linux or Gentoo for SOOOO long!  But for some reason, neither 64 bit edition's live cd (using Archie for Arch Live) will boot on my computer! :(

Arch looks so powerful! :'(

I even have an extra 2nd hard drive that is empty to use!  Arch looks like it has a great community (similar to this one in a way), and from what I've read, the wiki is fantastic.  Their wiki is probably one of the most useful wikis I've read for a Linux distro.

Are you running Arch under 64 bit?

---

### Post by midwinter on 2006-12-10
Good stuff. I absolutely love Arch and ran it for almost a year, it's fast, simple, the community is great and pacman is excellent.  

Within the last month I switched to Debian (testing) though, because the bugs in packages on Arch were just getting too much for me and I realised that a lot of the time I was having to avoid packages i'd like to use because they had annoying bugs in.  Running Gnome 2.16 on Arch for example meant having an extra drive shown in Nautilus (actually my / drive), which couldn't be accessed or unmounted or anything.  Gnome volume manager would frequently be broken, a week or two ago the only solution I found on the forums meant having to install GDM.  Over the last year, there has always been some kind of breakage in Gnome there and you never know if the next update is going to break something else.  Now, this isn't the fault of the Arch folk at all i'm sure, it's just the packages are new and cannot be thoroughly tested before inclusion, but that's not really the point of Arch, it's meant to be bleeding edge after all - just a little too bleeding edge and not well tested enough for me.  

Arch is beautiful in its simplicity though, and I miss it at times, Debian can be a bit of a mess in comparison.

---

