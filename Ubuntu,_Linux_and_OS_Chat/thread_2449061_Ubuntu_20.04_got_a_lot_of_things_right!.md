---
title: "Ubuntu 20.04 got a lot of things right!"
date: 2020-08-19
forum: Ubuntu, Linux and OS Chat
---

### Post by exploder on 2020-08-19
I recently installed Ubuntu 20.04 on my newer HP 15 laptop to try and resolve sound card issues. It turned out to be a kernel issue and I did get it resolved. I had been using Kubuntu 20.04 and I like it a lot. I passed on Gnome Shell originally thinking that it just looked dated. I tried a few distros on the laptop but Ubuntu by far has the most support and information easily available. Installing a mainline kernel was painless with the instructions available.

The new theme took me by surprise! Gnome Shell in it's default state looks like it's from the 90's. Ubuntu with it's community theme looks amazing! It's clear a lot of time and effort went into the new look! The customized dock in my opinion was a nice touch in that it retains the feel of Unity that some users liked very much. It's not all bling and no go like some other desktop environments. I have used Linux for many, many years and have always thought that default look and feel was what was holding Linux back. Ubuntu 20.04 has changed my view of Gnome Shell. The community did an outstanding job with the theme and icons.

I was not sure about snaps at first, I see both positive and negative comments. I gave the VLC snap a try after the version in the repos kept crashing. The snap version starts just as quick and works perfectly! I expected the app to take a while to start but I was willing to give it a try first rather than add a ppa. I don't know if all snaps work that well but I do like the idea of them in general and am glad they are available. Canonical seems to be addressing the issues originally associated with snaps rather quickly and I hope the technology continues to improve and become more popular.

I see a lot of newer technology in Ubuntu 20.04, snaps, improved plymouth, live patch for the kernel and a community theme that is unique and appealing. All of these things combined with the availability of support demonstrate that Canonical is headed in the right direction.

Edit: Forgot to mention the inclusion of a Wayland session! Wayland works well under Gnome Shell on two of my Intel systems. It was nice that it was included by default as an option.

---

### Post by TheFu on 2020-08-19
Using VLC as a snap, play a media file located anywhere outside of /home/, perhaps in /nfs/media/Movies/

---

### Post by mastablasta on 2020-08-19
VLC cna also do a bti of editing. you probably can't save it anywhere outside of home as well. if you can save it at all.

---

### Post by exploder on 2020-08-19
I never said snaps were perfect but if the technology continues to improve at it's current rate they could provide a competitive edge. Competing operating systems are still putting lipstick on a pig, Canonical and Redhat are developing new technology. Flatpack, snap and app images are all interesting concepts.

---

### Post by TheFu on 2020-08-19
> **exploder said:**
> Canonical and Redhat are developing new technology. Flatpack, snap and app images are all interesting concepts.

Agreed.  I love the way Wayland has been introduced.  It is optional.  
I hate the way snaps are being introduced in an LTS, before they are ready. Mandatory.

Fedora has made flatpaks so that local control is possible for the constraints.

Mandatory snaps without local controls are what will drive sophisticated users/companies away.

---

### Post by zebra2 on 2020-08-19
Lack of local control with Snaps aren't driving me away from Ubuntu but I don't use snaps. As to the OP, I use Ubuntu 20.10 with Wayland on all fo my machines.  I switch to Gnome when Unity was dropped.  It felt immature and actually childish compared to Unity at first but upped their game pretty fast. With all of the Gnome improvements in the Settings Manager it doesn't come close to CompizConfig in Unity. And especially with a 3D kernel driven compositor like Wayland on the buffet.  Also, I still use the retired system-config-printer with OEM drivers for my printer setup. I can't get a decent printout with the default print manager. I'm having no problem dual booting Windows in Legacy mode but have no use for UEFI.  I think when the time arrives and if it doesn't get fixed I will just set up a stand-alone Win Machine for my once a year Taxes and Garmin update. VM's don't get it for me and I have a lot of RAM. 
Other than that count me in as "just loving it". I agree that over all we are in a great place with the Ubuntu OS. 
PS , There is a lot of great information on this forum also.  Many of the posts here took a lot of time and effort. I especially like the Kernel thread and the Security section. You have to have a fire burning to keep things like that going.  I think I am blessed.

---

### Post by exploder on 2020-08-19
I wonder if Canonical decided to include snaps in the LTS as kind of an attraction to users migrating to Linux after support ended for Windows 7? Linux adaption has increased after all. Maybe that's stretching things a bit but how many times in the past has Linux missed the boat when things like that happen? There should be a clearer way in the software center to distinguish snaps from debs but I am sure sure that will come in time. We know what we are looking for but a new user probably wouldn't. Canonical would have been criticized if they hadn't included snaps too. I personally think they made the right choice by including them.

---

### Post by TheFu on 2020-08-19
I wouldn't know how to tell the difference in Software Center.  I've never used it.

Snaps have been around since at least 17.10.  Anyone who says they don't use snaps in 20.04 probably isn't looked. There are some core things in 20.04 that only come as snaps.  Even an Ubuntu Server install pushed a few snaps without asking.

Still, it is good that some people are happy with 20.04.  I'm not there yet. Perhaps 5-8 more months of fixes?

---

### Post by deadflowr on 2020-08-20
You can see where any package is from in the Software Store by looking at the package's Details section.

---

### Post by ajgreeny on 2020-08-20
> **TheFu said:**
> I wouldn't know how to tell the difference in Software Center.  I've never used it.

Snaps have been around since at least 17.10.  Anyone who says they don't use snaps in 20.04 probably isn't looked. There are some core things in 20.04 that only come as snaps.  Even an Ubuntu Server install pushed a few snaps without asking.

Still, it is good that some people are happy with 20.04.  I'm not there yet. Perhaps 5-8 more months of fixes?
I have never used the Software Centre/Software Store, or whatever name it uses now either; if I want a GUI for package management I go straight to synaptic as it is probably the easiest with which to search for packages.

You may be correct about snaps, ie they make up some of the core things in Ubuntu 20.04 but the snaps in some of the other flavours, eg Xubuntu which I use, are the snap management packages only such as snapd, snap-store, core18, and two versions of gnome, all of which I removed along with chromium after finding that it would not save any files where I wanted them; everything had to be saved in Downloads, not necessarily where I wanted.  I still use chromium but mine is now is from the PPA at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev).
If I wanted a snap now I could only install it by adding back the whole snap infrastructure, but I have realised I do not need nor want any snaps so unless things change, I am and will remain, totally snap free.

I have to warn anyone using default Ubuntu with the gnome desktop that their success removing all snaps could be totally different from mine with Xubuntu; maybe Ubuntu with gnome has a need for some of those snap packages that I removed but having used Ubuntu only for a very short time as a virtual install in Virtualbox, I am unable to say if removal of the snaps would cause problems of any sort.

---

### Post by monkeybrain20122 on 2020-08-20
> **TheFu said:**
> I wouldn't know how to tell the difference in Software Center.  I've never used it.

 There are some core things in 20.04 that only come as snaps.


Not sure what you mean by core things. I removed all snaps by purging snapd (it will remove all snap packages), nothing bad happened. I am running unity but I logged into gnome shell just to see if anything was broken and everything seemed fine. I also disabled tracker (which is a gnome shell thing I think) and nothing bad happened but now cpu is not running at 100% all the time and slowing things down.

Personally I prefer flatpak for things where I can't find in the standard repo because of local access control (and it doesn't mount a bunch of volumes)

---

### Post by TheFu on 2020-08-20
Just so I'm clear - of the 10,000 things that I use different Ubuntu system to accomplish, there are probably less than 100 issues that make me sad. Sure, I complain about bloated GUIs, systemd, pulse-audio, snaps, network configurations, name resolution, and solutions forced onto us for problems we never had.  Wish Canonical didn't have Ubuntu Core (embedded OS) locked down so much. I'll never, ever, deploy using it because it requires registration and Canonical demands to be in the middle. This turns me off about the snap store too.  Canonical should have made a F/LOSS reference implementation first, then created theirs with all the extra tracking and security mandates. Deploying to an internal snap store would be a good thing inside many enterprises, but they won't touch Canonical's setup and uncontrolled updates.

There are some really great things too.  LXD is pretty great - would be better without mandating snap packaging.  ZFS - oh boy!  Can't wait for that to be solid for any use. virsh/virt-manager + KVM are totally awesome.  All those little updates for thousands of packages with each release that don't get screwed - that is freakin' amazing.  I'm not big on using raspberry pi HW for general purpose stuff, but lots of other people get introduced to Ubuntu in that way. 

For me, Ubuntu almost always gets the right mix of new, but stable.  Long enough support, but not so long that change is deadly. 5 yrs between OS migrations is almost too long for a system that needs to be maintained the next 30 yrs.  Somewhere after 5 yrs, a system that "just works" becomes a "never, ever, touch" system by management.  There are still RHEL v5 systems running that way. All are a danger to the network they are on.  Getting 4+ yrs from an OS line an excellent compromise.

Now, if canonical will only make LXD in a non-snap package. That would really be nice. ;)  And don't force ZFS to be used so hard in LXD. Better LVM support would be appreciated.

---

### Post by exploder on 2020-08-21
The only problem I have had in my daily use was with the repo version of VLC, that wasn't a big deal to fix for my use case. I did find a small bug with the dash and mounted volumes under wayland, it also was very easy to work around. Both my desktop and laptop were running Windows 10. I am using public WiFi since the pandemic cost me my job and my divorce... It took hours on end to update Windows, if the updates ever actually installed and there was massive breakage with the May update. I had tried KDE Neon and Kubuntu originally but Ubuntu had more support when I had hardware issues with the new laptop.

For whatever reason I get a better WiFi signal under Ubuntu. I know I could have just installed the mainline kernel in Kubuntu but then I stated considering that Ubuntu has 5 years of support, massive amount of support documents all over the web and why not give it a try? I had no idea the new theme was so good or that it could look so modern with just a small amount of personalizing. I do pretty basic things with my computers right now and Ubuntu does them all well. I really want to stay with something, it's challenging downloading iso's over pubic WiFi, torrents are great!

I still have Kubuntu on my son's desktop, it has been problem free on his hardware. Kubuntu uses less resources and he has a dedicated graphics card. I have Intel graphics on both my machines and wayland seems to make my hardware work a little better. KDE appears to utilize the graphics card more, Ubuntu seems to utilize memory more. All our computers have 8 GB of RAM so memory use is not an issue. All have SSD's so performance is excellent. Ubuntu scaled well on the 15.6" screen of the new laptop, better than anything else I tried.

I rediscovered gnome extensions and I actually like how I can custom tailor the system with them. The disconnect WiFi extension helps using public WiFi when it drops my connection, impatience perks the animations up and let's face it, extensions are pretty cool! The default Gnome Shell menu works great on the smaller laptop screen and it's way better that the one in Windows 10 for sure! Use Chrome OS and Windows 10 for a year and you will certainly appreciate Ubuntu 20.04 a heck of a lot more!

It was a bold move in my opinion to include snaps in an LTS the way Canonical did but the greater the risk the greater the reward. Snaps, flat packs and app-images all have their advantages and disadvantages. Canonical was quick to jump on the technology and they appear to be improving on it at a good rate. I personally would like to see them succeed with their interpretation of these types of packages. Canonical at least tries new things, good or bad at least they give it their best shot. Canonical is noticed for the right these these days.

---

### Post by TheFu on 2020-08-21
> **exploder said:**
>  
It was a bold move in my opinion to include snaps in an LTS the way Canonical did but the greater the risk the greater the reward. Snaps, flat packs and app-images all have their advantages and disadvantages. Canonical was quick to jump on the technology and they appear to be improving on it at a good rate. I personally would like to see them succeed with their interpretation of these types of packages. Canonical at least tries new things, good or bad at least they give it their best shot. Canonical is noticed for the right these these days.

There's a fine line between bold and foolish.  Which side is often up for debate.

Fedora tries lots of new things too. That's the point of that release. But they leave a way out of the new stuff. Wayland on Ubuntu has a way out too.

---

### Post by maglin2 on 2020-08-22
> **exploder said:**
> KDE appears to utilize the graphics card more, Ubuntu seems to utilize memory more. 

I'd thought Ubuntu was a lot heavier on memory than kubuntu - one of the reasons I switched to kubuntu on my old laptop (4 Gig RAM).

I now wonder if this may be in part a function of the way their respective GUI tools measure memory.

Running an ubuntu wayland session with ksysguard also installed and no other apps open these are the simultaneous outputs from gnome system monitor, ksysguard and top (in terminal):

GSM 1.0 Gig

KSYS 0.58 Gig

TOP 0.67 Gig

On kubuntu ksysguard typically shows about 0.44 Gig with no apps open (increasing slowly with session length to about 0.55 Gig).

I don't claim any rigour for this, but it does seem to suggest that if you are comparing kubuntu RAM use on ksysguard with Ubuntu RAM use on gnome system monitor you aren't really comparing like with like.

---

### Post by exploder on 2020-08-22
@ Maglin2

You brought up an interesting point. The comparison you make supports it. As I recall, system information also varies in it's display of memory use too in KDE. I am going to have to look at my son's Kubuntu desktop and compare now. Thank you for your input!

---

### Post by mastablasta on 2020-08-25
they should have made snaps more like portable apps, where you would update the apps either through their portable app manager or individual apps would offer the update option. that way you can always turn off updates if needed or leave them on and have the apps updated.

they should not push snapd so much. if solution is good, people will pull anyway.

---

### Post by lammert-nijhof on 2020-09-07
You did forget to mention, that Ubuntu can be installed on ZFS. I now use it on all my PCs, simply because it protects my files against the frequent power fails in my country of residence. Backing-up the system and snapshots are that fast and elegant! I delete zsys after install, because that specific Ubuntu add-on is useless and causes more issues than it  solves. 

I appreciate Gnome and I use it for my Virtualbox Host OS, because of the great way they deal with workspaces. Gnome is the flavour, that takes the longest time to boot from a Silicon Power nvme-SSD (3200/2300 MB/s) in a Ryzen 3 2200G. My Ubuntu 20.04 VM boots in ~13 seconds, while my Xubuntu 20.04 VM boots in ~7 seconds. Most flavours boot in ~10 seconds:)  Boot times of Gnome still could use some improvement, being twice the boot time of Xubuntu or Ubuntu Cinnamon.

---

### Post by aaronrv2008 on 2020-09-27
Even through Ubuntu 20.04 is very stable and works great, I still prefer Kubuntu as it's very stable.

---

### Post by exploder on 2020-09-28
> 

    Even through Ubuntu 20.04 is very stable and works great, I still prefer Kubuntu as it's very stable. 



I started out this release with Kubuntu 20.04, still have it on my son's computer. To be perfectly honest, I started looking at Ubuntu 20.04 after seeing the new theme. I had always thought Gnome Shell looked old and dated but it looks great in Ubuntu now! I briefly tried Ubuntu Budgie on my new laptop but it did not scale well at all on it's 15.6" display. Ubuntu for me at least had everything I was looking for! TheFu is right, it is a little bloated but what isn't these days? Gnome Shell has gotten pretty nice over time, it's simple yet very functional. The new theme is the best out of the box I have ever seen. I don't like spending hours customizing and I like the few customization's Ubuntu provides.

I know that you can make any Linux distro look any way you want but the community did an outstanding job. I know it took awhile but the hard work in my opinion has really paid off! I used to ask my stepdad why he never used KDE, he said it looked too much like Windows. I ran Windows 10 for about a year and I have to admit I saw his point of view more after that. Some of my friends share this point of view too, it surprised me! In my opinion, if it looks like Windows, people expect it to work like Windows and it doesn't. People instantly know Ubuntu is not like Windows and they just except that they are learning something new. This is just my opinion, feel free to disagree if you like.

I always give new user's a choice between Linux Mint and Ubuntu, they always choose Ubuntu! Canonical I think without even trying got the right combination this time around, the right look and feel, ease of use and ease of maintenance. Ubuntu is criticized some over snaps but it does address the issue of people wanting newer versions of software. It's not a perfect solution just yet but it is a step in the right direction. I guess I see the glass as half full instead of half empty with this release!

---

### Post by mastablasta on 2020-09-29
> **exploder said:**
> 
I know that you can make any Linux distro look any way you want but the community did an outstanding job. I know it took awhile but the hard work in my opinion has really paid off! I used to ask my stepdad why he never used KDE, he said it looked too much like Windows. I ran Windows 10 for about a year and I have to admit I saw his point of view more after that. Some of my friends share this point of view too, it surprised me! In my opinion, if it looks like Windows, people expect it to work like Windows and it doesn't. People instantly know Ubuntu is not like Windows and they just except that they are learning something new. This is just my opinion, feel free to disagree if you like.


on the other hand, people have easier time to switch. we put KDE on my father's computer as an introduction to Linux and left him there with it. we also gave a promise that if he couldn't find anything he needed, we would buy and install windows for him. that was i think in 2012. he is still on KDE.

the menu on the side has nothing to do with windows 10. it's the GUI options available to users. everything is in GUI. that the philosophy behind it. on the other hand through time windows took some design features from KDE GUI and vice versa. so they do have some similarities. 

windows 10 GUI has some major GUI issues such as hiding settings from users (this is a Gnome feature) and advertisments in the menu. none of these are present in KDE. Menu in windows 10 is also horrible. i can never find anything there. at the same time it has some interesting features such as tasks check, cortana, the file manager is now quite descent... mostly the OS should not be noticed by user. windows is relatively unnoticed (until you have to do the updates). KDE as well. i can't say there are OS or major desktop issues. sure i had a few when setting up the PC, but once i set it (and all was done via GUI) it runs well.
on the other hand KDE was the first of GPU accelerated desktops that offered to turn off the desktop effects when user was running apps full screen.

---

