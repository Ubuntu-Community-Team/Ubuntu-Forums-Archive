---
title: "Can't luksAddKey, No key available with this passphrase."
date: 2010-09-02
forum: Security
---

### Post by ShadowTek on 2010-09-02
I'm trying to add a key to a new slot from a keyfile that I created, but I keep getting an error and I don't know what the problem is.

```
root@ubuntu:~# cryptsetup luksAddKey --key-slot 1 /dev/sda5 -d /media/Ubuntu_10_04/etc/cryptkeys/swap.key 
No key available with this passphrase.
```content of swap.key
```
nBPeNCr_PS-yEv5SYEyyzaEextllDLo7aHs7yZGW9dtC48GDlte6WYQe7iG2poJr84U6twxu1DImZcyoBPB1q1AjYAanPsre7qLr7VnN4G6u1x_WG-sja6U_pvnks9CTgcD4UmfBw9mkrU3YY4GknQXtpLvkiBkM1soJ0SYYQ2r-7CDZJvaiYJb9eOKKbMsjlrEG39IBdQwdcEp3D7PK5paTYZdVHU2ygrJvJy-sJly4oqb2274DO8hbYviQsPdawetglkhhhhhhh98h4erwjerfkasjnfhsahfocLnBPeNCr_PS-yEv5SYEyyzaEextllDLo7aHs7yZGW9dtC48GDlte6WYQe7iG2poJr84U6twxu1DImZcyoBPB1q1AjYAanPsre7qLr7VnN4G6u1x_WG-sja6U_pvnks9CTgcD4UmfBw9mkrU3YY4GknQXtpLvkiBkM1soJ0SYYQ2r-7CDZJvaiYJb9eOKKbMsjlrEG39IBdQwdcEp3D7PK5paTYZdVHU2ygrJvJy-sJly4oqb2274DO8hbYviQsPdawetglkhhhhhhh98h4erwjerfkasjnfhsahfocLnBPeNCr_PS-yEv5SYEyyzaEextllDLo7aHs7yZGW9dtC48GDlte6WYQe7iG2poJr84U6twxu1DImZcyoBPB1q1AjYAanPsre7qLr7VnN4G6u1x_WG-sja6U_pvnks9CTgcD4UmfBw9mkrU3YY4GknQXtpLvkiBkM1soJ0SYYQ2r-7CDZJvaiYJb9eOKKbMsjlrEG39IBdQwdcEp3D7PK5paTYZdVHU2ygrJvJy-sJly4oqb2274DO8hbYviQsPdawetglkhhhhhhh98h4erwjerfkasjnfhsahfocLnBPeNCr_PS-yEv5SYEyyzaEextllDLo7aHs7yZGW9dtC48GDlte6WYQe7iG2poJr84U6twxu1DImZcyoBPB1q1AjYAanPsre7qLr7VnN4G6u1x_WG-sja6U_pvnks9CTgcD4UmfBw9mkrU3YY4GknQXtpLvkiBkM1soJ0SYYQ2r-7CDZJvaiYJb9eOKKbMsjlrEG39IBdQwdcEp3D7PK5paTYZdVHU2ygrJvJy-
```What's going on here?

---

### Post by ShadowTek on 2010-09-03
I figured out the problem, which I feel could have been avoided with clearer response messages from cryptsetup, along with better handling of the --key-file option.

#1
Apparently, using the option --key-file after specifying the device
makes cryptsetup think that "--key-file" is the name of the file, which
causes the error "No key available with this passphrase."

```
root@ubuntu:~# cryptsetup luksAddKey --key-slot 1 /dev/sda5 --key-file /etc/cryptkeys/swap.key
No key available with this passphrase.
```#2
When I tried it without the --key-file option, it appeared to me that
the keyfile was again not being read correctly, and that I was being asked to manually enter a new passphrase.

```
root@ubuntu:~# cryptsetup luksAddKey --key-slot 1 /dev/sda5 /etc/cryptkeys/swap.key 
Enter any passphrase: 
No key available with this passphrase.
```# 3
When I tried to enter a new password manually, I was greeted with the
same error, so I was under the impression that I was running into the
same problem as before.

```
root@ubuntu:~# cryptsetup luksAddKey --key-slot 1 /dev/sda5
Enter any passphrase: 
No key available with this passphrase.
```

After trying #2 again, this time entering an *existing* passphrase, it worked. If cryptsetup had asked me to "Enter any *existing* passphrase", I would have done so, but I thought that it was asking for whatever new passphrase that I wanted to enter.

---

