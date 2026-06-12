---
title: "Load Ubuntu from RAM"
date: 2006-10-27
forum: The Cafe
---

### Post by /dev/psaux on 2006-10-27
How would I load Ubuntu from RAM after a small server install?

---

### Post by Tomosaur on 2006-10-27
This makes no sense. RAM is volatile memory, meaning whatever is stored in it is lost if the computer is shut down. You can not boot from RAM. You can, however, use a LiveCD to launch Ubuntu, which utilises lots of your RAM to show the desktop / run programs etc.

Alternatively, you may want to consider downloading a lightweight window manager so you can use Ubuntu with a GUI, while using minimal RAM. 

Basically - you cannot 'run Ubuntu from RAM'. Since you've made a server install, Ubuntu should boot fine, except you'll be at the command line instead of GDM. If RAM is limited on your machine, but you want to try a GUI anyway, then xubuntu may be for you. Log in as normal, and type 'sudo apt-get install xubuntu-desktop'. This should install the programs required to run the XFCE environment (and probably a bunch of other stuff too).

Alternatively, you can just find a window manager that suits you. I would go for Fluxbox.

For any GUI, you will need to install the X-server.

---

### Post by slimdog360 on 2006-10-27
I think you can load puppy linux completely into RAM, but I havent tried. But of course as it was already said this would only be a one time thing, unless you could save your session on a usb drive or something.

---

### Post by ~LoKe on 2006-10-27
Until DRAM, this would be pretty damn pointless.

---

### Post by red_Marvin on 2006-10-28
I am pretty sure he meant to ask "how to load ubuntu into ram att boot and then continue from there" DSL has such a feature (set "toram" as a boot command). But I don't know if ubuntu has an equivalent since it's bigger...

---

### Post by Tomosaur on 2006-10-28
Ah I see now.

Still, the question remains - what possible situation would require this? If the server install was successful, then running a lightweight GUI on top of that is pretty simple, unless the machine is actually being used as a server, in which case all of the RAM may be required for related processes.

If you are trying to achieve what red_Marvin suggested, then a different distribution may be what you need, since I don't think Ubuntu is able to do this (yet :P )

---

### Post by maniacmusician on 2006-10-28
yeah, i guess the OP needs to provide more information on why he wants this.

And please don't recommend to use apt-get like that...use

>  sudo **aptitude** install xubuntu-desktop

that way, you'll be able to uninstall it easily by doing "sudo aptitude remove xubuntu desktop", whereas it would be a little harder with apt-get, lol.

---

### Post by mips on 2006-10-28
The i-ram module is seen by the bios as a SATA drive. it connects via a normal sata cable just like the rest of your hard drives. So you should be able to simply install to it like any other drive, no problem.

I read somewhere that they are bringing out a 8GB version. You should be able to fit and entire linux install on that no problem, just have your /home on a normal HD. Geez 4GB is probably more than enough for most people.

The fact that is uses low latency DDR ram means that it should be snotfast. Would really be interesting to see it in action. A 5sec boot would be nice :)

I'm actually gonna call the local gigabyte distributor on monday for pricing as this looks really interesting.

Some more reading for those interested:
[http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2180&ProductName=GC-RAMDISK](http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2180&ProductName=GC-RAMDISK)
[http://www.tomshardware.com/2005/09/07/can_gigabyte/](http://www.tomshardware.com/2005/09/07/can_gigabyte/)
[http://www.anandtech.com/storage/showdoc.aspx?i=2480](http://www.anandtech.com/storage/showdoc.aspx?i=2480)
[http://www.overclockers.com/tips00788/index02.asp](http://www.overclockers.com/tips00788/index02.asp)
[http://www.pcper.com/article.php?aid=224&type=expert](http://www.pcper.com/article.php?aid=224&type=expert)

---

### Post by pyite on 2007-04-25
You would probably get the most benefit by just loading /usr onto the ram disk.  It doesn't change too often usually.  You might want to set up a cron job to tar up the contents of /usr every once in awhile, just in case you lose power for a few hours.

---

### Post by happy-and-lost on 2007-04-25
Didn't Knoppix have a load to RAM feature (For 1GB+) before it got bloated with Beryl?

---

### Post by matthinckley on 2007-04-25
> **maniacmusician said:**
> yeah, i guess the OP needs to provide more information on why he wants this.

And please don't recommend to use apt-get like that...use



that way, you'll be able to uninstall it easily by doing "sudo aptitude remove xubuntu desktop", whereas it would be a little harder with apt-get, lol.

Why is it harder with apt-get? now that it has the autoremove feature I find it very easy.  Is there something else I'm missing here?

---

### Post by ssam on 2007-04-25
its not quite the answer you are looking for, but:

the command
```
find / -exec cat {} \; > /dev/null
```

would read every file on the disk, and output them to /dev/null (ie nowhere).

when you read a file on linux the kernel keeps a copy in memory. it will only be remove from the memory cache if the space is needed by running programs.

you might want to tune the find bit of them command (see man find), so that it skips things like /proc (which is in memory anyway)

the whole coping your root partition to a ram disk and then running from that is possible (as people have said some live cds do it). i am not sure how one does it though. try looking up pivot_root and initrd.

--
found this [http://www.schnozzle.org/~coldwell/diskless/](http://www.schnozzle.org/~coldwell/diskless/)

---

### Post by h4mx0r on 2009-01-02
in /boot/grub/menu.lst there is are options after each kernel line such as quiet and splash etc. Just put toram there and if you load that option it will be fully in ram.

---

### Post by andamaru on 2009-01-02
> **maniacmusician said:**
> yeah, i guess the OP needs to provide more information on why he wants this.

And please don't recommend to use apt-get like that...use



that way, you'll be able to uninstall it easily by doing "sudo aptitude remove xubuntu desktop", whereas it would be a little harder with apt-get, lol.

the autoremove switch makes aptitude unneeded

sudo apt-get autoremove xubuntu desktop

should do the same thing as aptitude

---

### Post by Sef on 2009-01-02
Closed for necromancing.

---

