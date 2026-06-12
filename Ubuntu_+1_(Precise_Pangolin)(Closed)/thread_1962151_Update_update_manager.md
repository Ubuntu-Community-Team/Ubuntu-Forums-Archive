---
title: "Update update manager"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by geomcd1949 on 2012-04-20
I have 11.10 installed. The Update Manager does not list the 12.04 beta for upgrading. In Settings > Updates, I've checked both "Pre-released updates" and "Unsupported updates" (and re-started). But no notice that 12.04 can be downloaded. Any suggestions? Thanks.

---

### Post by for.i.am.root on 2012-04-20
Still in beta, but

sudo apt-get dist-upgrade

For development it's

sudo do-release-upgrade -d

---

### Post by philinux on 2012-04-20
Make sure your system is fully updated first.

If you want a gui upgrade using update manager then use the command below from a terminal.

```
update-manager -d
```

---

### Post by for.i.am.root on 2012-04-20
I'm addicted to cli and forget that most prefer a GUI. Follow his advice. Much easier.

Thanks philinux!

---

### Post by philinux on 2012-04-20
> **for.i.am.root said:**
> I'm addicted to cli and forget that most prefer a GUI. Follow his advice. Much easier.

Thanks philinux!

My suggestion would not work on a server so it's good to have choices. :p

The OP has to choose now !

---

### Post by tmaranets on 2012-04-20
I feel like i am going to wait for the actual release instead of trying the code.

---

### Post by philinux on 2012-04-20
> **tmaranets said:**
> I feel like i am going to wait for the actual release instead of trying the code.

I did a clean install as that is my method. I have home on it's own partition so I blew away all the .config folders except firefox and backed up evolution.

I find the upgrade process takes ages compared to a clean install.

---

### Post by Mathor on 2012-04-20
> **tmaranets said:**
> I feel like i am going to wait for the actual release instead of trying the code.

Or try an iso :biggrin:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by arpanaut on 2012-04-20
When 12.04 is released you will not need to run that code as Update Manager will present that option to you at that time.
If you have the correct settings in your Software Sources, under the Update tab.

@philinux  You are correct, It can be glacial in execution!

---

### Post by Frogs Hair on 2012-04-20
Thanks for the synaptic hint. I have been waiting for the gnome shell update in the update manager. For some reason I was able to complete the update with synaptic while the update manager reported a partial upgrade .

---

### Post by geomcd1949 on 2012-04-20
No joy.

Using update-manager -d in the terminal opens the Update Manager, which still doesn't list 12.04 as an option.

Using sudo apt-get dist-upgrade yields:
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

I AM connected to the Internet, and System Info confirms I currently have 11.10.

---

### Post by tekstr1der on 2012-04-20
> **geomcd1949 said:**
> I have 11.10 installed. The Update Manager does not list the 12.04 beta for upgrading. In Settings > Updates, I've checked both "Pre-released updates" and "Unsupported updates" (and re-started). But no notice that 12.04 can be downloaded. Any suggestions? Thanks.

I'm sure you've already checked this but... on that same tab in the Software Sources dialog, is the dropdown option set to the default:
> 
Notify me of a new Ubuntu Version: **For any new version**

If it's set to "Never", you'll not receive the distribution upgrade notice.

After changing this option, you'll need to run

```
update-manager -d
```

to be prompted for the 12.04 upgrade.

---

### Post by geomcd1949 on 2012-04-20
Checked for updates using Update Manager, with Settings > using both "For any new version" and "For long-term support versions." In either setting, when I click "Check" for updates, I get a box with a red circle saying "Failed to download repository information. Check your internet connection." [Internet is connected and working.]

Details  [in the popup] reads:

"W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64  (20110427)/dists/natty/Release  Unable to find expected entry  'main/binary-i386/Packages' in Release file (Wrong sources.list entry or  malformed file) 
, E:Some index files failed to download. They have been ignored, or old  ones used instead."

I tried searching for updates using Update manager both with and without the 11.04 CD in the laptop. [I upgraded to 11.10 after using the CD to install 11.04.]

Help is greatly appreciated.

---

### Post by geomcd1949 on 2012-04-20
Tekstr,

Ran the terminal code [update-manager -d] , and this time the Update Manager gave the option to upgrade to 12.04 (beta).

Thanks everybody!

~George


Gaakkhhh! Now, when downloading 12.04 using Update manager, I get the same error message:

"W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64   (20110427)/dists/natty/Release  Unable to find expected entry   'main/binary-i386/Packages' in Release file (Wrong sources.list entry or   malformed file) 
, E:Some index files failed to download. They have been ignored, or old  ones used instead."

I'm just going to burn a CD and run that.

Thanks.

---

