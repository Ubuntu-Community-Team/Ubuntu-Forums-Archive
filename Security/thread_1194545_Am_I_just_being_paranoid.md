---
title: "Am I just being paranoid?"
date: 2009-06-22
forum: Security
---

### Post by Lee_W on 2009-06-22
Go easy on me, I am a total newbie to Ubuntu, I am running Jaunty 9.04.

On April 15th my Windows network was completely hacked and rootkits were installed on every machine.  Once the malware was in place it proceeded to hijack Windows update and my anti-virus updates to complete its installation.

Once fully installed it was completely undetectable by normal malware scans such as MalwareBytes and SuperAntiSpyware.

In order to try to recover my data I set up a Linux computer (Since then I have set up several others, I really like this operating system so I am setting the other computers up as dual boot)  and I have been transferring data files from infected hard drives via a USB to IDE adapter to the main Ubuntu computer.  I then scan it with BitDefender while it is on the Ubuntu computer before I pass it off to another 1tb USB backup drive.

After the data is transferred I zero fill the old drive with the **sudo dd if=/dev/zero of=/dev/sdb** command before using Gparted to re-partition the drives.

I have installed the rkhunter and chkrootkit packages on my Linux computer and I run the checks daily since I have exposed the system to such a toxic environment.  I also bought a new router with a firewall to kill port forwarding to the internet.

Everything was smooth until today.  After closing Firefox I noticed that my desktop was quite different than it had ever been before.  I re-booted and the desktop returned to normal but I ran rkhunter and it came back with a hash code change in /usr/sbin/cron.  Also in that directory are the perl script files update-catalog and install-sgmlcatalog files and I notice that the file dates are both Tue Oct 24, 2004.

When I sent the rootkit files that I caught on the Windows computers to VirusTotal.com they decompiled it and part of its M.O. was to re-date any file it loaded to the date and time of the system bios - that would be about right for the old IBM NetVista that I am currently running.  Those file dates seem quite old for a 2 month old installation of Ubuntu.

What do you folks think?  Am in in for a new installation? 

...Lee

---

### Post by cariboo on 2009-06-22
Except for the cron problem everything looks OK. I would suggest you update rkhunter and run it again:

```
sudo rkhunter --update
```

to see if the error still shows up.

---

### Post by rookcifer on 2009-06-22
> **Lee_W said:**
> 
I have installed the rkhunter and chkrootkit packages on my Linux computer and I run the checks daily since I have exposed the system to suck a toxic environment.  I also bought a new router with a firewall to killl port forwarding to the internet.

You can run rootkit scanners all you want, but I think they are largely ineffective.  First off, any intruder who wastes his time targeting your box is not going to utilize a rootkit picked up by the scanners.  Secondly, the scanners themselves can be tampered with by the intruder.

> Everything was smooth until today.  After closing Firefox I noticed that my desktop was quite different than it had ever been before.  

Describe "different."

> I re-booted and the desktop returned to normal but I ran rkhunter and it came back with a hash code change in /usr/sbin/cron.  Also in that directory are the perl script files update-catalog and install-sgmlcatalog files and I notice that the file dates are both Tue Oct 24, 2004.

I assume you mean you found those two files in /usr/sbin (not /usr/sbin/cron because that isn't a directory).  Don't worry, I also have both of those files and they are also dated from Oct of 2004. These files are part of the SGML base installed by default.  As for the old dates - sometimes simple scripts like this aren't updated because there is simply no need for it.

> When I sent the rootkit files that I caught on the Windows computers to VirusTotal.com they decomplied it and part of its M.O. was to re-date any file it loaded to the date and time of the system bios - that would be about right for the old IBM NetVista that I am currently running.  Those file dates seem quite old for a 2 month old installation of Ubuntu.

You are over analyzing this. :)  Your machine is clean.  Windows viruses/malware cannot affect Linux machines even if you tried to infect your machine on purpose.

---

### Post by HermanAB on 2009-06-22
Well, you are not paranoid if they really are out to get you.  However, in this case they are not...
;)

---

### Post by Lee_W on 2009-06-22
> Describe "different."The "power" button next to my user name suddenly had a different Icon.  I guess the best I can describe it is a "running man" that was lime green instead of the reddish power button.  The desktop select icons at the lower right of the screen were blue instead of orange.  What is now my **? **icon on the main toolbar had a life preserver icon instead of the **?**.

When I shut the system down I get a mysterious "untitled" window that will pop up during the shutdown procedure - I don't recall seeing that before.

The system overall seems very sluggish.

Immediately after the *problem* my USB backup drive (USB 2.0 card added) dropped to under 500 kb / second when I transferred files.  It took over 6 hours to transfer 3.2 GB of data to the backup drive.  Before that episode a similar transfer would have been done in 10 to 15 minutes.

You are correct, I improperly described the directory where the catalog files are located, it was the /usr/sbin directory where the old files were located.

I have a strong password but it is a strong password that may have been logged/compromised under the Windows systems that were whacked before since I use the same password for other applications..

What was loaded on my Windows systems was not just spyware but a suite of programs, they hid themselves well by hiding under subdirectories on programs that already have a ton of subdirectories, much of the stuff was hidden under never accessed subdirectories in CorelDraw.  I am such a newbie on Ubuntu that I don't know what is normal or not.

*Tin foil hat on*

One other element is that before the original problem I wrote some very unhappy emails to my Congressman.  They were not threatening but I did call him a slang term for a rectum.

*Tin foil hat off*

Thank all of you very much for your help,

...Lee

---

### Post by rookcifer on 2009-06-22
Have you checked smartctl to see if your hard drive is failing?  It seems that 6 hours to transfer 3.2 GB is a bit much.  Something isn't right with that.  A failing disk might also explain strangely disappearing icons, etc.

If you don't have it installed, then install smartmontools:

```
sudo apt-get install smartmontools
```

Then to run it:

```
sudo smartctl -a /dev/hdx
```  

where hdx is the hard drive in question (substitute hdx for hda or sda, etc.).  The above command will show all possible info about the disk.

Or you can just add the --help flag to see a list of possible commands.  I suggest you run an extended offline test to see if perhaps the disk is failing. 

For a more detailed manual, just type:

```
man smartctl
```

---

