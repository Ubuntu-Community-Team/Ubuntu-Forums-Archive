---
title: "404 While updating."
date: 2011-11-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nperry on 2011-11-12
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libcups2 amd64 1.5.0-11
  404  Not Found [IP: 91.189.92.182 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libcups2 i386 1.5.0-11
  404  Not Found [IP: 91.189.92.182 80

Anyone else getting the same?

Thanks
Neil

---

### Post by suspect x on 2011-11-12
> **nperry said:**
> Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libcups2 amd64 1.5.0-11
  404  Not Found [IP: 91.189.92.182 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libcups2 i386 1.5.0-11
  404  Not Found [IP: 91.189.92.182 80

Anyone else getting the same?

Thanks
Neil
i did got such a message although the link is up to date and want a way to fix it
also i've got a "forbidden" alarm .if any one can help us

---

### Post by ronacc on 2011-11-12
it looks like libcups2-1.5.0-10 is the newest in the repo so -11 hasn't been uploaded yet or else it is a typo in the depends for something .

---

### Post by 3vi1 on 2011-11-12
Don't worry about it; it's the repo.  Apparently they have a lot of files that still need to upload:

```
Err http://archive.ubuntu.com/ubuntu/ precise/main libexpat1-dev amd64 2.0.1-7.2
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libexpat1 i386 2.0.1-7.2
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libexpat1 amd64 2.0.1-7.2
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libltdl-dev amd64 2.4.2-1ubuntu1
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libltdl7 i386 2.4.2-1ubuntu1
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libltdl7 amd64 2.4.2-1ubuntu1
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libx11-xcb1 i386 2:1.4.4-4
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libx11-xcb1 amd64 2:1.4.4-4
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libx11-data amd64 2:1.4.4-4
  404  Not Found [IP: 91.189.92.184 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libtool amd64 2.4.2-1ubuntu1
  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_2.0.1-7.2_amd64.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_2.0.1-7.2_i386.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_2.0.1-7.2_amd64.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl-dev_2.4.2-1ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl7_2.4.2-1ubuntu1_i386.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl7_2.4.2-1ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-xcb1_1.4.4-4_i386.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-xcb1_1.4.4-4_amd64.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-data_1.4.4-4_all.deb  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_2.4.2-1ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.184 80]

```

---

