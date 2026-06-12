---
title: "My Ubuntu Story"
date: 2006-11-01
forum: Testimonials &amp; Experiences
---

### Post by ericinwisconsin on 2006-11-01
First let me say that I'm by no means a newbie to computers or Linux. My first distro was Redhat 5.1 and I've tried a variety of distributions over the years. I walked away from Linux as a desktop when I got married, but still used it every day on my web server. Lately, with Windows about to launch a new version, I decided to see if my family could be weened off of Microsoft and onto something without MS's annoying registration system. I tried Mandriva, Fedora, MEPIS, Freespire, and lastly SuSE.

I got fed up with SuSE 10.1.

I managed to get my wireless network card to work (although it tended to lose the route to the router sometimes), but became frustrated with continual lockups every time I had to reboot the router. My family wasn’t happy with it, either. So I decided to download Ubuntu Linux and see what all the fuss is about.


I picked the perfect time to do it. Ubuntu 6.10 had just been released, with (it says) a lot of security fixes and updates from 6.06. Perfect… as long as it’s stable.

Ubuntu comes on a single CD. It’s a live distro with the option of installing from the desktop. I much prefer this technique because I can do a quick scope of the system and see what does and doesn’t work. I found that Ubuntu immediately located and configured my wireless card (50 points for that). All I had to do was configure it to log into my network. The default desktop was Gnome (which I’ve learned to hate more and more as it has matured; looks too much like the Mac OS), but I figured I could add KDE if I chose to install it. So I hit the “install” icon and held my breathe.

The install was fairly smooth, although it wouldn’t let me configure the partiions to please me. I generally perfer a 100 Meg ext3 partition (for /boot), followed by a swap partition, and finally the remainder of the hard drive (for /). While Ubuntu would allow me to create the partitions to suit me, it wouldn’t allow me to name them. Thus, I ended up with a swap partition and the remainder of the drive was one, big ext3 partition. Not my favorite way of doing things, but ok.

It also wanted me to create an account for myself during install. It didn’t ask me for a root password, so I assumed that like MEPIS, Ubuntu would assign my account admin functions, but lock down the root account. I hate that, but decided to forge ahead and see if I could change it later.

It came up with the gdm interface to log in, and I hate that, too. Ubuntu seemed to be racking up a lot of complaints already. I was committed at this point, so nothing to do but log in. I knew that Ubuntu defaulted to the Gnome desktop, so I wasn’t too disappointed when I saw the same, Mac-like desktop appear. I found that my wireless card was still configured. (Did Ubuntu remember the config when it was installing? Must have.)

After a quick look around, I found the Synapsis software manager and started to feel better. I liked Synapsis on MEPIS, so I was happy to see the sheer number of packages available for Ubuntu. KDE was there, so I immediately started downloading and installing it. Not a single hiccup.

Next, I switched to the KDE desktop. I remember an old distro of Redhat I once had. At the time, Redhat was insistent that everyone use Gnome and I had a devil of a time trying to add and configure KDE. The KDE desktop Ubuntu showed me looked great out of the box. I changed it to suit me, then I changed things to allow root to log in to the desktop. Next, I checked to see if my NTFS hard drive had mounted and it did! Score a BIG one for this Linux distro!

Ubuntu turned out to be totally configurable. It found my hardware without a hitch and is flexible to a fault. I may be in love.

---

### Post by taurus on 2006-11-01
If you want more control over the partition process, you should use the alternate CD to install it.  

I assume you know that there is Kubuntu CD and the default desktop top is KDE.  So, you don't have to worry about seeing or running Gnome at all...

[http://www.kubuntu.org/](http://www.kubuntu.org/)

Yes, the root account is disable so if you need to do something as root, you can use the sudo command.  And if you really need to become root, then you can assign a password for it with

```
sudo password root
```
And welcome to Ubuntu...  ;) 

p.s.  Will move this thread over to Testimonials then.

---

### Post by Ben Sprinkle on 2006-11-01
```
I found the Synapsis software manager and started to feel better.
```
Synaptic mate. :)

```

It also wanted me to create an account for myself during install. It didn&#8217;t ask me for a root password, so I assumed that like MEPIS, Ubuntu would assign my account admin functions, but lock down the root account.

```
Disables root login because you might f up your system. You can do:
```

sudo su
```
And type your current password to be root.

---

### Post by ericinwisconsin on 2006-11-01
Thank you for the info, guys.

I already did a sudo to change my root password and configured Ubuntu to allow root login. I don't log in as root unless I HAVE to, so I'm not likely to screw things up. It's just nice to be able to do some things graphically.

I knew about Kubuntu but didn't check to see if it was also recently upgraded to match version 6.10. Also, I wanted to see what I could and couldn't do, so I chose the one with Gnome as the default desktop to see how easy it would be to add KDE. You never know. My wife or one of my stepkids might like Gnome better. KDE is just my personal preference.

---

### Post by rvickers on 2006-11-16
I've been in the computer business for 40 years (63), mainframes, pc junior, dos, windows 3.1 and the start of Linux. I've said all along that until Linux  comes up with a friendly desktop, it's not going to compete with window$. I've tried Linux off and on since it's inception and Ubuntu is the first distro that I see as a serious threat to Window$, even with it's wireless issues. Good job guys!:)

---

