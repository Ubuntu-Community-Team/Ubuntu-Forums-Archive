---
title: "Fedora 9 through the eyes of the Ubuntu user"
date: 2008-05-17
forum: The Cafe
---

### Post by PryGuy on 2008-05-17
I was expecting the new Fedora eagerly; seventh version was nice and stable but there was one thing I didn't like most of all, once you installed Fedora from DVD you couldn't use it as a repository any more. That was really strange and confusing. Yet it was impossible for me to even think of Fedora as a default desktop platform for the clients. The reason was simple: apt. Apt is perfect if you need to install Linux on many machines as fast as possible. Fedora 9 still doesn't know how to install additional packages from local repos out of the box and it's very easy to do that in Ubuntu, especially in Hardy. The world is all about internet nowadays, but here in Russia for instance you still have to pay for traffic in many places outside Moscow, so it's a great waste of time and money fetching the packages you need from the internet every time. Do I need to mention that internet is not allowed in many companies? There are many countries where people still do not have internet at all. And what if I'm not at home and out of wi-fi/network coverage so I just can't fetch what I want? Very bad, Fedora team.

[SIZE="3"]Installation.[/SIZE]
Anaconda is Anaconda. It works... most of time... Installer crashed when I chose Russian as my language then tried to customize my installation and chose KDE as my second WM. Text install with Russian selected didn't work either. Okay, I chose English on the next boot and it let me do what I wanted finally! I customized the installation and chose the Russian locale files to install. The installation went fine, but I found my OpenOffice still speaks English as I booted into the newly installed system and chose Russian as my system locale. Yes, we have to download the OpenOffice locale files in Ubuntu, but look, It's a DVD, Fedora had to include it I think. Another thing I didn't like at all, Fedora tries to wipe partitions on your hard drive by default. Not a good thing for newbies. I couldn't find mc on the DVD, a tool that is very vital for me, overlooked it probably.

[SIZE="3"]Desktop.[/SIZE]
Fedora 9 looks and feels a lot like Ubuntu Hardy with blue theme. You get the same packages. It appears that Fedora developers like when Nautilus opens a new window for each new folder. It's ridiculous! I get 2 more unneeded windows when I open /home/user/Documents from the root. I have a mess on my desktop after the file operations. It can be fixed easily, but Ubuntu does it the right way out of the box! I couldn't find the Language Support tool in Administration. Where is it? I don't know, I could choose the language I needed from GDM only. There's no analogue to the Ubuntu's Hardware Drivers tool. That means you have to install restricted drivers manually. Newbies will definitely not like it. As I said above I couldn't install any additional packages from DVD. Yum still neglects local repos and tries to download anything from internet. I'm sure it can be fixed too, but why the Fedora team didn't fix it for us? Sudo is here but it doesn't work and su is so Stone Age to me. 

[SIZE="3"]Conclusion.[/SIZE]
Well, it is short. I haven't used Fedora server so far but as for the desktop Ubuntu still beats Fedora hands down. This is my personal opinion of course.

---

### Post by Mr. Picklesworth on 2008-05-17
I didn't expect this, but I have started to really like Spatial Nautilus + single click to open on my Ubuntu install. Unlike the browser mode, Nautilus is able to remember the positition and size of every folder that I open, so browsing becomes much more intuitive after a while. Further, it actually makes sense with the "folders" metaphor; if you open a folder, the one containing it is still open and still there!

Not for everyone, but I do think it makes a lot of sense. It's good for usability, too, since users can recognize folders by their size and position. It doesn't work in, for example, Windows because its window manager cannot cope with presenting piles of windows in terms of user interface. However, over here we have workspaces and window switching between only windows belonging to the same application, so it makes a lot of sense.

---

### Post by spamzilla on 2008-05-17
I tried Fedora 9 out too, and several it gave me no reason to ditch Ubuntu at all. Infact, I was quite unimpressed with Fedora to the extent that I have already removed the virtual machine files from my laptop - I only installed it last night!

---

### Post by lswest on 2008-05-17
my only 2 problems with Fedora's out-of-the-box setup (which is reason enough for me to not use it, because i customize Ubuntu anyways, and i don't have to waste time doing 2 things that get done automatically in Ubuntu) is the fact that the first user made is not in the sudoers file, and then the fact that the default filebrowser opens every folder in a new window, it just annoys me to no end.  Otherwise...yum isn't apt, and i prefer apt over yum any day, but it's more a preference thing.

---

### Post by cardinals_fan on 2008-05-17
> **PryGuy said:**
> Sudo is here but it doesn't work and su is so Stone Age to me. 
Some of us prefer su, you know :)

---

### Post by ghindo on 2008-05-17
> **cardinals_fan said:**
> Some of us prefer su, you know :)Why's that?

---

### Post by cardinals_fan on 2008-05-17
> **ghindo said:**
> Why's that?
Su is cleaner.  When I enter su and my password, I enter the root account.  I perform whatever I need to do, and sign out of the root account.  Sudo blurs the line between root and non-root.  I'm more comfortable with my lines nice and clear.

---

### Post by ghindo on 2008-05-17
> **cardinals_fan said:**
> Su is cleaner.  When I enter su and my password, I enter the root account.  I perform whatever I need to do, and sign out of the root account.  Sudo blurs the line between root and non-root.  I'm more comfortable with my lines nice and clear.Why not use sudo -i?

---

### Post by cardinals_fan on 2008-05-17
> **ghindo said:**
> Why not use sudo -i?
But why should I?

---

### Post by NightwishFan on 2008-05-17
I like the single click to interact with my file browser. I use dolphin kde4 because it looks great and can show files in groups. Fedora surprises me, the install (for me) was so polished and fast, but the user interface is slow and sloppy feeling.

---

### Post by ghindo on 2008-05-17
> **cardinals_fan said:**
> But why should I?I dunno, just curious.  I'm still trying to make the distinction between sudo -i and su.

---

### Post by karellen on 2008-05-17
Fedora 8 is just ok for me, I don't mind adding additional repos (livna), installing codecs manually. I like yum (from the cli), I agree that's a little slower than apt, but besides that I 've had no problems with it. and I like the default Fedora theme. nevertheless, I find Fedora and Ubuntu very similar in their Gnome approach, the differences are hidden from the user (rpm distro vs deb distro...). overall, Fedora 8 is still on my rig, dual-booting with Vista.

---

### Post by Erunno on 2008-05-17
> **PryGuy said:**
> It appears that Fedora developers like when Nautilus opens a new window for each new folder. It's ridiculous! I get 2 more unneeded windows when I open /home/user/Documents from the root. I have a mess on my desktop after the file operations. It can be fixed easily, but Ubuntu does it the right way out of the box!

Actually, this is a GNOME upstream default and Fedora is one of the few major distributions who keep instead of changing Nautilus to "browser mode". You can try complaining to the GNOME developers about this issue but they seem to firmly believe in this spatial browsing.

---

