---
title: "Ubuntu 20.04 Grub replaced by Debian Grub and the VM does not connect to the network"
date: 2021-06-13
forum: Virtualisation
---

### Post by exsurgo-ankit on 2021-06-13
Hello,

I am running Ubuntu 20.04 on a virtual machine hosted on VirtualBox software in Windows 10. Things were fine for a few months since install, then in the last couple days after a power outage, the system only shows Debian Grub options.
It only boots into Xfce UI. I can still login as the main user and I checked that all my files exist. But there is no network.

I tried booting with a live CD, and the networking works in a live session. 

I have tried running the Boot Repair but get an error - "The system is in Bios-compatibilty mode...."

Here is a pastebin link to the boot info
[https://paste.ubuntu.com/p/xMg8MjCrdj/](https://paste.ubuntu.com/p/xMg8MjCrdj/)

I am lost as to how I can revert back to the Ubuntu desktop where all my services were accessible and the networking was working. 

I have spent a few hours googling this and none of the suggestions have worked. I have tired modifying grub.cfg, running boot-repair.
The closest explanation similar to the issue I found in at this link but it has no solution.
[https://unix.stackexchange.com/questions/597750/why-do-i-have-a-debian-grub-boot-loader-with-debian-listed-as-the-default-os-to](https://unix.stackexchange.com/questions/597750/why-do-i-have-a-debian-grub-boot-loader-with-debian-listed-as-the-default-os-to)

Any pointers to get this resolved will be greatly appreciated.

Regards

---

### Post by slickymaster on 2021-06-14
Thread moved to **Virtualisation** for a better fit

---

### Post by MAFoElffen on 2021-06-15
Sorry for no response before this. I saw one post, and thought it had been addressed. I just noticed it had been moved from somewhere else.

So let's see where you are at. You say you installed clean/fresh with Ubuntu 20.04 a few months ago, as a Virtual box VM on a Windows 10 host. So it was not an upgrade from another release version, and it was installed as a Ubuntu Desktop... You now, after a power outage, have a problem with the desktop and with network settings... Is that about right?

My curiosities:
That you said you can start an Xfce desktop environment, that the Grub Menu changed from the Ubuntu Branding to some kind of Debian Branding. I was not aware that the Xfce desktop was installed on a vanilla install of Ubuntu. The same with the Debian branding of the Grub2 package. Both of those would take additional steps to get there. Is there something more or anything else you would like to add of packages you added after the installed? After the install and initial configuration, did you not take a snapshot to fall back to? (just something to think about in your practices).

Next, that with a power failure, was the VM running when the power (not powered down) was interrupted? If so, then the state file was corrupted. Again, in hindsight, if you used:
```

VBoxManage discardstate "vm_name"

``` 
... before you tried to reconnect to that VM, then it would have started clean from a fresh boot. You might still try that... I would. No harm right?

On the VM networking, did you configure networking on the VM after the install? For instance, the VM switch is working fine. You said you attached a LiveCD ISO to it and it booted fine and had networking. So default DHCP works on that VM. 

So with 20.04, the default networking is NetPlan. Using the LiveCD environment, look at the file at /etc/netplan/01-network-manager-all.yaml and post the contents of that in a post wrapped within code tags. 

I wrote it 10 years ago, but in the sticky in my signature line, in post #3, is a tutorial for using a LiveCD environment to mount an installed system. After doing that, you can diagnose that system, install and/or make changes to it, as if it had booted... Just saying that you don't have to start over. But that is an option also. 

You could just use the LiveCD environment to copy what you need to an USB drive or USB storage, export a installed package list to help you install what you installed after vanilla, and just start fresh. Your decision. Your investment in time.

I learned long ago, from mistakes and heart break. Use snap shots and backups.

---

### Post by exsurgo-ankit on 2021-06-15
Hello MAFoElffen

Thank you for getting back to me. Yes I did take a snapshot but it is over a couple months old. That would be my last resort, if I can't recover this instance.
What I don't understand is how I could have overwritten the UI and affected the networking. I did try running some updates as I working on setting up some plugins for jenkins.

Is there a way to revert those installations?
I can work with the Debian GUI as well if the networking worked. Without networking this image will be useless to us. What can I try to get the networking to work?

I have tried mounting the local file system as per your suggestion but I can unable to run any apt-get commands. The live system is unable to resolve network addresses for packages.
I tried switching the user from root@ubuntu to my local admin@ubuntu. 
All my folders and data are intact.

I will provide an update if something works out. Please provide any suggestions to get the networking working.

---

### Post by MAFoElffen on 2021-06-15
First would be to re-establish the networking on that image while mounted to it (easiest)... While mounted to it, does it lose the networking again?

*** You never did answer if you knew if it was using NetPlan or Network Manager to render the the networking(?) ***
If so, then you coudld use the configured (mounted) network manager renderer to reconfigure your network settings... (hint)

Later, after a resolved network connection, then you could re-install the Desktop, which would correct anything there that got wacked. But before doing that, I would try to fix any errors on the system, disk errors, any broken packages, and such. Instructions for that later...

---

### Post by exsurgo-ankit on 2021-06-15
Hello MAFoElffen,

I am googling netplan so I can try your suggestion. Networking did not work when I mounted the local file system. No apt-get commands could resolve the host.

On Debian boot, the icon says Xubuntu. Did it somehow update to Xubuntu? I am not sure how I did that.
When is shows the login prompt, it momentarily shows the ubuntu background and switches to xfce background.
Logging in as other user (my admin) still shows xfce desktop with no networking.

Regards

---

### Post by MAFoElffen on 2021-06-15
Did you install any "alternate" desktops to your Ubuntu image? What "Graphical Login Manager" is it using now? 

If not GDM (the Ubuntu default) currently, then do:
```
sudo [FONT=var(--ff-mono)]dpkg-reconfigure gdm3[/FONT]
```
To set your default desktop environment back to Ubuntu, do:
```

sudo update-alternatives --config x-session-manager

```
* Curious to hear what desktops it says is there.

On 20.04, post the contents of /etc/netplan/01-<file_name>.yaml. that will show what the renderer is.

---

### Post by exsurgo-ankit on 2021-06-15
I did not install any alternate desktops. It is using xfce. I probably ran apt upgrade  before the power outage and that may have triggered this state.
It did not work. Here are the outputs

gdm3 is broken or not fully installed.

for the second command it says
no alternatives for x-session-manager

---

### Post by MAFoElffen on 2021-06-15
And yet, you still have not posted your *.yaml file... I can not help you restore your network settings until provide that information. And answer the network related questions I asked above. I am sorry, but I have asked for that multiple times.

You cannot fix it until, well... I am in the dark until you can provide some info. I'm waiting on you. I am patient.

---

### Post by exsurgo-ankit on 2021-06-15
[COLOR=#000000]Hello MAFoElffen,

Apologies for the misunderstanding. I am a noob when it comes to Linux. I did not setup any networking. The VM is bridged to the host PC's network adapter.
It just worked seamlessly. It still does with the live session from the install DVD.

There is a single file called 01-network-manager-all.yaml



it has 4 lines that look like this

[/COLOR][COLOR=#7D8B99][FONT=Consolas]# Let NetworkManager manage all devices on this system
[/FONT][/COLOR][COLOR=#1990B8][FONT=Consolas]network[/FONT][/COLOR][COLOR=#5F6364][FONT=Consolas]:
[/FONT][/COLOR][COLOR=#1990B8][FONT=Consolas]version[/FONT][/COLOR][COLOR=#5F6364][FONT=Consolas]:[/FONT][/COLOR][COLOR=#C92C2C][FONT=Consolas]2
[/FONT][/COLOR][COLOR=#1990B8][FONT=Consolas]renderer[/FONT][/COLOR][COLOR=#5F6364][FONT=Consolas]:[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] NetworkManager[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by MAFoElffen on 2021-06-15
I tell you what. I have just had an epiphany, that might save us some time and head aches. From what you are doing and what you said, [COLOR=#ff0000]there are a whole lot of  unanswered questions on what happened to your VM.
[/COLOR][COLOR=#000000]
Do not "tell" me the translated results of these. Cut and paste, then wrapped them within code or quote tags please
```
lsb_relelase -a
uname -r
sudo apt-cache show *-desktop

## Then create these two text files to attach to a post or put into a PasteBin
cat /var/log/apt/history.log | tail -n 100 >> ~/Documents/apt.log.txt
cat  /var/log/sys.log | grep -i "NetworkManager\|woopsie" >> ~/Documents/net.log.txt

```
Why, because something either miraculous or very devious happened to your VM that defies all realms of known reality. Somehow this image died, then reincarnated as something else.

[/COLOR]

---

### Post by exsurgo-ankit on 2021-06-15
i tried following this
[https://linuxconfig.org/netplan-network-configuration-tutorial-for-beginners](https://linuxconfig.org/netplan-network-configuration-tutorial-for-beginners)

to configure netplan and then tried
sudo netplan try

but there is not netplan package installed to try it

---

### Post by MAFoElffen on 2021-06-15
From what you posted... Iit is still using the GUI Network Manager as the renderer. Go through the Xfce menu's to find it. Configure for now in (settings > Network > "Connect Automatically" (DHCP). 

Then from a terminal:
```

sudo netplan generate
sudo netplan apply --debug

```

Tell me if your networking comes back up...

EDIT: Saw your last post... No NetPlan Installed??? But netplan is the default in Ubuntu since 18.04... See what I said about it resurrecting into something else?

Please post the results of post #11

---

### Post by MAFoElffen on 2021-06-15
If, for some reason, the first command (lsb_release) does not work, then do
```

sudo hostnamectl

```
That will show more information, and show for any recent branch of Linux, using systemd.

---

### Post by exsurgo-ankit on 2021-06-15
The requested info can be fetched from these links. 

apt.log.txt
[https://www.dropbox.com/s/d1qm5g5yw6j037s/apt.log.txt?dl=0](https://www.dropbox.com/s/d1qm5g5yw6j037s/apt.log.txt?dl=0)

apt_cache output
[https://www.dropbox.com/s/7rxt9hojx9hypsd/apt_cache.log.txt?dl=0](https://www.dropbox.com/s/7rxt9hojx9hypsd/apt_cache.log.txt?dl=0)

sys.log file was not found

```

admin@VM:~$ cat /var/log/sys.log | grep -i "NetworkManager\|woopsie" >> ~/Documents/net.log.txt
cat: /var/log/sys.log: No such file or directory
[FONT=Verdana]admin@VM[/FONT]x:~$ lsb_release -a
bash: lsb_release: command not found
[FONT=Verdana]admin@VM[/FONT]:~$ unanme -r
bash: unanme: command not found
[FONT=Verdana]admin@VM[/FONT]:~$ uname -r
5.8.0-53-generic

admin@VM:~$ sudo hostnamectl
[sudo] password for admin: 
   Static hostname: VM
         Icon name: computer-vm
           Chassis: vm
        Machine ID: 0dc2967f828f4ef8aa271d327086898c
           Boot ID: 9c1df06d9b8d4497962d5a43b500b823
    Virtualization: oracle
  Operating System: Ubuntu 20.04.2 LTS
            Kernel: Linux 5.8.0-53-generic
      Architecture: x86-64
```

---

### Post by MAFoElffen on 2021-06-15
You didn't post the new text files that were created into your home directory. 

** "uanme" was (your) typo. Should have been "uname". I went back and checked what I typed. It was correct. No matter the last hostnamectl command answered what I needed to know from that.


*** AND you did not answer me if, when you mount the system from a LiveCD Environment, if you still have networking!

---

### Post by exsurgo-ankit on 2021-06-15
When I mount the file system in LiveCD environment, I still have networking but I cannot access package vis apt-get command.

the clipboard in the VM just does not work even after enabling bidirectional sharing. So I have to generate the files in xfce mode, then boot into LiveCD and upload those file from the browser as that is the only time networking works.

the dropbox links contain apt.log.txt and output for "[COLOR=#000000][FONT=&quot]udo apt-cache show *-desktop"



[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-06-15
I think you need an alternate plan... You are 2 day into this... 

Two options. Each would start with a recovery plan.

Preamble:
1. Take a snap shot now...
2. Create a new, small virtual disk and attach it to your VM. Get into the LiveCD Environrment. Partition it and create an Ext4 filesystem.  While you are in the Disks app, note the path to mount the partition there. Mount it. Copy everything from your home, so you don't lose anything.
3. Generate an installed package list via this (but modify that to how you mounted it with the path)
[code]dpkg --get-selections >dev/sdb/backup/installed-software.log

Option #1:
Restore from your snapshot.

Option #2:
Install fresh. There are some sub-options here... 
  (a) You can either install here using your second disk as your new home, but select not to format it, so it just mounts it and uses whatever is there without destroying it. But if you do that wrong, it will. 
  (b) Or (safer), use instructions from almost anywhere to mount the second drive as your new home after the install is completed...

Post Recovery:
if you reverted your snapshot, restore your home directory form the second drive.

If you installed fresh. mount the second drive as your home.

Install any programs not there from your installed package list.

---

### Post by exsurgo-ankit on 2021-06-16
Thank you for your support MAFoElffen.

I reverted to an old backup of VM and setup my software again. It was all done in a couple of hours and definitely faster than the troubleshooting we did in the last couple of days.

---

