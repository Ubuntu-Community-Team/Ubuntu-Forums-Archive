---
title: "Problem with installing Nessus 3.0"
date: 2006-01-01
forum: Server Platforms
---

### Post by DaturaX on 2006-01-01
I am running xubuntu on my X20 laptop and I presently have nessus version 2 installed. I downloaded the version 3 package from nessus.org but when I tried to install the debian package, I get this error message.

```
dave@dave-ubuntu:~/Desktop$ sudo dpkg -i Nessus-3.0.0-debian3_i386.deb
Password:
(Reading database ... 56989 files and directories currently installed.)
Preparing to replace nessus 2.2.4-2 (using Nessus-3.0.0-debian3_i386.deb) ...
Unpacking replacement nessus ...
dpkg: error processing Nessus-3.0.0-debian3_i386.deb (--install):
 trying to overwrite `/etc/init.d/nessusd', which is also in package nessusd
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 Nessus-3.0.0-debian3_i386.deb

```

When I tried to apt-get remove nessus, I get another error
```

dave@dave-ubuntu:~/Desktop$ sudo apt-get remove nessus
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  nessus
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 635kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 56987 files and directories currently installed.)
Removing nessus ...
Setting up nessusd (2.2.4-2) ...
update-rc.d: /etc/init.d/nessusd: file does not exist
dpkg: error processing nessusd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nessusd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have Nessus 3,0 running on another machine but its running fine. My only grip is that it scans very slow. A scan might take up to an hour.

---

### Post by jb1095 on 2006-01-02
I recommend adding ". /usr/share/debconf/confmodule" into the .prerm file just prior to the initial 'if' statement. removal/purge goes pleasantly after this fix.  The .prerm files are usually located in /var/lib/dpkg/info/

let us know if this helps.

-jb

---

### Post by DaturaX on 2006-01-03
[QUOTE=jb1095]I recommend adding ". /usr/share/debconf/confmodule" into the .prerm file just prior to the initial 'if' statement. removal/purge goes pleasantly after this fix.  The .prerm files are usually located in /var/lib/dpkg/info/

let us know if this helps.

-jb[/QUOTE]

I assume you are talking about the dpkg.prerm. I see no if statement in the file

```

undivert_md5sum() {
    dpkg-divert --rename --remove /usr/bin/md5sum.textutils
     dpkg-divert --rename --remove /usr/share/man/man1/md5sum.textutils.1.gz
}


case "$1" in
    remove|upgrade)
        case "$2" in
            0.* | 1.[0123456789].* | 1.10 | 1.10.* | 1.13.[01234] | '')
                undivert_md5sum
                ;;
        esac
        ;;

    failed-upgrade|deconfigure)
        ;;

    *)
        echo "$0 called with unknown argument \`$1'" 1>&2
        exit 1
        ;;
esac

```

---

### Post by DaturaX on 2006-01-03
a case of bad package. Deleted the bad package in /var/cache/apt and it worked.

---

### Post by jb1095 on 2006-01-04
nice - congrats.  i have been using 3.0 ever since it came out.  i like it.

---

### Post by poljm282 on 2006-03-01
This is my first post as I'm new to Ubuntu and the forum.  I'm having the same problems, but your fix does not have the detail I need to correct my problem.  I receive the same error as the original post.  Can someone please add detail to how this problem was resolved.
Thanks!

---

### Post by h3llfyr3 on 2006-03-19
For 5.10 Breezy Badger

#1.  Download the Debian package (Nessus-3.0.0-debian3_i386.deb) from [http://www.nessus.org/download/](http://www.nessus.org/download/).
  
#2. Install openssl Nessus needs it and it's not part of the base.

apt-get install openssl

#3 Install the package using dpkg. This will install the package into the /opt/nessus/ directory:
sudo dpkg -i Nessus-3.0.0-debian3_i386.deb
   
#4. Create your nessusd certificate then add users 
/opt/nessus/sbin/nessus-mkcert
/opt/nessus/sbin/nessus-adduser
   
#6.  /opt/nessus/bin/nessus-fetch --register XXXX-XXXX-XXXX-XXXX-XXXX
#7. Start the nessus daemon:

/opt/nessus/sbin/nessusd &#8211;D

you also need to install for the nessus client
apt-get install libssl-dev
apt-get install libz
apt-get install libgtk2.0-dev

---

### Post by parrybhinder on 2008-03-05
Hello friends,


i am not able to install Nessus 3 on xubuntu below message showing !!!

root@parminder:/home/parminder# dpkg -i Nessus-3.0.6-debian3_i386.deb
(Reading database ... 108481 files and directories currently installed.)
Preparing to replace nessus 3.0.6 (using Nessus-3.0.6-debian3_i386.deb) ...
$Shutting down Nessus : .
Unpacking replacement nessus ...
dpkg: dependency problems prevent configuration of nessus:
 nessus depends on libssl0.9.7 (>= 0.9.7e); however:
  Package libssl0.9.7 is not installed.
dpkg: error processing nessus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nessus

Regards,
PSB

---

