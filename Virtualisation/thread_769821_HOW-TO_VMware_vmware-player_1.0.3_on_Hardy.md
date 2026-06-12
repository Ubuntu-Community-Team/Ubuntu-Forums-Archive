---
title: "HOW-TO VMware vmware-player 1.0.3 on Hardy"
date: 2008-04-26
forum: Virtualisation
---

### Post by gary vollink on 2008-04-26
Edit : According to a new post; vmware-player-2.0.4 is out, it doesn't need the correction below.  I have tried this, so unless you specifically need 2.0.3, it is worth downloading 2.0.4 first.  See post: ([http://ubuntuforums.org/showthread.php?p=5087761#post5087761](http://ubuntuforums.org/showthread.php?p=5087761#post5087761))
 --------------------- (end edit)

I found that vmware-any-any-patch115 was not necessary (and doesn't work).

I did need to make a manual patch to one file in the installation folder

Here's what I did...
-----
Unpack vmware-player-2.0.3.tar.gz (to my home dir)

Open terminal ---
% cd ~/vmware-player-distrib
% cd lib/modules/source
% tar xvf vmmon.tar
vmmon-only/
....
% cd vmmon-only/include
% vim vcpuset.h  (any text editor will do)

In your editor ---
* Search for bitops.h
* First found is in a comment
* Second found should look like: #include "asm/bitops.h"
* Change that line to: #include "linux/bitops.h"
Save the File
Exit the Editor

In your terminal (recreate the tar file)
% cd ~/vmware-player-distrib/lib/modules/source
% mv vmmon.tar vmmon-old.tar
% tar cvf vmmon.tar vmmon-only
vmmon-only/
...
% cd ~/vmware-player-distrib
% sudo ./vmware-install.pl

(Then it installed normally for me).

---

### Post by kenred on 2008-04-27
Oh, thanks mate! 
That helped me a lot, btw it did work for VMPlayer 2.0.3 for me

---

### Post by slo0th on 2008-04-27
I upgraded to Hardy Heron and it broke my VMware workstation. Re-installing and using this method works for workstation. Thanks.

---

### Post by starbase1 on 2008-04-27
> **gary vollink said:**
> I found that vmware-any-any-patch115 was not necessary (and doesn't work).

I did need to make a manual patch to one file in the installation folder

Here's what I did...
-----
Unpack vmware-player-1.0.3.tar.gz (to my home dir)

Open terminal ---
% cd ~/vmware-player-distrib
% cd lib/modules/source
% tar xvf vmmon.tar
vmmon-only/
....
% cd vmmon-only/include
% vim vcpuset.h  (any text editor will do)

In your editor ---
* Search for bitops.h
* First found is in a comment
* Second found should look like: #include "asm/bitops.h"
* Change that line to: #include "linux/bitops.h"
Save the File
Exit the Editor

In your terminal (recreate the tar file)
% cd ~/vmware-player-distrib/lib/modules/source
% mv vmmon.tar vmmon-old.tar
% tar cvf vmmon.tar vmmon-only
vmmon-only/
...
% cd ~/vmware-player-distrib
% sudo ./vmware-install.pl

(Then it installed normally for me).

Sorry for some dumb questions here, but I understand about 1 line on three of what you have written!

I want to get vmware player running in my shiny new Hardy Heron 64 bit installation. The catch is I have no net connection under Ubuntu.

Can I follow the steps you list above to get the vmware player running on my PC without an internet connection active? It also looks from my limited understanding that this is a correction to some other routine that I am unaware of - are you fixing something for special circumstances or is there an easier way to get this working that should work for me?

Thanks, Nick

---

### Post by gary vollink on 2008-04-27
> **starbase1 said:**
> 
Can I follow the steps you list above to get the vmware player running on my PC without an internet connection active? It also looks from my limited understanding that this is a correction to some other routine that I am unaware of - are you fixing something for special circumstances or is there an easier way to get this working that should work for me?
Thanks, Nick

Background then...

VMware requires a small number of kernel modules for it to work properly.  These Kernel Modules are automatically built during vmware-player installation ( using the vmware-configure.pl script ).  Whenever the version of kernel changes, the "old" kernel modules are no longer available (this happens on major upgrades).  Normally, vmware-player can recompile the kernel modules (using vmware-configure.pl).  However, the source code for these modules has one line which is incompatible with the Hardy kernel / kernel source tree.  My instructions are about accessing the file with the error, patching that line, putting the patched source back into the place where the installer will take it, and then installing the vmware-player package.

* Technically - installing vmware-player takes the tar file that my instructions is replacing and puts it somewhere else (I didn't bother finding out where), and then vmware-configure.pl will build the modules from that new location...

I have only done this using the installable tar-files from vmware (2.0.3).  There is also a good possibility that 2.0.3, specifically, includes other changes that make vmware-player compatible with newer kernels, I say this, partly, because the vmware-any-any patch (see below) is no longer needed.

Finally, mention of vmware-any-any patch is about a patch-set for versions of vmware (prior to 2.0.3) to get those same modules compile on Ubuntu 7 versions.  So, it is likely that my instructions will not help you unless you already have 2.0.3 - and can both follow my instructions, and adapt them to wherever your 2.0.3 source is installed.

 ----

My recommendation is to get vmware-player-2.0.3 from some other computer, and follow my instructions (or get help following my instructions, one line at a time, by searching here or linuxquestions.org.

Overall - the process requires command-line access, (no Internet, once you have the vmware-player installation file), and a lot of patience with learning the command line tools that I refer to.

---

### Post by starbase1 on 2008-04-28
Thanks for such a clear and detailed explanation, I understand now.
:biggrin:

---

### Post by woko on 2008-04-29
Thanks for your posting. It helped me to install VMware-Player on Debian Lenny !

---

### Post by smithji2005 on 2008-04-29
Awesome!  Much thanks!

---

### Post by rfs1970 on 2008-04-29
You are the man!
Thank you very much for your help/time.

r.

---

### Post by karlatsaic on 2008-05-02
Brilliant. Upgraded to 8.04 yesterday and vmplayer was the only thing that didn't work. A quick search on this forum and 5 min after reading this post, all is great. THANK YOU!

---

### Post by mad-kow on 2008-05-03
I finally got the vmware player 2.0.3 working here again after the upgrade to hardy, following the steps you've posted.
Thanks for your help :)

---

### Post by ilikeopensource on 2008-05-06
You ROCK :guitar:
Thank you so much !!!

---

### Post by krazysmile on 2008-05-15
Hey every1.

i managed to install VMware Player 2.0.3 on ubuntu 8.04 
with this instructions.

now i'm wondering, isn't there a similar solution for installing vmware server on 8.04? cause i'm having the same compilation problems.

regards

---

### Post by gary vollink on 2008-05-18
> **krazysmile said:**
> now i'm wondering, isn't there a similar solution for installing vmware server on 8.04? cause i'm having the same compilation problems.

I think there is a newer VMWare-any-any patch for the server install.  I, for one, don't use the Server on Ubuntu, but I know I've seen a post about using that patch-set somewhere...

---

### Post by mike78_at on 2008-05-19
Thank you very much! I have just upgraded to 8.04 and vmplayer was the only package, which didn't work anymore.

---

### Post by Roo on 2008-05-20
I found this thread when I was trying to solve my Hardy upgrade problem.  Mostly the upgrade was smooth, but my vmware player install broke.

Like others, the steps in discussed in this thread helped me fix my problem and I can run my existing images fine.

I was previously running vmware player 2.0.2.  So I was required to first run the uninstall 
```
sudo vmware-uninstall.pl
```
Then I downloaded the new 2.0.3 from [http://www.vmware.com/download/player/download.html]("http://www.vmware.com/download/player/download.html")
and followed the steps in the [1st post]("http://ubuntuforums.org/showpost.php?p=4807296&postcount=1") of this thread.

Trying to follow the instructions in the 1st post without the uninstall step did not work for me (duh in retrospect).

Roo

---

### Post by sim909 on 2008-05-25
Thanks!
I had previously installed vmware with the any any patch, but it was giving me problems and I eventually lost all connectivity on my hardy.

All seems solved now!

thanks,
S

---

### Post by v4169sgr on 2008-05-31
Just as a FYI, it looks like the new VMWare player v 2.0.4 does not suffer from the problem that this thread tries to address.

Let me put it this way: I saw this thread, followed the directions, saw that I already had the correction in place, installed anyway and found that all has worked perfectly.

This is with 8.04.

---

### Post by gary vollink on 2008-06-01
v4169sgr, I have edited the top of my original post to point poeple to the newest version.  Hopefully this will help avoid the additional work.  ;-)

---

### Post by sunbird on 2008-06-03
I've followed all of these steps and vmplayer 2.03 still won't start. Running 8.04x64. All the modules "compile perfectly in the loaded kernel" but it still doesn't run. Any help?

**Edit:** It works now. I just uninstalled and reinstalled and now it works fine. I also deleted the /usr/bin/vmware directory, which for some reason was not completely removed after the uninstall. In any event, it's working now. :)

---

### Post by gary vollink on 2008-06-03
Sunbird, I would have to suggest that you download and run 2.0.4 at this point.  However, try to start vmware-player from the command line... Are there any errors output?  Those errors might point you (or someone here) in the right direction.

---

### Post by weaponx69 on 2008-06-18
Hi,
   I saw your link in VMware workstation posts and followed it here.  I'm thinking that what your talking about is related to my problem.  I installed VMware player by converting the .rpm to a .deb and then adding lines to a config file.  Everything compiled and boots up with icons but when I tried to run a team it said that I had the incorrect vmmon module.  It said that it expected 168.0 but saw 167.0.  It suggested that I try to reinstall vmware workstation.  Here is the exact error message.

"Version mismatch with vmmon module: expecting 168.0, got 167.0.
 You have an incorrect version of the `vmmon' kernel module.
 Try reinstalling VMware Workstation."

Any clue what I need to do?  Maybe I can go into synaptic and swap modules.  It seems like an easy problem to fix.

---

### Post by gary vollink on 2008-06-22
> **weaponx69 said:**
> Hi,
   I saw your link in VMware workstation posts and followed it here.  ...  I installed VMware player ... it said that I had the incorrect vmmon module.  It said that it expected 168.0 but saw 167.0.

...

Any clue what I need to do?  Maybe I can go into synaptic and swap modules.  It seems like an easy problem to fix.

Get the vmware-workstation install files.  Just like player, it will also have the source somewhere accessible.  (I use the tar.gz for player, maybe the same is available for workstation?)

vmware-workstation install itself should also be attempting to install the VMMon module, you'll just need to figure out where it is trying to keep it's copy for compile...  Then, totally un-install the vmware player stuff, and re-install workstation.

---

### Post by nossifer on 2008-06-25
good news / bad news.  mainly good.

i pulled down the sourceforge enterprise vmware appliance.  the instructions offered in the beginning of this thread did not work.

i then pulled down 2.0.4 .tar from vmware and it worked perfectly.  no mucking around required.

on hardy, gnome, all updates, etc.

---

### Post by AmanicA on 2008-06-26
> **weaponx69 said:**
> Hi,
   I saw your link in VMware workstation posts and followed it here.  I'm thinking that what your talking about is related to my problem.  I installed VMware player by converting the .rpm to a .deb and then adding lines to a config file.  Everything compiled and boots up with icons but when I tried to run a team it said that I had the incorrect vmmon module.  It said that it expected 168.0 but saw 167.0.  It suggested that I try to reinstall vmware workstation.  Here is the exact error message.

"Version mismatch with vmmon module: expecting 168.0, got 167.0.
 You have an incorrect version of the `vmmon' kernel module.
 Try reinstalling VMware Workstation."

Any clue what I need to do?  Maybe I can go into synaptic and swap modules.  It seems like an easy problem to fix.

I got it working by copying the vmmon.tar
from my vmware source
 vmware-player-distrib/lib/modules/source/vmmon.tar
to the patch
 vmware-any-any-update116

and then ran vmware-any-any-update116/runme.pl

thanx to this blog comments:
[http://liken.otsoa.net/blog/comments.php?entry=entry080301-173023#comment080618-202038](http://liken.otsoa.net/blog/comments.php?entry=entry080301-173023#comment080618-202038)

---

