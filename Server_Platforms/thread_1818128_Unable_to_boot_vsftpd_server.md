---
title: "Unable to boot vsftpd server"
date: 2011-08-04
forum: Server Platforms
---

### Post by olavgal on 2011-08-04
Hello,

I'm running ubuntu 11.04 on two computers, and I had two ftp-servers running fine and well. But then, after a computer reboot, I'm not able to boot the servers anymore.

```
root@kjellern-lima:~# service vsftpd start
vsftpd start/running, process 2552
```It says it starts running, but if I try to connect to it, or run:
```
root@kjellern-lima:~# netstat -a | grep ftp
```nothing happens


Anyone got any ideas what the issue might be?

---

### Post by skinnyquiver on 2011-08-04
Can you post the last 25 lines of your log

tail -n 25 /var/log/vsftpd.log

---

### Post by olavgal on 2011-08-04
```
Thu Aug  4 03:38:01 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E01 'Pilot Part 1'.mkv", 165272819 bytes, 1544.41Kbyte/sec
Thu Aug  4 03:39:51 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E02 'Pilot Part 2'.mkv", 157687699 bytes, 1403.66Kbyte/sec
Thu Aug  4 03:41:19 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E03 'Tabula Rasa'.mkv", 169887644 bytes, 1897.84Kbyte/sec
Thu Aug  4 03:42:36 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E04 'Walkabout'.mkv", 166998039 bytes, 2097.37Kbyte/sec
Thu Aug  4 03:43:54 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E05 'White Rabbit'.mkv", 165757583 bytes, 2073.55Kbyte/sec
Thu Aug  4 03:45:20 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E06 'House of the Rising Sun'.mkv", 167283404 bytes, 1900.95Kbyte/sec
Thu Aug  4 03:46:51 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E07 'The Moth'.mkv", 169361446 bytes, 1829.85Kbyte/sec
Thu Aug  4 03:48:21 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E08 'Confidence Man'.mkv", 169136007 bytes, 1826.25Kbyte/sec
Thu Aug  4 03:49:54 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E09 'Solitary'.mkv", 168934486 bytes, 1779.65Kbyte/sec
Thu Aug  4 03:51:21 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E10 'Raised by Another'.mkv", 167566676 bytes, 1890.66Kbyte/sec
Thu Aug  4 03:52:47 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E11 'All the Best Cowboys Have Daddy Issues'.mkv", 165151312 bytes, 1874.82Kbyte/sec
Thu Aug  4 03:54:15 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E12 'Whatever the Case May Be'.mkv", 169044790 bytes, 1872.61Kbyte/sec
Thu Aug  4 03:55:42 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E13 'Hearts and Minds'.mkv", 169304233 bytes, 1916.43Kbyte/sec
Thu Aug  4 03:57:07 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E14 'Special'.mkv", 169264278 bytes, 1936.17Kbyte/sec
Thu Aug  4 03:58:32 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E15 'Homecoming'.mkv", 162848296 bytes, 1877.26Kbyte/sec
Thu Aug  4 04:00:02 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E16 'Outlaws'.mkv", 169515867 bytes, 1842.18Kbyte/sec
Thu Aug  4 04:01:37 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E17 '...In Translation'.mkv", 168527010 bytes, 1727.30Kbyte/sec
Thu Aug  4 04:03:14 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E18 'Numbers'.mkv", 168729411 bytes, 1711.63Kbyte/sec
Thu Aug  4 04:04:49 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E19 'Deus Ex Machina'.mkv", 167044899 bytes, 1705.73Kbyte/sec
Thu Aug  4 04:06:26 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E20 'Do No Harm'.mkv", 169329045 bytes, 1716.05Kbyte/sec
Thu Aug  4 04:08:04 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E21 'The Greater Good'.mkv", 169201652 bytes, 1680.69Kbyte/sec
Thu Aug  4 04:09:42 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E22 'Born to Run'.mkv", 169153003 bytes, 1694.13Kbyte/sec
Thu Aug  4 04:11:21 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E23 'Exodus Part 1'.mkv", 169503738 bytes, 1676.37Kbyte/sec
Thu Aug  4 04:12:57 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E24 'Exodus Part 2'.mkv", 168464196 bytes, 1709.62Kbyte/sec
Thu Aug  4 04:14:34 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/serier/Lost Season 1 [Siz3King]/Lost.S01E25 'Exodus Part 3'.mkv", 169375350 bytes, 1712.87Kbyte/sec
Thu Aug  4 04:14:34 2011 [pid 3] [olav] OK DOWNLOAD: Client "192.168.10.102", "/home/ftp/readme.txt", 423 bytes, 6.10Kbyte/sec
Thu Aug  4 04:19:34 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 04:19:34 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 04:24:34 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 04:24:34 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 04:29:35 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 04:29:35 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 04:29:35 2011 [pid 3] [olav] OK MKDIR: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG"
Thu Aug  4 04:36:31 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG.avi", 734406624 bytes, 1723.97Kbyte/sec
Thu Aug  4 04:36:31 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/HPDH1-ETRG.nfo", 8384 bytes, 1092.25Kbyte/sec
Thu Aug  4 04:36:34 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/SaMple.avi", 6112572 bytes, 1734.57Kbyte/sec
Thu Aug  4 04:36:35 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/Torrent downloaded from extratorrent.com.txt", 85 bytes, 22.97Kbyte/sec
Thu Aug  4 04:36:35 2011 [pid 3] [olav] OK MKDIR: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/SubFiles"
Thu Aug  4 04:36:35 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/SubFiles/Harry Potter7-ETRG.idx", 372396 bytes, 1516.65Kbyte/sec
Thu Aug  4 04:36:47 2011 [pid 3] [olav] OK UPLOAD: Client "192.168.10.102", "/home/ftp/filmer/Harry Potter and the Deathly Hallows Part 1[2010]DVDRip XviD-ExtraTorrentRG/SubFiles/Harry Potter7-ETRG.sub", 20815872 bytes, 1730.97Kbyte/sec
Thu Aug  4 13:26:12 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 13:26:13 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 13:26:13 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 13:26:13 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 13:26:14 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 13:26:14 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 13:26:14 2011 [pid 3] [olav] OK DOWNLOAD: Client "192.168.10.102", "/home/ftp/readme.txt", 423 bytes, 20.87Kbyte/sec
Thu Aug  4 13:26:51 2011 [pid 2] CONNECT: Client "192.168.10.102"
Thu Aug  4 13:26:51 2011 [pid 1] [olav] OK LOGIN: Client "192.168.10.102"
Thu Aug  4 13:26:58 2011 [pid 3] [olav] FAIL RENAME: Client "192.168.10.102", "/home/ftp/Breaking Bad Season 1-3 /home/ftp/serier/Breaking Bad Season 1-3"
Thu Aug  4 13:27:43 2011 [pid 3] [olav] FAIL RENAME: Client "192.168.10.102", "/home/ftp/Breaking Bad Season 1-3 /home/ftp/serier/Breaking Bad Season 1-3"
```

Basically a load of uploads..

---

### Post by skinnyquiver on 2011-08-04
is this from the computer that it is not starting on? I forgot to specify that we need this log from the one that is not working I was expecting to see errors in your logs if it is not starting.

---

### Post by olavgal on 2011-08-04
None of the servers are starting (Same problem on both computers), I'll check the other one for errors aswell.

Edit: Exactly the same thing there, no errors

---

### Post by skinnyquiver on 2011-08-04
> **olavgal said:**
> None of the servers are starting (Same problem on both computers), I'll check the other one for errors aswell.

Edit: Exactly the same thing there, no errors

what happens when you run 
/etc/init.d/vsftpd stop
and 
/etc/init.d/vsftpd start

---

### Post by olavgal on 2011-08-04
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd
vsftpd start/running, process 3563
```I get that message, and the server still won't start running.

Edit: I get the same message when trying to stop the server, except the start = stop of course.

---

### Post by olavgal on 2011-08-04
I tried uninstalling vsftpd and setting the config file to default, but no luck, still won't start :(

---

### Post by olavgal on 2011-08-09
A small update. I figured out what the problem was, after reinstalling ubuntu quite a few times... Well, I found out that the server wouldn't boot if I installed it before I updated the machine. I have no idea how to fix it, but what I did is just update first.

---

