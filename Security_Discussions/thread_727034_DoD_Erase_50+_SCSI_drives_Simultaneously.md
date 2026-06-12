---
title: "DoD Erase 50+ SCSI drives Simultaneously ?"
date: 2008-03-17
forum: Security Discussions
---

### Post by JohnnyXmas on 2008-03-17
I have 4 Compaq StorageWorks SCSI Arrays connected to a Compaq Proliant DL580 G2 server using various SymBIOS Logic and Adaptec HBA's. Each array can hold and address up to 14 drives, and the server itself can hold another 12. The server is running a Win2K AS \ Ubuntu Gutsy Dual-Boot, and physically "sees" all drives that I install with no problems.

I need to be able to install drives in this unit, and perform a Full DoD (7-pass) erasure of these drives, without wiping the three drives the OS is on (RAID 5). I need to be able to do all the drives at once, rather than one at a time, for the sake of speed. I'm sure some kind of script can be put together, but that's where I personally come up short. I can't figure out how to rescan the SCSI buses, then use that information to run Wipe (or whatever) on the drives it finds.

I have been using Ubuntu for a few years now as a Desktop \ Laptop OS, so I am very familiar with it, along with the locations and functions of the major configuration files and such.

---

### Post by HermanAB on 2008-03-17
Here is some info on how you should do it and why what you want to do won't work:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

and here is the ultimate DOD certified bulk erase tool:
[http://www.hammersource.com/Brass_Hammers.html](http://www.hammersource.com/Brass_Hammers.html)

Cheers,

Herman

---

### Post by JohnnyXmas on 2008-03-19
Does anyone out there want to actually answer my question? I HAVE to do it this way per contractual agreements with the several major financial institutions who use us to remarket their IT equipment. 

Yes, these drives are resold to the public with YOUR credit card and other financial data "secure" erased from them. I suggest you write a letter. here's a hint: one of them is a MAJOR credit card \ load institution, and the other is one of "The Big Three."

I'm using Eban right now, but I'd really like to be able to do this without having to reboot the server the drivers are connected to. I can get this working on Solaris 10 just fine, but my Sun unit is severely lacking in its ability to physically hold a large amount of drives. Here's the script I'm using there; maybe someone can "convert" it to "linux-compatible" references:

#!/sbin/sh
BOOT=c1
#BOOT is the boot controller
LOG="tee -a wipelog.txt"
if [ -e wipelog.txt ]; then
echo Found old wipelog.txt, clearing log. | $LOG
rm -f wipelog.txt
touch wipelog.txt
fi
echo -n Standby while cleaning up device links... |$LOG
/usr/sbin/devfsadm -C -v | $LOG
echo OK |tee -a wipelog.txt
DISKS=`find /dev/rdsk -name \*d0s2 -exec basename {} \; |grep -v $BOOT`
# Did we actually find any disks? If not lets stop now.
if [ -z "$DISKS" ]; then
echo "Whoops! NO Disks Found (besides the boot disks)!" |$LOG
echo "Aborting." | $LOG
exit 1;
fi
echo "Found the following disks (minus boot array disks):" |$LOG
echo "$DISKS" | $LOG
echo -n "Do you wish to proceed with erasing these disks? (Y/N) " |$LOG
read continue
if ( [ "$continue" == "Y" ] || [ "$continue" == "y" ] ); then
echo "" | $LOG
echo `date` Proceeding to wipe all disks. | $LOG
for DISK in $DISKS
do
echo "-----------------------------------------------------------" | $LOG
echo Starting wipe of /dev/rdsk/$DISK at: `date` | $LOG
dd bs=128k if=/dev/urandom of=/dev/rdsk/$DISK 2>&1 |$LOG
echo Completed wipe at: `date` | $LOG
done
echo "============================================================" | $LOG
echo `date` All disks wiped. | $LOG
else
echo &#8220;User aborted.&#8221; | $LOG
exit
fi

---

### Post by HermanAB on 2008-03-19
Just boot off a Knoppix CD and all drives will end up listed on the desktop, then wipe them with 'dd'.  Don't mount them, just wipe them.

I'd make a simple script like this:
#! /bin/bash
dd if=/dev/zero of=/dev/sda &
dd if=/dev/zero of=/dev/sdb &
...
yadda yadda

The ampersand will push each process into the background, so they will all run in parallel.

If you are adventurous then you can try to do a loop, but a massive block copy is just as good - KISS.  See tldp.org for a Bash manual.

Since the erase machine doesn't need to have a HDD of its own - running off a CD, you can simply wipe all disks.  The ones that don't actually exist, will simply error out and the script will try the next one.  With something like this, there is no need for smarts, so keep it crude.

Cheers,

Herman

---

### Post by JohnnyXmas on 2008-03-19
Thanks! Taking the server down to boot off a CD is not an option here, as its also my DHCP \ TFTP \ PXE server for my lab, and I'm not the only one working in it. I AM the administrator, but I'd rather not inconvenience others, not to mention slow down \ stop other projects.

While your method is certainly valid, 

If you scan through the Solaris script, which is still executed in bash, but uses some non-Linux commands (devfsadm, etc), you can see the way i do it there is to mark which controller hosts the boot drives, then run a scan for hard drives on ALL controllers, and grep out the one that I marked as BOOT. It then takes that list, runs a DO loop for each drive listing in it. This is very similar to what you are stating, although more complex and the end results are the same.

I could very well use your method, and just not list the boot drives in the script, but I need to know how to re-scan the SCSI busses to find the new hotswap drives I've installed at the time. The other problem (and the whole reason I'm even asking this) is that I want to be able to do ALL drives at the same time, not one after another.   I have the SCSI bandwidth  (U320 with only 14 drivers per controller, and ALL U320 drives, and 100MHz PCI-X cards), but the only way I've been able to make that happen is opening individual terminal windows for each drive, and that is incredibly tedious when we're talking 500+ drives per week.

DBAN does a decent job ( [http://dban.sourceforge.net/](http://dban.sourceforge.net/) ), but again requires booting from independant media.

---

### Post by HermanAB on 2008-03-19
Seriously, I'll just make brute force script, excluding the system drives.  SCSI supports up to 14 devices per string so it is easy to see the pattern for the drive names and then just address all of them.  Commands for drives that don't exist, will error out and nothing will happen.

As I mentioned above, the '&' at the end of a command pushes it into the background so then everything will run at the same time.

---

### Post by Biochem on 2008-03-21
> **HermanAB said:**
> Just boot off a Knoppix CD and all drives will end up listed on the desktop, then wipe them with 'dd'.  Don't mount them, just wipe them.

I'd make a simple script like this:
#! /bin/bash
dd if=/dev/zero of=/dev/sda &
dd if=/dev/zero of=/dev/sdb &
...
yadda yadda

The ampersand will push each process into the background, so they will all run in parallel.

If you are adventurous then you can try to do a loop, but a massive block copy is just as good - KISS.  See tldp.org for a Bash manual.

Since the erase machine doesn't need to have a HDD of its own - running off a CD, you can simply wipe all disks.  The ones that don't actually exist, will simply error out and the script will try the next one.  With something like this, there is no need for smarts, so keep it crude.

Cheers,

Herman

I would use shred instead of dd

shred /dev/sda &

It uses Guntman secure eraser and would be way more secure than just a single pass with zeros. 

Wiping doesn't work with files on journaled filesystem but in this case your  overwirting the whole drive.

Beside, it doesn't need to be from a live cd. shred is installed in Ubuntu

---

### Post by HermanAB on 2008-03-21
Yup shred should work when run on the whole drive.  However, the only way to *really* erase a drive is by activating the erase utility that is embedded in the drive controller.  Unfortunately most people are unaware of it.

---

### Post by JohnnyXmas on 2008-03-24
I switched to using /dev/urandom as the if for dd instead of zero. I understand that Guttman is way more secure, but urandom seems to be faster. Our agreement with the vendors only requires us to write 7 passes of "random data." so the algorithm doesn't really matter (Yeah, their CIO's signed off on this. Go figure). 

Does shred have a switch to run a specified # of passes? Otherwise, I'm still stuck doing a For\Do loop with a counter.

Also, is there an algorithm I can use that is more secure than shred  \ urandom, but faster than Guttman?

---

### Post by HermanAB on 2008-03-24
All disk drives made in the last ten year or so, have a low level erase utility built into the drive controller.  That is the best way to erase a drive and you only need to run it once.

Overwriting using /dev/urandom using multiple passes (about 20 times) will achieve the same thing, but will of course take one helluvalot of time longer.

If you have a dumbass contract that requires multiple overwrites, then you need to improve your hardware so that it can run unattended.

BTW, the multi-pass 'DoD Erase' thing is a myth.  DoD doesn't actually do that anymore.  DoD erases things once then use the media at the same level of classification, or higher.  Failed media is physically destroyed - melted or shredded.  Used DoD media is never resold.

Cheers,

Herman

---

### Post by cdenley on 2008-03-24
> All disk drives made in the last ten year or so, have a low level erase utility built into the drive controller.
I never heard of this. How is the utility run?

---

### Post by HermanAB on 2008-03-24
There is a Windoze utility here [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml) that will activate it.

Cheers,

Herman

---

### Post by Biochem on 2008-03-25
> **JohnnyXmas said:**
> I switched to using /dev/urandom as the if for dd instead of zero. I understand that Guttman is way more secure, but urandom seems to be faster. Our agreement with the vendors only requires us to write 7 passes of "random data." so the algorithm doesn't really matter (Yeah, their CIO's signed off on this. Go figure). 

Does shred have a switch to run a specified # of passes? Otherwise, I'm still stuck doing a For\Do loop with a counter.

Also, is there an algorithm I can use that is more secure than shred  \ urandom, but faster than Guttman?

yes there is:

```
gabriel@nefuats:~$ shred --help
Usage: shred [OPTIONS] FILE [...]
Overwrite the specified FILE(s) repeatedly, in order to make it harder
for even very expensive hardware probing to recover the data.

Mandatory arguments to long options are mandatory for short options too.
  -f, --force    change permissions to allow writing if necessary
  -n, --iterations=N  Overwrite N times instead of the default (25)
      --random-source=FILE  get random bytes from FILE (default /dev/urandom)
  -s, --size=N   shred this many bytes (suffixes like K, M, G accepted)
  -u, --remove   truncate and remove file after overwriting
  -v, --verbose  show progress
  -x, --exact    do not round file sizes up to the next full block;
                   this is the default for non-regular files
  -z, --zero     add a final overwrite with zeros to hide shredding
      --help     display this help and exit
      --version  output version information and exit

If FILE is -, shred standard output.

```

so shred -n 7 should do it

---

### Post by cdenley on 2008-03-25
@HermanAB
How about hdparm's "security erase"? Does that do the same thing?

---

### Post by HermanAB on 2008-03-25
I guess the hdparm security features may be the Linux interface to these drive controller features, but I'm not going to try them... :)

---

### Post by JohnnyXmas on 2008-03-26
> **HermanAB said:**
> All disk drives made in the last ten year or so, have a low level erase utility built into the drive controller.  That is the best way to erase a drive and you only need to run it once.

Overwriting using /dev/urandom using multiple passes (about 20 times) will achieve the same thing, but will of course take one helluvalot of time longer.

Yeah, I tried that (with ATA drives at least). It took WAY longer than a 7-pass urandom overwrite (though I'm aware its not as "secure").

> **HermanAB said:**
> If you have a dumbass contract that requires multiple overwrites, then you need to improve your hardware so that it can run unattended.

That's precisely why I'm doing this. Load up 50 or so drives in the rack, hit go, walk away.

---

### Post by JohnnyXmas on 2008-03-26
> **HermanAB said:**
> I guess the hdparm security features may be the Linux interface to these drive controller features, but I'm not going to try them... :)

I believe it works under the same premise as [sg_dd]("http://sg.torque.net/sg/sg_dd.html") (from the sg3utils package). It's in my list of things to try, but I hear its dirt slow. Anyone tried it yet?

---

### Post by JohnnyXmas on 2008-03-26
> **Biochem said:**
> yes there is:

```
gabriel@nefuats:~$ shred --help
Usage: shred [OPTIONS] FILE [...]
Overwrite the specified FILE(s) repeatedly, in order to make it harder
for even very expensive hardware probing to recover the data.

Mandatory arguments to long options are mandatory for short options too.
  -f, --force    change permissions to allow writing if necessary
  -n, --iterations=N  Overwrite N times instead of the default (25)
      --random-source=FILE  get random bytes from FILE (default /dev/urandom)
  -s, --size=N   shred this many bytes (suffixes like K, M, G accepted)
  -u, --remove   truncate and remove file after overwriting
  -v, --verbose  show progress
  -x, --exact    do not round file sizes up to the next full block;
                   this is the default for non-regular files
  -z, --zero     add a final overwrite with zeros to hide shredding
      --help     display this help and exit
      --version  output version information and exit

If FILE is -, shred standard output.

```

so shred -n 7 should do it


Yeah, i had tried this before, but it says 7 is not a valid amount.

---

### Post by cdenley on 2008-03-26
> **JohnnyXmas said:**
> I believe it works under the same premise as [sg_dd]("http://sg.torque.net/sg/sg_dd.html") (from the sg3utils package). It's in my list of things to try, but I hear its dirt slow. Anyone tried it yet?

The hdparm "secure erase enhanced" seemed to take about as long as a single pass of a block erase. After looking over the CMRR documentation HermanAB linked to, it sounds like "security erase enhanced" is the same thing as a block erase with random data, except it is controlled by the drive itself, and erases unused/bad blocks as well. Assuming there are no unused blocks, what is the difference between a single-pass block erase with random data and a single-pass "security erase enhanced"?

---

### Post by HermanAB on 2008-03-26
As far as I know the drive controller will also erase the space between the tracks.  Apparently it is that space that is used to read old data.

Special equipment can recover old data 20 layers (or more) deep, so overwriting 7 times may comply with the OPs contract, but really makes no difference compared to overwriting once only.  However, overwriting using the drive controller does erase the data.

---

### Post by JohnnyXmas on 2008-04-15
> **HermanAB said:**
> All disk drives made in the last ten year or so, have a low level erase utility built into the drive controller.  That is the best way to erase a drive and you only need to run it once.

Yeah, it's insanely fast, but precisely what is it doing? Is it using the drive's hardware itself to write random data to the platters, or is it just writing 0's, or some set repeating pattern?

---

### Post by cdenley on 2008-04-15
The regular secure erase writes zeros to all usable sectors. The sercure erase enhanced writes random data to all sectors (usable or not). It also erases with a track offset in order to erase the track edges.

[http://cmrr.ucsd.edu/people/Hughes/CmrrSecureEraseProtocols.pdf](http://cmrr.ucsd.edu/people/Hughes/CmrrSecureEraseProtocols.pdf)

Insanely fast compared to a 21-pass erase. It seemed to take about as long as a single pass for me, which was about 1.5 hours.

---

### Post by JohnnyXmas on 2008-04-16
Cool, thanks. I was ALL about the secure-erase thing, but the drives that come through here range anywhere from 3 - 20 +years old, so it actually doesn't work o a majority of our drives. I need the script to be as universal as possible, so the secure erase command is out.

---

