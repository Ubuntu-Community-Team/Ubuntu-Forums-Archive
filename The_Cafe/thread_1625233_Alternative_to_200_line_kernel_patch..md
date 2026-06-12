---
title: "Alternative to 200 line kernel patch."
date: 2010-11-18
forum: The Cafe
---

### Post by mooreted on 2010-11-18
"Lennart Poettering, a RedHat developer replied to Linus Torvalds on a maling list with an alternative to this patch that does the same thing yet all you have to do is run 2 commands and paste 4 lines in your ~/.bashrc file. I know it sounds unbelievable, but apparently someone even ran some tests which prove that Lennart's solution works. Read on!"

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by Gremlinzzz on 2010-11-18
(important: this won't work on Ubuntu.
Think ill wait for the patch.

---

### Post by Decatf on 2010-11-18
> **Gremlinzzz said:**
> (important: this won't work on Ubuntu.
Think ill wait for the patch.

and what are you basing this on?

---

### Post by Gremlinzzz on 2010-11-18
> **Decatf said:**
> and what are you basing this on?

Phoronix recently published an article regarding a ~200 lines Linux Kernel patch that improves responsiveness under system strain. Well, Lennart Poettering, a RedHat developer replied to Linus Torvalds on a maling list with an alternative to this patch that does the same thing yet all you have to do is run 2 commands and paste 4 lines in your ~/.bashrc file. I know it sounds unbelievable, but apparently someone even ran some tests which prove that Lennart's solution works. Read on!

Basically, Lennart explains you have to add this to your ~/.bashrc file (important: this won't work on Ubuntu. See instructions for Ubuntu further down the post!):
on this.
Update 2: 64bit kernels (Warning: use these at your own risk!!!) for Ubuntu 10.10:

---

### Post by simpleblue on 2010-11-18
Linus Torvalds reply to this:

> On Tue, Nov 16, 2010 at 10:16 AM, Lennart Poettering
<mzxreary@0pointer.de> wrote:
>
> Here's my super-complex patch btw, to achieve exactly the same thing
> from userspace without involving any kernel or systemd patching and
> kernel-side logic. Simply edit your own ~/.bashrc and add this to the end:

Right. And that's basically how this "patch" was actually tested
originally - by doing this by hand, without actually having a patch in
hand. I told people: this seems to work really well. Mike made it work
automatically.

Because it's something we want to do it for all users, and for all
shells, and make sure it gets done automatically. Including for users
that have old distributions etc, and make it easy to do in one place.
And then you do it for all the other heuristics we can see easily in
the kernel. And then you do it magically without users even having to
_notice_.

Suddenly it doesn't seem that wonderful any more to play with bashrc, does it?

That's the point. We can push out the kernel change, and everything
will "just work". We can make that feature we already have in the
kernel actually be _useful_.

User-level configuration for something that should just work is
annoying. We can do better.

Put another way: if we find a better way to do something, we should
_not_ say "well, if users want it, they can do this <technical thing
here>". If it really is a better way to do something, we should just
do it. Requiring user setup is _not_ a feature.

Now, I'm not saying that we shouldn't allow users to use cgroups. Of
course they can do things manually too. But we shouldn't require users
to do silly things that we can more easily do ourselves.

If the choice is between telling everybody "you should do this", and
"we should just do this for you", I'll take the second one every time.
We know it should be done. Why should we then tell somebody else to do
it for us?

                         Linus

Courtesy of [http://lkml.org/lkml/2010/11/16/351](http://lkml.org/lkml/2010/11/16/351).

In any event, I'll be trying Lennart's way until the new kernel comes out.

---

### Post by Gremlinzzz on 2010-11-18
In any event, I'll be trying Lennart's way until the new kernel comes out.
isn't it out
If you want to go even further and install a patched Kernel, you can download a "200 lines" patched Kernel from HERE (thanks to accumulator @ Phoronix forums).
[http://www.outrightsolutions.nl/~sander/ubuntu/kernel/](http://www.outrightsolutions.nl/~sander/ubuntu/kernel/)
its from mooreted link same as the warning

---

### Post by mooreted on 2010-11-18
I figure it's worth a shot, just for the fun of it. :)

---

### Post by Gremlinzzz on 2010-11-18
You figured right, I hope they report back if it works.

---

### Post by cariboo on 2010-11-18
I use it on my netbook running Unity 10.10, it doesn't make a great huge difference, but it does feel faster.

---

### Post by libssd on 2010-11-18
> **Gremlinzzz said:**
> (important: this won't work on Ubuntu.
Think ill wait for the patch.
Not so; it **does** work for Ubuntu, just requires slightly different syntax. See this thread: [http://ubuntuforums.org/showthread.php?p=10134058](http://ubuntuforums.org/showthread.php?p=10134058)

I just applied it to an Acer netbook running 10.04LTS, and performance **seems** to be improved as described; no unexpected side effects observed. (But I **DID** make a full backup before applying the changes.)

---

### Post by Rave Gloves on 2010-11-19
i just tried this just now on ubuntu 10.10 on my laptop, Im certain i have done it right, i don't think there is really anything different, ubuntu booted super quick though, im unsure if that's what the patch can do mind you. I have yet to try some HD video to see how it goes. Maybe i have actually done it wrong and im experiencing a placebo :P

---

### Post by Decatf on 2010-11-19
It works and there is a simple way to check and test it.

> Whether you are running a patched kernel or [Lennart Poettering&#8217;s userspace implementation]("http://lkml.org/lkml/2010/11/16/392")  there is a simple way to demonstrate how and where exactly this patch  useful on a system. All that is required is a 1080p video (or any video  that will put your CPU to work decoding it.) and Pitivi with a  multithreaded video encoder installed on your system (e.g. x264 or VP8 ).  Here&#8217;s what I did under Ubuntu 10.10:

First we will demonstrate your system under normal desktop use.
 
[LIST]
[*]Get the patch installed on your system (either through patched kernel or userspace)
[*]Fire up Pitivi (Applications>Sound & Video>Pitivi)
[*]Import a video to be encoded. Drag the clip into the timeline
[*]Click on Render project. Click modify and select the WebM container.  Set the output resolution to 1080p full HD. Under Video Codec settings  set the number of threads to 64.
[*]Start rendering the video
[*]Now start playing a 1080p video (VLC/mplayer it doesn&#8217;t matter)
[*]Watch the playback suffer as Pitivi is eating up all the CPU time
[/LIST]
 Second we will see how the patch can be useful
 
[LIST]
[*]Re run the steps above but this time run Pitivi from a terminal
[*]The video playback should be much better than previously if the patch is working
[/LIST]
 There is the argument that nobody that knows anything about something  will run a 64 thread encoding operation. You can also test this with a  realistic case by using the same number of threads as cores. I&#8217;ve tested  this as well and noticed that the video playback still suffered under  the normal (first case) above and showed improvement in the second case.
 

       [Ref]("http://decatf.wordpress.com/2010/11/19/the-200-line-kernel-patch-is-it-working-for-me/")

---

### Post by gnuskool on 2010-11-19
[QUOTE

Basically, Lennart explains you have to add this to your ~/.bashrc file (important: this won't work on Ubuntu. See instructions for Ubuntu further down the post!):
[/QUOTE]

You said so yourself, so...did you see the instructions for ubuntu further down the post?

---

### Post by Gremlinzzz on 2010-11-19
> **gnuskool said:**
> [QUOTE

Basically, Lennart explains you have to add this to your ~/.bashrc file (important: this won't work on Ubuntu. See instructions for Ubuntu further down the post!):


You said so yourself, so...did you see the instructions for ubuntu further down the post?[/QUOTE]

I did and this part made my decision to wait and see.
Update 2: 64bit kernels (Warning: use these at your own risk!!!) for Ubuntu 10.10:

---

### Post by NightwishFan on 2010-11-19
What I have always done was:
```
nice make -j64
```

This starts the process and any child process at nice 10, which keeps it out of my hair. I also use alt+f2 and launch anything I do not interact with using nice. I think I am correct in saying nice 20 sets the process to batch scheduling?

---

### Post by dakota34 on 2010-11-20
nautilus no longer slows my admittedly aging system to a crawl after using the command line instructions to perform the 'equivalent' of the kernel patch. Previously, anytime I copied over large files from my desktop to our NAS the desktop became so slow it was basically unusable until the coyping was finished (Athlon single core 2800, 1 GB ram) I've previously tried many things to solve this, none ever worked. After completing the command line changes and rebooting I now copy files while continuing to work normally on my desktop.

---

### Post by smellyman on 2010-11-20
I must admit.  My system seems nimble now.

---

### Post by forrestcupp on 2010-11-20
> **simpleblue said:**
> Linus Torvalds reply to this:


I don't think that Linus understands that some people would rather do a quick & easy thing manually than to wait a year for Ubuntu (or whoever) to finally get around to including a patched kernel.

Sure, it's better to fix it automatically in the kernel.  This technique isn't for everyone, just the impatient.

---

### Post by Decatf on 2010-11-20
> **forrestcupp said:**
> I don't think that Linus understands that  some people would rather do a quick & easy thing manually than to  wait a year for Ubuntu (or whoever) to finally get around to including a  patched kernel.

Sure, it's better to fix it automatically in the kernel.  This technique isn't for everyone, just the impatient.


Anyone that understands this patch and knows what it's actually useful for should know how to compile the kernel.

By the time this makes it into any distro releases the work on it will be in a state which it will actually benefit average desktop user. There is really no reason to rush and cram this into current systems because some website decided to blow things out of proportion.

---

### Post by Gremlinzzz on 2010-11-20
Its done! thanks mooreted

---

### Post by opodaniel on 2010-11-20
Ubuntu implementation of the alternative
[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)
 > To use Lennart's solution in Ubuntu (not tested - thanks to Lsh for this), you have to replace "/sys/fs" with "/dev". So you would have to add the following commands in your /etc/rc.local (open it with: sudo gedit /etc/rc.local) file, above the "exit 0" line:

mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

and make it executable:
sudo chmod +x /etc/rc.local

And then add the following to your ~/.bashrc file (to open it: gedit ~/.bashrc):

if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

Run the following command:
sudo gedit /usr/local/sbin/cgroup_clean

And paste this:

#!/bin/sh
rmdir /dev/cgroup/cpu/$*

then save the file and make it executable:
sudo chmod +x /usr/local/sbin/cgroup_clean

And finally, restart the computer or manually run the /etc/rc.local file ("sudo /etc/rc.local").
 
Since I am beginner I don't know if the alternative is working or not. I see that in /dev/cgroup/cpu/user/ new folders are created but all the files inside are 0kb . 
Can someone post a step by step guide for beginners and how to test if the solution is working or not.

Found also this script that install the alternative. It is the first option "Acceleration..."
> Bleeding Edge is a shell script designed for Ubuntu 32 bit. It installs repositories, keys, and software - such as media players, codecs, MS fonts, drivers, etc. It also cleans up the system. VIEW SCREENSHOTS FOR USAGE INSTRUCTIONS
[http://sourceforge.net/projects/bleedingedge/](http://sourceforge.net/projects/bleedingedge/)

---

### Post by handy on 2010-11-21
I've been using this method for a couple of days & haven't really noticed any difference in speed:

[http://lkml.org/lkml/2010/11/16/413](http://lkml.org/lkml/2010/11/16/413)

It is working, the folders per/PID are being created & they have the appropriate content.

When I get around to using HandBrakeCLI again I may possibly notice a change (dual core CPU), maybe?

---

### Post by libssd on 2010-11-21
For reasons unrelated to this patch, I had the "opportunity" to restore from a backup that I made immediately before applying Lennart's code. This gave me a chance to do some A/B comparisons. 

In day-to-day usage, one of the most dramatic changes is with scrolling. Before, using gedit, scrolling through a 20,000 line text file by holding down the PgDn key, the text would continue to scroll for a while after releasing the key. After, not only is scrolling noticeably faster, but text stops scrolling as soon as the key is released. Similar improvements appear to exist with browser page loads, and file copying.

Lennart's changes are very easy to apply (and back out), so I see no reason to wait for a new kernel to be released that incorporates this patch. When such is released, it's very easy to undo Lennart's changes, which should no longer be necessary.

---

### Post by Ichido on 2010-11-21
> **cariboo907 said:**
> I use it on my netbook running Unity 10.10, it doesn't make a great huge difference, but it does feel faster.

Can you define "Feel" please?
How does it "Feel faster"?
Thanks:)

---

### Post by forrestcupp on 2010-11-21
> **Decatf said:**
> Anyone that understands this patch and knows what it's actually useful for should know how to compile the kernel.

But I don't have to understand the patch and what it's useful for.  All I have to know is this thing are make my intarnit thingy work faster. ;)

That's all someone needs to know for them to want it working now.  We don't need to know how it's made, and the technical description of exactly what it's doing.

---

### Post by cariboo on 2010-11-21
> **Ichido said:**
> Can you define "Feel" please?
How does it "Feel faster"?
Thanks:)

Some programs start faster than before adding the work around, while other operations seem to run at he same speed as before, so it feels faster.

---

### Post by dentaku65 on 2010-11-22
Fine applied here on Lucid 32bit

My impression is that the machine is more faster.

The instructions for Ubuntu are here:
[http://pastebin.com/raw.php?i=sHRYRuAN](http://pastebin.com/raw.php?i=sHRYRuAN)

Discussion:
[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

The alternative discover:
[http://lkml.org/lkml/2010/11/16/413](http://lkml.org/lkml/2010/11/16/413)

The kernel patch story of 200:
[http://www.phoronix.com/scan.php?page=article&item=linux_2637_video](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video)

---

### Post by dcstar on 2010-11-23
> **dakota34 said:**
> nautilus no longer slows my admittedly aging system to a crawl after using the command line instructions to perform the 'equivalent' of the kernel patch. Previously, anytime I copied over large files from my desktop to our NAS the desktop became so slow it was basically unusable until the coyping was finished (Athlon single core 2800, 1 GB ram) I've previously tried many things to solve this, none ever worked. After completing the command line changes and rebooting I now copy files while continuing to work normally on my desktop.

Yep, I put it on a new 10.04 build that was woeful under heavy disk I/O and these changes fixed the problem:

[http://ubuntuforums.org/showthread.php?p=10151482](http://ubuntuforums.org/showthread.php?p=10151482)

---

### Post by handy on 2010-11-23
> **dcstar said:**
> Yep, I put it on a new 10.04 build that was woeful under heavy disk I/O and these changes fixed the problem:

[http://ubuntuforums.org/showthread.php?p=10151482](http://ubuntuforums.org/showthread.php?p=10151482)

I think that YouTube is a better, which is nice. I hadn't noticed that it was before 'cause I don't regularly use it.

I'm not using Ubuntu, that combined with all of the different hardware/system/software & overall usage variables sure makes for a lot of different results that people can experience from the use of the kernel patch or the quick fix alternative.

---

### Post by mengtze on 2010-11-23
I applied this alternative to two machines. 

On the dual core Pentium it made a dramatic change in responsiveness. MUCH better! 2.6.32-25-pae kernel

On a AMD Athlon Neo X2 system, no noticeable improvements. 2.6.32-25-generic kernel

Both systems run 10.04,

---

### Post by NightwishFan on 2010-11-23
I say numbers or it did not happen. :)

---

### Post by mengtze on 2010-11-23
> **NightwishFan said:**
> I say numbers or it did not happen. :)

lol.

On P system, start up of chrome is about halved, evolution starts in 4 seconds  vs 9. I have not seen any improvements in the virtual machines (3 xp machines), but their parallel start up has improved. No numbers as they start via startup scripts.

The AMD machine, again  no realistic improvement. No degradation either.

---

### Post by NightwishFan on 2010-11-23
Well thanks for the reply, though I did not mean you exactly, I just meant in general. As the one user has been saying I doubt much is changed, though cgroups themselves are very useful, I run my processes cgrouped by user, and things seem better. I am working on getting numbers myself. :)

Though to be honest it makes no sense that program loading time would be improved with this, but who am I to say, I merely glanced at the code.

---

### Post by dcstar on 2010-11-27
> **mengtze said:**
> lol.

On P system, start up of chrome is about halved, evolution starts in 4 seconds  vs 9. I have not seen any improvements in the virtual machines (3 xp machines), but their parallel start up has improved. No numbers as they start via startup scripts.

The AMD machine, again  no realistic improvement. No degradation either.

On my own AMD platform - which was running fine anyway - the patch made no difference.

On a new 10.04 install on a different Intel platform that was pathetic under heavy disk I/O until the patch was implemented, it now runs as good as a normal system (which has saved me some embarrassment after promising good performance with an Ubuntu install).

The Ubuntu forums have many people posting that they have systems that basically grind to a halt under high disk I/O, if this patch has the same positive effect on their systems as it did on the problem system I had then it should cure most of their issues.

---

### Post by afilonov on 2010-12-07
Is there a way to make it work on Hardy (8.04)? I tried it, cgroup mounts fine, but I'm getting an error in .bashrc:


mkdir -p -m 0700 /dev/cgroup/cpu/user/$$
mkdir: cannot create directory `/dev/cgroup/cpu/user/6832': Invalid argument

---

### Post by handy on 2010-12-08
> **afilonov said:**
> Is there a way to make it work on Hardy (8.04)? I tried it, cgroup mounts fine, but I'm getting an error in .bashrc:


mkdir -p -m 0700 /dev/cgroup/cpu/user/$$
mkdir: cannot create directory `/dev/cgroup/cpu/user/6832': Invalid argument

It won't work with that kernel. You will need to upgrade your kernel & associated packages, which you can do, but I'm not sure how you will go with system compatibility?

If you have a look at the "Ubuntu Stuff" section which is a ways down the first post in this thread you will get the how-to for upgrading the kernel & your other packages, though I'd be particularly scared about that doing that from Hardy.

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by libssd on 2010-12-08
In late 2010, I'm wondering why there are people out there who are still running releases as old as Hardy Heron. Lucid is a long term support release, and (other than the switch from grub to grub2) has been much more satisfactory for me than earlier releases of Ubuntu. Of course, I wouldn't think of upgrading to a new release without first making a restorable backup....

---

