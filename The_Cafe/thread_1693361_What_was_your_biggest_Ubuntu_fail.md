---
title: "What was your biggest Ubuntu fail?"
date: 2011-02-22
forum: The Cafe
---

### Post by TriBlox6432 on 2011-02-22
What was your biggest Ubuntu fail?

Mine was when I first installed Intrepid without actually looking into it much.  Wifi didn't work.  I was ****** and thought Ubuntu was some under developed weird . . . thing.  :P

It was completely my fault, but yeah.  xD

---

### Post by Hur Dur on 2011-02-22
Installing Fluxbox. It totally messed up Ubuntu, which caused me to uninstall Ubuntu and never look back.

Biggest Linux fail: Uninstalling Python in Debian.

---

### Post by whatthefunk on 2011-02-22
About two weeks ago.  I had been keeping a list of blacklisted modules in a file without the .conf extension.  I then read somewhere that the blacklisted module list should have a .conf extension so I went and changed the name to have a .conf on the end, completely ignoring the message telling me that a file of the same name already exists.  I started having all sorts of Windows like problems.  My computer would think for half an hour randomly and take for ever to start up.  Reinstall.  Wont make that mistake again:)

---

### Post by marl30 on 2011-02-22
Fooling around Gparted when I just started out. I ended up messing up my partition had to do a fresh install after I had installed a ton load of program and customized how I wanted.

---

### Post by slooksterpsv on 2011-02-22
parted fail

Was using parted, deleting a partition from my /dev/sda (where Ubuntu is installed) while in Ubuntu, ended up deleting the wrong partition, fat fingered 1 instead of hitting 2. Yeah, I freaked when ls wouldn't work.

---

### Post by SeijiSensei on 2011-02-22
Recently I was setting up a virtual server running CentOS 5.5.  For some reason, I needed to upgrade the OpenSSL libraries and couldn't find the right RPM.  So I uninstalled OpenSSL, and naturally I could no longer do much of anything over the Internet.  I had intended to download and compile a new OpenSSL, but none of my file-retrieval clients would run because they all needed the OpenSSL libraries!

Luckily my VPS provider has a nice facility where you can connect with SSH and mount the entire VM to the filesystem.  I could then fix the problem by manually inserting the correct OpenSSL rpm.  

Don't ask me about the time I accidentally used "rm -rf" as root in the wrong directory and deleted a full year of a client's invoicing records!

---

### Post by steve161 on 2011-02-22
> Fooling around Gparted when I just started out. I ended up messing up my  partition had to do a fresh install after I had installed a ton load of  program and customized how I wanted.

Same here.  The moment I clicked I realized my mistake.  Unfortunately, my cheap-*** computer does not recognize the "no...wait" voice command.

---

### Post by Quadunit404 on 2011-02-22
Accidentally wiped Windows and took everything with it when trying to move a Wubi install to a dedicated partition last November (iirc.) That, and my hard drive decided to delete the partition I created over Windows on reboot, leaving me with no OS. Now I know better.

---

### Post by sandyd on 2011-02-22
biggest fail: upgrading python to v2.6.
Completely screwed up portage, and couldn't emerge stuff for days until I dragged  it back on...

---

### Post by SE7EN-LOCSTA on 2011-02-22
trying to use xchat to irc... still failing :(

---

### Post by whatthefunk on 2011-02-22
> **SE7EN-LOCSTA said:**
> trying to use xchat to irc... still failing :(

Really?  I love xchat and have never had a problem with it...

---

### Post by cariboo on 2011-02-22
@SE7EN-LOCSTA

I use xchat daily, and never have a problem, maybe you should have a look at bodhi.zazen's xchat customization [page]("http://blog.bodhizazen.net/linux/xchat-customizations/")

---

### Post by false truths on 2011-02-23
I tried to use unetbootin to create a live .iso of Natty on my laptop. Ended up breaking GRUB and my /boot files in the process. I had to reinstall Ubuntu several times to get users to work properly (my computer hates the live cd because of user IDs). Then I had to re-download my 3gb of programs and set my desktop back up from scratch. I finished this about 2 hours ago.

I learned the hard way not to bother with unetbootin and partitions. Instead I'll stick to a flash drive for live boots and CDs for emergency repairs.

---

### Post by Legendary_Bibo on 2011-02-23
I messed around with some config file to fix the resolution of the splash screen. It ended up breaking the gui because I changed it to a setting that my graphics card didn't support, and I didn't know how to fix it from the terminal because I didn't memorize the location of the file, I just copied and pasted the command from a half baked guide. I had to reinstall it which was fine because I had a lot of applications that I didn't need.

---

### Post by lisati on 2011-02-23
A couple of years back, I blamed problems with XP on one machine on a botched installation of Ubuntu. The real culprit was XP's SP3, which needed a patch from HP/Compaq to be applied on said machine before the updated system would work properly.

---

### Post by Copper Bezel on 2011-02-23
I made the mistake of buying Softmaker Office recently, which has this little habit of corrupting .doc files simply by opening them.

I wanted to show off my Ubuntu environment to a colleague, and happened to open up a class handout in OpenOffice first.

I had a series of error messages and eventually had to force kill OOo. This was this guy's first experience with a Linux desktop: a series of error messages, resulting in a force kill.

That's pretty fail. = (

---

### Post by Irihapeti on 2011-02-23
Two that I can think of.

One, I went sudo rm /*/* -- no, DON'T try it just for fun. Result: reinstall.

Two, change ownership of all files in /usr to root. Doesn't work; result: reinstall.

That was a few years ago. I'm sure I must have done some awful things since then, but I can't recall anything specific.

---

### Post by Jagoly on 2011-02-23
> **Irihapeti said:**
> Two that I can think of.

One, I went sudo rm /*/* -- no, DON'T try it just for fun. Result: reinstall.

Two, change ownership of all files in /usr to root. Doesn't work; result: reinstall.

That was a few years ago. I'm sure I must have done some awful things since then, but I can't recall anything specific.

I stuffed up permissions on the weekend... for the ENTIRE HARD DISK!!!
My other partitions were mounted under linux mint...

---

### Post by daksai3 on 2011-02-23
**Biggest Fail: **I got Ubuntu. 
I'm serious but not in the way you might think. It's an addiction. I end up finishing my homework really late at night because I spend too much of my time playing around with Ubuntu.

---

### Post by Copper Bezel on 2011-02-23
> **daksai3 said:**
> **Biggest Fail: **I got Ubuntu. 
I'm serious but not in the way you might think. It's an addiction. I end up finishing my homework really late at night because I spend too much of my time playing around with Ubuntu.

++. Like right now.

---

### Post by daksai3 on 2011-02-23
YUP. I should be writing a short story for english class right now...

2:20 am right now for those that arent in my zone. XD

---

### Post by linuxforartists on 2011-02-23
> **Legendary_Bibo said:**
> I just copied and pasted the command from a half baked guide.

I've made this mistake multiple times.  Sometimes you're just so desperate for a solution you'll run anything in Terminal to fix the problem.  Only to make things worse.  Usually, it's because I entered an outdated bash script I found online.

Would have kept making this mistake if not for an Australian techie friend.  He recommended using Google "Advanced Search" to get the most recent results:

[B]Google > Advanced Search > Date, usage rights, numeric range, and more > Date: (choose "Past Year")

[/B]Works like a charm!  Now I'm always able to get the most up-to-date solutions. 

Now if I could just fix my crashed LAMP server setup.  I got the LAMP working okay, but I stupidly forgot to install phpMyAdmin.  When I tried, I got all kinds of error messages.

---

### Post by mr_luksom on 2011-02-24
Trying to create a startup USB with usb-creator, I accidentally chose my usb harddrive, and wiped my wedding photos. No backups with us (maybe the photographer, but we had nothing).

That is when I learned to photorec.

---

### Post by Copper Bezel on 2011-02-24
I tried to create a USB startup disk by booting from a Live CD. Lost my MBR, thus, rendered the machine I was doing it on unbootable. = )

---

