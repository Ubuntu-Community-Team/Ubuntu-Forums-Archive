---
title: "Upping Open File Descriptors"
date: 2009-03-26
forum: Server Platforms
---

### Post by Newmaniese on 2009-03-26
Ok, this is becoming a real problem, my Web/nfs server is using all of its file descriptors. This is causing quite a bit of latency and causing me to pull my hair out. 

I have made sure to place in /etc/security/limits.conf:
```

*   hard    nofile  65536
*   soft    nofile  65536

```

I also updated sysctl.conf:
```

fs.file-max = 65536

```

After sysctl -p I can 
```

$ cat /proc/sys/fs/file-max 
65536

```

but ulimit -n still reads 1024. And trying to set it leads to errors:```

$ ulimit -n 65536
-bash: ulimit: open files: cannot modify limit: Operation not permitted

```

In the end I really need this increased for all users, including the www-data process. I am really having difficulty here. 

BTW, I am using Hardy.

Thanks for any help, Mn

---

