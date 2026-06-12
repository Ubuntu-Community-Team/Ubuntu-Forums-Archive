---
title: "Lost files in samba share - Please help me!!!"
date: 2012-12-15
forum: Server Platforms
---

### Post by harrisonford1 on 2012-12-15
We have used a samba server to share documents in windows network since one year ago. Everything was ok until Dec 5, when inexplicably it lost some files. I think only lost the files that were used in that day. Here I listed syslog errors from one file that had gone: November Control.xlsx, but several other files were lost. I googled very much before post this and I didn't found anything consistent that could help me solve the problem. Please advise.

Dec  5 15:14:39 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/November Control.xlsx
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|create_file|fail (Operation not supported)|0x20089|file|open|2012-November/November Control.xlsx
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|stat|fail (No such file or directory)|2012-November/~$November Control.xlsx
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|stat|fail (No such file or directory)|2012-November/~$November Control.xlsx
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|get_real_filename|fail (Operation not supported)|2012-November/~$November Control.xlsx->(null)
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|realpath|fail (No such file or directory)|2012-November/~$November Control.xlsx
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|realpath|fail (No such file or directory)|2012-November/~$November Control.xlsx
Dec  5 15:14:40 backup smbd[9480]: user | 10.218.230.60 | computer|realpath|fail (No such file or directory)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|chmod_acl|fail (Operation not supported)|2012-November/~$November Control.xlsx|766
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_fd|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|fchmod_acl|fail (Operation not supported)|2012-November/~$November Control.xlsx|766
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|chmod_acl|fail (Operation not supported)|2012-November/~$November Control.xlsx|666
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/~$November Control.xlsx
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|chmod_acl|fail (Operation not supported)|2012-November/~$November Control.xlsx|766
Dec  5 15:14:41 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/November Control.xlsx
Dec  5 15:14:42 backup smbd[9480]: user | 10.218.230.60 | computer|sys_acl_get_file|fail (Operation not supported)|2012-November/November Control.xlsx

---

### Post by darkod on 2012-12-15
Are you sure they weren't deleted? Do the users have permissions to delete?

If you login onto the server (directly or with SSH) and browse to the directory where the files should be, do they exist?

It looks like they were deleted. See if you recover them from a backup.

---

### Post by harrisonford1 on 2012-12-16
Hi, Darko. Thanks for reply.

I'm sure they didn't delete because others files were missed from others shares, which this user don't have access.
I've already tried to see the files by SSH and locally, but files haven't there.
What I did was run fsck in virtual disk and host. It reindexed well, but files didn't come back.
My major problem is to explain to my boss what happened. We have some backups to recover but were a little old. Other aggravating is that there is 1TB of files. So, all we can do delay a lot.
Do you understand what do mean this log errors? Please help me understand. 

Thank you.

---

### Post by darkod on 2012-12-16
First, you should ALWAYS have regular backups. For important files on daily basis.

I don't understand the logs. The "No such file or directory" sounds clear. And the "Operation not supported" might have something to do with the missing file too, if it's not there any more opening it won't be supported of course.

When you say 1TB of data, you mean the total amount of data or the missing data? You said only few files are missing, that is hardly 1TB unless they are really huge. It doesn't matter how much data there is in total, if you only need to restore few small files it should not take long.
Depends on the backup process you are doing, I hope you can restore only the files you need, not all of them.

When you say files are missing from a share where this user had no access, do other users have access to that share? Maybe someone else deleted them by mistake, not the same user.

It would be very rare samba to do something itself. I have samba at home for my personal storage, approx since a year ago, and I have never seen a single file to go missing.
How did you setup and administer samba, using SSH directly from ubuntu? Or you are using Webmin or similar? Webmin can create issues with configuration files, including on samba. But people often want a GUI for control and use it despite the risk.

---

### Post by harrisonford1 on 2012-12-16
1TB is the total amount of data. Not much files missed, at least users reclaimed only a few.
I had problem doing backup because ext3 partitions can reach a long path, but when I was backing up them, to a NTFS partition in another computer, some files were long path and didn't backed up. In additional, in those days our room was a mess because we were doing a change there. So backup machine was off and didn't backed up. The fault is mine. I admit.
There were other users having access, but I know they didn't delete because another shares were missed other files with others permissions.
I believe would happened a fail in virtual or host partition. Until two months ago we didn't have a ideal power protection. It lacked much energy.
I often manage samba by putty. I never had problem with this.
Do you know if exist any limitation of size of qemu virtual disks. This problem occurred just when partition reached 1TB and it is configured to increase size automatically with limit size of 1.8TB.

---

### Post by darkod on 2012-12-16
Unfortunately I have no idea how QEMU works. But it all points that it has something to do with your missing files when the partition limit was reached.

Is there really need to use QEMU? Why not simply using standard linux partitions with ext4.

---

### Post by harrisonford1 on 2012-12-17
I appreciate your help, Darko. If I have news I post here. Thanks.

---

