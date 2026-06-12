---
title: "Ubuntu Server 20.04 - Partition Size"
date: 2020-10-02
forum: Server Platforms
---

### Post by Dii_Reno on 2020-10-02
I have installed Ubuntu server 20.04 and 18.04 as GPT with the same results. The installer deploys Ubuntu however only shows 200GB of storage when doing a df -h. The physical dev shows as 6TBs but the usable partition space is only 200GBs  Is this a known bug. I have not been able to figure out how to resize the GPT partition. In the meantime I have added a second drive and partitioned it ext4 to get the space i required temporarily. Does anyone have any idea what might cause this?

---

### Post by TheFu on 2020-10-02
The base OS should only need 25GB. Any thing larger than that is a waste.  It was a long-time complaint that the installer assumed admins wanted the entire drive used. Professional admins want control over partition sizes and file systems.

Not a bug.  Working as designed.

If you use lvm, then you can resize in-use file systems easily.  Without lvm, the file system cannot be in-use during changes. For the OS, that means booting from a desktop install and using te "try ubuntu" option, then making the partition larger and resizing the file system. There are sone desktop distros for this too, if you don't have a GPU.

Need to see more facts from command outputs to talk specifics.  fdisk, lsblk are helpful.

---

### Post by Dii_Reno on 2020-10-02
Ok, I build these for small office NAS servers. Seems more inconvenient to be honest.

---

### Post by darkod on 2020-10-02
I would get (or repurpose) a much smaller HDD or SSD and use that as system drive. That way you also keep it physically separate from the data drive.

Do you plan to employ any type of raid? You didn't mention it but for any decent NAS solution I would consider it necessary.

If you use raid things change a little. You will usually have 25-30GB partitions on each disk and use them to make mdadm array for root. The rest can go for mdadm array device for data, etc.

PS. If you do insist to figure out the current disk situation, please post the output of lsblk to start with. That will show little more info.

---

### Post by TheFu on 2020-10-02
For systems that don't get reinstalled or upgraded, that may be true.
Many prefer to keep the OS separate from the data. Less risks to the data when completely different partitions are used. 

People tend to be resistant to changes when the benefits aren't clear for their needs. That's how i feel about many changes to solve problems I've never had.  resolvconf, systemd, gnome3, unity, snaps, avahi, network-manager either cause problems or solve problems we never had.  
I'm on the fence about netplan still.  It didn't start supporting my configs until 2020. In 2019, it didn't work. YAML is terrible for none programmers to setup.

---

