---
title: "Terminal window strange and not opaque via VNC on VM"
date: 2013-09-04
forum: Ubuntu Development Version
---

### Post by Doug S on 2013-09-04
Note Before: I am an Ubuntu server user for many years, but this is my first ever attempt at Ubuntu desktop.

Context: I am attempting to help with [ubuntu-docs 13.10,]("http://ubuntuforums.org/showthread.php?t=2172092") so wanted to be able to see on the desktop for myself some referenced items. Hence, I thought to install desktop on a VM, and connect to that desktop via VNC.

My issue: The display seems to mostly be O.K., however the terminal and some little text windows appear very strange. I have tried two different VNC viewers. My issue is best described by a screen shot, attached. I'm hoping my issue is simple and due to inexperience with the desktop. Any help/suggestions appreciated.

Edit:
The VM is on my main 12.04 test server (s15), and I used this command to make it:```
sudo virt-install -n desk_ss -r 8192 --disk path=/media/newhd/desk_ss.img,bus=virtio,size=100 -c saucy-desktop-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```And I start the VM via these commands:```
sudo mount -t ext4 /dev/sdb3 /media/newhd
virsh -c qemu:///system start desk_ss
```The iso was from the daily of 2103.09.03, but I have applied updates today. My 12.04 server has had all updates applied as of a few minutes ago. I do my VNC connection via "s15:5900" from a windows vista computer.

---

### Post by zero2xiii on 2013-09-04
Hay,

I have seen this before because of the VNC quality is set lowish, (something like "speed" or "quick refresh" instead of "Quality" or "High speed connection" or similar).

Also it might be since the VM's graphics is set to vnc, maybe it renders a lower quality display (32mb shared graphics for example) or the like.


Just my two cents....

Cheers

---

### Post by Doug S on 2013-09-04
Thanks for the reply. This is all on my giga bit LAN and I have the VNC viewer set to use maximum bandwidth. I have also tried pretty much every available option on the VNC viewer(s). Also, why would part of the display look and behave just fine, but the terminal window not?
System settings - Screen display - does show "Unknown Display" and resolution 1280X1024 which matches the VNC viewer. The system seems to think its graphics are: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits)

Edit: I have also tried every "Screen display" available, with the same results.

---

### Post by Doug S on 2013-09-05
Update: I did the exact same thing as I described in my original post, but for "ubuntu-12.04.3-desktop-amd64.iso" instead of "saucy-desktop-amd64.iso".
The 12.04.3 Desktop on a VM and via VNC is working fine. 

However, upon the first re-boot after installation the entire screen, as seen via the VNC viewer, was a mess, yet some windows would open and look just fine. The little gear thing in the top right corner of the screen could sort of be made out and was actually not in the correct location. I had to guess at where to actually place the cursor and then click to open the pull down menu that let me re-boot. After that second re-boot, everything was fine.

... Hold on... I re-booted the VM again and the screen was bad again. I re-booted again and then could not log-in. Again, and the display was a mess again. Under system settings - display it shows as "unknown", whereas it was "LapTop" (why I don't know). I did a shutdown and then resarted the VM, it was O.K. and seemed to think the display was "LapTop" again. ... To be continued...

Edit: Other than the obvious differences, such as MAC address, disk image name, uuid and domain, the VM config files are identical:```
doug@s15:/etc/libvirt/qemu$ ls -l desk*
-rw------- 1 root root 2190 Sep  5 14:56 desk_pp.xml
-rw------- 1 root root 2190 Sep  3 20:49 desk_ss.xml
```Edit 2: examining various log files for any potential clues...

Edit 3: Issues seem to be related to which video driver is used (cirrus or vga, the others don't work at all). Also sometimes with the 12.04.3 VM, the cirrus driver would fail to aquire vram. On the 13.10 VM, it can be made to work, sort of, by using the vga driver instead, but then screen resolution is much more limited. Using the cirrus driver (which virt-install will use by default), the little text box issues have been fixed (I don't know how or why). I also found xterm and uxterm terminal emulators which work fine. I also installed ssh server and can use ssh for terminal type stuff.

---

### Post by Doug S on 2013-11-15
The issue of this thread continues to haunt me. Now, it even prevents a simple 14.04 server VM from completing boot with an available terminal via VNC.
Instead of the cirrus default driver, or even vga, using vmvga seems to work wonders with many more screens resolutions (for a desktop VM).
I use the command (for my "serv_tt" VM):```
virsh edit serv_tt
```and change these lines:```
    <video>
      <model type='[COLOR=#ff0000]cirrus[/COLOR]' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```To this:```
    <video>
      <model type='[COLOR=#ff0000]vmvga[/COLOR]' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```And things seems to be O.K.

References:

Quote from somewhere (sorry, I forget where):> What is the workaround?
Change the video emulation setting to vga or vmvga (more resolutions).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080674)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/982889](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/982889) 
[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1091523](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/1091523)

---

