---
title: "How do i run GIMPshop?"
date: 2009-05-05
forum: Ubuntu Studio
---

### Post by Macfunky on 2009-05-05
Just downloaded GIMPshop to see what it is like. I downloaded a .deb package and installed it using GDebi. Now i don't know where to open it up. Its not in my menu and i don't know what to type to run the application. Anyone able to help?

Also since installing it Gimp has stopped opening up. I'm assuming thats cause its conflicting with the GIMPshop install. How do i go about uninstalling GIMPshop if i want to go back to Gimp? Its not showing up in synaptic package manager

---

### Post by lukeiamyourfather on 2009-05-05
Was the GIMPshop package made specifically for Ubuntu? If not that's probably what did the damage. Remove the package for GIMPshop and reinstall GIMP from the Ubuntu repositories. If you really want to use GIMPshop then compile it from source or find a package specifically made for Ubuntu (not Debian). Cheers!

---

### Post by Macfunky on 2009-05-05
It was a .deb file so i assumed it was compatible with ubuntu. So how do i uninstall it when i dont know where it is?

---

### Post by cotcot on 2009-05-05
Gimp and gimpshop are not compatible on the same system. You need to remove gimp if you want to install gimpshop.
Gimpshop is outdated (based on gimp 2.2) compared to gimp 2.6.

---

### Post by Macfunky on 2009-05-06
I have uninstalled gimp now and i have figured out how to get gimpshop running. I imaged the command would have been gimpshop but it is just gimp. If i want to go back to gimp how do i remove gimpshop? Can i remove it just knowing the command?

---

### Post by lukeiamyourfather on 2009-05-06
Remove Debian packages by using dpkg.

```
sudo dpkg -r whatever-package-you-want
```

You'll probably have to reinstall GIMP after removing the package if you still want to use GIMP. Cheers!

---

### Post by Macfunky on 2009-05-06
Tried that. Got the following message  

dpkg - warning: ignoring request to remove gimp, only the config
 files of which are on the system.  Use --purge to remove them too.

---

### Post by wabbalee on 2009-05-14
Interesting; using Jaunty I have installed the gimpshop.deb package with kpackagekit, no errors. to run it I have to type 'gimp' in a terminal. then the first use wizard for gimp2.2 shows up and when finished it shows the old gimp2.2 interface, not gimpshop unfortunately. I can run gimp2.6 simultanenously. I have not done all what is described [here]("http://linux.suramya.com/tutorials/Install_GIMPShop/") so I guess that is most likely the reason why it is not working for me.

I uninstalled gimpshop through synaptic, where it shows up if you click on the 'status' button under 'installed (local or obsolete)', without problems.

I am going to give it another try, I think there is a good chance it will work alongside existing gimp2.6 install. Installing the .deb was no problem but I did not install the other requirements, none seem to appear in synaptic so it looks like I am in for a bit of cli fiddling.

---

### Post by iroy2000 on 2010-05-19
I'm using 10.04 and I download the gimpshop deb package.  It works fine for me.

After you installed, go to terminal and type

gimp

If it is your first time installed, it will do the installation for you.

---

