---
title: "Hosting over a network share + permalinks issue"
date: 2010-12-11
forum: Server Platforms
---

### Post by never gonna give you up on 2010-12-11
Hello Ubuntu enthusiasts,

I tried posting this to the advanced forum to the folks over at wordpress but received no response, so I thought I'd try asking here to see if anyone can help. This one is proving to be a tough egg to crack.

Some background: Right now I'm hosting wordpress between two computers, one standard LAMP server running ubuntu 10.10 that takes care of the front end, database, scripting, apache, etc and another running windows 7 that actually stores all my files and shares them with the linux machine VIA a windows share and smbfs. The reason for this admittedly over-complicated setup is I need quite a bit of space (7TB) and the RAID array to do this only works on the machine running windows, and I can't uninstall windows or move the RAID array on that machine. So I have mounted the RAID array from a windows machine using smbfs on to the linux machine and then symlinked the mountpoint of the share to /var/www where apache looks to serve the website.

( side note to justify this insanity - I used to host directly from the windows machine but server administration was a nightmare, and I like working in linux way better, so this setup made the most sense. )

So no sweat right? Everything is working great... except for this issue with the permalinks (read: php virtual directories for those unfamiliar with wordpress). Basically, my website works fine ([stonelinks.org]("http://stonelinks.org")), however after enabling pretty permalinks (like it currently is), when you click on any link to a virtual directory it says that I am forbidden. In fact, I don't even get 404 pages for things that are not there. It seems that every URL that does not correspond to a real file or ends in something like ?p=1324 just gets thrown out by the server as a 403 forbidden. The actual error that appears in the apache log is this:
```
[Wed Dec 08 15:17:45 2010] [error] [client 66.249.65.250] Symbolic link not allowed or link target not accessible: /var/www
```

I have mod_rewrite enabled, but I can't even tell if my .htaccess files are working. My configuration files look like this:

/etc/apache2/sites-enabled/000-default
```
<VirtualHost *:80>
        DocumentRoot /var/www

        <Directory /var/www>
                Options Indexes FollowSymLinks
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

and in case this is a permissions thing here is /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f8fa3eb0-5f5e-4652-b5c4-4dcf7489f2cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=74efcd33-a45d-4a0f-b8d7-16c88755a0aa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//stonelinks.ath.cx/F  /media/stonelinks  smbfs  dir_mode=0775,gid=1002,credentials=/etc/auto.cifs.stonelinks,  0  0
```

where stonelinks.ath.cx is the windows server with the share called f
/etc/auto.cifs.stonelinks is my login info for the windows computer
group 1002 is a group I made called developers:
```
root@dildozer:~# grep developers /etc/group
developers:x:1002:luke,www-data,root
root@dildozer:~# members --all developers
luke www-data root
```

I suspect this is a permissions thing, but for the life of me I cannot figure it out. I've even tried changing everything to 777 permissions (which I know is dangerous, but I want to see it work before I batten down the hatches), both from the mountpoint of the share and from /var/www. Interestingly I can't change the permissions for /var/www if the remote filesystem is mounted.

So I'm throughly stumped. If there is any more info I can provide please let me know and thank you for all your help! You people are saints for what you do here.

---

