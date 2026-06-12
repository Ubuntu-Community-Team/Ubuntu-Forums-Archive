---
title: "LUKS Trouble"
date: 2020-03-14
forum: Security
---

### Post by sniper8752 on 2020-03-14
I am trying to encrypt an external drive.  When I do this: [FONT=&quot]sudo cryptsetup -v luksAddKey /dev/sdb1 /etc/luks-keys/disk_secret_key
I get this error:
[/FONT]Failed to open key file.
Command failed with code 22: Failed to open key file.
I am following this tutorial: [https://blog.tinned-software.net/automount-a-luks-encrypted-volume-on-system-start/](https://blog.tinned-software.net/automount-a-luks-encrypted-volume-on-system-start/). 
I know I am entering the passphrase right, and the file location definitely does exist.

---

### Post by EuclideanCoffee on 2020-03-14
Do you you have your keyfile set?

[B][FONT=&amp]/etc/luks-keys/disk_secret_key

[/FONT][/B][FONT=&amp]This [/FONT]path should be where a file exists. Do 

```

cat [FONT=&amp]/etc/luks-keys/disk_secret_key
[/FONT]
```[FONT=&amp]

If the output is blank or says there is no file, that's your problem.

Here's a quick tutorial on Red Hat on how to accomplish the same task with either a passphrase or keyfile.

[URL="https://access.redhat.com/solutions/230993"]https://access.redhat.com/solutions/230993

[/URL](I'm reposting because it seems that people like this here.)

Pass phrase:

[/FONT]```
[root ~]# **cryptsetup luksAddKey /dev/sda3**
Enter any existing passphrase: **Existing passphrase which can be used to open DEV**
Enter new passphrase for key slot: **New passphrase to add to DEV**
[root ~]# 

```

Key file

```

[root ~]# dd if=/dev/random bs=32 count=1 of=/root/random_data_keyfile1
[root ~]# printf "Simple passphrase which can also be used interactively" >/root/plaintext_passphrase_keyfile2
[root ~]# **cryptsetup luksAddKey /dev/sda3 /root/random_data_keyfile1**
Enter any passphrase: **Existing passphrase which can be used to open DEV**
[root ~]# 

```

---

### Post by TheFu on 2020-03-14
Think you need to specify the slot to be used.  There are 8, 0-7.
```
$ cryptsetup --key-slot=$SLOT luksAddKey $DISKPART $TMP_FILE
```

You can clear a slot using
```
$ cryptsetup luksKillSlot $DISKPART $SLOT
```

The cryptsetup manpage is quite excellent.

---

### Post by sniper8752 on 2020-03-15
So I can cat the file, and when I set the key slot to 1, it still throws the same error at me.

---

### Post by EuclideanCoffee on 2020-03-15
You haven't tried adding a key with the commands above? That way describes how I built out a system that self-manages thousands of machines. There is no need to specify which slot you use. There are 0-8, 0 typically being the first LUKS key made when you installed your OS. From how I understand LUKS today is that you don't even need to specify the slot as you will still need to provide the key you wish to modify. Using the key, it modifies or erases the index. So if you query what key 1 is, you would need to actually know key 1's value not the index value. This is to protect you from local attacks where someone doesn't know the key but knows that you have a key in slots 0-8. Adding the key is easy. Keeping the secret safe was the challenging part. :)

Adding the key only requires that a previous key exists.

If it does not, you may be stuck.

This may help.

[https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Unlocking/Mapping_LUKS_partitions_with_the_device_mapper](https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Unlocking/Mapping_LUKS_partitions_with_the_device_mapper)

---

### Post by sniper8752 on 2020-03-15
Yes: cryptsetup -v luksAddKey /dev/sdc1 of=/home/user/disk_secret_key
I am doing this as the root user.
Output:
Enter any passphrase: 
Key slot 0 unlocked.
Failed to open key file.
Command failed with code 22: Failed to open key file.
Lastly, permissions on the file:
-rwxrwxrwx  1 root root       4096 Mar 14 18:10 disk_secret_key

---

### Post by EuclideanCoffee on 2020-03-15
Thank you. That's helpful to know.

If instead of a keyfile, you use a passphrase, do you have the same problem?

If the pass phrase works, then we know it's a problem with your key file.

When you created your keyfile, did you follow the instructions above or created your own format?

---

### Post by sniper8752 on 2020-03-15
Here is the tutorial that I followed: [https://loganmarchione.com/2015/05/encrypted-external-drive-with-luks/](https://loganmarchione.com/2015/05/encrypted-external-drive-with-luks/).
The passphrase I set on it, successfully unlocks it.

---

### Post by TheFu on 2020-03-15
I've never used a key file, only a 2-part passphrase (HW+my passphrase) or yubikey challenge/response.
Some of the cryptsetup options changed a few years ago.  Might need to check that how-to with the current options available.

There are still 8 slots - 0-7.
```

       luksAddKey <device> [<key file with new key>]

              adds a new passphrase. An existing passphrase must be
              supplied interactively or via  --key-file.   The  new
              passphrase to be added can be specified interactively
              or read from the file given as positional argument.

              <options>  can  be   [--key-file,   --keyfile-offset,
              --keyfile-size,    --new-keyfile-offset,   --new-key-
              file-size,       --key-slot,       --master-key-file,
              --iter-time, --force-password].
```

Don't see any "of="  in the manpage here.

---

### Post by EuclideanCoffee on 2020-03-15
Yikes. This is a bit old.

I'm glad the passphrase works.

Have you done these steps to create a keyfile?

```

[root ~]# dd if=/dev/random bs=32 count=1 of=/root/random_data_keyfile1
[root ~]# cryptsetup luksAddKey /dev/sda3 /root/random_data_keyfile1

```
And then you get code error 22? Unfortunately the error is a bit vague, which is why I'm troubleshooting.

Another thing is to check if your partition is actually encrypted. You should have a crypt map. Let me know if you're trying to encrypt the correct partition too and if you can check for it. If not, learn to check.

blkid I believe assists. I'll need to dig up docs otherwise. But I encourage you to use Google to figure this one out.

Note:

```

blkid -t TYPE=crypto_LUKS

```

Mine is /dev/sda5

---

### Post by sniper8752 on 2020-03-28
Going through the conversation history, I noticed that I never created the file.  So after doing that now, and trying to automatically open the encrypted volume, I am presented with a different message now:
```
sudo cryptdisks_start sdb1_crypt * Starting crypto disk...                                                                                                                         * sdb1_crypt (starting)..
 * sdb1_crypt (failed)...                                                                                                                  [fail] 
```
I can manually unlock/lock it.

---

