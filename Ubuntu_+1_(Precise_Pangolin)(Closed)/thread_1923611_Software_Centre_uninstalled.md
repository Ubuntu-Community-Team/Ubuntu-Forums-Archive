---
title: "Software Centre uninstalled"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Mark Rooney on 2012-02-11
After completing a regular update today of 12.04 I noticed that the Software Centre was no longer in the launcher, searching for it in the Dash gives no results - it appears to be uninstalled.

I have the following packages held back at the moment after the upgrade - could one of them be causing the issue?

```
mark@NB550D:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gcc-4.6-base:i386 gwibber libgcc1:i386 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libstdc++6:i386 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libxi6:i386
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
```

---

### Post by KhaaL on 2012-02-11
> **starwarfans said:**
> Normally, the system patch usually unloaded, if installed software together with the system patch together a lot of, the user can select the interface." Does not display the Windows" installed patches" option to hide, so at the interface shows the user to install third party software applications, as shown in the figure, the user only be found in the list and select uninstall the software name, and then click the" software" button to automatically clear the software from the computer.</P>

What on earth are you talking about? Anyway I'm having similiar issues as the OP - my software centre wants since yesterday to be removed, and i'm holding off the upgrade because of that...

---

### Post by dino99 on 2012-02-11
there are huge differences between:
- upgrade
- dist-upgrade (dont use that till the final release is out)

see the manpage

---

### Post by jerrylamos on 2012-02-11
> **dino99 said:**
> there are huge differences between:
- upgrade
- dist-upgrade (dont use that till the final release is out)

see the manpage

I've found that upgrade may not install a new linux image so if I see one is being held back I do either (my preferred) sudo aptitude full-upgrade or (living dangerously) sudo apt-get dist-upgrade. And yes if either want to remove something significant without replacing it I don't - if I noticed.

I updated yesterday with aptitude.  I don't normally have the software launcher so I selected dash and entered sof and the software center shopping bag showed up.

Anybody who's affected write a launchpad bug yet?

Jerry

---

### Post by dino99 on 2012-02-11
> **jerrylamos said:**
> I've found that upgrade may not install a new linux image so if I see one is being held back I do either (my preferred) sudo aptitude full-upgrade or (living dangerously) sudo apt-get dist-upgrade. And yes if either want to remove something significant without replacing it I don't - if I noticed.

I updated yesterday with aptitude.  I don't normally have the software launcher so I selected dash and entered sof and the software center shopping bag showed up.

Anybody who's affected write a launchpad bug yet?

Jerry

AS already wrote, you should pay attention at the meta-package(s) dealing with such issue, like: linux-image-generic-pae. But you are free to continue with juncky commands of course. (manpage is your best friend if you have some doubts)

---

### Post by prusswan on 2012-02-11
I'm done with the normal upgrades now and faced with this option:

```

prusswan@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  apturl gir1.2-webkit-3.0 nautilus-share rhythmbox-plugins [COLOR="Red"][B]software-center
  ubuntu-desktop[/B][/COLOR]
The following packages have been kept back:
  gwibber libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0
The following packages will be upgraded:
  gir1.2-javascriptcoregtk-3.0 gnome-control-center-data
2 upgraded, 0 newly installed, 6 to remove and 5 not upgraded.
Need to get 1,134 kB of archives.
After this operation, 7,073 kB disk space will be freed.
Do you want to continue [Y/n]? 


```

red pill or blue pill?

---

### Post by dino99 on 2012-02-11
> **prusswan said:**
> I'm done with the normal upgrades now and faced with this option:

```

prusswan@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  apturl gir1.2-webkit-3.0 nautilus-share rhythmbox-plugins [COLOR="Red"][B]software-center
  ubuntu-desktop[/B][/COLOR]
The following packages have been kept back:
  gwibber libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0
The following packages will be upgraded:
  gir1.2-javascriptcoregtk-3.0 gnome-control-center-data
2 upgraded, 0 newly installed, 6 to remove and 5 not upgraded.
Need to get 1,134 kB of archives.
After this operation, 7,073 kB disk space will be freed.
Do you want to continue [Y/n]? 


```

red pill or blue pill?

Swallow them all (or take time to read previous comments)

---

### Post by prusswan on 2012-02-11
> **dino99 said:**
> Swallow them all (or take time to read previous comments)

I'm just posting for illustrative purposes :)

---

### Post by xajeiw9I on 2012-02-11
I am also having this problem. I admit I erroneously used the dist-upgrade argument. Is there an easy way to fix it? Maybe wait a couple days and try "sudo apt-get upgrade"?

---

### Post by prusswan on 2012-02-11
> **xajeiw9I said:**
> I am also having this problem. I admit I erroneously used the dist-upgrade argument. Is there an easy way to fix it? Maybe wait a couple days and try "sudo apt-get upgrade"?

reinstall ubuntu-desktop, halt with partial upgrades

---

### Post by grahammechanical on 2012-02-11
In my case I was following the instructions for installing Compiz 0.9.7.0-beta which included the apt-get dist-upgrade command. That was where the mistake was made.

It is because some of the libraries need upgrading. I found that I could not re-install software centre because a certain library would not be installed. That particular library needed another library which in turn needed a third library of which only an old version was available in the repositories.

I am not bothered about loosing Software Centre for a few days. I was only running it to test how well it worked with the Compiz beta. In a few days the various libraries needed will be upgraded as part of regular updates and then I will try again to re-install software centre.

That's life

---

### Post by matt_symes on 2012-02-11
I noticed this dist-upgrade an hour ago or so.

I have used dist-upgrade before but i take careful attention to what is being replaced, upgraded and removed.

This dist-upgrade i will leave alone for a while.

I must say though, this has been the most stable pre-release period i have seen in along time.

I have had next to no problems for a while and those have been small and have not required much fixing on my part.

Still waiting for some major breakage to give me something to fix. I'm sure it will come along.

---

### Post by KhaaL on 2012-02-11
> **matt_symes said:**
> 
I must say though, this has been the most stable pre-release period i have seen in along time.

In my experience, LTS pre-releases have been quite stable!

---

### Post by hugmenot on 2012-02-11
Tey tried three times to build webkit, each time it took four hours. On the last last it went past a packaging error but then the build exploded with not enough memory to link on i386 (4GB).

Funny. Why is Webkit so humongous?

---

### Post by mc4man on 2012-02-11
If you're on a 64 bit install then you'll need to wait till the 1386 build completes & publishes  - the 'common' package is built there for both

---

### Post by ronacc on 2012-02-11
since I use Gnome-shell and never use USC I went ahead and pulled the trigger on the dist-upgrade , I have not noticed any loss of functionality in G-S .

---

### Post by starNIX on 2012-02-11
I have the same problem.  I also erroneously did the dis-upgrade.  Trying to reinstall ubuntu-desktop doesn't work as I get the following errors:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: software-center but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

