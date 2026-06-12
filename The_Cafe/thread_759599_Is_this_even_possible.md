---
title: "Is this even possible?"
date: 2008-04-19
forum: The Cafe
---

### Post by Kernel Sanders on 2008-04-19
Hi all! I love ubuntu, but find myself still somewhat tied to Windows XP due to my quite frankly unnatural love and extensive use of Microsoft Office 2007.

My question is, is there a simple way to run this almost natively in Ubuntu?

I'm not thinking Wine or Cedega here, more some kind of virtualisation I think?

Specifically, is there a way for me to have a Word 2007 icon on my desktop, that when clicked will run Word 2007 in a virtualised window, that looks like it's actually being run natively, even though it's not?

Further to that, will Word 2007 run virtually be able to load from and save files from my home folder like it was installed natively on Ubuntu?

Please bear in mind I know absolutely NOTHING about virtualisation :(

Thanks for any and all help :)

---

### Post by rune0077 on 2008-04-19
If running through virtualization, you would have to boot up the virtual system before running anything from it. So if you clicked the icon on you desktop, it would then first have to boot XP/Vista normally, then run Office.

---

### Post by Kernel Sanders on 2008-04-19
> **rune0077 said:**
> If running through virtualization, you would have to boot up the virtual system before running anything from it. So if you clicked the icon on you desktop, it would then first have to boot XP/Vista normally, then run Office.

Oh ok. What about Office 2007 then being able too see and load files from my home folder in Ubuntu?

Also, is there any other method that can do what i'm looking for?

Cheers :)

---

### Post by rune0077 on 2008-04-19
> **Kernel Sanders said:**
> Oh ok. What about Office 2007 then being able too see and load files from my home folder in Ubuntu?


Yes, that would be possible with Windows XP, using shared folders (not yet implemented for Vista). I have never done this, but there should be a guide somewhere on the forum as to how this is done.

---

### Post by quanumphaze on 2008-04-19
Try out VirtualBox

[LIST=1]
[*]apt-get install virtualbox
[*]Add yourself to the 'vboxusers' group and logout>login
[*]Play with VirtualBox for a while
[*]Set up a WinXP VM with >256 MB RAM and >5 GB disk space
[*]Install XP onto the VM
[*]While running the XP VM click on one of the menu options to install guest additions
[*]You can now use 'Seemless' mode
[*]Enjoy
[/LIST]
This is a very cheap howto because I don't have it running in front of me at the moment and you have to figure most out yourself but I hope this gives you a basic idea on how to use it.

---

### Post by Kernel Sanders on 2008-04-19
Virtualbox is seemless? That sounds awesome!

Does that mean I can run Office 2007 as a native app? With it being able to access my home folder and the like?

---

### Post by billgoldberg on 2008-04-19
Letting virtualbox share the folders with ubuntu is tricky. 

I'm pretty sure the opensource client can't do it but the one on their website can.

---

### Post by popch on 2008-04-19
> **Kernel Sanders said:**
> Virtualbox is seemless? That sounds awesome!

Does that mean I can run Office 2007 as a native app? With it being able to access my home folder and the like?

Yes, yes, no and yes.

yes(1): 'Seamless' means that an application running under Windows in a virtual machine can show its window on your Linux desktop. I don't think that drag and drop between Linux and Windows applications will work, though.

Yes(2): Awesome: it can save quite some mouse clicking and such when cruising from application to application. Therefore, yes.

No: With VirtualBox you first start Windows much as you would start a browser or office. Once Windows is started, it looks much like any other application on your Linux desktop: it's just a window with your Windows desktop instead of your spreadsheet table or word document. It's within this Windows-in-a-window where you then start your Office 2007 (shudder).

Once your Windows and your Office is started, the window of the Office2007 app can be made to appear within a Gnome window on your Gnome desktop.

You can NOT start your MS Office app by double clicking an office document on your Gnome desktop.

You do not have to reboot your Windows in your virtual machine each time you want to use it. VirtualBox (and the other virtualisation tools I know of) implements some kind of 'hibernation' where the state of your Windows machine is saved to disk. Restoring a running Windows from this 'image' exactly as it was when saving usually takes less time than booting Windows and starting the applications anew.

Yes(3): You can attach any directory within the file system of your Linux session to a virtual box. Windows then uses that directory exactly as it would use a network drive - say - on your Samba or Windows server.

---

### Post by FuturePilot on 2008-04-19
You can set up a shared folder between the guest and the host so anything you put in that folder will be accessible to both the host machine and the guest.

---

### Post by Kernel Sanders on 2008-04-19
Excellent! Thanks for the info everyone! :)

---

### Post by the8thstar on 2008-04-19
Running either XP or Vista within VirtualBox is possible and it works very well in both cases. Just download the full version because it works better and it's still free (although not 'open-source').

To be 'comfortable', you need 1Gb RAM to run Ubuntu + XP in VirtualBox and 2Gb RAM for Ubuntu + Vista in VirtualBox. [COLOR="Red"]**In any case, hardware acceleration will not function which means that you can't play recent games. For the same reason, you won't be able to enable Aero in Vista (it will default to Basic).**[/COLOR]
[B][COLOR="Blue"]
However, Office 2007 will run perfectly in either environment.[/COLOR][/B]

As far as sharing folders, VirtualBox creates a virtual network between Ubuntu and Windows. First install VirtualBox utils (the .iso comes with the program) to set this automtically. Then to access your documents permanently, I would use for instance the following command at the prompt:

> c:>\ net use x: //<ubuntu>/<your home folder>/<whatever directory>

to assign your documents folder to a drive in windows. This way, you can easily access your documents in Ubuntu from Office 2007. In Vista, don't forget to run the prompt as an administrator, otherwise the command will fail. 

The info should be kept at the next logon, but just in case it's not, run the command again and things should be fine.

Let me know if this works or not.

---

### Post by meborc on 2008-04-19
[http://ubuntuforums.org/showthread.php?t=603661](http://ubuntuforums.org/showthread.php?t=603661) ([http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html) - this is the new version of the howto posted by the guy who made it on his blog)

this is a great guide for you :)

have fun!

[http://www.youtube.com/watch?v=Kxk6oFqMJVY](http://www.youtube.com/watch?v=Kxk6oFqMJVY) - this video is linked in the howto, you will see that it is possible to have one workspace completely run windows in seamless mode... still using the cube and compiz

everything is possible!!!

---

### Post by Kernel Sanders on 2008-04-19
You guys are awesome! Many thanks! :)

---

### Post by cardinals_fan on 2008-04-19
[http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml](http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml)

---

### Post by popch on 2008-04-19
There's a complete subforum dedicated to Virtualisation which very surprisingly is called [Virtualization.]("http://ubuntuforums.org/forumdisplay.php?f=308")

There are some very knowledgeable and helpful people there if it comes down to technical questions.

---

### Post by tylerspaska on 2008-04-19
I haven't tried this yet, but I think this is what you're looking for - or at least some variation of it.

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by intense.ego on 2008-04-19
Just out of curiosity, what's wrong with running it in Wine or Crossover?

---

### Post by cardinals_fan on 2008-04-19
> **intense.ego said:**
> Just out of curiosity, what's wrong with running it in Wine or Crossover?
Office **2007** doesn't run in either [yet].

---

