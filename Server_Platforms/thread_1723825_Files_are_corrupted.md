---
title: "Files are corrupted"
date: 2011-04-07
forum: Server Platforms
---

### Post by Sitix on 2011-04-07
Hey guys,

I'm running an Ubuntu server (10.04 LTS 32-bit, on a 32-bit system) and frankly nothing concerning files, seems to work as it should.

- I can't upload images, because after that they seem to be corrupted
- If I zip something on the server and try to open it elsewhere, it says the checksum isn't correct
- I can't export from MySQL from the server and import to another because apparently it contains errors

And who knows what else is coming :P

Does anyone have a clue of what's going on here? I updated everything to the last version of the software, so that can't be it.

Thanks in advance for helping!

---

### Post by falko on 2011-04-07
Did you check if your hard drive is ok?

---

### Post by Sitix on 2011-04-07
Well, it's a brand new system and the harddrive works fine for what I know. I run a search engine on it, and it manages fine with the database and such.

The problems come when I want to import or export something from/to another computer. So I guess it has something to do with my filesystem and not really my hard drive?

I just can't think of anything that could be wrong with it...

---

### Post by iissmart on 2011-04-07
> **Sitix said:**
> Hey guys,

- I can't upload images, because after that they seem to be corrupted
- If I zip something on the server and try to open it elsewhere, it says the checksum isn't correct
- I can't export from MySQL from the server and import to another because apparently it contains errors

For #2 and #3, how are you transferring the files to the other location? FTP? SFTP? HTTP?

---

### Post by Sitix on 2011-04-07
> **iissmart said:**
> For #2 and #3, how are you transferring the files to the other location? FTP? SFTP? HTTP?

I used mysqldump, saved it in /var/www/, then used wget [http://blabla](http://blabla) to retrieve it on the other server. So that would be HTTP.

But the problem is in the conversion I think. If I upload through FTP, the images get corrupted. ASCII text doesn't. Could it have something to do with binary file format not being processed correctly or something?

I managed to get my database on another server by now, by exporting through phpmyadmin, saving to my desktop computer, then uploading to another server. That somehow works...

---

### Post by iissmart on 2011-04-07
Not sure about your mysql situation, but #2 sounds like your FTP server or client isn't switching to Binary mode before the transfer (of non-text files). Try forcing it in your FTP client beforehand, and see if zip files open correctly. Or, switch to SFTP, which adds security and a guarantee of no corruption with a slight reduction in performance/transfer speed.

---

### Post by mikeygstl on 2011-04-07
> **iissmart said:**
> Not sure about your mysql situation, but #2 sounds like your FTP server or client isn't switching to Binary mode before the transfer (of non-text files). Try forcing it in your FTP client beforehand, and see if zip files open correctly. Or, switch to SFTP, which adds security and a guarantee of no corruption with a slight reduction in performance/transfer speed.

Agreed, although I would simply try forcing BINary through the command line ftp client first, i.e.:

```

ftp somehost.com
user someuser
pass somepass
cd wherever
lcd wherever 
bin
put/get whatever

```

---

