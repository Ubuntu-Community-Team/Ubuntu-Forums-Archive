---
title: "old ubuntu server with raid died - how do I fix or restart?"
date: 2015-12-05
forum: Server Platforms
---

### Post by david472 on 2015-12-05
I have an old ubuntu server with 2 x 1TB drive and a boot drive (250gig) in a RAID.
One of the 1TB drive has died, so I replace it with another 1TB drive.  The problem now that is gives me a screen that says "Skip or Mount Manually"
I don't want to lose the info on the 1TB drive that works, but I am not sure how to approach repairing this.

---

### Post by darkod on 2015-12-05
If the OS is completely on the 250GB disk, it can boot regardless of the raid status. But if mdadm was told on installation NOT to boot degraded, it will not boot right now because the array is degraded.

What is the actual question about skip or mount manually? For which device? It must say something more...

---

### Post by david472 on 2015-12-05
It does boot still, I shouldn't have mentioned that.  If I pick _**Skip**_, it goes to the desktop no problem.
When I boot, the BIOS says there are three drives (which is correct) and the RAID is degraded.

When the screen comes up to SKIP or MOUNT, I have tried to leave it all night, hoping it would copy the information to the new 1TB drive, but after 24 hours, nothing had changed.

---

### Post by darkod on 2015-12-05
The new disk will never be included in the array automatically. The OS can not "guess" what do you want to do with it. What if it does something you don't want to...

If the OS boots, you will need to partition the new disk accordingly so that the partitions match with the other array members. After that you will need to add each partition to each corresponding array (if there are more than one) with the command:
```
sudo mdadm /dev/md? --add /dev/sd??
```

You will need to use the correct /dev/md? and /dev/sd?? devices in that command, of course. That will add the partition(s) to the array(s).

---

### Post by david472 on 2015-12-05
Ok
Step 1 )  "[COLOR=#000000]you will need to partition the new disk accordingly"[/COLOR] - can this be done from ubuntu or the command line?  Is this the command you gave? [COLOR=#000000][FONT=Ubuntu Mono]sudo mdadm /dev/md? --add /dev/sd??  Are the question marks purposeful?[/FONT][/COLOR]
Step 2 )  "[COLOR=#000000]After that you will need to add each partition to each corresponding array"[/COLOR] I am guessing one thing at a time - how will I know when i can do this?

Will this keep in info on the OLD array drive?

---

### Post by darkod on 2015-12-05
Yes, of course you can do partitioning on the command line. All linux servers have only the command line. There are few programs you can use, personally I prefer parted. See below... The question marks you need to replace with correct letters and numbers. That's why I said to corresponding arrays... You can add one partition after the previous finishes the sync with the array, or you can add all at once, doesn't matter. Better to do it one by one to lower disk load...

If by the old array drive you mean the existing member that is still in the array, then yes. Of course the data stays there and will be synced to the new array member you are adding. That's the purpose of raid.

If you need more detailed help with the partitioning and adding partition to mdadm, post the output of this first:
```
sudo parted -l (that's small L)
cat /proc/mdstat
```

When posting the output use CODE tags so that it keeps the formatting.

---

### Post by david472 on 2015-12-07
Ok, two steps back.
1) The server has a few log ins.  The only one I can use is the GUEST log in, but that won't give me permission to get to the command line and use the code you gave me
2) The server has a log in for admin, and the password works BUT it flashes the screen and then brings up the login screen again.  I am guessing the password works because any other password brings up the "This password is incorrect".  The correct password does not.
3) Is there a safe mode or a way to boot to the command prompt so I can try to run those lines of code?

Lastly, the RAID no longer says DEGRADED, but instead it now says "REBUILD".  I did not do anything except create a USB boot disk.

---

### Post by darkod on 2015-12-07
You have few options...

1. Reset the password for an account that has sudo (admin) rights. You can do that following this procedure for example: [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password). Regardless of the raid issue, you need to get an admin user working.

2. Boot the machine with the desktop live CD/usb in live mode, and work with the raid from there. mdadm software raid offers you this flexibility, you can even use live mode to work on the arrays or get data out.

I don't know what's happening with the raid status, it would be very weird if the new disk "automatically" got included in the array. That's not how it works. Reset the password for the admin user, log in with it, and you can see and check more details. Then you will see the status of the raid arrays and what actions you need to take, if any.

---

### Post by david472 on 2015-12-07
Ok, thank you for the passcode help.  BUT I am still not able to log in for some reason.  Here it is :
1) I changed the passcodes
2) When I boot and try the passcode, the screen flashes BLACK and then returns to the log in prompt.
3) I am back where I started!
4)  There is a GUEST log in that works great, but the other logins do not take me to the desktop
Any ideas?

---

### Post by darkod on 2015-12-07
Desktop? Is this the server or desktop version of ubuntu? Not that it matters, most of the things we discuss here apply to both.

It is not normal that it doesn't let you log in. You could try creating new user from the root shell that you used to reset the password. It should work. Give it a go and see if that new user can log in normally. To create new user start with:
```
adduser <newusername>
```

To give sudo right to this user:
```
usermod -aG sudo <newusername>
```

Don't forget to remount the root partition as RW after entring the root shell. Just like that article explains.

You can also use that shell to check the status of the mdadm raid, if all else fails...

---

### Post by david472 on 2015-12-08
It returned Error code 10 and said it could not add user.

```
Groupadd : cannot lock / etc/ group : try again later
adduser: /user/sbin/groupadd -g 1002 david returned error code 10. Exiting
```

---

### Post by darkod on 2015-12-08
1. Does the group with gid 1002 exist? The adduser command can't create new groups if you are using the -g option. The group needs to exist already.

2. If the group exists but you still get this error, try removing two files that might remain from crashed sessions and lock the /etc/group file. Those are:
```
rm /etc/group.lock
rm /etc/gshadow.lock
```

After that try the adduser again.

And don't forget that unless this gid 1002 has sudo rights, you will need to add the user to the sudo group after you create it so that it can have admin rights.

PS. It just occured to me that the -g 1002 error might be message from the system, not that you are using -g 1002 in your adduser command. In that case ignore number 1 above and try number 2 directly. It seems the /etc/group has remained locked and it can't create new group when you are trying to create the user.

---

### Post by david472 on 2015-12-08
I don't know if the [COLOR=#000000]gid 1002 exist - I am taking over a server from another person and have no idea.  I am just following your directions now and don't know much else about it - although I wish I did!!

How do I find out if it exists?  If it does not - where do I go from here?[/COLOR]

---

### Post by darkod on 2015-12-08
If what you tried was adduser david, ignore number 1 in my previous post and try number 2.

If you want to look into which groups exists first, you can do that with cat /etc/group. You will be able to see if group with id 1002 exists or not. But I think you don't need to worry about that. I thought first that you ran a different command, to put the new user directly in group david.

---

### Post by david472 on 2015-12-08
But should I check to see if gid 1002 exists at all or it isn't important?

---

### Post by darkod on 2015-12-08
Not important.

---

### Post by david472 on 2015-12-08
When I try both 
```
[COLOR=#000000][FONT=Ubuntu Mono]rm /etc/group.lock &
[/FONT][/COLOR]rm /etc/gshadow.lock
```
[COLOR=#222222][FONT=Verdana] - it says "file does not exist"

I did a [/FONT][/COLOR][COLOR=#000000]cat /etc/group - and did not see any of those groups you listed.[/COLOR]

---

### Post by darkod on 2015-12-08
And if you try the adduser you still get the same error that you posted?

Also, did you do the RW remount step in the root shell? That's very important, otherwise the system is loaded read only...

---

### Post by david472 on 2015-12-08
I have added another user and got the same error.
I am unsure of the RW remount step in the root shell.  When and where do I do that?  Right now, I was just trying to "add" a new login as per your instructions.  Where do I use the RW remount?  What is the code please?

---

### Post by darkod on 2015-12-08
But I also said to make sure you do the remount step from that procedure I linked how to reset a password from the root shell. You have the link in post #8. That is very important because the shell by default is read only.

So, you need to:
1. In the grub menu boot the recovery mode entry.
2. In the menu that appears select "root - drop to root shell prompt".
3. Once in the prompt, execute:
```
mount -rw -o remount /
```

Only then you have a read-write system and you can try the adduser, or resetting a password with passwd <username>, etc.

---

### Post by david472 on 2015-12-08
ok, trying...success with the newuser and [COLOR=#000000][FONT=Ubuntu Mono]usermod -aG sudo <newusername>

[/FONT][/COLOR]Now what are the next steps for me - and thank you for your patience!

---

### Post by darkod on 2015-12-08
Now do reboot and log in with that new user and password. The user should have admin rights now...

After you log in, the first step would be to check current mdadm status with:
```
cat /proc/mdstat
```

Post the output here.

---

### Post by david472 on 2015-12-09
I searched for TERMINAL and got the command box.  In it I typed [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/mdstat[/FONT][/COLOR]


This is the response : 
```
[I]Personalities
Unused devices : none [/I]
```

Then it returns to the command prompt.

---

### Post by darkod on 2015-12-09
It seems there is no software raid. It might be hardware raid. I sort of failed to realize that so far. Some of the initial comments led me believe we are talking about SW raid.

If it is HW raid then it's controlled outside of ubuntu (outside the OS). In such case, yes, the array would have begin rebuilding as soon as you replaced a failed disk.

---

### Post by david472 on 2015-12-09
its weird because it didnt begin building - as I said, when I boot to the BIOS, it used to SAY DEGRADED and now it says REBUILD, but I am getting the same issues of not being able to access it or the files on the drives.
The previous owner (but he cant remember or is too busy) says it is software.

---

### Post by darkod on 2015-12-09
First it will say degraded until the rebuild process finishes. In fact the rebuild might mean it is still rebuilding the array. Depending on size it can take a while.
But we need to know if you are talking about hw raid or sw raid. You need to figure that out first. If during boot it gives a message you can enter raid bios with some key combination then usually it's hw raid. You can use that key combination and enter the raid bios. There you will be able to see status of all arrays. And that raid bios should be used for all raid manipulation. The OS sees the arrays as simple disks, nothing more.
SW raid works in completely different way. The OS configures and assembles the arrays.

---

### Post by darkod on 2015-12-09
If /proc/mdstat says there are no running arrays I find it highly improbable this is sw raid.
Should be easy to get more details. Post the output of the following terminal commands:
```
dpkg --list | grep mdadm
sudo blkid
```

---

### Post by david472 on 2015-12-09
too much to write, I have to take a picture.
[http://postimg.org/image/6kpyvcspf/](http://postimg.org/image/6kpyvcspf/)

---

### Post by darkod on 2015-12-09
HW raid

PS. To be more exact, I believe isw is onboard intel fakeraid. The term fakeraid is used for onboard controllers built into motherboards which are not dedicated HW raid card with its own CPU and memory, instead they use the system cpu and memory. So in a way it's SW raid but of a different kind.

What you have is definitely not mdadm linux SW raid and should be controlled from the raid bios menu. Most people avoid using this for servers because it offers no benefit over linux mdadm raid, only downsides. If there is no dedicated HW raid card, better to use mdadm raid.

But anyway, you've got what you've got...

You also managed to create a new user which has sudo rights... You can use this user for system administration, including resetting the passwords of all other users if needed. Or deleting those users if you wish...

Is there anything more to do? The machine is booting and working now, right?

---

### Post by david472 on 2015-12-09
Thank you for the concise and thorough answers!
I need to rebuild the raid, so I can get the data from the second drive and write it to the new one - and have the RAID working like it did before the drive died.

250 gig - boot disk
1 TB - RAID - old drive
1 TB - RAID  - new drive

Also, how can I see what is on the old and the new drive in ubuntu.  In Windows, I could just use explorer to look ...

---

### Post by darkod on 2015-12-09
What do you mean by "see what is on the old and the new drive"? The new disk I suppose is brand new, which means blank. The old disk is one half of a raid1 mirror and you should be able to check the data on it by opening it.

I would recommend few things.

1. It seems you are running Ubuntu Desktop as a server. Desktop version comes without openssh server by default. Instead of standing next to the server, install openssh and use ssh session from your desktop machine. That way you can also easily copy-paste output instead of taking pictures. :) To do this run:
```
sudo apt-get install openssh-server
```

After that you should be able to connect to the server IP from your local network using ssh from linux or putty from windows.

2. Go into the raid bios and check the array/disks status there. As we discussed, that's the only place to look for raid status. If it was mdadm raid, you had other options, but because it is not, you should manage it from the raid bios. In theory, the raid1 array should still be good even if one disk failed...

3. If you decide to install openssh server, connect to it and show us the output of:
```
df -h
sudo parted -l (that's small L)
```

The first command will show mounted partitions, and the second all disks and their partitions. Lets see if it shows the raid device from ubuntu.

---

### Post by david472 on 2015-12-09
I am doing this from another computer anyway. 
1)  The Ubuntu server is next to me, that is why I was taking pics. : [http://postimg.org/image/b3iycn46f/](http://postimg.org/image/b3iycn46f/)
2) Here is the pic from the first line you told me   ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install openssh-server[/FONT][/COLOR]
```
Not sure if I should proceed or not.  It is a ubuntu server.  If I hit YES will it erase anything

PS - how do I get to the RAID Bios - is that on startup with the regular raid.

---

### Post by darkod on 2015-12-09
Yes, continue with the apt-get and it will install all needed packages for openssh server.

And yes, the raid bios should be available with a key combination at the start of boot (after the main BIOS POST but before the OS starts loading). Depending on the motherboard I don't know what's the key combination, it will say it on screen. Something like Ctrl+A, Ctrl+R, etc...

PS. If the OS really is ubuntu server version someone installed the GUI interface. The server does not come with this graphical interface by default. Only with a command line...

---

### Post by david472 on 2015-12-09
It is warning me that the server packages cannot be authenticated - do I want to continue Y or N

```
openssh-server ssh-import-id
```

Should I install these packages without verification.
(if you can`t tell my question mark is not working)

---

### Post by darkod on 2015-12-09
I don't recall seeing such message about not being able to authenticate but usually everything installed with apt-get is safe. I see you also have a bunch of packages to upgrade... You can do that by updating apt-get first and then upgrading all packages that have a more recent version:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Note: the second command does NOT upgrade your ubuntu version, it only upgrades all installed packages that have a more recent version released.

---

### Post by david472 on 2015-12-09
Forgive me for being dense, but should I STOP what I am doing - hitting NO ([COLOR=#000000]server packages cannot be authenticated - do I want to continue Y or N) [/COLOR]and get the update from sudo aot-get update first?

---

### Post by darkod on 2015-12-09
It doesn't matter either way, but in fact do the apt-get update first because it might pull new package versions from the repositories. You can do only the apt-get update and then try installing openssh-server again. Don't forget that if you execute the dist-upgrade too, you might need to wait quite long, it will have many packages to download, depending on your internet speed that will take some time, and after that it will take quite long to actually install those upgraded packages. So, running the dist-upgrade right now might take long time... Doing the apt-get update is fast and probably better to do, so that apt-get chache gets up to date.

Don't forget that all of this is basically just to allow remote administration over ssh, and is not really crucial to do right now. If you want to focus on the raid right now, you can also do the openssh server installation later. But for the raid you need to reboot and open the raid bios menu. I can't help you much about that menu and its options because I have no idea how it will look.

---

### Post by david472 on 2015-12-10
Ok I did the:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[/FONT][/COLOR]sudo apt-get dist-upgrade
```

This is what I got for each line of code

```
sudo apt-get update
``` -- some index files failed to download.  They have been ignored or old ones used instead.

```
sudo-apt get-upgrade
``` -- it failed to fetch a almost all of upgrades. and some 404 file not found etc. (plus it needed 246mb of extra space)


Ok I ran the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install openssh-server[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]and it says "unable to fetch some archives, try running apt-get update or apt-get --fix missing 

I tried ```
 apt-get update
```
but it failed to fetch some files again - files have been ignored or old ones used.


And interestingly enough, the server does seem to work with the Tricaster broadcasting equipment and I think it is saving files on it, but I am still stuck with the drive isn't part of the raid yet.

---

### Post by darkod on 2015-12-10
If the ubuntu version is too old, and depending which version exactly it is, the repositories might have been moved when it reached end-of-life. So apt-get will not be able to find them at the expected location. You can get more data about the ubuntu version and the kernel with:
```
uname -a
lsb_release -a
```

As for the raid part, we discussed it already, you have to work in the raid bios menu. You should be able to check current status there and add the new disk to the existing array (if needed).

---

### Post by david472 on 2015-12-10
After the first reboot, here is the screen shot
[IMG]http://s21.postimg.org/a5a9mobiv/after_reboot.jpg[/IMG]


It was Cntr-I and I am in the RAID menu system.  Here is the screen:

[IMG]http://s9.postimg.org/3oep8m6wv/after_raid_image.jpg[/IMG]

---

### Post by darkod on 2015-12-10
As far as I can see both 1TB disks are members of the raid. Why do you think you still have to add the new disk to it?

---

### Post by david472 on 2015-12-10
I am glad this seems to be working, but it has brought up a few more questions:

0) It still asks whether I want to skip or manual mount the drive on boot up - why is that?

1) This is a ubuntu server - but why, when I boot and go to the log in, cannot see what is on each of the two x 1TB drives?  I thought it would be like ***windows file explorer*** and I could look at the files on them.  Maybe it is my unfamiliarity with ubuntu that is causing me to miss it?

2) This is a video server - before the RAID died and I took over, there was a batch file that was used to connect the other computers to the server :
```
 net use z: \\commtechserver\video /user:vidshare vidshare
```

3) The **vidshare** login and password does not work (meaning it does not log in).  Even with the right password, it flashes a black screen and then returns to the Videshare login.  I know the password is correct because if it is wrong, it tells you.  

The problem is now that although it used to work, it no longer does.  When you click the batch file, it runs but nothing happens.  There is no "Z" drive that appears in the directory.  Maybe I am wrong here, but I think that is how it is supposed to work.  
IF this is beyond ubunto, I'm sorry - it is all new to me.

4) Also just received this error message : unable to mount location 

And thanks for all your help so far!

---

### Post by darkod on 2015-12-10
0) That is not a good sign. It usually means the system can't find a partition it was mounting automatically so it is asking you if you want to skip it or mount it manually. It probably concerns the raid array/partition.

1) Are you familiar how raid1 works? Both disks make identical mirror, and a result is a single device. So you can't see what's on "each" disk, they don't exist as two disks any more. Not for the OS. Otherwise, yes, you can open the file explorer in ubuntu (if there is a GUI interface which it seems there is), called Nautilus, and browse any disks that are present. However, if there is something wrong with the raid and it's not mounted, of course you can't browse it.

2) If the raid is really not detected as mentioned above, this command is useless. It doesn't create the Z share if it can't find the share on the ubuntu server.

What you need to do now is check if the raid partition exists and if it's good, or not... But first, I am confused about something...

Was this server working all the time, and then a disk died and you simply bought a new one, shut down the server and replaced it?

Or the server was shut off long time, regardless of the disks (working or not)?

If the server was working, and you replaced a disk, did the share stopped working at that point of time? What did you do exactly?

What I am worried is that the old array was somehow overwritten with this new array. That's why ubuntu can't find the partition to mount, and it would mean the data is probably gone...

While answering these questions, pls also post the output of:
```
cat /proc/partitions
sudo parted -l (that's small L)
```

---

### Post by david472 on 2015-12-10
Ok, thanks for the quick reply.

Here is the situation. 
1) The server was running all summer (to the best of my knowledge)
2) I got here and found the server screen was on the login, but I couldn't log in - it gave me the same error it is giving now BLACK SCREEN, back to login screen.
3) I rebooted, thinking it might be a problem that would go away with a fresh book.
4) During the reboot, I found the SKIP and MANUAL mount occurred it also told me the RAID was degraded.
5) Also, a large clattering noise occurred indicative of a hard-drive failure. 
6) I was always able to boot, and hit SKIP thus getting to the Ubuntu login
7) The GUEST login always worked.  The other two logins, vidshare and otherwise, did not
8) I found the dead hd, replaced it and rebooted.
9) my OP began there

See thread above for details. 
Here are the pics for both lines of code :[IMG]http://s14.postimg.org/cd9lxzs3l/20151210_164052.jpg[/IMG]

[IMG]http://s1.postimg.org/qv9ymfcy7/20151210_164133.jpg[/IMG]

---

### Post by darkod on 2015-12-10
This is a very strange situation... It seems both 1TB disks are seen by the OS as separate (sda and sdc). Which shouldn't be the case if the raid is handled by the onboard raid. There is also that dm-0 device which might be how the resulting raid device should be called...

I have worked with either mdadm SW raid, or HW raid, but this seems to be some kind of hybrid situation... And the array looks definitely "broken" up otherwise with one disk failed the raid1 mirror should have kept working and mounting... That's the point of using mirror raid. The remaining good device still keeps working until you replace the broken disk...

I will try to investigate on google but I haven't seen a situation like this so far.

---

### Post by david472 on 2015-12-10
thank you, please let me know!

---

### Post by darkod on 2015-12-10
Some interesting info here: [http://askubuntu.com/questions/113561/how-to-modify-fix-incorrectly-detected-dmraid-fakeraid-raid-10-array](http://askubuntu.com/questions/113561/how-to-modify-fix-incorrectly-detected-dmraid-fakeraid-raid-10-array)

But nothing exactly the same like your case. It does show some dm commands though... Lets try listing info first, try something like:
```
sudo dmsetup info /dev/dm-0
```

Then try to get some more output with:
```
sudo dmraid -r
sudo dmraid -s
```

That should show if we are dealing with dmraid array and some basic info.

---

### Post by darkod on 2015-12-10
Just to add that this dmraid "fakeraid" is the worst option of all. Even if you make it work, it's not really recommendable... I would get the data out and remake the array with plain mdadm SW raid. But it's still too early to discuss something like that.

---

### Post by david472 on 2015-12-11
Thanks for your patience, I wasn't able to look at the computer until just now and was busy all day.  Now I am here!

Ok, here is the output for the 3 lines of code you gave me :

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dmsetup info /dev/dm-0[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR][IMG]http://s15.postimg.org/n4uv4sca3/20151211_152119.jpg[/IMG][COLOR=#000000][FONT=Ubuntu Mono]


and for 

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dmraid -r
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dmraid -s[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR][IMG]http://s15.postimg.org/nf6z1vga3/20151211_152222.jpg[/IMG]

Yes I am finding out this is not the option I would choose, but I am stuck with what I got for now.  I really need to get it working!

---

### Post by darkod on 2015-12-11
One thing... If you are running commands as root (as I can see on the screen), drop the sudo in front. Don't type it. For many commands we are used typing sudo in front if they are system commands and we assume you are running them with your own user, not with root. No need for sudo with root.

Unfortunately I don't know much about dmraid. I think the -r and -s commands should have given different output, but I can't be sure...

One thing I know is that -ay activates all found dmraid arrays. It should be safe for the data on the disks, it should only activate all arrays it can find and are good. In your case you have one array.

If you are running it as root, try only:
```
dmraid -ay
```

If you are not running it as root, put sudo in front.

That's the only way I know how to try and activate dmraid array, assuming it's not active and assuming it's a good array that can still run.

---

### Post by darkod on 2015-12-12
Meanwhile, I found some info on the internet that gives some hope. When you have access to the machine again, run the previously mentioned command as root:
```
dmraid -ay
```

Report the output so we can see the messages it gives.

One question: Even thought you din't manage to install openssh-server, did you try if maybe ssh is enabled on the server? Maybe you can access it remotely from another machine which will make the command issuing and copy-pasting the output much easier. Instead of posting pictures...

---

### Post by david472 on 2015-12-15
Ok I haven't been able to work on the server for a few days.  
I used the SHIFT key to get to the Root screen and tried 
```
dm raid -ay
```

It tells me : ERROR mkdir /var/lock/dmraid

---

### Post by darkod on 2015-12-15
Hold on, why are you using the recovery root shell? You did manage to set up a new admin user, why aren't you logging in with it?

It's not working?

If using the root shell, you didn't forget it loads as read-only right? That could explain the errors. You need to remount the root partition as read-write if using the root shell. Before running any other command.

Just use the user you created, if possible. That will also show you if login is working normally.

---

### Post by david472 on 2015-12-15
Ok, I tried to run it from the new user I created.  Went to TERMINAL and typed
 
```
[COLOR=#000000][FONT=Ubuntu Mono]dm raid -ay
```

It tells me YOU MUST BE ROOT.

Sorry about this, I am sure I am missing a step.

[/FONT][/COLOR]

---

### Post by darkod on 2015-12-15
I explained that 2-3 posts ago. If running as that user you need to use sudo in front of the command. And type again the user pass when it asks you.
Only root user doesn't need sudo.

---

### Post by david472 on 2015-12-15
Ok thank you

Here is the output 
```
RAID SET "isw_daaifhhhe_RAIDVOL" already active.
ERROR : DOS : partition address past end of raid device
```

---

### Post by darkod on 2015-12-15
Somehow it's complaining that the partition end is past the array size. I have to search what is the best way to try and sort that out...

---

### Post by david472 on 2015-12-15
thank you again.  I know this isn't a project of yours, so I really appreciate it!

---

### Post by darkod on 2015-12-15
Lets try to see which version are you running. Post the output of these:
```
uname -r
uname -a
lsb_release -a
dmraid -V
```

It seems there is bug in old versions of dmraid which might be affecting you.

---

### Post by david472 on 2015-12-15
1) 3.0.0-12-generic

2) Linux commtechsersver 3.0.0-12-generic #20 ubunto SMP Fri oct 7 14:50:42 UTC
i686 i686 i386 GNU/Linux

3) No LSB modules are available
Dist I : Ubuntu
Description : Ubuntu 11.10
Release : 11.10
Codename : oneiric

4) dmraid version: 1.0.0.rc16(2009.09.16) shared
dmraid library version : 1.0.0.rc16 (2009.09.16)
device-map[per version : unknown

---

### Post by darkod on 2015-12-15
1. In theory that dmraid bug was fixed in version 1.0.0.rc15 and you have rc16 which means it shouldn't affect you. Lets see...

2. You are running Ubuntu 11.10 32bit which is a very bad choice for any server, including basic home servers. Always, always use LTS versions for servers (I know, you didn't install this). The LTS versions come out every 2 years and have 5 years of support. The other releases come out every 6 months but have only 9 months of support (earlier it was 18 months). That's why apt-get can't find any repositories and doesn't let you install or update anything. You should upgrade your 11.10 to 12.04 LTS but we will talk about that later.

The raid is the primary goal now... Let me dig some more about that error message later on.

---

### Post by david472 on 2015-12-15
Also, if I reboot and go to the RAID bios, when of the options is to RESET DISK TO NON-RAID.  Do you know if they will delete everything on the drive that is there already?  Would this be something worth considering?
Just to recap -
There is : 
-Original 1TB drive (with video files - still working)
-New 1 TB drive (replacement of old one that doesn't work- brand new)

Ok, I am thinking if all else fails, I might have to buy another NEW 1TB hard drive - take out the original one with the video files and put it aside and start over - hoping that I can still retrieve info off the original drive that will not longer be in the RAID.

---

### Post by darkod on 2015-12-15
I can't find anything relevant to your error. Lets see if we can display the partition start/end... Try the output of these:
```
sudo fdisk -l isw_daaifhhhe_RAIDVOL
sudo parted isw_daaifhhhe_RAIDVOL unit s print
```

---

### Post by darkod on 2015-12-15
About the reset to non-raid question. I actually saw an advice in one blog that if such fakeraid fails, to reset the disks as non-raid and that will keep the data and make the disk like ordinary none raid disk. But I have never tried such a thing myself, and I don't use fakeraid at all, so I didn't want to risk giving you an advice that might possibly destroy the data on the only good disk...

You can try it on your own responsability. :) Try googling about that option some more, and see whether you like what you read...

---

### Post by david472 on 2015-12-15
From the TERMINAL: 

I tried this ```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l isw_daaifhhhe_RAIDVOL[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
(and I actually copy and paste the exact output) and it asked for my password and then brought me back to the command prompt and did nothing else


[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo parted isw_daaifhhhe_RAIDVOL unit s print[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] 
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Again, I copied and pasted the exact wording from the 
[/FONT][/COLOR]```
[FONT=Ubuntu Mono][COLOR=#000000]sudo dmraid -ay[/COLOR][/FONT]
```
[COLOR=#000000][FONT=Ubuntu Mono]to get the exact 
"[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]fdisk -l isw_daaifhhhe_RAIDVOL"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] and the second code said "Could not stat device - no such file or directory. REtry or Cancel[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]

-______________________________________________________

[/FONT][/COLOR]What about the manual mounting? What does that do? 
When I boot it says "Skip or mount Manually"

---

### Post by darkod on 2015-12-15
It doesn't recognize it to mount it automatically so I don't think you will be able to mount it manually anyway. Right now skip seems to be your only option. I might have selected the wrong parameter for the fdisk and parted commands. Try them again but replace the isw_*** device with /dev/dm-0. Everything else stays the same in the commands, just replace the disk device with /dev/dm-0.

---

### Post by darkod on 2015-12-16
I think there it's time to consider other options too, seeing how time consuming this troubleshooting is and without any guarantees of success.

In your place, I would investigate more the option to reset the disk as non-raid. I believe that keeps the data. If that is really the case, you have better ways to continue...

1. Forget about this installation completely, and on the OS disk install a brand new Server 14.04 LTS. That will depend on how the server is used. Is this used only for that share for windows workstations? If that is so, new OS install is fairly simple and fast. The ubuntu server will install in approx 30mins (depending on server specs) and setting up a simple samba share open to all takes only 2mins. The data disk is separate so it will not be affected at all.

2. If you would rather work on the current OS instead of reinstalling, I would do the following. Modify the apt-get sources because 11.10 is end of life. Ubuntu keeps archive of old versions for these cases. You just have to point the sources to the archive. Do an update/upgrade of all packages, then an upgrade to 12.04 LTS.

The above assumes that the only important thing on this server is the share. Is that so? What role does it have in your setup? Are there any restrictions on using the share by clients?

Because if it's only a simple open-to-all share, that is easily done and I would go for option 1.

Of course, all of this assumes that resetting the disk keeps the data on it intact. So that would be the first step of investigation. If the result is positive, we can discuss what to do and the best way to do it. The steps will involve setting up proper SW mdadm raid, so you will have raid1 again, only this time better than the dmraid.

Let me know what you think...

---

### Post by darkod on 2015-12-16
According to this: [http://forums.whirlpool.net.au/archive/1986490](http://forums.whirlpool.net.au/archive/1986490)

> You can convert onboard Intel Raid 1 back to single drives.I just upgraded my Raid 1 from 320Gb drives to 1Tb drives, and one of the one of the steps involved resetting the disks to non-raid without loosing any data.
[http://www.intel.com/support/chipsets/imsm/sb/CS-030751.htm](http://www.intel.com/support/chipsets/imsm/sb/CS-030751.htm)
If you're not upgrading/migrating your disks, then you should just be able to power down, remove one drive, then reset the remaining drive in the Raid BIOS to non-raid.
Bonus, if it doesn't work you still have all your data backed up on the drive you removed!

Also a similar discussion about resetting the disks and keeping the data here: [http://en.community.dell.com/support-forums/disk-drives/f/3534/t/18667121](http://en.community.dell.com/support-forums/disk-drives/f/3534/t/18667121)

Those are just few example I could find with a quick search...

---

### Post by darkod on 2015-12-16
Just to complete the list of your options, of course you also have the option to try and rebuild the current dmraid array and hopefully that can put the server back into production. After that you can adjust the sources list (from archive) and upgrade to 12.04 LTS.

Reading about the topic it seems the raid bios where you added the second disk is only labeling it for rebuild (if you double check the status and explanation in the raid bios it does say the array will rebuild in the OS). And it seems in these setups it is waiting for your order now to actually start the rebuild (it's not automatic). According to dmraid documentation the rebuild is done with -R and the array name. In your case that would be:
```
sudo dmraid -R isw_daaifhhhe_RAIDVOL
```

That should kick off the rebuild process. You can follow it with:
```
sudo dmsetup status
```

That is one way to go to try and finish the rebuild and get the server going fully.

One thing I remembered now is about those few dmraid commands we wanted to use and get more info. They failed with errors but that was probably because you were running them in root shell and read-only root partition. After you created new user I thought it was implied to use that user, and not the root shell any more.

So, if you want to try running those commands again and see what output they give, you can try:
```
sudo dmraid -r
sudo dmraid -s
```

That's it for now... Post back your comments/output/etc.

---

### Post by david472 on 2015-12-16
I tried the
```
sudo dmraid -R isw...
```

and it says :
```
Raid Set is already active
```

followed by
```

sgpio app not found
sgpio app not found

```

---

### Post by darkod on 2015-12-16
Strange. It doesn't look rebuilt but it doesn't want to start rebuilding either.
Did you try the fdisk and parted commands to try and list the partitions on /dev/dm-0?

---

### Post by david472 on 2015-12-16
Just tried ```
sudo dmsetup status
``` and got :

```
isw_daaifhhhhe_RAIDVOL : 0 1953519880 mirror 2 8:0 8:32 2488/14905 1 AA 1 core
```

I have tried the Fdisk and Parted commands in post #66 - see below. 

[COLOR=#000000]From the TERMINAL: [/COLOR]

[COLOR=#000000]I tried this[/COLOR][COLOR=#000000]Code:
 [COLOR=#000000][FONT=Ubuntu Mono][code]sudo fdisk -l isw_daaifhhhhe_RAIDVOL[\code][/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]
(and I actually copy and paste the exact output) and it asked for my password and then brought me back to the command prompt and did nothing else


[/FONT][/COLOR][/COLOR][COLOR=#000000]Code:
[COLOR=#000000][FONT=Ubuntu Mono][code]sudo parted isw_daaifhhhhe_RAIDVOL unit s print[\code]


Is that what you mean?  Also, why does it ask for my password and then do nothing but return the command line?
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
[/COLOR]

---

### Post by darkod on 2015-12-16
You are not reading my posts carefully, again... :(

The isw* parameter in fdisk and parted was my mistake, that's why I said "run it on /dev/dm-0" in the last post. And I also mentioned that few posts ago (in post #67 to be exact)... Anyway, since few commands gave you errors when running them in the read-only shell, lets get more output again. Post the result of:
```
sudo dmsetup status
sudo dmraid -r
sudo dmraid -s
sudo fdisk -l /dev/dm-0
sudo parted /dev/dm-0 unit s print
```

If I'm not mistaken that status output you posted might mean the rebuilding is in progress. The 2488/14905 means how far it got. That's why I am asking you for the same status command again to see if the 2488 changes. Maybe the dmraid -R you ran did help...

Lets see what the above commands give you...

---

### Post by david472 on 2015-12-17
Ok, I am sorry for not following instructions carefully.  I will endeavor to get it right in the future.
Here is a pic of the results from the code you gave me.  This was done in the TERMINAL.
[IMG]http://s11.postimg.org/7abgsiac3/20151217_122108.jpg[/IMG]

---

### Post by darkod on 2015-12-17
As you can see in the status output, it finished rebuilding 14905/14905.
And dmraid -r shows both disks sda and sdc as members if the array.
And dmraid -s gives type mirror, status ok.

Congrats, looks like you have your array rebuilt now.

The fdisk gave errors but don't worry about that right now. Probably we are using wrong device name.

Try rebooting now and see if it stops asking you to skip or hopelly it might boot normally without the skip question...

---

### Post by david472 on 2015-12-17
It still says "The drive for /home is not ready yet or not present

continue to wait SKip or MOUNT

---

### Post by darkod on 2015-12-17
Ok. Try this to check the disk devices:
```
sudo parted -l
sudo fdisk -l
```

PS. Also:
```
cat /etc/fstab
```

---

### Post by david472 on 2015-12-17
[IMG]http://i68.tinypic.com/rgyng3.jpg[/IMG]

[IMG]http://i67.tinypic.com/34qldnk.jpg[/IMG]

[IMG]http://s9.postimg.org/czsmf61e7/fdisk.jpg[/IMG]

---

### Post by darkod on 2015-12-17
Hmmm, strange... The entry in /etc/fstab searching for the /home to mount, is looking for the array with a different name. Compare the /dev/mapper/isw_cihgfecac_RAIDVOL1 entry in /etc/fstab, and the /dev/mapper/isw_daaifhhhhe_RAIDVOL1 that is the current name reported by fdisk/parted.

Lets try a quick fix, if it works. Open /etc/fstab for editing and modify the /dev/mapper/isw_*** entry as I have explained above. You can open it for editing with:
```
gksu gedit /etc/fstab
```

Make the change only in the isw_*** part of the /dev/mapper line. Nothing else!!! Save and close the file. Reboot and let us know if the skip message is still there...

PS. You don't even have to reboot to test it. It completely slipped my mind. After you modify the /etc/fstab file and save and close it, open terminal and try:
```
sudo mount /home
```

That will either mount it, or give you an error message. If it mounts it, it will probably keep mounting it on each reboot.

PPS. Another thing I noticed and that I don't like at all, is that in /etc/fstab the /dev/mapper/... device is mounted as ext4 filesystem. Which would be the correct way on linux. But the latest fdisk results show the _RAIDVOL1 partition as NTFS. It also shows sdc1 as NTFS too, the underlaying partition forming the raid array. If the array is really NTFS now, that would present big problem because it would mean the data is probably gone and it was formatted on top of it. But the steps you explained earlier that you took to revive the server looked correct, so I have no idea why the array would "recreate" as completely new one. If it was recreated it would explain the different name that it now has compared to before. But still, even a recreated array would not be NTFS right away, not until you format it. A new array would be unformatted at start...

Try the mount test as explained above, after you modify fstab, and lets see...

---

### Post by david472 on 2015-12-18
ok trying it now.

I tried this :

[IMG]http://s15.postimg.org/p5xuw87ob/20151218_130544.jpg[/IMG]

It still asks me to mount it.  Sigh

---

### Post by darkod on 2015-12-18
Doesn't look good unfortunately. Post the output of:
```
sudo blkid
```

But I don't have high hope for the data any more...

---

### Post by david472 on 2015-12-18
[IMG]http://s16.postimg.org/tkoj4yied/20151218_135507.jpg[/IMG]

If worse comes to worse, I am going to try and delete the RAID and get a new 1TB HD and start over, taking the old HD out (hopefully with info intact).

---

### Post by darkod on 2015-12-18
Well, I think we explored all possibilities... I have no more ideas. The partition with the data is simply not showing up.

If you are willing to break the raid and see if the data is there on the single disk, you don't need a new 1TB disk for that. You already have two, right? The old and the new one.

Go through the links I posted in the previous posts, about resetting the disks. It looks like the data is kept in such case (under the assumption the data is there right now, don't forget that). When the array breaks up you should get two separate disks. Then you can search if the data is on the old disk. The new one probably would not have it anyway.

That's all you need to test if the data is there. No need for buying another disk.

If the data/partition is not there, there is still hope to retrieve it using tools like testdisk. The thing is that even if new array/partition was created over the old one, it has never been used, which means there is no data overwritten. Assiming the Intel Raid didn't overwrite it. So you could try hipotetically restoring the partition...

So what have you decided? Breaking up the raid? Be careful not to delete it, only to reset the disks as non raid members. I think the Intel controller calls the option like that.

---

### Post by david472 on 2015-12-18
AT this point, I am going to break up the RAID

1) I need to understand how to look on HD using Ubuntu - is that the testdisk that you said?
2) If the data is there, I am going to take the old drive out and put it aside.  Buy a new one and start over knowing that the data from the old one is safe.
3) Do I just go to the RAID BIOS and reset from there?  AND I just found out, it gives me a warning "RESETTING the disk will erase all DATA"
4) On the RAID bios page, it tells me that ONE DRIVE is NON-RAID.

---

### Post by darkod on 2015-12-18
Which one? The small one or one of the 1TB disks?

---

### Post by david472 on 2015-12-18
Yes, it is the smaller one - so that is correct.

I guess I am going to have to buy a new drive or something to try and salvage the old one by not using it.

---

### Post by darkod on 2015-12-18
OK, but I don't see how that helps with getting the data out. Until you manage to mount and read the disk with the data, you can buy as many new disks as you want and you are still not getting closer to the data...

One thing that a new disk can help with, is that it will allow you to make a copy of the old disk and in a way insure yourself it is left aside. Then you can work on the copy and see if you get anywhere...

---

### Post by david472 on 2016-01-21
How do I make a copy of the old disk?  Sorry moved onto another project and now back to this

---

### Post by darkod on 2016-01-21
Which old, one of the raid disks? You can clone a disk with various tools, like clonezilla, dd, etc... Search on the internet for your preferred tool.

Although I can't see that helping you too much, because you will not be able to read that disk same like you can't read the current ones. They depend on the raid you had configured, and it is not assembling them now. But you can try anyway...

---

### Post by david472 on 2016-01-24
Yes, I am going to try and hook up an external drive to the system (the same system with RAID) and see if I can see what is on the RAID hard drives.

Are you saying that I am better off CLONING the entire drive rather than trying to copy the files onto another drive?  I am not even sure if I can see the other drive, so that is yet to be determined.
What would be a good program to try and see what is on the RAID drives?

---

