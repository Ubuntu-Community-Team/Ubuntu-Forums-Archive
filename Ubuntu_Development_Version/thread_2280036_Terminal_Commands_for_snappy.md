---
title: "Terminal Commands for snappy??"
date: 2015-05-27
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-05-27
This may not be the best choice for posting this here but I'm confident if it is not it will be moved.
As with any new OS DE sometimes command line is the only preferred method (Speaking for myself) of achieving success in installing package's or getting things done Etc. Etc. So in the spirit of sharing.
Here are a limited few that I have found in hopes others will also share!

Install new software from package repository.
```
sudo snappy install <your package here>
```
Update existing software.
```
sudo snappy update
```
Remove unwanted software.
```
sudo snappy remove <your pkg here>
```
Update system.
```
sudo snappy update
```
Search by package name.
```
sudo snappy search <your pkg here>
```
List installed packages.
```
sudo snappy list
```

I have yet to find a command for adding an outside repository or chanel or PPA.
And I found this just today.
[https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/](https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/)
Best Regards:D

---

### Post by Cavsfan on 2015-05-27
Is snappy new to Wiley and it seems to be a replacement for apt-get right? (dumb question :P)

I just installed it and there is no man page for it.

---

### Post by Cavsfan on 2015-05-27
Never mind. I installed it and tried sudo snappy update and it gave me errors and nothing else so I purged that and libclutter-gst-1.0-0 which it also installed.

---

### Post by deadflowr on 2015-05-27
It erred because you installed snappy the media player package.

---

### Post by QDR06VV9 on 2015-05-27
> **Cavsfan said:**
> Is snappy new to Wiley and it seems to be a replacement for apt-get right? (dumb question :P)
Nope but still under development, and yes a replacement for apt-get and there are NO Dumb Questions just Dumb answers:p

> **Cavsfan said:**
> Never mind. I installed it and tried sudo snappy update and it gave me errors and nothing else so I purged that and libclutter-gst-1.0-0 which it also installed.
I guess you already seen deadflowr post.
Kind Regards

---

### Post by ventrical on 2015-05-27
@runrickus
This is the place :)because that is about all there is right now with snappy.  I have the image on a USB and the kvm version and it works very well.... :)

regards..

---

### Post by QDR06VV9 on 2015-05-28
> **ventrical said:**
> @runrickus
This is the place :)because that is about all there is right now with snappy.  I have the image on a USB and the kvm version and it works very well.... :)

regards..
I Did the USB thing also!:D
Thanks Vent is this something you will add to your sticky(Commonly used sudo commands)Just asking?
No Pressure from me.
Kind Regards

---

### Post by Cavsfan on 2015-05-28
> **deadflowr said:**
> It erred because you installed snappy the media player package.

Yep, I guess that would explain it. :p

---

### Post by ventrical on 2015-05-29
> **runrickus said:**
> I Did the USB thing also!:D
Thanks Vent is this something you will add to your sticky(Commonly used sudo commands)Just asking?
No Pressure from me.
Kind Regards

It's already covered at - [https://wiki.ubuntu.com/U+1/library#Useful_Links_on_Snappy_How_Tos](https://wiki.ubuntu.com/U+1/library#Useful_Links_on_Snappy_How_Tos)

but probably more to come ! :)

regards..

---

### Post by QDR06VV9 on 2015-05-29
> **ventrical said:**
> It's already covered at - [https://wiki.ubuntu.com/U+1/library#Useful_Links_on_Snappy_How_Tos](https://wiki.ubuntu.com/U+1/library#Useful_Links_on_Snappy_How_Tos)

but probably more to come ! :)

regards..
Thank You!:D You and grahmmechanical, elfy, cariboo, zika and others do a lot we here in this forum just take for granted!
So here is my Thanks to you all:popcorn:

---

### Post by Cavsfan on 2015-05-30
> **ventrical said:**
> It's already covered at - [https://wiki.ubuntu.com/U+1/library#Useful_Links_on_Snappy_How_Tos](https://wiki.ubuntu.com/U+1/library#Useful_Links_on_Snappy_How_Tos)

but probably more to come ! :)

regards..

I tried to add the ppa and it got errors. It added a ppa with wiley-dev in it and the ppa is apparently named devel.

I tried to modify the name in SPM but bungled that also so I purged it.

[http://ppa.launchpad.net/snappy-dev/beta/ubuntu/dists/devel/main/](http://ppa.launchpad.net/snappy-dev/beta/ubuntu/dists/devel/main/)

Could you please fix the ppa in this part [https://developer.ubuntu.com/en/snappy/start/](https://developer.ubuntu.com/en/snappy/start/)

For those of us that are a bit slow.

---

### Post by ventrical on 2015-05-30
> **Cavsfan said:**
> I tried to add the ppa and it got errors. It added a ppa with wiley-dev in it and the ppa is apparently named devel.

I tried to modify the name in SPM but bungled that also so I purged it.

[http://ppa.launchpad.net/snappy-dev/beta/ubuntu/dists/devel/main/](http://ppa.launchpad.net/snappy-dev/beta/ubuntu/dists/devel/main/)

Could you please fix the ppa in this part [https://developer.ubuntu.com/en/snappy/start/](https://developer.ubuntu.com/en/snappy/start/)

For those of us that are a bit slow.

You started in the wrong area on that page. Please see screenshot below. That's where I started. We at the wiki did not create that webpage. You chose developers tools. It was inserted in the Library as part of the general install and into to snappy testing and install.

Regards..

---

### Post by Cavsfan on 2015-05-30
> **ventrical said:**
> You started in the wrong area on that page. Please see screenshot below. That's where I started. We at the wiki did not create that webpage. You chose developers tools. It was inserted in the Library as part of the general install and into to snappy testing and install.

Regards..

Oh thanks for the clarification. I'll just see what happens later. We're not even to the alpha stage yet.

Regards.

---

