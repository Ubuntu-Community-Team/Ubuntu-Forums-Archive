---
title: "Rootkit or paranoia??"
date: 2009-03-15
forum: Security
---

### Post by Jacdeb6009 on 2009-03-15
Hi there,

First off my apologies for such a long post.  I have lived happily in Linux-land now since about July of 2008, now however, there is something that is concerning.

My basic machine (Dell Vostro 1400) setup is as follows:

1. Dell utilities partition
2. Media-direct partition
3. Windows XP SP3
4. Ubuntu Hardy Heron
5. Swap partition
6. Home partition

The reason for the dual boot set-up is twofold.  (1) the machine belongs to my employer and came with Windows pre-installed and(2) the company I work for use Lotus Notes as their e-mailer, they did not want to give me a Linux version since they did not wish to support "that" operating system D:  for work purposes I am more or less forced also to use MS Project since this is what everyone else uses and I have not found an open source equivalent to this.  I played around with Wine but could not get either packages to work (admittedly, I did not spend weeks trying to do this).

Under Windows the following is installed:

- Microsoft Office XP
- Microsoft Project 2000
- Lotus Notes 7
- ACDSee
- Autocad Viewer
- Adobe Acrobat 8
- CCleaner
- F-Secure
- Firefox
- Pidgin
- Skype
- Winrar
- Workrave
- COD 10 English dictionary
- DWG to DXF converter
- Unit converter
- A number of utilities bundled with the machine for the Webcam, etc.

All of the above are either Open Source or legal commercial software.  No cracked or pirated software installed :)

The Ubuntu installation is a pretty standard installation from the Live CD and all remaining software was installed from the Ubuntu repositories, with the exception of :

- COD 10 (running under Wine)
- DWG to DXF converter (running under Wine)
- Unit converter (running under Wine)
- OpenOffice 3.0 (downloaded from Sun and MD5 verified)
- RawTherapee (downloaded from the developer's website and MD5 verified)
- Sunbird (downloaded from Mozilla and verified as good)

I don't run a firewall (a check with Gibson Reseacrh's "ShieldsUp" confirmed that my ISP effectively "cloaks" the machine) and viruses are checked for under Windows only using F-Secure (which is updated everytime the Windows machine is booted).

I ran "rkhunter" a couple of times after setting up the Linux machine, but after it not turning up anything, I stopped doing this (yes, I know I should have made it a CRON job, but being a relative Linux noob I haven't really figured this one out yet...)

The machine is used for work and for "tinkering".  I use Linux 90% of the time or more.  Windows is only used when I need MS Project and to update the Notes mail database once a day (for the rest I use the Notes Webmail interface from Linux).

A couple of weeks ago I installed Ibex on an external drive and set up a virtual machine to run MS Project and Notes.  Having done this succesfully, I set up a virtual machine in Hardy and installed Notes and Project.  This worked well, although updating Windows XP to SP3 tookforever.

Eventually I decided not move to Ibex since I had problems with the microphones (external and internal) and thus could not run Skype (also a pretty important tool to me).

About two weeks ago I decided to try and get my bluetooth headset to work.  After playing around with it for several hours (unsuccessfully) I gave up and decided that the external wired headset would suffice.

After giving up and rebooting the machine (the next morning), I noticed that I got the Ubuntu splash screen (as usual) but after a short while (about 10 to 15 seconds) this was replaced by the typical Linux "commentary" as the machine booted.  There was also an error regarding a "conflict" with the computer's name which could not be resolved.  In the last week or two, I have also been travelling quite a bit and connecting to various "public" networks (generally hard wired) in various offices and hotels.  This of course without a firewall (silly me, I had gotten so used to my set up at home that I didn't really think about this).

Generally, except for the change during the boot sequence, the machine seems to behave nomrally.  No unusual hard drive activity or anything like that.  Both the Ubuntu and Windows installations are current in terms of security updates and patches.

A couple of days ago (as I was in a tinkering mood) I decided to take a closer look at the whole issue and decided to run rkhunter and chkrootkit.  The results of this are my reason for the post...

Rkhunter (after updating several times) still reports a number of "problems", as shown below :

[18:45:57] Running Rootkit Hunter version 1.3.4 on gandalf-laptop
[18:45:57]
[18:45:57] Info: Start date is Wed Mar 11 18:45:57 ICT 2009
[18:45:57]
[18:45:57] Checking configuration file and command-line options...
...
[18:46:00] Performing 'shared libraries' checks
[18:46:00] Info: Starting test name 'shared_libs'
[18:46:00] Checking for preloading variables                 [ None found ]
[18:46:00] Checking for preload file                         [ Not found ]
[18:46:00] Info: Starting test name 'shared_libs_path'
[18:46:00] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[18:46:00]
[18:46:00] Performing file properties checks
[18:46:00] Info: Starting test name 'properties'
[18:46:00] Checking for prerequisites                        [ OK ]
...
[18:46:03] /bin/which                                        [ Warning ]
[18:46:03] Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script text executable
...
[18:46:05] /usr/bin/groups                                   [ Warning ]
[18:46:05] Warning: The command '/usr/bin/groups' has been replaced by a script: /usr/bin/groups: POSIX shell script text executable
...
[18:46:05] /usr/bin/ldd                                      [ Warning ]
[18:46:05] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable
...
[18:46:09] /usr/bin/lwp-request                              [ Warning ]
[18:46:09] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: perl script text executable
...
[18:46:11] /usr/sbin/adduser                                 [ Warning ]
[18:46:11] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: perl script text executable
...
[18:47:08] System checks summary
[18:47:08] =====================
[18:47:08]
[18:47:08] File properties checks...
[18:47:08] Files checked: 126
[18:47:08] Suspect files: 5
[18:47:08]
[18:47:08] Rootkit checks...
[18:47:08] Rootkits checked : 113
[18:47:08] Possible rootkits: 0
[18:47:08]
[18:47:08] Applications checks...
[18:47:08] Applications checked: 2
[18:47:08] Suspect applications: 0
[18:47:08]
[18:47:08] The system checks took: 1 minute and 10 seconds
[18:47:08]
[18:47:08] Info: End date is Wed Mar 11 18:47:08 ICT 2009

(The log file has been edited to get rid of everything that is "OK")

Running chkrootkit on the other hand produces a totally "clean" result.

So then the question... Is this a problem? Has the machine been infected by a rootkit or is this just a very unhealthy dose of paranoia?

The machine is critical to me as I am know working more or less in the middle of nowhere and my work depends heavily on the machine (also my ability to communicate with the outside world, my bank and conduct all manner of other business via the internet).

As far as using the Internet is concerned, Firefox is always run with NoScript in place and all scripts blocked, except for trusted sites (bank, etc.), and suspect websites are avoided.  I don't generally click on links in e-mails, except for those in newsletters from trusted sources (TechRepublic, Ubuntu Forums and the like).

I don't really see how a rootkit could've infected the machine, but then my understanding of these things is not very good, meaning that I cannot really say.

One possibility is that the strange behaviour during booting is the result of the Ibex installation.  Ibex was installed on a brand new 500 Gbyte external drive bought specifically to be able to "play" with various Linux distributions.  It has it own bootloader (Grub) installed on the external drive, meaning that when it is connected the machine will boot the Grub menu on the external drive and then whatever is selected on the external drive and when it is not connected, the machine will boot the Grub menu on its internal drive allowing either Hardy Heron or Windows to be selected. The conflict in resolving the computer name may also originate from there, but I cannot really tell.  I have looked through the logs in /var/log but cannot see this error/warning message in any of them (at least not the ones I can find).  The warning mentions a "Most Frequent" entry in the /docs directory, but I have looked through it (/usr/share/doc) and cannot find a file like this.

Also, if the machine can no longer be trusted, how do I correct this??  Will re-installing Hardy solve this problem or is it necessary to also re-install the Windows part of the dual boot? If re-installing Windows is necessary, is simply not booting or running Windows an option instead of re-installing it?

Can anybody help with this??  Am I just being paranoid after 20 years of using Windows, or is there possibly a real problem here?? Any advice / comments would be highly appreciated!  Thanks for your patience... :)

---

### Post by brian_p on 2009-03-15
> **Jacdeb6009 said:**
> 

So then the question... Is this a problem? Has the machine been infected by a rootkit or is this just a very unhealthy dose of paranoia?

These are false positives, documented many times in these forums. Relying in any way on chkrootkit or rkhunter for the security of your machine is unwise. If intrusion detection is what you want there are probably better ways of achieving it.

> I don't really see how a rootkit could've infected the machine, but then my understanding of these things is not very good, meaning that I cannot really say.

Running programs as root, not updating the system and installing packages from unsafe sources risk infection.

---

