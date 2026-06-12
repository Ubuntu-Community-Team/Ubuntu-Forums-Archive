---
title: "Ubuntu desktop for server?"
date: 2007-11-03
forum: Server Platforms
---

### Post by ARhere on 2007-11-03
Hello Everyone,

First off, I wanted to say, "Hello, first post" before coming to the appropriate topic for this thread.  I am a E.E. so I am not sure how much help I can offer in the development world.  However, I have fallen in love with Ubuntu, after declaring I will not make the Vista step, and want to get a little more involved.  I have done some work with my company designing Linux controllable analog circuits and power supplies so MSG me if there is something I can help with.:KS

On to the more appropriate topic...

I have a small PC that I use as a simple file and print server and want to remove the old Win2k OS and use linux for this function.  The only fancy "server" thing about it is a PROMISE RAID mirror card I use to help protect family pictures.  Normally I would install Fedora Core for light server duties but what to use Ubuntu instead, however I am not sure Ubuntu server is for me as I enjoy a GUI desktop with some basic server stuff like Samba and Apache.

My point is, what are some opinions as to why modding Ubuntu desktop to fit my needs would be better then just loading FC? (Besides Ubuntu is just cool!)

Cheers,
-Andrew

---

### Post by scorp123 on 2007-11-03
You could give "Xubuntu" a try. That's Ubuntu with the light-weight "XFCE" desktop instead of GNOME. As for "server". The point of "Ubuntu Server" is that admins who want to use Ubuntu for serving purposes don't get an OS (e.g. Ubuntu Desktop) which they would perceive as being "too bloated", e.g. because it has a GUI (which is pointless on a server). So instead of forcing admin folks to download "Ubuntu Desktop" and then have them remove GNOME and all the GUI tools after the installation (because it's "bloat" ...) they can download "Ubuntu Server" which is "out of the box" the way they want: No GUI, no "bloat", just right for server usage.

However, that doesn't mean you can't use the normal "Ubuntu Desktop" for the same purposes, especially if not having a GUI is an issue. All the Ubuntu variants use the same online repositories, so it's still the same software, and it's fairly easy to transform a "Ubuntu Server" installation into a "Ubuntu Desktop" installation and vice versa, it's just a question of installing the missing GUI packages on the "Ubuntu Server" or the needed server packages on the "Desktop" installation.

If you want a light-weight GUI desktop "out of the box" I'd suggest to give "Xubuntu" a try. Otherwise you could still e.g. install the normal "Ubuntu Desktop" and later on add smaller GUI environments, e.g. "openbox", "fluxbox" or whatever else you will find in the repos. You can then select the GUI environment at the login window ("Sessions" menu).

---

### Post by HermanAB on 2007-11-03
Linux is Linux is Linux...

One distro does not have any serious technical advantage over another.  The differences are mainly cosmetic.

Cheers,

Herman

---

### Post by ARhere on 2007-11-03
> **HermanAB said:**
> Linux is Linux is Linux...

One distro does not have any serious technical advantage over another...

This forces me to ask the question... If that is so, why are there so many distro's?  Why did Ubuntu branch off of Debian?  Is it just philosophy?

-AR

---

### Post by OmegaBLK on 2007-11-03
> **ARhere said:**
> This forces me to ask the question... If that is so, why are there so many distro's?  Why did Ubuntu branch off of Debian?  Is it just philosophy?

-AR

There are many distros because the GPL allows there to be.  There are many distros  because each one fits a specific need that the distro creators figured needing addressing.  Yes philosophy is one reason; some people believe  deeply in totally Free OS so distros like Debian fill that need.  Some distros cater to helping Windows switch over to Linux so they include proprietary software.  Some are server oriented.  Some are security oriented.   There are a few distros geared toward content creation.  Some distros are so specialized that they run from a floppy-disk or run on a obscure CPU architecture that are not supported by the major distros.  Some distros exist because their creators had a difference in opinion with another distro and so they split (fork) off to create their own.  Some distros are specifically made to run on video game consoles, appliances,  and other embedded devices like cell phones.  There are many distros just because.  There really is no one answer to that question, IMO.

Most distros are pretty much the same that is true.  However some of the enterprise and pay-for distros do offer some proprietary tools, software, and/or other copyrighted material that the [Ff]ree distros most likely do not have access to or can't distribute for legal reasons (in regards to the laws and people in the U.S. specifically).

As for Ubuntu, it exists IMO, as it addresses a need or audience that Debian was not really catering to.  Debian main mission is to be a complete [Free](http://www.gnu.org/philosophy/free-sw.html) OS.  Ubuntu, when it began, was very desktop oriented and still is.  Debian is somewhat stricter when it comes to including certain software due to their [philosophy](http://www.debian.org/social_contract).  I have noticed that Ubuntu is a little more liberal then Debian when it comes to including some software that is not necessarily Free.  Debian  Stable also has had an infamously long release schedule in the past that and I think there are on a 1 year and a half schedule now between Stable releases (not sure of that).  Ubuntu releases new Stable versions every 6 months.  I am sure others people could provide a better explanation, but that is how I see it basically.

Free =  [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html) & [http://www.debian.org/intro/free](http://www.debian.org/intro/free)

---

### Post by scorp123 on 2007-11-04
> **ARhere said:**
>  This forces me to ask the question... If that is so, why are there so many distro's? Tastes are different. To each his own. And with Linux you at least *can* adjust it to your needs in whatever way you wish. 

> **ARhere said:**
>    Why did Ubuntu branch off of Debian?  Maybe because they *could*? :)

---

### Post by HermanAB on 2007-11-04
There are over 50,000 Linux programs in the Mandriva repositories (one of the biggest distributions).  Some people like things to work one way, some like it another way.  However, the closer you get to the metal, the less pronounced the differences are.

The main difference between distributions are the installation and configuration wizards.  Some are more attuned to desktop maintenance (Mandriva) and others are more attuned towards server maintenance (Redhat), while Ubuntu is rather basic in comparison to both of those.  

The funny thing is that it is the simplicity of Ubuntu which is making it popular, but lots of questions on the Ubuntu forums never gets asked on the Redhat or Mandriva forums, since they have wizards for it which makes it all a non-issue.

Anyhoo, the main difference between a server and a desktop is that a server is usually a headless machine sitting in a rack in a data centre.  Since it is managed remotely over SSH a server doesn't need to have X and any of the desktop utilities installed.  If your server is in fact a desktop machine and has a screen and keyboard attached, then you may be better served by installing a regular desktop system on it.  

It used to be that X would gobble up lots of RAM and people would rather dedicate that to served processes, but two things have changed over the years.  RAM became cheaper and the Linux scheduler improved a lot.  The result is that having X installed on a server is not an issue anymore, since any process that is not used will get swapped out efficiently. So you need not feel guilty about managing your small server using X and a GUI - when you walk away, things will get swapped out if another process needs the RAM.

'Hope that helps!

Herman

---

### Post by ARhere on 2007-11-04
> **HermanAB said:**
> ... So you need not feel guilty about managing your small server using X and a GUI - when you walk away, things will get swapped out if another process needs the RAM.

'Hope that helps!

Herman

It does, thank you.

Funny, never considered Mandriva.

-AR

---

### Post by HermanAB on 2007-11-04
So if you use a desktop system as a server, just make sure that you have a large swap partition and that you run a firewall script that closes off port 6000 which is the X server port.

Cheers,

Herman

---

### Post by scorp123 on 2007-11-05
> **HermanAB said:**
>  and that you run a firewall script that closes off port 6000 which is the X server port.  Port 6000 isn't open per default :)

e.g. **/etc/gdm/gdm.conf** says: "DisallowTCP=true"; 

And **/etc/X11/xinit/xserverrc** says: "exec /usr/bin/X11/X -dpi 100 -nolisten tcp"

... This pretty much guarantees that port 6000 is already closed, even without firewall. :)

---

