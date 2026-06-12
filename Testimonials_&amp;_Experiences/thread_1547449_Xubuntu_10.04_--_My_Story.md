---
title: "Xubuntu 10.04 -- My Story"
date: 2010-08-06
forum: Testimonials &amp; Experiences
---

### Post by lespaul_rentals on 2010-08-06
I started out with Ubuntu back in the 7.04 days. I remember installing it on my laptop for the first time. I was filled with a sense of interest in this project, and it consumed me for weeks.

Kubuntu was next. After getting comfortable with Linux and starting to learn the package management system, I felt adventurous and wanted to explore the KDE way of things. The applications were still the best I have seen to this day. K3b, Amarok, all that stuff just worked. And it worked, for the most part, quite well. The magic apt-get for me was always **ubuntu-restricted-extras**. That completed my KDE install for a while.

Then, I moved on. I've tried everything from Slackware to Gentoo. The latter I could never get to run. I probably could these days, but I haven't gone back in some time, mainly because I prefer stable and secure. I can tell you that Arch is a fantastic bleeding-edge-at-times distro, and a very good one at that. Debian is another favorite. It's stable, secure, uses su, and has good repositories along with the best package management system I've ever used. OpenSuSE 10.3 is the distro I would have picked for any enterprise deployment back in the day. Very professional and clean.

I dumped my Windows and Linux dual-boot (for the 30th time). I needed a good install, one that would last me. I wanted to try Xfce and learn it a bit more, since I liked it the few times I had used it. I installed Fedora 13 Xfce Spin. It was great. Geany is a solid IDE for scripting and programming, and it's lightweight. Everything is, for the most part. I love the panel. It's just what I need. A bit more color customization built into the GUI would be nice, though.

Google Chrome is my browser now, by the way, as I was tired of the bloat and yet a lack of features that Firefox brought about.

Anyway, here I am now. Fedora's yum is wrought with DNS resolving issues. I don't mind adding a few lines to the necessary files every now and then, but this was just too much to deal with. I came back to the Ubuntu/Debian way of things, and went with Xubuntu 10.04. No hassles. I trimmed my menu up, got my laptop setup with a sweet look, set things up to work with my LG LCD widescreen monitor, and have every bit of functionality I need. Plus, it's reliable. The setup is a one-time deal, and this install will last me for a long time.

My advice to the noobs amongst us: get your repositories set up from the get-go. Learn the APT command-line, as it will aid you well.

```
sudo apt-get install *application_name*
```

```
apt-cache search *application_name* **OR** *application_description*
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

That's all you need to know, essentially. Get the rest through:

```
apt-get --help
```

Oh, and run this:

```
sudo nano /etc/apt/sources.list
```

And uncomment (remove the preceding # sign from the line) all the commented lines that do not have to do with the CD installer (that's at the very top unless you did something to change it).

Save the changes when you exit nano. Run the update command and enjoy.

---

### Post by lancest on 2010-08-06
I've had similar experiences and always end up back at Ubuntu.

Every pc I own runs Linux only.

Agreed- CLI is so incredibly useful.

Greetings from a former Poky (SE Id) resident.

---

### Post by XubuRoxMySox on 2010-08-07
I was a Xubuntu fanboy until 10.04 came out.

I loved their implementation of Xfce (it's still awesome), but what I liked best was that - until now - the Xubuntu devs did not feel bound to include the buggy, beta, experimental stuff that appears in every new Ubuntu release. Karmic, for example, did not include the troublesome PulseAudio. Now Lucid has it, and it's no less troublesome now than it was a year ago. Plymouth is new and experimental, something that Xubuntu devs might have avoided before. No longer. Xubuntu appears to be just "Ubuntu with Xfce tied on."

It still worked (once I removed PulseAudio and stuff) until an update completely disabled the video display. It literally put my monitor into sleep mode. Only a complete re-install (and repeating the removal of all the nasty cruft that shouldn't be included IMO) cured it, and only because I ignored updates.

My advice to anyone using any of the 'buntus (or anything *based* on Ubuntu) is to set your Update Manager preferences to **[COLOR="Red"]accept only security updates.[/COLOR]** Ignore the "recommended" ones that so frequently b0rk a perfectly good working system. The sheer number of "b0rked after update" threads in here makes it seem like the stuff they're sending down to users is totally random, hurried, and potentially harmful. I can well imagine that it must be full time job for developers of Ubuntu spin-offs like Mint and UberStudent, to protect their users from all the flotsam coming at them from upstream as well.

-Robin

---

