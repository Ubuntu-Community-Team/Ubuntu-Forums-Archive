---
title: "Fast booting OS for netbook"
date: 2009-09-29
forum: Ubuntu Moblin Remix
---

### Post by goseph on 2009-09-29
What is the fastest booting OS with a graphical window manager, web browser and bit torrent client for eee pc 1005HA?

Moblin 2 or Ubuntu netbook remix jaunty or other?

Thanks guys!

---

### Post by NormanFLinux on 2009-09-29
Kubuntu Netbook Edition. It boots up and shuts down very fast. The WM is designed specifically for netbooks.

---

### Post by goseph on 2009-10-01
Really? Surely not faster than XUbuntu netbook remix? Also is Moblin 2 a completely different kettle of fish to ubuntu netbook remix or do they share a codebase?

---

### Post by cimh on 2009-10-01
> **goseph said:**
> Really? Surely not faster than XUbuntu netbook remix? Also is Moblin 2 a completely different kettle of fish to ubuntu netbook remix or do they share a codebase?

Sharing my experience on the eee 901. 

Arch is fastest but it is hard to set up(from switch on to desktop 12-13s!).

Moblin 2beta booted in 18s. Now it has the package manager included it probably takes longer. I am running it off a stick; its fast and now very close to being a proper distro - (but I dont like the drop down menu and it has limited programs to download and much less flexibility than a standard distro) - I might install it for a while as I wait for karmic to be launched - Karmic alpha (34-45s) is lovely but sadly slower than 9.04 (33s) 

Crunchbang boots in 26-28s A popular distro on netbooks it just uses openbox on ubuntu 9.04. 

Ubuntu 9.04 (lxde) 28-30s (in my experience lxde is faster than gnome, kde or xfce) the difference between it and gnome used to be as much a 8-10 secs but gnome is slicker now so the difference is probably just 2-4 secs

Ubuntu 9.04 (gnome) 33s

ubuntu remix 9.04  35s. surprised to find Remix slower than the standard buntu.

Xubuntu 9.04 39s  A lot of people complain about xubuntu becoming bloated. Perhaps I am just less experienced with it.

Puppy is fast but too minimal for me. xtub is quick but only good for web use.  

If you want speed it is also worth thinking about your programs. Chromium is miles faster than firefox - and beautiful to use. 
Mtpaint is much faster than gimp much and good for basic image resizing etc. Then abiword and gnumeric are faster than openoffice but abiword falls apart if you throw a big document at it.

All very personal views of course.

(edit: I did try to install moblin 2.0 but it aborted at the partitioning stage claiming my ssds were corrupted. This happened a couple of times!)


cimh
901 karmic alpha6

---

### Post by alien21010 on 2009-10-02
Moblin remix boots very quickly, but more importantly is VERY responsive.  I had UNR installed on this before, and Windows 7.  Moblin remix makes this machine feel powerful, whereas with the other OSes its shortcomings were painfully apparent.

---

### Post by goseph on 2009-10-02
> **cimh said:**
> Sharing my experience on the eee 901. 
 Karmic alpha (34-45s) is lovely but sadly slower than 9.04 (33s) 

 
[I]What a detailed reply, thank you for sharing your wisdom. I am very disappointed to hear that Karmic has a lazy boot especially given the promise of improved boot here: [[COLOR=#444444]https://lists.ubuntu.com/archives/ub...ry/000536.html[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html")

Do you suppose that upon release Karmic will be faster? Maybe it is slowed down at the moment because of no -o flags or diagnostic kernel modules (or whatever) that will be removed from the stable?[/I]

---

### Post by cimh on 2009-10-03
> **goseph said:**
> Do you suppose that upon release Karmic will be faster? Maybe it is slowed down at the moment because of no -o flags or diagnostic kernel modules (or whatever) that will be removed from the stable?[/I]

For a few minutes this afternoon I had karmic booting to desktop in 29s which is very impressive for a gnome distro. Problem is 30 minutes later it was back to 40-50 seconds - so yes it has the potential to be fast but somethings are screwing it up just now. 

But its a great distro and everything works - you can find quicker but there is a price to pay.

Ideally karmic-moblin-remix will combine the benefits of both. Moblins speed and Ubuntus flexibility.

Downloading as we speak


cimh
901 karmic

---

### Post by rusty815 on 2009-10-04
hi, this is my first post here :P

ive been using karmic beta for three days (since it came out) and at first it had a boot time of about 50 seconds, which is terrible for me as i am using an eeepc 900 and 9.04 booted in about 25s, but after a little tweaking i got the 9.10 beta to boot as fast as 9.04, which is promising, i am expecting better boot times upon release :)

---

### Post by om26er on 2009-10-05
moblinV2 is fastest in boot just 10secs but its not great. its software garage don't have even a few good softwares. then there come ubuntu moblin remix 9.10 its much faster than previous ubuntu and uses lesser ram and provides a big database of softwares to install.

---

### Post by cimh on 2009-10-05
> **cimh said:**
> 
Ideally karmic-moblin-remix will combine the benefits of both. Moblins speed and Ubuntus flexibility.


Well I was a little disappointed with UMR. Admittedly I only ran it for about 10 mins, but I came away thinking it was just moblin 2.0 in ubuntu colours.

The team stress this is a development phase.  But I'd like to see more hints as to what Ubuntu plan to do to moblin to make it more unique and flexible and therefore open it up to users who are not so interested in social networking. 


cimh
901: karmic (booting 40-50s)

---

### Post by rusty815 on 2009-10-05
i was just using UMR, i didnt like it very much, it is substantially less functional than ubuntu nbr, and i also dont like the drop down menus, and even though it said all my hardware is functional (i.e. webcam and wireless) i still couldnt connect to the internet, i guess that probably due to the fact that it is so new, but theres just nothing great about it besides its boot time.](*,)

---

### Post by Tux Aubrey on 2009-10-05
> **rusty815 said:**
> ....but theres just nothing great about it besides its boot time.](*,)

I agree - very responsive but awful!  I tried doing some hacks (replacing some of the Moblin apps with lightweight "normal" ones.  End result was a whole lot of stuff not working (like synaptic!).

I'll give this another go later.

I find that about half the "boot" time for Ubuntu (and Xubuntu)is waiting for the WM to completely load.  I'm using e17 on my (Dell) netbook and it comes up much, much faster after GDM (2 seconds).  

Personally, I no longer see any point in Xubuntu - neither the WM or the apps are "lightweight".

---

### Post by goseph on 2009-10-06
> **rusty815 said:**
> ... but after a little tweaking i got the 9.10 beta to boot as fast as 9.04, which is promising, i am expecting better boot times upon release :)

Wow, where can I learn how to tweak my remix to improve boot time?

---

### Post by rusty815 on 2009-10-06
@ goseph, for starters, you could try this:

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)

it says its for ssd's, but the tweaks described can speed up ubuntu on any hard drive, theres many more but i dont remember where i got them, or how to do them again.

---

### Post by sam-c on 2009-10-14
Wow I managed at last to install, as you can see, ubuntu 9.04 on eeepc dualboot with "vindos XP" and it is so fast,
and for first time wifi wlan working, firefox and opera, picasa from Google, Better than Sex...
What excitement.
Uncle Sam
in Ajami Jaffa Israel:popcorn:
PS. Do I need Remix??

---

### Post by haddog on 2010-04-02
Lucid Lynx is even faster! UNE 10.04.

---

### Post by goseph on 2010-04-02
Hey Haddog,

Do you have any links or info on how to set up a triple boot windows/ubuntu/OSX ? Last time I checked, it was very difficult/impossible

---

### Post by jameshock on 2010-04-10
Good OS verify that Cloud boots in seconds and offers admittance to scheme browsing, e-mail, Skype and media playback, along with a range of another applications that can be created to alluviation up with the OS. You also have the ability to alluviation into Windows or UNIX from Cloud without the requirement for a drill reboot.

---

### Post by cariboo on 2010-04-29
Right now Lucid boots in about 20 seconds on my Compaq Mini 110, when the final release comes out, I intend on doing a clean install, as I have been updating since the beta 1 release. There is a bootchart thread in the Lucid Testing & Discussion sub-form, I've seen some results where with an SSD boot times are less than 7 seconds, it looks like the average with an SSD is 9-10 seconds. Both of my desktop systems boot up in 15-16 seconds, so hopefully a clean install of UNE 10.04 will decrease my boot times.

---

### Post by mihar on 2010-05-02
I optimised my Lucid install on an ASUS eeePC 1005PE, fixed up the Boot Booster in BIOS, now i get superfast boot times, somewhere around 12 seconds.

I jotted down notes on optimisations of netbooks in general and specific 1005PE tricks on my blog, check it out here: [http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04](http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04)

---

