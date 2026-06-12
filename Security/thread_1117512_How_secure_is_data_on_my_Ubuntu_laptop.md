---
title: "How secure is data on my Ubuntu laptop?"
date: 2009-04-06
forum: Security
---

### Post by Eugene_Bondarenko on 2009-04-06
Hi!

I have a netbook with eeebuntu installed on it. Yesterday my netbook got totally broken. Everything on the display is messed up and there is no chance to see anything however the netbook seems to boot up successfully. And if I blindly enter my login/pass it even plays the start up music.

This netbook is still under warranty and I am going to handle it to Asus tomorrow. However I have rather sensitive information on it. My Thunderbird is connected to my email accounts and Firefox has cookies to the bugtracker of my company. Of course I can change passwords there but I still have my invoices in /home/eugene. So if eeebuntu doesn't make any encryption on the stored data, Asus guys will see pretty detailed information on my income. So does eeebuntu make any encryption? And if no, could you think out any way to delete everything (without seeing what actually happens)?

PS. I tried connecting external display and that doesn't help :( The button that is supposed to switch to it doesn't help

---

### Post by Cybie257 on 2009-04-06
Have you tried shutting it down, connecting the external monitor, then rebooting? You didn't clarify if you just tried to add a monitor while it was booted. It's best to have the machine boot up after the monitor is connected AND powered on. That way the probing finds the monitor while booting to configure it. 

As for secure files... depends. do you have the system setup to require a password or just autologin? If you require a password, then they won't be able to get into some things. But, I'm not an expert in any way for this, so, maybe someone else can help there. 

Hope the monitor suggestion will help. 

-Cybie

EDIT: I see you 'blindly' enter name and password. So, there's that answer. :)

---

### Post by pmlxuser on 2009-04-06
deleting everything right??
well you can do the dangerous ```
sudo rm -r /homefolder 
``` from command prompt
of course the most secure one is a command called ```
 shred 
```

---

### Post by Eugene_Bondarenko on 2009-04-06
Yeah, I have login/password but I wonder if that's only primitive security against people who don't want to dig into it. So in other words if I create a home partition on a removable SD card, is there a way to read data on other computer? Or does it encrypt everything with the password I set?

Thanks, for "sudo rm -r /homefolder" and "shred". Killing everything is exactly what I need so I'll tell GRUB to load shell and run these commands. But I have a question. :) Will these commands ask me something like "do you really want..." or "are you sure...". You see, my display is totally dead so I do everything blindly and I won't have any chance to know if any confirmation needed.

---

### Post by Eugene_Bondarenko on 2009-04-06
> **Cybie257 said:**
> Have you tried shutting it down, connecting the external monitor, then rebooting? You didn't clarify if you just tried to add a monitor while it was booted. It's best to have the machine boot up after the monitor is connected AND powered on. That way the probing finds the monitor while booting to configure it. 

Yeah, I turned everything off, connected my old 19" display (that works perfectly with my old computer), turned display on, turn eee on, entered login/pass in a few minutes, got a "welcome" music  and waited for a few mins and then tried switching displays. Nothing happened. However I am not sure if it is supposed to work. I never connected external display since I installed Linux so may be it requires some config.

---

### Post by theozzlives on 2009-04-06
Dell will let you take the hard drive out (I did when I sent mine in). You should find out if Asus has such a policy.

---

### Post by HermanAB on 2009-04-06
Just keep the HDD when you send it in.  Asus is bound to have bazillions of HDDs in their workshop.

Note that your data is only secure if the HDD is encrypted.  The password means squat, since one can boot off a memory stick and then access all the data.  The main purpose of user permissions and passwords is to keep network users out of your data when the system is running - this doesn't help against someone that can do a cold boot.

---

### Post by gtr32 on 2009-04-06
Do you have ssh server running on the laptop? Log in from remote machine and backup any data you need, then shred it. If you don't have ssh, I would log in from the laptop, use the terminal shortcut key (forgot what it is :)) and type in this 3 part sequence (wait a while before the last step):

sudo apt-get install openssh-server <Enter>
youradminpassword here <Enter>
<Enter>

---

### Post by Eugene_Bondarenko on 2009-04-06
Well, killing everything blindly was kinda hard so I gave up. And Asus says that my SSDs are integrated so they can't give them to me. 

Well, I gave my EEE to sister and asked her to bring it to Asus guys. They told her that that's a mechanical damage and the warranty doesn't work (it's 100% that no mechanical damage was done) but they will repair everything for 480 USD. She told them to go to hell and left. When she was near the exit of the building an employee come up with her and told that it will cost only 240 USD if we ask him directly. Well, I can tell you that living in a f*cked up country sucks. :frown: I am going to visit them tomorrow and yell a little :p but most probably I am going to end up with a display baught from ebay that I'll install myself. And that's gonna be around 90 USD. :)

---

### Post by RansomStark on 2009-04-09
> **pmlxuser said:**
> deleting everything right??
well you can do the dangerous ```
sudo rm -r /homefolder 
``` from command prompt
of course the most secure one is a command called ```
 shred 
```


Shred is not a secure way of deleting files
Taken from the shred man page.

CAUTION:  Note  that  shred relies on a very important assumption: that the file system overwrites data in place.  This is the traditional  way to  do  things, but many modern file system designs do not satisfy this assumption.  The following are examples of file systems on which  shred is not effective, or is not guaranteed to be effective in all file sys-tem modes:

* log-structured or journaled file systems, such as those supplied with AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

---

### Post by Eugene_Bondarenko on 2009-04-09
Thanks for all the info but the problem has resolved by iteslef. I've baught the new 9" LCD from ebay and now waiting for it to be delivered from Taiwan. All the repairs will be done by me without 3rd party help so my data will be super secure :D

---

