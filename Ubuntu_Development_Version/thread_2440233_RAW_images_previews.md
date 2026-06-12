---
title: "RAW images previews"
date: 2020-04-07
forum: Ubuntu Development Version
---

### Post by jimbuntu1968 on 2020-04-07
Hi all,
Not sure if this is the right section of the forum so please move if not.
Currently running the 20.04 Beta and I'm having an issue with previews of RAW image files, in this case from a Sony camera. My collection of RAW images are currently stored on a NAS and when I open the folder containing them on the NAS i get no previews and also if i paste them into a folder on the local drive still no previews. In the previous LTS previews were available both locally and on the NAS using ufraw and gnome-rawthumbnailer I believe it was. These packages are not in the archive since I believe 19.10 and after searching online I came across this post [https://gist.github.com/h4cc/13450db3d4a7457f9b38](https://gist.github.com/h4cc/13450db3d4a7457f9b38) but the solution on there doesn't seem to work for me. I have various different distro's on different hardware and have managed to solve this issue on some of them, Fedora Gnome needed a couple of packages as did Manjaro Gnome (the packages were in the repos), Manjaro KDE needed a systemd-automount for the network share. I have tried the mounting in fstab method and also installed every package I could find to do with raw or thumbnail but no joy I'm afraid. Really loving the whole look and feel of 20.04 even in the beta but just wish I could solve this one issue, if I could just get the thumbnails on a local drive it wouldn't be perfect but would be workable. Any help would be much appreciated.
Thanks
James

---

### Post by slickymaster on 2020-04-08
Thread moved to **Ubuntu Development Version** for a better fit

---

### Post by corradoventu on 2020-04-08
In Ubuntu 20.04 if you search for 'ufraw' in synaptic you find 'darktable' and you can install darktable using gnome-sofware where you find both snap and .deb versions.

---

### Post by jimbuntu1968 on 2020-04-08
Thanks for the reply. I have installed darktable as you suggested. 
I still only get a preview of the particular file that is highlighted in the list, unless I maybe import the whole folder but that seems rather overkill if I just want to work on one image. 
The perfect outcome would be to have previews of the images on the NAS in the file manager so I can just import whichever image it is I wish to work on, do any editing that's required and then save back to the NAS.
I'm guessing ufraw-batch and gnome-raw-thumbnailer are no longer maintained hence removal from the repo?

---

### Post by Frogs Hair on 2020-04-09
[COLOR=#000000]Gnome-raw-thumbnailer has Bionic release, but no Focal release.


[/COLOR][https://launchpad.net/ubuntu/+source/gnome-raw-thumbnailer](https://launchpad.net/ubuntu/+source/gnome-raw-thumbnailer)[COLOR=#000000]
[/COLOR]

---

### Post by corradoventu on 2020-04-09
I hope it will work: [https://bugs.launchpad.net/ubuntu/+source/gnome-raw-thumbnailer/+bug/1871862](https://bugs.launchpad.net/ubuntu/+source/gnome-raw-thumbnailer/+bug/1871862)
if you have a launchpad account please subscribe

---

### Post by jimbuntu1968 on 2020-04-09
So if I was to install Bionic and then ufraw as I think that is all that is needed for previews what will happen if I then do an apt dist-upgrade to Focal? Excuse my ignorance I’ve don’t done a dist-upgrade before when I have been dependant on one particular package. If that package is no longer in the repo is it removed during the upgrade process or will it be retained?

> **corradoventu said:**
> I hope it will work: [https://bugs.launchpad.net/ubuntu/+source/gnome-raw-thumbnailer/+bug/1871862](https://bugs.launchpad.net/ubuntu/+source/gnome-raw-thumbnailer/+bug/1871862)
if you have a launchpad account please subscribe
Having re-read the post linked in my original posting it would seem that maybe ufraw-batch is more useful than gnome-raw-thumbnailer? 
Is it possible that could be added to 20.04 too? 
You'll have to again forgive my ignorance in this, I've never found myself being dependant on a package before now, digital photography is a fairly recent undertaking.

---

### Post by corradoventu on 2020-04-09
If you open your folder with gthumb (in 20.04 repository) you have the thumbnails of RAW pictures.
Edit: tested with RAW created by Nikon D5100

---

### Post by jimbuntu1968 on 2020-04-09
I'm just doing a fresh install of 18.04, going to try and get things working there and then do a dist-upgrade and see what happens. Depending on that I will do a fresh 20.04 install and try gthumb

Progress report, fresh install of 18.04.4 with ufraw and gnome-raw-thumbnailer installed, I have thumbnail previews of RAW images on both my local disk and on the NAS.
Now to do a dist upgrade and see what happens.

Upgraded to 19.10 first, at the end it was going to remove obsolete packages including ufraw and gnome-raw-thumbnailer. I didn't agree to the removal and still have thumbnails. 
Then upgraded to 20.04, agreed to package removal this time as ufraw and gnome-raw thumbnailer were not on the list.
Both these packages are still install and I still have thumbnail previews so I guess a level of success but it feels a bit dirty. 
Going to try a live image of 20.04 and gthumb and see what gives

So using 20.04 live image and gthumb I can see previews of the RAW files, though rather slowly compared to 18.04 with ufraw and gnome-raw-thumbnailer. 
I imagine a number of people will have this issue when they upgrade from 18.04 to 20.04 and allow the upgrade process to remove obsolete packages, I may be reading it wrong but feels a little unsatisfactory especially when it was working so sweetly :(

---

### Post by sshapiro632 on 2020-04-22
I am using nufraw with Manjaro. It creates raw images very quickly. Maybe it can be compiled to work with Ubuntu.

---

### Post by mc4man on 2020-04-23
> **sshapiro632 said:**
> I am using nufraw with Manjaro. It creates raw images very quickly. Maybe it can be compiled to work with Ubuntu.
Available here for 20.04, never tried, have no use case ...
[https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=focal](https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=focal)

---

### Post by sshapiro632 on 2020-04-23
> **mc4man said:**
> Available here for 20.04, never tried, have no use case ...
[https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=focal](https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=focal)

If looks like nufraw did not build correctly for 20.04.

---

### Post by mc4man on 2020-04-23
> **sshapiro632 said:**
> If looks like nufraw did not build correctly for 20.04.

Yeah, didn't notice. It's on a dependency wait that will not get resolved. (libgtkimageview
There are ways around that, I guess someone could even ppa it with a bit of 'sleigh of hand"  but not really worth it probably.

Did see way to package build locally, again no idea if the app will work. If someone genuinely interested will describe how to do..

```
~/Desktop/nuraw/test1$ ls -1 |grep .de
gimp-nufraw_0.43.3~focal_amd64.deb
gimp-nufraw-dbgsym_0.43.3~focal_amd64.ddeb
nufraw_0.43.3~focal_amd64.deb
nufraw-batch_0.43.3~focal_amd64.deb
nufraw-batch-dbgsym_0.43.3~focal_amd64.ddeb
nufraw-dbgsym_0.43.3~focal_amd64.ddeb
```

---

### Post by sshapiro632 on 2020-04-27
> **mc4man said:**
> Yeah, didn't notice. It's on a dependency wait that will not get resolved. (libgtkimageview
There are ways around that, I guess someone could even ppa it with a bit of 'sleigh of hand"  but not really worth it probably.

Did see way to package build locally, again no idea if the app will work. If someone genuinely interested will describe how to do..

```
~/Desktop/nuraw/test1$ ls -1 |grep .de
gimp-nufraw_0.43.3~focal_amd64.deb
gimp-nufraw-dbgsym_0.43.3~focal_amd64.ddeb
nufraw_0.43.3~focal_amd64.deb
nufraw-batch_0.43.3~focal_amd64.deb
nufraw-batch-dbgsym_0.43.3~focal_amd64.ddeb
nufraw-dbgsym_0.43.3~focal_amd64.ddeb
```

It's too bad that nufraw is not well-supported with Ubuntu 20.04. Nufraw does a great job on Manjaro; it builds thumbnails very quickly and I have not run into any errors (my raw files are Fujifilm RAFs). Being able to see thumbnails with the Files program is very useful. It seems Ubuntu is going to rely on raw editors for viewing thumbnails.

---

### Post by slickymaster on 2020-04-27
20.04 has been released. Thread closed.

Please start a new thread in the [https://ubuntuforums.org/forumdisplay.php?f=334](https://ubuntuforums.org/forumdisplay.php?f=334) sub-forum

---

