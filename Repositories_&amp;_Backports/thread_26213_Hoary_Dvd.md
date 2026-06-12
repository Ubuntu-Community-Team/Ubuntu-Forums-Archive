---
title: "Hoary Dvd"
date: 2005-04-12
forum: Repositories &amp; Backports
---

### Post by andreabg on 2005-04-12
Hello, 
I cannot connect my ibook to internet and I want to install Ubuntu and also some extra software that I0ve seen in the list of file on DVD.

I decided to download DVD for ppc and i386 (in order to have 2 pc with ubuntu \\:D/ ) I've tried this link [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) 

Everything seem to be working, but when i try to download it it's extremely fast and I've got a 0bite file.

What's happened?

Can someone help me to have a DVD with everything?

Thanks
Andrea

---

### Post by SFN on 2005-04-14
Just in case this helps to diagnose the problem:

I was having the same problem at home last night. Tried at work. I'm behind a firewall there and received the following message.

"Request denied for [http://82.211.81.155:80/dvd/current/hoary-dvd-i386.iso:](http://82.211.81.155:80/dvd/current/hoary-dvd-i386.iso:) Invalid HTTP "Content-Length" header"
Just for grins, I tried the AMD64 and PowerPC ISOs. Same thing.

So it does appear that the ISOs are corrupted. The torrents seem to be fine but slow to download.

---

### Post by floogy on 2005-04-14
Hello all,

the same thing here: The download with bittorrent stuck at 33% , I got only one peer and none of the others in the swarm got the complete download.

The other try: 
peers: 0 connected 3 in swarm
seeds: 0 connected 4 in swarm
:(

I tried these ones:
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
[http://ftp2.kgt.org/pub/ubuntu.com/dvd-iso](http://ftp2.kgt.org/pub/ubuntu.com/dvd-iso)

[http://torrent.ubuntu.com:6969/file?info_hash=%00/%5E%7D%1F%CC%04%11%3D%2C%AC%3C%CA%A6%7C%053%00%D0%A0](http://torrent.ubuntu.com:6969/file?info_hash=%00/%5E%7D%1F%CC%04%11%3D%2C%AC%3C%CA%A6%7C%053%00%D0%A0)
[http://torrent.ubuntu.com:6969/file?info_hash=%E1A%0A%10/%88%15%D3%BD%0E%10%CC%3A%E0%C6%28%1F%EA%B3L](http://torrent.ubuntu.com:6969/file?info_hash=%E1A%0A%10/%88%15%D3%BD%0E%10%CC%3A%E0%C6%28%1F%EA%B3L)

The iso ([http://cdimage.ubuntulinux.org/dvd/current/hoary-dvd-amd64.iso](http://cdimage.ubuntulinux.org/dvd/current/hoary-dvd-amd64.iso))  download didn't work at all, but today I got this:

Thu Apr 14 15:51:20 2005 File size unknown, can't start other parts.

So I expect a broken download. I will see...

bye

floogy

---

### Post by mark on 2005-04-14
I downloaded the DVD image from [ftp://cdimage.ubuntu.com/cdimage/dvd/current](ftp://cdimage.ubuntu.com/cdimage/dvd/current) - but it took a couple of gFTP sessions, due to the file size (and, I assume, initial server demand on the release date).

The .ISO checksummed okay, burned it & booted & ran the integrity check, which was also okay.  I plan to try an install this weekend - if I have any problems, I'll try to post here.

---

### Post by floogy on 2005-04-15
Hello Mark,

You're the happy one. I got still errors in FlashGet on winXP, but wget seems to be ok.

Does somebody know if its possible to complete a download with wget wich was started by FlashGet?

FlashGet fetched ~2GiB, and now I got this:

Fri Apr 15 08:43:29 2005 Connecting cdimage.ubuntulinux.org [IP=82.211.81.155:80]
Fri Apr 15 08:43:29 2005 Connected.
Fri Apr 15 08:43:29 2005 GET /dvd/current/hoary-dvd-amd64.iso HTTP/1.1
Fri Apr 15 08:43:29 2005 Host: cdimage.ubuntulinux.org
Fri Apr 15 08:43:29 2005 Accept: */*
Fri Apr 15 08:43:29 2005 Referer: [http://cdimage.ubuntulinux.org/dvd/current](http://cdimage.ubuntulinux.org/dvd/current)
Fri Apr 15 08:43:29 2005 User-Agent: Mozilla/4.0 (compatible; MSIE 5.00; Windows 98)
Fri Apr 15 08:43:29 2005 Range: bytes=-2077053383-
Fri Apr 15 08:43:29 2005 Pragma: no-cache
Fri Apr 15 08:43:29 2005 Cache-Control: no-cache
Fri Apr 15 08:43:29 2005 Connection: close
Fri Apr 15 08:43:29 2005 HTTP/1.1 416 Requested Range Not Satisfiable
Fri Apr 15 08:43:29 2005 Date: Fri, 15 Apr 2005 06:43:29 GMT
Fri Apr 15 08:43:29 2005 Server: Apache/2.1.3 (Ubuntu)
Fri Apr 15 08:43:29 2005 Connection: close
Fri Apr 15 08:43:29 2005 Transfer-Encoding: chunked
Fri Apr 15 08:43:29 2005 Content-Type: text/html; charset=iso-8859-1
Fri Apr 15 08:43:29 2005 Error occured!
Fri Apr 15 08:43:29 2005 Wait 5 second for retry
Fri Apr 15 08:43:35 2005 Connecting cdimage.ubuntulinux.org [IP=82.211.81.155:80]

Apache error codes:
416 - Requested Range Not Satisfiable
A 416 status code indicates that the server was unable to fulfill the request. This may be, for example, because the client asked for the 800th-900th bytes of a document, but the document was only 200 bytes long.

Bizarre: FlashGet expects to download minus 1443151872 bytes and stuck at -148% #-/

wget seems to be fine:
wget [http://cdimage.ubuntulinux.org/dvd/current/hoary-dvd-amd64.iso](http://cdimage.ubuntulinux.org/dvd/current/hoary-dvd-amd64.iso)
--08:30:40--  [http://cdimage.ubuntulinux.org:80/dvd/current/hoary-dvd-amd64.iso](http://cdimage.ubuntulinux.org:80/dvd/current/hoary-dvd-amd64.iso)
           => `hoary-dvd-amd64.iso'
Connecting to cdimage.ubuntulinux.org:80... connected!
HTTP request sent, awaiting response... 200 OK
Length: -1,443,151,872 [application/octet-stream]

***but: ------^^^^^^^^   the iso seems to be corrupt! ***

    0K -> .......... .......... .......... .......... .......... [  0%]
   50K -> .......... .......... .......... .......... .......... [  0%]

hmm. I tried now to complete the  2GiB downloaded by FlashGet , but with no luck:

wget -c  [http://cdimage.ubuntulinux.org:80/dvd/current/hoary](http://cdimage.ubuntulinux.org:80/dvd/current/hoary)
-dvd-amd64.iso
--09:51:44--  [http://cdimage.ubuntulinux.org:80/dvd/current/hoary-dvd-amd64.iso](http://cdimage.ubuntulinux.org:80/dvd/current/hoary-dvd-amd64.iso)
           => `hoary-dvd-amd64.iso'
Connecting to cdimage.ubuntulinux.org:80... connected!
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable
09:51:44 ERROR 416: Requested Range Not Satisfiable.

Interesting. Look at the file length. They are all negative!:

wget [http://cdimage.ubuntulinux.org/dvd/current/hoary-dvd-amd64.iso](http://cdimage.ubuntulinux.org/dvd/current/hoary-dvd-amd64.iso)
--09:58:49--  [http://cdimage.ubuntulinux.org:80/dvd/current/hoary-dvd-amd64.iso](http://cdimage.ubuntulinux.org:80/dvd/current/hoary-dvd-amd64.iso)
           => `hoary-dvd-amd64.iso'
Connecting to cdimage.ubuntulinux.org:80... connected!
HTTP request sent, awaiting response... 200 OK
Length: -1,443,151,872 [application/octet-stream]

wget [http://cdimage.ubuntu.com/dvd/20050407.1/hoary-dvd-amd64.iso](http://cdimage.ubuntu.com/dvd/20050407.1/hoary-dvd-amd64.iso)
--10:00:35--  [http://cdimage.ubuntu.com:80/dvd/20050407.1/hoary-dvd-amd64.iso](http://cdimage.ubuntu.com:80/dvd/20050407.1/hoary-dvd-amd64.iso)
           => `hoary-dvd-amd64.iso.1'
Connecting to cdimage.ubuntu.com:80... connected!
HTTP request sent, awaiting response... 200 OK
Length: -1,443,155,968 [application/octet-stream]

wget [http://cdimage.ubuntu.com/dvd/20050407.2/hoary-dvd-amd64.iso](http://cdimage.ubuntu.com/dvd/20050407.2/hoary-dvd-amd64.iso)
--10:00:47--  [http://cdimage.ubuntu.com:80/dvd/20050407.2/hoary-dvd-amd64.iso](http://cdimage.ubuntu.com:80/dvd/20050407.2/hoary-dvd-amd64.iso)
           => `hoary-dvd-amd64.iso.2'
Connecting to cdimage.ubuntu.com:80... connected!
HTTP request sent, awaiting response... 200 OK
Length: -1,443,155,968 [application/octet-stream]

wget [http://cdimage.ubuntu.com/dvd/20050407.3/hoary-dvd-amd64.iso](http://cdimage.ubuntu.com/dvd/20050407.3/hoary-dvd-amd64.iso)
--10:01:02--  [http://cdimage.ubuntu.com:80/dvd/20050407.3/hoary-dvd-amd64.iso](http://cdimage.ubuntu.com:80/dvd/20050407.3/hoary-dvd-amd64.iso)
           => `hoary-dvd-amd64.iso.3'
Connecting to cdimage.ubuntu.com:80... connected!
HTTP request sent, awaiting response... 200 OK
Length: -1,443,151,872 [application/octet-stream]

The i386-iso got the right content length:
Fri Apr 15 10:09:53 2005 Content-Length: 2929047552

ciao

floogy

---

### Post by SFN on 2005-04-15
Looks like it's working now. Downloading the ISO with good speed.

---

