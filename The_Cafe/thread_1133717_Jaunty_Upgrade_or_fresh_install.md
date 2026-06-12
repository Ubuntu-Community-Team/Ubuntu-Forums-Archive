---
title: "Jaunty Upgrade or fresh install?"
date: 2009-04-23
forum: The Cafe
---

### Post by kneewax on 2009-04-23
I am sure others have asked this before, but as releases get better the answers may change!

With the imminent arrival of Jaunty what is the recommended upgrade path?  Do you allow the upgrade to run within Intrepid using synaptic?  Or is it best to download ISOs and do a fresh install of the new version?

When I went from Gutsy to Hardy with my i386 system I had no problems using synaptic, but the same system had real issues when I did the same from Hary to Intrepid.

Now I have my shiny new Intrepid x64 machine running as I like it I don't know what the best course of action is Upgrade, fresh install or just hold those horses and wait a week or two for Jaunty to settle down....?

---

### Post by tatw on 2009-04-23
Now im using rc with update-manager

---

### Post by Eddie Wilson on 2009-04-23
Most of the time I do an upgrade but I've gotten some new hardware so I'll be doing a fresh install for the 64 bit distribution. I'm sure it will work out great.

---

### Post by Thelasko on 2009-04-23
In theory, if you have a separate /home partition, a fresh install should be very easy.  I've never tried it as I'm still using Hardy.  The only problem with this is that you won't be able to use ext4 on your /home partition.

---

### Post by Slim Odds on 2009-04-23
What about the option of using the alternate install CD?

---

### Post by Zyrshnikashnu on 2009-04-23
One of each. My laptop is a mess of old configurations, so I'm backing up my files (not my configs) and starting over.

I just built my desktop a couple months ago, though, so I figure it'll transition to 9.04 without too much trouble.

---

### Post by ptemple on 2009-04-23
Fresh install. I made the mistake of doing the upgrade and first all the graphics drivers died. No matter what mode I booted into I couldn't get any kind of display. Then I did ctrl-alt-f4 to get into a virtual terminal and did apt-get upgrade to finish the installation. Result is that booting didn't even recognised the fs. Using the LiveCD to painstaking comb through the drive and ensure I haven't missed backing anything up, and then will do fresh re-install. What a shame.

Phillip.

---

### Post by GOwin on 2009-04-23
> **Thelasko said:**
> In theory, if you have a separate /home partition, a fresh install should be very easy.  I've never tried it as I'm still using Hardy.  The only problem with this is that you won't be able to use ext4 on your /home partition.

It *sounds* easy, yes, but when you have a number of applications installed this just sounds like theory.

---

### Post by Arup on 2009-04-23
Best way is to fresh install but if you wish to upgrade do so via apt-p2p as explained in the post by ubuntu-geek at [http://www.ubuntugeek.com/how-to-use-apt-p2p-for-faster-upgrades-from-ubuntu-intrepid-810-to-jaunty-904.html](http://www.ubuntugeek.com/how-to-use-apt-p2p-for-faster-upgrades-from-ubuntu-intrepid-810-to-jaunty-904.html)

Even for downloading the disto, P2P is the only way.

---

### Post by Tweak42 on 2009-04-24
I did upgrade from 8.04 to 8.10 unscathed but lost my sound when doing upgrade to 9.04 RC.  Tried to fix it but just gave up and did a clean install to 9.04 from CD.  Everything seems to be working like before so far.:-)

---

### Post by jzalomon on 2009-04-24
I was using 9.04 beta for a couple of weeks...and loved it...backed up all my files and i just did a fresh install 0% problems...working fine...faster and lighter...keep up the good work...i would you always for a fresh install..download the ISO and voula!:guitar:

---

### Post by jespdj on 2009-04-24
I see it as a good opportunity to cleanup my system, so I'll backup important data and do a fresh install.

---

### Post by Thelasko on 2009-04-24
> **GOwin said:**
> It *sounds* easy, yes, but when you have a number of applications installed this just sounds like theory.

*In theory* you can save a list of your installed packages with synaptic and load it again after install.

If you didn't notice, I'm one of the few that isn't upgrading.

---

### Post by Slim Odds on 2009-04-24
> **Thelasko said:**
> *In theory* you can save a list of your installed packages with synaptic and load it again after install.
```
dpkg --get-selections 
```will give you a list of everything that's installed

---

### Post by Thelasko on 2009-04-24
> **Slim Odds said:**
> ```
dpkg --get-selections 
```will give you a list of everything that's installed

Thanks, I use the GUI method.  In synaptic I think it's under the file menu.  My only concern is, will it work from version to version? (i.e. Intrepid to Jaunty)

---

### Post by billgoldberg on 2009-04-24
A clean install is always better.

---

### Post by RedSquirrel on 2009-04-24
I prefer the clean install. I have a separate /home partition so I just drop the Ubuntu installer kernel and initrd on there and modify grub.conf/menu.lst to boot it.

---

### Post by NightwishFan on 2009-04-24
My data is on a separate partition, so I will do a clean install. I mount my Documents, Music, etc folders as a link in the new installations home folder.

---

### Post by Thelasko on 2009-04-24
> **NightwishFan said:**
> My data is on a separate partition, so I will do a clean install. I mount my Documents, Music, etc folders as a link in the new installations home folder.

I attempted that once, and had some problems.  I think it was because my other partition wasn't mounted on boot.

---

### Post by NightwishFan on 2009-04-24
> **Thelasko said:**
> I attempted that once, and had some problems.  I think it was because my other partition wasn't mounted on boot.

Use manual partitioning when you install, and choose the mount point for the data partition as something.

I use /mnt/backup

If you set the type in ubiquity to the correct filesystem, and do not check format, it will automatically mount it for you. If you do not have permissions on the folder, then run:

```
sudo chown -R username /mnt/backup
```

Then simply middle click your folders, and create links in your home in place of the default folders. Also finally in GNOME 2.26 they do not use "link to Documents" and just "Documents", which is great.

---

### Post by Slim Odds on 2009-04-24
> **billgoldberg said:**
> A clean install is always better.

Depends on what you mean by 'better'.

If better means easier, then an upgrade is the answer.

If better means cleaner, then a fresh install is superior.

I've done both and it all depends. I have some machines that I updated from 6.06 -> 6.10 -> 7.04 -> 7.10 -> 8.04 and had no issues.

---

### Post by pbhj on 2009-04-24
I [upgraded to jaunty and despite some errors]("http://alicious.com/2009/ubuntu-upgrade-intrepid-to-jaunty/") haven't really had any problems (even now I've rebooted).

It does appear that flash is missing in FF, but then that may have only been the FF update and if that is really the only issue then I'd have to say .. best .. update .. evar !

---

### Post by CraigPaleo on 2009-04-24
I upgraded from Hardy to Intrepid but have done a fresh install of Jaunty because I wanted to try out ext4. Otherwise, I would have upgraded. 

Upgrading preserved everything I'd done to get things working properly. After doing a fresh install of Jaunty, I remembered to install the restricted extras but flash had no sound. I'd forgotten to install flashplugin-nonfree-extrasound. Since I've done that, all has been well and fine with sound in Flash. 

Also, it took me a bit to remember how I'd gotten Frostwire to work. I had to download Sun's Java. I wish I'd kept a log of everything I'd done in Hardy. 

I'd say, upgrade if you want to stay with your current file system or don't have a separate home partition. Otherwise, do a clean install. 

Oh, and my back-ups of Firefox and Evolution were not completely intact. It was probably my ignorance but my emails were there in Evolution but I had to recreate my gmail account. Firefox didn't remember my bookmarks or cookies even though I renamed the backed up Firefox folder to match the newly installed one. 

It took me 5 DVDs to back everything up. As it was my first time, I probably went about it the wrong way. Everything was fine exept for some preferences is all.

---

### Post by gn2 on 2009-04-24
If I was going to install, it would be a clean install to new partitions after backing up needed files to my NAS.

But I won't be installing it, instead I will be sticking with 8.04.

---

### Post by dark_phantom on 2009-04-27
Depends on a few things, but for my laptop I did a fresh install to clean it up.

---

### Post by calrogman on 2009-04-27
A bit of a mix.  I downloaded the iso, burnt it to a CD, deleted all my configuration files/directories in ~/, then ran the installer.

When it got to the partitioner I made it format / (as Ext4) and not format /home (so  it keeps my personal stuff and creates configuration stuff).  By far the least likely method of upgrading to cause problems.

---

### Post by aaaantoine on 2009-04-27
I'm gonna have to do a fresh install -- on my USB drive.

The reason being that when you upgrade packages on a persistent Live USB, it stores the updated files in your persistent space.  And it takes a lot of space just to upgrade packages, let alone running a dist-upgrade.

---

