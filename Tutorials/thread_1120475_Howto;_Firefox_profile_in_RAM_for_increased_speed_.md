---
title: "Howto; Firefox profile in RAM for increased speed and stability"
date: 2009-04-09
forum: Tutorials
---

### Post by Bossieman on 2009-04-09
**NOTE**: This howto has been tested in Ubuntu 9.04 Jaunty Jackalope and Firefox version 3.0.8.

This howto is based on the discussion from a [[COLOR="Red"]forumthread[/COLOR]]("http://forums.gentoo.org/viewtopic-t-717117.html") over at the Gentoo Forums and this [[COLOR="Red"]guide[/COLOR]]("http://www.verot.net/firefox_tmpfs.htm") from verot.net
Credits goes to stevenrobertson at the Gentoo Forums for the original post

One of the problems that will disappear after completing this guide is based on the following

> Firefox uses SQLlite to store most of its information, which makes it quite slow. As SQLite accesses are IO-bound, Firefox suffers when the disk is heavily used by other processes.
[Source]("http://www.verot.net/firefox_tmpfs.htm")

The result of this guide will give you 

* Much less disk activity
* Immediate search results when you search in about:config and the AwsomeBar.
* None/Very few Firefox hangups/freezes.
* Faster rendering of webpages.
* Less power-consumption

For those of you who have slow SSD-harddrives and laptops with 5400 rpm harddrives will most likely benefit the most from this guide, the difference before and after will be huge.

You don't need a lot of RAM to benefit from this guide. Your Firefox profile don't need to be especially large if you reduce the amount of cache in your Firefoxprofile, I guess approximately 64 MB additional RAM is atleast required to benefit from this guide. 

To see how much difference this guide really do, I recommend that you start by doing the following easy tests. 
Open up a new tab and see how fast the new tab appears. Start typing some webpage you visit frequently into the address bar (AwsomeBar). Try to get an idea of how quickly the AwsomeBar works. Try also to enter **about:config** and get an idea of how quickly the results come up in your searches. After you completed this guide, do the same tests to see some of the differences in speed you will get from this howto.

So lets start this guide;

Type **about:config** into Firefox AwsomeBar and press Enter. Read the message that comes up and then click it to enter about:config

Type **browser.cache.disk.enable** into the filter field and verify that the value is **True**. If set to False doubleclick the result to change to True.  
Type **browser.cache.disk.capacity** into the filter field and doubleclick the result to change the value. If you want your Firefoxprofile to use only a small amount of RAM change the value to 20000 or below. If you have plenty of free RAM enter a big value, like 128000 or more. I have 4 GB of RAM so I use the value 131072 [128 Mb]
This value is just one part of your Firefoxprofile so the total amount of RAM the Firefoxprofile will use will be about 50 Mb more. Remember the value you enter, we need it later on.

The original author suggested to change the values for 

**browser.safebrowsing.enabled** to **False**

**browser.safebrowsing.malware.enabled** to **False**

I recommend you also to follow some guide on the internet that suggests good modifications for about:config for great improvement in speed. 

After this is done, go to your **.mozilla/firefox** folder and create a folder there and name it **profile**. The folder **.mozilla** is hidden so you have to press **Ctrl + h** in your homedirectory to see hidden files and folders.
Copy all of the content from the folder **xxxxxx.default**(xxxxxxx represents random letters and numbers) into the folder **profile**. If you are going to use a small amount of RAM for your Firefoxprofile then empty the folder **Cache** inside your **xxxxxx.default** folder before copying the content.
I recommend you to make another copy of xxxxx.default and place it somewhere safe just in case something happens. 
The folder profile will be used for saving the changes to your Firefoxprofile from RAM so the changes wont get lost after computer shut downs or a after a reboot. More on that later.

Create now in a place you remember an empty file (Right-click on eg the desktop and select **Create Document -> Empty file**). Give the file the name **tmpfs_firefox.sh** 
Doubleclick the file and paste the following text to it.

```
#!/bin/bash

# Change this to match your correct profile
PROFILE="xxxxxxxx.default"

cd "${HOME}/.mozilla/firefox"

if test -z "$(mount | grep -F "${HOME}/.mozilla/firefox/${PROFILE}" )"
then
    mount "${HOME}/.mozilla/firefox/${PROFILE}"
fi

if test -f "${PROFILE}/.unpacked"
then
    rsync -av --delete --exclude .unpacked ./"$PROFILE"/ ./profile/
else
    rsync -av ./profile/ ./"$PROFILE"/
    touch "${PROFILE}/.unpacked"
fi

exit
```

**[COLOR="Red"]Important[/COLOR]**: Modify the line **PROFILE="xxxxxxxx.default"** so it represent the [COLOR="Red"]exact[/COLOR] name of your xxxxxxxx.default directory.
My folder is named rcw72e7n.default so my line will look like this 

**PROFILE="rcw72e7n.default"**

When your are absolutely sure your file is correct save the file and exit your editor,
Rightclick the file **tmpfs_firefox.sh** and select **Properties**. Go to the tab **Permissions** and change the permissions so **Run** is marked to the right of **owner**. Close the window when you are finished.  

Now press **Alt + F2** and enter

**gksudo gedit /etc/fstab** 

and hit **Run**.

I the textdocument that appears put this line to the end of the file

```
firefox /home/USERNAME/.mozilla/firefox/xxxxxxx.default tmpfs size=AMOUNT_OF_RAM_TO_USE,noauto,user,exec,uid=1000,gid=1000 0 0
```

**[COLOR="Red"]Important:[/COLOR]** Change USERNAME to your own name. Change xxxxxxx.default so it represents the name of your xxxxxxx.default folder. Change AMOUNT_OF_RAM_TO_USE to a value about 70Mb larger than your **browser.cache.disk.enable** value. In other guides, where people have made similar modifications, it has been recommended **128M** if  browser.cache.disk.capacity is set to 20000. 
I used the value 131072 [128 Mb] for my browser.cache.disk.capacity so the line for me to put into /etc/fstab would look something similar like this

```
firefox /home/leif/.mozilla/firefox/rcw72e7n.default tmpfs size=200M,noauto,user,exec,uid=1000,gid=1000 0 0
```

When you are [COLOR="Red"]absolutely sure[/COLOR] your line is correct save the file and exit the editor.

We must now empty the content of your **.mozilla/firefox/xxxxxx.default** directory. To do this we have to shut down Firefox completely to avoid Firefox from re-create the profile. You can copy the relevant part of the guide to a text file or use another browser for the next part, but you have to exit Firefox before erasing the content.  Before you empty the folder, doublecheck that you have a copy of the content of **.mozilla/firefox/xxxxxx.default** in the directory **.mozilla/firefox/profile** and I recommend an extra copy somewhere safe.

When Firefox is closed erase the content of **.mozilla/firefox/xxxxxx.default**. Look down to the left corner in the Nautilus window and remember the amount of free space you have in your **.mozilla/firefox/xxxxxx.default** directory. 

When this is done locate the file **tmpfs_firefox.sh** we created earlier and doubleclick it. A window will appear. Chose **Run in terminal**. 
You will now see a terminal window open and close very quickly. This is normal and due to the fact that the whole process went very quickly. The script mounted your Firefox profile into your computer's RAM.  Double-click again on the file **tmpfs_firefox.sh** and select once more **Run in terminal**. The same thing happens as before but with the difference that the script synchronized the contents of the folder with your profile folder xxxxxx.default. 

Now enter the folder xxxxxx.default. You should now see that the erased files are back.
Look down to the left corner in the Nautilus window when you are in the folder xxxxxx.default and you should see that the value of free discspace now have changed and now shows the amount of free space in your computers RAM for the xxxxxx.default folder. If you see no difference try hitting refresh in nautilus.

If the content of xxxxxx.default is back and the amount of free discspace inside the xxxxxx.default directory have changed to a size around the same size you entered into your /etc/fstab file you can safetely start up Firefox.
After Firefox have started, repeat the same tests as we did at the beginning of the guide to confirm the difference in speed. Open up a new tab, this will be noticeably faster than before. Enter **about:config** into the awsomebar and press enter. Now the box to be careful should appear immediately. Press, I promise, I will be careful[ and you'll immediately arrive to about:config  
Perform a search in the filter box and you will see that the results will appear with no delays at all. Test also in the awsomebar to start typing a webpage you usually visit and note that the results from the search appears immediately. Another thing you will notice is that the your computer harddrive is working much less now than before. When Firefox have build up some cache, you'll also notice a difference in renderingspeed of the pages you visit. 

Now we have to make sure your computer synchronize the RAM to the hard disk so the changes in your Firefoxprofile is saved after you restart or shut down the the computer. To do this we need to install gnome-schedule. Click [[COLOR="Red"]here[/COLOR]]("apt:gnome-schedule") to install it. When the installation is complete, start the application, **Applications -> System Tools -> Scheduled tasks**. If you cant find the program enter **gnome-schedule** into the box that appears after you press **Alt + F2** and then hit **Run**.

When the program have started, click **New**, which is at the top left of the program. A window appears. Select the top option, **a task that is running recurring**. A new box appears. Enter the following

**Description:** Whatever you want

**Command:** $HOME/.tmpfs_firefox.sh

Mark the box that says **Advanced** and enter the following

**Minute:** */5

Enter a * into the four remaining fields,** Hour, Day, Month and Weekday**

You can change the number 5 to another value if that suits your better. The number represents the amount of time in minutes between each backupsynchronization from RAM to the folder **profile**.
After you are finished click **Apply** followed by **Ok**. Finally close Scheduled tasks.

Now locate once again the file **tmpfs_firefox.sh** and move it to your home directory. After this is done rightclick on the file and choose **Rename**. Put an . infront of the name so the name of the file becomes **.tmpfs_firefox.sh**. This will make the file hidden in your homedirectory. Press refresh in Nautilus and the renamed filed should vanish. Press **Ctrl + h** to show hidden files and directories and you can easily locate the file if you want to. 

Now go to System --> Settings --> Startup programs

Press **add** in the window that comes up. 
Enter the following:

Name: **Firefox RAM**
Command: **/home/USERNAME/.tmpfs_firefox.sh**
**[COLOR="Red"]Important:[/COLOR]** Change USERNAME to your own username

Click **Save** and then **Close** to complete the guide.
Now we just need to reboot the computer to make sure that everything works.
After reboot open up a terminal and enter the command **mount**. If you see a line that is similar to mine it works.

```
firefox on /home/leif/.mozilla/firefox/rcw72e7n.default type tmpfs (rw,nosuid,nodev,size=200M,uid=1000,gid=1000,user=leif)
```

---

### Post by Can0n on 2009-04-12
I've followed this guide and it works fine, except!
When I try to upload something (via a HTML-form) or try to download something (Right-click > Save as...) everything with FF dies completely and I have to kill it.
Any ideas ?
Is there some way I can check any errors? A debug-mode or whatever.

---

### Post by Bossieman on 2009-04-12
Can0n, I can do both uploads and download with no problems. I have done a lot of configs in about:config that is not mentioned in the guide. 
try setting

browser.cache.memory.enable --> True

and then 

browser.cache.memory.capacity --> 65536 

Just ad new Integer if browser.cache.memory.capacity doesn't exist.

Try also to ad (if you don't have it already) the string

browser.cache.disk.parent_directory

and put in the path to the directory

/home/[COLOR="Red"]USERNAME[/COLOR]/.mozilla/firefox/[COLOR="Red"]xxxxxxx[/COLOR].default

Hopes this solves it for you. What numbers did you use in the guide?

---

### Post by anthortic on 2009-04-28
thats an excellent guide which is perfect for my eeepc s101. one problem i came across was that the profile wasnt being loaded up after reboot. to get around this i had to add 
```
/home/anthony/.tmpfs_firefox.sh
```
into gnome-session-properties. now it works fine for me but i wondered what part of the guide i did wrong??? i checked through it 3 times but everything seemed covered. 

any thoughts?

---

### Post by Bossieman on 2009-04-28
> **anthortic said:**
> thats an excellent guide which is perfect for my eeepc s101. one problem i came across was that the profile wasnt being loaded up after reboot. to get around this i had to add 
```
/home/anthony/.tmpfs_firefox.sh
```
into gnome-session-properties. now it works fine for me but i wondered what part of the guide i did wrong??? i checked through it 3 times but everything seemed covered. 

any thoughts?


There is an error in the guide (fixed now).
Instead of 

```
firefox /home/USERNAME/.mozilla/firefox/xxxxxxx.default tmpfs size=AMOUNT_OF_RAM_TO_USE,noauto,user,exec,uid=1000,gid=1000 0 0
```

in fstab, it should be
```

firefox ~/.mozilla/firefox/xxxxxx.default tmpfs size=AMOUNT_OF_RAM_TO_USE,noauto,user,exec,uid=1000,gid=1000 0 0
```

This solves it.

[COLOR="Red"]EDIT[/COLOR]: Actually it doesnt solve it for me but I have modified the guide so it works now.

---

### Post by anthortic on 2009-04-29
thanks i made the changes and removed the .sh from the startup programs list

---

### Post by Onay on 2009-04-29
Thanks much! The speed is incredible... Ubuntu is great since it doesn't eat up memory like windows does so I can do this and still have tons of RAM.

---

### Post by Bossieman on 2009-04-29
> **Onay said:**
> Thanks much! The speed is incredible... Ubuntu is great since it doesn't eat up memory like windows does so I can do this and still have tons of RAM.

I noticed that using 

```
firefox ~/.mozilla/firefox/xxxxxx.default tmpfs size=AMOUNT_OF_RAM_TO_USE,noauto,user,exec,uid=1000,gid=1000 0 0

```

Doest work for me. I have changed the guide ones more. Now it should work.

---

### Post by loo0olz on 2009-04-29
thanx pro good jop

---

### Post by Onay on 2009-04-29
> **Bossieman said:**
> I noticed that using 

```
firefox ~/.mozilla/firefox/xxxxxx.default tmpfs size=AMOUNT_OF_RAM_TO_USE,noauto,user,exec,uid=1000,gid=1000 0 0

```

Doest work for me. I have changed the guide ones more. Now it should work.

Yep I did that too since it wouldn't mount for some reason. Simple fix though. Thanks again.

Another tip that some people might find excessive but I find useful is adding a custom launcher to the panel that executes the tempfs_firefox script. I click it before I exit out of firefox in case I did something between the 5 minute sync times that I wanted to keep. Totally worth having to click on that icon before I exit firefox to have such a snappier browser... One of my biggest complaints was having a slow firefox. Not anymore

---

### Post by Bossieman on 2009-04-29
> **Onay said:**
> Yep I did that too since it wouldn't mount for some reason. Simple fix though. Thanks again.

Another tip that some people might find excessive but I find useful is adding a custom launcher to the panel that executes the tempfs_firefox script. I click it before I exit out of firefox in case I did something between the 5 minute sync times that I wanted to keep. Totally worth having to click on that icon before I exit firefox to have such a snappier browser... One of my biggest complaints was having a slow firefox. Not anymore


You don't have to do that actually. It doesn't matter if Firefox is running or not, the synchronization happens every 5 minutes anyway. 
If you are planning to turn the computer off right after you exit Firefox then it would work as you intended.

---

### Post by Grenage on 2009-04-30
Excellent guide.

---

### Post by Bossieman on 2009-04-30
> **Grenage said:**
> Excellent guide.

Thanks! 
I guess you noticed the increased speed and stability? :popcorn:
I haven't had any hangups for FF since I started using this method.

---

### Post by bhagwad on 2009-05-04
Thank you for taking the trouble to write this guide!

---

### Post by spongypants23 on 2009-05-06
After following this guide, Firefox segmentation faults every time I go to the Add-ons menu.

The Downloads window has also stopped appearing, and the download-file dialog no longer shows up. Files are automatically saved to disk without any notification.

Help?

---

### Post by Bossieman on 2009-05-06
> **spongypants23 said:**
> After following this guide, Firefox segmentation faults every time I go to the Add-ons menu.

The Downloads window has also stopped disappearing, and the download-file dialog no longer shows up. Files are automatically saved to disk without any notification.

Help?

Can you post what numbers you used in the guide and what addons you have active?

---

### Post by spongypants23 on 2009-05-06
> **Bossieman said:**
> Can you post what numbers you used in the guide and what addons you have active?

Since we both have 4GB of RAM, I used the numbers you supplied in the howto.

Although, I managed to solve my problems with the information in [_[this]_]("http://ubuntuforums.org/showpost.php?p=7057921&postcount=3") post, mainly:

> 
Try also to ad (if you don't have it already) the string

browser.cache.disk.parent_directory

and put in the path to the directory

/home/USERNAME/.mozilla/firefox/xxxxxxx.default

The segmentation fault problems went away after uninstalling the Download Statusbar add-on.(By the way, downloading files weren't appearing there either while it was installed. They were still automatically being saved to disk, though this problem is also fixed).

---

### Post by Bossieman on 2009-05-06
> **spongypants23 said:**
> 
The segmentation fault problems went away after uninstalling the Download Statusbar add-on.

So it appears that add-on Download Statusbar doesn't work with this guide?

---

### Post by Postponing Camel on 2009-05-06
> **Bossieman said:**
>  Rightclick the file **tmpfs_firefox.sh** and select **Properties**. Go to the tab **Permissions** and change the permissions so **Run** is marked to the right of **owner**. Close the window when you are finished.  
 Thanks for the guide! I'm a bit of a (x)ubuntu noob myself - at this step, I can't seem to find the option you're referring to - is [this]("http://img24.imageshack.us/img24/6268/screenshotqda.png") it or something else entirely? I couldn't find any other &quot;run&quot; options...

---

### Post by Bossieman on 2009-05-06
> **Postponing Camel said:**
> Thanks for the guide! I'm a bit of a (x)ubuntu noob myself - at this step, I can't seem to find the option you're referring to - is [this]("http://img24.imageshack.us/img24/6268/screenshotqda.png") it or something else entirely? I couldn't find any other &quot;run&quot; options...

Yes, the box that says "Allow this file to run as a program" has the exact same meaning. Just make sure it is marked and you are good to go.

---

### Post by Bishop Hill on 2009-05-06
I managed to screw this up bigtime, and now I cant start Firefox at all, it just says that another process is running:(

I believe that the problem started with me copying and pasting my old windows profile into .mozilla/profiles, instead of the orignal one I also used the numbers supplied in the guide since I have 4GB RAM). This somehow led to firefox not restoring the files I deleted, and I thought that I would get the same effect if I manually pasted the files in the xxxxxxxx.default-folder. Which I, of course, didnt.

Please, can anyone help me restore Firefox?

---

### Post by Bossieman on 2009-05-06
> **Bishop Hill said:**
> I managed to screw this up bigtime, and now I cant start Firefox at all, it just says that another process is running:(

I believe that the problem started with me copying and pasting my old windows profile into .mozilla/profiles, instead of the orignal one I also used the numbers supplied in the guide since I have 4GB RAM). This somehow led to firefox not restoring the files I deleted, and I thought that I would get the same effect if I manually pasted the files in the xxxxxxxx.default-folder. Which I, of course, didnt.

Please, can anyone help me restore Firefox?

First of all, the guide is pretty complicated so errors may appear. I will try to help you to solve the problem. I need you to clarify some questions first.

1. Do you have a copy of your original Ubuntu-firefox profile in a safe place?
2. Did you use your Windows profile in this guide?

---

### Post by Bishop Hill on 2009-05-07
> **Bossieman said:**
> First of all, the guide is pretty complicated so errors may appear. I will try to help you to solve the problem. I need you to clarify some questions first.

1. Do you have a copy of your original Ubuntu-firefox profile in a safe place?
2. Did you use your Windows profile in this guide?

1. Yes, it is safe.

2. Yes.

---

### Post by Bossieman on 2009-05-07
> **Bishop Hill said:**
> 1. Yes, it is safe.

2. Yes.

Rename the file .tmpfs_firefox.sh to something else, like .tmpfs_firefox_HELLOWORLD.sh

Reboot computer.

Empty both the created profile directory and your xxxxx.default directory. Firefox must be closed when doing this.

Then copy the content of your backup into the profile directory.

Rename the file .tmpfs_firefox_HELLOWORLD.sh to .tmpfs_firefox.sh

Make sure firefox are closed. Doubleclick the file .tmpfs_firefox.sh and choose run in terminal. When completed do it ones again. 

Go to your xxxxx.default directory. Is the content from the profile directory there? Can you verify that the total diskspace in the directory xxxx.default now represents the amount you have put into fstab?
If so reboot. After reboot, start a terminal and enter the command mount
If you see a line starting with firefox it works. Start Firefox. 

If this didn't help, can you describe where it went wrong?

---

### Post by Bishop Hill on 2009-05-07
The **** hits the fan in the second last step. When the content should be back i the xxxxxxxx-dir, it's not. Also, mount does not show firefox.

---

### Post by Bossieman on 2009-05-08
Ok, I would like you to verify that...

1. ...the line [COLOR="Red"]PROFILE="xxxxxxxx.default"[/COLOR] in the file .tmpfs_frirefox.sh has the same xxxxxxxx values as your xxxxxxxx.default folder located in you /.mozilla/firefox/ directory. Please post the line so I can take a look at it. 

2. ...the line starting with [COLOR="Red"]firefox /home/[/COLOR] in your /etc/fstab file is correct. Please post the line so I can take a look at it.

Can you post a screen showing the content inside the folder /.mozilla/firefox/ ?

---

### Post by Bishop Hill on 2009-05-08
I "solved" the problem, just reinstalled Firefox. This is/was a clean install, so there was nothing lost. I will perhaps try this again later, but right now I'm not sure about my skills yet. Thank you very much for your help! (tackar sjukt mycket för hjälpen, jag uppskattar verkligen att du tar dig tid att hjälpa efterblivna människor!)

---

### Post by Bossieman on 2009-05-08
@Bishop Hill

You're from Sweden, me2. The fact that you are swedish will help you a lot to successfully complete the guide. I have a more detailed guide (this guide is based on it) and it is written all in swedish. 

If you want to try again follow the swedish guide [here]("http://ubuntu-bossieman.blogspot.com/2009/04/hur-man-kor-sin-firefoxprofil-fran-ram_08.html"), it will be much easier for you to follow and understand.
I would like to mention for you the following: When you complete a Howto-guide and the final result doesn't work as intended, all that time you spend on the guide is not wasted. You have learned some things even if you aren't aware of it.  The more you try the more you will learn.
When you have successfully completed the guide and it works as intended, I promise you that the time spent was easily worth it. Firefox will work much better! 
 
Regards
/Bossieman

---

### Post by Bishop Hill on 2009-05-12
I used the swedish guide, and I must say, this works better than expected! Thank you very much:)!

---

### Post by Makrin on 2009-05-14
Wow! A Faster Firefox
Thanks!  :-)

Just wondering...
Will this still work after updating firefox?

---

### Post by Bossieman on 2009-05-14
> **Makrin said:**
> 
Will this still work after updating firefox?

Yes.

---

### Post by risknothin on 2009-05-14
so i have tried this an i must have made an error what appears to be happening is the file is creating a profile within the profile and firefox is opening up as it would under a fresh install. i have to go into xxxxxx.profile where there is another folder xxxxxx.profile and copy those items over into the prior folder. how do i fix this?

thanks

---

### Post by Makrin on 2009-05-15
That happened to me aswell i fixed it by copying all files over from profile folder to xxxxxx.default and then closed firefox.After closing firefox I  launched the tmpfs_firefox.sh file.

after that it's been working fine

---

### Post by Bossieman on 2009-05-19
> **risknothin said:**
> so i have tried this an i must have made an error what appears to be happening is the file is creating a profile within the profile and firefox is opening up as it would under a fresh install. i have to go into xxxxxx.profile where there is another folder xxxxxx.profile and copy those items over into the prior folder. how do i fix this?

thanks

Have you managed to fix it?

---

### Post by risknothin on 2009-05-19
what appears to be happening is that it is saving the ram profile somewhere else than the folder that firefox uses.

i went into .mozilla and pasted the copy of the files that i saved from profile before starting the tweak.

when i restart my new links and stuff aren't saved

i'm not sure what the issue is

---

### Post by Bossieman on 2009-05-21
> **risknothin said:**
> what appears to be happening is that it is saving the ram profile somewhere else than the folder that firefox uses.

i went into .mozilla and pasted the copy of the files that i saved from profile before starting the tweak.

when i restart my new links and stuff aren't saved

i'm not sure what the issue is

You have to wait about 5 minutes before you restart the computer. 5 minutes is default in the guide for saving the changes to the computers HDD.

---

### Post by kay-man on 2009-05-22
I had the same issue with the nested profile folder. I changed the script to this:

```
#!/bin/bash

# Change this to match your correct profile
PROFILE="xxxxxxxx.default"

cd "${HOME}/.mozilla/firefox"

if test -z "$(mount | grep -F "${HOME}/.mozilla/firefox/${PROFILE}" )"
then
    mount "${HOME}/.mozilla/firefox/${PROFILE}"
fi

if test -f "${PROFILE}/.unpacked"
then
    rsync -av --delete --exclude .unpacked ./"$PROFILE"/ ./profile/"$PROFILE"
else
    rsync -av ./profile/"$PROFILE" .
    touch "${PROFILE}/.unpacked"
fi

exit
```

---

### Post by joesnose on 2009-05-22
hello, nice guide, i am having a problem though. The profile is not being loaded at start up, if i manually run the .tmpfs_firefox.sh, all is well, however it is failing to run at start up. also if i try /home/joe/.tmpfs_firefox.sh  from the terminal it says no such file or directory.

Am i missing something?

---

### Post by Bossieman on 2009-05-22
> **joesnose said:**
> [...] if i try /home/joe/.tmpfs_firefox.sh  from the terminal it says no such file or directory.

Am i missing something?

I guess you just have missed to rename tmpfs_firefox.sh to .tmpfs_firefox.sh

---

### Post by joesnose on 2009-05-22
> **Bossieman said:**
> I guess you just have missed to rename tmpfs_firefox.sh to .tmpfs_firefox.sh

Thanks but that is not the problem, it is hidden, any other ideas?

---

### Post by kay-man on 2009-05-22
Try

```
which tmpfs_firefox.sh
```

Double check the path and make absolutely sure you've got it right.

---

### Post by joesnose on 2009-05-22
> **paulklos said:**
> Try

```
which tmpfs_firefox.sh
```

Double check the path and make absolutely sure you've got it right.


no output from that at all! the file is definately in home/joe/ as i can load it manually. i don't get it.

---

### Post by kay-man on 2009-05-22
Sorry, my bad. Now I forgot the dot. So I really meant this:

```
which .tmpfs_firefox.sh
```

---

### Post by joesnose on 2009-05-22
> **paulklos said:**
> Sorry, my bad. Now I forgot the dot. So I really meant this:

```
which .tmpfs_firefox.sh
```

thats what i put, it still had no output.

---

### Post by kay-man on 2009-05-22
What about this?

```
ls -l .tmpfs*
```

---

### Post by risknothin on 2009-05-22
now im having a problem with my extentions, they are all gone
--------
edit
----------
i tried to copy and paste that old profile and it says that there is not enough room
 - i tried to reinstall some of the extension and there is issues with that also - it closes down firefox

---

### Post by 89vision on 2009-05-23
Worked great for me though I did have to make a pretty significantly bigger ramdisk than the author because of offline gmail.

---

### Post by joesnose on 2009-05-23
> **paulklos said:**
> What about this?

```
ls -l .tmpfs*
```

Thanks for the help.

That gives me...

```
joe@joe-laptop:~$ ls -l .tmpfs*
-rwxr-xr-x 1 joe joe 437 2009-05-22 15:42 .tmpfs_firefox.sh 
joe@joe-laptop:~$ 

```

does that help at all.

---

### Post by Bossieman on 2009-05-23
> **risknothin said:**
> now im having a problem with my extentions, they are all gone
--------
edit
----------
i tried to copy and paste that old profile and it says that there is not enough room
 - i tried to reinstall some of the extension and there is issues with that also - it closes down firefox

Your extensions still exists in your backup.
Exit firefox, empty both the profile and the xxxxxx.default directory. Then copy the content of your backup to the default directory. Wait a few minutes until the xxxxx.default directory becomes a copy of the default directory. Then start firefox.

---

### Post by cheesepenguins on 2009-05-25
Lovely guide worked first time :)

One niggle, is there anyway to make the script run upon firefox closing?

The script only updates every few minutes, obviously to reduce hard disk use and hence the speed increase, but it can lead to losing history items etc if it doesn't update right before exiting.

---

### Post by risknothin on 2009-05-25
yeah i restored the extensions from the back up but i had to undo the entire tweak because it would not let me save the back up into the profile folder because it said i didnt have enough room

---

### Post by aktiwers on 2009-05-25
Thanks for the great guide, its working great here :)

---

### Post by cheesepenguins on 2009-05-26
In response to myself and for anyone who wants FF to save their preferences instantly upon exit I created a Firefox add-on that runs the script upon window close.

Extract the Tar file, then right click on the file, open with "firefox".

The process is simple, edit the file "overlay.js" found in the content folder of the extension to have the full path to the script, e.g. /home/m00z0r/.firefox (where I have mine), highlighted in red below.

```
// create an nsILocalFile for the executable
            var file = Components.classes["@mozilla.org/file/local;1"].createInstance(Components.interfaces.nsILocalFile);
            file.initWithPath("[COLOR="Red"]//home//m00z0r//.firefox[/COLOR]"); //Insert path to script here, including script itself!
```

Thats it, lovely jubly :)

Note: This runs on every window closing.

---

### Post by 89vision on 2009-05-26
> **cheesepenguins said:**
> In response to myself and for anyone who wants FF to save their preferences instantly upon exit I created a Firefox add-on that runs the script upon window close.

Extract the Tar file, then right click on the file, open with "firefox".

The process is simple, edit the file "overlay.js" found in the content folder of the extension to have the full path to the script, e.g. /home/m00z0r/.firefox (where I have mine), highlighted in red below.

```
// create an nsILocalFile for the executable
            var file = Components.classes["@mozilla.org/file/local;1"].createInstance(Components.interfaces.nsILocalFile);
            file.initWithPath("[COLOR="Red"]//home//m00z0r//.firefox[/COLOR]"); //Insert path to script here, including script itself!
```

Thats it, lovely jubly :)

Note: This runs on every window closing.


I owe you a beer.

---

### Post by 89vision on 2009-05-26
> **cheesepenguins said:**
> In response to myself and for anyone who wants FF to save their preferences instantly upon exit I created a Firefox add-on that runs the script upon window close.

Extract the Tar file, then right click on the file, open with "firefox".

The process is simple, edit the file "overlay.js" found in the content folder of the extension to have the full path to the script, e.g. /home/m00z0r/.firefox (where I have mine), highlighted in red below.

```
// create an nsILocalFile for the executable
            var file = Components.classes["@mozilla.org/file/local;1"].createInstance(Components.interfaces.nsILocalFile);
            file.initWithPath("[COLOR="Red"]//home//m00z0r//.firefox[/COLOR]"); //Insert path to script here, including script itself!
```

Thats it, lovely jubly :)

Note: This runs on every window closing.

Is anyone else having trouble untarring this?

---

### Post by zika on 2009-05-27
These is a sort-of simple alternative to this:

in **/etc/fstab** add line: **tmpfs        /tmp         tmpfs    defaults    0    0**
empty Cache in Firefox ...
in **about:config** add string variable: **browser.cache.disk.parent_directory** with value **/tmp**
done.

This way You get:
a. /tmp is in memory ...
b. Cache for FF is in memory.

This way You might have problems with:
a. large files that should go in /tmp, rare situation ... in that case comment that line in fstab temporarily  and use  **/dev/shm** for parent_directory...
b. ...

Difference from the method in this thread:
a. this way only Cache is in memory and the rest of xxx.default folder is on disk but the main part of disk access is for Cache ...
b. You do not have problem with updating profile ... it is on disk ...

Following line done occasionally in Terminal will enhance Your access to FF data-base: **find ~/.mozilla/**{firefox, firefox-3.5,firefox-3.6, whatever version You have}**/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \; **

---

### Post by cheesepenguins on 2009-05-27
> **89vision said:**
> Is anyone else having trouble untarring this?
I just downloaded and tested the file, un-tars fine here using the Ubuntu extraction program on the right click menu.

Also un-tars fine from the tar command: tar -xvf sync...

Try downloading it again?

---

### Post by Auslegung on 2009-06-20
This isn't working for me.  It seemed a little faster at first, but the profile isn't being mounted and now it seems a little slower.  I have better gmail 2, Compact Menu 2, Download statusbar, Gmail Notified, Resurect Pages, Tiny menu, and Ubuntu Firefox Modifications for add-ons.  Here're the numbers I used: instead of 128MB, I put 64MB, and when adding 70 to that I put 140M.  I used 5 minutes as the interval.  Any ideas?  I'm using eeeBuntu 3.0 (based on Jaunty) on an eeePC 1000HA with 2gb RAM.

---

### Post by xodeus on 2009-06-20
This is just a great guide.
Thanks for this tip...
I'll rate it 5/5 stars...

---

### Post by anselm on 2009-06-22
Used this guide on hardy heron, firefox works great.

Thanks :D

---

### Post by lovinglinux on 2009-07-13
> **cheesepenguins said:**
> Lovely guide worked first time :)

One niggle, is there anyway to make the script run upon firefox closing?

The script only updates every few minutes, obviously to reduce hard disk use and hence the speed increase, but it can lead to losing history items etc if it doesn't update right before exiting.

I have created a script that automates everything. It's a different approach, since the profile is not loaded into RAM on boot, but loaded/unloaded on-demand. You can only load one profile at a time, but the script supports multiple profiles. It also creates the cron jobs for synchronization, perform a backup before loading the profile into RAM, updates firefox preferences, updates fstab and more:

Here is what it does:
[list][*] 
[*] The script first detect your existing profiles and prompt you to choose which one you want to load into RAM.You can load only one profile at a time.
[*] Then it asks how much memory you want to allocate for the profile in RAM
[*] Then asks the interval you want to synchronize the profile with a copy in the disk, so you can keep any changes after unloading the profile from RAM.
[*] Then it saves a tar backup of your profile inside ~/.mozilla/firefox/ just to be safe in case something goes wrong with the synchronized copy during operation. This backup is named using the profile name, date and time of creation. It also includes a backup of your /etc/fstab.
[*] Then it creates a temporary /etc/fstab.bak to allow reverting the changes after unloading the profile from RAM.
[*] Then it changes the necessary preferences in Firefox prefs.js file (please not that safe browsing feature is disabled)
[*] Then it moves the content from your profile to a temporary folder ~/.mozilla/firefox/ramprofile, mount the profile into the RAM, the copy the contents from ~/.mozilla/firefox/ramprofile into it.
[*] Then it creates a cron job to allow syncronization between ~/.mozilla/firefox/ramprofile and your profile in RAM. (this might override personal cron jobs)
[*] Then it launches Firefox using the selected profile and put a notification in the notification area, which must be clicked when you want to unload the profile from RAM.
[*] When unloading, it clears the cron job and synchronizes the current content of the profile in RAM with ~/.mozilla/firefox/ramprofile
[*] Then unmount the RAM profile, restore the profile folder in the disk with the modified content from ~/.mozilla/firefox/ramprofile, restores the fstab, deletes temporary files and perform sqlite database optimization.[/list]

The script and further instructions are available in the "Running Profiles from RAM" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). Sorry about not posting it here, but I want to keep everything related to Firefox optimization in one place, thus facilitating maintenance of the tutorial and scripts. Nevertheless, I haven't forgotten to give the proper credit to this tutorial.

---

### Post by andrewabc on 2009-07-16
Every once in a while my profile gets corrupted. Firefox starts and icons and everything are constantly moving around and looks wierd.

My guess is this happens if it is syncing to HD when I am shutting down computer.

I first noticed it when I changed sync time to 1 minute. So I changed sync time back to 5 min and it took longer before it corrupted. (1 in 60 chance compared to 1 in 300)

Of course it got corrupted this morning when I turned on computer, so then I had to use profile backup from a week ago.

Any way to prevent this? Should I set up an rsync backup so when it does get corrupted I only lose 1 day at most?

I tried backing up to HD with the firefox extension on close, but the extenion is out of date and hard to get to work. I did get it working, but then firefox would give errors saying 'well this is embarrassing' that it could not load all tabs properly when I restarted computer.

---

### Post by lovinglinux on 2009-07-16
> **andrewabc said:**
> 
Any way to prevent this? Should I set up an rsync backup so when it does get corrupted I only lose 1 day at most?

I tried backing up to HD with the firefox extension on close, but the extenion is out of date and hard to get to work. I did get it working, but then firefox would give errors saying 'well this is embarrassing' that it could not load all tabs properly when I restarted computer.

[FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

### Post by andrewabc on 2009-07-18
I also notice that every time I restart computer my cache folder in ram profile is empty.
The 'profile' folder has lots of cache, but for whatever reason it doesn't get transferred to the ram profile at startup.

The cache folder in 'profile' folder gets wiped at 5 min sync mark since the ram profile cache is pretty much empty.

Is there a reason why the cache folder (full of cache at end of days use of firefox) not being transferred into ram when computer starts?

Here's my stuff:
```
#!/bin/bash

# Change this to match your correct profile
PROFILE="8vvxpz8t.default"

cd "${HOME}/.mozilla/firefox-3.5"

if test -z "$(mount | grep -F "${HOME}/.mozilla/firefox-3.5/${PROFILE}" )"
then
    mount "${HOME}/.mozilla/firefox-3.5/${PROFILE}"
fi

if test -f "${PROFILE}/.unpacked"
then
    rsync -av --delete --exclude .unpacked ./"$PROFILE"/ ./profile/
else
    rsync -av ./profile/ ./"$PROFILE"/
    touch "${PROFILE}/.unpacked"
fi

exit
```


firefox /home/andrew/.mozilla/firefox-3.5/8vvxpz8t.default tmpfs size=250M,noauto,user,exec,uid=1000,gid=1000 0 0

EDIT:
rebooted and it did remember my cache. So it must forget cache when I get the "well this is embarrasing, sorry your tabs did not close properly". Or something.

---

### Post by I Am Ahab on 2009-07-18
```
Rightclick the file tmpfs_firefox.sh and select Properties. Go to the tab Permissions and change the permissions so Run is marked to the right of owner.
```

Forgive me, but I don't quite understand what I'm supposed to do here. I can't find any "Run" in my permissions tab.

---

### Post by andrewabc on 2009-07-18
> **I Am Ahab said:**
> ```
Rightclick the file tmpfs_firefox.sh and select Properties. Go to the tab Permissions and change the permissions so Run is marked to the right of owner.
```

Forgive me, but I don't quite understand what I'm supposed to do here. I can't find any "Run" in my permissions tab.

Yah the tutorial is a little out of date (or copy/pasted from another tutorial?). Make sure "allow executing file as program" is checked in permissions tab and it should work.

---

### Post by andrewabc on 2009-07-19
I started firefox and it doesn't remember I have any extensions or themes. It remembered bookmarks. Not corrupted (usable). Good thing I rsynced profile a day ago.

This whole profile in ram is quite unstable. :(

---

### Post by lovinglinux on 2009-07-19
> **andrewabc said:**
> I started firefox and it doesn't remember I have any extensions or themes. It remembered bookmarks. Not corrupted (usable). Good thing I rsynced profile a day ago.

This whole profile in ram is quite unstable. :(

You should try my script from the "Running Profiles form RAM" section [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). Instead of running the profile from RAM on boot, it allows you to load the profile into ram before starting Firefox and unloading when you want. It also makes automatic backups and creates the cron jobs for synchronization.

---

### Post by I Am Ahab on 2009-07-19
So I've followed the guide to the end and the performance increase was quite remarkable, The only problem is that the profile won't load into RAM after reboot. So I have to run the script manually everytime I reboot, thus losing surfing history etc.

A guide to revert the changes made would be delightful.

EDIT: Picture of my scheduled task

[IMG]http://www.home.no/svgrin/Screenshot-Edit%20a%20Scheduled%20Task.jpg[/IMG]

Is everything in order?

---

### Post by andrewabc on 2009-07-19
> **lovinglinux said:**
> You should try my script from the "Running Profiles form RAM" section [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). Instead of running the profile from RAM on boot, it allows you to load the profile into ram before starting Firefox and unloading when you want. It also makes automatic backups and creates the cron jobs for synchronization.

Yah, I restarted computer and firefox was missing extensions/themes again. Odd how I go from firefox corrupting, to missing cache, to now missing extensions/themes. I might try that guide. But for now it's back to hard drive version.

---

### Post by Zwangsregistrierung on 2009-07-20
at first, great idea !! but i have one error and one idea. My idea is to insert two items in the personal crontab.

```

crontab -e

```
```

@reboot     $HOME/.tmpfs_firefox.sh > /dev/null
*/5 * * * * $HOME/.tmpfs_firefox.sh > /dev/null

```
so i dont need a startscript and i dont have to install gnome-schedule ! ( i'm using kubuntu 8.10 )

My error: when i edit my fstab, i had to use the following code:
```

tmpfs	/home/<username>/.mozilla/firefox-3.5/xxxxx.default tmpfs	defaults,noatime,mode=1777	0	0

```
when i take your code, i get an error, script cant find path in fstab

regards from germany

---

### Post by adempewolff on 2009-07-21
@Zwangsregistrierung, using your idea will "@reboot" also execute the script on suspend to RAM and/or disk or just on restarts?  If not are there other parameters (eg: @suspend, etc)?

Thanks!

edit: I think I misunderstood the purpose of this, it is to mount the profile into RAM on start-up.  I was wondering if there was a way to make it run it before a shutdown/restart/suspend.  any ideas?

---

### Post by Zwangsregistrierung on 2009-07-22
> **adempewolff said:**
> @Zwangsregistrierung, using your idea will "@reboot" also execute the script on suspend to RAM and/or disk or just on restarts?  If not are there other parameters (eg: @suspend, etc)?

Thanks!

edit: I think I misunderstood the purpose of this, it is to mount the profile into RAM on start-up.  I was wondering if there was a way to make it run it before a shutdown/restart/suspend.  any ideas?

the second line in the crontrab make a rsync to disk every 5 min. so you max. loose 5min. of browsing history if your PC crash.

the first line runs the script on every startup not only on reboots !

I have tested suspend to ram and suspend to disk. It works !!

If jou want to run the script on shutdown you can do this:
in KDE you find in ~/home/.kde two folders autostart and shutdown

there must be a aquivalent folder in ~/.gnome

you can add a bash script in shutdown folder. only two lines are needed

```

#!/bin/bash
$HOME/.tmpfs_firefox.sh

```

then change the permissons of the new script to run.

you can also edit your ~/.bashrc

add a new line:

```

alias reboot='$HOME/.tmpfs_firefox.sh && sudo reboot'

```

Now if you type reboot on console, you make a rsync to disk before your system reboot.

Regards, sorry about my bad english, i will learn it ;-)

---

### Post by Roughtrade on 2009-07-22
1

---

### Post by andrewabc on 2009-07-25
I want to get this working, so I've been doing some testing.

I have my ramfile and fstab etc working (everything in tutorial). I have fstab set to 400mb to eliminate running out of space possibility. Profile taking up 151mb right now with cache I want.

So it correctly copies 'profile' folder into alphanumeric ram profile when computer starts. File contents in each folder are exact same.

The problems starts when I start firefox-3.5
It clears the cache! I don't know why but as soon as I start firefox the cache folder gets emptied. I close firefox, copy/paste backup profile with cache into ram profile, start firefox and it empties cache again! Over and over.

Any ideas why it is clearing cache when starting? I did have command: firefox-3.5 %u
I removed %u and same problem.

EDIT:
Now odd problem, so I start firefox, cache is cleared, I browse a bit and some cache forms, I close firefox and open it again and the small amount of cache is still there. I think for some reason once cache gets to certain size it clears itself.

EDIT:
my firefox cache setting is at 131mb. My backup cache folder is 95mb in size. But I know when I was using it a couple weeks ago it would clear cache with only 1 mb or less. So I don't think it has to do with cache size, and I don't think it has to do with backup cache as it would clear fresh (new) cache after a reboot.

Attached is my about:config cache settings. I don't see how any of these settings would cause cache to be eliminated randomly.

EDIT:
ARGH! Now even without using tutorial (ram profile), it is clearing cache folder (from backup). So now I'm thinking maybe preload is loading stuff or something.

Uninstalled preload, restarted computer and cache gets wiped still.

So how is this possible? I made backup of profile, then put backup back in place and for some reason firefox wants to wipe cache at startup? Are there files being written at some other location that affect profile, making profile folder backup pointless?

---

### Post by xzero1 on 2009-07-28
> **zika said:**
> These is a sort-of simple alternative to this:

in **/etc/fstab** add line: **tmpfs        /tmp         tmpfs    defaults    0    0**
empty Cache in Firefox ...
in **about:config** add string variable: **browser.cache.disk.parent_directory** with value **/tmp**
done.

This way You get:
a. /tmp is in memory ...
b. Cache for FF is in memory.

This way You might have problems with:
a. large files that should go in /tmp, rare situation ... in that case comment that line in fstab temporarily  and use  **/dev/shm** for parent_directory...
b. ...

Difference from the method in this thread:
a. this way only Cache is in memory and the rest of xxx.default folder is on disk but the main part of disk access is for Cache ...
b. You do not have problem with updating profile ... it is on disk ...

Following line done occasionally in Terminal will enhance Your access to FF data-base: **find ~/.mozilla/**{firefox, firefox-3.5,firefox-3.6, whatever version You have}**/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \; **

I kind of prefer this to the authors idea, but what is the difference between using /tmp and /dev/shm. Couldn't we use /dev/shm and be done with it?:confused:

---

### Post by andrewabc on 2010-03-17
Will this tutorial be updated for ubuntu 10.04 release? Or create a new one?

Hopefully, as lots of people have netbooks with crappy hard drives.

---

### Post by pqwoerituytrueiwoq on 2010-05-04
Holy crap it even improved flash performance dramatically
@andrewabc
it works on 10.04

---

### Post by gzarkadas on 2010-05-09
Works on 9.10 also. No problems up to now. Nice howto! :)

---

### Post by iGold on 2010-06-01
Thanks for the idea. In the first time I have made transition of Firefox profile to RAM just like in this guide, but later I have decided to use /dev/shm directory for profile storage. I've modified script to this one:```

#!/bin/sh

RAM_PATH="/dev/shm/firefox-$LOGNAME"

cd ~/.mozilla/firefox

if ! PROFILE=`egrep "^Path=$RAM_PATH/[^/]+$" profiles.ini | egrep -o '[^/]+$'` ; then
    printf "profiles.ini must be corrected first\n"
    exit 1
fi

if [ ! -d "$PROFILE" ] ; then
    printf "There is no profile directory '$PROFILE' in ~/.mozilla/firefox\n"
    exit 1
fi

if [ ! -d "$RAM_PATH" ] ; then
    mkdir "$RAM_PATH"
    cp -a "$PROFILE" "$RAM_PATH"
else
    rsync -a --delete "$RAM_PATH/$PROFILE" .
fi

```
and have changed ~/.mozilla/firefox/profiles.ini to point to the new dir:
```

...
IsRelative=0
Path=/dev/shm/firefox-igold/default.ckk

```
In crontab I've added such lines:
```

@reboot			/home/igold/bin/ff_sync_profile
*/5 *	*   *	*	/home/igold/bin/ff_sync_profile

```

It seems to work :)

---

### Post by XSAlliN on 2010-06-25
> **zika said:**
> These is a sort-of simple alternative to this:

in **/etc/fstab** add line: **tmpfs        /tmp         tmpfs    defaults    0    0**
empty Cache in Firefox ...
in **about:config** add string variable: **browser.cache.disk.parent_directory** with value **/tmp**
done.

This way You get:
a. /tmp is in memory ...
b. Cache for FF is in memory.

This way You might have problems with:
a. large files that should go in /tmp, rare situation ... in that case comment that line in fstab temporarily  and use  **/dev/shm** for parent_directory...
b. ...

Difference from the method in this thread:
a. this way only Cache is in memory and the rest of xxx.default folder is on disk but the main part of disk access is for Cache ...
b. You do not have problem with updating profile ... it is on disk ...

Following line done occasionally in Terminal will enhance Your access to FF data-base: **find ~/.mozilla/**{firefox, firefox-3.5,firefox-3.6, whatever version You have}**/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \; **

Tried the OP solution, but didn't prove to me more efficient then quoted one from above. Yet, this is for a Desktop system with 1.2 MB dw...

As for sqlite I use an extension caled Vacuum Places - which does what's suppose to...

=====

I do have a question regarding **/tmp**... I used to store my FF cache temporarily in /dev/shm. As for /tmp - I have an assigned /tmp partion of 30 GB made at install, sho should be enough. But if you mount:

tmpfs /tmp tmpfs defaults 0 0

Don't you need to have next line mounted asswel:

**none /dev/shm tmpfs defaults 0 0**

?

---

### Post by XSAlliN on 2010-06-25
nvm, i'll move back to my original settings, don't want disable /tmp partition and is also cleaner that way. :)

All I did was **/dev/shm/** to **browser.cache.disk.parent_directory**. done :)

---

### Post by firekage on 2012-09-08
> When you are absolutely sure your line is correct save the file and exit the editor.

We must now empty the content of your .mozilla/firefox/xxxxxx.default directory. To do this we have to shut down Firefox completely to avoid Firefox from re-create the profile. You can copy the relevant part of the guide to a text file or use another browser for the next part, but you have to exit Firefox before erasing the content. Before you empty the folder, doublecheck that you have a copy of the content of .mozilla/firefox/xxxxxx.default in the directory .mozilla/firefox/profile and I recommend an extra copy somewhere safe.

When Firefox is closed erase the content of .mozilla/firefox/xxxxxx.default. Look down to the left corner in the Nautilus window and remember the amount of free space you have in your .mozilla/firefox/xxxxxx.default directory. 

When this is done locate the file tmpfs_firefox.sh we created earlier and doubleclick it. A window will appear. Chose Run in terminal. 
You will now see a terminal window open and close very quickly. This is normal and due to the fact that the whole process went very quickly. The script mounted your Firefox profile into your computer's RAM. Double-click again on the file tmpfs_firefox.sh and select once more Run in terminal. The same thing happens as before but with the difference that the script synchronized the contents of the folder with your profile folder xxxxxx.default. 

Now enter the folder xxxxxx.default.** You should now see that the erased files are back.**

I don't know what i could do wrong but in my case ther aren't back.

---

