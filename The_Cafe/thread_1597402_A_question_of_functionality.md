---
title: "A question of functionality"
date: 2010-10-15
forum: The Cafe
---

### Post by Legeril on 2010-10-15
I've spent many an hour over the past couple of days trying to change the log in theme for my 10.04 login screen, and I've been recommended a very nice 'consolidation' program called Ubuntu Tweek. Which in itself is a very nice program for a newbie. Although the answer I've got a few times is this, the older themes for many of the functionality of Ubuntu has been taken out since 9.10 and as such you can't customise things like your login screen anymore.

I've managed to change my background, but there are some very nice themes out there. One of the reasons I switched to Linux (although admitedly not the deal breaker) was the allure of almost complete customisability (possibly not a word), and am a little bummed that many of these functions seemed to have been rejected in later versions of Ubuntu. 

People have also said that they just haven't put these functions in yet, but with the recent upgrade to 10.10 I find that line of thinking a little hard to swallow. 

Is it still possible to play with things like your login screen without being a Linux guru or a .C nut?

---

### Post by undecim on 2010-10-15
The new GDM isn't themable. If you need someone to blame for it, blame the gnome devs.

If you want, you can install KDM and get some themes for that.

---

### Post by matthew.ball on 2010-10-15
There's an application called "GDM2Setup" which enables you to change login screen.

I'm under the impression most themes are gdm, and since Ubuntu has moved to gdm2 they no longer work (I could be wrong here?).

That said, the gdm2setup tool is really quite easy (and customisable).

Edit: Maybe I am wrong, but my login picture is a slightly blurred version of my desktop background which I changed using the aforementioned tool (I'm running Lucid).

---

### Post by Spice Weasel on 2010-10-15
[SLiM]("http://slim.berlios.de/") ftw!

---

### Post by Legeril on 2010-10-15
That sounds like an interesting tool, I'd like to give it a look.

Would you be able to give me the terminal instructions to download the app + repositories etc?

---

### Post by undecim on 2010-10-15
> **Spice Weasel said:**
> [SLiM]("http://slim.berlios.de/") ftw!

I'm going to have to take a look at that.

---

### Post by Legeril on 2010-10-15
> **undecim said:**
> I'm going to have to take a look at that.

after looking at the online manual, this app looks a little complicated for me (a complete newbie).

Would anyone that has installed and used GDM2setup please give me a quick newbie guide to acquiring and installing this app please? I would very much appreciate it.

---

### Post by matthew.ball on 2010-10-15
> **Legeril said:**
> after looking at the online manual, this app looks a little complicated for me (a complete newbie).

Would anyone that has installed and used GDM2setup please give me a quick newbie guide to acquiring and installing this app please? I would very much appreciate it.
Try this: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

Edit: Whoops, [http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

---

### Post by Legeril on 2010-10-15
> **matthew.ball said:**
> Try this: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

Edit: Whoops, [http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

I have installed this app, although it doesn't seem to be working correctly 'yet'? The Accessibility and Theme menus are out of action. I realise this is turning into an 'app help me' thread now rather than just a chat on functionality so I'll take this over to another area if it is becoming inappropriate for this section of the board..

Have you managed to activate and use these menus? The app says something about conversion issues, I'm assuming this is converting gdm to gdm2.

---

### Post by matthew.ball on 2010-10-15
> **Legeril said:**
> I have installed this app, although it doesn't seem to be working correctly 'yet'? The Accessibility and Theme menus are out of action. I realise this is turning into an 'app help me' thread now rather than just a chat on functionality so I'll take this over to another area if it is becoming inappropriate for this section of the board..

Have you managed to activate and use these menus? The app says something about conversion issues, I'm assuming this is converting gdm to gdm2.
No, you are correct, they are greyed out for me too. If you add the PPA to your source.list, as they update the application they should eventually become available.

---

### Post by undecim on 2010-10-15
GMD2Setup doesn't do anymore than Ubuntu Tweak

---

### Post by NightwishFan on 2010-10-15
Ubuntu tweak can change the login screen background, however I think the image needs to be copied to /usr/share/backgrounds first to work.

---

### Post by Legeril on 2010-10-15
> **matthew.ball said:**
> No, you are correct, they are greyed out for me too. If you add the PPA to your source.list, as they update the application they should eventually become available.

ok thank you, would you be able to tell me how to do this? I've updated my source.list before but I dont remember the command or path :(

also where would I find the address for the PPA to add?

---

### Post by matthew.ball on 2010-10-15
> **Legeril said:**
> ok thank you, would you be able to tell me how to do this? I've updated my source.list before but I dont remember the command or path :(

also where would I find the address for the PPA to add?
[FONT="Courier New"]sudo add-apt-repository ppa:gdm2setup/gdm2setup[/FONT]
Just enter that in the terminal.

I don't use Ubuntu Tweak, sorry I don't know what it does (or does not do).

---

### Post by Simian Man on 2010-10-15
I hate to break it to you, but removing functionality and customizability is something that Gnome has done many, many times.

---

### Post by NightwishFan on 2010-10-15
> **Simian Man said:**
> I hate to break it to you, but removing functionality and customizability is something that Gnome has done many, many times.

This is true, sometimes for good, however not most of the time.

---

### Post by Legeril on 2010-10-15
> **matthew.ball said:**
> [FONT=Courier New]sudo add-apt-repository ppa:gdm2setup/gdm2setup[/FONT]
Just enter that in the terminal.

I don't use Ubuntu Tweak, sorry I don't know what it does (or does not do).

I believe I did that when installing the program, thank you though 

As for Gnome removing 'the best bits' as I'll put it (tongue in cheek), I guess I'll just live with it till I learn more about Linux and maybe change my kernel (right word?). Untill then I'll just have to settle with a stable and enjoyable OS, damn why do these things always happen to me?!..

---

### Post by undecim on 2010-10-15
> **Legeril said:**
> I'll just live with it till I learn more about Linux and maybe change my kernel (right word?).

I think you mean desktop environment? The kernel has nothing to do with the Gnome code (aside from where gnome has to interface with the kernel, of course)

If your computer can handle it (i.e. if it's designed to run Vista or Win7), then you can try install KDE It's über-customizable, and very good-looking, though tends to be a slower than Gnome.

```
sudo apt-get install kubuntu-desktop
```

That command will install KDE and all the default apps that come with Kubuntu (the KDE version of Ubuntu), including KDM, which is like GDM, but more customizable and made for KDE (though you can still choose between Gnome and KDE when you log in)

---

