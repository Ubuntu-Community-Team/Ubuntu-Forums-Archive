---
title: "HDD Space:  KDE Approach vs GNOME Approach."
date: 2012-01-16
forum: The Cafe
---

### Post by StephanG on 2012-01-16
ey guys,

I've recently been thinking about the different approaches behind KDE and Gnome.  With KDE using underlying infrastructure like phonon, while Gnome writes the complete functionalty into each of their apps.

Now, don't get me wrong, this post has NOTHING to do with the quality of the software, as that's a lot harder to judge, with some people prefering simplicity, and other features, and some experience serious bugs, while others don't.

But, what I am curious about, is that there seems to be a general conscensus that KDE's method results in them being able to put more programs and functionality into their software without using too much more hard drive space.  But, Gnome also shares its libraries with it's apps.  So, I wondered... How much of a difference does KDE's approach make?  Is it enough to justify the massive amount of libraries that non-KDE users would have to install to use something like Amarok?

So, what I did, was just to make a list of what functionality is included by DEFAULT on both the Ubuntu, and Kubuntu CDs.  The idea is to see if KDE provides significantly more functionality for the same storage space.

APPS/FEATURES THAT BOTH UBUNTU & KUBUNTU PROVIDE
(Apps with significantly more features than their Gnome/KDE counterpart marked with a "+")
  - Web Browser (+Firefox/Rekonq)
  - Email Client (Thunderbird/Kontact)
  - Music Player (Banshee/+Amarok)
  - Video Player (Totem/Dragon)
  - Libre Office
  - Package Manager (Did Ubuntu 11.10 ship with Synaptic, can't seem to remember if I installed it or if it was always there)
  - Software Center (+Ubuntu SC/Muon SC)
  - Calculator
  - Torrent Client (Transmission/+Ktorrent)
  - Disc Burning Application (Brasero/+K3B)
  - File Manager (Nautilus/+Dolphin)
  - Terminal
  - System Monitor
  - Instant Messenger (Empathy/Kopete)
  - Compression App (Archive Manager/Ark)
  - Solitaire
  - Virtual Keyboard (Onboard/Kvkbd)
  - Password Manager
  - Printer Setup/Settings
  - Image/Document Viever
  - Photo Manager (Shotwell/?What do you guys think, does Okular/Gwenview count?)
  - Screenshot App (Screenshot/KSnapshot)
  - Text Editor (Gedit/Kate)
  - Partition Editor (GParted/KDE-Parition Manager)  *Can't remember if I had to install either one or both.*
  - System Settings (Gnome SS/+KDE SS)
  - RSS Feed Reader (Part of Thunderbid/Akregator (Part of Kontact))
  - Bluetooth Management

Ubuntu = 2 '+'ses.
Kubuntu = 3 '+'ses.

APPS IN KUBUNTU THAT DON"T HAVE COUNTERPARTS IN UBUNTU
(Significant inclusions marked with "+" or "++")
  - IRC Client (Quassel)
  - KInfoCenter (What is the Gnome equivalent?)
 ++ Desktop Indexing (Nepomuk/Strigi)
  - KNotes
 ++ Widgets
      - Also includes +/- 30 widgets that do various tiny things like monitor CPU. (Too lazy too count)
  + Activities
  - Window Tabbing
  - Window Tiling
Total = 9 features that are not in Ubuntu of which 3 are significantly large. (Widget Functionality and indicidual widgets counted seperately.)

APPS IN UBUNTU THAT DO NOT HAVE COUNTERPARTS IN KUBUNTU.
(Significant inclusions size-wise marked with "+" or "++")
  - Gwibber
  - Disk Usage Analyzer
  + Cloud, UbuntuONE
  - Games
      - GBrainy
      - Mahjongg
      - Mines
      - Sudoku
 + Backup Utility
++ Several Wallpapers

Total = 9 features/apps not found in kubuntu, of which 3 are significantly large)


CONCLUSION:  So, KDE makes extensive use of common libraries, but it seems that the difference between a default install of Ubuntu and Kubuntu are fairly similar as far as features and apps goes.  But, I would like to mention that this quick little comparison did NOT take quality into account.  It is a bit of an insult to compare Firefox with Rekonq with rekonq for example.  But, the subjective "good vs bad" apps was a can of worms I didn't want to open right now.

It should also be noted, that the default install of both are fairly limited and that results may become more (or less) prominent as one goes about installing various apps like Krita, Gimp, Digikam, F-Spot, etc.

But, it looks to me, that the main gain in using common app infrastructure like Phonon is does not lie in saving HDD space. And, presumably RAM.  So, that would probably mean that the chief gain is in the integration between apps.

LASTLY:  What do you guys think?  Did I miss any obvious features or apps?  And do you think it's fair for me to completely disregard the quality of the apps?

---

### Post by koleoptero on 2012-01-16
You forget development. It's much easier to maintain an app that uses backends than an app that has everything hard-coded. In linux it's not all about the user, and most of the times it's almost all about the developer.

Also you're comparing ubuntu/kubuntu apps and not gnome/kde apps up there. Firefox is not a gnome app. Get your facts straight.

---

### Post by Supermouse on 2012-01-16
Also, it's not fair comparing the best music player in the whole world with Banshee.

---

### Post by StephanG on 2012-01-16
> You forget development. It's much easier to maintain an app that uses backends than an app that has everything hard-coded. In linux it's not all about the user, and most of the times it's almost all about the developer.

Also you're comparing ubuntu/kubuntu apps and not gnome/kde apps up there. Firefox is not a gnome app. Get your facts straight.

Yes, I am aware that Firefox is not a Gnome app, but comparing Kubuntu and Ubuntu was the easiest thing to do since they both take up almost exactly the same space.

But, the entire argument was about how much space you could potentially save using combined infrastructure, and the fact is that Firefox takes up CD space, and therefore impacts the results, so I couldn't just ignore it.  And if I removed it from the comparison and replaced it with Epiphany, I would have to recalculate the Ubuntu iso's size, and somehow have to factor that into the comparison, which sounds like a lot of work...

> Also, it's not fair comparing the best music player in the whole world with Banshee.

The idea of giving "+" symbols to more feature rich apps was not to show better/worse apps, it was merely to remind readers that there are extra features in these apps, which could take up extra space and skew the comparison.

---

### Post by Copper Bezel on 2012-01-16
Just so you know, GParted and Synaptic aren't included in the default install. (Strangely, GParted is used by the installer but isn't installed itself.)

And no, I don't think you can really disregard quality or complexity. If gedit and Kate have exactly the same number of lines of code, but Kate depends on a large external library, then there are still at least two possibilities - Kate could be inefficiently coded, or it could be more feature-rich. I don't think sheer kbs tell us much (and I don't think the +s fully account for the nuances.)

---

### Post by BrokenKingpin on 2012-01-16
This day in age hard drive space doesn't really factor in for me. I think it has a bigger impact on how applications communicate with each other, and how it affects the development process.

For me personally, I like applications that are more standalone, and don't need other components and backends. This makes it easier to switch out applications and keeps things more simplistic.

---

### Post by StephanG on 2012-01-17
> This day in age hard drive space doesn't really factor in for me. I think it has a bigger impact on how applications communicate with each other, and how it affects the development process.

For me personally, I like applications that are more standalone, and don't need other components and backends. This makes it easier to switch out applications and keeps things more simplistic.

Agreed.

The main reason for this comparison, was because I put a monitor for the reading/writing on my HDDs.  The thing I noticed, is that even apps like Gimp and Blender don't really access the HDDs when doing intensive tasks.  I can only assume this means that all the libraries, even ones such as blurring filters seem to get loaded when the app opens.

That put me on an interesting thought track, because I started pondering if the amount of HDD space an app uses could almost exactly predict the kind of space it would take up in the RAM.

And the reason I posted it, was because I was kind of shocked at the small difference.  I thought it would be much larger, because on my Ubuntu machine, it feels like I'm forever having to install additional software to do even simple task like formatting a USB.

But, now I'm starting to think that maybe it's just because I'm so used to installing that software on Kubuntu that I don't notice that I'm doing it anymore...

---

