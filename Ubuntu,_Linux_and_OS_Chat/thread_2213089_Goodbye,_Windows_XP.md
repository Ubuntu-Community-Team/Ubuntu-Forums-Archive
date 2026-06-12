---
title: "Goodbye, Windows XP"
date: 2014-03-24
forum: Ubuntu, Linux and OS Chat
---

### Post by rewyllys on 2014-03-24
Since this is the "Ubuntu, Linux and OS Chat" Forum, I think the comment I'm about to make can be justified here.

It is a personal pleasure to report to you all that today my wife talked me into cleaning up old files and materials from in our home office, with the following result.  One of the things that I uncovered was a copy of Windows XP -- OEM version -- in its original, still sealed package.

It gave me great delight to toss the package directly into my wastebasket!

---

### Post by thiebaude on 2014-03-24
Sir, Congratulations.

---

### Post by james114 on 2014-03-25
You made a right decision.  :P

---

### Post by Votlon on 2014-03-26
Grats :)

---

### Post by monkeybrain20122 on 2014-03-27
Friend got a refurbished hp laptop today sold with XP preinstalled(!) and was quite fed up with the endless rebooting and updates. I told him there will be no more updates after next week so he would be able to rest easy. :) I told him he had two options, either went back to the store and asked for an upgrade to win7 or I could install a *buntu for him (he was thinking of using gimp on his machine anyway) and he chose the latter, it was a rather easy conversion with hardly any selling on my part. :) The machine is not too bad, dual core with 2G of ram, I tried a Trusty usb on it and Unity ran pretty well, but I installed lubuntu 13.10 anyway as it is more familiar to him. 

So far everything seems ok, the only WTF moment came when I tried to teach him to use the lubuntu software center. It doesn't seem to have any install option!!!??? ("get software" only shows applications already installed!, "Add to app basket" does nothing) So I just removed it and installed the USC instead. The computer is powerful enough to run it (I think synaptic may be a bit difficult for him) The LSC is supposed to be an easy to use "app store" for newbies but I got so confused by it that I ended up installing most things with synaptic though I was trying to demo to him how to install things himself. I think this is a show stopper that needs to be addressed.

Edited: Also wonder if there is an easier way to put launchers on the desktop than copying from /usr/share/applications which doesn't require sudo and the terminal. Personally I detest the practice but since LXDE operates on a 'classic' XP like paradigm it should make easy accommodation for this common habit for that kind of use cases (because classic menus are a pain to look for things, people say they want it but end up never using it, they pin everything on the desktop)

---

### Post by Bucky Ball on 2014-03-27
Hotkeys? I use xfce and they are extremely easy to set up. Don't know about lxde. Holding the 'Super' (Windows key) then hitting 'g' to launch Gimp, say, is pretty easy. 

I have nothing on my desktop (and autohide my taskbar). Setting up the hotkeys might be a bit beyond the user, but if you can figure out how to do it then set them up for the most commonly used apps, that might remove some headaches.

And a hearty congratulations to the OP. Goodbye WinXP. I, on the other hand, will be continuing to use it, offline, of course, on my audio/video machine as my old A/V software won't work on Win7 (and not about to fork out a thousand or so for more software when what I have works fine for my needs ... ). ;)

---

### Post by vasa1 on 2014-03-27
> **monkeybrain20122 said:**
> ...
So far everything seems ok, the only WTF moment came when I tried to teach him to use the lubuntu software center. It doesn't seem to have any install option!!!??? ("get software" only shows applications already installed!, "Add to app basket" does nothing)...

After you add one item to the App basket, you'll see Apps Basket (1). If you click on that, you'll see "install packages" in the lower right corner of the new screen.

---

### Post by vasa1 on 2014-03-27
> **monkeybrain20122 said:**
> ...
Edited: Also wonder if there is an easier way to put launchers on the desktop than copying from /usr/share/applications which doesn't require sudo and the terminal. Personally I detest the practice but since LXDE operates on a 'classic' XP like paradigm it should make easy accommodation for this common habit for that kind of use cases (because classic menus are a pain to look for things, people say they want it but end up never using it, they pin everything on the desktop)

I don't use a desktop at all. The Openbox window manager allows one to setup keyboard shortcuts to launching most anything. W+F launches Firefox, W+C launches Chrome, W+M launches Medit, W+T launches the terminal and so on.

Anyway, I'll log into a Lubuntu session and see.

Pity you installed USC, the epitome of bloatware. It would have pulled a lot of unwanted dependencies. And now your user will get far, far, more updates that ever before because USC is being actively "developed".

---

### Post by vasa1 on 2014-03-27
> **monkeybrain20122 said:**
> ...
Edited: Also wonder if there is an easier way to put launchers on the desktop than copying from /usr/share/applications which doesn't require sudo and the terminal.


[s]I just tried this from the Lubuntu session: opened /usr/share/applications, highlighted Audacity. Pressed control+C, clicked on the desktop, pressed control+v. The Audacity icon appeared. Double-clicked on the icon and Audacity opened.

No sudo. No terminal.[/s]

I just remembered I don't have a pure LXDE desktop environment. My Lubuntu session is a mix of xfce+lxde. So the above isn't necessarily true of a "normal" Lubuntu session.

---

### Post by vasa1 on 2014-03-27
> **monkeybrain20122 said:**
> ... people say they want it but end up never using it, they pin everything on the desktop)
Wow! No doubt you have vast experience to make such a sweeping statement.

---

### Post by monkeybrain20122 on 2014-03-27
> **vasa1 said:**
> After you add one item to the App basket, you'll see Apps Basket (1). If you click on that, you'll see "install packages" in the lower right corner of the new screen.

When I clicked that nothing happened, there was no 'install packages' or new screen.

Guy is gone with his laptop now but I read afterwards that some packages are missing from LSC so doesn't work. If reinstall LSC after post installation update it would work. I will try that when he comes in a few days.

> I just tried this from the Lubuntu session: opened  /usr/share/applications, highlighted Audacity. Pressed control+C,  clicked on the desktop, pressed control+v. The Audacity icon appeared.  Double-clicked on the icon and Audacity opened.


Of course you are correct. that would work. Somehow didn't think of that. But then he would be asking me to write down /usr/share/applications on  a piece of paper for him. :)

> Pity you installed USC, the epitome of bloatware. It would have pulled a  lot of unwanted dependencies. And now your user will get far, far, more  updates that ever before because USC is being actively "developed".         


I didn't want to do it, but I had no choice. LSC wasn't working and synaptic doesn't look like an 'app store' and he had a hard time following me with synaptic (USC he could follow, with flashy icons, reviews and stars). I got nervous when he started complaining that the system was difficult to use. I don't want to give that impression to a new user, so I decided that a little bloat may be the price to pay for. You might have done something differenty, I don't know.

                           > Wow! No doubt you have vast experience to make such a sweeping statement.         

I have seen enough Windows and Linux desktops. :) Most Windows applications even create desktop icons when installed in addition to the menu entries. All of us have experienced the classic menu, it is not the most efficient way to find things and the Linux menus are even worse because they are organized to categories which are not always well defined and not consistent across DEs and distros (Windows seems to have only one level in the menu,--'all programs',-- in addition to those frequently used) The logic of pinning launcher on the desktop as a way to bypass the menu makes sense.

---

