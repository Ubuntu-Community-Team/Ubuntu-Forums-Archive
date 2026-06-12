---
title: "Vmware"
date: 2009-02-16
forum: Virtualisation
---

### Post by 9teen99 on 2009-02-16
Hello :) i would like to have some help with installing vmware on ubuntu 8.04 (Hardy). i like ubuntu alot and therefore want it as my main OS because it never gives me problems with anything and i dont have to reboot after any small thing has been installed (which is great). there are other people that use this computer also and even tho im trying to wing them off and go towards ubuntu they have not gotten quite use to it enough to feel comfortable "yet". im thinking vmware would be the way to go since once installed i can boot xp and not have to worry about rebooting the computer or even what they do on the xp image since it wont effect my ubuntu. i have installed windows and then installed vmware on xp and used ubuntu that way but thats not what i want. i simply feel more safe with main OS as ubuntu and run xp off an image of course, but im not quite up to par with the commands yet on how this is done. so im asking you for some help please to accomplish this with crystal clear directions. i don"t mind waiting a few days to go through the replies and info any of you post to do this. i rather do it right the first time then 10 times incorrectly. thank you for taking the time to read this and i look forward to all your replies.

---

### Post by x33a on 2009-02-16
it is really simple and risk free.

first install virtualbox, i prefer it over vmware.

[http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/](http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/)

the interface is pretty simple and clear to understand. if you get stuck after that, just ask here.

---

### Post by konqueror7 on 2009-02-16
i agree, virtualbox is much simplier (in my opinion) than vmware...

---

### Post by 9teen99 on 2009-02-16
The following packages have unmet dependencies:
  virtualbox-2.1: Depends: libqt4-network (>= 4.4.3) but it is not installable
                  Depends: libqtcore4 (>= 4.4.3) but it is not installable
                  Depends: libqtgui4 (>= 4.4.3) but it is not installable
E: Broken packages


after i got to the last option to do using this in terminal, "sudo apt-get install virtualbox-2.1" i got the above

---

### Post by 9teen99 on 2009-02-16
Do i need to update to a new ubuntu OS to make this work since im using 8.04 ?

---

### Post by perrti-y02 on 2009-02-16
Have you tried using synaptic instead of apt-get? I find it gives you a better idea of what is going on. If the packages that you need aren't on the list shown in synaptic then you might need to get another repository.
In my opinion you should update to 8.10 any way. I have found no problem with it and I use it everyday.

---

### Post by 9teen99 on 2009-02-16
unfortunately synaptic says the same thing 

virtualbox-2.1:
 Depends: libqt4-network (>=4.4.3) but it is not installable
 Depends: libqtcore4 (>=4.4.3) but it is not installable
 Depends: libqtgui4 (>=4.4.3) but it is not installable

also what does this mean ?

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by perrti-y02 on 2009-02-16
The second bit means that you have another package management program (such as synaptic or the Debian Installer) open and running. This is using the dpkg thing.

To solve the first problem add these two lines to your /etc/apt/sources.list (or add them using software sources program)

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

This will add the intrepid repos but you don't have to install intrepid to use some of the packages.

give it a go but if it asks you to upgrade a silly number of packages then leave it be.

---

### Post by 9teen99 on 2009-02-16
Thank you for that, it installed perfect :) it says to start virtualbox from system tools but the icons not there ? any help thank you.

---

### Post by x33a on 2009-02-16
type in a terminal

killall gnome-panel

then check again, if the icons are installed or not. 

if not, then press alt+f2, "VirtualBox" (preserve the case).

you can manually create a shortcut with the above command.

---

### Post by 9teen99 on 2009-02-16
killall gnome-panel did the trick thanks alot for the help guys :) this place is great !!

---

### Post by 9teen99 on 2009-02-16
I did notice 655 new updates after installing virtualbox, is this normal ?

---

### Post by konqueror7 on 2009-02-16
those updates are for ubuntu intrepid, they popped up because you added the intriped repos in your source.lst,,,comment out or delete those lines, so those updates won't popup...i don't know if what will happen if you installed all of those updates, never tried it...:)

---

### Post by 9teen99 on 2009-02-16
well there almost finished installing so im going to find out

---

### Post by konqueror7 on 2009-02-16
also, i have to agree that you could upgrade to 8.10...just upgraded mine last week...

---

### Post by konqueror7 on 2009-02-16
> **9teen99 said:**
> well there almost finished installing so im going to find out

hope it will have a good outcome...:P hehe

---

### Post by 9teen99 on 2009-02-16
ok so now on startup i get the following message " there was an error starting the GNOME settings Daemon " :(

---

### Post by 9teen99 on 2009-02-16
on reboot my pc crashed and will not boot up after them updates, so now i know what it does :o

---

### Post by bodhi.zazen on 2009-02-16
> **x33a said:**
> it is really simple and risk free.

first install virtualbox, i prefer it over vmware.

[http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/](http://tombuntu.com/index.php/2008/12/18/install-virtualbox-21-in-ubuntu-810/)

the interface is pretty simple and clear to understand. if you get stuck after that, just ask here.

> **deuphil.kaufmann said:**
> i agree, virtualbox is much simplier (in my opinion) than vmware...

Just a heads up, please keep these threads on topic.

There are many tools for virtualization and they all have advantages and disadvantages.

Off topic comments such as "use virtualbox" on a request for VMWare support are off topic and counterproductive.

---

### Post by bodhi.zazen on 2009-02-16
> **9teen99 said:**
> Hello :) i would like to have some help with installing vmware on ubuntu 8.04 (Hardy). i like ubuntu alot and therefore want it as my main OS because it never gives me problems with anything and i dont have to reboot after any small thing has been installed (which is great). there are other people that use this computer also and even tho im trying to wing them off and go towards ubuntu they have not gotten quite use to it enough to feel comfortable "yet". im thinking vmware would be the way to go since once installed i can boot xp and not have to worry about rebooting the computer or even what they do on the xp image since it wont effect my ubuntu. i have installed windows and then installed vmware on xp and used ubuntu that way but thats not what i want. i simply feel more safe with main OS as ubuntu and run xp off an image of course, but im not quite up to par with the commands yet on how this is done. so im asking you for some help please to accomplish this with crystal clear directions. i don"t mind waiting a few days to go through the replies and info any of you post to do this. i rather do it right the first time then 10 times incorrectly. thank you for taking the time to read this and i look forward to all your replies.

There are guides on the Virtualization form for installing VMWare.

They are listed here : [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

Direct link : [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

As your question is now asked and answered, and there are off topic posts, I am going to close this thread now.

If you have technical questions on installing vmware, please start a new thread.

---

