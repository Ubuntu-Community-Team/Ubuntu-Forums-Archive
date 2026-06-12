---
title: "UBUNTU 22: Security Issues AFTER new INSTALLATION install  ( rkhunter chkrootkit ) ++"
date: 2023-10-08
forum: Security
---

### Post by whysohard2 on 2023-10-08
lets keep this thread for Ubuntu 22 security concerns after a new installation only 
after a new install from U 18 to U20 to U22, now on U22, encountered some concerns likely false positives: check these out then share your own on this thread: 


rkhunter   OR     chkrookit        flagged the following 

[email]root@roots-computer:/etc/.java[/email]$ 
./.systemPrefs
./.systemPrefs/.system.lock
./.systemPrefs/.systemRootModFile


rkhunter     Checking for prerequisites                               [ Warning ]
/usr/bin/lwp-request                                     [ Warning ]
Checking for hidden files and directories                [ Warning ]
Checking for passwd file changes                         [ Warning ]
Checking for group file changes                          [ Warning ]
File properties checks...
    Required commands ---check failed
    Files checked: 144
    Suspect files: 1
    
Info: Disabled tests are: suspscan hidden_ports hidden_procs deleted_files packet_cap_apps apps
Info: Using syslog for some logging - facility/priority level is 'authpriv.warning'.
Info: Found the 'logger' command: /usr/bin/logger
Warning: User 'systemd-timesync' has been added to the passwd file.
Warning: User 'tss' has been added to the passwd file.
Warning: User 'tcpdump' has been added to the passwd file.
Warning: User 'fwupd-refresh' has been added to the passwd file.
Warning: User 'systemd-coredump' has been added to the passwd file.
Warning: User 'snapd-range-524288-root' has been added to the passwd file.
Warning: User 'snap_daemon' has been added to the passwd file.
Warning: User 'debian-tor' has been added to the passwd file.
 


Suspicious 	
/usr/lib/modules/5.4.0-163-generic/vdso/.build-id
/usr/lib/modules/5.15.0-84-generic/vdso/.build-id
/usr/lib/debug/.build-id
/usr/lib/ruby/vendor_ruby/rubygems/optparse/.document
/usr/lib/ruby/vendor_ruby/rubygems/ssl_certs/.document
/usr/lib/ruby/vendor_ruby/rubygems/tsort/.document
/usr/lib/ruby/gems/3.0.0/gems/minitest-5.14.2/.autotest
/usr/lib/ruby/gems/3.0.0/gems/rbs-1.0.4/.rubocop.yml
/usr/lib/ruby/gems/3.0.0/gems/power_assert-1.2.0/.travis.yml
/usr/lib/libreoffice/share/.registry



Not happy to see a new installation being flagged so many times unless there was DNS poisening , similar altering besides many apps no longer be active like Falkon. plus an extended boot time exactly 1 minute and 45 seconds from power on to desktop using an encrypted HD.  plus software downloader app doesnt show installed software 

Suggestions: 
1- Some kind of restore point
2- Easy terminal command to verify U22 OS is secure matches Main Server besides multiple signature/hash checks etc .
3-easy list of apps compatible w/ U22

---

### Post by TheFu on 2023-10-09
> rkhunter OR chkrookit flagged the following 
are both more trouble than they are worth. The false positives make them less than useful.

Also, there are 2 Ubuntu releases yearly, so U22 isn't sufficient to say a specific version. Use the **lsb_release -d** command so see the exact version.

Nobody here works for Canonical. We are just other users, like you.  Suggestions here will never reach Canonical.  The way to get Canonical to look at anything is to file a bug report through **Landscape**.

> Not happy to see a new installation being flagged so many times unless there was DNS poisening , similar altering besides many apps no longer be active like Falkon. plus an extended boot time exactly 1 minute and 45 seconds from power on to desktop using an encrypted HD. plus software downloader app doesnt show installed software
Do you realize that Canonical isn't responsible for every package installed?  There are tens of thousands of different teams producing libraries and software.  Canonical is like a sheep rancher without any dogs to help AND a cat herder without any fences.  That's the nature of the Linux ecosystems.  There's a little, but famous, book that tries to explain the concept: [https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar)  Linux is a bazaar, if that isn't clear.

As for slow booting, that is highly dependent on the applications, settings and hardware.  I'll post the times for 3 different systems here:
[SIZE=4]A[/SIZE]
```
$ systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

[B]graphical.target @13.097s
[/B]&#9492;&#9472;multi-user.target @13.097s
  &#9492;&#9472;getty.target @12.206s
    &#9492;&#9472;getty@tty1.service @12.205s
      &#9492;&#9472;system-getty.slice @12.205s
        &#9492;&#9472;setvtrgb.service @12.203s +1ms
          &#9492;&#9472;systemd-user-sessions.service @12.197s +2ms
            &#9492;&#9472;cloud-config.service @11.898s +297ms
              &#9492;&#9472;snapd.seeded.service @11.849s +48ms
                &#9492;&#9472;snapd.service @6.046s +5.801s
                  &#9492;&#9472;basic.target @5.990s
                    &#9492;&#9472;sockets.target @5.989s
                      &#9492;&#9472;libvirtd-ro.socket @5.988s
                        &#9492;&#9472;libvirtd.socket @5.975s +9ms
                          &#9492;&#9472;sysinit.target @5.966s
                            &#9492;&#9472;systemd-sysctl.service @6.153s +3ms
                              &#9492;&#9472;systemd-modules-load.service @415ms +34ms
                                &#9492;&#9472;systemd-journald.socket @363ms
                                  &#9492;&#9472;-.mount @319ms
                                    &#9492;&#9472;system.slice @319ms
                                      &#9492;&#9472;-.slice @319ms
```
[SIZE=4]B[/SIZE]
```
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

[B]graphical.target @4min 57.347s
[/B]&#9492;&#9472;multi-user.target @4min 57.347s
  &#9492;&#9472;zfs.target @4min 57.347s
    &#9492;&#9472;zfs-share.service @4min 57.325s +21ms
      &#9492;&#9472;nfs-server.service @2min 25.053s +2min 32.270s
        &#9492;&#9472;rpc-statd.service @4min 38.563s +15ms
          &#9492;&#9472;nss-lookup.target @4min 38.560s
```

[SIZE=4]C[/SIZE]
```
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

**graphical.target @2min 3.902s**
&#9492;&#9472;multi-user.target @2min 3.902s
  &#9492;&#9472;postfix.service @2min 3.900s +1ms
    &#9492;&#9472;postfix@-.service @2min 2.395s +1.503s
      &#9492;&#9472;network-online.target @2min 2.390s
        &#9492;&#9472;network.target @2.461s
          &#9492;&#9472;networking.service @2.297s +163ms
            &#9492;&#9472;network-pre.target @2.296s
              &#9492;&#9472;ufw.service @1.730s +566ms
                &#9492;&#9472;local-fs.target @1.713s
                  &#9492;&#9472;run-user-112.mount @3.363s
                    &#9492;&#9472;swap.target @1.420s
                      &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\x2>
                        &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\>
```

A and B are nearly identical systems - same RAM, same CPU, same GPU.  What's different?

A doesn't currently have any virtual machines or containers set to start at boot.
```
$ inxi -D
Drives:    Local Storage: total: 15.46 TiB used: 5.85 TiB (37.8%) 

```

B has 5 lxc containers and 4 full virtual machines. and about 2x the storage connected.
```
$ inxi -D
Drives:
  Local Storage: total: 37.13 TiB used: 28.05 TiB (75.6%) 

```

C is a desktop system. No containers. No virtual machines. Just enough storage connected:
```
$ inxi -D
Drives:
  Local Storage: total: raw: 40 GiB usable: 76.16 GiB used: 18.99 GiB (24.9%)
```
Actually, C is a virtual machine running on B and when it was started, all the other VMs and containers were also being started up.  Let me restart C now, alone and see what the results are:

```
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

**graphical.target @2min 3.070s**
&#9492;&#9472;multi-user.target @2min 3.070s
  &#9492;&#9472;postfix.service @2min 3.068s +984us
    &#9492;&#9472;postfix@-.service @2min 1.833s +1.234s
      &#9492;&#9472;network-online.target @2min 1.814s
        &#9492;&#9472;network.target @1.723s
          &#9492;&#9472;systemd-networkd.service @1.661s +61ms
            &#9492;&#9472;network-pre.target @1.659s
              &#9492;&#9472;ufw.service @1.030s +628ms
                &#9492;&#9472;local-fs.target @1.022s
                  &#9492;&#9472;run-user-112.mount @2.576s
                    &#9492;&#9472;swap.target @807ms
                      &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\x2>
                        &#9492;&#9472;dev-disk-by\x2duuid-ae4bb4de\x2d325f\x2d4133\x2dbd37\>
```
So that's over 50% faster because the hardware wasn't trying to do so many tasks concurrently.

See how things can be vastly different for each boot and different hardware?

BTW, C runs a version of 22.04.  The other 2 systems are running a very, very, light GUI on Ubuntu Server 20.04. No DE on any of them.

---

### Post by ian-weisser on 2023-10-09
> **whysohard2 said:**
> Not happy to see a new installation being flagged so many times unless...

You got suckered by false positives.
You are not the first person to get suckered into thinking the repos are poisoned, or that it's all (somehow) insecure.
It simply means that the complexity (and layers of security) are likely new to you. You have a new, complex system to explore, solve, and understand. Enjoy the new-puzzle smell!

---

### Post by whysohard2 on 2023-10-25
[QUOTE=TheFu;14160426]are both more trouble than they are worth. The false positives make them less than useful.

Also, there are 2 Ubuntu releases yearly, so U22 isn't sufficient to say a specific version. Use the **lsb_release -d** command so see the exact version.

Nobody here works for Canonical. We are just other users, like you.  Suggestions here will never reach Canonical.  The way to get Canonical to look at anything is to file a bug report through **Landscape**.


systemd-analyze critical-chain

[FONT=Verdana]bug report through [/FONT]**Landscape**

**lsb_release -d**[FONT=Verdana] 


great suggestions thanks[/FONT]

---

### Post by whysohard2 on 2023-10-25
> **ian-weisser said:**
> You got suckered by false positives.
You are not the first person to get suckered into thinking the repos are poisoned, or that it's all (somehow) insecure.
It simply means that the complexity (and layers of security) are likely new to you. You have a new, complex system to explore, solve, and understand. Enjoy the new-puzzle smell!


even though the following article  [https://www.zdnet.com/article/patch-now-serious-linux-kernel-security-hole-uncovered/](https://www.zdnet.com/article/patch-now-serious-linux-kernel-security-hole-uncovered/)
is not current , just found it online. 
[COLOR=#080A12][FONT=suisseintl]"Patch now: Serious Linux kernel security hole uncovered[/FONT][/COLOR][COLOR=#080A12][FONT=suisseintl]The Zero Day Initiative originally rated this Linux 5.15 in-kernel SMB server, ksmbd, bug a perfectly awful 10"

Any distro using the Linux kernel 5.15 or above is potentially vulnerable. This includes [Ubuntu 22.04]("https://releases.ubuntu.com/22.04/"),".....
....
[/FONT][/COLOR]

---

### Post by ian-weisser on 2023-10-26
You got suckered again, this time by zdnet.

zdnet and similar sites sell adverts. Spreading unnecessary fear, uncertainty, and doubt is part of their business model. They are not a source for accurate and complete information. 

Read all the way down to the seventh(?) paragraph and you will see that the mitigation is updating to the 5.15.61 or newer kernel, OR simply not using the ksmbd module.

A: Few folks use the vulnerable ksmbd module, and so are not affected by this. SMB servers don't use the ksmbd module yet -- that integration is incomplete. 
B: A new-install Ubuntu 22.04 will, if online, promptly update itself to 5.15.87 without any action needed by the user. Completely automatically. If not online, then it's unlikely to be vulnerable to a network-based attack.

Extra mockery deserved by zdnet quoting kernel developer GregKH out of context to make it seem like he is somehow disparaging the Mitre CVE system of tracking vulnerabilities. 

So a perfect 10 out of 10 for zdnet. They got your click. The bait worked.

---

