---
title: "Ubuntu Studio vs Ubuntu Multi-media vs Studio 64, ect"
date: 2010-05-26
forum: Ubuntu Studio
---

### Post by Nick_Jinn on 2010-05-26
So what are the differences between these? Especially, what is the difference exactly between Ubuntu Studio and Ubuntu Multimedia? Where can I download the later?


I am interested in making music and working with both open source and proprietary or even non-free as in cost software. I want the tools that are easiest to use without too steep of a learning curve. I am looking for the following....

MIDI.....I want to be able to use touch pad drum machines and have them 'play' or execute sounds that I load in the sound program, and I want it to be so easy to set up that its ridiculous.....if not, give me the easiest version available.

Webcasting of both video and audio....I want to stream video both from a cam as well as from movies and videos I compile.....Like, I would want to write a documentary or an interview and add it to a list, and for the list to keep playing these videos over and over again in a loop, and then I could use whatever tools are available so that people could view this streaming video or audio from my own desktop acting as a server while its also performing the basic duties of a graphical home desktop.......If not, I will settle for something that is set up for upload or streaming to an external website.

I need to be able to create fliers.

I would like to be able to work on some artwork with a wabcom bamboo, which is their cheaper model.

I would like some good video editing tools and audio editing.....it doesnt have to be open source. I wont be modding the software.

I want a really rich graphical interface for my desktop that I can turn on and off.....I want the cube that visually rotates, a 3d sub-background, and I want those app:fu pie graphs that look like occult runes or something.....I think those are from enlightenment.

I would like to use Gnome but also pull features and libraries from Enlightenment.



Anyway, that is a description of my needs if I ever got really ambitious.......but besides that, can anyone just explain the difference between Ubuntu Studio and Ubuntu Multimedia? Are they redunment? What does each bring to the table that the other doesnt?

Can regular Ubuntu become Ubuntu Studio? Can the same be said for Ubuntu Multimedia?

---

### Post by sgx on 2010-05-26
Hi, the foundations of linux are similar between distributions, like
a Christmas tree without the lights and decorations. A package manager
like synaptic in Ubuntu and many (linux), can be used to add or remove
software according to the users needs. Some apps will be dependencies
of others, but synaptic sorts those for us, and only rarely fails. Most
linux variants work with a decent subset of hardware. If you are willing
to purchase hardware known to work, the road will be much easier. If you are willing to dual boot, use multiple hard-drives, and multiple computers, you will evade common issues, and widely known limitations
of linux, and won't be dominated by surprise disapointments. Prepare for 30 hours of google time, vast amounts of experimenting, and accept that expectations and reality will be in a staredown more often than in a slow-dance.

That being said, you will be in charge of your computers, instead of
them being in charge of you, and linux will be a key part of that.
Windows and 0sx can be useful, perhaps essential for some things, but many find them minimized, and reserved for few and highly specialized applications, or mundane storage and games.

For brochures, Inkscape, Scribus, and Gimp will be useful.

Cheers

---

### Post by Stochastic on 2010-05-27
It sounds like your needs are closest to what Ubuntu Studio provides.

64studio is focused on audio only

Medibuntu is an add-on for regular ubuntu that allows for non-free format playback & editing.

Ubuntu Studio is designed for Audio professionals, Video professionals, and Graphics professionals.

---

### Post by Nick_Jinn on 2010-05-27
By "Ubuntu Multimedia" I dont mean "medibuntu". I was talking about an actual distro called Ubuntu Multimedia that was seperate from Ubuntu Studio.....has anyone heard of it?

I an not a noob....I may be a lower level user, but I am not new to linux.


The distros are not all the same though. Ubuntu studio actually tweaks the kernel for lower latency. Other factors include the choice of desktop, built in repositories, and the conflicts they could create. Also, just because you can get any OS into what you want if you are a hacker doesnt mean its the best starting place if you MAIN hobby is the music and art and activism rather than the computer hacking itself....I just want my computer to work to enable my other hobbies...its a minor hobby in itself, but I do want to get right to production withnout wasting too much time....others might prefer modding their system as the goal in itself....thats cool. I want to get right in and get practice with the apps though and my instruments.


:guitar:

---

### Post by Nick_Jinn on 2010-05-27
Hey, can anyone tell me what program I could use to run MIDI from my drum pads to a drum machine mixer in Linux so I can actually manually drum but instead of using the actual sound from the drum kit I use sounds that I program into the program?

---

### Post by cchhrriiss121212 on 2010-05-27
> **Nick_Jinn said:**
> By "Ubuntu Multimedia" I dont mean "medibuntu". I was talking about an actual distro called Ubuntu Multimedia that was seperate from Ubuntu Studio.....has anyone heard of it?

I haven't heard of this before and google shows a distro called ubuntu multimedia centre, which is not what you are looking for I presume. Where did you hear about this OS?

> The distros are not all the same though. Ubuntu studio actually tweaks the kernel for lower latency. Other factors include the choice of desktop, built in repositories, and the conflicts they could create. Also, just because you can get any OS into what you want if you are a hacker doesnt mean its the best starting place if you MAIN hobby is the music and art and activism rather than the computer hacking itself....I just want my computer to work to enable my other hobbies...its a minor hobby in itself, but I do want to get right to production withnout wasting too much time....others might prefer modding their system as the goal in itself....thats cool. I want to get right in and get practice with the apps though and my instruments.
You should try out Ubuntu Studio. Its just Ubuntu plus a few packages, the kernel and a different theme, it still uses Gnome and the regular repos plus an extra one. [Here]("http://ubuntuforums.org/showthread.php?t=1350304") is a good ppa that will give you more up to date programs plus extras and is regularly checked for conflicts.

> Hey, can anyone tell me what program I could use to run MIDI from my drum pads to a drum machine mixer in Linux so I can actually manually drum but instead of using the actual sound from the drum kit I use sounds that I program into the program?
Jackd (the linux sound server designed specifically for audio production) + Hydrogen, which is very simple and versitile. 

To be honest, after reading your first post, you might just be better buying a mac. As you are not new to linux you probably know you are not going to get the best software in the world that works magically the first try. You are going to have to do some research and get used to how things like jack work which you may or may not find to your tastes, and may take you a couple hours or a couple weeks. It will be easier if you ask for help on the forums as opposed to giving up on a failed first try.
If you get that down however, you will have a rock solid system that can handle a lot of audio production with quality output (can't speak for graphical/video).

---

### Post by sgx on 2010-05-27
> **Nick_Jinn said:**
> Hey, can anyone tell me what program I could use to run MIDI from my drum pads to a drum machine mixer in Linux so I can actually manually drum but instead of using the actual sound from the drum kit I use sounds that I program into the program?

Hi, qjackctl is the gui for jackd, to connect your linux hardware and software. Hydrogen connects itself automatically, if jackd is started
first.

jackd -d alsa -r 44100.

Then start qjackctl, click the setup button, in the panel that opens, on the right side, you'll see

Input device  >
Output device  >

click the  > widgets, your soundcard/chip/interfaces are listed there,
for you to choose the one needed.

Back at the main qjackctl screen, click the Connect button, and a panel
with 3 tabs opens. Midi devices in the Alsa tab on the right, audio in the
Audio tab on the left. Each tab has two sides, input and output, select items on each side, and press the connect button on this screen (not the main qjackctl screen) If jackd and hydrogen are started, you'll see
them connected already.

If you have a soundcard/interface with midi, and usb midi on your drumkit, experiment with when to plug it in, turn it on etc if it is not immediately detected.

 On my 88key keyboard, drums are mapped
from C2 up, 32 instruments is the max in hydrogen, so adjust your
drumkit outputs to the correct range.

The hydrogen Tools-->Preferences menu opens a panel where you can
change some items like midi channels towards your kit.

---

### Post by Nick_Jinn on 2010-05-28
Ubuntu Multimedia project is what I was thinking of, I think.


Any top the poster above, awesome. Thats a great explaination. Lets see if I can figure it out!

---

### Post by sgx on 2010-05-28
> **Nick_Jinn said:**
> Ubuntu Multimedia project is what I was thinking of, I think.


Any top the poster above, awesome. Thats a great explaination. Lets see if I can figure it out!

Hi, there are youtubes of hydrogen, ardour, rakkarack, zynaddsubfx, some detail use of qjackctl since it is run first.

Here is one that shows some qjackctl and midi: 

[http://www.youtube.com/watch?v=TMRQBCJDbH4&feature=related](http://www.youtube.com/watch?v=TMRQBCJDbH4&feature=related)

Cheers

---

### Post by cfhowlett on 2010-06-06
Ubuntu multimedia center hasn't had an update since '06.

64Studio hasn't updated since '08.

Neither distro shows any sign of updating to a new release.

Consider that you can add pretty much whatever you want to ubuntu, much less ubuntu studio.  Seems the default packages in Ubuntu Studio would be more than adequate for your task list.

Just my $0.02

---

### Post by Nick_Jinn on 2010-06-06
Thanks. 

Though I am not sure that constantly upgrading is necessary or even all that great. It seems like it causes more problems than it solves sometimes. Just my opinion.

I would rather upgrade every 2 years and really really hone the system to work flawlessly with improved support for hardware and software.

---

### Post by sgx on 2010-06-07
Hi, I to am loathe to update my system, but I find that key audio apps
often can be updated by themselves, or with minimum dependencies. A larger
app will sometimes invoke a new library that hasn't had the benefit of rigorous testing, and lead to a reinstall, or heavy research for the problem. So to be lucky, I have different versions of linux on 5 hard-disks, so backups and updates are not traumatic. Recordings go on two hard-disks, a usb stick, and cds/dvds. Bloatware is uninstalled and banned, and all dowloaded packages are stored on media, should manual install become necessary. (My skills insure it does ;)  ) 
And the oblgatory partition for /home :)
Cheers

---

### Post by Nick_Jinn on 2010-06-07
What is the last version of Linux or Mint that works well with Wacom Bamboo touch and pen?

---

### Post by sgx on 2010-06-07
bamboo? :popcorn: :guitar:
I don't know about that, but Mint9 is just out a couple of
weeks now, so its perhaps the newest ubuntu. I'm not a laptop
user, so maybe someone here can speak for it. Its working
on my wifes laptop, I think HP G60 model.
Cheers

---

### Post by Nick_Jinn on 2010-06-07
I hear the Wacom multi-touch and pen tablets are not supported in the new releases, so I am wondering if I can have a partition with an older release of Ubuntu or Mint and see if that works.

---

### Post by sgx on 2010-06-07
heres an article about such an arrangement :)

[http://chrisjean.com/2009/01/07/dual-boot-ubuntu-and-linux-mint-with-shared-home/](http://chrisjean.com/2009/01/07/dual-boot-ubuntu-and-linux-mint-with-shared-home/)

---

### Post by Nick_Jinn on 2010-06-08
I have been sharing Mint and Ubuntu and rotating versions of linux with /home since I heard you could do it.

---

