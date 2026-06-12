---
title: "Folder permission and groups"
date: 2009-10-01
forum: Server Platforms
---

### Post by Flarkis on 2009-10-01
Ok my problem is fairly simple. I am setting up a home server and want to have a samba share, a transmission daemon, and a mldonkey daemon running. Ideally the files downloaded by mldonkey or transmission would be put in a folder that can be read and edited via samba on another computer.

The samba share its self is located at /srv/samba/share/flarkis/. Transmission is set to download files to /srv/samba/share/flarkis/Downloads. To make the samba shares writable i had to "chmod 0755 /srv/samba", than to get transmission to be able to save files in that directory i had to set the folder owner ship to the transmission daemon "chown debian-transmission -R /srv/samba/share". Now everything is working in a manner, but if a file is saves in the Downloads folder it can only be read and not deleted.

Can anybody think of an elegant solution to this problem?

Many thanks

---

### Post by Flarkis on 2009-10-02
doing a little more research i found that the files in the samba share are owned by flarkis:flarkis by default, and files created by transmission are owned by debian-transmission:debian-transmission.

Adding flarkis to the debian-transmission group and adding debian transmission to the flarkis group didn't help the problem.

---

### Post by Flarkis on 2009-10-02
I eventually gave up the nice interface of transmission to do everything by mldonkey. No problems yet. Thanks to anybody who bothered to read this thread.

---

### Post by ConXtionS on 2009-10-02
I read bro, but I was not smart enough to say a word
 
 
glad you got it working tho
 
Jim

---

### Post by Vegan on 2009-10-02
I created some new folders and assigned them to nobody:nogroup and samba likes this fine as I told it to force user/force group so that I could use it like a simple Windows share.

I am safe behind a hardware firewall.

---

### Post by Flarkis on 2009-10-02
@Vegan
My problem was more with the permissions being set on files by transmission that made them unmodifiable under a samba share.

---

### Post by isaidi on 2009-10-08
you can set the UMASK for all files downloaded by Transmission as required in the 

```

/etc/transmission/settings.json file

```

be sure ot stop transmission first before editing file, then start it
```

/etc/init.d/transmission stop

```

details on options in the settings file are here
[http://trac.transmissionbt.com/wiki/EditConfigFiles](http://trac.transmissionbt.com/wiki/EditConfigFiles)

see UMASK

---

### Post by abdusamed on 2009-12-13
WANT GROUPS IN TRANSMISSION !! in UBUNTU 9.04!! ktorrent and deluge CRASH! im am so ANNOYED!

when can't the transmission for mac be the same as the LINUX!??

how do i get groups?

---

### Post by isaidi on 2009-12-13
> **abdusamed said:**
> WANT GROUPS IN TRANSMISSION !! in UBUNTU 9.04!! ktorrent and deluge CRASH! im am so ANNOYED!

when can't the transmission for mac be the same as the LINUX!??

how do i get groups?

MAC Transmission not the same.

Get the new Transmission 1.75 on Ubuntu 9.10 , it has a few new features, but groups not one of them..  I believe Ubuntu 9.04 only has Transmission 1.51..

---

### Post by Charles Kerr on 2009-12-13
> **abdusamed said:**
> WANT GROUPS IN TRANSMISSION !! in UBUNTU 9.04!! ktorrent and deluge CRASH! im am so ANNOYED!

when can't the transmission for mac be the same as the LINUX!??

Because we don't have enough developers on Transmission.  The person who works on the Mac GUI works *only* on the Mac GUI, but the person who work on the GTK+ client (me) also spends a lot of time working on libtransmission and transmission-daemon.

I'd love to see groups or tags implemented for Transmission's non-Mac clients.  It will get done a lot faster if someone submits a patch.  The ticket for this is [http://trac.transmissionbt.com/ticket/2175](http://trac.transmissionbt.com/ticket/2175) and it has the early stages of a patch, but needs a lot of work.

---

