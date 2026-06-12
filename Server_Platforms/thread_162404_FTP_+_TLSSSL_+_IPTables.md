---
title: "FTP + TLS/SSL + IPTables"
date: 2006-04-18
forum: Server Platforms
---

### Post by jinacio on 2006-04-18
I was wondering if there is any way to get and FTP server using TLS or SSL running behind a firewall...

I have the usual rule to open port 21, and it works as it should for unencripted connections, but when i connect from a ftp client using TLS or SSL, i can't get anything past the login (starting with the directory listing)

Has anyone came up with some kind of solution for this?

---

### Post by jinacio on 2006-04-20
Ok, i just found the answer on another [thread]("http://ubuntuforums.org/showpost.php?p=680757&postcount=4")

basicly the ftp server should be configured with a range of ports to use in PASV mode, and those ports can be opened in the firewall

vsftpd config section example:
```

pasv_enable=YES
pasv_min_port=3000
pasv_max_port=3010

```

---

