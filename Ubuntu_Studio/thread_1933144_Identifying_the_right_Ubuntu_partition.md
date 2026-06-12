---
title: "Identifying the right Ubuntu partition"
date: 2012-02-28
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2012-02-28
Greetings!

I am unsure whether to install the entire Ubuntu Studios with the ISO file or go about it the hard way by terminal commands... If I do decide to go for the whole deal and use the DVD-installation approach, I wonder how I can tell what partition will be the one Ubuntu is currently occupying so I replace "vanilla" Ubuntu with Ubuntu Studios instead of my Windows partitioning, which will be disastrous should that state of affairs unfold! :-) A backup has of course been created, but a ton of work in reinstalling a dual-boot et cetera will be necessary if things go badly, so please to be certain of your suggestions should you give any!! 

Thanks a lot:)

--> Leo

---

### Post by jejeman on 2012-02-28
Give us output from
```
sudo parted -l
```

---

### Post by sirriffsalot on 2012-02-28
Model: ATA WDC WD5000AAKS-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  310GB  310GB   primary   ntfs            boot
 2      310GB   500GB  190GB   extended
 5      310GB   494GB  184GB   logical   ext4
 6      494GB   500GB  6182MB  logical   linux-swap(v1)

---

### Post by utnubuuser on 2012-02-28
the extended partition, #2, envelops #3 and $4 which are your ubuntu partitions

ntfs is windows, ext2,3,4 etc are linux


the easiest way to see it graphically is to install gparted, then open gparted from System>>Partition Editor/Gparted

PS. I've not had good luck adding environments/windows managers such as kde or lfxe etc to an existing installation of Ubuntu - I'e never tried Ubuntu Studio.
IMHO you're way better off with a fresh install, and while you're at it, give your /home folder it's own partition so that if you want to re-install or upgrade, you can keep your existing documents and settings.
If you need help on adding a separate /home partition, here is one link:[http://sazeit.com/articles/manually-select-partitions-ubuntu]("http://sazeit.com/articles/manually-select-partitions-ubuntu") - there are several how-tos floating around out there.

Essentially, if you were doing a fresh install from CD or DVD, you'd select the option to partition manually, then take the existing 184GB partition (#5), and make a / (root) partition of around 10GB, then use the remaining space for a /home partition where all your files and folder etc will reside. - the root file-system, / , doesn't take up a lot of space, so even 10GB is lots.

---

### Post by jejeman on 2012-02-28
For Ubuntu Studio it's better to go 15GiB for /. On my installation I've used 12GiB on / partition. 20GiB is realy a max.

---

### Post by sirriffsalot on 2012-02-28
Yeah, I was using GParted to check, but I wanted to ensure if my guessing was correct:) While we're at it, can you tell me why ntfs is windows and the rest (sda2 and everything in it) is Linux? Is it because sda1 is the standard original (Winblows) and ntfs is a standard label for a Windows partition or...?

I've read through how to add environments or window managers as is one of Ubuntu Studio's options, and frankly there is no reason why I should take on that dreadful task anyway... Think I am going to do a fresh install since this Ubuntu version is freshly updated to 11.10 anyway. Your time and help is eternally appreciated! Fingers crossed:)

--> Leo

---

### Post by sirriffsalot on 2012-02-28
I'll go for 10 and if more space be necessary I suppose that will be a pretty simple configuration?:) Thanks for suggestions and help!!

---

### Post by sirriffsalot on 2012-02-28
Uhm, actually, there is a minor problem I wonder if can be fixed now that we're at it... I've done something strange in the past with my partitioning, the details of which how it went about I cannot recall, but when I boot my computer I get the normal suggestion of either Ubuntu 10.11 or its safe mode etc, and of course the windows partition option. But, if I choose windows, something funny happens. I am from there directed to choose between three further options: "Ubuntu", "Vista" or "Earlier version of microsoft" lol:) Long time since I did this so how this came about, like I said, I can't say.

But, judging from the terminal output, would installing Ubuntu Studios on top of "extended" leave me with only Ubuntu and Windows at the first selection screen prompted, and by doing so also eliminate the other partitioning settings for good? Good luck solving that one, haha, sorry if it was confusing!

Edit: *cough* the windows partition is of course the one that has the three other options underlying it, so installing on top of the current ubuntu partition will do nothing, hehe... Any idea how I would fix the windows partitioning problem though?

---

### Post by sirriffsalot on 2012-02-28
Forget all that if you will, I have a new question, haha:)

I wonder if you could give me a walk-through on how to safely install Ubuntu Studio on top of Ubuntu and scorning the Windows partition of any harm or deletion, because when I tried doing the things you said there were more complications than I thought, including terminology and requirements that I would not dare take chances on, such as making the right partition the root et cetera.. The guides given by Ubuntu Studio are very simplistic, and I cannot find any that covers my particular wishes to keep Windows while overwriting "vanilla" Ubuntu. In other words, I would be most beholden to you if you could take some time out to help me through this:)

--> Leo

---

### Post by cfhowlett on 2012-02-29
> **LeoTB said:**
> Forget all that if you will, I have a new question, haha:)

I wonder if you could give me a walk-through on how to safely install Ubuntu Studio on top of Ubuntu and scorning the Windows partition of any harm or deletion, because when I tried doing the things you said there were more complications than I thought, including terminology and requirements that I would not dare take chances on, such as making the right partition the root et cetera.. The guides given by Ubuntu Studio are very simplistic, and I cannot find any that covers my particular wishes to keep Windows while overwriting "vanilla" Ubuntu. In other words, I would be most beholden to you if you could take some time out to help me through this:)

--> Leo

Leo: follow this and you'll be fine - there's NOTHING in here that partitions your drive as you'll already have done that.  [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu") 

Problems?  Come by the irc channels; #ubuntu #ubuntustudio

---

### Post by sirriffsalot on 2012-02-29
Hello cfhowlett! I am well-aware of that too, but frankly I want a fresh install anyway as previously mentioned...:-) Thanks for jumping in though! Any suggestions to what I am looking to do?

---

### Post by jejeman on 2012-02-29
I realy don't know anymore what you want?
Just format sda5 and instal Ubuntu studio there.

As for win boot, you must had at some point ubuntu wubi install. It doesn't metter know.

And for your questions about partitions

sda1,sda2,sda3,sda4,sda5... are just the names of partitions. They are not associated with any filesystems.

They are named by sdXY formula. Where X is a letter of a drive, and Y is a number of a partition. Number 1-4 are reserved for primary partitions, and 5-21 for logical partitions.

---

### Post by sirriffsalot on 2012-02-29
Hey mate!

What I am basically concerned about is how I am to format the sda5 without affecting the other partitions... In other words, how do I format sda5?:)

---

### Post by jejeman on 2012-02-29
When you start the installer, you will know.

---

### Post by sirriffsalot on 2012-02-29
A guy with Quad Shot of Ubuntu will know, but I'm fairly new at this, and what I was asked to do at the partition stage confused me. I was asked to make a certain partition root for starters, and from there start all my troubles.. Pretend I'm a baby if you please :-)

---

### Post by oldfred on 2012-02-29
Herman's site is very detailed and he offers lots of explanation. You may think it is a bit much but if you want to be sure what you are doing.

He shows creating sda5 as / and sda6 as swap. Since you already have those you can skip all those steps and should see your sda5 & sda6 just as his screen shots show after he has created them. 
You just need to choose sda5 as / (root) and reformat to ext4 or ext3. It should automatically find swap and let you install.

[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")

---

### Post by sirriffsalot on 2012-03-01
Cheers! Thanks for detailed, baby-step help:) In the meantime I've deleted the ubuntu partition and the swap partition and told the partitioning to start over, essentially. In other words making a new partitioning setup

So I'll have a look in a minute and see if I'll get anywhere. Problems started since the install DVD wouldn't complete the installation for reasons unknown, no detail is given... Failures begin immediately after the partitioning stage or one to two stages after. Is that a clue? Thanks for jumping in!:)

--> Leo

---

### Post by oldfred on 2012-03-01
I usually partition in advance, and use manual install to choose already created partitions to format to ext4 and use as / (root). I usually want /home or  data partitions and shared NTFS partitions when running Windows and that is all easier if you partition in advance. If you want just the basic install it should be able to create the / & swap partitions.

How many partitions do you have.

Post this just to see from liveCD.
```

sudo fdisk -lu
```

---

### Post by sirriffsalot on 2012-03-01
Well, I have now managed to remove all other partitions entirely and I now am left with only windows vista so I can start from scratch. So only one partition:)

For those who have complications merging all the partitions into Windows, I highly recommend Aomei Partition Assistant; completely free and coherent program for difficulties in re-partitioning with the standard Windows programs.

That being said, I am tempted to try installing now, and let the CD work things out since Winblows is occupying the whole thing. I am still worried since it seems the CD or some fetching of download packages from the internet makes the installation progress fails. This is my only current obstacle, do you have any comments on why the installation would fail as I mentioned in my previous post?:)

Sorry for being so hasty here, and not doing as you say, but it seems so far that things are going well, so:)

--> Leo

---

### Post by sirriffsalot on 2012-03-01
It seems I have managed to sort things out, I managed to install at last:)

Perhaps it helps having a one-partition-only policy if you are a half-wit or a complete wit in doing what was discussed here, so there you go. Thanks for your assistance though, I am sure someone will find it handy!

--> Leo

---

