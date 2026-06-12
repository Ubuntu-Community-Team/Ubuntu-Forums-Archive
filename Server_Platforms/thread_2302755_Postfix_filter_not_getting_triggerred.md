---
title: "Postfix filter not getting triggerred"
date: 2015-11-13
forum: Server Platforms
---

### Post by akash16 on 2015-11-13
Hi All,

Need help with configuring postfix content filter. I added the below config to the master.cf file, however the script is not getting triggered. Are there any other configuration changes that I need to make?  

The "myscript" script is not called when postfix receives and sends messages.

------
```

smtp      inet  n       -       -       -       -       smtpd   -o content_filter=filter:dummy

```

```

filter     unix    -       n       n       -       -       pipe
    flags=Rq user=filter argv=/etc/postfix/myscript -f ${sender} -- ${recipient}

```


Thanks
Akash

---

