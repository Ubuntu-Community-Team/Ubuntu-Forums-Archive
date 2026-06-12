---
title: "I dont understand"
date: 2020-06-11
forum: Ubuntu, Linux and OS Chat
---

### Post by imsoslow on 2020-06-11
Help ....
Why is it soooo hard to do something so simple ???/
Let me explain, I have a Dell desktop ,, it running fine ,
it has loads of memory and 3 hard drives , and all kinds ,,
So .....
the problem is Google ... and Windows ... of course ...
this is fairly old computer ...
and its running Win XP !!
google wants to ''update chrome '' as many sites don't work well now.
Chrome wont update because ... win XP is no longer supported ..
I know , I know ,,, why not update win ... then chrome ,, and all my troubles will dissapear..

well then for the messing about and new software ,,,why not  just throw it away and get a new one ..
ok maybe ...........
but is quite good really ...still..
So what to do ? use it as a server ... mmmm no
how about a new operating system? .....welll yes...why not ?..lets see how good this linux is and all this new stuff i hear about ...why not ...?
well ok then ..
.I'll try Ubuntu ...OK theres a light version ....well ok 
so i  Put Lubuntu on a 16Gb USB stick .. with another boot program ... and away I go ...well ok ..this is good ..
Problem No 1 
Wifi ,,,,,,why..... is  the  WIFI ..., which is the simplest and most needed thing today,  soooo difficult to get going ...
I just cant get it ..
My computer logs onto the home wifi router with a USB stick in the front port ..
but Lubuntu cant find it ..... a most basic thing ,,,, 3 days and cant do it 
cant find nm-applet
when i first boot it up it says ... wifi is available in the network manager ,,, cant find that 
i find network connections in preferences .. but that just tell me about Ethernet ... 
then i look for help files online ...and I find ... open this ,, and type ...sudo apt-get
then log off then log on ... then type instal 
then iconfig this and that ...then more typing ... and instal more stuff ..REALLY !!
Im not a programmer .... i just want to connect to the internet and see if lubuntu is any good for me ...and then ... maybe  I could instal it in a hard drive ,..
I boot up with Try Lubuntu without installing ,,,
cos not yet ,,, if I mess up windows ..as bad as it is .. im doomed ////
so im thinking of a dual boot scenario until im more comfortable .... then ill let win float away into the void ...
but ...
I think to my self ....the internet is so important these days ... i cant belive a program would make it so akward and difficult to just find a network and log on ....
is the world of Lubuntu going to be like this ?
whats my next move ?

---

### Post by GhX6GZMB on 2020-06-11
First, I think you've been on the wrong Lubuntu download site. The correct one is [www.lubuntu.me](www.lubuntu.me)

Second, I have the feeling that your install is not complete. You'll need to copy the .iso image to a USB stick, or burn a DVD with the .iso image (I personally prefer this, as it gives audible feedback during install. Old fashioned, I know). Then boot from here.

Third: there's no "Try Lubuntu" in the current correct install image (there may be in older images). There's a "Start Lubuntu" which will bring you to a desktop after some minutes. From here you can play around a bit. The real install only happens when you click that item on the desktop.

I've had no pains with Lubuntu, my current laptop is 12 years old, born with Vista, and runs perfectly under Lubuntu.

---

### Post by poorguy on 2020-06-11
If you have a wired internet connection connect to it and then install the updates on your new install and restart the computer when finished.

Remove the wired connection and see if the wireless adapter finds your Wifi SSID and if it does than click to open it and enter your password.

In the **Menu** under** Preferences** look for** Additional Drivers** and open it and then go to **Additional Drivers** and open it and see if there is a driver offered for your wireless adapter.


Here's the official Lubuntu Manual.

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

---

### Post by TheFu on 2020-06-11
Canonical isn't Microsoft. 
Linux isn't MS-Windows.
There are very different philosophies between these 2 VERY DIFFERENT OSes.
There are very different prices too.

If you just want to get on the internet, then you want a chromebook, running ChromeOS.  They are designed to be easy enough for everyone to use, but there is an additional price beyond the hardware cost.  Your privacy.  Chromebooks **are** probably the most secure internet devices available today, but they are far from private.

There is good news. A few companies do make something called ChromiumOS which is the basis for ChromeOS.  Also, ChromiumOS runs on almost any 64-bit computer.  [https://www.neverware.com/](https://www.neverware.com/) is one option.  I don't know whether it can dual boot or not. I've never used it. I know 1 person who used it for college work that was google-docs-centric and she loved it.

As for driver problems - complain to the vendor who made the hardware. They are the people who fund making drivers for different OSes.  If they don't make a Linux driver, then it is up to volunteers who care to do it.  If no volunteer cares, then it doesn't get done.  Often, very popular hardware has excellent support under Linux.  It is when we stray into the niche hardware that things become more difficult.  Before spending any money on hardware, always, always, always, check that specific compatibility is built into the shipping Linux you will be using.  Don't get burned when a box says "Supports Linux!" on the outside.  I've been burned by that.  The "support" was for an 8 yr old kernel version that hadn't been used in about 6 yrs. I ended up with some hardware that worked in a minimal way, but not in the intended way to justify the price paid.  That was an expensive lesson.  It has happened a few times in my decades of Linux use.

Switching from an OS with 90% of the world's desktops to an OS with, say 3% of the world's desktops AND next to zero funding can take some getting used to.  The ecosystem is very different.  Canonical is trying to make their desktops as ready-for-grandma as possible.  But the Lubuntu team doesn't work for Canonical. They are people with a passion.  The release notes for 20.04 Lubuntu.  [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/)  They've made some huge, but necessary changes since 18.04. Some of their choices were brave and solved some issues that were definitely problems. Of course, they've also inherited some new problems due to the switch.

While almost everything can be accomplished using the point-n-click interface, it isn't the most efficient way to explain to someone else how to setup things.  Fortunately, we have the terminal (a program to type commands into), shell (the program that a terminal runs) and CLI (command line interface) to provide accurate, short, text answers.  BTW, nobody types most of those commands in. We use tab-completion so the computer fills in the correct answer after we type just a few characters.  If you are typing, it is worth the effort to seek out a youtube video for any Linux or Unix how-to that does command completion. It takes 30 seconds to learn, a week to remember to use, and a lifetime to master.  The shell is what provides command completion. There are multiple shell programs - bash being the most popular and the default.

Where to find the nm-applet?  There is probably a small icon in the upper right corner of your Lubuntu desktop that looks like 3 curved lines or some sort of network connection. Left click on that with the mouse. THAT is the nm-applet.  "applet" means something that runs on your desktop to provide feedback and quick access to some settings. I love the alarm-clock-applet - it provides alarms and multiple timers so time doesn't slip away while I'm working or playing.

Anyways, don't feel bad if you try a Linux for a week or two and just don't like it.  Linux is all about choice. There are probably 50 different GUIs that you can choose, see what you like and what works with your hardware.  Some are heavy. Some are lighter and some are so light they'd work extremely fast on hardware from 2000.  TinyCore is in the extremely Lite group. It needs only 64MB of RAM to run with a nice GUI.  Lubuntu probably needs 2G to run fast, but will run in about 750MB of RAM.

So you have plenty of options to try.  The only thing wasted is time.

---

### Post by Skaperen on 2020-06-11
the simple summarized answer is that too many people want to monetize all aspects of computers.

their efforts include trying to demonetize it for others in the hope this means more for themselves.  this is why we have so many licensing and patent issues with various software and hardware.

---

### Post by GhX6GZMB on 2020-06-11
BTW, my newest laptop is three years old, a Dell running Win 10. I have this to be able to work in both worlds, but much prefer my 12 years old Lubuntu laptop (20.04).
Anyhow, as Win 10 cannot be downloaded or installed, the recommendation from Dell was to make a system backup first.

It took over 6 hours to generate the system backup USB stick!!!

A complete Lubuntu install takes around 30 minutes on my ancient hardware.

How's that for progress?

---

### Post by grahammechanical on 2020-06-11
I think I am correct in saying that when we run a live session (Try, not install) we are running an OS using free and open source software only. This applies to hardware drivers as well as other software. It is great if the Linux firmware package includes drivers for our hardware. Not great when it does not.

When we install Lubuntu/Ubuntu we can tick a box to install non-free software. That will/should install any proprietary drivers that are needed. As well as audio & video codecs We can install drivers in a live session as outlined in an earlier post. They will last only for that session.

I think that I am correct about this.

Regards

---

### Post by wildmanne39 on 2020-06-11
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

If you want help please start a thread in the networking forum with a descriptive title and post the results of the wireless script in my signature.

This old of a laptop is very likely to have a broadcom device and it probably needs the b43 firmware and the reason it is not installed by default is because of legal reasons that do not allow ubuntu  to add it at the time of install.

---

### Post by Impavidus on 2020-06-12
If you use a fairly old computer with Windows XP, I find it a bit hard to believe that it has loads of memory (as in RAM). Web browsers need quite a lot of memory. A few more details on your hardware may help. Maybe the recycling centre is the best place to send it. Yes, it will probably work fine as a server, but if you don't need a server, that's irrelevant.

Then there's the matter of 32 bit versus 64 bit. I'm not sure about Windows, but on Linux Google doesn't support anything 32 bit any more. And Lubuntu 18.04 is the last Lubuntu release to support 32 bit.

Which release of Lubuntu have you tried? Best option to try now is 20.04, although 18.04 still has 10 months of support left.

I understand you try to use a USB wifi device. Most of those work out of the box, but maybe it helps if you tell us the exact model.

On the bright side, dual booting Lubuntu (or any other Ubuntu) with Windows XP is fairly easy. Simpler than with Windows 8 and later.

---

### Post by imsoslow on 2020-06-12
This is a lot of stuff ... which is good as it means Lubuntuists care 
and especially since my post was so negative and whiney ...so let me wade through this , 
as you all deserve aknowledgement at least for taking the time out to type a reply.


ml9104
Im not sure about the wrong download site , but i have no problems re-downloading for yuor link.
I did copy everything onto a USB stick of 16Gb as per a tutorial i read . also onto that stick goes the program  
UNEBOOTIN windows ,, for booting it up from the stick 
and in fairness .. it boots up no problem .., I press F12 on the satrt then choose to boot from the USB port
and it does ... that all seems fine.
Lubuntu is 18,4 Bionic beaver .. it SEEMS correct , but what do I know 
the bluebird apears ,,, some dots ,,, and then the desktop ... 
all fine up to there ...
connectint to internet is the problem as mentioned


POORGUY 
No ... there is no wired internet ,,, there is WiFi  and I also have a wifi booster plugged in upstairs ,,boosts and cures any blind spots in rooms .I will check out the Additional Drivers bit ... as now im typing on Win xp on this desktop but i made a note of it 
Ill et back to you on that one ... and thank you for the manual.


The FU
I do understand that they are different OS's and thats why im here to try to start a different one.
I do not want a chromebook, thanks for the link , but its a bit too tied into chrome for me .. windows is bad enough 
I know that is clearly less popular then what Mr Gates offers , however ... at the moment i want to use it ,, i just cant get the online bit done ,
to be clear ,, that is the question of the post.
the learnig bit will happen as time oes on andi become slowly enlightened.
So... I have read on help files ... nmapplet in the top right hand corner .. but i have nothing up there ...zilch.
and I am trying it ... its not a waste of time .. i have a big learnig curve ahead of me .. but going from win to lubuntu so i can get info online is a pain .. so this is my first hurdle .. or challenge if you like..
Thank you for you advice.




Skaperen
erm yes .. your may well be correct ... ill look out for that when im online. 
thanks


mL9104 again ..
im pleased to hear that your 12 year old computer is running fine on Lubuntu .. one day i hope to tell you the same thing.


 Grahamechanical
Unfortunatley you are too far ahead of me .. although i do use the Try not instal option ...
I have no problem putting it onto the spare hard drive if this would help




wildemann39 
**** ... now the Moderator is onto me ,,, ill get detention soon 
sorry im on the wrong thread .. feel free to move it , or whatever you think best ..
thread in networking forum .. got it 
sorry .. ill reply here first .. it seems rude not too 
BTW.. its a desktop nop laptop ... if that makes any difference.,, wifi through USB dongle 802.11 b/g/n




Lmpavidus


yes i can get some details , it has a fair ammount of memory ... hard drives and enough RAM because it been geting updated over the years ... its now maxed out i think ....however the original computer card is still the old one.
OK tyring to make compatability out of things I dont understand is how i ended up with 18.4 bionic beaver .. Dell Optiplex in X86 .. which is 32 bit 
I could try 20.04 if you thought it would help ... and keep the USB of 18.4 in case flames and smoke come out of the back ...
 as mentioned i downloaded 18.04 from a site as i felt it was the most compatible .. and downloaded UNEBOOtin as well , pput them onto a spare USB stick I had ,,, that bit was honestly easy .. i was so pleased when it came on first time no problem .. now the internet thing .
I did get it from lubuntume site but it says 20.o4 is for 64 bit and the 32 bit version is the 18 .04 that i have ... i just checked , thats why i have it ...








OK ...so quite a lot of info there na d quite a lot of replies .. not as much ... how to get online as i may need but I never give up .. so ill keep on keeping on

---

### Post by GhX6GZMB on 2020-06-12
Dell Optiplex can be a lot of things. Could you provide a precise model, please?

Also, you don't need "UNETBOOTIN" (whatever that is). Just put the .iso file on a USB or DVD and boot from there. The only thing you have to do is to make your boot device first option in the BIOS.

---

### Post by Impavidus on 2020-06-13
> **ml9104 said:**
> 
Also, you don't need "UNETBOOTIN" (whatever that is). Just put the .iso file on a USB or DVD and boot from there. The only thing you have to do is to make your boot device first option in the BIOS.
You can't simply copy the .iso file to the usb drive in the same way you can copy a .jpeg image there. You have to burn it somehow, replacing the original filesystem that was on that usb drive, and on Windows that means using a tool like unetbootin or rufus. Some people just unpack the .iso as an archive and put all contents on the usb drive, but that will only be uefi bootable and I think OP's computer is too old for that.

As you can run a live session, we can help you find more information about your hardware. I suggest you follow wildmanne39's suggestion and open a new thread in the networking forum (if you haven't already done so; I haven't checked) and post the results from his wireless script.

The following command will tell how much memory your computer has available, in megabytes. With 2GB it should be comfortable if you don't open too many webpages simultaneously, 1GB may just work.```
free -m
```

The following command will list many details about your processor, including whether it has the capabilities for a modern web browser and whether it's capable of 64 bit. Many computers sold with Windows XP were 64 bit capable, but only had a 32 bit Windows, which leads to people falsely believing they need a 32 bit OS. If you really need a 32 bit OS, you have to use Lubuntu 18.04 for the next 10 months at most, then you'll have to move out of the Ubuntu family. If you're really tight on RAM, a 32 bit system is better as it can do a bit more with the same amount of RAM.```
cat /proc/cpuinfo
```

If you want to dual boot Windows and Lubuntu, you'll have to partition your hard drive accordingly. With multiple hard drives, it's best to do so manually. The following command will list the hard drives in your computer and how they are currently partitioned.```
sudo parted -l
```

If you need any help with these steps, show us the output of those commands.

---

### Post by SeijiSensei on 2020-06-13
> **ml9104 said:**
> Anyhow, as Win 10 cannot be downloaded or installed, the recommendation from Dell was to make a system backup first.
That's not true. You can download an installation image for Win 10 from here: [https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)  It includes installers for Win 10 Home, Win 10 Pro, and Win 10 N (for European users).

You will need a valid Product Key to activate it, but from experience, you can run without activation for a very long time. Unactivated Win 10 won't let you customize your desktop and occasionally pops up a graphic in the lower right-corner of the screen saying this version is not activated.  I've installed Win 10 from this medium on a couple of machines including VirtualBox virtual machines.

---

### Post by jw-middleton on 2020-06-13
> **imsoslow said:**
> Help ....
Why is it soooo hard to do something so simple ???/
Let me explain, I have a Dell desktop ...

I'm pretty slow as well, but at 74 that is kind of expected. I recently bought a Dell Optiplex 7010 MT from walmart for $133 + tax, they shipped me a 7020 with an i5-4590 CPU, so I didn't complain. I wanted it to play with. It only had 4GB of DDR3 RAM and a 500 MB HDD. With spare parts I doubled the RAM and replaced the HDD with a 2TB one. The integrated video allowed me to enter the BIOS and set the boot priority to DVD drive. So, all was well.

 I burned a DVD with Ubuntu 20.04 LTS on my Win10 system. I had a Netgear USB WiFi adapter that I used for the installation. The process worked flawlessly. 

I have been so impressed with Ubuntu! I popped in a GPU and the latest drivers were automatically loaded. I attached my Samsung printer and it worked fine. But, some stuff can be a PAIN! I wanted to do some folding (Folding@Home) with my new GPU. I had to do manual install, for which I can follow instructions. F@H worked on my CPU, not my GPU. I spent hours trying to get FAHControl to install so I could reconfigure my setup, only to find errors in the loader based on obsolete dependencies. It was frustrating and some stuff might be more trouble than it is worth, but overall it is a great experience.

Good luck with it!

John

---

### Post by GhX6GZMB on 2020-06-13
> **Impavidus said:**
> You can't simply copy the .iso file to the usb drive in the same way you can copy a .jpeg image there. .

Yes, well, that's why I used the term "put", not "copy".

My assumption was that people know how to handle .iso files. Silly of me, perhaps.

---

### Post by GhX6GZMB on 2020-06-13
...

---

### Post by CelticWarrior on 2020-06-13
> **ml9104 said:**
> What you **cannot** download is an image tailored for my Dell machine. And this is unfortunately needed in the M$ ecosystem.

Last time I checked Dell never released special media. You should be able to use the Windows media everybody uses and then install all the Dell drivers and software in the recommended order to achieve the same result. Of course, using a system backup or recovery system avoids the hassle of installing drivers and everything else. That said, there's no problem in using the regular installation media for Windows 8 and newer - it activates normally - and when Dell still provided physical media for the PCs that was standard versions of Windows XP/7 and older Windows versions.

---

### Post by GhX6GZMB on 2020-06-13
We're off topic.
OP, which Dell Optiplex do you have, please?

---

### Post by CelticWarrior on 2020-06-13
> **ml9104 said:**
> We're off topic.
OP, which Dell Optiplex do you have, please?

Indeed we are and sadly since many posts ago. This is often the result of users not explaining themselves properly and posts that are walls of text from where extracting vasluable information is very hard. Such is the case here with a story that doesn't matter to anything but to understand the OP doesn't care about their personal safety online and even less about others. It's very sad that what prompted the OP to think about not using an obsolete OS wasn't any concern for the aspects that matter but because > many sites don't work well now.

And previous rant notwithstanding, what is really the problem here with Lubuntu? The story told with too much tangents and irrelevant comments **suggests only an issue with WiFi**, not any problem booting the Lubuntu live session. And what problem specifically? Likely NONE! Why? >  when i first boot it up it says ... wifi is available in the network manager ,,, cant find that  tells us 
[LIST=1]
[*]the WiFi is recognized (supported) already
[*]It found WiFi networks
[*]**The user doesn't know where to select their network!!**
[/LIST]
**@imsoslow - the network manager, in Lubuntu, is at the BOTTOM right just like in Windows:** [https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html)
Left-click or right-click I don't know, I don't use Lubuntu, but one of them will open the list of available networks. Select yours and type in the password when required, just like in Windows.

I the above doesn't work for you then please describe the actual problem keeping in mind **assertiveness is key.**

---

### Post by GhX6GZMB on 2020-06-13
I'd still like to know which Dell Optiplex the OP has, as this is important for choosing the OS version. OP says X86, but this can be anything and says nothing about 32- or 64-bit architecture.
For 32-bit, Lubuntu 18.10 is the last. I've used this, and it's stable and works extremely well with LXQt as desktop environment. I recommend this over 18.04 LTS, as LXDE is going EOL.
For 64-bit, Lubuntu 20.04 LTS of course. I have this on my machine right now and it runs beautifully.

After a full install, you'll find the networking icon bottom right as CelticWarrior says. It looks like an Ethernet receptacle. Left-click: active connection; right-click: connection settings.

---

### Post by CelticWarrior on 2020-06-13
> **ml9104 said:**
> I'd still like to know which Dell Optiplex the OP has, as this is important for choosing the OS version. 

#metoo ):P

> OP says X86, but this can be anything and says nothing about 32- or 64-bit architecture.
For 32-bit, Lubuntu 18.10 is the last. I've used this, and it's stable  and works extremely well with LXQt as desktop environment. I recommend  this over 18.04 LTS, as LXDE is going EOL.
For 64-bit, Lubuntu 20.04 LTS of course. I have this on my machine right now and it runs beautifully.

Indeed, it can be anything... But probably 64-bit, hopefully 64-bit, because even if with RAM maxed out, it may not be enough for a comfortable experience in today's internet if it really is an old 32-bit Optiplex. That being the case not even Lubuntu is recommended. I would instead recommend Debian 32-bit.

Yes, Lubuntu 18.10 was probably the last release with 32-bit but it shouldn't be used because EoL.
Yes, I agree LXQt is overall better than the rapidly aging LXDE but unlike the previous situation, Ubuntu 18.04 still has support until April 2021.

So, again, hopefully it's 64-bit. 32-bit machines will very soon make their way into retrocomputing.

---

### Post by robhill19652 on 2020-06-13
[https://support.microsoft.com/en-us/help/15088/windows-10-create-installation-media](https://support.microsoft.com/en-us/help/15088/windows-10-create-installation-media)

---

### Post by robhill19652 on 2020-06-13
I've had problems with wifi and Linux for years. Sometimes it won't connect to anything, and sometimes it connect for awhile, drops off, I have to disconnect and reconnect etc. I feel your pain.
 I finally found two options.

Get a usb wifi dongle that is ready for Linux out of the box. This one below needed no installing. I had to install the driver on my Windows 7 partition, so it's easier for a change with Linux.

[https://www.amazon.com/Adapter-1200Mbps-Wireless-802-11ac-10-6-10-15/dp/B081V8TDMF/ref=sr_1_9?dchild=1&keywords=usb+wifi+for+linux&qid=1592104334&s=electronics&sr=1-9](https://www.amazon.com/Adapter-1200Mbps-Wireless-802-11ac-10-6-10-15/dp/B081V8TDMF/ref=sr_1_9?dchild=1&keywords=usb+wifi+for+linux&qid=1592104334&s=electronics&sr=1-9)

Another option, which I did til I found that usb dongle, is to get a wifi extender that has ethernet ports built in. You can pick up your wifi with THAT. It will rebroadcast wifi AND you have a port to plug in, completely bypassing the wifi problems with linux.

As someone stated before, you may want to consider moving to 64 bit if you're not there already. I would also recommend the LTR version and no higher than 19.04. 20.04 is still buggy. On an older pc, Lubuntu is ok. Xubuntu is even easier to run but I didn't like the windows manager. Both Ubuntu and Kubuntu are a bit heavy for a 12 year old pc.

Again, I feel your pain. I'm still struggling with Linux and I've been using it dual boot for about 10 years now. Until you learn the file structure, and terminal, you'll be stuck, (as I am), trusting the info you find online. I'll give you a big hint though...., search on multiple sites for your answer before you commit to the terminal. I've screwed up installation quite a few times plowing ahead with bad advice on what to put into the terminal, because they didn't tell me how to reverse it.

---

### Post by DieB on 2020-06-16
> **imsoslow said:**
> Help ....

Wifi ,,,,,,why..... is  the  WIFI ..., which is the simplest and most needed thing today,  soooo difficult to get going ...
I just cant get it ..
My computer logs onto the home wifi router with a USB stick in the front port ..
but Lubuntu cant find it ..... a most basic thing ,,,, 3 days and cant do it 
cant find nm-applet
when i first boot it up it says ... wifi is available in the network manager ,,, cant find that 


Okay as it appears you have trouble with your usb-wifi-dongle.

First:
To help us in helping you, it would be great if you could run following command in an terminal(Ctr+Alt+t) while your dongle is attached:
```
lsusb
```
now copy that line that identifies your dongle ( or if you don't know which one it is - copy the whole output)

Second:
With a little web search I found this: [https://askubuntu.com/questions/322861/how-to-connect-to-wireless-network-in-lubuntu](https://askubuntu.com/questions/322861/how-to-connect-to-wireless-network-in-lubuntu)
best you try the answer by MaFiA that starts with: "Though its been long and many years ..."
or have a look here: [https://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing](https://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing)

Good luck

---

### Post by mmoseeker on 2020-06-19
linux is not windows
There are very big difference between these 2 VERY DIFFERENT OSes.

---

### Post by poorguy on 2020-06-19
> **mmoseeker said:**
> linux is not windows
There are very big difference between these 2 VERY DIFFERENT OSes.

A good read.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

