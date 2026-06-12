---
title: "NVME format command not working / correct usage?"
date: 2023-12-10
forum: Ubuntu/Debian BASED
---

### Post by keith-scarlett on 2023-12-10
Hello,

I've recently got a new to me (i.e. used) laptop and I'd like to use the nvme format command to securely erase the contents. I am aware this may be excessive / unnecessary, it's more for future reference.

Here's the relevant terminal output:

```
mint@mint:~$ nvme list
Node                  SN                   Model                                    Namespace Usage                      Format           FW Rev  
--------------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1                                                                        1           0.00   B /   0.00   B      1   B +  0 B   
mint@mint:~$ sudo nvme format --ses=2 /dev/nvme0 -n 0xffffffff
You are about to format nvme0, namespace 0xffffffff(ALL namespaces).
Controller nvme0 has child namespace(s):nvme0n1

WARNING: Format may irrevocably delete this device's data.
You have 10 seconds to press Ctrl-C to cancel this operation.

Use the force [--force|-f] option to suppress this warning.
Sending format operation ... 
NVMe status: INVALID_NS: The namespace or the format of that namespace is invalid(0x200b)
mint@mint:~$ sudo nvme format --ses=2 /dev/nvme0n1 -n 0xffffffff
You are about to format nvme0n1, namespace 0xffffffff(ALL namespaces).
Namespace nvme0n1 has parent controller(s):nvme0

WARNING: Format may irrevocably delete this device's data.
You have 10 seconds to press Ctrl-C to cancel this operation.

Use the force [--force|-f] option to suppress this warning.
Sending format operation ... 
NVMe status: INVALID_NS: The namespace or the format of that namespace is invalid(0x200b)

```

As you'll see I'm trying to do this on a Linux Mint installation (sorry!) - I couldn't get definitive / clear help on the Linux Forum.

The drive has 4 namespaces (each identified with a different 'p' number, or are these actually partitions?) by the way; my intention is to have the format command apply to all at once and thereby 'unify' the drive.

Any help much appreciated, thanks.

---

### Post by howefield on 2023-12-10
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2023-12-10
[FONT=monospace][COLOR=#000000]/dev/nvme0n1 [/COLOR]
[/FONT]NVMe drives have something new as namespaces. Not seen it used.
But the n1 is the first name space.
[https://nvmexpress.org/resource/nvme-namespaces/](https://nvmexpress.org/resource/nvme-namespaces/)

The p's are partitions. 
```
[FONT=monospace][COLOR=#000000]Model: Samsung SSD 970 EVO Plus 500GB (nvme) [/COLOR]
Disk /dev/nvme0n1: 500GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  538MB   537MB   fat32        esp_nvme   boot, esp 
 2      538MB   32.0GB  31.5GB  ext4         noble 
 3      32.0GB  63.5GB  31.5GB  ext4         focal_k 
 5      63.5GB  273GB   210GB   ext4         nvme_data 
 4      469GB   500GB   31.5GB  ext4         jammy 
[/FONT]
```

sudo nvme format -s1 <device>

[https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing](https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing)
 nvme-sanitize

I do not think I would use any of these commands to bulk erase unless I was planning to destroy drive.
I would just format & run run trim which clears cells.

---

### Post by keith-scarlett on 2023-12-16
Thanks for your reply but it seems unclear. I'd be grateful if you could confirm:

1. How using nvme format would 'destroy' a drive?

2. Whether I am using the correct device name in the code I shared above? If not what is the correct syntax if I decide I do want to use nvme format?

3. What is the usage / syntax for trim and what does trim do?

Thanks!

---

### Post by yancek on 2023-12-16
>   How using nvme format would 'destroy' a drive?

I'm not familiar with the software you are using but it states specifically that it will destroy the "data" on the drive so if you have files/directories on the device, yes, they will be destroyed.  As to the correct device name, running the command:  sudo parted -l will list the device name to the right of the word :   Disk  and will show its size.

If you are not familiar with the software, I would suggest not using it.  If there is no data on the drive, I would not expect it to be a problem but if you are going to use it again you will probably need to create a new partition table and partitions and filesystems.  As I said, I'm not familiar with the software so you might wait for someone who has experience with it to respond but it is pretty clear that any data will be deleted/overwritten.

---

