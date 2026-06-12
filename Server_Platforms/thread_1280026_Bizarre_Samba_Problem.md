---
title: "Bizarre Samba Problem"
date: 2009-10-01
forum: Server Platforms
---

### Post by mjohns930 on 2009-10-01
I have recently set up a little mini itx server using this board ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359)) to be used mainly for backups of my main desktop and a media streamer for my PS3. I initially had it set up running 9.04 desktop 32 bit. I set up samba via this tutorial ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) and tried to connect to it from my desktop running Win7 RC. 

I was able to connect to it from the windows machine but when I tried a file transfer of about 5GB of mp3's from the server to the desktop it would get anywhere from 1/3 - 3/4's of the way done and then just stop and disconnect. I tried various fixes such as redoing my smb.conf and even reinstalling Ubuntu but nothing helped. I ruled out my network hardware (Linksys WRT310N router) and resorted to reinstalling Ubuntu on the server.

I set everything up fresh including the smb.conf. Still it did the same as it did before. I tried my old smb.conf and the same thing. I was convinced the issue was with Windows 7.

I pulled out a spare hard drive and installed Vista on it and updated it and tried connecting to my share and transferring the same ~5GB of mp3's. It worked! So I moved back to Vista as my main OS and it continued to work. Until....

Now several days ago I decided to make the jump to Ubuntu 64bit server. I set up only samba to begin with using my old smb.conf and sure enough it is doing the same as it had before and disconnecting from the share midway through the transfer to my windows machine. I once again set up samba from scratch and still the same problem. 

Here is my smb.conf:

```
[global]
    ; General server settings
    netbios name = server
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[stuff]
    path = /home/mitch/stuff
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0777
    directory mask = 0777
    force user = mitch
    force group = mitch
```

I am at a complete loss as to what the problem might be. I don't even know if it is with my server or my desktop. I am going to attempt to try a fresh install of Vista on a spare hard drive and see if it works again. But if that works I have no idea why it wouldn't work on my current install. 

Any samba gurus have any ideas?

Thanks for the help.

Mitch

---

### Post by openfly on 2009-10-02
I'd suggest ensuring there aren't any weird power saving options enabled on either side of the equation.

Also I'd be concerned about network failures... something like very large packets or fragmented packets can really mess up some gear if not handled properly.

beyond that is there anything in any of the samba logs?  do you have verbose logging enabled?

---

### Post by HDave on 2009-10-02
I hate to say this, but I have had intermittent problems copying either a few huge files (movies at 8GB each) or many smaller files.  Seems it can't get beyond 5-15GB before it hangs.

After extensive Googling, I found many people with this problem...and absolutely no solution.

Sorry for this no-help, depressing post....

---

### Post by mjohns930 on 2009-10-02
Thanks for the replies.

openfly:

I have made sure that nothing at all has anything that has to do with power saving turned on at this point in time. That was one of my first thoughts.

Now you are referring to network failures. Do you mean like my router dying? Or possibly the NIC's on my computers failing?

I had it set up to log to the syslog but I have since turned that off and set it up to log for each computer that tries to connect to it. I set it up to look like this:

```
    syslog = 0
#   syslog only = no

    log file = /var/log/samba/log.%m
    max log size = 1000
    log level = 3
```

So I am going to try the transfers again a few more times and then see what I get in the log file and post it back here.

HDave:

That is very depressing, but I find it difficult to believe that a piece of software that seems to work in high demand business oriented situations won't work in low demand consumer type situations.



Now one other thing I forgot to mention in my first post. When the share disconnects from my desktop, I can't access the server at all through SSH until I reboot it (I SSH into it from my laptop running Ubuntu as well). If I reboot it then I can access it again.

Does anyone think it could possibly be something to do with my router's built in switch? It is a gigabit switch but obviously it is consumer grade and may not be able to handle this type of traffic. Although I find that hard to believe. :confused: 

The part that still throws me for a loop is that when I did several clean installs of Vista, it worked every time correctly until this last reinstall of Ubuntu on the server.

I will post back with some log files here in the next couple days and see if there is anything in there to help.

Also if you see anything in my smb.conf that may need to be changed to help such as the logging please let me know.

Thanks.

Mitch

---

### Post by openfly on 2009-10-02
Samba doesn't actually see all that much deployment in large scale business environments.  Contrary to what the liniban turrorists might want you to believe.  And I've seen some pretty queer behavior out of it with environments of 100 users or more.

But, what I meant with networking issues was this... 

Networks can be fairly complex.  A lot more complex than hey let me plug my cable into this switch and it automagically knows how to get my tcp ip from point a to point b.  With consumer end chipsets and network gear sometimes they don't invest the time in ensuring the complete stability and robust handling of the protocols inherit in providing a network link.

Lots of switches even big industrial iron have issues with large file transfers if not configured properly.  This has to do with the size of packets being transferred.  Sometimes they get just a little too big for the hardware to take apart properly... and that's when either the hardware chokes.. or you start breaking up the packets into smaller chunks... this would be packet fragmentation.  Handling of fragmented packets, and choking on large packets are both possible points of failures in switches... as is the possibility of the issue being related to buffers being too full too long on the device.

Have you tried connecting directly to the samba server and running the transfer over a crossover cable?

That would ensure that the problem is not related to any routing / switching gear in between.

hrmm files over 4 gigs used to play hell on windows.  I wonder if it's something related to that... I mean samba isn't exactly state of the art, they implement windows networking about 4-5 years behind the curve... sometimes that means there are some limitations so to speak.  Still you'd think it'd end up in the logs if it was a samba issue...

I mean I'd almost suggest bouncing the samba daemon through strace... or smbclient through strace and giving it a go.

Which reminds me...

Does this fail linux to linux?  or just linux to windows?

If at the end of the samba proves to be a failure... there's always openafs =/  (god help you)  or maybe some form of software iscsi.

---

### Post by HDave on 2009-10-02
I have reasonable high-end switches and routers in my home.  I could never get these samba transfer's to happen.  So now I use "scp" and they work just fine.   So I definitely can't blame it on the iron.

Perhaps the OP could try scp (or rsync) to see if it works.  If it does, it's definitely samba.

---

### Post by Vegan on 2009-10-02
I suggest using the default smb.conf and merely append  you shares from that. I do that and keep my iTunes library on the server fine.

---

### Post by mjohns930 on 2009-10-03
HDave:

I would like to stick with samba so I don't have to log into the server to initiate the transfer. I don't have my Windows machine set up with an SSH client so I can't do anything with it from that, it all has to be done with my laptop. 

Rsync is another option, but I want this to be as seamless as possible with Windows so even my wife can work it and get data off the server with little effort.

Vegan:

I have tried that as well, but I still can't make the transfers of the files as I need to. I am capable of accessing the data on the drive and playing it but when the time comes to transfer it, it disconnects.

 



Ok, so I tried an Ubuntu to Ubuntu transfer but it has one catch, I did it on my laptop which only has a 100mb ethernet connection. But it did work. Multiple times it worked with no disconnects. It was slow but it worked. So I tried the same on my Windows computer slowing the network card down to 100mb and once again it worked over and over.

I have not tried a machine to machine transfer without the router yet as that is something I am a bit unsure how to do so the computers have IP addresses and stuff. 

The one thing I would like to try though is to perhaps change the packet size or something that samba sends. Like openfly said, maybe it has something to do with packet size so if I could experiment with that maybe I can find a size that would work without having to slow my network cards down. 

If you go to this link ([http://oreilly.com/catalog/samba/chapter/book/appb_02.html](http://oreilly.com/catalog/samba/chapter/book/appb_02.html)) and scroll down to B.2.2.5 it starts discussing packet sizes and how to change them. If anyone has messed with this let me know if I am on the right track to adjusting these parameters. Or if there is a better way to do it please tell me. I am going to do some messing with the variables it gives and if I get anywhere I will post back with it.

Thanks

Mitch

---

### Post by mjohns930 on 2009-10-10
Ok, so I have tried various settings in the smb.conf from my previous post and nothing changed. It never slowed it down or anything. So I am thinking I am going to try some traffic shaping with iptables...

I have no idea what I am doing with iptables or any other tool to do traffic shaping so now its time to do some research. If/when I figure anything out about this and get it to work I will post back with my progress.

Thanks for all the help.

Mitch

---

