---
title: "experience on installation of ubuntu 8.10 on vaio"
date: 2008-12-28
forum: Testimonials &amp; Experiences
---

### Post by ndefontenay on 2008-12-28
Hi all,

My girlfriend after using ubuntu on my desktop for a long time now and liking it asked me to install it on her laptop too.

It has been managed pretty well and she was ready to move after we went to a shop and bought a 320 GB external disk to backup all her important data and song.

We tried booting from the usb key I created but it wouldn't boot. It turns out there's no USB boot in the Vaio (a pretty old one).

After burning the ISO on a CD, she installed it all by herself up to the reboot.

Getting the concept of install programs from the repository (add/remove) was a breeze.

She has noticed that some of her song bought on itunes wouldn't even show. She was a bit pissed off by that first but decided that it's not normal that she is not allowed to play them on the OS she chose and is now resolved to get them for free (we are in Thailand and it's not like she didn't pay for it).

Quite surprisingly, the wireless connection and file sharing between 2 ubuntu machines is NOT EASY!

These are 2 things which we will really have to improve to reach the masses.

When a folder is shared, it should be available in Places>Network and we should then be able to mount it to some places say in /media/mysharedfolder

2nd the wireless is not very smooth either. Haven't managed to go around that yet. For now she is connecting with a LAN cable at my place.

I know there are how tos and documents on how to get wireless and file sharing working but my point is that it's not easy.

Wireless and file sharing should be as easy as install ubuntu on a machine. If it takes a wizard to install wireless or a file sharing then so be it but there's not even that!

OK. To finish this post on a good vibe: I now have a linux PC, a linux laptop and a macbook pro and 0 windows :)

---

### Post by WiFi Ed on 2008-12-29
> **ndefontenay said:**
> 
She has noticed that some of her song bought on itunes wouldn't even show. She was a bit pissed off by that first but decided that it's not normal that she is not allowed to play them on the OS she chose and is now resolved to get them for free (we are in Thailand and it's not like she didn't pay for it).

Apple doesn't much care which OS she chose, Apple just insists that any "protected" files downloaded from the iTunes store are played only on an "authorized" computer or device. Since iTunes only works on Windows or Mac operating systems, that does limit choices somewhat.

You could always burn an audio cd of the protected files (in Windows or OSX) and then rip the cd into your Ubuntu installation. That's how I get my "protected" iTunes files into my Ubuntu...

---

### Post by MaxIBoy on 2008-12-29
Save yourself the CD, write them to a disk image instead.

---

### Post by ndefontenay on 2008-12-29
Hi.

Can you develop a bit on the ISO part?

Do you mean all I got to do is create an ISO of the itunes mp3 and somehow it turns into DRM free music?

How can I create an ISO on linux?

I don't see the option on Brasero.

---

### Post by sigurnjak on 2008-12-29
sudo dd if=/dev/sdb of=/home/yourusername/xp.dd

get your  itunes and :guitar:enjoy!

or

mkisofs -o $ISO_FILENAME.iso $DIRECTORY to make image from directory

or you can install acetone iso and create iso from a file via gui
[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

---

### Post by Bölvaður on 2008-12-29
Everything is easy on linux if you know beforehand what you are doing, which is a shame because then you have to at least having to struggle once.

File sharing is very simple. The idea behind NFS sharing folders is like this:

Computer1 allows the ip of the Computer2 to connect to some directory on Computer1.
When Computer2 needs to connect to Computer1 she mounts it with 1 command.


For making it easy to use you can have both computers as "servers" and "clients" allowing all ips from within the house.

To mount the folder you use full paths with parameters like if it would be a normal harddiskdrive and either have the mount command as a script in a luncher (on the panel [lunchers are called shortcuts in win]) or have it auto mount at boot.

This is much safer than windows shares as you control who has access to what, and are able to forbid incoming connections from the outside world.
All you need is to download the NFS server and client tools... well Im not sure if they are default on or not but it shouldn't be too difficult for  you.



About wireless. You can blame the company that made that card for not supplying (proper) linux drivers, as that is how the problem sounds. It will be a struggle using OS on unsupported hardware (until they make those drivers) because the company that made that hardware are apparently just bunch of tos.. wait I think Im not allowed to say that word.
There is a way to use the windows wireless drivers on linux (just to let you know what to google for in the future).


btw the trick about burning protected iso files to audiotrack is that when it is burned it gets converted to form of .wav that is stored on cds. From there you can convert them to what ever you want.

---

### Post by ndefontenay on 2008-12-29
Hi.

For the wireless drivers, I know. It's like the modems in the past before adsl and it prevented me from using linux back then when it was red hat 7.2 and debian ruling.

But we have to keep going because every laptop we install, every time we go through the pain of setting up a new PC/laptop, there's a new user and as the user base grows, they will ultimately think of building drivers for wireless.

Even so, installing ndiswrapper and find the driver online was piece of cake. I just hate the idea that I have a piece of windows running on my linux box!

---

For the itunes songs, would converting them to wav on linux by selecting them get rid of the DRM? Because when I burn an ISO of the mp3s thanks to sigurnjak below, all I get is an iso of drm mp3s right?

---

For file sharing, yeah true enough, maybe it's my learning curve and my given idea that a shared file should be seen by the world...

I still think that we should have some basic sharing mechanism such as the dropbox on OSX. 

Ubuntu is linux for the masses and the masses should use as little command line as possible. At least at the beginning when a command line is so dreadful.

When I think of features, I always imagine people like my dad or my girlfriend, full of emotions and not born with a brain working like an algorithm.

I've tried NFS already. It worked alright on the server side. It kind of failed on the client side with an "NFS internal error", nothing more and I got a bit disappointed after that... But I'm hardcore linux so not to worry, but what about someone else?

Here's what I think it should look like:

1) On the server side which we will call "computer/person who wants to share a file or folder", it's fairly easy, I right click on my folder, choose sharing option. If it's the first time it downloads NFS but... not nfs-common and not nfs-server... Isn't that weird? Most likely it generates a Samba entry. It could do the same for NFS, or we could have a choice! Also there's the concept of allowing a client to connect. That is really important because it gives security, so what about the ability of inputting a list of IPs, or network range like in firefox for proxy exceptions?

2) On the client side, ok fair enough, we don't want the world to see that there's a shared folder but then why don't I have an NFS option when I go to Places->"Connect to Server" which could give me a new graphical interface when I pick "Connect to a shared folder". The person would then enter the IP address or host name (She chose Bliss as a computer name and it's way easier than 192.168.1.3 which could change since it's dynamic...), would also enter the file location on the host and the mount point which could be created if it doesn't exist yet. An option to auto mount on start up would be given by ticking a box. And voila!

Right now it's all command line, maybe easy when someone grasp the concepts but they need the will to learn and that's not a given...

There's way to go for file sharing on linux.

---

### Post by WiFi Ed on 2008-12-30
> **ndefontenay said:**
> For the itunes songs, would converting them to wav on linux by selecting them get rid of the DRM? Because when I burn an ISO of the mp3s thanks to sigurnjak below, all I get is an iso of drm mp3s right?

If you burn an audio CD from within iTunes from your protected files (*.m4p types), the resulting audio CD will not have any Digital Rights Management protection and then can be ripped into regular *.mp3 format (or any other format you like) and played on any device.

---

