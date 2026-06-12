---
title: "does UBUNTU AUTO-compress the drive when it runs out of space?"
date: 2009-02-05
forum: The Cafe
---

### Post by macvr on 2009-02-05
hi all,
i'm using UBUNTU 8.10
 i'v been downloading a 38GB torrent file,mp4 files.
my /home drive is a 60gb partition[ext3], before downloading i had a little over 40GB of free space, so i had calculated that i would have more than 2 gb to spare...
now when i check the free space in the conky, it says i have 6.77 gb !
i'v noticed that the free space has been the same 6.77GB ever since there was still 3.5GB remaining to download, ever since 6.77GB the free space has not reduced...

 would my files have been downloaded properly? but i'm able to use the mp4 files. why is there a difference of 4 gb ??? 

even more weird is that when i check with partition editor is says i have free space of 9.2GB!!!

why is this difference? does UBUNTU compress when it reaches a certain limit? does this mean i have extra space[6.77GB/9.2GB] which i could use???

i'm hoping some of the pundits could have the ans... :D

P.S : i didnt think that this is a major help question but since i,a noob, just wanted to know more about UBUNTU's working i posted it here[if the admins feel this thread needs to be in a different section,pls move it]

---

### Post by MaxIBoy on 2009-02-05
No, there is no compression. 

My guess is that, if the torrent included a bunch of seperate files, space was "allocated" for a lot of them in advance, even if the full file wasn't fully downloaded. I'm not sure if ext3 does this, but it's possible. That's still not enough to account for all of the reduced space, so something else might be contributing to it.

The reduce in disk usage could be enhanced because you emptied your trash. You might have removed/purged/autoremoved some programs, which could have taken some assets (like icons, help files, etc.) out of your home directory; this can happen as part of an automatic update, so you might not have done it yourself.

---

### Post by macvr on 2009-02-05
> **MaxIBoy said:**
> No, there is no compression. 

My guess is that, if the torrent included a bunch of seperate files, space was "allocated" for a lot of them in advance, even if the full file wasn't fully downloaded. I'm not sure if ext3 does this, but it's possible. That's still not enough to account for all of the reduced space, so something else might be contributing to it.

but the files are totally 38GB, so even if it was allocated , shouldnt the space  have been used?

> **MaxIBoy said:**
> The reduce in disk usage could be enhanced because you emptied your trash. You might have removed/purged/autoremoved some programs, which could have taken some assets (like icons, help files, etc.) out of your home directory; this can happen as part of an automatic update, so you might not have done it yourself.

nope i dint empty trash , in fact i had tried every possible way to see if i could increase the space , but thats all i had left in that partition.
 no update was done either, i dont have automatic updates

---

### Post by MaxIBoy on 2009-02-05
Okay, I realized that it's quite possible that your Conky setup isn't reporting your disk usage accurately. In general, I'd suspect Conky more than I'd suspect the system's built-in software. 

Keep in mind that any file or directory with a dot as the first letter of its name is "hidden," so going to your home folder and hitting "ctrl-a" isn't going to be accurate unless (assuming you use the default Nautilus file manager) you hit "ctrl-h" first. I know you didn't use that method to measure the available space, but if you wanted to use that method as a source of additional information, keep that in mind.

My suggestion is to figure things out by experiment: create a file with a specific size, then copy and paste it over and over until you run out of space. See what happens.

Also, turn those updates back on-- ignoring them is bad, m'kay?;) If you're worried about running low on space, "apt-get autoremove" uninstalls anything you don't need anymore (doesn't free up space on /home so much, but it's a good idea anyway.)

---

### Post by macvr on 2009-02-05
> **MaxIBoy said:**
> Also, turn those updates back on-- ignoring them is bad, m'kay?;) If you're worried about running low on space, "apt-get autoremove" uninstalls anything you don't need anymore (doesn't free up space on /home so much, but it's a good idea anyway.)

i have the update st to reminder and for the 2 week intervals, since i was downloading this ...,  i usually check it daily

> **MaxIBoy said:**
> Okay, I realized that it's quite possible that your Conky setup isn't reporting your disk usage accurately. In general, I'd suspect Conky more than I'd suspect the system's built-in software. 

Keep in mind that any file or directory with a dot as the first letter of its name is "hidden," so going to your home folder and hitting "ctrl-a" isn't going to be accurate unless (assuming you use the default Nautilus file manager) you hit "ctrl-h" first. I know you didn't use that method to measure the available space, but if you wanted to use that method as a source of additional information, keep that in mind.

My suggestion is to figure things out by experiment: create a file with a specific size, then copy and paste it over and over until you run out of space. See what happens.

using [COLOR="RoyalBlue"]nautilus[/COLOR] it says that used is> 53.8GB
but the free space reported in the status bar in the bottom of the nautilus> is [COLOR="RoyalBlue"]6.8GB[/COLOR] [i think that it has rounded up the 6.77GB]...
[COLOR="DarkRed"]
partition editor[/COLOR] says> total size>60.80 GB ,  used 51.60 GB [COLOR="DarkRed"]FREE>9.20GB!!![/COLOR]

i dont understand why it shows different ! even if conky is wrong why is the drastic difference in nautilus and partition editor?

---

### Post by Polygon on 2009-02-05
check system monitor as well


also, by default ext3 drives have 5% of the disk space allocated for root, in case you run out of room, the root user still has space to execute commands (like rm, to delete files :D )

there is a command to change that to 1% which should gain you back some space. this can only be done on a unmounted drive (so run it from a live cd if its your root/home partition)

```

tune2fs -m 1 /dev/external

```

replace /dev/external with /dev/sda1 or whatever

also, running 

```
sudo apt-get autoremove 
sudo apt-get autoclean

```

should regain you back some space

clean your trash, and delete your .thumbnails folder as well =)

---

### Post by macvr on 2009-02-05
> **Polygon said:**
> check system monitor as well
WOW ...i had never checked this tab in the system monitor!:KS
now i understand why the difference exists between the conky and the partition editor, check attached pic...
i guess that conky displays the available space and the partition editor displays the total free space...

> **MaxIBoy said:**
> 
My suggestion is to figure things out by experiment: create a file with a specific size, then copy and paste it over and over until you run out of space. See what happens.


ok i did this and found that space was being reduced , ... , so maybe that some torrent files were pre-allocated, as u had said earlier... i dont think there could be any other explanation..

---

### Post by Polygon on 2009-02-05
to get that extra space back, run the tune2fs command i posted above.

---

### Post by macvr on 2009-02-06
> **Polygon said:**
> to get that extra space back, run the tune2fs command i posted above.

would that cause any other problems? anything i should lookout for /be careful not to do?

i need to run it as root? while the partition is online? or from livecd? [worried since i'm a noob , dont want to do it wrong] :)

---

### Post by Polygon on 2009-02-06
actually i think you can run it while the partition is mounted, but you do need to be root though. the only thing it does is reduce the amount of space on the partition reserved for root from 5 % to 1 %. Most people don't even need that reserved space, its more of a precaution. 

so just run

```
sudo tune2fs -m 1 /dev/sda7
```

---

### Post by macvr on 2009-02-06
> **Polygon said:**
> actually i think you can run it while the partition is mounted, but you do need to be root though. the only thing it does is reduce the amount of space on the partition reserved for root from 5 % to 1 %. Most people don't even need that reserved space, its more of a precaution. 

so just run

```
sudo tune2fs -m 1 /dev/sda7
```

did that and got back around 2.5 GB back... thanx :)

but i dont understand the rationale why 5% has to be reserved for a non-root partition? the reservation has it use only when the / , /home are all in the same partition, right ? if there is no use , why dont they change it to NO-reservation in a non-root partition, anyway the root is not going to be using the /home , but instead only /root? so why is this done,?

[COLOR="Blue"]is there any harm in reducing the root resvation in a non-root partition?[/COLOR] 

also, when there are separate partitions , what is the use for the reservation in / ? anyway the root user is going to have full access to the / partition , and going to be able to use the 5%

hence [COLOR="Blue"]could this reservation reduction to 1% be applied to the / partition too?[/COLOR]

---

### Post by 3rdalbum on 2009-02-06
> **macvr said:**
> 

[COLOR="Blue"]is there any harm in reducing the root resvation in a non-root partition?[/COLOR] 

Probably not - 5% of a modern hard disk is still a large amount. 1% should be fine.

[QUOTE]also, when there are separate partitions , what is the use for the reservation in / ? anyway the root user is going to have full access to the / partition , and going to be able to use the 5%

Not necessarily - many processes don't run as root but can create log files in /var/log. A runaway process can spew out massive log files.

---

### Post by Polygon on 2009-02-06
the reason 5% by default of each ext3 partition is reserved for root is if you COMPLETELY run out of space, you will still have some space left (the space reserved for root) to run some root programs like cp and rm to get your space back. but i'm glad it worked out for you =)

---

### Post by macvr on 2009-02-06
thankx guys for the help...

---

### Post by mihai.ile on 2009-02-06
well I think this thread is [SOLVED]?

---

### Post by macvr on 2009-02-06
> **mihai007 said:**
> well I think this thread is [SOLVED]?

well i didnt think it was a problem... i dont think  u can mark the cafe threads as solved!

---

### Post by FuturePilot on 2009-02-06
> **mihai007 said:**
> well I think this thread is [SOLVED]?

That feature has temporarily been disabled.

---

