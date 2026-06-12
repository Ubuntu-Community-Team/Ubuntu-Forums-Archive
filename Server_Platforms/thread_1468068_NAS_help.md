---
title: "NAS help"
date: 2010-05-01
forum: Server Platforms
---

### Post by dd1313 on 2010-05-01
Hi GUys

I am new to ubuntu and have been reading instructions 
[here]("http://samiux.wordpress.com/2008/08/12/howto-home-made-nas-server-with-ubuntu-8041-%E2%80%93-part-i/") on how to setup a NAS.My question is how can I have my folders acessible from a remote location, connect from home to office NAS.

Thanks
Devan

---

### Post by bgabga on 2010-05-01
use FTP

---

### Post by dd1313 on 2010-05-01
> **bgabga said:**
> use FTP


Is here any other option that enables connection via a browser
besides FTP

Thanks
DD

---

### Post by bgabga on 2010-05-04
Webmin, but is only for management and cli.

---

### Post by arrrghhh on 2010-05-04
Sftp/ssh...

You could setup something like ajaXplorer, but you'd need a web server (which I assume you were aware of since you want to access via a browser...)

If that's the case, then yes... use ajaXplorer if you want a webUI to handle your files with.  I just use SFTP and WinSCP if I'm on a Windows client.

---

