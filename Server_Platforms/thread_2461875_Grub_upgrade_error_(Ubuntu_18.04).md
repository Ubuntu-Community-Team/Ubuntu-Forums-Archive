---
title: "Grub upgrade error (Ubuntu 18.04)"
date: 2021-05-09
forum: Server Platforms
---

### Post by raverdave2k on 2021-05-09
Hi,

I have a couple of remote dedicated servers running 18.04 (They are on Dell PowerEdges if it matters). Last night I ran 'apt update / apt upgrade' on both of them and received the following errors relating to Grub.

```

Setting up grub-efi-amd64 (2.04-1ubuntu44) ...
Installing for x86_64-efi platform.
efibootmgr: option requires an argument -- 'd'
efibootmgr version 15
usage: efibootmgr [options]
        -a | --active         sets bootnum active
        -A | --inactive       sets bootnum inactive
        -b | --bootnum XXXX   modify BootXXXX (hex)
        -B | --delete-bootnum delete bootnum
        -c | --create         create new variable bootnum and add to bootorder
        -C | --create-only      create new variable bootnum and do not add to bootorder
        -D | --remove-dups      remove duplicate values from BootOrder
        -d | --disk disk       (defaults to /dev/sda) containing loader
        -r | --driver         Operate on Driver variables, not Boot Variables.
        -e | --edd [1|3|-1]   force EDD 1.0 or 3.0 creation variables, or guess
        -E | --device num      EDD 1.0 device number (defaults to 0x80)
        -g | --gpt            force disk with invalid PMBR to be treated as GPT
        -i | --iface name     create a netboot entry for the named interface
        -l | --loader name     (defaults to "\EFI\ubuntu\grub.efi")
        -L | --label label     Boot manager display label (defaults to "Linux")
        -m | --mirror-below-4G t|f mirror memory below 4GB
        -M | --mirror-above-4G X percentage memory to mirror above 4GB
        -n | --bootnext XXXX   set BootNext to XXXX (hex)
        -N | --delete-bootnext delete BootNext
        -o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)
        -O | --delete-bootorder delete BootOrder
        -p | --part part        (defaults to 1) containing loader
        -q | --quiet            be quiet
        -t | --timeout seconds  set boot manager timeout waiting for user input.
        -T | --delete-timeout   delete Timeout.
        -u | --unicode | --UCS-2  handle extra args as UCS-2 (default is ASCII)
        -v | --verbose          print additional information
        -V | --version          return version and exit
        -w | --write-signature  write unique sig to MBR if needed
        -y | --sysprep          Operate on SysPrep variables, not Boot Variables.
        -@ | --append-binary-args file  append extra args from file (use "-" for stdin)
        -h | --help             show help/usage
grub-install: error: efibootmgr failed to register the boot entry: Operation not permitted.
Failed: grub-install --target=x86_64-efi  
WARNING: Bootloader is not properly installed, system may not be bootable
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-142-generic
Found initrd image: /boot/initrd.img-4.15.0-142-generic
Found linux image: /boot/vmlinuz-4.15.0-141-generic
Found initrd image: /boot/initrd.img-4.15.0-141-generic
done
Setting up grub-efi-amd64-signed (1.167~18.04.1+2.04-1ubuntu44) ...
Installing for x86_64-efi platform.
efibootmgr: option requires an argument -- 'd'
efibootmgr version 15
usage: efibootmgr [options]
        -a | --active         sets bootnum active
        -A | --inactive       sets bootnum inactive
        -b | --bootnum XXXX   modify BootXXXX (hex)
        -B | --delete-bootnum delete bootnum
        -c | --create         create new variable bootnum and add to bootorder
        -C | --create-only      create new variable bootnum and do not add to bootorder
        -D | --remove-dups      remove duplicate values from BootOrder
        -d | --disk disk       (defaults to /dev/sda) containing loader
        -r | --driver         Operate on Driver variables, not Boot Variables.
        -e | --edd [1|3|-1]   force EDD 1.0 or 3.0 creation variables, or guess
        -E | --device num      EDD 1.0 device number (defaults to 0x80)
        -g | --gpt            force disk with invalid PMBR to be treated as GPT
        -i | --iface name     create a netboot entry for the named interface
        -l | --loader name     (defaults to "\EFI\ubuntu\grub.efi")
        -L | --label label     Boot manager display label (defaults to "Linux")
        -m | --mirror-below-4G t|f mirror memory below 4GB
        -M | --mirror-above-4G X percentage memory to mirror above 4GB
        -n | --bootnext XXXX   set BootNext to XXXX (hex)
        -N | --delete-bootnext delete BootNext
        -o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)
        -O | --delete-bootorder delete BootOrder
        -p | --part part        (defaults to 1) containing loader
        -q | --quiet            be quiet
        -t | --timeout seconds  set boot manager timeout waiting for user input.
        -T | --delete-timeout   delete Timeout.
        -u | --unicode | --UCS-2  handle extra args as UCS-2 (default is ASCII)
        -v | --verbose          print additional information
        -V | --version          return version and exit
        -w | --write-signature  write unique sig to MBR if needed
        -y | --sysprep          Operate on SysPrep variables, not Boot Variables.
        -@ | --append-binary-args file  append extra args from file (use "-" for stdin)
        -h | --help             show help/usage
grub-install: error: efibootmgr failed to register the boot entry: Operation not permitted.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Setting up grub-efi (2.02-2ubuntu8.23) ...
Processing triggers for install-info (6.5.0.dfsg.1-2) ...
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
Processing triggers for systemd (237-3ubuntu10.47) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for dbus (1.12.2-1ubuntu1.2) ...
Processing triggers for ureadahead (0.100.0-21) ...
Processing triggers for initramfs-tools (0.130ubuntu3.11) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-142-generic
I: The initramfs will attempt to resume from /dev/md3
I: (UUID=e70a60f6-9b9c-4998-935f-29d9205f4544)
I: Set the RESUME variable to override this.
Errors were encountered while processing:
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried grub-install and it throws the same error, using the --no-nvram option completed without error but I'm not sure it actually worked because running apt update / upgrade again just results in the same attempt to install "grub-efi-amd64-signed" with the same problem.

Given the error above contains the line _**WARNING: Bootloader is not properly installed, system may not be bootable**_, I am very concerned.


**Edit**: After further reading I ran the command  [FONT=Consolas]sudo grub-install --efi-directory=/boot/efi --target=x86_64-efi --no-nvram  [/FONT]   and it says "Installation Finished. No error reported." however anytime I run apt for anything it tries again to install grub-efi-amd64 / grub-efi-amd64-signed and results in the same error. Hopefully this command is fixing the error and making the machine bootable and I just need to some how clean up apt?

---

### Post by Frogs Hair on 2021-05-09
Moved to ***Server Platforms***.

---

### Post by highbir on 2021-05-09
Also having this issue on 18.04.

---

### Post by raverdave2k on 2021-07-16
Does any one have any information on this?, still getting plague by the error any time I use apt. Have to remember to run the fix afterwards and have still not dared rebooted the either machine as I'm still not 100% confident if the fix is solving the problem or not.

---

### Post by MAFoElffen on 2021-07-16
> **raverdave2k said:**
> Does any one have any information on this?, still getting plague by the error any time I use apt. Have to remember to run the fix afterwards and have still not dared rebooted the either machine as I'm still not 100% confident if the fix is solving the problem or not.
Please try:
```
sudo apt --only-upgrade install grub-common
```
And post the results...

---

### Post by raverdave2k on 2021-07-17
Here is the output of that command

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version (2.02-2ubuntu8.23).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up grub-efi-amd64-signed (1.167~18.04.5+2.04-1ubuntu44.1.2) ...
Installing for x86_64-efi platform.
efibootmgr: option requires an argument -- 'd'
efibootmgr version 15
usage: efibootmgr [options]
        -a | --active         sets bootnum active
        -A | --inactive       sets bootnum inactive
        -b | --bootnum XXXX   modify BootXXXX (hex)
        -B | --delete-bootnum delete bootnum
        -c | --create         create new variable bootnum and add to bootorder
        -C | --create-only      create new variable bootnum and do not add to bootorder
        -D | --remove-dups      remove duplicate values from BootOrder
        -d | --disk disk       (defaults to /dev/sda) containing loader
        -r | --driver         Operate on Driver variables, not Boot Variables.
        -e | --edd [1|3|-1]   force EDD 1.0 or 3.0 creation variables, or guess
        -E | --device num      EDD 1.0 device number (defaults to 0x80)
        -g | --gpt            force disk with invalid PMBR to be treated as GPT
        -i | --iface name     create a netboot entry for the named interface
        -l | --loader name     (defaults to "\EFI\ubuntu\grub.efi")
        -L | --label label     Boot manager display label (defaults to "Linux")
        -m | --mirror-below-4G t|f mirror memory below 4GB
        -M | --mirror-above-4G X percentage memory to mirror above 4GB
        -n | --bootnext XXXX   set BootNext to XXXX (hex)
        -N | --delete-bootnext delete BootNext
        -o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)
        -O | --delete-bootorder delete BootOrder
        -p | --part part        (defaults to 1) containing loader
        -q | --quiet            be quiet
        -t | --timeout seconds  set boot manager timeout waiting for user input.
        -T | --delete-timeout   delete Timeout.
        -u | --unicode | --UCS-2  handle extra args as UCS-2 (default is ASCII)
        -v | --verbose          print additional information
        -V | --version          return version and exit
        -w | --write-signature  write unique sig to MBR if needed
        -y | --sysprep          Operate on SysPrep variables, not Boot Variables.
        -@ | --append-binary-args file  append extra args from file (use "-" for stdin)
        -h | --help             show help/usage
grub-install: error: efibootmgr failed to register the boot entry: Operation not permitted.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by MAFoElffen on 2021-07-17
Please report it to launchpad, as a bug. There is something wrong with their script. There seems to be missing variable loading or not reading the variable from EFI.

Or give one last try, starting out a bit differently:
```
# This time, "Ensure" load of the Kernel module that reads the EFI variables, to give it all chances to read the EFI variables...
sudo modprobe efivars

## There is some varied confusion here, whether it should be to reinstall the whole grub-common package, grub-efi-<arch>, or grub-efi-<arch>-signed... 
## Though your system is complaining about grub-efi-amd64-signed, but since during an apt update, maybe should be both.
sudo apt-get install --reinstall grub-common grub-efi-amd64 

# Then reconfigure it manually "Tailored To Your Own System"
sudo grub-install [FONT=Consolas]--no-nvram[/FONT] --boot-directory=/boot --bootloader-id=ubuntu-fix --target=x86_64-efi --efi-directory=/efi
sudo  update-grub
```

---

### Post by raverdave2k on 2021-07-17
Thanks but still no go.

The second of those commands gives the error "E: Internal Error, No file name for grub-efi-amd64-signed:amd64"
The third command gives "grub-install: unrecognized option '--nonvram'

Will try putting a bug report

---

### Post by MAFoElffen on 2021-07-17
Sorry. I went back to that post and corrected the typo's. Could you please try again?

---

### Post by raverdave2k on 2021-07-17
Third and fourth commands now show completed without error but running the second command as well as a normal apt update / upgrade still try's and fails to install 'grub-efi-amd64-signed'.

---

### Post by oldfred on 2021-07-17
Do you have a valid mount of an ESP in fstab?
System defaults to using that partition for reinstall, but if some change and now not a valid entry, it will fail.

---

### Post by raverdave2k on 2021-07-17
> **oldfred said:**
> Do you have a valid mount of an ESP in fstab?
System defaults to using that partition for reinstall, but if some change and now not a valid entry, it will fail.

This is the contents of my fstab

[FONT=Consolas][COLOR=#2DDAFD]# /dev/md4[/COLOR]
UUID=55b66fff-5353-4e7d-807f-c0ba77473325     /    ext4    errors=remount-ro     0 0                                                                                                                

[COLOR=#2DDAFD]# /dev/md2[/COLOR]
UUID=9ad5ab3d-97f3-47d8-8339-7b3ea88667f5     /boot    ext4    rw,relatime,stripe=4     0 2                                                                                                          

[COLOR=#2DDAFD]# /dev/md1 LABEL=EFI\134x20SYSTEM[/COLOR]
UUID=BE2A-43C2    /boot/efi    vfat    rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,errors=remount-ro     0 2                                                  

[COLOR=#2DDAFD]# /dev/md3[/COLOR]
UUID=21a89a52-a9aa-49b2-a121-bfe22ee69c1d     none    swap    defaults,pri=-2     0 0   
[/FONT]

---

