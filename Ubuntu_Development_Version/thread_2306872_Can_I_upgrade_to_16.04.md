---
title: "Can I upgrade to 16.04?"
date: 2015-12-19
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-12-19
Hi,
I have always used development versions of Ubuntu. I'm not afraid about bugs and I often backup my /home so I can quickly restore the whole system. I've always upgraded to development versions as soon as they has been released.

I would like to upgrade to 16.04 but I'm little worried about MIR and Unity 8. How much stable are these critical software? I think that 16.04 could be much more unstable than previous versions due to the revolution Canonical is doing on Ubuntu.

---

### Post by deadflowr on 2015-12-19
> I would like to upgrade to 16.04 but I'm little worried about MIR and Unity 8. How much stable are these critical software?
Stable enough that i don't think you'll even notice them. Or see them installed.

---

### Post by enricobe on 2015-12-19
> **deadflowr said:**
> Stable enough that i don't think you'll even notice them. Or see them installed.

Thank you! I'm very curious to see this new version and look if system performance with U8&Mir are better than U7&Xorg :D Tomorrow (in Italy it's almost 11PM) I'll upgrade my Ubuntu ;)

---

### Post by grahammechanical on 2015-12-19
Ubuntu Xenial Xerus (16.04) is not using Mir & Unity 8. Ubuntu 16.04 is LTS and will be running X + Unity 7. So, no change.

As in previous Ubuntu versions there is a unity8-desktop-session-mir package that we can install. We get an additional session we can load into at the lightdm login screen. It will not work on proprietary video drivers. Once we get past the lighdm login we get the phone login screen. If you get past that & I cannot, what you will get is a very limited phone OS. The app store does not work. 

I have been trying the unity8 session from 14.04 onwards and as far as I am concerned it has gone past being a curiosity to be useless. But see for yourself. Meanwhile, development has moved into other directions.

Snap packaging and transactional updates have got the developers attention. There is talk of a version of Ubuntu called Ubuntu Personal. It will have MIr & Unity 8. The OS will be a snap and get transactional updates. All applications will be snaps and run in confinement. If an update to the OS fails the then update will be rolled back.

But all this still has a long way to go. The only image that was installable (personal_x86.img) has not been updated since 17 October. I doubt if we will see Ubuntu Personal by April 2016 but may be by October 2016.

There is a thread on this section all about this experiment (Ubuntu Desktop Next). And that is the nearest we get to a version of Ubuntu running on Mir & Unity 8. 

Regards.

---

### Post by enricobe on 2015-12-20
> **grahammechanical said:**
> Ubuntu Xenial Xerus (16.04) is not using Mir & Unity 8. Ubuntu 16.04 is LTS and will be running X + Unity 7. So, no change.

As in previous Ubuntu versions there is a unity8-desktop-session-mir package that we can install. We get an additional session we can load into at the lightdm login screen. It will not work on proprietary video drivers. Once we get past the lighdm login we get the phone login screen. If you get past that & I cannot, what you will get is a very limited phone OS. The app store does not work. 

I have been trying the unity8 session from 14.04 onwards and as far as I am concerned it has gone past being a curiosity to be useless. But see for yourself. Meanwhile, development has moved into other directions.

Snap packaging and transactional updates have got the developers attention. There is talk of a version of Ubuntu called Ubuntu Personal. It will have MIr & Unity 8. The OS will be a snap and get transactional updates. All applications will be snaps and run in confinement. If an update to the OS fails the then update will be rolled back.

But all this still has a long way to go. The only image that was installable (personal_x86.img) has not been updated since 17 October. I doubt if we will see Ubuntu Personal by April 2016 but may be by October 2016.

There is a thread on this section all about this experiment (Ubuntu Desktop Next). And that is the nearest we get to a version of Ubuntu running on Mir & Unity 8. 

Regards.
Thank you very much too :)

So there is no Mir and no Unity 8 in xenial?
I was running the daily live dvd and checked this [http://askubuntu.com/questions/330862/how-do-i-find-out-if-my-system-is-using-mir](http://askubuntu.com/questions/330862/how-do-i-find-out-if-my-system-is-using-mir)
If that answers are correct, xenial should run Mir because that string appears. Moreover, the unity interface looks a bit different than the current Unity 7. Icons on the desktop are much bigger and the clock is ugly.
Could you explain me why of this difference?

I thought differences were due to U8&Mir, was I wrong?

---

### Post by MikeMecanic on 2015-12-20
That shouldn't stop you from trying and testing Xenial.  The icons are not that big and if you remove them it comes back to normal after.  Try upgrading with no icon on the desktop. 
.
Running Xubuntu 16.04 LTS (Kernel 4.4 rc5 alone with Proposed enable) since a week and I didn't experience any major issues.

Open the switch instead and share your experience with us.


Regards,

---

### Post by deadflowr on 2015-12-20
I'm not sure you can even throw icons on a unity8 desktop, for starters.
And the big odd icons seems more like a current (or recently development) problem with nautilus.
Which is not used in unity8, afaik.
I also think there are theming problems here and there, if I'm not mistaken; odd gtk-3 problems with unity7.

As to why the output string the unity-compositor-system would be the same beats me, but anything is possible.
Especially considering two years since that command was posted there in askubuntu.

Edit:comical how no one will post for half a day and then two or more post simultaneously.

As a bonus though, here's one nautilus big icon bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316)

---

### Post by enricobe on 2015-12-20
> **MikeMecanic said:**
> That shouldn't stop you from trying and testing Xenial.  The icons are not that big and if you remove them it comes back to normal after.  Try upgrading with no icon on the desktop. 
.
Running Xubuntu 16.04 LTS (Kernel 4.4 rc5 alone with Proposed enable) since a week and I didn't experience any major issues.

Open the switch instead and share your experience with us.


Regards,
Don't worry, I will upgrade to 16.04 anyway. I don't use my personal notebook so much and not for productivity use so I love to help testing considering that I can't help developing. 

I've not yet upgraded to 16.04 because I want to "upgrade" to Ubuntu Next first. I'm quite sure that Next is not good for daily use (and maybe not even to try it) so I'm going to downgrade in one or two days to 16.04, but I'm really curious about Next :D. Now that you explained me that Mir&U8 are not in 16.04, I'll upgrade with no worries

---

### Post by enricobe on 2015-12-21
I'm now on 16.04 LTS. All ok so far. :-D

Icons are stille huge, but I've seen that there is a new option from the right-click menu: resize icon!

---

### Post by mrroberthadley on 2015-12-21
Did you upgrade by way of reinstall or can you upgrade from within Ubuntu?

---

### Post by deadflowr on 2015-12-21
> **mrroberthadley said:**
> Did you upgrade by way of reinstall or can you upgrade from within Ubuntu?
You can upgrade through the terminal by either running 
```
do-release-upgrade -d
```
or use the terminal to open the update manager with
```
update-manager -d
```
notice the -d flag in each, that signifies the development release.

do-release-upgrade is the terminal way, as update manager is the gui way.

do-release will start the process automatically.
The update manager won't automatically start the process, you still need to choose the option.

If you are running 14.04 you might want to check that the upgrade is set to upgrade to the next lts and not the next release.

---

### Post by enricobe on 2015-12-21
I've upgraded using the ISO disc. The first time that I have upgraded to 16.04 an error occurred because the installation program did not restore all the programs, so I've decided to reinstall the whole system (I have a separated /home partition which is really useful in these cases)


The icons are HUGE also in nautilus :(

---

### Post by deadflowr on 2015-12-21
> [COLOR=#000000]The icons are HUGE also in nautilus [/COLOR]:sad:

Makes sense as nautilus controls the desktop.

---

### Post by flocculant on 2015-12-21
> **enricobe said:**
> I've upgraded using the ISO disc. The first time that I have upgraded to 16.04 an error occurred because the installation program did not restore all the programs, so I've decided to reinstall the whole system (I have a separated /home partition which is really useful in these cases)


The icons are HUGE also in nautilus :(

> **deadflowr said:**
> Makes sense as nautilus controls the desktop.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316)

[https://bugzilla.gnome.org/show_bug.cgi?id=748441](https://bugzilla.gnome.org/show_bug.cgi?id=748441)

---

### Post by enricobe on 2015-12-23
> **flocculant said:**
> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1522316)

[https://bugzilla.gnome.org/show_bug.cgi?id=748441](https://bugzilla.gnome.org/show_bug.cgi?id=748441)

Thank you! I've added my "+1";)

---

### Post by flocculant on 2015-12-23
welcome - obviously they don't affect me - but I do hang about in irc channels and notice things :)

---

### Post by kurt18947 on 2015-12-23
re icon size. There is a way to reduce the size from huge to big:). Open nautilus, in the upper right hand corner are icons for search (magnifying glass), a grid like icon  and an icon with 3 lines. If I click on the center (grid) icon, there is a slider. The default is centered, slide it to the left and the icons should be smaller. I'm using Ubuntu-gnome but I presume Ubuntu-unity would be similar.

---

### Post by ebenash on 2015-12-23
I have upgraded to ubuntu gnome 16.04 :D. Its smooth ( as far as explored), just some issues with headphones.

Go ahead.

---

### Post by enricobe on 2015-12-24
> **kurt18947 said:**
> re icon size. There is a way to reduce the size from huge to big:). Open nautilus, in the upper right hand corner are icons for search (magnifying glass), a grid like icon  and an icon with 3 lines. If I click on the center (grid) icon, there is a slider. The default is centered, slide it to the left and the icons should be smaller. I'm using Ubuntu-gnome but I presume Ubuntu-unity would be similar.
Thank you very much! This helped a lot!
They are still too big for me, but far better than before :D

> **ebenash said:**
> I have upgraded to ubuntu gnome 16.04 [IMG]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]. Its smooth ( as far as explored), just some issues with headphones.

Go ahead.
Welcome to the 16.04 club ;)

---

