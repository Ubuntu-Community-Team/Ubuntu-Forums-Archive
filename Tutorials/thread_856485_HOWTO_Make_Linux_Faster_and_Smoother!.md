---
title: "HOWTO: Make Linux Faster and Smoother!"
date: 2008-07-11
forum: Tutorials
---

### Post by sayakb on 2008-07-11
[I][B][FONT=trebuchet ms][SIZE=4][COLOR=Sienna]Reduce Swappiness[/COLOR][/SIZE]
[/FONT][/B][/I][FONT=trebuchet ms][SIZE=3]If your computer has 1GB+ RAM, you would be hardly needing your swap space in most cases. It is evident that the RAM is much faster than your hard drive (A good 677MHz DDR2 can give 3000+ MiB/s while a standard hard drive can give around 50MiB/s). So it's better to let the RAM handle most of the processes. The tendency to use swap is called **swappiness**.Swap space is a cached area on the HDD that the OS utilizes as a memory overflow/dump area. To reduce swappiness, at a terminal, type in:
[/SIZE][/FONT][FONT=courier new][SIZE=3]```
sudo sysctl -w vm.swappiness=10
```[/SIZE][FONT=trebuchet ms][SIZE=3]If you wish to reduce the swappiness permanently, do:
[/SIZE][/FONT][SIZE=3]```
sudo nano /etc/sysctl.conf
```[/SIZE][FONT=courier new][SIZE=3]

[/SIZE]  [FONT=trebuchet ms][SIZE=3]And change the **vm.swappiness **value to 10. If the line doesnot exist, add the line [/SIZE][/FONT][/FONT][/FONT][SIZE=3]*vm.swappiness=x*[/SIZE][FONT=courier new][FONT=courier new][SIZE=3]
[/SIZE] 
[SIZE=4][COLOR=Sienna]
[/COLOR][/SIZE][I][B][FONT=trebuchet ms][SIZE=4][COLOR=Sienna]Using preload[/COLOR][/SIZE]
[/FONT][/B][/I][FONT=trebuchet ms][SIZE=3]Preload caches the most accessed applications on your disk and memory. Preload should not be installed on systems having memory less than 1GB, otherwise, it would not have any effect, or rather would advesly affect the performance. To install preload, at a terminal:
[/SIZE] [FONT=courier new][SIZE=3]```
sudo apt-get install preload
```[/SIZE][FONT=trebuchet ms][SIZE=3]Once installed, preload will automatically start during boot. It normally takes 20-30 launches of a program to start being cached by preload.
[/SIZE] [SIZE=4][COLOR=Sienna][SIZE=3]
[/SIZE] 
[/COLOR][/SIZE][I][B][SIZE=4][COLOR=Sienna]Disable unneeded startup services[/COLOR][/SIZE]
[/B][/I][SIZE=3]Some services start-up automatically even if you don't need them. Goto **System->Administration->Services** and press Unlock to provide your password for the keyring. You may disable services like Bluetooth, Logging and Printing services if you don't need them.
[/SIZE] [/FONT][/FONT][/FONT][/FONT][/FONT][SIZE=3][[IMG]http://i34.tinypic.com/29aqwrm.png[/IMG]]("http://i34.tinypic.com/29aqwrm.png")


[/SIZE]   [FONT=trebuchet ms][SIZE=3]
[COLOR=Sienna]***Use lighter alternatives***[/COLOR]
You can use lighter alternatives to the existing programs you may use:
[/SIZE][/FONT]
[LIST]
[*][SIZE=3]**[FONT=trebuchet ms]Firefox[/FONT]**[/SIZE][FONT=trebuchet ms][SIZE=3]: Firefox has slightly higher memory consumption. You may use *Opera* or *Epiphany* as an alternative.[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]**OpenOffice:** You may use  *AbiWord *and *Gnumeric Spreadsheet* as an alternative to OO-Word Processor and OO-Spreadsheet[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]**Nautilus:** You may use *Thunar *or *PCManFM *as an alternative.[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]**Gnome-Panel:** You can use *FBPanel* as an alternative.[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]**Gnome-Terminal: **You may use *XTerm *as a lighter alternative.[/SIZE][/FONT]
[/LIST]
[FONT=trebuchet ms][SIZE=3]If you want to reduce RAM usage drastically, use a lite WM like Openbox and configure it to use Gnome apps. In that way, you can use all Gnome apps but you would use up very less memory.
Openbox configuration guide: [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
[/SIZE] 

[SIZE=4][COLOR=Sienna]***Disable unneeded ttys***[/COLOR][/SIZE]
[SIZE=3]Ubuntu comes with 6 ttys enabled. You usually don't need more than 1 tty at a time. To disable tty2 to tty6:
[/SIZE] [/FONT][SIZE=3]```
sudo bash
cd /etc/event.d
mv tty2 tty2~
mv tty3 tty3~
mv tty4 tty4~
mv tty5 tty5~
mv tty6 tty6~

```[/SIZE][FONT=trebuchet ms][FONT=courier new][SIZE=3]
[/SIZE] [FONT=trebuchet ms][SIZE=3]Now, at a terminal, do:
```
sudo gedit /etc/securetty
```[/SIZE][SIZE=3]And **carefully** comment out **tty2 to tty6 **by adding a # in front of them. Save it and close the file. Disabling unneeded ttys also helps to enhance security: [http://www.bigwebmaster.com/General/Howtos/Net-HOWTO/x810.html](http://www.bigwebmaster.com/General/Howtos/Net-HOWTO/x810.html).
[/SIZE]  [SIZE=4][COLOR=Sienna]
[/COLOR][/SIZE][SIZE=4][COLOR=Sienna]***Make OpenOffice faster in Ubuntu***[/COLOR][/SIZE]
[SIZE=3]Launch OO-Word Processor. Goto **Tools->Options **and click on **Memory**. From top to bottom on the window:
[/SIZE] [/FONT][/FONT][/FONT]
[LIST]
[*][FONT=trebuchet ms][SIZE=3]Reduce the **Number of steps** to 20[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Set **Use for OpenOffice.org** to 128MB[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Set **Memory per object** to 20MB[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]Set **Number of Objects **to 20[/SIZE][/FONT]
[*][FONT=trebuchet ms][SIZE=3]*Check*** Enable systray Quickstarter**[/SIZE][/FONT]
[/LIST]
[FONT=trebuchet ms][SIZE=3]And press **OK** button.
Note: Enable the quickstarter only if you use OpenOffice extensively. Otherwise, the quick starter would be unneeded.


After performing these changes, do a reboot for the settings to take effect.

**NOTE: This HOWTO is based on useful information collected from various online resources. This is neither a speculation, nor has been benchmarked and published. Users can try these tweaks, and keep the new settings if they find it beneficial, or switch back to their old settings otherwise, as these are completely safe and reversible changes to your system. I personally see productive output of these tweaks on my computers :)**
[/SIZE][/FONT]

---

### Post by sarah.fauzia on 2008-07-12
What is the effect of disabling the other ttys? It's nice to disable what I don't need but if it has any risks involved.. just would like to know! :)

---

### Post by sayakb on 2008-07-12
> **sarah.fauzia said:**
> What is the effect of disabling the other ttys? It's nice to disable what I don't need but if it has any risks involved.. just would like to know! :)
No, there are no risks involved. Also, we rarely actually need the ttys until something goes wrong and we need the terminal immediately. You may keep two ttys active and disable the rest.

---

### Post by nycste on 2008-07-12
heya just found this thread trying to fix the ttys

is my error, what do i do

sudo bash
cd /etc/event.d
/etc/event.d# ls
control-alt-delete  rc1  rc4  rc-default   sulogin  tty3~  tty6
logd                rc2  rc5  rcS          tty1     tty4~
rc0                 rc3  rc6  rcS-sulogin  tty2~    tty5
mv tty2 tty2~
mv: cannot stat `tty2': No such file or directory


thanks

so i want to 
1. check to see if i already disabled them? and 
2. if they are still running findout how to properly disable them

---

### Post by sayakb on 2008-07-12
You have disabled (renamed) tty2, tty3 and tty4 as the output reflecs. Do:
```
mv tty5 tty5~
mv tty6 tty6~
```

Here is how it should look:
```
glade@Mean-Machine:/etc/event.d$ ls
control-alt-delete  rc1  rc4  rc-default   sulogin  tty3~  tty6~
logd                rc2  rc5  rcS          tty1     tty4~
rc0                 rc3  rc6  rcS-sulogin  tty2~    tty5~
glade@Mean-Machine:/etc/event.d$ 
```

---

### Post by nycste on 2008-07-12
> **LinuxIsInnovation said:**
> You have disabled (renamed) tty2, tty3 and tty4 as the output reflecs. Do:
```
mv tty5 tty5~
mv tty6 tty6~
```

Here is how it should look:
```
glade@Mean-Machine:/etc/event.d$ ls
control-alt-delete  rc1  rc4  rc-default   sulogin  tty3~  tty6~
logd                rc2  rc5  rcS          tty1     tty4~
rc0                 rc3  rc6  rcS-sulogin  tty2~    tty5~
glade@Mean-Machine:/etc/event.d$ 
```

ok well i did what you told me, i currently have no idea what i fully even did lol, but my ls command shows your setup so thanks

how do i see that i disabled them, sorry for asking such a simple question prob

---

### Post by sayakb on 2008-07-12
Renaming them and commenting them in the /etc/securetty file would disable them. Sorry, I just missed out the /etc/securetty file in the post. I'll add it now :)

---

### Post by nycste on 2008-07-12
> **LinuxIsInnovation said:**
> Renaming them and commenting them in the /etc/securetty file would disable them. Sorry, I just missed out the /etc/securetty file in the post. I'll add it now :)

just to make sure
```

# /etc/securetty: list of terminals on which root is allowed to login.
# See securetty(5) and login(1).
console

# for people with serial port consoles
ttyS0

# for devfs
tts/0

# Standard consoles
tty1
#tty2
#tty3
#tty4
#tty5
#tty6
tty7
tty8
tty9

ETC.......
```

looks solid?

---

### Post by sayakb on 2008-07-12
Sorry for the late reply.. I was offline..
And yes, looks OK to me :)

---

### Post by PGLGreg on 2008-07-12
What reasons are there to think that the changes you recommend improve the operation of a Linux system?  What tests have you performed, and how did they come out?

---

### Post by sayakb on 2008-07-12
Except for the tty disabling (which is more inclined towards better security), decreasing swappiness, using preload, disabling unneeded services are directly related to increase in performance. 
1. Preload: Caches applications priorly. Minimum requirements are 1GB RAM.
[http://digg.com/linux_unix/Drastically_Speed_up_your_Linux_System_with_Preload](http://digg.com/linux_unix/Drastically_Speed_up_your_Linux_System_with_Preload)
2. Disabling unneeded services dont need any clarification IMO
3. Decreasing Swappiness: This has been tested and found to be effective. Due to that reason, new kernels would support dynamic control of swappiness. For lesser RAM usage, swappiness would decrease to much lower values than the current fixed value: [http://kerneltrap.org/node/1044](http://kerneltrap.org/node/1044)
4. OO performance: [http://www.blog.solarwind.metafy.org/2008/02/25/how-to-speed-up-openoffice-in-linux/](http://www.blog.solarwind.metafy.org/2008/02/25/how-to-speed-up-openoffice-in-linux/)

---

### Post by Jose Catre-Vandis on 2008-07-12
i don't have a vm.swappiness entry in my sysctl (on Hardy). Should I still add one?

---

### Post by sayakb on 2008-07-12
Yes.. Add the line.

---

### Post by Jose Catre-Vandis on 2008-07-12
OK thanks :)

---

### Post by PGLGreg on 2008-07-12
> **LinuxIsInnovation said:**
> Except for the tty disabling (which is more inclined towards better security), decreasing swappiness, using preload, disabling unneeded services are directly related to increase in performance. 
1. Preload: Caches applications priorly. Minimum requirements are 1GB RAM.
[http://digg.com/linux_unix/Drastically_Speed_up_your_Linux_System_with_Preload](http://digg.com/linux_unix/Drastically_Speed_up_your_Linux_System_with_Preload)
2. Disabling unneeded services dont need any clarification IMO
3. Decreasing Swappiness: This has been tested and found to be effective. Due to that reason, new kernels would support dynamic control of swappiness. For lesser RAM usage, swappiness would decrease to much lower values than the current fixed value: [http://kerneltrap.org/node/1044](http://kerneltrap.org/node/1044)
4. OO performance: [http://www.blog.solarwind.metafy.org/2008/02/25/how-to-speed-up-openoffice-in-linux/](http://www.blog.solarwind.metafy.org/2008/02/25/how-to-speed-up-openoffice-in-linux/)
Thanks for the references.  I don't have any questions about 1. or 4., but I have some doubt about 2. and 3.  For 2., I just don't see any reason to think that disabling an unused service will have a good effect on performance.  For 3., I would like some evidence that your value for swappiness is better than the default or other values one might assign.

---

### Post by sayakb on 2008-07-12
2. The bluetooth service and the cupsys service keeps running in background. If I dont use it, I find no reason to keep it running.

3. Have you tried to fill up your RAM? Let swappiness be at its default value, open FF and keep pressing Ctrl+T and keep a watch on the system monitor side by side. Check when and how much the swap fills up at the default swappiness level. Now decrease swappiness and check again. Ofcourse, the swap would start filling up much later. I tested this on my laptop.. With the default swappiness, with about 45-50 tabs open, my RAM usage goes upto 700MB and swap goes 250MB.
With swappiness at 10, the swap usage is 100MB when RAM is 900MB full. More the swap is used, slower the system gets. I dont know if you would regard this as, but what I have seen that even with the RAM empty, the swap fills up unnecessary, and makes the system slow. And that is the reason why the new kernel has a dynamic swappiness value..

---

### Post by PGLGreg on 2008-07-12
Thanks for taking the time to tell us what sort of evidence supports your recommendations.

---

### Post by sayakb on 2008-07-12
np.. The Note portion at the bottom of the HOWTO is clear enough I guess :)
You may not wish to alter swappiness, rather wait for the new kernel to release and do it for you!
Plus, its not my recommendations. Its a collection of facts that you can easily find arbitrarily distributed on the web..

---

### Post by nycste on 2008-07-19
heya, im just looking through my processes running and all that jazz and have no idea unless i google each and every one of them about what they are and what they do..


are there any guides or scripts to remove most of these programs that are never needed as long as they can be installed at a later date

case in point i removed bluetooth thing from startup following ur guide, i thought it worked but clearly bluetooth-applet thing was still running so i said lets remove you. looked it up was told to go to synaptic and remove everything connected to bluez, i didnt remove the libblue something file because it said it was needed for 5-10 other things and i used my brain quickly and said dont remove that lol..

bluetooth-applet was still running after removing all bluetooth applications and programs minus the libblue file in question.. then i read people who removed that lost ability to use nautilus and another major program... so im glad i didnt..

summary. guide to removing all this useless stuff for people who might never need it.. bluetooth is a simple example, and printing servies if you dont have a printer.. now if you do ever add a printer id imagine it would be as easy as going to add/remove or synaptic and installing drivers again and printer should work or donwloading them from the companies website or something

thanks for any response to this

---

### Post by Martin von Wittich on 2008-08-01
> **LinuxIsInnovation said:**
> 
Ubuntu comes with 6 ttys enabled. You usually don't need more than 1 tty at a time. To disable tty2 to tty6:
```
sudo bash
cd /etc/event.d
mv tty2 tty2~
mv tty3 tty3~
mv tty4 tty4~
mv tty5 tty5~
mv tty6 tty6~
```
Now, at a terminal, do:
```
sudo gedit /etc/securetty
```
And **carefully** comment out **tty2 to tty6 **by adding a # in front of them. Save it and close the file. Disabling unneeded ttys also helps to enhance security: [http://www.bigwebmaster.com/General/Howtos/Net-HOWTO/x810.html](http://www.bigwebmaster.com/General/Howtos/Net-HOWTO/x810.html).


Sorry for these harsh words, but that is blatant nonsense. While disabling ttys is not that dangerous as long as there is at least one still active, it's nonetheless of no use. For each activated tty, Upstart will spawn one getty process. According to pmap, one such getty processs requires just about 270KB memory. So what's the point? Disabling 5 ttys will effectively save just ~1MB memory and therefor the computer won't get any faster (nor more secure, see below).

> **LinuxIsInnovation said:**
> 
Now, at a terminal, do:
```
sudo gedit /etc/securetty
```
And **carefully** comment out **tty2 to tty6 **by adding a # in front of them. Save it and close the file. Disabling unneeded ttys also helps to enhance security: [http://www.bigwebmaster.com/General/Howtos/Net-HOWTO/x810.html](http://www.bigwebmaster.com/General/Howtos/Net-HOWTO/x810.html).


When reading this I feel impelled to assume that you have actually no idea what you're talking about; even the website you're using as reference doesn't support your statement at all.
The securetty file is read by login(1) to determine on which ttys root is allowed to login; it has absolutely nothing to do with enabling/disabling ttys. Probably the only time when you need to edit this file is when you're using a serial console - if that is not listed in this file, you'd need to add it so you can login as root over the serial console.

Martin

---

### Post by rbolio on 2008-08-04
HI!
 Hey i did all of the recomendations.... and uh....my Laptop doesnt work right... none of the applications, places system......menus work, none of the bars work and i dont know.....its as if my computer was partially frozen.....any help please?

---

### Post by sayakb on 2008-08-05
I don't think any of the tweaks described can cause such results. Can you provide more details? Try changing the swappiness back to 30 (which is the default value), though I doubt that it would do any good. Further information will be appreciated.

---

### Post by bhavi on 2008-08-20
Nice tutorial. If you can mention the websites in a references heading it would be great.

---

### Post by Stoowyguy on 2011-08-16
Thanks Bro!! The installing that preload thing kind of helped alot. Why does it help so much?:-s

---

### Post by Duncan Williams on 2011-08-18
[http://techthrob.com/2009/03/02/dra](http://techthrob.com/2009/03/02/dra)

---

### Post by '76 on 2011-08-20
great thread, never seen libre-office load so fast!

thanks sayakb!

---

### Post by timitiwinkle on 2012-06-20
we can make  Linux to run faster by changing the file system that was installed on the computer or use a program called Prelink, which links shared objects for programs. [mainframe modernization](http://www.mosttechnologies.com/mainframes) Find a system on Linux that will optimize how small files are used with help from a software developer in this free video on Linux.

---

