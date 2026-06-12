---
title: "Intel® Wireless 4965AGN"
date: 2007-07-02
forum: Utah Team - US
---

### Post by heartsbane on 2007-07-02
I recently had a friend of mine call me this weekend to help him install Ubuntu on his Dell Inspiron 6400/e1505. Everything runs great but the Intel® PRO/Wireless 3945ABG Network Connection adapter. From what I have read at: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

Before I can use the iwlwifi projects drivers, I must build the mac80211 module.

```
$ wget \
  http://intellinuxwireless.org/mac80211/downloads/mac80211-8.0.1.tgz
  % tar xvf mac80211-8.0.1.tgz
  mac80211-8.0.1/origin/GIT
  mac80211-8.0.1/origin/net/mac80211/Makefile
  ...
$ cd mac80211-8.0.1 
$ make
  Building modified version in 'modified/' directory:
  Copying modified/ from origin/...done
  Applying patches and scripts from pending/.
   + Applying: pending/14-d46...0bb780bba2b5db.patch
   ...
   % make patch_kernel <-- You need to be root for this
   Patching from compatible/ to /lib/modules/2.6.18-gentoo-r6/build/:
    + Replaced 43 files.
    ...
```

But here is where I encounter the problem, because you need to 'make menuconfig' to configure the kernel to include d82011. This is where Ubuntu is giving me a little bit of trouble, because I never had the need to use 'make menuconfig' under Ubuntu.

I can only assume that is why the drivers listed on the download page ([http://intellinuxwireless.org/index.php?n=Downloads](http://intellinuxwireless.org/index.php?n=Downloads)) are for Debian, Gentoo, Red Hat, Arch linux, etc. because they will all you recompile and make changes to the kernel.

Please advise, because I think this could be a good learning experience.

---

### Post by TeeJR on 2007-07-02
It's nice to see someone else with the same hardware as me running Ubuntu.

I am glad you posted that link since I need the drivers. I am currently just using ndiswrapper with the windows drivers for the 4965AGN. They seem to work pretty decent as long as all I do is browse the web. I only have trouble when I try to play video or download stuff. Doing either of those two things seems to kill the wireless driver and then I just have to use modprobe to remove/reload the ndiswrapper. That will bring it back. I hate doing that.

I will look at the link you posted and see if I can get my 4965AGN working with real drivers. I don't know much about building kernels just yet. I'm admittedly a noob, but I'm persistent and frustrated with Vista enough to, more likely than not, getting all my laptop's devices working with Linux.

If I do figure it out or you figure it out, please, let's post the details here. I have been working on getting everything on my laptop working for a week and I would like to help others get their stuff working. I have been keeping a list of what I have done to get things working on my Toshiba P205-S6267. Once I have a complete list I'll post the details. But I work in a very structured, systematic, way so you won't get a try this, try that, type of solution. You'll get the solution that worked for me.

---

### Post by heartsbane on 2007-07-02
Yes but were you getting the 1000N speed because we were not?

---

### Post by TeeJR on 2007-07-02
I don't know what 1000N means so I can't answer that. All I know is that I am using that wireless adapter right now and it's working great. I just don't dare download stuff until I get things figured out. 

Could you please explain your question and maybe it will make more sense to me.

Thanks

---

### Post by heartsbane on 2007-07-03
Sorry It had been a long day when I posted that.

I was curious if you had done any speed tests... what are your connect speeds? Are you able to connect at 300 Mbps Draft-N data rates? Because the fastest we were able to connect was 54Mbps. Sorry I can understand how that made little to no sense.

---

### Post by TeeJR on 2007-07-03
I am connected at 54Mbps. That is the fastest I have ever been able to connect for wireless. Probably a limitation of my AP.

I am currently in the process of following some directions for installing iwlwifi. There is a good link with some instructions at: [http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550)

This is a thread on how to build everything in. I haven't tried it, but I am going to if I have time tonight. The guy is very helpful and has posted on this forum under: [http://ubuntuforums.org/showthread.php?t=396204&page=5](http://ubuntuforums.org/showthread.php?t=396204&page=5)

His name is ciphermonk. I would read through his stuff. He seems to be very experienced at building kernels and stuff. I'm not sure what you level of expertise is, but mine is noob. I'm surprised I got ndiswrapper working well.

Good Luck,

---

### Post by ehmdjii on 2007-07-08
has anyone had any success with the new releases at intellinuxwireless.org ?

i also have the problem when doing make menuconfig that ubuntu doesnt allow me to modify stuff
```

:/lib/modules/2.6.20-16-generic/build$ sudo make menuconfig  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before &#8216;chtype&#8217;
scripts/kconfig/lxdialog/dialog.h:187: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:193: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:195: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:196: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:197: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:198: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:200: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c: In function &#8216;dialog_checklist&#8217;:
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;dialog&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;list&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function &#8216;getmaxy&#8217;
scripts/kconfig/lxdialog/checklist.c:129: error: &#8216;stdscr&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: &#8216;KEY_MAX&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function &#8216;getmaxx&#8217;
scripts/kconfig/lxdialog/checklist.c:137: error: &#8216;COLS&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: &#8216;LINES&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function &#8216;draw_shadow&#8217;
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function &#8216;newwin&#8217;
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function &#8216;keypad&#8217;
scripts/kconfig/lxdialog/checklist.c:143: error: &#8216;TRUE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function &#8216;draw_box&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function &#8216;wattrset&#8217;
scripts/kconfig/lxdialog/checklist.c:147: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function &#8216;mvwaddch&#8217;
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function &#8216;waddch&#8217;
scripts/kconfig/lxdialog/checklist.c:151: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function &#8216;print_title&#8217;
scripts/kconfig/lxdialog/checklist.c:156: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function &#8216;print_autowrap&#8217;
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function &#8216;subwin&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function &#8216;print_item&#8217;
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function &#8216;print_arrows&#8217;
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function &#8216;print_buttons&#8217;
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function &#8216;doupdate&#8217;
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function &#8216;wgetch&#8217;
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: &#8216;FALSE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function &#8216;scrollok&#8217;
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function &#8216;wscrl&#8217;
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function &#8216;wrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function &#8216;delwin&#8217;
scripts/kconfig/lxdialog/checklist.c:297: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function &#8216;on_key_esc&#8217;
scripts/kconfig/lxdialog/checklist.c:312: error: &#8216;KEY_RESIZE&#8217; undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

---

### Post by monkey89 on 2007-07-09
> **ehmdjii said:**
> has anyone had any success with the new releases at intellinuxwireless.org ?

i also have the problem when doing make menuconfig that ubuntu doesnt allow me to modify stuff
```

...
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
...

```

Install libncurses5-dev.

---

### Post by ehmdjii on 2007-07-15
thanks, now i have ncurses installed and get this error:

```
Kernel Makefile not found at '/lib/modules/2.6.20-15-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

```

although i have kernel-sources and linux-headers installed

---

### Post by tamasrepus on 2007-07-23
> **ehmdjii said:**
> thanks, now i have ncurses installed and get this error:

```
Kernel Makefile not found at '/lib/modules/2.6.20-15-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1

```

although i have kernel-sources and linux-headers installed

You forgot to make a symlink:
```

ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source

```

---

### Post by csgrad on 2007-09-10
Ive made it through the steps you guys have mentioned above, and everything has been going good but now im stuck here:

```
 sudo make SHELL=/bin/bash modules modules_install
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

```

---

### Post by dgtldaydrmr on 2007-09-12
I'm stuck here as well...
:(

---

### Post by evilpeno on 2007-09-19
Stumbled across this info on making the 4965AGN work.

[http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller)

---

### Post by rGoodie on 2007-09-24
For those having problems with the makefile I found an alternate method that worked for me

First add the following line to your /etc/apt/sources.list file

access the file with
```
sudo gedit /etc/apt/sources.list
```

add this to the end of the sources.list file
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
```

now just run your update manager system->administration->update manager reboot and you should be good to go

this is a modified version of what i found at
[http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller)

cheers
Goodie

---

### Post by nagrover on 2007-09-26
> **rGoodie said:**
> For those having problems with the makefile I found an alternate method that worked for me

First add the following line to your /etc/apt/sources.list file

access the file with
```
sudo gedit /etc/apt/sources.list
```

add this to the end of the sources.list file
```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
```

now just run your update manager system->administration->update manager reboot and you should be good to go

this is a modified version of what i found at
[http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller)

cheers
Goodie

No dice here. When I do an update after adding to sources.list I get:

Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages [4044kB]                                    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages [159kB]                                   
Fetched 5356kB in 28s (189kB/s)                                                                      
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing xlog (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by nagrover on 2007-09-26
A ha, found the solution if anybody runs into what I got above. Just do this for an update after changing sources.list:

sudo apt-get update -o APT::Cache-Limit=25165824

---

