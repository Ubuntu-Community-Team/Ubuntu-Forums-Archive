---
title: "Update claims no more space. Inode usage almost full. Manual clean up: missing dep's."
date: 2014-06-16
forum: Server Platforms
---

### Post by Coder68 on 2014-06-16
I have been on every thread I can find, and tried every fix I could find, but not a single one has fixed this issue. 
This seems to be a bug that Ubuntu is not fixing... [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1089195](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1089195)
I need to get a confirmed step by step fix in my sandbox version so I can do it on the production server. 

**Facts**:
This is a production server. (Virtual)
I am working on a clone in a sandbox so I do not have to worry about breaking the production server further. I can try anything and reset the clone if need be.
The entire install is on one drive. 
The server is 12.04.4 LTS
I removed some of the old 3.2.0-x items.
apt-get clean, autoclean, etc do not help.
inode usage before my manual clean up was at 96% IIRC. 

Please see attached images for what I am getting from various commands.
Attached in this order - named for command: 
1. df -i
2. upgrade -f install
3. apt-get update
4. df -h
5. uname -a

I was able to delete old header files and get my inode usage down. 
At this point I thought I could just install the missing linux-headers-3.2.0-58-generic.
I found a thread that spoke to this, but I get the same error "Try -f install".
This is where I am now. 

I can reset the VM and start over at any point.

Thank you,

C68




-

---

### Post by Gyokuro on 2014-06-16
Hi

What do you mean you have removed some old stuff - I can not see how you removed them? Dpkg, apt or deleted them via rm -rf?? Your error indicates that you simply removed them and this is my guess via rm and therefor you have unmet dependencies but to help you what do you get if you enter:

dpkg --list 'linux-image*'

should give you a list of kernel and you can remove them from the system/package database via:

apt-get -y purge linux-image-whatever-kernel-should-get-removed-version

---

### Post by Coder68 on 2014-06-16
I followed a thread on manually removing them. I am looking for the  commands I used, but am not finding any rm's in the history. I removed  them from /usr/src.

Attached is the output of the dpkg --list command and the purge command.

When I try the apt-get -y purge linux-image-to-be-removed I get the same try apt-get -f install error. I was getting this before I removed any files. 

I can restore this sandbox VM from the production one if need be.

[ATTACH=CONFIG]253997[/ATTACH][ATTACH=CONFIG]253995[/ATTACH][ATTACH=CONFIG]253996[/ATTACH]

---

### Post by Gyokuro on 2014-06-16
Ok - could you post following command output:

df -h /boot

and there is no need to restore your VM - we will fix this one. However how you have removed the files in /usr/src - via dpkg, apt-get or rm? Another thing is maybe you can post the thread which you used as a  guide so we are able to check what got suggested. The problem is the package manager is unable to locate the files at your disk but they are still marked as installed in your package database.

Then we should try to clean something up:

apt-get clean && apt-get autoremove
apt-get -f install

---

### Post by Coder68 on 2014-06-16
I wish I could tell you for sure how I removed them. Since is the sandbox version, I was just trying threads until I found a fix, which I did not. There are no rm's in the recent history. I went back to days before I started to try and fix this. 

df -h /boot
[ATTACH=CONFIG]253999[/ATTACH]

I need to be able to go from broken to fixed step by step so I can fix the production version. (This is the sandbox - no worry if we kill it version) This is why I think it might be better to start from scratch. :D

I am out the door in a few minutes but will check in first thing in the morning.

Thank you.

---

### Post by elico on 2014-06-16
If you can run the command:
"touch /home/1 && ls /home/1"
as root and you can see the result of the ls you are ok by inodes point of view then the issue is not INODES but deb db or any-other issue related to the packages tree and software.

---

### Post by Coder68 on 2014-06-17
**In the sandbox version, which I have removed some files:**
Typing in sudo touch /home/ && ls /home/ worked.

I have removed the file 1.

df -i results on sandbox copy say 34% in use.


**In the production server, where I have not done any work:**
Typing in sudo touch /home/ && ls /home/ worked.

I have removed the file 1.

df -i results on production server say 100% in use, but with 1937 IFree.

---

### Post by Gyokuro on 2014-06-17
My bet is that the users /boot directory is full due to the large amount of kernels in the posted screen shots. I never understood why old kernels get never removed as on RHEL/SLES you will never have more as the current one and the former kernel and clean up occurs during the install of a new kernel or next successful boot. Ubuntu users should run from time to time apt-get autoclean/autoremove or manually clean up /boot or change the default /boot size to 512MB (however you will gain only some time this should get fixed from the vendor asap). I have checked launchpad bugs concerning this problem and it seems it got never resolved in an automatic way. Suse handles it via a do_purge which get called from systemd.

---

### Post by Coder68 on 2014-06-17
Which is why I removed some of the old kernels.

How do I fix this? I can do any automated stuff...

---

### Post by Coder68 on 2014-06-19
Bump.

---

### Post by Coder68 on 2014-06-20
I could really use some help. :frown:

---

### Post by Bashing-om on 2014-06-20
Coder68; Hello,

Let's see if we can cut to the heart of the matter. Look'n at the probable cause as the /boot directory full of old kernels;
As well, what release are we dealing with here , as the method to remove the kernels differs from earlier releases ?
Show us the output - BETWEEN code tags - of terminal commands:
```

lsb_release -a
uname -a
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Will tell the tale and we will see what can be done.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-06-23
This is still an issue. Can anyone please help?

---

### Post by Bashing-om on 2014-06-23
Coder68; Hello,

My post #12 still applies, please provide the requested outputs - formatted by the code blocks - so we can continue.

[INDENT][INDENT]my regards
[/INDENT][/INDENT]

---

### Post by Gyokuro on 2014-06-23
The user already posted details: like 12.04.4 (testing the commands in a VM) and in post #3 a screen shot of installed kernels but I agree an output in text form is easier to read. Following command should purge all old kernel except the current one:

**sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')**

- HTHT

---

### Post by Bashing-om on 2014-06-23
@ Gyokuro; sure I do agree, but

Related headers, not shown or known that also need to be removed - keeping what is current.

[INDENT][INDENT]just my way of doing it
[/INDENT][/INDENT]

---

### Post by Gyokuro on 2014-06-24
@ Bashing-om: Sorry my bad in case my post was rough - was not my intention - tried to save you some time :-)

---

### Post by Coder68 on 2014-06-25
Sorry, I was out for a bit. I was also not showing any updates until today. 

Here are the request. I had to do it two posts as it only let me do 5 images in one post.

[ATTACH=CONFIG]254237[/ATTACH][ATTACH=CONFIG]254238[/ATTACH][ATTACH=CONFIG]254239[/ATTACH][ATTACH=CONFIG]254240[/ATTACH][ATTACH=CONFIG]254241[/ATTACH]

---

### Post by Coder68 on 2014-06-25
Here is the last image.

[ATTACH=CONFIG]254242[/ATTACH]

---

### Post by Coder68 on 2014-06-25
I get a bash error !d; event not found
**sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed   '/^ii/[COLOR=#ff0000]!d;[/COLOR]/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*   [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')**

---

### Post by Bashing-om on 2014-06-25
Coder68; Hi !

I am more than willing to try and help. Please observe and comply with my post #12 for my assistance. Those commands will tell us a lot, amongst witch is the kernel you are using that we MUST keep, all the kernels and related files that are installed and the numbers to use to remove them properly with the package manager. It is difficult to manage working from a screen shot, posted outputs make life here much easier.
Please use code tags to post those outputs per the posted tutorial.

This ain't
[INDENT][INDENT][INDENT]nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-06-25
> **Gyokuro said:**
> @ Bashing-om: Sorry my bad in case my post was rough - was not my intention - tried to save you some time :-)

Hey, no offense taken. All help on this forum is a good thing !

It's open source ->
[INDENT][INDENT]we are all in this together
[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-06-26
I am unable to post the outputs in text form. The sandbox is only available through vCenter's console, hence the screenshots. (I can't ssh in.)

---

### Post by Bashing-om on 2014-06-26
Coder68; Well, well ..

Maybe no big deal, depends on your interpretation skills.

Here is how I have removed old kernels from the CLI using the package manager.
Do terminal commands:
```

uname -r ## to KNOW the kernel you are presently booting
dpkg -l | grep linux- ## to see the images and HEADERS to be removed.##
sudo dpkg -P linux-image-3.2.0-{29,38,39}-generic
sudo dpkg -P linux-headers-3.2.0-{29,38,39}-generic
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##not a release upgrade, this will pull in the new kernel and header files - WE hope !##

```
You MUST keep the current kernel ( image and headers), and remove all others. As I do not know what headers are installed, the above is but a suggestion, check, verify, remove also the corresponding headers for the installed images that will also be removed.

Once the old images and headers are removed, and the new kernel is installed:
Reboot at this time to boot with the newer kernel;

If the above 'dist-upgrade' completed and a new kernel was installed. - Then -
Repeat the procedure to remove the now old kernel(s) .. 
Ain't nothing to it
[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-06-26
I ran uname -r which gave me: 3.2.0-64-generic

Then I ran the following lines:
sudo dpkg -P linux-image-3.2.0-{29,38,39}-generic
sudo dpkg -P linux-headers-3.2.0-{29,38,39}-generic
sudo apt-get update
sudo apt-get upgrade -f

I get an error to use -f on the upgrade. When I use -f I get the following error:

[ATTACH=CONFIG]254260[/ATTACH]


When I try the dist-upgrade I get the following error:

[ATTACH=CONFIG]254259[/ATTACH]

Thank you.

---

### Post by Bashing-om on 2014-06-26
Coder68; Welp;

Real tough to work from a screen shot in this case.
Let's try and see if we can give the package manager what it wants:
```

sudo apt-get install linux-headers-3.2.0-58-generic

```
Check for typos on my part and MAybe there is enough headroom to install the header file... else going to have to jump through some hoops to make some room.
There is still a way
.

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT][/INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-06-27
When I try to run the install, I get an error saying to run -f:
[ATTACH=CONFIG]254275[/ATTACH]

Running the install -f command, gives me the following result:
[ATTACH=CONFIG]254276[/ATTACH]

Saying Y and letting it run gives me the following errors:
[ATTACH=CONFIG]254277[/ATTACH]

It seems to be a dreaded loop I can't get out of!

---

### Post by Bashing-om on 2014-06-27
Coder68; Well, wellll ..

As the package manager is already broken, I can not see how manually intervening here to remove images can hurt things more.
With that in mind ( NOT normally a good thing to do, all others be warned !!), let's consider manually removing the images and then try and fix the package manager.
We must be assured what kernel is booting, and what images are installed on the system,
Provide the outputs of terminal commands:
```

uname -a
ls -la /boot/initrd.img-*

```
To prepare to remove the old initrd.img files, see if "apt-get -f install " will pick up the missing headers, and then we purge the old images. Then see what state the package manager is in.

Anybody with a better suggestion, now is the time to speak up. I have no confidence that any "configure -a" commands will be of effect in this case.

[INDENT][INDENT]rip it all out
[INDENT][INDENT][INDENT]and then rebuild
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-06-27
Same errors. 

I went back to the oldest kernel I could. No help.

Is there a way to uninstall the current version of linux-image-server 3.2.0.65.77?

This is a virtual copy of the real VM. I can re-copy it and start over. With just your instructions... it had other stuff done to it before you came on the scene.
[ATTACH=CONFIG]254286[/ATTACH][ATTACH=CONFIG]254285[/ATTACH]

---

### Post by Bashing-om on 2014-06-27
Coder68; Yeah .

I am keeping in mind this is a Virtual Copy of the production machine. And to be honest, at this point what ever it may take too fix this virtual machine will no longer apply to the production server fix. As I understand, this Virtual copy is but a test to see what is required in the real machine.
SO, yeaah, let's reimage this copy to what is on the production machine, and start all over from scratch. Seeing what is.
We will then try and go by the book and stay within the realm of the package manager.

Else we can continue here for the learning exercise - what not to do and how to fix it. To pursue fixing this copy - and we stay on the same pages - need to know the results of the commands from my last post. We can then remove files and rebuild the package manager's index files.

[INDENT][INDENT]all in a day's work
[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-06-30
I am waiting for the systems admin to create new copy of the server in the sandbox environment. (Might take a day or two.) Then I will start over with your commands. 

If that does not work, then I will have to look at building the server over. 
This is a **very locked down **DMZ box... and is not a fast build. I will want to ensure that I do not have these issues again... (I never had issues with this server until it ran out of inodes.)

Thank you,

C68

---

### Post by Bashing-om on 2014-06-30
Coder68; Not at all a problem, at your time and pace.

This is a situation I have dealt with several times, and we will get through this one also. So long as the package manager is in good shape, I expect it to me nothing more than letting the package manager take care of all the details. Just tell it to remove the kernels - to make the room in the /boot directory - and remove those old headers.
When you are ready:
```

df -h
df -i
dpkg -l | grep linux-

```
to start the ball rolling again.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-07-01
We had no power most of the day to our main offices. Spent all day running temp power and setting up laptops... might be another day or so, and then I am gone on staycation.

---

### Post by Coder68 on 2014-08-01
OK. I am back. Sorry for the long delay, we had major issues at work due to a switch stack crashing randomly. 

With a fresh copy of the offending VM, what should I do first? BTW, if this does not work, I will just rebuild it from scratch. (And hopefully avoid this issue again.)

Thanks, 
C68

---

### Post by Bashing-om on 2014-08-01
Coder68; OK, All good now !

Meanwhile here at the ranch, Let's look at the current status on this "testing" install:
```

dpkg -l | grep "linux-"
df -h
df -i

``` to see what is to be done.

[INDENT][INDENT]look first,
[INDENT][INDENT][INDENT]then act, once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2014-08-02
[http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) provides a script that somewhat simplifies the kernel-cleanup effort. I suppose using **aptitude** instead of apt-get will also handle it.  Aptitude automatically cleans up unused packages - though I don't know if it does old kernels or not. Sorry.

I've been using the script in that link to generate the old kernel removal commands for over a year. It is relatively safe and lets the person running it double-check the command.

---

### Post by Coder68 on 2014-08-05
Sorry, the VM guy was updating the servers and wanted me to wait. 

I will post my results as soon as I get through my morning stuff. 

What do you think of the script post by TheFu?

---

### Post by ian-weisser on 2014-08-05
> **Coder68 said:**
> BTW, if this does not work, I will just rebuild it from scratch. (And hopefully avoid this issue again.)

You probably selected LVM when you installed. There were a couple bugs with autoremoving those kernels upon upgrade when /boot was on a separate partition, most since fixed. That's one of the causes...so you can avoid it.

> **Coder68 said:**
> What do you think of the script post by TheFu?

It's a script that does all the right things...but it probably won't help you. It does all the same things you are already trying.

The problem here is that apt-get  keeps track of stuff you previously told it to install. So when you run apt-get, one of the first things it does is look to see if anything is waiting to be installed...and a whole kernel is waiting! So it tries to install, and fails due to a lack of inodes. But it still remembers that you want it installed for next time.

-f won't work because you don't have a package conflict. You have a full partition. Totally different kind of problem.

There are lots of ways to solve the problem. Here's one way:

 1) Identify an old kernel package (any kernel you are NOT currently running)

Example:
```
$ uname -r
3.13.0-32-generic
```
So kernel -32-generic is the one I should _not_ remove.

```
$ ls /boot | grep initrd
initrd.img-3.13.0-30-generic
initrd.img-3.13.0-32-generic
```
I should keep -32, so I can remove -30

2) Remove the kernel package (and it's associated headers package) using dpkg instead of apt-get. Example:
```
$ sudo dpkg --remove linux-headers-3.13.0-30-generic
$ sudo dpkg --remove linux-image-3.13.0-30-generic
```

3) You have probably freed enough inodes to let apt-get install the newer kernel. Let's also run 'autoremove' in case you had any -extra kernel packages orphaned by that -30 kernel.
```
sudo apt-get update && sudo apt-get autoremove && sudo apt-get upgrade
```

4) Now that apt-get is working again, you can use apt-get to remove the other older kernels.
Or, if apt is not working yet, you can continue to remove older kernels using dpkg until you free up enough inodes and apt does start to work...or you discover a different problem.

---

### Post by Coder68 on 2014-08-05
I have attached images for each command you gave me.

[ATTACH=CONFIG]255258[/ATTACH][ATTACH=CONFIG]255257[/ATTACH][ATTACH=CONFIG]255256[/ATTACH][ATTACH=CONFIG]255252[/ATTACH]

---

### Post by Coder68 on 2014-08-05
Last two.

[ATTACH=CONFIG]255259[/ATTACH][ATTACH=CONFIG]255260[/ATTACH]

Thanks!
C68

---

### Post by Coder68 on 2014-08-05
Uname -r shows 3.2.0-57-generic.

---

### Post by Bashing-om on 2014-08-05
Coder68; Morning !

-and- @ ian-weisser, so nice of you to pop in here, your sage advise and background info is informative and a comfort to accept.
 
OK, let's try this - bearing in mind it is difficult to work from screen shots. Trying to piece this together.
Let's do:
```

sudo dpkg -P linux-headers-3.2.0-{43,44,45,48,51,52,53,54,55}-generic
sudo dpkg -P linux-image-3.2.0-{43,44,45,48,51,52,53,54,55}
sudo dpkg -P linux-image-3.2.0-{43,44,45,48,51,52,53,54,55}-generic

```
Which should give us some head room, take a breath and see where we are and what else now remains to be done .

Be a lot more consistent if we can work from exact copy and paste for command outputs .

[INDENT][INDENT]small steps;
[INDENT][INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-08-08
Sorry for the delay yet again. Was out of office working on a project. I will do this on Monday and send back the results. 

Thank you!

---

### Post by Coder68 on 2014-08-14
> **Bashing-om said:**
> Coder68; Morning !

-and- @ ian-weisser, so nice of you to pop in here, your sage advise and background info is informative and a comfort to accept.
 
OK, let's try this - bearing in mind it is difficult to work from screen shots. Trying to piece this together.
Let's do:
```

1. sudo dpkg -P linux-headers-3.2.0-{43,44,45,48,51,52,53,54,55}-generic
3. sudo dpkg -P linux-image-3.2.0-{43,44,45,48,51,52,53,54,55}
2. sudo dpkg -P linux-image-3.2.0-{43,44,45,48,51,52,53,54,55}-generic

```
Which should give us some head room, take a breath and see where we are and what else now remains to be done .

Be a lot more consistent if we can work from exact copy and paste for command outputs .[INDENT][INDENT]small steps;[INDENT][INDENT][INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


OK. I did this, but I screwed up. I did them in the order you see above, 1,3,2.... (I arrowed up and forgot to remove the -generic). When I ran the one listed as 3, I get a warning that there is no package matching linux-image..... 43-55.

Is this an issue? I can have the sysadmin restore a copy.

Thanks!

---

### Post by TheFu on 2014-08-14
> **Coder68 said:**
> Is this an issue? I can have the sysadmin restore a copy.

No.

Uh ... why isn't the sysadmin handling this issue?

---

### Post by Bashing-om on 2014-08-14
Coder68; Hey !

see TheFu's last -- I too am wondering if this is a training exercise for your benefit.
Does not matter as this forum also functions as a teaching medium. But am curious as the end is a production server, why the matter is not expedited ?
OK, with the above done ( now real old info IRT the real production server), what is the status in this "test bed".
show us the new condition:
```

df -h
df -i
dpkg -l | grep linux-

```
and we see what remains to be done.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-08-14
He don't know Linux. :) 

I am the security admin and I do know Linux... but I am not a guru at it, but I am pretty good.

---

### Post by Coder68 on 2014-08-14
Here you go:

[ATTACH=CONFIG]255479[/ATTACH][ATTACH=CONFIG]255480[/ATTACH][ATTACH=CONFIG]255481[/ATTACH][ATTACH=CONFIG]255482[/ATTACH][ATTACH=CONFIG]255483[/ATTACH]

---

### Post by Bashing-om on 2014-08-14
Coder68; OK !

We are looking good, have operating head room now ! That production server should run.
All that is left is to remove those old un-needed kernels.
To preclude me making typos - so I can copy/paste let's do this:
```

sudo apt-get install pastebinit
dpkg -l | grep linux- | pastebinit

```
Passing that resulting URL back here to us, and I will craft up the command to remove them.

I make enough typos and am trying
[INDENT][INDENT][INDENT]to make haste slowly
[/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-08-15
After a nightly reboot... it crashes. I am not sure if this is a VM issue, or a issue with the SAN in the old sandboxed environment. Recovery mode gives the same result. So do previous Linux kernels. 

The 8th line says Cannot open root device "sda1" or unknown-block(0,0)

Other VM's are running OK off the same LUN, so I am suspecting it is the VM. This is why we test in a sandbox first... :D

I can't get it restored today, the sysadmin is off. I do not dare touch "his" stuff. 

[ATTACH=CONFIG]255503[/ATTACH]

---

### Post by TheFu on 2014-08-15
> **Bashing-om said:**
> 
Passing that resulting URL back here to us, and I will craft up the command to remove them.


Or he could just use the script I posted a link for last week.
I'm lazy, hence the script. It works and won't remove the currently running kernel.

Of course, I haven't read any later posts carefully (just the email notice), if the system isn't booting currently, then using boot-repair may fix it. If not, the boot-repair process will post the current config for us - to craft a grub-update command.

Ok - - so perhaps I haven't been paying enough attention here, but this is running inside a VM?  There are many things we can do with that - more options. Which virtualization is being used? Specifics, please.

---

### Post by Coder68 on 2014-08-22
It is sitting on an EMC LUN being run by and ESX 5.5 server. I had him restore it today. (The sand-boxed VM is sitting on old hardware.) With the huge medical breach with CHS, I was busy doing other investigations... 

I will rerun the steps next week. 

Thank you for sticking with me on this. I know it is slow going but I am a single person responsible for a large companies security!  Thanks again!

---

### Post by TheFu on 2014-08-23
For out-of-inode issues, create a new vHDD of the size you like, connect both the old (A) and new (B) vHDDs to the same VM, boot off a save-your-butt distro (or live Ubuntu ISO) and move all the data from A to B. If you use fsarchive, the target file system can be grown.

If there is plenty of real space and it is just inodes that are short, use tune2fs or re-allocate the /boot partition with a larger (4x? or 10x?) the number of inodes from the default.  Small partitions never seem to get enough inodes - the default estimation calculation used by ext4 was designed for larger partition sizes.  Using ext2 (no journal) for /boot isn't a bad idea, though I don't bother on VMs. Personal decision.

---

### Post by Coder68 on 2014-08-25
Doing this in the correct order gives me the following error on line 2.

```
dpkg: warning: there is no installed package matchinglinux-image-3.2.0-43
Same error for each one, 44, 45... 55
```

The third line ran and appears to be find.

Rebooting.... results in the same error.. even in recovery mode.

```
VFS: Cannot open root device "sda1" or unknown-block(0,0)
```

Going back a few kernels allows it to boot. 

Now what? 

Again, thank you!!!

---

### Post by Bashing-om on 2014-08-25
Coder68; Welp;

Hard to say, a lot of time has past, and things can and do change.
Let's look and see what is:
```

ls -al /
ls -al /boot
dpkg -l | grep linux-

```
Fix and remove and see what the status is then.

[INDENT][INDENT][INDENT]it is a process
[/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-08-26
Here the outputs of ls commands.

---

### Post by Coder68 on 2014-08-26
Here are the outputs of dpkg.

Thanks again!

---

### Post by Bashing-om on 2014-08-26
Coder68; shucks !

Can't tell from a screen shot.
The system expects to boot kernel 3.2.0-57 ; (an old one - hummm, why ?), and I can not even tell if that kernel is installed from the screenshot of the output of the 'dpkg' command.

All we know presently is that there exist tons of old kernels that -because of no operating head room - is causing all kinds of problems.

Can you come up with some way to copy and paste the commands outputs , say to a file  and transfer the contents back here to the post so the outputs are sensible and formatting is retained ? 
What is required at this time is to ascertain what kernel is booting and remove a bunch of these old kernels.
Must keep the kernel that is booting per the symlink in '/'' AND does that link agree with the output of "uname -r" ??
Must keep the kernel that is symlinked as .old in '/'
Must keep the 2 most current kernels ( headers and images)

All the rest need to be gone.

It is as simple as that, but, making it happen - with no head room - may not be so simple.

As templates; you can try something like:
```

sudo apt-get autoremove linux-image-2.6.32-22-generic linux-image-2.6.32-21-generic
sudo apt-get autoremove linux-headers-2.6.32-22-generic linux-headers-2.6.32-21-generic
##OR maybe and incantation like this may work##
sudo dpkg --purge linux-image-3.2.0-36-generic
sudo dpkg --purge linux-headers-3.2.0-36-generic

```
Once you have the head room back, then you can see about fixing the remaining kernels and the booting situation.

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-08-27
I will have to physically go to the sandbox and jack into that switch to SSH in. But first I must set it up. I will get back with you soon.

Thanks!

---

### Post by Coder68 on 2014-09-17
OK. I finally have got some time starting later this afternoon. I will be able to ssh in to the sandbox as well. :) 

I will give these a try:

> sudo apt-get autoremove linux-image-2.6.32-22-generic linux-image-2.6.32-21-generic
sudo apt-get autoremove linux-headers-2.6.32-22-generic linux-headers-2.6.32-21-generic
##OR maybe and incantation like this may work##
sudo dpkg --purge linux-image-3.2.0-36-generic
sudo dpkg --purge linux-headers-3.2.0-36-generic

via SSH and report back. If I cannot fix this by the end of the week, I will have to rebuild it from scratch. The SSL cert is about to expire.

I also need to fix the issue where it will not boot to the most recent kernel. I have to go back several to get it to boot. It needs to auto reboot nightly.

---

### Post by Bashing-om on 2014-09-17
Coder68; 

K

---

### Post by Coder68 on 2014-09-17
I am going to build a new server instead. I can do that faster then fix it. However, how do I prevent this issue from occurring again? I will be using 14 LTS instead of 12.

---

### Post by Bashing-om on 2014-09-17
Coder68; Welp ;;

On this new server, IF you set it up with a separate /boot partition, make sure it is large enough to meet your needs.

In 14.04 the "autoremove" command will also remove old kernels, so this situation will never arise again with the application of just the normal house cleaning routine.

But, it always pays to pay attention to what the operating system is doing, particularly in respect to disk space ! .. I always run 'df' and 'du' on regular basis just to make sure nothing is overly logging to the log files Nor have I crowded out my "user" space.
IF I can boot cleanly, and
IF the log files are orderly I can safely assume - on my system - all else is orderly too .

[INDENT][INDENT]take care of the pennies
[INDENT][INDENT][INDENT]and the dollars will take care of themselves
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-17
I am sitting at the partition section of the install. I am looking around for recommendations. LVM will **not **give me a separate /, /boot right?
I am building this with 30 Gig of space, so that is not an issue. This does not have users except for the admin of course. It is basically an idle server that relays information. Other then updates, it should not grow in size at all. 

Suggestions?

This is what I currently have.

/boot  ext4 1 GB
swap - 4 GB
/   ext4 27.2 GB

Thoughts?

---

### Post by Elfy on 2014-09-17
If you're not going to use LVM - then I would not be creating seperate partitions like /boot unless you have a REAL reason to do so.

LVM does give seperate /boot - it sets up /boot seperately - BUT it sets size to 256Mb or so.

Once you've installed look into resizing LVM - it is possible and as far as I am aware you can do so without needing a livesession [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

Most importantly, watch what's going on with the system before it goes wrong.

---

### Post by Coder68 on 2014-09-17
OK. So if I do a guided LVM setup I will get a /boot and a swp and a /root.??

I had never had this issue before and caught it early on. A vulnerability scan showed that it had not been updated recently. When I tried to update it manually it would not. That is where this issue came in. 
I am not sure what I could have monitored to find out this was becoming an issue. The website never stopped working... and still works. 

What should I have been monitoring?

---

### Post by Bashing-om on 2014-09-17
Coder68; Welp...

IF you have no over riding reason not to use encryption (LVM, on that initial install) DON'T ! That is a level of complexity in times of trouble can not be overcome,
Also there is presently this bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
where /boot is created to small:
I am running on this old box that used to be a file server in my glory days; This is my current configuration:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  1.8G  2.8G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  736K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   21M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  1.3G  7.8G  14% /home
/dev/sda8       4.7G  1.8G  2.8G  39% /var

```

note that I do not use or believe in a separate /boot partition. That old anachronism is but a means now-a-days of problems.
If you anticipate heavy loggage, you will want /var larger. You will also take note that I run a "dynamic" /tmp in ram.
What you do not see here is 2 other hard drives and my /data partitions, these I choose not to automount. It takes but a tic to mount and UN-mount as I have a need to access them. Following this method I have yet to ever experience any corruption in my 'data' or in my backups !

Depending on the type of server, you will also have to make up the application directories. Again, only time will tell as to what size they should be.
As you can see there are no set rules. It is your system, set it up for how you use it, and for what you intend to use it as/for.
With good backups and a good restoration plan it is but a matter of 20 minutes to (RE-)install after one has made any changes to the system.
- I also maintain a "change log" of anything I change on the operating system, and you best believe that file is backed up and backed up again -
It is always a process of learning and changing to what you have learned. Ain't no big deal with P,P,P,P.P.P.P
(Prior Prudent Planning Preventing Pi** Poor Performance).

[INDENT][INDENT]install
[INDENT][INDENT][INDENT]adjust
[INDENT][INDENT][INDENT]all good in the end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-18
OK, now I am confused. Do I manually create the partitions I created or not?

Here are my current options:
[ATTACH=CONFIG]256519[/ATTACH]

So, should I be choosing the one that is highlighted one and let it do all of the partitioning for me? Or should I just leave my current setup of having a /boot, swap, and a /, as seen below. 

/boot  ext4 1 GB
swap - 4 GB
/   ext4 27.2 GB

---

### Post by Bashing-om on 2014-09-18
Coder68; Well, well;

I can only say what will result, I can not tell you how you will use your system.
OK, LVM is a great thing for a server environment with multi disks. LVM allows re-sizing and moving partitions around on the fly - dynamic allocation ! Be aware that the option you have highlighted will do just as it says, take up the entire disk(s) and there is not a thing 'wrong' with that if this is a dedicated server.
Also, not a thing wrong with setting up as you think, finding out that it is not what you wanted, and (RE-)installing once more. As a general rule, you want you /home on a separate partition than that of the operating system - a greater degree of protection and security for your personal stuff. I also advocate a separate /var partition for the event of excessive and/or run amuck or malicious attacks, when the logs fill up will not knock the server down.

Mission critical means raid, and I do like LVM on top of raid. As you can see there are a myriad of options available and it is mind boggling to decide on what is best - it is your best interest and only you know what that is. Do you have the means to support your choices ? Knowledge is power.

Install;
Keep good backups;
[INDENT][INDENT][INDENT]and do it different next time
[/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-18
This is on a SAN which is in RAID 6. However, I am not running RAID on the server box. This web server runs a static never changing website. Only the OS, which gets updates, changes. This site is just used to relay information form one server to another for monitoring purposes. I choose the basic default setup last time as I have never had issues with that at home on any of my Ubuntu servers or desktops. However, I do believe it was a bug that was in 12.04 LTS that bit me. Otherwise, this would not have been an issue. I would use some monitoring on this server if I knew what to monitor for the issue I was bit by. 

There are no users on this other then the administrator. 
There is no need for a /var
There may be a need for a /tmp for log files. 

I am leaning towards the LVM auto partition layout. However, if I want to use a /tmp, I can't use LVM default settings, can I?

---

### Post by Bashing-om on 2014-09-18
Coder68; Humm,

> 
 However, if I want to use a /tmp, I can't use LVM default settings, can I?


One way is after all set up with LVM, add the tmpfs as a ram device:
```

#/moving /tmp to ram 27may13
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```
by adding that entry to "/etc/fstab" . But, you have to have the ram to do this.. say as a minimum 4 Gigs (?). 

Get it installed and up

[INDENT][INDENT]tweak'n time
[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-18
Argh. I am not sure what is best to do.

Why would I not want a /boot partition as suggested by another user?

If I have the following:

swap - 3 GB since I have 2 GB of RAM
/tmp - 5 GB for log files
/ - 22 GB for other data like the website code. 

That should work great. RIGHT?

---

### Post by Bashing-om on 2014-09-18
Coder68; Well.

My thoughts,
IF youhave an old old bios then I can see using a separate /boot partition.

Keep in mind there is no such thing as the best way to do anything, it is what suits your use case.
But, there is "better practice" ! There are lots of ways to set up booting.


However, separating /boot is more complex and generally not a good idea, especially as Ubuntu defaults to using no separate boot partition. A separate /boot is something of an anachronism, dating back to limited PC BIOSes that could only handle small disks, so the boot files had to be at the start of the disk. Nowadays, this is no longer applicable and I don't use a boot partition on anything ---I have learned my lessons the hard way -. You do have options. The best in the long term, but the most work, is to back up your install, using either a second drive or a pile of DVDs, and repartition the disk from scratch to have the set up YOU want.

It applies similarly;
If you want to install GRUB2's boot code to the boot sector of a partition for some strange reason, you may use something like /dev/sda1 or /dev/sda2 for writing GRUB's boot.img to a partition boot sector. The practice of installing GRUB2 to partition boot sectors is not encouraged. It reduces GRUB's reliability and it could be dangerous to other operating systems if users use the grub-install command carelessly or ill-informed and write GRUB to the wrong boot sector. Keep it simple and standard, install the boot code to the MBR ( sector 0 ) Where bios expects to find the boot code.
In particular to LVM .. the boot code must be installed outside the volume group(s).

Now all that said, there is nothing "wrong" with the manner you propose to install with. It will work ! Using a separate /boot partition one has to keep a closer eye on it for space constraints - as you have learned the hard way - 85% capacity, start house cleaning !.

[INDENT][INDENT]it it works
[INDENT][INDENT][INDENT]don't knock it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-19
After reading that, I will just use the default LVM setup. I have never done this one before, but I doubt it is any different then next - next -apply. I will do some research. 

Thank you,

C68

---

### Post by Coder68 on 2014-09-22
I setup the server during install to auto update.

1. Do I need to write my own script to do this since it is already set?
2. How do I CORRECTLY run autoclean on a regular basis? 

My update script that I had **on the broken server** had autoclean in it!!! I must have done it wrong... 



[LIST]
[*]#!/bin/bash
[*]# This script will auto update the server weekly.
[*]apt-get update
[*]apt-get upgrade &#8211;y
[*]apt-get autoclean
[/LIST]

I have a script to reboot daily at 4 AM to ensure that any update that requires a reboot, will get one.

---

### Post by Bashing-om on 2014-09-22
Coder68; Morning !

No, there is no pressing need to have a cleanup script, but if you do, the script must have root privileges to perform the functions.
I do prefer "hands on" to occasionally look over the system and at that time do some cleanup. - I do want to know what is going on with my system - and in the event that something breaks in the update/upgrade/cleanup process, I am there to at least have a good idea of what broke, where. Say every 3 or 4 months take a look, depending on how heavy of usage the system gets.

Are you up and running now on the new install ? Did you opt for "LVM auto partition layout" ?

[INDENT][INDENT]depending on what is
[INDENT][INDENT][INDENT][INDENT]is what I do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Michael_McKenney on 2014-09-22
sudo apt-get autoremove did not cleanup over 30 Linux-images.  I had to use Synaptic.  I did all the 2.x kernels.  Rebooted and then did 3.0 to 3.11 kernels.  I am on 3.13.

---

### Post by Coder68 on 2014-09-22
No, after reading about LVM, it seemed to me that I did not need it. I hope the bug that was in the last version I was running is FIXED in 14!

---

### Post by Coder68 on 2014-09-22
It seems that more and more issues are creeping into Ubuntu. It used to  be build it and it just worked. Now it seems I am always having to fix *something*!

How often does the auto update feature, that I turned on during the build, run? I was doing a manual update daily.

---

### Post by Bashing-om on 2014-09-22
Coder68; Huh ??

What release did you (RE-)install ?? I assure you that in release 14.04, from experience, the command "sudo apt-get autoremove" removes the old kernels, but NOT the kernels prior to 13.10 . In a clean install of 14.04 I would expect there to be only 1 old kernel after the update/upgrade process.
There should have only been 2 kernels installed; that initial one, and the latest kernel available, and none others at this time !

[s]I have no idea where this is coming from or what it is:[/s]
> 
sudo apt-get autoremove did not cleanup over 30 Linux-images. I had to use Synaptic. I did all the 2.x kernels. Rebooted and then did 3.0 to 3.11 kernels. I am on 3.13.


[s]I am so lost as to what is happening.[/s]

Once more, if there are multiple problems at this time - DO a fresh clean install from scratch of the current-est Long Term Support release 14.04; for the best in long term results.

For my use case 14.04 is stable and is much smoother and faster than 12.04.

Else: we clear the deck, get us a firm foundation from which to look at things, and take up the battle once more.

[INDENT][INDENT]ain't one to run away
[INDENT][INDENT][INDENT][INDENT]from a fight
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-22
That 30 kernel statement was not from me. 

It was 12.04 LTS that had the issues. I did a clean install of 14.04 LTS.  I am now wondering about the "auto update" that I turned on during the install. 

My only question at this point is how often does the auto update feature run. I was running my script to auto update and auto clean weekly. I was and will be again, rebooting nightly.

---

### Post by Bashing-om on 2014-09-22
Coder68; ump, pardon me, please.

Teach me to read, and pay closer attention.

Got me scratching my head as to where on a server - no GUI - the config files for " update-manager " ->  auto update are. I am going to have to think/research before I can respond further.


Forcing me to learn, I love it !

---

### Post by Bashing-om on 2014-09-22
Coder68; Hey;

Looky what I found !
[https://help.ubuntu.com/14.04/serverguide/automatic-updates.html](https://help.ubuntu.com/14.04/serverguide/automatic-updates.html)

Appears to be the answer to all your questions.
unattended-upgrades
:: Update-Package-Lists
:: Download-Upgradeable-Packages 
:: Periodic::AutocleanInterval
:: Periodic::Unattended-Upgrade

And I bet can be configured to do a lot more.
[INDENT]ubuntu:[/INDENT]
[INDENT][INDENT]seek and ye shall find[/INDENT][/INDENT]

---

### Post by Coder68 on 2014-09-23
Nice find. Looking into it now.

---

### Post by Coder68 on 2014-09-23
Here is what I have.  If I understand what I read correctly, this will, on a daily basis, update the package list, will download packages that can be upgraded, and install them. It will also run autoclean once a week.

/etc/apt/apt.conf.d/10periodic

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";

It looks like the correct log to see updates has a different name from each day it updates... that will be harder to monitor by an automated means at my disposal... Security is my job, not servers. If you recall, I am doing this because I am the only Linux guy here!

---

### Post by Bashing-om on 2014-09-23
Coder68; Hey, hey :

Yeah, I think that will do nicely. As to the logging. I bet there is a config file "somewhere" and we can make it append the info rather than overwrite/create anew.
So, let's start with the log file name that it creates. and the location. I see what I can come up with for the means to alter the default behavior.

[INDENT][INDENT]2 heads are
[INDENT][INDENT][INDENT]better than 1
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-09-23
> **Coder68 said:**
> 
/etc/apt/apt.conf.d/10periodic

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

If you have a /etc/apt/apt.conf.d/50unattended-upgrades file, the final line of your 10periodic file may conflict.

---

### Post by Coder68 on 2014-09-24
I pulled those lines from here: [https://help.ubuntu.com/14.04/serverguide/automatic-updates.html](https://help.ubuntu.com/14.04/serverguide/automatic-updates.html)

I did not modify the /etc/apt/apt.conf.d/50unattended-upgrades file.

---

### Post by Bashing-om on 2014-09-27
Coder68; Hey;

Hope things are now well in hand, 
If so and this matter is now satisfied ->
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.

[INDENT][INDENT]we move'n on to other others
[/INDENT][/INDENT]

---

