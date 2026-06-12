---
title: "Kubuntu 9.10 - first thoughts"
date: 2010-02-02
forum: Testimonials &amp; Experiences
---

### Post by jward3010 on 2010-02-02
I'll cut a long story short, I'm writing this post because of the amount of grief I had with Kubuntu 9.10. I'm a seasoned Gnome Ubuntu user. I have been using it right up to Karmic and I'm well acquainted with it's interface and foibles, which are rarely a big deal.

The problems I ran into in Kubuntu we're only overcome thanks to my previous experience with earlier Kubuntu's. Most newcomers to Linux and Kubuntu would be flummoxed and frustrated by a lot of the issues I faced, and hence might be completely switched off. I want to stress that they are interface issues, not hardware.

Here's what I ran into with Kubuntu.

**Installation**
Installation was a fine part of it all, so a good beginning. It was easy, clear, basically Ubiquity for Kubuntu which is a good installer. Around then I knew hardware seemed to be working with Kubuntu.

**First use and wireless**
I now had an installed system. Desktop performance seemed to be good, unlike previous releases. I decided to join a wireless network. Good news was my wireless card worked, no additional grief involved - but the amount of dialogs I went through to get joined up was ridiculous - I guessed the icon, select "Connect to other network" (not obvious), pick network, it offered me which security to pick, why didn't it know, popped in the key - OK - KDE Wallet - 5 choices - finally connection. Gnome is way more efficient. On another note I didn't notice any updates being recommended.

**Would you like CODECS - yes, but...**
Soon after, a dialog popped up about additional restricted software to install (DVD playback, MP3 codecs etc.). I thought, this is even better than Ubuntu, you have to search for this stuff. I accepted installation and it quickly told me packages we're already installed - which later I learnt they weren't.

**Going Online and easy Firefox**
Next was trying out internet, I fired up Konqueror and went to my favourite place - GMail.com. Everyone knows the story - Knoqueror is not compatible with Gmail somehow and still isn't and they recommended me to use another browser. Well my favourite is Firefox and I heard about the included install link in the "Internet" menu. Went there and tried it - "packages already installed" - But of course they weren't.

**Where are the updates?**
I decided there had to be updates to do and they'd probably help the problems I was having as fixes usually fix problems. I went looking in the menu's and I finally decided on System Settings and Add / Remove Software where I found it - not obvious to a newcomer, and once again surprised that I didn't see this stuff automatically on startup - even after 5 minutes. Checking for updates and installing wasn't difficult although having an "Install updates" instead of "apply" button would be more logical. After updating the codecs and Firefox installers worked flawlessly but, once again this could throw a new user.

**Top Widget bar**
When I maximised a Konqueror window I found that it wouldn't maximise to the top of the screen area. About 20 to 25 pixels were reserved by some widget tool at the top left of the screen. It did nothing as far as I could see. I could reduce it to gain back about 10 pixels but that's all. An advantage of the KDE desktop over Gnome is the lack of a top panel which grants you extra screen space, always appreciated on 1280 X 800 laptop screens especially for fattish browsers like Firefox. This is now gone again because of this widget requirement.

**Overall**
What I have found is that a lot of work has gone into the interface of KDE 4.3.5. it looks slick and cool, it's colours match nicely, the grey might be a tad boring but it's obvious that the desktop and plasma have had a lot of work put in. This is a pity as I still find the basic functionality missing; connecting wirelessly is arduous and complicated, the first popup installers don't work (codecs and Firefox), updates have to be found and don't make themselves known, and the K menu (application launcher) is difficult and slow to use - many clicks to get anywhere. Konqueror's lack of compatibility with GMail (and maybe other popular sites) will be another punch in the stomach.

What has improved is hardware compatibility and general performance. The desktop was zippy and quick for a visually appealing design and browser scrolling wasn't a big deal, then again I was using it on a high performance laptop (Intel Centrino 2 P8800, 4GB RAM, nVidia 9300GM with 256MB vRAM).

To conclude, it still feels like an incomplete OS with lots of room for improvement and streamlining, the streamlining that Gnome Ubuntu has received or by default always had. For new users I don't think this will be a nice experience, even for Gnome heads and KDE virgin's it will be difficult and may not be worth sticking with.

---

### Post by Dov on 2010-02-02
Unless you have the latest hardware (which seems to be what they are pandering to now), don't worry about Karmic. I just downgraded to 9.04 after months of Ubuntu paying out Karma on me. 

My laptop would not return from hibernate, but would hibernate automatically if the power cord slipped out and was plugged back in again, leaving me with a black screen on boot. How useful.

Karmic seemed to have trouble mounting disks at boot and if there were two partitions being fsck'd at boot, you couldn't avoid both of them. The second ESC would always land you in a recovery shell with root privileges. How lovely and secure.

The new xsplash boot screen looked fantastic around alpha 4, but they screwed it left, right and centre after that and ended up with something just as patchy and flickery as before, just slower and less stable. Great.

Karmic filled up my root partition like no other Linux distro I have ever run. what have they been feeding the Koala? Steroids with it's gum leaves?

I don't have time to list all the wonderful fun I had while on the receiving end of Ubuntu's bad Karma. All I have to say is this. I've been using Ubuntu happily since 5.04 and have probably done in excess of 100 installs on friends computers. No more. If Lucid isn't drastically better I'm going to Debian. Software that WORKS. 

I always dreaded the day when Ubuntu would get too big and start to get sucky. Time to jump ship I think.It's never going to be as good as it was.

---

### Post by overdrank on 2010-02-02
Moved to  Ubuntu Testimonials & Experiences

---

### Post by Dov on 2010-02-02
Hmmm. I looked at LXDE a while ago and it still needs a lot more work. don't get me wrong. I love the stuff that pcman has done, but it all seems to be just stuff he's tacked onto the fantastic file browser he wrote.

---

### Post by Firestem4 on 2010-02-02
No offense OP but most of your complaints seem petty. Kubuntu was the first distribution I used when I got into Linux (I started with 8.10 so if you want to talk about a release ridden with problems). I had no trouble finding what I needed to; as a virgin Linux user as well.

9.10 has a few bugs but they're typically minor. I'm not disagreeing with you that there is some dysfunction with the UI, but Apply vs Cancel is kind of a no brainer (regarding updates).

The reason why there are so many dialogs with the wireless setup is because you must A) Choose what wireless network you want to connect to; B) Enter in any information needed to connect (seems pretty standard for any wireless manager right?). The only reason you have to do more is because Kubuntu (and KDE) use Kwallet to securely store program passwords/secrets, which is a very smart idea since most systems leave these in plaintext. (This functionality can be disabled/denied for any program at will). KNetworkManager automatically tries to save the password in KWallet. How is it a problem if you hvae to configure your password for Kwallet, once? And say "Allow this program to always use KWallet".

Bear in mind that gnome != KDE, and things work differently on each system. 

Also, KPackageKit is the Kubuntu Software Updater, its in Kicker>Utilities>, as well as available in System Preferences > Add/Remove Software.

---

### Post by Tamlynmac on 2010-02-03
To the OP:

Thank you for sharing your experience. Since this isn't a debating section of the forum, I will not comment on your opinions.

Good Luck and I wish you well.

---

### Post by r_s on 2010-02-03
It all depends on your choice , if you want some nice effects and all that aesthetic pleasure while working , one should opt for Kubuntu , ubuntu on the other hand with gnome is made for easy going users, who like the ease of operation.

---

### Post by jward3010 on 2010-02-04
> **Firestem4 said:**
> No offense OP but most of your complaints seem petty...I had no trouble finding what I needed to; as a virgin Linux user as well.
Well, now I'm finding my feet with it and getting used to different things. But at the same time I shouldn't confuse being used to something with it being a good design to begin with. We're all to used to XP but it doesn't mean that if you were a first timer you'd be impressed with it, especially if you were used to something better. My problems are UI errors in a lot of cases not just differences in desktop principles.

> **Firestem4 said:**
> 9.10 has a few bugs but they're typically minor. I'm not disagreeing with you that there is some dysfunction with the UI, but Apply vs Cancel is kind of a no brainer (regarding updates).
To be clear I said it's the difference between clicking "Apply" or "Install updates" and that is only a minor annoyance. I didn't mention "Cancel". The reason being is that the Apply button looks like the "save-settings" type of "Apply" throughout the rest of the system.

> **Firestem4 said:**
> The reason why there are so many dialogs with the wireless setup is because you must A) Choose what wireless network you want to connect to; B) Enter in any information needed to connect (seems pretty standard for any wireless manager right?).
Not when you come from Gnome Ubuntu's network manager, it's much simpler and streamlined. It knows what security the networks uses (which is ALWAYS a given) and just requests the key, Kubuntu doesn't. In regards KWallet, I have no problem with it, although I feel I see it too often, in regards lots of stuff, Amarok too. Also the network menu on first use is not so clear. You have two options - both of which work: 
1. "Connect to other network" - What other network? I've never connected before.
2. Some kind of wireless icon, which I clicked out of curiosity and found networks.

The point is there should be no need for second guessing and first users or novices will be thrown by this lack of focus, ruining their expectation for the rest of the OS.

> **Firestem4 said:**
> Bear in mind that gnome != KDE, and things work differently on each system.
Absolutely true, and in this case Gnome works way better. In my opinion.

---

### Post by jward3010 on 2010-02-04
> **r_s said:**
> It all depends on your choice , if you want some nice effects and all that aesthetic pleasure while working , one should opt for Kubuntu , ubuntu on the other hand with gnome is made for easy going users, who like the ease of operation.
That shouldn't make excuses for "Nice UI = Bad operation", there is no reason to say you can't have a nice UI and good flow of operation and design. At the end of the day window design, button placement, work flow and dialog design is something that just has to be edited. 

What I'm finding is that Kubuntu is looking nicer with every release but better functionality isn't being worked on, like for example (like I said above) connecting to a wireless network. It involves about 5 window appearances and too many options, and yet it's such a common operation nowadays. The K menu is annoying to trawl through to get to basic things like Firefox and System Settings (yes, I know I can favourite things but that's limited too), it's not even that quick to respond to mouse input.

---

