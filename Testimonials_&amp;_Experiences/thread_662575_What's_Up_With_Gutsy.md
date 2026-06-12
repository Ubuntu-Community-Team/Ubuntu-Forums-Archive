---
title: "What's Up With Gutsy?"
date: 2008-01-09
forum: Testimonials &amp; Experiences
---

### Post by mntlasasin on 2008-01-09
I have been using Gutsy since it released; I originally upgraded from Feisty. I have had to reinstall the OS three times now. I am not sure what is going on. I never had this problem with Feisty, Edgy, or Dapper. The problems that I am experiencing are slow system response and constant freezing of the OS; the mouse moves but you can not select anything. I have let it sit for over an hour once and it never released. I love Ubuntu, but I am looking at other OS's at the current time.

---

### Post by armandh on 2008-01-09
I would suspect hardware 
does it lock up running live cd?
I once spent a week chasing problems [a loose Hdd cable] thinking GD windows
my experience has made me look to hardware first

---

### Post by peachy on 2008-01-09
i've got the same general feeling about Gutsy, it doesn't seem to be as responsive as previous releases. I can't really pin it down. Gutsy server is fine, no problems there.

As negative as it sounds i'm not sure I can be bothered to work out the problem. I have always run Ubuntu as it has been a zero effort zero maintainance OS, i'm looking at my options now, i think PC-BSD looks good once they incorporate the ipw3945 driver.

---

### Post by observative on 2008-01-09
I HAD the same exact bug, and so do so many people its not funny. Take a look here ([https://bugs.launchpad.net/ubuntu/+bug/177439](https://bugs.launchpad.net/ubuntu/+bug/177439)) I know it says nfs in the bug report I'm referring to, but there are so many other threads that point to the same solution. It tells you how to do a temporary work around using the synaptic to rollback the kernel update. Its near the bottom look for the steps 1. 2. 3. etc.., and if you have Gutsy you're searching for 2.6.22-16 and if you have Fiesty you're searching for 2.6.20-16. The steps leave a bit to be desired as they are not exact. Between step 1 and 2 click the "Status" button or your you won't see the "installed" link in step 2. I have re-installed Ubuntu enough times to see that after an update the crashing begins! And after limiting what gets updated, I have isolated it to the kernel update.

Hope this helps and solves the mysterious "Lockup". I believe it will, as it did for me.

EDIT: Ok, so I'm really sorry but after a few more re-boots the above info that I dug up only made the bug worse. In fact, it got so bad that I'm back on my windows boot so I can post this. Personally I have spent enough time wasting time on Ubuntu. I never thought I would say that after being so excited about moving off Windows and on to a Linux box...I feel real disappointed at this point. Perhaps I will give it a try after I retire, for now back to the money maker Windows.

---

### Post by conehead77 on 2008-01-09
> **observative said:**
>  ... for now back to the money maker Windows.

If Feisty worked, you have the option to reinstall it instead of Gutsy. Well, your choice.

---

### Post by snakeeyes on 2008-01-10
I seriously suggest upgrading to Hardy's development kernel, it solved all my 7.10 problems.

---

### Post by observative on 2008-01-10
snakeeyes:
Thats good to know. I'm willing to give upgrades a try. Hope it solves my gutsy bugs too. Do you have a link for downloading Hardy?

conehead77:
Gutsy is my first entanglement with Ubuntu, and I hate downgrading cause eventually you have to upgrade. But just the same thanks for the push of confidence. I've been really frustrated with Ubuntu not working any better than expected, especially after so many releases. I might be using windows to make money today, but I sure hope it will be Ubuntu in the near future :)

---

### Post by conehead77 on 2008-01-10
> **observative said:**
> conehead77:
Gutsy is my first entanglement with Ubuntu, and I hate downgrading cause eventually you have to upgrade. But just the same thanks for the push of confidence. I've been really frustrated with Ubuntu not working any better than expected, especially after so many releases. I might be using windows to make money today, but I sure hope it will be Ubuntu in the near future :)

My mistake, i thought you were the OP :oops:

---

### Post by snakeeyes on 2008-01-11
No, I think u misunderstood me. I meant that u start using the Hardy kernel which is Linux kernel 2.6.24-3. Its a lot more stable and solved all my problems. I had a lot of issues with Gutsy default kernel 2.6.22-14. Hardy's kernel is a lot more stable. I will give u the instructions on upgrading but tell me r u using a desktop or a laptop, and what vga card do u use and other detail about ur hardware.

---

### Post by observative on 2008-01-11
Yep I did misunderstand. I was hoping not to have to upgrade to an alpha 3 version lol. Ok, here's my specs;

- 1ghz Intel on an ASUS motherboard
- Ultra 66 PCI card for my WDC hd's*
- 1 WDC 40gb (for my dual boot w2k server and Gutsy)*
- 1 WDC 120gb (used as a shared drive)*
* located on Ultra 66 not the primary IDE.
- Matrox Millennium G200 video card
- Acer AL2223W lcd monitor
- Realtek RTL8139 Fast Ethernet NIC
- DVDRW IDE 1008**
- E-IDE CD-950E/TKU**
** located on the second IDE.
- PS2 mouse w/wheel and standard 107 keyboard
- Epson Stylus CX6000 printer/scanner

Thanks for the help snakeeyes :)

conehead77: What does "OP" mean?

---

### Post by snakeeyes on 2008-01-11
Hi, ok I am not sure whether u r using as nvidia or an ati card. I am sorry I don't have any experience with an ati or intel card, but here u go.

If u r using an nvidia card then just do this:

In terminal type:

sudo nano /etc/apt/sources.list

At the bottom of the file enter this new repo:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

press ctrl+o to save and then ctrl+x to exit

sudo apt-get update

sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic nvidia-glx-new

After the install reboot into the new kernel and everything should work perfect.

Now just remove the hardy repository u added before and be careful to not upgrade from it.

If u were using envy then u may have to reinstall the driver and before upgrading to the new kernel remove the previous nvidia or ati driver other wise the new kernel won't boot.

If u r using an ati card then instead of installing nvidia-glx-new at the end type in what the ati drivers r called, I am sorry I don't know much about ati.

Intel cards should be detected by default and remember to remove the hardy repo from your list.

Visit this thread for more info:

[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Good Luck!

:)

---

### Post by frodon on 2008-01-11
First you don't have to upgrade to hardy to use the hardy kernel, this is not mandatory.

tutorial on the topic :
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Other kernel you can try easily :
[http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

Try these to kernels then tell us if you have still the same issues.

---

### Post by snakeeyes on 2008-01-11
> **frodon said:**
> First you don't have to upgrade to hardy to use the hardy kernel, this is not mandatory.

tutorial on the topic :
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Other kernel you can try easily :
[http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

Try these to kernels then tell us if you have still the same issues.
I am not telling him to upgrade to Hardy, these instructions will only install Hardy's Linux kernel 2.6.24-3.

---

### Post by frodon on 2008-01-11
Sorry but i was not answering your post.

---

### Post by observative on 2008-01-11
Thank you very much. Yes I understand that I'm not upgrading to Hardy, just the kernel. I'll go have a look and give it a shot.

From what I have read, Matrox is neither ATI or nVidia, it is an older card made by Matrox. The drivers for it come standard with all versions of Ubuntu, no special permissions or configuration needed. Although I did update the drivers that came with Ubuntu Gutsy with some help from [http://forum.tuxx-home.at](http://forum.tuxx-home.at).

---

### Post by snakeeyes on 2008-01-11
> **frodon said:**
> Sorry but i was not answering your post.


oh ok no problem :)

---

### Post by snakeeyes on 2008-01-11
> **observative said:**
> Thank you very much. Yes I understand that I'm not upgrading to Hardy, just the kernel. I'll go have a look and give it a shot.

From what I have read, Matrox is neither ATI or nVidia, it is an older card made by Matrox. The drivers for it come standard with all versions of Ubuntu, no special permissions or configuration needed. Although I did update the drivers that came with Ubuntu Gutsy with some help from [http://forum.tuxx-home.at](http://forum.tuxx-home.at).
Hey ok, if your drivers r default in ubuntu then just upgrade the kernel, no need to upgrade any drivers.

---

### Post by observative on 2008-01-11
Thanks for confirming that, guess thats what I was getting at with the video drivers being default.

---

### Post by Ripfox on 2008-01-11
If you have problems with Gutsy, I seriously recommend just installing Feisty until Hardy is released.

---

### Post by conehead77 on 2008-01-11
> **observative said:**
> 
conehead77: What does "OP" mean?

OP = original poster, the one who started the thread

---

### Post by observative on 2008-01-23
Here's my follow-up after following everyone's advice...Thank you all for the input, it was quite the experience following some of the help :).

It was hardware configuration that caused Gutsy lock up ,at least for me. So I must send the thank you "kudo" to [armandh]("http://ubuntuforums.org/member.php?u=345993") for the hardware advice :KS.

It turns out that over the years of trying to get Windows to operate the way I wanted and the replacement/upgrading of hardware, that my cmos and a few card's bios' where not up to date, or not optimally configured/installed. While trouble shooting, I noticed that if I skipped pci slots or used any extra hardware that I didn't use (ie extra drive controllers) Gutsy would lock up at random...amongst the myriad of other difficulties I was having...like ntfs mount/access/write. Perhaps this finding will help some with older systems manufactured post-2k.

Everything works beautifully now! and I mean everything including the dual boot share of Thunderbird, Firefox, and a few other applications. Even though I am not running a modernly fast system, Gutsy is at least equal to my old w2k if not a bit faster. And the "new" features like multi desktops is really cool.

Now I can seriously consider using Ubuntu for my new "money maker" \\:D/and truly leave Windows and Gates for the openness of Ubuntu.

In short, "What's Up With Gutsy?", some really great stuff, thats what!

---

### Post by slimordium on 2008-02-25
I have the following machine (Dell XPS 410)
Intel Core 2 Duo
Nvidia geForce 8300 GS

On which I am having similar problems. After new install of Gutsy, and first boot, the system hangs after the splash screen. I have let the system sit in this state and it never recovers. 

I have seen others having very slow boot times, but this does not seem to be the case. Unless it is over 30 min or more. It freezes at the round waiting cursor, you can still move it around but nothing else.

---

