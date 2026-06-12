---
title: "Writing udev Rules"
date: 2009-10-13
forum: Tutorials
---

### Post by Penguin Guy on 2009-10-13
[COLOR="Red"]**Problem:** Looks like the drive is mounted *after* the script has finished. If anyone knows a fix for this, please post a message here.[/COLOR]

**Detect the USB**
Firstly you'll need to set up a system to detect when your USB drive is plugged in, and run a script when it is. We will use udev to achieve this.

Create the file [COLOR="Green"]/etc/udev/rules.d/91-local.rules[/COLOR] and copy this into it: 
```
SUBSYSTEMS=="usb", KERNEL=="sd??", ACTION=="add", RUN+="/usr/local/bin/USB %k"

```
This will run a script located at [COLOR="Green"]/usr/local/bin/USB[/COLOR] and pass it [COLOR="Green"]%k[/COLOR] (the kernel name for the device detected).


Now we'll need to test that this works - create a script at [COLOR="Green"]/usr/local/bin/USB[/COLOR] and copy this into it:
```

#!/bin/bash
echo 'Hello World!' >>"/home/*<username>*/Desktop/udev.out"
exit

```
(obviously replacing *<username>* with your username)
Now add the execute bit ([COLOR="Green"]sudo chmod +x /usr/local/bin/USB[/COLOR]), and finally test that everything works by plugging in a USB drive. If everything does work you should see a file called [COLOR="Green"]udev.out[/COLOR] appear on your desktop, upon opening it you should see that it contains the text 'Hello World!' [COLOR="Red"]Do not continue until this part of the system works.[/COLOR]


**Find Your USB Identifier**
We will need a way to identify your USB so that we can treat it differently to other USBs. If you do not plan to give your USB any special treatment, feel free to skip to the next section.
We will use the disk identifier to identify your USB, you can find this by plugging in your USB and running [COLOR="Green"]sudo fdisk -l[/COLOR] - if you're not sure which one in the list is yours then look at the amount of GBs and the number of partitions each disk has.


**Create the Backup Script**
Finally the actual backup script ([COLOR="Green"]/usr/local/bin/USB[/COLOR]), you can write your own in a language of your choice, or use mine, written in bash. If you use mine you'll have to change the variables at the top and [install rsync]("apt:rsync"). Here it is:

**[BASH]**
[PHP]
#!/bin/bash
exec &> /var/log/udev-USB

MY_DRIVE_UUID='????-????'  # My USB disk identifier
OUT='/home/bob/USB-Backup'  # Where the backups are stored
SIZE_LIMIT='1GB'  # Size gets rounded to nearest unit
USERNAME='bob'  # Username to chown the backup to

function error { echo "$@, aborting." >&2; exit 1; }

drive_kernel="${1}"
if [ -z "${drive_kernel}" ]; then error "Could not detect drive kernel"; fi
echo "drive_kernel=${drive_kernel}"

drive_uuid=$(blkid -c /dev/null -o value -s UUID /dev/${drive_kernel})
if [ -z "${drive_uuid}" ]; then error "Could not detect drive UUID"; fi
echo "drive_uuid=${drive_uuid}"
if [ "${drive_uuid}" != "${MY_DRIVE_UUID}" ]; then error "Not my drive"; fi  # Only backup my drive

drive_size=`df -B "${SIZE_LIMIT}" | grep "^/dev/${drive_kernel}" | awk '{print $3}'`
if [ -z "${drive_size}" ]; then error "Could not detect drive contents"; fi
echo "drive_size=${drive_kernel}"
if [ "${drive_size}" > 1 ]; then error "Drive contents too big"; fi

drive_mountpoint=`df | grep "^/dev/${drive_kernel}" | awk '{print $6}'`
if [ -z "${drive_mountpoint}" ]; then error "Could not detect drive mountpoint"; fi
echo "drive_mountpoint=${drive_mountpoint}"

if [ ! -d "${OUT}" ]; then mkdir -p "${OUT}"; fi  # If $OUT does not exist, then make it

if [ "${drive_uuid}" == "${MY_DRIVE_UUID}" ]
then
	rsync -ac "${drive_mountpoint}/"* "${OUT}/My USB/" &&\
	chown -R "${USERNAME}" "${OUT}/My USB/"
else
	rsync -ac "${drive_mountpoint}/"* "$OUT/${drive_uuid}/" &&\
	chown -R "${USERNAME}" "${OUT}/${drive_uuid}/"
fi

exit $?
[/PHP]


**P.S.**
If you have any trouble following this guide or want to offer a suggestion on how it could be improved, please just post here. If it helped you, add a few tags - it makes it easier for other people to find it that way.

See Also: [http://www.reactivated.net/writing_udev_rules.html]("Writing udev Rules").
Thanks to [flaconindy]("http://ubuntuforums.org/showthread.php?t=1290438&page=2#16").

---

### Post by bapoumba on 2009-11-05
Sorry it took so long for the tutorial to be approved. Thanks for you patience :)

---

### Post by Penguin Guy on 2009-11-06
> **bapoumba said:**
> Sorry it took so long for the tutorial to be approved. Thanks for you patience :)
Oops, after waiting a month I figured something must have gone wrong so I re-posted it  [here]("http://ubuntuforums.org/showthread.php?t=1281418"). Sorry.

Edit: Fixed, I got a mod to jail the duplicate.

---

### Post by francois.marot on 2009-11-15
Hi,

I am currently strugling with an udev rule that used to waork correctly under Jaunty (now I use Karmic).
It is quite similar to the ones above, but it is for me impossible to get the mount point of the USB device. It seems that my USB device is only mounted in its final mountpoint (/media/whatever) only AFTER my programm has finished executing.
So when I execute my programm, I can't retreive the mount point ! It does not exists ! If I wait x seconds, then try to obtain the mount point (by reading /etc/mtab or doint something like df | grep /dev/sdd1 | awk '{print $6}' ) I can't retreive it !
Does anybody is in the same situation as me ? Anybody knows a way to get the final mountpoint in a script and access it ?

---

### Post by Penguin Guy on 2009-11-16
@francois.marot

Have you tried waiting a second or two to give the system time to mount the device correctly? Try using [COLOR="Green"]sleep 1s[/COLOR] before you check the mountpoint - this worked for me.

---

### Post by francois.marot on 2009-11-16
That's the problem ! ;)
        Now (Karmic), the mtab or df command are only populated with the information AFTER my script is executed.
        This means that if I make my programm wait 5 seconds, then mtab and df contain the new info only after 5 seconds.
        If I wait 30seconds, it 's the same: for 30 seconds, if I type df on the command line or read mtab, the new info is not in it.
        So there is no way my programm can access the mount point.
        I must be missing something...
        The only solution I see is to create a cron job that will be run later (say 30s) and quit my script once the job is created in order to release UDEV, make it poppulate mtab. Than 30s later, I can read it. But this is kinda overkill !

---

### Post by Penguin Guy on 2009-11-17
@francois.marot

What directory is your script in, and what is it called? Things like this will have an effect on it's run-order which could mean it get's run before the mounter script. My script is in [COLOR="Green"]/etc/udev/rules.d/91-local.rules[/COLOR].

---

### Post by francois.marot on 2009-11-17
Hi Penguin Guy,

I knew the rule and named my script (that used to work on Jaunty...) something like 99-myScript.rules. It should be executed last. But something seem to wait for it to finish before the USB drive is mounted in /media/USBDriveName

---

### Post by Penguin Guy on 2009-11-17
@francois.marot

I would suggest starting with a simple 'Hello World!' program before moving on to add the more advanced features - have you tried something like:
```

#!/bin/sh
echo 'Hello World!' >>"/home/*<username>*/Desktop/udev.out"
exit

```
And if so, did it work?

---

### Post by francois.marot on 2009-11-18
I tried something like that and there was no problem... As I said, the problem is mtab and df command not containing the new mount point until my script has finished. But my script NEEDS this information ! Don't know what to do for the moment...

---

### Post by Penguin Guy on 2009-11-18
@francois.marot

Could I suggest following my guide and see if that works, if it does it's just a case of editing it to do what you want. If you don't want to do that it would be helpful if you posted your udev rule and your script here so that I can take a look at them. In the mean time I'm going to run some tests to see if my rule is actually working as expected.

Edit: Hey, looks like my rule is faulty too - the data I want doesn't seem to appear in the output of the df command until after the script has exited. I'll post back if I find a solution.

---

### Post by francois.marot on 2009-11-23
Hey Pengin Guy, I was about to try your suggestion when I saw your edit. You confirm my problem ?
I imagine that your solution used to work but doesn't work any more on Karmic, am I right ?

---

### Post by Penguin Guy on 2009-11-24
> **francois.marot said:**
> Hey Pengin Guy, I was about to try your suggestion when I saw your edit. You confirm my problem ?
I imagine that your solution used to work but doesn't work any more on Karmic, am I right ?
Yes, that's right. I'll put a note on the first post, but I'm not sure how to work around the problem.

---

### Post by bounty123 on 2009-11-29
Thank you, this howto was very useful!

---

### Post by francois.marot on 2010-01-02
Nobody still able to retreive the mountpoint by running a script launched from udev under Jaunty ?
I desperatly need help on this one !
Bounty123 are you on Karmic ? If yes did yyou upgrade with latest packages and could you provide your complete scripts if different than those given by Penguin Guy ?

---

### Post by falconindy on 2010-01-02
This rule works under Karmic. 

```
SUBSYSTEM=="usb", KERNEL=="sd??", ACTION=="add", PROGRAM="/usr/local/bin/USB %k"
```

Little did I realize there's a great man page on udev and writing rules. And of course, if you haven't seen it, [this](http://www.reactivated.net/writing_udev_rules.html) is just about the only other comprehensive resource available.

Also, might I suggest:

...a simpler way to get the UUID of a drive? If $1 is a device file, such as /dev/sda1, then:
```
blkid $1 | sed -n 's/.*UUID=\"\([0-9a-z\-]*\)\".*/\1/p'
```
Would return the UUID without worrying about parsing ls.

You can also have udev mount the drive for you rather than waiting for HAL to do it. I use the following rule to mount all my removable media (since I don't use HAL at all).
```
KERNEL!="sd[a-z][0-9]", GOTO="media_by_label_only_auto_mount_end"
ACTION=="add", PROGRAM!="/lib/initcpio/udev/vol_id --label %N", GOTO="media_by_label_only_auto_mount_end"
ACTION=="add", RUN+="/bin/mkdir -p /media/$env{ID_FS_LABEL}"

# Global mount options
ACTION=="add", ENV{mount_options}="relatime,users"
# Filesystem specific options
ACTION=="add", PROGRAM=="/lib/initcpio/udev/vol_id -t %N", RESULT=="vfat|ntfs", ENV{mount_options}="$env{mount_options},utf8,uid=1000,gid=1000,umask=002"

ACTION=="add", RUN+="/bin/mount -o $env{mount_options} /dev/%k /media/$env{ID_FS_LABEL}"
ACTION=="remove", ENV{ID_FS_LABEL}=="?*", RUN+="/bin/umount -l /media/$env{ID_FS_LABEL}", RUN+="/bin/rmdir /media/$env{ID_FS_LABEL}"
LABEL="media_by_label_only_auto_mount_end"
```
Mind you, Ubuntu no longer carries vol_id by default.

---

### Post by Penguin Guy on 2010-01-03
@ falconindy

Thanks for your help, when I said that it doesn't work under Karmic, I meant the script - it appears that Ubuntu now waits for udev to finish before starting HAL. Your script is to complicated for me, but hopefully someone else will find it helpful. Thanks.

---

### Post by francois.marot on 2010-02-06
Well falconindy, thanks too for the script but it was too much complicated for me too ! ;)
I found another method which seems to work quite well for now: i made a script monitoring the mtab file and runnning a Groovy script (Groovy being a java based language) whenever a change is detected in order to get the mount point on which a change happened.

Here is my monitorMtab.sh script (make sure to install the inotifywait tool in order to use it):
```

MTAB=/etc/mtab
MTAB_BAK=/tmp/mtab
cd /path/to/current/directory

cp $MTAB $MTAB_BAK
while true
do
	inotifywait -e modify,close_write,create $MTAB
	echo "- - - - - - - - - - - - - USB change detected on `date` - - - - - - - - - - -"
	groovy analyzeMTab $MTAB_BAK $MTAB 
	cp $MTAB $MTAB_BAK 
done

```

Here's my analyzeMTab.groovy file that detects modified lines and path in mtab:
```

#!/usr/bin/env groovy

println "in analyzeMTab..."
// the groovy script to be run with new mount point as parameter
File mountPointAnalyzer = new File("mountPointAnalyzer.groovy")

if (args.length != 2) {
	println "Bad args number..." + args.length +". Exiting..."
	System.exit(-1)
}

String newFileName = args[1]
File oldFile = new File(args[0])
File newFile = new File(newFileName)

List oldLines = oldFile.readLines()
List newLines = newFile.readLines()

// Fill 'modifiedEntries' with new or modified entries in mtab
def modifiedEntries = []
newLines.each {
	try {
		if ( ! oldLines.contains(it) ) {
			modifiedEntries.add(getMountedPath(it))
		}
	} catch(Exception e) {println e}
}

modifiedEntries.each{
	println "In ${newFileName}, following mountpoint has changed and will be analyzed: "+it
	//run mountPointAnalyzer groovy script with the path to analyze as parameter
	new GroovyShell().run(mountPointAnalyzer, [it])
}

/** Return the mount path from a line in the mtab file*/
String getMountedPath(String mtabLine) {
	mtabLine.split(' ')[1]
}

```


... then my mountPointAnalyzer.groovy script runs and makes the operations I want according to the path given. For completeness, it is mostly retreiving photos from my various USB keys and sdcards and backuping them on my computer.

---

### Post by Chikitulfo on 2010-09-02
Hey, I know it's a bit late, but someone might find it useful.

I found an utterly easy workaround for the issue you are having here:
Since udev waits for the "RUN" program to finish before it continues, you can launch it background so that udev can continue.

To do it I just run the program/script from within bash. This is my udev rule. If everything else is working you should only worry about the RUN string.

```
SUBSYSTEM=="block", ATTR{size}=="15679488", ATTRS{serial}=="0019E02D40CF5A8A130308AB", RUN+="/bin/bash -c '/home/chikitulfo/bin/pruebackups &'"
```

The script I want to run is /home/chikitulfo/bin/pruebackups. I also make the script wait 10 seconds before it starts to do things in the fs, just to give udev time to finish.

---

### Post by francois.marot on 2010-09-02
Thanks Chikitulfo, this might be REALLY usefull :)
Just for the record, which version of Ubuntu are you running and are you up to date ?

---

### Post by Chikitulfo on 2010-09-02
Running Lucid 64 bits (profile info was outdated)

---

### Post by Penguin Guy on 2010-09-05
Sorry people, but I've given up on this how-to and udev in general. I can't even get the 'Hello World!' test to work anymore.

---

### Post by TheTank on 2010-09-09
Thanks for the guide. Really cool.
I am now able to have my ext drive automatically start xmms2d (using xmms2-launcher fyi).

Only problem I could see was this line:
```

drive_uuid=`drive_uuid=`blkid -c /dev/null -o value -s UUID /dev/${drive_kernel}``

```
Issnt the double assignment kinda redundant? IIRC it also threw an error on my system.

---

### Post by Penguin Guy on 2010-09-09
> **TheTank said:**
> Thanks for the guide. Really cool.
I am now able to have my ext drive automatically start xmms2d (using xmms2-launcher fyi).

Only problem I could see was this line:
```

drive_uuid=`drive_uuid=`blkid -c /dev/null -o value -s UUID /dev/${drive_kernel}``

```
Issnt the double assignment kinda redundant? IIRC it also threw an error on my system.
Glad the guide was helpful, thanks for reporting that problem - yes, I think it is indeed majorly erroneous so I've changed it to:
```
drive_uuid=$(`blkid -c /dev/null -o value -s UUID /dev/${drive_kernel})
```

---

### Post by TheTank on 2010-09-10
Small correction: I thought it was starting xmms2d, but that is not the case. But that seems to be more of an issue with launching stuff from the script then with the udev rules.

Again, thanks!

---

### Post by ThQuincey on 2012-11-05
I have a question related with this thread. I´m new with linus, so I hope that you can help me and I apologize if my question is stupid or here is not the right place to do it

I'm writing a new udev for the usb devices. I will only that one in Qt developed program started when the usb is connected.

I write the USB script and the 91-local.rules and it worked. 

When I modify my USB file to exec my program:

$/opt/program/# ./SH_Update

 My program works, but I get the next warning:

(process:4022): GConf-WARNING**: Client failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply time out expired, or the network connection was broken.

When I connect the USB stick, the program SH_Update doesn't work.

Have you any Ideas??

Best

---

### Post by Smika on 2013-04-23
I have the problem that it will first start the script and after finishing the script it will mount my device. When I use SUBSYSTEM==&#8221;block&#8221;, my device is mounting perfectly, but my script will never start. How can I solve this?

Smika

---

