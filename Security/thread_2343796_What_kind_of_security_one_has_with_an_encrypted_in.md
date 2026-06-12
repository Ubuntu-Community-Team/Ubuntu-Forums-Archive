---
title: "What kind of security one has with an encrypted installation questions"
date: 2016-11-19
forum: Security
---

### Post by xenon3 on 2016-11-19
Hackers still can of course place files in the /home directory?

The OS software containing directories are only encrypted of course, the files in these directories can not be messed with of course, maybe they cannot even place malicious files in these directories? They would need to know the encryption key. The encryption key is specified by the user while the installation wizard is not online?

After installation of OS to get in the system the key is typed while system is not online? This is right after GRUB menu.

/home is not encrypted? Not part of the encrypted OS? /home is the only internet accessible directory? Maybe the browser cache directory in /home? 

If hardware viruses exist as build in the hardware straight from the factory, or maybe there are even hardware day zero exploits, than I can imagine hackers have already the encryption key by hardware key loggers, maybe of everyone :(

---

### Post by HermanAB on 2016-11-19
Encryption protects data at rest.

That means your data is safe if someone would steal your machine and sell it on Ebay, or if some Jackboots would break down your door and seize your machine.  However, while the machine is running, the encrypted data is accessible to you.

For protection against malicious programs and hackers, there are other mechanisms, such as SELinux and AppArmor.  These systems provide protection while the machine is running.  Think of AppArmor/SELinux as Access Control Lists on steroids.

---

### Post by xenon3 on 2016-11-19
> **HermanAB said:**
> 

Encryption protects data at rest.



Thanks! I know what you mean. However only at rest is a pity, someone is placing millions of empty files in my /home subdirectories, maybe wants to flood the FAT table, I don't know, trying to sabotage my computer?

---

### Post by HermanAB on 2016-11-19
"someone is placing millions of empty files in my /home subdirectories" - On a UNIX/BSD/Linux machine, this is very unlikely to happen.  On these systems, there is strong separation between user accounts.  Each service typically runs with a unique user name.  If you are joesixpack and run a web server named apache, then a hacker who breaks into the web server will only be able to mess with apache files and not with joesixpack files.  This separation is even more strongly enforced when you have SELinux or AppArmor.

Anyhow, I've been using UNIX/Linux since about 1985 and never had serious security issues on my own machines.  I have had to fix many servers that were administered by morons who used 4 character passwords though...

---

### Post by xenon3 on 2016-11-19
> **HermanAB said:**
> 

I have had to fix many servers that were administered by morons who used 4 character passwords though...



I have 20 characters strong password Numbers - Uppercase - Lowercase - Special Signs (all mixed) for the only (admin) user on the machine, I'm the only one who has access and uses my machine, my machine is in a locked room

What happens finally when system is over-flooded with empty files in /home? there are coming more and more I can see them with clamscan from terminal, directories I can see in file explorer

---

### Post by cariboo on 2016-11-19
Did you run top, to see what is creating these empty files in your home directory?

---

### Post by xenon3 on 2016-11-19
> **cariboo said:**
> Did you run top, to see what is creating these empty files in your home directory?

Must I look for an odd USER?

Normally I would only have kingdom and root as USER

Would be nice if top had a cumulative option, than I would run it all day and night, see if there were intermediate other USERs

---

### Post by kpatz on 2016-11-19
Are these files only appearing in your home directory?  Only your user account and root should have access to your home so either a program you're running from your account or one running as root could be doing this.

Are the files appearing directly in your /home/(yourusername) or in subdirectories within?  What are the files named?  Can you post a screenshot showing some of them?

Can you post the output of the command:```
ls -ld ~
```to show what your home directory permissions are?

---

### Post by xenon3 on 2016-11-20
> **kpatz said:**
> Are these files only appearing in your home directory?  Only your user account and root should have access to your home so either a program you're running from your account or one running as root could be doing this.

Are the files appearing directly in your /home/(yourusername) or in subdirectories within?  What are the files named?  Can you post a screenshot showing some of them?

Can you post the output of the command:```
ls -ld ~
```to show what your home directory permissions are?

```


clamscan -r /home
 ...
/home/kingdom/bt4e2BN7gn/VBTYJS : Empty file
/home/kingdom/bt4e2BN7gn/ABCTYS : Empty file
/home/kingdom/bt4e2BN7gn/XYZVTJ : Empty file
...


```

```


kingdom@king-MS-7728:~$ ls -ld
drwx------ 30 kingdom kingdom 12288 nov 17 13:49 .
kingdom@king-MS-7728:~$ 


```

---

### Post by kpatz on 2016-11-20
Are all the empty files in bt4e2BN7gn ?  Or in multiple directories?

What happens if you run the command ```
rm -rf ~/bt4e2BN7gn
``` ?

Run top or htop and see if there is some process running that may be creating these files.

---

### Post by xenon3 on 2016-11-20
> **kpatz said:**
> Are all the empty files in bt4e2BN7gn ?  Or in multiple directories?

What happens if you run the command ```
rm -rf ~/bt4e2BN7gn
``` ?

Run top or htop and see if there is some process running that may be creating these files.

There wore at least 4 such directories with empty files with same number format 2 in /home/kingdom/ (my user home directory) and 2 way up subdirectories in /home = /home/.../.../.../...

I could delete them with delete button, they went in trash bin, can remove them from trash with "empty trash", but they come back after reboot, I tried to remove them from ./trash with file explorer and delete button from keyboard, but they come immediately back renamed as bt4e2BN7gn.2, once again bt4e2BNgn.2.2 and so on

I'm not so worried about removing them as what creates them and why?

What can I see with top and htop? What must I look for? How is the process called that creates files?

When it are hackers or hacker software that creates them, they must have my 20 characters strong password hacked!

---

### Post by cariboo on 2016-11-20
Post a screenshot of top similar to this:

---

### Post by xenon3 on 2016-11-21
> **cariboo said:**
> Post a screenshot of top similar to this:

Here it is, can one see it in a snapshot? I mean what about if process is accidentally not active?

---

### Post by kpatz on 2016-11-21
Were you surfing the web right before you took that screenshot?  Firefox is using up a bunch of CPU there.  Try rebooting, log in, don't launch anything but a terminal and run top again, take the screenshot (ideally when you see it creating files), then open firefox and post the screenshot here.

I like htop better than top personally... install it with **sudo apt-get install htop**

---

### Post by xenon3 on 2016-11-21
> **kpatz said:**
> Were you surfing the web right before you took that screenshot?  Firefox is using up a bunch of CPU there.

Maybe I had a couple of streaming videos running, I don't know anymore, can be also I had 30 tabs with websites open than, I cannot verify anymore did clean shutdown.

I will get back to you about proper htop screenshot, later on. OK? I'm now in a hurry

---

### Post by xenon3 on 2016-11-21
> **kpatz said:**
> 

 run top again, take the screenshot (ideally when you see it creating files), then open firefox and post the screenshot here.



htop screenshot, all apps and firefox closed

PS: I see thunderbird was still open, sorry, clickt an email address, thunderbird is voor my email archive, I use gmail as email client

---

### Post by kpatz on 2016-11-24
Try the command:```
lsof dir
``` but replace **dir** with one of the directories that the empty files are being created in... ideally when the files are being created.  This will tell what process(es) are doing it.

---

### Post by xenon3 on 2016-11-25
> **kpatz said:**
> Try the command:```
lsof dir
``` but replace **dir** with one of the directories that the empty files are being created in... ideally when the files are being created.  This will tell what process(es) are doing it.

```


kingdom@king-MS-7728:~$ lsof /home/kingdom/.local/share/Trash/files/9tn1w97rXc.2.2
COMMAND   PID    USER   FD   TYPE DEVICE  SIZE/OFF    NODE NAME
nautilus 2704 kingdom   25r   DIR   0,27 375033856 4063246 /home/kingdom/.local/share/Trash/files/9tn1w97rXc.2.2
kingdom@king-MS-7728:~$ 


```

these directories wore in /home/kingdom/ I could delete them and they got into the Trash bin, but now I cannot empty Trash bin anymore, as you maybe remember, they get renamed with .2 appended, every time you try this.

Don't know if hackers can add more empty files while directories wore replaced to ./Trash/files/ folder, anyways there seem to be no new ones added in /home/kingdom/ (not even hidden ones)

PS: I never used nautilus command, seems to be a file manager, maybe because I am with file explorer in /home/kingdom/.local/share/Trash/files/ ?

---

### Post by kpatz on 2016-11-25
Since you deleted them they're in trash and nautilus is accessing the directory.  Nautilus is the GUI file manager, like Explorer in Windows.

Run the lsof command on the folder where the empty files are being created, before you delete them.  That will (hopefully) tell us what process is creating the files.

---

### Post by xenon3 on 2016-11-25
> **kpatz said:**
> Since you deleted them they're in trash and nautilus is accessing the directory.  Nautilus is the GUI file manager, like Explorer in Windows.

Run the lsof command on the folder where the empty files are being created, before you delete them.  That will (hopefully) tell us what process is creating the files.

This too weird, or the directories with these empty files have some kind of protection to be removed permanently (from the trash bin), until now I only have troubles with them during /home clam scans, with takes 4 hours to complete, so I think that is the intend, to discourage me from clam scanning my computer, or it is some kind of real weird corruption of the OS, could be an unknown virus, even clam scan did not see, I used to clam scan every day, not any more takes too long

I deleted them from /home/kingdom they went in to trash bin, they cannot be removed from trash bin, there were no new ones created in /home/kingdom (I mean directories with millions of empty files) so I can't lsof in /home/kingdom.

---

### Post by vasa1 on 2016-11-26
Do you use Bleachbit?

---

### Post by kpatz on 2016-11-26
Let's get your trash cleaned out another way...

Hit Ctrl-Alt-F1 to get to a console, and login there.

Then run the command```
sudo service lightdm stop
``` to shut down the GUI manager, Unity, and everything else.

Then clear your trash folder with:```
rm -rf ~/.local/share/Trash/*
```If that command fails, try it again with sudo.

Restart the GUI manager with ```
sudo service lightdm start
``` and then log out of the console with Ctrl-D or the logout command.

Hit Ctrl-Alt-F7 to get back to the GUI.  Log in and see if things are working ok now.  If you start seeing the empty files appear again, run the lsof command I mentioned before on one of the directories the empty files are being created in.

---

### Post by xenon3 on 2016-11-29
> **vasa1 said:**
> Do you use Bleachbit?

Yes mostly as root, normal takes a couple of hours :(

---

### Post by xenon3 on 2016-11-29
> **kpatz said:**
> 

Let's get your trash cleaned out another way...

Hit Ctrl-Alt-F1 to get to a console, and login there.

Then run the command```
sudo service lightdm stop
``` to shut down the GUI manager, Unity, and everything else.

Then clear your trash folder with:```
rm -rf ~/.local/share/Trash/*
```



Yes it worked, in a weird kind of way, after issuing command rm ... it took a couple of minutes, cursor was gone, then screen went black, I thought maybe it takes long to delete the millions of empty files, waited an hour screen was still black and no cursor, rebooted, looked in trash the empty files containing directories were gone, but I had other stuff in the Trash bin which was still there, which is weird because rm ... should have deleted every thing, however I could empty Trash from the GUI now, so Trash is completely empty now, I could not do it before as you know.

---

