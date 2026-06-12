---
title: "How to dual boot 8.10/9.04 on panp4n"
date: 2009-05-07
forum: System76 Support
---

### Post by Eldera on 2009-05-07
This is low priority. An answer in the next week or two would do. I can always bump if the post gets lost.

Before I bought my Pangolin in February, I asked S76 support if it were possible to dual boot two versions of Ubuntu. TA replied
> We can provide instructions for doing so.

So, Tom, Jaunty is out and I am ready for those instructions.

I am guessing that those instructions would be this tutorial
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine) 
changed to use the Ubuntu CD instead of a Windows CD. 

I already have some questions.

Does the download from the Ubuntu home page from which I will make my Jaunty live CD use the same servers that have been overloaded by the Jaunty upgrades? (If yes, I can wait another week or two before doing my project.)

Do you use the md5sum check tool? The Ubuntu site mentions it, but Keir Thomas does not.

After following the prompts on the live CD for partitioning and installing, will I still have to do something with GRUB and MRB? Please be very specific because this is the part where I haven't been able to find any background.

After installing the material from the live CD, will I need to install the S76 driver?

Will I need to install the nVidia driver?

If yes, and yes, in which order? S76 and then nVidia or nVidia and then S76?

After I have I done this set-up will software installed or updated while running Intrepid go onto the same partition as the Intrepid OS by default and software installed or updated while running Jaunty go onto the same partition as the Jaunty OS by default? 

If not by default, can this be set up? This would be my personal preference since if I get an app running well in Intrepid for a particular desk top publishing job, I might not want to update it.

Thank you again for all your help.

---

### Post by thomasaaron on 2009-05-07
> I am guessing that those instructions would be this tutorial
[http://knowledge76.com/index.php/Win...stem76_Machine](http://knowledge76.com/index.php/Win...stem76_Machine)
changed to use the Ubuntu CD instead of a Windows CD.

Right-o. Have you considered doing virtual machines instead of dual-booting? (I'm sure you have your reasons. I'm just curious.)

> I already have some questions.

Well, then, let's get down to business! Shall we? :popcorn:

> Does the download from the Ubuntu home page from which I will make my Jaunty live CD use the same servers that have been overloaded by the Jaunty upgrades? (If yes, I can wait another week or two before doing my project.)

Not really sure if they use different servers for different versions. Probably not. At any rate, I think traffic has settled down enough that you can download whenever you're ready.

> Do you use the md5sum check tool? The Ubuntu site mentions it, but Keir Thomas does not.

You know, I don't use it as much as I should, but it's a good idea to verify the accuracy of your download. A hosed image would just be a waste of your time.

> After following the prompts on the live CD for partitioning and installing, will I still have to do something with GRUB and MRB? Please be very specific because this is the part where I haven't been able to find any background.

If you dual boot with Ubuntu, Ubuntu will actually detect your *other* Ubuntu installation and set Grub up for you. So you won't have to worry about it. On the tutorial mentioned above, you *do* have to modify grub, because Windows will not do that *for* you. So, you can skip that part on the tutorial.

> After installing the material from the live CD, will I need to install the S76 driver?

> Indeed. You can follow these instructions...
To install the System76 Driver, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it.

Once installation is complete, go to System > Administration > System76 Driver > Restore (tab) > Restore (Button) to re-set your machine to factory standards (which may include some software downloads). If you only want to install drivers, select the 'Install' tab and the 'Install' button.   


> Will I need to install the nVidia driver?

When you finish your installation, you *should* be able to go straight to System > Administration > Hardware Drivers and enable the drivers. If the driver doesn't appear there, we'll have to take some additional steps, and I'll walk you through it.

> If yes, and yes, in which order? S76 and then nVidia or nVidia and then S76?

Dang! You've got some good questions! Here's the order...

[LIST=1]
[*]Install
[*]Run updates
[*]Reboot
[*]Run System76 Driver
[*]Enable nVidia
[*]Reboot
[/LIST]

If you mess that up, though, it's no big deal. That's the way I do it, though.

> After I have I done this set-up will software installed or updated while running Intrepid go onto the same partition as the Intrepid OS by default and software installed or updated while running Jaunty go onto the same partition as the Jaunty OS by default?

Yes. The two versions of Ubuntu will not be linked.

> If not by default, can this be set up? This would be my personal preference since if I get an app running well in Intrepid for a particular desk top publishing job, I might not want to update it.

I think you're good-to-go on that one.

Great questions. These definitely will be helpful to the community.

---

### Post by Eldera on 2009-05-07
Thank you. Instructions are clear and I'm good to go, probably this weekend.

[quote=TA]Have you considered doing virtual machines instead of dual-booting?[/quote]

I have studied dual booting much more intensely and virtual machines not at all. I am actually more comfortable with dual boot at this stage of the game.

[quote=TA](I'm sure you have your reasons. I'm just curious.)[/quote]

I'll answer that when I have more time to condense a long story into a short post.

Thanks again, Eldera

---

### Post by Eldera on 2009-05-20
WARNING: If you try this and are offered an option by the partitioner to install Intrepid and Jaunty side by side, DON'T do it. Use "Manual" partitioning. 

I was so messed up at one point I could only run the computer from the live CD. After a few emails to faithful TA, I did a clean install of Jaunty to get back in business.

After reading more about the partitioner, I installed dual boot using these instructions and manual partitioning. My problems were mistakes I was making with Gparted.

---

