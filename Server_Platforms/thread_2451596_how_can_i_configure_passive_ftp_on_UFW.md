---
title: "how can i configure passive ftp on UFW???"
date: 2020-10-07
forum: Server Platforms
---

### Post by math492m on 2020-10-07
Hi

i need to configure passive ftp on my physical ubuntu server

i am using UFW firewall but how do i do it

it works fine when UFW is turned off 

on UFW???

---

### Post by darkod on 2020-10-07
The FW does not care about active or passive ftp. It cares only about which ports you need to open.

You need to check how passive ftp is configured for the specific application you use for ftp.

---

### Post by math492m on 2020-10-07
then why is it working fine when i turn the firewall off?

i feel kind of dumb:)

---

### Post by LHammonds on 2020-10-07
> **math492m said:**
> then why is it working fine when i turn the firewall off?

i feel kind of dumb:)

He was not saying the firewall does not matter, he is saying the FTP server you have uses a specific set of ports and THOSE are the ports you need to open on the firewall.

I have used vsftpd before and here are the passive port range used:

FTPS Port: 990
Minimum Passive Port: 9000
Maximum Passive Port: 9020

So the firewall commands I used are as follows:

```
ufw allow proto tcp to any port 990 comment 'FTPS'
ufw allow proto tcp to any port 9000:9020 comment 'FTP Passive'
```

Find out what yours uses and adapt the commands to your specific case.

[Reference page](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=265)

LHammonds

---

### Post by TheFu on 2020-10-07
There are times, for LAN use only, that plain FTP really is the only option for a variety of reasons. Someone else will need to help with how to limit the data ports. I haven't setup a plain FTP server in nearly 20 yrs. Sorry.

TL;DR .... 

Any chance we can convince you to use a 1000x more secure protocol, like sftp, instead?
[https://security.stackexchange.com/questions/112585/plain-ftp-no-encryption](https://security.stackexchange.com/questions/112585/plain-ftp-no-encryption)

Plain FTP should have died in 2002 around the time the last people using telnet, rsh, rlogin, rscp stopped doing that.

Passive FTP is a problem for all firewalls because the data port is random.  Some plain FTP servers allow limiting the data channel to a range of ports, but then a client still needs to open that complete range up.  I suppose the firewall could be configured to allow only that range only from the known plain FTP server to vastly improve security, but it can't get passed the fact that credentials are transmitted 100% as plain text.

If the downloads don't use credentials, then just setup an HTTP or HTTPS server, which is much more firewall friendly already. If you need it for just a few transfers, cd into the directory to be shared, run:
```
$ python -m SimpleHTTPServer 8000
```
This will display index.html or a list of all the files in that directory.

If the problem is that some 3rd party tool is making the call to **ftp .....**, we've swapped out that ftp call with sftp and the systems all kept working. Just modify the PATH and setup a hard-link to /usr/local/ftp ---> /usr/bin/sftp. If you setup ssh-keys, no password will be requested. That is all client-side. There are sftp clients for all networked OSes.  Windows users complain the loudest, so they should use either filezilla or WinSCP.  sftp uses the same port as ssh and is configured in the sshd_config on the server-side. Normal ssh credentials work.  22/tcp is the default port and probably already sufficiently opened to the world.

Google-Chrome and Firefox is/has removed support for plain FTP. That says a bunch about that protocol. Version 82 shouldn't support it at all. I don't use chrome, so don't know this personally.  Chromium appears to be on v85 now.

Anyways, there are options that are more firewall friendly and use only well-defined ports.

---

### Post by LHammonds on 2020-10-07
I do not know of any legit reasons to run plain FTP on the internet but there is at least one requirement for it on a LAN.  We had a Mitel phone system that only had an option to backup to FTP.  Of course we configured the firewall on the FTP server so that it only accepts connections from the IP of the Mitel server but it was a definite use case in recent history.  ;-)

The above commands can be modified to accept a connection from a single IP address like this:

```
ufw allow proto tcp from 192.168.1.21 to any port 990 comment 'FTPS'
ufw allow proto tcp from 192.168.1.21 to any port 9000:9020 comment 'FTP Passive'
```

LHammonds

---

### Post by math492m on 2020-10-09
i need to use ftp berceuse that is the standard for plex servers

---

### Post by TheFu on 2020-10-09
> **math492m said:**
> i need to use ftp berceuse that is the standard for plex servers

What?!!!  You are misinformed.  
I've run plex for a few years and have NEVER used plain FTP.

Almost everyone uses either NFS or CIFS to get files onto their Plex Media Storage system, which isn't always the same system where Plex runs.  I happen to run Plex on my LAN NFS server because it is just powerful enough for both (and about 10 other services), but plex is the secondary purpose for that system.  NFS is the primary reason it exists.
It has a bunch of storage connected, both locally and via NFS from another system:
```
$ df -Th
Filesystem                                   Type  Size  Used Avail Use% Mounted on
/dev/sde2                                    ext2  237M  136M   89M  61% /boot
/dev/mapper/istar--vg-root                   ext4  101G   82G   15G  86% /
/dev/mapper/istar--vg-lv_media               ext4  3.5T  3.5T   21G 100% /d/D1
/dev/mapper/istar--vg2-lv_media2             ext4  3.6T  3.5T   37G  99% /d/D2
/dev/mapper/istar--vg3--back-lv_media3_back  ext4  3.6T  3.6T   50G  99% /d/D3
/dev/mapper/istar--stuff-lv--tv              ext4  294G  101G  193G  35% /TV
/dev/mapper/istar--8TB-istar--back3--a       ext4  3.6T  3.5T  130G  97% /d/b-D3
/dev/mapper/istar--8TB-istar--back3--b       ext4  3.6T  3.5T   85G  98% /d/b-D4
/dev/mapper/istar--vg2--back-lv_media2_back  ext4  3.6T  3.6T   47G  99% /d/b-D5
romulus:/export/www/vhosts/gallery           nfs   151G  107G   37G  75% /Photos
romulus:/raid/media                          nfs   1.8T  1.7T   42G  98% /R
romulus:/Data/r2                             nfs   1.3T  1.2T   60G  96% /S
```

I strive to make the mount locations identical across all systems whether the storage is local or not. My LV naming could be better, but that really isn't too important.  The /d/D[1-9] storage is exported as NFS to most other systems here.

No need for plain FTP.

---

### Post by ameinild on 2020-10-09
> **math492m said:**
> i need to use ftp berceuse that is the standard for plex servers

I'm gonna chime in with the others here - please describe your usecase for using plain FTP with Plex - we simply don't get it.

---

### Post by math492m on 2020-10-22
look guys i know plain ftp sucks.... but it is for work, and it is what my boss wants. so how do i do it?

---

### Post by darkod on 2020-10-22
1). Configure the ftp software to work in passive mode as per their instructions (you can use different packages/software so just saying ftp doesn't say much). There are many tutorials available online.
2). Configure iptables to allow traffic on the ports you decide to use for the passive ftp.

Those two steps are the only thing you need to do. I basically tried to say this from the start, not sure if my message got through. :)

---

### Post by LHammonds on 2020-10-22
> **math492m said:**
> look guys i know plain ftp sucks.... but it is for work, and it is what my boss wants. so how do i do it?
What exactly are you expecting from us?  Your title asks how to configure UFW.  I gave you two very-specific UFW commands which were specific to "my" situation and specified the ports "my" situation required and how I made it work.

Are you wanting something else....like the exact commands "you" would type?  If so, you failed to answer the question about what ports you need...which is defined in your FTP server configuration.

LHammonds

---

