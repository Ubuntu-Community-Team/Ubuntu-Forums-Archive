---
title: "Where do I find my shared folders in vmware Windows Vista"
date: 2021-08-03
forum: Virtualisation
---

### Post by snype9lives on 2021-08-03
I  dont know where to find it

---

### Post by QIII on 2021-08-03
Do you mean folders on Vista (which you should most definitely not be using) that you share?

---

### Post by snype9lives on 2021-08-03
Im trying to install firefox on it

---

### Post by QIII on 2021-08-03
What does that have to do with "Shared folders"?

You install software in a VM in exactly the same manner as you do with a bare-metal OS.

---

### Post by snype9lives on 2021-08-03
internet explorer  isnt working on it so im trying to put a portable version of firefox on it

---

### Post by QIII on 2021-08-03
What do you mean by a "portable version"?  What are you doing to try to install it?

---

### Post by snype9lives on 2021-08-03
A portable version is "A fully functional package of Firefox optimized for use on a USB key drive. A specialized launcher will allow most favorite extensions to work as you switch computers. You can use sync to share data between profiles. But some data cannot be shared between different versions".

---

### Post by QIII on 2021-08-03
That question was didactic in nature.  I know exactly what it is and where you got that citation.

What are you doing to attempt to install it?  I cannot divine your expectations, understanding of your difficulty, or your actions without a crystal ball -- I am asking questions to lead you to provide that insight and, I hope, to help you work through your difficulty with your own help.  Do you go to the doctor and say "My elbow hurts.  What can you do?" or do you provide some information -- even if the doctor has to ask for it?

What does the maintainer of the app give as instructions?  Is Vista supported?

---

### Post by snype9lives on 2021-08-03
Point is, I need a working browser.

---

### Post by QIII on 2021-08-03
What have you done to install the browser?

---

### Post by snype9lives on 2021-08-03
I tried putting a folder of the exe and data to share it to the vm through vmwares shared folder option and I dont  know where to find it

---

### Post by snype9lives on 2021-08-03
I tried sharing a folder of the browser but i dont know where to run it

---

### Post by QIII on 2021-08-03
Why don't you try just putting the file/folder in your Vista user account's documents folder?  Why involve the VM software at all beyond making the USB device available to the machine?

How about on your Windows desktop?

I believe you are overthinking this.

---

### Post by MAFoElffen on 2021-08-03
What OS is the Host? And what is the VM's OS? That would give details to people tring to help you with installing a browser. Is your host computer 32bit?

Easiest way to install a browser, depends on the OS...And the variety of Firefox you described, was not meant for a VM... and is not the easiest way for any VM or computer host.

If you share a folder, via VMware, when you open the file manager of your VM, which you have not identified, so I have to write in very general terms without any specifics... The shared folders will map as extra mounted drives into the VM's filesystem.

But agree with QIII. I think you are overthinking this.

The only OS you have mentioned so far is Windows Vista, which was dropped by Firefox for support. But you still have other options.
[https://windowsreport.com/browsers-old-computer/](https://windowsreport.com/browsers-old-computer/)

And how does any of that tie back into Ubuntu, any of it's flavors (where you are posting for help)  or anything in the Debian Branch itself. Not a criticism, but if one of those Distro's (graphical) in a VM, they already contain a web browser of some type... 

Just an observation and curiosity. Genuinely just trying to help.

---

### Post by QIII on 2021-08-03
Are you downloading the file to the host and then looking for it from the guest?

Why not make your USB device available to the guest and download it on the guest and follow the developer's instructions for installing it on the USB device?

If that application is not meant for a VM as suggested above, you may be on a wild goose chase.

---

### Post by MAFoElffen on 2021-08-03
Even if his host is 32bit: If he installed an Ubuntu Flavored Release, in a VM... Even if one of the Last 32bit Lubuntu versions (16.04) and release upgraded it to 18.04 LTS... He would have something supported, with a Web Browser... Firefox. That is lightweight and doesn't use much resources.

If firefox is still too heavy, then one of these: [https://www.triveditech.com/best-lightweight-and-fastest-browser/](https://www.triveditech.com/best-lightweight-and-fastest-browser/)

BUT, if he only is doing it to have a working Web Browser... He does not need to run a VM, with the extra overhead of running a VM just to use a web browser.

Another alternative... Install an Ubuntu Flavored Distro on the Host. Microsoft Windows Vista has been End Of Life since 4/11/2017 (Over 4 years now.)

Without the missing info and not knowing the overall picture of things. I'm only guessing and thinking I'm missing something there. We are missing pieces of the puzzle and making a lot of guesses at what you need to do, to do what you need.

---

### Post by MAFoElffen on 2021-08-03
> **snype9lives said:**
> [COLOR=#ff0000]internet explorer[/COLOR]  isnt working on it so im trying to put a portable version of firefox on it
I'm guessing that this means that the VM Guest is Vista? and for some reason Microsoft Explorer is not working(?)

Which if installed as a guest to a VM, it would not get updates, because it has been End of Service for over 4 years. It would still work, but say it is out-of-date. I mean, you need to turn auto-update off in the OS. It's not going to get any anyways. While it is working, then you just download what you need and install it, as you do in that OS...

I mean that I can install Windows 3.0, Windows NT or IBM OS2 in a VM and their old Web Browsers still work, if you have a working network connection for the VM... And configure the network connection.

If your web browser doesn't work... Do you have a working network connection from your VM to the outside world? Can you open a Command Line Session window and ping to the outside work from the VM? Such as maybe you don't have a working network driver for the for Vista to work as a VM? Or remembering back to Windows Vista, you haven't configured your networking yet, which part of that, concerns an internet connection...

I'm still guessing here.

---

### Post by MAFoElffen on 2021-08-03
For Instance, attached is a Windows Vista Ultimate VM I just spun  up...That version of Internet Explorer works, but with errors on invalid Site  Certs... and it doesn't understand HTML5,CSS3 and plugins... When it gives you a security error on certs, you just tell it you trust the site. It still works as a basic web browser, enough to download another.

From that you can go to kmeleonbrowser.org and download that browser and install it. See 2d attachment...

The link I gave you a few posts ago, Opera and UR also no longer supports MS VIsta since that article was written. K-Meleon still does. It uses the Gecko Engine from FireFox.

---

