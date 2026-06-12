---
title: "really messed up, initramfs only"
date: 2012-01-15
forum: Server Platforms
---

### Post by Hylianux on 2012-01-15
Hey, somehow I've royally messed up my installation of ubuntu server 11.10 with the fsck command.

At this point, the best course of action for me, I'm thinking, is just to zip my my whole home directory and paste it all back into a new installation.  

The problem is I can't access it.  When I boot in, I can only access things through an initramfs prompt, which doesn't have much functionality.  if i go to /root/home/ i can see my home directory there, as well as the home directory of my users.  I can enter and copy my other users' home directories, but my own directory is off-limits.  if i try to copy it, it tells me that the directory is read only.  if i try to enter it, it simple says it cannot.

I've tried booting into liveCD versions of linux (knoppix and ubuntu) and can't seem to find these locations at all.  it's almost as if the only place I can even look at it is in this initramfs place, which isn't helpful at all.

I ran a boot script i found on sourceforge that supposedly helps diagnose problems in booting, and i'm not sure if there are any problems with booting seeing as it all flashes too fast for me to see before i'm staring at the initramfs prompt.  if anyone can help me get into my home directory to copy out the files in it (assuming that's even possible) i'd really appreciate it.  there's so much stuff saved in there...

I'm not having much luck in googling this particular issue, as any place I got kinda sounds like my issue, but then branches off into something else that's way too specific to be my issue.

---

### Post by Buntumatic on 2012-01-15
First, fsck really shouldn't mess up anything that is not FUBAR.
Second, best option to recover is to restore from backup.
Third, do we have to suspect a failing hard drive here? You did not provide any clues why you had to run fsck in first place.
Fourth, when booting from some rescue CD or USB stick first run ```
fdisk -l
```to see if your hard drive is recognized, then ```
mount
```to see if your hard drive partitions are already mounted somewhere, if not (or mounted readonly, umount in that case) run fsck on them again.

---

### Post by Hylianux on 2012-01-15
Thank you for your reply.

restore from backup?  let me put it this way: this experience has taught me just how important backups would be to have...  on top of trying stuff on a test server first before deploying to a live one.  long story short: i did not make backups.  absolutely horrendous, isn't it?  soon as this is fixed, you'd better believe there'll be some .sh files designed specifically for backing stuff up.

why did i run fsck in the first place... here's the "cool story, bro, tl;dr" version:
=========================================================
i was trying to locate a mounted usb drive.  i'd had absolutely no problems mounting it in the past, then suddenly i just couldn't see any files on it anymore.  i tried running fsck without specifying which drive, which made it list all, and in my haste and impatience, i just told it to check 'em all.  one big problem with that is that it prompted me left and right for "do you want to fix this?"  i wasn't even familiar with this command, so i didn't know to run it with fsck -y.  since i'd already started answering questions that for some reason disabled all connections to the server except the putty terminal i was connected to it with.  I knew if i terminated that, i'd never get back in, so my only other course of action was to do something even dumber: keep the 'Y' key held down overnight.  this successfully got through the questions... i think... but the problem is the putty terminal was stuck trying to print out backlogged 'Y's after i stopped it.  this got me nowhere, so i again lost my patience with it (this seems to be a recurring issue with me... perhaps i should drink some soothing tea and put some cool ambience music on in the future when i troubleshoot things...)  after a restart, here i am at the initramfs prompt.  
=========================================================



anyway, on to the results of an fdisk -l:

i see my main hard disk with 3 partitions... (sda1) one for boot (which in my limited linux knowledge is the partition that holds all the information the pc needs to boot and run linux from... correct?), and 2 with lots of space (sda2, sda5).

a mount command prints a lot of data on what is mounted, but nothing pertaining to /dev/sda2 or /dev/sda5

i've tried running fsck on both those partitions, here are the results:

```

fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

``````

fsck from util-linux 2.19.1
fsck: fsck.LVM2_member: not_found
fsck: Error 2 while executing fsck.LVM_2member for /dev/sda5

```If you need any more information, please let me know.  I thank you for taking the time to fix an error by an impatient noob such as myself... lessons learned.

---

### Post by Hylianux on 2012-01-16
I'm looking at GParted now... i think I at least see the issue with why fsck is returning what it does... it shows both of those partitions as completely unused.  why is it that initramfs can see inside the hard drive and see my home directory (though not be able to really interface with it) but no other avenue (especially ones with more powerful commands) can?  am i royally screwed out of this one?

---

### Post by Hylianux on 2012-01-16
is there another tool i could use specifically designed for retrieving data from a hard drive?  maybe another distro or something?  i've looked around and tried a few, but they're either too confusing or can't find what i'm looking for.

perhaps something as smart as initramfs is at searching my hard drive?

---

### Post by Buntumatic on 2012-01-16
Did you use LVM?

---

### Post by Hylianux on 2012-01-16
not consciously.  sda5 looks to me like it's a lvm drive, but i didn't specifically tell ubuntu to make it so when i installed it, unless that happens automatically when you tell it to "erase and use entire drive."

---

### Post by Hylianux on 2012-01-18
i'm gonna try one more thing...  i'll see what happens when i slave the drive in windows.  doubt this will work, but i'm out of ideas.  after a couple days, i think i'm beginning to finally accept the death of my website and game worlds.  are there any other last-ditch effort things I can try?

---

### Post by Hylianux on 2012-01-18
is it possible to somehow use root priveleges in the initramfs prompt?  that's the only hangup i'm having.  if i could just sudo cp homeDirectory, i think it might work.  it yells at me currently about it being readonly when i do that, but i don't see how something being readonly has anything to do with me being able to copy it.  i'm not modifying it, so why can't i copy it?

it's like a patient in a vegetative state.  if i could just get his organs out, i could put him in another living host to live on.

---

### Post by Hylianux on 2012-01-18
Hmmm... this is interesting.  I tried running in "recovery mode" and saw some more output.  it apparently tries to mount the filesystem as ext4, then fails.

I'm pretty sure I remember the partition being created as ext4, rather than lvm.  Now I'm wondering how in the hell my other partition became known as lvm...

anyway, I tried running the fsck command, and it does nothing at all.  can't mount it as anything either, since the mount command does not recognize a lvm filesystem.  i'll try loading this in knoppix and see if there's a difference.

---

### Post by arrrghhh on 2012-01-18
LVM sits "on top" of ext4 if you will.  AFAIK it'll sit "on top" of any file system.

Don't even bother with Windows, it doesn't read Linux partitions.  Boot an Ubuntu live CD, or Knoppix like you said.  Make sure you an at least mount the disks.

---

### Post by Hylianux on 2012-01-26
sorry i haven't been able to get back sooner.  crazy week at work.  haven't had much time to mess with this.

my attempts at "mounting" fall pretty short, because as stated before, the mount command doesn't recognize a fs type of "LVM". So, I did some searching.  I found a couple tutorials on LVM mounting, ran through all the steps, and in the end it says "special device [devicename] does not exist."

I found [this post]("http://pissedoffadmins.com/?p=481") useful (don't worry, it's a quick tutorial... for anyone else who's lost), and i might wanna add that i knew i'd successfully mount the thing just from the website name.  it was just written in the stars... (or in this case, the url).

in the end, success!  i was finally able to mount the drive!

now to browse the drive and get to my home directory so i can copy things out of it.

i'm successfully able to browse to the /home/ directory and i see the home directories of my other users, but mine is in green letters...  what the hell?  ok, maybe it's just special (of course it is... it's my home directory... it's very special to me...).

enough humor, on with the story:

```
cd hylianux
```

drumroll...

```
bash: cd: hylianux: Not a directory
```

huwhaaaaaaa?!

my this looks familiar.  looks exactly the same as it does in initramfs.  i tried chmod, among other things...  no avail.  ok, so if it's not a directory, what the heck is it?

```
file hylianux
>>hylianux: data
```

oh.  it's a "data" file.  not really helpful.  and... this is where i go "now what?"  does anyone have a clue of where to go from here?

Thank you for your replies thus far.  :)

---

### Post by varunendra on 2012-01-27
**DISCLAIMER:** [I]I have absolutely no idea about your problem, its causes or a solution. It's just an experience I thought could be worth sharing.
[/I]
Once I was messing with permissions on some experimental directories (viewed/changed them in GUI, then again via terminal). While doing this, I somehow managed to make them appear as files (same 'green' in terminal, and 'unknown' files in GUI). Since I had no idea how to change it back, I just tried **chmod 777** on the directories (don't remember if it was recursive or not). And they were back to directories....! Oh, and I figured I could do it any number of times.... (mess it up > use chmod 777 > fixed!).

Wanna try! ;)

---

### Post by Hylianux on 2012-01-27
Funny you should mention that... thats the first thing i tried!  Lol.  It didnt do anything... although i did it differently
```
chmod -R 777 hylianux
```

It didnt change anything.  :(

---

### Post by arrrghhh on 2012-01-27
> **Hylianux said:**
> Funny you should mention that... thats the first thing i tried!  Lol.  It didnt do anything... although i did it differently
```
chmod -R 777 hylianux
```

It didnt change anything.  :(

You posted all these things, but not ```
ls -l /home
```?  

(Or wherever it's mounted live...)

If it's green, it sounds like a file... not a directory.

Edit - do you have your home directory encrypted...?

---

### Post by Hylianux on 2012-01-27
It certainly seems to be treating the directory like a file...

I dont think i had it encrypted... is there any way to check?

I cant post the exact results of a ls- l at this time since i'm at work, but the results are pretty much this: the hylianux directory has full access for anyone or anything.

---

### Post by arrrghhh on 2012-01-27
> **Hylianux said:**
> It certainly seems to be treating the directory like a file...

ls -l would tell us what it is....

> **Hylianux said:**
> I dont think i had it encrypted... is there any way to check?

```
mount | grep ecryptfs
```

But that would only work if you were logged into it...

Based on [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

It seems like you should have a .encryptfs in /home...

How do you NOT know if your /home is encrypted?  I'm no expert on encryption...

Edit - this seems to be the ticket -

[http://askubuntu.com/questions/53242/check-if-partition-is-encrypted](http://askubuntu.com/questions/53242/check-if-partition-is-encrypted)

---

### Post by Hylianux on 2012-01-27
I dont belive i encrypted it.  This is my second foray into ubuntu server.  The first time i encrypted it (just to see what would happen).  I remember i had some trouble with it after that, but i cant really remember where since i abandoned it and installed the server on another machine without encryption.  However, i have no idea what fsck might have done to the drive in all its attemtps to "fix" stuff.  Not knowing much about the command, im guessing it doesnt, but im no expert.

Ill try all the things you mentioned when i get home tonight and let you know.

Again, i appreciate your time.

---

### Post by arrrghhh on 2012-01-27
> **Hylianux said:**
> I dont belive i encrypted it.  This is my second foray into ubuntu server.  The first time i encrypted it (just to see what would happen).  I remember i had some trouble with it after that, but i cant really remember where since i abandoned it and installed the server on another machine without encryption.  However, i have no idea what fsck might have done to the drive in all its attemtps to "fix" stuff.  Not knowing much about the command, im guessing it doesnt, but im no expert.

Ill try all the things you mentioned when i get home tonight and let you know.

Again, i appreciate your time.

fsck in of itself is harmless... however, if you have a dead/dying disk, fsck could put the final nail in the coffin.

It certainly wouldn't magically encrypt your disk on the fly :p.

No worries, take your time.

---

### Post by Hylianux on 2012-01-27
```

ls -l
>>-rwxrwxrwx 1 1003 1003 3493888 2011-11-01 00:02 hylianux
>>drwxr-xr-x 4 1002 1002    4096 2011-10-19 20:15 user1
>>drwxr-xr-x 2 1001 1001    4096 2011-05-19 22:54 user2
```

ls -a did not reveal a .encryptfs in /home, nor did mount | grep encryptfs, so i'm pretty sure my directory isn't encrypted.

---

### Post by arrrghhh on 2012-01-27
> **Hylianux said:**
> ```

ls -l
>>-rwxrwxrwx 1 1003 1003 3493888 2011-11-01 00:02 hylianux
>>drwxr-xr-x 4 1002 1002    4096 2011-10-19 20:15 user1
>>drwxr-xr-x 2 1001 1001    4096 2011-05-19 22:54 user2
```

ls -a did not reveal a .encryptfs in /home, nor did mount | grep encryptfs, so i'm pretty sure my directory isn't encrypted.

Huh, okie.  Well, based on that ls -l output, 'hylianux' is a ~3mb file - not a directory.  Not sure what else to tell you at this point...

---

### Post by varunendra on 2012-01-27
> **arrrghhh said:**
> Not sure what else to tell you at this point...
Maybe testdisk/photorec? Maybe it could find and recover the  directory if it ever existed on that partition!

I was also wondering if loop-mounting can be tried on that 'file' (even though it is detected as a 'data' file)!

---

### Post by Hylianux on 2012-01-29
I have no idea what any of that is lol.  I'll google it and try 'em out and let you know the results.

---

### Post by Hylianux on 2012-02-10
Photorec is the most awesome program ever.

I was able to recover all but 5 of my files for my website of articles  (4 of which i can just rewrite better than they were before).

I was even able to recover my minecraft worlds I was hosting.  

I've learned a valuable lesson here about backups... 

Thank you for all your help in getting my files out of that bad drive.

---

### Post by varunendra on 2012-02-11
> **Hylianux said:**
> I was able to recover all but 5 of my files for my website of articles  (4 of which i can just rewrite better than they were before).
Awesome!

Good to hear yet another success story with testdisk/photorec. I think with a nice GUI and a few more functionalities, like the option to select and recover individual files, with their original names if possible, this program can beat even most of the expensive commercial software out there- both in terms of capabilities and popularity.

Thanks for the feedback!

---

