---
title: "Linux 'Freeze' Number One."
date: 2010-11-24
forum: The Cafe
---

### Post by Sean Moran on 2010-11-24
Since the days of RedHat 6.1 back in 1999 or 2000 (I forget exactly), and through Mandrake 10 and onto Ubuntu, I never had a system freeze until just then today.

I had the Terminal open running a chroot script to build another distro, and gEdit open to keep track of the script progress, and Nautilus open to watch the .deb files accumulate into the /var/cache/apt/archives/ directory inside the target filesystem dir, and then I did a dumb thing.  I do a lot of dumb things but usually Linux forgives me.  

Rather than start from the top and press SHIFT+END to select the entire directory, I was at the bottom, so I pressed SHIFT+HOME to select the entire '/apt/archives/ list, and that was when everything went to Antarctica.

First ever time that Linux has frozen on me.

Please tell me if there have ever been any times in the past for you that Linux has called it a day without asking.

---

### Post by amauk on 2010-11-24
Chances are it was only nautilus that puked, and not the entire system

Nautilus can be a bit flaky when it comes to extracting the metadata out of files (particularly if they're changing at the time)

A quick "killall nautilus" should do

I had a corrupted mpg video file a while back that would send nautilus packing whenever it tried to extract a frame for the thumbnail

---

### Post by czr114 on 2010-11-24
I've had my share of freezes from bad RAM and spilled liquids, but that's a hardware problem.

Other than that, I haven't had Linux freeze since Valhalla, which could be successfully locked up by routine GUI usage, although X crashes were more common.

---

### Post by Sean Moran on 2010-11-24
> **amauk said:**
> Chances are it was only nautilus that puked, and not the entire system

Nautilus can be a bit flaky when it comes to extracting the metadata out of files (particularly if they're changing at the time)

A quick "killall nautilus" should do

I had a corrupted mpg video file a while back that would send nautilus packing whenever it tried to extract a frame for the thumbnail
Mate I have the system monitor up there on the very right side of my top panel, but I couldn't even get that to run.  No menus either.  The whole thing just took off on holidays, after a two hour distro build was 90% done I might add.  Mouse pointer wouldn't even move after a few minutes.  All I could do was to hit the OFF button for ten secs and start again.  

I have never had a problem with Linux until that moment.  Running a very reliable version of Karmic and building a chroot distro based on Maverick, but I agree that it was something stupid I did in Nautilus that caused the catastrophe.


---o0o---

The rule I have learned about Nautilus when there are 1,000 odd files and ever increasing, is to NEVER start at the bottom and press SHIFT+HOME to go upward, because that will just confuse the poor little file-browser.  Go to the top and press SHIFT+END so that Nautilus doesn't run the whole system aground.

---

### Post by Dragonbite on 2010-11-24
Worst I had was when my CAP and NUM LOCK lights were flashing and the entire system froze.  This was years ago, though, and since then I've had Linux handle crashes relatively nicely.

Upon reboot, did you try it again and did the system freeze on you?  Anything in the log files?

---

### Post by Bodsda on 2010-11-24
I have had a fair few Freezes and crashes. Usually down to me playing "delete the file, see what happens" game but I often get the grey screen of annoyance. Where one app decides to hang up, so gnome thinks it would be a good idea to stop me using the entire DE. A quick trip to tty1 and a killall later and everything comes back to life
 
Bodsda

---

### Post by samalex on 2010-11-24
I can probably count the number of times Linux has truly frozen on me on one hand, and that's in almost 15 years of using it.  I've had the GUI hang before, but SSHing in from another device or even switching to another terminal window (Ctrl-Alt-Fn#) would bring up a new shell and let me see what's happening.

And honestly the times it has truly frozen it was generally due to either a recent hardware or driver change I made, so none have been just random.

---

### Post by joepie91 on 2010-11-24
Recognizable. I think I've had 1 or 2 freezes in the past... 6 months that I've fully switched back to OpenSuSE. And it was always Nautilus. For some reason, Nautilus apparently thought "*oh, if I have to freeze you won't get your panels either :twisted:*" and everything hung. Couldn't even start GNOME monitor or even a terminal. Chrome still responded (it was on foreground) but that was about it.

Thinking back of it, it started after I installed the Catalyst drivers (which nuked my system) and manually reverted back to the open-source drivers. But it was definitely Nautilus freezing up.

---

### Post by TheSqueak on 2010-11-24
Ubuntu froze on me a few times a couple of months back, but that was because my primary hard drive was starting to fail and ended up having to be replaced

---

