---
title: "How to detect free space on FTP"
date: 2010-03-21
forum: Server Platforms
---

### Post by muhahacz on 2010-03-21
Hi,i have question... 
How to detect free space on FTP? df doesnt work. I have to mount FTP a then try df ?
Thanks.Sry for my engish

Or you can help me with script. I tried this without ftp, but now, i have to add FTP
```


        FS="path to ftp" // maybe lftp -u user:pass adress:/directory ,but doesnt work
//Detect free space on  $FS 
        USAGE=`df -h $FS | awk '{ print $5 }C | sed "s/Volno//;s/%//"`
        PERCENT=90

        echo "USAGE = $USAGE"

    if [ $USAGE -lt $PERCENT ] ;
        then
                  set $(date)
                  cp -r -v /home/lukas/soft/backup/ $FS/backup_$7_$3_$2_$6_$4
          
        else

           delete file
              find $FS -type f -print | xargs ls -t | tail -1 | xargs rm -r
        
           delete directory
              find $FS/backup* -type d -print | xargs ls -d | head -1 | xargs rmdir
              fi              


```

---

### Post by KB1JWQ on 2010-03-22
There is no facility in FTP to show available disk space.

---

### Post by HermanAB on 2010-03-23
on some FTP system you can invoke a shell and run df.

---

### Post by KB1JWQ on 2010-03-23
> **HermanAB said:**
> on some FTP system you can invoke a shell and run df.

I didn't know that-- and I'm having trouble finding a reference to it (it's not in the RFCs at any rate).  Can you point me to an ftp daemon that supports this?

---

