---
title: "Your Preferred Package Manager"
date: 2012-08-31
forum: The Cafe
---

### Post by Ubun2to on 2012-08-31
Today I was booting a VM, when VirtualBox notified me that there was an update available.
So, I downloaded the file, went to open it, and I got the reply "The Ubuntu Software Center has unexpectedly closed". Seems this happens every time I try to open a .deb file without having already launched the Software Center sometime after I turned on my computer.
I have GDebi and Synaptic on my computer (GDebi is great for installing packages that the Software Center won't work with due to being "incomplete"; Synaptic for multi-package installs), and I use both of them frequently.
So, what is your primary package manager? Do you stick with the Software Center? Or do you use an application like Synaptic? How about a combination of both?
I prefer the Software Center for looking at apps and deciding which ones I want (and installing .deb files I find online), and Synaptic for installing the packages I found in the Software Center.

---

### Post by nativehound on 2012-08-31
I like 

```
aptitude
```

Best there is.

---

### Post by Jakin on 2012-08-31
Synaptic preferred, but its just there incase, i mostly terminal apt install and update everything.

I do have Software Center for those boring days.. When i want to just look through a convenient catalogue to try something new- that i might never have aware of, had it not been for such a neat app.

---

### Post by mips on 2012-08-31
pacman

---

### Post by sffvba[e0rt on 2012-08-31
apt-get has super cow powers.


404

---

### Post by wojox on 2012-08-31
```
sudo dpkg -i <application.deb>
```

---

### Post by vasa1 on 2012-08-31
> **mips said:**
> pacman
On Xubuntu?

---

### Post by Mikeb85 on 2012-08-31
Zypper...

---

### Post by mips on 2012-08-31
> **vasa1 said:**
> On Xubuntu?

On Arch.

pacman as far as I'm aware is available for debian but does not integrate well.

---

### Post by mamamia88 on 2012-08-31
I like both pacman and apt.  Wish pacman would use pacman -i to installl package rather than pacman -S to install a package since it makes more sense.  pacman is also easier to spell than aptitude which i always mess up somehow.   Other than that it's pretty much all the same to me.  Pacman seems a little faster but honestly who really cares as long as it works?

---

### Post by johnnybgoode83 on 2012-08-31
Synaptic and apt-get install

---

### Post by Primefalcon on 2012-08-31
My fav gui is synaptic, though I usually just use the CLI.... tbh one of the first things I remove is the update manager.......

I have a script that runs updates as I shut my system down anyhow... so.... update manager is kinda pointless to me

---

### Post by lykwydchykyn on 2012-08-31
> **nativehound said:**
> I like 

```
aptitude
```

Best there is.

Me too!  Hope they get the multiarch issues worked out so I can use it on 64 bit again.

---

### Post by vexorian on 2012-08-31
I use apt-get when installing small things. It is fast.

For installing things that take long to download. Or when uninstalling packages or managing repos, I prefer Synaptic.

Although what I do lately is use synaptic to generate a list of package URLs to download (inderectly, by using its download script generator) and then take the list to jdownloader. It allows me to pause download and control the download speed). Then I put redirects of the downloaded packages to /var/cache/apt/archives

---

### Post by oldos2er on 2012-08-31
apt-get

---

### Post by uhgreen on 2012-08-31
pacman and portage.

pacman is, obviously, faster but portage is great because of customization and options.

---

### Post by Lucradia on 2012-08-31
Aptitude / Apt-Get

Synaptic, that's all.

---

### Post by KiwiNZ on 2012-08-31
Software Centre, simple, quick and no messing around.

---

### Post by vexorian on 2012-08-31
And might freeze or crash while installing.

---

### Post by Mikeb85 on 2012-08-31
> **vexorian said:**
> And might freeze or crash while installing.

+1

I love the fact they make it so easy to buy software, but it's so slow and buggy it makes me angry every time I use it....

---

### Post by njwarrior on 2012-08-31
I find aptitude to be the best method. Definitely prefer it over software center or synaptic.

---

### Post by josephmills on 2012-08-31
```
dpkg
```

---

### Post by MadmanRB on 2012-08-31
Synaptic though Muon is growing on me.

---

### Post by Gone fishing on 2012-08-31
I seem to use lots of them!

Software centre usually its nice to browse and see what's available. I don't like the lack of information about progress perhaps a button or a keystroke to open a teminal so you could see the progress would be nice. dpkg for installing single deb files, which I try to avoid much better to use a proper repository and apt-get to install packages I know, simply and quickly.

For being geeky the ports system in FreeBSD takes some beating.

---

### Post by Linuxratty on 2012-09-01
Synaptic for me.

---

### Post by malspa on 2012-09-01
Synaptic, and apt-get.

---

### Post by pqwoerituytrueiwoq on 2012-09-01
synaptic
i set my .debs to open in GDebi
apt-get

---

### Post by effenberg0x0 on 2012-09-01
> **not found said:**
> apt-get has super cow powers.


404

But it has no elephant being eaten by a snake:
```
aptitude -vvvvvvv moo

```
:)

Regards,
Effenberg

---

### Post by mamamia88 on 2012-09-01
isn't synaptic just a front end for aptitude? when i was using ubuntu i found the software center too slow on my machine.  so unless i didn't know the name of the program i wanted to install and i had to search by description i would avoid it at all costs.   i would only use synaptic if i didn't know the exact package name.   now i do the same thing with arch i just don't need a front end i just use [http://www.archlinux.org/packages/](http://www.archlinux.org/packages/) as a replacement for synaptic and when i find one i want to install i just pacman -S nameofpackage

---

### Post by malspa on 2012-09-01
> **mamamia88 said:**
> isn't synaptic just a front end for aptitude?

Front-end for apt.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[http://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](http://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

---

### Post by vexorian on 2012-09-01
They need to update synaptic so that it can run without root. Let it request root only when installing/uninstalling packages or modifying repository list.

Right now, since you have to run in root, it can't, for example, use the global menu, and has issues with local GTK themes.

---

### Post by malspa on 2012-09-01
You can actually run Synaptic as a normal user, although you can't install anything or modify the repositories. I just started it in Debian Squeeze from the command line:

```
$ /usr/sbin/synaptic
```

---

### Post by ratcheer on 2012-09-01
I also prefer aptitude, but I hear it has a some problem with Ubuntu 12.04 and higher, so now I use apt.

Tim

---

### Post by forrestcupp on 2012-09-01
Let's not forget that most of what people are talking about aren't actually package managers. The two biggest package managers are apt and rpm. Things like Synaptic, Software Center, Aptitude, Yum, and even apt-get are all front-ends to the actual package manager. Pacman is an actual package manager, though.

> **mamamia88 said:**
> I like both pacman and apt.  Wish pacman would use pacman -i to installl package rather than pacman -S to install a package since it makes more sense.  pacman is also easier to spell than aptitude which i always mess up somehow.   Other than that it's pretty much all the same to me.  Pacman seems a little faster but honestly who really cares as long as it works?

I saw someone once who created a script named "pacman", and it took whatever arguments you pass to it to convert it to an apt-get command. I thought that was interesting for people who are coming from using pacman.

---

### Post by smellyman on 2012-09-01
pacman/yaourt

---

### Post by mamamia88 on 2012-09-01
> **forrestcupp said:**
> Let's not forget that most of what people are talking about aren't actually package managers. The two biggest package managers are apt and rpm. Things like Synaptic, Software Center, Aptitude, Yum, and even apt-get are all front-ends to the actual package manager. Pacman is an actual package manager, though.



I saw someone once who created a script named "pacman", and it took whatever arguments you pass to it to convert it to an apt-get command. I thought that was interesting for people who are coming from using pacman.

wonder if they have something that is the opposite of that.

---

### Post by forrestcupp on 2012-09-03
> **mamamia88 said:**
> wonder if they have something that is the opposite of that.

I'm sure if you were using Arch, it wouldn't be very hard to create a script called "apt-get" that can use your apt-get arguments to execute a pacman command.

---

### Post by OrangeCrate on 2012-09-03
Though I've tried rpm based distros over the years, I started with apt, and I prefer it for day-to-day use. Synaptic is my favorite front end, but, I use apt-get in the terminal just as often, I guess.

---

### Post by mamamia88 on 2012-09-03
> **OrangeCrate said:**
> Though I've tried rpm based distros over the years, I started with apt, and I prefer it for day-to-day use. Synaptic is my favorite front end, but, I use apt-get in the terminal just as often, I guess.

yeah no point launching a gui just to install a package

---

