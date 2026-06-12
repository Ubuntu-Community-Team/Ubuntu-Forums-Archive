---
title: "starling on a ball and chain"
date: 2010-01-17
forum: System76 Support
---

### Post by nealaustin on 2010-01-17
My new Starling came on Friday and I was very pleased. It was running the Jackalope As a final touch I updated through the update manager and now no wireless. I figured time for the Koala and upgraded, in the wired connection downloaded the 2.4.4 Drivers and the installation hangs up on installing drivers. Killed the process and rebooted, still no Wireless. Looking at the sticky thread there is in .ect/modeprob.d a file named RTL8187 and the text in it it says Blacklist RTL8187. I tried to corrupt this text with an extra "X" and to delete it all together but I do not have permission. I'm not good at the command prompt can anyone help?

---

### Post by lev-unr on 2010-01-17
If you dont have permission did you access the file using "sudo gedit"

---

### Post by nealaustin on 2010-01-17
Gee I didn't know that sudo was THAT powerful. I changed the text in the file to Xlacklist RTL81X87 (former Blacklist RTL8187) but to no avail the driver still doesn't install

---

### Post by lev-unr on 2010-01-17
I know how frustrating this can be. Hold on. :) I will try to help you. 

and for future reference SUDO is very powerful, and essentally stands for Super User. giveing you all the permission in the world. :D

---

### Post by lev-unr on 2010-01-17
> **nealaustin said:**
> Gee I didn't know that sudo was THAT powerful. I changed the text in the file to Xlacklist RTL81X87 (former Blacklist RTL8187) but to no avail the driver still doesn't install

did you write xlacklist or blacklist?

---

### Post by nealaustin on 2010-01-17
I also tried just commenting it with # before but that doesn't seem to work either

---

### Post by nealaustin on 2010-01-17
> **lev-unr said:**
> did you write xlacklist or blacklist?

yes I wrote Xlacklist

---

### Post by nealaustin on 2010-01-17
Right now that RTL8187.conf File has as a text 
# Blacklist RTL8187
and the 76 driver is still in eternal-install
Maybe that wasn't the problem?

---

### Post by lev-unr on 2010-01-17
Just read the sticky - did you update ALL systems before installing the 2.4.4 Drivers?

I am trying to go back to basics. Often times the most frustrating problems have the easiest fixes. :)

I am used to working with crappy computers - system76 is supposed to be designed to work with linux. therefore I am surprised you are having these issues. 

after the last couple of years I have become a resident expert on broadcom installation. i have however installed the RTL8187 on a couple other machines. it took a while for everything to square away but we will get it done ! Dont worry.

---

### Post by nealaustin on 2010-01-17
I left that file as is with the comment and went back into the 76 driver installer and clicked into the factory settings and did system Restore but now it seems that I am in Eternal-Restore

---

### Post by nealaustin on 2010-01-17
I think so ,yes 
I Just stopped the eternal-restore.

---

### Post by lev-unr on 2010-01-17
Going back to your original post- you said it hung up on the installation of the 2.4.4 drivers. Did you ever finish the install?

---

### Post by nealaustin on 2010-01-17
> **lev-unr said:**
> going back to your original post- you said it hung up on the installation of the 2.4.4 drivers. Did you ever finish the install?

no

---

### Post by nealaustin on 2010-01-17
What happens is tha a pop-up box says installing drivers with a waving bar that will go on for hours. I have always forced Quit after about 1 hour. same the restore which I killed after 15 minutes

---

### Post by lev-unr on 2010-01-17
THAT might be the issue. 

Ok I know this is going to be a pain in the ***, and if anyone has a better idea. PLEASE post it here.

But download 9.10 to a USB flash drive and reinstall it. 

then go though the steps on the sticky and install the wireless.

---

### Post by nealaustin on 2010-01-17
> **lev-unr said:**
> THAT might be the issue. 

Ok I know this is going to be a pain in the ***, and if anyone has a better idea. PLEASE post it here.

But download 9.10 to a USB flash drive and reinstall it. 

then go though the steps on the sticky and install the wireless.

It sounds good to me but Ill wait an hour or 2 to see if anyone has a better Idea. I'll start the download  and backup in the meantime
Thanks ( I was afraid this would happen )

---

### Post by lev-unr on 2010-01-17
Let me know if it works out. 

I have found that at times the easiest thing to do is just reinstall. When you upgrade, and try tofix issues you try so many things that you dont remember what you do and you cant figure out how to undo them. 

Good luck! 

Sorry that I could not be more help.

---

### Post by nealaustin on 2010-01-17
Say the Russian imaging software that unr links to is for windows. I'm running Linux how do I get it on the disk does the dvd/cd creator do that? Which one of the starlings usb drives is bootable

---

### Post by nealaustin on 2010-01-17
I seem to be too stupid to make the USB Disk any help?

---

### Post by nealaustin on 2010-01-17
I'm going to have to give this whole deal a great big giant WTF?
I was desperately trying to figure out how to make a usb image and which of the usb drives is bootable. So I ran the system test and the !@#$%& thing turned the network on. I rebooted and it's all rainbows, chocolate and unicorns. I'm still to "stoopid" to make that usb drive.

Thanks for all your help though.

---

### Post by lev-unr on 2010-01-17
Sorry I'm at work now but I can't believe that randomly fixed it. Haha. Linux does magical things sometimes. Or completely ridiculous things. 

I am not sure what your next question was. U want to make a bootable disk? There is a program that I used called unetbootin .sourceforge.net  that threw the 9.10 iso on a flash drive would that work?

---

### Post by nealaustin on 2010-01-17
One thing that I noticed is that the software package never showed 3rd party software but instead other. The planet76 repository choice never showed up until I chose restore. I'm wondering if that installing bar has a bug that just kept it from closing. Anyway I found the USB creator under System Administrator. This little Starling is changing my behavior at the keyboard. I used to be a 3 window maniac and the UNR is forcing me to use shortcuts that I never saw before. You are right LEV it (UNR) is magic.

---

### Post by thomasaaron on 2010-01-18
>  The planet76 repository choice never showed up until I chose restore.

Part of the "Restore" functionality of the driver is installing our repositories in your software sources list.

 > I'm wondering if that installing bar has a bug that just kept it from closing. 

I'm not *exactly* sure what you're talking about there, but if you upgraded from 9.04 to 9.10, there is a grub issue that causes the driver's "Install" functionality to hang. To fix that, you need to open a terminal and run...

sudo apt-get install grub-pc

...and choose all default selections when prompted.

---

### Post by Teasdale on 2010-01-18
> **nealaustin said:**
> I seem to be too stupid to make the USB Disk

As I remember, when I installed EEEbuntu to my EEEPC, getting the OS onto the USB and getting it to work as a bootable disk was the most complicating part of the whole process.

---

### Post by thomasaaron on 2010-01-18
> As I remember, when I installed EEEbuntu to my EEEPC, getting the OS onto the USB and getting it to work as a bootable disk was the most complicating part of the whole process.

That has changed with 9.10.

In 9.04, you had to deal with the .img file. In 9.04, it's just an .iso. Just download it and use USB Startup Disk Creator to make the disk.

---

### Post by nealaustin on 2010-01-21
> **thomasaaron said:**
> Part of the "Restore" functionality of the driver is installing our repositories in your software sources list.

  

I'm not *exactly* sure what you're talking about there, but if you upgraded from 9.04 to 9.10, there is a grub issue that causes the driver's "Install" functionality to hang. To fix that, you need to open a terminal and run...

sudo apt-get install grub-pc

...and choose all default selections when prompted.

Yep, ran it and all is well. Thanks again Thomas. My Starling now purrs like a kitten. It now has replaced my desktop computer completely. I will be buying a System 76 next time around (for my wife) !

---

### Post by nealaustin on 2010-02-07
I got involved with the update while System 76 was down. The only way I could get the wireless to work was to once again comment the ect/modeprobe.d/rtl8187.conf. (#blacklist rtl8187). I did the "apt-get install grub-pc" several times. I did the system76 restore several times. I did the install 76drivers several times. I did all three processes in different sequences with and without rebooting. I also did all of those things with and without the rtl8187 commented. I have done every thing I could think of except offer a chicken to the gods of Ubuntu. I do have wireless but nowhere near as good as during the magical days between the Upgrade and that 76-less update. Any help?

---

### Post by thomasaaron on 2010-02-08
Now that our website is back up, you can uncomment the...

#blacklist rtl8187

...and give it another try.

---

### Post by macabrem on 2010-02-08
> **thomasaaron said:**
> Now that our website is back up, you can uncomment the...

#blacklist rtl8187

...and give it another try.

If you click on System 76 from a Google search, the link [http://system76.com/](http://system76.com/)

still gives a message that the site is down - although I know that if I just add a www to it then it comes up.  Just a FYI, Tom.

---

### Post by thomasaaron on 2010-02-08
OK, thanks. I'll report this one to our webmaster.

EDIT: I just tried that, and the site came up fine. I googled for System76, and then clicked the link Google provided. Is that what you're talking about?

---

### Post by nealaustin on 2010-02-08
Ok I uncommented did the sys76 install drivers -> rebooted -> still no wireless. ran the system restore after rebooting still no wireless. Actually I had to double boot to comment and uncomment again because I Used the wireless to get back on line.

---

### Post by macabrem on 2010-02-08
> **thomasaaron said:**
> OK, thanks. I'll report this one to our webmaster.

EDIT: I just tried that, and the site came up fine. I googled for System76, and then clicked the link Google provided. Is that what you're talking about?

Yes.  It is still coming up with the black screen that says "we are currently having issues with our datacenter..."  I'm not sure why it didn't happen on your end, but the top Google result, and clicking on [http://system76.com](http://system76.com) without the WWW still provide it.  

Using Firefox, cache cleared and all that good stuff.

Edit:  I just tried this with Internet Explorer and got the same result.

Edit:  This is probably too much info, but just so you know I'm not crazy, here is the html code for the page:

<html>
<head>
<title>System76 - site_update</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
<body bgcolor="#000000" leftmargin="0" topmargin="0" marginwidth="0" marginheight="0">
<div align="center"
<img src="[images/site_update.jpg]("http://ubuntuforums.org/view-source:http://system76.com/images/site_update.jpg")" width="650" height="300" alt="">
</div>
</body>
</html>

---

### Post by nealaustin on 2010-02-08
I just now with a wired connection uncommented the rtl file -> rebooted ->
ran system restore -> did the apt-get install grub pc. I did not remove the grub headers that it said were not needed 2.6.31-17 binutils-static and generic because i was not sure whether to do that. -> rebooted -> ran install sys76 drivers -> rebooted -> STILL NO WIRELESS. The planet76 repositories have a 2.4.5 version and I noticed that my version is 2.4.4.
On my side there is a sys76.com site and a planet76.com site

---

### Post by jbelmonte on 2010-02-08
> **macabrem said:**
> Yes.  It is still coming up with the black screen that says "we are currently having issues with our datacenter..."  I'm not sure why it didn't happen on your end, but the top Google result, and clicking on [http://system76.com](http://system76.com) without the WWW still provide it.  

Using Firefox, cache cleared and all that good stuff.

Edit:  I just tried this with Internet Explorer and got the same result.

Edit:  This is probably too much info, but just so you know I'm not crazy, here is the html code for the page:

<html>
<head>
<title>System76 - site_update</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
<body bgcolor="#000000" leftmargin="0" topmargin="0" marginwidth="0" marginheight="0">
<div align="center"
<img src="[images/site_update.jpg]("http://ubuntuforums.org/view-source:http://system76.com/images/site_update.jpg")" width="650" height="300" alt="">
</div>
</body>
</html>

If System76 moved servers and changed IP addresses, this could be a DNS issue. Your local DNS server may have retained the old System76 IP addresses rather than using the new ones that go to the live site. DNS changes take time to propagate depending on TTL of the record, but sometime a local DNS server does not retrieve fresh data when it is supposed to.  Alternatively, since you are on a Windows box, the local DNS Resolver cache could have the old information and won't look for new data for a day or two. You can clear that cache by opening a command prompt and running the following command: ipconfig /flushdns

---

### Post by macabrem on 2010-02-08
> **jbelmonte said:**
> If System76 moved servers and changed IP addresses, this could be a DNS issue. Your local DNS server may have retained the old System76 IP addresses rather than using the new ones that go to the live site. DNS changes take time to propagate depending on TTL of the record, but sometime a local DNS server does not retrieve fresh data when it is supposed to.  Alternatively, since you are on a Windows box, the local DNS Resolver cache could have the old information and won't look for new data for a day or two. You can clear that cache by opening a command prompt and running the following command: ipconfig /flushdns

Thanks.  I was kinda wondering if it was on my end.  I was viewing on a Windows work computer and we have all kinds of firewalls and other junk that I don't know about.  But, yeah, at home on my Mac the site looks fine (I'm sure it will look fine on my Starling too).  

I just wanted to ensure System 76 had all of their stuff in order - I thought it was strange I was getting that window after the site was already back up.

---

