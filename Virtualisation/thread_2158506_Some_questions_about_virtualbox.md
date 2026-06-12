---
title: "Some questions about virtualbox"
date: 2013-06-29
forum: Virtualisation
---

### Post by Inodoro Pereyra on 2013-06-29
I'm planning to buy a new laptop shortly. Somebody told me, a few years ago, that I could run Windows 7 on virtualbox, and that way I could run Solidworks (the only reason I need windows) on  it.

Now, these are the questions:
I'm planning to try Openbox, as I'm having problems with Unity and Conky on my actual PC.

1. Is that the best way to run Solidworks on Openbox?
2. Do I have to dual boot Windows and Openbox, or do I have to install Windows inside Openbox (in a kinda wuby configuration)?
3. If I have to dual boot, will the Solidworks work store in the Windows partition, or the Openbox partition?
4. Do I have to look for any specific hardware configuration to run this setup?

Thanks in advance. :D

---

### Post by deadflowr on 2013-06-29
Since you'll be running Windows7 in a virtualbox, the Ubuntu desktop shouldn't matter.
Basically what you'll be doing is running a program within Ubuntu to run Windows.
Virtualbox is quite easy to setup.
The base setup for a Virtualbox is a .vdi virtual file, which takes space for within the Ubuntu partition and pretends it's a separate partition.
They offer other disk setups as well.
It's best to read through the documenation though, for a better understanding of what you'll need to do to get it running smoothly.
[https://www.virtualbox.org/wiki/Documentation](https://www.virtualbox.org/wiki/Documentation)

Once you get it setup though, it'll be just like installing any system, just that you'll be doing while another system is still in use.

Additionally, hardware configurations will need the guest additions installed.
The documentations should give a good explanation of how to do that. It's quite simple.

---

### Post by SeijiSensei on 2013-06-29
Just remember that to install Windows in a VirtualBox you need a licensed DVD installation disk.  Most computers do not ship with Windows DVDs these days, so you will need to burn a set using whatever utility your computer's OEM provides.  If you blow away the pre-existing Windows installation before creating an installation image you will be out of luck.

---

### Post by Inodoro Pereyra on 2013-06-29
Thank you both for replying. 

Deadflowr: I don't know if I can't find it, or if it's written in a way that I can't understand it (don't get fooled by the time I've been a member of this forum, due to circumstances beyond my control, I'm as noob as they come), but I can't find the answers to my questions in the virtualbox page. Could you, or anybody else, answer them, so I have a place to start? 
So far, all I could find is that I will need enough memory to run both OS's at the same time, and more is better.

   > **deadflowr said:**
> Since you'll be running Windows7 in a virtualbox, the Ubuntu desktop shouldn't matter. 

  Uh, oh. I hear bad news coming... 
 I want to run virtualbox (and W7 in it) on only one desktop, while I keep Openbox on the other ones. Can't I do that? 

 Seijisensei: the Windows installation disk is not a problem.

---

### Post by coldraven on 2013-06-30
From memory you can run your Win7 VM in seamless mode. (my memory that is, I don't have it installed at the moment)
[http://www.techrepublic.com/blog/opensource/virtualbox-seamless-mode-the-only-way-to-virtualize/757](http://www.techrepublic.com/blog/opensource/virtualbox-seamless-mode-the-only-way-to-virtualize/757)
That means it is just another window that you can drag to any desktop.
Don't use the Virtualbox from the repos, download the latest version from [URL="https://www.virtualbox.org/"]https://www.virtualbox.org/



[/URL]

---

### Post by SeijiSensei on 2013-06-30
I use seamless mode when running Win7 in VirtualBox.  The two operating systems share the display.  I configure Windows to put its taskbar at the top of the screen.  Then I can move my cursor to the bottom to bring up the KDE panel or up to the top to bring down the Windows taskbar.

---

### Post by Inodoro Pereyra on 2013-07-02
Thanks everybody. 
I finally decided not to use it. Way too much trouble.

I just installed #! on my new lappy. So far, I'm loving it. :D

---

