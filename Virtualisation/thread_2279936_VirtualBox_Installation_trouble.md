---
title: "VirtualBox Installation trouble"
date: 2015-05-26
forum: Virtualisation
---

### Post by RobGoss on 2015-05-26
Hello everyone, I wanted to see what Virtualbox was about so I installed it from their website, after doing so when the installation was completed

I noticed there was a few on my icons that were on my dock had changed their colors to blue with  a question mark and I could not locate my terminal. 

I then rebooted my machine to see if things would go back to normal but it's still like that. And my software center is no were to be found along with my side panel.... Is there any way for me to remove Virtualbox at this point?

Thanks so much

---

### Post by papibe on 2015-05-26
Hi robert159.
> **robert159 said:**
> ... I installed it from their website ...
How? Could you tell us the instructions/steps you followed?

Regards.

P.S.:
> **robert159 said:**
> I wanted to see what Virtualbox was about...
I'd recommend installing the version available on the Software Center.

---

### Post by RobGoss on 2015-05-26
> **papibe said:**
> Hi robert159.

How? Could you tell us the instructions/steps you followed?

Regards.

P.S.:

I'd recommend installing the version available on the Software Center.


I downloaded  Vm from their website and installed it that was it and it seem to mess my system up.

---

### Post by papibe on 2015-05-26
Thanks, yet not enough information yet.

What did you download (link)?
Was it a .deb file?
Did you modify your sources too?

How did you install it? Double click, or from the terminal?

Regards.

---

### Post by RobGoss on 2015-05-26
It was a deb.file and I installed it by right clicking and installing it.

I downloaded it from [https://www.virtualbox.org](https://www.virtualbox.org)
it looked safe to me so I installed it.

I had a clone of my system so I able to restore it completely. But to those who want to install VM don't  download it from their website because it will mess up your system.

I did look for VM in the software  center but I was not able to locate it, it might be under a different name.

The worst part about it is my software center dissappeard and so did my terminal so I had no way to remove it.

---

### Post by papibe on 2015-05-26
So, I understand you solved your problem?

If you search for 'Virtualbox' on the software center, you should be able to find it easily (choose the one with the blue icon).

Regards.

---

### Post by oldos2er on 2015-05-26
Moved to Virtualisation.

---

### Post by RobGoss on 2015-05-26
> **papibe said:**
> So, I understand you solved your problem?

If you search for 'Virtualbox' on the software center, you should be able to find it easily (choose the one with the blue icon).

Regards.

Yes I was able to restore my machine using Clonezilla it was my first time using this method worked like a charm. Thank you

---

### Post by SeijiSensei on 2015-05-26
I've installed VirtualBox at least a dozen times by adding the Oracle repositories to my system then using apt-get following the i[nstructions for "Debian-based" systems]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions").  I can't re,ember a time when this method failed to work correctly. As far as I know, the .deb you get this way is the same as the one you would get from downloading it off the website.

VB needs to compile and install a kernel module with dkms.  Did you install that package as well?  Usually it's a dependency of the VB package itself.  If you use apt to install VB, it will download dkms and the build-essential package that are required to compile the module.  I don't know what happens if you just install the .deb file.  I'm sure that if you don't have dkms already installed VB cannot function.

---

### Post by sammiev on 2015-05-26
> **robert159 said:**
> It was a deb.file and I installed it by right clicking and installing it.

I downloaded it from [https://www.virtualbox.org](https://www.virtualbox.org)
it looked safe to me so I installed it.

I had a clone of my system so I able to restore it completely. But to those who want to install VM don't  download it from their website because it will mess up your system.

I did look for VM in the software  center but I was not able to locate it, it might be under a different name.

The worst part about it is my software center dissappeard and so did my terminal so I had no way to remove it.

After reading this I went to the above website and select to download the deb file for the ubuntu version I was using.

Worked perfect with no issues.

The best way to install is from the software center, I just had to try it.

---

### Post by RobGoss on 2015-05-27
Thank you guys so much I don't know what happen with my download but it was not successful at all and very strange.

I managed to locate VB from the software center and proceeded to download it and everything seems to be ok so I don't  know what happen with the previous download. 

I will start downloading software only from the softwares center lessons learned.

---

### Post by SeijiSensei on 2015-05-27
> **sammiev said:**
> The best way to install is from the software center, I just had to try it.
For most applications, most of the time, this is the correct advice.  However I strongly recommend following the instructions I linked above to add the Oracle repository to your system and use that method instead.  The release version of VirtualBox in the [repositories]("http://packages.ubuntu.com/trusty/virtualbox") (4.3.10) does not keep pace with Oracle's releases (currently 4.3.28).  That may be less of an issue these days as VB is more stable.  Still once the repository is added, VirtualBox will be installed and upgraded just like any other package when you run "apt-get install|upgrade".

The Oracle package has a different name, "virtualbox-4.3" at the moment, from the Ubuntu package which is just called "virtualbox."  This avoids any conflicts.  Installing virtualbox-4.3 will automatically remove Ubuntu's version and replace it with Oracle's.

---

### Post by RobGoss on 2015-05-27
How do I add the Oracle repositories to my system?

Thank so much for the tip I will follow it  carefully.

---

### Post by chris382 on 2015-05-27
> **robert159 said:**
> Hello everyone, I wanted to see what Virtualbox was about so I installed it from their website, after doing so when the installation was completed

I noticed there was a few on my icons that were on my dock had changed their colors to blue with  a question mark and I could not locate my terminal. 

I then rebooted my machine to see if things would go back to normal but it's still like that. And my software center is no were to be found along with my side panel.... Is there any way for me to remove Virtualbox at this point?

Thanks so much

The similar situation happened to me and is now resolved. If you don't have access to a terminal try booting into recovery mode and once at the menu with options go ahead and choose resume and it should take you to the login screen. Once at the login try ctrl alt f3 or ctrl alt f1 to get into the terminal . Once inside login with your username and password. Once there enter this command >   ```
[COLOR=#000000] sudo apt-get install --reinstall ubuntu-desktop[/COLOR] 
```
This will bring back terminal as well as the menu and anything that you had lost before and remove virtual box. Don't panic i was in the same situation and it's fixable, we just need to know what's wrong. Most likely it is virtual box so try running the code and it will take it off.

---

### Post by RobGoss on 2015-05-28
Thanks Chris for the tip I wish I had known this but as I stated I just did a restore and all was well and I did Install VB from the software center and it was ok......Thank you and glad you got it fixed

---

