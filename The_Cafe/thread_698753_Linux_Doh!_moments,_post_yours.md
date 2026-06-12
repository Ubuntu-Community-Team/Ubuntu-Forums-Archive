---
title: "Linux Doh! moments, post yours"
date: 2008-02-16
forum: The Cafe
---

### Post by bwhite82 on 2008-02-16
Mine came today. I always knew you could use wildcards * for  many things on the CLI, but never thought to use them for changing directories. In the past, I'd always type out the full name of the directory (because I didn't know any better):

> cd new_fangled_program_v_1.0.2.4-linux-i686-smp-full-version-uncut-2.22-5

vs.

> cd new*

Doh!

---

### Post by p_quarles on 2008-02-16
> **Soldierboy said:**
> Mine came today. I always knew you could use wildcards * for  many things on the CLI, but never thought to use them for changing directories. In the past, I'd always type out the full name of the directory (because I didn't know any better):



vs.



Doh!
Try typing:
```
cd new
```
and then hit the tab button. ;)

---

### Post by phrostbyte on 2008-02-16
In Ubuntu 7.10, wildcards (and the more powerful UNIX regular expression) work for apt-get too, you also get tab completion for package names.

---

### Post by 23meg on 2008-02-16
Ctrl + R will rock your world.

---

### Post by bwhite82 on 2008-02-16
> Ctrl + R will rock your world.
Doing that on a terminal window gives this:

> (reverse-i-search)`':
??

---

### Post by bwhite82 on 2008-02-16
Ah, NM. That's sweet! :)

---

### Post by 23meg on 2008-02-16
Hit Ctrl + R, type any part of a previous command you've entered and the first match will come up. Hit Enter to issue it. Keep hitting Ctrl + R to scroll through the matches in your BASH history.

---

### Post by 1337455 10534 on 2008-02-16
cd /home/theuserwiththeverylongusernamewhichistedious/Desktop/complicatedfoldername
as opposed to
cd ~/D*/c*
Wildcards rock.

---

### Post by FuturePilot on 2008-02-16
Spelled "Option" wrong in my xorg.conf and then wondered why X wouldn't start ](*,)

Accidentally overwrote my xorg.conf with edid.bin #-o
instead of moving it to /etc/X11 I moved it to /etc/X11/xorg.conf because I'm so used to typing /etc/X11/xorg.conf

Good policy: keep a copy of xorg.conf somewhere safe

---

### Post by icechen1 on 2008-02-16
> **Soldierboy said:**
> Mine came today. I always knew you could use wildcards * for  many things on the CLI, but never thought to use them for changing directories. In the past, I'd always type out the full name of the directory (because I didn't know any better):



vs.



Doh!

Same here,thank you!

---

### Post by bwhite82 on 2008-02-16
This could turn into a useful thread. Keep em comin'!

---

### Post by Retrograde77 on 2008-02-16
Had no idea about that CTRL-R, very nice :)

Had one just now. Have wanted all my vids to play in VLC not totem for a while, happen to be looking in file properties a few minutes ago and there lies Open With which sets it for all files of that type.
No idea how I missed that.

---

### Post by weresheep on 2008-02-16
Ctrl-Z and the 'fg' and 'jobs' commands.

Learning these commands and the principles behind them was a real eye opener for me. Up until that point I don't think I had really understood the power of the CLI environment that Unix offers.

Of course, later I learned about 'screen' and things really took off :-D

-weresheep

---

### Post by chris4585 on 2008-02-16
i didnt know that with compiz you could use the scoll button, click then view the cube from any angle, i felt stupid since my friend found that out before me and i use my computer more than he does... that was a duh moment for me

---

### Post by Irihapeti on 2008-02-16
Discovering that you can open up an ISO file like an archive and extract files from it. I'd feel lost without it now. I don't think that can be done in Windows unless you install some special program.

---

### Post by steveneddy on 2008-02-16
Anyone remember Beryl in the early days?

Do I need to say more?

---

### Post by argraff on 2008-02-17
Installing WINE and not using it for months because I didn't know how...Right-click, open with WINE - duh!!!

---

### Post by tvdxer on 2008-02-17
A few weeks ago, trying to set up my sister's laptop's bcm43xx-chipset Wifi in Puppy Linux with ndiswrapper and the Windows drivers I had copied to a Flash drive, when I just happened to notice that Puppy's "Network Wizard" had a "Config" button where I could further click "Scan" to get to my wifi network.  And it worked!

---

### Post by Irihapeti on 2008-02-17
Since someone's mentioned Puppy, there is this: I thought my sound wouldn't work in Puppy, though it's always worked in Ubuntu. Various others were having problems so I thought, oh well, I'm in good company and anyway, Puppy is only a sideline for me (to fill in the time I used to spend defragging, updating AV etc in Windows he he).

Anyway, one day, it occurred to me to type alsamixer in a terminal... guess what: my speakers were muted, and that was the only thing preventing me from having sound in Puppy all along :oops:

---

### Post by k2t0f12d on 2008-02-17
> **Irihapeti said:**
> Anyway, one day, it occurred to me to type alsamixer in a terminal... guess what: my speakers were muted

This happened to me in another distro.  I also had a problem with sound until I figured out my mobo built-in was still set to default.  I reboot into the BIOS and disabled, and my SB *Live!* came to life.

---

### Post by billgoldberg on 2008-02-17
One of the first days I was using linux and followed a guide to do something (forgot what).

I got stuck and after a few hours I realized i had not changed 

/home/username/Desktop/...

to 

/home/rw/Destkop/...

hahaha, I could have slapped myself.

---

### Post by EdThaSlayer on 2008-02-17
I remember the days when I was so amazed to see that you didn't have to type in the names of the files.

For example, typing ls in the terminal gives me this:

```
MyDownloads


```

and all I have to type in the terminal is "MyD" and press tab and it will finish the sentence for me. :)
That saves me a lot of time going around my filesystem, especially with directory names that have a space between them. :popcorn:


I have to say the second thing was the hiding the files thing. When I started, I thought that adding a period in front of a filename will make it "disappear"(deleted...), later on I figured out it was just the way you hide things in Linux.

---

### Post by Xavieran on 2008-02-17
I have had many,many Doh! moments :D

Moment A: I had somehow stuffed up my mom's sound for her user account,but it worked perfectly well on root's account (in sabayon).After hours of reinstalling drivers etc. I decided to look closer at some sound issues other sabayon users had been having...
I looked at the top thread on sound and found my answer: 
usermod -aG audio username :D

Moment B: Also on sabayon, I decided to change the permissions of the /tmp directory and somehow erased all the contents of all folders inside it.I got a ton of Corba not authenticated errors when I restarted gnome and then spent a few hours on the sabayon irc (Very helpful people there!) debating on whether to do a hard reinstall or not, when a kind soul suggested to delete /tmp...

I did and it worked fine!


Anyway,just my stupid moments ;)

---

### Post by Gigamo on 2008-02-17
During the first week I switched to linux/ubuntu, I couldn't get my sound working at all. I have a Compal laptop with Realtek HD sound, and I googled and added a line to my alsa config:

```
option snd-hda-intel model="...."
```

Where .... had to be the model of the card. There were 4 possibilities: auto, 3stack, acer and toshiba, and ofcourse, I only tried the first three, gave up, and found out way later that it had to be toshiba. :D

---

### Post by bwhite82 on 2008-02-17
> Installing WINE and not using it for months because I didn't know how...Right-click, open with WINE - duh!!!

Doh! Thats a good one. :)

Another one for me: This was back on Edgy, trying to get my wireless card working. I read every single thread I could find (on multiple forums), read multiple wikis, ran countless commands in the CLI, tried this driver tried that driver, reinstalled this reinstalled that, only to learn at the very end that all I had to do was press the hardware switch on my laptop and my wifi came to life. I could have cried I was so frustrated.

---

### Post by arman.haghi on 2008-02-17
couldn't get my sound to work. tried everything, for days.

drivers, settings, resources, everything.

then i found out that by disconnecting the front panel audio connectors, as I had done a few days earlier while modding my box,  I had disabled the back panel too. 

Just needed some jumpers to fix it up, sound working a treat..

technically not a Linux doh moment, but definitely a Doh moment, and goes to show that you shouldn't start by blaming the software...

---

### Post by xpod on 2008-02-17
> i didnt know that with compiz you could use the scoll button, click then view the cube from any angle, i felt stupid since my friend found that out before me and i use my computer more than he does... that was a duh moment for me

Or the Left & Right Mouse buttons together,or indeed CTRL-ALT-LMB.:)
The latter is probably better because you dont have to be clicking *on* the actual Desktop for it to activate,like you do with Scroll or the RMB & LMB methods.

I`m currently having a wee look at the next installment of Ubuntu though and the cube seems to be staying in whatever position i leave it in,till i click back on the thing anyway.
Dont think that happens back in 7.10`s default Compiz?

Back OT!
Every day is full of "Doh Moments" for moi....
If it`s a box with wires & stuff inside then theres just no avoiding them:)

---

### Post by mridkash on 2008-02-17
For me it was the discovery of backticks ` ` . You can enclose any command in those and it runs, wherever you put it.

Example, for changing directories I have made a script called goto and placed it in /usr/bin

the script echoes the path of the directory when I call it. So for changing to My Documents Folder in Windows, I do
```
cd `goto mydocs`
```and the full command becomes,
```
cd '/media/sda1/Documents and Settings/name/My Documents'
```Later I found out that technically the backticks thing is called command substitution in shell.

---

### Post by Tristam Green on 2008-02-17
While just beginning to learn Linux/Ubuntu, I removed the account created on Ubuntu install from the "admin" directory in a bold security move.

Took me a couple days to remember the **usermod** command.

---

### Post by staticvoid on 2008-02-17
for the longest time i couldn't figure out how to cp a file to a dir, then i realized i had not cd'ed to the dir where the file was... doh!

sv

---

### Post by happyhamster on 2008-02-17
Not really linux specific, but here goes:

After a fresh install of Ubuntu Gutsy I just couldn't get flash to work (youtube). I spend days trying to (re-)install several versions of flashplugin-nonfree and gnash. And it had worked fine before. :confused:

Eventually I figured it out: youtube (the only site I checked to see if the plugin worked or not) had changed. Before, I only had to tell the noscript-plugin to allow "youtube.com" to be able to see the videos. But nowadays you have to allow "youtube.com"  and "ytimg.com".

Flash probably worked the first try :lolflag:

---

### Post by bwhite82 on 2008-10-31
> **Tristam Green said:**
> While just beginning to learn Linux/Ubuntu, I removed the account created on Ubuntu install from the "admin" directory in a bold security move.

Took me a couple days to remember the **usermod** command.

lulz

---

### Post by aeiah on 2008-10-31
i had several scripts in my /usr/bin that i needed to set as executible and had to set the access rights properly. in a moment of stupidity i used a wildcard in my command and set my 'other users' part of the access rights to 'none' for all the files in /usr/bin

which is kind of awkward when sudo lives in there. the only user that could use it was root, which kinda defeats the purpose  =D>

---

### Post by ModelM on 2008-10-31
I've been using GNU/Linux long enough that I've made most of the errors one can, but I'm still exploring.

One of the screwups from my hall of fame occurred when I was building a new kernel. I thought, "Instead of building everything in like I usually do, let's build everything as a module". So, I did - selected everything to be built as a module, including the reiser filesystem support.

Since I was using reiserfs, and had built the support as a module, the kernel couldn't read the disk to load the module so it could read the disk.

That one set a record for the fastest kernel panic I've ever had.

---

### Post by ethoxyethaan on 2008-10-31
mixed up cp and rm damn dyslexia.

---

### Post by lucasl on 2008-10-31
Blanking a usb stick:
```
dd if=/dev/null of=/dev/sda
```
Problem being, I did a typo: sda is my main hard drive, I meant sdb.
It ran for 10 seconds before I realized. Backed up my work to an external drive and restarted, hoping nothing bad would happen. I was wrong.
Luckily for me my Windows partition is first and I had that partition table repair utility (forget the name) on a live cd. Lost my COD4 Multiplayer data though:D

---

### Post by chris4585 on 2008-11-03
> **Soldierboy said:**
> Doh! Thats a good one. :)

Another one for me: This was back on Edgy, trying to get my wireless card working. I read every single thread I could find (on multiple forums), read multiple wikis, ran countless commands in the CLI, tried this driver tried that driver, reinstalled this reinstalled that, only to learn at the very end that all I had to do was press the hardware switch on my laptop and my wifi came to life. I could have cried I was so frustrated.

I've had a similar experience on my PSP, it went something like "Is the switch turned on?" or something I could of sworn it was talking about some network switch, not on the PSP.. my friend pointed out the obvious though

---

