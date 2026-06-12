---
title: "Fedora run virtually doesn't save any changes"
date: 2011-10-31
forum: Virtualisation
---

### Post by bobman321123 on 2011-10-31
When I run Fedora 64 on an Ubuntu (11.10)  host machine (AMD phenom II x6, 3.2 ghz, 4gb of RAM) , the operating system saves no changes and boots from default every time... I'm running it on Virtualbox.
Help?

---

### Post by haqking on 2011-10-31
> **bobman321123 said:**
> When I run Fedora 64 on an Ubuntu (11.10)  host machine (AMD phenom II x6, 3.2 ghz, 4gb of RAM) , the operating system saves no changes and boots from default every time... I'm running it on Virtualbox.
Help?

is it installed, or have you left the Live CD/.iso setup with boot to CD-Rom first setup ;-)

---

### Post by bobman321123 on 2011-10-31
Well, it's a live CD, but the live CD doesn't want to install because it doesn't recognize my graphics card, but I can't really fix the graphics card if I can't save any changes.
(p.s. the graphics card is an Nvidia something or other. :P Helpful I know)

---

### Post by haqking on 2011-10-31
> **bobman321123 said:**
> Well, it's a live CD, but the live CD doesn't want to install because it doesn't recognize my graphics card, but I can't really fix the graphics card if I can't save any changes.
(p.s. the graphics card is an Nvidia something or other. :P Helpful I know)

you cant save changes to a live cd ;-)

You need to install it and then fix issues.

Choose a text installer instead of GUI.

or choose vga mode etc, i cant remember fedora options now

---

### Post by bobman321123 on 2011-10-31
Is it not possible to install from a live Cd? That's how I installed Ubuntu. 
Also, I'm not the most Linux skilled person out there (*cough*) BUT I'd really like to learn, so, how exactly would one do a text install of Fedora?

---

### Post by haqking on 2011-10-31
> **bobman321123 said:**
> Is it not possible to install from a live Cd? That's how I installed Ubuntu. 
Also, I'm not the most Linux skilled person out there (*cough*) BUT I'd really like to learn, so, how exactly would one do a text install of Fedora?

yes you can install from it, you asked about saving changes...you cant save changes to a Live CD.

You setup your VM boot to the live CD and then choose install

see here [http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15](http://www.sysprobs.com/install-fedora-15-virtualbox-steps-install-virtualbox-guest-additions-fedora-15)

---

### Post by bobman321123 on 2011-10-31
Oh, the live CD doesn't display the "install" option because it can't launch Gnome because it doesn't recognise my graphics card.

---

### Post by haqking on 2011-10-31
> **bobman321123 said:**
> Oh, the live CD doesn't display the "install" option because it can't launch Gnome because it doesn't recognise my graphics card.

im confused.

You are using a virtual machine, it wont see a Nvidia graphics card anyways, your VM virtualises an instance of it.

can you show me a screen dump of your VM settings (display) and a VM not working screen dump

---

### Post by bobman321123 on 2011-10-31
Here is a screenshot of the display settings for the Fedora Virtual machine and a screenshot of the error message it gives me.

---

### Post by haqking on 2011-10-31
> **bobman321123 said:**
> Here is a screenshot of the display settings for the Fedora Virtual machine and a screenshot of the error message it gives me.

ok so all you have is a 3d issue, that is not related to not installing or Nvidia.  You need to enable 3d from your display settings however, i doubt you need 128MB either.

So i dont see anything from preventing you from installing though ?

Follow the guide as i posed above.

Either way for Live or Install your VM needs 3D enabled

---

### Post by bobman321123 on 2011-11-01
I tried that, and it gave me the same error message. 
I even tried bumping up the amount video memory, and it gave me the same error message.

---

### Post by haqking on 2011-11-01
> **bobman321123 said:**
> I tried that, and it gave me the same error message. 
I even tried bumping up the amount video memory, and it gave me the same error message.

I still dont get your issue, you are getting an error to say you are in fallback mode.

So what ?

Why cant you go ahead and install ?

---

### Post by bobman321123 on 2011-11-01
The option to install simply does not exist. I suspect this is as a result of gnome not loading, but I could be wrong.

---

### Post by haqking on 2011-11-01
> **bobman321123 said:**
> The option to install simply does not exist. I suspect this is as a result of gnome not loading, but I could be wrong.

well as it is fedora related you might want to head over to the fedora forums.

The installer will be there somewhere as it is a live CD.

the fact it is using session fallback wont prevent you from installing, that is purely graphic related

I have a xfce fedora VM but i dont have a gnome 3.2 one im afraid to help you any further.

However let me just say that the nvidia thing is not related as a VM is using virtualised hardware, and the session fallback is purely because of display drivers.

You can still install

---

### Post by bobman321123 on 2011-11-04
Ok, thanks for your help thus far. I appreciate it. :)

---

