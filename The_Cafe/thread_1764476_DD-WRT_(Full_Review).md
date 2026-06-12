---
title: "DD-WRT (Full Review)"
date: 2011-05-21
forum: The Cafe
---

### Post by toupeiro on 2011-05-21
Just wrote a review up on my personal page about my first dive into dd-wrt.  Quite amazing stuff.  I realize its been around a while, but I thought I would share it here.  it's quite wordy, but hopefully it benefits somebody:

Cheers! 

-T


------------------------------------------------------

Alas.  The main DD-WRT system is completed.

 

So I probably did my install a little non-standard from most people because my wife and I are both linux users, but I'm going to share with you some steps I took to make this work and work well, and I'll address my method of approach to security.

 

 

**_A little bit of history behind this: _**

 

Any IT guy worth their salt should be using at least one type backup system for their important files at home.  CD, Flash drives, network storage or any combination of these..  Some time ago, I started to use the luckybackup program in the ubuntu repositories for my wife's computer and my own.  Luckybackup is basically a very user friendly and elegant frontend to rsync and cron and works for local file copies and SSH file copies across the network. In short, it gives you a nice pretty window to use to schedule when you want to do backups and what exactly you want to backup.   To keep things simple, I just attached a big beefy USB drive to my computer, created a few SSH keypairs (I hate passwords, and I will get into this later) and we were off.  Well, sort of.  One big problem came up.  I became obsessed with how much we were paying for tier 3 power this day and age in California and did a little math on how much it was costing us to leave just my computer on year round. (like I've done forever.)  The number was significant, and shocking...  Granted, I tend to run beastly systems with huge power supplies, but I never expected the number I saw, and from my bills, I was right.  So, that meant that backups were only going to run while my computer was running.  At the time, I was also able to stream my entire library of music and any video if desired to any device that could hit the web.  I put all that to rest until I could find the right solution. 

Now, I could have solved this problem many ways.  I was considering Wake-on-LAN but that just really wasn't the solution I wanted because I would have to configure every device that hit this storage to be able to do it.  I wanted something online all the time. I've looked into all of these NAS in a box products that have been coming out lately and for the price and what I was wanting it for, it just wasn't that impressive.   Whatever I did to fix this had to be smarter than a bunch of spinning disks on a network.  I was really starting to lean towards a freeNAS suite on top of a mini-ITX system, but I just never got motivated enough to really dive into it.

Then, my coworker started talking about DD-WRT and what you can do with it.  I knew the name sounded familiar because a few of my coworkers out of town were using this I believe to tie into google voice and get free USA calling (on the roadmap for me now, by the way. :) )  My first thought was that there is no way my router would have enough RAM to run the software needed to host my media streaming stuff.  Thats when he pointed me to the ASUS RT-N16.  For a router under $100 to have 128MB of RAM and a 32MB ROM (of which dd-wrt-mega with all the NAS Features requires roughly 6-7 ROM and consumes about 50MB of RAM) is quite impressive. Add on the 1GB ports and wireless N and you have an amazing little router here.  Then I started googling about what people have done with it, and when adding a set of software (basically a linux repository) called optware, this thing can literally do everything I wanted, (after all, routers do stay running all the time) including host all the necessary parts to run my streaming media server, and it was going to cost me less about 75 after shipping to do it!  Sold!

 
[U]**installing dd-wrt:**
[/U]
First things first, lets not fool ourselves.  We're dealing with ROM here, and cpu's made by companies like Broadcomm, not intel or AMD.  In other words, this is not your standard PC you're installing software/firmware on, **_and there is always the risk of bricking your router which is why its important to read the links I'm providing_**.  Most set-top devices use what are called MIPS processors, so your average applications you would download would never work on them.  There is plenty of really helpful documentation here: [http://bit.ly/m7vCh](http://bit.ly/m7vCh)  to help you get started.  For starters, read a thread titled "the peacock thread" regarding how to "hard reset" your router versus a regular reset.  These are important steps that apply to almost every type of home router out there, and you will need to know them to install dd-wrt properly.

Next, you'll want to download the version of DD-WRT that corresponds with your router.  You can find this using the router database here: [http://bit.ly/8c6q32](http://bit.ly/8c6q32)

Finally, you will want any router specific instructions to flashing your router that might not be covered by "the peacock thread".  There is a pretty comprehensive list of instructions for different routers here:

[http://bit.ly/di9E5t](http://bit.ly/di9E5t)

Now, if you don't find your router here, that doesn't mean it won't work, it just means it hasn't been documented, and you should do some specific google searches for your router model to see if anyone has done this with your router before proceeding into an untested install if this is your first time.  Be sure you do a little research on what versions of dd-wrt there are, because they are optimized for different uses.  Everything will be described in the links provided about the versions.  I won't go into all the things DD-WRT can do besides what I am using it for, but lets put it this way, it gives your home router an enterprise class set of features (Bridging, Vlan tagging, and multiple wireless networks just to name a few) and it costs nothing for the firmware.

 
[B][U]
Storage:[/U][/B]

 

Rather than buy a separate drive, I opted to use a wall-powered 1TB external USB drive that I already owned and was using for our backups previously.  It had a linux filesystem already on it (though one too new, but that'll come later).  I made a realization that home use routers do not have beefy power supplies, and that buying a USB powered hard drive could potentially overload the thing.

DD-WRT says it can recognize and use FAT32 drives, however I highly recommend formatting the drive with the EXT3 filesystem.  This can be done very easily by booting to a linux live-CD and using a tool called gparted.  Why?  Because FAT filesystems have issues with single files of a certain size.  For example, if you had an ISO file of a full double-layer DVD, a fat32 filesystem would likely not be able to access it.  EXT3 does not have this issue.  Booting to this CD and creating the EXT3 partition on a USB or external hard drive will not make any changes to your computer!  If you just don't ever see that happening, then using FAT32 will probably work out for you.

There is a guide to setting up USB storage here: [http://bit.ly/mtm1gw](http://bit.ly/mtm1gw), but I will try to simplify this for you.  Once you've flashed your router, go to the Services | USB tab and enable all the types of USB support.  When it asks you where to mount the USB drive, select /opt.  For your information, the NAS tab simply turns on an FTP server.  Do this if you want an FTP server. :)  In fact, if you are afraid of, or inexperienced with linux, turning on the FTP server, defining your password through the web gui, will give you the basic remote storage capabilities you are looking for. **_ If you wanted to, you can stop here_**, but if you care about things like mounting that storage as a drive letter (Some FTP clients can do this), account security and some other really cool tools you can download for your new linux based router, then I would recommend reading on.

 

 

 

 

 

 

 

You're still reading....  OK good! :)


**_Software:_**

So now you've added this drive to your router, so what else can you do with it?  Well, if you used EXT3 like I recommended, the possibilities are more than if you just used FAT32 because you can now use native Linux filesystem security to seperate and restrict things down as well as other goodies depending on how far you want to go with your configuration.  Why is this important?  I will go into this at the beginning of the security section..

 

First, lets talk about a suite of software called optware.  Just like it might sound, optware is going to be installed in /opt.  If you remember in one of the above steps, you told dd-wrt to mount the drive in /opt.  There was a very good reason for that. :)  To install the optware suite, you need to log into your routers command line.  In windows you can use the built in telnet client, or download a suite of tools called PuTTY to use SSH (which I recommend for reasons later discussed in this post)

1) Telnet/SSH to your router's IP address, and login with the account name and password you set when you installed dd-wrt.
2) verify your disk is mounted to /opt like you expect.  type: 'mount' (without quotes) then press the enter key.  You should see a line like /dev/discs/disc#/part# mounted to /opt.  This is the device path to your external drive as seen by your router.  If you do NOT see this here, please refer back to the USB setup guide linked above for troubleshooting this.
3) run the following command: 
```
wget -O /tmp/prep_optware [http://wd.mirmana.com/prep_optware](http://wd.mirmana.com/prep_optware)

```
4) run the following command:

```
sh /tmp/prep_optware
```

Now, wait while the software is downloaded from the internet and is installed.  It takes about 5 minutes or so..   Optware enables so many things to you.  Asterisk servers for VOIP service, database servers, even torrent daemons to download stuff without tying up your computer.  For full disclosure of everything optware can do for you, I recommend digging into the wiki here: [http://bit.ly/cSpQUp](http://bit.ly/cSpQUp)


**_Security:_**

In the storage section, I mentioned the ability to create different user accounts and seperate connectivity by accounts and native linux file permissions.  This is important because, quite frankly, you do not want to fat finger something as the admin account of your router!  Most of the problems windows systems have been riddled with over the years has been greatly due to the fact that the user account was the granddaddy admin account of the entire system.  Having an account for yourself and anyone else on your network seperate from the root account helps keep data better protected on a device that runs 24/7 and also has your internet connection wired directly into it.  It keeps the permissions with the files so if you want to keep your hacker teen out of your private files, you can do so, or at least give him or her enough road blocks that you'll know he/she is trying hopefully before they succeed. :)

 One of the things optware can provide is a samba server.  For you winders guys out there, Samba is a toolset in linux that allows you to create windows shares amongst other things to be accessed by native windows clients.  But before we get there, lets define a few things.

First thing I did is install the good old fashioned adduser program.  to do this type:

```

ipkg-opt update <enter>
ipkg-opt install adduser <enter>
```

 
Now, I add the user accounts by typing:

 

adduser <username_goes_here> -h /opt/<username> 


the -h specifies where the home directory will be created.  put it on the external drive, anywhere you want if you dont like my example above.

Now, I know what you're thinking... what about the passwords???  Well guess what, in either their infinite wisdom, or ignorance, optware did NOT include the passwd tool!  So these accounts you created will not have passwords, in this case meaning they cannot login!!  To me, this was WONDERFUL!  Why?  Because I hate passwords emmensely.  As an admin, I have to remember far too many of them, and re-remember them every so many days when I reset them all.  Where I can and where it makes sense, I like to use key based authentication.  A.k.a. SSH Keys!  Here's how you do this:

 

If you have a linux computer:

 

type ssh-keygen and walk through the rsa key generation.  do not put in a passphrase when requested (unless you really want to)

 

in your home directory there will be a directory called .ssh.  In that directory, there will be a file called id_rsa.pub.  This is your public key that you put on other systems. Open this file and copy out its contents to the clipboard. (Do NOT open the id_rsa file.  this is your PRIVATE key, and you do NOT want to give this one out.

Now, as the admin account on your router, run the following commands:
```

 

mkdir /opt/<username>/.ssh

echo (right-click and paste your ssh key to the command line) > /opt/username/.ssh/authorized_keys

chown <username>:<username> /opt/<username>/.ssh

chmod 700 /opt/<username>/.ssh

```
 

You have just saved your public key from your linux computer to your account on your router, and set security so that only that user account (and the router admin account) can access the directory where the keys are saved..  you can now do: ssh <router ip address> -l <username> from your computer and log in without a password! as well as use scp and rsync all securely and all without passwords

 

If you have a windows computer:

 

Download and save the following PuTTY tools from here. [http://bit.ly/1kyS98](http://bit.ly/1kyS98)
putty.exe
puttygen.exe

Run the puttygen.exe tool to generate your keys and follow the instructions provided.
Copy the Public key to the clipboard, then save both the public and private keys to files on your windows computer.
telnet(or use putty.exe for ssh) to your router with the admin account and run these commands:

 
```

mkdir /opt/<username>/.ssh

echo (right-click and paste your ssh key to the command line) > /opt/username/.ssh/authorized_keys

chown <username>:<username> /opt/<username>/.ssh

chmod 700 /opt/<username>/.ssh

```
 

Now, you may use WinSCP (google it) and point it to your newly saved private key file and securely FTP to your router without the use of a password.  You can also use putty to login as you without a password by supplying the path to your private key under the left hand side options below Connection | SSH | Auth.

If you actually want to use drive mounting to a windows machine.  There are a few options.  Dokan_sshfs is availableL [http://bit.ly/Hr1DR](http://bit.ly/Hr1DR) though I've never messed with it. Alternatively, you can use this link to learn how to configure samba on DD-WRT:  [http://bit.ly/myYCvf](http://bit.ly/myYCvf)  I would think the dokan_sshfs is a better route to go because most routers do not have a terrible amount of RAM.  sshfs puts the workload on your PC's end and uses the native SSHD provided with DD-WRT. 

Above and beyond this, I chose to install lighthttpd and postgreSQL which I need to host my media streaming application.  These steps were very easy to do, but I will not document them as they are very specific needs.  This is only the beginning of what you CAN do.  If you are not new to linux or care to learn more about it, you can configure sudo, add DNS authentication to your SSH keys and so many more things to really get defined about your security, as well as open up so many more uses for your dd-wrt router. However, the above steps are what I would consider your basic security steps to take on a router that is now also a media server and backup server.

[B][U] 

So what have we learned?[/U][/B]

For less than $100, you can have one hell of a router and NAS, chalk full of applications and tools, and last but not least, full SSH encryption for security purposes, all without having to remember another password! I just wanted to share this little project with everyone.  Maybe you will never do it, but if you ever wanted to, this is here to help!  Its easy, you will learn a lot, and you will have a pretty awesome home network when its all said and done!!

 

Cheers!

---

### Post by CharlesA on 2011-05-21
Nice write up. :)

---

### Post by toupeiro on 2011-05-21
> **CharlesA said:**
> Nice write up. :)

Thanks man!  It was a fun little project that I got a lot out of and I thought other people may be interested.  There is still so much stuff out there, this barely scratches it. :)

---

### Post by Spr0k3t on 2011-05-21
I won't even consider a router unless I know for a fact I can throw DD-WRT on it.  Good writeup for the newbs.

---

### Post by CharlesA on 2011-05-21
> **Spr0k3t said:**
> I won't even consider a router unless I know for a fact I can throw DD-WRT on it.  Good writeup for the newbs.
Same here, now that I've had a taste of what it is capable of. (I run it on my crappy dlink router)

---

### Post by toupeiro on 2011-05-21
> **Spr0k3t said:**
> I won't even consider a router unless I know for a fact I can throw DD-WRT on it.  Good writeup for the newbs.
:KS:KS:KS
Cool, thanks!  It was written for just that intended audience.  This was my first stab at it so its pretty easy to think about doing this in the terms of someone who hasn't done it before.  I can see where someone not too horribly technical would have some anxiety about doing this so I really wanted to lay it out as simply as I could.  It really isn't hard to do if you follow the instructions.  I can't foresee myself ever owning another router I can't do this to in the future.  I already flashed my old linksys with it and bridged it across powerline ethernet to expand my wireless coverage.  Amazing to be doing this with commodity equipment!

Also plan on dropping a donation to dd-wrt of what its enabled me to do.  Need to keep this project funded! :)

---

### Post by kerry_s on 2011-05-21
i use 2 dd-wrt's set up as wireless extenders. both made from U.S.Robotics USR5430 wireless gaming bridge.

---

### Post by FuturePilot on 2011-05-22
I would also recommend reading this thread for some important points.

[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=51486]("http://www.dd-wrt.com/phpBB2/viewtopic.php?t=51486")

---

### Post by matthew on 2011-05-22
Nice post. You mention some ideas I haven't tried, and I've used DD-WRT on my wrt54g (v2) for many years. Great stuff!

---

