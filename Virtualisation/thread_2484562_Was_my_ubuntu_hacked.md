---
title: "Was my ubuntu hacked??"
date: 2023-03-03
forum: Virtualisation
---

### Post by yigal2 on 2023-03-03
I am running Ubuntu 22.04.2 on a virtual machine above Windows 10.
Lately I noticed twice that the "share" option of the settings was opened when I re-logged in, yet I am sure I didn't open that window earlier.

Could it be I was hacked?
How can I check that?

---

### Post by ajgreeny on 2023-03-03
We  need much more information to be able to help you properly. 

Is this a desktop version of Ubuntu or a server and which VM hypervisor are you using? I'm not sure what options are available with Windows as host system but other users will know more than I do so give all the detail you can.

---

### Post by yigal2 on 2023-03-03
Ubuntu desktop.
VM is VirtualBox.

---

### Post by ajgreeny on 2023-03-03
And what is this "share" option in the settings?

Do you mean the shared folder in the VM settings itself, and if so where do you see that it is open, or is it in the Virtualbox settings window, or something in the Windows host?

I know almost nothing now about running Windows having stopped using Windows-XP almost 17 years ago and not really used it since.

---

### Post by ajgreeny on 2023-03-03
Thread moved to **Virtualisation** as it is a better fit here.

---

### Post by MAFoElffen on 2023-03-03
The only "shared" option I know of in VritualBox Setting is for "Shared Folders." This is so you can share data between the Host and VM.

That would not be a security "hacked" kind of thing and had nothing to do with sharing the VM with anyone, as thinking they were hacked. That is trivial.

Much more info is needed to explain what was going on, and what the User found.

---

### Post by yigal2 on 2023-03-03
About "share" - while in Ubuntu OS (not in the VM control):
In setting program (looks like tooth wheel), there is an "sharing" option.
This sharing option has main "ON/OFF" option on top (it is off by default).
There are also two grayed options (grayed because it is OFF) - one for remote desktop, and one for Media sharing.

This is the "share" window that was opened when I logged in.
I didn't open it when I logged out last time.

---

### Post by ian-weisser on 2023-03-03
"Hacked", meaning unauthorized access and control *by somebody unknown to you*, seems very unlikely.

Somebody competent enough to remotely access your VM could get your files many other (and easier) ways than by enabling File Sharing in the GUI.

It's also unlikely that a hacker could be so competent as to tracelessly invade and control your system, yet so incompetent as to leave obvious, visible settings mis-set and windows open.

"Hacked," meaning unauthorized access by somebody KNOWN to you seems more likely. Since they seemingly made no attempt to hide their access, perhaps they do not consider it unauthorized. Ask around among your peers who have access to your hardware.

---

### Post by yigal2 on 2023-03-03
I tend to agree that is it unlikely someone from the outside took control over my Ubuntu VM.
So I ignored it the first time. 
But now it happened again.

There is no one at my home that could access it either, so it must be from the outside.
(unless my dog is very smart, which is clearly not true :) )

What can I do to monitor or protect? 
I use ubuntu out of the box after install.

---

### Post by ian-weisser on 2023-03-03
> **yigal2 said:**
> 
I use ubuntu out of the box after install.

That cannot be true. VirtualBox is not included with a stock install of Ubuntu.

Therefore, you have changed the system in ways that you have not disclosed. One of those ways might be important. But disclosure is up to you; speculation is pointless.

> **yigal2 said:**
> 
What can I do to monitor or protect? 

Depends upon the value to you of what's on your VM Guest and of the VM Host.

You seem to be saying that you have identified a probable (according to you) compromise that has already occurred. Since you don't know how they got in, and you did not identify the inevitable backdoors they installed to keep getting in, the typical solution is to wipe-and-reinstall your entire system so you KNOW it's clean. One hopes you have clean backups of your data and VMs, because only a fool would keep the compromised stuff.

But, again, that identification of a compromise comes from YOU. And we don't have the full story about what's going on.

---

### Post by yigal2 on 2023-03-03
> **ian-weisser said:**
> That cannot be true. VirtualBox is not included with a stock install of Ubuntu.
Therefore, you have changed the system in ways that you have not disclosed. One of those ways might be important. But disclosure is up to you; speculation is pointless.


The host of the VM is Windows 10 machine.
The Ubuntu desktop is out of the box install. 
Why this can't be true?

---

### Post by ian-weisser on 2023-03-03
Well, you are right about the Virtuabox part, of course. Cheerfully withdrawn.

However, a stock install of Ubuntu Desktop (since you have windows that open) from a normal install .iso doesn't have any exploitable listening services. It doesn't have an ssh server installed. It doesn't have any users created. The root user doesn't have a password. There's nothing for an attacker to connect to. It's the services you add, and the way you configure those services, that might open vulnerabilities.

Your Windows 10 machine is more vulnerable. But that's not a topic for here.

---

### Post by ajgreeny on 2023-03-03
I am still confused and would like to be able to see what you are seeing so please take a screenshot, with camera if necessary, but preferably with the Print-Screen keyboard key (does that work in Windows: I've no idea) then attach the saved screenshot with the paperclip icon in the ***Reply to Thread*** window toolbar.

---

### Post by yigal2 on 2023-03-03
> **ian-weisser said:**
> However, a stock install of Ubuntu Desktop (since you have windows that open) from a normal install .iso doesn't have any exploitable listening services. It doesn't have an ssh server installed. It doesn't have any users created. The root user doesn't have a password. There's nothing for an attacker to connect to. It's the services you add, and the way you configure those services, that might open vulnerabilities.
.
The installation was from the regular ISO, there is a user name and password when I login (auto lock exists, so it is locked automatically if I leave the Ubuntu VM an attended). 
I never tested ssh.

Perhaps the best thing to do now is to follow the /var/log/auth.log and compare it to my logins (I started to write it down).

---

### Post by monkeybrain20122 on 2023-03-03
If it was hacked it would be the Windows host that was hacked because you can't change your VM settings from the guest.

---

### Post by DuckHook on 2023-03-03
> **yigal2 said:**
> …(unless my dog is very smart, which is clearly not true :) )
Hey, let's not sell them short: I know many cases of dogs being smarter than their owners. :lolflag: But I digress.
> What can I do to monitor or protect?
I agree with other posters in thinking that the cause of this is probably innocuous. However, it is a good habit to remain vigilant so I think you did the right thing seeking out advice.

It appears that you come from a Windows background. Windows does a lot of really reckless things by default, thus conditioning their users to bad habits. It's not the users' fault because Windows doesn't leave them any choice but to do things recklessly.

One of these reckless habits is to use RDP to access remote machines. Did you activate some sort of RDP app in Ubuntu? Something like Remmina or similar? If so, then it is possible that such an app would override your system settings to always allow remote desktop access.

This might also happen if you enable remote desktop inside some VBox setting. I haven't used VBox for years so this is just a wild guess. But it is something to check out.

Whenever you have concerns about questionable access, the first thing to do is to check your logs, especially auth.log. Always. I'm not going to mince words—log checking is arcane and a pain, but there is no better methodology.
> **monkeybrain20122 said:**
> …you can't change your VM settings from the guest.
It's very hard to do, but it can be done. VMWare has had to patch a couple of zero&#8209;day exploits that did exactly this. I don't recall out of hand if VBox had the same holes.

---

### Post by yigal2 on 2023-03-04
> **monkeybrain20122 said:**
> If it was hacked it would be the Windows host that was hacked because you can't change your VM settings from the guest.
Can you please explain while you refer to changing VM setting?

I would think that if there was a hacker (just assume), he would somehow remotely  login into my VM machine, the sme way he would remotly login into any other computer.
Why is the focus here on the VM, and not on the Ubuntu machine?
Does it matter if I run Ubuntu on a VM or on a real separated hardware?

---

### Post by DuckHook on 2023-03-04
> **yigal2 said:**
> Can you please explain while you refer to changing VM setting?
This arose from an initial misunderstanding. Many forum members thought that the "shares" that you were referring to was filesharing between VM and host, which is a setting that can only be set in VBox itself. Your problem is actually the sharing option in the general computer settings of Ubuntu. This has now been clarified.
> I would think that if there was a hacker (just assume), he would somehow remotely  login into my VM machine, the sme way he would remotly login into any other computer.
This is true. In fact, it is the reason that VMs are used as sandboxes. If a hacker compromises your VM OS, your host OS is still protected. However, Ubuntu has no ports open by default. Moreover, depending on how you set up networking in VBox, you should have firewall safeguards there as well, so it becomes even more challenging for some bad guy to penetrate your Ubuntu installation.
> Why is the focus here on the VM, and not on the Ubuntu machine?
The relationship between a VM and its platform is a complicated one. I have already mentioned that although it is very difficult to do, it is possible for a VM to penetrate its sandbox to compromise its VM platform and then its host. However, this is not really something to worry about in the real world. If we eliminate the VM platform as a possibility, then the focus can be concentrated on the Ubuntu machine.

[LIST=1]
[*]I have asked whether you have enabled some RDP setting in VBox. Such a setting may force Ubuntu into enabling "share" mode.
[*]I also asked if you have ever used some form of RDP within Ubuntu itself. This could also force the "share" setting.
[*]Lastly, I asked about your auth.log entries. Does anything there look wrong to you?
[/LIST]
Please answer the above questions for us to help you.
> Does it matter if I run Ubuntu on a VM or on a real separated hardware?
There is always some difference between a VM and bare metal, but with respect to your problem, I don't think those differences would matter.

The issue of security is a deep dive into very complex and arcane underwater caves. Software issues do arise, but our experience has shown that it is usually human causes that compromise security. For example, what sites have you visited in your Ubuntu VM? What third party repos/PPAs have you installed? What additional apps, utilities, services, customizations have you added? etc. There are a thousand questions and endless ways for things to go wrong.

Since you have Ubuntu installed in a VM, hopefully you have a snapshot from your initial install. At worst, backup your important data outside the VM, then restore Ubuntu to its initial state. See if "shares" is still on.

It is also worth it to install a fresh version of Ubuntu to a second VM and see what "shares" looks like there. Make sure you use a proper official ISO from Canonical's website. Checksum the download to make sure it hasn't been tampered with. Then, install it choosing standard defaults. Don't use unusual configurations or options.

Given that you use Ubuntu in a VM, it may not be worth your time trying to chase this problem down unless you are doing so for self education. It is so easy to restore snapshots, clone another instance or just install again from scratch. That's the beauty of VMs. So it is your choice whether it makes any sense to play detective on this issue.

---

### Post by DuckHook on 2023-03-04
A friend posted the following in another thread: [https://ubuntuforums.org/showthread.php?t=2484613&p=14133490#post14133490](https://ubuntuforums.org/showthread.php?t=2484613&p=14133490#post14133490)
For completeness, I quote it in its entirety:> **1fallen said:**
> From a previous bug:
```
sudo unlink /etc/systemd/user/gnome-session.target.wants/gnome-remote-desktop.service
```

Now when enabling/disabling the remote desktop service a symlink is instead created/removed at

```
~/.config/systemd/user/gnome-session.target.wants/gnome-remote-desktop.service
```

and as such the user's on/off preference is respected.
Will the OP confirm?
[LIST=1]
[*]Please post results of:```
ls -laH /etc/systemd/user/gnome-session.target.wants/
```
[*]If you see:```
gnome-remote-desktop.service
```…then do:```
sudo unlink /etc/systemd/user/gnome-session.target.wants/gnome-remote-desktop.service
```
[*]You should now be able to turn off "shares" in Ubuntu settings.
[/LIST]

---

### Post by #&amp;thj^% on 2023-03-04
Nice, Thanks DuckHook

---

### Post by yigal2 on 2023-03-05
> **DuckHook said:**
> 

[LIST=1]
[*]I have asked whether you have enabled some RDP setting in VBox. Such a setting may force Ubuntu into enabling "share" mode.
[*]I also asked if you have ever used some form of RDP within Ubuntu itself. This could also force the "share" setting.
[*]Lastly, I asked about your auth.log entries. Does anything there look wrong to you?
[/LIST]
Please answer the above questions for us to help you.

As for the RDP: no. I never opened RDP, nor used it. I only access the VM directly from the host.
As for auth.log: I will be there physically later and I will report it. I wrote every access (start and end) lately. I will compare it to the auth.log.
However, there are als0 daemon accesses there, which I don't know how to judge if they make sense or not.

---

### Post by #&amp;thj^% on 2023-03-05
> **yigal2 said:**
> As for the RDP: no. I never opened RDP, nor used it. I only access the VM directly from the host.

The point is it's enabled by default, and it shouldn't be without notifying the user first.

---

### Post by DuckHook on 2023-03-05
> **yigal2 said:**
> As for the RDP: no. I never opened RDP, nor used it. I only access the VM directly from the host.
As for auth.log: I will be there physically later and I will report it. I wrote every access (start and end) lately. I will compare it to the auth.log.
However, there are als0 daemon accesses there, which I don't know how to judge if they make sense or not.
Please follow instructions in post #19.

---

### Post by maglin2 on 2023-03-06
It is noted here [https://askubuntu.com/questions/1407444/ubuntu-22-04-remote-desktop-headless](https://askubuntu.com/questions/1407444/ubuntu-22-04-remote-desktop-headless)
that disabling Remote Desktop does not have any effect after installing xrdp . After a reboot the Remote Desktop setting reverts to enabled.
Not likely to be relevant here, but you never know.

---

### Post by yigal2 on 2023-03-20
After some observations, the setting shared page of the Linux virtual machine (not the windows host) was opened again while I was gone.
It was with OFF set.

Here is the auth.log file. To me it looks ok, except for some pam_unix which I assume are daemons. The unlock keyring is aligned with mu access
Does it look reasonable?

```

Mar 19 00:17:01 ubu-VirtualBox CRON[91003]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 00:17:01 ubu-VirtualBox CRON[91003]: pam_unix(cron:session): session closed for user root
Mar 19 01:17:01 ubu-VirtualBox CRON[91604]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 01:17:01 ubu-VirtualBox CRON[91604]: pam_unix(cron:session): session closed for user root
Mar 19 02:17:01 ubu-VirtualBox CRON[92186]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 02:17:01 ubu-VirtualBox CRON[92186]: pam_unix(cron:session): session closed for user root
Mar 19 03:10:01 ubu-VirtualBox CRON[92764]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 03:10:01 ubu-VirtualBox CRON[92764]: pam_unix(cron:session): session closed for user root
Mar 19 03:17:01 ubu-VirtualBox CRON[92801]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 03:17:01 ubu-VirtualBox CRON[92801]: pam_unix(cron:session): session closed for user root
Mar 19 03:30:01 ubu-VirtualBox CRON[92979]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 03:30:01 ubu-VirtualBox CRON[92979]: pam_unix(cron:session): session closed for user root
Mar 19 04:17:01 ubu-VirtualBox CRON[93396]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 04:17:01 ubu-VirtualBox CRON[93396]: pam_unix(cron:session): session closed for user root
Mar 19 05:17:01 ubu-VirtualBox CRON[93991]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 05:17:01 ubu-VirtualBox CRON[93991]: pam_unix(cron:session): session closed for user root
Mar 19 06:12:34 ubu-VirtualBox PackageKit: uid 1000 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
Mar 19 06:12:34 ubu-VirtualBox PackageKit: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
Mar 19 06:15:23 ubu-VirtualBox pkexec: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Mar 19 06:15:23 ubu-VirtualBox pkexec[95093]: ubu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar 19 06:17:01 ubu-VirtualBox CRON[95106]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 06:17:01 ubu-VirtualBox CRON[95106]: pam_unix(cron:session): session closed for user root
Mar 19 06:25:01 ubu-VirtualBox CRON[95270]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 06:25:01 ubu-VirtualBox CRON[95270]: pam_unix(cron:session): session closed for user root
Mar 19 06:43:03 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 19 06:47:01 ubu-VirtualBox CRON[95737]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 06:47:01 ubu-VirtualBox CRON[95737]: pam_unix(cron:session): session closed for user root
Mar 19 07:17:01 ubu-VirtualBox CRON[96976]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 07:17:01 ubu-VirtualBox CRON[96976]: pam_unix(cron:session): session closed for user root
Mar 19 07:30:01 ubu-VirtualBox CRON[97148]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 07:30:01 ubu-VirtualBox CRON[97148]: pam_unix(cron:session): session closed for user root
Mar 19 07:33:21 ubu-VirtualBox pkexec: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Mar 19 07:33:21 ubu-VirtualBox pkexec[97673]: ubu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar 19 08:17:01 ubu-VirtualBox CRON[98144]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 08:17:01 ubu-VirtualBox CRON[98144]: pam_unix(cron:session): session closed for user root
Mar 19 08:30:01 ubu-VirtualBox CRON[98344]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 08:30:01 ubu-VirtualBox CRON[98344]: pam_unix(cron:session): session closed for user root
Mar 19 08:30:03 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 19 08:55:14 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 19 09:17:01 ubu-VirtualBox CRON[100475]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 09:17:01 ubu-VirtualBox CRON[100475]: pam_unix(cron:session): session closed for user root
Mar 19 09:30:01 ubu-VirtualBox CRON[101256]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 09:30:01 ubu-VirtualBox CRON[101256]: pam_unix(cron:session): session closed for user root
Mar 19 10:17:01 ubu-VirtualBox CRON[103423]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 10:17:01 ubu-VirtualBox CRON[103423]: pam_unix(cron:session): session closed for user root
Mar 19 10:30:01 ubu-VirtualBox CRON[104271]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 10:30:01 ubu-VirtualBox CRON[104271]: pam_unix(cron:session): session closed for user root
Mar 19 11:17:01 ubu-VirtualBox CRON[104711]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 11:17:01 ubu-VirtualBox CRON[104711]: pam_unix(cron:session): session closed for user root
Mar 19 11:30:01 ubu-VirtualBox CRON[104897]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 11:30:01 ubu-VirtualBox CRON[104897]: pam_unix(cron:session): session closed for user root
Mar 19 12:17:01 ubu-VirtualBox CRON[105330]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 12:17:01 ubu-VirtualBox CRON[105330]: pam_unix(cron:session): session closed for user root
Mar 19 12:30:02 ubu-VirtualBox CRON[105518]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 12:30:02 ubu-VirtualBox CRON[105518]: pam_unix(cron:session): session closed for user root
Mar 19 13:17:01 ubu-VirtualBox CRON[105909]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 13:17:01 ubu-VirtualBox CRON[105909]: pam_unix(cron:session): session closed for user root
Mar 19 13:30:01 ubu-VirtualBox CRON[106081]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 13:30:01 ubu-VirtualBox CRON[106081]: pam_unix(cron:session): session closed for user root
Mar 19 14:17:01 ubu-VirtualBox CRON[106488]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 14:17:01 ubu-VirtualBox CRON[106488]: pam_unix(cron:session): session closed for user root
Mar 19 14:30:01 ubu-VirtualBox CRON[106674]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 14:30:01 ubu-VirtualBox CRON[106674]: pam_unix(cron:session): session closed for user root
Mar 19 15:17:01 ubu-VirtualBox CRON[107280]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 15:17:01 ubu-VirtualBox CRON[107280]: pam_unix(cron:session): session closed for user root
Mar 19 15:30:01 ubu-VirtualBox CRON[107499]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 15:30:01 ubu-VirtualBox CRON[107499]: pam_unix(cron:session): session closed for user root
Mar 19 16:17:01 ubu-VirtualBox CRON[107959]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 16:17:01 ubu-VirtualBox CRON[107959]: pam_unix(cron:session): session closed for user root
Mar 19 16:30:01 ubu-VirtualBox CRON[108135]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 16:30:01 ubu-VirtualBox CRON[108135]: pam_unix(cron:session): session closed for user root
Mar 19 17:17:01 ubu-VirtualBox CRON[108524]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 17:17:01 ubu-VirtualBox CRON[108524]: pam_unix(cron:session): session closed for user root
Mar 19 17:26:38 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 19 17:30:01 ubu-VirtualBox CRON[108763]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 17:30:01 ubu-VirtualBox CRON[108763]: pam_unix(cron:session): session closed for user root
Mar 19 18:17:01 ubu-VirtualBox CRON[109149]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 18:17:01 ubu-VirtualBox CRON[109149]: pam_unix(cron:session): session closed for user root
Mar 19 18:30:01 ubu-VirtualBox CRON[109324]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 18:30:01 ubu-VirtualBox CRON[109324]: pam_unix(cron:session): session closed for user root
Mar 19 19:16:17 ubu-VirtualBox gnome-keyring-daemon[1230]: asked to register item /org/freedesktop/secrets/collection/login/7, but it's already registered
Mar 19 19:16:42 ubu-VirtualBox dbus-daemon[672]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Mar 19 19:17:01 ubu-VirtualBox CRON[109885]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 19:17:01 ubu-VirtualBox CRON[109885]: pam_unix(cron:session): session closed for user root
Mar 19 19:30:01 ubu-VirtualBox CRON[110393]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 19:30:01 ubu-VirtualBox CRON[110393]: pam_unix(cron:session): session closed for user root
Mar 19 20:17:01 ubu-VirtualBox CRON[111082]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 20:17:01 ubu-VirtualBox CRON[111082]: pam_unix(cron:session): session closed for user root
Mar 19 20:30:01 ubu-VirtualBox CRON[111253]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 20:30:01 ubu-VirtualBox CRON[111253]: pam_unix(cron:session): session closed for user root
Mar 19 20:43:23 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 19 21:17:01 ubu-VirtualBox CRON[113075]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 21:17:01 ubu-VirtualBox CRON[113075]: pam_unix(cron:session): session closed for user root
Mar 19 21:30:01 ubu-VirtualBox CRON[113609]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 21:30:01 ubu-VirtualBox CRON[113609]: pam_unix(cron:session): session closed for user root
Mar 19 22:17:01 ubu-VirtualBox CRON[115373]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 22:17:01 ubu-VirtualBox CRON[115373]: pam_unix(cron:session): session closed for user root
Mar 19 22:30:01 ubu-VirtualBox CRON[115551]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 22:30:01 ubu-VirtualBox CRON[115551]: pam_unix(cron:session): session closed for user root
Mar 19 23:17:01 ubu-VirtualBox CRON[116009]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 23:17:01 ubu-VirtualBox CRON[116009]: pam_unix(cron:session): session closed for user root
Mar 19 23:30:01 ubu-VirtualBox CRON[116196]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 19 23:30:01 ubu-VirtualBox CRON[116196]: pam_unix(cron:session): session closed for user root
Mar 20 00:17:01 ubu-VirtualBox CRON[116675]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 00:17:01 ubu-VirtualBox CRON[116675]: pam_unix(cron:session): session closed for user root
Mar 20 01:17:01 ubu-VirtualBox CRON[117332]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 01:17:01 ubu-VirtualBox CRON[117332]: pam_unix(cron:session): session closed for user root
Mar 20 02:17:01 ubu-VirtualBox CRON[117927]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 02:17:01 ubu-VirtualBox CRON[117927]: pam_unix(cron:session): session closed for user root
Mar 20 03:10:01 ubu-VirtualBox CRON[118533]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 03:10:01 ubu-VirtualBox CRON[118533]: pam_unix(cron:session): session closed for user root
Mar 20 03:17:01 ubu-VirtualBox CRON[118556]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 03:17:01 ubu-VirtualBox CRON[118556]: pam_unix(cron:session): session closed for user root
Mar 20 04:17:01 ubu-VirtualBox CRON[119161]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 04:17:01 ubu-VirtualBox CRON[119161]: pam_unix(cron:session): session closed for user root
Mar 20 05:17:01 ubu-VirtualBox CRON[119758]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 05:17:01 ubu-VirtualBox CRON[119758]: pam_unix(cron:session): session closed for user root
Mar 20 06:12:34 ubu-VirtualBox PackageKit: uid 1000 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
Mar 20 06:12:34 ubu-VirtualBox PackageKit: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
Mar 20 06:15:23 ubu-VirtualBox pkexec: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Mar 20 06:15:23 ubu-VirtualBox pkexec[120905]: ubu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar 20 06:17:01 ubu-VirtualBox CRON[120916]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 06:17:01 ubu-VirtualBox CRON[120916]: pam_unix(cron:session): session closed for user root
Mar 20 06:25:01 ubu-VirtualBox CRON[121074]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 06:25:01 ubu-VirtualBox CRON[121074]: pam_unix(cron:session): session closed for user root
Mar 20 06:42:18 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 20 07:17:01 ubu-VirtualBox CRON[122951]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 07:17:01 ubu-VirtualBox CRON[122951]: pam_unix(cron:session): session closed for user root
Mar 20 07:30:02 ubu-VirtualBox CRON[123141]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 07:30:02 ubu-VirtualBox CRON[123141]: pam_unix(cron:session): session closed for user root
Mar 20 08:17:01 ubu-VirtualBox CRON[123605]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 08:17:01 ubu-VirtualBox CRON[123605]: pam_unix(cron:session): session closed for user root
Mar 20 08:30:01 ubu-VirtualBox CRON[123779]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 08:30:01 ubu-VirtualBox CRON[123779]: pam_unix(cron:session): session closed for user root
Mar 20 09:17:01 ubu-VirtualBox CRON[124240]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 09:17:01 ubu-VirtualBox CRON[124240]: pam_unix(cron:session): session closed for user root
Mar 20 09:30:01 ubu-VirtualBox CRON[124428]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 09:30:01 ubu-VirtualBox CRON[124428]: pam_unix(cron:session): session closed for user root
Mar 20 10:17:01 ubu-VirtualBox CRON[124838]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 10:17:01 ubu-VirtualBox CRON[124838]: pam_unix(cron:session): session closed for user root
Mar 20 10:30:01 ubu-VirtualBox CRON[125016]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 10:30:01 ubu-VirtualBox CRON[125016]: pam_unix(cron:session): session closed for user root
Mar 20 11:17:01 ubu-VirtualBox CRON[125462]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 11:17:01 ubu-VirtualBox CRON[125462]: pam_unix(cron:session): session closed for user root
Mar 20 11:30:01 ubu-VirtualBox CRON[125648]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 11:30:01 ubu-VirtualBox CRON[125648]: pam_unix(cron:session): session closed for user root
Mar 20 12:17:01 ubu-VirtualBox CRON[126071]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 12:17:01 ubu-VirtualBox CRON[126071]: pam_unix(cron:session): session closed for user root
Mar 20 12:30:01 ubu-VirtualBox CRON[126279]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 12:30:01 ubu-VirtualBox CRON[126279]: pam_unix(cron:session): session closed for user root
Mar 20 13:17:01 ubu-VirtualBox CRON[126688]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 13:17:01 ubu-VirtualBox CRON[126688]: pam_unix(cron:session): session closed for user root
Mar 20 13:30:01 ubu-VirtualBox CRON[126881]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 13:30:01 ubu-VirtualBox CRON[126881]: pam_unix(cron:session): session closed for user root
Mar 20 14:17:01 ubu-VirtualBox CRON[127335]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 14:17:01 ubu-VirtualBox CRON[127335]: pam_unix(cron:session): session closed for user root
Mar 20 14:30:01 ubu-VirtualBox CRON[127517]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 14:30:01 ubu-VirtualBox CRON[127517]: pam_unix(cron:session): session closed for user root
Mar 20 15:17:01 ubu-VirtualBox CRON[127957]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 15:17:01 ubu-VirtualBox CRON[127957]: pam_unix(cron:session): session closed for user root
Mar 20 15:30:01 ubu-VirtualBox CRON[128127]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 15:30:01 ubu-VirtualBox CRON[128127]: pam_unix(cron:session): session closed for user root
Mar 20 16:17:01 ubu-VirtualBox CRON[128528]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 16:17:01 ubu-VirtualBox CRON[128528]: pam_unix(cron:session): session closed for user root
Mar 20 16:30:01 ubu-VirtualBox CRON[128708]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 16:30:01 ubu-VirtualBox CRON[128708]: pam_unix(cron:session): session closed for user root
Mar 20 17:17:01 ubu-VirtualBox CRON[129112]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 17:17:01 ubu-VirtualBox CRON[129112]: pam_unix(cron:session): session closed for user root
Mar 20 17:30:01 ubu-VirtualBox CRON[129888]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 17:30:01 ubu-VirtualBox CRON[129888]: pam_unix(cron:session): session closed for user root
Mar 20 17:30:21 ubu-VirtualBox pkexec: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Mar 20 17:30:21 ubu-VirtualBox pkexec[129901]: ubu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubu] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar 20 18:17:01 ubu-VirtualBox CRON[130301]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 18:17:01 ubu-VirtualBox CRON[130301]: pam_unix(cron:session): session closed for user root
Mar 20 18:30:01 ubu-VirtualBox CRON[130475]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 18:30:01 ubu-VirtualBox CRON[130475]: pam_unix(cron:session): session closed for user root
Mar 20 19:17:01 ubu-VirtualBox CRON[130938]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 19:17:01 ubu-VirtualBox CRON[130938]: pam_unix(cron:session): session closed for user root
Mar 20 19:17:58 ubu-VirtualBox gdm-password]: pam_unix(gdm-password:auth): authentication failure; logname= uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=ubu
Mar 20 19:18:02 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 20 19:30:01 ubu-VirtualBox CRON[131493]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 19:30:01 ubu-VirtualBox CRON[131493]: pam_unix(cron:session): session closed for user root
Mar 20 20:17:01 ubu-VirtualBox CRON[132833]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 20:17:01 ubu-VirtualBox CRON[132833]: pam_unix(cron:session): session closed for user root
Mar 20 20:30:01 ubu-VirtualBox CRON[133381]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Mar 20 20:30:01 ubu-VirtualBox CRON[133381]: pam_unix(cron:session): session closed for user root
Mar 20 21:02:14 ubu-VirtualBox gdm-password]: pam_unix(gdm-password:auth): authentication failure; logname= uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=ubu
Mar 20 21:02:23 ubu-VirtualBox gdm-password]: gkr-pam: unlocked login keyring
Mar 20 21:03:25 ubu-VirtualBox polkitd(authority=local): Operator of unix-session:1 successfully authenticated as unix-user:ubu to gain TEMPORARY authorization for action org.gtk.vfs.file-operations-helper for unix-process:134118:48554044 [/bin/sh -c pkexec /usr/libexec/gvfsd-admin "$@" --address $DBUS_SESSION_BUS_ADDRESS --dir $XDG_RUNTIME_DIR gvfsd-admin --spawner :1.5 /org/gtk/gvfs/exec_spaw/6] (owned by unix-user:ubu)
Mar 20 21:03:25 ubu-VirtualBox pkexec: pam_unix(polkit-1:session): session opened for user root(uid=0) by (uid=1000)
Mar 20 21:03:25 ubu-VirtualBox pkexec[134119]: ubu: Executing command [USER=root] [TTY=unknown] [CWD=/home/ubu] [COMMAND=/usr/libexec/gvfsd-admin --spawner :1.5 /org/gtk/gvfs/exec_spaw/6 --address unix:path=/run/user/1000/bus --dir /run/user/1000]
Mar 20 21:03:31 ubu-VirtualBox polkit-agent-helper-1[134137]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=ubu rhost=  user=ubu
Mar 20 21:03:40 ubu-VirtualBox polkitd(authority=local): Operator of unix-session:1 successfully authenticated as unix-user:ubu to gain TEMPORARY authorization for action org.gtk.vfs.file-operations for unix-process:133514:48389063 [/usr/bin/nautilus --gapplication-service] (owned by unix-user:ubu)



```

---

