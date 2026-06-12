---
title: "Solved! VirtualBox +12.04 Installation Pro ((rc=-1908) + '/etc/init.d/vboxdrv setup')"
date: 2013-10-10
forum: Virtualisation
---

### Post by Jeff_Berrian on 2013-10-10
*SOLVED* (read below OP)

So I am running into this seemingly common issue with installing virtualbox. Yes, I am getting the (rc=-1908) "virtualbox-dkms" kernel error with the [COLOR=#0000FF]'/etc/init.d/vboxdrv setup' [/COLOR]message and after trying various proposed solutions to the problem, I am still stuck at square one. 

I've searched and mined through multiple threads and tried and tried to follow all proposed solutions to no avail. The issue I am having is that most of the solutions and members proposing them seem to vary considerably on how to resolve the problem particularly the steps to follow and where/how to start them.

I am relatively new to using Ubuntu so what helps someone out like me the most is having a solution with the exact steps outlined to follow like what to type into terminal/CL and all of that.

I am taking the time and effort to learn and the growing pains are expected. I am fine with that but when I try multiple solutions on threads marked 'solved' to no avail, it stings. Or when a thread is marked 'solved' and the solution is generally described with no real steps to follow (i.e. Run this line...set your repository source to this...download the latest .deb and install after updating to the latest dkms through synaptic.). I am not complaining out of bitterness b/c any knowledge helps toward finding a solution, but I have yet find the common solution to this seemingly common problem. 

I remain optimistic the solution is out there! 

I'll digress...

Can someone provide a bit more clarity on how to resolve this virtualbox installation issue particularly for newbie's? If possible, we could use the exact steps to follow with your proposed solution. I am running Ubuntu 12.04 64-bit and downloaded/installed VirtualBox via the Ubuntu Software Center. VirtualBox doesn't really fully install throwing a "A problem with the system occurred" window along with the issue described above regarding "virtualbox-dkms" kernel?

Thank you!

(Apologies for yet another thread on this issue however this one is for the noobs!).


****SOLVED****

For anyone (including newbs) who want to solve this common issue, here's what worked for me:

* Uninstall/Remove VirtualBox from your system completely by going into Terminal ctrl+alt+T and typing:

            "sudo apt-get remove --purge virtualbox"

Step 1: Next, download VirtualBox (.deb file) DIRECTLY from this link: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) 
Note: This version of VirtualBox is the Oracle version. Be sure to choose your  the appropriate package for your Linux distribution. If you're using Ubuntu 12.04 64-bit for example, download the associated .deb file from list.

Step 2: Open Ubuntu Software Center. Search and Install "gdebi" - this application will manage/open/install the .deb package you've just downloaded. 

Step 3: Locate the VirtualBox .deb file on your system. Mine was located in Home/Downloads b/c I used Firefox to download the .deb package from the link in Step 1. Once you found the VirtualBox .deb file, right-click > properties > "Open With" tab > Select "GDebi Package Installer" as your Default Application to open .deb files.

Final Step: Double-Click the VirtualBox .deb file (now associated with gdebi) and gdebi will install VirtualBox for you. 

Done!

I've confirmed that I was able to successfully launch VirtualBox by following these steps outlined above.

Good Luck!!!

Special Thanks to ibjsb4 for pointing me in the right direction :)

---

### Post by ibjsb4 on 2013-10-10
This is my fix :)

[http://ubuntuforums.org/showthread.php?t=2175822&p=12795536&viewfull=1#post12795536](http://ubuntuforums.org/showthread.php?t=2175822&p=12795536&viewfull=1#post12795536)

---

### Post by Jeff_Berrian on 2013-10-10
> **ibjsb4 said:**
> This is my fix :)

[http://ubuntuforums.org/showthread.php?t=2175822&p=12795536&viewfull=1#post12795536](http://ubuntuforums.org/showthread.php?t=2175822&p=12795536&viewfull=1#post12795536)

Thank you for the reply. This looks like a promising solution. I was curious if you can flesh this out a bit more for us newbie's? I can navigate around Ubuntu pretty well for a beginner but getting lost at steps like:

(As per your linked thread):

"Then do a search in nautilus in your FileSystem for virtualbox and remove any leftovers."

How do I remove any leftovers of VirtualBox? What exactly constitutes leftovers? For example, the VirtualBox crash reports directory and ".crash" files show up along with the .vbox file and associated directory that was created when attempting to run/install Windows XP. 

Should these be deleted?

Also...

"Then download per site instructions."

I can locate the VirtualBox distribution to download but it's not clear what instructions to follow next for the installation? I know these are very basic steps but for someone new to Ubuntu, you could see how they would be a bit lost and require orientation.

Finally...

"Then install dkms and build-essential"

Exactly what does this step do? And how do I know I've installed correctly? I entered the code in CL and didn't get any response (?)

Thank you in advance for the in-depth help! I appreciate it more than you know.

---

### Post by Jeff_Berrian on 2013-10-10
> **ibjsb4 said:**
> This is my fix :)

[http://ubuntuforums.org/showthread.php?t=2175822&p=12795536&viewfull=1#post12795536](http://ubuntuforums.org/showthread.php?t=2175822&p=12795536&viewfull=1#post12795536)

RE: "Then download per site instructions."

I downloaded the VirtualBox .deb file from the link provided in your thread. It is located in my Home/Downloads directory. I managed to locate the code to install the .deb and it says "cannot access archive: No such file or directory..."

I made sure to type in the name of the .deb file correctly.

Do I have to change directory and/or specify the location of the .deb file in terminal/CL?

***Solved***

See OP for edit.

***Thread Closed***

---

### Post by ibjsb4 on 2013-10-11
Gdebi is a popular package.  Another tool like this is Synaptic Package Manager that allows a greater range of control.  Try it :)

sudo apt-get install synaptic

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

---

### Post by Jeff_Berrian on 2013-10-12
Nice!

Worked like a charm :)

Thank you!

---

