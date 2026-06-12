---
title: "Trying to give my server a little omp!"
date: 2010-08-30
forum: Server Platforms
---

### Post by JD32 on 2010-08-30
So i decided to set up a old laptop of mine to act as a server for my various desktops and laptops around the house. Its just an old HP laptop with a 1GB Pentium and like 512MB RAM, Nothing special. It only has a 40GB HDD so i connected a 1TB & 2TB externals drives to store my movies/music.  

I have the server connected to the router with a cable and when i pull from it from my laptop via wireless (which is only 10ft away) i only get about ~700KB transfer. Is this about all i can expect or should i be getting more? i can pull from my desktop to the server, which is connected with a wire, at about ~8-9 MB. But from server to desktop still is only a max of 2MB

Anyone no how i can speed up my transfers? I was thinking that pulling from a external drive through (im guessing its only USB 1) and then through the network is slowing it down??? Or is this the best that particular setup will ever achieve. 

PS- Would running the actual server edition of Ubuntu help? just curious

---

### Post by msandoy on 2010-08-30
There is a couple of things here, first it seems you are using SMB, witch is a slow protocol. I would go for FTP or NFS. USB1 will slow things down conciderably, try to transfer a file from the local HD to compare, some old laptops had both USB 1 and 2, so try another usb port on the laptop. Wireless is generally slow, and will sometimes become unstable at prolonged high load. Running server edition would reduce the load on your CPU, but I doubt it will give you any increase in network performance. When you install a server service on a desktop system, it is the same server service used in the server edition.
Hope this answers some of your questions.

---

### Post by JD32 on 2010-08-30
Will FTP or NFS still work with windows?

---

### Post by arrrghhh on 2010-08-30
FTP will easily.  NFS... not so much.  I believe there are some tools, but NFS is not native to Windows.  Usually best (eaiset) to use Samba with Windows, and NFS with Unix/Linux clients.

msandoy made a good point about USB1&2... if those external drives are running on USB1, it's going to be very slow.

He also made a very good point about wired vs wireless connections - you also may want to ensure the wired connection is going at 100mbps as opposed to 10mbps.

---

### Post by JD32 on 2010-08-30
So how do i go about switching to FTP? 

I think im pretty much stuck with USB 1 though, you cant really drop a PCI card into a laptop can ya?

The HDD's support esata which would really help but no port on the box, anyway i could that hooked up?

---

### Post by msandoy on 2010-08-30
Well, the easy way of installing ftp would be to just install GADMIN-PROFTPD from the repositories. It gives you a fairly easy GUI for setting up ftp. It will not speed up USB 1 connection, but you should be able to get up around 12 MB/sec on a wired 100Mb line. Easy connection from a windows box is done by entering the following in the location bar of your file browser:
ftp:\\username@192.168.1.10 substitute what is needed. choose remember password, and bookmark the location when the page is loaded. A bookmark can be placed on the desktop for easy access. It's quite similar in Ubuntu too. same procedure, and make a bookmark in Nautilus.

---

### Post by arrrghhh on 2010-08-31
> **JD32 said:**
> So how do i go about switching to FTP? 

I think im pretty much stuck with USB 1 though, you cant really drop a PCI card into a laptop can ya?

The HDD's support esata which would really help but no port on the box, anyway i could that hooked up?

I wouldn't recommend FTP for a LAN.  NFS/SMB are what I recommend on the LAN.  FTP/SFTP is more for WAN transfers.

Now there's nothing keeping you from doing it... I just usually don't recommend it.

You can put what's called a 'PCMCIA' card in the laptop that adds e-SATA or USB2.  However, you may be better off putting your money into a new rig - new hardware is cheap, save a couple hundred bucks and build yourself a dedicated server :D

---

### Post by JD32 on 2010-08-31
> **arrrghhh said:**
> I wouldn't recommend FTP for a LAN.  NFS/SMB are what I recommend on the LAN.  FTP/SFTP is more for WAN transfers.

Now there's nothing keeping you from doing it... I just usually don't recommend it.

You can put what's called a 'PCMCIA' card in the laptop that adds e-SATA or USB2.  However, you may be better off putting your money into a new rig - new hardware is cheap, save a couple hundred bucks and build yourself a dedicated server :D


Will wireless transfer to my laptops is what im gonna be doing most. My desktops even wirless because it so far away from my modem and router.

But ya saving up to build a better rig is what im leaning towards.

---

