---
title: "I am having problems removing the live session user account ubu10.04 USB+ persistence"
date: 2013-06-29
forum: Security
---

### Post by neilmaclennan on 2013-06-29
I have looked at other another thread on the matter but in that persons instance they wer able to successfully change it's password, I however have not been able to. I leave the field blank and enter a new password and I get an error that I need to enter the current password in order to make the change. I have managed to change the live session users account type to a regular desktop one because I created another admin account. I can see a potential security risk in having the live session user account present on a persistent USB drive especially. I cannot see the account using the GUI at all when I am logged into my admin account. So I cannot delete it from there. And as I have changed the live session user (refered to from now on as LSU) to a desktop user that doesn't have the ability to admin the system I figured that that would be good enough but I was able to switch back to an admin again while inside the LSU account. 

My goal is to delete the LSU account or failing that change the password so that the security flaw is not an issue anymore. I would normally just play around with the terminal trying this that and the other suggestion using an answer to a question that was sorta similar and likely break the USBs ability to function properly then reinstall however I want to not do that this time if at all possible because it takes so dang long to create the persistence partition on the USB key that it's why I don't normally create them. This USB key is for a friend's kid whose HDD has failed and until I can find another one to replace it with (he can't afford much so it has to be a used one).

I am thinking that the best most efficient way to work around this problem would be to use the other account and start breaking things relating only to the LSU's account so that it generates an error that prevents the ability for that account to function properly, however I am a little skittish in attempting to start sudo chopping that account and end up having to start from scratch. I know enough commandline to mess the whole system up as I try to apply previous knowledge of one thing and apply it to another & that doesn't always work out. The last serious screw up I deleted the entire usr\bin folder when I forgot to add the foldername I wanted to delete during a manual uninstall of sublime text 2. Anyway I have rambled on enough sorry about the detritus but not enough to remove it apparently. Thanks for any help :eek:

---

### Post by neilmaclennan on 2013-06-29
I used an ubu10.04 LTS 64bit live DVD to create the 4GB USB start-up disk and used the other 3GB if free space to create a persistence layer.

I have looked at other another thread on the matter but in that persons instance they were able to successfully change it's password, I however have not been able to. I leave the field blank and enter a new password and I get an error that I need to enter the current password in order to make the change. I have managed to change the live session users account type to a regular desktop one because I created another admin account. I can see a potential security risk in having the live session user account present on a persistent USB drive especially. I cannot see the account using the GUI at all when I am logged into my admin account. So I cannot delete it from there. And as I have changed the live session user (referred to from now on as LSU) to a desktop user that doesn't have the ability to admin the system I figured that that would be good enough but I was able to switch back to an admin again while inside the LSU account. 

My goal is to delete the LSU account or failing that change the password so that the security flaw is not an issue anymore. I would normally just play around with the terminal trying this that and the other suggestion using an answer to a question that was sorta similar and likely break the USBs ability to function properly then reinstall however I want to not do that this time if at all possible because it takes so dang long to create the persistence partition on the USB key that it's why I don't normally create them. This USB key is for a friend's kid whose HDD has failed and until I can find another one to replace it with (he can't afford much so it has to be a used one).

I am thinking that the best most efficient way to work around this problem would be to use the other account and start breaking things relating only to the LSU's account so that it generates an error that prevents the ability for that account to function properly, however I am a little skittish in attempting to start sudo chopping that account and end up having to start from scratch. I know enough commandline to mess the whole system up as I try to apply previous knowledge of one thing and apply it to another & that doesn't always work out. The last serious screw up I deleted the entire usr\bin folder when I forgot to add the foldername I wanted to delete during a manual uninstall of sublime text 2. Anyway I have rambled on enough sorry about the detritus but not enough to remove it apparently. Thanks for any help :eek:

---

### Post by lisati on 2013-06-29
Duplicate of [http://ubuntuforums.org/showthread.php?t=2158452](http://ubuntuforums.org/showthread.php?t=2158452) closed.

Please do not start multiple threads for the same question, it dilutes the community's ability to help.

---

### Post by Cheesemill on 2013-06-29
If you are worried about security then don't use 10.04. The desktop version reached end-of-life in April and as such doesn't receive bug fixes or security updates any more.

---

### Post by neilmaclennan on 2013-06-29
ok. But I would still like to know how to remove the live user account anyway unless it's not an issue with 12 or 13 anymore. I did create a regular install to usb. One of the main reasons that I like 10.04 is the launcher. Unity would be great if it didn't have the screwy file menus for the active window on the taskbar. I don't know how many times I either searched for a setting for one app but because another was selected etc... Now I look each time when I have more than one window open and yes I could use separate desktops but all these things amount to wasted time remembering keyboard shortcuts or navigating around manually between the lot. It certainly makes it harder for Ubuntu to bring people over from the darkside (windows) when even silly (but easily changeable) things like the location if the min max close buttons messes with people. It's like wearing gogles that make everything look upside down, it's hard to pour a glass of water properly. But that is something else. And I understand that Linux has certain physical traits too but it didn't have to get worse.

---

