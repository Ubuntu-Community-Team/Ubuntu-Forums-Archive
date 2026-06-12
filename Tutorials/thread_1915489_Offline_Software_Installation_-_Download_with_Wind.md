---
title: "Offline Software Installation - Download with Windows"
date: 2012-01-26
forum: Tutorials
---

### Post by cortman on 2012-01-26
**[SIZE="3"]Offline Software Installation - Download with Windows[/SIZE]**

[COLOR="Red"]In light of T&T policy changes I have moved this tutorial to my blog and will maintain it there.  [http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/) [/COLOR]

Thank you for your thread and the work you have done in keeping it current and of use to the community.


It's commonly known how to download programs (and dependencies) for an offline computer with an online machine running Ubuntu, but what if your only access to the internet is through Windows?
You can still do it! I've written a small program in VB.Net that should run on any Windows computer. It takes a user-specified download script and downloads the files just the same as Ubuntu would.
You can download this program on SourceForge [here.]("https://sourceforge.net/projects/wassail/") It's available as a zipped .exe, or you can download the entire source code from the same site and compile it yourself if you prefer.
If you did a fresh installation of 11.10 Oneiric Ocelot or higher, you'll need to install Synaptic on the offline machine first. (For some reason it didn't come bundled with 11.10) This is a little involved but very doable. [Here's]("http://ubuntuforums.org/showthread.php?t=1901446") a link to my tutorial on that procedure.

[SIZE="2"]**1.**[/SIZE] On **offline** Ubuntu machine: Open a terminal with Control+Alt+t and type

```
synaptic
```

This will open up the Synaptic Package manager. You can browse available software in the column on the far left, or if you know specifically what you're looking for, type it into the search box.
When you find the software you want to install, right click it and select "Mark for Installation". If a dialog comes up "Mark Additional Required Changes" select Mark. This will ensure that all the packages required for the selected software get installed as well.

[SIZE="2"]**2.**[/SIZE] Once you've picked your software, go to File>Generate Package Download Script. Save the script to its own folder (call the folder "packages") on a USB flash drive or some other portable media. You can name the script whatever you want, but for clarity we'll assume you named it "download".
The Package Download Script is just a little text file that will tell your online computer which packages to download, so you can transfer them to the offline computer.

[IMG]http://dl.dropbox.com/u/54881717/Windows%20download%20tutorial/Packages%20folder.JPG[/IMG]

**[SIZE="2"]3.[/SIZE]** Take the flash drive to your **online** Windows computer. Download [Wassail]("https://sourceforge.net/projects/wassail/") and extract the .exe program file from the .zip into the same "packages" folder.

[IMG]http://dl.dropbox.com/u/54881717/Windows%20download%20tutorial/extract%20all.png[/IMG]


[IMG]http://dl.dropbox.com/u/54881717/Windows%20download%20tutorial/extracted.JPG[/IMG]

NOTE: If when you try to run Wassail it returns an error message saying that the .NET framework is not installed, it's easily fixed. You can download .NET 4.0 for free at [http://www.microsoft.com/download/en/details.aspx?id=17851]("http://www.microsoft.com/download/en/details.aspx?id=17851")

[SIZE="2"]**4.**[/SIZE]Double click the Wassail.exe and press the "Select Download Script" button. Find and select your script.

[IMG]http://dl.dropbox.com/u/54881717/Windows%20download%20tutorial/select%20script.jpg[/IMG]

This will download the packages to the "packages" folder. If you open the folder in a file manager you'll see one or more files with the extension .deb. These are the software package files.

Wassail will return a message of "Done!" when it is complete. Be patient! Some package files can be quite large.

[IMG]http://dl.dropbox.com/u/54881717/Windows%20download%20tutorial/done.JPG[/IMG]


[SIZE="2"]**5.**[/SIZE] Copy the "packages" folder containing the .deb files to the /home folder of the **offline** Ubuntu computer.

[SIZE="2"]**6.**[/SIZE] Open up a terminal on the offline computer and type

```
sudo dpkg -iR packages
```

You'll be prompted for your administrator password, which will be the same as your user login password. Enter it and Ubuntu will install your software!

---

### Post by qdb on 2012-01-27
Thanks, that's a nice concept.
I've got an Ubuntu Server running on vmware hosted on Windows for web development purposes and updating it's packages is always tricky.
I could use your program :)

---

### Post by cortman on 2012-01-27
If anyone can think of a more succinct title for this thread, I'm open to suggestions. I wanted something fairly descriptive but not too wordy.
And if any godlike C programmers want to have a stab at translating the program into C (so it'd compile and run on any Windows, with or without .NET framework), let me know!

---

### Post by chanzich on 2012-02-02
I'm not quite following you on step three when you say "download wassail and extract the .exe program file from the .zip into the same packages folder. Everything seems to go ok up until step three when i bring the script over from ubuntu to windows 7 and have to try and unzip it. Also when i go into a file manager i see no .deb files....

---

### Post by cortman on 2012-02-02
> **chanzich said:**
> I'm not quite following you on step three when you say "download wassail and extract the .exe program file from the .zip into the same packages folder. Everything seems to go ok up until step three when i bring the script over from ubuntu to windows 7 and have to try and unzip it. Also when i go into a file manager i see no .deb files....

So you're having trouble extracting the .exe? Have you actually run the program yet? You can unzip it by right clicking and selecting extract.

---

### Post by chanzich on 2012-02-02
I brought my flash drive back over to my laptop with ubuntu on it. I now see about eight different things with wget starting them and .deb ending.  Im assuming these are the eight packages i need for build essential. But when I go into the terminal and enter sudo dpkg -iR Packages (Packages is what i called it) I get dpkg: searched, but found no packages (files matching *.deb).

---

### Post by cortman on 2012-02-02
> **chanzich said:**
> I brought my flash drive back over to my laptop with ubuntu on it. I now see about eight different things with wget starting them and .deb ending.  Im assuming these are the eight packages i need for build essential. But when I go into the terminal and enter sudo dpkg -iR Packages (Packages is what i called it) I get dpkg: searched, but found no packages (files matching *.deb).

They shouldn't start with "wget" - that's part of the script. I just downloaded wassail and ran it on a fresh script, and it worked fine, so I'm not sure what the problem is. May I ask what program you're trying to download? I'll try it here to make sure.
As far as installing, did you copy them to your /home/your_name folder? They need to be there for the dpkg -iR command to work.
Sorry it's giving you problems!

---

### Post by chanzich on 2012-02-02
I cant thank you enough for you patients.  Im trying to install the build-essential so that I can compile my wireless driver.  I have been having a hell of a time. I understand the first few steps but im getting bogged down by having to unzip them.  I use 7zip (any suggestions for a better program.) I guess my biggest problem right now is taking them off my jump drive, unzipping them and using wassail.  Lol Im might need a step by step procedure.  Sorry, like i said i am an absolute noob.

---

### Post by cortman on 2012-02-02
> **chanzich said:**
> I cant thank you enough for you patients.  Im trying to install the build-essential so that I can compile my wireless driver.  I have been having a of a time. I understand the first few steps but im getting bogged down by having to unzip them.  I use 7zip (any suggestions for a better program.) I guess my biggest problem right now is taking them off my jump drive, unzipping them and using wassail.  Lol Im might need a step by step procedure.  Sorry, like i said i am an absolute noob.

Don't be sorry for being a beginner! Everyone here was one once too.
Here it is in a little more detail.

Download the Wassail.zip file on your Windows computer. Right click Wassail.zip and select "Extract all...". This will bring up the extraction location dialog. Click "browse" and select the "Packages" folder as the extract destination. Click Ok. A second window should come up showing the Wassail.exe file in the Packages folder. Double click Wassail.exe and click "Select download script". Select the download script. Wassail should start downloading, and will say Done! when complete. Then just take the flash drive with the .deb files over to the Ubuntu computer, copy "Packages" to your /home/username, and run the dpkg command.

Ok, I just successfully downloaded and installed the build-essentials on a VBox here, so it should work! Good luck!

---

### Post by chanzich on 2012-02-03
I tried what you said (thanks for spelling it out).  I tried it both on my desktop which has seven on it and my laptop which has ubuntu 10.04 64bit and seven.  When I get done using Wassail, I look in the folder where my packages and Wassail both are and the packages file is only about 2kb. So I opened in in ubuntu and all it is is this:
 
[FONT=Batang][SIZE=3]#!/bin/sh[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.5_all.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/b/build-essential/build-essential_11.4build1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_amd64.deb[/SIZE][/FONT]
 
I can't find where any .deb files are located. I must be making a mistake somewhere I just don't know where.  Thanks

---

### Post by cortman on 2012-02-03
> **chanzich said:**
> I tried what you said (thanks for spelling it out).  I tried it both on my desktop which has seven on it and my laptop which has ubuntu 10.04 64bit and seven.  When I get done using Wassail, I look in the folder where my packages and Wassail both are and the packages file is only about 2kb. So I opened in in ubuntu and all it is is this:
 
[FONT=Batang][SIZE=3]#!/bin/sh[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.5_all.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/b/build-essential/build-essential_11.4build1_amd64.deb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wget -c cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_amd64.deb[/SIZE][/FONT]
 
I can't find where any .deb files are located. I must be making a mistake somewhere I just don't know where.  Thanks

Whoa. Let me start again here.

When you say the "packages file" I assume you are referring to the download script you created with Synaptic. If so, the packages file is just a text file. All it does is tell Wassail "there's a package (a .deb file) at this web address, please download it." It doesn't contain any packages itself, it's only a text file.
Wassail looks at the addresses in the download script and downloads each .deb file individually. It saves these .deb files in the same folder that it is in. I.e., if I have Wassail.exe in a folder called "stuff", it will save all the .deb files in "stuff". Each .deb is its own file. When you get done running the script you pasted, you should have eight files with .deb on the end.
Once they're downloaded, you can delete the download script- you have no more use for it. The .deb files are what comprises the actual software.
If you opened Wassail, selected the script with it, and it returned the message "done", you will have a bunch of .deb files in the same folder as Wassail.

Hope this helps!

---

### Post by cortman on 2012-02-03
Here's some screenshots of running the program. View in order. Hope this helps.

---

### Post by Gonioscope on 2012-02-21
Hi, this method seems to be a bit difficult-recently I read recently about Keryx, but  I did not give it a try, someone else?

Best regards

Goni

---

### Post by cortman on 2012-02-21
Hi, I've used this method to install a number of programs and it worked perfectly every time.
Use whatever works best for you; if you prefer Keryx, don't let this hold you back. This is my program that suits my needs well, and if it works for anyone else, I'm happy.

---

### Post by elliotn on 2012-03-02
wassail.exe works great but not every time as it needs .Net and I found many Windows users don't even know what it is.....we need something that won't require any installation of a dependent ...

---

### Post by cortman on 2012-03-02
> **elliotn said:**
> wassail.exe works great but not every time as it needs .Net and I found many Windows users don't even know what it is.....we need something that won't require any installation of a dependent ...

I agree that would be fantastic, but I don't know enough C to write a dependent-less binary. If you're good at C then by all means get the source code and rewrite it.

There's a link both in this tutorial and on the Sourcforge wiki to MS's .Net framework download site, so if you are on an online computer, it should be a snap to download and install it.

---

### Post by elliotn on 2012-03-03
> **cortman said:**
> I agree that would be fantastic, but I don't know enough C to write a dependent-less binary. If you're good at C then by all means get the source code and rewrite it.

There's a link both in this tutorial and on the Sourcforge wiki to MS's .Net framework download site, so if you are on an online computer, it should be a snap to download and install it.

unfortunately I am not a programmer but hope someone will come through

---

### Post by cortman on 2012-03-03
Yes. In the meantime, I really wish Keryx would become easier to install/use. I really think that is the real "killer app" of offline installation if only it would install more simply.

---

### Post by tea for one on 2012-07-03
Good evening

@ cortman 

I read your tutorial with interest and tried your utility for the first time today. I must say that it is impressive.

Your instructions were concise and and I successfully created a synaptic script for installing Wine.

I took the script to my Windows 7 PC at work and easily downloaded all the .deb files (22 in my case - approx 112MB).

I took the .deb files home, followed the remainder of your tutorial and the Wine software successfully installed.

Just for fun, because I do not have any Windows software at home, I tested it with Portable Apps on a USB stick [http://portableapps.com/](http://portableapps.com/) and it opened start.exe perfectly.

Congratulations on producing a piece of software that I'm sure will be helpful to many Ubuntu users.

As a matter of interest, Bodhi Linux also have a system where you can download applications on a connected machine and then take them to an un-connected pc. Their files are in a format called ???.bod e.g firefox.bod.

I suspect that each file includes all the dependencies for the relevant application?

Kind regards

---

### Post by cortman on 2012-07-03
Hi tea for one,

Thanks very much for the kind words- I'm glad the program worked for you! It's probably a duplication of effort, and as elliotn pointed out, not perfect, but it scratched an itch for me, and I'm glad it did for you too.

+1 for Bodhi Linux- I run it on my netbook. I'm usually able to get the netbook online, so I've never used the .bod packages but I understand they're specifically tailored for offline use- a brilliant and really, really handy feature.

Regards

---

