---
title: "Transfer Wine Directory to Hard Another Hard drive"
date: 2010-02-15
forum: Wine
---

### Post by boo12345679 on 2010-02-15
I want to transfer an entire wine directory from my 8.04LTS Ubuntu to my 9.10 hard drive.    Basically I am upgrading my harddrive and Ubuntu installation .

I have MS Office installed on the 8.04 version and works perfectly.   I want a clean install of 9.10 and so I have purchased a new hard drive, a bit bigger and installed 9.10 on it.  I will use the old hard drive for storage

My question is that on my new hard drive that I have 9.10 can I just copy the relevant directory from 8.04 version to my 9.10 version ?  

The MS Office is a licensed version and requires internet authentication, which I have done on the 8.04 LTS version (so it works without restrictions).  What I am concerned about is that if I uninstall MS OFFice  from 8.04LTS version evil Microsoft may not register the uninstallation and then wont allow me to install MS Office on the new 9.10 version without the purchase of a new license.  Something Im don't want to do as I only have one laptop. 

Also Im not sure of what directory to copy ? Does anyone know ?

I know how to copy all my personal data, and it works like really well as Ive done this before.  What I have not done is the transfer of the wine directory. 

Thank you.

---

### Post by dino99 on 2010-02-15
you are right when you want a clean install, it's always better.
So, clean install for 9.10, clean install for wine (take it from wine ppa for the latest), add your backup work you have previously done.

I think that if you give to your new wine installation, all the same names for directories, folders and subfolders, existing into the old wine, wine should work as well. If it complaint, recreate some links (ln -s ...) or direct click on your apps.

---

### Post by boo12345679 on 2010-02-15
Thanks for that.  But what I was looking for is how to transfer the ms office application from my old wine folder to the new wine folder and what the relevant folders are that I need to move ?

---

### Post by dino99 on 2010-02-15
Wine is a windows like system, so you need to reinstall MS apps, or better, why are you not using Openoffice instead ?

---

### Post by boo12345679 on 2010-02-15
> **dino99 said:**
> Wine is a windows like system, so you need to reinstall MS apps, or better, why are you not using Openoffice instead ?

Thanks again.  I have open office but having used excel for 15 years its a difficult move.  I am using the same laptop with exactly the same spec so would that make a difference ?  

Also does anyone know if I uninstall the MS Office apps from wine does evil Microsoft know about this ?  I need them to acknowledge that the product has been uninstalled and therefore I can then use the same license to reinstall ?

Has anyone tried this out or is it a matter of basic knowledge that reinstall is required ?  As for Linux apps you dont need to reinstall - just moving the files to the normal place is sufficient.

Where are the wine directories on the system kept ? is it in /etc ? are there multiple wine directories ?

---

### Post by Mocker on 2010-02-15
I've had few problems when installing a new Ubuntu or other distro with just copying the .wine directory over. You do sometimes run into issues with newer versions of Wine breaking previously working applications, but that can happen even if you'e installing them from scratch. I've never had so many issues that I've had to ditch my entire set of installed applications and start from scratch.

My advice: yes, you can just copy your .wine directory and give it a shot. The worst that can happen is that the applications won't work, and you'll need to delete the .wine directory (or just the directory and settings for the applications that don't work) and reinstall. The time spent copying over the files is small compared to the time it would take you to reinstall a bunch of applications, so you have little to lose. 

The only other annoyance is that you lose the program menu entries that Wine will create when you install a new application, but you can pretty easily recreate these. I just create application launchers on the desktop that run wine with the windows path of the program I want to start (i.e. wine "C:\Program Files\My Application\MyApp.exe").

---

### Post by ttn13 on 2010-02-16
It's worth a try. I've been transferring wine installation with Office 2007 among three PCs without any problems. You may also need to copy the ~/.local/applications since wine places application mines there (I guess).

---

