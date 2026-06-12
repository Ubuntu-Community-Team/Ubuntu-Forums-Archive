---
title: "location of apt-get partial downloads?"
date: 2011-02-25
forum: The Cafe
---

### Post by mips on 2011-02-25
I was busy installing flightgear and it was busy downloading the fgfs-base package when the power went out. I was pretty sure the file had completed downloading at that time because the last time I checked it was sitting at 97% completed.

When I try and install flightgear again it wants to download the entire package again and it's over 300MB. I checked /var/cache/apt/archives/ and the package is not there. The one in /var/cache/apt/archives/partial/ is only 1.6MB so I might have overwritten it when I tried installing after the power failure.

Where would I find the partially downloaded file as I would like to resume it if possible. Can it be recovered from the FS somehow if it was overwritten?

---

### Post by CharlesA on 2011-02-25
Not sure how the partial archives folder works, exactly. Probably the easiest thing to do would be to redownload it again. :(

---

### Post by mips on 2011-02-25
Whoohoo, I found it. Or should I rather say PhotoRec found it.

I did a recovery on the / partition with PhotoRec specifying it only searches for "[X] a    Unix Archive/Debian package"

After the search I sorted based on size and found one .deb file in the 300MB size range which I inspected the contents of with deb-gview and it's fgfs-base!!!

Now I just have to figure out how to restore the file as copying it back to /partial does not seem to help seeing apt-get still wants to download the whole file, grrr. 

I'll figure it out even if I have to try and continue the download with something like wget and then manually install it.

Anybody got any ideas on how to continue the download from [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games

---

### Post by handy on 2011-02-25
Can apt be configured to use wget by default like pacman can?

---

### Post by mips on 2011-02-26
No idea.

---

### Post by handy on 2011-02-26
It would certainly be a good option for large downloads with wget's ability to pick up & continue after an interruption.

I used to use wget in pacman, as for some temporary reason I needed to, to do my Arch system upgrades. wget was probably a little slower than pacman, but it surely was reliable. Still, when it was set as the download tool for pacman it downloaded the file & then pacman installed it as per usual, which was pretty cool.

---

### Post by mips on 2011-02-26
You need to change your avatar back to the old one :D
I'm very much into visual association so your new avatar throws me off a bit.

---

### Post by handy on 2011-02-26
> **mips said:**
> You need to change your avatar back to the old one :D
I'm very much into visual association so your new avatar throws me off a bit.

Unlike yours & my old Van Gogh, the current one is a painting of me that someone I met when travelling a while back asked me if they could do later from a photo!!!

Which is most certainly a first.

I'm still getting used to it myself after all these years. lol

P.S. I'm very much a visual person too.

---

### Post by mips on 2011-02-26
Do you have a bigger pic of the painting, would not mind seeing it. PM or email me if you don't want to share in the open.

---

### Post by mips on 2011-02-26
So anybody got any idea how I can resume this download from the getdeb repo using something like wget.

I cannot seem to browse the archive in order to specify a correct like for wget.

Edit:

I did a google search for the package and did a 

wget -c [http://archive.getdeb.net/getdeb/ubuntu/pool/games/f/fgfs-base/fgfs-base_2.0.0-1~getdeb1_all.deb](http://archive.getdeb.net/getdeb/ubuntu/pool/games/f/fgfs-base/fgfs-base_2.0.0-1~getdeb1_all.deb)

Irony is the remaining part was so small it took less than 10sec to download....

---

### Post by mips on 2011-02-26
This looks like a never ending problem, I now get this:


> xxxx@obelix:~/Desktop$ sudo apt-get -f install fgfs-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fgfs-base
0 upgraded, 1 newly installed, 0 to remove and 298 not upgraded.
22 not fully installed or removed.
Need to get 0B/316MB of archives.
After this operation, 566MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  fgfs-base
Install these packages without verification [y/N]? y
(Reading database ... 198337 files and directories currently installed.)
Unpacking fgfs-base (from .../fgfs-base_2.0.0-1~getdeb1_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid stored block lengths'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/fgfs-base_2.0.0-1~getdeb1_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/games/FlightGear/Airports/apt.dat.gz'
Errors were encountered while processing:
 /var/cache/apt/archives/fgfs-base_2.0.0-1~getdeb1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xxxx@obelix:~/Desktop$ 

---

