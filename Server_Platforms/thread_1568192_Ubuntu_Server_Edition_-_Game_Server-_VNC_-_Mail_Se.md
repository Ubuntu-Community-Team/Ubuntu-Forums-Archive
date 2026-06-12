---
title: "Ubuntu Server Edition - Game Server- VNC - Mail Server"
date: 2010-09-04
forum: Server Platforms
---

### Post by TeamXlink on 2010-09-04
Hello.

I run a dedicated specialty Quake 3 Arena Server.It currently runs a stock Debian 5.05. These are the hardware specifications.

256mb SD Ram
10gb Hard Drive
Intel Celeron

I think I should be getting more speed then I am.

I would like to install Ubuntu Server.

What version is the most stable, and will provide the best speed?

I have to download my server files from the internet. Is this possible without the GUI?

Is there anyway to control my server remotely, without any impact on performance, VNC is a huge impact.

I want to run a mail server as well, is this possible with out a performance hit?

Thank you.

---

### Post by CharlesA on 2010-09-04
> **TeamXlink said:**
> Hello.

I run a dedicated specialty Quake 3 Arena Server.It currently runs a stock Debian 5.05. These are the hardware specifications.

256mb SD Ram
10gb Hard Drive
Intel Celeron

I think I should be getting more speed then I am.



You'd probably be getting more performance if you didn't use a GUI (which I guessing you are, since you have VNC installed. It's a pretty weak server if you are hosting games, considering the RAM and drive space.

> I would like to install Ubuntu Server.

What version is the most stable, and will provide the best speed?

The newest version of Ubuntu Server is 10.04, and it's a LTS release (long term support - supported for 5 years). However the minimum RAM required is 256MB.

You might be better suited for running Hardy (8.04) which has 3 years of support left on the server platform.

Also judging by the RAM specs and HDD size, I'm figuring you are running a 32-bit CPU as well, so you'd need the 32-bit version of Ubuntu Server. You can get Hardy [here]("http://releases.ubuntu.com/hardy/") and Lucid [here]("http://releases.ubuntu.com/lucid/"). The 32-bit version is listed at i386.

> I have to download my server files from the internet. Is this possible without the GUI?

Are you getting the files from an http or ftp site? You can use wget from an ssh session (use screen, so that you won't terminate the download when you disconnect)

> Is there anyway to control my server remotely, without any impact on performance, VNC is a huge impact.

Running a GUI on a server is a huge resource hog, especially if it's got not so stellar specs. You can use SSH to remotely manage the machine, just make sure to properly secure it.

> I want to run a mail server as well, is this possible with out a performance hit?

I think it depends on the mail server, but I've got a simple SMTP relay installed that doesn't use much resources.

---

### Post by TeamXlink on 2010-09-04
The files I need to download are on a file host site, megaupload.

I also forgot to mention.

There isn't a battery on the motherboard so the time and date don't save.

---

### Post by CharlesA on 2010-09-04
I don't know if you can download from megaupload with wget, but you can try.

If you aren't able to keep the correct time, you can always install a NTP client to keep the clock in sync.

Check [here]("https://help.ubuntu.com/10.04/serverguide/C/NTP.html") for more info.

---

### Post by TeamXlink on 2010-09-05
Would 8.10 be alright? 

I already have a cd of that, it is the ones you can request.

I have:

7.something
8.10
9.something
10.04 LTS Server
10.04 LTS Desktop

Is there anyway to install a desktop version get all of my files downloaded and setup and then remove everything so its a server install?

---

### Post by CharlesA on 2010-09-05
What you could do it just install 8.04 or 10.04 Server, download the files on another machine and then sftp them to the server.

You'd need to install SSH on the server first:

```
sudo apt-get install ssh
```

Then just sftp it to the server.

---

### Post by TeamXlink on 2010-09-05
Is there a simple way to install 8.10 Desktop Ubuntu and make it the equilvalent to a server install?
 
Is there a web interface for remote access, similar to the web interface of an apache server?
 
Where I can log in and just execute commands remotely?
 
Also, if I have to burn 8.04 Server, is there a way to include things with it, could I be able to make a disc with 8.04 Server that is already setup with all of my files, packages and what not?
 
EDIT: After searching I foundout how to include applications with a Ubuntu Installation CD.
 
I ran accross Ubuntu Minimal, this seems like a good thing to use, does anyone else suggest this for a server installation? Considering my hardware I thought this might be better.
 
So I guess it is between these:
 
8.04 Server
8.10 Desktop
8.04 Minimal
 
Which one is best for my purpose?
 
EDIT 2:
 
If I can fit all of my files on my 10gb hard drive, why does it make it faster to have a larger one? I have a 60gb hard drive, but it is in use, and thought it would be a waste because of the amount of free space I already have.
 
EDIT 3:
 
I figure I might as well ask all of my questions about my server here.
 
The bios is rather annoying on my server computer.
 
It won't boot if there isn't a monitor plugged in.
 
If booting wihtout a keyboard a screen shows up and says there is no keyboard, it requires you to press F1 to continue booting.
 
Without a battery it recreates all of the settings and requires me to press keys with a keyboard every time it boots.
 
Is there anyway to bypass all of this?
 
I don't think there is because it is a bios problem, but maybe there is an easy way. If it comes down to it, I might have to install a battery, wire up a device to to trick it into thinking heres a monitor hooked up, and I could probably get a cheap usb keyboard and wire the main chip directly inside the case.
 
There is no PS/2 ports, only usb ports.

---

### Post by CharlesA on 2010-09-05
The only difference (realitively speaking) between a desktop and server install is that the desktop install has a GUI installed, the server install doesn't.

I suggested installing the server version, since the machine you are trying to make into a server has pretty low specs on drive space and RAM, and having a GUI installed tends to be resource heavy. Check [here]("https://help.ubuntu.com/community/ServerGUI") for more info.

The minimal cd is used to do a net install of desktop/server IIRC.

As for running commands remotely over a web interface, you could take a look at webmin, but (IMHO) it's just easier to connect via SSH and deal with the machine that way.

If you don't turn the machine off after setting everything in the BIOS is will keep those settings. However, as soon as the machine is turned off or loses power you will be back to square one.

Best thing to do would be to replace the missing battery, then you could set it to ignore all errors and see if it'll boot without a keyboard or monitor.

---

### Post by kulshoks2121 on 2010-09-05
Try using SCP transfering large files through ssh

---

### Post by CharlesA on 2010-09-05
> **kulshoks2121 said:**
> Try using SCP transfering large files through ssh
sftp is easier to use tbh, but scp works too. :)

---

### Post by TeamXlink on 2010-09-06
> **CharlesA said:**
> The only difference (realitively speaking) between a desktop and server install is that the desktop install has a GUI installed, the server install doesn't.

I suggested installing the server version, since the machine you are trying to make into a server has pretty low specs on drive space and RAM, and having a GUI installed tends to be resource heavy. Check [here]("https://help.ubuntu.com/community/ServerGUI") for more info.

The minimal cd is used to do a net install of desktop/server IIRC.

As for running commands remotely over a web interface, you could take a look at webmin, but (IMHO) it's just easier to connect via SSH and deal with the machine that way.

If you don't turn the machine off after setting everything in the BIOS is will keep those settings. However, as soon as the machine is turned off or loses power you will be back to square one.

Best thing to do would be to replace the missing battery, then you could set it to ignore all errors and see if it'll boot without a keyboard or monitor.

I think I will choose the minimal cd because it can install ubuntu server by downloading the packages from the web and with only 20mb on the disc, I should have enough room for my server files.

Thank you.

I'm going to look into ssh.

I never thought my hardware for my server was low for linux.

I guess I won't be hosting anything on my 128mb ram, Pentium 3 pc.

---

### Post by CharlesA on 2010-09-06
It depends on the distro tbh. Ubuntu tries to "work with everything" so it does tend to bit a bit on the heavy side. You could always just stick to Debian or something like CentOS as well.

Could try Damn Small Linux on the Pentium 3 w/ 128 RAM.

---

### Post by TeamXlink on 2010-09-10
I replaced the missing battery but without a keyboard plugged in there is no way for it to work.

If I don't have a keyboard plugged in, it gives a keyboard error message that requires you to press F1 to boot.

I tried searching for an option to ignore errors, but couldn't find one, I may be looking in the wrong place, or for the wrong thing.

Currently the server has the latest Debian, but that has a gui. I thought Ubuntu was based off of Debian.

I have looked into CentOS, and for some reason, Ubuntu seems much more appealing.

CentOS, seems kind of confusing, from what I understand, it uses Redhat as its base.

It seems strange to me, Windows XP has a minimum requirement of 64mb of ram, but ubuntu Linux as well as other Linux Distributions have much higher requirements.

On any computer I run Windows or plan to windows on, I install Windows XP.

You also said that a server install is essentually a desktop install without a GUI. Does this mean I am getting all of the packages that I have no use for?

I still don't understand the advantage of running a server install or a minimum server install.

I think I'm going to use Ubuntu, because it seems to fit my needs and I can install it off of a USB Drive.

Also, can I ssh from a web browser from any pc, that way I could execute commands and manage my server while I am elsewhere.

I also acquired a dell pc, it currently has 256mb of DDR ram, abd a Pentium 4 processor.

I also found 60gb hard drive, while going through my parts box.

I think I want to continue using my current server pc, because it is about the Same of a normal Xbox 360, except its a little bit thinner. And it has a better proccesor, but that advantage might be leveled out because of the sd ram.

Thank you for the help.

---

### Post by CharlesA on 2010-09-10
Ubuntu server doesn't have any of the "desktop" packages installed.

Less packages = less stuff needing updates and less stuff at risk of exploits.

The advantage of running a server install over a desktop install is resources. The GUI uses a "boatload" of resources that could be used for serving stuff, running VMs, etc.

Check here for more info: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by TeamXlink on 2010-09-10
I'm not asking for the advantage of a desktop install versus a server install.

I'm asking about a minimum server install versus a normal server install.

---

### Post by CharlesA on 2010-09-10
There shouldn't be a difference, outside of the minimal does a netinstall vs a normal install.

---

### Post by Vegan on 2010-09-10
Yuu might want to replace your machine for a server as that old Celeron platform is way past its bets before date.

---

### Post by TeamXlink on 2010-09-10
Why, I thought the dual core Celeron's based on the Pentium 4 processors were better then the standard Pentium 4 processors.

---

### Post by CharlesA on 2010-09-10
Celerons are stripped down CPUs. If you have a single core P4, the celeron is better, but if you already have a dual core CPU, the celerons are garbage.

Check here: [http://computer.howstuffworks.com/question268.htm](http://computer.howstuffworks.com/question268.htm)

---

### Post by TeamXlink on 2010-09-11
> **CharlesA said:**
> Celerons are stripped down CPUs. If you have a single core P4, the celeron is better, but if you already have a dual core CPU, the celerons are garbage.

Check here: [http://computer.howstuffworks.com/question268.htm](http://computer.howstuffworks.com/question268.htm)

All I have are single core Pentium 4's, so the Celeron is better in this case.

---

### Post by CharlesA on 2010-09-11
> **TeamXlink said:**
> All I have are single core Pentium 4's, so the Celeron is better in this case.
In that case, yeah. Good luck with the minimal install. :)

---

### Post by TeamXlink on 2010-09-11
> **CharlesA said:**
> In that case, yeah. Good luck with the minimal install. :)

Thank you.

Also, would a pc with these specs improve performance for my server?

80gb hd
1gb ddr2 ram
Pentium 4

I also forgot to mention that most of the clients that connect to my server are using modems and the maximum clients that can be connected to the server at one time is only four.

Thank you.

I think I  might as well as my other question here.

I currently have a server running Ubuntu 8.10 Desktop, I would like to make this server a headless server but don't know how to set it up.

It runs an mgetty on the modem, I want to make it auto-answer.

I currently have to do this:

Start dialing on other device.

Run this command on the server:

sudo mgetty -D /dev/ttySHSF0

Then about 2 seconds later run this command:

sudo killall -USR1 mgetty

Thank you.

---

### Post by CharlesA on 2010-09-11
If you've only got 4 clients connected at a time, then either of those would work. :)

No idea on what to do with the modem thing. :(

---

### Post by TeamXlink on 2010-09-11
So if I download the minimal cd from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I can use it to install a server install, right?

---

### Post by CharlesA on 2010-09-11
> **TeamXlink said:**
> So if I download the minimal cd from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I can use it to install a server install, right?

Yes.

---

### Post by TeamXlink on 2010-09-12
Thank you.

But I loaded the minimal install disc.

I typed in cli

I was expecting to at some point in time, get a list of packages I can install.

---

### Post by CharlesA on 2010-09-12
Did it already install the base system?

If so, run this:

```
sudo tasksel
```

---

### Post by TeamXlink on 2010-09-12
It is all fine and dandy.

I installed openssh and it is working great.

My only problem now is getting my server files onto the server pc.

I tried setting up a ftp server on another linux pc using vsftpd but on that pc I couldn't even get it to allow me to upload the files.

I tried putting my hard drive in an external drive enclosure but the linux pc didnt detect it.

Any ideas?

Thank you.

---

### Post by TeamXlink on 2010-09-12
I got it to work by setting up an FTP server in windows xp with ServU.

I used the default ftp client on the ubuntu 8.04 cli install.

I have no idea where it put the files on my pc.

IS there anyway to find out?

EDIT:

I managed to find the files and put them in the correct directories, however.

When I had the gui install, I used this command to start the server:


./q3ded +set dedicated 2 +set net_port 27970 +exec server.cfg

The problem is when I type that in, this is what it says:

sudo: ./q3ded: command not found

So, I tried doing it like this:

sudo bash ./q3ded +set dedicated 2 +set net_port 27970 +exec server.cfg

It then tells me this:

./q3ded: ./q3ded: cannot execute binary file

Does anyone know how to fix this?

---

### Post by CharlesA on 2010-09-12
It would have been easier to just use an sftp client such as Filezilla to transfer the files to the server, since it uses SSH.

What are the permissions on that file? It should be rwx.

Check here as well: [http://tldp.org/HOWTO/archived/Game-Server-HOWTO/quake3.html](http://tldp.org/HOWTO/archived/Game-Server-HOWTO/quake3.html)

---

### Post by TeamXlink on 2010-09-12
> **CharlesA said:**
> It would have been easier to just use an sftp client such as Filezilla to transfer the files to the server, since it uses SSH.

What are the permissions on that file? It should be rwx.

Check here as well: [http://tldp.org/HOWTO/archived/Game-Server-HOWTO/quake3.html](http://tldp.org/HOWTO/archived/Game-Server-HOWTO/quake3.html)

My server files are already setup.

That tutorial also uses ./q3ded

Which was what was giving me problems in the first place.

---

### Post by TeamXlink on 2010-09-14
I'm trying to compile it from the source.

However when I try to download the source from my ftp server it gives me an error about read only file access.

Also, you mentioned filezilla, isn't that a gui based program?

I would rather use the stock programs to do things, as I don't want to clutter up the file system with "run one" packages.

However a very simple basic explorer would be great full, but not a full gui. It would be a lot easier to be able to plug in my usb drive and get them from there, and if it is only 1 package I could remove it when I was done with it! Does such a thing exist?

And is sftp a more secured version of ftp? At the moment I am not worried about security, I might worry about that after I get everything setup.

Thank you for the help so far.

Also, another reason I don't plan on securing my pc until I get everything setup is because I will be blocking every port accept for 3 ports, because thats all I will need. And those ports will be in use constantly. I still need to find a way to go about doing this though, I will worry about it when I get everything setup.

---

### Post by CharlesA on 2010-09-14
Yeah sftp is included with the ssh package. It's encrypted, which ftp is not.

It's command-line based, so you can pull the files over that way.

---

### Post by TeamXlink on 2010-09-15
> **CharlesA said:**
> Yeah sftp is included with the ssh package. It's encrypted, which ftp is not.

It's command-line based, so you can pull the files over that way.

Thank you.

I got the file onto my server by using wget to download it from the only host I could find.

Now that I got the file onto my server, I am trying to run it, but I'm having problems with it.

It is a .run file

This is the command I use:

```

sudo bash ./linuxq3apoint-1.16n.x86.run

```

This is the output:

```

Verifying archive integrity...tail: cannot open '+6' for reading: No such file or directory
Error in check sums 2988782453 4183380385

```

Now, I know its not a checksum problem because the md5 matches.

I was searching online and I cam across a post about someone who was having a tail error in fedora, one of the replies stated that the way older Linux kernels handled the tail is different then newer ones. Could this be the problem?

Another weird thing is the .run file compiled find in a Desktop Ubuntu 8.10 install.

Thank you for the help so far!

---

### Post by CharlesA on 2010-09-15
Does it have execute permission?

Also, try just using "sh" instead of bash, even tho there shouldn't be any differences.

---

### Post by TeamXlink on 2010-09-15
> **CharlesA said:**
> Does it have execute permission?

Also, try just using "sh" instead of bash, even tho there shouldn't be any differences.


Same problem except I got a different checksum number for the error.

---

### Post by CharlesA on 2010-09-15
I don't know what the problem could be. A checksum error normally means the file is corrupted.

---

### Post by TeamXlink on 2010-09-16
> **CharlesA said:**
> I don't know what the problem could be. A checksum error normally means the file is corrupted.

It has nothing to do with the checksum.

Its a version bug wtih tail, this bug is in multiple linux distros.

I tried the fix from here, [http://forums.fedoraforum.org/archive/index.php/t-111386.html](http://forums.fedoraforum.org/archive/index.php/t-111386.html) But it gave me other errors.

---

### Post by TeamXlink on 2010-09-17
Alright, I got it to install, but I am still getting the same error I had gotten before:

```

q3ded: cannot execute binary file

```

Any ideas?

Thank you.

EDIT:

I got it working, and I can't what I had to do to get it working.

Thank you everyone!

Things I have learned:

What is ssh
How to use ssh
How to use command line ftp
How to use wget
How to use nano
How to install a Cli install
How to use the Linux Terminal
Users on the Ubuntu forums are very nice
General sh scripting
Linux without a GUI isn't so bad!

EDIT:

I have another question

If I login to my server under its default account through ssh and start my server, does it continue when I disconnect from ssh?

EDIT2:

I'm also trying to secure my server.

I can use the ufw to allow or deny access to a single port, but there has to be an easier way then just going through all xxxx setting them up to deny.

I want every port to be blocked except for three ports.

---

### Post by CharlesA on 2010-09-17
As long as you start the server in the background by adding "&" to the end, it'll terminate when you disconnect. It's either that or start it in a screen session and detach it.

Just tell it to deny all and allow only those ports you want open.

```
sudo ufw default deny
```
```
sudo ufw allow (port number)
```

---

### Post by TeamXlink on 2010-09-17
Well, I have it running on boot by editing a line in the rc.local file, it works fine.

I was originally worried about it disconnecting when I disconnect from ssh, but my new problem is this:

When I login to it through openssh I can't see the status for the server like I can on an actual monitor connected to the pc.

Thank you, for the help!

---

### Post by CharlesA on 2010-09-18
Try using screen. I don't know if the server output anything to the GUI or not, but screen is pretty handy.

Check [here]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/").

---

### Post by TeamXlink on 2010-09-18
> **CharlesA said:**
> Try using screen. I don't know if the server output anything to the GUI or not, but screen is pretty handy.

Check [here]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/").

That will allow me to login through ssh and see the terminal session with the server console?

My existing script is this:

```

cd /home/alexander/Quake3
./q3ded +set dedicated 2 +set net_port 27960 +exec server.cfg

```

I call it in /etc/init.d/rc.local

By having this at the end of the file.
```

sudo bash /home/alexander/Quake3/Server.sh
echo 'Quake 3 Dedicated Server Started'

```
All I would have to do is edit the Server.sh script to be like this, right?
```

screen
cd /home/alexander/Quake3
./q3ded +set dedicated 2 +set net_port 27960 +exec server.cfg

```

Then when I login through ssh all I have to do is this:

```

screen which

```

Right?

I also don't need to output anything to the GUI because I don't have a GUI, unless you meant the terminal?

Thank you.

EDIT:

I installed screen and tried that and it didn't work.

It came up with a window that talked about screen and required me to press enter or space, so I plugged in my keyboard and did that and it didn't start my server.

I tried adding this to the beginning of my Server.sh file.
```

su -c "screen -m -d -S $srnname" $user

```

So my whole Server.sh file looks like this:

```

su -c "screen -m -d -S $srnname" $user

cd /home/alexander/Quake3
./q3ded +set dedicated 2 +set net_port 27960 +exec server.cfg

```

It started my server but I couldn't login to a screen session from ssh and there wasn't any screen sessions listed in ssh when I did screen -ls.

---

### Post by CharlesA on 2010-09-18
I don't know how you can launch it from screen automatically, unfortunately.

You might have to just launch it manually after a reboot or something.

EDIT: It looks like you can create a new detached screen by running this command here:

```
screen -d -m
```

---

### Post by TeamXlink on 2010-09-18
> **CharlesA said:**
> I don't know how you can launch it from screen automatically, unfortunately.

You might have to just launch it manually after a reboot or something.

EDIT: It looks like you can create a new detached screen by running this command here:

```
screen -d -m
```

I will try it out, thank you!

EDIT:

I was able to attach to the screen, I had to use sudo because the server is ran under root because it is called from rc.local, but my server terminal/console didn't show up.

Thank you.

EDIT2:

I've been playing around with this, trying to get it to work, and I think these are the steps needed to get it to work, I don't know how to accomplish these steps though.

Start an attached screen

Run my commands

Detach screen

---

### Post by TeamXlink on 2010-09-25
I still haven't got the screen thing working but I also have a new question.

It currently has a 10gb hard drive.

Everyone says you should have a large hard drive to host a game server.

Would there be a speed increase at all if I installed a 60gb hard drive?

Thank you.

---

### Post by CharlesA on 2010-09-25
> **TeamXlink said:**
> I still haven't got the screen thing working but I also have a new question.

It currently has a 10gb hard drive.

Everyone says you should have a large hard drive to host a game server.

Would there be a speed increase at all if I installed a 60gb hard drive?

Thank you.

I doubt it'll make a huge difference. It's only a matter of storage.

Also check [here]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/") for info on screen.

---

### Post by TeamXlink on 2010-09-25
> **CharlesA said:**
> I doubt it'll make a huge difference. It's only a matter of storage.

Also check [here]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/") for info on screen.

When you say huge difference, do you think it will make a noticeable one at all? even if it is just boot-up time?

Thank you, for the page on screen I think I now know a way to get it to work for me.

Another thing, how do I send a directory through ftp?

I want to be able to download and upload a folder that has files in it and sub folders with files, but I want to keep the directory structure the same I think this means I need to do it recursively.

Thank you.

---

### Post by CharlesA on 2010-09-25
There won't be any noticeable difference in speed.

You'd probably have to use something like clonezilla to do a recursive transfer. I'm not sure how to do it from the command line.

---

