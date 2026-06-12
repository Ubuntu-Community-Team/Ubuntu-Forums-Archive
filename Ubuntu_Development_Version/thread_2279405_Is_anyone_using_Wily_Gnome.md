---
title: "Is anyone using Wily Gnome?"
date: 2015-05-23
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-05-23
Instead of Ubuntu, this time I am using Wily Gnome and Wily Kubuntu. I don't have any problems with Wily Kubuntu, but have a small problem with Wily Gnome, but that problem is quite minor. Both get dist-upgraded everyday and nothing serious bad happened. Actually, its becoming boring. Is it the same with other Gnome and Kubuntu users?

---

### Post by Hazzabin on 2015-05-23
> **Chanath said:**
> Instead of Ubuntu, this time I am using Wily Gnome and Wily Kubuntu. I don't have any problems with Wily Kubuntu, but have a small problem with Wily Gnome, but that problem is quite minor. Both get dist-upgraded everyday and nothing serious bad happened. Actually, its becoming boring. Is it the same with other Gnome and Kubuntu users?

Yes and Yes it is kind of 'boring' at the moment as and I'm guessing here that not a real lot has happened as far as new stuff to be tested ummm yet :p  etc etc

I am running Gnome, Gnome with flashback, Xubuntu, Ubuntu Mate, and Ubuntu Unity and they all much the same

regards

Hazza

---

### Post by rrnbtter on 2015-05-23
Greetings,
I am currently using GDM with the Unity Desktop due to my Lightdm borking. It (gdm) is doing just fine and haven't had time to fix my other display manager. We got some Mir updates yesterday and since I was running with xmir enabled I think it caused me some problems. Like no graphics adapter enabled.

---

### Post by sudodus on 2015-05-23
Lubuntu Wily is also quite stable. I had an issue one day on a system that was updated/dist-upgraded for a few days, but the current/next daily iso file was good again.

---

### Post by ventrical on 2015-05-23
Wily gnome is working good for me. Systemd and wily gnome seem to be made for each other :)

Regards..

---

### Post by ronacc on 2015-05-23
running wily gnome here, only one glitch so far . I get a random disconnects from wifi and it usually wont reconnect without a reboot .  Otherwise very smooth going .

---

### Post by mrfelker on 2015-05-23
Yes.  I upgraded ubuntuGNOME 15.04 to 15.10 (Wily) directly by just pointing the links in sources.list from utopic to wily and doing an aptitude dis-upgrade.  So far it seems about 500 files were  updated.  Works amazingly well - congrats to the developers.  Also now install XFCE, LXDE,MATE desktops and using kernel 4.1rc4.  Fasst and no problems yet.  Running a VMware 11 Virtual Machine on a openSUSE Tumblewee host.

---

### Post by Chanath on 2015-05-24
> **Hazzabin said:**
> Yes and Yes it is kind of 'boring' at the moment as and I'm guessing here that not a real lot has happened as far as new stuff to be tested ummm yet :p  etc etc

I am running Gnome, Gnome with flashback, Xubuntu, Ubuntu Mate, and Ubuntu Unity and they all much the same

regards

Hazza

I have a little problem with Gnome-flashback. When you right click on nautilus, there aren't any minimize, maximize, close buttons. It doesn't poweroff, restart, but goes into login. Other than that, it works well. Everything is somewhat boring, really.

Not like those days, nothing much to read in this development forum too

---

### Post by sudodus on 2015-05-24
Wait until there are major updates of the kernel :-P

---

### Post by ventrical on 2015-05-24
Just for clarification I am speaking of ubuntugnome distro which is gnome3. I have never seen it work this well.  All the systemd bugs appear to be worked out although I must admit that I have  only been testing it on one form factor so far. In some respects it has properties that one might describe as a 'super-unity' panel.

Regards..

---

### Post by Hazzabin on 2015-05-24
> **ventrical said:**
> Just for clarification I am speaking of ubuntugnome distro which is gnome3. I have never seen it work this well.  All the systemd bugs appear to be worked out although I must admit that I have  only been testing it on one form factor so far. In some respects it has properties that one might describe as a 'super-unity' panel.

Regards..
PS I re-read your post now that I'm awake :-) of course you using the latest, so please ignore
Can I ask is your Ubuntu Gnome the latest 15.10 from daily downloads, all that I have except 1 have been upgrades so am interested in your comments

regards
Hazza

---

### Post by ventrical on 2015-05-24
> **Hazzabin said:**
> PS I re-read your post now that I'm awake :-) of course you using the latest, so please ignore
Can I ask is your Ubuntu Gnome the latest 15.10 from daily downloads, all that I have except 1 have been upgrades so am interested in your comments

regards
Hazza

It is upgrade continuance from vivid. But I do have 15.10 iso zsynced and ready to go I think ... I'll check.

regards..

---

### Post by ventrical on 2015-05-24
The ubuntugnome live /daily/ (wily) on the USB has far succeeded  most of what I've seen so far. It is one of those phenom pre-alpha releases. 

```

ubuntu-gnome@ubuntu-gnome:~$ systemd-analyze
Startup finished in 12.984s (kernel) + 22.104s (userspace) = 35.088s
ubuntu-gnome@ubuntu-gnome:~$ 



```

this is just awesome for a USB ver 2.0.

```

ubuntu-gnome@ubuntu-gnome:~$ inxi -b
System:    Host: ubuntu-gnome Kernel: 3.19.0-18-generic x86_64 (64 bit)
           Desktop: Gnome 3.14.4 Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 4005 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 84.0GB (5.4% used)
Info:      Processes: 161 Uptime: 9 min Memory: 687.4/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ubuntu-gnome@ubuntu-gnome:~$ 

```

---

### Post by v3.xx on 2015-05-24
@ventrical

What package needs to be installed to use the 'inxi -b' command?

Thanks

---

### Post by Elfy on 2015-05-25
> **v3.xx said:**
> @ventrical

What package needs to be installed to use the 'inxi -b' command?

Thanks

inxi

[http://manpages.ubuntu.com/manpages/trusty/man1/inxi.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/inxi.1.html)

---

### Post by ventrical on 2015-05-25
thnx elfy;)

I hard installed it seamlessly from daily. It keeps getting more stable. Even during last release it only had one hiccup with not being able to shut down but that being fixed and now this ...  so there is a duality in convergence .. we can converge in to snappy/ubuntu-next  and converge out to ubuntugnome/xubuntu/unity .. etc... which are all stabilizing under systemd.

regards..

---

### Post by v3.xx on 2015-05-25
Thanks Elfy

Found it

Seems to be 14.04 and up, not in 12.04, I was on 12o4 when I asked.   Nice command.

I'll shut up now, before I am reminded this is the developmental forum :D

---

### Post by Hazzabin on 2015-05-25
Gnome 15.10 from daily dated 24th May, does not behave anywhere near as well as the upgrade from Vivid on my machines

It does seem as some parts of the 'window manager' is missing or something related to it

regards

Hazza

---

### Post by Chanath on 2015-05-27
I even installed Gnome shell 3.16.2, and still no problems.
In my 4th year i3 laptop,```
systemd-analyze
Startup finished in 7.258s (kernel) + 35.336s (userspace) = 42.594s

```
and, ```
systemd-analyze critical-chain
graphical.target @35.284s
&#9492;&#9472;multi-user.target @35.284s
  &#9492;&#9472;getty.target @35.283s
    &#9492;&#9472;getty@tty1.service @35.283s
      &#9492;&#9472;rc-local.service @26.448s +32ms
        &#9492;&#9472;network.target @26.447s
          &#9492;&#9472;wpa_supplicant.service @26.663s +487ms
            &#9492;&#9472;basic.target @18.161s
              &#9492;&#9472;sockets.target @18.161s
                &#9492;&#9472;acpid.socket @18.160s
                  &#9492;&#9472;sysinit.target @18.141s
                    &#9492;&#9472;networking.service @17.949s +191ms
                      &#9492;&#9472;apparmor.service @15.737s +2.210s
                        &#9492;&#9472;local-fs.target @15.735s
                          &#9492;&#9472;run-cgmanager-fs.mount @23.295s
                            &#9492;&#9472;local-fs-pre.target @15.735s
                              &#9492;&#9472;systemd-remount-fs.service @15.708s +15ms
                                &#9492;&#9472;systemd-fsck-root.service @14.980s +727ms
                                  &#9492;&#9472;systemd-journald.socket @3.609s
                                    &#9492;&#9472;-.slice @3.608s

```
Quite impressive. There is a problem of getting the network on, but that maybe resulting from a router/internet provider matter.

By the way, I have also Solus OS, from Ikey Doherty, and that boots up so fast;```
systemd-analyze
Startup finished in 556ms (kernel) + 6.511s (initrd) + 15.546s (userspace) = 22.615s
```
I'm going to test Kubuntu Wily in a few minutes.

---

### Post by Chanath on 2015-05-27
Kubuntu Wily boots up even faster than Gnome-Wily.```
[FONT=monospace][COLOR=#000000]systemd-analyze [/COLOR]
Startup finished in 7.785s (kernel) + 32.493s (userspace) = 40.279s
[/FONT]
```

Both Gnome-Wily and Kubuntu-Wily are not giving trouble, and the situation is pretty boring.

---

### Post by neb8 on 2015-05-28
I recently installed Wily Gnome, it's working well except for the fingerprint gui doesn't work during login. I think it's something to do with the new login scripts and/or shell?

---

### Post by monkeybrain20122 on 2015-06-03
For gnome 3.16 in Wily, do you have an option to delete bypassing trash in Files > Preferences > Behavior? This appears to be gone in my Fedora 22.

---

### Post by ronacc on 2015-06-03
Using wily gnome fo a few days now , all well except the background on conky does not go transparent . On my wily ubuntu desktop with gnome-shell it does . This is with the same conkyrc on both . both installs are 64bit .

---

### Post by QDR06VV9 on 2015-06-03
> **ronacc said:**
> Using wily gnome for a few days now , all well except the background on conky does not go transparent . On my wily ubuntu desktop with gnome-shell it does . This is with the same conkyrc on both . both installs are 64bit .
Compiz or Compositing? I can make mine as transparent as i want.(Gnome-Flashback)
Regards

---

### Post by harry332 on 2015-06-03
Wily 15.10 Gnome DE does not yet have nautilus v. 3.16.
However, I have installed the nautilus v. 3.16.2 from Gnome Staging PPA (vivid branch) and that seems to be working just fine, also with the trash bypass option.

---

### Post by sgage on 2015-06-03
Wily Gnome has been working very well for me. I clean-installed from the May 25 daily, and it's been smooth sailing. I'm using it as my daily driver, and don't even think of it as being a dev version (that's the way I like to test things). I'm sure it'll bite me in the a** sooner or later ;-)  No worries - I'm well backed up...

---

### Post by ronacc on 2015-06-03
> **runrickus said:**
> Compiz or Compositing? I can make mine as transparent as i want.(Gnome-Flashback)
Regards

I installed gnome-flashback and compiz and that took care of it . Thanks  , I haven't been following this forum for a few iterations so it will take me awhile to get back up to speed .

---

### Post by QDR06VV9 on 2015-06-03
> **ronacc said:**
> I installed gnome-flashback and compiz and that took care of it . Thanks  , I haven't been following this forum for a few iterations so it will take me awhile to get back up to speed .
It's all good, It is nice to see you around again.

---

### Post by Chanath on 2015-06-06
> **ronacc said:**
> I installed gnome-flashback and compiz and that took care of it . Thanks  , I haven't been following this forum for a few iterations so it will take me awhile to get back up to speed .

Have you installed a different menu with search abilities in Gnome-flashback?

---

### Post by ronacc on 2015-06-06
> **Chanath said:**
> Have you installed a different menu with search abilities in Gnome-flashback?

no , I haven't done much customization yet ,  just use dconf-editor to make the titlebar buttons the way I want . I cannot stand the rt click to min/max .

---

### Post by zika on 2015-06-23
For a week or more:```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  fonts-guru fonts-guru-extra fonts-lohit-guru
Use 'apt-get autoremove' to remove them.
Done
The following packages will be REMOVED:
  compiz compiz-gnome libmetacity-private2 ubuntu-desktop unity
  unity-tweak-tool
The following NEW packages will be installed: libmetacity-private3
The following packages will be upgraded: metacity metacity-common
2 upgraded, 1 newly installed, 6 to remove and 0 not upgraded.
Need to get 356 kB of archives.
After this operation, 11,3 MB disk space will be freed.
Do you want to continue? [Y/n] 
``````
:~$ sudo aptitude dist-upgrade
The following NEW packages will be installed:
libmetacity-private3{a} 
The following packages will be upgraded:
metacity metacity-common 
2 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 356 kB of archives. After unpacking 148 kB will be used.
The following packages have unmet dependencies:
 libmetacity-private2 : Depends: metacity-common (= 1:3.14.3-1ubuntu7) but 1:3.17.2-2ubuntu1 is to be installed.
```;)

---

### Post by QDR06VV9 on 2015-06-23
That Strawberry is still making me hungry
metacity-commom is still being held up by compiz [http://ubuntuforums.org/showthread.php?t=2282595](http://ubuntuforums.org/showthread.php?t=2282595)

---

### Post by zika on 2015-06-23
> **runrickus said:**
> That Strawberry is still making me hungry
metacity-commom is still being held up by compiz [http://ubuntuforums.org/showthread.php?t=2282595](http://ubuntuforums.org/showthread.php?t=2282595)
[IMG]http://cdn.desktopwallpapers4.me/wallpapers/animals/2560x1600/3/21421-turtle-eating-a-strawberry-2560x1600-animal-wallpaper.jpg[/IMG]
[IMG]https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcR-OEjKpH3yJoEY4WUeM1aQECgT8eh_MiQqEzYuHusEKO6crMMq4g[/IMG]

---

### Post by QDR06VV9 on 2015-06-23
I Like it. Thanks zika.;)

---

