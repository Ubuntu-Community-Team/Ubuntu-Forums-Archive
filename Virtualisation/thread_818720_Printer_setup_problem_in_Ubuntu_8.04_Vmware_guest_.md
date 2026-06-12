---
title: "Printer setup problem in Ubuntu 8.04 Vmware guest with WinXP as host"
date: 2008-06-04
forum: Virtualisation
---

### Post by gcshum on 2008-06-04
Installed Vmware Workstation 6.0.4 under WinXP.
Installed Ubuntu 8.04 as guest OS.
Installed Vmware Tools okay.

Parallel port is passed onto Ubuntu by Vmware and is shown as available under VM menu of Vmware Workstation application.

A HP Laserjet 6MP is connected to lpt1: and it's working fine under WinXP.

I want to set up this printer in the Ubuntu guest for printing. But when I go to System>Administration>printing, I am not able to add a printer as most of the buttons are grayed out. I can only select Goto Server or Refresh buttons.

When I select Goto server, a small box opens for my CUPS server. /var/run/cups/cups.sock is there by default and user name is my login id. When I press Connect button, an error message comes up saying 'CUPS server error There was an error during the CUPS operation: 'httpConnectionEncrypt failed'.'

I know that cupsys is running already. The Printer service is enabled as shown under System>Administration>Services.

It seems Ubuntu is not able to connect to the server. But I checked that cupsd.conf already has the following lines:

Listen localhost:631
Listen /var/run/cups/cups.sock

I also tried lpinfo -v in terminal, bit it returned
lpinfo: Unable to connect to server: Connection refused

I'm now lost. As I am a noob in Linux, can someone please help?

It's not really a critical piece of feature to setup as I can always copy & paste the file to WinXP and print there. It's just more convenient to be able to print directly from within the guest OS.

TIA

gcshum

---

### Post by Anicka on 2008-06-11
I have the same problem, with the same setup as gcshum, so I'm bumping this thread in hope of someone finding a solution.

---

### Post by gcshum on 2008-06-11
More info...

In a terminal, I typed in

sudo /etc/init.d/cupsys status

And it returned with

Status of Common Unix Printing System: cupsd is not running but /var/run/cups/cupsd.pid exists.

I don't quite understand this message. So I restarted cupsd with

sudo /etc/init.d/cupsys restart

The message followed indicated sucess. But the same error message returned when I do a 2nd 'sudo /etc/init.d/cupsys status' command.

What's stopping cupsd???

---

### Post by Anicka on 2008-06-12
I second that too! Help!

---

### Post by gcshum on 2008-06-12
Looking through the user.log file, I found the following.

cupsd: *** glibc detected *** /usr/sbin/cupsd: double free or corruption (!prev): 0x080dc790 ***

As a matter of fact, I have this entry everyday. The only difference is the last part which I think is a hex memory location.

After searching on Google, it seems this may be caused by a run-time error of the compiler. But there is no solution on what I should do.

Anyone?

---

### Post by skaranko on 2008-06-13
Exactly the same setup and the same problem. Some more info:

When running "/etc/init.d/cupsys restart" in /var/log/messages I get the following:

```
Jun 13 15:13:52 vm kernel: [67185.717317] audit(1213359232.014:14): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=32301 profile="/usr/sbin/cupsd" namespace="default"
Jun 13 15:13:52 vm kernel: [67185.756659] audit(1213359232.050:15): type=1503 operation="inode_permission" requested_mask="Ux::" denied_mask="Ux::" name="/usr/lib/vmware-tools/bin32/vmware-tpvmlp" pid=32301 profile="/usr/sbin/cupsd" namespace="default"
Jun 13 15:13:52 vm kernel: [67185.757151] audit(1213359232.050:16): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/dev/tty" pid=32301 profile="/usr/sbin/cupsd" namespace="default"
Jun 13 15:13:52 vm kernel: [67185.930769] audit(1213359232.226:17): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=32313 profile="/usr/sbin/cupsd" namespace="default"
```

---

### Post by gcshum on 2008-06-13
Yes, I have the same lines in the /var/log/messages file. There is one line just before them.

Jun 13 09:15:45 gs-ubuntu kernel: [   81.863242] ppdev: user-space parallel port driver

I'm surprised not too many people are having this problem. Maybe I'm missing something somewhere. I'm just too new in linux.

---

### Post by skaranko on 2008-08-14
Seems like apparmor is preventing access to the vmware printer drivers. 

However, I still can't print after tweaking apparmor confs. Now I'm seeing the VMware virtual printer ok, but when printing a test page I get in /var/log/syslog:

 tpvmlp[6500]: bad device "/dev/No" given

I might have messed up the apparmor conf though, this is the first time I checked it out.

---

### Post by gcshum on 2008-08-14
Please let me know once you have found a solution. I've given up on trying further with my little knowledge.

Thanks.

---

### Post by smspiff1 on 2009-02-01
After spending days trying to fix this issue (i.e., can't print with Ubuntu 8.04 Guest in VMWare Fusion host), I found something that is working for me.  Turns out, when I install the 'Install VMware Tools', this inserts two new links in /usr/lib/cups/backend/ which renders all printing useless -- no matter what I tried!

The following is what I did, then, to fix issue:

  $ cd /usr/lib/cups/backend/

  $ ls -lFat  (<-- '-lFat' just to see everything 'nicely')

you'll see some 'standard' stuff, i.e.,:

  ...
  bluetooth
  ...
  cupspdf
  ...
  lpd
  ...

but, also two vmware links, mine looked like this:

  tpvmgp -> /usr/lib/vmware-tools/bin/vmware-tpvmlp
  tpvmlp -> /usr/lib/vmware-tools/bin/vmware-tpvmlp

So, for me, removing these did the trick:

  $ sudo rm tpvmgp
  $ sudo rm tpvmlp

I've done some 'post-op', and it seems like this has had no 'ill' affects.  Instead, now, all printing works fine, again!  I say 'again' because it had been working for months. Don't know if VMware Fusion 2.0 or Ubuntu updates changed things, but now all cups/printing/processes work fine.

---

