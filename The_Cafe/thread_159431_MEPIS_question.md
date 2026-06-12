---
title: "MEPIS question"
date: 2006-04-12
forum: The Cafe
---

### Post by quadomatic on 2006-04-12
I heard about how MEPIS's base is now Ubuntu. I was wondering, does this mean that I would be able to use howtos or other guides that are here on the new MEPIS with no problems?

---

### Post by Robocoastie on 2006-04-12
dunno but I've been trying to figure out what the point of it is /boggle I mean its essentially ubuntu w/kde right? that equals Kubuntu doesn't it?

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=quadomatic]I heard about how MEPIS's base is now Ubuntu. I was wondering, does this mean that I would be able to use howtos or other guides that are here on the new MEPIS with no problems?[/QUOTE]
It uses KDE as a DE. It is not based on Ubuntu but it uses the Ubuntu repos. I doubt that you would be able to use all the guides. I think it is debian based so I think that you would be able to use some tutorials.

Edit: Yes, it appears that the alpha versions are based on Ubuntu.

---

### Post by quadomatic on 2006-04-12
[QUOTE=MasterChief1234]It uses KDE as a DE. It is not based on Ubuntu but it uses the Ubuntu repos. I doubt that you would be able to use all the guides. I think it is debian based so I think that you would be able to use some tutorials.

Edit: Yes, it appears that the alpha versions are based on Ubuntu.[/QUOTE]

yes, as i had said it is based on ubuntu.

Since it's based on Ubuntu, does that mean that guides on the forums and wiki (for kubuntu and guides made for both kubuntu and ubuntu), will work for MEPIS? I really like the community here and want to know I move to MEPIS whether or not I can stick with it.

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=quadomatic]yes, as i had said it is based on ubuntu.

Since it's based on Ubuntu, does that mean that guides on the forums and wiki (for kubuntu and guides made for both kubuntu and ubuntu), will work for MEPIS? I really like the community here and want to know I move to MEPIS whether or not I can stick with it.[/QUOTE]
I assume that it uses Grub so I am going to say yes. Most if not all guides will work.

---

### Post by mstlyevil on 2006-04-12
The kernel is the same kernel but there are some differences in the overall structure of the operating system. Some files are named different and located in different places. Simple how to's will work well but trying to adapt a more complex how to like XGL/Compiz for Kubuntu is a royal pain.

The answer to your question is it is hit and miss. It does not hurt to try out the how to's and see if they work or not.

---

### Post by purdy hate machine on 2006-04-13
I would not advise it, _Mepis is not Ubuntu. _
Ubuntu is based on Debian, do you use the Debian guides to set up your Ubuntu? I doubt it.
Use the right tool for the right job.

---

### Post by dermotti on 2006-04-13
Mepis also does not use sudo

---

### Post by Zerocool10482 on 2006-04-13
I'm thinking of trying Mepis but I'm just thinking. I know it's different but I still want to try it.

---

### Post by oblio on 2006-04-13
[QUOTE=mstlyevil]The kernel is the same kernel but there are some differences in the overall structure of the operating system. Some files are named different and located in different places. Simple how to's will work well but trying to adapt a more complex how to like XGL/Compiz for Kubuntu is a royal pain.

The answer to your question is it is hit and miss. It does not hurt to try out the how to's and see if they work or not.[/QUOTE]

The Mepis 6.0 alpha1 kernel has the same name, but it's not the same as the 2.6.15-20-386 (k)ubuntu kernel in Dapper. 

Mepis 6.0 alpha1               kernelsize = 1.851.376 kB
(K)ubuntu Dapper Flight 6 kernelsize = 1.413.740 kB

Mepis configs tend to be a bit different too.  The 'easy' howto's' will probably work as well.  Just don't bring in the 'sudo' thing..... "su" once will do...:-)  Mepis uses a user account + root account.

Regards,  Ko

---

### Post by oblio on 2006-04-13
[QUOTE=Zerocool10482]I'm thinking of trying Mepis but I'm just thinking. I know it's different but I still want to try it.[/QUOTE]

Give it a try.  You might like it.  It's faster than Dapper too - despite its bigger (modified) kernel.

Regards,  Ko

---

### Post by Blarion on 2006-04-13
Erm, I think you might want to post it in the mepis lover forum.

[SIZE=-1][COLOR=#008000]www.**mepislovers**.org/[/COLOR][/SIZE]

---

### Post by mstlyevil on 2006-04-13
[QUOTE=oblio]The Mepis 6.0 alpha1 kernel has the same name, but it's not the same as the 2.6.15-20-386 (k)ubuntu kernel in Dapper. 

Mepis 6.0 alpha1               kernelsize = 1.851.376 kB
(K)ubuntu Dapper Flight 6 kernelsize = 1.413.740 kB

Mepis configs tend to be a bit different too.  The 'easy' howto's' will probably work as well.  Just don't bring in the 'sudo' thing..... "su" once will do...:-)  Mepis uses a user account + root account.

Regards,  Ko[/QUOTE]

The Mepis kernel is a modified Dapper kernel. It comes from the Ubuntu Dapper repos and uses the exact same restricted modules for the Nvidia driver. I have been using Mepis 6 Alpha 1 for three days now and have managed to use several how to's from the Ubuntu forums successfully. I also successfull installed the Ubuntu Gnome Desktop and XGL/Compiz.

You are correct that some configs are different as I found out when installing XGL. Mepis 6 is not Ubuntu, that is for sure even if they share the same base kernel and use the same repo's as much as Mepis was not official Debian either when they used their kernel and repo's. The same thing goes for Ubuntu which uses modified debian packages and kernels.

Now if you want to argue that those modifications that Warren made to the Dapper kernel makes it a different kernel, then I can accept that. But the base of the kernel is the same base Kubuntu uses. But all that is just semantics. Mepis is Mepis and Ubuntu is Ubuntu because it is the entire build of the operating systems that make them completely different.

---

### Post by mstlyevil on 2006-04-13
[QUOTE=purdy hate machine]I would not advise it, _Mepis is not Ubuntu. _
Ubuntu is based on Debian, do you use the Debian guides to set up your Ubuntu? I doubt it.
Use the right tool for the right job.[/QUOTE]

Correct-Mepis is not Ubuntu. Use the guides made for the specific operating system. If one does not exist for Mepis and you have the skills, then it should be fairly easy to adapt Ubuntu guides for Mepis since both are debian based distros and use many of the same packages.

Just remember, you are taking a bigger risk of using a how-to from one distro and using it on another.

---

### Post by oblio on 2006-04-13
[QUOTE=mstlyevil]
But the base of the kernel is the same base Kubuntu uses. But all that is just semantics. Mepis is Mepis and Ubuntu is Ubuntu because it is the entire build of the operating systems that make them completely different.[/quote]

No, you're absolutely right.  
I should have stated in my earlier post that the base for the Mepis 6.0 alpha1 kernel is (K)Ubuntu kernel 2.6.15-20-386. 

Regards,  Ko

---

### Post by oblio on 2006-04-13
[QUOTE=mstlyevil]
But the base of the kernel is the same base Kubuntu uses. But all that is just semantics. Mepis is Mepis and Ubuntu is Ubuntu because it is the entire build of the operating systems that make them completely different.[/quote]

You're absolutely right.  
I should have stated in my earlier post that the base for the Mepis 6.0 alpha1 kernel is (K)Ubuntu kernel 2.6.15-20-386. 

Regards,  Ko

---

### Post by oblio on 2006-04-13
[QUOTE=Blarion]Erm, I think you might want to post it in the mepis lover forum.

[SIZE=-1][COLOR=#008000]www.**mepislovers**.org/[/COLOR][/SIZE][/QUOTE]

Sorry, I didn't mean to be offensive or provoking.  Just that one might be pleasantly surprised.  Once again, sorry.

Regards,  Ko

---

### Post by newbie2 on 2006-04-28
> MEPIS has announced the beta1 development release of SimplyMEPIS 6.0. The ISO image is available for download and testing in the mepis 'testing' subdirectory at the MEPIS Subscriber's Site and public mirrors.

Beta1 includes many package updates. For example, Warren Woodford, founder of MEPIS, says "Thanks to the hard work of Jonathan Riddell and the Kubuntu team, the latest Ubuntu Dapper updates to KDE and Cups greatly improve print support. Yea team!" Beta1 provides a 2.6.15.6 kernel based on Ubuntu kernel version 2.6.15-21.32. MEPIS kernels are source-identical with Ubuntu kernels but the configurations are tweaked to accommodate MEPIS specific requirements.

SimplyMEPIS strives to provide complete multimedia support out-of-the-box. Based on user feedback, xawtv has been replaced by tvtime. Browser plug-in links for Macromedia Flash and Sun Java have been repaired and improved. Media notification popups have been limited to pluggable media in an effort to improve cooporation between udev and kde. MEPIS packages have been tweaked to better handle updates and to enforce specific MEPIS configuration requirements.

Beta1 was synchronized with the Ubuntu Dapper pools around 7PM on April 26. The MEPIS pools have been updated to include the latest version of the transitional MEPIS OS Center and other MEPIS provided packages. Starting with Beta1, it is hoped that users will be able to maintain and update 6.0 incrementally from packages in the MEPIS and Dapper pools.

SimplyMEPIS 6.0 is a new concept in desktop Linux, combining the user enabling Magic of MEPIS with the solid engineering Goodness of Ubuntu.
Published Apr. 28, 2006 
[http://br.sys-con.com/read/213750.htm](http://br.sys-con.com/read/213750.htm)

---

### Post by aysiu on 2006-04-28
I don't think you'll be able to use the same guides.

I just downloaded the Mepis Beta last night and ran it through Qemu, and it appears to be the same old Mepis. Structurally (behind the scenes), it may be based off Ubuntu, but in terms of the user interface--it's Mepis all the way.

---

### Post by mstlyevil on 2006-04-28
The guides work well for the most part. You just have to remember to remove sudo and use su instead when applying the (k)ubuntu guides. The more I use it and apply the Ubuntu guides, the more similarities I find between the two than differences.

Beta 1 is very well done and IMHO is release quality like it is right now. Both Ubuntu and Mepis have done a great job in making the Dapper system extremely well polished and stable. Kudos to both of them.

---

