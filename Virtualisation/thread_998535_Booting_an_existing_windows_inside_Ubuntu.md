---
title: "Booting an existing windows inside Ubuntu"
date: 2008-11-30
forum: Virtualisation
---

### Post by amirage on 2008-11-30
Hi all

I have been searching high and low for the past several days to get the above subject matter a working proposition. However, so far I've only been able to get information on how to do the same with an XP installation. 

The issue is that I already have a valid Vista Business installation in my laptop (Dell XPS1730 - 2.4ghz, 2gbDDR2, 200HDD split into 3 partitions one with windows, other with ubuntu and another with drivers). The question you will be asking is why would anyone in their right mind want to boot into windows...simple I have a custom-made accounting package that runs solely on windows. The package uses the server to log me in and run several funtions...

The best help I have got so far is from [http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

I haven't tried anything yet as the steps mentioned in the above link is for XP. As we all know how notorious is Vista known for making simple things complicated, I haven't gone ahead.

Hence, can someone please help me out over here with a "how-to". I will greatly appreciate any help. Please let me know if you need further information.

Regards

Amit

---

### Post by p_quarles on 2008-11-30
Moved to Virtualization.

I have heard of people doing this successfully with Virtualbox. I haven't done this myself, but that's one direction to explore.

---

### Post by lykwydchykyn on 2008-11-30
What you're wanting to do is virtualize, which you can do with vmware, qemu, or, as suggested, VirtualBox.  Personally I use the latter, and I recommend it highly.

Now, the problematic part is that you want to use an *existing* windows install.  It can be done, but there is a problem.  Windows is very finnicky about changes to the underlying hardware -- I've not worked much with Vista, but 2k and XP would crash if you changed the hardware to any great extent. 

When you run something like virtualbox, you are presenting the guest OS with a set of Virtualized hardware, which is very likely nothing remotely like the actual hardware on your system.  So, if you try to use that install, it's likely to crash on you.  Sometimes you can rescue it with a repair install, but I wouldn't be able to vouch for that technique on Vista.

Your best bet is to create a fresh Vista install in a virtual environment, though you may want to check on the legality of that with your Vista license.

---

### Post by p_quarles on 2008-11-30
> **lykwydchykyn said:**
> Your best bet is to create a fresh Vista install in a virtual environment, though you may want to check on the legality of that with your Vista license.
+1.

If it's possible to reinstall, this is by far the easiest way of approaching a situation requiring a virtualized Windows installation.

---

### Post by canabal on 2008-12-01
I created a tutorial [here.]("http://ubuntuforums.org/showthread.php?t=984437")

Try it out and feel free to leave feedback.

---

### Post by bodhi.zazen on 2008-12-01
There are 2 tutorials linked in the Mega sticky on how to do this (One for Vista and the other for XP).

---

### Post by amirage on 2008-12-02
All

Thanks very much for the support for far. I have read a lot about the whole virtualisation concept and have understood it to a large extent. Today, I tried to do it step-by-step as stated by canabal in the relevant post. However, I regret to say that I have failed. It's like that I did something wrong with the grub.iso creation. I simply couldn't understand the following steps:
    > Change the default option to your vista partition.
    > Set the timeout at 1.
    > If your vista partion says savedefault in the grub.lst be sure to delete that line.

Can someone please help me out over here? 

In the event that I get Vista to boot in VM, do you think I can use the Windows Network? My accounting package accesses the network to log me into the server. 

Your views will be greatly apprecitated...

Cheers

---

### Post by bodhi.zazen on 2008-12-02
Those are edits or changes to /boot/grub/menu.lst

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Dedoimedo on 2008-12-02
You might have problems with the activation as the underlying hardware changes. The best bet, as already mentioned, is to create a dedicated virtual machine and install windows (whichever) from scratch.
Dedoimedo

---

### Post by amirage on 2008-12-03
All

Thanks for the support so far. I did figure out that the steps I mentioned pertained to editing the menu.lst. However, after opening the menu.lst in a notepad, I was completely lost on what to do next. This is why I had asked about the steps in detail.

I would greatly appreciate your help in this regard. If you could give further steps for each of the steps mentioned.

Another question, when I make the .vmdk file, can I simply copy paste canabal's code into the terminal or is there a need to edit the code. If so, can you please guide me as to what needs to be done...

Awaiting your kind help...

---

