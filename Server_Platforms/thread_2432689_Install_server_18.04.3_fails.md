---
title: "Install server 18.04.3 fails"
date: 2019-12-06
forum: Server Platforms
---

### Post by paul.a on 2019-12-06
Trying to install 18.04.3 from most recent ISO (files all dated 5 August 2019) via usb stick. Fails at "A start job is running for Snappy daemon" ==> "[FAILURE] Failed to start Snappy daemon" in an endless loop (3 hours is repeatable). 

I can install 18.04.1, but after apt update and apt upgrade, I can't reboot, different errors: "Running scripts /scripts/local-premount ==> UUID=C79...7ac does not exist (IT DOES, as /dev/sda1 mounted as / ) ==> The "The busy Box can't find mouse" (which it did before going to busy box) ==> (initramfs) and stops...

Is the ISO broken? (checksums OK)
Thanks -- Paul

---

### Post by LHammonds on 2019-12-06
You should really post more details than this.  I have not seen issues with installing Ubuntu Server 18.04.x but then again, I do not install via USB or on bare-metal most of the time.

What is the name of the iso file you downloaded?  Is it the new installer version or the traditional installer?  How far in the installation did you get?  Did you install and choose to let it use the whole disk for a single partition or did you specify partitions?

Did the disk(s) you are installing to already have an OS or data on them?

What are the hardware details?  Is there some kind of RAID hardware in the mix that could be affecting installation?

LHammonds

---

### Post by paul.a on 2019-12-06
Thanks for replying. This was a brand new install, using ubuntu-18.04.3-live-server-amd64.iso downloaded from <http://releases.ubuntu.com/18.04/>. 
For the partitions, I used gparted live prior to installation on a new Seagate SSD. Partition table to MSDOS (MBR) then put a 5GB swap at the end, and filled the remainder with an ext4 with 1GB unused at beginning and end, made it bootable to "/". During installation went to manual partition, and verified/reformatted to exactly the same (2 other HDDs for future raid were correctly "do not use".)
It went ahead, but then failed at "A start job is running for Snappy daemon" ==> "[FAILURE] Failed to start Snappy daemon".
Rinced aand repeated (after deleting partition, remaking it) twice with identical results
However, exactly the same process with ubuntu-18.04-live-server-amd64.iso from <http://old-releases.ubuntu.com/releases/18.04.1/> works perfectly -- up and running first shot.
I think this answers your questions.
Note that 18.04.1 reports:
318 packages can be updated.
166 updates are security updates.
If I update/upgrade, a reboot fails with messages as in my first post above

Again thanks -- Paul

---

### Post by mastablasta on 2019-12-09
> **paul.a said:**
> 
For the partitions, I used gparted live prior to installation on a new Seagate SSD. Partition table to MSDOS (MBR) then put a 5GB swap at the end, and filled the remainder with an ext4 with 1GB unused at beginning and end, made it bootable to "/". During installation went to manual partition, and verified/reformatted to exactly the same (2 other HDDs for future raid were correctly "do not use".)


hard to say what went wrong from the description. However here are some things to consider:

1. you might need to use GPT instead of MBR. Depending on which method is supported by motherboard (UEFI? BIOS? Is secure boot turned ON?). more here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
2. you might need a separate boot partition (again depending on the install method)
3. Don't put SWAP on SSD drive. if you must, then at least reduce swapiness. more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
4. make sure the downloaded image is good (check md5sum); if image is good try another image recording software. some can cause issues. in fact when i did my current desktop install i had to use DVD because none of them would load the OS properly at boot.

---

### Post by paul.a on 2019-12-10
Thanks.  Checksum on ISO is good. UNetbootin USB stick has always worked (I run seven servers, 19 workstations). UEFI ignored, normal BIOS boot. Finally got it done as follows (for anyone else having the same problem) :

1. Installed 18.04.1 (actually 18.04 first release, but updates to 18.04.1 with 4 series kernel)

2. ```
sudo apt remove --purge ureadahead
sudo apt remove --purge snapd
sudo vim /etc/network/interfaces  #set static IP
sudo systemctl unmask networking && sudo systemctl enable networking && sudo systemctl restart networking
# systemctl stop systemd-networkd.socket systemd-networkd && systemctl disable systemd-networkd.socket systemd-networkd && systemctl mask systemd-networkd.socket systemd-networkd && apt --assume-yes purge nplan netplan.io
sudo vim /etc/systemd/resolved.conf  # add DNS to first line
sudo mv /etc/netplan/01-netcfg.yaml /etc/netplan/01-netcfg.yaml_old
sudo systemctl restart systemd-resolved
sudo apt update
sudo apt dist-upgrade
sudo apt install --install-recommends linux-generic-hwe-18.04  # kernel to series 5

```

Then I had an 18.04.3 server, ready to tweak to my environment ;=}

Again, with my thanks for your looking into this.  -- Paul

---

