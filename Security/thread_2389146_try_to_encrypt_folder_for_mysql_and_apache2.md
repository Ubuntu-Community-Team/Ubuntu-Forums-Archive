---
title: "try to encrypt folder for mysql and apache2"
date: 2018-04-12
forum: Security
---

### Post by kasper2083 on 2018-04-12
Hi


I want to encrypt my folders for mysql-database and apache2-webserver and see 2 possibilities.
Encrypted folder with ecryptfs and moving the folders to my crypted extern hdd.
My system is a rpi3 with ubuntu server 16.04.


I tried 3 following ways, all without success. :(


#1
add one other user with "adduser --encrypt-home x" and store both folders in the new home directory, giving rights and access to them and update folder paths to mysql and apache configs.
Unfortunately the user isn't only logged out with "exit" in terminal, but also the home directory will then umount and all setup is broken. With a new "su x" the home is mounted again, yes, but that doenst help.
With a manually "ecryptfs-mount-private" (or similar) the home should be mounted, but that comes to an error message telling me that "setup wasnt done properly" or similar. The error already known by many users on the internet and bug reports, but all without solutions :(


#2
encrypting a new folder to store the mysql and apache folder (without user link). Unfortunately the command "sudo mount.ecryptfs /.folder /folder" comes with the error "Unable to find a list of options to parse, defaulting to interactive mount". Maybe thats the result of my first try to encrypt the folder, but just with a missing point in first path, so I deleted the folder after first success and then the error came.


#3
Moving both folder to the encrypted hdd and use symbolcc links to original paths, giving access and rights to the new location. Theoretical ok, but really a problem, because the root user for mounted folder is a different user, so mysql and www-data have to be a group member of that user. Thats done, but mysql-servie doesnt understand this and gives me error message to not have access to the root folder "/var/lib/mysql" (symbolic link).
As a conslusion, the two differences to default status is first the symbolic link (transparent, so doesnt matter) and second the user access to the root folder containing new mysql and new www folder.


In my understanding both programs need service-root folder in first level under root folder as to see in "/var/www" for apache2 and "/var/lib/mysql" for mysql... but oops mysql is the 3rd level, thats crazy. :(


So where are my problems, solution possible?
Please help


Thanks, kasper

---

### Post by TheFu on 2018-04-13
TL;DR. Sorry.  I skimmed it and 1 & 2 can't work.  3 should work, if the permissions are correct, but unlocking the encrypted storage BEFORE any service starts means no automatic start for those services.

I'd use FDE, but not on a raspberry pi.  I don't have a v3 PI online to check now. AES-NI CPU extensions help with performance.

Home directory encryption requires a login to decrypt the directory.  Service accounts don't do logins, so that storage isn't opened.  I tried using HOME directory encryption for my normal login account, but it broke backups, so after a few months, I wiped and reloaded using FDE instead. FDE performance is reported to be significantly faster than encryptfs or encfs too.

I have ZERO idea if that FDE is possible on a raspberry pi, but a shared USB2 bus is pretty slow for storage (shared by 2 storage devices and the NIC too).  On a recent (5 yrs) Intel CPU, the overhead of FDE is only about 3%. Hardly noticeable.  But it does require a way to type in an unlock passphrase very early in the boot process.

---

### Post by kasper2083 on 2018-04-16
Thank you for answer.

Solution 3 would be ok and maybe easier to me than 1 & 2, although I dont understand the problem(s)... Starting the services after mounting everything is just the way it works right now :D
FDE (full disc encryption?) wont work by many reasons...

But please help me understand the permissions  for mysql and apache2 root folder in sub-directories, then for storing it to the mounted encrypted hdd on usb2. Currently the root-user of the mount-folder, as described above, is "minidlna" user with "mysql" and "www-data" as group members. Theoretically that should work, but it doesnt.

Btw: yes, raid1 with 2x usb2 hdds and encryption IS slow, but as a small-nas for availability-solution the real (max) 12MB/s is enough for all traffic.

Thanks, kasper

---

