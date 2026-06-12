---
title: "ssh is slow ..."
date: 2005-11-16
forum: Server Platforms
---

### Post by dbee on 2005-11-16
I'm copying files from one computer to another on my LAN, my ssh is running at about 4MB/s ? 

What's the story ?

---

### Post by ofek on 2005-11-16
I don't think its a ssh problem.
It should be something regarding your network. (like network setting)

---

### Post by dbee on 2005-11-16
> 
I don't think its a ssh problem.
It should be something regarding your network. (like network setting)


err ... care to elaborate there ofek ?
what could slow down a LAN exactly ? ... both systems are idle and they are connected through a home router. 
Can you think of anything I should try ?

Thanks :)

---

### Post by grendelkhan on 2005-11-16
That's insanely slow - do either of these machines upload/download that slow normally?   Have you tried a regular ftp rather than a sftp?

---

### Post by dbee on 2005-11-16
```

That's insanely slow - do either of these machines upload/download that slow normally? Have you tried a regular ftp rather than a sftp?

```
... they both download from the Internet with no problems at all

... scp doesn't use ftp (as far as I know), so I don't know what good that would do me ?

thanks :)

---

### Post by LordHunter317 on 2005-11-16
What are the specifications of the machines?  Slow CPUs can yield slow speeds when doing AES.

---

### Post by hostile on 2005-11-16
Over a LAN, using sftp/scp, 4 MB/s is just fine. There is a lot of overhead when using encryption, especially AES/MD5.

---

### Post by dbee on 2005-11-16
The machine is a P3, 128MB so it's kind of an oldie. 
I'm in the middle of transferring files to my new AMD64, 1GB ...

---

### Post by Glut on 2005-11-17
[QUOTE=hostile]Over a LAN, using sftp/scp, 4 MB/s is just fine. There is a lot of overhead when using encryption, especially AES/MD5.[/QUOTE]
Although there is an overhead using encryption, in the case of scp this overhead is placed entirely on the computing power of the machine, rather than the throughput of the network. 
With a pair of resonably modern 2gz P4s I can manage double that. So I'd put the blame squarely on the P3.

---

