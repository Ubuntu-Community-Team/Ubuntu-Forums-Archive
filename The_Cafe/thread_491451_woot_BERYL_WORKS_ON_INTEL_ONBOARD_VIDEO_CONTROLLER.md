---
title: "*woot* BERYL WORKS ON INTEL ONBOARD VIDEO CONTROLLER"
date: 2007-07-03
forum: The Cafe
---

### Post by Prometheus.172214 on 2007-07-03
First the lapto specs : 

Processor : 1.6 Ghz single core Pentium Mobile
Systemboard Chipset : Intel 915 Mobile Express
Memory : 512 Mb
Ubuntu Version : Feisty Fawn Base Installation For X86 

                                                                 Beryl was installed and Beryl and Emerald Themes Manager work perfectly here..... No system issues, no problems at all. . . . Here is what I did.

I use the GUI, since I am not very good with manual work via a terminal...

SYSTEM >> ADMINSTRATION >> SOFTWARE SOURCES >> THIRD PARTY.

ADD >> ```
deb http://ubuntu.beryl-project.org feisty main
```
 and click OK. It will ask you to Reload the database and then tell you that the GPG key was not found. Don't worry.

Press ALT and F2 togethar and type terminal and click OK. Iit will launch a terminal . . . . copy and paste the code below and hit enter 

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add - 

```

if it goes right, you should see some information about the download at the end....

Now type the next line of code into the same terminal

```
sudo apt-get update
```

This will update the database and will confirm the same. You need working Internet connections for all codes entered into the terminal....

Now, in the terminal, type the next code string
```
sudo apt-get install beryl-manager beryl-settings
```

This will download and install the Beryl Manager, it will prompt you for installation and when it does, hit Y and hit enter to start the download and installation of this package.

Now, in the terminal, type the next code string
```
sudo apt-get install emerald emerald-themes
```
This will download and install the Emerald Theme Manager, it will prompt you for installation and when it does, hit Y and hit enter to start the download and installation of this package.

Now, in the terminal, type the next code string
```
sudo apt-get install emerald-themes
```

This will download and install the themes for Emerald....

Great you are done with the work.

Now APPLICATIONS >> SYSTEM TOOLS >> BERYL MANAGER.
This will put a Red Diamond icon on the top right of the screen, where you have the date and time. Click it once to see the options.

SYSTEM >> PREFERENCE >> EMERALD MANAGER will give you access to the themes.

This is just what I did and I am hopin, it will work for others........ If it does not, unfortunately I am also a novice and so, it is a request that you ask a being with greater intellect than me, to get an answer......

The final say, a competing operating system has a good interface that needs 2Gb ram and 512 mb video memory for smoothest performance and in my system, I have exceptionally smooth performance with the specs mentioned above..... Boy, I am happy.....

---

### Post by beercz on 2007-07-03
I know - had mine working for months :-)

---

### Post by macogw on 2007-07-03
Why use the Beryl repos?  Those are generally outdated as compared to Ubuntu's.  Beryl is in Universe.  All you had to do for Intel graphics is "sudo apt-get install beryl emerald-themes"

---

### Post by Prometheus.172214 on 2007-07-04
Macogw : You are speaking to a total novice..... What I wrote above is not my solution, but what I did from my research on the internet. I just wanted to put the same sequence of steps so others like me can try it..... So, you are saying that I can install this fine, if I run the code you mention..... cool
:popcorn:

---

### Post by PriceChild on 2007-07-04
Did you know that Ubuntu includes Compiz by default? System > Preferences > Desktop Effects> **macogw said:**
> Why use the Beryl repos?  Those are generally outdated as compared to Ubuntu's.  Beryl is in Universe.  All you had to do for Intel graphics is "sudo apt-get install beryl emerald-themes"The 0.2.0 in the beryl repos and the 0.2.1 in the Ubuntu repos are the same... the ubuntu version just has better packaging to comply with policy.

---

### Post by Prometheus.172214 on 2007-07-04
Yes, I was aware that Compiz was there in F.F. However I was not very sure on how to perform theme management tasks and I mainly am using this system to learn as much as I can about Linux . . . So, that was the real reason I tried Beryl......

---

### Post by ceelo on 2007-07-04
Yep, have never had any problems with my Intel chip either.

---

### Post by orange2k on 2007-07-04
> **ceelo said:**
> Yep, have never had any problems with my Intel chip either.

Intel chips have community developed drivers, as far as that is concerned, they are even better than NVidia and ATI...

---

### Post by Prometheus.172214 on 2007-07-04
Well, I have tried this on my laptop unit that has the Intel Onboard 915 Video Controller and like I said, it works like a dream. I have a desktop, which runs on ATI Corssfire. At the moment, I am waiting for part replacements due to a fried systemboard. So, I am sure to give this a try, once the desktop goes on and am keeping my fingers crossed that the ATI guide works for the system.

---

### Post by macogw on 2007-07-05
> **Prometheus.172214 said:**
> Macogw : You are speaking to a total novice..... What I wrote above is not my solution, but what I did from my research on the internet. I just wanted to put the same sequence of steps so others like me can try it..... So, you are saying that I can install this fine, if I run the code you mention..... cool
:popcorn:
It's also in Synaptic (and therefore probably in Add/Remove), so instead of typing in the apt-get, you can just click the checkboxes for Beryl and Emerald themes too.

---

### Post by Tux Aubrey on 2007-07-05
> It's also in Synaptic (and therefore probably in Add/Remove), so instead of typing in the apt-get, you can just click the checkboxes for Beryl and Emerald themes too.

That's what I did as soon as Feisty came out and all was fine.  What was the question again? Did I miss something?

---

### Post by skooter on 2007-07-06
You say intel onboard graphics works well...? I can't even get my GMA X3000 installed. What video card you have? And where can i find info to install?

---

### Post by walkerk on 2007-07-06
Just so you know.. Compiz-Fusion works aswell :) I have it running on a 945GM onboard intel

Runs great!

---

### Post by reacocard on 2007-07-06
I also have an i915, beryl worked great, but compiz fusion runs even better. (aside from the occasional crash...)

---

### Post by macogw on 2007-07-06
> **skooter said:**
> You say intel onboard graphics works well...? I can't even get my GMA X3000 installed. What video card you have? And where can i find info to install?
In a #ubuntu discussion the other day, I think the person had that working for 2D with generic drivers but not 3D.  I think the problem is that that card is too new for the drivers to be in Feisty's kernel.  I think the last graphics set to have drivers in the kernel was i945, and X3000 is i965.  They'll probably be in Gutsy's (I would hope).  Intel's are always open source, so you can just download and compile them.  I looked around, and someone built a deb for the i965 chipset drivers.  You can get it here [http://home.teleos-web.de/obrackmann/libgl1-mesa-dev_6.5.1~20060817-0ubuntu3+local1_i386.deb](http://home.teleos-web.de/obrackmann/libgl1-mesa-dev_6.5.1~20060817-0ubuntu3+local1_i386.deb)

---

### Post by skooter on 2007-07-07
Thanks macogw. 

Also take a look at this: [http://ubuntuforums.org/showthread.php?p=2978382#post2978382](http://ubuntuforums.org/showthread.php?p=2978382#post2978382)

---

### Post by mytwobears on 2007-07-07
Thanks for the info. Prometheus.  I have the same specs that you do, so I am happy to hear that it's working for you.  I have been hesitant to try it, even though i really, really want to.

I assume that you are running Feisty Fawn, however, I am still running Ubuntu 6.10, do you think that will be problematic.  Also, do you think the size of the hard drive Ubuntu  is on matters for trouble free operation of Beryl?
 
If these issues matter, I will just wait until I upgrade my desk top with new hardware and Feisty Fawn.  Thanks for your feedback :).

---

### Post by Prometheus.172214 on 2007-07-09
Well, for starters, I did not try Beryl on E.E., I decided to update to F.F a few days ago and the moment, I did I had Compiz working. But, I wanted to try Beryl and that led to trawling the internet and then this post. A few weeks ago, I did try getting Beryl on the E.E installation I had, however I the gpg key did not download at that time and I did not try again. This could have been due to a slower internet connection I had at that time. So, I cannot be sure. The file sizes that I observed for the installation where quite small and also, the memory usage of Beryl itself is not extremely high. Disc space in my opinion should not be a big problem, unless you have a very full hard drive with less than 2 ~ 3 % free space. the swap partition on my HDD is 1Gb and I am assuming that the files are run from there.  Let me try Beryl on an E.E system my friend has an I will get back to you.

P.S. Apologize for a delayed response. I was on a weekend tour to a different city and had no access to the internet.

---

### Post by Prometheus.172214 on 2007-07-09
I have heard a few people mentioned issues with getting it to work on the newer Intel drivers. My system is a an older one and uses the Intel 915 Onboard video. System specs are mentioned in the first post of this thread. Did you check the xorg config file to get the details of the adapter. Most of what I did came from here:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)

---

### Post by mytwobears on 2007-07-10
I believe I have your exact specs, I also have the 915 onboard video chip, my swap is 1 GB as well and I have maybe about 50% of my HD available.  I've just been very hesitant since so many people seem to have problems with it.  But I will probably just jump in and try it, maybe :).  

If you do test it on your friends system with Edgy, please let me know.  Thanks for helping.


Edits:  Thanks for the wiki, now that I am seriously considering taking the plunge, I'll look around to see if there is any Edgy specific guidelines.

---

### Post by argie on 2007-07-10
> **walkerk said:**
> Just so you know.. Compiz-Fusion works aswell :) I have it running on a 945GM onboard intel

Runs great!

Yeah, it works wonderful. Only the blur effects don't work.

---

### Post by bakie on 2007-07-18
sweet, works great for me. Thx for the help :)

---

