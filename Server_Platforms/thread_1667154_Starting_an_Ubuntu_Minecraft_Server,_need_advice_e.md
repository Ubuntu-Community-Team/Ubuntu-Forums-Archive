---
title: "Starting an Ubuntu Minecraft Server, need advice etc."
date: 2011-01-14
forum: Server Platforms
---

### Post by willystylee on 2011-01-14
Hi everyone!

Ok so i'm going to explain my situation tot he best of my ability. I've  been a mostly unsatisfied Window's user all my life, and always have  just stayed with MS because of the common reasons i'm sure you Linux  guys all have heard before. A little sidenote, my uncle has always been a  linux guy, and upon researching the os personally i was reminded of  fond memories of him trying to explain the OS and why it was so great. I  was reminded of random linux terms like 'Gnu' and such. :smile:

So anyways, to the main point. I've been running a successful Minecraft server ([http://www.minecraft.net/download.jsp](http://www.minecraft.net/download.jsp))  for the past couple months and it got to the point where even having a  decent dual core cpu and 8 gb of ram wasn't cutting it when it came to  running the server (hey0 actually) and myself playing in the server at  the same time, pretty java intensive, and i dont think even 8 gb's of  ram wasn't working well as the world/server files got larger and larger.   So i decided to rent a dedicated game server from xenonservers.com.  Well long story short that was a lesson learned, lag wasn't solved and  it seemed i was actually **paying** for a downgrade and not an upgrade at all. 

So that brings us to present time. After seeing many signs of what  looked like many people saying that a linux server definitively beats a  Windows run server any day, i decided i was going to go that route. I  purchased a Dell Poweredge 1850 off ebay, has 8 gb of ram and dual 64  bit 3.4 ghz Xeons'. I'm planning on just running the machine in my room,  i even have a perfect cubby in my desk that rolls out where i'm  planning on putting it. I purchased a KVM switch as well, for ease of  operation. I'm going to be running Ubuntu Server on it, i already  followed the steps the Ubuntu website provided for putting it onto a usb  drive and installing it from there. I am excited to get it all set up  and learn the new OS! 

So basically i am making this thread asking for advice regarding my  plans.. are there certain things i should/could do to make it run most  efficiently? Hows the best way possible to go about doing this? Are  there other distros that would be a better choice?

Thanks everyone, i really appreciate any help/advice anyone could provide.


Edit:

I'm sorry for the duplicate threads, it wasn't loading... :(

---

### Post by sj1410 on 2011-01-14
your plans are perfect and Ubuntu server is a good choice. make sure that its a LTS version. the current LTS version that you should use Ubuntu 10.04 64bit server.

Thats my personal choice of using LTS and i see it more stable from the others.


Good Luck!!!


meanwhile can you explain me what minecraft is...... If its something related to games i am interested in it.

plese get back to me on swapnil dot indore at gmail dot com

---

### Post by willystylee on 2011-01-15
> **sj1410 said:**
> your plans are perfect and Ubuntu server is a good choice. make sure that its a LTS version. the current LTS version that you should use Ubuntu 10.04 64bit server.

Thats my personal choice of using LTS and i see it more stable from the others.


Good Luck!!!


meanwhile can you explain me what minecraft is...... If its something related to games i am interested in it.

plese get back to me on swapnil dot indore at gmail dot com


Thanks for the response!! Thanks for the input. Minecraft is a open world exploration & construction are the main aspects of the game. Its super fun and quite addictive! The variety of construction possibilities is very wide! Here are a couple youtube videos of some amazing things people have built!

[http://www.youtube.com/watch?v=MMW_jraSjq8](http://www.youtube.com/watch?v=MMW_jraSjq8)

[http://www.youtube.com/watch?v=kn2-d5a3r94](http://www.youtube.com/watch?v=kn2-d5a3r94)

it's a pretty java intensive program!

---

### Post by sj1410 on 2011-01-15
Thanks a lot. Pretty interesting.

Actually i am looking for some game developers so thought it might be helpful. Thanks a lot.

---

### Post by elico on 2011-01-15
good choice ubuntu..
10.04 LTS is my version also.
if you needs is just to host this game it will probably bee more then you really need.
notice that you can make it work faster and redundent with raid arrays..

---

### Post by Thirtysixway on 2011-01-15
Yes as everyone else said, go with 10.04.  This way the server is supported for 5 years and once you set it up you won't have to do too much to keep it going.

I would follow the minecraft guides
[http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Linux](http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Linux)
[http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

With server version you don't get a GUI, but that's good because then you're not wasting ram :).  Make sure to either install OpenSSH so you can connect into it and edit settings, or have a monitor/keyboard hooked up to it. So some of the linux steps on that guide are made for GUI, just adapt to command line (like making a folder is mkdir foldername)

---

### Post by Thirtysixway on 2011-01-15
Yes as everyone else said, go with 10.04.  This way the server is supported for 5 years and once you set it up you won't have to do too much to keep it going.

I would follow the minecraft guides
[http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Linux](http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Linux)
[http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

With server version you don't get a GUI, but that's good because then you're not wasting ram :).  Make sure to either install OpenSSH so you can connect into it and edit settings, or have a monitor/keyboard hooked up to it. So some of the linux steps on that guide are made for GUI, just adapt to command line (like making a folder is mkdir foldername)

---

### Post by Thirtysixway on 2011-01-15
(stupid server. doublepost :s )

---

### Post by willystylee on 2011-01-15
> **Thirtysixway said:**
> (stupid server. doublepost :s )


Hey thanks for the advice! Yeah i was getting trolled by the lag too yesterday XD.


SO the server i bought (coming in the mail soon) the details on it said no RAID. I don't really know that much about what raid does a friend of mine tried explaining it like it's makes HDD's backup to the other one? Sorry if that's a stupid question...

Also, so the version i put onto my usb drive ([http://www.ubuntu.com/server](http://www.ubuntu.com/server)) is by default GUI-less? So basically i will be operating it from a command line? (That's what i wanted).

Can someone explain OpenSSH for me? Is there anything else that i need to do to the server before setting it up for minecraft? Again i'm a total newb with linux! Some links you guys could provide?

---

### Post by darthrax on 2011-02-19
Hi willy,

i've been running a minecraft server (ip: minecraft.co.in) on an old acer dual core machine running ubuntu 10.04 LTS, since November 2010. its got a 2.0 ghz processor, 2gb ram and a 320gb hdd.

Its not the fastest machine i have (i play on that one :)) but it gets the job done. As my server became more popular, a lot of people started complaining of lag. Now, being the good admin i am, i scoured the internetz for a solution, and heres what i came up with. 

The two main choke-points were the internet connection and the size of the world. Im getting a new connection right now, so that should solve the internet problem. For world size, there's lots of posts saying that a SSD can improve the server speed. This is because the minecraft map is stored in a HUGE number of individual files for each 'chunk' (16x16x128 blocks) of the world. ATM my world is ~112mb and ~34000 individual files ([Here's a MAP]("http://zoom.it/QTOh")). For each player online, the server loads a 40x40 chunk 'Active' region around them, and the balance chunks loaded are dependent on their view distance. The 'Active' region is basically where mobs spawn, trees grow etc. So, for EVERY player, there are a lot of HDD reads and writes that have to take place. This is where an SSD with its blazing r/w speeds comes in handy.

I personally cannot afford a SSD at the moment so i went and did one better, i used a RAMdisk. While the average SSD reads at ~700mbps, a RAMdisk reads at ~1300mbps. (i read these figures somewhere, i dont remember exactly where and they might not be accurate but RAM is a helluva lot faster than any SSD). The disadvantages of a RAMdisk is the volatility of your data, which basically means that if the power dies, your data goes too. This can be avoided with a regular backup and some smart scripting. Ubuntu has a default ramdisk (located at /dev/shm) which takes not more that half your ram. Which basically means that in my setup, i have a 1gb (max) ramdisk, which is more than enough to run my world.

So here's what i did.

Assuming that you have a folder layout like this:
/home/$USER/Desktop/MCSERVER
/home/$USER/Desktop/MCSERVER/world/
/home/$USER/Desktop/MCSERVER/minecraft_server.jar
etc.

Step 1. Move world to permanent storage
```
cd /home/$USER/Desktop/MCSERVER
mv world/ world_storage/
```

Step 2. Link the world to ramdisk
```
mkdir -pv /dev/shm/minecraft/world
ln -s /dev/shm/minecraft/world/ .
```

You will now have a folder called world in you MC directory which is a symbolic link to the folder on the ramdisk.This folder is currently empty, and we will populate it with our modified startup script:

```
#!/bin/sh

RAM="/home/$USER/Desktop/MCSERVER/world/"
HDD="/home/$USER/Desktop/MCSERVER/world_storage/"

mkdir -pv /dev/shm/minecraft/world
rsync -r -t -v "$HDD" "$RAM"

java -Xms1024M -Xmx1024M -jar Minecraft_Mod.jar nogui
```

So when we start the server(even after a power outage), the world gets copied to the ramdisk and then the server starts. We now need to create a script which will copy the world from the ramdisk back to the hdd at regular intervals. Save the following script as saveworld.sh


```
#!/bin/sh
RAM="/home/$USER/Desktop/MCSERVER/world/"
HDD="/home/$USER/Desktop/MCSERVER/world_storage/"

rsync -r -t -v "$RAM" "$HDD"
```

Now all we have to do is add a simple cron job and we're done

```
crontab -e
```

This will open the editor to add a cron job. I am saving my files every 5 minutes but you can change that to suit your needs.

```
*/5 * * * * bash /home/<your username>/Desktop/MCSERVER/save_world.sh &>/dev/null
```

That's it... Your Done...

A little advice against griefers: TAKE MULTIPLE BACKUPS

I use Back in Time (available in the repos) to backup my entire minecraft folder every 15 minutes. Its hassle free, lets you restore from multiple restore points and saves only changes into the backup. So if your world is ~20mb and players make changes worth ~1mb, the second backup will not be 21mb but just 1mb, which saves A LOT of hdd space, and game time lost to griefers.

---

### Post by wog on 2011-03-09
Since I don't actually know how to script things, could someone please make up a script that sets up the ramdrive and the cron job so when the power goes out in my particular part of the world, I can just run this thing and expect it to work?

...or explain to me why I don't need to?

I can do each and every part of this by hand, but it would really be nifty if there were a script for setting up the server and then taking it down afterward.

If that's asking too much, where can I go to learn how to write a script, myself? Is there a good webpage for this stuff, somewhere?

---

### Post by t3k on 2011-03-10
Your setup sounds entirely ideal. I now plan on configuring my server in this fashion. I have a few questions though if you don't mind..

Is /dev/shm/ always a ramdisk? What is this file used for? cd /dev/shm/ ls currently lists mine as empty.

Is there any way to manage the size of your /dev/shm/ or does it just expand until it fills up to existing usage or runs into the 1/2 RAM barrier?

Did you have to do anything special to get your minecraft_server.jar to read your files from your desktop? No matter where I run it from, it will only read a server.properties file and world folder from my /home/myusername/ folder. I'm unable to find any documentation about this and I don't like the clutter it causes since everytime the server is ran, it will generate any files that it uses that are missing.

TIA

---

### Post by darthrax on 2011-03-10
to wog:

scripting's easy. create a new file with gedit or nano named startserver.sh and paste the modified startup script code in it. Save the file and make it executable by right clicking on the file, going to properties then the permissions tab and selecting Allow executing file as program. Do the same process for the backup script. All the other code is to be entered in a terminal. To run your script simply double click and select run in terminal. I'll work on a script for this but i dont really have time atm so i don't know how long you'll have to wait.

To t3k:

1. /dev/shm is ALWAYS a ramdisk. its size is at most 1/2 your ram. I dont know what ubuntu uses it for but im sure theres a good reason its there. Anyways, it suits my purpose. To see how much space you have in the ramdisk open /dev/shm in the file browser and in the bottom status bar you should see the available space.

2. The server creates files in the directory that minecraft_server.jar is located in. This is the first instance i've heard of that reads files from your home folder. I have multiple versions with multiple maps in different folders all the way from alpha 1.01 to the current beta 1.3_02 and they all run fine, and read data from within their folders. I did nothing to configure this behavior. The minecraft single player client creates a .minecraft folder in your home folder which stores all data for the client including maps. You might have some path conflicts or something else on your machine. I dont know your exact setup so i cannot be more specific on this issue. Sorry.

---

### Post by t3k on 2011-03-10
After a little experimenting I discovered what was happening. It turns out that it will attempt to save all of its essential files into whichever folder I launch the server from, even though it is using the minecraft_server.jar from another directory. I do not have a minecraft_server.jar in my home directory so it's definitely using the one I'm instructing it to. 

My ventrilo server was giving me the same problem when I first made a script to launch it. I found a workaround to get it to use the files I want to use: ```
cd /usr/local/bin/minecraft/
java -Xms512M -Xmx512M -jar /usr/local/bin/minecraft/minecraft_server.jar nogui
```
Without changing directory to where the files I want to use are it defaults to /home/myuser/.

---

### Post by wog on 2011-03-11
to darthrax:
How do I change the cron line so it backs up every 2 minutes?

The current behavior I get is that the server runs okay for a while and then starts bogging down and complains of a possible time change or being unable to keep up.

Around the time the server starts bogging down, that's also when I notice lag problems like dug blocks reappearing. My current theory is that more frequent backups will help deal with that, although I admit I'm shooting in the dark.

Admittedly, I do have just 3 gigs of ram and not 8 gigs (which I think your system has, right?), and I suspect that's a part of my current problems.

If you want to help me fix these problems, tell me what you want to know and I will either provide the information or ask you how to do that.

Thanks for everything so far.

---

### Post by wog on 2011-03-12
Okay, for backups every 2 minutes the cron line should read:
```
*/2 * * * * bash /home/<your username>/Desktop/MCSERVER/save_world.sh &>/dev/null
```

Now what I want to know is what to do with the backups in order to restore the game to the latest state backed up.

I also want to know what should be in save_world.sh assuming one uses back in time as one's backup program.

---

### Post by darthrax on 2011-03-16
More frequent backups take a lot of system resources which could be the cause of your lag. The save_world.sh file is basically saving the map from ram to the hdd, so in case of a power loss the map is saved.

---

### Post by wog on 2011-03-30
The next version of the minecraft server basically fixed my lag problems. The trouble is, now cron isn't running the backup as far as I can see, so I have to do it manually. I even switched it back to 5 minutes, and cron still isn't doing anything.

How do I get cron to run the backup? I used your backup line to the letter and space.

---

