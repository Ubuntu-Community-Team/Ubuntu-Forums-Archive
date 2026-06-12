---
title: "Suspend quirk"
date: 2015-06-12
forum: Ubuntu/Debian BASED
---

### Post by deliveryman2 on 2015-06-12
Hi Forum,
About one year with a Linux Lite desktop. Ubuntu 14.04.2LTS   Numerous times during a day, I put my computer into suspend. Once every few days, it will not come out of suspend. The computer itself starts up but the display remains suspended. The only option at that point is to hold power button until it shuts down and then restart. 

Once it restarts, I get at least 4 popups telling me I have a system problem., do I want to report the problem?  I have reported the problem for a year and it still is unresolved. I believe the error message mentions a kernel oops. I have no idea how to decipher or track down the problem. I am concerned that one of these times with the hard power button reset the machine won't come back to life. 

I have upgraded to different kernels but the problem remains. Any feedback on how to diagnose and perhaps solve this problem would be greatly appreciated. Thank you.

---

### Post by ajgreeny on 2015-06-12
Even though you can not see anything on screen you could try using the soft shutdown procedure.

Once the disk is spinning and leaving a few seconds for the now hidden OS to get running, hold the Print-screen/SysRq + Rt-Alt and slowly type REISUB (BUSIER backwards) and hopefully the machine will reboot.  You can also substitute a letter o, not figure 0, zero at the end of the sequence to shutdown, not reboot.

It is safer to do that than to hard reboot or shutdown.

---

### Post by deliveryman2 on 2015-06-12
ajgreeny... Thank you for the suggestion. I have tried that soft shutdown. The computer will not respond. That was one of the first things I tried so long ago and I have many kernel updates since then. 

Next time it happens, I will try that sequence of keys and report back. But as far as I know, it didn't work. I also tried ctrl alt del    and ctrl alt f2

I just love my linux and this suspend problem is the only quirk I have but it is pretty frustrating.  Have a good day.

---

### Post by Bucky Ball on 2015-06-12
Are you using Linux Lite or Ubuntu 14.04 LTS or both? They are not the same beast. Sorry, little confused as to which you're posting about from your post intro.

---

### Post by deliveryman2 on 2015-06-12
Bucky Ball... Sorry about that. I should have been more clear. It is Linux Lite but uses ubuntu 14.04 as the base. I'm a former windows user and have only been using linux for a year or so.

---

### Post by Bucky Ball on 2015-06-12
> **deliveryman2 said:**
> Bucky Ball... Sorry about that. I should have been more clear. It is Linux Lite but uses ubuntu 14.04 as the base. I'm a former windows user and have only been using linux for a year or so.

Thanks. Many distros are based on the Ubuntu kernel: 

*Thread moved to **Ubuntu/Debian Based**.*

... for clarity. The main support areas are intended for the official Ubuntu flavors only. No matter, when someone posts on your thread it will go to the top of the list in the 'New Posts' regardless. 

There are a LOT of distros based on the Ubuntu kernel and would get confusing and crowded trying to provide specialised support for everyone of them. While you are more than welcome to post in this section, you may want to increase your chances by posting in the Linux Lite forum as well as here, if they have one. 

When you get the pop-up errors, write them down or take a screenshot and attach it to your next post. That would be very helpful. When it says 'Do you want to send an error report', does it have an option to look at the details?

Another thing to try at the black screen. Can you press control+alt+F1 and get to a CLI (like a giant terminal)?

---

### Post by deliveryman2 on 2015-06-12
Bucky...
Thanks for moving to the appropriate thread. Never dawned on me there was Ubuntu stand alone operating system. DUH! Thanks for your patience. 

I have posted on the Lite forum when this first occurred and they suggested trying a series of key strokes and felt since it was a Ubuntu error code, specifically a kernel oops, that it likely is a problem with Ubuntu or conflict with my my hardware ??. 

I had the problem occur tonight. There were 4 popups and I took a series of screenshots of the details. I also tried both of your suggestions earlier today.    control+alt+F1 did nothing.  Print-screen/SysRq + Rt-Alt and slowly type REISUB did nothing. The disc spins but the display remains off. 

I uploaded 5 screenshots so I hope they are available. Thank you so much to all that have any solutions to this problem. It happens too often to ignore.

---

### Post by Bucky Ball on 2015-06-13
Yes, pictures fine and thanks for attaching rather than plopping them in the post. 

Ok, when you can log in see if you can switch off the backports PPA. May not be a problem but your last screenshot is showing an error about it so switch off and reboot. Perhaps something is installed from a backport that is causing hiccups (do you remember installing anything from a newer release from the backports?).

Two of the errors appear to be related to your wireless. There is 'iw' and 'iwconfig' showing errors. Does the wireless work OK on this machine?

---

### Post by deliveryman2 on 2015-06-13
Thank you for the suggestions. I did some research on PPA's and  backports since I didn't know what they were. I took some screen shots  that I think are getting me in the ballpark. Is there anything on those  screenshots that need adjustment? I may have added a repository  somewhere along the lines but this suspend problem has been with me ever  since I installed the operating system. What specifically do I need to  do to switch off backport PPA's. I see on the update tab a mention of a  backport. Do I just uncheck that and I've accomplished your suggestion  of turning off all backport PPA's?  

Odd about the wireless since  this desktop does not have a wireless feature. I have a satellite  modem. The satellite modem goes to a router for a wireless printer and  old lenovo laptop. But this desktop is cabled right to the router. No  wireless.

---

### Post by Bucky Ball on 2015-06-13
Is the system running quite normally once you get rid of these error messages? If so, could be the same issue as I had awhile back. Try switching off apport and reboot:

[QUOTE=bodhi.zazen]```
sudo nano /etc/default/apport
```

A file editor is now open. Change enabled from "0" to a "1" so it looks like this:

```
enabled=1    
```

To turn it off make it:

```
enabled=0
```

Now save your changes and close the file editor.

You can also use 'sudo service apport stop' to turn it off temporarily.[/QUOTE]

From [here]("http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport"). Let us know how you went.

---

### Post by deliveryman2 on 2015-06-13
I came across the thread to turn off the reporting function apport  a few weeks ago but thought that would only stop the reporting of the problem but have nothing to do with the original suspend problem. Once I get rid of the error messages, the computer runs perfectly again. 

I apologize for being extremely careful on this. I live very remote and this computer is our connection to the outside world ( yes, I still have the old laptop as backup)  I need to make sure I understand everything I do or I may be in a world of hurt. 

I have included a screenshot of the terminal window. In that configuration, the editor will not allow me to move my cursor around and simply change the 1 to a 0 . In other words, if I enter the sudo command in the editor, it brings up that terminal window but will not allow me to edit. I suspect one of the commands below will let me do it but I can't afford to experiment and kill my computer. Shouldn't I be able to simply change the 1 to a 0 once I am in the terminal? Thanks.

---

### Post by Bucky Ball on 2015-06-13
Yes, you should be able to move the cursor. No, this will not kill the system and put you in a world of pain, just switch off the annoying messages. If they were dire, you'd know about it by now. I researched all this when I installed 14.04 and got sick of the messages after about three months. :)

See [here]("https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F").

So, you are doing this in a terminal? I see no cursor anywhere on your screen and I see 'command line' at the top, not your user and computer names which suggests you are not using a regular terminal. Find it in Accessories and launch that then try again.

PS: Are you running 14.04.1 incidentally? I installed 14.04.2 on a machine just recently and this problem wasn't happening so maybe fixed. Your kernel is a little behind anyhow so I suggest you:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

This will get you to kernel 3.13.0-54.

---

### Post by deliveryman2 on 2015-06-13
Bucky... I feel bad that I am taking so much of your time on this and  thank you for all your help. I never knew there were two terminals. I'm  learning. :wink:     You were right that I was using command line terminal. You are also  right, there is no cursor. It will not allow me to click in the window  and place my cursor anywhere.

So I found root terminal and tried that. Same thing... no cursor. I am running ubuntu 14.04.2LTS     

OK , I see you modified some instructions. No problem. I tried both terminal versions. I am able to enter the instruction and the terminal window displays information but it will not allow me to place my cursor anywhere in the window. The only thing I can do is ctrl and letters at the bottom to get it to respond.

---

### Post by deliveryman2 on 2015-06-13
I meant to attach a image. So in other words, I am entering the new sudo instruction which brings up the proper terminal display but I cannot put my cursor and click anywhere on the screen. It appears that the only way to talk to the terminal at that point is to utilize the highlighted ctrl letters at the bottom and I don't know what one I am supposed to use.

---

### Post by Bucky Ball on 2015-06-13
Use lxterminal, yes, but not sure what the screen you've attached is. You should be opening this file:

```
sudo nano /etc/default/apport
```

... then changing the digit:

```
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=0
```

You can't move cursor? Try in the correct file in lxterminal and use the up down arrow keys to move the cursor to where you want then type. The mouse doesn't work in the terminal.

---

### Post by deliveryman2 on 2015-06-13
OK Bucky ...  Quite baffling. While I was writing to you this morning, I noticed an edited post where you suggested this command. sudo nano /etc/apport/crashdb.conf    That is where that one screenshot showed. However, I cannot see that addition to any post so I don't know where it went or why it showed up on my screen from you.

So I went back to    sudo nano /etc/default/apport    I was trying to use my mouse. OK, I can now move the cursor, delete the 1 and change to a 0. It should be that simple. Exit and done. It was not. I hit exit and then it went to the file name with numerous ctrl or M-keys to finish the job.  I spent an hour researching and trying to change that value in the terminal and failed. Change the value and exit. Not that simple or intuitive. I programmed "basic" a gazillion years ago so I have a good idea of how it should work. Anyways, I went to terminal, forced leafpad (text editor ) to open and in 30 seconds, it was changed and saved. 

I am convinced I have turned apport off so we'll see how it goes. I'll let things run now and see how the system performs. I'll let the board know how I make out and whether the problem is solved. Thank you so much for taking the time to help me. I wish you the best.

---

### Post by Bucky Ball on 2015-06-14
Change the value, contol+x to exit, 'Y' to save, 'enter' to exit. that's it. You should now be back at the terminal. Enter 'nano /etc/default/apport' and check your changes have stuck. Don't be 'pretty sure', be certain.

If no issues, see the second link in my signature. Thanks.

---

### Post by deliveryman2 on 2015-06-14
I just double checked. No question, the value is now 0.  I would be happy to mark it solved. I'm not certain it is solved though. Time will tell. The reporting of the problem, all the popup error messages are solved. They no longer will show but the initial problem of waking up from suspend and being forced to do a hard reset because the standard control+alt+F1 or  Print-screen/SysRq + Rt-Alt and slowly type REISUB does nothing may still exist. 

In other words, do you think turning off apport fixed my suspend problem? Was that the reason the computer would not respond to any keystroke combinations? Because apport was on, the only way to deal with the computer was a hard power button reset merely because apport was on?  I don't know the answer to those questions. I'm thinking the suspend problem is still here but at least it won't force popup messages and try reporting the problem back to ubuntu. I can mark this solved if you wish and if the suspend problem shows again, I can start a new thread. Thanks Bucky.

---

### Post by Bucky Ball on 2015-06-14
> They no longer will show but the initial problem of waking up from suspend and being forced to do a hard reset because the standard control+alt+F1 or Print-screen/SysRq + Rt-Alt and slowly type REISUB does nothing may still exist. 

Is it still locking up when coming out of suspend or hasn't since the change? If it hasn't and you would expect it would have, then it may be connected to the apport issue. Give it a day or two and see what happens. If no issue, then mark as solved. If problem persists, [s]take an aspirin and go directly to bed[/s] please let us know if it is the same issue and we'll keep digging. ;)

Is the machine working as it should otherwise?

---

### Post by deliveryman2 on 2015-06-14
This suspend problem only manifests itself every few days. I will give it a few days and see what happens. The computer is running fine and always runs fine after I do the hard power button reset. If I have an open program like office running and I need to do a hard reset because of the suspend problem, libre office needs to do a recovery but so far, all programs recover just fine. One of these days though, if it doesn't, you might find me halfway out the first floor window ready to hurtle myself the three feet to the waiting ground below. :p
I will resolve this thread one way or the other by wed morning. All the best.

---

### Post by Bucky Ball on 2015-06-14
Fingers crossed. If it does lock again, hit control+alt+F1. That should get you to a CLI. Log in and type in 'dmesg'. At the bottom of that output you will find some clues as to what happened. Good luck.

---

### Post by deliveryman2 on 2015-06-14
My suspend failed again tonight. I suspended for an hour, came back and the disc came to life but the display remained dark. No combination of key strokes would bring it back to life and I was again forced to do a hard reset via the power button. I did not have any error messages so apport is off but the problem remains.

Would there be an error log stored that would offer a clue? This is really frustrating. Seems like a significant quirk if the only option is a hard reset. Anyone have any ideas to try to cipher this out? Thanks.

---

