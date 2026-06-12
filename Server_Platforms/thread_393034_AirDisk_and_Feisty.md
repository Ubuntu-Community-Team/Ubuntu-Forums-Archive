---
title: "AirDisk and Feisty"
date: 2007-03-25
forum: Server Platforms
---

### Post by giambrone on 2007-03-25
Hey guys, first post (doubt its even in the right place!),

I've been using Ubuntu for a while now, and only just managed to get my wireless working (I can finally unplug my ethernet!). I was trying to get my computer to see the Apple AirDisk on the network. After installing Avahi Zeroconf etc I've got it to print over bonjour, I'm wondering how to get it to mount the Disk on the network because my entire music collection is on there!!

Any help appreciated...

Matt :):KS :)

---

### Post by huygens on 2007-03-30
I would expect Apple using Samba to share the disk with the rest of the network.
So under Ubuntu, if you go to the menu Places (top-left of your screen after a default install) then choose Network. You should be able to see your AirDisk (no clue what would be the name there, as I do not own one AirPort myself).
Simply double-click on it to view the files. You might need to authenticate, depending how you set it up.

---

### Post by giambrone on 2007-03-31
First off thanks for the reply; been trying different things and still havent got it to work.

In going to ¨Network¨ all that appears is ¨Windows Network¨ - I double click it and it goes to ¨smb:///¨ (samba?) - I know that when I was running windows it appeared as a removable drive formatted for fat32 (even though the mac saw it as HFS+). 

If it required a password to access it would a password box pop up?

Thanks again,

Matt:KS

---

### Post by huygens on 2007-03-31
Yep if a password is required, you will be prompt by Ubuntu for it.
If you do not see it in the network places, then it is maybe not shared via Samba... In which case, I am clueless.
As I do not have one with me, it is difficult to help you further. I will try to look a bit on other forum if I find something...

---

### Post by giambrone on 2007-04-01
Okay, thanks

Matt :KS

---

### Post by huygens on 2007-04-02
Reading the following Apple source: [http://docs.info.apple.com/article.html?artnum=305038](http://docs.info.apple.com/article.html?artnum=305038)
Your airdisk should be accessible via the network (Samba, CIFS or SMB are from a user point of view the same thing).

What you could try is the command line (open a terminal and type the following line)
```
smbclient -L <name or IP of AirPort Extreme>
```You should replace '<name or IP of AirPort Extreme>' by the IP address of your AirPort Extreme or by its hostname. It might request you for a password in which case this would be the password that you set to share your disk.
You should see an output similar to this:
```
Domain=[MyHost] OS=[Unix] Server=[Samba]
        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (MyHost server (Samba, Ubuntu))
        AirDisk         Disk      
        print$          Disk      Printer Drivers
Domain=[MyHost] OS=[Unix] Server=[Samba]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        MyGroup               MyHost

```This would mean that the disk is shared with the name AirDisk (replace this name by what you will find out) in the network group MyGroup (replace this name by what you will find out). So if you go to the menu Places->Network and then open the "Windows Network", you should see the group MyGroup and if you double-click on it, you will see your hard disk :-)
Another solution would be to use the item "Connect to Server..." under the menu Places. You have to choose "Windows share" for the service type. the Server would be the IP or hostname of your AirPort Extreme. The share would be the name of the shared disk (above was AirDisk, but replace by what you have found out). You *could* leave "Folder", "User name" and "Domain name" blank. Finally the last field is the name you want to give to this connection, so you could give AirDisk for example :-)

---

### Post by MikeMay on 2007-04-06
So its no problem to mount a harddrive on an AirPort Extreme with Linux?
Do I get this right?

---

### Post by huygens on 2007-04-08
> **MikeMay said:**
> So its no problem to mount a harddrive on an AirPort Extreme with Linux?
Do I get this right?
It should yes because the hard drive is shared via SMB/CIFS (according to Apple documentation), but you should wait for a confirmation of giambrone as I do not own such a device.

---

### Post by giambrone on 2007-04-09
Ok guys, I've tried it and it works to the extent that it mounts. After I open the folder it is blank - I don't know why because theres about 80GB of media on there - Any ideas??

Here's what happens when I enter [FONT="System"]smbclient -L 10.0.1.1[/FONT] in the terminal...
> Domain=[WORKGROUP] OS=[Wasabi Certified BSD] Server=[NQ 4.30]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       
        320GB           Disk      
session request to 10.0.1.1 failed (Call returned zero bytes (EOF))
session request to 10 failed (Call returned zero bytes (EOF))
Domain=[WORKGROUP] OS=[Wasabi Certified BSD] Server=[NQ 4.30]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


Thanks,

Matt :KS

---

### Post by huygens on 2007-04-10
Now if you try this:
```
[FONT=System]smbclient //10.0.1.1/320GB[/FONT]
```Note: if you need to use a specific user name to connect to your box, try this instead:
```
[FONT=System]smbclient //10.0.1.1/320GB -U username[/FONT]
```You should then be connected much like with an FTP client. So you can do 'ls' to list all files and directories, 'cd' to change to another directory, 'put' to upload files, 'get' to download files and 'quit' to exit.
Does it works?

If it does, then you should try again by going to the Gnome menu called Places and then Connect to server. You then select[LIST]
[*]Service type: "Windows share"
[*]Server: 10.0.1.1
[*]Share: 320GB
[*]Folder: *leave it empty*
[*]Username: *specify it if needed*
[*]Domain name: *leave it empty*
[*]Name to use for the connection: *give what ever name you like :-) like AirDisk*[/LIST]As for the failed session request.... I would leave them for now. I have no clue what they mean. Let's first try how it works with the above, and we will see later :-)

---

### Post by giambrone on 2007-04-10
OK, thanks - I have a bit of a problem at the moment 'cause the wireless in the house has gone down at the moment (apple tv's fault!!). I'll try this when i've got it all up and running again :).

Thanks huygens,

Matt:KS

---

### Post by giambrone on 2007-04-11
wAw.

Thanks so much for your help huygens - i could access the disk in the terminal... Currently updating everything at the moment and so not much I can do with it at this point in time...xD

Once again, thanks :KS

Matt

---

### Post by MikeMay on 2007-04-11
> **giambrone said:**
> Thanks so much for your help huygens - i could access the disk in the terminal... Currently updating everything at the moment and so not much I can do with it at this point in time...xD

Have you been able to mount the volume or just "access the disk in the terminal"?

---

### Post by giambrone on 2007-04-12
Alas only in the terminal... But I could retrieve files from it and stuff...
It would be nice to be able to access it via GDE/nautilus but thats the next step!

Matt:KS

---

### Post by huygens on 2007-04-12
> **MikeMay said:**
> Have you been able to mount the volume or just "access the disk in the terminal"?

If you can access the disk via the terminal, you can mount it too :-) If the automatic way fails (I mean, if with the graphical interface (GUI) it does not seem to work), it is still easy to do the mount manually once with the command line and it will be done automatically after.
:-)
For example, the following post talk about [mounting a shared drive with Samba using the command line]("http://ubuntuforums.org/showthread.php?p=1440697"). This might help you if the GUI fails, but hopefully it won't fail ;-)

---

### Post by huygens on 2007-04-12
> **giambrone said:**
> Alas only in the terminal... But I could retrieve files from it and stuff...
It would be nice to be able to access it via GDE/nautilus but thats the next step!

Giambrone, you can try to follow my advice in my above post. It is using the command line to mount the partition, after it appears like a normal local drive.
However, it should be working with Gnome GUI. If you have tried to follow my previous post on this matter, did Nautilus/Gnome gave any error or warning message? In which case, what was it?

---

### Post by giambrone on 2007-04-12
Okay - in trying to use the GUI with the settings suggested it an error window pops up saying ""320GB" couldn't be found. Perhaps it has recently been deleted."
We all know it hasn't been deleted!

Matt:KS

---

### Post by huygens on 2007-04-12
I did try again the GUI, and it works with a share drive I have access to.
So I took a screenshot with what I suppose you should have for data. The only thing you need to change is the username. I have used your forum username, but it is probably different. You should use the same one as for the command line.
Also, check that I did not made a mistake for the IP address ;-)

---

### Post by giambrone on 2007-04-12
-once again i'm stuck-
It doesn't require a username to connect on Windows, or Mac -> The software just finds the Disk and asks for a password...

...Do you think there would be a default login name for the disk?

Matt:KS

---

### Post by huygens on 2007-04-12
You could try just leaving no user name or specifying 'guest' as a username.

I was trying to set up such configuration and test it. However, I do not manage to create a share with just a password. There is always a user attached to it (either on XP Pro or on Linux, I have the same issue). You will have to try the above suggestion, but I do not find much help in the documentation.

---

### Post by giambrone on 2007-04-13
Okay I've tried that and there was still no joy :o

I'm wondering if there is a way to find out the username that you use from the terminal method -> that could get us closer.

Thanks anyhow :)

Matt:KS

---

### Post by huygens on 2007-04-13
> **giambrone said:**
> I'm wondering if there is a way to find out the username that you use from the terminal method -> that could get us closer.

OK, first you could try in the blind, here are some possible "username":[LIST]
[*]the hostname of you computer
[*]the hostname of the airport
[*]guest[/LIST]I none of the above works, you could try to sniff it. There is no easy way or easy guide to do it. Though there is a graphical tool to help you with that. You can install wireshark. Then launch it from the terminal: gksudo wireshark
Once wireshark is launch, you then press Ctrl+K. A small window will open. The only thing you should take care of are the "capture filter" text area, you should write there "port 139" to avoid too much noise. The second thing is completely at the top. You should verify that the correct network interface is selected. If you do not know, use the "Pseudo device ............ any"
Click on the start button.
Now use the command line to connect to the shared drive. Once done, stop the capture in wireshark.
You will see data appear on the screen in wireshark. The difficult part comes now in analysing them. Hopefully wireshark understand the SMB protocol, and you should look at the lines marked SMB, in the column info you will see the information about the username (if used) written in plain English.


If you do not understand anything of it, you can save the capture as a file and send it, however it might contains sensitive information and you should probably not put it on the forums. I can guarantee you that I won't use the data for anything but to help you. So if you are willing to trust me you can send them to me. If you go on [my launchpad]("https://launchpad.net/%7Ehuygens-25") you can find my OpenPGP key (so you can encrypt the file for better security) as well as an e-mail address you can use. I will not take offence if you decline this proposal nor if you manage to read the capture by yourself ;-) but in case you accept, you can be sure that I won't retain your data longer than needed to help you.
*For information on encryption, you can read the [Ubuntu help on the GNU Privacy Guard]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto"). You might want to consider [SeaHorse]("http://www.gnome.org/projects/seahorse/") which is available in the repositories as well as mentioned in the previous guide. It is part of the Gnome project and greatly help to manage OpenPGP keys and to encrypt files (just right click on a file in Nautilus, the file explorer)*

---

### Post by giambrone on 2007-04-14
Okay it came up with something that I *think* is the username, but I'm not sure which part to use, here is the packet info I think that I need...
> Account: matt
Domain: MSHOME

I've tried usernames: [LIST]
[*]MSHOME\matt
[*]matt
[*]uname: matt, domain: MSHOME
[/LIST] 

And all of them come up with "320GB could not be found - perhaps the folder has been deleted"

Thanks for your persistence :)

Matt :KS

---

### Post by giambrone on 2007-04-14
Okay I've now managed to mount it over the samba/ hard disk method - my domain/ username was <router's network ip>\matt
I can finally listen to all of my music :)
I still don't understand why the "connect to server" method hasn't worked... But that's a story for another day ;D.

Thanks huygens for all of your help :)

Matt:KS

---

### Post by huygens on 2007-04-14
OK, I'm happy it is working now :-)
It is a pity that it does not work with the GUI...

I'm thinking of opening a bug report on Nautilus, however as I cannot reproduce the problem it is difficult to create it. Perhaps, having some log messages information would be nice.
If you go under /var/log/samba, do you have a file with the name: "log.<router's network ip>"? If yes, is there any relevant information about why Nautilus was failing to connect to your AirDisk?

In case the file is too much confusing (too many information in), you can do this do wipe it:
```
sudo /etc/init.d/samba stop
sudo mv /var/log/samba/log.<router's network ip> /var/log/samba/log.<router's network ip>.backup
sudo /etc/init.d/samba start
```Now, you should try to connect with Nautilus ("Places" -> "Connect to server") again. After it is failing, you can check the log file, it should have less information now.

---

### Post by giambrone on 2007-04-14
Sadly there is no log in there - i think this is due to the fact that I may be using the wrong credentials; no password box pops up if I try _any_ username, and the attached message pops up...

Matt:KS

---

### Post by huygens on 2007-04-14
Giambrone,
I have opened a bug report in Launchpad: [https://bugs.launchpad.net/bugs/106511](https://bugs.launchpad.net/bugs/106511)
If you have a launchpad account, you can subscribe to this bug and get notification of its evolution.
I'm subscribed to it too. Perhaps could you do it also. In case the developers or maintainers need further information, I am not sure if I could provide it to them.
Cheers,
Huygens

---

### Post by giambrone on 2007-04-14
Okay thanks Huygens - I'm subscribed :)

Now all i have to do is get round my wireless card errors :o.

Thanks for now...

Matt:KS

---

### Post by MikeMay on 2007-05-10
Which filesystem (Fat 32, NTFS ...) does the AitPort Extreme support? Whats the maximum Volume size?

I am asking this, because I would also like to directly connect the disk to Mac OS and Windows and
FAT 32 has some limitations I dont want (max file size of 4 GiB).

Thanks,
Philip

---

### Post by giambrone on 2007-05-14
This is just a long shot - and its from what I can remember, but I think that because it acts as a samba server it shouldn't matter what filesystem you use. I'm pretty sure that my AirDisk uses HFS+, but in Windows it shows up as FAT32 - so I think its an on-the-fly thing. I'm not too sure about which filesystems it supports though - if you stick to the major ones (apart from ext and reiser) it should be all good.
Hope this helps.

Matt:KS

---

### Post by huygens on 2007-05-16
Yes Gianbrone is right. If you format the harddisk in HFS+, when it is shared over the network, it is viewed as a SMB/CIFS file system for Windows/Linux system and as a AFP file system for Mac OS X system. So the remote client does not see (it is transparent for him) what is the real file system of the hard drive.

---

### Post by Son of Silas on 2007-11-16
I have an Airport Extreme-N with a Western Digital USB drive plugged into it. I had exactly the same issues as reported in this thread. I resolved this by running the Airport Extreme Configuration Utility from my windows machine, in the disk configuration tab, selecting the option to allow guest access. From my ubuntu laptop i then use 'guest' as the User name.

---

### Post by bohbot16 on 2008-01-11
I was able to set up my AirDisk to automatically mount properly in Gutsy by using CIFS instead of SMBFS.  There are some great instructions here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) including how to automatically unmount at shutdown.

---

### Post by giambrone on 2008-01-13
Thanks :-) this problem is long gone since our network was super slowed down by the AirDisk over n and g... Its a good starting point though :)

---

