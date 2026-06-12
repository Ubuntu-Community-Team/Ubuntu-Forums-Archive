---
title: "HOWTO Ridiculously easy home file sharing with FTP and Zeroconf"
date: 2006-07-18
forum: Tutorials
---

### Post by dyssident on 2006-07-18
The information in this thread has been moved to [https://help.ubuntu.com/community/EasyHomeFileSharingWithFTPAndZeroconf](https://help.ubuntu.com/community/EasyHomeFileSharingWithFTPAndZeroconf)


A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012424](http://ubuntuforums.org/showthread.php?t=2012424)

Thread closed.

This tutorial will cover setting up ridiculously easy, reliable, cross platform, standards based home networking. You will be able to share files from any Ubuntu/Debian system and connect to them from any Linux, Windows or OS X box. If you want to share your files on a firewalled home network but dont want to bother with Samba, NFS, or AFP this is for you.

I chose FTP because it is supported on all systems since the beginning of time, it is secure enough for home use and its easy get working. Samba/SMB is too difficult to set up for the novice user, is Windows centric and has various problems with transfer failures and slowdowns. NFS was designed for Linux, but is, like Samba, too difficult for the novice user.

I started out to do this with SSH, but decided on FTP after seeing GShare. I chose not use GShare for several reasons: it has a great many dependencies that my approach doesnt require, its FTP server was written from scratch and is therefore almost by definition more insecure and less interoperable than the FTP daemon we will use and I wanted to lock users into their home directories by default.

Enough with the formalities, lets get to it.

[SIZE="4"]Setting up the FTP daemon[/SIZE]

We will use vsftpd (Very Secure FTP Daemon) as our FTP server.

[SIZE="3"]Install vsftpd[/SIZE]

    ```
sudo apt-get install vsftpd
```

[SIZE="3"]Configuring vsftpd[/SIZE]

We need to modify some vsftpd settings. To edit your configuration file by hand, open the configuration file with

    ```
sudo gedit /etc/vsftpd.conf
```

Change or uncomment (remove the #) the following parameters

```
    local_enable=YES
    write_enable=YES
    anonymous_enable=NO
    chroot_local_user=YES
```

[SIZE="3"]Start vsftpd[/SIZE]

    ```
sudo /etc/init.d/vsftpd restart
```

Vsftpd will now always start automatically when your computer starts.

[SIZE="4"]Setting up Zeroconf[/SIZE]

Vsftpd will do the file transfer for us, but need some way to find services and name the boxes on our network. Avahi allows us to give our systems names without setting up a DNS server and easily discover services. It is a completely free Zeroconf daemon and the choice of Gnome.

[SIZE="3"]Install Avahi[/SIZE]

```
sudo apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan
```

If all you want is convenient host naming that allows you to use DNS names (ie. hostname.local) without setting up your own DNS server, you can skip the next section. Instructions are provided for connecting to shared files with and without zeroconf service announcements.

[SIZE="3"]Create Zeroconf Service Announcements (Optional)[/SIZE]

Most OSes zeroconf service discovery support, even zeroconf creator's OS X, is very limited. The potential of this technology is great, but for now this section is helpful but not critical.

To edit by hand, run

    ```
sudo gedit /etc/avahi/services/ftp.service
```

and paste

```
    
    <?xml version="1.0" standalone='no'?>
    <!DOCTYPE service-group SYSTEM "avahi-service.dtd">
    <service-group>
    <name>FTP file sharing</name>
    <service>
    <type>_ftp._tcp</type>
    <port>21</port>
    </service>
    </service-group>

```

Save an close Gedit.

[SIZE="3"]Restart Avahi[/SIZE]

    ```
sudo /etc/init.d/avahi-daemon restart
```

[SIZE="4"]Repeat![/SIZE]

Now do what you just did on every Ubuntu/Debian computer you wish to share files from. You only need to do the Install Avahi section on the Ubuntu/Debian systems that you want only to connect to shares from.

[SIZE="4"]Connecting to your shared files[/SIZE]

[SIZE="3"]Connect from Ubuntu/Debian (or any Gnome desktop)[/SIZE]

*With zeroconf service announcements*

Click Places->Network Servers. You should see an icon labeled FTP File Sharing. Right click on it and click Connect To This Server. You can give this link a new name or just click Connect.

You should now see an icon labeled FTP File Sharing on your desktop. Double click the icon. You will be asked for your username and password: Select Connect as User. Enter your username and password *that you use to log into the box you are connecting to*. Check 'Remember password for this session.' After you click OK, your home directory on your remote machine should appear. You should not have to enter your username or password again until you log out of your computer.

*Without zeroconf service announcements*

Click Places->Connect to Server. Click the Service Type dropdown and select 'FTP (with login)'. Enter hostname.local in Server, in 'User Name' enter the username *that you use to log into the box you are connecting to*, and set 'Name to use for this connection' to FTP File Sharing.

You should now see an icon labeled FTP File Sharing on your desktop. Double click the icon. Enter your password *that you use to log into the box you are connecting to* and check 'Remember password for this session'. After you click Connect, your home directory on your remote machine should appear. You should not have to enter your username or password again until you log out of your computer.

[SIZE="3"]Connect from OS X[/SIZE]

OS X natively supports connecting to FTP through the Finder. The only drawback is that mounted shares are read only.

*Without zeroconf service announcements*

Open Finder. Click Go > Connect to Server. Enter 'ftp://hostname.local' then click Connect. Enter your username, password and check 'Remember this password', then click OK. There will now be a new Finder entry for your ftp site.

*With zeroconf service announcements*

Open Safari. Press Option+Apple+B to open bookmarks. Click on the Bonjour icon. Find the name of the service you want to connect to and double click it.

[SIZE="3"]Connect from Windows[/SIZE]

Because Microsoft is backing its own zeroconf-ish protocol, Windows support for zeroconf service announcements is practically non-existant. Apple's Bonjour client is the only real free support for zeroconf on Windows. Its service browsing functions are extremely limited, but it works quite well for host naming. Because service discovery support is so limited, we will not use service discovery when connecting from Windows. Therefore, after installing Bonjour, you can use can use either of the following connection methods whether or not you created zeroconf service announcements.

*Install Bonjour*

[Download Apple's Bonjour for Windows here](http://support.apple.com/downloads/Bonjour_for_Windows). Run the setup like any other; answer Next, Yes and OK to every question. After your computer restarts, you will have full zeroconf naming support.

*With Explorer*

This method does not create a new drive letter; you will only be able to access files through Explorer.

Open an Explorer window. Click Tools > Map Network Drive... Click the "Sign up for online storage or connect to a network server" hyperlink. Click Next on the Add Network Place wizard. Click the "Choose another network location" icon and click Next. Enter the host to connect to in the form [ftp://hostname.local](ftp://hostname.local) and click Next. Uncheck "Login anonymously" and fill in the username that you want to connect with then click Next. Change the name of the network place if you wish and click Next then click Finish.

A window should open and you should be prompted for your password. Enter your password and check Save Password then click Log On. You should now see your files on the remote machine.

*With NetDrive*

Windows cannot mount FTP as a drive natively, but there is a program called NetDrive that does an excellent job. There is already a tutorial that is more complete than anything I could do so [follow these instructions to install NetDrive](http://www.loyola.edu/5555/netdrive/installingnetdrive) and make one critical change: When you get to "add new site", enter the "Site Address/URL" in the form HOSTNAME.local, where HOSTNAME is the name of the box you are connecting to.

[SIZE="4"]Success![/SIZE]

Thats about all there is to it.

The major drawback to this setup is that most gui-less Linux applications will not be able to save and open files directly. Applications designed especially for Gnome will most likely work, but support is currently hit-and-miss. If you find that your application cannot directly access the share, you will need to manually copy the files, work on them, then copy them back.

[SIZE="4"]Conclusion[/SIZE]

IMHO, this completely blows away Samba/SMB and NFS for ease of setup, ease of use and cross platform interoperability (although we have not yet made use of this).

Making our shared files act like part of our file system, and therefore work with any application, is possible and will be covered in a future tutorial. In the future I will add information about mounting FTP shares so that you may access files from any application as if there were on your system. I will also describe how to mount our FTP share on Windows and OSX for truly sublime cross platform file sharing.

[Origionally posted here]("http://sketchyscience.blogspot.com/2006/07/ridiculously-easy-home-networking-with.html")

Edit 2006/08/26: Made zeroconf service announcements optional. Added mounting instructions for OS X and Windows.

---

### Post by GameManK on 2006-07-19
Thanks!

Had a little trouble with konqueror and setting it up in remote:/ but now it works perfectly, dunno what was happening at first.

For anybody trying with konqueror by typing in the address yourself: for some reason using [ftp://hostname:21/](ftp://hostname:21/) gives some error about the password, but [ftp://username@hostname:21/](ftp://username@hostname:21/) works fine.

Also, you should edit the name and host name in the provided ftp.service file.

---

### Post by dyssident on 2006-07-19
> **GameManK said:**
> for some reason using [ftp://hostname:21/](ftp://hostname:21/) gives some error about the password, but [ftp://username@hostname:21/](ftp://username@hostname:21/) works fine.

Also, you should edit the name and host name in the provided ftp.service file.

good catches. ive updated the ftp.service file to remove hostname; it is not actually necessary. and i also unscrambled the ftp.service file that i posted inline.

i used this today in an open lab to transfer files between Windows, OSX and Linux boxes; it worked like a dream. hopefully ill have time to add exact instructions soon.

IMHO, IPP + FTP + Zeroconf could completely replace Apple and Microsofts respective workgroup networking schemes. If only FTP did file locking.

---

### Post by vkkim on 2006-07-20
Maybe I missed something here, but why is this method any better than SMB or NFS?  I'm looking to configure file sharing on my home network right now, and it would be great if you could figure out how to mount drives across the network like other protocols.  I'm interested in implementing this, because SMB has performance issues and NFS is *nix only.

---

### Post by dyssident on 2006-07-20
> **vkkim said:**
> 
Maybe I missed something here, but why is this method any better than SMB or NFS?


my reason for going with this setup was a frustration with nfs and samba. experienced users can handle the setup, but my mom cant; the complexity simply isnt justified for home or small workgroup users. plus, this setup adds interoperability between OSes, without loosing any functionality (except file locking). 

> **vkkim said:**
> 
it would be great if you could figure out how to mount drives across the network like other protocols.


it can definiately be done. im working on instructions for mounting on Windows and OSX at this very moment. btw, what OS are you running?

---

### Post by vkkim on 2006-07-20
Well, I'm obviously running Ubuntu on my server, but the rest of my environment is a mix of Windows XP/Vista and Ubuntu.

---

### Post by dyssident on 2006-07-21
> **vkkim said:**
> it would be great if you could figure out how to mount drives across the network like other protocols.

Ive done some research, and you probably wont be surprised to learn that it will work on windows but it is much less elegant.

The two Zeroconf clients that exist for windows only look for HTTP services. Zeroconf will still do easy host naming for us, but we wont be able to conveniently browse for the FTP service like with linux.

Try these steps and let me know what you think:

[Follow these instructions to install NetDrive]("http://www.loyola.edu/5555/netdrive/installingnetdrive") and make one critical change: When you get to "add new site", enter the "Site Address/URL" in the form HOSTNAME.local, where HOSTNAME is the name of the linux box you are connecting to.

That is about the most elegant solution ive found. If this works for you, let me know and ill add it to this tutorial.

---

### Post by vkkim on 2006-07-22
> **dyssident said:**
> [Follow these instructions to install NetDrive]("http://www.loyola.edu/5555/netdrive/installingnetdrive") and make one critical change: When you get to "add new site", enter the "Site Address/URL" in the form HOSTNAME.local, where HOSTNAME is the name of the linux box you are connecting to.

That is about the most elegant solution ive found. If this works for you, let me know and ill add it to this tutorial.

I'm not too sure about running NetDrive, read the comments [here]("http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/").  Anyway, installing a Samba server isn't much more than aptitude install samba, which I think is much easier than setting up an ftp PLUS zeroconf, and I'm running an SFTP server now as well which is more secure than FTP.  I'm also looking for (S)FTP mounting solutions to get rid of Samba, but for now I think Samba is a better choice (at least for Windows).

---

### Post by handy on 2006-07-24
Thanks Dyssident, this is just what I need to set up my wifes OSX Panther Powerbook to be able to save files onto her Dapper desktop box.  We allready have our 2 Dapper boxes the Mac & an HP LJ-5 on the LAN, they only print & use the internet together at the moment though.

So, I will be watching this thread like a hawk to see when you add the OSX how-to... :cool: 

Do you think I will have to run Firestarter, even though the router has a firewall function built in?

Thanks again, I believe that you will have made life a lot less stressful for a lot of people with these how-to's! :KS

---

### Post by dyssident on 2006-07-24
> **handy said:**
> We allready have our 2 Dapper boxes the Mac & an HP LJ-5 on the LAN, they only print & use the internet together at the moment though.


How are you doing network printing? Is one box a print server or do you print directly with a jetdirect card?

> **handy said:**
> 
So, I will be watching this thread like a hawk to see when you add the OSX how-to... :cool: 


Unfortunately, the only access i have to Macs is on campus and their network is segregated from the open network, so a really elegant solution might take me a while. However, I know that since Tiger 10.4 comes with Bonjour by default, as long as you are on the same subnet, which no doubt at home you are, you can just use Finder's Connect to Server (or something like that) option and give it the servers mdns name eg HOSTNAME.local

You should then have a new drive in Finder that is the default directory of your remote FTP server.

> **handy said:**
> 
Do you think I will have to run Firestarter, even thought the router has a firewall function built in?


Some security hardcases will tell you to run a firewall on everything, but i dont see how two firewalls are more secure than one, assuming that one is set up correctly (ie. you dont have a virtual server for your boxes FTP server set up).

---

### Post by handy on 2006-07-24
Yes, jetdirect for the HP.

I only started looking today for a solution to connect my wifes 2 machines.  I found [this link]("https://help.ubuntu.com/community/HowToZeroconf") which started me down the Zeroconf path, & led me to your thread here.

We are running 10.3X Panther, not Tiger, (don't want to buy an upgrade, Panther does all required)  Does that make difference do you think?

I haven't even begun to actually set up the ftp stuff.  This is me still working out what I am going to do...

---

### Post by dipasqum on 2006-07-25
Apologies in advance if this is a dumb question...

I followed the steps to the letter. I have two Ubuntu machines.  The only time I can see the FTP sharing icons is if I launch a nautilus window under sudo.

Meaning, off the menu bar they don't appear but avahi zerconf browser sees the services.  When I launch places/ network servers I just see Windows network.

When I 'gksudo nautilus', Go/Network, I see Windows network FTP FIle Sharing FTP FIle Sharing #2.

Permissions seems to be the logical place to look but is it my ID or the configuration of avahi?  Guidance would be much appreciated!

TIA

---

### Post by dyssident on 2006-07-28
> **dipasqum said:**
> When I 'gksudo nautilus', Go/Network, I see Windows network FTP FIle Sharing FTP FIle Sharing #2.

wow,, that is strange.. ill check the bug database because,, as i understand it,, zeroconf announced services should always be shown.. frankly,, ive been consistently underwhelmed by most OS's support for zeroconf browsing,, so i cant say this entirely surprises me.. 

that said,, zeroconf host naming should still work for you,, so you can always do Places > Connect to Server, set Service Type to FTP with Login,, and enter the name of the box you are connecting to in "Server" in the form HOSTNAME.local..

perhaps,, like Icarus,, we are trying to fly too close to the glorious sunlight of effortless file sharing..

---

### Post by blip on 2006-08-01
Well this actually worked for me!  After having nothing but frustration with Samba, this actually worked on my first try.

Anyway, I was just wondering a few things:

1) Just to confirm, the FTP server in this setup can only be accessed from inside the local network, right?

2) On one computer I want to share a whole partition. The only way I could get this to work was by mounting the partition to the home directory I login to.  It works, but is there a more elegant approach?

3) Does anyone have a simple way of doing scheduled backups to the local vsftpd server?

Sorry for the newbish questions and thanks for the great write up!

---

### Post by behemot on 2006-08-02
Thanks,
It is a great how-to.

Do you know how to get rid of "Windows Network" under Places-> Network Servers?  
I have no Windows machines running on my network and I am not planning on sharing files in Windows environment.

---

### Post by dyssident on 2006-08-02
> **blip said:**
> 
1) Just to confirm, the FTP server in this setup can only be accessed from inside the local network, right?


right, unless you create a virtual server through your home networks firewall. but i would not want to expose an ftp service to the outside world. im going to do this same tutorial with SSH in the future, and that would be a much better choice.

> **blip said:**
> 
2) On one computer I want to share a whole partition. The only way I could get this to work was by mounting the partition to the home directory I login to.  It works, but is there a more elegant approach?


im on a windows box, so im doing this from memory. forgive me if it doesnt work the first time.

1. edit configuration file with `sudo gedit /etc/vsftpd.conf`
2. comment out "chroot_local_user=YES" 
3. set 'local_root' to the directory users should start out in. in your case, it will be the mount point of a given drive like /dev/hda
4. close vsftpd.conf
5. restart with `sudo /etc/init.d/vsftpd restart` 

whenever you log in, you will start out in /dev/hda, or whatever directory you set local_root to.

> **blip said:**
> 
3) Does anyone have a simple way of doing scheduled backups to the local vsftpd server?


as soon as i add the bit to the tutorial (which i will do very soon) that describes how to mount a remote ftp server as a local drive, it will be as easy as writing a script and running it as a cron job. with what you have now, all file shuffling is done through Gnome, so its not really easy to script. i think your only real option is to drag and drop.

---

### Post by dyssident on 2006-08-02
> **behemot said:**
> 
Do you know how to get rid of "Windows Network" under Places-> Network Servers?  


yea, that is quite an eyesore. im not aware of a way, but you may want to ask on the [Gnome Nautilus mailing list]("http://mail.gnome.org/mailman/listinfo/nautilus-list").

---

### Post by bparker2003 on 2006-08-03
Ive followed this really easy walk thru, thanks for that by the way, but when i try to connect inbetween my two ubuntu machines, the folders that open are empty and i cant write to them, does anyone know where i went wrong?

---

### Post by blip on 2006-08-06
Thanks for the answers dyssident! Look forward to seeing the mounting instructions.  Honestly setting this up was so much easier than working with samba I could hardly believe it!

bparker2003 - I'm new to this too so my advice isn't the most useful but the thing that comes to my mind first is a funny firewall setting on either or both machines.  I seem to recall running into similar problems with a misconfigured firewall in windows a few years back but I could be wrong.

---

### Post by bparker2003 on 2006-08-06
ill check my firestarter settings, thanks i didnt think of that

---

### Post by powder22 on 2006-08-11
I can't see any directories when I connect to my host. I connect just fine but see no directories. I don't know how to share directores, like Home folder, ect. Can someone please tell me what I need to do to get this working?

---

### Post by dyssident on 2006-08-16
> **powder22 said:**
> I can't see any directories when I connect to my host.

are you connecting with the same username that you normally use on that box? when you connect to the remote host, you start out in the home directory of the user whos name you supply. so if you log into the remote box as USER1 when you are setting in front of it, and you log in as USER2 when you are connecting via FTP, you will not see USER1's home directory, you will see USER2's empty home directory.

so basically, if you created a special user to log in via ftp with, just use the username/password that you would normally use.

---

### Post by Delerious on 2006-08-17
Hi, thanks for this HOWTO thread :) it let me do exactly what I wanted to do. 
I followed all the directions exactly, but did encounter one problem. First my situation:

I am using an Ubuntu linux box as a local music server which I have all my mp3s stored that is running a surround sound audio system. I wanted an easy way to transfer files from my windows gaming/work machine to my linux box. This helped me tons and I followed all the directions as stated above. 

Once I set up my old wsftp pro client on my windows box with my ubuntu log in name and password, I recieved an error that I could only log on as anon, but when I did so, I could not view any files on the linux box. To fix this I changed this line 
```

sudo /etc/init.d/vsftpd start
```

to 

```
sudo /etc/init.d/vsftpd restart
```

because upon installing it started the server and failed to start (because it was already running) and following along the HOWTO, you are editing the conf file and not getting the server to restart using the new conf. Anyway doing the restart fixed my problem :)

---

### Post by igor4u on 2006-08-20
Thank you!
It works! :D 

I connected 2 Ununtu PCs by crossover cable in order to make local network.

**PC 1: **
IP 192.168.0.1 
FTP
Zeroconf

**PC 2: **
IP 192.168.0.2

Only one question. Why do I need Zeroconf? :confused:

---

### Post by dyssident on 2006-08-31
Edit 2006/08/26: Made zeroconf service announcements optional. Added mounting instructions for OS X and Windows. Grammar.

---

### Post by natgwil on 2006-10-29
I wanted to connect my laptop to my desktop PC and share files. I had Kubuntu on both and followed the HOWTO and things worked very well. However because my laptop is not very high-powered I changed over to Xubuntu. Now I'm not sure how to setup the final stage "Connecting to your shared files." Can anybody help?

---

### Post by Sandman32 on 2006-12-02
This is a little old, but I am hoping someone might be able to help out.  I'm really trying to share my /media folder (so I can get to my mounted drives) more so than my home folder.  Is this possible using this method?  Thanks for any help you can offer.

I tried mounting my drives in my home folder but for some reason couldn't get that to work...

---

### Post by lhtown on 2006-12-08
Has anyone gotten this to work on Edgy?

I followed the instructions to the letter, but it doesn't connect with or without zeroconf.

I have two computers running Ubuntu Edgy through a netgear wired router.

---

### Post by lhtown on 2006-12-08
I think I have it working now in Edgy. 

Under System>Administration>Networking I went to the General tab and selected the option "Scan for available services..." on both machines and then rebooted both machines.

I haven't tried it all out, but at least they are seeing each other and allowing me to browse around.

That is with the zeroconf services.

---

### Post by rcatman on 2007-05-13
Works perfect on feisty. I followed each step exactly. 

I have a iMac G5 in another room and an ubuntu fiesty fawn computer connected to the internet through a linksys router. On the macosx computer I went into finder and typed [ftp://ip.of.ubuntu.computer.on.network](ftp://ip.of.ubuntu.computer.on.network)  and connected, it worked great! I logged in using my username and my home directory popped up. 

Although its read only I'm going to work out how to upload files aswell. Because after all, file-sharing is both ways!

Thanks for the great tutorial!

---

### Post by Banny706 on 2007-05-13
Hi, trying to set up an FTP server such that I can share my pics with my family.  I could e-mail them but they are of high quality and cumbersome to send since I would like to send more than 5 pics each time (my mailbox can't handle the size).  I am running Ubuntu Feisty and my Mom is using Windows Vista.  What do each of us need to do in order for this to happen.  Meaning:  What do I have to set up and configure?  What do I need to give my Mom in order to connect?  Simple enough but am complete noob on doing things such as this and I have absolutely no knowledge of Vista (ewww!).  I have tried to set up Samba, FTP before but can't seem to make things work as they should.  Any help would be greatly appreciated.  You may reach me at [email]rjbanfield@ns.sympatico.ca[/email] with your answer as well.

---

### Post by Scheater5 on 2007-06-08
Been struggling with networking for weeks, and now I'm not only able to share files via FTP but also remotely login (currently further testing the latter).  Thanks.

---

### Post by stewacide on 2007-06-12
> **rcatman said:**
> Works perfect on feisty. I followed each step exactly. 

I have a iMac G5 in another room and an ubuntu fiesty fawn computer connected to the internet through a linksys router. On the macosx computer I went into finder and typed [ftp://ip.of.ubuntu.computer.on.network](ftp://ip.of.ubuntu.computer.on.network)  and connected, it worked great! I logged in using my username and my home directory popped up. 

Although its read only I'm going to work out how to upload files aswell. Because after all, file-sharing is both ways!

Thanks for the great tutorial!

This tutorial worked for me as well, including the Rendezvous, but similarly I'm getting read-only access. Any luck figuring out how to get write as well?

edit -- actually it's just Finder that refuses to write: other FTP progs have no problem. Weird.

---

### Post by xjgnsdof on 2007-07-21
Ok, I've done all of the steps, but I still can't connect to my other computer.

On my desktop, I'm emones-homePC
On my laptop, I'm emones-laptop

I want to connect TO my desktop FROM my laptop. What information do I enter, and where?

---

### Post by Mode_Locrian on 2007-07-24
Thanks for the really clear guide.  I followed all of the instructions correctly (I think) but I am still unable to connect to my Ubuntu share from my OSX machine.  I have confirmed that my Ubuntu box and my OSX box are on the same subnet and, here's the kicker, I can get them to connect just fine via their respective IP addresses for using Synergy (mouse/keyboard sharing over TCP/IP).  So maybe I'm just being stupid here (I am rather new to both OSes).

Suppose, for example, the network name of my Ubuntu box is "MyUbuntuBox".

Then, in the finder dialogue that you describe your guide I should literally type "ftp://MyUbuntuBox.local" and then hit connect?  If that's not right, what should I do instead?  And if it is right, any idea why it doesn't work for me?

---

### Post by Mode_Locrian on 2007-07-28
Ok, I solved the problem.  It turns out that I needed to turn on the FTP proxy (and, in particular, the "use passive FTP mode" option) on my Mac.  I can now access my Ubuntu shares from my Mac, and vice versa--almost.  I say almost because now I have another question:  Can I use this technique to access shares on mounted volumes as well?  I've got an NTFS partition (mounted at /media/sda2) that has some shares on it that I'd like to access, but I can't see how to make this work.  Thanks for the help.

---

### Post by Depressed Man on 2007-07-29
It worked great, but apparantly I have two FTP connections? FTP Share 1 and FTP Share 2. Share 1 takes me to the share folder. Share 2 does nothing, and I can't delete it (even as root).

---

### Post by Fittersman on 2007-08-22
thanks alot for the guide man, i was having alot of trouble getting my ubuntu files to fedora, not much trouble the other way though, but this guide helped alot

thanks alot :D

is this thread a sticky? if not it should be

---

### Post by bdmp on 2007-08-23
Has there been any success on gettin read/write access from a mac? 
I really like this method but I can't edit any files. Please help.

Thanks

---

### Post by gottatrieit on 2007-09-11
:)  ):P  dyssident,
 Finally, after posting, prowling, head-banging, and just plain --- almost -- giving up, I now have 2 of my 3 Ubuntu machines file sharing!  I finished up the 2nd. one just a few minutes ago and am now going to bed.  Tomorrow, I will tackle no. 3, and then be one very happy gNu-Bee!!

 Thank You!                           Thank You!                      Thank You!

---

### Post by maverick78 on 2007-09-14
Dyssident thanks for the awsome guide.  I'm now sharing files between the gaming computer in my home office and the media center computer in my living room.  I'm running Ubuntu Feisty on both of my machines.  Like Depressed Man who posted above I also have FTP Share 1 and FTP Share 2, but I'm guessing thats okay since everything seems to be working properly.

---

### Post by HeresJohnny on 2007-09-21
Dyssident, I love you.  I really, really love you.  I've been trying to share files across my local wireless network (ubiquitous Linksys router) for the longest, and it seemed like I was never going to get this to work.  And then I saw your howto.  Both my desktop and laptop are running Ubuntu 7.04, and after following your instructions to the letter, I am sharing files between my computers like a pro.  Mad kudos to you.  :guitar:

In appreciation,
Heresjohnny

---

### Post by mikeize on 2007-10-12
I just keep getting kicked back to the login dialog, I know I have the right hostname and user/password, it just won't take!  Any ideas?  *waiting for the truly simple gui method*

also, if I just can't get this to work, do I need to somehow clean up/reset all the stuff I did, before I try some other method?

-mike

---

### Post by morningboat on 2007-10-24
For the ZeroConf protocol, I'd recommend an even better solution: the CrossFTP Server and CrossFTP Client. They both support the Bonjour (ZeroConf), and they are quite easy to use and of good quality, so that even beginners can set up everything easily in 5 minutes. Here are some tutorials:
[LIST]
[*][Text tutorial]("http://www.ubuntugeek.com/how-to-setup-file-sharingsftp-for-machines-by-newbie-in-5-minutes.html")
[*][Flash tutorial]("http://www.crossftp.com/tutorials/tutorial_server_setup_demo/tutorial_server_setup_demo.htm").
[/LIST]

---

### Post by ericartman on 2007-10-27
Thanks ever so for the instructions, worked like a charm once I really followed them (lol). Off to try connecting my g4 this way.

Cart

---

### Post by ubunoobie on 2007-10-31
Excuse my noobness, but what about filezilla? Doesn't filezilla do all of this? Is it necessary to take all of the steps described in this how-to? Or does a program like filezilla take care of things?

I've been looking for a home network/file transfer solution for some time now but I can't seem to find something that is easy (I'm a linux noob), preferably gui-based, secure. I'm shying away from setting up Samba (because of how involved it is... I don't want to screw up my machine) and leaning towards some sort of FTP solution.

Any suggestions?

Thanks.

---

### Post by kmclar on 2007-10-31
I've followed the instructions to seup my Ubuntu 7.04 desktop as the vsftp server. I don't see the vsftp server when using the Safari/Bonjour instruction on my macbook?  The gnome instruction works fine from my Ubuntu 7.10 laptop.  Do I need to do something more on the macbook?  I can find it with Finder, and interestingly, if I type in the [ftp://ip.address](ftp://ip.address) of the server in the Safari address bar, it starts Firefox (which is also installed on the macbook), and Firefox displays the folders on the server.

---

### Post by werdna5225 on 2007-11-01
> **elgilicious said:**
> Ok, I've done all of the steps, but I still can't connect to my other computer.

On my desktop, I'm emones-homePC
On my laptop, I'm emones-laptop

I want to connect TO my desktop FROM my laptop. What information do I enter, and where?

I was having trouble also, but instead of entering hostname.local i entered the ip of the computer i wanted to connect to and so far it works great.

---

### Post by haz2a on 2007-11-12
It is most commonly suggested to insert the following rules into the file /etc/firestarter/user-pre.
```
$IPT -A INPUT  -p udp --dport 5353 -d 244.0.0.251 -j ACCEPT
$IPT -A OUTPUT -p udp --dport 5353 -d 244.0.0.251 -j ACCEPT
```
These did NOT work for me in Firestarter v1.03, in Ubuntu 6.10 or 6.06.

The following DOES work for me in Firestarter v1.03, in both Ubuntu 6.10 and 6.06 LTS:-
```
$ sudo -s
# cd /etc/firestarter
# chmod +w user-pre
# vi user-pre
Add the lines:-
$IPT -A INPUT  -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A OUTPUT -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A INPUT  -d 224.0.0.0/8 -s 0/0 -j ACCEPT
$IPT -A OUTPUT -d 224.0.0.0/8 -s 0/0 -j ACCEPT
# chmod -w user-pre
```   

Credit for these rules to Mike Pepe on the firestarter-user.lists.sourceforge.net see:- 
[HTML]http://ml.osdir.com/security.firewalls.firestarter.user/2006-04/msg00017.html[/HTML]

---

### Post by gigaferz on 2007-11-21
i did it a while ago, now i was all desperate, but looking @ my .bash-history on  one computer i found some commands wich lead me here again... I'm not letting go now....

seriously is very frustrating....I just can't believe is not included by default in ubuntu.

---

### Post by Paulr-55 on 2007-12-01
SOLVED -- NEVER MIND

I have two desktops running feisty and gutsy on a wired router (linksys)

I followed all instructions on both machines, but each FTP File Sharing folder connects to the machine's own home folder rather than that of the other machine.

What have I done wrong here?

*** Update

After restarting, each machine fails to connect to the other : can,t find ftp: [email]paul@dellbot.loca[/email]l or [email]paul@moonunit.loca[/email]l. and suggests I check proxy settings. How can do that?

*** Update

Ok, got it going. I had to use "Connect to Server" and use ip address, not localhost.

Thanks, Paul

---

### Post by Amstell on 2007-12-05
Thanks that was great advice and really easy to setup.  Whenever I want to uninstall it how would I go about doing that.  Thanks.

---

### Post by bconverse on 2007-12-05
> **Sandman32 said:**
> This is a little old, but I am hoping someone might be able to help out.  I'm really trying to share my /media folder (so I can get to my mounted drives) more so than my home folder.  Is this possible using this method?  Thanks for any help you can offer.

I tried mounting my drives in my home folder but for some reason couldn't get that to work...

Also having this problem...any way to get this working? The drive I want to be shared as all the files worth sharing on it, so its kind of pointless without it haha. Anyways thanks for any help.

---

### Post by gigaferz on 2007-12-08
[http://ubuntuforums.org/showthread.php?t=91887&highlight=user+ftp+share](http://ubuntuforums.org/showthread.php?t=91887&highlight=user+ftp+share)

here you could find something useful how to set it up  the way you like, ill try it tomorrow

---

### Post by zorkerz on 2007-12-14
Im using Ubuntu 7.10 64bit.
I have followed the directions in this threads initial post.

When I go to places->network (there is no network servers) I do not see an FTP file sharing icon only Windows Network and various computers on the network.

When I try to connect from a mac it says "could not connect to the server because the name or password is not correct" but it never asks me for a name or password.

and in safari i do not see my computer. So it looks like something has gone wrong with my setup maybe?

This should let me see things an OS X box is sharing to right?

:This is my goal:
-> I have one folder I would like to share without any login or passwords as read only over any local network. 
-> I would like to have one subfolder of this allow writing or uploading by anyone so that people can give me files.
-> I would like to be able to access files shared on an OS X computer without any special configuration on the mac.

This thread seems to provide the most promising solution Im just missing a few pieces apparently.

---

### Post by gonzolono on 2007-12-22
does this work with PCLinuxOS?

---

### Post by checho4 on 2008-01-21
Does anyone know how to REMOVE the broadcast?  I no longer want to broadcast my FTP connection.

---

### Post by samden on 2008-12-07
Works great, I have two machines running Hardy talking together happily and wirelessly, thanks heaps for the great how-to!

---

### Post by enginuysal on 2009-01-12
[http://www.voxpopulimedia.com](http://www.voxpopulimedia.com) is down. Could you give us another link for the vsftpd.conf
Thanks...

---

### Post by HuaiDan on 2009-01-30
> **enginuysal said:**
> [http://www.voxpopulimedia.com](http://www.voxpopulimedia.com) is down. Could you give us another link for the vsftpd.conf
Thanks...

You don't need the voxpopuli links, Just edit the files as directed. Just copy and paste the changes if you want to.

What I'd like to know is if I can use this method to make an FTP server available to the internet on my external IP. Would that be a matter of just opening port 20 on the firewall? I would like to share some video by sending my friends a login and an IP, if that's possible. How would I go about doing that?

Edit: Forwarded ports 20 and 21 through my router, ftp'd to my external IP, logged in with my user creds, and I could see my entire home folder on the internet, read, write, delete.
Now this is cool, but I need a way to button this down and get a secure login with read-only I can give out to people.

---

### Post by dmizer on 2009-02-01
> **HuaiDan said:**
> What I'd like to know is if I can use this method to make an FTP server available to the internet on my external IP. Would that be a matter of just opening port 20 on the firewall? I would like to share some video by sending my friends a login and an IP, if that's possible. How would I go about doing that?

Edit: Forwarded ports 20 and 21 through my router, ftp'd to my external IP, logged in with my user creds, and I could see my entire home folder on the internet, read, write, delete.
Now this is cool, but I need a way to button this down and get a secure login with read-only I can give out to people.
I would suggest disabling this as soon as possible.

The method outlined here is extremely insecure and not meant for WAN traffic.

If you want a WAN accessible FTP server, check the 3rd link in my sig.

---

### Post by mgw2008 on 2009-02-03
Just noticed that the netdrive link doesn't work. Are you refering to netdrive from SolutionBOX?

---

### Post by mgw2008 on 2009-02-03
Downloaded netdrive from ZDNet but it doesn't do the trick. 

I reverted to Ftpdrive  [http://www.killprog.com/fdrve.html](http://www.killprog.com/fdrve.html) which actually works but has some things I don't like (storing passwords in plaintext).

You may want to include a hint that this is sufficient Windows, i.e. you **don't **need to install the Apple stuff (Bonjour) on any Windos machine.

---

### Post by MedellinManDem on 2009-02-20
I've just done this, but I am not sure if it wil work when I am away from home. It works while I am at home, but both computers are using the same router (one connected by wireless, one connected by hard wires).

I use the [ftp://Desktop:local](ftp://Desktop:local) command to get into my filesharing pc while I'm here (i'm given a login and pwd prompt), but can anyone confirm whether this will work when I am in another city tomorrow? I suspect not seeing as I have entered no IP information throughout this process.

---

### Post by dmizer on 2009-02-20
> **MedellinManDem said:**
> I've just done this, but I am not sure if it wil work when I am away from home. It works while I am at home, but both computers are using the same router (one connected by wireless, one connected by hard wires).

I use the [ftp://Desktop:local](ftp://Desktop:local) command to get into my filesharing pc while I'm here (i'm given a login and pwd prompt), but can anyone confirm whether this will work when I am in another city tomorrow? I suspect not seeing as I have entered no IP information throughout this process.
Do NOT use this method for sharing files over the internet. This method is tuned specifically for sharing inside a protected network.

If you want to access your shares over the internet, you're better off with an encrypted protocol like VPN or SSH. If you must have ftp, I highly suggest the third link in my sig.

---

### Post by MedellinManDem on 2009-02-20
> **dmizer said:**
> Do NOT use this method for sharing files over the internet. This method is tuned specifically for sharing inside a protected network.

If you want to access your shares over the internet, you're better off with an encrypted protocol like VPN or SSH. If you must have ftp, I highly suggest the third link in my sig.

I don't have to use FTP!!!

I just want the easiest and safest method of sharing files from my desktop over the internet.

Any links to howtos?

---

### Post by MedellinManDem on 2009-02-21
Well?

---

### Post by jms1989 on 2009-02-22
http comes to mind. Apache2 web server is pretty simple to setup. Just need a base dir and links to your files outside the base dir.

---

### Post by dmizer on 2009-02-22
> **jms1989 said:**
> http comes to mind. Apache2 web server is pretty simple to setup. Just need a base dir and links to your files outside the base dir.

Also not secure at all.

As I suggested earlier, [SSH](https://help.ubuntu.com/community/AdvancedOpenSSH), [VPN](https://help.ubuntu.com/community/OpenVPN) or the FTP howto (third link in my sig) would be preferable.

---

### Post by MedellinManDem on 2009-02-22
Thank you.

---

### Post by taisao on 2009-02-22
Thank you.

I didn't know that I have to open firestarter to allow the service, take like half a day to figure it out :( . Anyway, it work now :popcorn:

---

### Post by MedellinManDem on 2009-02-22
> **taisao said:**
> Thank you.

I didn't know that I have to open firestarter to allow the service, take like half a day to figure it out :( . Anyway, it work now :popcorn:

What's firestarter?

---

### Post by taisao on 2009-02-23
firestarter is a graphical program that can be used to control the firewall installed with ubuntu (iptables) .

1. open firestarter with Run Command (pressing "Alt+F2")
2. type in firestarter
3. provide superuser password if asked
4. from firestarter, go to policy tab 
5. to allow service right click, chose ftp and add rule

that's how I fix my problem, but it's not the same as yours, I'm just trying to share files between computers at home

---

### Post by PermNoob on 2009-03-03
So I got this working super fast between my two ubuntu machines (8.4 and 8.10)  thank you so much.  I floundered on makieng it work w/ windows, but that was partly because I didn't really care and ended out wiping my M$ partition anyways.
Here is my big question.  Can I set up multiple logins?  I have two computers, Computer A and Computer B.  A is the workhorse, B is generally used for storage or when A is in use by someone else.  Multiple users on both machines.  I want to be able to sit behind A and login w/ a username and password and arrive in the / directory, however when someone else w/ a username/PW on B logs in, from A, they land in their home directory.  Can that be done?

---

### Post by NESFreak on 2009-03-12
Hi,
first thanks for your tutorial.
I think i've set up everything correctly and i can access my files, however i can't see any files or directories (there all invisible), i can only access them if i enter their full path, i.e. to for instance open ~\Documenten\calculus.pdf i need to enter it's full path.

so i guess i've got some screwed up permissions somewhere, but where...

thanks,

---edit----
mmm, firefox and nautilus are showing all my files invisible, but winXP explorer.exe is actually working WTF

--edit2---
just repaired itself, didn't even had to hit it

---

### Post by skullmunky on 2009-07-26
Great guide - google brings me back here about once a year ;) 

I'm having a problem with the Avahi publishing part.  Server is running Kubuntu 9.04, client is Ubuntu 9.04.  

I can connect to the server by explicit IP address (Places->Connect to Server->FTP With Login).

But, I can't get the server to show up in Places->Network.  

avahi-discover only finds one service, of type '_workstation._tcp', even if I run it locally on the server - so my guess is that the service is not being published correctly ... what did I miss?

---

### Post by jimmx2 on 2009-11-19
any changes to this guide due to 9.10?

---

### Post by rpaco on 2009-11-20
Well it worked for three days then stopped just like samba does. When I say it worked I mean I had to use "Connect to server" there was no list of ftp networks as suggested there would be.
While it was working I could only access the home directory on the remote not all the others and other drives I used to via samba. 

I now get "Could not display [ftp://me@mypc.local](ftp://me@mypc.local)  nautilus cannot handle ftp locations"

I have checked that vsftpd is running though it says "inet_csk_wait_for_connect"
Four avahi procs are running, system monitor says:
avahi-autoipd: [eth0] bound and an IP address 
avahi-autoipd: [eth0] callout dispatcher do_poll.
avahi-deamon:chroot helper
avahi-deamon:running[mylaptop.local]
Now eth0 is my lan connection (disconnected) while I am actually using my wireless connection on eth1. 
If I plug the lan [eth0] in as well then I get "Could not display [ftp://me@mypc.local](ftp://me@mypc.local). Because the host could not be found." BUT the two avahi-autopid procs have diappeared from the list.
Unless it is simple to fix I see no advantage over samba at all.

---

### Post by jimmx2 on 2009-11-20
> **rpaco said:**
> Well it worked for three days then stopped just like samba does. When I say it worked I mean I had to use "Connect to server" there was no list of ftp networks as suggested there would be.
While it was working I could only access the home directory on the remote not all the others and other drives I used to via samba. 

I now get "Could not display [ftp://me@mypc.local](ftp://me@mypc.local)  nautilus cannot handle ftp locations"

I have checked that vsftpd is running though it says "inet_csk_wait_for_connect"
Four avahi procs are running, system monitor says:
avahi-autoipd: [eth0] bound and an IP address 
avahi-autoipd: [eth0] callout dispatcher do_poll.
avahi-deamon:chroot helper
avahi-deamon:running[mylaptop.local]
Now eth0 is my lan connection (disconnected) while I am actually using my wireless connection on eth1. 
If I plug the lan [eth0] in as well then I get "Could not display [ftp://me@mypc.local](ftp://me@mypc.local). Because the host could not be found." BUT the two avahi-autopid procs have diappeared from the list.
Unless it is simple to fix I see no advantage over samba at all.
ya same here after upgrade

---

### Post by Ixtao on 2009-12-15
Nice!! I couldn't wish for more right now. it's easy to set up and it is neatly integrated in my regular file management with Nautilus. For ages I've been moving/syncing files around between my laptop to my workstation and now all I do is hook up the laptop to the network and I can just work with a single set of files. Whoeps, I get an idea; I could even tell the Claws mail on my workstation to work with the files on my laptop :KS

---

### Post by liquidfunk on 2009-12-29
So how do I go about connecting from a Mac remotely? How do I find out the settings of the ftp server?

---

### Post by aceplayer97 on 2009-12-30
I finished all of these steps but where and how do I select a folder that I want to share via FTP? And how do I find out my FTP address? I made a FTP server on windows XP using FileZilla and in that for my FTP address I mapped my IP address to a domain name using DnyDNS. Would I have to do the same in Ubuntu?

---

### Post by dmizer on 2009-12-30
> **aceplayer97 said:**
> I finished all of these steps but where and how do I select a folder that I want to share via FTP? And how do I find out my FTP address? I made a FTP server on windows XP using FileZilla and in that for my FTP address I mapped my IP address to a domain name using DnyDNS. Would I have to do the same in Ubuntu?

This method is designed for LAN use only. It is not safe for use over the Internet. If you want to access FTP from remote, you're better off with an encrypted protocol like SSH or VPN.

This method shares Ubuntu's entire home directory by default. You'll have to look at /etc/vsftpd.conf to change that.

---

### Post by aceplayer97 on 2009-12-31
> **dmizer said:**
> This method is designed for LAN use only. It is not safe for use over the Internet. If you want to access FTP from remote, you're better off with an encrypted protocol like SSH or VPN.

This method shares Ubuntu's entire home directory by default. You'll have to look at /etc/vsftpd.conf to change that.

Oh okay. Do you any good guides for SSH?

---

### Post by dmizer on 2009-12-31
> **aceplayer97 said:**
> Oh okay. Do you any good guides for SSH?

[https://help.ubuntu.com/community/SSH/OpenSSH/InstallingConfiguringTesting](https://help.ubuntu.com/community/SSH/OpenSSH/InstallingConfiguringTesting)

And if you will be forwarding ssh from the unfiltered Internet, you should configure ssh for encrypted key authentication: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) and disable password auth: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication).

The above are STRONG suggestions for an ssh server. If you have a good pasword, you might be okay with default settings, but I would advise against it. There are a lot of exploits out there for ssh servers, so pay attention and do it right. If you don't understand or need help, just ask. Make sure you have everything set up correctly and securely before you decide to start forwarding Internet traffic to your ssh server.

---

### Post by 99_rover on 2010-01-02
OK - I am running two Ubuntu boxes  - one under 9.10 and one under 9.04 (was too lazy to upgrade that last one)

Ran the tutorial on both as shown. Works awesome on the 9.04 box - I can see all files on the 9.10 machine and read/write

Does not work on the 9.10 box keep getting a time out and server not recognized.

Pretty much tried everything I have seen on this thread - any suggestions?

---

### Post by dmizer on 2010-01-02
> **99_rover said:**
> OK - I am running two Ubuntu boxes  - one under 9.10 and one under 9.04 (was too lazy to upgrade that last one)

Ran the tutorial on both as shown. Works awesome on the 9.04 box - I can see all files on the 9.10 machine and read/write

Does not work on the 9.10 box keep getting a time out and server not recognized.

Pretty much tried everything I have seen on this thread - any suggestions?

If it's just between two Ubuntu boxes, use either NFS (4th link in my sig) or you can try sshfs: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by 99_rover on 2010-01-03
> **dmizer said:**
> If it's just between two Ubuntu boxes, use either NFS (4th link in my sig) or you can try sshfs: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

I wanted the ability to use other units if needed and it sounded as though this method was ideal. Like I said it worked perfectly on the 9.04 box and would read the Karmic box fine. But would not work going the other way. Can you think of a reason? 

It feels as though I am either not doing something or have done something dumb. Would rather not mix a bunch of protocols together if I can help it.

---

### Post by mlnease on 2010-01-12
Hello Dyssident,

I can see that this thread's getting pretty old but thought I'd have a go anyway:  I have two computers running Ubuntu (Jaunty and Karmic), connecting to the web via a Linksys router.  I followed your excellent tutorial to the letter; then again, just to double check; still no icon on either desktop and no network connection  (other than 'Windows Network') under Places/Network or under Places/Connect to Server.

I'm pretty good at troubleshooting my computers as a rule but somehow always end up at a total loss with any attempt at home networking.  I had hoped that this angle would be the exception but alas...

By the way, I've found that the IP Address on both computers is the same--that of the router.  Could this be the problem or part of it?

I've tried disabling IPBlock (which I run routinely) and UFW (I don't use Firestarter) but to no avail.  Can you (or anyone) suggest any troubleshooting approach?

Thanks in advance.

---

### Post by marseille on 2010-01-12
hello everyone,

i am also having issues.  i have a wired gnome desktop (ibex) and a wireless netbook _[LXDE]("http://lxde.org/")_ desktop (9.10 karmic koala) connected to a linksys router.

both computers are able to ping each other successfully but that's as far as i've got so far.

AVAHI on the netbook says this:

> Service Type: _ftp._tcp
Service Name: FTP file sharing
Domain Name: local
Interface: eth1 IPv4
Address: my-laptop.local/192.168.10.102:21
TXT Data: empty

on my gnome ibex desktop [under places] i am able to open a dialog box and choose ftp with login but i can't seem to figure out the correct info to put in the boxes despite reading reading through the various suggestions in the thread. 

also, my problem is similar to the one mentioned just above (ipblock and firestarter are installed on the desktop; the netbook just has UFW firewall at this point) 

please help and many thx in advance;)  i look forward to making this work :D

---

### Post by jis on 2010-01-13
> **mlnease said:**
> Hello Dyssident,
By the way, I've found that the IP Address on both computers is the same--that of the router.  Could this be the problem or part of it?

Thanks in advance.

Are you sure? Does ifconfig tell in both computers that "inet addr" is the same?

---

### Post by willowave on 2010-03-09
THANK YOU, THANK YOU, THANK YOU for this How-to. I've been pulling my hair out between trying to set up a storage server for my home network and dealing with Samba. What a pain in the BUTT. I'm not ever touching Samba again. I don't have the time to deal with it. Your ftp transfer how-to was exactly what I wanted to do, to just simply transfer stuff between systems.
Thanks again!!

---

### Post by mlnease on 2010-03-09
> **jis said:**
> Are you sure? Does ifconfig tell in both computers that "inet addr" is the same?
JIS,

Thanks very much for the response and my apologies for my late response--somehow I missed the notification.

Yes, the ifconfig output for both computers is inet addr:127.0.0.1  Mask:255.0.0.0.

Thanks again for your attention.

mike

---

### Post by ASPCartman on 2010-03-26
Lot's of FAQ's and tutorials and nothing mentions setting ftp catalog o_O Wtf? I started a server and how the hell to set a directory for it? Nothing in config. Not a single string about dirs :evil:! 
I want to share a /home/user/Downloads. That's all i need. Blah =\

PS
Yep. It's hard on linux after macosx. Mac eat your brain. You are warned.

---

### Post by eexpress on 2011-02-25
i follow all steps. include
> Create Zeroconf Service Announcements (Optional)
ssh vnc ftp between 2 machines all ok. /usr/bin/avahi-discover show each machine. avahi-browse -ac, i can see each side IPv6 IPv4's Workstation.

i install "service-discovery-applet", but i only got "No server found".

this is ok.
> Click Places->Connect to Server. Click the Service Type dropdown and select 'FTP (with login)'. Enter hostname.local in Server

this is false. this part is just i want.
> Click Places->Network Servers. You should see an icon labeled FTP File Sharing.

---

### Post by marawuti on 2011-05-16
Nice tutorial. Works fine, but I've got a question relating to the FTP server's apparent limitations. I keep videos & photos on a separate larger drive and my Docs in the "home" tree on an SSD. A symbolic link to the videos is seen as broken by Nautilus and it queries me to move it to the trash.

I like the simplicity [& non-Windoz centricity] of this setup, but is there a way to overcome the apparent weaknesses of FTP, symbolic links, and/or Nautilus?

---

### Post by wally the duck on 2012-04-29
I know it's an old thread, but...

Users of Ubuntu 12.4 will find that this method is broken, The fix is fairly simple.
 in the vsftpd.conf file
-do NOT uncomment the "#chroot_local_user=YES" line.
-immediately after that line add "local_root=/home/{name}/Public" where {name} is the name on the user's home folder and "Public" can either be the Public folder installed by default in Ubuntu or any other subfolder you want... it just cannot be the home folder. (vsftp does not want you connecting with write privileges directly to the home folder)

Also, you'll find it is not necessary to load Avahi at all. In the Nautilus file manager window you can go to the 'File" menu and click 'connect to server' and enter the proper information. Once you connect, "Bookmark" the connection and it will not only always be there in the Nautilus side pane, but you can also go the directly from the Unity Launcher by right clicking on the folder icon, then on the bookmarked link.
Faster than ever!

---

### Post by willowave on 2012-05-06
> **wally the duck said:**
> I know it's an old thread, but...

Users of Ubuntu 12.4 will find that this method is broken, The fix is fairly simple.
 in the vsftpd.conf file
-do NOT uncomment the "#chroot_local_user=YES" line.
-immediately after that line add "local_root=/home/{name}/Public" where {name} is the name on the user's home folder and "Public" can either be the Public folder installed by default in Ubuntu or any other subfolder you want... it just cannot be the home folder. (vsftp does not want you connecting with write privileges directly to the home folder)

Also, you'll find it is not necessary to load Avahi at all. In the Nautilus file manager window you can go to the 'File" menu and click 'connect to server' and enter the proper information. Once you connect, "Bookmark" the connection and it will not only always be there in the Nautilus side pane, but you can also go the directly from the Unity Launcher by right clicking on the folder icon, then on the bookmarked link.
Faster than ever!

Thank you :) You have good timing. I was just going to look into this again to keep my files handy until prices come down on HD's so I can get a NAS.

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/EasyHomeFileSharingWithFTPAndZeroconf](https://help.ubuntu.com/community/EasyHomeFileSharingWithFTPAndZeroconf)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012424](http://ubuntuforums.org/showthread.php?t=2012424)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

