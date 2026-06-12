---
title: "error upgrading to 8.04"
date: 2008-04-24
forum: Server Platforms
---

### Post by jonabyte on 2008-04-24
I am getting this error on one of my servers, trying to use the do-release tool.
Anyone have any ideas??
Thanks

```

sudo do-release-upgrade --devel-release
Password:
Checking for a new ubuntu release
Failed Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'hardy.tar.gz'
authenticate 'hardy.tar.gz' against 'hardy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 2
Debug information:

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpMi8LCO'

gpg: can't open `/tmp/tmpMi8LCO/hardy.tar.gz.gpg'
gpg: verify signatures failed: file open error

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.
joel@ubserv:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
```

---

### Post by LeChacal on 2008-04-24
I am getting the same error also. I am upgrading from 6.06-2 server editon without x installed. Googling the error only comes up with this same problem when Gusty came out and people were trying to upgrade to Feisty.

---

### Post by jimwillsher on 2008-04-24
It's almost certainly due to the servers getting a hammering. Try again tomorrow.

---

### Post by sanmarcos on 2008-04-25
Why is the --devel-release flag needed?

---

### Post by jonabyte on 2008-04-25
well just tried it and got the same:
```
sudo do-release-upgrade
Password:
Checking for a new ubuntu release
No new release found

```


will wait a bit longer now and try again.

---

### Post by jimwillsher on 2008-04-25
I did a "do-release-upgrade" this morning. It stuttered for a minute or two but then completed normally. 8.04 is now installed.

---

### Post by jonabyte on 2008-04-25
Well I did one with the --devel-release and it upgraded it, but not sure if thats the new release or still the rc version.

---

### Post by TheFuzzy0ne on 2008-04-26
> **jimwillsher said:**
> I did a "do-release-upgrade" this morning. It stuttered for a minute or two but then completed normally. 8.04 is now installed.

Will...

```

do-release-upgrade

```

...work for my desktop PC? It worked great on my server, I'm just not sure if it's the right thing to use for my desktop.

Thanks.

---

### Post by xubean on 2008-04-26
anybody, I seriously need some help.
I'm getting this error. I'm pretty sure it's because my "/" is full, but I don't know how to free it up. or is it some other error? Help is really appreciated. 

xubean@ALIEN:~$ do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmp8DF21T/hardy.tar.gz'
authenticate '/tmp/tmp8DF21T/hardy.tar.gz' against '/tmp/tmp8DF21T/hardy.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 

gpg: WARNING: unsafe permissions on homedir `/tmp/tmp8DF21T'
secmem usage: 1408/1408 bytes in 2/2 blocks of pool 1408/32768

gpg: Signature made Tue 22 Apr 2008 03:12:41 AM CDT using DSA key ID 437D05B5
gpg: fatal: error writing to `/tmp/tmp8DF21T/.#lk0x8123310.ALIEN.7387': No space left on device

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

Thanks!

---

### Post by vloris on 2008-05-02
I'm getting this error too. When I checked the /tmp/foobar/ directory created by update-manager the hardy.tar.gz.gpg file the errormessage refers to was not there. Why doesn't update-manager download it?

---

### Post by gwhit918 on 2008-05-02
just like @jonabyte, do-release-upgrade returned "No new release found".  When I added the "-d" parameter, it ran... but returned "Could not calculate the changes" and aborted. 

The additional info provided with the error message mentions "Unofficial software packages not provided by Ubuntu" as a possible cause. Not sure what that would be referring to.

Any thoughts?  Thanks,   --Gary

---

### Post by dendrobates on 2008-05-02
if you are upgrading from a recent release, this should work:

```

sudo apt-get update
sudo apt-get dist-upgrade
```

---

