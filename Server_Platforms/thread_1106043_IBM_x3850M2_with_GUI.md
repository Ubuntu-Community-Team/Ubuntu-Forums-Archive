---
title: "IBM x3850M2 with GUI"
date: 2009-03-25
forum: Server Platforms
---

### Post by lloydbme on 2009-03-25
Hello,

I'm currently doing a test environment for a client and I've installed Ubuntu AMD64 on an IBM x3850M2 box.  Part of the testing involves setting up a GUI so I've done the following :

> You need the Ubuntu Alternate CD (not the Desktop CD).

Then type sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

However, when I do the last command, I get a blank screen. 

I'm wondering if its Ubuntu not understanding the RSA II adapter or some such and I was wondering if anyone can help me out.

Thanks

---

### Post by zd_024 on 2011-04-05
[FONT=Arial][FONT=Arial]hi, I find the question you asked about the "**IBM x3850M2 with GUI** "
[/FONT][FONT=Arial][http://ubuntuforums.org/showthread.php?t=1106043](http://ubuntuforums.org/showthread.php?t=1106043)[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I am currently trying to  install the ubuntu amd64 on an IBM X3850M2 box. when I insert the install CD,  it can't be booted. 
[FONT=Arial]can you give me some suggestions about how to install the ubuntu amd64 ont X3850M2. [/FONT]
 
[/FONT][FONT=Arial] Additions: I loaded the bios with the default settings, and it dosen't work too. I had used the "Server Guide CD" the IBM supply to install Windows Server 2003 successfully, but when I find the topic on how to install ubuntu on x3850M2 on the official website, it says there is no support.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I am very urgently needing your help about intalling the ubuntu amd64.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]please give your reply to me ASAP.[/FONT]
[FONT=Arial][/FONT] 
[/FONT][FONT=Arial][/FONT]

---

### Post by lloydbme on 2011-04-05
Hello, 

As you can see, I did this around 2 years ago while I was an intern at IBM doing a POC.

The entire report I wrote may be considered an internal IBM document, but here is an excerpt from my report that talks about how I set up the environment.  I hope it will be of use to you and allow you to enjoy the x3850M2

Initial setup:

> To prepare the x3850 M2 for installation, the LSI Webbios was used to create a redundant array across the two 73GB 2.5” SAS drives using the easy configuration.  The volume was initialized through the ‘fast initialize’ option.  The BIOS of the x3850M2 was also restored to factory defaults.

Ubuntu Server Edition x64 8.10 was downloaded from the official website ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)).  The proper tabs and radio buttons were selected and when the download was complete, the ISO was burned onto a CD-R.  

Upon booting the CD-R, the default options were selected (US English, Canada as the region, time zone was left as default, keyboard was set to US standards).  The installer was able to see the volume created earlier and the default partition scheme was accepted.  The install carried through without any problems.
When the server rebooted, there was a command prompt that requested a login.  After logging in, a GUI environment was installed by downloading the AMD64 “Alternate install CD”, adding the CD into the repository, and installing the packages from the CD. (see appendix A for instructions)


Aforementioned appendix A

> Appendix A 
Installation of Ubuntu Desktop GUI on Ubuntu Server Edition
Source: [http://ubuntuforums.org/showthread.php?t=972693](http://ubuntuforums.org/showthread.php?t=972693)
1.) Download the alternate cd 
The alternate cd is: a text based installer."This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd or because their computer requires configuration after the installation is complete in order to use the desktop."

2.) Burn the ISO.

3.) Boot the server up and insert the alternate c.

4.) Type sudo apt-cdrom add
This adds the CD to the software sources list. 

5.) Type sudo apt-get update
This will update the software sources and make the CD available.

6.) Type sudo apt-get install ubuntu-desktop
This will install the Ubuntu GUI

7.) Type sudo dpkg-reconfigure xserver-xorg

8.) Type startx 


Cheers

---

