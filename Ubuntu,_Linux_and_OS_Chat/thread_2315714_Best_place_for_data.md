---
title: "Best place for data?"
date: 2016-03-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Odyssey1942 on 2016-03-01
Am about to start upgrading my Ubuntu 12.04 installs (to Ubuntu Mate), and am trying to decide how to arrange my data (/home) most expeditiously.

My 12.04 OS is currently on a SSD, and /home is on a separate HDD. One thing I can remember is what a challenge and an ordeal it was to set up as it is now. Took me many hours (mostly because I have to start from scratch each time it is necessary.) The whole mounting sequence and related is really above my pay grade and I would prefer to simplify the process.

I could go back to using only HDD's (more stable than SSD's) and just have /home on a separate partition of the same HDD that the system is on. Backups would be simple by copying to an attached USB HDD.

The more I think about mount points, permissions, etc, needed in my present setup, the better that option sounds.

Any thoughts, alternatives, suggestions with simplification in mind will be most appreciated.

---

### Post by Bucky Ball on 2016-03-01
*Thread moved to **Ubuntu, Linux and OS Chat**.*

You are looking for ' ... thoughts, alternatives, suggestions with simplification in mind ...' rather than looking for technical support.  

The rule of thumb is to have the OS on the SSD and /home on the HDD. But in the end, what suits you best is the best.

I personally have several installs and let /home be inside / by default. I then delete the folders in /home and create symlinks to folders on a separate /data partition. That way, all installs access the same data and there is no redundancy or confusion.

Horses for course, but as I say, I'd put the data on a HDD. But that's me. Might not be ideal for you. Sure you'll get plenty of suggestions that work great for others. Might not be what you're looking for. 

(Incidentally, what gives you the impression that an SSD with no moving parts is less reliable than a HDD which has many more mechanical bits that can fail???)

---

### Post by Odyssey1942 on 2016-03-02
BuckyBall, my impression that SSD's are less reliable is informed by several posts and various articles that say SSD's have a finite life (XYZ read/writes) with abrupt termination. My impression may be a bit dated as it came about a couple of years ago and hasn't been updated. Over the last two decades, the only HDD failure I have had was (ironically) a backup drive. We are probably talking 40 or more HDD's over that period.

Still, my preference would be root on a SSD, data on a HDD, but at my level of expertise, maybe better stated, lack of expertise, setting up mount points and making all the minor tweaks that I seem to remember were needed, sets me trembling. I just don't have the experience to know how to do it (don't even know what symlinks are), and therefore it involves leaning on the community each time to fumble my way through it, and it never turns out to be simple. If it were simple, I would certainly do it that way. If you can point me to a tutorial that accomplishes this, I would be grateful.

---

### Post by howefield on 2016-03-02
In terms of the question posed in the thread title, it doesn't really matter where the data is, whether it is SSD or HDD it is the backup strategy that matters. The main reason for having /home on a separate drive/partition is mostly to facilitate easy reinstalls. Even that is debatable these days.

Symlinks are basically just shortcuts to files or folders..

```
ln -s /Data/Documents/ ~/
```

would put a folder in /home pointing to the Documents folder in /Data - (in the screenshot you can see a shortcut arrow on the folder icon indicating it is a symlinked folder).

If you want simplification, then install to decent sized hard drive (HDD). All you need is / and /swap. Then work out how to maintain a backup. If you need to reinstall in the future, as long as you do not mark / for formatting during the partitioning stage /home will be left intact.

12.04 is good for another year, time enough to find someone local who can help you through it, local computer club / linux user group maybe ?

---

### Post by oldfred on 2016-03-02
New SSD have lives similar to HDD. And either can fail at any time. Or good backups always required.

 [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

Separate /home should be easier to set up as you can do that during install. And if reinstalling you can then just include it during install using Something Else but DO NOT format it.
I also use separate data partition, but that requires creating partition, formatting partition as ext4, giving yourself ownership & permissions to use partition, mount partition by adding entry to fstab. If /home only during install all that is automatic. It is not really difficult but requires multiple steps to complete.

---

### Post by mikodo on 2016-03-02
Well, oldfred also lists his steps for using a "data" sub-directory with symbolic links to it also. I am going to link that to you as an option to follow, the one that I use. I used the guide to switch from a separate /home partition to not having one. Though, one could use it to set up a "data" sub-directory similarly if, one didn't have a separate /home partition, initially. I imagine this is what howefield and Bucky Ball are now using, too. After, I had set up the mnt/data/ sub-directory and symbolically linked to the folders within it from my /home, I make rsync backups of my /mnt/data/ sub-directory, to the backup partition to, keep it current. 

When it comes time for new installs, I install it with, "no" separate /home partition and actually  delete the folders in my new install's  /home that I have in my backup partition, (Documents, Music, Pictures and so on). Then, do the making of, ownership, permissions and mounting process again for a for a new mnt/data/ sub-directory as oldfred outlines and then sync the folders from my backup partition to the new /mnt/data/ sub-directory. Then, follow oldfred's instructions to make the new symbolic links to those folders from, the new install's /home.

 I use rsync to keep my backup partition in sync with my /mnt/data/ sub-directory (which has changes to it, as I use it) and for the movement of my "data". Then, repeat the process for each new install. But, one could use cp or mv or, which ever one prefers.

This process is nice for multi-boot installs of Linux as, one distro's /home partitions are not usually compatible with other distros or, for that matter, may not be compatible with different releases of the same distro. This process, allows one to keep the data sub-directory separate from all the installs' /homes and, to reuse it in each, through symbolic links.

As pointed out above, you have time to decide what you want to do and, to do some reading on how to do what you decide.

 So, here is "pure" oldfred. See post #4:

[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)


  Notes

I just read through that post of oldfred. A few things on that:

Instead of: **gksudo** gedit /etc/fstab 

Note. I understand that pkexec is now default in 16.04  as gksudo is now deprecated.So it would be: pkexec gedit /etc/fstab. 

For now, I now use **sudo -H** mousepad in 14.04.  Mousepad only because I use Xubuntu and the default text editor of Xfce is that.

On:   sudo chmod -R a+rwX /mnt/data

See Morbius1's posts #8 & #10 for more explanation: [URL="http://ubuntuforums.org/showthread.php?t=1795369"]http://ubuntuforums.org/showthread.php?t=1795369
[/URL]
I forgot, I use LABELS now too. See Morbius1's post #13 here: [http://ubuntuforums.org/showthread.php?t=1795369&page=2](http://ubuntuforums.org/showthread.php?t=1795369&page=2)

See the next post by oldfred on, his changing of his script for this. I don't know how to write scripts so, I have never really paid any attention to it.

  If one is using GPT now, one needs to reflect oldfred's guide to include, how to see the GUID's or, use the LABEL with the partition. Is that better Fred?

---

### Post by oldfred on 2016-03-02
Nice link, mikodo. :)

I have been posting that same link, but have not looked at it for ages. Did not realize it was back in 2011.
I now use nano to edit and ext4 for format.
sudo nano /etc/fstab

You do not use GUIDs with gpt (UEFI does), but still use UUIDs. I have been using gpt since about 2011, but link to old ext3 was on old mbr drive.

I install enough times that I got frustrated looking up details and typing same commands, so I scripted it. On same system UUID for data partition is always the same so script works well. But I just built new system and had to do major edits to script. Bash script was just removing sudo from list of history for commands I used.

---

### Post by DuckHook on 2016-03-03
> **Odyssey1942 said:**
> ...I just don't have the experience to know how to do it (don't even know what symlinks are)...From one old guy to another:

Contrary to the what the young 'uns say, the Linux learning curve is sometimes rather steep. But the results are worth it.

Here are my two bits.

The key to reaching a satisfying conclusion is to keep things as simple as possible. 

1. Make a simple install. This means everything including /home on the SSD, all on one partition.
2. Using the GUI tools like gparted, create your "data" partition on the HDD.
3. *Take your time* learning how to symlink files/directories from your /home directory onto the HDD "data" partition.
4. Also take your time learning which files to move/symlink and which not to.

The advantages to this strategy are that you will have a working system from the get go, without having to agonize about choices or procedures right off the bat. However, it is relatively simple to move and symlink files later, when and only when you are ready.

You'll find that it isn't that difficult to learn how to symlink, but practice with a few test files first to gain confidence. Then move/symlink the following directories:

~/Documents
~/Downloads
~/Music
~/Pictures
~/Videos
~/Templates

Do not move/link ~/Desktop. That way, if you multi-boot different OSes you can maintain individual desktops for each of them. Over time, you might also consider moving/linking your browser files, e-mail and other data, but that can wait until you are confident in your setup and have researched which files/directories belong to which apps.

---

### Post by Odyssey1942 on 2016-03-03
For two days now, I have been reading and reading, and I hope I am making some progress. As each of you weigh in, that gives me more to read about, think about and weigh up. And thanks so much for each of your very valuable posts.

DuckHook's post came at just the right time and helped clarify things for me.

One of these days, I hope to be able to spend ENOUGH time for some of what I have to periodically re-learn to sink in, but right now my main concern is to replace each of our 12.04 fallbacks with a more uptodate LTS version, and if possible simplify the process so as to expedite the "next times.". So time for some decisions to streamline this discussion:

--distro: have selected 14.04 Ubunutu Mate (which will be replaced in a few months by 16.04 after 16.04 has "seasoned" a bit, assuming of course that UM meets my expectations)

--will go with SSD for system 

--and a HDD for /home

That takes me to how best to accomplish the latter. The choice is symlink vs mounting /home (hope I am saying this correctly) on the HDD.

Symlink: Do I understand that I must create a new symlink for each new file or folder on my desktop? While it appears easy (as DuckHook's code shows), it seems to create a continuing need to add (and presumably subtract symlinks) as files and folders on the desktop change. I constantly add and delete files and folders depending on what I am working on.

Mounting: While it is a bit more complicated to set up, once mounting /home on the HDD is done, I don't have to think about it again until the next upgrade (and maybe it simplifies the ongoing backup process?)

FWIIW, there is almost no chance that i will be testing other distributions and using the data in my /home folder, so while symlink offers an advantage there, I just don't need it.

So I will just close this post now with this question. I haven't used symlinks and so want the benefit of your experience. Is there a clear advantage that you can see, that I haven't mentioned (or excluded as above) to one over the other?

There may be another question or two once I have become comfortable with my choice between the two, but want to take this a step at a time. Thanks again.

---

### Post by DuckHook on 2016-03-03
> **Odyssey1942 said:**
> Is there a clear advantage that you can see, that I haven't mentioned (or excluded as above) to one over the other?On the matter of desktop files, you are correct. If you are in the habit of leaving files on your desktop, then it makes no sense to symlink each of them. You may as well put /home on the HDD and then rely on backing up to safeguard your data.

Actually, you touch upon a very good point: there is little sense in going through the whole symlink exercise unless your objective is to segregate data so that it survives limitless upgrade cycles. The motivation for this is because experienced users usually don't want to inherit their /home directories on upgrades. This in turn is motivated by the fact that old config files (in /home) will sometimes crash new versions of the OS, or worse, make them behave erratically, which is even more difficult to diagnose. So, those of us who have experienced such problems prefer to install without inheriting anything (wiping out /home) and then just symlink our permanent data back into the new install. Since the directories that contain our permanent data are usually limited and easy to identify (I listed them in my last post), it just makes more sense to hold only this data in the HDD and leave /home on the SSD since we want to wipe /home clean with every version upgrade anyway.

Hope the above makes sense.

What's important to remember is that every use-case is different. If you prefer the simplicity of /home on its own partition or even on a separate HDD, then you should implement it that way because that's the best solution for your needs. In your case, conceptual simplicity trumps flexibility, and that's a good thing.

The flexibility of Linux is almost endless. It is important to note that if, at some future point, you want to move your data files to another partition because you grow to value the above flexibility, and because you become confident with symlinking, then it's easy enough to do at that time. You don't have to do so right now.

Given your current knowledge and your comfort level, I would say that you've made an excellent plan.

---

### Post by Bucky Ball on 2016-03-03
No symlinks for files, only the folders they are in. 

Let me break it down like this. You do a standard install with no external /home, the /home is in the / partition which is the default setup.

Inside /home you will have default folders like /Documents, /Video, /Music, etc. Delete all those folders (not Desktop and not hidden files and folders).

Recreate the folders you are wanting to use on another partition, even on another drive if you want, then you create symlinks to those folders in /home in /. 

For instance, you have create a /Documents folders in your /Data partition, so the path would be, say, /Data/Documents. Open a terminal and navigate to the folder where you want to create the symlink, then:

```
ln -s /Data/Documents Documents
```

That should work to create the symlink /Documents in / which links to /Data/Documents. Take a [look here]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html"). 

I think you could make a symlink to a file, but in your situation, not sure why you'd want to. Good luck.

---

### Post by howefield on 2016-03-04
> **Bucky Ball said:**
> ```
ln -s /Data/Documents Documents
```

That should work to create the symlink /Documents in / which links to /Data/Documents. Take a [look here]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html").

After a fresh install the command I use is.. (terminal opened in ~/home)

> rm -r Documents Downloads Music Pictures Videos && ln -s /Data/Documents/ /Data/Downloads/ /Data/Music/ /Data/Pictures/ /Data/Videos/ /Data/Data_Store/.kde ~/ && echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" | sudo tee -a /etc/fstab

which removes the original ~/home folders Documents, Downloads, Music, Pictures and Videos and recreates them with symlinks to identically named folders that reside on the HDD. There is an "extra" folder named /Data_Store/.kde which I use to store profiles and certain config files on the HDD to save a little wear on the SSD, also makes it easy to share between multiple installs, although that isn't a consideration for the OP.

The third command above adds a line to /etc/fstab designed to ease wear on the SSD. Not that I worry about the life of the disk, I agree with whoever said above that these days SSDs have, in general,  as much longevity as HDDs.

---

### Post by Bucky Ball on 2016-03-04
Now, I like that Howefield. Thanks for sharing. :)

---

### Post by Odyssey1942 on 2016-03-04
HoweField, thanks for the code. I have captured that for possible future use. The absolute simplicity of it makes it attractive. So before I move on to my code for mounting, I would like to confirm one point about symlink.

To restate, I am a Gnome 2 fan. I love the ability to lodge links on the top taskbar, have all my workspaces visible at all times in the right side of the bottom taskbar, and to have my folders/files that are currently in use/frequently accessed visible on the desktop. So key to me is that overall view. If I understand it, one would not create a symlink to a desktop, and given that the desktop is really the difference for GUI oriented users, I think I get why. Is that understanding (i.e., not symlinking to the desktop) correct?

Just as soon as that is confirmed, I intend to post my code for mounting for comment.

Thanks all.

Edit: Next step for me is code to mount /home on the HDD. Since it is code, is this the appropriate forum, or should I go to installation and upgrades? Since everyone involved in this post already understands where I am coming from, this forum seems logical to me, but thought I should ask.

---

### Post by howefield on 2016-03-04
> **Odyssey1942 said:**
> HoweField, thanks for the code. I have captured that for possible future use. The absolute simplicity of it makes it attractive.

You're welcome, a small point about the code.. a copy/paste fail means I added the start of the next command (that I would run). Won't do any harm, just changes the present working directory but I didn't mean to include :)

I have edited out "*&& cd /etc/xdg/autostart/*"of the post above.

---

### Post by v3.xx on 2016-03-04
> **howefield said:**
> which removes the original ~/home folders Documents, Downloads, Music, Pictures and Videos and recreates them with symlinks to identically named folders that reside on the HDD.

I started using this method last year and found that once I got use to it, I like it :)

---

