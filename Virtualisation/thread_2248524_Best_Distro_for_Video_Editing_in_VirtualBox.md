---
title: "Best Distro for Video Editing in VirtualBox"
date: 2014-10-15
forum: Virtualisation
---

### Post by Wl73OMA7GA on 2014-10-15
I started a newscast at my high school last year. Because the school has an extremely small budget, I decided to do the entire show using open source software. All the software I used runs in both Windows and Linux except the video editor, OpenShot. That was not a problem when i was there, since I run Ubuntu; however, I am now trying to get a friend of mine setup with creating the show. He uses Windows only. I wanted to run the video editor in VirtualBox to make it easier for him and then transition to OpenShot 2.0 for Windows when it is released. 

Now the question: What would be the best Linux distro to use for this? All that will run in the VirtualBox is OpenShot. I want a light distro, so that OpenShot gets as much resources as possible. I would prefer an Ubuntu based distro because that's what I have experience using, but I am open to others, if there is something better.

If it matters: If i had to guess, I think he is using Windows 8 with 4GB RAM and either a Core i3 or i5 processor.

Thanks for your help.

---

### Post by ajgreeny on 2014-10-15
I'm no expert but I wonder if VBox is the way to go at all.

The maximum graphics memory you can use in VBox is 128MB, as far as I'm aware, and I have some uncertainty about whether or not that is going to be enough for video editing.

I hasten to add that I do not really do any video editing myself, so I may be quite wrong about the graphics requirements, and sufficient CPU power is perhaps all you need. Also you should check out multi-threading when the video editor is running as I don't know how, or if, that will be affected by running in a VM.

---

### Post by Wl73OMA7GA on 2014-10-15
I forgot to specify. Because of the cable system at our school, the entire show is produced in Standard Definition. For a while, I edited the show on a decade old machine that had only 1GB RAM and a Pentium 4 processor (It froze a lot, but it was possible), so it should be possible to do this in VirtualBox. I just want to know what would be a good really light distro to limit the memory consumption.

---

### Post by hamishmb on 2014-10-15
Well, Lubuntu wouldn't do too badly, and it doesn't look too unlike Windows either. You can get even lighter than that, but that's when it starts getting tricky to set up I think.

Hamish

---

### Post by ajgreeny on 2014-10-15
I agree that Lubuntu may be a good one to try, and if you do that, you can choose openbox from the login screen and have an incredibly low resource using system; it will look very spartan with a totally empty desktop by default, but a right click on the desktop will give you a menu, if I remember correctly.

---

### Post by calebp on 2014-10-17
Thanks for the tips. I'll try it out.

---

### Post by MartyBuntu on 2014-10-19
If you're friend is a Windows person, they should just use some native Windows app.

Video editing in a virtualised environment, by someone who doesn't prefer/use/want Linux is going to be brutal.

---

### Post by calebp on 2014-10-19
Yes, a Windows program would be the prefered option; however, I searched and searched for months before starting the program, and there is no free Windows program that has all of the necessary features. I am just trying to get him by with VirtualBox until the Windows version of OpenShot is released.

I would expect that this is at least possible because another friend of mine has run Kdenlive successfully on regular Ubuntu through VirtualBox before, but he had a much nicer machine with a rediculous amount of RAM.

---

