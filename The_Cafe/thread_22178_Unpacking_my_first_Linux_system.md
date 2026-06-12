---
title: "Unpacking my first Linux system"
date: 2005-03-26
forum: The Cafe
---

### Post by greenwom on 2005-03-26
Well my install looks good,  it's unpacking the last end right now.
exciting!!!!

there went Open office!

xserver!
sweat!!!

What the first thing I should do :) 

chicagomike

 :D

---

### Post by greenwom on 2005-03-26
Question to the experts.  Will I be able to use my lynksys PCMIA wireless card upfront? or will I have to do some more work?

Chicago mike

---

### Post by greenwom on 2005-03-26
I know I'm talking to myself in this thread but dang I'm impressed!!!!!!!!!!

I just finished the install on a dual boot system and no problems at all.

My fujifilm thumbdrive is working and my IPOD shows up as a drive, I think I'll have to work this out from what I've read to get it to work.....

but hey -- hats off to the ubuntu folks

Chicago mike

---

### Post by az on 2005-03-26
Gidde up.

---

### Post by hashimoto on 2005-03-26
The first thing to do depends on what you want, I guess. If you want to fine tune your system,the standard first stop would be [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html) 

Enjoy!

---

### Post by defkewl on 2005-03-26
Why don't you help us fill in our wiki.

---

### Post by greenwom on 2005-03-26
Can you explain Wiki a bit to me?  I've looked it up but haven't poured thru it all.

---

### Post by DJ_Max on 2005-03-26
[QUOTE=greenwom]Can you explain Wiki a bit to me?  I've looked it up but haven't poured thru it all.[/QUOTE]
 Not complicated at all, rather simple. Anyone can add/edit pages to a site. There a quite a few Wiki web applications out,  but all serve the same purpose.

---

### Post by greenwom on 2005-03-26
Great concept, didn't know about it!  

Now as a newbee I'm faced with a challenge.  Installing my wacom 4x5 tablet.

I downloaded the tarball and now I don't know what to do.

Again I find that most online tutorials/forums for this stuff is missing something.

What do I do!!!!! :)  I want to start painting again in the GIMP.

I have the same problem with the GIMP help files got the Tarball don't know what to do with it.

Well day two with my Ubuntu system,

chicagomike

---

### Post by emperor on 2005-03-27
First you need un-tar it!
If the tarball ends in .gz use: tar -xzvf tarball.gz
If the tarball ends in .bz2 use: tar -xjvf tarball.bz2

For most source files you will need to do these steps:
1. Configure it for your system: "./configure"
2. Compile it:   "make"
3. install it:  "install"

For step 3 you must be logged in as root or use sudo, for exampe:
"sudo install"

If any of the first 2 steps fail, you may need to install other packages to resolve the problem. This is easier after you have expience with the 3 steps.

e.p.

---

### Post by greenwom on 2005-03-27
Thanx, but like I said it's only day 2 with Ubuntu/ Linux.  I've never played with this system before :)

Do I run thise commands from a terminal window in the desktop or do I need to 
go directly to a prompt outsite the desktop.  

Directly from the install I can't even creat a folder on the hard drive with the login.

---- help ==== :)

---

### Post by poofyhairguy on 2005-03-27
[QUOTE=greenwom]
Do I run thise commands from a terminal window in the desktop or do I need to 
go directly to a prompt outsite the desktop.  
[/QUOTE]

First one. The only time you want to see your desktop at this stage is when you reset the x server (what you see) in order to add newly installed programs to the menu without resetting the whole thing.

alt-ctrl-backspace for that.....

---

### Post by greenwom on 2005-03-27
Ok so I press CTRL-ALT-Backspace and I get the prompt for like 3 seconds and then the Ubuntu screen?  

I'm a terminal newbee!!!!!

to recap -- I have the Tar-ball for my Wacom and my linksys wireless card sitting on my desktop.

I can't creat folders.

I understand the commands given above for the install but I haven't gotten that far yet to mess with it.

---- Hate being the newbee -----

chicagomike ](*,)

---

### Post by emperor on 2005-03-27
You can open a terminal in a window.
Look in the System or System Tools menu for "Terminal".

The other method is press 'Ctl-Alt F2", and then you have to login.
Press "CTL-ALT F7" to return to your Desktop.

---

### Post by poofyhairguy on 2005-03-27
[QUOTE=greenwom]
to recap -- I have the Tar-ball for my Wacom and my linksys wireless card sitting on my desktop.
[/QUOTE]


Don't worry about being a newbie. I was green not to long ago. 


You can pick it up fast.

---

### Post by kanem on 2005-03-28
[QUOTE=greenwom]
to recap -- I have the Tar-ball for my Wacom and my linksys wireless card sitting on my desktop[/QUOTE]

The Wacom might take a little work. See this page:
[http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue)

I think only the second paragraph in italics is actually useful now unless you want to follow the original instructions which are much longer. The paragraph in italics is just an update explaining that getting the Wacom working is easier than the rest of the wiki suggests. Even so, it looks complicated. I don't want to discourage you, but it looks like it's gonna take quite a bit of reading, googling and asking. 

What are the tarballs you're talking about for your Wacom? Some kind of drivers? Maybe they're all you need and the above paragraph is garbage. If you want to see what's in them (tarballs) you can either just double-click one or right click on it and select "Extract Here" in the pop-up window. Hopefully there will be instructions inside.

Easiest way to get a terminal is to right click on the desktop and select "Open Terminal" in the pop-up menu. If you're gonna become familiar with the command-line (If you get that Wacom working you probably will have to) I recommend bookmarking this page:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

If this seems like too much to get some hardware working that already worked in Windows, don't worry, it's worth it and it gets easier (You'll learn more, and Linux will get better). I spent lots of time learning how to get stuff working. Some I figured out, some things just started working when new Linux kernels came out.

---

### Post by greenwom on 2005-03-31
Thankx I'll look into the articles.  

The tar ball came from this site, recommended by wacom.

[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

I downloaded the linuxwacom-0.6.6 tarball.  I have it uncompressed but the help files minght as well be in hebrew .....

So if anyone can help with this that'd be sweet.

I also just got a .deb file from netzero for there dial up software.  I will not be using it long I'll be putting in a wireless router but I'd like to learn.
What do you do with a debian file?  .deb

---

### Post by emperor on 2005-03-31
sudo dpkg -i yourfile.deb

---

### Post by greenwom on 2005-03-31
:oops: 
ok so I did the dpkg -i netzero.deb and the prompt went nuts as expected
now what?  I don't see any files on the machine? nor a application shortcut in the gn.    

---------------  :?:  NEW BEE BLUES  :?:  ----------------

I still don't have the wacom up and runnging :)

---

### Post by greenwom on 2005-03-31
I must be a complete retard, I've done everything everyone has offered 
and now I still have nothing working .... Well Ubuntu itself is working like a champ!

 :-({|= 

I haven't gotten the Wacom up, The DVD & MP3 player working, netzero, and I'm waiting to see is my linksys wireless card will work.

 :confused:

---

### Post by emperor on 2005-03-31
If your running warty, log out and then back in and see if you can find a launcher in the menu for netzero.

If that doesn't work, open a terminal and update the locate database and then do a search for "netzero"; the binary may be in /usr/bin. For example:

sudo updatedb
locate netzero

I would bet if you type:  netzero now the launcher will come up.

try it!

---

### Post by greenwom on 2005-03-31
Ok I've done what you said, when I type in Netzero to run I get nothing (command not found) ,  when I go {locate netzero I get a list of where some files are now located.  What should I look for.

BTW I am looking for some more on line tutorials to get a handle on all this, and I promise I will return the support when I know what I'm doing LOL


chicago mike
 :mrgreen:

---

### Post by emperor on 2005-03-31
The executable should be in a "bin" directory.
In may be in "/usr/local/bin" or "/usr/bin"

also see if there is a man file typing:

man netzero

or whatever the name of the binary file is

---

### Post by emperor on 2005-03-31
I downloaded the source tarball and it looks the binary may be "nzclient" and the package is installed in  the /opt directory tree.

---

### Post by greenwom on 2005-03-31
NO JOY ,   I want linux to work so bad...........

I'm at a lose, the DEB file was uncompressed.. and the install commands did there deed from what I can tell.    

Am I missing something?  This ubuntu install is days old and I've yet to install anythign on it.  Do I need something that I'm missing.   

Did the install come with everything?  I've read more than once about compling abd building drivers and such from scratch.  Does this warty install come with everything one needs to acomplich this?

drawing a blank (because my WACOM doesn't work)

 ](*,)  ](*,)  ](*,)

---

### Post by emperor on 2005-03-31
No, here is the info from the desktop icon. There is a script file in "/opt/nzclient"
called runclient.sh

/opt/nzclient/runclient.sh

I could send you the desktop icon via e-mail

---

### Post by greenwom on 2005-03-31
The desktop icons are there (in the folders)
I saw those when I ran $ locate netzero

I get (working with two computer so this will be short/ no cut and paste)

two icons
four documents (no help)
and a few files in /var/lib/dpkg/info folders


(also I've been reading the Wacom/Ununtu issue wiki and it's no help.  I have a serial wacom that's powered through a USB port (split wire)  The wiki speaks of a USB only device.  I  wondering if I'll be able to get it working at all (without re-inventing the wheel.
mike

(nice website emperor.)

---

### Post by emperor on 2005-04-01
It doesn't sound like it installed properly.

I would remove it if there is anything to remove via:

dpkg -r yourpackagename.deb

Here is a link to the source tarball:
[http://software.linspire.com/pool-src/n/netzero/]("http://software.linspire.com/pool-src/n/netzero/")

download to your home directory and then expand via:

tar -xzvf netzero_6.2.0b5-5.0.0.50.linspire0.3.tar.gz

change to the created directory directory (don't have to type all of it) for example:

cd marlin*

(then do the following)

make
sudo install

******
The other problem you may have is your modem!
What kind of modem do you have and was it detected by linux?
If you have a PCI modem, check vai "lspci" for your modem hardware
Also check "dmesg" or your system log file "/var/log/syslog"

Use "cat" to read the log files and pipe through "less", for example:

cat dmesg | less
cat /var/log/syslog | less

---

### Post by greenwom on 2005-04-01
well that download for netzero was different from what I got from them!

Anyway un compressed it -- ok
make --- ok
sudo install -- nogo ---[to few arguments]  So now what?


lspci -- I do see a line about my intel modem in there and assume that ubuntu   
            sees it. 

Anyway, I haven't had luck adding one thing to my new Ubuntu install but I have hope    ;) .

---

### Post by emperor on 2005-04-01
sudo make install

---

### Post by MaZiNgA on 2005-04-01
Sorry to interrupt here but when you typed Netzero up there, was it "Netzero" or "netzero"? It makes a difference! ;)

---

### Post by greenwom on 2005-10-04
Wow, it's been a few months since I started this post, I've learned allot from the forum and even helped a few folks.  
I know have 3 Ubuntu box's running, a Sony Viao, Dell Latitude LS and my desktop hp pavilion 503n (dual boot with Fedora).  I haven't used windows box (Dell Inspireon) w/ the exception of some old school/work software.  
It's kind of funny to look at my old posts and see how much I didn't know, not to mention how much I've learned.... Still a long way to go :-)

(I still haven't gotten my Wacom to work :)) that's tonights project.

---

### Post by greenwom on 2005-10-05
Well I followed the latest forum on wacom and 15 minutes later!!! it works.

I'm now 100% up

---

