---
title: "Suckit rootkit... Warning: /sbin/init INFECTED"
date: 2011-02-02
forum: Security
---

### Post by zimshuge on 2011-02-02
Hello there, 

Yesterday I did a apt-get upgrade and the following was updated.

>  Upgraded:
   base-files 5.0.0ubuntu20.10.04.2 => 5.0.0ubuntu20.10.04.3
   bsdutils 1:2.17.2-0ubuntu1.10.04.1 => 1:2.17.2-0ubuntu1.10.04.2
   consolekit 0.4.1-3ubuntu1 => 0.4.1-3ubuntu2
   libblkid1 2.17.2-0ubuntu1.10.04.1 => 2.17.2-0ubuntu1.10.04.2
   libc-bin 2.11.1-0ubuntu7.7 => 2.11.1-0ubuntu7.8
   libc-dev-bin 2.11.1-0ubuntu7.7 => 2.11.1-0ubuntu7.8
   libc6 2.11.1-0ubuntu7.7 => 2.11.1-0ubuntu7.8
   libc6-dev 2.11.1-0ubuntu7.7 => 2.11.1-0ubuntu7.8
   libck-connector0 0.4.1-3ubuntu1 => 0.4.1-3ubuntu2
   libpam-ck-connector 0.4.1-3ubuntu1 => 0.4.1-3ubuntu2
   libuuid1 2.17.2-0ubuntu1.10.04.1 => 2.17.2-0ubuntu1.10.04.2
   mount 2.17.2-0ubuntu1.10.04.1 => 2.17.2-0ubuntu1.10.04.2
   upstart 0.6.5-7 => 0.6.5-8
   util-linux 2.17.2-0ubuntu1.10.04.1 => 2.17.2-0ubuntu1.10.04.2
   uuid-dev 2.17.2-0ubuntu1.10.04.1 => 2.17.2-0ubuntu1.10.04.2

When my daily chkrootkit scanned it found 

Suckit rootkit

rkhunter did not find anything

I restored from a previous image, checked again and nothing. Updated and it is back, could it be a false positive?

I took an md5 (ce3316f99cf04c20e92d92179d26f8eb) of /sbin/init not sure if that helps or not :lolflag:

Thanks for any help you can provide!

---

### Post by cariboo on 2011-02-02
Which package is supposed to be infected?

---

### Post by WinstonChurchill on 2011-02-02
> **zimshuge said:**
> 
I took an md5 (ce3316f99cf04c20e92d92179d26f8eb) of /sbin/init not sure if that helps or not
That depends on what type of processor you're running on... plus it probably varies depending on the version of the kernel you're using - I'm not entirely sure.

---

### Post by zimshuge on 2011-02-02
Sorry about that, I should have been more specific. 

When I run 

apt-get install upstart 

After it updates my current upstart, it says I have the Suckit rootkit

---

### Post by Azren0 on 2011-02-02
Hey

Out of curiosity I also did a quick scan with chkrootkit and had the same issue; anything to be worried about?

The file which is apparently infected is /sbin/init

I also had the following show up:

wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1832], /sbin/dhclient3[2437])

FYI I am running Xubuntu 64 bit 10.10, 2.6.35-25-generic.

---

### Post by zimshuge on 2011-02-02
I have found the problem from this thread

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1554553](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1554553)

It seems that a reboot of the system will fix the problem, there is more details in the thread above. I did try it and it comes up clean for me now.

---

### Post by demarshall on 2011-02-11
> **zimshuge said:**
> I have found the problem from this thread

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1554553](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1554553)

It seems that a reboot of the system will fix the problem, there is more details in the thread above. I did try it and it comes up clean for me now.

The discussion at that link was last summer so I wonder if it is still relevant today or this week.

I did a reboot as you suggested and Chkrootkit does not find the possible infection but does that mean that it is gone or has it been concealed?

Is there another tool or another procedure that we can use to ensure our systems are secure?

I heard recently from somebody who is working for a security software company as a salesperson that although Linux has been safe, it has recently become more of a target. Should we be running Kyspersky or something like that on our Linux boxes?

David

---

### Post by demarshall on 2011-02-11
I found another application called tiger in the repositories through Synaptic and installed it. Although it did not find any problem in the rootkit area, it did come up with another problem that I'm a bit unsure how to deal with. That is in checking permissions and ownership of system files. It seems that it has a problem with 

--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem

I read about it as a bug on Launchpad here: 
[https://bugs.launchpad.net/ubuntu/+source/tiger/+bug/606837](https://bugs.launchpad.net/ubuntu/+source/tiger/+bug/606837)

but it seems that they are unsure how to deal with this problem although it does not seem to be a security issue but rather a problem in Tiger.

Tiger checks much more than just for rootkits. If you are interested in checking the security of your system, you may want to check it out.

Also, since my last post, I applied with both Kaspersky and Bitdefender in order to check out their security suites. I noticed, I believe on both site, that there were comments as I mentioned earlier about Linux being more of a target now. Any thoughts about how we're going to deal with that? I always figured that since it required a password to make any changes that we were safe but I guess that's not true anymore.

I have had Tiger running while I typed this and it seems to have stalled at 

06:45> Performing system specific checks...
/bin/grep: /etc/inittab: No such file or directory

Any idea what to do about this stall or is Tiger, perhaps, not totally compatible with Ubuntu 10.04?

---

