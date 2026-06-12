---
title: "Natty Narwhal: My personal review: Day 25"
date: 2011-05-25
forum: Testimonials &amp; Experiences
---

### Post by Barnacle on 2011-05-25
I've seen quite a bit of complaints regarding the direction Ubuntu decided to take and while some of the complaints could be valid, my experience seem to be quite different in terms of the basic. I did however run into some serious problems, but these also appear to be more related to propriety drivers. I can however appreciate the direction it is moving in, but the release schedule and process seems to be all wrong...

_**Background: Hardware & OS**_
Just to give some background. I use Ubuntu for my Desktop computer at the office and as I play around quite a bit I have installed a number of server related packages. I used to work on an old box and when the motherboard failed, I decided to upgrade. But I did not want a top of the range machine, because I run Linux. Because I know I don't need the resources Windows would need. So I went for the cheapest option at that stage available from my supplier, an Acer Extenza E264. The upgrade itself was easy and no additional installation was required. I put in the old hard drive and booted up from the old hard drive. At that stage I was running Ubuntu 8.04LTS. I also installed Ubuntu on my second laptop and with the visual changes I decided to move away from the LTS versions and to be "more up to date", so I also upgraded to the standard versions on the desktop. No problems there. 

_**Background: Software**_
As mentioned I use the desktop for work and a bit of testing. For work, I am firstly a Forensic Engineer and therefore I need software related to the work I do. I use GPS devices and download information to mapsource, which is a windows application. I also use a windows based drawing program and therefore use wine. I also use the standard OpenOffice packages and Google-Earth a lot. The same applies to photo editing (mostly resizing for reports).

In terms of the testing, I installed the standard Apache webserver, with a few subdomains and have an email server (postfix) and the usual add-ons, amavis, clamav, etc running, which means it is a fully functional web and email server too. Most of the configurations were tweaked to suit me and the setups are therefore personalised.

_**28 April 2011: Natty Narwhal arrives**_
Usually I am quite conservative (not really though :P ) when it comes to upgrades and usually I wait a month or two before upgrading. As I had some time available, I did it on the release date this time. 

_**The upgrade process**_
I did the standard upgrade process, initialised from the update manager. As I have so much varying packages installed, it is rumoured that the upgrade should break at some stage. Apparently my upgrades are immune to catastrophic failure and while the upgrade process failed to clean up old software that weren't removed properly, when I rebooted, the system functioned immediately. I had to run the system janitor a few times to properly clean up residual configs, but nothing was broken. (I have upgraded from 7.04 -----> 11.04 without a catastrophic failure)

_**Unity interface**_
Probably like most users, my initial reaction was WTF, but I decided to play around a bit to give it a proper chance. As I have certain setups that came along from the time of Noah's ark, it meant I had to try to copy those setups from previous versions. Again a bit of background. I used six workspaces on gnome, switching between them with ALT-1 to ALT-6 or by using the workspace switcher on the taskbar. I switched between applications, with the standard ALT-TAB, or by using the taskbar. I had wobbly windows enabled and a few other effects. Everything was personalised. 

Now suddenly with unity, all my personal settings were either missing, or not functioning properly. This meant I had to go to the compiz settings manager and had to change the settings, so that I could get close to my personal preferences. After much tweaking, I managed to get to basically the same setup. I enabled the desktop wall and use six workspaces. I can switch between them with my original keyboard shortcuts, or use the workspace switcher on the launcher (this is however slower than the original gnome taskbar, which means I'm using the keyboard shortcuts more often). I had to change the settings to limit the applications with the ALT-TAB switching to only the current workspace. 

The problem with many of these settings is the fact that the new "taskbar" seem to fail after every change to the compiz settings, which also means I had tty1 available most of the time to restart gdm "on demand". In the end I had quite a few extra features available too, but I'm not going into too much detail on that. The rest of the system worked normally and I had very little problems. 

_**Memory**_
This is where it become a bit more of a problem. In the process of enabling a lot of eye-candy, compiz starts to use more memory. This also means that with the amount of additional memory used, I had to upgrade the amount of memory on my desktop. With the webserver and email server open, plus mapsource, google-earth, OpenOffice, etc, etc, the memory usage was too high to my liking, so I upgraded the amount of ram to 4GB, from 2GB. I prefer my memory usage to be in the order of 50% (It is much less now), with little or no swap space being used. As I had 4GB, I had to use the PAE (Physical Address Extension) kernel and header to make use of all the memory. 

_**Problems**_
And this is where the problems started. Somehow I never really noticed that I had the NVIDIA-173 driver installed (My own memory problem?) and amazingly after the PAE kernel was installed, it sort of worked. But then I noticed the option for the NVIDIA-current driver. Big mistake! After installation I immediately had a flickering launcher and the screen froze after a minute or so. So I switched back to the NVIDIA-173 driver and it sort of worked again. I still had freezes, but not as severe. I then thought it was related to the installation procedure of the PAE kernel and first tried to remove the propriety drivers and re-install the kernel, then re-enable the drivers... ... ... ... ... ... All I had was a black screen.

I had to boot up with the Natty CD, which I had to download from another PC, then had to remove xorg.conf and when I rebooted it in any case did not have the propriety drivers installed properly. I still had to enable it through Control-Center > Additional drivers. First the NVIDIA-current - Did not work. Then back to the NVIDIA-173 and it "appeared to" work. After a day or two, however, it was freezing up again, so that I had to use tty1 every now and then to restart gdm.

We are now on day 25 and I removed the PAE kernel today to see if the problems still exist using the standard kernel headers to install the NVIDIA-173 driver (NVIDIA-current does not work). This also means I am minus 1GB of memory for now. We will now have to wait and see.

_**Summary**_
For those who complain about the fact that Unity and the launcher cannot be personalised, just look a little bit further and you WILL find that you can personalise just about everything if you look for it. I do however blame Ubuntu for not sticking to proper defaults as a basis to work from. At the same time the "launcher editor" is till under development, so why use a launcher that is not yet fully configurable.

Although I appreciate the direction Ubuntu is moving in, with the demise of Gnome 2 and the implementation of Gnome 3, I think they have done themselves a huge disservice with the release date of a product that was not yet ready for the market. The fact that Gnome 3 will be used means that there are other major changes lined up for the next distribution. Also looking at the number of updates within the first month of release, it is also clear that Natty was NOT ready for release on the specific release date. There are still too many bugs with unity, compiz and the specifically the NVIDIA propriety drivers to make it a good experience.

If you want a stable system, then stick with the LTS release. The current release is to buggy to be called stable and should in fact be called "testing", while the upcoming releases should be called "unstable", in line with the debian terms.

-----

Just some additional information:

- I don't do sudo, it is just too ghei!
- I don't use gnome-terminal, I use Eterm
- I don't use bash, I use zshell
- I only allow ssh with authorised keys, no standard passwords allowed

These things should be default too! :P

---

### Post by dreamer3kx on 2011-05-25
Very nice review man, seems like Unity is meant to be installed cleanly but most people need to go the upgrade route leading to many problems, at least I get that impression in the forums, thats not good, I myself did a clean install and everything is really stable, running great.

---

### Post by mastablasta on 2011-05-25
with so much ram perhaps a better solution would be to use 64bit OS.
 
clean install and then hunting for packages you had before? ok why th eupgrade feature if it's broken?

---

### Post by Barnacle on 2011-05-25
Just to make sure there is no confusion... I terms of the upgrade, I had very little problems and it worked properly... I actually can't understand the problems others have with upgrades, as I probably have MUCH more to upgrade than most other users. And as I've said, I've upgraded from 7.04 > 7.11 > 8.04 > 8.04LTS > 10.04 > 10.10 > 11.04 without serious problems...

In terms of the amount of RAM, it was less and I only added additional RAM after the upgrade, which means I might be looking to the 64bit version in future in any case. I know one day we will all be forced to do that update anyhow ;)

The only problems I have experience with Natty so far is actually (or probably) related to compiz and the propriety drivers. And this is specifically unpleasant for me, as I am not a compulsive rebooter... But let's wait and see what happens, as it appears that there might be some fixes in the new kernel related to the driver issues....

---

### Post by ventrical on 2011-05-25
Hi Barnacle,

Great review!! I have an AMD Acer Extensa 4420 and I have found  that at first it seems a little bit buggy with 32 bit distros , ie Fedora 14, but I was able to tame it after a while.

 I am not suggesting you use a 64 bit Natty distro. In fact, I may just try that.

  I also agree... that with a little work, Natty can become a great desktop experience.

  Pehaps Natty *was* released too soon but I admire Canonical for showing all their cards, aces and kings .. and yes, even all the 2's and 3's :)

---

### Post by Barnacle on 2011-05-26
I actually realised that I had an empty 60GB partition (it had Vista on it, so it was empty for for practical purposes :P )
So I quickly did a clean 64bit install on it (in 1 hour, including ALL the updates) for the basic install. 

But just to explain my working process a bit: 
- Install the 64bit on a clean partition/drive
- Mount the old install on a directory "olroot32/"
- Copy whatever configs I want to copy to the new partition/drive
- Keep the old install and mount the new partition on "newroot64/", when using the old install
- After the new one is finalised just rm the oldroot32/ ;)

Anyway, getting back to the point... The NVIDIA propriety driver still sucks. When I CTRL-ALT-F1 to work on tty1 and then go back to the GUI, the whole desktop is an artifact... I have to admit it installed the NVIDIA-173 driver automatically and I haven't tried the NVIDIA-current on the 64bit install yet, but that will have to wait a bit, as I have REAL LIFE &#8482; work to do.

But the point is that the good things are the same and the bad thing (nvidia) appears to be the same. But no one can really complain, as it is so easy to set up and update... If I for example, had to install a certain "other OS", it would take me a few days (up to a week) to install and setup to my liking. If I worked on ubuntu and just focused on the set up of the box, I would do EVERYTHING, including the firewalling, webserver, email server, five different CMS's for the webserver, the personalisation of the GUI, The transfer of the data from the old install to the new one, the set up of email client, install of all other software, etc... in about one workday.

---

### Post by ventrical on 2011-05-27
Yeah , yeah .. thanks .. ya know I have been at this now steady for 9 months (Ubuntu/Fedora/PCLinux) and I'm just starting to catch on. Iv'e been writing batch files in the MD-DOS environment for so long that it has been real hard for me to make the Ubuntu transition.. but I am getting it , slowly but surely.

I mean , somedays I have moments of Ubuntu brilliance .

:)

---

### Post by Barnacle on 2011-05-28
Just a quick update om the NVIDIA driver issue (NOT). It "appears as if" the NVIDIA-current driver is functioning properly on the 64bit install.  I say "appears as if", as I worked on it for only a short while. 

Because I have a lot of configurations, to transfer to the new install, I will have to switch between the two installs a bit, so I'm now back on the 32bit for now.

So, from me it's a big THUMBS-UP!  =D>

---

### Post by el_koraco on 2011-05-28
I don't use Nvidia drivers, but with ATI, the drivers you can get through jockey kinda suck. The "proper" ones, from ATI, do the trick quite nicely, with the added inconvenience of having to uninstall them and reinstall after kernel upgrades.

---

### Post by Barnacle on 2011-06-01
> **Barnacle said:**
> Just a quick update om the NVIDIA driver issue (NOT). It "appears as if" the NVIDIA-current driver is functioning properly on the 64bit install.  I say "appears as if", as I worked on it for only a short while. 

Because I have a lot of configurations, to transfer to the new install, I will have to switch between the two installs a bit, so I'm now back on the 32bit for now.

So, from me it's a big THUMBS-UP!  =D>

And "appeared as if it worked" was the correct term... Did all the webserver, email and other setups and everything is working, but compiz kept crashing with the NVIDIA-current driver... Reverted to the NVIDIA-173 driver and all is normal again...

So the only thing issue is still the NVIDIA driver/s :neutral:

---

### Post by Crempel on 2011-06-01
I did a clean 64-bit install , and the current Nvidia driver did not work, Unity was frozen , and I had to reboot. For good measure repeated this a few times, same result. With the 173 driver Unity worked fine and then all of a sudden, when selection Ubuntu in gdm it brought up "standard" gnome, and no Unity.
Also, according to /System/Adminitration/Additional Drivers, the Nvidia drivers were "activated but not currently in use", no matter whether they were working or not. By the way, I didn't touch compiz.
It's a real shame, I like Unity very much, but with this Nividia nightmare I'm about to give up.:(

---

