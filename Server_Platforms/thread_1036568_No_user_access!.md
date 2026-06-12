---
title: "No user access!"
date: 2009-01-10
forum: Server Platforms
---

### Post by adlabens on 2009-01-10
This is driving me crazy, NUTS I tell ya!

Ubuntu Server 8.10 with Samba 3.2.3.  I've got a RAID5 array mounted that contains nothing but data, and my OS is on it's own, dedicated HDD (I can pull it out & replace it within 60 seconds, leaving the data intact).  It's a dedicated box doing nothing but file serving - AT LEAST THAT'S WHAT IT'S SUPPOSED TO DO!!!

The server is in the same workgroup as my two WinXP Pro boxes, and I can SEE it in the Windows Explorer.  But, I can't get access to the share.  I can PuTTY into it and get access to everything.  I have created my users in both Linux and Samba, with the same UID & PW as used when logging in to the XP boxes.  When I click on the share in Windows Explorer, it asks for my password with the dialog box:

[IMG]http://www.readycashhomebuyers.com/Linux/ConPwDlg.jpg[/IMG]

But it won't let me get past that.

I'll be glad to post any info, any file contents or output.  Tell me what you want & I'll be glad to make it happen.  

This thing has just about fried my brain.  I've spent the past week trying to get over this hump, and almost all day today constantly hacking at it to see what will make it work.  I'm convinced it's something so simple that I'll want to shoot myself when it's fixed.  (The blood that's running down my chin is from me bitting my tongue trying not to curse at this thing.)

Thanks,
David

---

### Post by linux_tech on 2009-01-11
To clarify you are trying to access a ubuntu share from windows box and are unable to login to access the share.  You have samba installed and are using smb. 

 I'm not sure what you have done to configure samba. So first I would make sure you have samba setup correctly
here are a few guides-

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-samba-configuring.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-samba-configuring.html)
[http://www.novell.com/documentation/opensuse102/index.html?page=/documentation/opensuse102/opensuse102_reference/data/sec_samba_serv_inst.html](http://www.novell.com/documentation/opensuse102/index.html?page=/documentation/opensuse102/opensuse102_reference/data/sec_samba_serv_inst.html)

you can also use swat to do the samba configuration for you
[http://humanreadable.nfshost.com/sdeg/enabling_swat.htm](http://humanreadable.nfshost.com/sdeg/enabling_swat.htm)

---

### Post by adlabens on 2009-01-11
I've a little bit of new information:

All 3 computers are in the workgroup RCH-WORKGROUP, the server's name is RCH-SERVER, my computer is named RCH-DAVID, and April's computer is RCH-APRIL.

I have created the users "david" & "april" exactly the same way, but they act differently.  "april" is able to log into the server, but "david" is not.  Neither is able to browse the share.  This is just from either the PuTTY console or from the actual server box keyboard at the  login prompt.

I have, apparently, failed to create the users correctly - in LINUX - before I ever get to Samba, and I've failed to give them proper permissions.

I can see the share, when logged in as root (sudo su) and executing "smbclient -L localhost": 
```

Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (RCH-SERVER server (File & Print Server))
        DATA            Disk      Network-Data
        print$          Disk      Printer Drivers
Domain=[RCH-SERVER] OS=[Unix] Server=[Samba 3.2.3]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        RCH-WORKGROUP        RCH-APRIL

```
So, it appears that the users are not propery setup in Linux (which trumps Samba), which indicates that my first task should be to get them setup in Linux properly so that they can login and access the share when working FROM the Linux keyboard or from PuTTY.  I think I have to figure that out first.

-> David

---

### Post by adlabens on 2009-01-11
Working strictly in Linux (not even GETTING to Samba yet), I've tried to add the user "david" - here's the dialog:

```

root@RCH-SERVER:/home/admiral# users
**[COLOR="Red"]admiral april[/COLOR]**
root@RCH-SERVER:/home/admiral# useradd -g users -p password  david
useradd: **[COLOR="red"]user david exists[/COLOR]**
root@RCH-SERVER:/home/admiral# usermod -g users -p password  david
root@RCH-SERVER:/home/admiral# users
**[COLOR="red"]admiral april[/COLOR]**

```

So, what in the programmer's world is going on?

I'm rebooting the server to see if that makes any diff.

---

### Post by adlabens on 2009-01-11
I've rebooted the server, and still can't login as david

So, I've done
```

root@RCH-SERVER:/home# userdel david
root@RCH-SERVER:/home# useradd -d /home/david -p password -s /bin/bash -g users -G admin david

```
& I still can't login as david

```

login as: david
david@192.168.2.5's password:
Access denied

```

So, I'm going to delete the user, reboot the server, add the user, & see what happens there.  

Am I missing something here?

---

### Post by adlabens on 2009-01-11
I have been entering the password as one of the parameters in the useradd command.  It has apparently failed, thus preventing user "david" from logging in.  I tried the passwd command, entered the password, and am now able to login, and it shows "david" as a response to the users command.

Another baby step taken!

---

### Post by Iowan on 2009-01-11
Progress is progress - I hate it when every step takes you further from target... I've had days like that.

---

### Post by adlabens on 2009-01-11
Well, this one is solved.  I had a heck of a day with this - actually, a heck of a month trying to make it work.  Now, I can do the install consistently and have it work consistently.  

For $35.00 each, I had bought a couple of extra 80 GB SATA3 drives.  So, today has been an experiment in perserverance, as well as installation procedures.  I finally got one to work.  

To do that, I tried to uninstall Samba and the delete the contents of the /etc/samba folder.  That was a mistake because it wouldn't install Samba again after that.  SO, I was forced to wipe out the HDD and start again.  

No problem, I just swapped the cable over to the other OS HDD I had attached inside the machine.  This time, I had my own documentation to follow, and did the job as simply as possible, using some notes I'd collected from others in response to other topics on several forums.  It took about 3 hours to do the whole thing - mostly because I was tweaking my documentation as I went along.  It worked, but I had installed some unneeded stuff in an effort to make it easier (like SWAT, which I never could make work).  

Sometimes, the easiest solutions are the obvious ones that are not as obvious when you start as they are when you finish!  

So, I got it working and had complete access to the server stored data files from both XP boxes.  

Shut her down, swap the cable, and do another from-scratch install.  This one took about 2 hours, because I was tweaking the documentation still, but without attempting to install "helper" stuff like SWAT.  No mistakes & it was working perfectly.  

So, I swapped the cable again, back to the other drive that was working but had had other unneeded stuff installed, and I wiped that HDD clean and did a completely new install.  That one took only about 90 minutes - still with some documentation tweaks, but not much.  I could probably have done it in 1 hour if I was only following the documentation I'd made & not verifying and tweaking.  

At that point, I had two exact same 80 GB HDDs with Ubuntu Server 8.10 installed and working with my RAID5 array and providing both users access to all the files.  So, I shut her down and swapped the cable and she booted up and gave me complete access just like I had been using that HDD the entire time.  No remounting the RAID, no setting up users again, no nothing - just flawless execution.  

So, now I'm confident that I can make it happen at will.  And, with the documentation I've got, I can do it again in 3-5 years without having to worry whether I'm able to remember the stuff, and especially without having to take several weeks to make it happen!

If you, or anyone, is/are interested, my documentation is [here]("http://www.readycashhomebuyers.com/Linux/Ubuntu%208.10%20Server%20-%20Disaster%20Recovery%20Guide%2001.doc").  There are a few things to note about the documentation.  
[LIST]
[*]It mentions Webmin.  I did not like Webmin, instead opting to use the CLI.  So, Webmin is mentioned at the beginning of the document, but is not included in the instructions.  
[*]Also, it mentions that the Disaster Recovery Document is for both replacement of the OS HDD as well as repairing the RAID5 array.  I've only been able to mess with getting the OS HDD replaced and haven't yet addressed how to repair a failure of one of the drives in the RAID5 array.  I've got some other stuff to handle first, like establishing reliable backups, before I start screwing around with the integrity of my data storage system (that should make sense to just about anyone with any brains).  
[/LIST]So, for now, the Disaster Recovery Document only addresses replacing the OS HDD, but I know the instructions are correct and that it'll work now as well as in the future after I've long forgotten what I've learned!

I'm a happy camper now!

Time for a beer!

---

