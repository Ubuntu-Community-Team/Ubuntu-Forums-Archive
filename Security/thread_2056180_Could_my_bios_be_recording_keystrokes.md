---
title: "Could my bios be recording keystrokes?"
date: 2012-09-10
forum: Security
---

### Post by jonnyboysmithy on 2012-09-10
This will sound paranoid but; could my bios be capturing keystrokes, saving them and then say at some special request send the data to whoever requested it? Even when powered down (similar to wakeup on lan)? 

If the bios software is proprietary no one would know that a special code/request can be made. Flash memory is physically really small so it should be possible to have this onboard with the bios chip say and record a couple of Gb's worth.. 
This is plausible right?

---

### Post by Hungry Man on 2012-09-10
Anything's plausible. Not very likely. It would probably have to be done by the hardware manufacturer.

---

### Post by jonnyboysmithy on 2012-09-10
Yea, actually thats exactly what I had in mind. The manufacturer could do something like this right? Well I'd image it would be a trick up their sleeve they'd save until it was worth using... wait a minute .. then how do governments know their systems are secure against other companies? What if the manufacturer was infiltrated and some other company/organization got hold of the codes?

---

### Post by QIII on 2012-09-10
This reminds me.

I need to run to the store for some more tinfoil.

---

### Post by jonnyboysmithy on 2012-09-10
> **QIII said:**
> This reminds me.

I need to run to the store for some more tinfoil.
Hu?

---

### Post by Stonecold1995 on 2012-09-11
While technically possible it's highly unlikely.  The BIOS would have to write the keystroke logs somewhere, and most BIOSes aren't able to write to the disk (support for all the filesystems, checks, etc would make the BIOS too large).  As for whether it could while powered down, the answer is no.  This is because the BIOS is, to the CPU, simply code, nothing more, no special hardware or tricks or anything, just plain old code.  That means that the CPU itself has to be on to be able to run the BIOS's code, and the CPU is shut completely off when it receives the power off signal.  There would have to be a deal between Intel/AMD and your BIOS manufacturer to enable that, which would be WAY to hard to make.

So few people use Linux that it's much more likely for governments to spy on people through backdoors in Windows/Macintosh (which actually happens).  You'd have to be a pretty high profile target for someone to specifically target Linux on your computer (you don't hack .gov sites or keep kiddie porn, do you? ;)).

There are far more things to worry about security wise than a keylogging BIOS.

---

### Post by jonnyboysmithy on 2012-09-11
> While technically possible it's highly unlikely.  The BIOS would have to write the keystroke logs somewhere, and most BIOSes aren't able to write to the disk (support for all the filesystems, checks, etc would make the BIOS too large).I was thinking more of a onboard flash memory somewhere on the motherboard or so rather than an actuall harddrive.

> 
There are far more things to worry about security wise than a keylogging BIOS.You're probably right.. I should be more careful with what minecraft mods I run :P
> 
So few people use Linux that it's much more likely for governments to  spy on people through backdoors in Windows/Macintosh (which actually  happens).  You'd have to be a pretty high profile target for someone to  specifically target Linux on your computer (you don't hack .gov sites or  keep kiddie porn, do you? :wink:).Of course not. I was just brainstorming and the idea struck me that bios keylogging could happen.
> 
 to  spy on people through backdoors in Windows/Macintosh (which actually  happens) Any examples?

---

### Post by Hungry Man on 2012-09-11
> **jonnyboysmithy said:**
> Yea, actually thats exactly what I had in mind. The manufacturer could do something like this right? Well I'd image it would be a trick up their sleeve they'd save until it was worth using... wait a minute .. then how do governments know their systems are secure against other companies? What if the manufacturer was infiltrated and some other company/organization got hold of the codes?

This has recently been an issue as we get so much hardware from China. There were unsubstantiated rumors of backdoors being built in.

---

### Post by rookcifer on 2012-09-11
> **jonnyboysmithy said:**
> Yea, actually thats exactly what I had in mind. The manufacturer could do something like this right? Well I'd image it would be a trick up their sleeve they'd save until it was worth using... wait a minute .. then how do governments know their systems are secure against other companies? What if the manufacturer was infiltrated and some other company/organization got hold of the codes?

In the USA at least, our NSA has it's own chip manufacturing fab for sensitive systems for precisely this reason.

---

### Post by Stonecold1995 on 2012-09-11
> **jonnyboysmithy said:**
> I was thinking more of a onboard flash memory somewhere on the motherboard or so rather than an actuall harddrive.
That's possible, but it would be more likely that it would be a hardware keylogger then a bugged BIOS.  A hardware keylogger would be more reliable and harder to detect.

> **jonnyboysmithy said:**
> Any examples?
[https://newsworldwide.wordpress.com/2008/05/02/microsoft-discloses-government-backdoor-on-windows-operating-systems/]("https://newsworldwide.wordpress.com/2008/05/02/microsoft-discloses-government-backdoor-on-windows-operating-systems/")
[http://www.intego.com/mac-security-blog/us-government-wants-backdoors-in-all-communications-devices/]("http://www.intego.com/mac-security-blog/us-government-wants-backdoors-in-all-communications-devices/")
[https://www.eff.org/deeplinks/2010/08/steve-jobs-watching-you-apple-seeking-patent-0]("https://www.eff.org/deeplinks/2010/08/steve-jobs-watching-you-apple-seeking-patent-0")
[https://www.eff.org/issues/nsa-spying]("https://www.eff.org/issues/nsa-spying")
[http://nakedsecurity.sophos.com/2011/10/09/government-backdoor-trojan-chaos/]("http://nakedsecurity.sophos.com/2011/10/09/government-backdoor-trojan-chaos/")
[https://www.f-secure.com/weblog/archives/00002423.html]("https://www.f-secure.com/weblog/archives/00002423.html")
[https://newsworldwide.wordpress.com/2012/02/26/windows-8-will-have-a-kill-switch/]("https://newsworldwide.wordpress.com/2012/02/26/windows-8-will-have-a-kill-switch/")
[http://www.quora.com/Is-there-any-evidence-for-backdoors-in-Windows-or-other-client-software-for-the-NSA-CIA]("http://www.quora.com/Is-there-any-evidence-for-backdoors-in-Windows-or-other-client-software-for-the-NSA-CIA")
[http://www.heise.de/tp/artikel/5/5263/1.html]("http://www.heise.de/tp/artikel/5/5263/1.html")
[https://en.wikipedia.org/wiki/NSAKEY]("https://en.wikipedia.org/wiki/NSAKEY")
[https://en.wikipedia.org/wiki/Cofee]("https://en.wikipedia.org/wiki/Cofee")
[http://www.theforbiddenknowledge.com/hardtruth/nsa_backdoor_windows.htm]("http://www.theforbiddenknowledge.com/hardtruth/nsa_backdoor_windows.htm")
[http://www.judiciaryreport.com/the_fbi_has_built_in_backdoor_in_windows_used_for_spying.htm]("http://www.judiciaryreport.com/the_fbi_has_built_in_backdoor_in_windows_used_for_spying.htm")

There's a lot more but I'm too lazy and I don't want to trip any anti-spam systems.

---

### Post by jonnyboysmithy on 2012-09-11
> **Stonecold1995 said:**
> That's possible, but it would be more likely that it would be a hardware keylogger then a bugged BIOS.  A hardware keylogger would be more reliable and harder to detect.


[https://newsworldwide.wordpress.com/2008/05/02/microsoft-discloses-government-backdoor-on-windows-operating-systems/](https://newsworldwide.wordpress.com/2008/05/02/microsoft-discloses-government-backdoor-on-windows-operating-systems/)
[http://www.intego.com/mac-security-blog/us-government-wants-backdoors-in-all-communications-devices/](http://www.intego.com/mac-security-blog/us-government-wants-backdoors-in-all-communications-devices/)
[https://www.eff.org/deeplinks/2010/08/steve-jobs-watching-you-apple-seeking-patent-0](https://www.eff.org/deeplinks/2010/08/steve-jobs-watching-you-apple-seeking-patent-0)
[https://www.eff.org/issues/nsa-spying](https://www.eff.org/issues/nsa-spying)
[http://nakedsecurity.sophos.com/2011/10/09/government-backdoor-trojan-chaos/](http://nakedsecurity.sophos.com/2011/10/09/government-backdoor-trojan-chaos/)
[https://www.f-secure.com/weblog/archives/00002423.html](https://www.f-secure.com/weblog/archives/00002423.html)
[https://newsworldwide.wordpress.com/2012/02/26/windows-8-will-have-a-kill-switch/](https://newsworldwide.wordpress.com/2012/02/26/windows-8-will-have-a-kill-switch/)
[http://www.quora.com/Is-there-any-evidence-for-backdoors-in-Windows-or-other-client-software-for-the-NSA-CIA](http://www.quora.com/Is-there-any-evidence-for-backdoors-in-Windows-or-other-client-software-for-the-NSA-CIA)
[http://www.heise.de/tp/artikel/5/5263/1.html](http://www.heise.de/tp/artikel/5/5263/1.html)
[https://en.wikipedia.org/wiki/NSAKEY](https://en.wikipedia.org/wiki/NSAKEY)
[https://en.wikipedia.org/wiki/Cofee](https://en.wikipedia.org/wiki/Cofee)
[http://www.theforbiddenknowledge.com/hardtruth/nsa_backdoor_windows.htm](http://www.theforbiddenknowledge.com/hardtruth/nsa_backdoor_windows.htm)
[http://www.judiciaryreport.com/the_fbi_has_built_in_backdoor_in_windows_used_for_spying.htm](http://www.judiciaryreport.com/the_fbi_has_built_in_backdoor_in_windows_used_for_spying.htm)

There's a lot more but I'm too lazy and I don't want to trip any anti-spam systems.
Thanks a lot for that.. Lots of reading :)

---

### Post by tubbygweilo on 2012-09-11
Following on from rookcifer's contribution:

No one can say whether it is happening or not but some bodies are concerned. 

Bruce Schneier has a few thoughts on this subject Backdoor Found Maybe in Chinese-Made Military Silicon Chips [http://www.schneier.com/blog/archives/2012/05/backdoor_found.html](http://www.schneier.com/blog/archives/2012/05/backdoor_found.html)

---

### Post by mike acker on 2012-09-11
if you're to the point of fussing over hardware backdoors you probably want to go air-gap and use the Vernam cipher

what you would do is scrounge around and find some older computers put Ubuntu on 2 of them. Connect 1 to the net and leave the other offline.  write your messages on the offline 'puter and encrypt them using the Vernam cipher. then carry them to the online puter via SneakerNet -- on a CD perhaps -- or better yet use a null modem cable with an old copy of ProComm -- or just some re-directed I/O -- move the ciphertext to the online puter and send it with T/Bird . by the time you have created this toggled-up mess nobody's virus is going to work on it any how tee hee

i have a sample Vernam cipher program (CodeBook1) in C++ for Windows. be sure to google for the vernam cipher so you understand 1-time keypads.

---

### Post by Lulutoujourslatortue on 2012-09-12
> **jonnyboysmithy said:**
> Thanks a lot for that.. Lots of reading :)
Hello, it's very possible, i'have problem with latest virus in the bios (keyloger, vnc...), but for to delt in the rom, we must flash the bios, but in the tread :
[http://lists.debian.org/debian-live/2010/09/msg00254.html](http://lists.debian.org/debian-live/2010/09/msg00254.html)

Ubuntu have error :
I: -input-charset not specified, using utf-8 (detected in locale settings)
call to search_tree_file with an absolute path, stripping
initial path separator. Hope this was intended...
genisoimage: Uh oh, I cant find the boot image ~/Download/Acer_Bios_v1.14_2_8Mo.IMG

I would creat news thread here for to help peapol withe laptop. Good look!

---

### Post by rookcifer on 2012-09-12
> **mike acker said:**
> if you're to the point of fussing over hardware backdoors you probably want to go air-gap and use the Vernam cipher

what you would do is scrounge around and find some older computers put Ubuntu on 2 of them. Connect 1 to the net and leave the other offline.  write your messages on the offline 'puter and encrypt them using the Vernam cipher. then carry them to the online puter via SneakerNet -- on a CD perhaps -- or better yet use a null modem cable with an old copy of ProComm -- or just some re-directed I/O -- move the ciphertext to the online puter and send it with T/Bird . by the time you have created this toggled-up mess nobody's virus is going to work on it any how tee hee

How do you propose to exchange keys with your contacts?  Carrier Pigeon?  That's why OTP's are never used IRL.  They are too impractical.  That is the whole reason some very smart people invented public-key cryptography.

> i have a sample Vernam cipher program (CodeBook1) in C++ for Windows. be sure to google for the vernam cipher so you understand 1-time keypads.

I wrote a OTP implementation in Python for kicks and grins.  Of course I'll never use it since key exchange is near impossible (also because it uses /dev/random, while strong, it's not perfectly random in the truest sense).

---

### Post by Lulutoujourslatortue on 2012-09-12
Problem resolve withe this thread : 
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

good loock!

---

### Post by blortuga on 2012-09-17
maybe you mean something like this?
[http://www.wondcam.com/spy-keyboard-01.html](http://www.wondcam.com/spy-keyboard-01.html)

It doesn't have to be part of the BIOS.

And yes, government agencies (particularly those who deal with sensitive information) take a lot of effort to try to ensure that their hardware comes only from trusted vendors.  It's not a small task.

---

### Post by ShadowVegan on 2012-09-18
To my understanding, a keylogger (or screenlogger) can exist as:
-Physical extension (mainly an issue in desktops, there might be a device attached where the keyboard connects to the computer), easily detected and removed
-Firmware based (does not require physical access, very hard to detect and remove, but also very unlikely to have)
-Software based (rare in Linux, common in Windows, fresh OS install will get rid of it, virus scans MAY detect it; using a non-writeable Live CD could circumvent this risk)

The [Wikipedia article](http://en.wikipedia.org/wiki/keylogger) has some pretty good info.

---

### Post by Stonecold1995 on 2012-09-18
I found a script however on the Arch Linux wiki that checks the files in /boot at each boot and alerts you to the changes to prevent bootkits and kernel keyloggers from going unnoticed.  Specifically, it checks the sha1sum of the files against those at the last boot, it checks the MBR against the MBR of the last boot, and also checks to see if any of the inodes of the files have changed.  The script works best if you are using disk encryption, but may provide a *little* extra security even if you aren't using encryption.  It's kind of outdated though so I modified it and gave it a few improvements.  I'm not sure if it works if you aren't using KDE, because it uses some KDE utilities like kdialog and also needs ".kde/Autostart" to be the autostart directory.  Anyways, it comes in two parts, [chkboot]("http://pastebin.com/mG1u9Mmq") and [chkboot_user]("http://pastebin.com/RAy9xhaE").  Download them to home as chkboot.sh and chkboot_user.sh.  Open chkboot.sh in any text editor and change where it says "bdev=/dev/sdb5" and "bdisk=/dev/sdb" to whatever you're using for your /boot partition and the disk it is on respectively (run "mount | grep /boot | awk {'print $1'}" in Terminal to see what partition /boot is on).  Then run these commands in Terminal:
```
sudo -i
cd /home/your_username
chmod a+x chkboot*
chown root:root chkboot*
mv chkboot* /usr/local/bin
ln -s /usr/local/bin/chkboot_user.sh /home/your_username/.kde/Autostart
exit
```

Now open "/etc/rc.local" in a text editor and add "/usr/local/bin/chkboot.sh &" to it to make it look something like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/chkboot.sh &

exit 0
```

Now reboot and the script should be ready.  The requirements are that you are using KDE (although it can be modified to work on other DE's, but I only have KDE so I don't know how to do that), that you have access to sudo, and that your /tmp partition is not using the "noexec" flag (if running "cat /etc/fstab | grep /tmp | grep -c noexec" outputs 0 then /tmp is mounted without noexec).

This script won't provide absolute security.  An advanced enough kernel rootkit may be able to disable this script if it knows you're using it.  Also, it only notifies you of /boot changes, but doesn't do anything about it (although it makes backups of /boot, and it'll let you manually restore files if you want) so if the rootkit is designed to send your password over the network as soon as the computer boots then you're screwed.  I may modify it to attempt to disable the network if changes in /boot are found, but that may become annoying because kernel upgrades and other benign /boot modifications trigger the script.

Disclaimer: I didn't make this script, I just modified and improved the original a little bit.

I use this script as my tinfoil hat and it makes me feel a lot safer. ^^

---

### Post by cariboo on 2012-09-18
Just to add to everyone's paranoia, [This]("http://www.keelog.com/hardware_keyboard_logger.html") one should be pretty hard to detect for the average user.

---

### Post by jon zendatta on 2012-09-19
Is it possible to detect a Keylogger?

```
lspci -v
```

---

### Post by Stonecold1995 on 2012-09-19
> **jon zendatta said:**
> Is it possible to detect a Keylogger?

```
lspci -v
```

That wouldn't detect a hardware keylogger, no non-invasive keylogging device would announce itself to the operating system.  All a hardware keylogger does is receive what you type through the keyboard, and then send that on to the computer itself while secretly logging it.  It's like asking "Is it possible for a computer to detect a USB cable with an extender?", unless the keylogger is particularly invasive, there is no way to detect it with any programs or commands.

Hardware keylogger:
-No computer software can detect it (completely transparent to any operating system)
-Very cheap to buy, and you can get them just about anywhere
-It can be detected more easily if you know what your computer looks like inside (monitoring the physical hardware for changes vs monitoring several hundred-thousand constantly changing files)
-Unless it is particularly advanced, the attacker would have to have complete physical access to your computer
-Can only detect what is typed in through the logged device, nothing else at all (so using a virtual keyboard would protect you)

Software keylogger:
-Can be detected by software, although kernel-based keyloggers can be particularly stealthy
-Advanced or stealthy ones can be extremely expensive (sometimes thousands of dollars), and are hard for the average person to buy (you'd usually have to go to underground hacker groups to get really powerful, stealthy ones...  the cheap ones you can download legally won't have 0days, or will be easy to detect and remove, except for on Windows)
-Very hard to detect if you don't know a lot about computers
-Can be installed remotely, and have logs retrieved remotely
-Can do much more then just log keys, it could take screenshots, log running processes, record audio/video, change files, etc

---

