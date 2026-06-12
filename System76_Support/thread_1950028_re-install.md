---
title: "re-install"
date: 2012-03-31
forum: System76 Support
---

### Post by m90benaiah on 2012-03-31
If I wanted to wipe my Lemur and reinstall Ubuntu, how do I do that. Downloaded some programs that I can't get off and the Lemur is freezing a lot.

---

### Post by WasMeHere on 2012-03-31
Hi m90benaiah,

It is straight-forward to install, if you are simply going to overwrite the whole drive. Just boot from the install CD or USB drive and follow the simplest path suggested.

But if you have some partition, that you want to keep, another OS or maybe a /home partition, you must be more careful, and select 'something else' when asked how to manage the partitions. In that case select the partition you want to wipe/overwrite, and make it the root file system of Ubuntu, /

Do you have a swap partition? In that case, I suggest that you reuse it.

Good luck :-)
Olle

---

### Post by m90benaiah on 2012-03-31
> **Olle Wiklund said:**
> Hi m90benaiah,

It is straight-forward to install, if you are simply going to overwrite the whole drive. Just boot from the install CD or USB drive and follow the simplest path suggested.

But if you have some partition, that you want to keep, another OS or maybe a /home partition, you must be more careful, and select 'something else' when asked how to manage the partitions. In that case select the partition you want to wipe/overwrite, and make it the root file system of Ubuntu, /

Do you have a swap partition? In that case, I suggest that you reuse it.

Good luck :-)
Olle
The laptop didn't come with a cd so I nothing to boot with. Then would I just download it from the website?

---

### Post by WasMeHere on 2012-03-31
> **m90benaiah said:**
> The laptop didn't come with a cd so I nothing to boot with. Then would I just download it from the website?
You can download the iso-files of one or more of the Ubuntu flavours. Then make an install CD or USB drive from each iso file and test it live (boot from the CD/USB drive) without installing.

- Ubuntu  - Unity, fancy and demanding desktop environment
- Kubuntu - KDE, fancy and demanding desktop environment
- Xubuntu - XFCE, nice and light-weight desktop environment
- Lubuntu - LXDE, fast and ultra-light desktop environment

After testing, select the flavour to install :-)

If you post the specs of your computer (cpu, ram, graphics chip), we can suggest what might work well, if you don't want to test it yourself.

---

### Post by m90benaiah on 2012-03-31
> **Olle Wiklund said:**
> You can download the iso-files of one or more of the Ubuntu flavours. Then make an install CD or USB drive from each iso file and test it live (boot from the CD/USB drive) without installing.

- Ubuntu  - Unity, fancy and demanding desktop environment
- Kubuntu - KDE, fancy and demanding desktop environment
- Xubuntu - XFCE, nice and light-weight desktop environment
- Lubuntu - LXDE, fast and ultra-light desktop environment

After testing, select the flavour to install :-)

If you post the specs of your computer (cpu, ram, graphics chip), we can suggest what might work well, if you don't want to test it yourself.
Thanks for the info; here is what I know about it: memory 3.8 GiB, Processor Intel Core i5-2450M CPU @ 2.50GHzx4, OS typte 64-bit, Disk 488.4 GB. I don't know if this helps, I'm really quite the beginner in all this, here is a link to what I ordered from system76: [https://www.system76.com/laptops/model/lemur](https://www.system76.com/laptops/model/lemur)

---

### Post by ubuntu27 on 2012-04-01
I believe you can run Ubuntu fine. You can choose any [flavors of Ubuntu]("http://www.psychocats.net/ubuntu/whichbuntu") you want.

[See also: [KDE and Gnome Comparison]("http://www.psychocats.net/ubuntu/kdegnome").  Not up to date]


Soon a new version of Ubuntu is going to be released, so perhaps you might want to wait a little. The new version will be released almost at the end of April.

I am running the development version now, and I feel that it is stable. The mileage might vary depending on your hardware, software, and perhaps even luck (if you believe in that).

If you want to have the current version of Ubuntu:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)


If you want to install the developmental version of Ubuntu that is going to be the new Ubuntu 12.04:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


Once you install the developmental version of Ubuntu Precise Pangolin, you don't need to reinstall Ubuntu once the final version comes out. Simply update normally, and you will be up to date.




Whatever your choice, once you install (K/X/L)Ubuntu, you should install your System76 Driver for your model. You can download it from their website.

---

### Post by WasMeHere on 2012-04-01
> **ubuntu27 said:**
> I believe you can run Ubuntu fine. You can choose any [flavors of Ubuntu]("http://www.psychocats.net/ubuntu/whichbuntu") you want.
...
+1 :KS

I agree with *ubuntu27*, with your hardware you can run fancy and demanding desktop environments if you want.

---

### Post by m90benaiah on 2012-04-01
> **ubuntu27 said:**
> I believe you can run Ubuntu fine. You can choose any [flavors of Ubuntu]("http://www.psychocats.net/ubuntu/whichbuntu") you want.

[See also: [KDE and Gnome Comparison]("http://www.psychocats.net/ubuntu/kdegnome").  Not up to date]


Soon a new version of Ubuntu is going to be released, so perhaps you might want to wait a little. The new version will be released almost at the end of April.

I am running the development version now, and I feel that it is stable. The mileage might vary depending on your hardware, software, and perhaps even luck (if you believe in that).

If you want to have the current version of Ubuntu:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)


If you want to install the developmental version of Ubuntu that is going to be the new Ubuntu 12.04:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


Once you install the developmental version of Ubuntu Precise Pangolin, you don't need to reinstall Ubuntu once the final version comes out. Simply update normally, and you will be up to date.




Whatever your choice, once you install (K/X/L)Ubuntu, you should install your System76 Driver for your model. You can download it from their website.
When I hit the button to burn after a few seconds (reads, creating image checksum) the disk ejects with an error.

---

### Post by m90benaiah on 2012-04-01
It reads; Error while burning, the drive is busy. Can anyone help me with this?

---

### Post by ubuntu27 on 2012-04-02
Which iso image were you trying to burn? And with what program and version?

---

### Post by WasMeHere on 2012-04-02
> **m90benaiah said:**
> It reads; Error while burning, the drive is busy. Can anyone help me with this?

- You might have a checksum error. That means that something went wrong when downloading the image. You can find the md5sum via the internet and compare it to the output of the command
```
md5sum filename.iso
```
If you let us know which version and flavour of Ubuntu you are trying to install, we can help you find the md5sum.

- Use a program where you can set the burning speed manually, and burn with lowest possible speed. That method has helped me several times. Otherwise, maybe you can borrow a computer with a good CD/DVD writing drive.

- Or are you trying to burn an oversized iso file (but I guess you have a DVD writer, not only a CD writer)

---

### Post by m90benaiah on 2012-04-02
> **Olle Wiklund said:**
> - You might have a checksum error. That means that something went wrong when downloading the image. You can find the md5sum via the internet and compare it to the output of the command
```
md5sum filename.iso
```
If you let us know which version and flavour of Ubuntu you are trying to install, we can help you find the md5sum.

- Use a program where you can set the burning speed manually, and burn with lowest possible speed. That method has helped me several times. Otherwise, maybe you can borrow a computer with a good CD/DVD writing drive.

- Or are you trying to burn an oversized iso file (but I guess you have a DVD writer, not only a CD writer)
Thanks for the info and this morning I did exactly that. I used my other laptop, burned Ubuntu 11.10 and then installed it back on. So, everything is a good for now. Thanks for the help and information, appreciate it.

---

### Post by WasMeHere on 2012-04-02
> **m90benaiah said:**
> Thanks for the info and this morning I did exactly that. I used my other laptop, burned Ubuntu 11.10 and then installed it back on. So, everything is a good for now. Thanks for the help and information, appreciate it.
I'm glad Ubuntu works for you now :KS

Please click on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page and mark this thread as SOLVED

---

