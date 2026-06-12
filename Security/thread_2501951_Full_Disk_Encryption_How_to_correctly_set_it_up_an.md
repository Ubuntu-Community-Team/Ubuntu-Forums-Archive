---
title: "Full Disk Encryption: How to correctly set it up and what would be best practice?"
date: 2024-10-27
forum: Security
---

### Post by anekdoteles on 2024-10-27
If I interpret [the documentation]([https://ubuntu.com/core/docs/full-disk-encryption](https://ubuntu.com/core/docs/full-disk-encryption)) correctly, Ubuntu should use FDE by default. However, I'm currently on a live system and can simply access the data of the broken installation on the disk. For a fresh installation I would like to have securely encrypted data, so that it can not be read from live booting systems or some kind of attack during boot. Furthermore I want to separate /home on a different partition in the future, so that future reinstallations are less of a hassle. So, how do I set up an Ubuntu with a separate partitions for /home and the system that are both fully encrypted? Or is this even not advised to begin with, as encrypting /home is generally enough for data privacy?

As a last question: If I understand correctly, data at rest encryption is only helpful before the system is booted and hence not a protection for the lock-screen. Is that so and how do I maximize security of the lock-screen?

---

### Post by werewulf75 on 2024-10-27
[SIZE=2]For non-system partitions/drives I [/SIZE]use Veracrypt, which can provide cascading encryption. Combined with a very complex, very long password, this is the most secure encryption. However, this would not work with a separate /home partition, as the OS needs access to this at boot time.

---

### Post by 0f4d0335 on 2024-10-27
Perhaps you misread because Ubuntu doesn't FDE by default. You'd need to set that while installing. There's an option to do so, so unless you're installing from an automated script, the encryption setup should be something you select. 

There used to be a encrypt home feature, but it got removed and wasn't very secure as it could be bypassed quite easily by using the root account once logged in. But regardless you can still set it up using these instructions: [https://ubuntuhandbook.org/index.php/2024/05/encrypt-home-ubuntu-24-04/](https://ubuntuhandbook.org/index.php/2024/05/encrypt-home-ubuntu-24-04/)

The best method of FDE is up for your use case. For personal use I want encryption for data deletion when I recycle the computer and hard drive. For work FDE has two keys, one that rotates when support needs it, and the other the user controls. If you want more secure OS for lock down features, perhaps Ubuntu is not good for your usecase as more specialized distributions are developed for quick lockdown and encryption. I don't want to recommend these as I think it's irresponsible to endorse such solutions.

---

