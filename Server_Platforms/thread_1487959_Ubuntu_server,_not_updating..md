---
title: "Ubuntu server, not updating."
date: 2010-05-19
forum: Server Platforms
---

### Post by robofighter on 2010-05-19
When ever I try to get my Ubuntu server 10.04, the thing refuses to acquire any updates. 

If it helps, tinyproxy and dansguardian is installed on the server.

Anyway here is what the sessions shows when ever I try to update it:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
99% [1 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
99% [2 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
99% [3 Sources bzip2 0B] [Waiting for headers] [Connecting to 127.0.0.1 (127.0.bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
99% [4 Sources bzip2 0B] [Waiting for headers] [Waiting for headers]  871B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
99% [5 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
99% [6 Sources bzip2 0B] [Waiting for headers] [Waiting for headers]  871B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
99% [7 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
99% [8 Sources bzip2 0B] [Waiting for headers]                        871B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
99% [9 Packages bzip2 0B] [Waiting for headers]                     2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
99% [10 Packages bzip2 0B] [Waiting for headers]                    2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
99% [11 Sources bzip2 0B] [Waiting for headers]                     2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
99% [12 Sources bzip2 0B] [Waiting for headers]                     2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
99% [13 Packages bzip2 0B] [Waiting for headers]                    2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
99% [14 Sources bzip2 0B] [Waiting for headers]                     2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
99% [15 Packages bzip2 0B] [Waiting for headers]                    2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
99% [16 Sources bzip2 0B]                                           2,520B/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 42.0kB in 18s (2,317B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cdenley on 2010-05-19
Post this output.
```

echo -e "GET /ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2 HTTP/1.0\nHost: security.ubuntu.com\n"|nc -q 1 -w 4 security.ubuntu.com 80|strings|head -n 30

```

---

### Post by robofighter on 2010-05-19
```
 HTTP/1.1 200 OK
Date: Wed, 19 May 2010 21:29:55 GMT
Server: Apache/2.2.8 (Ubuntu)
Last-Modified: Thu, 13 May 2010 12:08:43 GMT
ETag: "14b6-486789eaa48c0"
Accept-Ranges: bytes
Content-Length: 5302
Cache-Control: max-age=-548772, s-maxage=3300, proxy-revalidate
Expires: Thu, 13 May 2010 13:03:43 GMT
Connection: close
Content-Type: application/x-bzip2
BZh91AY&SY
__gy
2=OS
jQ-|
jm#[N
!YtD-
F	PF
GCr_
-PV\V
8xT#9
|^h.
H2_Y
Y@A=
NXA 
"gL6)
rAhx!
5:UJ
I#ov
TFZ(

```

---

### Post by cdenley on 2010-05-19
You appear to be downloading a valid bz2 file from [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2) now. Try using apt-get again.

---

### Post by robofighter on 2010-05-20
same message
```

Get:1 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Get:2 http://security.ubuntu.com lucid-security Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com lucid-updates Release.gpg [189B]
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Get:4 http://security.ubuntu.com lucid-security/main Packages
99% [4 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/main Packages          
  Sub-process /bin/bzip2 returned an error code (2)
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Get:5 http://security.ubuntu.com lucid-security/restricted Packages
99% [5 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/restricted Packages    
  Sub-process /bin/bzip2 returned an error code (2)
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Get:6 http://security.ubuntu.com lucid-security/main Sources                   
99% [6 Sources bzip2 0B] [Waiting for headers] [Waiting for headers]  942B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/main Sources                     
  Sub-process /bin/bzip2 returned an error code (2)
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:7 http://security.ubuntu.com lucid-security/restricted Sources             
99% [7 Sources bzip2 0B] [Waiting for headers] [Connecting to 127.0.0.1 (127.0.bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/restricted Sources               
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com lucid Release                                 
Get:8 http://security.ubuntu.com lucid-security/universe Packages              
99% [8 Packages bzip2 0B] [Release gpgv 57.2kB] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/universe Packages                
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Get:9 http://security.ubuntu.com lucid-security/universe Sources               
99% [9 Sources bzip2 0B] [Waiting for headers] [Waiting for headers]  942B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/universe Sources                 
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Get:10 http://security.ubuntu.com lucid-security/multiverse Packages           
99% [10 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/multiverse Packages     
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Get:11 http://security.ubuntu.com lucid-security/multiverse Sources            
99% [11 Sources bzip2 0B] [Waiting for headers]                       942B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com lucid-security/multiverse Sources               
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Get:12 http://us.archive.ubuntu.com lucid-updates/main Packages                
99% [12 Packages bzip2 0B] [Waiting for headers]                    2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/main Packages                   
  Sub-process /bin/bzip2 returned an error code (2)
Get:13 http://us.archive.ubuntu.com lucid-updates/restricted Packages          
99% [13 Packages bzip2 0B] [Waiting for headers]                    2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/restricted Packages             
  Sub-process /bin/bzip2 returned an error code (2)
Get:14 http://us.archive.ubuntu.com lucid-updates/main Sources                 
99% [14 Sources bzip2 0B] [Waiting for headers]                     2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/main Sources                    
  Sub-process /bin/bzip2 returned an error code (2)
Get:15 http://us.archive.ubuntu.com lucid-updates/restricted Sources           
99% [15 Sources bzip2 0B] [Waiting for headers]                     2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/restricted Sources              
  Sub-process /bin/bzip2 returned an error code (2)
Get:16 http://us.archive.ubuntu.com lucid-updates/universe Packages            
99% [16 Packages bzip2 0B] [Waiting for headers]                    2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/universe Packages               
  Sub-process /bin/bzip2 returned an error code (2)
Get:17 http://us.archive.ubuntu.com lucid-updates/universe Sources             
99% [17 Sources bzip2 0B] [Waiting for headers]                     2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/universe Sources                
  Sub-process /bin/bzip2 returned an error code (2)
Get:18 http://us.archive.ubuntu.com lucid-updates/multiverse Packages          
99% [18 Packages bzip2 0B] [Waiting for headers]                    2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/multiverse Packages             
  Sub-process /bin/bzip2 returned an error code (2)
Get:19 http://us.archive.ubuntu.com lucid-updates/multiverse Sources           
99% [19 Sources bzip2 0B]                                           2,428B/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid-updates/multiverse Sources              
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 42.6kB in 18s (2,284B/s)                                               
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by cdenley on 2010-05-20
So you can download the headers fine until you use apt-get. Are you using a proxy specifically for apt-get?
```

cat /etc/apt/apt.conf.d/*|grep -i proxy
env|grep -i proxy
sudo apt-get update

```

---

### Post by robofighter on 2010-05-20
It says that the proxys avialable are for http, ftp, and https. All are loopback (127.0.0.1) with the port 8080.

---

### Post by cdenley on 2010-05-20
```

echo -e "GET http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.bz2 HTTP/1.0\n"|nc -q 1 -w 4 127.0.0.1 8080|strings|head -n 30

```

---

