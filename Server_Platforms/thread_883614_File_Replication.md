---
title: "File Replication"
date: 2008-08-08
forum: Server Platforms
---

### Post by PACSFerret on 2008-08-08
Hi.. Does anyone have any experience with file replication?  The background to my question is this: After upgrading our SAN we have SAN-hardware-level replication across two sites for our critical servers, but this has left us with the 'old' SAN (9TB) which doesn't have the same capability.  

However I'd like to do the same thing with the old SAN - have copy-on-write across two different servers to use for disaster tolerance (at least for one service).  Looking into the options OpenAFS seems to be the best but it doesn't feel like I'd be using it 'as designed'.

The service I'm looking to do this with is fairly storage intensive - multi-TB with 100M+ individual files.

Any thoughts welcome.

---

### Post by Cadmus on 2008-08-08
I've been doing some research into this sort of CoLo stuff and it seems (if youve got a fast line between the sites) that GlusterFS is getting very mature for this kind of stuff.

---

### Post by PACSFerret on 2008-08-08
GlusterFS came second in my list - one of my use cases was the 'primary' site going awol for a period, and the secondary site continuing to add data. It seemed to me that OpenAFS has a mechanism for journal replay so 'primary' can catch up when it returns & resume role as primary.  I may be wrong but I didn't see anything in GlusterFS that indicates that.

---

### Post by Cadmus on 2008-08-08
As I understand it the AFR translator does bi-directional (or more) replication

[http://www.gluster.org/docs/index.php/GlusterFS_Translators_v1.3#Automatic_File_Replication_Translator_.28AFR.29]("http://www.gluster.org/docs/index.php/GlusterFS_Translators_v1.3#Automatic_File_Replication_Translator_.28AFR.29")

There's a better example on this page

[http://www.gluster.org/docs/index.php/Understanding_AFR_Translator]("http://www.gluster.org/docs/index.php/Understanding_AFR_Translator")

---

### Post by sharma2008 on 2008-08-08
I am also searching...

---

### Post by PACSFerret on 2008-08-08
Thanks Cadmus. My mistake. it does indeed look like GlusterFS has all I need. I'll crank up a couple of virtual servers & test it out.

---

### Post by Cadmus on 2008-08-11
Thanks! I don't have the resources right now to do that, let us all know what you find out!

---

### Post by PACSFerret on 2008-08-18
Noted upsides:

    * Project wiki is deep and resplendent with documentation and tutorials
    * Architecture effectively &#8216;pipes&#8217; file system features through each other - so combinations of features can be built from mirroring, striping, unification, read-ahead, write-behind, encryption and more.
    * Automagic self-healing if a server drops it&#8217;s pants. (Obviously, after pants have been replaced!)
    * Strong roadmap includes web-based console and HSM (? not according to official roadmap but according to a FAQ).

Downsides:

    *  Runs in UserSpace (FUSE) rather than as a kernel module.  Not sure if this is a significant downer, though - as long as it works.
    * the only documentation is on the wiki.
    * Not included in Ubuntu repositories. There is a &#8216;personal&#8217; repository with a deb package but I don&#8217;t like such sources so I compiled from scratch.  Get tarball, unpack and

        ./configure &#8211;prefix=
        make install

The configure process ended by reporting fuse was absent, which it clearly is not ( /proc/modules) and even tobesuretobesure

    modprobe fuse

Not surprisingly the daemon process failed when started with failure to initialise fuse.  Cause? package libfuse-dev needs to be installed when ./configure process is run.  Other packages required: libtool gcc flex bison byacc.

So the configuration files go to /etc/gclusterfs.  Set up a two-way replication config between two servers, in these cases with the base folder at /opt/gfs-ds.  Each server mounts a client to itself at /mnt/rep(1,2) which is the entry point for data itself.

Mixing and matching from a couple of tutorials on the GlusterFS site, one side of the server config (the other side is symmetrical):

    ##############################################
    ###  GlusterFS Server Volume Specification  ##
    ##############################################

    # dataspace on storage2
    volume gfs-ds
    type storage/posix
    option directory /opt/gfs-ds
    end-volume

    # posix locks
    volume gfs-ds-locks
    type features/posix-locks
    subvolumes gfs-ds
    end-volume

    # dataspace on storage1
    volume gfs-storage1-ds
    type protocol/client
    option transport-type tcp/client
    option remote-host 10.17.100.110      # storage network
    option remote-subvolume gfs-ds
    option transport-timeout 10           # value in seconds; it should be set relatively low
    end-volume

    # automatic file replication translator for dataspace
    volume gfs-ds-afr
    type cluster/afr
    subvolumes gfs-ds-locks gfs-storage1-ds         # local and remote dataspaces
    end-volume

    # the actual exported volume
    volume gfs
    type performance/io-threads
    option thread-count 8
    option cache-size 64MB
    subvolumes gfs-ds-afr
    end-volume

    # finally, the server declaration
    volume server
    type protocol/server
    option transport-type tcp/server
    subvolumes gfs
    # storage network access only
    option auth.ip.gfs-ds.allow 10.*.*.*,127.0.0.1
    option auth.ip.gfs.allow 10.*.*.*
    end-volume

and a client config (again, symmetrical):

    #############################################
    ##  GlusterFS Client Volume Specification  ##
    #############################################

    # the exported volume to mount                    # required!
    volume localgfs
    type protocol/client
    option transport-type tcp/client
    option remote-host 10.17.100.111
    option remote-subvolume gfs                     # exported volume
    option transport-timeout 10                     # value in seconds, should be relatively low
    end-volume

So on each side,

    glusterfsd -f /etc/glusterfs/glusterfs-server.vol
    glusterfs -f /etc/glusterfs/glusterfs-client.vol /mnt/rep{1,2}

Snip snip and Bob&#8217;s your Auntie.

So how does it hang as a disaster tolerance thang?  I took one side down with no warning (power off).  Made some changes to the other side & brought the first back up.  Lo and beyond as soon as the daemon was running and an access point mounted, there were the changes all replicated.

Except not quite.  Glusterfs uses &#8216;lazy healing&#8217;, which means although the existance/metadata of the new files is transparent immediately, the contents themselves are not actually &#8216;healed&#8217;  until the file is opened.  This could be left as-is but carries the risk that if the data on server B is lost before healing occurs, the data is, in fact, eh, gone. An easy way to gee-up the lazy healing is:

    find /mnt/rep -type f -exec head -n 1 {} \;

    or, more efficiently (limiting file touches to last n days):

    find /mnt/rep -type f -mtime -1 -exec head -c 1 {} > /dev/null \;

So far it looks good on a small sandbox.  Lets do a stress-test.  I'll be back.

---

### Post by HermanAB on 2008-08-18
I think the latest version of NFS can also do what you need.

Cheers,

Herman

---

### Post by PilotJLR on 2008-08-22
I don't have a free or FOSS suggestion for you... but if you can present a LUN on the new SAN at DR, then EMC RecoverPoint will take care of the replication. It does heterogeneous array based replication over IP.
It's also quite expensive.  :-)

But it's good stuff if you have mission critical DR replication needs.

---

### Post by say2sky on 2008-10-13
thx for this useful info. 

I have noted that GlusterFS has been included in intrepid Ubuntu repositories.

I am looking for a solution of real-time sync all data in different PCs through internet.
I think GlusterFS can meet my requirements but I don't know if the data transfer on internet with any kind of encryption protocol or it can be used combined with ssh.

---

### Post by promodus on 2008-10-13
why not use drbd ?

---

### Post by say2sky on 2008-10-14
> **promodus said:**
> why not use drbd ?

thanks a lot for your info. drbd look great. I will try it and I also hope to know if data can be encrypted when using drbd between systems through internet.

---

### Post by PACSFerret on 2008-10-14
I wasn't aware drbd could encrypt. Is that recent?  Glusterfs doesn't encrypt (unless you count ROT-13) but there are intentions in the roadmap. One of the things I like about glusterfs is the modular, pipe-like way something like encryption can be included.
Another option designed to work over the internet is [cleversafe]("http://www.cleversafe.org")

---

### Post by promodus on 2008-10-14
[http://www.stunnel.org/](http://www.stunnel.org/)

You can encrypt any network network traffic you want.
Either directly or indirectly.

---

### Post by say2sky on 2008-10-14
I haven't think it clear how to combine ssl with drbd. 

I know in linux cryptsetup is used to map device to encrypt data in drive.

Now I am trying to found if it is possible to use cryptsetup above drbd just like use cryptsetup above raid. if possible then all the data transfer in internet will be encrypted.

---

### Post by PACSFerret on 2009-01-07
Well.. having promised to report back here is some experience.

I have a pair of servers replicating using GlusterFS - a total of 640GB in around 47000 files.  All files were generated on ServerA and replicated to ServerB without a hitch, and the arrangement has been running smoothly for around 2 months. 

Performance, wise, there is a hit.  I havn't done a benchmark for writing but for reading, I ran the following command:

find . -type f -exec hexdump -n 50 {} >> /dev/null ';' 

.. on the 'raw' partition as well as the Glusterfs mount point (i.e. IO being piped through GlusterFS).
'raw' partition:  1071 seconds
Through GlusterFS: 4302 seconds

There was nothing else running on the server at the time, so the discrepancy is all glusterFS (although, lets face it - it's not an entirely rigorous bench ;-) )

---

